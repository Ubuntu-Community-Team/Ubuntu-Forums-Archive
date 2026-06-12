---
title: "Windows security for beginners (in a nutshell)"
date: 2007-01-13
forum: Windows
---

### Post by pichalsi on 2007-01-13
Ive seen the warning that this is not a bashing area, but I couldnt find a better place where to post a rant. If you know about some windowsxp-forums.org please tell me so that I can post it there too.  Also sorry for a long post (looks like my longest here hehe) and bad English.

I used and still use Windows XP, although now only for one game (Warcraft3 TFT, I know it runs in Wine but Im too lazy and there are a few other issues...). I used to be a "power-user" and still know (in comparison to other people) a lot about that operating system. I always had my family's desktop set well, using only a firewall (Zone Alarm, no advertising :) ) and "educating" other users of that PC. I remember myself helping others, either friends or family with viruses, troyans or just partitioning and installing OS (from my burned CD, sorry but I have not seen original Windows disc in my whole life except on pictures). All these people were the ones that "just use the PC", set everything to run after start, using IE and think that Internet cant do anything to their PC. I dont have problems helping people but from the time around half a year ago, when i started using Linux, it gets worse and worse. Im loosing my patience.

This morning my uncle called me, his PC, bought for his family for this Christmas, already "doesnt connect to Internet". Internet Explorer kept telling him it cant find c:/secure32.html (try to Google it to see how many people experience it if you wonder) and exiting. He told me his antivirus found a virus yesterday so he scanned whole disc, quarantined viruses (not one), and turned off PC thinking hes safe only to find his PC crippled today. I first thought its not that hard to fix (it wasnt before) but from what Ive seen in forums I found by Google he didnt have one spyware but many... 

Now the part about Windows being newb-friendly (sorry if it sounds like an insult). I asked him how he connects to Internet, answer was he clicks on IE icon. So I asked if the PC connects right after start but of course he knew nothing. He didnt know about anything he downloaded, but he probably installed a lot of things he didnt want. Is this really so user friendly to tell user nothing about whats happening? Internet is becoming wide-spread (and in other countries it already is) but with this development and users being so dumb...

So I gave him Firefox and antispyware with only hope in Firefox, so that his PC is connected to Internet but only IE doesnt work... When I read the steps to remove the malware I better didnt try to tell him to do anything of what was there. Now I come to thinking if poeple had better protection software, more antivirus and firewalls, they would still have their PCs infected, cause social engineering, ads and ignorant user in first place are the reasons. 

Last and most important thing I found out is how bad the system is and how great Linux is. Guess I had similar problem in Linux Im 99 percent sure si could find solution by Google or someone on these wonderful forums would help me. I realized I cant find any really reliable source of information for Windows problem, and Im becoming more paranoic when using closed source and unknown software (I dont trust any of the "fixes".exe that I found... who will confirm that they are not spyware too?).

Conclusion? My faith in Linux being newb friendly has doubled. Until now I thought "Ubuntu is great for me but why should I spread it to others? They can choose themselves...". Reality is different...

---

### Post by PurplePenguin on 2007-01-13
> **pichalsi said:**
> Conclusion? My faith in Linux being newb friendly has doubled. Until now I thought "Ubuntu is great for me but why should I spread it to others? They can choose themselves...". Reality is different...

I found myself in the same boat, getting call after call from people who need help after being infested with viruses and spyware.  When I tell people that I use linux and don't worry about any of this bad stuff, they automatically want in.  The big question, though, is always how hard it is to use.  I tell them that I'll fix their Windows (that is, format and reinstall) but I'll also make a new partition and install Linux.  This way - at worst - if they run into viruses, they'll have a backup.  At best, they'll boot into Ubuntu and see the big Firefox icon that I put on their desktop staring at them and they'll try using it.

I don't want to sound like some kind of open source missionary, but I do find that the average computer user (that is, who wants to go onto the internet every day and maybe every so often write a letter or something) finds Ubuntu to be quite intuitive and is willing to learn a new environment in order to not worry about viruses.

---

### Post by aysiu on 2007-01-14
Security and convenience are often at odds when it comes to computers.

If someone were insistent on using Windows and wanted to be safe, I would advise using a limited user account. You can't get everything you want done using a limited account (Explorer as root, for example, or even some programs that require you to be administrator), but you're generally pretty safe.

---

### Post by MindRiot on 2007-01-14
I agree with aysiu.

You should run Windows under a limited user account.  You essentially do the exact same thing in Linux.

I have often used the "run as" administrator command in Windows XP, which you can access from the context menu, by right-clicking on the executable file or icon, and this tends to work more often than it doesn't.

Its a shame there isn't a similar context menu option for Ubuntu. Would be nice to run a program by right-clicking the file and then select "run as" and this diplays the password dialogue box, instead of having to bash the program in the terminal if it needs sudo priveledges.

---

### Post by PurplePenguin on 2007-01-14
> **MindRiot said:**
> Its a shame there isn't a similar context menu option for Ubuntu. Would be nice to run a program by right-clicking the file and then select "run as" and this diplays the password dialogue box, instead of having to bash the program in the terminal if it needs sudo priveledges.

I agree!! I made use of this "run as" quite often when I was using Windows.

I recently installed some nautilus scripts that come close, though... "gedit as root" is very helpful!

---

### Post by aysiu on 2007-01-14
> **MindRiot said:**
> 
Its a shame there isn't a similar context menu option for Ubuntu. Would be nice to run a program by right-clicking the file and then select "run as" and this diplays the password dialogue box, instead of having to bash the program in the terminal if it needs sudo priveledges. I've been annoyed the other way around. Usually in Ubuntu the programs that require root access are already built to *sudo* (for example, Synaptic Package Manager or the GDM configuration), so when you click on the icon, it already asks for authentication. The one exception to this is Nautilus (which you sometimes run as root and other times run as user), but Windows doesn't let you Run as... for Explorer, anyway, and it's not that difficult to create a launcher for *gksudo nautilus*--or even a keyboard shortcut.

On the other hand, right-clicking, selecting Run as..., and then pressing the down arrows to the appropriate account--that I find annoying, especially since you can't do it for the Control Panel items (you have to find the actual .cpl files) or for Explorer.

---

### Post by Yossarian on 2007-01-14
> Originally posted by **aysiu**
I've been annoyed the other way around. Usually in Ubuntu the programs that require root access are already built to sudo (for example, Synaptic Package Manager or the GDM configuration), so when you click on the icon, it already asks for authentication. The one exception to this is Nautilus (which you sometimes run as root and other times run as user), but Windows doesn't let you Run as... for Explorer, anyway, and it's not that difficult to create a launcher for gksudo nautilus--or even a keyboard shortcut.

On the other hand, right-clicking, selecting Run as..., and then pressing the down arrows to the appropriate account--that I find annoying, especially since you can't do it for the Control Panel items (you have to find the actual .cpl files) or for Explorer.


IIRC you can hold shift and right click the control panel icons to Run as.

---

### Post by holylucifer on 2007-01-14
Well windows is designed for that,i say again.

---

### Post by aysiu on 2007-01-14
> **Yossarian said:**
> IIRC you can hold shift and right click the control panel icons to Run as.
That's *really* handy! Thanks for that. Can I ask how you knew that? I thought I Googled around for that already. Guess I wasn't as thorough in searching as I thought I'd been.

---

### Post by MindRiot on 2007-01-14
> **aysiu said:**
> ...and it's not that difficult to create a launcher for *gksudo nautilus*--or even a keyboard shortcut..

True.

But isn't the nautilus launcher basically the equivalent of Run from the Windows Start menu.?  I definitely appreciate the "*builtin sudo*" in gnome applications like the synaptic package manager, but what if I want to run an executable file in one my system folders from the file browser? Do I always have to make a shortcut with root?  A simple context menu option that allows quick authentication would be, if anything, helpful and convienent.

---

### Post by aysiu on 2007-01-14
Alt-F2 is basically the equivalent of Run

If I could *gksudo explorer* in Windows, that'd be helpful. How do you right-click My Documents to edit as root?

---

### Post by MindRiot on 2007-01-14
> **aysiu said:**
> If I could *gksudo explorer* in Windows, that'd be helpful. How do you right-click My Documents to edit as root?

If I could gksudo file browse in Ubuntu, that'd be helpful.  Can you do that?

> **aysiu said:**
> How do you right-click My Documents to edit as root?

Yes, unfortunately in WIndows, many files, such as cookies and the temp cache, are located in folders under Local settings which are hidden and would require administrative priviledges,   but more often you wouldn't need to edit many of the files in My Documents as root.  However, almost all files located outside the home (user) folder (except some commands in /bin are read-only and cannot be executed without sudo.  In other words, if an executable is in a system folder in Ubuntu, it has, by default, read-only priveledges (this isn't the case with the WINDOWS system folder), and therefore sudo is required to run or edit the file.  Since you cannot log-in as root in Ubuntu, you need to use the terminal to sudo or Alt-F2 to gksudo the file, or change the permissions as root for the filesystem.  Is this not correct?

---

### Post by aysiu on 2007-01-14
> **MindRiot said:**
> If I could gksudo file browse in Ubuntu, that'd be helpful.  Can you do that? Yes! Alt-F2 ```
gksudo nautilus
``` Ta-da!

---

### Post by 3rdalbum on 2007-01-14
Or add that command to your panel as a launcher.

You can also say "open this file as root" by creating a launcher on your desktop, attaching the following command:

```
gksudo -m "Enter your password to open the file as root." gnome-open %u
```

Dragging and dropping the file onto the launcher will ask you for your password, before opening the file as root.

---

### Post by Yossarian on 2007-01-16
> Originally posted by **aysiu**
That's really handy! Thanks for that. Can I ask how you knew that? I thought I Googled around for that already. Guess I wasn't as thorough in searching as I thought I'd been.
I did LAN administration/desktop support for 4 months and I picked it up there.  I think it's a bad UI decision, as it's not particularly discoverable or documented, and the alternatives are frustrating.

Edit:

It looks like 'Run as' might be scriptable.  MS has [a web page]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/windows_security_runas_shortcut.mspx?mfr=true") that shows how to 'Run as' from Windows wonderful command line.  A family member has Final Fantasy XI, a video game that requires admin rights to be run.  I will try to set him up with this instead.  Anyone have any experience with this?

---

