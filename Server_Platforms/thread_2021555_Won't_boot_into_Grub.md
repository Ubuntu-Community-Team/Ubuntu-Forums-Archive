---
title: "Won't boot into Grub"
date: 2012-07-09
forum: Server Platforms
---

### Post by Twinnie on 2012-07-09
Hi guys, sorry if this is in the wrong forum but I wasn't sure where to put it and it is an issue with Server so I figured I'd leave it here.

I've installed Ubuntu Server onto an old laptop that I was going to stick behind the TV and use as a little NAS box (I know I could use something like FreeNAS but this is also something of a learning experience for me) and it all works fine except for the fact that it won't boot from the HD, it just skips the drive and moves onto the next item in the boot order. It works aright if I boot from the CD and use Grub on there to "Boot the first hard drive" but that's not a lot of good if I want to reboot remotely.

Boot sectors are a bit of a mystery for me and every other article I've read like this says to use stuff like boot-repair to reinstall Grub but none of that's worked for me and a lot of it's GUI based. Are there any other tools or am I missing something. I definitely chose to install Grub (I also format the disk with the LVM, dunno if I should have) and I've installed Server a few times before with no problem.

Any suggestions appreciated. Thanks.

---

### Post by oldfred on 2012-07-09
I think Boot_repair should still work, but you can directly down load the bootinfoscript to show how the system is configured.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Server is not a liveCD, so you still have to download and use a liveCD with a gui for repairs. 
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Twinnie on 2012-07-09
Thanks.

I've used the LiveCD to run boot-repair and used it to run Boot Info Script (I'm assuming it's the same thing, I can run the script if it's necessary), and it gave me this:
[http://paste.ubuntu.com/1083170/](http://paste.ubuntu.com/1083170/)

Does this have any clues in it?

---

### Post by oldfred on 2012-07-09
I do not know lvm. I know many with servers suggest it as it allows repartitioning on the fly, but it adds  a level of complexity. Since it is a smaller drive, is there some reason for LVM?

I thought Boot-Repair automatically added the lvm2 driver as liveCD does not have that normally.

Script seemed to have trouble mounting lvm partition, not sure if driver missing or issue, but grub2 looks like it is installed ok, and uses /boot partition to boot. When you boot you should get grub menu. I do not see anything wrong.

---

### Post by Twinnie on 2012-07-09
I think whenever I've installed Server before I haven't bothered with it but since it's the default option and this was a learning experience I thought I'd give it a go. I guess I've learnt something. I'll reinstall without it and see what happens.

Thanks, I'll report back with results.

*Update*

Didn't work. I zeroed the drive before I reinstalled and when I select the "Boot from first drive" option it briefly shows the Grub install from the drive as it would normally before booting the default option. Would it help if I ran Boot Info again? Is there something about the laptop that might be causing this? When I started Boot-Repair last time it complained about RAID being enabled but I seriously doubt the laptop's capable of RAID as it's that crap and there's nothing in the BIOS about it.

---

### Post by YannBuntu on 2012-07-10
Hello

- Boot-Repair automatically tries to enable RAID in case there is one. You can ignore messages about it.
- Boot-Repair successfully activated LVM:

```
VGSCAN
File descriptor 10 (/proc/12728/mounts) leaked on vgscan invocation. Parent PID 12735: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "NAS" using metadata type lvm2
VGCHANGE
File descriptor 10 (/proc/12728/mounts) leaked on vgchange invocation. Parent PID 12735: /bin/bash
2 logical volume(s) in volume group "NAS" now active
File descriptor 10 (/proc/12728/mounts) leaked on lvscan invocation. Parent PID 12735: /bin/bash
LVSCAN:
ACTIVE            '/dev/NAS/root' [73.30 GiB] inherit
ACTIVE            '/dev/NAS/swap_1' [1016.00 MiB] inherit
```

I don't see any error in the log, and the OS is correctly detected in the LVM:

Please run Boot-Repair, update it, click "Advanced options", go to the "Other options" tab, select "Place the boot flag on: **sda1**" option, apply.

---

