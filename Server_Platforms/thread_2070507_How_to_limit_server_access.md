---
title: "How to limit server access?"
date: 2012-10-12
forum: Server Platforms
---

### Post by ELMIT on 2012-10-12
I got a problem with a search engine crawler. It is nice when they come, but now they kill my site: Bing e.g., found my blog and crawles back to day 1, - not with 1, but with xx instances. Server load I could see was 96 !!!!

I want to limit access to the server so that the load is in a "normal range"

Is there a way to limit search engines to one instance only?
Is there another way to limit acces when it is geting critical?

The wordpress blog uses a database and this one is at his moment still on the same cloud instance. I hope that I can get this out into another instance soon.

---

### Post by lisati on 2012-10-12
The [robots.txt]("http://www.robotstxt.org/") and [.htaccess]("http://en.wikipedia.org/wiki/Htaccess") files might be good places to start.

---

### Post by ELMIT on 2012-10-12
I don't see how I can limit with that, just how to block, ... that is different.

It does not bother that the robots are coming, just too many at once is not good.


And what if it is just a great article that 1000s of people want to see? Maybe I limit in apache2.conf:

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

change to MaxClients  to 10

What is your opinion?

---

### Post by HermanAB on 2012-10-14
Howdy,

Iptables has a limit function.  You can experiment and change the below somewhat.

```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

```

---

### Post by sandyd on 2012-10-14
> **ELMIT said:**
> I don't see how I can limit with that, just how to block, ... that is different.

It does not bother that the robots are coming, just too many at once is not good.


And what if it is just a great article that 1000s of people want to see? Maybe I limit in apache2.conf:

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

change to MaxClients  to 10

What is your opinion?
You can.

you are looking for the Crawl-Delay function ```

User-agent: Google
Crawl-Delay: 120

```

That only works for Yahoo - you will have to use Google webmaster tools to accomplish the same for google. [http://support.google.com/webmasters/bin/answer.py?hl=en&answer=48620](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=48620)

Btw, is this the blog you mentioned in the other thread?

If it is, there are actually some managed providers that specialize in Wordpress Hosting, and you may find hosting at those places a bit easier. Some of the more popular ones today are Page.ly, Zippykid, and WPEngine.

---

### Post by thnewguy on 2012-10-14
You can use the ufw firewall tool to easily limit mass connection attempts like this. A simple command line

sudo ufw limit 80/tcp

should do the trick, assuming your web server is running on port 80. I believe that, by default, the client is limited to 6 connections within 30 seconds, which should be enough for normal users, but it will slow down web crawlers.

See the "man ufw" page for more details.

---

