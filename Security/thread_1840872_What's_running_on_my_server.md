---
title: "What's running on my server?"
date: 2011-09-08
forum: Security
---

### Post by clegends on 2011-09-08
Hi, I'm running 10.04.1 server on my system... D510 pinetrail motherboard (dualcore) with 2Gb of ram. Low powered, runs at abot 60 watts, etc. I'm using it to host 3 websites, one of which is having fairly steady traffic, a citadel groupware server, which hosts about 12 email accounts, LAMP stack,, dns, and various other bits and pieces. I'm aware that using all this on one box is not advised, so that's not the issue.

I'm wondering how I tell what trafic is going through my server at a given time, and what processes are being used? Just now I noticed lots of connection activity through our modem, and could hear various hard disk operations in our server... and no, I was not using it. I checked out busiest site, and no one was on it. No process currently would make sense to be generating this... no mailouts were being sent out, very few processes running, etc. And yet the top comand showed memory usage at 50%.

So my question, what logs do I look at to preview what's happeningover the past 24 hours, and what logs can I look at 'as this happnes'? Cheers.

---

### Post by Lars Noodén on 2011-09-08
> **clegends said:**
> I'm aware that using all this on one box is not advised, so that's not the issue.


It's fine to do so.  That's how Linux systems are designed - to successfully be running many services.

> **clegends said:**
> 
I'm wondering how I tell what trafic is going through my server at a given time, and what processes are being used? 

Would something like Cacti do what you want?
 [http://www.cacti.net/](http://www.cacti.net/)

---

### Post by BkkBonanza on 2011-09-10
The simplest tool for watching processes is **htop**. You can install it with,

sudo apt-get install htop

The netstat command is useful for quick checks of connections,

**sudo netstat -ntp**
or
sudo netstat -lntp
(which shows what services are listening on what ports)

There are some other packages for monitoring traffic. eg. apachetop is apache top tool shows what connections apache is handling, and similarly for mytop for mysql connections.

The **iptraf** package is pretty good for keeping an eye on net traffic too.

There is a lot of other things out there and it just depends on what you need and the balance between logging/realtime and presentation.

---

### Post by MCr3sist on 2011-09-14
You might also try 'ps' if you happen to notice it happening again.

for example:

ps -C apache2 u

That would show you Mem/CPU resource usage for any apache2 processes running on your server at that moment.  It would also show you what user.

you could also run 

ps -e u > file.txt

then review the file.  That would show you every process running.  Maybe shed some light onto which process is using the resources.

---

