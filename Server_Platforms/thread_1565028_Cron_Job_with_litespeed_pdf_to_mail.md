---
title: "Cron Job with litespeed pdf to mail"
date: 2010-08-31
forum: Server Platforms
---

### Post by rajatjpatel on 2010-08-31
Hi all :KS

I have install Ubuntu 10.04 server with litespeed web server php5 / mysql and tcpdf every think working very well.


we have url like that [https://test-ubuntu.com/datatools/](https://test-ubuntu.com/datatools/)
To Run The Tool: Info -> Profiler (drop down menu)

it will ask for email id once you provide it will sent mail to use one link 

[http://173.XXX.XXX.XXX/datatools/rep...2010-08-27.pdf]("http://173.xxx.xxx.xxx/datatools/reports/Company_name_Inc-2010-08-27.pdf")

my question to you all is 

i want this think to happens through cron and i dont know how to coding if any one has done before like wise pls share with me

i have suggestion on above question if we have same think like that 

watch /root/datatools/report/IntegraMed-echo "$(date)".pdf (grep -i todays date)
wget [http://173.xxx.xxx.xxx/datatools_raj/comapany-name-inc-echo](http://173.xxx.xxx.xxx/datatools_raj/comapany-name-inc-echo) "$(date)".pdf
MAILTO=rajatjpatel@gmail.com

---

