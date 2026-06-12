---
title: "accessing storage array drives from LiveCD"
date: 2011-06-22
forum: Server Platforms
---

### Post by rawlins02 on 2011-06-22
I'm trying to delete directories (long story, Mac temp files there, Windows not cooperating) on a sever connected to a HP 20 Modular Smart Array set up as RAID5. System currently running Windows. I've booted from a 9.10 LiveCD but can't see the external drives. Is it correct that I need to install mdadm to "see" those drives from LiveCD?  From a different machine (linux) I can mount the drive using samba like so:

sudo smbmount //IP address/hostname\ RAID5\ Root\ Share /mnt/ntserver -o username=smith,password=abcde123

I have admin privileges on the Windows OS. In linux (or Windows beforehand), is it possible to take ownership of the directories so that I can do a rm -f -r <dir> ?

---

### Post by YesWeCan on 2011-06-22
I can point you in the right direction.
mdadm is for linux software RAID.
Your server will be probably be using Windows "FakeRAID": [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
which requires a different utility called dmraid.
See also: [http://linux.die.net/man/8/dmraid](http://linux.die.net/man/8/dmraid)

Check in the Software Centre whether dmraid is already installed in your live CD session. The command for activating the (all) RAID is sudo dmraid -ay

---

### Post by rawlins02 on 2011-06-22
ubuntu@ubuntu:~$ sudo dmraid -ay
no block devices found

Sorry, but in my original post I did not make clear that the directories/folders are under one user, and I'm another user with admin privileges. Before going further, I should understand if accessing from the LiveCD will allow me to delete the directories. I understand I should be able to take ownership of the files in my Windows admin account. Just hadn't figured out how in my first attempt from Windows.

---

### Post by YesWeCan on 2011-06-22
Oh. I didn't read your post correctly. You are trying to access one of these: [http://h10010.www1.hp.com/wwpc/ca/en/sm/WF05a/12135568-12135820-12135820-12208862-12208862-12312576.html](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF05a/12135568-12135820-12135820-12208862-12208862-12312576.html)

Am am not familiar with this kit. How does it connect to the server? What HW and SW interface does it use?

---

### Post by rawlins02 on 2011-06-22
The specs say storage array has: SATA 1.5Gb/s to Hard Drives; Ultra320 SCSI to Host Servers. The server is HP Proliant DL380 G4 and has a integrated Smart Array 6i Ultra320 Array Controller.  Have to admit this hardware is all new to me as I've only recently been tasked with admin here and everything has been running fine.

Thanks for the help. I've spent the day convincing myself that this hardware has excellent driver and history with running under linux. We've also got an HP 1/8 G2 autoloader for backups. Think it's best to just set this current task aside and take up a fresh install of Ubuntu 10.04 Server Edition LTS. Reformatting the drives and setting up a new RAID5 will be some work, but in the end I'm sure it will be worth the effort. Windoze hasn't been treating me well.

Look for my post on getting linux up on this system in a week or so.

---

### Post by YesWeCan on 2011-06-22
The thing is you say you cannot "see" the external disks when using the live CD. Do you mean they do not show up in 'sudo fdisk -l'? If they do not then there is a chance they won't once you've installed 10.04 either. So tackling the SCSI interface seems the first step. I never use SCSI so I don't think I can help much with this aspect.

This brief article [http://www.zaphu.com/2009/06/17/install-ubuntu-on-a-hp-xw9300-workstation-with-ultra320-scsi-hard-drives-ubuntu-tip/](http://www.zaphu.com/2009/06/17/install-ubuntu-on-a-hp-xw9300-workstation-with-ultra320-scsi-hard-drives-ubuntu-tip/) mentions turning off ACPI which is a boot option on the CD -  via F6 (I think) at the menu.

---

### Post by rawlins02 on 2011-06-22
Did not try fdisk.  I did note a 2000 GB volume using the LiveCD Disk Utility but could not see where in there the user accounts and directories were located. I may try again with fdisk and the Disk Utility tool first thing tomorrow. From what I've read many folks are running linux on this hardware so I'm optimistic the proper software and firmware is out there. 

[http://h18000.www1.hp.com/products/servers/linux/dl380g4-drivers-cert.html](http://h18000.www1.hp.com/products/servers/linux/dl380g4-drivers-cert.html)

---

