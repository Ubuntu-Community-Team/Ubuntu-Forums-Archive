---
title: "Jaunty x64 Host, WinXP x64 Guest, Slow VBox. Samba?"
date: 2009-08-10
forum: Virtualisation
---

### Post by raywood on 2009-08-10
I have been using VMware Workstation 6.5.2 and Player to run WinXP virtual machines on 64-bit Ubuntu 9.04 (Jaunty Jackalope).  VMware became [erratic on audio playback]("http://raywoodcockslatest.blogspot.com/2009/08/ubuntu-904-vmware-workstation-652.html"), so I decided to try using VirtualBox.

As in VMware, I have used the built-in Shared Folders approach to enable VBox to access my WinXP NTFS partitions.  Unfortunately, VBox is extremely slow in operations involving those shares.  For instance, file-moving operations on the NTFS partitions can take minutes rather than seconds.

I have seen some posts that say Samba provides a faster way to give a VBox VM access to shared partitions.  I am not familiar with Samba, though, and my attempts to use it have not worked so far.

My questions:  (1) Could someone provide or point me toward a simple guide for setting up Samba shares?  (2) Is there some better way?

Thanks ...

---

### Post by arch0njw on 2009-08-11
Have you tried this guide on Samba?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Ultimately, it is pretty easy, but there always seems to be a few gotchas.  One trick with windows is that it is always running around pantsless... by that I mean file sharing is usually turned on.  You can check by trying the following from your Ubuntu machine.

1) open nautilus
2) in the address bar type: smb://*your-win-xp-machine-name*/c$

You should get a login box.

If that doesn't work, you might need to enable "Simple File Sharing" on the XP VM.  That way, you can at least do a push from Ubuntu to XP (or pull from).  You can then work on getting Samba working under Ubuntu at your leisure.

---

### Post by raywood on 2009-08-11
I did see that Samba guide.  Thanks.  It was kind of intimidating.

For the moment, I'm back to using VMware.  Next time I get an opening to tinker, I'll try again with VirtualBox.

---

### Post by arch0njw on 2009-08-11
Samaba can be intimidating.  I use Kubuntu, and I really should get Ubuntu installed in a VM so I can walk through this.  As I recall, there is a nice interface to configure what directories are shared, how they should be shared, and who they can be accessed by.  I believe there is even a checkbox to indicate if users will authenticate with their existing system passwords, or if you want to generate a samba-specific password for them.

I can usually get samba up and running in about 20 minutes.  It looks ugly, but that's because it has a lot of extra features that most folks don't use.

---

### Post by arch0njw on 2009-08-11
There is also this guide.
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

The one thing I don't like about that is it doesn't have a map to your user folder (e.g., /home/*your-user-name*).  That guide assumes a common shared directory.  However, it would work.

---

### Post by raywood on 2009-08-11
If I give Samba another whirl, I'll try working through that guide.  If it works, great.  If not, I'm looking at that thread.  It runs on for 83 pages.  I'm thinking that's me, that poor schmuck who's still trying to get it working after 83 pages.

I wouldn't have started with VirtualBox if I hadn't been having audio problems in VMware.  I'm not sure why those problems went away, or for how long.  Virtualization is great, except when it's not.

---

### Post by arch0njw on 2009-08-11
> **raywood said:**
> If I give Samba another whirl, I'll try working through that guide.  If it works, great.  If not, I'm looking at that thread.  It runs on for 83 pages.  I'm thinking that's me, that poor schmuck who's still trying to get it working after 83 pages.

I wouldn't have started with VirtualBox if I hadn't been having audio problems in VMware.  I'm not sure why those problems went away, or for how long.  Virtualization is great, except when it's not.

Oh, I hear ya.  I've had to sort out a few problems with that.  Wonky keyboards, no sound, glitchy graphics (cure was to **remove** vmware-tools...!), and more.  I enjoy VMs, but they can be testy at times.  I wish I knew more about it so I could talk less about it like it was voodoo.

---

