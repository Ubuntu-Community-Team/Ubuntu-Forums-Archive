---
title: "grub failed install please help"
date: 2017-02-16
forum: Ubuntu/Debian BASED
---

### Post by elamrai.13 on 2017-02-16
I have downloaded iso kalli linux. OK
I have created a USB bootable l help Rufus; OK
I have allows the safety boot .ok
I have change the boot order, key first. OK
I have a HP probook 5320 m 4 GB RAM, trial i5, 320 DD
I have partitions the hard drive on two 150 GB for windows on the windows session and 150 GB appoints D.free for linux kali, j I formate partition D on windows (manage disks), after that j have starts the installation linux everything is ok .the language, keyboard, network, until the failed grub installation
After I took tutorials. Ko  I have downloaded also repair  boot but after installing I do not know how I open and click tip auto  repair i have removable usb 8 GB apartI m a new user to linuxm i have a connexion with wifi and i lunch  linux kali live with usb bootable is good , iso after this step i  encountred this message for repair grub failed install 
```
 root@kali:~# mount /dev/sda5 /mnt
mount: /dev/sda5 is already mounted or /mnt busy
       /dev/sda5 is already mounted on /media/root/f77dc759-6c9e-46fe-9a1c-d9330d71fd98
       /dev/sda5 is already mounted on /mnt
root@kali:~# mount –bind /dev /mnt/dev
root@kali:~# mount –bind /dev/pts /mnt/dev/pts
root@kali:~# mount –bind /proc /mnt/proc
root@kali:~# mount –bind /sys /mnt/sys
root@kali:~# chroot /mnt
root@kali:/# grub-install /dev/sda
bash: grub-install: command not found
root@kali:/# update-grub
bash: update-grub: command not found
root@kali:/# exit
exit
root@kali:~# os-prober
/dev/sda1:Windows 8 (loader):Windows:chain
/dev/sda5:Kali GNU/Linux Rolling (kali-rolling):Kali:linux
root@kali:~# update-grub
bash: update-grub: command not found
root@kali:~# 
```
 if you have any idea or solution please help me

---

### Post by wildmanne39 on 2017-02-16
*Thread moved to **Ubuntu/Debian BASED**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by elamrai.13 on 2017-02-16
OK thanks c is the first time that I post a problem

---

### Post by yancek on 2017-02-16
> I formate partition D on windows (manage disks),

Most likely the first problem as you will need a Linux filesystem and a standard windows install is not only not capable of formatting with a Linux filesystem but cannot read them.
You would need to format with a Linux filesystem which can be done during the install.  Did you do that?
Which version of windows do you have installed?  Are you using UEFI/GPT or the older MBR?

If your windows is prior to windows 8 and using MBR, the tutorial at the link below at the Kali site should be good.

 [http://docs.kali.org/installation/kali-linux-hard-disk-install](http://docs.kali.org/installation/kali-linux-hard-disk-install)

The link below has all kinds of documentation on different install of Kali installs as well as it's purpose and who should or shoult not use it.  If you are planning to use it to learn penetration testing, there are instructions for installing to a usb on that page which might be simpler.

[URL="http://docs.kali.org/"]http://docs.kali.org/




[/URL]

---

### Post by elamrai.13 on 2017-02-19
Thanks for the first response, I am a Microsoft technician, and I want to change the OS to linux,
This is the concern I have:
I formatted the machine in windows 7 pro, I installed it on the partition of 320GB (because I have a single partition)
Windows 7 has been properly installed.
Now i want to know is what if i create a bootable key that contains liux-kali 2016, is what i will have the same error message grub failed install into the target. ?
Or do I have to create a blank partition only for liux (ie have two partitions, one for windows 7 that contains 160GB and the second free 150GB for linux)?
If yes, do I have to select all the folders in a single partition and let linux handle the second partition automatically?
Or I have to format the second 150 GB partition in GPT or with another software?
Otherwise I can keep only one partition that contains windows 7 afterwards
Install linux on the same session?
Thanks for helping me to install linux in dual boot with windows 7, i am interested in this system and thanks

---

### Post by oldfred on 2017-02-19
How was drive partitioned originally? gpt or MBR?

The Windows 7 installer on DVD is BIOS only and it converts a gpt drive to MBR, incorrectly. It leaves the backup gpt partition table.
Then most Linux tools get confused as you have a primary MBR and gpt backup. (MBR has no backup).

You can either reinstall Windows 7 in UEFI mode to gpt drive. But have to copy to flash drive and move some files around to make it UEFI bootable.
UEFI boots from /EFI/Boot/bootx64.efi, so you create that using a Window boot file.

Or you can remove the backup gpt partition table with fixparts. Then be sure to only boot in BIOS mode.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by elamrai.13 on 2017-02-19
Thanks for the answer I have a single partition on my PC of 320 GB e MBR UEFI , order bios is on the usb key. The widows 7 is installed now on the partition 320GB,
I start kali-linux on the boot-able USB key then I run live mode liux and I open the terminal to type this command: sudo fixparts / dev / sda
Then i can started installing linux (which is on a bootable key)
On the same partition of windows 320Go to have a dual boot? Or I create a new free partition only for linux of 150G NTFS and when the installux inux will handle the grub to not have the error grub failed to install package ?

---

### Post by yancek on 2017-02-19
In windows 7, use the Disk Management tool to resize/shrink the 320GB partition and leave free/unallocated space on which to install Kali Linux.  You will need to format the partition on which you want to install Kali from the Kali installer as windows systems are not capable of doing that. 

You haven't answered whether your windows 7 is the default MBR or whether you have a UEFI system.

---

### Post by elamrai.13 on 2017-02-24
:DThank you very much for your answers, your support for an agent who just use linux, it's nice to have this community.
My concern has been resolved I do exactly,.
1 - the disk partitioning hard on two (C: for windows, and the second partition is for linux empty, unallocated to 150 GB.)
2. then put iso liux on a USB stick 8 GB of space.
3. change from the bios boot order to boot on the key
4. start graphical installation
NB: at the end of the installation I chose no to mirror network and I met concern grub failed install
I restarted the installation and I chose yes mirror network, and here it works
now the boot loader grub is installed and I have a choice between windows 7 and liux kali is what I'm looking for, thank you thank you very much for your help.
the problem is resolved, marked the resolved because I do not know commenent do
-just last question: useful link to start to learn liux kali please well detailed for a beginner?

---

### Post by #&amp;thj^% on 2017-02-24
> **elamrai.13 said:**
> 
-just last question: useful link to start to learn liux kali please well detailed for a beginner?
The four best ways (in my opinion) to learn and understand Kali better is to -

1. Use it and experiment with it in a virtual machine. ([http://www.linux.org/threads/an-introduction-to-oracles-virtual-box-vbox.5018/](http://www.linux.org/threads/an-introduction-to-oracles-virtual-box-vbox.5018/))

2. Read and ask questions on Linux and kali forums: 

3. Read Kali's documentation. ([http://www.kali.org/official-documentation/](http://www.kali.org/official-documentation/))

4. Watch videos. ([https://www.youtube.com/user/kalilinux](https://www.youtube.com/user/kalilinux))
A good Start [([https://www.quora.com/What-is-the-best-way-to-learn-Kali-Linux](https://www.quora.com/What-is-the-best-way-to-learn-Kali-Linux))]("https://www.quora.com/What-is-the-best-way-to-learn-Kali-Linux")

tutorials to start learning hacking with Kali Linux ([https://www.techworm.net/2016/11/top-10-best-tutorials-start-learning-hacking-kali-linux.html)]("https://www.techworm.net/2016/11/top-10-best-tutorials-start-learning-hacking-kali-linux.html")
Just remember With Great Power comes Great Responsibility.;)
And This also is a good read: ( [https://www.techworm.net/2016/11/top-10-best-tutorials-start-learning-hacking-kali-linux.html)]("https://www.techworm.net/2016/11/top-10-best-tutorials-start-learning-hacking-kali-linux.html")

---

### Post by elamrai.13 on 2017-02-24
thank u bro for your help,

---

