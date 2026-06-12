---
title: "Repeating &quot;GRUB Loading stage 1.5.&quot;"
date: 2006-09-05
forum: Server Platforms
---

### Post by timelord726 on 2006-09-05
Hi everyone,

I just bought a brand new 64-bit server with no OS preinstalled intending to load it with Ubuntu Server 6.06.  The server is a Visionman Advantage 6422 Server, and its specs are as follows:

AMD Athlon 64 3500+ processor with 1MB Cache
1GB DDR400 memory
Dual 160GB SATA-II HDDs with hardware RAID 0 and 1
Gigabit LAN
Sony CD-ROM

I configured the hardware RAID so that the two drives were mirrored, then installed Ubuntu Server onto the first drive.  The install completed successfully, but upon rebooting the server, I get a stream of repeating messages that looks like this:

GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.
GRUB Loading stage 1.5.

It continues to flood the screen until I turn the machine off with the power switch.  Does anyone have any idea what could be causing this?  Could it possibly be something to do with the RAID configuration?  I'm not really sure what to do.  Any help would be appreciated!  Thank you!

---

### Post by Glut on 2006-09-06
Sounds like you have a boot record issue. I'm assuming that you've installed RAID 1, rather than RAID 0+1 or 1+0, because that would require 4 drives. I'm not sure if the current installer correctly installs grub on both boot partitions, but the old one didn't so you needed to setup both or you would need to do a boot record rescue if one of the disks failed (of course if you're running RAID 0 and one of the disks fails, you needn't care about any rescue) 

Assuming RAID 1, you will need to boot either off a live disk or a rescue disk and install grub to both partitions. Boot up, go to terminal and do the following, which I've copied from: [http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)

6. Setting up GRUB: (assuming you've already installed it)
------------------------------------------------------------------
# grub
grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0xfd

grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are
embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p
(hd0,0)/boot/grub/stage2 /boot/grub/grub.conf"... succeeded
Done.

grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0xfd

grub> setup (hd1) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are
embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p
(hd1,0)/boot/grub/stage2 /boot/grub/grub.conf"... succeeded
Done.

grub> quit

---

### Post by timelord726 on 2006-09-06
Hi Glut!  Thanks for your response.

I did as you suggested and installed GRUB to both drives.  The problem has changed, which I assume is a sign of progress.  Now instead of endless lines of "GRUB Loading stage 1.5." I instead receive a single line that says "GRUB Loading stage2.." and then the system just stops.  A flashing cursor appears beneath the GRUB message and the system won't boot.  Still, though, at least it's not doing what it was before, right?

Any other suggestions?  I appreciate the help!

---

### Post by Glut on 2006-09-06
Grub stage 2 generally gives an error or dumps you at the grub prompt if it can't load. Given that it hasn't, my guess is that you have file system corruption - something may have gone wrong in the install. A quick search reveals that this can happen on old machines with console redirection enabled in bios, but given your specs I'd be surprised if this were the case: [http://www.askbjoernhansen.com/2004/11/19/grub_stage2_loa.html](http://www.askbjoernhansen.com/2004/11/19/grub_stage2_loa.html)

---

### Post by timelord726 on 2006-09-10
I don't think this is the case.  Let me ask another question -- if I have configured hardware RAID to mirror the drives, should I see both drives in the Ubuntu installer?  I can see both drives even with hardware RAID configured and my dad seems to think that's wrong, and that with hardware RAID it should only show up as one drive.  The Windows Server 2003 installer does only show one drive, but I certainly have no desire to turn this brand new server into a Windows one.  Can someone tell me why I can't seem to get my RAID-configured server to boot Linux once it's installed?

---

