---
title: "how to ffado and freebob on hardy - easy tutorial - for dummies!"
date: 2009-05-03
forum: Ubuntu Studio
---

### Post by rafafredd on 2009-05-03
First add khashayar PPA to software sources (check [https://launchpad.net/~khashayar/+archive/ppa](https://launchpad.net/~khashayar/+archive/ppa) for more info):

adding key, as sudo:

open terminal

type:

sudo su

enter password

wget -q [http://dl.getdropbox.com/u/175461/khashayar_ppa.asc](http://dl.getdropbox.com/u/175461/khashayar_ppa.asc) -O- | sudo apt-key add -

then add the sources:

go to system>administration>Software Sources

Then Third-Party Software tab

click +Add... button

type as APT line:

deb [http://ppa.launchpad.net/khashayar/ppa/ubuntu](http://ppa.launchpad.net/khashayar/ppa/ubuntu) hardy main

click +Add Source button

Now click +Add... button again

and type as APT line:

deb-src [http://ppa.launchpad.net/khashayar/ppa/ubuntu](http://ppa.launchpad.net/khashayar/ppa/ubuntu) hardy main

click +Add Source button again, and then close the window.

Open System>Adminstration>Synaptic Package Manager and check for libraw1394, libfreebob and libffado (or something alike, lke libraw1394-8, libfreebb0 and libffado2). These should all be installed.

Now we are going to make sure you are a member of the audio group:

for that, back to the terminal window, where you are still sudo (if you've closed it, please, sudo su to become root again) type:

groups username

where username is your username -OK, don't be that dummie!

well, it will list some groups, and audio must be listed there. It always is from a fresh Hardy install, as ar as I know, but just to check, make sure it is.

now that you know that you ae a member of the audio group, go ahead and add raw1394 to the audio group.

in the same sudoed terminal window type:

cd /
cd etc
cd udev
cd rules.d
ls

now make sure you can see a filename called 40-permissions.rules there. You should.

If so, type:

gedit 40-permissions.rules

a text editor opens

now add the following two lines to the end of the file:

# by username
KERNEL=="raw1394", GROUP="audio"
KERNEL=="raw1394", MODE="666"

again, don't be DUMB. Change username to your username. It keeps the file organized if future changes are needed.

then, in the same file, find the line:

KERNEL=="raw1394", GROUP="disk"

and add a # in front of it, so it looks like that:

# KERNEL=="raw1394", GROUP="disk"

with this, you removed raw1394 module from the disk group (it would probably make jack crash), added it to the audio group and changed the mode so that jack can now run on firewire port.

save the file, close the window and get back to the terminal (you still must be root! If you closed the terminal wndow, open it agan and become rot again by doing sudo su!)

now type:

cd /
cd etc
gedit modules

the text editor opens

add the following lines in the end of the file:

# by username
raw1394

save the file
close the window
back to the terminal, as root, type:

cd /
cd etc
cd security
gedit limits.conf

the Mr. Text Editor, your friend by now, pops up. Add the following lines in the end of the file:

#by username
@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited

save the file, close the window.

install gscanbus:

in the ever same root terminal:

apt-get install gscanbus

you have a configured system.

Reboot.

Check to see if your system can see yor firewire device. Connect it, turn it on, and run on a terminal:

sudo su (enter password)
gscanbus

You should see your soundcard, whatever it is.

Now you can close gscanbus.

Check for on System>Adminisration>Udate Manager

You should update any freebob, ffado and jack related packages.

if not necsessary to eboot after the updates (but probably will be), you are eady to run jack.

On jack setup, choose freebob or firewire.

check realtime option.

set priority to 89

check No Memory Lock option (if I don't, I get system crashes...)

Some firewire interface only works with periods/Buffer = 3. If yours wont't work, here is a hint.

Also, if jack won't start, try changing he Interface to anther value other than default.

I hope you have a working firewire linux audio system by now.

Good luck!

---

