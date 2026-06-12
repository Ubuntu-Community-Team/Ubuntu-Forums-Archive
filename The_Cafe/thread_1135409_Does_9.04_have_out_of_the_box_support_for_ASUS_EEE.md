---
title: "Does 9.04 have out of the box support for ASUS EEE netbooks?"
date: 2009-04-24
forum: The Cafe
---

### Post by NintendoTogepi on 2009-04-24
I'm currently running Eeebuntu 8.10...I'd consider swapping to regular Ubuntu 9.04, if it works. Does it?

---

### Post by JohnFH on 2009-04-24
I also have an eeepc and am running eeebuntu for 8.10.  The eeepc works much better with the Array kernel (non-standard kernel shipped with eeebuntu but not standard Ubuntu), so your options are:

1) Keep using eeebuntu for 8.10 until eeebuntu for 9.04 is released.  This might not happen for a few weeks yet.
2) Switch to using Ubuntu Netbook Remix (UNR) for Jaunty (endorsed by Canonical unlike eeebuntu).  See here:  [https://wiki.ubuntu.com/UNR]("https://wiki.ubuntu.com/UNR").

I tried earlier versions of UNR and I like eeebuntu better, so I'm waiting for the next eeebuntu release.

---

### Post by billgoldberg on 2009-04-24
Everything seems to work using Ubuntu 9.04 except the camera and multitouch on the touchpad.

---

### Post by GeorgeVita on 2009-04-24
> **billgoldberg said:**
> Everything seems to work using Ubuntu 9.04 **except the camera** and multitouch on the touchpad.

Go to BIOS SETUP: keep pressing **F2** while booting
Enable camera from bios.
Save & exit

Retry it.

EVERYTHING is working to me EeePC 1000H (except 'standard desktop')

Regards,
George

---

### Post by NintendoTogepi on 2009-04-24
> **billgoldberg said:**
> Everything seems to work using Ubuntu 9.04 except the camera and multitouch on the touchpad.

Well, no multitouch is a dealbreaker. I'll stick with Eeebuntu 8.10.

---

### Post by billgoldberg on 2009-04-25
> **NintendoTogepi said:**
> Well, no multitouch is a dealbreaker. I'll stick with Eeebuntu 8.10.

I'm sure support can be hacked in, but haven't bothered yet as I use a mouse with it most of the time.

---

### Post by lefen on 2009-04-25
In addition to the other issues people have mentioned, 9.04 **RC1** didn't have support for most of the Fn keys on my EEE 901, (including the numpad, which I missed more than I thought I would). So I went back to EEEbuntu 2.0 for now and will probably investigate the 3.0 release rather than Jaunty NBR.

---

### Post by bobbocanfly on 2009-04-25
Jaunty UNR (netbook remix) works fine out of the box for me on my Eee 701. There are some issues (outlined in the UNR release notes) of screen size where a lot of applications just don't fit on the tiny screen, but it's not much of a problem really.

---

### Post by zekopeko on 2009-04-25
i have an asus 1000hg and it works perfectly.
take into account that a model like 1000h uses 3 different camera or wireless chipsets so some might not be supported depending which one you have.

btw what's this about multitouch? i know that 2 finger scroll works but i don't know if there is any other.

---

### Post by billgoldberg on 2009-04-25
> **zekopeko said:**
> i have an asus 1000hg and it works perfectly.
take into account that a model like 1000h uses 3 different camera or wireless chipsets so some might not be supported depending which one you have.

btw what's this about multitouch? i know that 2 finger scroll works but i don't know if there is any other.

Well I can't drag windows or highlight text, which both need both fingers to do.

---

### Post by RandomJoe on 2009-04-25
I bought a 1000HE a few weeks ago, and all it's ever run is straight 9.04.  Everything worked just fine straight up, that I tried.  I've never even needed to plug in an Ethernet cable, which is quite impressive to me - all my previous laptops took "setting up" to get the wireless going.  Can't say if the camera works as I didn't want it anyway and disabled it.  This is the first time I've had a "multitouch" pad so don't know all the possible things it should do, but the ones I know about work just fine.

The only annoyance so far:  When I first installed, suspend and hibernate worked perfectly.  Somewhere along the way - I assume an update changed something - they broke.  It still suspends/hibernates fine, but when I turn it back on the backlight won't come on.  Most annoyingly, if I fumble around to find "shutdown" or "restart", the instant it starts shutting down the backlight comes on!

I ran 'powertop' on it recently, and found the Intel graphics driver was generating a slew of interrupts.  As mentioned on the lesswatts.org site, disabling DRI (Option "NoDRI" in xorg.conf) let the processor sleep a lot more and improved run time some.  Not like I need 3D on that little screen! :)

---

### Post by lefen on 2009-04-25
> **zekopeko said:**
> 
btw what's this about multitouch? i know that 2 finger scroll works but i don't know if there is any other.


Also, a 3 finger tap on the touchpad brings up the right-click context menu; so useful when you know it, but I had my EEE for about 2 months without realising :P

---

### Post by mister_pink on 2009-04-25
901 here, tried the NBR live only, but everything seemed to work. Need to find an app to let me switch things off and scale the CPU for battery purposes. Will probably stick with 8.10 and openbox for the time being. Very happy with my almost 6 hrs battery life for light usage :)

---

### Post by aysiu on 2009-04-25
I'm using vanilla Jaunty on my Eee PC 701, and *almost* everything works out of the box, except the mic with Skype (which you can fix by removing Pulse Audio and making a few setting changes).

701s don't support multi-touch.

---

### Post by GeorgeVita on 2009-04-25
> **lefen said:**
> Also, a 3 finger tap on the touchpad brings up the right-click context menu; so useful when you know it, but I had my EEE for about 2 months without realising
[B]
OK, above works[/B]!

Three fingers = right click
Two fingers = scroll up or down

EDIT: deleted info regarding solved problems after reinstallation.

---

### Post by enchantedsky on 2009-04-26
> **NintendoTogepi said:**
> Well, no multitouch is a dealbreaker. I'll stick with Eeebuntu 8.10.

This is not true. Multi-touch works on my 1000HE:

Press 2 fingers together to scroll
Press 2 fingers on a link in Firefox to create a new tab
Press 3 fingers to right-click
etc

The only thing which does not work with multi-touch (and I actually miss) is pressing 3 fingers down, and drawing a line to the left is supposed to hit the back button in Firefox. It works with the pre-installed Win XP on 1000HE, but not Ubuntu 9.04 (as yet).

Anyway, overall the 1000HE works perfectly. The only minor bugs I've seen is that sometimes when you mute the volume, it makes a buzzing sound through the speakers (however, I haven't experienced it lately, so perhaps the bug was corrected).

---

### Post by dmorris68 on 2009-04-26
Just finished installing final UNR 9.04 on my 1000HE.  Multi-touch and camera both work fine.  What seems to be problematic is my wifi connection.  I had tried a couple of Live versions of beta 9.04 UNR and had the same issue.  I just kept trying and re-entering my PSK over and over and it eventually worked.  

But so far this full install is being stubborn.  I've re-entered the key several times, and even tried my fallback 802.11b AP with WEP security -- that failed too.  The netbook can see the available networks, and the AP can see the client attempting to connect, but then the netbook disconnects itself complaining that it timed out waiting for a DHCP response.  I even tried with a neighbor's unsecured router, and it failed at that too.  So it doesn't appear to be security related.

---

### Post by zemz0r on 2009-04-27
eee-control know supports 1000he FN keys and more...

[http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/)

I don't know if "apt-get install eee-controll" is the newest version, however this app might sort out some problems for people.

---

### Post by Helmi on 2009-04-27
@zemzor - that's cool, does it also make multitouch working with 9.04? I'm planning to get a 1000HE and it will be worth nothing without ubuntu :)

---

### Post by JohnFH on 2009-04-27
> **zemz0r said:**
> eee-control know supports 1000he FN keys and more...

[http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/)

I don't know if "apt-get install eee-controll" is the newest version, however this app might sort out some problems for people.

That link answers my biggest question.  From the link:

> 
For Ubuntu (8.04/8.10), the array.org customized kernel is recommended, which includes the module and hardware drivers.
Ubuntu 9.04 does not need a customized kernel anymore. 


Thanks!

---

### Post by days_of_ruin on 2009-04-27
> **enchantedsky said:**
> This is not true. Multi-touch works on my 1000HE:

Press 2 fingers together to scroll
Press 2 fingers on a link in Firefox to create a new tab
Press 3 fingers to right-click
etc

The only thing which does not work with multi-touch (and I actually miss) is pressing 3 fingers down, and drawing a line to the left is supposed to hit the back button in Firefox. It works with the pre-installed Win XP on 1000HE, but not Ubuntu 9.04 (as yet).

Anyway, overall the 1000HE works perfectly. The only minor bugs I've seen is that sometimes when you mute the volume, it makes a buzzing sound through the speakers (however, I haven't experienced it lately, so perhaps the bug was corrected).

Sounds like the fire gestures plugin. Did you try installing that?
Because right click drag left in firefox with plugin installed does just 
what you are talking about.:)

---

### Post by Tha-Fox on 2009-04-29
Has anyone tried 901? I have fully working (except multitouch) netbook right now but I'd like to return to "normal" Ubuntu and kernel.

---

### Post by Orlsend on 2009-04-29
I am on 8.10 eeebuntu (on a 900HA), the guys over at the eeebuntu forums are waiting on that patch for the Intel graphics.... So far jaunty has done a bad job regarding that Issue.

Lol I cant believe I just learned about the Mulitouch in this thread, It work like a charm on my Install.

---

### Post by Deamos on 2009-04-29
Running on a 1000HA and it runs perfectly out of the box.  Haven't had an issue yet.

---

### Post by JohnFH on 2009-04-29
> **Tha-Fox said:**
> Has anyone tried 901? I have fully working (except multitouch) netbook right now but I'd like to return to "normal" Ubuntu and kernel.

I have a 901 and am running Jaunty and standard kernel.  Everything seems fine and very fast, although I haven't tested everything.  I was running eeebuntu for 8.10 and then upgraded to Jaunty and installed the generic kernel (eeebuntu for Jaunty doesn't exist yet).  Couldn't have been easier.  Jaunty on eeepc boots extremely quickly - makes using the eeepc a lot more convenient.

---

### Post by Tha-Fox on 2009-04-29
> **JohnFH said:**
> I have a 901 and am running Jaunty and standard kernel.  Everything seems fine and very fast, although I haven't tested everything.  I was running eeebuntu for 8.10 and then upgraded to Jaunty and installed the generic kernel (eeebuntu for Jaunty doesn't exist yet).  Couldn't have been easier.  Jaunty on eeepc boots extremely quickly - makes using the eeepc a lot more convenient.

Thanks for the response! Now I have enough courage to update :)

---

### Post by JC Cheloven on 2009-04-30
Hi, I wrote recently a brief review about jaunty on three popular netbooks, including asus eee. I'd say the result is outstanding.

[http://ubuntuforums.org/showthread.php?t=1123926](http://ubuntuforums.org/showthread.php?t=1123926)

As an update: things are equally well after jaunty release.

---

### Post by NintendoTogepi on 2009-05-12
So what is the conclusion here? Switch or not? :confused:

(I have a 900a)

Also how big is Jaunty? I have only a 4GB hard drive on my 900a.

---

### Post by drawkcab on 2009-05-13
I have a 900a coming and I am going to replace the 4gb with a faster 16gb ssd.

One thing you might want to do is wait and install eeebuntu 3.0 which is based on jaunty features the array kernel and comes in 1) full 2) NBR an 3) base.  Rumor has it that it will be available this weekend, possibly Friday.

---

### Post by Orlsend on 2009-05-13
I tried Jaunty the other day and most of the features worked,except the the mouse the sensitive was way to high. The regular mouse settings would not help at all. Anyway the Guys over at eeebuntu will release **Jaunteee** this weekend! with all the fixes and the tweaks you need for a perfect desktop in EeePc.

---

### Post by drawkcab on 2009-05-13
> **Orlsend said:**
> I tried Jaunty the other day and most of the features worked,except the the mouse the sensitive was way to high. The regular mouse settings would not help at all. Anyway the Guys over at eeebuntu will release **Jaunteee** this weekend! with all the fixes and the tweaks you need for a perfect desktop in EeePc.

And hopefully the intel video issue will be largely resolved!  ;)

---

