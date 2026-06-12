---
title: "“dssi-vst” package in Ubuntu"
date: 2012-06-24
forum: Ubuntu Studio
---

### Post by subculture on 2012-06-24
Hello,

is there any documentation on the web about this package and how to use it...“dssi-vst” package in Ubuntu ?                                                                              

[https://launchpad.net/ubuntu/+source/dssi-vst](https://launchpad.net/ubuntu/+source/dssi-vst)

---

### Post by sgx on 2012-06-24
Hi, for dssi-vst to find your vsts, you give it a path to follow,
by making a textfile like the example below, in the folder
/etc/profile.d

Create the folders needed for the path

sudo mkdir /usr/lib/vst

Then copy the vsts there, and reboot. Then, run a command,
based on vsts in the folder:

vsthost ZebraCM.dll


# Set DSSI_VST_PATH for Bash shell
if [ -n "\$DSSI_VST_VST_PATH" ]; then
   export DSSI_VST_VST_PATH="/usr/lib/vst"
fi

Use a text editor as sudo, to edit or create files in your
/etc/profile.d folder.

For very large vsts, on a small root partition,
you might use a symbolic link from a location in /home/you
to /usr/lib/vst. This should appear as an option during
a drag/drop operation from a file manager like nautilus,
pcmanfm, dolphin etc started as sudo.

Stick to vsts that have built-in preset handling
unless you will be making your own. U-he instruments
all do this, and should work. Free ones are
tyrelln6, zebralette (part of zebra 2,5 installer)
bazille, and TripleCheese. ZebraCM is on every dvd from
Computer Music Magazine. Free ampsims from
[www.guitarampmodelling.com](www.guitarampmodelling.com) work and sound great, presets
less important. The free Guitar Rig 5 player should work,
its very nicely done. 
Cheers

edit you could also do

cd /usr/lib/vst   then

vsthost TyrellN6.dll

etc

---

### Post by subculture on 2012-06-25
> **sgx said:**
> 

Then, run a command,
based on vsts in the folder:

vsthost ZebraCM.dll


This was the problem... I did compile dssi-vst about 3 years ago openSusse 11.0 i even made a tutorial which sits on my hp :)

thank you very much... i owe you a cold beer :)

---

### Post by sgx on 2012-06-25
I'll waddle over to the 'fridge, and crack one,
to save on the postage, and more importantly,
the time lag :wink:

Cheers

---

