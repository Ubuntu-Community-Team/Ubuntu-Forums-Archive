---
title: "How to input a password in rc.local script?"
date: 2016-09-10
forum: Security
---

### Post by tornadof3 on 2016-09-10
So

I have been setting up a home laptop to use the pam_ccreds module for cached credentials when away from small home network that runs OpenLDAP for user auth etc. NFS shares from the server are mounted on the laptop and synchronised with local copy of /home on laptop which is used as primary data source when away from the network; laptop's copy of server's /home is stored in a luks volume contained within a file.

I am using a bash script in /etc/rc.local on boot to check if it is in the home network etc; it asks for the password to the encrypted volume. Unfortunately, when using the ```
cryptsetup luksOpen
``` command on its own, the password (usually!!) echoed in plain text when the user typed it in. So now I was using ```
stty -echo
``` and reading the password into a bash variable before passing it to the ```
cryptsetup
``` command. *sometimes* the password does not come up when the user types, *sometimes* it appears in plain text... I cannot work out why this happens or what governs it... For background, this is using the Ubuntu 14.04 sources on the laptop (it's Linux Mint 17.3). Laptop does *not* have the ```
quiet splash
``` grub options so initially boots in a traditional text mode before the graphical login prompt loads; users generally have to Ctrl-Alt-F7 to get to the waiting password prompt to unlock encrypted volume before Ctrl-Alt-F8 to get back to graphical login prompt.

Any help appreciated; my /etc/rc.local:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
stty -echo
printf "Enter password for local hard drive: "
read PASSWD
stty echo
printf "\n"
echo -n $PASSWD | cryptsetup luksOpen /lhome/homes.img lhomes -
sleep 1
LHOMES="/dev/mapper/lhomes"
if [ -b "$LHOMES" ] 
	then
		mount /dev/mapper/lhomes /home
		echo "Mounted luks volume to /home"
	else
		echo "Crypt loopback device "$LHOMES" does not exist"
fi

sleep 5

if ping -c 1 blacktower &> /dev/null
then
	mount -t nfs -o proto=tcp,port=2049 blacktower:/homes /lhome/remotehomes
	echo "Mounted remote homes"
else
	# host unreachable, use local /home
	echo "Blacktower unreachable; using local home repository only"
fi
exit 0
```

---

### Post by TheFu on 2016-09-10
Don't know how to do what you are asking, but perhaps using the cryptab to open the crypt container before mounting would be better?  That is how a fully encrypted (excluding /boot/)  install works.  Cannot tell you all the steps necessary to make the cryptab work, wish I could.

---

### Post by tornadof3 on 2016-09-10
Hi, thanks for that. I did put an entry in crypttab, but not sure if I need to enable a setting to force the system to 'read' or 'do' the crypttab - it seems to ignore it and never do anything with it. I googled around and couldn't find any suggestion that crypttab has to be 'enabled'... ?

---

### Post by TheFu on 2016-09-10
initrd needs to be rebuilt.  **update-initramfs** is the tool for that, but exactly how to get it working with cryptab has eluded me as well.

---

### Post by tornadof3 on 2016-09-14
So, after a bit of thinking, I found a (sub-optimal) solution to this problem; rather than asking for a password in /etc/rc.local, I call a Perl script in rc.local, and then have:

```
#!/usr/bin/perl -w

use Term::ReadKey;
print "Enter password for local hard drive: ";
ReadMode('noecho'); # don't echo
chomp(my $password = <STDIN>);
ReadMode(0);         # back to normal
print "\n";
system("echo -n $password | cryptsetup luksOpen /lhome/homes.img lhomes -");
```

This achieves the desired result. Hope it is useful to someone else.

---

