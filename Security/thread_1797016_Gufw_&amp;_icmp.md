---
title: "Gufw &amp; icmp"
date: 2011-07-04
forum: Security
---

### Post by CVGH on 2011-07-04
I can't seem to find a way to set a rule to deny ICMP.
Is that not a feature of the GUI?
 All I can find is references to directly editing the ufw rules....

I'd like to set it for a few hrs after shutting down transmission and re-enable it later.

---

### Post by e79 on 2011-07-04
I don't think there is a way via the Gufw. Howerver, if you fire up a Terminal and follow Ubuntu's documentation :

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
> 
**Enable PING **Note: Security by obscurity may be of very little actual benefit with modern cracker scripts. **By default, UFW allows ping requests**. You may find you wish to leave (icmp) ping requests enabled to diagnose networking problems. 
You need to edit **/etc/ufw/before.rules** and remove edit the following lines: 

# ok icmp codes
```

-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT 
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```
Change the "ACCEPT" to "DROP" or 
# ok icmp codes 
```

-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

```
Hope this helps

---

### Post by haqking on 2011-07-04
If you want to do it via GUI then i suggest Firestarter, it is in the repos/software centre and provided more options that Ufw/Gufw.

it allows ICMP filering from preferences.

Firestarter,UFW/GUFW etc are really only interfaces to allow you to manage netfilter/iptables which is the firewall hardcoded into the kernel. And some have more features than other available.

hope this helps

---

### Post by CVGH on 2011-07-04
Thanks for the help folks.
Tried Firestarter a while ago, but hasn't been updated since 2005....

---

### Post by iavor on 2011-07-04
another way to block icmp is to add a line in /etc/sysctl.conf

net.ipv4.icmp_echo_ignore_all = 1

then simply sysctl -p

---

### Post by haqking on 2011-07-04
> **CVGH said:**
> Thanks for the help folks.
Tried Firestarter a while ago, but hasn't been updated since 2005....

Well its curenlty in version 1.0.3....why does it need to be updated ? it is only a GUI to netfilter.

It does the same job it has always done.

And it offers you ICMP filtering in a GUI which is what you want ;-)

The firewall itself remember is in the kernel itself, Firestarter is just a GUI to allow you to access it, so in that sense the firewall is upto date as your kernel ;-) it is not like it needs a definition update like AV.

---

### Post by wildmanne39 on 2011-07-04
Hi, I was actually told by an ubuntu staff member that firestarter is out dated and to use gufw

---

### Post by Dangertux on 2011-07-04
Hmm...

I'm with Haqking on this one. It's iptables, it does pretty much the same thing it's done for a very long time now. A front end for managing it from 3 years ago or 5 years ago wouldn't be too much different from a front end managing it today. Just my thoughts.

---

### Post by haqking on 2011-07-04
> **wildmanne39 said:**
> Hi, I was actually told by an ubuntu staff member that firestarter is out dated and to use gufw

Well all respect meant for the staff member.

GUFW is not doing what he wants it to, firestarter will. so ?

As already stated, there is not much to update which is probably why it is out of date, it is purely a GUI to manage iptables/netfilter which is in the kernel.

but it is personal preference, there are other ways to achieve the results. he asked for GUI ICMP filtering and Firetarter will do that ;-)

who cares if its 10 years old or 1 month old, it still is has more options and more configurable that GUFW...and they are both just a GUI for the firewall itself which is independant of both of them.

it is one of those "if it aint broke dont fix it" things.

remember ufw means uncomplicated firewall which exaclty it is and works fine as it is purely an interface for the built in firewall, Gufw is just the GUI for and uncomplicated firewall, the request is for a little more GUI manipulation which is not provided in the uncomplicated interfaces.

if its for a home system the chances are its not needed anyways, as unless you are internet facing then out of the box all ports are closed.  And your internet router can provide the firewall service including ICMP blocking, which by the way is likely also to be iptables as most home routers run Linux, and so yet again, same firewall, different interface

peace

---

### Post by cariboo on 2011-07-05
The problem with Firestarter is that most users use it to monitor the firewall, which needs to be run as root, which could be a security problem. If users just used the gui to set firewall rules, then shut it down, there wouldn't be a problem.

---

### Post by haqking on 2011-07-05
> **cariboo907 said:**
> The problem with Firestarter is that most users use it to monitor the firewall, which needs to be run as root, which could be a security problem. If users just used the gui to set firewall rules, then shut it down, there wouldn't be a problem.


yeah i understand that, i am purely providing a direct answert to his question which is a GUI for ICMP filtering.

LIke i said there are other ways to achive his goals i just think Firestarter provides his need very easily.

I personally dont use it, (have done historically)...as for running as root, i am an elitist i am afraid and think along the lines of, if you dont know why or what or how then dont ;-)

---

### Post by Soul-Sing on 2011-07-05
firestarter bugs will not be fixed===> launchpad
: [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759)
etc/etc

---

### Post by bodhi.zazen on 2011-07-08
> **haqking said:**
> Well all respect meant for the staff member.

GUFW is not doing what he wants it to, firestarter will. so ?

With all due respect, please do not advise software that is no longer maintained.

gufw / ufw are the defaults, and the fix is a "simple" edit to a configuration file, not much more difficult then copy / paste.

If you want to advise a graphical interface , use one that is at least maintained, and be prepared to debug conflicts you create with ufw / gufw.

Honestly, IMO, firestarter should be removed from the repos. It is no longer maintained and it conflicts with ufw / gufw, so it is not as straght forward as "install firestarter".

---

