---
title: "Need Assistance Setting up Server"
date: 2009-01-28
forum: Server Platforms
---

### Post by audio_uphoria on 2009-01-28
Hello, I have a desktop that I'm trying to run as a dedicated server. I installed ubuntu 8.04 lts and I'm following this [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3") tutorial. I'm stuck on setting my ip to static. when I open vi /etc/network/interfaces it will show, 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0

but will not let me edit it and I already set it up so I have root priveledges. I'm not sure how my network is set up because I'm living in an apartment complex that just has an ethernet cord fed through the wall. I know everyone in the apartments is hooked up to this one network.... Also I cannot find the gateway, I type route and under default it says dsl-domain 0.0.0.0. What can I do to get around this and get this working? I'm guessing it has something to do with the network I'm on but I'm just learning all of this stuff as I go. Any help appreciated.

---

### Post by audio_uphoria on 2009-01-28
No one?

---

### Post by and12345 on 2009-01-28
you meant that you're running desktop edition right?

if that so.. why don't you just right click on networking icon right above your desktop rather than using command line:p
from there you can change your ip and so on easier;)

---

### Post by audio_uphoria on 2009-01-28
Thanks for the reply but like I stated in the first post I'm running 8.04 lts, which is a server edition, which is in command line only as far as I know...

---

### Post by lloyd_b on 2009-01-28
First, exactly how did you "set it up so I have root priveledges"?  On Ubuntu, you typically access root commands via a "sudo" command:
```
sudo vi /etc/network/interfaces
```

As for the gateway, run "route -n" (to get the ip address of "dsl-domain", instead of the name).

One question: Do you have access to the router?  If not, how are you going to choose an IP address that won't conflict with one assigned by the router to someone else?

---

### Post by ramsam on 2009-01-29
lloyd_b .... there is a way to just log in as root in the ubuntu system.
so you do not need the sudo thinge at all.
My friends done that on his system but i never go to it since I like the sudo thinge.

---

### Post by happycodemonkey on 2009-01-29
lloyd_b raises a good point, if you don't have control over the router, you probably cannot assign yourself a static IP.

In this case I would recommend [ddclient]("http://ddclient.wiki.sourceforge.net/") and [DynDNS]("http://www.dyndns.com/"), both of which I use on my own Ubuntu server, and which work out wonderfully for me. DynDNS allows you to pick a host name on their website, and ddclient is the daemon that updates your ipaddress if it's dynamic (which it likely is).

(Also, the regular Ubuntu desktop edition has an 8.04 lts version, but that's besides the point :P)

I hope this was helpful, good luck with your server!

---

### Post by gtdaqua on 2009-01-29
> **audio_uphoria said:**
> Hello, I have a desktop that I'm trying to run as a dedicated server. I installed ubuntu 8.04 lts and I'm following this [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3") tutorial. I'm stuck on setting my ip to static. when I open vi /etc/network/interfaces it will show, 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0

but will not let me edit it and I already set it up so I have root priveledges. I'm not sure how my network is set up because I'm living in an apartment complex that just has an ethernet cord fed through the wall. I know everyone in the apartments is hooked up to this one network.... Also I cannot find the gateway, I type route and under default it says dsl-domain 0.0.0.0. What can I do to get around this and get this working? I'm guessing it has something to do with the network I'm on but I'm just learning all of this stuff as I go. Any help appreciated.

First, you have to find the router's IP. Then find an IP that nobody in the apartment uses, so you can use it. 

Third, use nano - its easier than vi or vim. Edit the interfaces file in nano using sudo command:
```

sudo nano /etc/network/interfaces

```
Make the changes in the file and press Ctrl+O to save and Ctrl+X to exit nano.

Restart the network using:
```

sudo nano /etc/init.d/networking restart

```.

Remember, step 1 and 2 are important! If you can't get around these two steps, then you should simply use DHCP.

---

### Post by audio_uphoria on 2009-01-29
lloyd I followed the instructions in the tutorial to login as root, as far as choosing an ip that wont conflict I was going to call whoever is in charge of our network here at the apartments or I was going to find one that would work. Thanks code monkey, if all else fails I will go with what you recommended. GT after not being able to edit anything in vi I tried to run nano etc/network/interfaces and it came up blank.

---

### Post by lloyd_b on 2009-01-29
> **audio_uphoria said:**
> lloyd I followed the instructions in the tutorial to login as root, as far as choosing an ip that wont conflict I was going to call whoever is in charge of our network here at the apartments or I was going to find one that would work. Thanks code monkey, if all else fails I will go with what you recommended. GT after not being able to edit anything in vi I tried to run nano etc/network/interfaces and it came up blank.

A question: what exactly did you mean by "did not let me edit it"?  Was it giving you a read-only warning when you tried to save?  If you aren't familiar with "vi", it can be tricky to use, so it may be you just weren't giving it the command to allow you to insert text...

As for "nano etc/network/interfaces", please try again, with a "/" before the "etc" - "etc/network/interfaces" is relative to the *current* directory (i.e. if you're in /home/mydir, it'll try to edit "/home/mydir/etc/network/interfaces").  "/etc/network/interfaces" with the leading slash is relative to the root directory, and is the file you need to edit.  At any rate, I *would* suggest using "nano" rather than "vi" unless you're familiar with "vi" - "nano" is pretty user-friendly.

Finally, regarding just finding an IP that'll work, you may have problems in the future if that address happens to be picked up by another machine.  You really need to get into the router, and reserve an address.

---

### Post by bibleman on 2009-01-29
I just recently posted a how-to on my website. Just click the link below and you will find all the information you need to set up a static IP.

---

### Post by audio_uphoria on 2009-01-30
Thanks you everyone for your help. I decided to use dyndns.com because I have no control over the router that is used in the building. Regards.

---

