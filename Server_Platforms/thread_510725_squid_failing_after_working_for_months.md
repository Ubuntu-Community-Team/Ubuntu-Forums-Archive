---
title: "squid failing after working for months"
date: 2007-07-26
forum: Server Platforms
---

### Post by bturrie on 2007-07-26
I went on a business trip this week when I got home my squid proxy server was not working. It had worked fine for months but now it won't. I'm running my ubuntu dapper server in vmware. I.ve tried several things to no avail here's what I tried



restarting my cable modem
restarting my router
restarting networking on the host machine 
Restarting networking and squid on the virtual machine
turning off all my firewalls

a different virtual machine with squid in xubuntu dapper (firefox can connect from that machine

nothing has worked. Any thoughts?

---

### Post by koenn on 2007-07-27
restart squid and see if it compeins about anything
```
/etc/init.d/squid restart
```

look at the log files in /var/log/squid/ to see if they mention anything gone wrong.

---

### Post by bturrie on 2007-07-27
Thanks for the suggestion. I'd already tried restarting squid, but never looked at the logs. Anyway, i stopped squid restarted it, tried to call up something via the squid, shut squid down and then went to the log directory as you suggested.

In the access.log I found lots of lines that contained TCP-MISS/503

as best I can tell the first part means that it could not find the site in the cache (which seems strange since it was google.com which i call up all the time

the second bit means Service Unavailable but I don't know whether that means the cache was unavailable or squid couldn't get to the internet. either one seems bad. worse I don't understand how either one could be happening.

---

### Post by koenn on 2007-07-28
on first sight that looks as if the page you requested was not in cache (MISS), and could not be retrieved from the web server (503).
Assuming that google is always online, there could be a network problem between squid and the internet.
You could check if the machine that runs squid can access webservers by telnetting to port 80 of a webserver, from a shell on the squid machine itself, eg
```
$ telnet www.google.be 80
Trying 66.249.91.99...
Connected to www.l.google.com.
Escape character is '^]'.

GET
Connection closed by foreign host.
kn@knix:~$

```
Here, you see that the connection is succesful - "the connection closed by foreign host" is because the GET command is incomplete.

---

