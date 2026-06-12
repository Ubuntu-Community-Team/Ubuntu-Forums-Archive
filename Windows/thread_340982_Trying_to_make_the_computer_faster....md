---
title: "Trying to make the computer faster..."
date: 2007-01-18
forum: Windows
---

### Post by SZF2001 on 2007-01-18
OK, so my family runs a Windows box, and it's all fine and dandy - except that it was bought back in '01, we've never run another fresh install since then (because Dell didn't think they needed to provide us with any OS disks of any kind), and has had a LOT of crap (and not crap) installed onto it, through the years, on and off.

Now, I've found this Windows box to become very tedious and slow.

One problem I saw was how much resources were needed to make all the Bubbly Wubbly effects come to place that you usually see in Windows (like the blue Start button, side panels, etc), so I switched everything to faster performance rather than better appearance. That cut boot and loading time at least in half.

Now I find that we have a bunch of old programs no one needs or uses booting up into the tray at startup, making startup slow as HELL (except, now, after switching to better performance, it isn't a problem since they all just sit there). So I'm wondering, since I can't find half the crap on the tray with the Add/Remove programs option in Control Panel, I'm wondering if there is a way I can change how things boot up - as in, making all the programs not boot with boot up, for faster performance.

Any ideas? I'm pretty used to Linux now so being back on a Windows box may have made my brain switch a few triggers, or something...

---

### Post by blackened on 2007-01-18
I think a couple versions of Windows have a utility that can do this, but honestly it's been so long since I've used Windows I don't really remember. I know that there are a few things in the registry that you can change to alter the boot process. Such as:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
There are similar keys that have the same effect in
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce

These can be accessed using regedit from the command prompt or the run dialog. Another side benefit of this approach is that the path to the executables will show up in regedit when you find their entries.

---

### Post by aysiu on 2007-01-18
This link may help:
[http://www.jasonn.com/turning_off_unnecessary_services_on_windows_xp](http://www.jasonn.com/turning_off_unnecessary_services_on_windows_xp)

---

### Post by Cope57 on 2007-01-18
Here is a few tips to speed up your PC...

**Speed up Menu Display**

You can use this tip to speed up the way menus display in Windows XP.
*Click Start, click Control Panel, click Performance and Maintenance, and the click System.
 *Click the Advanced tab, and under Performance, click the Settings button.
 *Clear the Fade or slide menus into view check box, and then click OK.
Now when you bring up a collapsed menu, it will expand without delay.


**Turn Off Indexing to Speed Up XP**

Windows XP keeps a record of all files on the hard disk so when you do a search on the hard drive it is faster. There is a downside to this and because the computer has to index all files, it will slow down normal file commands like open, close, etc. If you do not do a whole lot of searches on your hard drive then you may want to turn this feature off:

    *Open My Computer.
    *Right-click your hard drive icon and select Properties.
    *At the bottom of the window you'll see "Allow indexing service to index this disk for faster searches," uncheck this and click ok.
    *A new window will pop up and select Apply to all folders and subfolders.
It will take a minute or two for the changes to take affect but then you should enjoy slightly faster performance.


**Clean Your Prefetch to Improve Performance**

This is a unique technique for WinXP. We know that it is necessary to scrub registry and TEMP files for Win9X/ME/2000 periodically. Prefetch is a new and very useful technique in Windows XP. However, after using XP some time, the prefetch directory can get full of junk and obsolete links in the Prefetch catalog, which can slow down your computer noticeably.

    *Open C(system drive):/windows/prefetch, delete those junk and obsolete files, reboot. It is recommended that you do this every month


**Performance Increase Through My Computer**

Easy enough tweak to usually find out about it on your own, but still, some of us still don't find it right away. So here it is:

    *Start > right-click on My Computer and select Properties.
    *Click on the "Advanced" tab.
    *See the "Performance" section? Click "Settings".
    *Disable the following:

      Fade or slide menus into view
      Fade or slide ToolTips into view
      Fade out menu items after clicking
      Show Shadows under menus
      Slide open combo boxes
      Slide taskbar buttons
      Use a background image for each folder type
      Use common tasks in folders

There, now Windows will still look nice and perform faster.

You could also use [http://www.ccleaner.com/](http://www.ccleaner.com/) to help clean up some old junk from the PC.
Also a scan disk, defrag, update all drivers could not hurt. Scan for viruses, Trojans, spyware, malware, and other M$ issues.

I know this is not a M$ website and somebody would have just told you to post this in a different forum, but I believe that all Linux users should be able to help out anybody with any PC issue they are having... Just don't make it a habit... ;)

---

### Post by aysiu on 2007-01-18
> **Cope57 said:**
> 
I know this is not a M$ website and somebody would have just told you to post this in a different forum, but I believe that all Linux users should be able to help out anybody with any PC issue they are having... Just don't make it a habit... ;) This isn't an MS website, but this is the Windows Discussions subforum, so the question is more than appropriate.

---

### Post by riven0 on 2007-01-18
CCleaner and [Spybot Search & Destroy]("http://www.spybot.info/") were the two programs I used the most. Also, depending on what anti-virus program your using that can cause your comp to drag. I recommend [anti-vir]("http://www.free-av.com/") as it's pretty low on resources.

---

### Post by irish_flu on 2007-01-18
Go to **Start Menu** --> **RUN** then type "**msconfig**".  This GUI app will give you a whole lot of control over what programs are running at startup.  It's pretty cool.

---

### Post by blackened on 2007-01-18
Not all versions of Windows come with msconfig.

---

### Post by irish_flu on 2007-01-18
> **blackened said:**
> Not all versions of Windows come with msconfig.

Good point, I just assumed (given the age of the machine) that it's probably Windows 98, Windows ME, or Windows XP (which all have msconfig).

If you have Windows 95, Windows NT4, or Windows 2000 Professional my earlier advice won't work for you.

---

### Post by derjames on 2007-01-18
-Remove Norton or McAfee (if you have them of course) they slow down a system significantly
-For a firewall activate the WIndows Firewall
-For an Antivirus use AVAST which is free for non-commercial usage 
-Install CrapCleaner (CCleaner) and run it several times
-Install Spybot search and destroy. 
-Disable all the unwanted services (see posts above)
-USe the CLassic windows theme
-Remove any other application you are not using
-Defrag de HArd drive

If you have the winXP install CD then backup all your stuff and reinstall Windows...


Hey... I do not have to do anything like this in Linux... just a thought!

---

### Post by SZF2001 on 2007-01-19
Well obviously. :P I'm aware of that. (about the thought provided, not the advice, thanks btw)

There are really a few main reasons why my parents won't make the switch - one is the Shockwave support, they love to play against each other in this "Lingo" game which requires Shockwave. Hopefully GNash will fix this (or already has) - btw, how is Flash support with GNash? Any better or on par with Flash 9?

Another thing is that we have a keystrokker - a thing that records and stores everything typed in to a keyboard all the time. Even though I hate the idea of these things, it's kind of there to see if anyone has been looking up pr0n or whatnot, ya know. So he has some control while not there. Anything like this in Ubuntu?

My dad loves to play Age of Empires, a M$ game, so of course there is no freakin' way in hell I can be able to convert them.

If only they wanted a computer for the basic things like Internet and document typing... ](*,)

---

### Post by K.Mandla on 2007-01-19
Some of my fastest WinXP and Win2K builds were made with custom [nLite]("http://www.nliteos.com/")'d installation discs. If you're keen on making it quick and you don't mind going through the hassle of building and rebuilding and troubleshooting and retroubleshooting ... it's worth it.

---

### Post by slimdog360 on 2007-01-19
type into the run dialog box 'msconfig' and take a look around in that for the programs you dont want to start at startup. Also install ccleaner (the double c was intended).

---

### Post by Furious1 on 2007-01-20
> **irish_flu said:**
> Good point, I just assumed (given the age of the machine) that it's probably Windows 98, Windows ME, or Windows XP (which all have msconfig).

If you have Windows 95, Windows NT4, or Windows 2000 Professional my earlier advice won't work for you.

True but MSCONFIG can be downloaded and work with Win2k for example.  Just do a Google search on MSCONFIG and download it.

---

