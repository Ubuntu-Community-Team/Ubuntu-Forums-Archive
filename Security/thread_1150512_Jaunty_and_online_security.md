---
title: "Jaunty and online security"
date: 2009-05-06
forum: Security
---

### Post by GL_NORWAY on 2009-05-06
I'm soon going to put a lot of faith into Ubuntu. I'm talking about putting a lot of my life  
and privacy into this OS that I haven't used before, like online banking services,  
credit card purchases, e-mail, web hosts, and things that involve ones personal identity 
and economy. We all need to have a certain online security policy regardless of OS used. 
Most of us I guess know about the five golden rules for online security:

* Have all the latest updates and patches
* Have a working software and/or hardware firewall
* Have an updated antivirus and/or know what's going on on the process list
* Be a little bit cautious and don't install _everything_
* Use a "guest" or restrictive user account for default use

This is my security policy for Windows. But how about Linux/Ubuntu?

The latest and greatest updates are not a problem as I can see 
What about a firewall solution? Does Jaunty have this bundled? I do have firewall in my DSL modem and router box
I haven't heard much about viruses on Linux, so what's your take in this issue?
Ubuntu supports a software catalogue -- are _all_ these software suits safe to install?
Do you recommend using a guest account with less access during default use?

Are there anything more I should be aware of or secure myself before converting 
and diving into this new OS? Or is it safe to use straight out of the box?

Thanks in advance!

---

### Post by bryncoles on 2009-05-06
these issues come up a lot for new people. let me direct you to some readings:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

that should see you in good stead!

*edit*

bonus reading!

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by mister_pink on 2009-05-06
I'll take these one at a time:

> **GL_NORWAY said:**
> 
* Have all the latest updates and patches

As you've noticed, updates come quickly to ubuntu, and are very easy to install. You can set it to automatically install security patches if you wish.
> 
* Have a working software and/or hardware firewall

There are many available for ubuntu, most of which are actually just tools to manage the inbuilt (but rather complicated) firewall called iptables. Try looking in add/remove programs for "gufw"
> 
* Have an updated antivirus and/or know what's going on on the process list

Most people don't bother with antivirus in linux. Its been debated many many times so have a google to find some discussion. If you decide you want one then try clamav
> 
* Be a little bit cautious and don't install _everything_

As you noted below, installing from the official repositories is almost risk free. As always, installing random things from the internet has some risk associated, but I've never seen anything cause problems.
> 
* Use a "guest" or restrictive user account for default use

You can do if you like, just set one up in System> Admin > Users and groups. However its not really necessary as by default you are not an admin, but can elevate yourself to admin (or "root") privileges with your password.

> 
Are there anything more I should be aware of or secure myself before converting 
and diving into this new OS? Or is it safe to use straight out of the box?

I think its pretty secure to begin with! The most vulnerable bit of the OS, as with any, is the browser, so if you're concerned with security try checking out the noscript extension.

---

### Post by GL_NORWAY on 2009-05-06
Thank you both for your information! -- especially those links that 
answered most of my questions and are nice to go back to.

As a new Linux user, this is really exciting! :)

> **mister_pink said:**
> There are many available for ubuntu, most of which are actually just tools to manage the inbuilt (but rather complicated) firewall called iptables. Try looking in add/remove programs for "gufw"


If I've understood things correctly, Ubuntu has no open ports by 
default after install? So there's no need to do anything unless 
you need to open any for special applications in the future?

---

### Post by stwschool on 2009-05-06
This is linux. The ideas behind Linux are very similar to those of Unix, and as such security is about as good as you could reasonably expect it to be. Viruses are basically non-existent, and the level of security is a LONG way ahead of any Windows version.

Regarding noscript, be aware that there are many innocent uses of javascript (it helps me make some wonderfully intuitive interfaces for starters), and use of noscript may render many pages unusable.

Usual rules apply, don't go downloading stuff willy-nilly. Check your sources. The repos are safe as houses, getdeb is kosher and launchpad should be ok (google it before you download so you know it's safe).

---

### Post by albinootje on 2009-05-06
> **GL_NORWAY said:**
> 
* Have all the latest updates and patches

Yes.
> 
* Have a working software and/or hardware firewall

Not needed, I'd say unless you're in an untrusted LAN, but I recommend gufw (GUI for Ubuntu's ufw) if you want a firewall.
> 
* Have an updated antivirus and/or know what's going on on the process list

I would like to have written evidence here about which anti-virus software actually support the list of known Linux viruses, like here :
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

It is my firm assumption that all of almost all anti-virus software are for MS-Windows viruses/trojans etc.
None of the anti-virus software has support for a list of known Linux viruses.
In other words, it is a waste of resources to run anti-virus software in Linux, unless you're worried that your MS-Windows friends or relatives are gonna accuse you of giving them MS-Windows viruses via others ;-)
See also : [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
> 
* Be a little bit cautious and don't install _everything_

With Ubuntu you can stick to the repositories to install software.
That should be pretty safe, as well for [http://getdeb.net/](http://getdeb.net/)
See also : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
> 
* Use a "guest" or restrictive user account for default use

You can do that for Internet usage.
But perhaps easier is to use Firefox add-ons NoScript and WOT, and study AppArmor if you like.

---

### Post by mister_pink on 2009-05-06
> **GL_NORWAY said:**
> If I've understood things correctly, Ubuntu has no open ports by default after install? So there's no need to do anything unless you need to open any for special applications in the future?
I think technically it actually has all its ports open, but whilst this sounds bad its not really. There's no programs listening to them, so anything sent to them is ignored anyway.

---

### Post by ice60 on 2009-05-06
i always make sure my browser is hardened, it's the program that's most likely to come across an exploit. i use an http proxy to filter all traffic and rewrite web pages, i use proxomitron with wine for that, but there's privoxy too.

then i make sure all my network facing apps are profiled with either apparmor or SELinux. and i harden the rest of the os doing things like disabling things that aren't used or needed much and hardening settings.

i used the first link from this post, below, for my browser, opera. there are lots of posts for hardening firefox around if you use that. -
[http://ubuntuforums.org/showpost.php?p=5459672&postcount=37](http://ubuntuforums.org/showpost.php?p=5459672&postcount=37)

here are some useful links for securing linux as a whole -
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)
[http://tuxtraining.com/2008/05/09/avoid-big-brother-and-hackers-on-a-linux-box/](http://tuxtraining.com/2008/05/09/avoid-big-brother-and-hackers-on-a-linux-box/)

if you are really in to securing your box there's loads of information about.

---

### Post by GL_NORWAY on 2009-05-07
> **albinootje said:**
> 
In other words, it is a waste of resources to run anti-virus software in Linux, unless you're worried that your MS-Windows friends or relatives are gonna accuse you of giving them MS-Windows viruses via others ;-)


This also applies to root-kits? Forgive my lacking knowledge, but root-kits and viruses are basically the same?

---

### Post by albinootje on 2009-05-07
> **GL_NORWAY said:**
> This also applies to root-kits? Forgive my lacking knowledge, but root-kits and viruses are basically the same?

Rootkits and viruses are not the same.
You should know that viruses are basically not a problem in a Linux desktop. 
But trojan horses and also rootkits are a risk.
Rootkits would be installed after the attacker gained root access, which is not so likely to happen if you keep up with security updates and don't compile software from possibly untrusted third parties.

See here for descriptions :
[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)
[http://en.wikipedia.org/wiki/Trojan_horse_(computing](http://en.wikipedia.org/wiki/Trojan_horse_(computing))
[http://en.wikipedia.org/wiki/Linux_Virus](http://en.wikipedia.org/wiki/Linux_Virus)
and read this too :
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Sealbhach on 2009-05-07
> **mister_pink said:**
> I think technically it actually has all its ports open, but whilst this sounds bad its not really. There's no programs listening to them, so anything sent to them is ignored anyway.
 
I thought the situation with default install of Ubuntu was:
 
1. all ports are closed.
 
2. Firewall is already enabled with iptables.
 
This piece from [Psychocats]("http://psychocats.net/ubuntu/security#firewallantivirus") seems to confirm that:
 
>  
By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited. 
 
A firewall, however, adds the benefit of peace-of-mind from accidentally installing a server program that opens up a port by default. Also, it satisfies curiousity by logging potential "hits." Linux comes with a very strong, secure, and powerful firewall called *iptables*, but it is relatively difficult to use from a new user's standpoint. As a result, there are many graphical tools that give you a simple user interface for configuring *iptables*, such as Firestarter for GNOME or Guarddog for KDE. By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited. 
 
A firewall, however, adds the benefit of peace-of-mind from accidentally installing a server program that opens up a port by default. Also, it satisfies curiousity by logging potential "hits." Linux comes with a very strong, secure, and powerful firewall called *iptables*, but it is relatively difficult to use from a new user's standpoint. As a result, there are many graphical tools that give you a simple user interface for configuring *iptables*, such as Firestarter for GNOME or Guarddog for KDE. 


---

### Post by albinootje on 2009-05-07
> **Sealbhach said:**
> 
1. all ports are closed.
2. Firewall is already enabled with iptables.


All ports are open by default. 

You can try this on a default Ubuntu installation : 
```

sudo iptables -L -n
sudo iptables -L -t nat

```
Ufw, the new easy firewall configuration software in the newer Ubuntu releases is also not enabled by default.

---

### Post by ice60 on 2009-05-07
> **albinootje said:**
> All ports are open by default..do you mean all ports aren't firewalled by default because there's nothing listening on a default install?

---

### Post by albinootje on 2009-05-07
> **ice60 said:**
> do you mean all ports aren't firewalled by default because there's nothing listening on a default install?

Right.
Try installing apache on your desktop machine, and test connecting to apache from another machine, you'll see that it works right away.

Then fire up gufw (GUI for ufw) and use "deny all incoming", try apache again, and see the difference.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gufw](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gufw)
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by GL_NORWAY on 2009-05-09
> **albinootje said:**
> Rootkits and viruses are not the same.
You should know that viruses are basically not a problem in a Linux desktop. 
But trojan horses and also rootkits are a risk.
Rootkits would be installed after the attacker gained root access, which is not so likely to happen if you keep up with security updates and don't compile software from possibly untrusted third parties.

See here for descriptions :
[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)
[http://en.wikipedia.org/wiki/Trojan_horse_(computing](http://en.wikipedia.org/wiki/Trojan_horse_(computing))
[http://en.wikipedia.org/wiki/Linux_Virus](http://en.wikipedia.org/wiki/Linux_Virus)
and read this too :
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Thanks for all this kind help! :)

One more question: If anyone should be able, hypothetically, to hack my Ubuntu and run things as root, should I be able to see that person logged on by [COLOR="Red"]$ who[/COLOR]?

---

### Post by albinootje on 2009-05-09
> **GL_NORWAY said:**
>  One more question: If anyone should be able, hypothetically, to hack my Ubuntu and run things as root, should I be able to see that person logged on by [COLOR="Red"]$ who[/COLOR]?

That depends, if you have for example set a weak password and you're using ssh server, and a brute force attack succeeds, then yes.
But if the attacker uses an exploit in your browser, and then uses a local root exploit, then I would think it will not be visible with "who" or "w" or "last".

---

