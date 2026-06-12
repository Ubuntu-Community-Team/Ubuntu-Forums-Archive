---
title: "weird artifacts / - what are they?"
date: 2011-08-14
forum: Server Platforms
---

### Post by 007casper on 2011-08-14
weird artifacts / - what are they?

I occasionally get these weird files show up on the main system directory of the server.

cd /
ls -al
0þÚ·ûÚ·&#137;C·  152B 07/17/11
ÐZ¹ÐZ¹Ð:2·    0B 07/19/11
Pr&#146;¹@&#135;&#146;¹ ß5·  152B 07/16/11
puN·          152B 07/19/11
tÿÑ&#145;         152B 08/13/11

They are either 0B or 152B in size.

I tried to read them on the terminal.  I was able to read only two of them.

cat 0?&#1719;??&#1719;??C?
[17-Jul-2011 05:23:05] PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0

[19-Jul-2011 04:14:24] PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0

cat Pr??@??? ?5?
cat: Pr??@???: No such file or directory
cat: ?5?: No such file or directory

why am I getting these files there?  I am going to delete them, but I would like to find out why this is happening.  

Thank you.

---

### Post by SavageWolf on 2011-08-14
They look like corrupted files, you should probably do a fsck and check the status of the disk.

---

### Post by 007casper on 2011-08-14
what is the full command 
fsck -n

?

---

### Post by SeijiSensei on 2011-08-14
First, you can't run fsck while the filesystem is mounted.  You must, instead, boot an installation image from a CD or USB drive.  Choose the "Try Ubuntu" option and open a terminal when the desktop has loaded.  If there's only one hard drive it will be called /dev/sda.

Before you boot with the CD, open a terminal on your current system and type the "mount" command to determine which partition on the drive contains the Linux root filesystem.  If you have a dual-boot setup, it will likely be /dev/sda3 or something like that.

Now, while running from the CD image, open a terminal and run "fsck /dev/sda3" or whichever partition holds the filesystem with errors.  You might also want to type "man fsck" to see the complete documentation for that utility.

---

### Post by 007casper on 2011-08-14
oh thank you.  I am on vps environment. So, I cant boot from CD or USB drive. 

is there any other way I could do fsck?

---

### Post by 007casper on 2011-08-14
I found this thread
[http://ubuntuforums.org/showthread.php?t=1259850](http://ubuntuforums.org/showthread.php?t=1259850)

> It's probably easier to force the system to do an fsck at reboot. It will mount / readonly so it can safely be checked and repaired.

there used to be an option to shutdown to do this but apparently it got removed. You can emulate it by

Code:

sudo touch /forcefsck
sudo shutdown -r now



then again I am not really sure what kind of raid set up is on the vps.

---

