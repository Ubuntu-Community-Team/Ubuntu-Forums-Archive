---
title: "Good way to keep multiple servers up to date?"
date: 2007-08-17
forum: Server Platforms
---

### Post by Viruk on 2007-08-17
Hi, 

I started looking around the forums to find out if there was an equivilent to WSUS to update several servers but only downloading the data once.

I run a few basic servers now (ticketing/wiki/cacti etc) and wondered if there was a way to avoid downloading the same updates for each box - I was thinking something that is (functionally at least) a little like WSUS but I appreciate there may be better ways to do this that I haven't thought of yet. 

Any suggestions for a good way to minimise the effort (and bandwidth used) updating ubuntu servers would be greatly appreciated. 

While searching for an answer to my question I just found out the news about the LoCo servers - sorry to hear that, but I think it may be a good time to cover this question to help people keep things up to date.

---

### Post by heimo on 2007-08-17
For saving bandwidth, one of these may help:
[http://packages.ubuntu.com/feisty/net/apt-cacher](http://packages.ubuntu.com/feisty/net/apt-cacher)
[http://packages.ubuntu.com/feisty/admin/apt-proxy](http://packages.ubuntu.com/feisty/admin/apt-proxy)

---

### Post by Viruk on 2007-08-17
Thanks for a really quick reply - they both look like they would do the job nicely =)

Is there much difference between these packages? They look like they do pretty much the same thing - have you tried both? Can you reccomend one rather than the other?

Is the best way to automatically update to run a cron job on each server that updates from a server running one of those packages?

---

### Post by koenn on 2007-08-17
I use apt-proxy at home and find it easy to use and well documented (most documentation refers to the debian package, but applies to the ubuntu version as well). Can't comment on apt-cacher - never used it. 

You could use a cron job to check for, download, and install updates, but you should ask yourself if you *should* - you might want to read changelogs or test the packages before you install them, if your servers are production servers of some importance.

---

### Post by Viruk on 2007-08-17
I've been having a read around since my last post, from what I can see it looks like apt-proxy might be the better option for me. 

Apart from anything else the ubuntu documentation is better for [Apt-Proxy]("http://help.ubuntu.com/community/AptProxy") :)

> You could use a cron job to check for, download, and install updates, but you should ask yourself if you should - you might want to read changelogs or test the packages before you install them, if your servers are production servers of some importance. 
Fair point, but finding time to test things adequately is extremely hard here. I stick to 6.06 LTS, do you think this reduces the need for testing new packages compared to using a newer version?

---

### Post by koenn on 2007-08-17
I suppose it's mostly a matter of trade-offs (isn't everything ?) - what's worse : running an unpatched system, or applying patches without verifying if they'd cause trouble on *your* system(s) ? 

Running LTS is a good choice - updates are limited to critical patches / security updates so you don't risk getting "latest newest bleeding edge but possibly buggy" updates, and if an occasional bad patch finds its way to a repo, it's usually quickly followed by a fix, so unless you need to guarantee 99% uptime on those servers, I guess you can risk it. But it's not my call, really.

---

### Post by Viruk on 2007-08-17
Thanks for replying again koenn - I appreciate your feedback, its nice to hear as many opinions as possible when forming your own. I am just weighing up my options at the minute and trying to find out if there are any major pros or cons that I may have missed. 

I don't have enough experience of Ubuntu to know what my chances are of getting an update that breaks things. I have been using ubuntu server for about a year now and have been very impressed with the updates, unlike the updates for another server OS that have broken quite a few apps on the other type of server I look after ;)

---

### Post by koenn on 2007-08-17
I've seen 2 bad updates in the year I'm using ubuntu. The infamous X server breakage, and a recebt thread here somewhere about a broken package, and a fix on its way within minutes. So I'd say they're doing OK. 
You're probably not running X on a server, but it's that kind of thing you 'll wish you'd catched before you installed the update it on a production system/

---

### Post by ihristov on 2007-08-17
Another way that works completely efortlessly is to use a transparent HTTP proxy.

My firewall is IPCop and I have enabled the transparent option for Squid and it works great.

It would apply to all your HTTP traffic, not only apt, but works great and requires 0 configuration on the Ubuntu machines.

---

### Post by netlogic on 2007-08-17
I suggest use LTS for servers.

On your /etc/crontab
# m h dom mon dow user  command
* *   * * *     root    apt-get update
* *   * * *    root    apt-get upgrade -y

I never had any problems with any updates. I only use Ubuntu supplied packages and apps that I compiled it myself. Anything, I compiled it myself, I just get on the applications mailing lists for the news about critical errors, which is received to another mail account that I don't manually read. I have a simple script to grep for keywords in the mail spool and anything important, the mail gets forwarded to my regular account and my phone. I use no  backports, universe, and multiverse for the servers. I don't trust the community to maintain things in the mission critical time.

---

