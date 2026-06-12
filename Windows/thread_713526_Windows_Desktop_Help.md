---
title: "Windows Desktop Help"
date: 2008-03-02
forum: Windows
---

### Post by Gannon8 on 2008-03-02
About a day or so after installing linux, when I log on to my windows account, the start menu nor my desktop icons appear or my startup programs launch. Right clicking does nothing. I can however bring up the task manager and click New task to start up programs, and they work OK (otherwise I wouldn't be typing this message). Is there anyway to fix this?

---

### Post by Oldsoldier2003 on 2008-03-02
> **Gannon8 said:**
> About a day or so after installing linux, when I log on to my windows account, the start menu nor my desktop icons appear or my startup programs launch. Right clicking does nothing. I can however bring up the task manager and click New task to start up programs, and they work OK (otherwise I wouldn't be typing this message). Is there anyway to fix this?

Actually if windows starts its really got nothing to do with your Ubuntu installation. I've run into that issue before with Windows XP but it was so long ago i don't remember what i did  to fix it. You'd probably have better luck searching the Microsoft knowledge base or posting on a windows specific forum.

---

### Post by Gannon8 on 2008-03-02
> **Oldsoldier2003 said:**
> Actually if windows starts its really got nothing to do with your Ubuntu installation. I've run into that issue before with Windows XP but it was so long ago i don't remember what i did  to fix it. You'd probably have better luck searching the Microsoft knowledge base or posting on a windows specific forum.
Well, it appeared after I enabled the driver for my graphics card on linux and then my monitor showed a blank screen. I did something in a command line, I think it was this:
[CODE]sudo dpkg-configur xserver-xorg[CODE]
Anyway, I did all the defaults or blank, exept for a few. After that this problem started.

Btw, I found a Ubuntu-Backup folder with nothing in it in the root of the windows partition. Might that have anything to do with it?

---

### Post by Oldsoldier2003 on 2008-03-02
> **Gannon8 said:**
> Well, it appeared after I enabled the driver for my graphics card on linux and then my monitor showed a blank screen. I did something in a command line, I think it was this:
[CODE]sudo dpkg-configur xserver-xorg[CODE]
Anyway, I did all the defaults or blank, exept for a few. After that this problem started.

Btw, I found a Ubuntu-Backup folder with nothing in it in the root of the windows partition. Might that have anything to do with it?

Ubuntu doesn't do anything to your windows install except shrink the partition (if you installed in on the same drive on shrunk the windows partition to make room), and Insert GRUB into the MBR so that you can dual boot. it is possible however that in the pratitioning process something got damaged, but its highly unlikely. The symptoms you decribe are fairly common for windows and before jumping to conclusions and blaming unbuntu you should take a look at the fixes for windows. in fact the issues you are having with windows right  now are part of the reason a good portion of us are using linux.

---

### Post by uberlube on 2008-03-02
If you didnt defrag your windows partition before you resized it you could have lost some important sectors.

---

### Post by Gannon8 on 2008-03-02
Yay, Multiquote.> **Oldsoldier2003 said:**
> Ubuntu doesn't do anything to your windows install except shrink the partition (if you installed in on the same drive on shrunk the windows partition to make room), and Insert GRUB into the MBR so that you can dual boot. it is possible however that in the pratitioning process something got damaged, but its highly unlikely....and...> If you didnt defrag your windows partition before you resized it you could have lost some important sectors.Windows ran normally for awhile so I don't think those are the problems.

> The symptoms you decribe are fairly common for windows and before jumping to conclusions and blaming unbuntu you should take a look at the fixes for windows.
1. I'm not blaming Ubuntu. I was saying that was where the problem started and that I wanted help.
2. I searched the forums and I could not find fixes.
> in fact the issues you are having with windows right  now are part of the reason a good portion of us are using linux.I can 100% agree with that and if everything that worked on windows could work on ubuntu then I would have kicked windows off months ago:D

---

### Post by aysiu on 2008-03-02
As others have said, I suspect this has absolutely nothing to do with Ubuntu, especially since it happened a day after installing Ubuntu, not right away.

Can you try creating a new test user in Windows and seeing if that new test user experiences the same problem? At least that way you can tell if it's a system-wide Windows problem or a user-specific Windows problem.

---

### Post by seventhc on 2008-03-02
I'm not sure, I don't have window..but the part about the defrag is true. It basically get's all the scattered files together, so when you resize your partition there is less of a chance that any files are present in that area.
But if it's starting, I'm sure it can be fixed. Have you tried a system restore..if it's xp.?

---

### Post by amingv on 2008-03-02
Is it Windows XP? If you can see the desktop, but not the icons or the taskbar, check if explorer.exe is loading at startup, or try running it from the task manager.

---

### Post by Gannon8 on 2008-03-03
> **amingv said:**
> Is it Windows XP? If you can see the desktop, but not the icons or the taskbar, check if explorer.exe is loading at startup, or try running it from the task manager.
Yes, it is Windows XP. I don't see explorer.exe in the processes tab in task manager. Where can I find it on the C drive?

I can't create a new user because I can't open explorer.

---

### Post by BillDozer on 2008-03-03
In the task manager:
Pick menu: File/New task

And type explorer.exe

---

### Post by Gannon8 on 2008-03-03
Ok, windows works now.
Will it work even if I reboot or do I have to use task manager again?

---

### Post by aysiu on 2008-03-03
> **Gannon8 said:**
> 
Will it work even if I reboot or do I have to use task manager again? Can you try creating a test user and seeing if that user runs into the same problem? That's the best way to diagnose if the failure is system-wide or user-specific?

---

### Post by corney91 on 2008-03-03
I once had a virus, which prevented explorer.exe from running at startup. Yours sound like the exact symptoms I had. This was on Vista but it could be related...
I couldn't be bothered to run through virus scans so I used system restore to fix it.

---

### Post by Gannon8 on 2008-03-03
> **aysiu said:**
> Can you try creating a test user and seeing if that user runs into the same problem? That's the best way to diagnose if the failure is system-wide or user-specific?I made a new account, rebooted my computer, and logged in to the new user. Same problem.

I'm taking corney's advice and downloaded ClamWin. It's scanning right now and I'll edit this post when it gets done.

---

### Post by seshomaru samma on 2008-03-04
you should really scan for viruses /malware
use [adaware]("http://www.lavasoftusa.com/") / [spybot]("http://www.spybot.info/en/index.html") /[AVG]("http://free.grisoft.com/")

try [panda online scan ]("http://www.pandasecurity.com/homeusers/solutions/activescan/?"), [kasparsky online scan ]("http://www.kaspersky.com/virusscanner") and [trend micro ]("http://housecall.trendmicro.com/") (probably the best)

if you are interested in keeping your windows virus free - it's possible but involves quite a lot of tweaking -read[ this excellent guide  ]("http://forums.windowsforum.org/index.php?showtopic=33716") (his HOSTS file can be applied in Linux as well)

---

### Post by sayakb on 2008-03-04
> **Gannon8 said:**
> Yes, it is Windows XP. I don't see explorer.exe in the processes tab in task manager. Where can I find it on the C drive?

I can't create a new user because I can't open explorer.

The explorer.exe can be found in c:\windows folder. Open task manager and just type explorer in the New Task to start explorer. Check for any spoilt startup entries by going to Run and typing "msconfig" then going to the startup tab.

---

