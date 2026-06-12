---
title: "Improve mouse capturing using rdesktop?"
date: 2010-10-06
forum: Virtualisation
---

### Post by Jesse B on 2010-10-06
I've got multiple virtual machines running on my headless server (running Ubuntu Server 10.04.1), and I've been accessing them via rdesktop, which has been working just fine.  However, I am having issues with mouse capturing in the virtual machines.  It does work, but not well.  The cursors do not line up, and moving the mouse very quickly will cause the virtual cursor to move at an alarming rate relative to my actual cursor.  Is there anything I can do to improve this, or do I have to put up with it?  I was wanting to run a virtual machine to do some of my AutoCAD work (just basic 2D drawings mostly), but I won't be able to do so under these conditions.

Thanks,


- Jesse

---

### Post by HermanAB on 2010-10-08
Howdy,

Install VMware Tools on the Windoze VM.

---

### Post by Jesse B on 2010-10-09
> **HermanAB said:**
> Howdy,

Install VMware Tools on the Windoze VM.

I'm not sure if this makes any difference, but I'm running VirtualBox.  Does it matter, or will the VMWare tools work with pretty much any virtualization software?

Thanks,


- Jesse

---

### Post by HermanAB on 2010-10-10
Virtualbox is the same idea as VMware, but different.  You got to find and install the 'virtualbox tools' in WinXP.  Some googling will get you going - I don't use virtualbox so I cannot give you specifics.

---

### Post by Jesse B on 2010-10-10
> **HermanAB said:**
> Virtualbox is the same idea as VMware, but different.  You got to find and install the 'virtualbox tools' in WinXP.  Some googling will get you going - I don't use virtualbox so I cannot give you specifics.

Ahh, gotcha.  Alright, thank you very much!  I think it's Guest Additions or something to that effect, but I'll just take your advice and Google it ;)

Thanks,


- Jesse

---

### Post by Jesse B on 2010-10-12
Alright, just got home last night.  Installed the Windows 7 guest additions, works like a charm!  Was a bit of a pain in the *** to do on a headless server, but I got it done.  Thanks!

---

