---
title: "Apparmor vs SElinux"
date: 2019-08-23
forum: Security
---

### Post by soufianta on 2019-08-23
Hello,

I'm actually in front of a choice between fedora (RedHat) and Ubuntu (Canonical) for my desktop / server.
Honnestly, I prefer APT to DNF (pacman is very good too but I'm not a particular fan of rolling releases and certainly not on servers !). But fedora (Redhat) is using SElinux (by default) why other distributions are using Apparmor.

I've heard that SElinux is very difficult to configure/understand why apparmor is more user friendly but what about the security? Is one better than the other? Apparmor concern only application rights but does SElinux do more?

Thanks.

---

### Post by TheFu on 2019-08-23
Don't use Fedora on a freakin' server.  Would you run alpha software on a server?  Use CentOS or RHEL if that is the way you are headed.
Security isn't a checkbox (Y/N).  SELinux has industrial strength capabilities, but you have to know how to use them. Lots of SW installation guides for RPM-based distros begin by turning off SELinux.  That isn't much use, is it?
Apparmor has fewer capabilities, but is much more approachable so you might actually use it.

Unix security is made up from many layers, not 1 single tool.

---

### Post by soufianta on 2019-08-23
@TheFu: It's not a production server but only a simple server for test purposes so nothing "freaky". The fact that we have to turn off SElinux to have something working is non-sense for me but it solves problems. But we're on a ubuntu forum, so I think you will advise me to use Ubuntu (or debian)? Can you give me some practical advantages in comparaison to Fedora (except the packaging tool) ?

---

### Post by uRock on 2019-08-23
Here's a doc that compares the two. [https://elinux.org/images/3/39/SecureOS_nakamura.pdf](https://elinux.org/images/3/39/SecureOS_nakamura.pdf)

Personally, I've toyed with Fedora, but I too prefer using APT. I have also messed around with creating AppArmor profiles. I haven't touched SELinux, though I don't have any public facing servers. I do currently have two LAN facing servers and they're both running Debian. Debian was chosen because one of the servers is 32 bit and Ubuntu no longer supports 32 bit processors.

---

### Post by soufianta on 2019-08-23
So I'll go for ubuntu or debian (for 32bits version servers). I've a big problem with that huge choice of distro ! There are few differences but there are more distros than the differences themselves and that makes GNU/Linux from my point of view a little bit unserious !

And thanks for the comparaison doc :).

---

### Post by cruzer001 on 2019-08-23
32 bit support

[https://ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer](https://ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer)

---

### Post by uRock on 2019-08-23
> **soufianta said:**
> So I'll go for ubuntu or debian (for 32bits version servers). I've a big problem with that huge choice of distro ! There are few differences but there are more distros than the differences themselves and that makes GNU/Linux from my point of view a little bit unserious !

And thanks for the comparaison doc :).

Not sure how that makes Linux an unserious thing. Pick the distro of your liking, then build it to do what you need it to do. The different distros off different defaults, but they're just defaults.

---

### Post by uRock on 2019-08-23
> **cruzer001 said:**
> 32 bit support

[https://ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer](https://ubuntu.com/download/alternative-downloads#alternate-ubuntu-server-installer)

I require a GUI on that machine. Debian made it easier. I don't see a 32bit server image listed on the alternate installer list.

Edit: I also wanted LXDE on it. Canonical only offers 3 year LTS for Lubuntu. I preferred to put something on it that won't require a reinstall during the rest of its life. I don't expect the Netbook to last longer than five to six years.

---

### Post by cruzer001 on 2019-08-23
BitTorrent list, link drops to wrong screen.

---

### Post by soufianta on 2019-08-23
You can have different options/choices of products but not a HUGE choice of the same product (GNU/LINUX) but that's only my opinion... It's like in a restaurant, if the customer has a huge choice, he will most probably try/take something he don't want and will never come back :D...

---

### Post by cruzer001 on 2019-08-23
And cars all have 4 wheels, why do we need so many choices :D

---

### Post by QIII on 2019-08-23
The world of Linux (Don't get me started on "GNU/Linux" -- but note that neither Canonical nor Red Hat uses the term "GNU/Linux") is not a restaurant.  It is not a monolithic entity.  It's not Windows.

And it is exactly that which many find appealing.

---

### Post by soufianta on 2019-08-23
@cruzer001: I agree but it's not the ideal solution too !
@QIII: "many" is not "everybody". Everybody love choice but too many choice will kill the choice (french sentence). 

Peace...

---

### Post by uRock on 2019-08-23
> **cruzer001 said:**
> BitTorrent list, link drops to wrong screen. I only see 32 bit in 16.04, which has moved on to a kernel that borks the computer. Debian doesn't change unless there's a security update.

> **soufianta said:**
> You can have different options/choices of products but not a HUGE choice of the same product (GNU/LINUX) but that's only my opinion... It's like in a restaurant, if the customer has a huge choice, he will most probably try/take something he don't want and will never come back :D...

There's not really that many choices when you cross out all of the derivatives of derivatives. I'd much rather have a large selection, instead of a limited selection. It gives the power of selecting what you want. Like comparing In & Out vs McDonald's. One has just burgers and fries, while the other has a full selection.

---

### Post by cruzer001 on 2019-08-23
32 bit has been dropped.

And right Linux is not like a restaurant, but like cars the personalization is endless.  Its modular in build and sooo many ways to put it together.

---

### Post by QIII on 2019-08-23
> **soufianta said:**
> 
@QIII: "many" is not "everybody". Everybody love choice but too many choice will kill the choice (french sentence).

Again:  The world of Linux is not a monolithic entity.  The developers of each distribution are free to go their own route.   There is no governing body telling developers what they can and can not do with their distributions.  It's a city full of independent food carts.  If you don't like one, go to a different one.

---

### Post by cruzer001 on 2019-08-23
> **QIII said:**
> It's a city full of independent food carts.  If you don't like one, go to a different one.
I don't like anything :) so I build (roll) my own, thats how easy Linux makes it.

You must run 32 bit?  Choice may be made for you depending on Debian 32 bit support.

---

### Post by TheFu on 2019-08-23
[https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar) has some interesting ideas about centralized control and the bazaar model.

---

### Post by #&amp;thj^% on 2019-08-23
I'll quote a Dev i used to follow {rook} And I also subscribe to his input on the matter>
> 

These security systems provide tools to isolate applications from each other... and in turn isolate an attacker from the rest of the system when an application is compromised.

SELinux rule sets are incredibly complex but with this complexity you have more control over how processes are isolated. Generating these policies can be automated. A strike against this security system is that its very difficult to independently verify.

AppArmor is very straight forward. The profiles can be hand written by humans, or generated using aa-logprof. AppArmor uses path based control, making the system more transparent so it can be independently verified.

I've grown accustom to "AppArmor" myself. (Just my 2cents worth)
I would think though, both are not bullet proof these days. :)

---

### Post by kevdog on 2019-09-07
What do you want to do with your server?  If its simple, Ubuntu is good, however Debian usually is more stable.  I run a number of servers, some ubuntu, some not -- just depends what your looking to do with your server.

---

### Post by soufianta on 2019-09-17
SElinux is something hard but very secure (MAC) and you can even install SElinux on Ubuntu (apparmor by default). The main differences are the packet manager / repos / release cycle.
For the rest, linux stays linux...

---

