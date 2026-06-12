---
title: "Suddenly Win 7, Win 2K, and Ubuntu don't run (under VB in Kubuntu)"
date: 2024-08-23
forum: Virtualisation
---

### Post by Tom_ZeCat on 2024-08-23
Hey, everyone.  I&#8217;m super frustrated.  On my Kubuntu Linux (22.04) PC, I run VirtualBox to run the following guest Oses: 

Windows 7 Ultimate
Windows 2000
Ubuntu 22.04.  

Both of those Windows guests are important to me for running older Windows software.  The Ubuntu guest is only there because I was trying it out, and is therefore not important.  But to suddenly not be able to run those two older Windows OSes has caused headaches for me.  I run an old program named Dramatica for outlining novels, plays, and screenplays.  It runs under WINE, but not very well.  There&#8217;s also other old Windows software that I run, not every day, but when I need it I need it.  

Suddenly, maybe after an update, none of those guest OSes run anymore.  I get the following error: 

[IMG]https://i.postimg.cc/7LQ0T987/Error-Message-Win2-K.png[/IMG]

I get the same error no matter which guest OS I try to run.  I have the guest additions, and my version is as follows: 

VirtualBox 6.1.50_Ubuntu r161033

My guest operating systems are in Home/VirtualBox Vms/[OS Name].  Screen shots: 

[IMG]https://i.postimg.cc/W18Msj55/Win2-KGuest-OS.png[/IMG]

[IMG]https://i.postimg.cc/KYYtzVVx/Win7-Guest-OS.png[/IMG]

I don&#8217;t know why these operating systems quit working, but it&#8217;s quite frustrating.  I could, of course, uninstall and reinstall them, but I&#8217;ve got both Win 7 and Win 2K highly configured to my needs with the apps installed also highly configured.  We&#8217;re talking a lot of work here if I have to install everything from scratch.  

Can I simply back up those guest OSes and, reinstall VB, and then copy the OSes back to those same folders and have it work?  Or can I just install the newer VB over everything and get it working again.  

Win 7 and Win 2K are both important, but Ubuntu as a guest isn&#8217;t.  I was just seeing what the latest Ubuntu is like.  The VB version available in Kubuntu&#8217;s Discover repository is: 

6.1.50-dfsg-1~ubuntu1.22.04.3

I usually install from the repository, but I could do so from the latest version (via deb file, PPA, or whatever) if that would be better.  I don&#8217;t care whether I have the latest version.  All I care about is getting my two old Win OSes working again.  Thank you for any help.

PS: In that first screen shot, you can see that it suggests asking in Oracle's forum at [www.virtualbox.org](www.virtualbox.org).  However, I tried that, but all their boards crash.  I think they may have shut them down, but if anyone here knows what might work, I very much appreciate any help.

===================================
Edit: 
I have my VB logs.  If they would be helpful, let me know.  I can post them.

---

### Post by &amp;KyT$0P# on 2024-08-23
> **Tom_ZeCat said:**
> Suddenly, maybe after an update, ...

VirtualBox 6.1.50_Ubuntu r161033

There have been several reports of this version breaking with kernel update to 6.8.x, see e.g. [this thread]("https://ubuntuforums.org/showthread.php?t=2499957")

---

### Post by Tom_ZeCat on 2024-08-23
Thanks.  I'll probably just install the newest VB and reinstall those OSes in it, or possibly that other option for virtualization -- I forget its name.

---

### Post by Tom_ZeCat on 2024-08-23
An update: 

I purged the old version of VirtualBox and then installed the new version 7.  That did not delete my old guest OSes (and I also had them backed up).  As soon as I ran Windows 7, it ran fine, and then it offered to update the Guest Additions.  It's all running great now.  This was way less painful than I thought it would be.  I thought I would have to reinstall all the guest OSes and all my applications in them.  I'm happy that I don't have to.  This seems a better solution than downgrading my Linux kernel.  I'm posting this for the benefit of the next person who runs across this problem.

---

