---
title: "From Windows, boot in Linux. From Linux boot into windows."
date: 2007-06-06
forum: Windows
---

### Post by some11 on 2007-06-06
Hey!
Ok
Im using this as a "remote server". (meaning to view it, I have to connect via VNC, SSH, TELNET or FTP (once OS and programs installed)

Ive manage to install XP and Ubuntu, setup the network, and internet...
Installed, and and make autorun all the servers/services....

Now...
When I first turn on the PC, as I installed ubuntu last, there is a boot screen saying "ubuntu or XP", and the default is ubuntu...so it will boot into ubuntu...great! can VNC to it :) now what if I want to get to XP remotly? 

Could I make a shortcut/script/program to change the default boot, and then restart the box? e.g.

1st boot - LInux
2nd boot - Windows
3rd boot - linux
4th boot - windows
5th boot - linux.....

Linux to windows, Ive found this:
 gksudo gedit /boot/grub/menu.lst
Which is the boot order yea?

Windows to Linux
In  "my computer" there is just the XP HDA, and It cant see linux partitions! (this is going to be a problem!!!)


anyhoo....
Basicly, can I make a script, that changes the default OS when the PC  is turned on, and then restart it after?;)

Sorry if this doesn't make any sense! :(

---

### Post by some11 on 2007-06-06
Hey (again)

with menu.lst
What do these do? I dont understand the comments about them,..,,:
>>savedefault
>>makeactive
>>chainloader

I think, what I could try and do, is when it boots into Ubuntu, it runs a script there, to change the menu.lst. and with the new menu.lst the default is XP. when its next restart, it will boot into xp, run the script, and change it back into the old one, which Ubuntu is then the default! That would do the trick!

What commands can I run from menu.lst? is there a rename one? move file? delete file?

Thanks for your time

edit: Something like this (its a .bat file)

> if exist menu1.lst goto MENU1
:MENU2
rename menu.lst menu1.lst
rename menu2.lst menu.lst
exit
:MENU1
rename menu.lst menu2.lst
rename menu1.lst menu.lst


---

### Post by the_tazinator on 2007-06-06
I did something like this a while ago. This is what I did:

Install Ext2ifs on your windows partition ([http://www.fs-driver.org](http://www.fs-driver.org)) This allows your windows OS to see your linux drive(s). In your /boot/grub/menu.lst file, change the setting of # howmany=all to # howmany=1. This will make it so that is your grub boot menu shows only the most recent kernel version. This is done so that the location of the Windows XP menu item is always in the same place. (This is not the best thing if you boot older kernel versions.) Then you create a shell script for the linux side and a batch file for the windows side that changes the value for 'default' in the menu.lst file. The default value for 'default' is 0 meaning that grub selects the first line. You will have to look at your grub menu to see what value to change the 'default' value to. With the 'howmany' setting changed, your grub menu should look something like this:

Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Other operating systems:
Microsoft Windows XP Professional

Starting with 0 at the top, count the number of lines until you get to the OS you want to boot. When you get to the one you want, that is the number you want to set as default. In this case, if I want to boot Windows XP then default would be set to 3.

Depending on your level of script writing, you can get very creative with this. If you don't want to do any scripting, you can just go in and change the file each time you want to reboot into a differt partition. Also be cautious with using two files for this since when you upgrade your kernel, your menu.lst file changes. If both files don't match you could have issues.

---

### Post by some11 on 2007-06-06
THanks for your reply!
Right
its now:
# howmany=1
(Should there be a #?)

Also found this,
[http://www-128.ibm.com/developerworks/linux/library/l-osswitch/](http://www-128.ibm.com/developerworks/linux/library/l-osswitch/)

I will try it out later, and get back!

Thank you!

Edit:
I can do the windows script (a batch file), but as this is my second day in linux, I haven't got a clue about that!

---

### Post by the_tazinator on 2007-06-06
Yes, keep the # in front of 'howmany'

---

### Post by some11 on 2007-06-06
_**Windows to Linux**_ (Note: I got the driver package, like *the_tazinator* said, and label up the drive as "Z:". I also move about the position of XP in menu.lst)
**File**:/boot/grub/menu.lst
**replace**: default 1
**with**: default 0

Ubuntu.vbs
> Const ForReading = 1
Const ForWriting = 2

Set objFSO = CreateObject("Scripting.FileSystemObject")
Set objFile = objFSO.OpenTextFile("Z:\boot\grub\menu.lst", ForReading)

strText = objFile.ReadAll
objFile.Close
strNewText = Replace(strText, "Default 1", "Default 0")

Set objFile = objFSO.OpenTextFile("Z:\boot\grub\menu.lst", ForWriting)
objFile.WriteLine strNewText
objFile.Close

_**Linux to Windows**_
**File**:/boot/grub/menu.lst
**replace**: default 0
**with**: default 1

XP.sh
> sudo sed -i 's/default 0/default 1/' /boot/grub/menu.lst
sudo reboot
[SIZE="5"][COLOR="Red"]
[CENTER]

Cracked it!
Thank you![/CENTER][/COLOR][/SIZE]

---

### Post by fmen on 2007-06-11
This is great stuff. I've been looking for a solution like this for SimplyMepis.

Would the xp.sh script work for Mepis if sudo was changed to su?

---

