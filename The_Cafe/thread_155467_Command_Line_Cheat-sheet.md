---
title: "Command Line Cheat-sheet"
date: 2006-04-05
forum: The Cafe
---

### Post by gingermark on 2006-04-05
I'm comfortable with the terminal, but don't remember that many commands. As such I'm planning a little cheatsheet (well, a text file in my home directory) that I can read if things go wrong in the future, and I can't get into a DE.

So far I have:

sudo chown -R username : username /home/username
sudo chmod -R u+w /home/username

sudo nvidia-glx-configure enable

sudo dpkg-reconfigure xorg-xserver

And that's it. I was wondering if there were any other commands that people found especially useful when things aren't working as they should.

Thanks,
gingermark.

---

### Post by trent dillman on 2006-04-05
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm stop

sudo ifdown wlan0
sudo ifup wlan0

sudo apt-get -f install

and my favorite command of all time:

ddate 

:-D

---

### Post by htinn on 2006-04-05
Speaking of references, I just noticed this on digg:

[http://people.debian.org/~debacle/refcard/](http://people.debian.org/~debacle/refcard/)

---

### Post by rado_london on 2006-04-05
pkill 
sudo ifdown eth0
sudo ifup eth0

---

### Post by mstlyevil on 2006-04-05
[QUOTE=htinn]Speaking of references, I just noticed this on digg:

[http://people.debian.org/~debacle/refcard/](http://people.debian.org/~debacle/refcard/)[/QUOTE]

Thanks for the link. I am printing one up today.

---

### Post by basketcase on 2006-04-05
I recieved the message below when trying to access the above link

Access Denied (policy_denied) 

 
Your system policy has denied access to the requested URL.  
 

For assistance, contact your network support team.

---

### Post by curuxz on 2006-04-05
sudo shutdown -h -f -n now

Great for shutting down a pc in a couple of seconds, usefull if you are not willing to wait :)

---

### Post by red_Marvin on 2006-04-05
Maybe just putting the obvious ones here, but they are useful in an cli only environment.

acpi -btas
ls
cat
nano
top
sudo mount -t fstype device moutpoint
cd
cp
rm
mkdir
rmdir
man

---

### Post by SadPrince on 2010-09-07
> **basketcase said:**
> I recieved the message below when trying to access the above link

Access Denied (policy_denied) 

 
Your system policy has denied access to the requested URL.  
 

For assistance, contact your network support team.


talking about this error message, i already got it when i tried to visit Hi5.com
it was working fine couple days ago, By the way.....am not expert in using commands or even using the OS itself, am just beginner .... so bear with me and take me step by step :D
Thanks in advance :)

---

### Post by Legendary_Bibo on 2010-09-07
> **SadPrince said:**
> talking about this error message, i already got it when i tried to visit Hi5.com
it was working fine couple days ago, By the way.....am not expert in using commands or even using the OS itself, am just beginner .... so bear with me and take me step by step :D
Thanks in advance :)

Don't revive 4 year old threads...The necromancy...it scares us!! Burn the witch!!

---

### Post by garvinrick4 on 2010-09-07
```
sudo apt-get upgrade && sudo apt-get upgrade (to fetch upgrades.) 

If you use GUI upgrade tool NEVER use partial upgrades will dork the system for sure. Just wait till they get full packages. Will not happen when use command line just GUI. 

sudo aptitude update && sudo aptitude upgrade 
Will show packages that are outdated if you need space. 

sudo apt-get -f install (fix broken packages) 

sudo apt-get clean (will clean out cache of packages in system) so as to fetch new package from repository. 

sudo update-grub (use everytime you change grub menu) 

sudo grub-mkconfig (will make a new grub config file) 

gksudo gedit to "path"such as /etc/fstab (will open gedit in root 
always use gksudo for opening file system in root from command line.) 

ALT/F2 together type in "gksudo nautilus" and run wiil open file system in root. 

sudo adduser username audio (10.04 update 7-02-10) 

uname -a (show version UBuntu installed) 

aptitude show "package name" (will show if installed and what it does) 

sudo blkid ( show all labels with sdxy numbers 

sudo fdisk -l (Show all partitions by sdxy numbers 

Run fsck (never on mounted drive) like a chkdsk in Windows. 
sudo e2fsck /dev/sdx# 

Start graphic drivers first in boot #540801 launchpad 
sudo -i 
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 

Change permissions media: 
sudo chown -R rick:rick /media/redhat (for example) 
ls -la /media (to give permissions of media) 

Code: 
cd /media 
Then: 
Code: 
sudo chmod a=rwx -R lucid 

aplay -l (audio) 

lspci | grep VGA ( graphics card) 

sudlspci -v | less (Cards & Drivers) 

{Download boot script. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) 
Make sure script is on Desktop. 

Run this and Results of Script will be on Desktop. 
sudo bash ~/Desktop/boot_info_script*.sh } 

Computer info: lshw | less (everything) 

Samba password: sudo smbpasswd -a linuxcss 

grep menuentry /boot/grub/grub.cfg

grub-probe -t device /boot/grub

Best web page grub: 
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202") 

Gparted sites
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)[https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions)[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

sudo mount /dev/sdb1 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sdb

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda


 

 

 

 Reinstall grub2 
sudo mount /dev/sda5/media/maverick 
sudo grub-install --recheck --root-directory=/media/maverick /dev/sda 

If needed run this twice to reinstall grub2 
sudo grub-install --recheck --root-directory=/media/maverick /dev/sda 

Reinstall grub 2 Live CD 
Make a directory: sudo mkdir /media/maverick 

Mount your OS with grub on it: sudo mount /dev/sda5/media/maverick 

Mount mbr on seperate partition if is one: sudo mount /dev/sda1/media/SYSTEM 

Install Grub to sda: sudo grub-install --root-directory=/media/maverick /dev/sda 
Reinstall: sudo grub-install --recheck --root-directory=/media/maverick /dev/sda 

Unmount partition: sudo umount /media/maverick 

Unmount MBR partition: sudo umount /media/SYSTEM 

Get into root in live CD or any OS partition not mounted Linux. 

sudo mkdir /media/lucid (make directory) 
sudo mount /dev/sda2/media/lucid ( mount a drive) 
sudo cp /etc/resolv.conf/ media/lucid/etc.resolv.conf (internet connection) 
sudo chroot /media/lucid (to root) 
apt-get update (If you want to update and upgrade) 
apt-get upgrade 

Are now in root on karmic with internet connection wifi, I believe in wired can pass this step, have to check out. 

Install Windows bootloader with Linux Live CD: 

Restore basic windows boot loader - universe enabled 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Mute Fix: load-module module-device-restore in /etc/pulse/default.pa with #load-module module-device-restore 


XP fix boot 
How to restore the Windows install grub /etc/ XP bootloader For this you will need your Windows install grub /etc/ XP installation CD. Boot into it now. You will get to a part where it asks if you want to repair or recover. To do so, press "r". If prompted, enter your Windows install grub XP administrator password. This will leave you at at a command line, so type in the following two commands: 

Code: fixboot 

Code: fixmbr 

Code: exit 

Vista and 7 fix boot 
How to restore the Windows install grub / Vista or 7 bootloader To restore the Windows install grub bootloader, you must first boot off your Windows install grub Vista/7 installation DVD. If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7. When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer." On the next page, if it finds your Windows install grub Vista/7 installation, make sure it is UNSELECTED before clicking next. Then click on "Command prompt". From there, type in the following: 

Code: bootrec.exe /fixboot 

Code: bootrec.exe /fixmbr 

and click "Restart." 

Install in Ubuntu All 
[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software) 

Suppose you have a source file name src.tar.gz, what you do initially is that you need to extract the source files and then in the terminal&#8230;. 
navigate to the folder where the source file is extracted using the cd commands&#8230;.. and then 
type the following&#8230; 

./configure 

make 

sudo make install 

clean install 

lets see what each one of them does&#8230; 

./configure&#8230;.. checks whether the required dependencies are available on your system or not&#8230;.. if not an error is reported&#8230;. 

make...... compiles the source code and make install is used to install the program in to the location 

if it asks for an installation location it is recommended to install all the source to /usr/src 

clean install...... removes any temporary files created in the installation process of the source and thats it your source file in installed in your system. 

UPGRADE Debian Way && My way and source.list upgrade. 

For command line upgrades run: 

Code: 
sudo aptitude install update-manager-core 
sudo do-release-upgrade -d 

BTW, if you want to upgrade without the tools, I think it is wise to do it the Debian way: 

# Change sources to new release 
perl -p -i.lucid -e 's/lucid/maverick/' /etc/apt/sources.list 

# Start upgrading to new release 
sudo aptitude update 
sudo aptitude install dpkg aptitude apt 
sudo aptitude safe-upgrade 
sudo aptitude full-upgrade 

My Way to UPGRADE Verision: 
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

```

---

### Post by del_diablo on 2010-09-07
Entire 2 pages and no "dmesg", or "htop"?!

---

### Post by garvinrick4 on 2010-09-07
> **del_diablo said:**
> Entire 2 pages and no "dmesg", or "htop"?!
Made list for my brother when I sent him a flash drive to use some time ago. He never
said to much about it. Cost me a 16 gig Centon flash drive so maybe someone else can use it. No flash drive this time.

---

### Post by wkhasintha on 2010-09-07
Here is an excellent book for Linux commands. grab it.

[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download)

---

### Post by chubbtech on 2010-09-16
> **curuxz said:**
> sudo shutdown -h -f -n now

Great for shutting down a pc in a couple of seconds, usefull if you are not willing to wait :)

yeah...like -Halt -F..ing -NOW  8)

---

