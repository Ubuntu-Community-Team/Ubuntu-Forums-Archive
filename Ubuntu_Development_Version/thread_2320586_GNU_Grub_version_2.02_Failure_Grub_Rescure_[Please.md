---
title: "GNU Grub version 2.02 Failure Grub Rescure [Please Help]"
date: 2016-04-15
forum: Ubuntu Development Version
---

### Post by Rajesh_Pratap on 2016-04-15
Hello,

I Had a Dual Booted PC Which  had a Debian linux and Windows 8.1 since 4 Months it  was Running Fine as a Normal PC, But Unfortunately, today i ran into a  Error while opening the PC Next Time, When my PC Started i got an a  Black Screen which said  

Error : file "/grub/i386-pc/normal.mod" Not Found and a Terminal Like Thing which was Written as 
grub-rescue>


  I did a Bit Extensive Research and wrote some commands like


  grub-rescue> ls (hd0,5)/ 
grub-rescue> set root = (hd0,5)/ 
grub-rescue> set prefix =(hd0,5)/usr/lib/grub/ 
grub-rescue> insmod normal 
grub-resuce> normal



  Then it Loaded a Bit and presented me to Another Black Screen which  prints `GNU Grub Version 2.02 Minimal Bash like Editing is Supported...

  grub>


  Now, What i Would Like to tell is i did a 
grub> ls (hd0,5)/



  Which Prints out lost+found/ etc/ media/ dev/ lib/ lib64/ live-build/ mnt/ opt/ proc/ root/ run/ sbin/ sys/ srv/ tmp/ usr/ var/ vmlinuz lib32/



  What i Did Next is Wrote the command


  grub> ls (hd0,5)/root/Desktop



  Which Presented me The Files Which were Present in my Linux ! A Relief sign indeed, which means My Data hasn't been lost

  Than i Tried to Find out My Windows booted Sector by 

grub> ls (hd0,3)/



  Than it listed me all the files Present in C:\ Folder which were there in Windows 8.1 , So that means the Data of My Windows Sector hasnt been Lost.
  But, After Reaching upto this, i am Confused what to Do Next, How do i  Bring my OS Back in Graphics, currently i just see Dark screen with  grub> written . 
I am Bit tensed as well as Confused.  Now i am Clueless Ahead that How to get GUI Version of OS Back, i can only see cli of grub> currently


  Questions: 
**1) How do i restore my Old graphical GUI OS back along with GRUB**

  [B]2) How do i Save the Data , i dont want to lose data ( Because the Data seems to be in there, and i dont want to lose it by Typing any Risky Commands)


[/B]

  Please Help , if you need any More Information apart from these, kindly Comment below. Thank you

---

### Post by izznogooood on 2016-04-15
I would download the Ubuntu ISO and boot this. Try using the boot menu to boot existing system, then run:

```
sudo update-grub 
```

Se if this fixes your problem.

If this does not work for you, you could always take it a step further. Boot the Full linux (Try Live). and follow this guide: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

And i have to ask, are you on debian or Ubuntu?

---

### Post by danrgmc-yahoo2 on 2016-04-15
I had a similar problem two days ago when I did a clean install of Xenial. I have 4 operating systems on 2 harddrives-2 Mint,  Ubuntu 16.04 and Windows 7. I rebooted to a blank screen-no error messages. I ran my Xenial disk as 'try Ubuntu' downloaded and installed Boot-Repair and followed instructions. Worked flawlessly. Sorry I don't remember the instructions-I didn't save them.

---

### Post by grahammechanical on 2016-04-16
Are you using Debian or Ubuntu? A Ubuntu live session will let you backup your data.

---

### Post by Rajesh_Pratap on 2016-04-17
Hey, @izznogooood 

I Booted a live Ubuntu and Tried the code

sudo update-grub

Which gave me Output as "/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'. "

Than i Tried to use following commands
mkdir /mnt
mount /dev/sda5 /mnt
cd /mnt
ls -lBy ls -l I saw my / (root) Directory of My Old Linux , So i wrote a command
grub-install --recheck --root-directory=/mnt /dev/sda

Which Ran without Errors, than i tried the command

update-grub but it gave Same Cow error :( , Than i tried restarting my PC and again Got that Black Screen which wrote

Grub2,xx ~ Minimal Bash like Shell
grub> 

I am so confused now

---

### Post by Rajesh_Pratap on 2016-04-17
I Ran an Boot-Repair Today From Ubuntu (Automatic Repair) and it's Report is Generated Here 

[http://paste.ubuntu.com/15886861/](http://paste.ubuntu.com/15886861/)

But still i Get same Black Screen like gnu gurb version2.02~beta

Minimal Bash Like Editing .....

grub>

Please Help me, I could now not move to Linux nor Windows.. I have Backed up data using live USB, But nothing working to restore grub

---

### Post by valereguerin on 2016-04-17
if you have some place on your dd (3/5 giga) you can install a "system-rescue" (another Ubuntu/Mint/Debian, test one of them 
if you have another Pc : [https://distrowatch.com/](https://distrowatch.com/)

if not....
downstairs to the library buy Linux magazine you have exploitation system inside, live CD and install 32/64 Bits ) and you will have a new grub....

if you have another dd "it's better"   for the new install  ; you put your new grub on your new /boot partition 

or not :   read the installation message ! where new install go on your only one HDD/SSD (Gparted !...en live avant install !)

reboot your new install  : ```
sudo apt-get update && sudo update-grub
```

yours systems back !

if not....maybe your HDD/SSD.... change it after fsck/.....

ddrescue/foremost    for your data recovery (terminal- software) if you will not be able to with your live CD/Live USB

[http://www.tomshardware.fr/forum/id-1805247/tuto-guide-pratique-recuperation-donnees-disque-dur.html](http://www.tomshardware.fr/forum/id-1805247/tuto-guide-pratique-recuperation-donnees-disque-dur.html)

---

### Post by izznogooood on 2016-04-17
I think its time to have a look in your BIOS, find something named SECURE BOOT, and disable it!

---

### Post by LostFarmer on 2016-04-17
It looks like you have major problems.
> Which Prints out lost+found/ etc/ media/ dev/ lib/ lib64/ live-build/  mnt/ opt/ proc/ root/ run/ sbin/ sys/ srv/ tmp/ usr/ var/ vmlinuz lib32/  I do not see " /boot  /home  /bin "  and the pastebin says it can not find some needed folders/files in /ect --ect/fstab , /etc/grub.d/, and no /boot/grub/grub.cfg is listed.

I would recommend backing up needed files in windows and linux.  

I do not know just what to say to do.  

> But Unfortunately, today i ran into a  Error while opening the PC Next Time  is ** PC Next Time** the way you wrote the sentence or is it some type of program that could be the problem ?

---

### Post by grahammechanical on 2016-04-17
I still do not know if the OP is running Ubuntu or Debian. As I do not use Debian I cannot say for sure if the advice that is being given is suitable for Debian boot problems. I just get the feeling that Debain & Ubuntu differ about where the Grub configuration files go.

> Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.

For the record. update-grub & grub-install are Ubuntu scripts that activate certain Grub applications. I am not sure they work on a Debian install.

Regards.

---

### Post by LostFarmer on 2016-04-17
> **grahammechanical said:**
> 
For the record. update-grub & grub-install are Ubuntu scripts that activate certain Grub applications. I am not sure they work on a Debian install.
Regards.
I did not try 'grub-install' but Debian's 'update-grub' script  does the same thing as Ubuntu's, running 'grub-install --h' looks the same.   I did not know if the scripts are written the same or not.   "/etc/default/grub and /etc/grub.d/ '" are valid folders. ( I am running Debian)

added:  I do not know what will happen running 'boot-repair' and tell it to install grub on a Debian install.

---

### Post by Cavsfan on 2016-04-18
> **LostFarmer said:**
> I did not try 'grub-install' but Debian's 'update-grub' script  does the same thing as Ubuntu's, running 'grub-install --h' looks the same.   I did not know if the scripts are written the same or not.   "/etc/default/grub and /etc/grub.d/ '" are valid folders. ( I am running Debian)

added:  I do not know what will happen running 'boot-repair' and tell it to install grub on a Debian install.

Did you enter **sudo grub-install /dev/sda** (where a is your first drive, b second, etc.) ?

**sudo fdisk -l** or **sudo blkid** will list your partitions but you want to install grub on the drive itself.

Perhaps these will help:

[Debian Grub2]("https://wiki.debian.org/Grub2")

[Debian GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html")

---

