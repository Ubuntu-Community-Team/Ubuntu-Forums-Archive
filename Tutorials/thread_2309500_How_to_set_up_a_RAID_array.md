---
title: "How to set up a RAID array"
date: 2016-01-11
forum: Tutorials
---

### Post by Edward_Fish on 2016-01-11
Still figuring out how to use the forums, don't mind me...
Also I'm typing on my phone, and I don't have my Ubuntu PC in front of me. I will follow this up and make corrections.
I'm pretty good at Ubuntu, even though I'm new to the forums. Please bear that in mind.

Ok, so the other day, I wanted to make a RAID 0 array of 2 USB flash drives. Just for fun. The Internet wasn't terribly helpful, but I got it to work in the end. I thought I would share instructions for anyone else interested in creating a RAID too.

You will need:
Common sense
An Ubuntu PC or Mac
2 or more removable drives
Knowledge of what a RAID is
Knowledge of how partitions work and how to manage them
Basic Ubuntu skills
Super-user privileges on the machine
A Plan!

Getting started:
So the first thing to do is gather the drives. (Mine were 8GB each - you will want larger ones.) Ideally they are of similar sizes. Then, read the Wikipedia page about RAID and decide which level to go for. (Level 0 has no backup, level 10 has lots of fallbacks in case something fails.)
Copy/move all the data off the drives. We will be working with partitions and everything on them will be deleted!

Get a shell:
Press Ctrl-Alt-F1 to open a terminal and login to it. (You can get back to the desktop by pressing Ctrl-Alt-F7.)
Or, use Ctrl-Alt-T to get a Terminal window in the GUI.
Type "sudo -s" to get a root shell. If you feel unsafe in a root shell, just put "sudo" before each command.

Identify the drives:
Do "fdisk -l" without the drives connected, then plug them in and run the same command again. Compare the output to identify the drives. Mine were /dev/sdb and /dev/sdc. Make sure to replace these with your own drives!!

Partitioning:
Before you do this, MAKE SURE everything important is off the drive and in a safe place. ALL DATA on the drive will be ERASED PERMANENTLY!!!
Still with me? Here we go...
Unmount the disks. You may be able to use nautilus, otherwise run:
$ umount /dev/sdb
Replace /dev/sdb with the drive name. Repeat for every drive.
Now we've unmounted, we can partition:
$ fdisk /dev/sdb
where /dev/sdb is the name of the first removable drive.
- Create a new partition table by typing "o".
- Create a new partition with "n"
- Select a primary partition with "p"
- Select partition 1 with "1"
- Press enter to select the default value for the start sector.
- Press enter again to select the defualt value for the end sector.
- Hit "t" to change the type.
- Type the code "fd".
- Finally, type "w" to write and exit.
Phew, you did it. Now go back to the start of this step and perform it with every drive you identified before. (/dev/sdb, /dev/sdc, etc.) I'll compact the instructions:
fdisk /dev/???; o; n; p; 1; enter; enter; t; fd; w.
Make sure to NOT wipe the hard drive!!!
Done? Let's move on!

Installing some software:
Hop back to the command prompt and install mdadm.
$ sudo apt-get install mdadm
You might get some popups while installing this. Read them carefully and select the best answer for you.
If it's something about a mail server or whatever, try to get it to go away, I don't think it matters.

Check that it didn't do something weird:
$ fdisk -l
If you see a /dev/md127 or similar entry, then run these commands:
$ mdadm --stop /dev/md127 (or whatever it was)
$ mdadm --zero-superblock /dev/???
Run that last command for every device, replacing /dev/??? with your device.

Make the RAID (finally!):
$ mdadm
Just to check it installed.
Figure out the RAID level you are using, how many drive you have, and their /dev identifiers.
To get help:
$ mdadm --help
or
$ mdadm --create --help
To create the array: (here it comes!)
$ mdadm --create <RAID name> --level=<level> --num-devices=X <device names...>
Replace the slots as necessary. For me it was:
$ mdadm --create /dev/md1 --level=0 --num-devices=2 /dev/sdb /dev/sdc
I recommend you use /dev/md0 or /dev/md1.
Just sit back, relax, and wait for it to do its thing.
The array is now set up! But before you can use it, you still have some more tasks.

Setting up the config file:
sudo mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf
Ah, that was an easy one.

Making a data partition:
$ gparted /dev/md1
(or whatever your array name is)
Oh, so gparted wasn't installed?
$ sudo apt-get install gparted
You should have a nice GUI with a big, black-bordered slice of RAID.
Wipe the array:
- Menu > Devices > Create Partition Table > msdos
Add a partition:
- Menu > Partition > New
- Drag the arrows out so the partition takes up as much space as possible.
- Select a type. I used ext4, but you could pick ext2, fat32, ntfs, etc. Make sure to research the type you choose to make sure it fits your needs!
- Label it. Easy peasy.
- Hit the button with "add" or "create" or whatever.
Wait for it to do its thing, then look at your lovely shiny new partition!
Close gparted and unplug the drives.

Mounting the drives:
Plug them back in again. As soon as they are all in place, you will either get a nice big volume, or nothing will happen.
If you got a nice big volume, pat yourself on the back. Then restart your machine and see if it still works.
If nothing happens:
$ mdadm --assemble /dev/md1
(or the id of the RAID)
Then mount it:
$ mkdir <mount point>
$ mount <raid dev> <mount point>
If you got "bad superblock" or some crud like that, you probably messed up. You can restart and cross your fingers, or do something clever with /etc/fstab to try to fix it, or start over. If it mounted ok, restart your machine to check if it still works.
Enjoy your RAID!!!!!

Did you mess up, or does it just not work? Here's how to get your drives back to normal operation:
$ umount /dev/md1 (use your array name there)
$ mdadm --stop /dev/md1 (use your own name again)
$ mdadm --zero-superblock /dev/??? (insert a single drive name there; repeat for every drive)
Unplug the drives and plug them back in.
$ gparted /dev/sdb /dev/sdc etc... (insert the drive names as before)
Use gparted to repartition the drives.
Unplug the drives, plug them in again, and they should be back to normal.

Thank you very much How To Geek for being awesome (and producing the following webpage!)
[http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/](http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/)
Seriously, without that, I would have no clue.

Questions? Comments? I'm ready. Go ahead and post a reply! (Please don't quote the entirety of this message. Please.)
I hope I helped!

Phew.

---

