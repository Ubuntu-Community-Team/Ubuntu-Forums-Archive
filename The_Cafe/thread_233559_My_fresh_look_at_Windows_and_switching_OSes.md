---
title: "My fresh look at Windows and switching OSes"
date: 2006-08-10
forum: The Cafe
---

### Post by hizaguchi on 2006-08-10
I got rid of my Windows partition a long time ago, but my new laptop came with an XP license and I wanted to run SolidWorks at home, so I've been giving the OS another try lately.  I wanted the full experience, so I reinstalled from scratch and set everything up myself, just like I would with Ubuntu.  The experience has made a few impressions on me.

First off, Windows is annoying!  There's a pop-up message in the task bar every time either of my network cards can't get a connection.  I finally got that disabled and noticed the pop-ups from the Windows security monitor complaining that I didn't have antivirus (I guess Clam doesn't count?) and that I didn't have automatic updates enabled.  I got it to shut up about the antivirus, but I had to turn on updates to stop the other message.  Now instead of complaints, I get persistent "Windows will now restart to finish installing your updates" windows every few days.  I click "restart later" and they just go away for about 15 minutes and then pop back up.  I'm afraid to leave my computer unattended without saving whatever I'm working on because who knows what'll happen if I don't catch the reboot screen in time.  And the final annoyance is networking.  About half the time, if I take my computer to work and connect to their wireless network and then bring it home, it can't connect to my wireless network without rebooting first.  This is amazingly frustrating, and because I don't know of any manual command line tools to manage the wireless card, I have no idea how to troubleshoot the problem other than to click "Repair this connection", which doesn't work.

Also, installing Windows is by no means easier than installing Linux or FreeBSD.  The actual installation process is far less descriptive, and then the following scavenger hunt for hardware drivers is mind boggling.  I had to get 3rd party drivers for my touchpad, video card, sound card, wireless card, processor, camera, card reader, and USB ports.  On top of this, it took me several hours to get the base Windows install to behave the way I wanted (it didn't even suspend when I closed the lid), and 2 days to find, download, and install enough software to fill most of the roles that my Linux desktop previously handled.

Despite all of this, though, I'm finding it difficult to start to install FreeBSD like I had planned today.  I think it is because all of the work I've put into getting my Windows to behave acceptably well and to not be repulsively ugly makes me feel more attached to the OS.  I want to do a dual boot and just hibernate both OSes so I can switch back and forth fairly quickly, but it feels like all that Windows work would be wasted if I only used it for SolidWorks.  It also has me in the mindset that manipulating my computer is a painful and frustrating experience... something that is only true for this particular OS... and that feeling makes me (illogically) dread installing yet another OS, even though I know I can configure a KDE desktop to my liking in about an hour.

So I think I have discovered for myself a huge part of the reason people are reluctant to switch to a new OS.  It isn't because Linux is hard to install/configure/use.  It is because Windows is hard to install, configure, and use, and once you've been through all of that it is really hard to get excited about installing an operating system.

---

### Post by prizrak on 2006-08-10
On half of my Windows installs I have given up about halfway into it and rebooted into a Linux install disk :)

---

### Post by skirkpatrick on 2006-08-10
Windows has always had a problem with requiring you to reboot when you switch networks.  To get full access between work and home, I have to change my Workgroup name and in Windows, that requires a reboot and not just restarting a daemon.

As for Automatic Updates, go to Control Panel then Security Center then click on Automatic Updates at the bottom where it says "Manage security settings for:".  You can then change how you want updates to be handled.  The only problem is that if you don't pick what Microsoft "recommends", you will sometimes get the annoying yellow shield in the system tray.

---

### Post by aeiah on 2006-08-10
linux took me a lot longer to customise to how i wanted the first time i installed it compared to windows. the most recent time i installed it, the day after dapper was released, it took about the same time as win xp did to get things the way i wanted (not including compiz).

but i dont think its really the installation people balk at. its the fact that they dont care enough to learn a new OS. they really dont give a shit that they have to update their anti virus every few days, run scans, accept proprietary EULAs etc.

but i certainly agree that from my perspective at least, having customised ubuntu to just the way i want it, i have become more attatched to it, despite it not particularly doing anything that much better than win xp does

---

### Post by xtacocorex on 2006-08-10
> **skirkpatrick said:**
> Windows has always had a problem with requiring you to reboot when you switch networks.  To get full access between work and home, I have to change my Workgroup name and in Windows, that requires a reboot and not just restarting a daemon.

If you just need to change the IP and not the workgroup the following should work in the Windows command line:
```

ipconfig /release
ipconfig /renew

``` and that should take care of the reboot.

---

### Post by G Morgan on 2006-08-10
It is possible to get rid of the update notifications without turning on automatic updates. When you get the security center theres an option which says 'Change the way security center notifies me' on the left which allows you to stop nagware for updates.

Automatic updates are insane given their tendancy to sneak things in.

---

### Post by RAV TUX on 2006-08-10
> **G Morgan said:**
> It is possible to get rid of the update notifications without turning on automatic updates. When you get the security center theres an option which says 'Change the way security center notifies me' on the left which allows you to stop nagware for updates.

Automatic updates are insane given their tendancy to sneak things in.

I'm not a windows expert but you should be able to disable those. I've done it but don't ask me how, I don't remember.

---

