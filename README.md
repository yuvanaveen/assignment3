# assignment3


getwd()
install.packages("lubridate")
library(lubridate)

install.packages("tidyverse")
library(tidyverse)


head(StormEvents_details.ftp_v1.0_d1992_c20170717,5)
myvars <-c ("BEGIN_DATE_TIME","END_DATE_TIME","BEGIN_LAT")
newdata <- StormEvents_details.ftp_v1.0_d1992_c20170717[myvars]
head(newdata,5)

newstorms <- mutate(.data = newdata, BEGIN_DATE_TIME = dmy_hms(BEGIN_DATE_TIME), END_DATE_TIME = dmy_hms(END_DATE_TIME))

str_to_title(CZ_NAME)

str_pad(newdata$STATE_FIPS, width=3, side = "left", pad = "0")

rename_all(newdata, toupper)

us_state_info<-data.frame(state=state.name, region=state.region, area=state.area)

Newset<-data.frame(table(us_state_info$state))
head(Newset)

newset1<-rename(newset, c("state"="Var1"))

merged<-merge(x=newset1,y=us_state_info,by.x="state",by.y="state")
head(merged)

newdatasetname<-(mutate_all(df,toupper))

merged<-merge(x=newset1,y=us_state_info,by.x="state",by.y="state")
View(merged)
head(merged)


library(ggplot2)
storm_plot <- ggplot(state_storms, aes(x = area, y = n)) + geom_point(aes(color = region)) + labs(x = "Land area (square miles)", y = "# of storm events in 2017")
storm_plot


