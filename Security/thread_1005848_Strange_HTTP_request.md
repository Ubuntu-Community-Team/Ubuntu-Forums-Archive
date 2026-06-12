---
title: "Strange HTTP request"
date: 2008-12-08
forum: Security
---

### Post by Dr Small on 2008-12-08
My dad has assigned me to figure out what is happening on our website, as he reads the access logs like your grandfather does the newspaper. He has seen this one line continuously keep accessing the website, and he believes that we are being hacked...

Anyhow, here is the line:
```
193.200.50.5 - - [07/Dec/2008:18:22:47 -0600] "GET http://cpanel.sslpayments.com/ HTTP/1.1" 200 13897 "-" "-"
```

[LIST=1]
[*]The IP Address is from Romania
[*]It continuously access the site every 13-14 minutes
[*]The address it is requesting is off site, and if you notice, it is an "Access Denied" page. Strange in itself.
[*]No referring link
[*]No Useragent (because it is a bot).
[/LIST]

If anyone could provide some additional information on what is actually happening here, if this is causing any harm, and if it is, how we should attempt to stop it, as it is using 13897b every time it comes.

Dr Small

---

### Post by Kinstonian on 2008-12-08
I'm not sure what exactly it is.  My guess is that it's some kind of automated attack that has failed.  Then again, I'm no expert.

How long have those connection attempts been going on?  Are there any other relevant logs relating to that IP?  Are there any other relevant logs relating to that cpanel page?  It probably wouldn't hurt to firewall the offending IP.

Kudos to your dad for reviewing the logs though.  I'm not sure if you meant he was just using grep and a pager... if he is, something like Splunk would probably make things a lot easier for him.

---

### Post by Dr Small on 2008-12-08
We are hosted on a Shared Server, so firewalling the IP isn't much of an option, and I don't think .htaccess would stop it, although I could try. Those connections have been going on for about 2 days now. At first, there was more time between them, and then they have just become more frequent throughout the day.

He actually reads the log through the browser, from a script I wrote for him that displays the log for that day (since logroller rolls the logs every evening) and he just refreshes it and views the logs. I don't think he would understand grep or a pager :D

Thanks for replying though.
He keeps telling me that someone is trying to 'access our cpanel', which we don't have (since the webhost is using Hsphere), and he thinks we are getting hacked. I don't know what to think either, but it looks like the bot is using the connection as a proxy, but how I don't know.

---

### Post by cdenley on 2008-12-09
It is very common for someone/something to attempt to use your web server as a http proxy. However, by default, apache will serve the URI of the request, which is why the request returns a 200 status. It is just as if they requested "/", unless you configured apache to work as a proxy. You can try it for yourself.
```

$ nc mydomain.com 80
GET http://cpanel.sslpayments.com/ HTTP/1.1
Host: mydomain.com


```
That is one command, then the rest should be typed in standard input. The input is terminated by a blank line. You should see the same page as [http://mydomain.com/](http://mydomain.com/) in the output.

---

### Post by Dr Small on 2008-12-09
Thanks for that information. I never understood how to use netcat properly, and I guess I need to do some futher research on it.

Apache is not configured to work as a proxy. I have seen the VirtualHost container before. Besides, the webhost probably wouldn't approve of it! :D

So really, is this automated request doing any harm, other than using 13KBs every time it comes?

---

### Post by cdenley on 2008-12-09
> **Dr Small said:**
> So really, is this automated request doing any harm, other than using 13KBs every time it comes?

No. It shouldn't be any different than "GET / HTTP/1.1".

Netcat is a useful little tool for simple protocols like FTP, SMTP, or HTTP. All it does is open a socket connection on the specified host/port, then pipe the input/output over that socket. Basically, you talk to the server the way a client (in this case a web browser) would. You can do the same thing with the telnet command.

---

### Post by toddkaufmann on 2008-12-16
> **Dr Small said:**
> My dad ... has seen this one line continuously keep accessing the website, ...

Anyhow, here is the line:
```
193.200.50.5 - - [07/Dec/2008:18:22:47 -0600] "GET http://cpanel.sslpayments.com/ HTTP/1.1" 200 13897 "-" "-"
```

[LIST=1]
[*]The IP Address is from Romania
[*]It continuously access the site every 13-14 minutes
[*]The address it is requesting is off site, and if you notice, it is an "Access Denied" page. Strange in itself.
[*]No referring link
[*]No Useragent (because it is a bot).
[/LIST]

If anyone could provide some additional information on what is actually happening here, if this is causing any harm, and if it is, how we should attempt to stop it, as it is using 13897b every time it comes.

Dr Small

I've been seeing this exact thing in my log for a while now (month or so).

```

193.200.50.5 - - [16/Dec/2008:12:53:11 -0500] "GET http://cpanel.sslpayments.com/ HTTP/1.1" 403 425 "-" "-"

```

I've thought about adding a configuration to apache httpd so it could proxy this request, and then see what kind of traffic occurs..  but I've been too lazy to look it up (send me a sample if you got one handy).

Or add an ipfilter rule to block their traffic and just ignore it.

There are a fair amount of http servers on that network.  It seems odd that either 
1) something would be misconfigured and go to my IP (and your IP), or 
2) someone is scanning for some exploit here (not documented anywhere), 
3) looking for a proxy -- this is the most likely, but why with this URL?  And why every 14 minutes?

---

### Post by caesar77 on 2009-04-10
It's some kind of a portscanner

I've encountered the same requests on my windowz servers where I got a portguardian running on, wich shows me the ports with the requests done.

It tries to connect on a certain port, 3 seconds after that it tries again then the next try is 6 seconds later (each time on the same port) then approx 22 minutes later it tries again on another port.

---

