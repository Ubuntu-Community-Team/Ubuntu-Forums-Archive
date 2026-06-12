---
title: "Monitoring MySQL-PHP-Apache on Ubuntu Server 12.04.4"
date: 2014-08-08
forum: Server Platforms
---

### Post by matthiascsg on 2014-08-08
Good morning, 

I have a situation, and I'm kind of stuck. I have a web application (SugarCRM). It requires MySQL, Apache and PHP. A few months ago this application was running on one server (databases & application on the same server). Everything was working fine. Then it was decided that the application and databases were to be separated on two servers. I now have delays (30 seconds and more, or even a frozen application) when browsing into the application.

Here are the different versions of softwares : 

- PHP version 5.3.10
- mySQL version 14.14 
- Apache version 2.2.22 (All these software installed from Aptitude)

I compared the configuration files I had on the server that worked fine, but could'nt find any differences that could cause this.

So, do you guys know a good software, or a good way to monitor what the application is requesting or doing while it's freezing or when there are delays ?
I could display the log of each application (PHP, Apache, MySQL, SugarCRM) while it's happening, I guess. But is there an easier way to do it ? 

I would like to understand what's happening behind the scene.

Thank you for your consideration,

--
Matthias.

---

### Post by SeijiSensei on 2014-08-08
Start by using telnet to connect to port 3306 on the MySQL server.  How long does that take?  If that works fine, use the command-line mysql client and see what happens.

Any weird routing issues?  What does the command "route -n" show?  Is there only one way for the client to connect to the server?  Sometimes multiple routes to the same address can slow things down.

It could also be an issue with name resolution.  Make sure both machines can resolve the other's name, and that reverse IP resolution is set up in your DNS.  Alternatively add an entry for the other machine in each server's /etc/hosts file.  Alternatively you can also use IP addresses rather than hostnames throughout.

Are the two machines on the same network?  Any firewalls in the way?  If they're not on the same subnet, use traceroute to see if there are any delays when connecting from the client.

I use PostgreSQL rather than MySQL and connect to remote servers nearly instantaneously.  It should be the same for you.

---

