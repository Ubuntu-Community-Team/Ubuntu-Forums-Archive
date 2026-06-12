---
title: "Computer Hangs After 49.7 Days"
date: 2010-09-13
forum: The Cafe
---

### Post by sulekha on 2010-09-13
Hi all ,

      See this article :- [http://support.microsoft.com/kb/216641](http://support.microsoft.com/kb/216641)

     It says that win  95/98 machines wont work for more than 49.7 days continously. my question is , following the lines of above article , does linux distros (ubuntu in particular) have any such issues ?

---

### Post by endotherm on 2010-09-13
I certianly would hope not. many linux servers can run for months and years without reboot, if correctly administered.

---

### Post by CharlesA on 2010-09-13
> **endotherm said:**
> I certianly would hope not. many linux servers can run for months and years without reboot, if correctly administered.
This.

I am curious why you'd worry about something from an OS that is like 15+ years old and obviously obsolete.

---

### Post by endotherm on 2010-09-13
btw, thanks for the lolz. that support doc gave me the best laugh I'm gonna get today. makes me think of what happened to my 386 (WFW311) at midnight 1/1/2000. the date jumped back to 1986, and the keyboard got all wonky.

---

### Post by perspectoff on 2010-09-13
> **sulekha said:**
> Hi all ,

      See this article :- [http://support.microsoft.com/kb/216641](http://support.microsoft.com/kb/216641)

     It says that win  95/98 machines wont work for more than 49.7 days continously. my question is , following the lines of above article , does linux distros (ubuntu in particular) have any such issues ?

I have had a Linux DNS server (for our small hospital) running for 7 years without needing a reboot. It has rebooted automatically after power outages a few times, though, but without needing intervention.

After a Windows 2003 terminal server crashed after only 3 years, requiring an expensive replacement (Microsoft demanded an upgrade to Server 2008 minimum -- very expensive), we duplicated the DNS server, just in case some hardware would fail. 

(I'm actually impressed the DNS server hardware has never failed after 7 years 24/7.)

---

### Post by Elfy on 2010-09-13
moved to the cafe

---

### Post by samalex on 2010-09-13
Yeah, Linux definitely isn't plagued by this problem... At my former employer we had a DEC Alpha running Red Hat Linux 7.2 as our FTP and proxy server, and until we replaced the UPS and had to bring down all servers it had about 4 years of uptime.  And even after the scheduled reboot it ran for about another 2 years before it was replaced.

I've had impressive uptimes on my home systems as well, but generally due to power outages I'm good to get a few months if that between reboots.

Sam

---

### Post by Xianath on 2010-09-14
I've always found it ironic that it took them several years to find that particular bug :D

---

### Post by handy on 2010-09-14
Reboot on day 49!

---

### Post by scottuss on 2010-09-14
Even modern versions of Windows don't suffer from this (they just suffer from everything else!)

Don't worry about it, you'll have years of uptime with Linux

---

### Post by s0rc3r3r on 2010-09-14
> **scottuss said:**
> Even modern versions of Windows don't suffer from this (they just suffer from everything else!)

Don't worry about it, you'll have years of uptime with Linux

aye aye!!:popcorn:

---

### Post by kamaboko on 2010-09-14
Ridiculous.  I've had Win95 machines set up to deliver services that went for up to five years w/o a reboot.  They were setup, put in a server room closet and generally forgotten about.

---

### Post by V for Vincent on 2010-09-14
> **kamaboko said:**
> Ridiculous.  I've had Win95 machines set up to deliver services that went for up to five years w/o a reboot.  They were setup, put in a server room closet and generally forgotten about.

It's on microsoft.com and it's been confirmed, so it must affect some versions of windows. Not saying that's worth slagging MS, though. After all, 9x is ancient.

---

### Post by m4tic on 2010-09-14
I once went for 73 days on a OpenSuse desktop installation. I shut it down once i saw my electricity for the two months its been on.

---

### Post by Khakilang on 2010-09-14
I don't remember my computer hang at all using Window 95/98. Hardware failure yes but that does not involve Windows. At present my Linux didn't hang either. But I am curious to know whether it happen on the latest Window OS.

---

### Post by roddie on 2010-09-14
> **m4tic said:**
> I once went for 73 days on a OpenSuse desktop installation. I shut it down once i saw my electricity for the two months its been on.
:lolflag:

---

### Post by Grenage on 2010-09-14
> **Khakilang said:**
> I am curious to know whether it happen on the latest Window OS.

Certainly not. :)

---

### Post by julio_cortez on 2010-09-14
> **sulekha said:**
> It says that win  95/98 machines wont work for more than 49.7 days continously.Well, they still are rock solid compared to the one that came after: **ME barely worked for more than 49 MINUTES in a row!!**
*..sorry, couldn't resist..* :p :p :p

---

### Post by NMFTM on 2010-09-14
I'm going to be installing ME on my main computer later today. Because it seems like an easier solution than getting them to work on XP or 7.

---

### Post by julio_cortez on 2010-09-14
> **NMFTM said:**
> I'm going to be installing ME on my main computer later todayWell, I wish you good luck, brave fellow poster :D

---

### Post by grobar87 on 2010-09-14
> **julio_cortez said:**
> Well, they still are rock solid compared to the one that came after: **ME barely worked for more than 49 MINUTES in a row!!**
*..sorry, couldn't resist..* :p :p :p

hahahaha :p:p:p

---

### Post by Johnsie on 2010-09-14
Modern versions of Windows are on par with, if not better than Linux when it comes to uptime. Obviously it depends on your hardware compatibility/setup as well. If linux is running pretty hot on a machine (which it does quite often) then you might need it serviced earlier. Sometimes Linux locks up on some hardware combinations or freezes because a program is using too much ram. I ran a grep command on a server ther other day and it locked up. I've also seen the shoutcast server cause several ubuntu machines to crash. The same can happen with Windows.

---

### Post by blueturtl on 2010-09-14
Windows 95 also had a bug that caused it to BSOD pretty much immediately on boot if your CPU was faster than 350/400 MHz. The Microsoft patch page spesifically says there is no fault on part of the CPU, but that is a timing loop issue in Windows itself.

The uptime cap seems like another example of badly underengineered or just plain botched design and/or programming.

This level of reliability was a joke as much back in 1995 as it is today. 
Just something for you all to keep in mind when you say it's ok cause it was such a long time ago.

A certain nerd who started his own operating system and only targeted it for his own 386 initially had higher design standards than Microsoft had when they had already set to take over the world.

---

### Post by kelvin spratt on 2010-09-14
How can windows run for months years without a reboot seeing as it forces you to reboot monthly when it updates with security patches come on boys and girls all this trying to get one over the other. with Linux you  have to reboot for Kernel patches so what are you guys saying you never update, Well thats a bad practice. somebody ran a Elive Live cd for i think over a year maybe 2 continual and kept it updated was featured on the old site.

---

### Post by endotherm on 2010-09-14
> **kelvin spratt said:**
> How can windows run for months years without a reboot seeing as it forces you to reboot monthly when it updates with security patches come on boys and girls all this trying to get one over the other. with Linux you  have to reboot for Kernel patches so what are you guys saying you never update, Well thats a bad practice.
agreed, but at the same time it's not quite apples-to-apples either. kernel upgrades can be done without reboot via ksplice if you are running a high uptime server, and due to the lack of a central registry that is partially autogened at boot, most other updates can be done with no reboot (at most a service restart). 
additionally, kernel upgrades are often put off for planned downtime. kind of like installing a service pack. you don't just let windows update install it whenever it wants to.

---

### Post by scottuss on 2010-09-14
> **kelvin spratt said:**
> How can windows run for months years without a reboot seeing as it forces you to reboot monthly when it updates with security patches come on boys and girls all this trying to get one over the other. with Linux you  have to reboot for Kernel patches so what are you guys saying you never update, Well thats a bad practice. somebody ran a Elive Live cd for i think over a year maybe 2 continual and kept it updated was featured on the old site.

I would presume they don't include planned downtime, as any and all systems have this at some point.

---

### Post by Grenage on 2010-09-14
> **scottuss said:**
> I would presume they don't include planned downtime, as any and all systems have this at some point.

Bingo, planned downtime is not generally detracted from total uptime.

---

### Post by CharlesA on 2010-09-14
> **endotherm said:**
> agreed, but at the same time it's not quite apples-to-apples either. kernel upgrades can be done without reboot via ksplice if you are running a high uptime server, and due to the lack of a central registry that is partially autogened at boot, most other updates can be done with no reboot (at most a service restart). 
additionally, kernel upgrades are often put off for planned downtime. kind of like installing a service pack. you don't just let windows update install it whenever it wants to.

+1 to ksplice. I've done security updates and had to reboot after they were installed. If you are running a machine that requires a high amount of uptime, it would be worth it to look into ksplice.

But yah. Planned downtime is a fact of life when servers are concerned. Hardware needs maintenance even if the software doesn't need it all the time. All software needs maintenance as well, not just Windows.

---

### Post by NCLI on 2010-09-14
> **perspectoff said:**
> I have had a Linux DNS server (for our small hospital) running for 7 years without needing a reboot. It has rebooted automatically after power outages a few times, though, but without needing intervention.

After a Windows 2003 terminal server crashed after only 3 years, requiring an expensive replacement (Microsoft demanded an upgrade to Server 2008 minimum -- very expensive), we duplicated the DNS server, just in case some hardware would fail. 

(I'm actually impressed the DNS server hardware has never failed after 7 years 24/7.)

How did you make the server turn itself on after outages like that?

---

### Post by V for Vincent on 2010-09-14
> **blueturtl said:**
> This level of reliability was a joke as much back in 1995 as it is today.

Windows is stable nowadays. I don't think I've experienced any lockups so far and I've been using 7 (quite casually, I'll admit) for months.

Maybe you've had less luck on your hardware, but I can't help moralizing here: false claims about windows (or OSX for that matter) do the open source community more harm than good.

---

### Post by Rasa1111 on 2010-09-14
> false claims about windows (or OSX for that matter) do the open source community more harm than good.

but false claims about Linux by MS people are cool and do allot of good, right. There are MS ppl who talk a whole lot more crap about linux distros than any linux user does about windows. lol

 It's just karma man,
Universe gotta stay balanced somehow...

---

### Post by TiBaal89 on 2010-09-14
hmmm...

[IMG]http://i192.photobucket.com/albums/z121/tibaal89/Misc/top_uptime.png[/IMG]

---

### Post by blueturtl on 2010-09-14
> **V for Vincent said:**
> Windows is stable nowadays. I don't think I've experienced any lockups so far and I've been using 7 (quite casually, I'll admit) for months.

Maybe you've had less luck on your hardware, but I can't help moralizing here: false claims about windows (or OSX for that matter) do the open source community more harm than good.

Neither of the mentioned issues in my post are false claims.
[http://support.microsoft.com/kb/216641](http://support.microsoft.com/kb/216641)

[http://news.cnet.com/Windows-95-patch-for-K6-2-chips-now-free/2100-1001_3-218430.html](http://news.cnet.com/Windows-95-patch-for-K6-2-chips-now-free/2100-1001_3-218430.html)

I'm glad that you've found Windows 7 to be more reliable (it would be terrible if it wasn't!).

---

### Post by tatose on 2010-09-20
I had an eeebox connected to 2 usb JBODs and serving my lans. This machine keeps dying every few days and fails to reboot due to ACPI issues, probably a bug after I had installed win7 home.

Out of rage and frustration of getting ACPI to work correctly, I VMed the whole win7home under vbox (non-ose).

I thought the whole thing will die sooner or later... since the processor is atom and stuff and its not meant for virtualisation.

Never had I knew it went for 4mths of uptime at least, only manually rebooted twice last due 'critical security issues',

just because ubuntu is running on bare-metal instead of windows.

---

