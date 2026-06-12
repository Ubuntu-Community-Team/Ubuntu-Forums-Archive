---
title: "Ubuntu 12.10 vs Windows 8 benchmark."
date: 2012-11-03
forum: The Cafe
---

### Post by agy2154 on 2012-11-03
<snip>
Ubuntu's drive accesss speeds are faster but Windows 8 boot time is. Is this because of Ubuntu EXT drive format?

---

### Post by Eggnog on 2012-11-03
Not a bad article.  Unfortunately, the average user probably won't be very inclined to worry about benchmarks too much, and especially with installing an OS on their own, or in dual booting.  

I imagine Win 7/8 will win with the average user because, as we all know, it comes pre-installed on most desktops and laptops.  They log in, clear out the pre-installed spam, fire up IE and go.  Joe Six Pack will get used to Win 8 because it's "Windows" and it's what he knows.

When Ubuntu/Linux starts to hit shelves pre-installed, and people can try it out in-store, with knowledgeable sales people, then it will become interesting, especially if strides are made in gaming, like with Steam, etc.  Believe it or not, gaming is a huge factor for many people, because they use their PCs to surf the web, write a few docs and emails, and play games.  Not everyone is a serious Access or Excel user.

---

### Post by zombifier25 on 2012-11-04
> **agy2154 said:**
> <snip>
Ubuntu's drive accesss speeds are faster but Windows 8 boot time is. Is this because of Ubuntu EXT drive format?

Windows 8 boots faster because Windows 8 doesn't shutdown, it **hibernates**. I have a machine that supports hibernating on Ubuntu, and waking up from hibernating is indeed faster than booting from a shutdown.

---

### Post by Jakin on 2012-11-04
> **zombifier25 said:**
> Windows 8 boots faster because Windows 8 doesn't shutdown, it **hibernates**. I have a machine that supports hibernating on Ubuntu, and waking up from hibernating is indeed faster than booting from a shutdown.

Yep, had a user totally shut win8 down, it is probably no faster than windows 7 boot.

> Plus, it now comes with your next favorite web browser, Internet Explorer 10.

What? :lolflag:

---

### Post by Linuxisfast on 2012-11-04
Security
Ubuntu is more secure than Windows. It has less flaws and fewer people use it. Because fewer people use it, there are fewer people targeting it. Windows 8 does come built with &#8220;Windows Defender&#8221; which is supposed to help out a bit.

Quite an amateurish and flawed statement in every sense, this is what MS sales pitchers use and use it regularly to gullible buyers.

---

### Post by mastablasta on 2012-11-05
> **Eggnog said:**
> When Ubuntu/Linux starts to hit shelves pre-installed, and people can try it out in-store, with knowledgeable sales people, then it will become interesting, especially if strides are made in gaming, like with Steam, etc. Believe it or not, gaming is a huge factor for many people, because they use their PCs to surf the web, write a few docs and emails, and play games. Not everyone is a serious Access or Excel user.
 
they have it here in major electronics retailer. Ubuntu was the system of choice....
had a chance to try it out though i don't know knowledgable the sales persons are. since they were more interested in Apples and some other customers. probably they would push windows on me. anyway ubuntu preinstaleld there was missing a browser. :-o unity interface though and computer was entry level Acer with Celeron.
 
in major online shops as well as this retailer they were selling HPs with SUSE enterprise linux preinstalled. Cousin bought one and immediatelly replaced it with win7 - needs specialised win software...(still has SUSE sticker though).
 
i think that plenty of hardware works on linux these days if all applications people use (especially games) would work on linux windows would not be necessary. what i use windows for is games and 1 must have widnows only application (bastards dont' want to make linux version even when enterprises requested it).

---

### Post by Jakin on 2012-11-05
> **mastablasta said:**
> anyway ubuntu preinstaleld there was missing a browser.

Thats not such a big deal i guess, as long as there is a guide somewhere in paperwork that comes with the computer for a new to Ubuntu user to know, they can pick one from the built in software center. Although being a system setup to mess around with, they should have installed one, if the store had wifi..

---

### Post by chideock on 2012-11-05
If there was a store here in Canada (Ontario) that sold a Ubuntu laptop with the wifi, video and sound all working I would go buy it, however, I have never seen such a setup in any store I have been in.

---

### Post by TheMTtakeover on 2012-11-05
> **zombifier25 said:**
> Windows 8 boots faster because Windows 8 doesn't shutdown, it **hibernates**. I have a machine that supports hibernating on Ubuntu, and waking up from hibernating is indeed faster than booting from a shutdown.
 
It shutdowns? I didn't click the link so maybe they didn't shut it down and just hibernated it, but Windows 8 does shut down.

---

### Post by Roasted on 2012-11-05
> **Linuxisfast said:**
> Security
Ubuntu is more secure than Windows. It has less flaws and fewer people use it. Because fewer people use it, there are fewer people targeting it. Windows 8 does come built with “Windows Defender” which is supposed to help out a bit.

Quite an amateurish and flawed statement in every sense, this is what MS sales pitchers use and use it regularly to gullible buyers.

While to some degree this makes some sort of sense, the reality is targeting Linux is still a huge incentive to hackers because Linux is a tremendous backbone to the internet. Linux as a whole may have a small desktop share, but that doesn't mean it makes them any less of a target considering their wide spread server use.

---

### Post by lykwydchykyn on 2012-11-05
Do people really waffle between two fundamentally different operating system platforms, offering completely different user experiences and application availability, on the basis of minor benchmark differences?

---

### Post by coffeecat on 2012-11-05
> **TheMTtakeover said:**
> It shutdowns? I didn't click the link so maybe they didn't shut it down and just hibernated it, but Windows 8 does shut down.

It might appear so, but the default behaviour in Win8 is a hybrid hibernation/shutdown in order to speed up boot times. Win8/Ubuntu dual-booters might want to take note of this because it can cause data loss if you write to a shared NTFS partition from Ubuntu while Windows is in its curious semi-hibernated shutdown state. Link:

[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)

---

### Post by mike acker on 2012-11-05
> **Linuxisfast said:**
> Security
Ubuntu is more secure than Windows. It has less flaws and fewer people use it. Because fewer people use it, there are fewer people targeting it. Windows 8 does come built with “Windows Defender” which is supposed to help out a bit.

Quite an amateurish and flawed statement in every sense, this is what MS sales pitchers use and use it regularly to gullible buyers.

"IMHO", it's important to understand the what makes a difference in Windows v Linux security

[ Suggested Reading ]("http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/")

the essay is a little dated but still relevant and insightful

Windows patched up the admin user problem pretty good by adding UAC in Vista

but the problems with remote procedure calls leading directly into kernel code remains. and they keep fussing with "ASLR" and "DEP" -- which is just playing hide and seek with the hackers. Not a good plan because to make a computer work the control blocks are all chained together with address pointers -- which the hacker can follow just like the system does

I think part of the problem in Windows is that in rushing to implement the Hardware Abstraction Layer ("HAL") they neglected to implement fully memory protection as provided by x86 chosing to rely instead on the virtual memory feature set
Reference: _Rootkit Arsenal_ Bill Blunden

I wish I could find out more about "userland" in Linux

---

### Post by parvas24 on 2012-11-14
In the past 10 to 12 years I had used various operating systems at home using disk partitions  on my hard drive.
In those days I tried  Windows 95 and Windows XP, Mac OS X ,  PC BSD and recently Windows 7 operating systems.
As far as my affair with Linux operating systems .. I tried Mandriva, Xandros linux, OpenSuse, Fedora, CentOS , Lintlinux and PearLinux.
I saw a demo of Windows 8 operating system at a nearby computer retail store and was not impressed.

Recently started using UBUNTU 12.04 and upgraded to UBUNTU 12.10 
I am really hooked unto this UBUNTU 12.10 operating system .... 
First was impressed me the most about Ubuntu 12.10 ... 
1) It was easy to install and did not take took much time either.
2) did not require high end hardware to install the operating system.
3) I was comfortable with the UI of Unity, and the DASH has a Mac like
     feel so anybody    can get used to it , it is actually easy on Unity . 
4) newer graphics cards are also being supported to play games.
5) Wine allows you to run Windows programmes which is useful since many people would want to run Microsoft Office for productivy in home or office setttings. 
6) community support is very good on Ubuntu to resolve issues.
7) licence is free of cost . No hassles.
8) Hardware manufacturers are now bringing in linux compatible products , these days linux compatible means - Ubuntu compatible. 
9) NO VIRUS OR MALWARE problems.
10) Ubuntu has better hardware support with drivers .
11) Ubuntu software center provides many useful applications. 
12) Wifi accessibilty is great on Ubuntu ... I remember struggling with Cent OS and
     OpenSuse to gain Wifi access at home and work. 

**A few things Cannonical and Ubuntu developers do are :**
1) Open up Debian / Ubuntu training courses across the globe or through the internet.
   Something on the lines of REDHAT certification or Novell certtification .
2) Encourage the Ubuntu operating system in primary and secondary schools , at present they teach older Microsoft operating systems to students.
3) Develop gaming program for Ubuntu to run all Windows compatible games .
4) All graphic cards - both new and old should work with Ubuntu .
5) Tweak Libre office to be more compatible with MS office 2003 , 2007 , 2010 , etc
     so that there is no need for anybody to use MS office anymore ... the work 
     environment depends on MS office at present .. that needs to change permanently.
6) Preinstalled Ubuntu operating systems at retail stores would be helpful.
7) Set up service cum software support center for Ubuntu . Many people with computer issues can fix their computers and also learn about Linux and Ubuntu as an alternative to their current operating system.

---

### Post by agy2154 on 2013-02-18
I mean there are two things Ubuntu can get, in my opinion, to beat Windows, applications and make things easier for new users.

---

### Post by Kov3nant on 2013-02-18
> **agy2154 said:**
> I mean there are two things Ubuntu can get, in my opinion, to beat Windows, applications and make things easier for new users.

It doesn't get much easier for new users than Ubuntu. You can accomplish almost anything with point and click. My first time on Ubuntu was WAY easier than my first time on Windows. People only know windows because it's what "everybody" uses. I've suggested Ubuntu to all my family members, and the ones that have switched all say how "intuitive and simple it is" to use Ubuntu.

---

### Post by agy2154 on 2013-03-02
I see your point. But Ubuntu still has problems. If it weren't for a couple of things I would have went full steam ahead with Ubuntu. When I use After Effects Photoshop with Ubuntu via WINE its isn't as fast as Windows and the most important thing is that my Windows audio driver supports noise suppression for my microphone, I don't think Ubuntu has that.

---

### Post by lykwydchykyn on 2013-03-02
> **agy2154 said:**
> I see your point. But Ubuntu still has problems. If it weren't for a couple of things I would have went full steam ahead with Ubuntu. When I use After Effects Photoshop with Ubuntu via WINE its isn't as fast as Windows and the most important thing is that my Windows audio driver supports noise suppression for my microphone, I don't think Ubuntu has that.

If you run anything that isn't the OS running on ~90% of the world's PCs -- the OS that your PC was designed to work with, and whose logo is probably stuck to the front of the machine -- then *at best* you're going to have little things like this that don't work.  That's just reality.  

I've been using Linux for ten years now.   I remember a time when you were lucky to have a sound card that even worked at all.   I remember when WINE couldn't run much of anything useful, and if it did you didn't dare upgrade it because chances are it wouldn't in the next release.  Heck, I remember when getting to a desktop with any given video chipset was a crapshoot.

If your comments represent the real state of problems with Linux compatibility these days, I'd say things are moving pretty nicely.

---

### Post by Lupi on 2013-03-02
> **chideock said:**
> If there was a store here in Canada (Ontario) that sold a Ubuntu laptop with the wifi, video and sound all working I would go buy it, however, I have never seen such a setup in any store I have been in.

[https://www.system76.com/laptops/](https://www.system76.com/laptops/)

---

### Post by justincarter on 2013-03-04
Yes, I agree with you. Nice article.

---

