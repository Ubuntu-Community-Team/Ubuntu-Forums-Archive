---
title: "How do I install Wrath of the Lich King on Ubuntu 9.04?"
date: 2009-05-27
forum: Wine
---

### Post by Sanof on 2009-05-27
Kind of new to Ubuntu and I am not quite understanding the guides. Does the guide [http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04](http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04) say to type those commands only without the $ and # signs? 

And for [http://forums.wow-europe.com/thread.html?topicId=8611091191&sid=1](http://forums.wow-europe.com/thread.html?topicId=8611091191&sid=1) I copy from the when it says ------BEGIN PNG BLOCK-----? And just put the file name as whatever.png?

I was having a hard time before and if someone could help me out with a detailed instruction it would be of great help.

---

### Post by 8Kuula on 2009-05-27
> **Sanof said:**
> Kind of new to Ubuntu and I am not quite understanding the guides. Does the guide [http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04](http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04) say to type those commands only without the $ and # signs? 

Yes. Without those & and # signs.

> **Sanof said:**
> 
And for [http://forums.wow-europe.com/thread.html?topicId=8611091191&sid=1](http://forums.wow-europe.com/thread.html?topicId=8611091191&sid=1) I copy from the when it says ------BEGIN PNG BLOCK-----? And just put the file name as whatever.png?

I was having a hard time before and if someone could help me out with a detailed instruction it would be of great help.

For that part I would recomend to use this page [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

P.S.
Did install and play WoW with ubuntu (8.10 x64) back in december-january, and I did go around that DVD installation with downloading whole WoW from blizzards site. When downloading+installing was done, only thing I did change was adding -opengl to startup command. All did work smoothly, I was realy supriced.

---

### Post by Sanof on 2009-05-27
Quick question before I mess up, 

 sudo mkdir /mnt/lich
 sudo su -
 mount -t udf -o ro,unhide,uid=1000 /dev/scd0 /mnt/lich (replace /dev/scd0 with your cdrom)
 exit
 cd /mnt/lich
 wine Installer.exe

What do I type in the /dev/scd0? I dont know what to type to have it be my cd.

Edit: This is what I got

kanti@kanti-desktop:~$ sudo mkdir /mnt/lich
[sudo] password for kanti: 
kanti@kanti-desktop:~$ sudo su -
root@kanti-desktop:~# mount -t udf -o ro,unhide,uid=1000 /media/cdrom0 /mnt/lich
mount: /media/cdrom0 is not a block device
root@kanti-desktop:~# mount -t udf -o ro,unhide,uid=1000 /dev/scd0 /mnt/lich
root@kanti-desktop:~# exit
logout
kanti@kanti-desktop:~$ cd /mnt/lich
kanti@kanti-desktop:/mnt/lich$ wine Installer.exe
wine: could not load L"D:\\Installer.exe": Module not found
kanti@kanti-desktop:/mnt/lich$

---

### Post by 8Kuula on 2009-05-28
Hmm...
Only thing I can think of is that check your wine configuration -> drives tab, and see is there drive that has mapping "/".  If not then you need add that cdrom mount path there, or add that drive mapping "/".
If there is, my knowhow on wine has hit to the roof :D

command: winecfg
opens wine configuration.

---

### Post by Sanof on 2009-05-28
My Wine shows: 

C: ../drive_c
Z: /

Also, that .gpg file in the second guide isnt working, when I try to add it to Wine it just doesnt pop up. The .gpg on the wine page you linked me does work though. Does it matter which I use, or do both work the same?

Edit: And did I do the commands fine on the terminal? I still dont get what it means when they say to replace the /dev/scd0 with your cd drive.

---

### Post by 8Kuula on 2009-05-28
> **Sanof said:**
> My Wine shows: 

C: ../drive_c
Z: /

Also, that .gpg file in the second guide isnt working, when I try to add it to Wine it just doesnt pop up. The .gpg on the wine page you linked me does work though. Does it matter which I use, or do both work the same?

Paths seems to be in order.

Better gpg key one in official site, imho.

> **Sanof said:**
> 
Edit: And did I do the commands fine on the terminal? I still dont get what it means when they say to replace the /dev/scd0 with your cd drive.

If no errors did pop up, all ok.

You can check what is your cdrom actual device path from /etc/fstab file.
command: cat /etc/fstab

There should be line similar to:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
^^^^^^
cdrom device path.

I think thou since your mount command did not give errors, that /dev/scd0 is your cdrom device path.

Extra info:
wine: could not load L"D:\\Installer.exe": Module not found.

Error tells that wine can't find that file in that location, wine handles all paths, even if you give linux style from terminal, as windows style, so if that path can't be located thru ones given in winecfg -> Drives paths then wine can't see it. But since you have drive Z: as root directory "/", wine should find it. Thou error says wine tries to get it from drive D:.
Maybe should manualy after mounting add that path there as drive D: (or next free one) just to be sure (D: /mnt/lich).

Whell I think thats enough confusing information for today? ):P

---

### Post by Sanof on 2009-05-28
Reformatted and re-installed everything, but I still am having trouble with Wotlk.

[FONT=monospace]
[/FONT]kanti@kanti-desktop:~$ sudo mkdir /mnt/lich
[sudo] password for kanti: 
kanti@kanti-desktop:~$ sudo su -
root@kanti-desktop:~# mount -t udf ro,unhide,uid=1000 /dev/scd0 /mnt/lich
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@kanti-desktop:~# exit
logout
kanti@kanti-desktop:~$ cd /mnt/lich
kanti@kanti-desktop:/mnt/lich$ wine Installer.exe
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
kanti@kanti-desktop:/mnt/lich$ 
kanti@kanti-desktop:/mnt/lich$ 

I dont quite get why it doesnt want to launch ;(. 

Wine shows me: 
C: //drive_
D: /media/cdrom0
Z: /

Edit: If anyone knows how to dl Wotlk off the Blizz website and install it that way Im up to do that too. Or the cd, whichever works really.

---

### Post by 8Kuula on 2009-05-29
> **Sanof said:**
> I dont quite get why it doesnt want to launch ;(. 
I do not either, seems all is ok but no go, can't think any reason(s).

> **Sanof said:**
> 
Edit: If anyone knows how to dl Wotlk off the Blizz website and install it that way Im up to do that too. Or the cd, whichever works really.

At [http://www.wow-europe.com](http://www.wow-europe.com), from side menu under account is download option ( [http://www.wow-europe.com/en/downloads/client/](http://www.wow-europe.com/en/downloads/client/) ).

Dunno where it is hidden in US pages. Did not poke my eye, when I did check.

If that InstallWoW.exe agrees to run with wine then its straight forward.

I did run to check what it do, and in early start did pop some "red X error" window without any text, so I just did click "OK" and installer did continue, I did go up to install location and it started to download.
So seems atleast up to that point it works.

---

### Post by cspack on 2009-05-29
> **Sanof said:**
> 
kanti@kanti-desktop:~$ cd /mnt/lich
kanti@kanti-desktop:/mnt/lich$ wine Installer.exe
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
kanti@kanti-desktop:/mnt/lich$ 
kanti@kanti-desktop:/mnt/lich$ 

I dont quite get why it doesnt want to launch ;(. 



It looks like it's searching for Installer.exe in the wrong place.  Try this:

kanti@kanti-desktop:~$ cd /mnt/lich
kanti@kanti-desktop:/mnt/lich$ wine ./Installer.exe

note the ./ before Installer.exe.  That tells the shell to run the program from the current directory.

---

### Post by hikaricore on 2009-05-29
I'm actually suspecting it's not mounting properly.
After mounting and changing directories type:

> ls -la

This will show you what's in the directory.
You should see the Installer.exe and several mpq files at the very least.

---

### Post by Sanof on 2009-05-30
Well, I managed to just dl Wrath and install it by running the .exe through Wine, and I dled all the patches, but now I have a new problem.

Whenever I try to login it tells me that I have the incorrect username or password,even though I am using the right one. Ive had a friend login and check for me and then I try and it fails. Anyone have an idea on how to fix this?

Edit: This might sound rediculous, but maybe its because I downloaded a european client and it is mean to only login european characters?

---

### Post by David-IT on 2009-06-07
i am not to familiar with the euro client but yes you have to change the realmlist.wtf located in your data folder to connect to the us servers look up wow realmist us on google

---

### Post by Dokken767 on 2010-01-04
hey i got a similar problem except that its about the patches. when i went and installed WoW and got it to run i needed to patch up. when i try and log in it says it cannot find a patch to install... also when i down load the patches manually i am not really sure how to get them to work. when i use the patcher in the WoW folder it brings up the patching page but with no words in it. anyone no how to patch a downloaded version of WoW?

---

### Post by pedro_orange on 2010-01-04
When you load up the patcher; because you don't have Gecko installed, it will appear like a blank window. You can either just wait for the progress bar at the bottom of the window, or you can install Gecko. 
Just download the patches manually. Run them in wine, wait. Then it will all be fine.

---

