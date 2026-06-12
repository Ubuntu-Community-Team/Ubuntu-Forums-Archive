---
title: "Adventures w/ (Windows) Server 2008"
date: 2009-12-07
forum: The Cafe
---

### Post by SmittyJensen on 2009-12-07
I recently got access to a bunch of Microsoft's products (student), and was wanting to try something new. I settled on Server 2008 Enterprise (Enterprise just sounds cooler than Standard :)). Here's my adventure with it:
 
I downloaded the ISO (from a specialized MSDN), and then extracted the files from the ISO onto a folder on my hard disk. I then ran setup.exe, downloaded the updates for the installer, and installed over my existing XP install (renaming Windows to Windows.old). It asked pretty much no questions, except for which edition of Windows I wanted to install and if I really wanted to install the product (you know, the usual).
 
After about 10-15 minutes, I came back to my computer and the installation was finished. On first boot it asked me to make a new password for the "Administrator" user. It had to be a really hard password, as it seems it will only take a password with at least one uppercase letter, one number, and one alpha-numerical character (don't quote me on this).  I logged on afterwards. before I actually got to my desktop it asked me to press CTRL + ALT + DEL (to show the desktop). I still need to turn that off.
 
Upon the initial desktop, it was pretty bare. No audio, no windows media player, no Aero. I quickly installed my graphics card drivers and audio card driver, then I made the Windows Audio service start on boot (it isn't enabled by default, it seems).
 
I rebooted a few times (after installing one driver, then another, etc.). You can enable the "Windows Desktop Experience" feature, which provides Aero and what not. I chose not to -- why should I?
 
Disabled a few things, changed the wallpaper, and am now installing updates. Here's what it looks like so far:
[[IMG]http://img189.imageshack.us/img189/1692/reviewk.th.jpg[/IMG]](http://img189.imageshack.us/i/reviewk.jpg/)
 
 
I'll keep updating my thread to tell everyone how my experience has been. So far, so good. No crashes, freezes, or any real problems. It seems very fast. I don't claim to know it all, so if you see any typos or anything just let me know and I'll correct it.

---

### Post by SmittyJensen on 2009-12-07
I also enabled Superfetch, here's how:
 
> **8. SuperFetch**
As a workstation, enabling SupertFetch will give you that additional bit of responsiveness. The SuperFetch services is disabled by default and when you try to enable it you will most likely get an error message "**The operating system is not presently configured to run this application**" 
You will have to make two registry changes to enable this service. I basically copied them over from my Vista machine.
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management\PrefetchParameters
EnablePrefetcher DWORD 3
EnableSuperfetch DWORD 3
 
 
Courtesy of [http://blogs.msdn.com/vijaysk/archive/2008/02/11/using-windows-server-2008-as-a-super-desktop-os.aspx](http://blogs.msdn.com/vijaysk/archive/2008/02/11/using-windows-server-2008-as-a-super-desktop-os.aspx) .
 
 
Here's how to disable CTRL + ALT + DEL on logon:
 
Start --> Run --> gpedit.msc --> Computer Configuration --> Windows settings --> security settings --> local policies --> security options --> 
[LEFT]Double click Interactive Logon: Do not require CTRL+ALT+DEL and set it to Enabled, then press OK[/LEFT]

---

### Post by dragos240 on 2009-12-07
Tell me if it stays up for more than a month m'kay?

---

### Post by Bachstelze on 2009-12-07
> **dragos240 said:**
> Tell me if it stays up for more than a month m'kay?

Mine has been up for 127 days now. And the reboot was because of a kernel update on the OpenSuse Xen dom0 it lives under.

---

### Post by autonomy on 2009-12-07
> **SmittyJensen said:**
> Here's how to disable CTRL + ALT + DEL on logon
awesome! I'm finishing up a crash course on this. I had it virtualized, but it didn't restore well from backup; so I deleted it. Of course, you'll want to disable the screensaver lock if you haven't already.

---

### Post by SmittyJensen on 2009-12-07
> **Bachstelze said:**
> Mine has been up for 127 days now. And the reboot was because of a kernel update on the OpenSuse Xen dom0 it lives under.
 What he/she said. I'm sure I could keep it up for a long time too but I don't really see a point if I'm not actually on a server.

---

