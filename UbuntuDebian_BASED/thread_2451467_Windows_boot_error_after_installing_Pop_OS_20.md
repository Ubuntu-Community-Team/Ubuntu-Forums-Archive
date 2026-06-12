---
title: "Windows boot error after installing Pop OS 20"
date: 2020-10-05
forum: Ubuntu/Debian BASED
---

### Post by alvarezjones on 2020-10-05
Hello folks I am new here and to Linux.
A quick rundown on my issue.
I  decided to try out the PopOs distro after some research on the best linux for work productivity and also gaming. I would have also gone for Manjaro.
I created a 3rd partition on my HDD for the Linux. I already  have 2 OS Win 10(makes my system overheat) & 7(awesome OS). Installed Win7 after WIn10.
I used Rufus to burn the PopOs ISO. Then i restarted the system and ran the install. 
I used the partition after making it ext4 format.
After the setup. The PopOS ran perfectly.
I  restarted the system. The grub bootloader came up and I saw only windows 10(on /dev/sda1) and Samsung recovery(on /dev/sda4). I chose the windows 10 but i get a black green with gray error messages. 
I have used boot-repair but it does not work. 
This is my lsblk;
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0   104K  1 loop 
sda      8:0    0 698.7G  0 disk 
&#9500;&#9472;sda1   8:1    0   100M  0 part /media/gamers/SYSTEM
&#9500;&#9472;sda2   8:2    0   408G  0 part /media/gamers/01D694331E7D2810
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9500;&#9472;sda4   8:4    0  23.9G  0 part /media/gamers/SAMSUNG_REC
&#9500;&#9472;sda5   8:5    0    95G  0 part 
&#9500;&#9472;sda6   8:6    0 101.7G  0 part 
&#9492;&#9472;sda7   8:7    0    70G  0 part /
sdb      8:16   1   962M  0 disk 
&#9500;&#9472;sdb1   8:17   1   880M  0 part /media/gamers/Boot-Repair-Disk 64bit
&#9492;&#9472;sdb2   8:18   1   2.4M  0 part 
sr0     11:0    1  1024M  0 rom  






What do I do to get my windows to work. The bootable windows USB is not working as well. 



The boot-repair paste.
[http://paste.ubuntu.com/p/vvYkpnqcR3/](http://paste.ubuntu.com/p/vvYkpnqcR3/)

---

### Post by ActionParsnip on 2020-10-05
Is PopOS! supported here or is it Ubuntu only support? Not sure of the politics here......

PopOS! is definitely supported here
[https://pop-planet.info/forums/](https://pop-planet.info/forums/)

---

### Post by yancek on 2020-10-05
Since you already have boot repair, I would suggest you run it again and select the option to Create BootInfo Summary and post the link you get when it finishes here.  That will give details so that someone will be able to help.

---

### Post by alvarezjones on 2020-10-05
Hello i did that below. But i did it again. This is the link 
[http://paste.ubuntu.com/p/hFVvrnTtpD/]("http://paste.ubuntu.com/p/vvYkpnqcR3/")

---

### Post by alvarezjones on 2020-10-05
> **ActionParsnip said:**
> Is PopOS! supported here or is it Ubuntu only support? Not sure of the politics here......

PopOS! is definitely supported here
[https://pop-planet.info/forums/](https://pop-planet.info/forums/)


Thanks for this but does it matter. If somone can do it then you assist. No politics.

---

### Post by alvarezjones on 2020-10-05
> **yancek said:**
> Since you already have boot repair, I would suggest you run it again and select the option to Create BootInfo Summary and post the link you get when it finishes here.  That will give details so that someone will be able to help.


Hello i did that below. But i did it again. This is the link 
[http://paste.ubuntu.com/p/hFVvrnTtpD/]("http://paste.ubuntu.com/p/vvYkpnqcR3/")

---

### Post by wildmanne39 on 2020-10-05
Moved to Ubuntu/Debian BASED.

---

### Post by alvarezjones on 2020-10-05
> **wildmanne39 said:**
> Moved to Ubuntu/Debian BASED.


Thanks, I have no idea which forum to ask for help. Just following whatever i see online

---

### Post by oldfred on 2020-10-05
I did not know you could install Pop!OS as it uses systemd boot for UEFI booting on gpt partitioned drive.

You have UEFI system, but MBR(msdos) partitioned drive with Windows 7 in a logical partition.
Windows only boots in BIOS mode from MBR.
Windows only boots in UEFI mode from gpt.

Grub only boots working Windows.
And Windows 10 typically turns fast start up back on with updates and then grub cannot boot it. You have to directly boot Windows from BIOS. With UEFI that is easy as it is an option.
But with BIOS, you have to temporarily install a Windows BIOS boot loader to MBR, fix Windows, and restore grub to be able to dual boot.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You will not be able to directly boot your now obsolete Windows 7 from grub, only from Windows 10 BCD menu.

Windows only boots from primary NTFS partition with boot flag or your sda1.
Some have reconfigured a second Windows install in a primary partition to temporarily have boot flag & run repairs to add Windows boot files to that install also.  Then grub sees both Windows installs & can directly boot it. But you cannot repair a Windows in a logical partition to directly boot.

---

### Post by alvarezjones on 2020-10-06
> **oldfred said:**
> I did not know you could install Pop!OS as it uses systemd boot for UEFI booting on gpt partitioned drive.

You have UEFI system, but MBR(msdos) partitioned drive with Windows 7 in a logical partition.
Windows only boots in BIOS mode from MBR.
Windows only boots in UEFI mode from gpt.

Grub only boots working Windows.
And Windows 10 typically turns fast start up back on with updates and then grub cannot boot it. You have to directly boot Windows from BIOS. With UEFI that is easy as it is an option.
But with BIOS, you have to temporarily install a Windows BIOS boot loader to MBR, fix Windows, and restore grub to be able to dual boot.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You will not be able to directly boot your now obsolete Windows 7 from grub, only from Windows 10 BCD menu.

Windows only boots from primary NTFS partition with boot flag or your sda1.
Some have reconfigured a second Windows install in a primary partition to temporarily have boot flag & run repairs to add Windows boot files to that install also.  Then grub sees both Windows installs & can directly boot it. But you cannot repair a Windows in a logical partition to directly boot.


hello Thanks for your reply. But I cannot do the above becvause i can only boot into my popOS using grub. I cannot boot into windows. So all the provided links were all about using fast start and hibernation Windows commands via windows command prompt.

---

### Post by oldfred on 2020-10-06
With UEFI, you can directly boot Windows from UEFI boot menu.
Grub only boots working Windows and you need to then diretly boot Windows.

With BIOS, you then have to use your Windows repair flash drive to temporaily install the Windows boot loader to MBR, boot Windows, fix Windows, and then restore grub, so you can dual boot.
Note that Windows will keep turning fast start up on. Or Windows 10 is not particularly easy to dual boot in the now 35 year old BIOS/MBR configuration. Just be sure to always have your Windows repair disk and Ubuntu live installer and know how to add Boot-Repair or do manual grub reinstall.

Boot-Repair may offer to install Windows type boot loader to MBR, syslinux or you may be able to force install. But if Windows fast start up on, it just may not see the NTFS partition to know you need a Windows type boot loader.

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by alvarezjones on 2020-10-15
[LIST]
[*][#4]("https://pop-planet.info/forums/threads/windows-10-boot-error-via-grub-after-installing-pop-os-20-solved.1050/post-4912")
[/LIST]
[COLOR=#1F1F1F][FONT=&quot]I have solved the issue.

I used boot-repair.
went to advanced options
went to reinstall MBR and repair windows files
chose the windows recovery sda as the default boot, restarted then
chose the windows 7 partition as the default boot. restarted then
chose the windows 10 partition as the default boot.
restarted it.
And signed into my windows 10.

Then deleted the popOS partition for future reinstallation.

[/FONT][/COLOR]

---

