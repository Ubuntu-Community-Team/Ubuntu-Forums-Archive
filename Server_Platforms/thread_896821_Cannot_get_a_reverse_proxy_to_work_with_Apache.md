---
title: "Cannot get a reverse proxy to work with Apache"
date: 2008-08-21
forum: Server Platforms
---

### Post by bh5505 on 2008-08-21
Hello all,

I have been struggling with this for about a week now with no results. I simply cannot get a reverse proxy to function within Apache2 on Ubuntu Server 8.04.

I originally used CentOS to build a log collection/analysis server using Splunk. The no-cost version of Splunk does not include any type of access control for the web interface of Splunk. I was able to set up Apache to act as a reverse proxy between the Splunk web interface and users to provide access control via a .htpasswd file. [This was the tutorial I used.]("http://www.deckerd.com/splunk-free-htaccess-protection-using-apache/")

I decided to move to Ubuntu from CentOS for unrelated reasons. I built the Ubuntu server (using the most basic package loadout) and restored everything, except for my Apache reverse proxy.

What I am trying to accomplish:

I have a web app currently available (not using Apache) at [http://127.0.0.1:8000/](http://127.0.0.1:8000/). I want to use Apache to make that app available via proxy at [http://192.168.20.13:80](http://192.168.20.13:80) (my server's IP address). I cannot get this to work. I have tried to proxy other things, like Google, with no luck still. Firefox reports that it thinks the site is valid, but cannot display a page. If I can get that proxy to work, I will then work on getting .htpasswd based user access control working. If possible, I would like for someone to explain how to get a proxy working, starting with installing Apache2.

Thanks in advance for all your help. I am a somewhat-seasoned Windows systems admin that is trying hard to learn how to use Linux for these roles.

---

### Post by winddummy on 2008-08-21
You haven't supplied any error messages but the first thing to try might be in this thread [http://ubuntuforums.org/showthread.php?t=838193&highlight=apache+reverse+proxy](http://ubuntuforums.org/showthread.php?t=838193&highlight=apache+reverse+proxy)

---

