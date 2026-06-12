---
title: "VB-Win 7's C drive ... where? / shared folders?"
date: 2013-11-26
forum: Virtualisation
---

### Post by Tom_ZeCat on 2013-11-26
Shared folders the answer?  

I've used Kubuntu 13.x for many months now.  I first set the laptop up as a dual boot with Kubuntu and Windows 7.  However, it became monotonous to reboot every time I needed to run a Windows program, and there were programs that simply would not run under WINE.  

Enter VirtualBox.  I've gotten Windows 7 running under Kubuntu via VB.  I had to troubleshoot some to get my printer and my DVD drive working in Win 7.  I appear to have been successful.  However, getting my thumb drives to work has thus far been hit and miss.  

I store everything on thumb drives.  I have one for my writing, another for research info, and another for my language studies.  Then I have a backup one of each of those that I keep synced up with FreeFileSync.  This worked fine with the dual boot because I would reboot into Windows 7 and then all the same drives would show up.  However, with Win 7 under VB, if I manage to get Win 7 to recognize a thumb drive, then it's no longer available in Kubunutu.  

So I figured maybe I should just save anything I created under Win 7 to the C drive and then copy that over to the thumb drive in Kubuntu.  I wanted to know where the VB/Win 7 drive was.  You can find the WINE C drive easy enough.  I figured there was something similar in VB.  No such luck.  I saved a file named Test Play.fdx on drive C and then went back into Kubuntu and used the Find Files/Folders command, patting myself on the back for my sheer genius detective skills.  Soon the Find program would locate the file and reveal its location to me.  No such luck.  

So what's up?  Is it not possible to see Win 7's C drive from Kubuntu?  Is my best bet to look into this “shared folder” thing?  Would it be better to create and share something on Win 7's C drive or to share something on my Kubuntu hard drive?  My idea is to make it possible to copy back and forth and then in Kubuntu to copy my files over to the thumb drives when needed there.

---

### Post by rackit on 2013-11-26
The c drive is typically stored as a .vdi file in ~/VirtualBox VMs under the machine name. You can't access it as a drive outside of the vm, gernerally speaking. Have a look at [http://is.gd/LK2FOF](http://is.gd/LK2FOF) for a tutorial on connecting USB devices to VMs. I typically share with RW access my entire home directory for easy access to all of my files. It shows up as a mapped drive in the Windows 7 VM under "Computer".

---

### Post by Tom_ZeCat on 2013-11-27
Thanks.  That explanation and the tutorial were both helpful.

---

