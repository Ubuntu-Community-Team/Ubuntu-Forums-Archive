---
title: "cheat sheet"
date: 2008-10-08
forum: The Cafe
---

### Post by neba on 2008-10-08
I am a total noob at linux. after installing ubuntu 8.4 on my laptop, desktop, and girlfriends pc. I have made a cheat sheet to make things easier. It consists of some programs and terminal commands. 
IF you have any sort of cheat sheet please post it here. I want to know if you have found stuff out that might make ubuntu easier for me and others. thanks


This is what I have:


first off
application/ accessories/ terminal

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring

sudo apt-get update 


 skype
sudo apt-get install ia32-libs lib32asound2 libasound2-plugins; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb;


terminal partition (a web site)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


partition
sudo apt-get update && sudo apt-get install gparted ntfsprogs

gksudo gparted


adobe acrobat reader
sudo apt-get install acroread


lime wire
[http://www.gnutellaforums.com/general-linux-support/39850-how-install-limewire-ubuntu-debian.html](http://www.gnutellaforums.com/general-linux-support/39850-how-install-limewire-ubuntu-debian.html)


 amarok

 
BOOT ORDER 
from ubuntu and win. xp

application/accessories/terminal

su (enter)
psw: **** (enter)
gedit /boot/grub/menu.lst (enter) <.lst is a Lst> <space after gedit >

(you should see something like this in the beginning)
--- --- --- ---
# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not use 'savedefault' or your 
# array will desync and will not let you boot your system. 
default		0
--- --- --- ---
right here at the bottom of the example it says  'default        0' 
change the '0' to a  '4' if you want to have win. xp  to start up first
change it back to a '0' to have ubuntu start up automatically
remember to save

---

### Post by neba on 2008-10-08
Please note that all of this worked for me right after I installed Ubuntu 8.04 Hardy Heron (the '64' one).

---

### Post by Alan Coleman on 2008-10-08
[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

good starter...

---

### Post by neba on 2008-10-08
> **Alan Coleman said:**
> [http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

good starter...

wow I wish that found that web page earlier. thanks

---

### Post by adamogardner on 2008-10-08
credit for this excellent list goes to bill goldberg in his thread very similar to this one.

[http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/](http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/)

here's goldberg's thread which has more than just that.

[http://ubuntuforums.org/showthread.php?t=936906](http://ubuntuforums.org/showthread.php?t=936906)

---

### Post by neba on 2008-10-09
> **adamogardner said:**
> credit for this excellent list goes to bill goldberg in his thread very similar to this one.

[http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/](http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/)

here's goldberg's thread which has more than just that.

[http://ubuntuforums.org/showthread.php?t=936906](http://ubuntuforums.org/showthread.php?t=936906)

lot of that is over my head. lol

---

