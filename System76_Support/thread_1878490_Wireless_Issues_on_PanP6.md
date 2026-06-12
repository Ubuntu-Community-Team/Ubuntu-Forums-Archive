---
title: "Wireless Issues on PanP6"
date: 2011-11-09
forum: System76 Support
---

### Post by Noah0504 on 2011-11-09
I've had my PanP6 for almost two years now, and I've actually had this problem since shortly after I purchased it, it just hasn't really bothered me that much, but now I want to get down to the bottom of it!

I'm currently running Ubuntu 10.04 (I just can't force myself to use Unity yet!).  After a random amount of use, the wireless connection will usually drop and try to reconnect.  After trying to connect for 30-45 seconds, the network manager appears asking for the network key.  Even if I try to connect again, it will fail.  Usually, I am able to disable and then re-enable the wireless card.  After this is will work.  If that process fails, I just reboot the machine.

I used to use the computer on my desk most of the time and just use an Ethernet connection, but now I find myself using the wireless more and more.  It's only really annoying if I am downloading a large file, playing a game over the Internet or on Skype.

Anyone have any guesses as what could be wrong?  I know Debian Squeeze does the same thing, but I haven't used a newer version of Debian or Ubuntu, so I don't know if that solves the problem!

Thank you in advance.

---

### Post by isantop on 2011-11-10
How long does it usually take to drop the connection? My guess is that this is related to 10.04, and that running from a LiveCD of 11.10 would not show this issue.

---

### Post by Noah0504 on 2011-11-10
> **isantop said:**
> How long does it usually take to drop the connection? My guess is that this is related to 10.04, and that running from a LiveCD of 11.10 would not show this issue.

Well, it's really random.  Sometimes it could take 3, 4 or more hours, other times it may happen in 30 minutes from a reboot or from re-enabling the wireless card.

I've only ever run Ubuntu 9.10 and 10.04 on this laptop, so I guess there is a chance it is a kernel issue.  I just have never seen anyone else metion the problem in the couple of years I have had it.

---

### Post by duphenix on 2011-12-02
What router are you using? Also which wireless option do you have?  I have a buffalo router running dd-wrt.  Currently there is an incompatibility between the intel wireless driver and the most recent dd-wrt firmware.  

See [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2297](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2297) for details that are beyond my skill level.

If this is your issue they suggest two options. 1) use openwrt instead of dd-wrt (comment # on the linked page), or 2) they have instructions for recompiling with a line of code commented out, but I'm not sure if they mean the wifi card driver or the router firmware (comment #19 on the linked page). 

If anyone succeeds in recompiling I would be super grateful if you could post instructions.

---

### Post by Noah0504 on 2011-12-02
> **duphenix said:**
> What router are you using? Also which wireless option do you have?  I have a buffalo router running dd-wrt.  Currently there is an incompatibility between the intel wireless driver and the most recent dd-wrt firmware.  

See [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2297](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2297) for details that are beyond my skill level.

If this is your issue they suggest two options. 1) use openwrt instead of dd-wrt (comment # on the linked page), or 2) they have instructions for recompiling with a line of code commented out, but I'm not sure if they mean the wifi card driver or the router firmware (comment #19 on the linked page). 

If anyone succeeds in recompiling I would be super grateful if you could post instructions.
I'm running Tomato on a Linksys WRT54GL.  I'm pretty sure that Tomato is based on OpenWrt.  So, it shouldn't have this problem, right?

---

### Post by duphenix on 2011-12-03
I did some looking into this.  The last post on the intellinuxwireless link mentions that it might be dependent on the kernel version of the firmware of the router.  It looks like kernels before 2.6.38 (2.6.38 works as well) work, those after it don't.  I don't see where Tomato firmware mentions which kernel it is based on. It says that as long as the data transfer stays low the router doesn't lock up.  

The post also has several people that say the problem goes away if you set the router mode to G Only, (Not N or N/G Mixed), this solution worked for me though hopefully it is only temporary.

---

### Post by HotShotDJ on 2011-12-06
> **Noah0504 said:**
> I've only ever run Ubuntu 9.10 and 10.04 on this laptop, so I guess there is a chance it is a kernel issue.  I just have never seen anyone else metion the problem in the couple of years I have had it.On my PanP5, I ran into a very similar problem.  I believe the PanP6 has the same WiFi card so it very well might be the same problem that you are experiencing.

At some point, and update to the kernel broke Wifi.  Locking the router to "G" mode helped.  A kernel upgrade finally solved the problem.  This all happened using OpenSUSE 11.4.  The latest release (12.1) does not have this issue.  Since the issue with the Intel driver was an upstream bug, this very well might be the same problem with you even though your using Ubuntu.

To test this hypothesis, follow Isantop's advice and try to see if booting a newer LiveCD corrects the problem.

---

