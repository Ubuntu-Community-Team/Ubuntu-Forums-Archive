---
title: "Log Monitoring Email Reports"
date: 2014-09-03
forum: Security
---

### Post by daniel.fazio.92 on 2014-09-03
Hello,

In our company we use Logwatch to have a daily report of all logs, by a report for each machine installed.
I don't really know how it works, as It was already presented and configured ages ago this system, before I was starting to look on this. But I know we want to change this method as we get a mail for each host, with too many info (ofc for the info we just need to better filter and config everything), and so reading everyday thousand of long emails is impossibile for us.

We wanted to find some alternative to it, and a good one we found was Splunk. It was able to collect all data, query them with its powerful SPL language and have a daily report of the query output. But of course the license was too expensive.

So we tryed an other alternative: Logstash + Elasticsearch.  From a first look I really like Logstash, on how you can filter all data and have them in a standard format. 
I like less Elasticsearch, maybe because I tryed Splunk before it. The query looks bit messy and difficult to write, to have for example an output which list all the machines where a user (and so the list of the users) failed to log more than x time in a time range. 
Maybe I just have to learn to use it better, but anyway it doesnt suit to us because it doesn't have a report system which should do something like what I just described before. I know there are some Web GUI like Kibana or something else, but they still don't have a report system (and not alert, which is triggered when something happens), and so we don't have to use it to analyze the logs in real time.

Does anybody else had a similiar experience/needs or know some solutions?

Cheers,
Daniel

---

### Post by frankmorris2 on 2014-09-03
Hello,

I am not sure this will fit your needs, but InfluxDB could be used to store your data. InfluxDB comes with a SQL-like query language.

You can use the built-in web frontend or you can also use another frontend like Grafana.

Hope this helps.

Have a nice day.

---

### Post by daniel.fazio.92 on 2014-09-04
Hello, Thank you for the answer.

My main problem is a way to have a daily report system. 
Grafana, like Kibana or Marvel looks to be just a tool for real time analyzing. Where you want to see what happened in a certain time or have a graph to better understand some behavior. We don't need it for this reason. 
We would like to have a tool like Logwatch, but its problem is that you will get a mail from each host, with all the services/logs reporting. We need an email from every services/log type with the list of the machines and the better description/log.
For example an email from sshd with a list of all machines we are monitoring, and for each entry a list of all users that for example failed to login 3 times.
With Logstash and Elasticsearch (when I'll better get used to its query language) I can easily collect all logs from rsyslog, filter them to better separate key=value how we wants, and store theme and query them. But  we are looking for the last piece of the puzzle which set some query and daily report us about their result. We Would like a tools to better have all in one place, let's say without re-inventing the wheel.

Hope it's a bit clearer.

---

