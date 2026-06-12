---
title: "ubuntu server vs redhat servers"
date: 2009-04-22
forum: Server Platforms
---

### Post by salim.madni on 2009-04-22
hello sir

we want to switch our redhat 4/5 to ubuntu server. we are using oracle 10g. can some one comments suggest.

is it stable reliable durable unbreakable to use ubuntu server.

redhat response taking years to reply now a days. the support is not good enough in our area. i dont know what exactly problem there.

can someone suggestion advise

and is there any article available how and why ubuntu server is better then other redhat,suse better or best

can some one share his experience knowledge article website that help how to make build and performance

everyone when we ask, people say go to redhat go to suse or go to unbreakable linux of oracle distribution

kind regards
salim

---

### Post by Stuggi on 2009-04-22
Ubuntu is based on Debian, which is probably one of the most stable server Linuxes. Debian is a bit more stable as Ubuntu is based on testing/semi-unstable Debian releases. That said, unstable Debian has worked without flaws on my server for 4 years non-stop, so Ubuntu should be stable enough. :D 

What kind of servers are you running? File/Print, databases, LAMP?

---

### Post by salim.madni on 2009-04-22
dear gurus

thanks for details

we are using all servers on various machines some are redhat base and some are windows 2003/2000 servers

we are planning to switch move to ubuntu

but since it is based on debian, so debian server are update more fastly or how it is?

shell we prefer to use ubuntu or debian servers

regards
salim

---

### Post by Spikerok on 2009-04-22
no difference.. only difference is in shell. Any OS can be secured it. depends on admin

---

### Post by salim.madni on 2009-04-25
i would revised statement any linux distribution can be secured

rather using windows

but suggest and advise something if i can share with someone experiences in past

---

### Post by fabsbsd on 2009-04-25
Hi!

Ubuntu is good option but is not supported by Oracle, at least not the last time I checked,

If you are using Oracle Express Edition you should be ok, and you can buy support from Canonical

cheers!

---

### Post by HermanAB on 2009-04-25
Howdy,

Linux is Linux is Linux...

Down at the bottom of it all there is no difference between distributions, they all use the same projects for the various components.  The place where things are different, is at the desktop, GUI and wizard level.  In general, the best wizards are in Mandriva, Suse and Redhat (in that order).  So if you are a pointy-clicky kind of administrator, then you should probably stick with what you got.

If you have trouble with Redhat, then you will likely have the exact same trouble with Ubuntu, Mandriva, Suse or whatever, since as I said, they are all the same down in the dirty.  Your best solution is to buy some books and clue yourself up.

In the mean time, when you got things working - leave it the heck alone - don't do automatic updates to a server, ever - don't fix it if it ain't broke - most Linux problems are caused by finger trouble.  I install my servers and then leave them alone for about 3 years, then I re-install them and run them for another 3 years, then I throw them away and install new servers.  Linux servers are almost zero maintenance - the more you try to actively maintain them, the more they will screw up, so don't.

---

### Post by NathanDS101 on 2009-04-25
Hello,

I think you would enjoy Linux there are several tyoes if you didnt know. Kubuntu, Xubuntu, MythUbuntu and i think several more. Good Luck budyy

---

### Post by bigbearomaha on 2009-04-25
> no difference.. only difference is in shell. Any OS can be secured it. depends on admin

I don't mean to be disagreeable, but that is simply not true.

If it were as simple as being Debian, then there would be no point in having ubuntu.  There IS a difference.

Not only is it 'based' on debian testing, Ubuntu modifies the packages, sometimes in a manner that do not lend to increased security, and at times have led to reduced security.

I don't know of too many production servers using 'testing' based repos.  The VAST majority will prefer to stay well within the confines of 'stable' repos of Debian, CentOS, RHEL, Suse, et al...

Really, I am not trying to rain on Ubuntu's parade here, it makes a darn fine LAN server.

I personally would not use or recommend it over a WAN/Web facing though.

the argument 'linux is linux is linux'  works for generalities.  comand line functionality, general interface issues, etc..

However, each distro uses different specs and methods for packaging that do not equate to the methods used by another distro.

Sometimes those packaging methods are considered as 'more reliable' such as Debian enjoys, without qualification, sometimes, those methods do not warrant such undoubtable fame.

Debian is Debian, Ubuntu is Ubuntu, there is a difference.

to the OP,  If you don't like the support RHEL is providing ( and I wonder if you are paying for support, if so, a nasty phone call to upper management may be in order)  if you are not, then as with any unpaid support, you are expected to do a bit of your own homework first.

---

### Post by TR1X on 2009-04-25
I only recently made an ubuntu server, but it works wonders.

100% uptime

---

### Post by linux_tech on 2009-04-26
Oracle on Deb
[http://mediakey.dk/~cc/howto-install-oracle-on-debian/](http://mediakey.dk/~cc/howto-install-oracle-on-debian/)

---

