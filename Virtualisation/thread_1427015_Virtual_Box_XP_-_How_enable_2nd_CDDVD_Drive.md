---
title: "Virtual Box XP - How enable 2nd CD/DVD Drive?"
date: 2010-03-11
forum: Virtualisation
---

### Post by FredVanH on 2010-03-11
Hi.  I just installed VirtualBox 3.1.4 in Ubuntu 9.10 and installed XP as a guest.  Upon invoking VirtualBox and before the XP install, I was able to specify 1 of my 2 CD/DVD-RW drives as connected to VB;  but not the second one.

Now in XP Windows Explorer the file tree shows the first but not the second.

On the bottom right of the VB window are a bunch of icons which stand for the connected devices.  When I right-click on the CD-looking icon, which says it's for the IDE Controller controlling the CD/DVD Drives, it shows the first drive checked and the second not checked.  When I check-mark the second, the checkmark goes away from the first.

Is there a way to enable both CD/DVD drives in the guest at the same time?
Thanks,
Fred

---

### Post by Hero of Time on 2010-03-11
With the latest version (3.1.0 and above), you can have more than one optical drive for the VM. Simply shut down the VM, open it's settings and add it on the Storage section.

---

### Post by FredVanH on 2010-03-11
Thanks, Hero, for your helpful response.  I did it and it looked promising - Under Settings's IDE Controller, where the virtual HDD was its primary Master and the 1st CD was its Secondary Master, by right clicking the IDE Controller I was able to add the second CD drive as its Primary Slave.

However, after starting the guest XP, Windows Explorer and MyComputer no longer show the first CD Drive and also do not show the second.

In the bunch of icons on the bottom right of the VB window, mentioned in my previous post, now when I right-click on the CD-looking icon it shows both cd/dvd drives checked as it looks like they should be - nevertheless I can't get 'em to work in the XP, even after a bunch of rebooting XP and Ubuntu.

Any ideas?
Thanks,
Fred

---

### Post by FredVanH on 2010-03-13
Some time after sending the above email, I tried uninstalling & reinstalling Virtual Box, attaching the CD/DVD drives again in the manner I stated above, and installing XP - no change - they were still not recognized.

As a last resort, I reinstalled Ubuntu 9.10, downloaded and installed Virtual Box PUEL 3.1.4, invoked Virtual Box and again tweaked the Storage "Settings" to enable the CD drives.

At first, I got cute and switched the master-slave relationships to what I thought would make more sense than what I had set up before.  I made them:
Primary Master:      Hard Drive
Primary Slave:        Unused
Secondary Master:  CD/DVD Drive 1
Secondary Slave:    CD/DVD Drive 2
When I then Started the virtual XP machine preparatory to installing XP, it would not boot and said no boot media, even though I pushed F12 in the VB window and picked all of the boot options one-by-one, including "CD".

So I went back and changed the relationships to:
Primary Master:      Hard Drive
Primary Slave:        CD/DVD Drive 1
Secondary Master:  CD/DVD Drive 2
Secondary Slave:    Unused
, which were the ones I had originally used based on the generic suggestion and my stumbling into it.
This time the virtual machine booted, I installed XP and XP updates;  and 5 hours later I had a good XP installation which now included the 2 CD/DVD drives.

So - Hero's suggestion was a good one;  but I had apparently screwed something up in the machinations surrounding the problem and needed to go way back to a reinstall of Ubuntu.  Who said (my) superstition is invalid?  Thanks again, Hero!

BTW, I still cannot get the first DVD drive to open manually or eject from any XP program, including Explorer;  but who's counting?  I found the workaround - get out of Virtual Box and eject/open it in Ubuntus's "Places";  then go back into VB's XP.

---

