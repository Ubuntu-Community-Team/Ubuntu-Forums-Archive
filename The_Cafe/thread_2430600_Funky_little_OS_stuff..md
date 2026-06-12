---
title: "Funky little OS stuff."
date: 2019-11-04
forum: The Cafe
---

### Post by Shibblet on 2019-11-04
As a longtime Linux and Windows User, I have noticed many differences between the operating systems that are not usually talked about when people try to compare the two.  Small things like "how quickly the computer shuts down," "how fast programs launch from when you click on them," and "why are windows drives mounted by default, and not linux..." etc.  Minor things like that.

A lot of it comes down to how you have your computer configured, but some of these things are still there.

Ever close a program in Ubuntu, then realize you need to open it again, and it seems to take longer to re-open?
Ever sit there watching Windows "Shut-Down" screen for an absurd amount of time, wondering what the heck could be taking it so long to shut down?
Ever uninstall an application and watch how Windows and Linux leave a truck ton of unnecessary dependencies all over the HD?

Just a couple of things that I noticed.

However, the question for everyone is, "What kind of little things have you noticed between OS's that bug you, and how have you fixed or learned to deal with them?"

---

### Post by uRock on 2019-11-04
I've definitely contemplated the long time Windows takes to shut down. I'd like to one day set up a network to monitor traffic and see what may be happening during shutdown, such as logs being transmitted.

I don't use Windows often, so not seeing many other quirks.

---

### Post by CatKiller on 2019-11-04
> **Shibblet said:**
> 
Ever close a program in Ubuntu, then realize you need to open it again, and it seems to take longer to re-open? 
Nope. Restarting an application is quicker than starting it from scratch. 

If you mean that applications sometimes take longer to initialise than they do to exit, then of course they do. Kill the window, free the memory is trivial compared to setting up whatever memory structures it might need to actually run, much of which might need to be retrieved from the hard drive. 
> Ever sit there watching Windows "Shut-Down" screen for an absurd amount of time, wondering what the heck could be taking it so long to shut down? 
I haven't used Windows in nearly 15 years, so, no. 
> Ever uninstall an application and watch how Windows and Linux leave a truck ton of unnecessary dependencies all over the HD? 
Nope. Dependencies that are no longer needed are listed as such, and can be automatically removed with an *apt autoremove*.

---

### Post by sdsurfer on 2019-11-05
The only thing that "bugs" me about Ubuntu is the screwy window scrollbars. It's a pretty good tradeoff. An excellent tradeoff, actually, my list is much longer for Windows.

The worst of it is, I run multiple applications with dual monitors, generally with windows maximized on the monitors. The cursor sometimes "slips" off the scrollbar on the left main monitor and into the app on the right. Most of the time that's Evolution, and the effect is the cursor "grabs" one of the mailboxes and starts to move it in the direction I was scrolling. Evolution hangs for a bit when that happens and I sit there facepalming . . .

It's 99% user error. I try to minimize Evolution after checking mail, then when the cursor slips off the scrollbar it just slides across the desktop. :-)

---

### Post by TheFu on 2019-11-05
There is often some expectation by many new Linux users that the way Microsoft chose to do things was the right way.  That preconception is hardly the fault of Linux, which is based on Unix.   Expecting an entirely different OS to behave the same as any other OS is crazy.

Most of the issues I had with Windows was solved by limiting my need to use it.  A simple solution.

I tried OSX for 3 weeks and found it incredibly frustrating. Before I threw the Mac against the wall, I had someone come pick it up.  Another simple solution.

Every OS isn't for every user.  For years and years, I tried to convince people that Unix was a superior OS compared to all others.  That just left everyone frustrated - them and me.  

Mom's PC got hacked.  I'd been moving her off Windows-only software onto F/LOSS versions for a few years.  The hacking wasn't her fault - what Grandma would not click a link for "New Baby Photos!" sent from a grand daughter with a new baby?  She new the hack happened immediately and powered off the system, then called me.  We talked it over and she decided that running Linux was the best answer.  She was very afraid because I run a very streamlined GUI without menus.  Put her on LXDE with a custom side menubar that had the 5 programs she used.  After a few hours, she was comfortable, though not completely happy.  While I was there, I setup local and offsite versioned backups.  We never needed those.   After a few years, I learned that the only people unhappy with the change were the grandkids who came over to play online computer games.

I do keep a Win7 machine around to handle small biz accounting needs and simple video editing. No plan to move to Win10. Simply cannot accept the new terms from MSFT.  Had setup WINE for use with the accounting program, but only about 80% of it worked and the mouse was always a little "off."  After 3 yrs of that, I gave up.  A Windows VM solved it for about a decade.

As for Ubuntu GUI issues, I solved those by switching back to a WM-only solution using a WM first started using in 1995. I've always preferred the lighter GUIs anyway. This WM, fvwm, allows complete control over window decorations. I seldom run any windows full screen, except lite video playback thru mpv. The heavy GUIs don't work well running inside VMs.  My main desktop is running inside a VM on a headless server - the connection to it is over x2go either from the LAN or 2 continents away.

I do have a major issue with Thunderbird today.  Had it a few months ago and solved it.  Mozilla keeps trying to protect normal people from themselves, which is causing me lots of problems.  Their DNS override effectively breaks access to internal servers here because Firefox won't follow the OS rules to check /etc/hosts first.

---

### Post by CatKiller on 2019-11-05
> **sdsurfer said:**
> The only thing that "bugs" me about Ubuntu is the screwy window scrollbars. It's a pretty good tradeoff. An excellent tradeoff, actually, my list is much longer for Windows.

The worst of it is, I run multiple applications with dual monitors, generally with windows maximized on the monitors. The cursor sometimes "slips" off the scrollbar on the left main monitor and into the app on the right. Most of the time that's Evolution, and the effect is the cursor "grabs" one of the mailboxes and starts to move it in the direction I was scrolling. Evolution hangs for a bit when that happens and I sit there facepalming . . .

It's 99% user error. I try to minimize Evolution after checking mail, then when the cursor slips off the scrollbar it just slides across the desktop. :-)

I haven't tried to grab a scrollbar since the late-90s when I got a mouse with a scroll wheel.

---

### Post by uRock on 2019-11-05
> **CatKiller said:**
> I haven't tried to grab a scrollbar since the late-90s when I got a mouse with a scroll wheel.

I only ever use it on this site. I haven't had that issue, though.

---

### Post by SeijiSensei on 2019-11-05
I've found that Windows takes a long time to shut down after a system update.  Most anything involving software updates on Windows takes inordinately longer than on Linux.  And, of course, you cannot track the progress of Windows updates to see why they are slow. Very annoying when you're used to running "sudo apt update; sudo apt upgrade" from the terminal prompt.

On the issue of mounting drives, I assume you're asking why does Windows ignore the ext2/3/4 filesystems on your drive while Ubuntu identifies NTFS filesystems and adds them to /etc/fstab during installation. MS's whole raison-d'etre is based on convincing users that Windows is the only game in town.

---

### Post by #&amp;thj^% on 2019-11-05
At work we have one W10 tower and on that I use only command line.
Windows Powershell for command line updates (W10):
type in,
```

Install-Module PSWindowsUpdate
```

to install the Windows Update module for Windows Powershell.

After that,
```

Get-WindowsUpdate
```

to connect to the Windows Update servers and download the updates if found.

Finally, type in,
```

Install-WindowsUpdate
```
Start checking for updates:
```

UsoClient StartScan
```

Start downloading Updates:
```

UsoClient StartDownload
```

Start installing the downloaded updates:
```

UsoClient StartInstall
```

Restart your device after installing the updates:
```

UsoClient RestartDevice
```

Check, Download and Install Updates:
```

UsoClient ScanInstallWait
```

It is worth noting that, the Command Prompt commands mentioned above are just meant for Windows 10. For older versions of Windows, you need to use the following commands,

Start checking for updates:
```

wuauclt /detectnow
```

Start installing the detected Updates:
```

wuauclt /updatenow
```

Check, download and install updates:
```

wuauclt /detectnow /updatenow
```
Just trying to be helpful, though I don't personally use it. ;)

---

### Post by sdsurfer on 2019-11-06
> I do keep a Win7 machine around to handle small biz accounting needs

So GnuCash won't work from you? It was one of the first things I did, exported my QuickBooks files as .IIF and imported them into GnuCash, it works better, easier to use, and of course free. A bit of a learning curve though, and the graphs/reports are fairly basic (I seldom need them anyway.)

Their dev team is really responsive to reported bugs, I had one just the other day with the latest version and they already have a patch in the next push but told me how to correct it locally.

---

### Post by TheFu on 2019-11-06
> **sdsurfer said:**
> So GnuCash won't work from you? It was one of the first things I did, exported my QuickBooks files as .IIF and imported them into GnuCash, it works better, easier to use, and of course free. A bit of a learning curve though, and the graphs/reports are fairly basic (I seldom need them anyway.)

Their dev team is really responsive to reported bugs, I had one just the other day with the latest version and they already have a patch in the next push but told me how to correct it locally.

Stock investing.

---

### Post by Shibblet on 2019-11-12
Here's an interesting one...

Install the Brave Browser from the Snap on Ubuntu 19.10, and the launcher doesn't work from the side menu.  It does work if you go into the apps menu though.  It also works fine in Kubuntu 19.10, through the launcher, or K Menu.

Weird stuff like that.

---

### Post by bernard010 on 2019-11-28
Lenovo desktop- Ubuntu 19.10 Gnome - Online logged into Ubuntu server - Thunderstorm with Power outage _no UPS. Lengthy Outage.
Power starts up... Computer comes on..OS starts...Everything even re-logged me back into the Ubuntu Server on its own. 
Opened up to the very page that I was working on too. .. **Funky little OS stuff.  I have save my session checked on the logout screen.**

---

