---
title: "Ubuntu Server basic cPanel functions"
date: 2011-04-04
forum: Server Platforms
---

### Post by HittingSmoke on 2011-04-04
This is a broad issue as I'm sort of asking several technical questions in the form of one shotgun question about Ubuntu Server management from the command line.

I've had web sites hosted before and all companies had cPanel available to manage it. All of my Linux experience is with Ubuntu, so when I decided to set up a test web server on my LAN, Ubuntu Server was a no-brainer.

My question is, breaking down essential services, how do you manage them from the command line with no cPanel access? Anti spam and other things aside of course. For clarity I'll just break down what I can think off off the top of my head.

Things I know how to manage:
SSH Server
FTP Server
Apache settings

Things I don't:
DNS
Subdomains
MySQL databases (although I know how to use PHPMyAdmin)
Mail (ALthough I haven't tried this one yet)

It would be nice if there was a comprehensive all-in-one guide that walked you through all of the basic features included in cPanel and explained how to do those on Ubuntu over SSH.

If there is no such guide, my main question is how to manage subdomains through the command line and do I need to be running my own DNS server to do so? On google the only info I've found is how to do it over LAN using hosts.

If I can get all of the info I need put together, I may make an HTML cPanel recreation where if you click on a feature it takes you to a guide to manage it via the command line. I think it would be a helpful tool for Debian/Ubuntu users who don't want to learn CentOS to run a web server.

If I've left anything out regarding basic web server management, feel free to include it.

---

### Post by DaltonXJ on 2011-04-05
[http://www.webmin.com](http://www.webmin.com)  
 
this might be what you are looking for...

---

### Post by HittingSmoke on 2011-04-05
> **DaltonXJ said:**
> [http://www.webmin.com](http://www.webmin.com)  
 
this might be what you are looking for...

Thanks! I spent quite a while looking for something like this and didn't come across this one.

Ideally, in the end, I'd like to learn to do it all via the command line, but this will help me fill in gaps as I learn.

---

