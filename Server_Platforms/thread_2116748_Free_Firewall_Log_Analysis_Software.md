---
title: "Free Firewall Log Analysis Software?"
date: 2013-02-16
forum: Server Platforms
---

### Post by sixstorm on 2013-02-16
I currently have 2 Fortigate firewalls that I manage.  The built-in log analysis reports aren't bad, but when you get more than 10 devices, it isn't so great any more.

I basically want to find a free software piece to analyze my firewall logs; I also mainly want some reporting that I can pull for individual IPs, stuff like "Top Domain Requests" and such.  Anything like this exist for Ubuntu/Debian?  Everything I can find costs quite a bit for our organization.

---

### Post by chadk5utc on 2013-02-16
I use logwatch for my setup but another suggestion to look at splunk and a few others.

---

### Post by sixstorm on 2013-02-17
> **chadk5utc said:**
> I use logwatch for my setup but another suggestion to look at splunk and a few others.

How do the reports look?  I've been trying to find more screens and report examples, but it's a no go.

---

### Post by sixstorm on 2013-02-17
After asking over at Reddit, I've been recommended Kibana and Logstash.  Will try these out hopefully this week and report back for anyone else wanting to know the same thing as me.

---

### Post by sixstorm on 2013-02-18
Update:  Logstash is pretty nice so far, but I ran into an issue with setting up and running Kibana.  Waiting on some help via IRC.

My Combo:  rsyslog+logstash+(built in)elasticsearch+kibana

Pretty straightforward install and setup, even for a noob.

---

### Post by sixstorm on 2013-02-20
So it doesn't look like Logstash likes the pattern for the Fortinet syslogs.  Not sure what to do now.

Guess I could make a MySQL DB and feed syslogs into it . . . but argh.

---

