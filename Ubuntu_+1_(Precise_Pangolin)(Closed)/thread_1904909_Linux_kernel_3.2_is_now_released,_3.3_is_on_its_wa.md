---
title: "Linux kernel 3.2 is now released, 3.3 is on its way."
date: 2012-01-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-05
Here is the release announcement:

[https://lkml.org/lkml/2012/1/4/395](https://lkml.org/lkml/2012/1/4/395)

---

### Post by Harry33 on 2012-01-06
And in Launchpad, here:

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-8.14](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-8.14)

---

### Post by VinDSL on 2012-01-07
Working fine!

Thanks, Harry!

---

### Post by xyzzyman on 2012-01-07
Usually the .tar file on launchpad already has the patches applied. Anyone have an idea why the difference this time?

Or has it been backwards during the RC's? Not that big of a deal. Now that it's out of RC just means that I won't be re-compiling as often. :)

---

### Post by VinDSL on 2012-01-07
> **xyzzyman said:**
> Usually the .tar file on launchpad already has the patches applied. Anyone have an idea why the difference this time?
I don't know exactly "why the difference", but...

Linux 3.2 has been rather problematic on my ancient iron.

I have a *hunch* that "they" got their hands full with 3.2

My biggest issue with Linux 3.2 is not being able to use network-manager et al. (the default Ubu network manager).  

Example: I've been using Wicd for my network manager, since switching to 3.2.  And, while Wicd works okay, it doesn't support specifying the MTU.

The MTU needs to be set to 1492 on my 7GB DSL connection, for it to work properly.  Since I cannot specify the MTU in Wicd, I end up having to do a LOT of extra clicking (re-clicking hyperlinks), when I'm surfing the web.

Anyway, I'll be happy when they get the Linux 3.2 patches finalized!

Hopefully, I'll be able switch back to network-manager.  Otherwise, I'll be forced to run Linux 3.1 on this machine. :(

---

### Post by xyzzyman on 2012-01-07
> **VinDSL said:**
> I don't know exactly "why the difference", but...

Linux 3.2 has been rather problematic on my ancient iron.

I have a *hunch* that "they" got their hands full with 3.2

My biggest issue with Linux 3.2 is not being able to use network-manager et al. (the default Ubu network manager).  

Example: I've been using Wicd for my network manager, since switching to 3.2.  And, while Wicd works okay, it doesn't support specifying the MTU.

The MTU needs to be set to 1492 on my 7GB DSL connection, for it to work properly.  Since I cannot specify the MTU in Wicd, I end up having to do a LOT of extra clicking (re-clicking hyperlinks), when I'm surfing the web.

Anyway, I'll be happy when they get the Linux 3.2 patches finalized!

Hopefully, I'll be able switch back to network-manager.  Otherwise, I'll be forced to run Linux 3.1 on this machine. :(

So a 3.1 kernel on precise allows network manager to work for you, but a 3.2 kernel breaks it? And it still does when installed from a daily? I'm actually using 3.2 on oneiric (Just compiling precise's 3.2 sources even though the provided DEB's work) as I've had too much IRL to get into alpha testing ATM.

---

### Post by VinDSL on 2012-01-07
> **xyzzyman said:**
> So a 3.1 kernel on precise allows network manager to work for you, but a 3.2 kernel breaks it?
Yeppers!  That's what I'm saying...

I haven't tried network-manager in the last couple of RCs.  It's a PITA to switch network managers, but...

Yes, Linux 3.2 breaks network-manager on this machine.

Never had a kernel do that before.  I have a kernel fetish, and install new ones at the drop of a hat.  It's usually as exciting as bushing my teeth or shaving. But, Linux 3.2 has been a challenge.

I dunno.  Maybe it's because this machine is old as Moses (in computer years).

I digress:  I drive a shaved n' slammed '98 Honda CiViC with a '99 Si motor swap.  Nobody can beat me, coming off a light -- and it looks/works great.  It rips "modern cars" a new one...

However, my top-of-the-line 2005 gaming machine is starting to look n' feel like a Model-T Ford.  LoL!  :D

Maybe it's time to put a modern mobo in this thing -- the functional equivalent of a motor swap, yes?!?!?

---

### Post by MoreOrLess on 2012-01-07
3.3 may be on the way, but IIRC, Precise will use the 3.2 series (seems like a good idea for an LTS release). Of course, important fixes/features from a newer kernel can be backported if the devs want.

---

### Post by Harry33 on 2012-01-08
> **MoreOrLess said:**
> 3.3 may be on the way, but IIRC, Precise will use the 3.2 series (seems like a good idea for an LTS release). Of course, important fixes/features from a newer kernel can be backported if the devs want.

In fact, newer kernel is always a better idea.
Precise should have kernel 3.3. It will mature in good time.

---

### Post by xyzzyman on 2012-01-08
> **MoreOrLess said:**
> 3.3 may be on the way, but IIRC, Precise will use the 3.2 series (seems like a good idea for an LTS release). Of course, important fixes/features from a newer kernel can be backported if the devs want.

QFT. 3.3 is a development release and 3.2 is what has been announced for precise. Esp w/LTS newer isn't always better for stability & maturation.

---

### Post by ethan1701 on 2012-01-08
Any information regarding an expected kernel upgrade in Oneiric?

---

### Post by JMB74 on 2012-01-08
The precise 3.2 build has already been backported/rebuilt for Oneiric in several PPAs. 
[URL="https://launchpad.net/%7Exorg-edgers/+archive/ppa/+packages?field.name_filter=linux&field.status_filter=published&field.series_filter="]
xorg-edgers[/URL] for one

and it works very nicely on my Oneiric install.

As for any (semi) official backport? Not sure.

---

### Post by Buntumatic on 2012-01-08
> **VinDSL said:**
> I don't know exactly "why the difference", but...

Linux 3.2 has been rather problematic on my ancient iron.

I have a *hunch* that "they" got their hands full with 3.2

My biggest issue with Linux 3.2 is not being able to use network-manager et al. (the default Ubu network manager).  

Example: I've been using Wicd for my network manager, since switching to 3.2.  And, while Wicd works okay, it doesn't support specifying the MTU.

The MTU needs to be set to 1492 on my 7GB DSL connection, for it to work properly.  Since I cannot specify the MTU in Wicd, I end up having to do a LOT of extra clicking (re-clicking hyperlinks), when I'm surfing the web.

Anyway, I'll be happy when they get the Linux 3.2 patches finalized!

Hopefully, I'll be able switch back to network-manager.  Otherwise, I'll be forced to run Linux 3.1 on this machine. :(
Use post-connection script to set it without user interaction.
[http://wicd.sourceforge.net/moinmoin/Adding%20pre%20and%20post%20(dis)connection%20scripts](http://wicd.sourceforge.net/moinmoin/Adding%20pre%20and%20post%20(dis)connection%20scripts)

The command is simple ```
ifconfig <iface> mtu <number>
```

---

### Post by VinDSL on 2012-01-09
> **Buntumatic said:**
> Use post-connection script to set it without user interaction.
[http://wicd.sourceforge.net/moinmoin/Adding%20pre%20and%20post%20(dis)connection%20scripts](http://wicd.sourceforge.net/moinmoin/Adding%20pre%20and%20post%20(dis)connection%20scripts)

The command is simple ```
ifconfig <iface> mtu <number>
```
Whoa!  How did I miss that?!?!?


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/mtu-9-jan-2012(650x520).png[/img]]("http://vindsl.com/images/mtu-9-jan-2012.png")[/INDENT]


Thanks!  That worked a treat!

I'm going surfing...  :D

---

### Post by Buntumatic on 2012-01-09
You are welcome! :)

For those who have a single connection (desktop) and really do not need any on-fly connection management, all connection parameters can still be written into interfaces file in good old Debian way.

---

### Post by VinDSL on 2012-01-09
Heh!  I hate to tell you this, but...

This machine is running better under Liquorix 3.1 than the patched Linux 3.2 kernel.


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/liquorix-9-jan-2012(650x520).png[/IMG]]("http://vindsl.com/images/liquorix-9-jan-2012.png")[/INDENT]


Oh, well.  Maybe Linux 3.3 will be better.

---

### Post by zika on 2012-01-09
> **VinDSL said:**
> Heh!  I hate to tell you this, but...

This machine is running better under Liquorix 3.1 than the patched Linux 3.2 kernel.


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/liquorix-9-jan-2012(650x520).png[/IMG]]("http://vindsl.com/images/liquorix-9-jan-2012.png")[/INDENT]


Oh, well.  Maybe Linux 3.3 will be better.Hm, I thought I was being delusional... Great that I'm not the only one... ;)
I was stubborn in testing myself...

---

### Post by xyzzyman on 2012-01-09
Outside of ureadahead, ubuntu's patches and configs aren't as much about performance as stability and compatability (Except in your circumstance). That's why I use ubuntu's source instead of mainline, and compile my own. There's alot of debugging stuff left on that I'll never need. I'll have to take a look at liquorix and see what he's enabling/disabling to incorporate into my build. Thanks for giving me a new project. :)

I would try the mainline 3.2 PPA kernel now that it's final. If you're still having problems then it's a change upstream from Ubuntu that broke things. 3.2 did have alot of driver changes (My intel 5150 was merged into another driver.)

EDIT: Took a look at liquorix. It will be snappier as it seems to disable apparmor security and cpufrequency so it's always running at the max (Which for more desktop users is fine, but not for notebook or people anal about their power bill. He also switches to 1000hz instead of 250hz.). Esp on your system the BFS scheduler will see an improvement on normal day-to-day usage. I'm just on a core2 duo myself so I threw the 3.2 BFS patch into the source tree and I'm compiling right now so we'll see.

---

### Post by xyzzyman on 2012-01-11
Left dynamic ticks on, and kernel set at 300hz, but applied the BFS patch that Liquorix uses... Not noticeable normally, until I started another instance of Win7 in a VirtualBox and no stutter from NetFlix in another VirtualBox.

---

