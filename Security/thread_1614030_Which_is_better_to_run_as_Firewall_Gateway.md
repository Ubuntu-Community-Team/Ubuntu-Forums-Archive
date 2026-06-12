---
title: "Which is better to run as Firewall Gateway?"
date: 2010-11-05
forum: Security
---

### Post by sadaruwan12 on 2010-11-05
I'm pretty new to linux server side. I'm looking at two distro's

[LIST=1]
[*]Ubuntu Server 10.04
[*]ClearOS
[/LIST]

I'm currently running a win2003 server with a proxy software which has user authentication when they want to use the internet but I now use the MAC address to give access.

What I want to do is to have linux server which run as my proxy and my firewall. Currently I'm not running a firewall 'cos It's too costly.

I need to have good content filtering as well 'cos our most user are addicted to face book and porn. Currently I'm using openDNS as my main content filtering service but it seems to be not very customizable.

So I want to have good URL block + content filtering as time moves on I'm planing to have an email distribution server as well which will download all the emails from all the clients in our parent server and distribute them locally after ward.

Please help me if I'm posting this in wrong place please move it to the right one but please help with this.

And thank you in advance for who replied and to the people who just had a look.

---

### Post by gary0 on 2010-11-05
If you're looking for a hardware (linux) firewall, take a look at Smoothwall. It is a dedicated firewall and can be installed on that old junk computer you have over there in the corner...

---

### Post by sikander3786 on 2010-11-05
For firewall only purposes, I found IPCop to be a great distro.

[http://sourceforge.net/apps/trac/ipcop/wiki](http://sourceforge.net/apps/trac/ipcop/wiki)

If you want to stick to your mentioned one's, I would say Ubuntu Server as these are Ubuntuforums :-)

---

### Post by sadaruwan12 on 2010-11-05
Thank you guys

---

### Post by bioterror on 2010-11-05
Or you can try Zentyal (eebox or something like that) [http://trac.zentyal.org/wiki/Document/Documentation/InstallationGuide]("http://trac.zentyal.org/wiki/Document/Documentation/InstallationGuide") At least I got that one working and the web interface is pretty good.

But still, I'm going to say this: pfSense, I'm using it all the time in my home.

---

### Post by sadaruwan12 on 2010-11-05
Thank you I'm down loading it right now.

Or can turn my ubuntu server in to a good proxy and a firewall machine by using some kind of good software.

I know I can use SQUiD as my proxy and webAdmin as the configuration interface but as the firewall what can I do.

Any one to suggest some thing?

---

### Post by CharlesA on 2010-11-05
I've played around with pfSense and had good results.

As for configuring it, the web interface should be all you need.

---

### Post by uRock on 2010-11-05
Moved to Security Discussions.

---

### Post by ubudog on 2010-11-05
CentOS is probably the best server distro around.  CentOS is pretty secure, and you can use it for about anything. It's free, compared to RHEL and is pretty much the same thing.  Iptables is a great firewall tool.

---

### Post by sadaruwan12 on 2010-11-05
OK, I've used CentOS but I don't like it much I think Ubuntu Server is much better but can any one verify that.

I want to use Ubuntu Server if nothing comes up I'll go with CentOS.

---

