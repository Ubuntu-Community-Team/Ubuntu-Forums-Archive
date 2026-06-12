---
title: "HOWTO: DViCO FusionHDTV DVB-T Dual Digital 4 with remote tutorial"
date: 2007-11-17
forum: Tutorials
---

### Post by oobe-feisty on 2007-11-17
**Quick Note**

As of Ubuntu 8.10 driver installation is no longer necessary for rev 1 tuners and no longer necessary for rev2 as of 9.04 you just need to pop the attached firmware into /lib/firmware if you have the rev 2 then you dont need the firmware. 



**Driver Installation**

sudo -i 

apt-get update

apt-get install install mercurial build-essential linux-headers-`uname -r`

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

cd v4l-dvb

make && make install 

exit


**Rev 2 is now supported ** 
 
thanks to Anton Blanchard
it is has now been merged into tip. follow same steps for rev1 but dont worry about firmware
rev 2 does not require firmware

**Firmware Installation**

as of writing this 25/08/08 the firmware for dvico no longer needs chris pascoes australian firmware you need one single file called 
xc3028-v27.fw 

i found a script on a mailing list that extracts it from  some hauppauge drivers i will attach the firmware here just extract it to 
/lib/firmware 

download xc3028-v27.fw.tar.bz2 
tar xvjf xc3028-v27.fw.tar.bz2 
sudo cp xc3028-v27.fw /lib/firmware

reboot

**Quick test**
 
apt-get install dvb-utils

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-sydney_north_shore > channels.conf

sudo cp channels.conf /etc && cp channels.conf ~/.tzap

tzap -c /etc/channels.conf -r "ABC2"

leave open and from a new terminal window as a normal user type

mplayer /dev/dvb/adapter0/dvr0

the above example assumes your in sydney you can find your conf file for your town or city in /usr/share/doc/dvb-utils/examples/scan/dvb-t


now su back to normal user by typing "exit" or "su - user"




**Remote installation**

**Create Symlink**

type

dmesg | grep IR

you should see somthing like this

input: IR-receiver inside an USB DVB receiver as /class/input/input6

now open  /etc/udev/rules.d/60-symlinks.rules

gksudo gedit /etc/udev/rules.d/60-symlinks.rules

or kubuntu 

kdesu kate /etc/udev/rules.d/60-symlinks.rules

and add this line at the bottom

KERNEL=="event*",SYSFS{name}=="IR-receiver inside an USB DVB receiver",SYMLINK="input/irremote" 

reboot so /dev/input/irremote is made
[B]
UPDATE:[/B] on newer versions of udev ATTRS is used instead of SYSFS as SYSFS is no longer accepted i.e 
KERNEL=="event*",ATTRS{name}=="IR-receiver inside an USB DVB receiver",SYMLINK="input/irremote"

I dont know which version this change took effect but I had to change it once my system had upgraded to 175-2


**Configuring LIRC**

in a console type

sudo dpkg-reconfigure lirc

scroll down to linux input layer then select it 

on page 2 for IR transmitter select none

on page 3 select  /dev/input/irremote 

download attached lirc1.tar.bz2 if you remote look like [this]("http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dd4-remote.PNG")

and download lirc2.tar.bz2 if you remote looks like [this]("http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg") 

replace lircx with lirc1 or lirc2 in terminal type

tar xvjf lircx.tar.bz2

cd lircx

sudo cp -R lirc /etc

**Install the basic lircrc config for mythtv**

mv /etc/lirc/lircrc ~/.mythtv

ln -s ~/.mythtv/lircrc ~/.lircrc

sudo ln -s ~/.mythtv/lircrc /etc

sudo ln -s ~/.mythtv/lircrc /etc/lirc

**now restart lircd**

sudo /etc/init.d/lirc restart 

**test **

irw 

press keys on remote


**Rev 2 remote**

i dont not own a rev 2 tuner i cannot test or produce working configs thanks to [tvars]("http://ubuntuforums.org/showpost.php?p=6232229&postcount=42") i now have a working lircd.conf for the rev2 remote and have updated the attached lirc2 files to be complient 


you will have to make a lircrc from scratch or modify mine that is attached also 


**Different Remote's Bundled with DD4** 

if your remote looks like [this ]("http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dd4-remote.PNG") then use lirc1.tar.bz2 
if your remote looks like [this]("http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg") then use lirc2.tar.bz2
you need to map a few extra buttons in lircrc for lirc2 but most of the buttons will work as is

apperently this [one]("http://www.overclockers.com.au/wiki/Image:Dvico_remote.jpg") works with the lirc2 config aswell
however there are different remotes around the instructions above for the most part will still work but you will have to make your own lircd.conf 
and lircrc files i would welcome people to add there remote's pics and configs in this thread

**Trouble Shooting**

There only 2 issues i can think off one is that sometimes one of the tuners disappears or becomes unaccessible 
and the other is "dvb-usb: bulk message failed: -110" spamming the terminal making the keyboard and mouse erratic see [here]("https://bugs.launchpad.net/ubuntu/+bug/229879")
I haven't had many issues with the first one for ages may be fixed and the 2nd very very rarely since the dvico drivers started 
using non AU firmware ( I dont blame the AU firmware im simply using this as a time line) anyhow both can be resolved by turning off PC for a minute then turning it back on rebooting will** not** resolve this.

dont know which revision? you can check with lsusb you should see 0fe9:db78 DVICO for rev1 and 0fe9:db98 DVICO for rev2

in ubuntu 8.10 the remote gets detected by hal as a pointer device making the remote not work at all you can fix it with this [post]("http://ubuntuforums.org/showthread.php?p=6093982#post6093982")

Its's worth pointing out to newbies if you upgrade your kernel through ubuntu updates you will need to reinstall your drivers some people didnt relise this they also had trouble grabbing new source cause the old v4l-dvb source was in the same directory you dont need new source but it's recommended you can rm -rf v4l-dvb and repeat the steps above which is probably the easiest way. to use the old source "cd v4l-dvb"  and type  "make distclean". dont use the quoutes, if you have trouble understanding what i just said then just delete v4l-dvb and start from scratch at the top of the guide 

**For Karmic Users **

kernel 2.6.31 seems to mess up a lot the tuners dont work and the console is constantly flooded 

adding this line "options dvb-core dvb_powerdown_on_sleep=0" to /etc/modprobe.d/options will fix it 

**Mailing list**

Join the linuxtv mailing list and report your bugs a lot of people tend to make the mistake of reporting bugs
in a distro specific way when it actually is the code that goes into the kernel that requires appendages. ( this requires users to know the difference). not being cheeky this is an example of a bug that ubuntu developers cannot fix and requires input from v4l-dvb developers [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229879]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229879")


[http://vger.kernel.org/vger-lists.html#linux-media]("http://vger.kernel.org/vger-lists.html#linux-media")
[http://www.linuxtv.org/lists.php]("http://www.linuxtv.org/lists.php")


**Extrenal Links**

[http://turtlespond.net/scripts/dvb-t.html](http://turtlespond.net/scripts/dvb-t.html)
[http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation#Remote_Control_.28Lircd.29](http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation#Remote_Control_.28Lircd.29)
[http://forums.whirlpool.net.au/forum-replies.cfm?t=919552&p=7](http://forums.whirlpool.net.au/forum-replies.cfm?t=919552&p=7)
[http://www.ozmyth.com/wiki/Configuring+MythTV+for+Australian+Digital+TV]("http://www.ozmyth.com/wiki/Configuring+MythTV+for+Australian+Digital+TV")

---

### Post by tsharkey on 2008-03-08
Hi - This was a very useful page (particularly getting the FusionHDTV remote working). Two of the command lines got attacked by smilies when posted, they being the CVS version control commands for installing lirc. They probably should read (keeping the whole word cvsroot as well)

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
Enter
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc

Thanks for a great peice of work

---

### Post by imugli on 2008-03-27
Just want to say thanks for this! I tried every other guide I could find and this was the one that did the trick! 

Thanks heaps!

---

### Post by qhaz on 2008-04-01
I'm not sure what your script did . . . but it works!  Thank you so much.  I tried sooooo many other avenues until I was nearly googled out . . . with no luck.  So thanks again.

---

### Post by oobe-feisty on 2008-08-25
I have changed this tutorial dramatically i took out a bunch of info on testing as there are many generic dvb-t instructions around plus i stopped using a script as dd4 support is now in the main hg repo it should work again now anyone who has problems should post here

---

### Post by nagen on 2008-08-31
at last a clear and easy tutorial.....big thanx

---

### Post by itne on 2008-09-16
I hope someone can help, have been reading the many posts and tutorials for dvico dual digi 4 tuner rev 2 and remote. I have been successful through these tutorials in getting my tuner to work many thanks for that. I am struggling with remote though. I can see the input devices created on boot through dmesg i get /dev/input/event7 and /dev/input/event8 but they do not seem to receive anything when i press buttons on the remote. I have cloned  the latest v4l-dvb source and even cxusb each time the tuner works but not the remote. I am running up to date mythbuntu 8.0.4.1 with kernel 2.6.24-21 the only message visible on boot is error dvb_register (-22)

is it possible to get the remote working?

Rgs
John

---

### Post by Hellfire29 on 2008-09-18
I followed the exact steps for rev 2 of the card (except for the cd command should be cxusb) and it still doesn't work!! If any one can tell me how to fix it I would greatly appreciate it. I'm running Mythbuntu 8.04.1

---

### Post by oobe-feisty on 2008-09-19
> **Hellfire29 said:**
> I followed the exact steps for rev 2 of the card (except for the cd command should be cxusb) and it still doesn't work!! If any one can tell me how to fix it I would greatly appreciate it. I'm running Mythbuntu 8.04.1

i really cant help you as you have not given much info on your situation all i can suggest is that you perhaps try an older revision of the cxusb tree perhaps the the day rev 2 support was added or you compile a vanilla kernel and try again i dont own a rev 2 and cannot give good support on it really im basing what i wrote reguarding rev2 on the whirlpool thread that i added to external links

can you see /dev/dvb "ls /dev/dvb/*"  

does dmesg say anything 

"dmesg | grep DVB"
"dmesg | grep dvb"
dmesg | grep error"

---

### Post by oobe-feisty on 2008-09-19
> **itne said:**
> I hope someone can help, have been reading the many posts and tutorials for dvico dual digi 4 tuner rev 2 and remote. I have been successful through these tutorials in getting my tuner to work many thanks for that. I am struggling with remote though. I can see the input devices created on boot through dmesg i get /dev/input/event7 and /dev/input/event8 but they do not seem to receive anything when i press buttons on the remote. I have cloned  the latest v4l-dvb source and even cxusb each time the tuner works but not the remote. I am running up to date mythbuntu 8.0.4.1 with kernel 2.6.24-21 the only message visible on boot is error dvb_register (-22)

is it possible to get the remote working?

Rgs
John

can you see somthing like this " input: IR-receiver inside an USB DVB receiver as /class/input/input6"
when you type "dmesg | grep IR-rec" ?

what steps have you taken to test the device?

what lircd.conf files are you using?

have you looked at the whirlpool thread i left?

or the old mythtv wiki dvico thread as that thread is still relevant in terms of making a functional lircd.conf that is how i made mine that i have attached? 

does your remote look anything like the picks i have linked? 

if you are already using a working lircd.conf then you may need to go over the steps to link your /dev/input correctly

im happy to work this out with you im particularly interested in getting working lirc configs for the rev2 to add to this thread the linked lircd files are both known to work 
with rev one and the whirpool thread i linked contains someones working rev 2 lircd.conf once you get this fixed with or without my help i would appreciate you linking your working configs and how you remedied the situation so i can update this thread


EDIT: i think the reason the remote is not working is because in dmesg your remote device makes different text out put to this line 

"IR-receiver inside an USB DVB receiver" 

you need to do " dmesg | grep IR " or dmesg | grep IR-rec to find out if it is different then you need to modifiy the line you added in 

/etc/udev/rules.d/60-symlinks.rules

to KERNEL=="event*",SYSFS{name}=="Whatever rev2 now says in dmesg",SYMLINK="input/irremote"

and make sure you have REMOTE_DEVICE="/dev/input/irremote" in your /etc/lirc/hardware.conf

---

### Post by wombo on 2008-09-26
After Ubuntu / Mythbuntu 8.10 will we still need to do this? or will it all be included in the release.

Im hoping to do a rebuild after 8.10 and finally use this tuner that is sitting in the cupboard.

---

### Post by oobe-feisty on 2008-09-27
> **wombo said:**
> After Ubuntu / Mythbuntu 8.10 will we still need to do this? or will it all be included in the release.

Im hoping to do a rebuild after 8.10 and finally use this tuner that is sitting in the cupboard.


it will eventually be supported in the kernel rev1 got included in 2.6.25.x but it got broken by some changes in v4l-dvb that got merged into 2.6.26.x now im anticipating that rev 1 support will be in 2.6.27.x but i dont really now how long it takes for a project's current code to be merged as for rev2 not for at least 12 months and longer for ubuntu to be using a kernel that has its support as there release cycle starts working with a new kernel every 6 months personally i dont think its that big of deal to follow the steps i wrote but i love it when stuff works auto magically

---

### Post by mjpaton on 2008-09-30
> **oobe-feisty said:**
> **Driver Installation**

**Rev 2 is now supported ** 
 
thanks to Anton Blanchard
until it is has been merged into tip. follow the steps above except change the hg clone address to 

hg clone [http://linuxtv.org/hg/~mkrufky/cxusb](http://linuxtv.org/hg/~mkrufky/cxusb) 

rev 2 does not require firmware


Hey, thanks for the guide. I've had my Dual Digital 4 rev 2 working for a few weeks now following the instructions from Whirlpool.

However, I've now run into problems in that it picks up the card but does not pick up the tuners. I thought it may be related to a kernel update - does this make sense? I went to follow these steps again, however the cxusb tree appears to have disappeared from linuxtv.org ...

Do you have any advice?

Thanks,

Matt

uname -r
2.6.26.3-29.fc9.i686

dmesg | grep usb (edited)
usb 2-1: new high speed USB device using ehci_hcd and address 2
usb 2-1: configuration #1 chosen from 1 choice
usb 2-1: New USB device found, idVendor=0fe9, idProduct=db98
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=4
usb 2-1: Product: Bluebird
usb 2-1: Manufacturer: Dvico
usb 2-1: SerialNumber: 0000bea0
usb 2-2: new high speed USB device using ehci_hcd and address 3
usb 2-2: configuration #1 chosen from 1 choice
usb 2-2: New USB device found, idVendor=0fe9, idProduct=db98
usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=4
usb 2-2: Product: Bluebird
usb 2-2: Manufacturer: Dvico
usb 2-2: SerialNumber: 00003ea0

dmesg | grep dvb
(nothing returned)

lsusb
Bus 002 Device 003: ID 0fe9:db98 DVICO 
Bus 002 Device 002: ID 0fe9:db98 DVICO

no /dev/dvb/ ...

---

### Post by mjpaton on 2008-09-30
> **mjpaton said:**
> Hey, thanks for the guide. I've had my Dual Digital 4 rev 2 working for a few weeks now following the instructions from Whirlpool.

However, I've now run into problems in that it picks up the card but does not pick up the tuners. I thought it may be related to a kernel update - does this make sense? I went to follow these steps again, however the cxusb tree appears to have disappeared from linuxtv.org ...

Do you have any advice?

Thanks,

Matt


so .... getting the latest tree ([http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)) rather than the cxusb tree fixed me up ... possibly worth updating in the guide?

---

### Post by oobe-feisty on 2008-09-30
> **mjpaton said:**
> so .... getting the latest tree ([http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)) rather than the cxusb tree fixed me up ... possibly worth updating in the guide?

ok thanks for letting me know

---

### Post by jalapeno on 2008-10-13
Hi,

I have a i386 Ubuntu 8.10 box with a DVICO FusionHDTV DVB-T Dual Digital 4 card, revision 1. I performed the following steps to install the driver:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make && make install
fetch the firmware file xc3028-v27.fw and install it in /lib/firmware .
modprobe dvb-usb-cxusb

The results are as follows:
[LIST]
[*] I can tune to channels and use MythTV to watch/record programs.
[*] gdm's autologin feature is disabled
[*] MythTV's shutdown button disappears, and gdm's shutdown button just causes the system to return to the gdm login screen.
[*] System stability is reduced (seems pretty stable before this change)
[*] I saw a kernel panic once while rebooting after pressing the reset button.
[*] Wife Acceptance Factor goes way down :-(
[/LIST]
I have tried building the driver twice, with two different versions of the v4l-dvb Mercurial repository, from 5 Oct 2008 and 13 Oct 2008, both with the same results (as described above).

I can reverse these symptoms by un-installing the v4l-dvb modules:

/etc/init.d/mythtv-backend stop
cd v4l-dvb
make rmmod
make rminstall
reboot

So, it would be useful for me to know 
1) Can anyone else reproduce any of these symptoms, or am I alone here?
2) What the latest working version of the driver is for rev1 cards, and how to retrieve a particular revision/date using Mercurial.

Thanks,
jalapeno.

---

### Post by oobe-feisty on 2008-10-14
im guessing your problems have nothing to do with the driver i really cant say that for sure and dont have any suggestions for you in regards to what you need to check

EDIT: i noticed you are using 8.10 which is beta still may i suggest you try 8.04.1 as its known as stable and has 
a 3 year support cycle


> **jalapeno said:**
> Hi,

I have a i386 Ubuntu 8.10 box with a DVICO FusionHDTV DVB-T Dual Digital 4 card, revision 1. I performed the following steps to install the driver:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make && make install
fetch the firmware file xc3028-v27.fw and install it in /lib/firmware .
modprobe dvb-usb-cxusb

The results are as follows:
[LIST]
[*] I can tune to channels and use MythTV to watch/record programs.
[*] gdm's autologin feature is disabled
[*] MythTV's shutdown button disappears, and gdm's shutdown button just causes the system to return to the gdm login screen.
[*] System stability is reduced (seems pretty stable before this change)
[*] I saw a kernel panic once while rebooting after pressing the reset button.
[*] Wife Acceptance Factor goes way down :-(
[/LIST]
I have tried building the driver twice, with two different versions of the v4l-dvb Mercurial repository, from 5 Oct 2008 and 13 Oct 2008, both with the same results (as described above).

I can reverse these symptoms by un-installing the v4l-dvb modules:

/etc/init.d/mythtv-backend stop
cd v4l-dvb
make rmmod
make rminstall
reboot

So, it would be useful for me to know 
1) Can anyone else reproduce any of these symptoms, or am I alone here?
2) What the latest working version of the driver is for rev1 cards, and how to retrieve a particular revision/date using Mercurial.

Thanks,
jalapeno.

---

### Post by jalapeno on 2008-10-16
Hi,

Sorry, I did say 8.10, didn't I... My mistake, its 8.04, fully updated except for the new kernel from a few days ago. I'll put that mistake down to late night hacking...

I was very surprised at the symptoms, given that it is installing a set of kernel modules that causes it. However, removing them definitely cures my system of the described login/shutdown symptoms.

I'll hassle the mailing lists over at linuxtv.org. Unfortunately, I expect them to tell me to try a vanilla kernel.org kernel...

Thanks for trying,
jalapeno.

---

### Post by oobe-feisty on 2008-10-18
> **jalapeno said:**
> Hi,

Sorry, I did say 8.10, didn't I... My mistake, its 8.04, fully updated except for the new kernel from a few days ago. I'll put that mistake down to late night hacking...

I was very surprised at the symptoms, given that it is installing a set of kernel modules that causes it. However, removing them definitely cures my system of the described login/shutdown symptoms.

I'll hassle the mailing lists over at linuxtv.org. Unfortunately, I expect them to tell me to try a vanilla kernel.org kernel...

Thanks for trying,
jalapeno.


im afraid i use a vanilla kernel myself i cant really say what works and what doesn't with the ubuntu one however i have the version number of v4l-dvb here that i last used and known to work ok 

[http://linuxtv.org/hg/v4l-dvb/rev/38a147f457e5](http://linuxtv.org/hg/v4l-dvb/rev/38a147f457e5)

and 

[http://linuxtv.org/hg/v4l-dvb/rev/a4843e1304e6](http://linuxtv.org/hg/v4l-dvb/rev/a4843e1304e6)

both worked ok for me

---

### Post by oobe-feisty on 2008-10-18
just a question i forgot to ask if you are using re1 or rev2

sorry i read your post again and your using rev1 dont worry about answering that try the tree's i posted

---

### Post by bayvista on 2008-10-20
Firstly, many thanks for your excellent notes. I have a Rev 2 Tuner and have got a mplayer picture using an indoor aerial. A couple of things I could not get to work:

cp channels.conf /etc ~/.tzap

Is this a typo? I ended up copying the channels.conf file to /etc/.tzap and then

tzap -c /etc/.tzap/channels.conf -r "SBS"

Is this correct? Also, how do you stop tzap?. How do you SU back to normal user?

I'll carry on now and try and get the remote working.

---

### Post by oobe-feisty on 2008-10-20
> cp channels.conf /etc ~/.tzap


is meant to copy channels.conf to /etc/ and your .tzap folder in you home dir

yes you are correct it should be like "cp channels.conf /etc && cp channels.conf ~/.tzap" i will update 

tzap -c /etc/.tzap/channels.conf -r "SBS" is unecessary as it will default to the channels conf in your home dir the -c option specifys where the config goes if not given it will default to the path you are already specifying  

tzap -r "SBS" is all you need 


also you can just stop tzap by pressing ctl+c you can SU back to normal user 

by simply typing exit or su - username or su username without the - the - gives you a fresh shell without the - you will become the user in the same working directory.

 i hope this helps regards

---

### Post by Jimwah on 2008-11-02
> **wombo said:**
> After Ubuntu / Mythbuntu 8.10 will we still need to do this? or will it all be included in the release.


I installed Mythbuntu 8.10 this weekend and I thought I'd share the results regarding support for the DVICO dual digital 4 (Rev2). So, it complained about not having xc3028-v27.fw (which I've seen in other forums). I dropped in the one I got here and it stopped complaining about it at least. 

Using mythtv I could scan for channels and it picked them all up okay. Then when I went to watch TV, the picture seemed laggy and there was no sound. This was the same on all channels and both tuners.

Figuring the v4l-dvb drivers may not be the most recent, I grabbed the source and followed the steps in this thread. Now tzap can't find any channels at all (neither can MythTV). 

I should note that using the first post in this thread the card was working fantastically in 8.04, so I'm going to go back to it. It's a shame because there's some nice things about 8.10, but I've also been having trouble with ndiswrapper (WG311). I think I'll consider upgrading again once support is built-in and bulletproof

---

### Post by askvictor on 2008-11-03
I've just installed a fresh mythbuntu 8.10 box, using a DD4 rev 1. You no longer need to compile anything! woohoo! But you do need the firmware - didn't realise this at first and tried the old australian firmware without success. But just drop the file attached to the first post into /lib/firmware and you're away!

I still haven't got the remote working completely, but will advise what happened and why when I get it going.

(btw, why the need to tar a single file i.e. the firmware? just use bzip2)

---

### Post by askvictor on 2008-11-03
Alright; I just got my remote working after a bit of a struggle. The problem symptoms were (after following all aforementioned instructions, and comparing with my previously working setup): the number keys and arrow keys worked fine, but nothing else did. Somewhere along the way, linux was interpreting those keys as keyboard presses, and that's about it. lirc wasn't getting a chance to intercept the signal. So a quick bit of digging led me to the file /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi which should look something like:
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>

```
There was no reference to "saa7134 ir" in any of my devices, so I found the info.product for my device by running 'hal-devices' and found it was "IR-receiver inside an USB DVB receiver" (incidentally the same as what is mentioned in dmesg). And I changed lirc.fdi to look like:
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>
```

Then I rebooted. 

And it was good.

---

### Post by oobe-feisty on 2008-11-03
askvictor can you do me a favour and check your Xorg logs for any mention of the IR-reciever when i upgraded to 8.10 hal misconfigured my remote reciever to and it ended up crashing x as it interpreted it as a input device like a mouse 

the results of these 2 commands would be much appreciated

cat /var/log/Xorg.0.log | grep IR

and 
cat /var/log/Xorg.0.log | grep DVB

---

### Post by askvictor on 2008-11-03
> **oobe-feisty said:**
> askvictor can you do me a favour and check your Xorg logs for any mention of the IR-reciever when i upgraded to 8.10 hal misconfigured my remote reciever to and it ended up crashing x as it interpreted it as a input device like a mouse 

the results of these 2 commands would be much appreciated

cat /var/log/Xorg.0.log | grep IR

and 
cat /var/log/Xorg.0.log | grep DVB

Nothing turns up in either of them after the HAL modification detailed in my previous post. But if I revert to my original HAL setup I get the following for both commands:
```
(II) config/hal: Adding input device IR-receiver inside an USB DVB receiver
(**) IR-receiver inside an USB DVB receiver: always reports core events
(**) IR-receiver inside an USB DVB receiver: Device: "/dev/input/event6"
(II) IR-receiver inside an USB DVB receiver: Found keys
(II) IR-receiver inside an USB DVB receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD)
(**) IR-receiver inside an USB DVB receiver: xkb_rules: "evdev"
(**) IR-receiver inside an USB DVB receiver: xkb_model: "pc105"
(**) IR-receiver inside an USB DVB receiver: xkb_layout: "us"
(WW) IR-receiver inside an USB DVB receiver: unable to handle keycode 352
```

Seems to be the same problem I was having (though mine wasn't crashing X); get HAL to ignore the device as described above.

btw, the pedant in me feels obliged to point out that 'cat foo | grep bar' can be more efficiently (both in terms of typing and processes spawned (since memory is so precious ;)) be written as 'grep bar foo'

---

### Post by oobe-feisty on 2008-11-04
> Seems to be the same problem I was having (though mine wasn't crashing X); get HAL to ignore the device as described above.

btw, the pedant in me feels obliged to point out that 'cat foo | grep bar' can be more efficiently (both in terms of typing and processes spawned (since memory is so precious ;)) be written as 'grep bar foo'

thanks heaps for this i will try upgrading again next weekend only thing i will miss is kde3 i backed up before my upgrade then restored after i couldnt solve this

---

### Post by Mitch72 on 2008-11-06
Is [this]("http://www.austin.net.au/ProductList/ProductDetail/tabid/104/ProductCode/VC-DVICO-DUAL4/Default.aspx") card supported? I was just looking around for prices etc, and noticed the "Rev 4" in the description line... I assumed rev 2 was the latest. Am I misreading it, or is it another revision? If it is, does anyone have any experience with it?

Cheers, Mitch

---

### Post by oobe-feisty on 2008-11-06
> **Mitch72 said:**
> Is [this]("http://www.austin.net.au/ProductList/ProductDetail/tabid/104/ProductCode/VC-DVICO-DUAL4/Default.aspx") card supported? I was just looking around for prices etc, and noticed the "Rev 4" in the description line... I assumed rev 2 was the latest. Am I misreading it, or is it another revision? If it is, does anyone have any experience with it?

Cheers, Mitch

im sorry i dont think it would be however i think its nice they warn you in the description as a lot of ppl bought rev2 tuners before it was supported without warning

---

### Post by Mitch72 on 2008-11-06
woah thanks for the fast response! Yeah, that's what I thought- pity, seems like a good card from what I've heard- good price considering it's got the dual tuners... I'll have to keep an eye out for an older one. Thanks for the help :-P

---

### Post by askvictor on 2008-11-09
Could be that they mistake the 4 in "Dual Digital 4" for revision 4 of the Dual Digital series. There was, I think, a dual digital 1 and 2.

---

### Post by oobe-feisty on 2008-11-09
> **askvictor said:**
> Could be that they mistake the 4 in "Dual Digital 4" for revision 4 of the Dual Digital series. There was, I think, a dual digital 1 and 2.

you might be right about that however i would prefer to buy from retailers with accurate and specific info about my hardware. i havent heard of a rev 4 either nor a rev 3

---

### Post by jmkortsch on 2008-11-13
So this might be a little bit of a change of focus for this thread..always a bad sign right  :) 

But I just installed the DViCO HDTV5 USB Gold which has an IR receiver on the unit.  The tuner side is working fine, but i was wondering whether I can get the IR receiver to work with a different remote than what originally came with the package. (the guy I bought it from had lost the remote).

I actually have a MCE remote, but without the IR receiver.  Could I use this remote with the DViCO receiver? I've tried everything I can think of, but neither evtest, nor irw is returning any results.

I'm running Mythbuntu 8.10.

Thanks for any thoughts.
Jon-Marc

---

### Post by wombo on 2008-11-13
> **jmkortsch said:**
> So this might be a little bit of a change of focus for this thread..always a bad sign right  :) 

But I just installed the DViCO HDTV5 USB Gold which has an IR receiver on the unit.  The tuner side is working fine, but i was wondering whether I can get the IR receiver to work with a different remote than what originally came with the package. (the guy I bought it from had lost the remote).

I actually have a MCE remote, but without the IR receiver.  Could I use this remote with the DViCO receiver? I've tried everything I can think of, but neither evtest, nor irw is returning any results.

I'm running Mythbuntu 8.10.

Thanks for any thoughts.
Jon-Marc

Could you please start a new thread as that is a very different card from the DViCO FusionHDTV DVB-T Dual Digital 4.

---

### Post by askvictor on 2008-11-15
I've discovered a problem with my setup - the second tuner on the card doesn't lock onto channels. The config is identical for both tuners, but when one thing is recording and I try to watch something else, it fails to get a lock. 

I can tune two different channels simultaneously outside myth (e.g using mplayer or vlc)

If I shut down myth backend, then run tzap on the second tuner to tune to any channel, it gets a lock, and then if I start myth it works fine. But if I try to do this before myth starts (as a startup script) tzap won't get a lock.

Any thoughs? 

I'll get my progress posted.

---

### Post by sledski on 2008-11-15
Hi guys,

Firstly, thankyou for such a great guide. This proved invaluable in getting my card up and running however I'm having a few problems getting my remote to work properly within MythTV. 
I've stepped through this guide a couple of times so far to no avail. I'm hoping someone might be able to give me a hand finding what the problem might be.

My issue is this, within MythTV the keys on my remote do not appear to be mapped correctly. It appears as though the remote is functioning as the up/down/left/right arrows function and I am able to navigate my way through menu's and scroll up and down through channels etc. I am able to turn the system volume up and down with the volume buttons (yes the system volume and not MythTV's volume) however no other keys are working.

My remote matches the photo of lirc1 so I downloaded that file and followed the instructions to place the files.

lsusb gives this:
```
bobby@loque:~/.mythtv$ lsusb
Bus 011 Device 003: ID 0fe9:db78 DVICO 
Bus 011 Device 002: ID 0fe9:db78 DVICO 
Bus 011 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

dmesg | grep IR looks like this:
```
bobby@loque:~/.mythtv$ dmesg | grep IR
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.388196] ENABLING IO-APIC IRQs
[    0.560612] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.560612] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.560612] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.560612] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.560689] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.560821] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.560952] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.561084] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.564542] PCI: Using ACPI for IRQ routing
[    0.572098] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.615367] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.615381] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.789924] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.272632] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.376264] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.483317] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.688315] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.916257] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.020211] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.124207] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.228276] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.352227] uhci_hcd 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.560792] uhci_hcd 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.768222] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.768586] eth0: RTL8168c/8111c at 0xf8884000, 00:1f:d0:2e:50:51, XID 3c4000c0 IRQ 221
[    3.771375] ehci_hcd 0000:03:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.010075] ohci1394 0000:03:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.059796] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e2004000-e20047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.063845] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.063907] pata_acpi 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.063953] pata_acpi 0000:03:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.068873] pata_it8213 0000:03:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.287743] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.127243] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.513642] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.504435] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:03:00.2/usb11/11-1/input/input6
[   16.518364] cx8800 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.625002] cxusb: No IR receiver detected on this device.
[   16.977701] input: cx88 IR (Leadtek Winfast 2000XP as /devices/pci0000:00/0000:00:1e.0/0000:03:01.0/input/input7
[   37.538360] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

```

/etc/udev/rules.d/60-symlinks.rules looks like:
```
# This file establishes user-friendly symlinks to devices according to
# Ubuntu policy.  See udev(7) for syntax.
#
# The names of the actual devices themselves must not be set here, but
# in 20-names.rules; the permissions and ownership of those devices
# should be set in 40-permissions.rules.

# Compatibility symlinks for /dev/scd* devices
SUBSYSTEMS=="scsi", KERNEL=="sr[0-9]*",	SYMLINK+="%k"

# Compatibility symlinks for USB printers
SUBSYSTEMS=="usb", KERNEL=="lp[0-9]*",  SYMLINK+="usb%k"

# Compatibility symlink for the CMOS RTC
SUBSYSTEM=="rtc", DRIVERS=="rtc_cmos", SYMLINK+="rtc"

# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
					SYMLINK+="pilot"

# Reverse mapping for /sys/dev
SUBSYSTEM=="block", SYMLINK+="block/%M:%m"
SUBSYSTEM!="block", SYMLINK+="char/%M:%m"

KERNEL=="event*",SYSFS{name}=="IR-receiver inside an USB DVB receiver",SYMLINK="input/irremote"
```

/etc/lirc/lircd.conf looks like:
```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3-CVS(devinput) on Sun Nov 18 05:44:43 2007
#
# contributed by Kemble Wagner
#
# brand: DViCO FusionHDTV DVB-T Dual Digital 4 
# model no. of remote control: Fusion REMOTE MCE
# controlled by this remote:DViCO FusionHDTV DVB-T Dual Digital 4 

begin remote

  name  DViCO_Dual_Digital
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x1
  gap          203977
  toggle_bit_mask 0x16000000
  toggle_bit      0

      begin codes
          start                    0x001C
          ok                       0x0160
          left                     0x0069
          right                    0x006A
          down                     0x006C
          up                       0x0067
          back                     0x009E
          guide                    0x016D
          tvpower                  0x0164
          more-i                   0x0166
          alttab                   0x000F
          replay                   0x00A5
          voldn                    0x0072
          volup                    0x0073
          dtv                      0x0179
          mp3                      0x0187
          dvd                      0x0185
          cpf                      0x016C
          skip                     0x00A3
          replay                   0x00A5
          camera                   0x00D4
          live                     0x0182
          folder                   0x0086
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          aspect                   0x0173
          zoom                     0x0174
          rew                      0x00A8
          playpause                0x00A4
          ff                       0x00D0
          mute                     0x0071
          stop                     0x0080
          rec                      0x00A7
          power                    0x0074
          live                     0x0182
          dvdmenu                  0x008B
          setup                    0x008D
          chup                     0x0192
          chdn                     0x0193
          0                        0x000B
end codes

end remote
```

/home/bobby/.mythtv/lircrc looks like:
```
#
#
#
# 
# 
#
# Save this file in ~/.mythtv/lircrc
#
# You will also need to make a few changes to the MythTV key bindings and jump
# points as follows.
#
# Jump Points:
#
#   TV Recording Playback:                      Alt+R
#   Program Guide:                              Alt+G
#   Live TV:                                    Alt+P
#   MythVideo -> The MythVideo default view:    Alt+V
#   Main Menu:                                  Alt+Home
#   DVD Menu:                                   Alt+D
#   DVD Title Menu:                             Alt+Q
# Key Bindings:
#
#   TV Playback -> CHANNELDOWN:  Down,PgDown
#   TV Playback -> CHANNELUP:    Up,PgUp
#   TV Playback -> JUMPRWND:     Shift+PgUp
#   TV Playback -> JUMPFFWD:     Shift+PgDown
#

###################################################################
# Begin of mythtv key bindings.
##

#
# Program Navigation
#

begin
    prog   = mythtv
    button = start
    config = Alt+Home
end

begin
    prog   = mythtv
    button = rec
    config = Alt+R
end

begin
    prog   = mythtv
    button = guide
    config = Alt+G
end

begin
    prog   = mythtv
    button = dtv
    config = Alt+P
end

begin
    prog   = mythtv
    button = tvpower
    config = Alt+P
end


begin
    prog   = mythtv
    button = cpf
    config = Alt+V
end

begin
    prog   = mythtv
    button = dvd
    config = Alt+D
end

begin
    prog   = mythtv
    button = dvdmenu
    config = Alt+Q
end



#
# Menu Navigation
#

begin
    prog   = mythtv
    button = back
    config = Esc
end

begin
    prog   = mythtv
    button = aspect
    config = W
end

begin
    prog   = mythtv
    button = ok
    config = Space
end

begin
    prog   = mythtv
    button = more-i
    config = i
end

begin
    prog   = mythtv
    button = left
    config = Left
end

begin
    prog   = mythtv
    button = right
    config = Right
end

begin
    prog   = mythtv
    button = up
    config = Up
end

begin
    prog   = mythtv
    button = down
    config = Down
end

#
# TV Control
#

begin
    prog   = mythtv
    button = voldn
    config = F10
end

begin
    prog   = mythtv
    button = volup
    config = F11
end

begin
    prog   = mythtv
    button = mute
    config = F9
end

begin
    prog   = mythtv
    button = chdn
    config = Down
end

begin
    prog   = mythtv
    button = chup
    config = Up
end

begin
    prog   = mythtv
    button = live
    config = V
end

begin
   prog   = mythtv
    button = folder
    config = B
end

begin
    prog   = mythtv
    button = alttab
    config = N
end

begin
    prog   = mythtv
    button = camera
    config = Y
end








#
# Video Navigation
#
begin
    prog   = mythtv
    button = playpause
    config = P
end

begin
    prog   = mythtv
    button = Stop
    config = Esc
end

begin
    prog   = mythtv
    button = ff
    config = Z+End
end

begin
    prog   = mythtv
    button = rew
    config = Q+Home
end

begin
    prog   = mythtv
    button = replay
    config =  <
end

begin
    prog   = mythtv
    button = skip
    config = >
end

begin
    prog   = mythtv
    button = rec
    config = R
end



#
# Miscellaneous
#

# M for Menu
begin
    prog   = mythtv
    button = setup
    config = M
end

begin
  prog = irexec
  button = start
  config = start-myth&
end

begin
    prog = irexec
    button = power
    config = /usr/local/bin/monitorpowerbutton.sh
end

begin
    prog   = mythtv
    button = mp3
    config = Alt+8
end
begin
    prog   = mythtv
    button = fullscreen
    config = Alt+S
end


#begin
#   prog = irexec
#   button = *
#   config = xset dpms force on &
#end

#
# Numbers
#

begin
    prog   = mythtv
    button = 0
    config = 0
end

begin
    prog   = mythtv
    button = 1
    config = 1
end

begin
    prog   = mythtv
    button = 2
    config = 2
end

begin
    prog   = mythtv
    button = 3
    config = 3
end

begin
    prog   = mythtv
    button = 4
    config = 4
end

begin
    prog   = mythtv
    button = 5
    config = 5
end

begin
    prog   = mythtv
    button = 6
    config = 6
end

begin
    prog   = mythtv
    button = 7
    config = 7
end

begin
    prog   = mythtv
    button = 8
    config = 8
end

begin
    prog   = mythtv
    button = 9
    config = 9
end

##
# End of mythtv key bindings.
##

###################################################################
# Begin of mplayer key bindings.
##

begin
 prog = mplayer
 button = back
 config = quit
end

begin
 prog = mplayer
 button = more-i
 config = osd
end

begin
 prog = mplayer
 button = replay
 config = seek -10
 repeat = 1
end

begin
 prog = mplayer
 button = rew
 config = seek -10
 repeat = 1
end

begin
 prog = mplayer
 button = skip
 config = seek +10
 repeat = 1
end

begin
 prog = mplayer
 button = ff
 config = seek +10
 repeat = 1
end

begin
 prog = mplayer
 button = left
 config = seek -60
 repeat = 1
end

begin
 prog = mplayer
 button = right
 config = seek +60
 repeat = 1
end

begin
 prog = mplayer
 button = playpause
 config = pause
end

begin
 prog=mplayer
 button=mute
 config=mute
end
begin
    prog   = mplayer
    button = voldn
    config = volume -1
end

begin
    prog   = mplayer
    button = volup
    config = volume 1
end




##
# End of mplayer key bindings.
##

##
# Start of Kaffeine bindings

begin
    prog   = irexec
    button = playpause
    config = dcop kaffeine KaffeineIface pause
end

begin
    prog   = irexec
    button = ok
    config = dcop kaffeine KaffeineIface dvbOSD
end

begin
    prog = irexec
    button = stop
    config = dcop kaffeine KaffeineIface stop
end

begin
    prog = irexec
    button = skip
    config = dcop kaffeine KaffeineIface posPlus
end

begin
    prog = irexec
    button = replay
    config = dcop kaffeine KaffeineIface posMinus
end

begin
    prog = irexec
    button = up
    config = dcop kaffeine KaffeineIface next
end

begin
     prog = irexec
     button = down
     config = dcop kaffeine KaffeineIface previous
end

begin
     prog = irexec
     button = power
     config = dcop kaffeine KaffeineIface quit
end

begin
     prog = irexec
     button = volup
     config = dcop kaffeine KaffeineIface volUp
end

begin
        prog = irexec
        button = mute
        config = dcop kaffeine KaffeineIface mute
end
begin
        prog = irexec
        button = voldn
        config = dcop kaffeine KaffeineIface volDown
end
begin
        prog = irexec
        button = tvpower
        config = dcop kaffeine KaffeineIface fullscreen
end
begin
        prog = irexec
        button = chup
        config = dcop kaffeine KaffeineIface dvbOSDNextChannel
end
begin
        prog = irexec
        button = chdn
        config = dcop kaffeine KaffeineIface dvbOSDPreviousChannel
end
begin
        prog = irexec
        button = left
        config = dcop kaffeine KaffeineIface dvbOSDNextProgram
end
begin
        prog = irexec
        button = right
        config = dcop kaffeine KaffeineIface dvbOSDPreviousProgram
end
begin
        prog = irexec
        button = 1
        config = dcop kaffeine KaffeineIface setNumber 1
   repeat = 0
end
begin
        prog = irexec
        button = 2
        config = dcop kaffeine KaffeineIface setNumber 2
   repeat = 0
end
begin
        prog = irexec
        button = 3
        config = dcop kaffeine KaffeineIface setNumber 3
   repeat = 0
end
begin
        prog = irexec
        button = 4
        config = dcop kaffeine KaffeineIface setNumber 4
   repeat = 0
end
begin
        prog = irexec
        button = 5
        config = dcop kaffeine KaffeineIface setNumber 5
   repeat = 0
end
begin
        prog = irexec
        button = 6
        config = dcop kaffeine KaffeineIface setNumber 6
   repeat = 0
end
begin
        prog = irexec
        button = 7
        config = dcop kaffeine KaffeineIface setNumber 7
   repeat = 0
end
begin
        prog = irexec
        button = 8
        config = dcop kaffeine KaffeineIface setNumber 8
   repeat = 0
end
begin
        prog = irexec
        button = 9
        config = dcop kaffeine KaffeineIface setNumber 9
   repeat = 0
end
begin
        prog = irexec
        button = 0
        config = dcop kaffeine KaffeineIface setNumber 0
   repeat = 0
end

begin
prog = irexec
button = aspect
config = dcop kaffeine XinePartIface zoomIn
end

begin
prog = irexec
button = zoom
config = dcop kaffeine XinePartIface zoomOut
end




## end of kaffeine bindings
```

This is a pretty fresh install of Ubuntu 8.10. If anyone has any ideas your assistance would be greatly appreciated

---

### Post by askvictor on 2008-11-16
sledski; did you try the directions in [this post]("http://ubuntuforums.org/showthread.php?p=6093982#post6093982") ?

---

### Post by sledski on 2008-11-19
> **askvictor said:**
> sledski; did you try the directions in [this post]("http://ubuntuforums.org/showthread.php?p=6093982#post6093982") ?

Thanks Askvictor you're a super star. Works like a charm.

---

### Post by askvictor on 2008-11-20
> **askvictor said:**
> I've discovered a problem with my setup - the second tuner on the card doesn't lock onto channels. The config is identical for both tuners, but when one thing is recording and I try to watch something else, it fails to get a lock. 


So I've managed to fix this by running the backend setup, going into one of the capture cards (I ended up doing this on both, but it might work for just one of them), then 'Recording Options', then selecting 'Open DVB card on demand' and de-selecting 'Use DVB Card for active EIT scan'. It is possible that this can be fixed by just deactivating active EIT scan, but I haven't tried.

---

### Post by tvars on 2008-11-21
Hi,

Thanks for the guide, it got my Fusion DD4 tuner working great on Mythbuntu 8.10. Now I'm stuck trying to get the remote to work! I have one of [these]("http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg").

The problem I have is that only a few keys in the remote work (arrow keys, enter key) and they are obviously not being interpreted by lirc because when I stop lirc the keys still work.

I followed the guide exactly, including the step about modifying /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi as suggested by askvictor.

One thing that looks kind of different in my system is that the device is reported by dmesg as "/devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb5/5-1/input/input5" rather than "/class/input/input5" as suggested by other posters. 

Any ideas?

irw doesn's print anything, irrecord times out, cat /dev/input/input5 prints nothing.

Here's some relevant prints. 

```

tom@mythbox:~$ ls -l /dev/input/
total 0
drwxr-xr-x 2 root root     60 2008-11-22 14:58 by-path
crw-rw---- 1 root root 13, 64 2008-11-22 14:58 event0
crw-rw---- 1 root root 13, 65 2008-11-22 14:58 event1
crw-rw---- 1 root root 13, 66 2008-11-22 14:58 event2
crw-rw---- 1 root root 13, 67 2008-11-22 14:58 event3
crw-rw---- 1 root root 13, 68 2008-11-22 14:58 event4
crw-rw---- 1 root root 13, 69 2008-11-22 14:58 event5
lrwxrwxrwx 1 root root      6 2008-11-22 14:58 irremote -> event5
crw-rw---- 1 root root 13, 63 2008-11-22 14:58 mice
crw-rw---- 1 root root 13, 32 2008-11-22 14:58 mouse0

tom@mythbox:~$ dmesg | grep "IR-receiver"
[   10.220648] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb5/5-1/input/input4
[   10.622795] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb5/5-2/input/input5

tom@mythbox:~$ hal-device

22: udi = '/org/freedesktop/Hal/devices/temp/92'
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_fe9_db98_000080f2'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb5/5-2/input/input5/event5'  (string)
  info.subsystem = 'input'  (string)
  info.ignore = true  (bool)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_fe9_db98_000080f2'  (string)
  info.product = 'Ignored Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ignored-device'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.product = 'IR-receiver inside an USB DVB receiver'  (string)


27: udi = '/org/freedesktop/Hal/devices/temp/87'
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_fe9_db98_000000f2'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb5/5-1/input/input4/event4'  (string)
  info.subsystem = 'input'  (string)
  info.ignore = true  (bool)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_fe9_db98_000000f2'  (string)
  info.product = 'Ignored Device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ignored-device'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.product = 'IR-receiver inside an USB DVB receiver'  (string)




```

---

### Post by tvars on 2008-11-22
Ok I fixed my remote.

Here's a summary of the problems I had.

1) I had to update /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi to stop my remote key-presses being interpreted as keyboard presses. Added the following match xml element.

```

     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>

```

2) I have two IR-receiver devices, event4 and event5. The rule to create a symlink /dev/input/irremote on boot was always picking up event5. "sudo cat /dev/input/eventX" and pressing buttons on the remote did not give any output for event5, but it did for event4. I switched my /etc/lirc/hardware.conf to point directly at event4 without going through the irremote symlink.

3) Lastly, the lircd.conf that is attached to this thread (lirc2.tar.bz2) did not match the codes for my remote. I had to record a new one using "sudo irrecord --driver=devinput --device=/dev/input/event4 lircd.conf". I've attached the resulting file to this post. I must have a newer version of this remote.

4) I had a problem with remote key presses being duplicated. irw showed two lines per keypress. I fixed this by setting "toggle_bit_mask 0x16000000" in the lircd.conf.

---

### Post by oobe-feisty on 2008-11-25
> **tvars said:**
> Ok I fixed my remote.

Here's a summary of the problems I had.

1) I had to update /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi to stop my remote key-presses being interpreted as keyboard presses. Added the following match xml element.

```

     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>

```

2) I have two IR-receiver devices, event4 and event5. The rule to create a symlink /dev/input/irremote on boot was always picking up event5. "sudo cat /dev/input/eventX" and pressing buttons on the remote did not give any output for event5, but it did for event4. I switched my /etc/lirc/hardware.conf to point directly at event4 without going through the irremote symlink.

3) Lastly, the lircd.conf that is attached to this thread (lirc2.tar.bz2) did not match the codes for my remote. I had to record a new one using "sudo irrecord --driver=devinput --device=/dev/input/event4 lircd.conf". I've attached the resulting file to this post. I must have a newer version of this remote.

4) I had a problem with remote key presses being duplicated. irw showed two lines per keypress. I fixed this by setting "toggle_bit_mask 0x16000000" in the lircd.conf.

thank you very much for this post can i ask what your remote looks like can you post a link to a photo does it look like one of the pics i have posted if so can you point it out

---

### Post by tvars on 2008-11-25
> **oobe-feisty said:**
> thank you very much for this post can i ask what your remote looks like can you post a link to a photo does it look like one of the pics i have posted if so can you point it out

My remote looks like [this one]("http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg").

---

### Post by oobe-feisty on 2008-11-26
thanks tvars i will update my attached lirc files with yours soon if you dont mind i appreciate this post as i have the old remote and have no way of supporting or testing your remote

---

### Post by Mr_Q on 2008-11-30
I have a question if anyone can help:

I have installed the card as per the OP on Mythbuntu 8.04 and 8.10 (and I previously had it working fine on 7.10).  Using tzap I can see all the channels locking correctly (and with mplayer can view them).  However within MythTV some of the channels (that scan fine) just won't lock when I try to play them back. 

Anyone have any ideas?

---

### Post by askvictor on 2008-11-30
> **Mr_Q said:**
> I have a question if anyone can help:

I have installed the card as per the OP on Mythbuntu 8.04 and 8.10 (and I previously had it working fine on 7.10).  Using tzap I can see all the channels locking correctly (and with mplayer can view them).  However within MythTV some of the channels (that scan fine) just won't lock when I try to play them back. 

Anyone have any ideas?

I'm curious if it's the same problem I experienced here:
[http://ubuntuforums.org/showthread.php?p=6188530#post6188530](http://ubuntuforums.org/showthread.php?p=6188530#post6188530)
which I fixed here:
[http://ubuntuforums.org/showthread.php?p=6215542#post6215542](http://ubuntuforums.org/showthread.php?p=6215542#post6215542)

The other thing you could try is to increase the tuning delay (I think that's what it's called) in the advanced settings for the capture card in the backend setup. I think the default values are something like 500ms and 3000ms; in previous installations I've increased them to 1000ms and 6000ms.

---

### Post by smeago1 on 2008-12-05
hi guys

first of all thanks in advance for your help.

SO i'm trying to get this cardworking and just upgraded to 8.10

ubuntu recognise the card but it seems it only sees one card. My /dev/dvb/ only sees one adapter0, and mythbackend setup only allows me to create one card.

i've posted some info below so any help is appreciated.

LSUSB

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 0fe9:db78 DVICO
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



dmesg

[   14.770760] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm                              state.
[   14.771086] dvb-usb: will pass the complete MPEG2 transport stream to the sof                             tware demuxer.
[   14.771141] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct                               1 14:43:46 PDT 2008
[   14.792055] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.802088] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital                              4)
[   14.889549] cxusb: No IR receiver detected on this device.
[   14.889557] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   14.909384] xc2028 2-0061: creating new instance
[   14.909389] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   14.910050] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initi                             alized and connected.
[   14.910092] usbcore: registered new interface driver dvb_usb_cxusb
[   16.328048] lp0: using parport0 (interrupt-driven).
[   16.548513] Adding 3012148k swap on /dev/sdb5.  Priority:-1 extents:1 across:                             3012148k

---

### Post by oobe-feisty on 2008-12-05
> **smeago1 said:**
> hi guys

first of all thanks in advance for your help.

SO i'm trying to get this cardworking and just upgraded to 8.10

ubuntu recognise the card but it seems it only sees one card. My /dev/dvb/ only sees one adapter0, and mythbackend setup only allows me to create one card.

i've posted some info below so any help is appreciated.

LSUSB

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 0fe9:db78 DVICO
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04b3:3108 IBM Corp. 800dpi Optical Mouse w/ Scroll Point
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



dmesg

[   14.770760] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm                              state.
[   14.771086] dvb-usb: will pass the complete MPEG2 transport stream to the sof                             tware demuxer.
[   14.771141] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct                               1 14:43:46 PDT 2008
[   14.792055] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.802088] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital                              4)
[   14.889549] cxusb: No IR receiver detected on this device.
[   14.889557] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   14.909384] xc2028 2-0061: creating new instance
[   14.909389] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
[   14.910050] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initi                             alized and connected.
[   14.910092] usbcore: registered new interface driver dvb_usb_cxusb
[   16.328048] lp0: using parport0 (interrupt-driven).
[   16.548513] Adding 3012148k swap on /dev/sdb5.  Priority:-1 extents:1 across:                             3012148k



read the trouble shooting part of the first post it covers this 

try shutting down you your computer as in not rebooting but shutting down that will work

---

### Post by OzDude on 2008-12-13
Howdy from a linux noob!

I'm trying to get a Rev 2 ( db98 ) card to work on Mythbuntu 8.10.

> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
But, "the specified repository "v4l-dvb" is unknown, sorry."

Where do i go now?

BTW, "lsusb" correctly displays the two DVICO devices, "dmesg|grep dvb" and "dmesg|grep error" both return nothing.

Thanks in advance,
OzDude

---

### Post by oobe-feisty on 2008-12-16
> **OzDude said:**
> Howdy from a linux noob!

I'm trying to get a Rev 2 ( db98 ) card to work on Mythbuntu 8.10.


But, "the specified repository "v4l-dvb" is unknown, sorry."

Where do i go now?

BTW, "lsusb" correctly displays the two DVICO devices, "dmesg|grep dvb" and "dmesg|grep error" both return nothing.

Thanks in advance,
OzDude


this is strange do you have mercurial installed

---

### Post by smeago1 on 2009-01-08
hi guys...

this card is driving me nuts...

i installed Vista MCE didn't work, install XP didn't work ...installed mythbuntu no love, installed mythdora no love, installed linuxmce absolutely no love.( all last night too)

Then i read this forum about 100 times and can't seem to get it working.

I do have one question i think may solve the problem.

Right now i can see one tuner only and can't get the second one to show up in any of the OS i'm using. I've concluded that it must be a PCI power issue. I have the asus a8n-sli delux board. I also noticed that on the Dvico Digital 4 card there are pins for an internal USB cable to be plugged in. Perhaps I need this to power the second USB tuner?

Can anyone tell me if they had to use the pins to plug into their mobo?

Before you ask me if i'm using the old Dvico card i can tell u now i am not! i only have the antena plug in and the remote control holes in the back of the card and my lsusb defitely tells me i have the db78 Dvico.

I will give a random homeless person $10 bucks if someone can help me to get this working :)

cheers

smeags.

---

### Post by tqft on 2009-01-09
Smeags

Have a look in Nautilus or command at 

/dev

Is there a video0, video1 maybe video2 if you have a webcam - you should have one for each card & webcam.

---

### Post by askvictor on 2009-01-09
smeago:

On my card there are three sets of jumpers. One is a switch between the two different ways to wake up the computer from the remote. One is a jumper to connect this wakeup function to the motherboard for older motherboards. The third set is undocumented. On my system I don't have anything connected to any of the jumpers, as the motherboard is recent enough to allow wakeup over PCI. Unless the undocumented jumper does something, i think you're out of luck on this front. 

First up - can I confirm that you have one tuner working properly? Under linux and windows? In an earlier post you had lsusb showing exactly one dvico device? Mine shows two.

Second - If possible, try the card in a different machine. It shouldn't be any different, but you never know your luck.

Third - if you bought the card new, I'd be considering a warranty repair/replacement.

---

### Post by smeago1 on 2009-01-11
Hi Victor,

thanks for the response.

Yes my lsusb still only shows 1 dvico db78.

Which is why i suspect the power issue. I know about the other two jumpers. One is for PME so the mobo can wake it up and my bios supports that so its not a problem. The other one is there so if u don't have pme function u can manually use the supplied cable to re-route it to the pwr switch jumpers on the mobo. 

But there is a third set of jumpers which is for the usb power and data.

I suspect my board or psu can't supply enough power via the pci slot to fire up the card so i can only see one tuner. Very odd.

i know it can't be the psu b/c i don't think i need more than 500w just to run myth. Plus i've unplugged all the hard drives and dvdroms.

I've tried two different machines already and same problem (although both are around the same time as when i bought the A8N-SLI Deluxe).

I'm going to try it on a 2008 board tonight and see what luck i get if any.

When i dmesg|grep error i get the descriptive error at -110 or something like that. I can post the exact error logs.

But yes i can get one tuner to work perfectly in all OSes including mythbuntu.

Finally, another thing that makes me think thats its a power problem is that the remote and IR receiver doesn't work under any OS and there's literature from DVICO that says these don't work unless the PIP is working ie. two usb devices detected.

I didn't put in a change request with the wife for this major change and no mythtv is killing me. 

Any suggestions or help is appreciated.

thanks

Precious.


***update****

Here's my error log

dmesg |grep error
[    5.165033] usb 3-1: device descriptor read/64, error -71
[    5.407356] usb 3-1: device descriptor read/64, error -71
[    5.732037] usb 3-1: device descriptor read/64, error -71
[    5.948028] usb 3-1: device descriptor read/64, error -71
[    6.573021] usb 3-1: device not accepting address 4, error -71
[    7.093019] usb 3-1: device not accepting address 5, error -71
[    7.719259] usb 4-1: device descriptor read/64, error -71
[    7.945027] usb 4-1: device descriptor read/64, error -71
[    8.281026] usb 4-1: device descriptor read/64, error -71
[    8.505126] usb 4-1: device descriptor read/64, error -71
[    9.129035] usb 4-1: device not accepting address 4, error -71
[    9.649048] usb 4-1: device not accepting address 5, error -71
[   25.673028] usb 4-1: device descriptor read/64, error -71
[   25.901042] usb 4-1: device descriptor read/64, error -71
[   26.236028] usb 4-1: device descriptor read/64, error -71
[   26.465035] usb 4-1: device descriptor read/64, error -71
[   27.089898] usb 4-1: device not accepting address 8, error -71
[   27.613027] usb 4-1: device not accepting address 9, error -71
[   48.429032] usb 4-1: device descriptor read/64, error -71
[   48.653020] usb 4-1: device descriptor read/64, error -71
[   48.989020] usb 4-1: device descriptor read/64, error -71
[   49.213020] usb 4-1: device descriptor read/64, error -71
[   49.841018] usb 4-1: device not accepting address 12, error -71
[   50.360033] usb 4-1: device not accepting address 13, error -71

---

### Post by marcovanb on 2009-01-13
Hi, please help as I have very little hair left.

I have run through the instructions to get the rev 1 card working in mythtv but it is not working. I'm using mythbuntu 8.10.

In mythtv-setup it says in capture card setup, when I select 'dvb dtv capture card (v3.x)':

Frontend ID: Could not get card info for card #0 subtype: unknown error

I also tried to uninstall the driver? It seems like it is locked in some way.

root@mythbuntu:~/v4l-dvb# make rmmod
make -C /root/v4l-dvb/v4l rmmod
make[1]: Entering directory `/root/v4l-dvb/v4l'
scripts/rmmod.pl unload
found 0 modules
/sbin/rmmod tuner_xc2028
ERROR: Module tuner_xc2028 is in use
/sbin/rmmod tuner_xc2028
ERROR: Module tuner_xc2028 is in use
Couldn't unload: tuner_xc2028
make[1]: Leaving directory `/root/v4l-dvb/v4l'

DMESG output 

root@mythbuntu:~/v4l-dvb# dmesg | grep DVB
[   13.776201] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   13.807454] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   14.358259] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   14.401729] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:10.0/0000:04:08.2/usb5/5-1/input/input4
[   14.432522] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   14.432538] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   14.463811] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   14.512544] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[   14.513284] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected

LSMOD

root@mythbuntu:~/v4l-dvb# lsmod | grep dvb
dvb_usb_cxusb          43524  0 
dib7000p               24584  1 dvb_usb_cxusb
dvb_usb                27660  1 dvb_usb_cxusb
dvb_core               94208  1 dvb_usb
dib0070                15620  1 dvb_usb_cxusb
i2c_core               31892  8 tuner_xc2028,zl10353,dib7000p,dibx000_common,dvb_usb,dib0070,i2c_nforce2,nvidia
usbcore               148848  6 dvb_usb_cxusb,dvb_usb,ehci_hcd,uhci_hcd,ohci_hcd

SOME OUTPUT FROM TEST ON FIRST PAGE.

nmagers@mythbuntu:~$ mplayer /dev/dvb/adapter/dvr0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/dvb/adapter/dvr0.
File not found: '/dev/dvb/adapter/dvr0'
Failed to open /dev/dvb/adapter/dvr0.


Exiting... (End of file)
nmagers@mythbuntu:~$ 



Thanks in advance.

---

### Post by askvictor on 2009-01-14
marcovanb: 

In ubuntu 8.10 you shouldn't need to any drivers - they are part of the shipped kernel. You do however need the australian firmware file (if you're in australia) that is attached to the original post. There are also hints deep inside this thread for getting the remote to work properly if you need. 

I assume you've tried compiling from mercurial sources? Not quite sure how to get rid of that - try 'make uninstall' and reboot? That might get rid of the compiled modules, then it can't load them next boot as they don't exist... If it can't unload the module then something is using it - perhaps you have mythtv running? Or some other module is dependent on it, but I would have guessed the script would take care of those dependencies. I really don't know how the modules compiled from source interact with existing modules, but if you're on a fresh install it might just be easier to reinstall.

(btw it's generally a bad idea to run anything as root that you don't need to run as root - compile as a normal user, then run 'sudo make install' for the last bit where it actually needs root privileges (or in the previous case, 'sudo make uninstall')

Good luck!

---

### Post by marcovanb on 2009-01-14
Thanks for your response.

I have reinstalled mythbunto 8.10.

This time I should not follow the instructions:

[B]Driver Installation
sudo -i
apt-get update
apt-get install install mercurial build-essential linux-headers-`uname -r`
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make && make install
exit[/B]

But I should follow the instructions:

[B]download xc3028-v27.fw.tar.bz2
tar xvjf xc3028-v27.fw.tar.bz2
sudo cp xc3028-v27.fw /lib/firmware
[/B]
Is that correct?

PS Thanks for the security tip. I come from a fedora background and while it does make sense to not log in as root I am a bit lazy but will endevour not do it :)

---

### Post by askvictor on 2009-01-15
Yep that's correct.

Good luck!

---

### Post by enchesss on 2009-01-22
The nano+ uses bluebird2 drivers for windows and there are some hints around at how to extract the firmware here:

[http://www.linuxtv.org/wiki/index.php/Development:_How_to_extract_a_firmware](http://www.linuxtv.org/wiki/index.php/Development:_How_to_extract_a_firmware)

have been unable to extract firmware though.

I have the windows drivers disk and know that the firmware needs to go into /lib/firmware.

---

### Post by chipppy on 2009-01-26
I am a newbie to the terminal.  I am trying to running 8.10 version of Ubuntu with this specific rev2 card and the rev2 remote.

i am trying to follow the instruction as per the start of this thread but i run into a problem and I dont understand what i am doing wrong.

I type in first two lines and all seems to works OK
I type in the third line (apt-get install install mercurial build-essential linux-headers-`uname -r`) and I get the following error.

root@*****:~#apt-get install install mercurial build-essential linux-headers-`uname -r`
Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package install
root@*****:~#

I tried moving a few spaces around in case I was missing a space or had a space where it wasn't but the same error always comes back

Anyone have any idea what i am doing wrong?

Cheers
chipppy

---

### Post by askvictor on 2009-01-26
The problem is that the word 'install' occurs twice. It should only be there once. 

But before you do this, try not doing anything at all - 8.10 works (almost) out of the box (i.e. you don't need to compile drivers) with the rev.1 cards (you still need the firmware), but I'm not sure if the rev.2 cards are included. Try the quick test steps without doing anything else, and report back what happens!

---

### Post by chipppy on 2009-01-27
OK tried the the Quick Test and the following is what happened
Open terminal
sudo -i
root@**:~# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Perth > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-perth
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
root@****:~#

I am in Perth Australia that is why I used the au-Perth. 




Also removed the second 'install'

This happened
root@*****:~#apt-get install mercurial build-essential linux-headers-`uname -r`   (note: there is **no** space between ******headers-'uname*******)
Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package linux-headers-uname -r
root@*****:~#

I also tried
root@*****:~#apt-get install mercurial build-essential linux-headers- `uname -r`   (note: there is **now** a space between ******headers- 'uname*******)
Reading package list...Done
Building dependency tree
Reading state information...Done
Package linux-headers is not installed, so not removed
E: Couldn't find package uname -r
root@*****:~#

Does this help to diagnose the error that I am making.  Is there anything else that I can do to try and help?

I am really new to the terminal so working out the simple things are still hard for me, so please be gentle with me.

Cheers
chipppy

---

### Post by askvictor on 2009-01-27
chippy; type 'ls -al /dev/dvb/adapter0' and post the output. If there is nothing in the directory then you probably _do_ need to compile the driver. If there is something, can you also post the output of running 'lsmod' and 'dmesg' (see if there is anything there that refers to dvb or dvico)

---

### Post by chipppy on 2009-01-27
typed in 
root@******:~# ls -al /dev/dvb/adapter0
ls: cannot access /dev/dvb/adapter0: No such  file or directory
root@***:~#

I also typed in lsmod and dmesd and read through the huge list of stuff and didnt see and dvb or dvico.

I there anyway for me to cut (from forum) and paste (into terminal)  This will help me to reduce my misplacement of spaces and typos?

Thanks for the help

Cheers
chipppy

---

### Post by askvictor on 2009-01-27
OK; it looks like you will have to compile - follow the instructions (but only type install once in the apt-get statement).

As for copying and pasting, there are two ways - Ctrl-C/Ctrl-V copy and paste in the browser. But in the Terminal you need Shift-Ctrl-C and Shift-Ctrl-V. Or use Edit->Copy etc in the menu bar. The other way is nice if you have a three button mouse. To copy something, just select it. Nothing more to do - it is now copied. To paste it just click the middle mouse button. It's fast, but doesn't work everywhere, and gets confusing at times.

Good luck

---

### Post by chipppy on 2009-01-27
Copy and paste the driver steps into the terminal and it looks like it all work.  Well it did a huge amount of things anyway.

Copy and paste the quick test steps into the terminal and still having problems


root@****:~# apt-get install dvb-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dvb-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@****:~# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Perth > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Perth
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
root@****:~#

I have changed the location to Perth as this is where I live.

Isther any risk of doing damage if I follow the firmware upgrade steps??  This is the only thing that I can think of.

Cheers 
chipppy

---

### Post by oobe-feisty on 2009-01-27
you might want to try rebooting after install assuming the install worked ok and there were no errors and assuming you may of neglected to

---

### Post by oobe-feisty on 2009-01-27
yep that space you added will definitely render that command useless you may of misinterpreted someone's advice 

you can right click and copy commands directly from web pages and and documents then paste it into a console terminal right click paste should work ok in konsole and the gnome terminal 


as a last resort you can try uname -r by itself then copy and paste the results to the end of this line

sudo apt-get install mercurial build-essential linux-headers-


which should look similar NOT THE SAME as this apt-get install mercurial build-essential linux-headers-2.6.26.5-version1


> **chipppy said:**
> OK tried the the Quick Test and the following is what happened
Open terminal
sudo -i
root@**:~# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Perth > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-perth
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
root@****:~#

I am in Perth Australia that is why I used the au-Perth. 





Also removed the second 'install'

This happened
root@*****:~#apt-get install mercurial build-essential linux-headers-`uname -r`   (note: there is **no** space between ******headers-'uname*******)
Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package linux-headers-uname -r
root@*****:~#

I also tried
root@*****:~#apt-get install mercurial build-essential linux-headers- `uname -r`   (note: there is **now** a space between ******headers- 'uname*******)
Reading package list...Done
Building dependency tree
Reading state information...Done
Package linux-headers is not installed, so not removed
E: Couldn't find package uname -r
root@*****:~#

Does this help to diagnose the error that I am making.  Is there anything else that I can do to try and help?

I am really new to the terminal so working out the simple things are still hard for me, so please be gentle with me.

Cheers
chipppy

---

### Post by chipppy on 2009-01-27
Yep reboot fixed that problem.  Ran the quick test and all good.

Moving onto the remote rev2 section

root@**********:~# dmesg | grep IR
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.448824] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
 IRQ 16
*lots of IRQ statemets like the one above*

[B][   11.995475] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:05:02.2/usb11/11-1/input/input7
[   12.387253] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:05:02.2/usb11/11-2/input/input9[/B]
root@*****:~#

Then gksudo gedit /etc/udev/rules.d/60-symlinks.rules (as i am using GNOME)

Text editor type program opens with lots of stuff in it.
Scroll down the very bottom and copy-pasted  
KERNEL=="event*",SYSFS{name}=="IR-receiver inside an USB DVB receiver",SYMLINK="input/irremote" 
Saved, close, exit.

An I supposed to replace 'name' with something?  SYSFS{**name**}

Reboot computer and then 
root@***:~# sudo dpkg-reconfigure lirc
Package `lirc' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: lirc is not installed
root@******:~# 

i looked through the code (although I don't really understand what I am reading) and I cannot see a referenace to 'lirc' or anything that looks like it should create that file.

Do i need to create this file somehow or is it supposed to already exist?

Cheers
chipppy

---

### Post by indulis on 2009-01-27
Some of the normal LIRC setup steps will not work, if you are using LMCE which alters some of the standard Ubuntu packages and repositories.

---

### Post by chipppy on 2009-01-28
I am using straight Ubuntu/GNOME, though the 64bit downloaded iso option, on a brand new install. Intel E8500 cpu, 4gb ram, asus 9400gt gpu, asus p5q se/r main-board, couple of big HDD's

I noticed that I forgot to mention earlier that I got my picture via Me TV (application => Sound & Video => digital television)  This actual proves that the TV tuner card works.  it doesn't get all the channels but this most probably has more to do with the old analogue antenna that i have more then the card.  I notice on my set top box hat the levels are all low (50%-60% at best)

Does the following help from the Quick Test
leave open and from a new terminal window as a normal user type
mplayer /dev/dvb/adapter/dvr0
and got the following

****@****:~$ mplayer /dev/dvb/adapter/dvr0
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/dvb/adapter/dvr0.
File not found: '/dev/dvb/adapter/dvr0'
Failed to open /dev/dvb/adapter/dvr0.


Exiting... (End of file)

I had to apt-get install mplayer as it wasn't automagically installed from the CD or updates.  I also found that i had to add the GSTreamer plug-ins as per the web page.  i did this before i found the info refering to the Ubuntu-Restricted-Extras.  I tried to add the Ubuntu-Restricted-Extras but there is a conflict and it says to switch to Synaptic Package Manager to fix, but i have no idea what to do in there or even how to find the conflicting software.



Also did this
*****@****:~$ ls -l /dev/dvb*
total 0
drwxr-xr-x 2 root root 120 2009-01-28 22:42 adapter0
drwxr-xr-x 2 root root 120 2009-01-28 22:42 adapter1
*****@***:~$ 

 
Does this help any with my problem?

Cheers
Chipppy

---

### Post by oobe-feisty on 2009-01-28
Im sorry but im still using 8.04 as it has a 3 year support life and i have modified it to my liking the point being some of the things that work in 8.04 may not work in 8.10 i need to update the thread to be more able to suite 8.10 but am unable to test commands 

such as "sudo dpkg-reconfigure lirc" which happens to work fine in hardy 
> 
Reboot computer and then 
root@***:~# sudo dpkg-reconfigure lirc
Package `lirc' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: lirc is not installed
root@******:~# 

i looked through the code (although I don't really understand what I am reading) and I cannot see a referenace to 'lirc' or anything that looks like it should create that file.

Do i need to create this file somehow or is it supposed to already exist?

Cheers
chipppy


basically your tuner is working and you need to configure your remote control that is what lirc is used for also you need to decide what software you want to use your tuner with i use mythtv but kaffine works fine just to watch 

so now you know your tuner is working you need to decide what you want to use it for and read appropriate guides and documentation

---

### Post by chipppy on 2009-01-29
Ok starting to get somewhere

After much playing around I eventually got  the lirc thing to happen (dont understand how though).

sudo dpkg-reconfigure lirc worked and brought up the various pages.
On page 3

Page 1: Linux input layer (/dev/input/eventX)
Page 2: None
Page 3: There is no /dev/input/irremote 

This is what the page looks like
 Many remotes that were previously supported by the lirc_gpio interface   
now need to be set up via the dev/input interface.  You will need to     custom select your remote's event character device.  This can be
determined by 'cat /proc/bus/input/devices'.                                                                          
Select your custom event interface for your dev/input device:
  
 /dev/input/event3
 /dev/input/event4 
 /dev/input/event5 
 /dev/input/event6
 /dev/input/event7 
 /dev/input/mice   
 /dev/input/mouse0 
 /dev/input/mouse1

there is no /dev/input/irremote  to select

I selected /dev/input/by_id in the hope that it would be close

root@***:~# sudo dpkg-reconfigure lirc
 * Stopping remote control daemon(s): LIRC                       [ OK ] 
 * Reloading kernel event manager...                             [ OK ] 
 * Loading LIRC modules                                          [ OK ] 
 * Starting remote control daemon(s) : LIRC                      [ OK ] 
root@***:~# 
Is the last thing that appeared on the screen

I then moved onto the download of the tarball thingy
           
root@****:~# tar xvjf lirc2.tar.bz2
tar: lirc2.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@******:~# 

How does the tar command know where to find the downloaded file???
I downloaded it to my desktop (automagic option)??
Do I need to copy/paste this file somewhere else so that tar can use it??

This is a very steep learning curve for me but good fun

Cheers
chipppy

---

### Post by oobe-feisty on 2009-01-30
> there is no /dev/input/irremote  to select

you have to create a symlink to /dev/input/irremote its in the instructions

> How does the tar command know where to find the downloaded file???
I downloaded it to my desktop (automagic option)??

it does not know you have to do it from the same directory as the file 

cd /home/user/Desktop 



just a point things will work out for you a lot faster and easier in general if you understand what you are doing copying things from a web page literally without understanding what you are doing will work a lot if you don't make a mistake that's why people suggested copy and pasting to prevent typo's however in the event something does not work it is easier to figure out why if you understand at least what you are trying to achieve i do not mean this in a negative way I'm suggesting you try learning more about basic linux concepts and commands first you can visit the threads in the beginners section or check out a page like this [http://www.linux.ie/newusers/beginners-linux-guide/](http://www.linux.ie/newusers/beginners-linux-guide/) wish you well.

P.S my tutorial used to contain a shell script that did it all for you i removed it cause as things changed it stopped working plus i decided not to update the script in hopes people would learn and understand what they are doing.

---

### Post by chipppy on 2009-01-31
1

---

### Post by enchesss on 2009-01-31
have just completed automatic update and now dual digital four card is not recognised.

nothing output lspci | grep dvico

nothing output dmesg | grep dvb

new kernel is 2.6.27-11-generic


The card will work if I boot into the old kernel at grub though.

have tried to reinstall using these instructions but still only works in previous kernel

---

### Post by oobe-feisty on 2009-01-31
> **enchesss said:**
> have just completed automatic update and now dual digital four card is not recognised.

nothing output lspci | grep dvico

nothing output dmesg | grep dvb

new kernel is 2.6.27-11-generic


The card will work if I boot into the old kernel at grub though.

have tried to reinstall using these instructions but still only works in previous kernel

that is correct you built the drivers for your specific kernel if you build drivers for the new kernel it will work you may need to go over your steps again if you cant be bothered thats ok just make grub boot your old kernel by default your not missing out on much without the new kernel

---

### Post by enchesss on 2009-01-31
I have tried following these steps again to compile with the new kernel however it keeps compiling for the old kernel when looking at the output of the make make install.


also - can you help me with the firmware for the dvico nano+ ? it does not work with this firmware.

I have usbsnoop and created a log file from the windows drivers but am stuck at this step.

---

### Post by oobe-feisty on 2009-02-01
> **enchesss said:**
> I have tried following these steps again to compile with the new kernel however it keeps compiling for the old kernel when looking at the output of the make make install.


also - can you help me with the firmware for the dvico nano+ ? it does not work with this firmware.

I have usbsnoop and created a log file from the windows drivers but am stuck at this step.

problem is you are using the source you download for the old kernel 
you need to do a make distclean or re download a fresh copy

P.S i dont know much about the nano you will have to check the mailing lists for people who use it and dev's who post patches and firmware etc.

---

### Post by enchesss on 2009-02-01
mmm


A bit unclear when you say OR download a fresh copy

when i do these steps:


```
sudo -i

apt-get update

apt-get install mercurial build-essential linux-headers-`uname -r`

hg clone http://linuxtv.org/hg/v4l-dvb


```


i get an error that v4l-dvb already exists and it exits


can you post the command for needing to do a make distclean please, thank you

---

### Post by tqft on 2009-02-01
"hg clone http://linuxtv.org/hg/v4l-dvb"

You have already pulled the base source code , so hg pull -u; hg update is what you do if you want to to update to the very latest version - or even skip it as it is doesn't change much and you have working source already.


"i get an error that v4l-dvb already exists and it exits"
Because you have already done this step see above.


"can you post the command for needing to do a make distclean please,"
cd into the <...>/v4l-dvb type
make distclean  /*yes exactly that*/

---

### Post by chipppy on 2009-02-02
Quick update to my issue with this card.  
Had to run a new install.  Completed install.
Followed steps and all good.  worked perfect first time.
I dont know or understand what went wrong the first time around.

Thanks for all the help.  

cheers
chipppy

---

### Post by marvincide72 on 2009-02-03
**Re: HOWTO: DViCO FusionHDTV DVB-T Dual Digital 4 with remote tutorial **

Hi,
Thanks to Oobe-feisty i have now got my rev2 board working.
I am new to linux and have struggled through ok.

I started trying version 8.10, but couldn't achieve success.
I then found that Oobe-feisty had been using version 8.04.
I then downloaded 8.04 desktop amd64 version.
After the initial updates and driver install the card came to life (both blue leds lit up on the board). Firmware not needed.

In reference to 
*apt-get install install mercurial build-essential linux-headers-`uname -r`*
I had help with this detail, type at terminal prompt, "uname -r"
Copy and paste this where 'uname -r' is.

Tuner card tuned the channels ok. And i could watch live tv, record etc.

BUT, it all fell over when newer updates had come thru after. As a newbie i couldn't track what would have caused this to fail.
So i re-installed mythbuntu and turned automatic updates off.

Has worked for a couple of days so far. 

Well next step is the remote.

Thanks for the good input from this forum.;)

---

### Post by askvictor on 2009-02-03
> **marvincide72 said:**
> **Re: HOWTO: DViCO FusionHDTV DVB-T Dual Digital 4 with remote tutorial **
BUT, it all fell over when newer updates had come thru after. As a newbie i couldn't track what would have caused this to fail.
So i re-installed mythbuntu and turned automatic updates off.


When I was running 7.10 I had the same issues with updates - whenever a new kernel was pushed through the dvico drivers would stop working. So I ended up re-compiling the drivers after every kernel update. Not updating is not the best idea in the world, particularly if your machine pulls any epg data or is otherwise connected to the internets.

My problems were solved in 8.10, which includes the drivers for the rev.1 card :)

---

### Post by laffinet on 2009-02-04
Hi all. Thanks to the great instruction by the OP I got my rev.2 to work under 8.10 (haven't bothered with the remote yet, I'm using a separate one at the moment).

I do have a small but annoying problem which seems a bit like reception glitches:

while watching liveTV or recording I here and there get picture and/or sound "mistakes". Similar to having reception problems (blocky areas in the picture, sound interrupts, things like that). Signal strength is >50% across all channels.
Any idea what could be causing this and what to do about it ?

---

### Post by deepee_oz on 2009-02-14
Thanks for a great howto.

However, the howto for getting the IR Remote for a revision 2 card to work has become very convoluted and unclear.

The initial instructions, the Whirlpool threads and various other contributions make it incredibly difficult to follow.

If anyone who has got the Revision 2 remote to work properly in a Mythbuntu 8.10 system could put together a remote specific step by step howto, it would help a lot of people.

Slightly off topic, this card is now end of life and already in short supply.

---

### Post by oobe-feisty on 2009-02-16
the driver for your remote is included in the v4l-dvb tree 

having said that configuring the remote for this particular card is not unlike configuring any other so really what you are asking for is step by instructions to configure lirc as far as i can tell the instructions i left in the thread are adequate if you have a specific question i will be happy to help you 


> **deepee_oz said:**
> Thanks for a great howto.

However, the howto for getting the IR Remote for a revision 2 card to work has become very convoluted and unclear.

The initial instructions, the Whirlpool threads and various other contributions make it incredibly difficult to follow.

If anyone who has got the Revision 2 remote to work properly in a Mythbuntu 8.10 system could put together a remote specific step by step howto, it would help a lot of people.

Slightly off topic, this card is now end of life and already in short supply.

---

### Post by keyboardslave on 2009-02-17
Mate you are a legend that's one fantastic tutorial... i couldn't even get my card to work with windows (conflicts cause it really was a usb device) now on ubuntu it works..

I must point out though for me Rev2 the tuners are located at:
/dev/dvb/adapter0/dvr0
/dev/dvb/adapter1/dvr0

Not:

/dev/dvb/adapter/dvr0

Also another hint for newbs, on the first comment to install it should only be one install not install install ^_^

Thanks again mate one hell of a awesome tut.

_People whant to know how to kill tzap, exit or ctr+c will not do it, you have to do:_
ps -a (this will list all proccesses)
sudo kill -9 PROCCESSID (this will kill the proccess with the PROCCESSID, you will find the id with the ps -a command.)

One more problem you might be able to help me with, after 5min of tv watching the audio goes out of sync, i tried the command "mplayer /dev/dvb/adapter0/dvr0 -ao sdl"
But it still goes out of sync after a few min of watching.
[U]
UPDATE: Tip for people who are looking for a more GUI solution (nothing is wrong with mplayer):[/U]

sudo apt get-install kaffeine

It found my card (rev2) and scaned the channels all for me.. 
(i use gnome but kaffeine is just to good, i tried tvtime but failed)

Thanks in advance,
scott

---

### Post by keyboardslave on 2009-02-18
Tried to install on mythbuntu 10.8 and got this error:

```

The following NEW packages will be installed:
  dvb-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 146kB of archives.
After this operation, 2941kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com intrepid/universe dvb-utils 1.1.1-3 [146kB]
Fetched 146kB in 2s (51.6kB/s)   
Selecting previously deselected package dvb-utils.
(Reading database ... 115221 files and directories currently installed.)
Unpacking dvb-utils (from .../dvb-utils_1.1.1-3_amd64.deb) ...
Setting up dvb-utils (1.1.1-3) ...
udev active, devices will be created in /dev/.static/dev/
mkdir: cannot create directory `dvb': Read-only file system
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter0/video0-': No such file or directory
makedev dvb/adapter0/video0 c 212 0 root video 0660: failed
mknod: `dvb/adapter0/audio0-': No such file or directory
makedev dvb/adapter0/audio0 c 212 1 root video 0660: failed
mknod: `dvb/adapter0/frontend0-': No such file or directory
makedev dvb/adapter0/frontend0 c 212 3 root video 0660: failed
mknod: `dvb/adapter0/demux0-': No such file or directory
makedev dvb/adapter0/demux0 c 212 4 root video 0660: failed
mknod: `dvb/adapter0/dvr0-': No such file or directory
makedev dvb/adapter0/dvr0 c 212 5 root video 0660: failed
mknod: `dvb/adapter0/ca0-': No such file or directory
makedev dvb/adapter0/ca0 c 212 6 root video 0660: failed
mknod: `dvb/adapter0/net0-': No such file or directory
makedev dvb/adapter0/net0 c 212 7 root video 0660: failed
mknod: `dvb/adapter0/osd0-': No such file or directory
makedev dvb/adapter0/osd0 c 212 8 root video 0660: failed
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter1/video0-': No such file or directory
makedev dvb/adapter1/video0 c 212 64 root video 0660: failed
mknod: `dvb/adapter1/audio0-': No such file or directory
makedev dvb/adapter1/audio0 c 212 65 root video 0660: failed
mknod: `dvb/adapter1/frontend0-': No such file or directory
makedev dvb/adapter1/frontend0 c 212 67 root video 0660: failed
mknod: `dvb/adapter1/demux0-': No such file or directory
makedev dvb/adapter1/demux0 c 212 68 root video 0660: failed
mknod: `dvb/adapter1/dvr0-': No such file or directory
makedev dvb/adapter1/dvr0 c 212 69 root video 0660: failed
mknod: `dvb/adapter1/ca0-': No such file or directory
makedev dvb/adapter1/ca0 c 212 70 root video 0660: failed
mknod: `dvb/adapter1/net0-': No such file or directory
makedev dvb/adapter1/net0 c 212 71 root video 0660: failed
mknod: `dvb/adapter1/osd0-': No such file or directory
makedev dvb/adapter1/osd0 c 212 72 root video 0660: failed
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter2/video0-': No such file or directory
makedev dvb/adapter2/video0 c 212 128 root video 0660: failed
mknod: `dvb/adapter2/audio0-': No such file or directory
makedev dvb/adapter2/audio0 c 212 129 root video 0660: failed
mknod: `dvb/adapter2/frontend0-': No such file or directory
makedev dvb/adapter2/frontend0 c 212 131 root video 0660: failed
mknod: `dvb/adapter2/demux0-': No such file or directory
makedev dvb/adapter2/demux0 c 212 132 root video 0660: failed
mknod: `dvb/adapter2/dvr0-': No such file or directory
makedev dvb/adapter2/dvr0 c 212 133 root video 0660: failed
mknod: `dvb/adapter2/ca0-': No such file or directory
makedev dvb/adapter2/ca0 c 212 134 root video 0660: failed
mknod: `dvb/adapter2/net0-': No such file or directory
makedev dvb/adapter2/net0 c 212 135 root video 0660: failed
mknod: `dvb/adapter2/osd0-': No such file or directory
makedev dvb/adapter2/osd0 c 212 136 root video 0660: failed
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter3/video0-': No such file or directory
makedev dvb/adapter3/video0 c 212 192 root video 0660: failed
mknod: `dvb/adapter3/audio0-': No such file or directory
makedev dvb/adapter3/audio0 c 212 193 root video 0660: failed
mknod: `dvb/adapter3/frontend0-': No such file or directory
makedev dvb/adapter3/frontend0 c 212 195 root video 0660: failed
mknod: `dvb/adapter3/demux0-': No such file or directory
makedev dvb/adapter3/demux0 c 212 196 root video 0660: failed
mknod: `dvb/adapter3/dvr0-': No such file or directory
makedev dvb/adapter3/dvr0 c 212 197 root video 0660: failed
mknod: `dvb/adapter3/ca0-': No such file or directory
makedev dvb/adapter3/ca0 c 212 198 root video 0660: failed
mknod: `dvb/adapter3/net0-': No such file or directory
makedev dvb/adapter3/net0 c 212 199 root video 0660: failed
mknod: `dvb/adapter3/osd0-': No such file or directory
makedev dvb/adapter3/osd0 c 212 200 root video 0660: failed


```

Didnt have these problems on ubuntu, Any ideas?

---

### Post by bazzawill on 2009-02-20
Further to TVars comments on getting a rev2 remote to work, if like me your events do change when you reboot (if say you may have a game pad plugged in one day and not the next) then you can use this udev rule to differentuate the two.
Run udevinfo -a -p /sys/class/input/eventX/
on the first eventX you get when you run dmesg|grep IR
fine line that starts ATTRS{phys}== and write your udev rule accordingly this is mine.
KERNEL=="event*",ATTRS{phys}=="usb-0000:04:07.2-1/ir0",SYMLINK="input/irremote"
This seems to be the only thing that differentiates the two devices.

---

### Post by marcus-brutus on 2009-02-24
> **bazzawill said:**
> 
This seems to be the only thing that differentiates the two devices.

Rather than making the udev rule port|slot specific, it can be done simply with:
```
# /etc/udev/rules.d/10-local.rules
KERNEL=="event*", \
    ATTRS{manufacturer}=="Dvico",\
    ATTRS{product}=="Bluebird", \
    ATTRS{serial}=="00008070", \
  SYMLINK="input/irremote"
```

Where the serial differs between the two USB devices: 00000070 or 00008070.
I assume that the other IR receiver is a dummy (not connected).

You can find the udev attributes for making such rules quite easily:
```
$ udevinfo -p `udevinfo -q path -n /dev/input/event2` -a
```

and you can find the event path above with:
```
$ grep -A4 "IR-receiver" /proc/bus/input/devices | egrep "class|event"
```

Assuming that the serial is the same for all rev2 units, this approach means that the same rule can be used for all users, regardless of which slot the card is in, and what other USB devices are present (ref: probe order).

PS: Works for me ;)

---

### Post by bazzawill on 2009-02-26
Indeed there is a ATTR(serial) I must of missed it when I was looking the first time as that was what I was looking for, so not sure how I missed it. All serial numbers however are different so as to allow you to differentiate from two (or more) cards should you need to.

---

### Post by qigong888 on 2009-02-27
Hi All,

Firstly I'd just like to say a very big thank you to oobe-feisty!
Great job on the tutorial... \\:D/

Now here is a real Curly one!

I have installed x3 _PCI**e**_ DVICO Fusion HDTV DVB-T Dual Digital cards on my server.  Please note these are the PCI-E version!
The server has 8.10 Intrepid server OS with current 2.6.27-7 Kernel.

All installs fine and scanning works immediately without any problems.
All 3 cards (6 tuners) tune fine no problems there.
The system runs flawlessly without even 1 glitch!

However...

Once a scan has completed (in order to load the channel list), and then I perform another scan, just for the heck of it, the tuner cannot lock onto any signals.  The same thing goes for using tuner, for example, on adapter 0.  If I tune it to digital 7 on 177500000 (AU-MELB) it works perfectly.  Then I stop it and then start it again, it doesn't stream any longer and it considers that there is no signal.  Even the tzap command shows this because I'm not able to lock on that frequency no more.

At first I rebooted the server/reload drivers to get the streaming working again, but that is a pain in the proverbial and it just shouldn't be doing that.

I assume that this has something to do with the drivers and that just maybe, the current drivers don't support PCIe ?

Has anyone had this experience with the PCIe version of this card?
If yes, how did you fix this?

I've got the same card but the PCI version and it doesn't give this problem, at all on the same OS so I am really stumped by this... :-?

Your reply would be greatly appreciated... [-o<
cheers!

---

### Post by oobe-feisty on 2009-02-27
Hi qigong888 im glad you found this guide helpful unfortunately i do not know how to help you with this problem as the pci-e version are most likely very different boards however this tutorial may cover the setup procedure by coincedence as im pretty sure the pci-e and pci dvico tuners both have different chips on each board as do the rev1 and rev2 and im unable to make this tutorial anymore comprehensive.

your best bet is to search the linuxtv.org wiki or subscribe to there mailing list and look for some advice.

P.S just out of curiosity how do you make use of 6 tuners all at once i dont find there is enough on FTA to need more that 2 dvb tuners at once personally

---

### Post by oobe-feisty on 2009-02-27
I'm assuming you already have this sorted out but it looks like you installed dvb-utils on a fresh install of intrepid before installing your drivers for the rev2 tuner and it could not find the /dev/dvb locations 

> **keyboardslave said:**
> Tried to install on mythbuntu 10.8 and got this error:


```

The following NEW packages will be installed:
  dvb-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 146kB of archives.
After this operation, 2941kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com intrepid/universe dvb-utils 1.1.1-3 [146kB]
Fetched 146kB in 2s (51.6kB/s)   
Selecting previously deselected package dvb-utils.
(Reading database ... 115221 files and directories currently installed.)
Unpacking dvb-utils (from .../dvb-utils_1.1.1-3_amd64.deb) ...
Setting up dvb-utils (1.1.1-3) ...
udev active, devices will be created in /dev/.static/dev/
mkdir: cannot create directory `dvb': Read-only file system
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter0/video0-': No such file or directory
makedev dvb/adapter0/video0 c 212 0 root video 0660: failed
mknod: `dvb/adapter0/audio0-': No such file or directory
makedev dvb/adapter0/audio0 c 212 1 root video 0660: failed
mknod: `dvb/adapter0/frontend0-': No such file or directory
makedev dvb/adapter0/frontend0 c 212 3 root video 0660: failed
mknod: `dvb/adapter0/demux0-': No such file or directory
makedev dvb/adapter0/demux0 c 212 4 root video 0660: failed
mknod: `dvb/adapter0/dvr0-': No such file or directory
makedev dvb/adapter0/dvr0 c 212 5 root video 0660: failed
mknod: `dvb/adapter0/ca0-': No such file or directory
makedev dvb/adapter0/ca0 c 212 6 root video 0660: failed
mknod: `dvb/adapter0/net0-': No such file or directory
makedev dvb/adapter0/net0 c 212 7 root video 0660: failed
mknod: `dvb/adapter0/osd0-': No such file or directory
makedev dvb/adapter0/osd0 c 212 8 root video 0660: failed
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter1/video0-': No such file or directory
makedev dvb/adapter1/video0 c 212 64 root video 0660: failed
mknod: `dvb/adapter1/audio0-': No such file or directory
makedev dvb/adapter1/audio0 c 212 65 root video 0660: failed
mknod: `dvb/adapter1/frontend0-': No such file or directory
makedev dvb/adapter1/frontend0 c 212 67 root video 0660: failed
mknod: `dvb/adapter1/demux0-': No such file or directory
makedev dvb/adapter1/demux0 c 212 68 root video 0660: failed
mknod: `dvb/adapter1/dvr0-': No such file or directory
makedev dvb/adapter1/dvr0 c 212 69 root video 0660: failed
mknod: `dvb/adapter1/ca0-': No such file or directory
makedev dvb/adapter1/ca0 c 212 70 root video 0660: failed
mknod: `dvb/adapter1/net0-': No such file or directory
makedev dvb/adapter1/net0 c 212 71 root video 0660: failed
mknod: `dvb/adapter1/osd0-': No such file or directory
makedev dvb/adapter1/osd0 c 212 72 root video 0660: failed
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter2/video0-': No such file or directory
makedev dvb/adapter2/video0 c 212 128 root video 0660: failed
mknod: `dvb/adapter2/audio0-': No such file or directory
makedev dvb/adapter2/audio0 c 212 129 root video 0660: failed
mknod: `dvb/adapter2/frontend0-': No such file or directory
makedev dvb/adapter2/frontend0 c 212 131 root video 0660: failed
mknod: `dvb/adapter2/demux0-': No such file or directory
makedev dvb/adapter2/demux0 c 212 132 root video 0660: failed
mknod: `dvb/adapter2/dvr0-': No such file or directory
makedev dvb/adapter2/dvr0 c 212 133 root video 0660: failed
mknod: `dvb/adapter2/ca0-': No such file or directory
makedev dvb/adapter2/ca0 c 212 134 root video 0660: failed
mknod: `dvb/adapter2/net0-': No such file or directory
makedev dvb/adapter2/net0 c 212 135 root video 0660: failed
mknod: `dvb/adapter2/osd0-': No such file or directory
makedev dvb/adapter2/osd0 c 212 136 root video 0660: failed
mkdir: cannot create directory `dvb': Read-only file system
mknod: `dvb/adapter3/video0-': No such file or directory
makedev dvb/adapter3/video0 c 212 192 root video 0660: failed
mknod: `dvb/adapter3/audio0-': No such file or directory
makedev dvb/adapter3/audio0 c 212 193 root video 0660: failed
mknod: `dvb/adapter3/frontend0-': No such file or directory
makedev dvb/adapter3/frontend0 c 212 195 root video 0660: failed
mknod: `dvb/adapter3/demux0-': No such file or directory
makedev dvb/adapter3/demux0 c 212 196 root video 0660: failed
mknod: `dvb/adapter3/dvr0-': No such file or directory
makedev dvb/adapter3/dvr0 c 212 197 root video 0660: failed
mknod: `dvb/adapter3/ca0-': No such file or directory
makedev dvb/adapter3/ca0 c 212 198 root video 0660: failed
mknod: `dvb/adapter3/net0-': No such file or directory
makedev dvb/adapter3/net0 c 212 199 root video 0660: failed
mknod: `dvb/adapter3/osd0-': No such file or directory
makedev dvb/adapter3/osd0 c 212 200 root video 0660: failed


```

Didnt have these problems on ubuntu, Any ideas?

---

### Post by qigong888 on 2009-02-27
Hi oobe-feisty,

Thanks anyway for your reply.  I guess I will take your advice and subscribe to that mailing list.  If I find an answer, I will definitely let you know so you can add it to your great guide!

And just to answer your question, I use the 6 tuners because I am streaming every single channel available on DVB-T, all at the same time.  I've 8 PCs and 4 IP STBs in my home and everyone likes something different, usually at the same time so by using the old 1 card and 2 tuners trick doesn't cut it unfortunately, at my house anyway.  At the moment only 5 tuners are used but shortly will be another addition I think, so it will come in handy.

---

### Post by oobe-feisty on 2009-02-27
wow this sounds like quite a unique and complex setup i would like to see you document it somtime once you have it down pat if you get a chance.

also if you post your lsusb or lspci i can do a bit of googleing for you im curious as i have heard of the dvico dual express i think that may be what you have the name is similar but not the same as "DViCO FusionHDTV DVB-T Dual Digital 4" also the output of dmesg would be helpful aswell particually after the tuning errors occur and after manually loading modules like in this post [http://www.linuxtv.org/pipermail/linux-dvb/2008-May/026256.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-May/026256.html)

P.S here is a good place to start [http://www.linuxtv.org/lists.php](http://www.linuxtv.org/lists.php) can search the archives using [google]("http://www.google.com.au/search?hl=en&as_q=dvico+dual&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=http%3A%2F%2Fwww.linuxtv.org%2Fpipermail%2Flinux-dvb&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=off") 


> **qigong888 said:**
> Hi oobe-feisty,

Thanks anyway for your reply.  I guess I will take your advice and subscribe to that mailing list.  If I find an answer, I will definitely let you know so you can add it to your great guide!

And just to answer your question, I use the 6 tuners because I am streaming every single channel available on DVB-T, all at the same time.  I've 8 PCs and 4 IP STBs in my home and everyone likes something different, usually at the same time so by using the old 1 card and 2 tuners trick doesn't cut it unfortunately, at my house anyway.  At the moment only 5 tuners are used but shortly will be another addition I think, so it will come in handy.

---

### Post by qigong888 on 2009-02-28
Thanks for the message!

Actually, although it seems complex, its really not.  At the moment I use getstream to multicast the channels into my LAN.  Here have a look at this page to get started:
[http://silicon-verl.de/home/flo/projects/streaming/](http://silicon-verl.de/home/flo/projects/streaming/)

You can also use vlc but it has an awful memory leak which ends up stopping the server multicast output after a few hours.  It uses up all of the RAM so you need to reboot the server again.  So then I just used VLS and that solves the problem.  Although an older version, it does its job very well.   But I like getstream better because of its simplicity and fantastic features :)

Although you are correct in your statement that the card is actually a DViCO FusionHDTV Dual Express, I guess it is the same as the DViCO FusionHDTV DVB-T Dual Digital 4 but it has a different chipset, namely the Conexant CX23885.  Probably different in design schematic but I think is quite similar due to the fact that it actually works.
Here is the link to it: [http://www.fusionhdtv.co.kr/ENG/products/DVBTDualExpress.aspx](http://www.fusionhdtv.co.kr/ENG/products/DVBTDualExpress.aspx)

Anyway, with regards to the dmesg, I will output it now for you in the next post.
Let me get the output and post it underneath this post and then you can understand what is happening.  I can show you pre-scan output and then post-scan output.

---

### Post by qigong888 on 2009-02-28
Hi oobe-feisty,

Here it goes: (This will be quite lengthy) !

root@dvbt-server:~# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-server (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:16:57 UTC 2008 (Ubuntu 2.6.27-7.16-server)
[    0.000000] Command line: root=UUID=ee92e0dc-d982-4fb8-9cc3-54c4cd6c7e24 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fb50000 (usable)
[    0.000000]  BIOS-e820: 000000007fb50000 - 000000007fb66000 (reserved)
[    0.000000]  BIOS-e820: 000000007fb66000 - 000000007fb85c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fb85c00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fe000000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fb50 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 007fa00000 page 2M
[    0.000000]  007fa00000 - 007fb50000 page 4k
[    0.000000] kernel direct mapping tables up to 7fb50000 @ 8000-c000
[    0.000000] last_map_addr: 7fb50000 end: 7fb50000
[    0.000000] RAMDISK: 377e3000 - 37fef341
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP 000F2160, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 000F21FC, 0084 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: FACP 7FB83524, 00F4 (r3 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: DSDT 7FB66000, 4996 (r1 DELL   PE_SC3          1 INTL 20050624)
[    0.000000] ACPI: FACS 7FB85C00, 0040
[    0.000000] ACPI: APIC 7FB83078, 0092 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: SPCR 7FB83130, 0050 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: HPET 7FB83184, 0038 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: MCFG 7FB831C0, 003C (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: WD__ 7FB83200, 0134 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: SLIC 7FB83338, 0024 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: ERST 7FB6AB18, 0210 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: HEST 7FB6AD28, 027C (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: BERT 7FB6A998, 0030 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: EINJ 7FB6A9C8, 0150 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: TCPA 7FB834BC, 0064 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fb50000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fb50000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000a000 -  0000000000019f6f] pages 10
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fb50000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b6f9c]    TEXT DATA BSS ==> [0000200000 - 00008b6f9c]
[    0.000000]   #3 [00377e3000 - 0037fef341]          RAMDISK ==> [00377e3000 - 0037fef341]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000fe710] 000fe710
[    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0007fb50
[    0.000000] On node 0 totalpages: 522992
[    0.000000]   DMA zone: 2114 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 510882 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 512996
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=ee92e0dc-d982-4fb8-9cc3-54c4cd6c7e24 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.987 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Calgary: detecting Calgary via BIOS EBDA area
[    0.010000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.010000] Memory: 2043388k/2092352k available (3110k kernel code, 48580k reserved, 1573k data, 536k init)
[    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.010000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.010000] hpet clockevent registered
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.97 BogoMIPS (lpj=19949870)
[    0.010000] Security Framework initialized
[    0.010000] SELinux:  Disabled at boot.
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 0/0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] CPU0: Thermal monitoring enabled (TM1)
[    0.010000] using mwait in idle threads.
[    0.010000] ACPI: Core revision 20080609
[    0.010000] ACPI: Checking initramfs for custom DSDT
[    0.363861] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.463880] CPU0: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.463884] Using local APIC timer interrupts.
[    0.470001] APIC timer calibration result 20781153
[    0.470003] Detected 20.781 MHz APIC timer.
[    0.470137] Booting processor 1/2 ip 6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3990.03 BogoMIPS (lpj=19950184)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 1/2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.631077] CPU1: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.631099] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.640086] Booting processor 2/1 ip 6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 3990.06 BogoMIPS (lpj=19950303)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 2/1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] CPU2: Thermal monitoring enabled (TM2)
[    0.801037] CPU2: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.801059] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.810155] Booting processor 3/3 ip 6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 3990.02 BogoMIPS (lpj=19950130)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 3/3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] CPU3: Thermal monitoring enabled (TM2)
[    0.971067] CPU3: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.971089] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.980024] Brought up 4 CPUs
[    0.980027] Total of 4 processors activated (15960.09 BogoMIPS).
[    0.980078] CPU0 attaching sched-domain:
[    0.980081]  domain 0: span 0,2 level MC
[    0.980083]   groups: 0 2
[    0.980087]   domain 1: span 0-3 level CPU
[    0.980089]    groups: 0,2 1,3
[    0.980092]    domain 2: span 0-3 level NODE
[    0.980094]     groups: 0-3
[    0.980098] CPU1 attaching sched-domain:
[    0.980100]  domain 0: span 1,3 level MC
[    0.980101]   groups: 1 3
[    0.980104]   domain 1: span 0-3 level CPU
[    0.980106]    groups: 1,3 0,2
[    0.980109]    domain 2: span 0-3 level NODE
[    0.980111]     groups: 0-3
[    0.980114] CPU2 attaching sched-domain:
[    0.980115]  domain 0: span 0,2 level MC
[    0.980117]   groups: 2 0
[    0.980120]   domain 1: span 0-3 level CPU
[    0.980121]    groups: 0,2 1,3
[    0.980124]    domain 2: span 0-3 level NODE
[    0.980126]     groups: 0-3
[    0.980129] CPU3 attaching sched-domain:
[    0.980130]  domain 0: span 1,3 level MC
[    0.980132]   groups: 3 1
[    0.980135]   domain 1: span 0-3 level CPU
[    0.980136]    groups: 1,3 0,2
[    0.980139]    domain 2: span 0-3 level NODE
[    0.980141]     groups: 0-3
[    0.980300] net_namespace: 1552 bytes
[    0.980300] Booting paravirtualized kernel on bare hardware
[    0.980300] Time:  5:15:10  Date: 02/28/09
[    0.980325] NET: Registered protocol family 16
[    0.980345] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.980345] ACPI: bus type pci registered
[    0.980345] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.980345] PCI: MCFG area at e0000000 reserved in E820
[    0.990418] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.990420] PCI: Using configuration type 1 for base access
[    0.990423] PCI: Dell PowerEdge 2950 detected, enabling pci=bfsort.
[    0.990438] ACPI: EC: Look up EC in DSDT
[    0.993875] ACPI: BIOS _OSI(Linux) query ignored
[    0.993878] ACPI: DMI System Vendor: Dell Inc.
[    0.993879] ACPI: DMI Product Name: PowerEdge 2950
[    0.993881] ACPI: DMI Product Version:
[    0.993882] ACPI: DMI Board Name: 0H603H
[    0.993883] ACPI: DMI BIOS Vendor: Dell Inc.
[    0.993884] ACPI: DMI BIOS Date: 09/12/2008
[    0.993886] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    0.993887] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.994244] ACPI: Interpreter enabled
[    0.994246] ACPI: (supports S0 S4 S5)
[    0.994257] ACPI: Using IOAPIC for interrupt routing
[    1.000731] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.000731] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:00.0: PME# disabled
[    1.000731] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:02.0: PME# disabled
[    1.000731] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:03.0: PME# disabled
[    1.000731] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:04.0: PME# disabled
[    1.000731] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:05.0: PME# disabled
[    1.000731] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:06.0: PME# disabled
[    1.000731] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:07.0: PME# disabled
[    1.000731] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:1c.0: PME# disabled
[    1.000731] PCI: 0000:00:1d.0 reg 20 io port: [cce0, ccff]
[    1.000731] PCI: 0000:00:1d.1 reg 20 io port: [ccc0, ccdf]
[    1.000731] PCI: 0000:00:1d.2 reg 20 io port: [cca0, ccbf]
[    1.000731] PCI: 0000:00:1d.3 reg 20 io port: [cc80, cc9f]
[    1.000731] PCI: 0000:00:1d.7 reg 10 32bit mmio: [dee00000, dee003ff]
[    1.000731] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.000734] pci 0000:00:1d.7: PME# disabled
[    1.000833] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    1.000839] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    1.000845] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    1.000851] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    1.000856] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f]
[    1.002580] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    1.002672] pci 0000:04:00.0: PME# disabled
[    1.004553] pci 0000:04:00.3: PME# supported from D0 D3hot D3cold
[    1.004645] pci 0000:04:00.3: PME# disabled
[    1.004859] PCI: bridge 0000:00:02.0 32bit mmio: [d2000000, d9ffffff]
[    1.006894] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    1.006985] pci 0000:05:00.0: PME# disabled
[    1.011510] pci 0000:05:01.0: PME# supported from D0 D3hot D3cold
[    1.011602] pci 0000:05:01.0: PME# disabled
[    1.013162] PCI: bridge 0000:04:00.0 32bit mmio: [d4000000, d9ffffff]
[    1.015319] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    1.015411] pci 0000:06:00.0: PME# disabled
[    1.017017] PCI: bridge 0000:05:00.0 32bit mmio: [d6000000, d9ffffff]
[    1.019037] PCI: 0000:07:00.0 reg 10 64bit mmio: [d6000000, d7ffffff]
[    1.020641] pci 0000:07:00.0: PME# supported from D3hot D3cold
[    1.020733] pci 0000:07:00.0: PME# disabled
[    1.022431] PCI: bridge 0000:06:00.0 32bit mmio: [d6000000, d9ffffff]
[    1.023992] PCI: 0000:08:00.0 reg 10 64bit mmio: [d5c00000, d5dfffff]
[    1.025598] pci 0000:08:00.0: supports D1
[    1.025599] pci 0000:08:00.0: supports D2
[    1.025601] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot
[    1.025689] pci 0000:08:00.0: PME# disabled
[    1.027295] PCI: bridge 0000:05:01.0 32bit mmio: [d5c00000, d5ffffff]
[    1.030344] PCI: 0000:01:00.0 reg 10 io port: [ec00, ecff]
[    1.030353] PCI: 0000:01:00.0 reg 14 64bit mmio: [decfc000, decfffff]
[    1.030362] PCI: 0000:01:00.0 reg 1c 64bit mmio: [dece0000, deceffff]
[    1.030372] PCI: 0000:01:00.0 reg 30 32bit mmio: [ded00000, dedfffff]
[    1.030389] pci 0000:01:00.0: supports D1
[    1.030390] pci 0000:01:00.0: supports D2
[    1.030420] PCI: bridge 0000:00:03.0 io port: [e000, efff]
[    1.030423] PCI: bridge 0000:00:03.0 32bit mmio: [deb00000, dedfffff]
[    1.030469] PCI: 0000:0a:00.0 reg 10 64bit mmio: [de600000, de7fffff]
[    1.030527] pci 0000:0a:00.0: supports D1
[    1.030528] pci 0000:0a:00.0: supports D2
[    1.030529] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot
[    1.030534] pci 0000:0a:00.0: PME# disabled
[    1.030566] PCI: bridge 0000:00:04.0 32bit mmio: [de600000, de9fffff]
[    1.030645] PCI: 0000:0c:00.0 reg 10 64bit mmio: [de200000, de3fffff]
[    1.030703] pci 0000:0c:00.0: supports D1
[    1.030704] pci 0000:0c:00.0: supports D2
[    1.030706] pci 0000:0c:00.0: PME# supported from D0 D1 D2 D3hot
[    1.030710] pci 0000:0c:00.0: PME# disabled
[    1.030742] PCI: bridge 0000:00:06.0 32bit mmio: [de200000, de5fffff]
[    1.030840] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.030844] pci 0000:02:00.0: PME# disabled
[    1.030877] PCI: bridge 0000:00:1c.0 32bit mmio: [da000000, ddffffff]
[    1.030938] PCI: 0000:03:00.0 reg 10 64bit mmio: [da000000, dbffffff]
[    1.030987] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    1.030992] pci 0000:03:00.0: PME# disabled
[    1.031043] PCI: bridge 0000:02:00.0 32bit mmio: [da000000, ddffffff]
[    1.031103] PCI: 0000:0e:0d.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    1.031109] PCI: 0000:0e:0d.0 reg 14 io port: [dc00, dcff]
[    1.031116] PCI: 0000:0e:0d.0 reg 18 32bit mmio: [de1d0000, de1dffff]
[    1.031137] PCI: 0000:0e:0d.0 reg 30 32bit mmio: [0, 1ffff]
[    1.031151] pci 0000:0e:0d.0: supports D1
[    1.031152] pci 0000:0e:0d.0: supports D2
[    1.031175] pci 0000:00:1e.0: transparent bridge
[    1.031179] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
[    1.031182] PCI: bridge 0000:00:1e.0 32bit mmio: [de000000, de1fffff]
[    1.031187] PCI: bridge 0000:00:1e.0 64bit mmio pref: [f0000000, f7ffffff]
[    1.031217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.031873] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    1.032074] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST._PRT]
[    1.032219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST.DWN1._PRT]
[    1.032419] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST.DWN2._PRT]
[    1.032617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    1.032817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3.PE2P._PRT]
[    1.032989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    1.033188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    1.033386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SBEX._PRT]
[    1.033584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.COMP._PRT]
[    1.033799] ACPI: PCI Interrupt Link [LK00] (IRQs 3 4 5 *6 7 10 11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK01] (IRQs 3 4 *5 6 7 10 11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK02] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    1.033799] ACPI: PCI Interrupt Link [LK03] (IRQs 3 4 5 6 7 10 *11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK04] (IRQs 3 4 5 6 7 *10 11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK05] (IRQs 3 4 5 6 7 10 *11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK06] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    1.033799] ACPI: PCI Interrupt Link [LK07] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    1.033799] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.033799] pnp: PnP ACPI init
[    1.033799] ACPI: bus type pnp registered
[    1.042566] pnp: PnP ACPI: found 12 devices
[    1.042566] ACPI: ACPI bus type pnp unregistered
[    1.042566] PCI: Using ACPI for IRQ routing
[    1.090011] NET: Registered protocol family 8
[    1.090013] NET: Registered protocol family 20
[    1.090027] NetLabel: Initializing
[    1.090027] NetLabel:  domain hash size = 128
[    1.090027] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.090027] NetLabel:  unlabeled traffic allowed by default
[    1.090044] PCI-GART: No AMD northbridge found.
[    1.090048] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.090052] hpet0: 3 64-bit timers, 14318180 Hz
[    1.095887] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    1.095889]    actual entries 65586
[    1.095955] AppArmor: AppArmor Filesystem Enabled
[    1.095973] ACPI: RTC can wake from S4
[    1.100007] Switched to high resolution mode on CPU 0
[    1.101094] Switched to high resolution mode on CPU 2
[    1.101127] Switched to high resolution mode on CPU 3
[    1.101135] Switched to high resolution mode on CPU 1
[    1.130025] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.130027] system 00:08: ioport range 0x880-0x8bf has been reserved
[    1.130030] system 00:08: ioport range 0x8c0-0x8df has been reserved
[    1.130032] system 00:08: ioport range 0x8e0-0x8e3 has been reserved
[    1.130034] system 00:08: ioport range 0x900-0x900 has been reserved
[    1.130036] system 00:08: ioport range 0xc00-0xc7f has been reserved
[    1.130038] system 00:08: ioport range 0xca0-0xca7 has been reserved
[    1.130040] system 00:08: ioport range 0xca9-0xcab has been reserved
[    1.130042] system 00:08: ioport range 0xcad-0xcaf has been reserved
[    1.130048] system 00:09: ioport range 0xca8-0xca8 has been reserved
[    1.130050] system 00:09: ioport range 0xcac-0xcac has been reserved
[    1.130055] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[    1.135702] pci 0000:06:00.0: PCI bridge, secondary bus 0000:07
[    1.135704] pci 0000:06:00.0:   IO window: disabled
[    1.135821] pci 0000:06:00.0:   MEM window: 0xd6000000-0xd9ffffff
[    1.135912] pci 0000:06:00.0:   PREFETCH window: disabled
[    1.136096] pci 0000:05:00.0: PCI bridge, secondary bus 0000:06
[    1.136097] pci 0000:05:00.0:   IO window: disabled
[    1.136233] pci 0000:05:00.0:   MEM window: 0xd6000000-0xd9ffffff
[    1.136325] pci 0000:05:00.0:   PREFETCH window: disabled
[    1.136508] pci 0000:05:01.0: PCI bridge, secondary bus 0000:08
[    1.136510] pci 0000:05:01.0:   IO window: disabled
[    1.136646] pci 0000:05:01.0:   MEM window: 0xd5c00000-0xd5ffffff
[    1.136738] pci 0000:05:01.0:   PREFETCH window: disabled
[    1.136921] pci 0000:04:00.0: PCI bridge, secondary bus 0000:05
[    1.136923] pci 0000:04:00.0:   IO window: disabled
[    1.137059] pci 0000:04:00.0:   MEM window: 0xd4000000-0xd9ffffff
[    1.137151] pci 0000:04:00.0:   PREFETCH window: disabled
[    1.137334] pci 0000:04:00.3: PCI bridge, secondary bus 0000:09
[    1.137336] pci 0000:04:00.3:   IO window: disabled
[    1.137472] pci 0000:04:00.3:   MEM window: disabled
[    1.137564] pci 0000:04:00.3:   PREFETCH window: disabled
[    1.137747] pci 0000:00:02.0: PCI bridge, secondary bus 0000:04
[    1.137749] pci 0000:00:02.0:   IO window: disabled
[    1.137752] pci 0000:00:02.0:   MEM window: 0xd2000000-0xd9ffffff
[    1.137755] pci 0000:00:02.0:   PREFETCH window: disabled
[    1.137759] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    1.137762] pci 0000:00:03.0:   IO window: 0xe000-0xefff
[    1.137765] pci 0000:00:03.0:   MEM window: 0xdeb00000-0xdedfffff
[    1.137768] pci 0000:00:03.0:   PREFETCH window: disabled
[    1.137772] pci 0000:00:04.0: PCI bridge, secondary bus 0000:0a
[    1.137774] pci 0000:00:04.0:   IO window: disabled
[    1.137777] pci 0000:00:04.0:   MEM window: 0xde600000-0xde9fffff
[    1.137780] pci 0000:00:04.0:   PREFETCH window: disabled
[    1.137784] pci 0000:00:05.0: PCI bridge, secondary bus 0000:0b
[    1.137785] pci 0000:00:05.0:   IO window: disabled
[    1.137789] pci 0000:00:05.0:   MEM window: disabled
[    1.137791] pci 0000:00:05.0:   PREFETCH window: disabled
[    1.137795] pci 0000:00:06.0: PCI bridge, secondary bus 0000:0c
[    1.137797] pci 0000:00:06.0:   IO window: disabled
[    1.137800] pci 0000:00:06.0:   MEM window: 0xde200000-0xde5fffff
[    1.137803] pci 0000:00:06.0:   PREFETCH window: disabled
[    1.137807] pci 0000:00:07.0: PCI bridge, secondary bus 0000:0d
[    1.137809] pci 0000:00:07.0:   IO window: disabled
[    1.137812] pci 0000:00:07.0:   MEM window: disabled
[    1.137815] pci 0000:00:07.0:   PREFETCH window: disabled
[    1.137819] pci 0000:02:00.0: PCI bridge, secondary bus 0000:03
[    1.137820] pci 0000:02:00.0:   IO window: disabled
[    1.137826] pci 0000:02:00.0:   MEM window: 0xda000000-0xddffffff
[    1.137830] pci 0000:02:00.0:   PREFETCH window: disabled
[    1.137837] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.137838] pci 0000:00:1c.0:   IO window: disabled
[    1.137843] pci 0000:00:1c.0:   MEM window: 0xda000000-0xddffffff
[    1.137846] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.137854] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0e
[    1.137856] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    1.137861] pci 0000:00:1e.0:   MEM window: 0xde000000-0xde1fffff
[    1.137864] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    1.137877] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.137881] pci 0000:00:02.0: setting latency timer to 64
[    1.137977] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138069] pci 0000:04:00.0: setting latency timer to 64
[    1.138253] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138344] pci 0000:05:00.0: setting latency timer to 64
[    1.138620] pci 0000:06:00.0: setting latency timer to 64
[    1.138803] pci 0000:05:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138895] pci 0000:05:01.0: setting latency timer to 64
[    1.139170] pci 0000:04:00.3: setting latency timer to 64
[    1.139218] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139222] pci 0000:00:03.0: setting latency timer to 64
[    1.139226] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139230] pci 0000:00:04.0: setting latency timer to 64
[    1.139235] pci 0000:00:05.0: setting latency timer to 64
[    1.139240] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139243] pci 0000:00:06.0: setting latency timer to 64
[    1.139248] pci 0000:00:07.0: setting latency timer to 64
[    1.139254] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139258] pci 0000:00:1c.0: setting latency timer to 64
[    1.139267] pci 0000:02:00.0: setting latency timer to 64
[    1.139273] pci 0000:00:1e.0: setting latency timer to 64
[    1.139276] bus: 00 index 0 io port: [0, ffff]
[    1.139278] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    1.139280] bus: 04 index 0 mmio: [0, 0]
[    1.139281] bus: 04 index 1 mmio: [d2000000, d9ffffff]
[    1.139283] bus: 04 index 2 mmio: [0, 0]
[    1.139284] bus: 04 index 3 mmio: [0, 0]
[    1.139286] bus: 05 index 0 mmio: [0, 0]
[    1.139287] bus: 05 index 1 mmio: [d4000000, d9ffffff]
[    1.139289] bus: 05 index 2 mmio: [0, 0]
[    1.139290] bus: 05 index 3 mmio: [0, 0]
[    1.139292] bus: 06 index 0 mmio: [0, 0]
[    1.139293] bus: 06 index 1 mmio: [d6000000, d9ffffff]
[    1.139295] bus: 06 index 2 mmio: [0, 0]
[    1.139296] bus: 06 index 3 mmio: [0, 0]
[    1.139297] bus: 07 index 0 mmio: [0, 0]
[    1.139299] bus: 07 index 1 mmio: [d6000000, d9ffffff]
[    1.139301] bus: 07 index 2 mmio: [0, 0]
[    1.139302] bus: 07 index 3 mmio: [0, 0]
[    1.139304] bus: 08 index 0 mmio: [0, 0]
[    1.139305] bus: 08 index 1 mmio: [d5c00000, d5ffffff]
[    1.139307] bus: 08 index 2 mmio: [0, 0]
[    1.139308] bus: 08 index 3 mmio: [0, 0]
[    1.139310] bus: 09 index 0 mmio: [0, 0]
[    1.139311] bus: 09 index 1 mmio: [0, 0]
[    1.139312] bus: 09 index 2 mmio: [0, 0]
[    1.139313] bus: 09 index 3 mmio: [0, 0]
[    1.139315] bus: 01 index 0 io port: [e000, efff]
[    1.139317] bus: 01 index 1 mmio: [deb00000, dedfffff]
[    1.139318] bus: 01 index 2 mmio: [0, 0]
[    1.139320] bus: 01 index 3 mmio: [0, 0]
[    1.139321] bus: 0a index 0 mmio: [0, 0]
[    1.139322] bus: 0a index 1 mmio: [de600000, de9fffff]
[    1.139324] bus: 0a index 2 mmio: [0, 0]
[    1.139325] bus: 0a index 3 mmio: [0, 0]
[    1.139327] bus: 0b index 0 mmio: [0, 0]
[    1.139328] bus: 0b index 1 mmio: [0, 0]
[    1.139329] bus: 0b index 2 mmio: [0, 0]
[    1.139331] bus: 0b index 3 mmio: [0, 0]
[    1.139332] bus: 0c index 0 mmio: [0, 0]
[    1.139334] bus: 0c index 1 mmio: [de200000, de5fffff]
[    1.139335] bus: 0c index 2 mmio: [0, 0]
[    1.139336] bus: 0c index 3 mmio: [0, 0]
[    1.139338] bus: 0d index 0 mmio: [0, 0]
[    1.139339] bus: 0d index 1 mmio: [0, 0]
[    1.139341] bus: 0d index 2 mmio: [0, 0]
[    1.139342] bus: 0d index 3 mmio: [0, 0]
[    1.139343] bus: 02 index 0 mmio: [0, 0]
[    1.139345] bus: 02 index 1 mmio: [da000000, ddffffff]
[    1.139346] bus: 02 index 2 mmio: [0, 0]
[    1.139348] bus: 02 index 3 mmio: [0, 0]
[    1.139349] bus: 03 index 0 mmio: [0, 0]
[    1.139351] bus: 03 index 1 mmio: [da000000, ddffffff]
[    1.139352] bus: 03 index 2 mmio: [0, 0]
[    1.139353] bus: 03 index 3 mmio: [0, 0]
[    1.139355] bus: 0e index 0 io port: [d000, dfff]
[    1.139357] bus: 0e index 1 mmio: [de000000, de1fffff]
[    1.139358] bus: 0e index 2 mmio: [f0000000, f7ffffff]
[    1.139360] bus: 0e index 3 io port: [0, ffff]
[    1.139361] bus: 0e index 4 mmio: [0, ffffffffffffffff]
[    1.139370] NET: Registered protocol family 2
[    1.240115] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    1.240792] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    1.242533] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.243123] TCP: Hash tables configured (established 262144 bind 65536)
[    1.243126] TCP reno registered
[    1.270140] NET: Registered protocol family 1
[    1.270259] checking if image is initramfs... it is
[    1.992482] Freeing initrd memory: 8240k freed
[    1.996477] audit: initializing netlink socket (disabled)
[    1.996499] type=2000 audit(1235798109.990:1): initialized
[    2.002674] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.005356] VFS: Disk quotas dquot_6.5.1
[    2.005440] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.005544] msgmni has been set to 4007
[    2.005670] io scheduler noop registered
[    2.005672] io scheduler anticipatory registered
[    2.005674] io scheduler deadline registered (default)
[    2.005799] io scheduler cfq registered
[    2.005922] pci 0000:0e:0d.0: Boot video device
[    2.006059] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    2.006085] pcieport-driver 0000:00:02.0: found MSI capability
[    2.006111] pci_express 0000:00:02.0:pcie00: allocate port service
[    2.006156] pci_express 0000:00:02.0:pcie01: allocate port service
[    2.006238] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    2.006263] pcieport-driver 0000:00:03.0: found MSI capability
[    2.006284] pci_express 0000:00:03.0:pcie00: allocate port service
[    2.006328] pci_express 0000:00:03.0:pcie01: allocate port service
[    2.006413] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.006439] pcieport-driver 0000:00:04.0: found MSI capability
[    2.006461] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.006504] pci_express 0000:00:04.0:pcie01: allocate port service
[    2.006585] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.006611] pcieport-driver 0000:00:05.0: found MSI capability
[    2.006632] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.006675] pci_express 0000:00:05.0:pcie01: allocate port service
[    2.006755] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.006781] pcieport-driver 0000:00:06.0: found MSI capability
[    2.006802] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.006847] pci_express 0000:00:06.0:pcie01: allocate port service
[    2.006928] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    2.006954] pcieport-driver 0000:00:07.0: found MSI capability
[    2.006975] pci_express 0000:00:07.0:pcie00: allocate port service
[    2.007021] pci_express 0000:00:07.0:pcie01: allocate port service
[    2.007104] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.007133] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.007162] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.007209] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.007540] pcieport-driver 0000:04:00.0: setting latency timer to 64
[    2.008871] pci_express 0000:04:00.0:pcie11: allocate port service
[    2.010983] pcieport-driver 0000:05:00.0: setting latency timer to 64
[    2.012269] pcieport-driver 0000:05:00.0: found MSI capability
[    2.013646] pci_express 0000:05:00.0:pcie21: allocate port service
[    2.015712] pcieport-driver 0000:05:01.0: setting latency timer to 64
[    2.017043] pcieport-driver 0000:05:01.0: found MSI capability
[    2.018420] pci_express 0000:05:01.0:pcie21: allocate port service
[    2.023701] aer 0000:00:02.0:pcie01: service driver aer loaded
[    2.026880] aer 0000:00:03.0:pcie01: service driver aer loaded
[    2.030065] aer 0000:00:04.0:pcie01: service driver aer loaded
[    2.033257] aer 0000:00:05.0:pcie01: service driver aer loaded
[    2.036441] aer 0000:00:06.0:pcie01: service driver aer loaded
[    2.039619] aer 0000:00:07.0:pcie01: service driver aer loaded
[    2.072257] hpet_resources: 0xfed00000 is busy
[    2.072318] Linux agpgart interface v0.103
[    2.072323] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.072467] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.072610] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.073166] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.073422] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.075348] brd: module loaded
[    2.075418] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.075598] PNP: No PS/2 controller found. Probing ports directly.
[    2.078003] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.078012] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.131663] mice: PS/2 mouse device common for all mice
[    2.131824] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.131847] rtc0: alarms up to one day, y3k, hpet irqs
[    2.131898] cpuidle: using governor ladder
[    2.131900] cpuidle: using governor menu
[    2.132282] TCP cubic registered
[    2.132514] registered taskstats version 1
[    2.132707]   Magic number: 13:326:265
[    2.132759] tty ttyx7: hash matches
[    2.132773] tty ttyua: hash matches
[    2.132939] rtc_cmos 00:04: setting system clock to 2009-02-28 05:15:11 UTC (1235798111)
[    2.132942] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.132944] EDD information not available.
[    2.132973] Freeing unused kernel memory: 536k freed
[    2.133138] Write protecting the kernel read-only data: 4344k
[    2.232909] fuse init (API version 7.9)
[    2.250488] ACPI: CPU0 (power states: C1[C1] C3[C3])
[    2.250546] processor ACPI0007:00: registered as cooling_device0
[    2.251018] ACPI: CPU1 (power states: C1[C1] C3[C3])
[    2.251067] processor ACPI0007:01: registered as cooling_device1
[    2.251498] ACPI: CPU2 (power states: C1[C1] C3[C3])
[    2.251545] processor ACPI0007:02: registered as cooling_device2
[    2.251981] ACPI: CPU3 (power states: C1[C1] C3[C3])
[    2.252031] processor ACPI0007:03: registered as cooling_device3
[    2.416548] SCSI subsystem initialized
[    2.419173] Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v1.8.0 (Aug 14, 2008)
[    2.419208] bnx2 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.419569] eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem da000000, IRQ 16, node addr 00:22:19:93:11:49
[    2.419682] bnx2 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.422882] eth1: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem d6000000, IRQ 16, node addr 00:22:19:93:11:4b
[    2.438283] Fusion MPT base driver 3.04.07
[    2.438285] Copyright (c) 1999-2008 LSI Corporation
[    2.452882] usbcore: registered new interface driver usbfs
[    2.452907] usbcore: registered new interface driver hub
[    2.452961] usbcore: registered new device driver usb
[    2.461522] Fusion MPT SAS Host driver 3.04.07
[    2.461589] mptsas 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.461752] mptbase: ioc0: Initiating bringup
[    2.463350] USB Universal Host Controller Interface driver v3.0
[    2.467034] No dock devices found.
[    2.480547] libata version 3.00 loaded.
[    4.000010] ioc0: LSISAS1068E B3: Capabilities={Initiator}
[    4.000061] mptbase: ioc0: PCI-MSI enabled
[    4.000086] mptsas 0000:01:00.0: setting latency timer to 64
[   22.562569] scsi0 : ioc0: LSISAS1068E B3, FwRev=00192f00h, Ports=1, MaxQ=266, IRQ=2294
[   22.585612] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1601ABYS-1 6H05 PQ: 0 ANSI: 5
[   22.587625] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   22.587636] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   22.587639] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.587681] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.587717] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000cce0
[   22.587873] usb usb1: configuration #1 chosen from 1 choice
[   22.587906] hub 1-0:1.0: USB hub found
[   22.587913] hub 1-0:1.0: 2 ports detected
[   22.592970] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   22.602937] Driver 'sd' needs updating - please use bus_type methods
[   22.603276] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   22.608469] sd 0:0:0:0: [sda] Write Protect is off
[   22.608473] sd 0:0:0:0: [sda] Mode Sense: 73 00 00 08
[   22.610285] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.610626] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   22.615829] sd 0:0:0:0: [sda] Write Protect is off
[   22.615832] sd 0:0:0:0: [sda] Mode Sense: 73 00 00 08
[   22.617619] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.617623]  sda: sda1 sda2 < sda5 >
[   22.653044] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.691450] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   22.691459] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   22.691462] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.691484] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.691516] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000ccc0
[   22.691597] usb usb2: configuration #1 chosen from 1 choice
[   22.691621] hub 2-0:1.0: USB hub found
[   22.691628] hub 2-0:1.0: 2 ports detected
[   22.801409] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[   22.801415] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   22.801419] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.801440] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.801462] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000cca0
[   22.801538] usb usb3: configuration #1 chosen from 1 choice
[   22.801562] hub 3-0:1.0: USB hub found
[   22.801568] hub 3-0:1.0: 2 ports detected
[   22.911381] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[   22.911387] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   22.911390] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.911410] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.911434] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000cc80
[   22.911507] usb usb4: configuration #1 chosen from 1 choice
[   22.911530] hub 4-0:1.0: USB hub found
[   22.911536] hub 4-0:1.0: 2 ports detected
[   23.020150] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   23.020163] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   23.020166] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.020187] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.024095] ehci_hcd 0000:00:1d.7: debug port 1
[   23.024100] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   23.024105] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xdee00000
[   23.041287] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.041362] usb usb5: configuration #1 chosen from 1 choice
[   23.041385] hub 5-0:1.0: USB hub found
[   23.041391] hub 5-0:1.0: 8 ports detected
[   23.260311] ata_piix 0000:00:1f.1: version 2.12
[   23.260317] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.260356] ata_piix 0000:00:1f.1: setting latency timer to 64
[   23.260429] scsi1 : ata_piix
[   23.260494] scsi2 : ata_piix
[   23.260528] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   23.260530] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   23.380014] usb 5-5: new high speed USB device using ehci_hcd and address 2
[   23.440387] ata1.00: ATAPI: TEAC DVD-ROM DV28EV, D.AG, max UDMA/33
[   23.480263] ata1.00: configured for UDMA/33
[   23.480298] ata2: port disabled. ignoring.
[   23.480332] isa bounce pool size: 16 pages
[   23.484847] scsi 1:0:0:0: CD-ROM            TEAC     DVD-ROM DV28EV   D.AG PQ: 0 ANSI: 5
[   23.484975] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   23.501315] Driver 'sr' needs updating - please use bus_type methods
[   23.511102] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   23.511105] Uniform CD-ROM driver Revision: 3.20
[   23.511196] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.531743] usb 5-5: configuration #1 chosen from 1 choice
[   23.531813] hub 5-5:1.0: USB hub found
[   23.531910] hub 5-5:1.0: 4 ports detected
[   23.573012] PM: Starting manual resume from disk
[   23.573015] PM: Resume from partition 8:5
[   23.573016] PM: Checking hibernation image.
[   23.573202] PM: Resume from disk failed.
[   23.630471] kjournald starting.  Commit interval 5 seconds
[   23.630491] EXT3-fs: mounted filesystem with ordered data mode.
[   25.983003] udevd version 124 started
[   26.195831] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.238689] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[   26.242220] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.257572] EDAC MC: Ver: 2.1.0 Nov  4 2008
[   26.275542] EDAC MC0: Giving out device to 'i5000_edac.c' 'I5000': DEV 0000:00:10.0
[   26.275563] EDAC PCI0: Giving out device to module 'i5000_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
[   26.311284] ACPI: Power Button (FF) [PWRF]
[   26.481009] Linux video capture interface: v2.00
[   26.605911] cx23885 driver version 0.0.1 loaded
[   26.606062] cx23885 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.606136] CORE cx23885[0]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
[   26.773620] intel_rng: FWH not detected
[   26.862233] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.873284] input: i2c IR (FusionHDTV) as /devices/virtual/input/input3
[   26.911183] iTCO_vendor_support: vendor-support=0
[   26.913196] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   27.070944] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.071383] iTCO_wdt: Found a 631xESB/632xESB TCO device (Version=2, TCOBASE=0x0860)
[   27.071431] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.230798] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-0/0-006b/ir0 [cx23885[0]]
[   27.231129] cx23885_dvb_register() allocating 1 frontend(s)
[   27.231132] cx23885[0]: cx23885 based dvb card
[   27.308327] xc2028 0-0061: creating new instance
[   27.308330] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   27.308336] DVB: registering new adapter (cx23885[0])
[   27.308339] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.308694] cx23885_dvb_register() allocating 1 frontend(s)
[   27.308696] cx23885[0]: cx23885 based dvb card
[   27.309275] xc2028 1-0061: creating new instance
[   27.309277] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   27.309280] DVB: registering new adapter (cx23885[0])
[   27.309282] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.309638] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   27.309690] cx23885[0]/0: found at 0000:08:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xd5c00000
[   27.309782] cx23885 0000:08:00.0: setting latency timer to 64
[   27.309871] cx23885 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.309950] CORE cx23885[1]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
[   27.450322] input: i2c IR (FusionHDTV) as /devices/virtual/input/input4
[   27.541932] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-3/3-006b/ir0 [cx23885[1]]
[   27.574901] cx23885_dvb_register() allocating 1 frontend(s)
[   27.574904] cx23885[1]: cx23885 based dvb card
[   27.575485] xc2028 3-0061: creating new instance
[   27.575487] xc2028 3-0061: type set to XCeive xc2028/xc3028 tuner
[   27.575490] DVB: registering new adapter (cx23885[1])
[   27.575492] DVB: registering adapter 2 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.575783] cx23885_dvb_register() allocating 1 frontend(s)
[   27.575785] cx23885[1]: cx23885 based dvb card
[   27.576359] xc2028 4-0061: creating new instance
[   27.576361] xc2028 4-0061: type set to XCeive xc2028/xc3028 tuner
[   27.576363] DVB: registering new adapter (cx23885[1])
[   27.576367] DVB: registering adapter 3 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.576638] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   27.576645] cx23885[1]/0: found at 0000:0a:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xde600000
[   27.576652] cx23885 0000:0a:00.0: setting latency timer to 64
[   27.576690] cx23885 0000:0c:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.576767] CORE cx23885[2]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
[   27.717130] input: i2c IR (FusionHDTV) as /devices/virtual/input/input5
[   27.791915] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-6/6-006b/ir0 [cx23885[2]]
[   27.824771] cx23885_dvb_register() allocating 1 frontend(s)
[   27.824773] cx23885[2]: cx23885 based dvb card
[   27.825348] xc2028 6-0061: creating new instance
[   27.825350] xc2028 6-0061: type set to XCeive xc2028/xc3028 tuner
[   27.825353] DVB: registering new adapter (cx23885[2])
[   27.825355] DVB: registering adapter 4 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.825642] cx23885_dvb_register() allocating 1 frontend(s)
[   27.825644] cx23885[2]: cx23885 based dvb card
[   27.826218] xc2028 7-0061: creating new instance
[   27.826220] xc2028 7-0061: type set to XCeive xc2028/xc3028 tuner
[   27.826222] DVB: registering new adapter (cx23885[2])
[   27.826225] DVB: registering adapter 5 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.826499] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   27.826505] cx23885[2]/0: found at 0000:0c:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xde200000
[   27.826510] cx23885 0000:0c:00.0: setting latency timer to 64
[   28.745024] loop: module loaded
[   28.822744] lp: driver loaded but no devices found
[   29.023021] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k
[   29.312302] EXT3 FS on sda1, internal journal
[   30.157079] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.301087] bnx2: eth0: using MSI
[   30.653748] NET: Registered protocol family 10
[   30.654200] lo: Disabled Privacy Extensions
[   30.654624] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.987148] bnx2: eth0 NIC Copper Link is Up, 100 Mbps full duplex, receive & transmit flow control ON
[   31.987579] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.220005] eth0: no IPv6 routers present

then lsusb command:

root@dvbt-server:~# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

then lspci command:

root@dvbt-server:~# lspci
00:00.0 Host bridge: Intel Corporation 5000X Chipset Memory Controller Hub (rev 12)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 2 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 12)
00:04.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 4-5 (rev 12)
00:05.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 5 (rev 12)
00:06.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 6-7 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 7 (rev 12)
00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 12)
00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)
00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 12)
00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)
00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 12)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
01:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 08)
02:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev c3)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
04:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
04:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
05:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
05:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)
06:00.0 PCI bridge: Broadcom EPB PCI-Express to PCI-X Bridge (rev c3)
07:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
08:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
0a:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
0c:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
0e:0d.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)

Now, I do a quick signal lock check:

root@dvbt-server:~# tzap -a 0 -c channels.conf -r "ABC1"

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 226500000 Hz
video pid 0x0200, audio pid 0x028a
status 00 | signal 5320 | snr 0000 | ber 00000000 | unc 00000000 |
status 1e | signal b954 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal b944 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal b9a0 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal b9f4 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal b978 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal b9c4 | snr ffff | ber 0000000e | unc 00000000 | FE_HAS_LOCK

However, now I just do the exact same scan again and this is what happens:

root@dvbt-server:~# tzap -a 0 -c channels.conf -r "ABC1"

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 226500000 Hz
video pid 0x0200, audio pid 0x028a
status 00 | signal 0000 | snr fafa | ber 0000000e | unc 00000107 |
status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 |
status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 |
status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 |
status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 |
status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 |

as you can see, now it cannot lock!
Now here is the dmesg output which shows something very interesting at the bottom !

root@dvbt-server:~# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-server (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 20:16:57 UTC 2008 (Ubuntu 2.6.27-7.16-server)
[    0.000000] Command line: root=UUID=ee92e0dc-d982-4fb8-9cc3-54c4cd6c7e24 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fb50000 (usable)
[    0.000000]  BIOS-e820: 000000007fb50000 - 000000007fb66000 (reserved)
[    0.000000]  BIOS-e820: 000000007fb66000 - 000000007fb85c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fb85c00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fe000000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fb50 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 007fa00000 page 2M
[    0.000000]  007fa00000 - 007fb50000 page 4k
[    0.000000] kernel direct mapping tables up to 7fb50000 @ 8000-c000
[    0.000000] last_map_addr: 7fb50000 end: 7fb50000
[    0.000000] RAMDISK: 377e3000 - 37fef341
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP 000F2160, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 000F21FC, 0084 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: FACP 7FB83524, 00F4 (r3 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: DSDT 7FB66000, 4996 (r1 DELL   PE_SC3          1 INTL 20050624)
[    0.000000] ACPI: FACS 7FB85C00, 0040
[    0.000000] ACPI: APIC 7FB83078, 0092 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: SPCR 7FB83130, 0050 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: HPET 7FB83184, 0038 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: MCFG 7FB831C0, 003C (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: WD__ 7FB83200, 0134 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: SLIC 7FB83338, 0024 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: ERST 7FB6AB18, 0210 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: HEST 7FB6AD28, 027C (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: BERT 7FB6A998, 0030 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: EINJ 7FB6A9C8, 0150 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] ACPI: TCPA 7FB834BC, 0064 (r1 DELL   PE_SC3          1 DELL        1)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fb50000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fb50000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000a000 -  0000000000019f6f] pages 10
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fb50000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b6f9c]    TEXT DATA BSS ==> [0000200000 - 00008b6f9c]
[    0.000000]   #3 [00377e3000 - 0037fef341]          RAMDISK ==> [00377e3000 - 0037fef341]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000fe710] 000fe710
[    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0007fb50
[    0.000000] On node 0 totalpages: 522992
[    0.000000]   DMA zone: 2114 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 510882 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 512996
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=ee92e0dc-d982-4fb8-9cc3-54c4cd6c7e24 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.987 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Calgary: detecting Calgary via BIOS EBDA area
[    0.010000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.010000] Memory: 2043388k/2092352k available (3110k kernel code, 48580k reserved, 1573k data, 536k init)
[    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.010000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.010000] hpet clockevent registered
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.97 BogoMIPS (lpj=19949870)
[    0.010000] Security Framework initialized
[    0.010000] SELinux:  Disabled at boot.
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 0/0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] CPU0: Thermal monitoring enabled (TM1)
[    0.010000] using mwait in idle threads.
[    0.010000] ACPI: Core revision 20080609
[    0.010000] ACPI: Checking initramfs for custom DSDT
[    0.363861] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.463880] CPU0: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.463884] Using local APIC timer interrupts.
[    0.470001] APIC timer calibration result 20781153
[    0.470003] Detected 20.781 MHz APIC timer.
[    0.470137] Booting processor 1/2 ip 6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3990.03 BogoMIPS (lpj=19950184)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 1/2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.631077] CPU1: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.631099] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.640086] Booting processor 2/1 ip 6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 3990.06 BogoMIPS (lpj=19950303)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 2/1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] CPU2: Thermal monitoring enabled (TM2)
[    0.801037] CPU2: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.801059] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.810155] Booting processor 3/3 ip 6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 3990.02 BogoMIPS (lpj=19950130)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 3/3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] CPU3: Thermal monitoring enabled (TM2)
[    0.971067] CPU3: Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz stepping 06
[    0.971089] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.980024] Brought up 4 CPUs
[    0.980027] Total of 4 processors activated (15960.09 BogoMIPS).
[    0.980078] CPU0 attaching sched-domain:
[    0.980081]  domain 0: span 0,2 level MC
[    0.980083]   groups: 0 2
[    0.980087]   domain 1: span 0-3 level CPU
[    0.980089]    groups: 0,2 1,3
[    0.980092]    domain 2: span 0-3 level NODE
[    0.980094]     groups: 0-3
[    0.980098] CPU1 attaching sched-domain:
[    0.980100]  domain 0: span 1,3 level MC
[    0.980101]   groups: 1 3
[    0.980104]   domain 1: span 0-3 level CPU
[    0.980106]    groups: 1,3 0,2
[    0.980109]    domain 2: span 0-3 level NODE
[    0.980111]     groups: 0-3
[    0.980114] CPU2 attaching sched-domain:
[    0.980115]  domain 0: span 0,2 level MC
[    0.980117]   groups: 2 0
[    0.980120]   domain 1: span 0-3 level CPU
[    0.980121]    groups: 0,2 1,3
[    0.980124]    domain 2: span 0-3 level NODE
[    0.980126]     groups: 0-3
[    0.980129] CPU3 attaching sched-domain:
[    0.980130]  domain 0: span 1,3 level MC
[    0.980132]   groups: 3 1
[    0.980135]   domain 1: span 0-3 level CPU
[    0.980136]    groups: 1,3 0,2
[    0.980139]    domain 2: span 0-3 level NODE
[    0.980141]     groups: 0-3
[    0.980300] net_namespace: 1552 bytes
[    0.980300] Booting paravirtualized kernel on bare hardware
[    0.980300] Time:  5:15:10  Date: 02/28/09
[    0.980325] NET: Registered protocol family 16
[    0.980345] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.980345] ACPI: bus type pci registered
[    0.980345] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.980345] PCI: MCFG area at e0000000 reserved in E820
[    0.990418] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.990420] PCI: Using configuration type 1 for base access
[    0.990423] PCI: Dell PowerEdge 2950 detected, enabling pci=bfsort.
[    0.990438] ACPI: EC: Look up EC in DSDT
[    0.993875] ACPI: BIOS _OSI(Linux) query ignored
[    0.993878] ACPI: DMI System Vendor: Dell Inc.
[    0.993879] ACPI: DMI Product Name: PowerEdge 2950
[    0.993881] ACPI: DMI Product Version:
[    0.993882] ACPI: DMI Board Name: 0H603H
[    0.993883] ACPI: DMI BIOS Vendor: Dell Inc.
[    0.993884] ACPI: DMI BIOS Date: 09/12/2008
[    0.993886] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[    0.993887] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.994244] ACPI: Interpreter enabled
[    0.994246] ACPI: (supports S0 S4 S5)
[    0.994257] ACPI: Using IOAPIC for interrupt routing
[    1.000731] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.000731] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:00.0: PME# disabled
[    1.000731] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:02.0: PME# disabled
[    1.000731] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:03.0: PME# disabled
[    1.000731] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:04.0: PME# disabled
[    1.000731] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:05.0: PME# disabled
[    1.000731] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:06.0: PME# disabled
[    1.000731] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:07.0: PME# disabled
[    1.000731] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.000731] pci 0000:00:1c.0: PME# disabled
[    1.000731] PCI: 0000:00:1d.0 reg 20 io port: [cce0, ccff]
[    1.000731] PCI: 0000:00:1d.1 reg 20 io port: [ccc0, ccdf]
[    1.000731] PCI: 0000:00:1d.2 reg 20 io port: [cca0, ccbf]
[    1.000731] PCI: 0000:00:1d.3 reg 20 io port: [cc80, cc9f]
[    1.000731] PCI: 0000:00:1d.7 reg 10 32bit mmio: [dee00000, dee003ff]
[    1.000731] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.000734] pci 0000:00:1d.7: PME# disabled
[    1.000833] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    1.000839] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    1.000845] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    1.000851] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    1.000856] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f]
[    1.002580] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    1.002672] pci 0000:04:00.0: PME# disabled
[    1.004553] pci 0000:04:00.3: PME# supported from D0 D3hot D3cold
[    1.004645] pci 0000:04:00.3: PME# disabled
[    1.004859] PCI: bridge 0000:00:02.0 32bit mmio: [d2000000, d9ffffff]
[    1.006894] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    1.006985] pci 0000:05:00.0: PME# disabled
[    1.011510] pci 0000:05:01.0: PME# supported from D0 D3hot D3cold
[    1.011602] pci 0000:05:01.0: PME# disabled
[    1.013162] PCI: bridge 0000:04:00.0 32bit mmio: [d4000000, d9ffffff]
[    1.015319] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    1.015411] pci 0000:06:00.0: PME# disabled
[    1.017017] PCI: bridge 0000:05:00.0 32bit mmio: [d6000000, d9ffffff]
[    1.019037] PCI: 0000:07:00.0 reg 10 64bit mmio: [d6000000, d7ffffff]
[    1.020641] pci 0000:07:00.0: PME# supported from D3hot D3cold
[    1.020733] pci 0000:07:00.0: PME# disabled
[    1.022431] PCI: bridge 0000:06:00.0 32bit mmio: [d6000000, d9ffffff]
[    1.023992] PCI: 0000:08:00.0 reg 10 64bit mmio: [d5c00000, d5dfffff]
[    1.025598] pci 0000:08:00.0: supports D1
[    1.025599] pci 0000:08:00.0: supports D2
[    1.025601] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot
[    1.025689] pci 0000:08:00.0: PME# disabled
[    1.027295] PCI: bridge 0000:05:01.0 32bit mmio: [d5c00000, d5ffffff]
[    1.030344] PCI: 0000:01:00.0 reg 10 io port: [ec00, ecff]
[    1.030353] PCI: 0000:01:00.0 reg 14 64bit mmio: [decfc000, decfffff]
[    1.030362] PCI: 0000:01:00.0 reg 1c 64bit mmio: [dece0000, deceffff]
[    1.030372] PCI: 0000:01:00.0 reg 30 32bit mmio: [ded00000, dedfffff]
[    1.030389] pci 0000:01:00.0: supports D1
[    1.030390] pci 0000:01:00.0: supports D2
[    1.030420] PCI: bridge 0000:00:03.0 io port: [e000, efff]
[    1.030423] PCI: bridge 0000:00:03.0 32bit mmio: [deb00000, dedfffff]
[    1.030469] PCI: 0000:0a:00.0 reg 10 64bit mmio: [de600000, de7fffff]
[    1.030527] pci 0000:0a:00.0: supports D1
[    1.030528] pci 0000:0a:00.0: supports D2
[    1.030529] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot
[    1.030534] pci 0000:0a:00.0: PME# disabled
[    1.030566] PCI: bridge 0000:00:04.0 32bit mmio: [de600000, de9fffff]
[    1.030645] PCI: 0000:0c:00.0 reg 10 64bit mmio: [de200000, de3fffff]
[    1.030703] pci 0000:0c:00.0: supports D1
[    1.030704] pci 0000:0c:00.0: supports D2
[    1.030706] pci 0000:0c:00.0: PME# supported from D0 D1 D2 D3hot
[    1.030710] pci 0000:0c:00.0: PME# disabled
[    1.030742] PCI: bridge 0000:00:06.0 32bit mmio: [de200000, de5fffff]
[    1.030840] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.030844] pci 0000:02:00.0: PME# disabled
[    1.030877] PCI: bridge 0000:00:1c.0 32bit mmio: [da000000, ddffffff]
[    1.030938] PCI: 0000:03:00.0 reg 10 64bit mmio: [da000000, dbffffff]
[    1.030987] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    1.030992] pci 0000:03:00.0: PME# disabled
[    1.031043] PCI: bridge 0000:02:00.0 32bit mmio: [da000000, ddffffff]
[    1.031103] PCI: 0000:0e:0d.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    1.031109] PCI: 0000:0e:0d.0 reg 14 io port: [dc00, dcff]
[    1.031116] PCI: 0000:0e:0d.0 reg 18 32bit mmio: [de1d0000, de1dffff]
[    1.031137] PCI: 0000:0e:0d.0 reg 30 32bit mmio: [0, 1ffff]
[    1.031151] pci 0000:0e:0d.0: supports D1
[    1.031152] pci 0000:0e:0d.0: supports D2
[    1.031175] pci 0000:00:1e.0: transparent bridge
[    1.031179] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
[    1.031182] PCI: bridge 0000:00:1e.0 32bit mmio: [de000000, de1fffff]
[    1.031187] PCI: bridge 0000:00:1e.0 64bit mmio pref: [f0000000, f7ffffff]
[    1.031217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.031873] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    1.032074] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST._PRT]
[    1.032219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST.DWN1._PRT]
[    1.032419] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST.DWN2._PRT]
[    1.032617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    1.032817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3.PE2P._PRT]
[    1.032989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    1.033188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    1.033386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SBEX._PRT]
[    1.033584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.COMP._PRT]
[    1.033799] ACPI: PCI Interrupt Link [LK00] (IRQs 3 4 5 *6 7 10 11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK01] (IRQs 3 4 *5 6 7 10 11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK02] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    1.033799] ACPI: PCI Interrupt Link [LK03] (IRQs 3 4 5 6 7 10 *11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK04] (IRQs 3 4 5 6 7 *10 11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK05] (IRQs 3 4 5 6 7 10 *11 12)
[    1.033799] ACPI: PCI Interrupt Link [LK06] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    1.033799] ACPI: PCI Interrupt Link [LK07] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    1.033799] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.033799] pnp: PnP ACPI init
[    1.033799] ACPI: bus type pnp registered
[    1.042566] pnp: PnP ACPI: found 12 devices
[    1.042566] ACPI: ACPI bus type pnp unregistered
[    1.042566] PCI: Using ACPI for IRQ routing
[    1.090011] NET: Registered protocol family 8
[    1.090013] NET: Registered protocol family 20
[    1.090027] NetLabel: Initializing
[    1.090027] NetLabel:  domain hash size = 128
[    1.090027] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.090027] NetLabel:  unlabeled traffic allowed by default
[    1.090044] PCI-GART: No AMD northbridge found.
[    1.090048] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.090052] hpet0: 3 64-bit timers, 14318180 Hz
[    1.095887] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    1.095889]    actual entries 65586
[    1.095955] AppArmor: AppArmor Filesystem Enabled
[    1.095973] ACPI: RTC can wake from S4
[    1.100007] Switched to high resolution mode on CPU 0
[    1.101094] Switched to high resolution mode on CPU 2
[    1.101127] Switched to high resolution mode on CPU 3
[    1.101135] Switched to high resolution mode on CPU 1
[    1.130025] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.130027] system 00:08: ioport range 0x880-0x8bf has been reserved
[    1.130030] system 00:08: ioport range 0x8c0-0x8df has been reserved
[    1.130032] system 00:08: ioport range 0x8e0-0x8e3 has been reserved
[    1.130034] system 00:08: ioport range 0x900-0x900 has been reserved
[    1.130036] system 00:08: ioport range 0xc00-0xc7f has been reserved
[    1.130038] system 00:08: ioport range 0xca0-0xca7 has been reserved
[    1.130040] system 00:08: ioport range 0xca9-0xcab has been reserved
[    1.130042] system 00:08: ioport range 0xcad-0xcaf has been reserved
[    1.130048] system 00:09: ioport range 0xca8-0xca8 has been reserved
[    1.130050] system 00:09: ioport range 0xcac-0xcac has been reserved
[    1.130055] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[    1.135702] pci 0000:06:00.0: PCI bridge, secondary bus 0000:07
[    1.135704] pci 0000:06:00.0:   IO window: disabled
[    1.135821] pci 0000:06:00.0:   MEM window: 0xd6000000-0xd9ffffff
[    1.135912] pci 0000:06:00.0:   PREFETCH window: disabled
[    1.136096] pci 0000:05:00.0: PCI bridge, secondary bus 0000:06
[    1.136097] pci 0000:05:00.0:   IO window: disabled
[    1.136233] pci 0000:05:00.0:   MEM window: 0xd6000000-0xd9ffffff
[    1.136325] pci 0000:05:00.0:   PREFETCH window: disabled
[    1.136508] pci 0000:05:01.0: PCI bridge, secondary bus 0000:08
[    1.136510] pci 0000:05:01.0:   IO window: disabled
[    1.136646] pci 0000:05:01.0:   MEM window: 0xd5c00000-0xd5ffffff
[    1.136738] pci 0000:05:01.0:   PREFETCH window: disabled
[    1.136921] pci 0000:04:00.0: PCI bridge, secondary bus 0000:05
[    1.136923] pci 0000:04:00.0:   IO window: disabled
[    1.137059] pci 0000:04:00.0:   MEM window: 0xd4000000-0xd9ffffff
[    1.137151] pci 0000:04:00.0:   PREFETCH window: disabled
[    1.137334] pci 0000:04:00.3: PCI bridge, secondary bus 0000:09
[    1.137336] pci 0000:04:00.3:   IO window: disabled
[    1.137472] pci 0000:04:00.3:   MEM window: disabled
[    1.137564] pci 0000:04:00.3:   PREFETCH window: disabled
[    1.137747] pci 0000:00:02.0: PCI bridge, secondary bus 0000:04
[    1.137749] pci 0000:00:02.0:   IO window: disabled
[    1.137752] pci 0000:00:02.0:   MEM window: 0xd2000000-0xd9ffffff
[    1.137755] pci 0000:00:02.0:   PREFETCH window: disabled
[    1.137759] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    1.137762] pci 0000:00:03.0:   IO window: 0xe000-0xefff
[    1.137765] pci 0000:00:03.0:   MEM window: 0xdeb00000-0xdedfffff
[    1.137768] pci 0000:00:03.0:   PREFETCH window: disabled
[    1.137772] pci 0000:00:04.0: PCI bridge, secondary bus 0000:0a
[    1.137774] pci 0000:00:04.0:   IO window: disabled
[    1.137777] pci 0000:00:04.0:   MEM window: 0xde600000-0xde9fffff
[    1.137780] pci 0000:00:04.0:   PREFETCH window: disabled
[    1.137784] pci 0000:00:05.0: PCI bridge, secondary bus 0000:0b
[    1.137785] pci 0000:00:05.0:   IO window: disabled
[    1.137789] pci 0000:00:05.0:   MEM window: disabled
[    1.137791] pci 0000:00:05.0:   PREFETCH window: disabled
[    1.137795] pci 0000:00:06.0: PCI bridge, secondary bus 0000:0c
[    1.137797] pci 0000:00:06.0:   IO window: disabled
[    1.137800] pci 0000:00:06.0:   MEM window: 0xde200000-0xde5fffff
[    1.137803] pci 0000:00:06.0:   PREFETCH window: disabled
[    1.137807] pci 0000:00:07.0: PCI bridge, secondary bus 0000:0d
[    1.137809] pci 0000:00:07.0:   IO window: disabled
[    1.137812] pci 0000:00:07.0:   MEM window: disabled
[    1.137815] pci 0000:00:07.0:   PREFETCH window: disabled
[    1.137819] pci 0000:02:00.0: PCI bridge, secondary bus 0000:03
[    1.137820] pci 0000:02:00.0:   IO window: disabled
[    1.137826] pci 0000:02:00.0:   MEM window: 0xda000000-0xddffffff
[    1.137830] pci 0000:02:00.0:   PREFETCH window: disabled
[    1.137837] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.137838] pci 0000:00:1c.0:   IO window: disabled
[    1.137843] pci 0000:00:1c.0:   MEM window: 0xda000000-0xddffffff
[    1.137846] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.137854] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0e
[    1.137856] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    1.137861] pci 0000:00:1e.0:   MEM window: 0xde000000-0xde1fffff
[    1.137864] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    1.137877] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.137881] pci 0000:00:02.0: setting latency timer to 64
[    1.137977] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138069] pci 0000:04:00.0: setting latency timer to 64
[    1.138253] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138344] pci 0000:05:00.0: setting latency timer to 64
[    1.138620] pci 0000:06:00.0: setting latency timer to 64
[    1.138803] pci 0000:05:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.138895] pci 0000:05:01.0: setting latency timer to 64
[    1.139170] pci 0000:04:00.3: setting latency timer to 64
[    1.139218] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139222] pci 0000:00:03.0: setting latency timer to 64
[    1.139226] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139230] pci 0000:00:04.0: setting latency timer to 64
[    1.139235] pci 0000:00:05.0: setting latency timer to 64
[    1.139240] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139243] pci 0000:00:06.0: setting latency timer to 64
[    1.139248] pci 0000:00:07.0: setting latency timer to 64
[    1.139254] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.139258] pci 0000:00:1c.0: setting latency timer to 64
[    1.139267] pci 0000:02:00.0: setting latency timer to 64
[    1.139273] pci 0000:00:1e.0: setting latency timer to 64
[    1.139276] bus: 00 index 0 io port: [0, ffff]
[    1.139278] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    1.139280] bus: 04 index 0 mmio: [0, 0]
[    1.139281] bus: 04 index 1 mmio: [d2000000, d9ffffff]
[    1.139283] bus: 04 index 2 mmio: [0, 0]
[    1.139284] bus: 04 index 3 mmio: [0, 0]
[    1.139286] bus: 05 index 0 mmio: [0, 0]
[    1.139287] bus: 05 index 1 mmio: [d4000000, d9ffffff]
[    1.139289] bus: 05 index 2 mmio: [0, 0]
[    1.139290] bus: 05 index 3 mmio: [0, 0]
[    1.139292] bus: 06 index 0 mmio: [0, 0]
[    1.139293] bus: 06 index 1 mmio: [d6000000, d9ffffff]
[    1.139295] bus: 06 index 2 mmio: [0, 0]
[    1.139296] bus: 06 index 3 mmio: [0, 0]
[    1.139297] bus: 07 index 0 mmio: [0, 0]
[    1.139299] bus: 07 index 1 mmio: [d6000000, d9ffffff]
[    1.139301] bus: 07 index 2 mmio: [0, 0]
[    1.139302] bus: 07 index 3 mmio: [0, 0]
[    1.139304] bus: 08 index 0 mmio: [0, 0]
[    1.139305] bus: 08 index 1 mmio: [d5c00000, d5ffffff]
[    1.139307] bus: 08 index 2 mmio: [0, 0]
[    1.139308] bus: 08 index 3 mmio: [0, 0]
[    1.139310] bus: 09 index 0 mmio: [0, 0]
[    1.139311] bus: 09 index 1 mmio: [0, 0]
[    1.139312] bus: 09 index 2 mmio: [0, 0]
[    1.139313] bus: 09 index 3 mmio: [0, 0]
[    1.139315] bus: 01 index 0 io port: [e000, efff]
[    1.139317] bus: 01 index 1 mmio: [deb00000, dedfffff]
[    1.139318] bus: 01 index 2 mmio: [0, 0]
[    1.139320] bus: 01 index 3 mmio: [0, 0]
[    1.139321] bus: 0a index 0 mmio: [0, 0]
[    1.139322] bus: 0a index 1 mmio: [de600000, de9fffff]
[    1.139324] bus: 0a index 2 mmio: [0, 0]
[    1.139325] bus: 0a index 3 mmio: [0, 0]
[    1.139327] bus: 0b index 0 mmio: [0, 0]
[    1.139328] bus: 0b index 1 mmio: [0, 0]
[    1.139329] bus: 0b index 2 mmio: [0, 0]
[    1.139331] bus: 0b index 3 mmio: [0, 0]
[    1.139332] bus: 0c index 0 mmio: [0, 0]
[    1.139334] bus: 0c index 1 mmio: [de200000, de5fffff]
[    1.139335] bus: 0c index 2 mmio: [0, 0]
[    1.139336] bus: 0c index 3 mmio: [0, 0]
[    1.139338] bus: 0d index 0 mmio: [0, 0]
[    1.139339] bus: 0d index 1 mmio: [0, 0]
[    1.139341] bus: 0d index 2 mmio: [0, 0]
[    1.139342] bus: 0d index 3 mmio: [0, 0]
[    1.139343] bus: 02 index 0 mmio: [0, 0]
[    1.139345] bus: 02 index 1 mmio: [da000000, ddffffff]
[    1.139346] bus: 02 index 2 mmio: [0, 0]
[    1.139348] bus: 02 index 3 mmio: [0, 0]
[    1.139349] bus: 03 index 0 mmio: [0, 0]
[    1.139351] bus: 03 index 1 mmio: [da000000, ddffffff]
[    1.139352] bus: 03 index 2 mmio: [0, 0]
[    1.139353] bus: 03 index 3 mmio: [0, 0]
[    1.139355] bus: 0e index 0 io port: [d000, dfff]
[    1.139357] bus: 0e index 1 mmio: [de000000, de1fffff]
[    1.139358] bus: 0e index 2 mmio: [f0000000, f7ffffff]
[    1.139360] bus: 0e index 3 io port: [0, ffff]
[    1.139361] bus: 0e index 4 mmio: [0, ffffffffffffffff]
[    1.139370] NET: Registered protocol family 2
[    1.240115] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    1.240792] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    1.242533] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.243123] TCP: Hash tables configured (established 262144 bind 65536)
[    1.243126] TCP reno registered
[    1.270140] NET: Registered protocol family 1
[    1.270259] checking if image is initramfs... it is
[    1.992482] Freeing initrd memory: 8240k freed
[    1.996477] audit: initializing netlink socket (disabled)
[    1.996499] type=2000 audit(1235798109.990:1): initialized
[    2.002674] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.005356] VFS: Disk quotas dquot_6.5.1
[    2.005440] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.005544] msgmni has been set to 4007
[    2.005670] io scheduler noop registered
[    2.005672] io scheduler anticipatory registered
[    2.005674] io scheduler deadline registered (default)
[    2.005799] io scheduler cfq registered
[    2.005922] pci 0000:0e:0d.0: Boot video device
[    2.006059] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    2.006085] pcieport-driver 0000:00:02.0: found MSI capability
[    2.006111] pci_express 0000:00:02.0:pcie00: allocate port service
[    2.006156] pci_express 0000:00:02.0:pcie01: allocate port service
[    2.006238] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    2.006263] pcieport-driver 0000:00:03.0: found MSI capability
[    2.006284] pci_express 0000:00:03.0:pcie00: allocate port service
[    2.006328] pci_express 0000:00:03.0:pcie01: allocate port service
[    2.006413] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.006439] pcieport-driver 0000:00:04.0: found MSI capability
[    2.006461] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.006504] pci_express 0000:00:04.0:pcie01: allocate port service
[    2.006585] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.006611] pcieport-driver 0000:00:05.0: found MSI capability
[    2.006632] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.006675] pci_express 0000:00:05.0:pcie01: allocate port service
[    2.006755] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.006781] pcieport-driver 0000:00:06.0: found MSI capability
[    2.006802] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.006847] pci_express 0000:00:06.0:pcie01: allocate port service
[    2.006928] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    2.006954] pcieport-driver 0000:00:07.0: found MSI capability
[    2.006975] pci_express 0000:00:07.0:pcie00: allocate port service
[    2.007021] pci_express 0000:00:07.0:pcie01: allocate port service
[    2.007104] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.007133] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.007162] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.007209] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.007540] pcieport-driver 0000:04:00.0: setting latency timer to 64
[    2.008871] pci_express 0000:04:00.0:pcie11: allocate port service
[    2.010983] pcieport-driver 0000:05:00.0: setting latency timer to 64
[    2.012269] pcieport-driver 0000:05:00.0: found MSI capability
[    2.013646] pci_express 0000:05:00.0:pcie21: allocate port service
[    2.015712] pcieport-driver 0000:05:01.0: setting latency timer to 64
[    2.017043] pcieport-driver 0000:05:01.0: found MSI capability
[    2.018420] pci_express 0000:05:01.0:pcie21: allocate port service
[    2.023701] aer 0000:00:02.0:pcie01: service driver aer loaded
[    2.026880] aer 0000:00:03.0:pcie01: service driver aer loaded
[    2.030065] aer 0000:00:04.0:pcie01: service driver aer loaded
[    2.033257] aer 0000:00:05.0:pcie01: service driver aer loaded
[    2.036441] aer 0000:00:06.0:pcie01: service driver aer loaded
[    2.039619] aer 0000:00:07.0:pcie01: service driver aer loaded
[    2.072257] hpet_resources: 0xfed00000 is busy
[    2.072318] Linux agpgart interface v0.103
[    2.072323] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.072467] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.072610] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.073166] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.073422] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.075348] brd: module loaded
[    2.075418] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.075598] PNP: No PS/2 controller found. Probing ports directly.
[    2.078003] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.078012] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.131663] mice: PS/2 mouse device common for all mice
[    2.131824] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.131847] rtc0: alarms up to one day, y3k, hpet irqs
[    2.131898] cpuidle: using governor ladder
[    2.131900] cpuidle: using governor menu
[    2.132282] TCP cubic registered
[    2.132514] registered taskstats version 1
[    2.132707]   Magic number: 13:326:265
[    2.132759] tty ttyx7: hash matches
[    2.132773] tty ttyua: hash matches
[    2.132939] rtc_cmos 00:04: setting system clock to 2009-02-28 05:15:11 UTC (1235798111)
[    2.132942] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.132944] EDD information not available.
[    2.132973] Freeing unused kernel memory: 536k freed
[    2.133138] Write protecting the kernel read-only data: 4344k
[    2.232909] fuse init (API version 7.9)
[    2.250488] ACPI: CPU0 (power states: C1[C1] C3[C3])
[    2.250546] processor ACPI0007:00: registered as cooling_device0
[    2.251018] ACPI: CPU1 (power states: C1[C1] C3[C3])
[    2.251067] processor ACPI0007:01: registered as cooling_device1
[    2.251498] ACPI: CPU2 (power states: C1[C1] C3[C3])
[    2.251545] processor ACPI0007:02: registered as cooling_device2
[    2.251981] ACPI: CPU3 (power states: C1[C1] C3[C3])
[    2.252031] processor ACPI0007:03: registered as cooling_device3
[    2.416548] SCSI subsystem initialized
[    2.419173] Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v1.8.0 (Aug 14, 2008)
[    2.419208] bnx2 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.419569] eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem da000000, IRQ 16, node addr 00:22:19:93:11:49
[    2.419682] bnx2 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.422882] eth1: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem d6000000, IRQ 16, node addr 00:22:19:93:11:4b
[    2.438283] Fusion MPT base driver 3.04.07
[    2.438285] Copyright (c) 1999-2008 LSI Corporation
[    2.452882] usbcore: registered new interface driver usbfs
[    2.452907] usbcore: registered new interface driver hub
[    2.452961] usbcore: registered new device driver usb
[    2.461522] Fusion MPT SAS Host driver 3.04.07
[    2.461589] mptsas 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.461752] mptbase: ioc0: Initiating bringup
[    2.463350] USB Universal Host Controller Interface driver v3.0
[    2.467034] No dock devices found.
[    2.480547] libata version 3.00 loaded.
[    4.000010] ioc0: LSISAS1068E B3: Capabilities={Initiator}
[    4.000061] mptbase: ioc0: PCI-MSI enabled
[    4.000086] mptsas 0000:01:00.0: setting latency timer to 64
[   22.562569] scsi0 : ioc0: LSISAS1068E B3, FwRev=00192f00h, Ports=1, MaxQ=266, IRQ=2294
[   22.585612] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1601ABYS-1 6H05 PQ: 0 ANSI: 5
[   22.587625] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   22.587636] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   22.587639] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.587681] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.587717] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000cce0
[   22.587873] usb usb1: configuration #1 chosen from 1 choice
[   22.587906] hub 1-0:1.0: USB hub found
[   22.587913] hub 1-0:1.0: 2 ports detected
[   22.592970] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   22.602937] Driver 'sd' needs updating - please use bus_type methods
[   22.603276] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   22.608469] sd 0:0:0:0: [sda] Write Protect is off
[   22.608473] sd 0:0:0:0: [sda] Mode Sense: 73 00 00 08
[   22.610285] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.610626] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[   22.615829] sd 0:0:0:0: [sda] Write Protect is off
[   22.615832] sd 0:0:0:0: [sda] Mode Sense: 73 00 00 08
[   22.617619] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.617623]  sda: sda1 sda2 < sda5 >
[   22.653044] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.691450] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   22.691459] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   22.691462] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.691484] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.691516] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000ccc0
[   22.691597] usb usb2: configuration #1 chosen from 1 choice
[   22.691621] hub 2-0:1.0: USB hub found
[   22.691628] hub 2-0:1.0: 2 ports detected
[   22.801409] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[   22.801415] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   22.801419] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.801440] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.801462] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000cca0
[   22.801538] usb usb3: configuration #1 chosen from 1 choice
[   22.801562] hub 3-0:1.0: USB hub found
[   22.801568] hub 3-0:1.0: 2 ports detected
[   22.911381] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[   22.911387] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   22.911390] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.911410] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.911434] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000cc80
[   22.911507] usb usb4: configuration #1 chosen from 1 choice
[   22.911530] hub 4-0:1.0: USB hub found
[   22.911536] hub 4-0:1.0: 2 ports detected
[   23.020150] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   23.020163] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   23.020166] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.020187] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.024095] ehci_hcd 0000:00:1d.7: debug port 1
[   23.024100] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   23.024105] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xdee00000
[   23.041287] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.041362] usb usb5: configuration #1 chosen from 1 choice
[   23.041385] hub 5-0:1.0: USB hub found
[   23.041391] hub 5-0:1.0: 8 ports detected
[   23.260311] ata_piix 0000:00:1f.1: version 2.12
[   23.260317] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.260356] ata_piix 0000:00:1f.1: setting latency timer to 64
[   23.260429] scsi1 : ata_piix
[   23.260494] scsi2 : ata_piix
[   23.260528] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   23.260530] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   23.380014] usb 5-5: new high speed USB device using ehci_hcd and address 2
[   23.440387] ata1.00: ATAPI: TEAC DVD-ROM DV28EV, D.AG, max UDMA/33
[   23.480263] ata1.00: configured for UDMA/33
[   23.480298] ata2: port disabled. ignoring.
[   23.480332] isa bounce pool size: 16 pages
[   23.484847] scsi 1:0:0:0: CD-ROM            TEAC     DVD-ROM DV28EV   D.AG PQ: 0 ANSI: 5
[   23.484975] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   23.501315] Driver 'sr' needs updating - please use bus_type methods
[   23.511102] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   23.511105] Uniform CD-ROM driver Revision: 3.20
[   23.511196] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.531743] usb 5-5: configuration #1 chosen from 1 choice
[   23.531813] hub 5-5:1.0: USB hub found
[   23.531910] hub 5-5:1.0: 4 ports detected
[   23.573012] PM: Starting manual resume from disk
[   23.573015] PM: Resume from partition 8:5
[   23.573016] PM: Checking hibernation image.
[   23.573202] PM: Resume from disk failed.
[   23.630471] kjournald starting.  Commit interval 5 seconds
[   23.630491] EXT3-fs: mounted filesystem with ordered data mode.
[   25.983003] udevd version 124 started
[   26.195831] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.238689] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[   26.242220] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.257572] EDAC MC: Ver: 2.1.0 Nov  4 2008
[   26.275542] EDAC MC0: Giving out device to 'i5000_edac.c' 'I5000': DEV 0000:00:10.0
[   26.275563] EDAC PCI0: Giving out device to module 'i5000_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
[   26.311284] ACPI: Power Button (FF) [PWRF]
[   26.481009] Linux video capture interface: v2.00
[   26.605911] cx23885 driver version 0.0.1 loaded
[   26.606062] cx23885 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.606136] CORE cx23885[0]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
[   26.773620] intel_rng: FWH not detected
[   26.862233] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.873284] input: i2c IR (FusionHDTV) as /devices/virtual/input/input3
[   26.911183] iTCO_vendor_support: vendor-support=0
[   26.913196] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   27.070944] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.071383] iTCO_wdt: Found a 631xESB/632xESB TCO device (Version=2, TCOBASE=0x0860)
[   27.071431] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.230798] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-0/0-006b/ir0 [cx23885[0]]
[   27.231129] cx23885_dvb_register() allocating 1 frontend(s)
[   27.231132] cx23885[0]: cx23885 based dvb card
[   27.308327] xc2028 0-0061: creating new instance
[   27.308330] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   27.308336] DVB: registering new adapter (cx23885[0])
[   27.308339] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.308694] cx23885_dvb_register() allocating 1 frontend(s)
[   27.308696] cx23885[0]: cx23885 based dvb card
[   27.309275] xc2028 1-0061: creating new instance
[   27.309277] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   27.309280] DVB: registering new adapter (cx23885[0])
[   27.309282] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.309638] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   27.309690] cx23885[0]/0: found at 0000:08:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xd5c00000
[   27.309782] cx23885 0000:08:00.0: setting latency timer to 64
[   27.309871] cx23885 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.309950] CORE cx23885[1]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
[   27.450322] input: i2c IR (FusionHDTV) as /devices/virtual/input/input4
[   27.541932] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-3/3-006b/ir0 [cx23885[1]]
[   27.574901] cx23885_dvb_register() allocating 1 frontend(s)
[   27.574904] cx23885[1]: cx23885 based dvb card
[   27.575485] xc2028 3-0061: creating new instance
[   27.575487] xc2028 3-0061: type set to XCeive xc2028/xc3028 tuner
[   27.575490] DVB: registering new adapter (cx23885[1])
[   27.575492] DVB: registering adapter 2 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.575783] cx23885_dvb_register() allocating 1 frontend(s)
[   27.575785] cx23885[1]: cx23885 based dvb card
[   27.576359] xc2028 4-0061: creating new instance
[   27.576361] xc2028 4-0061: type set to XCeive xc2028/xc3028 tuner
[   27.576363] DVB: registering new adapter (cx23885[1])
[   27.576367] DVB: registering adapter 3 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.576638] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   27.576645] cx23885[1]/0: found at 0000:0a:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xde600000
[   27.576652] cx23885 0000:0a:00.0: setting latency timer to 64
[   27.576690] cx23885 0000:0c:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.576767] CORE cx23885[2]: subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]
[   27.717130] input: i2c IR (FusionHDTV) as /devices/virtual/input/input5
[   27.791915] ir-kbd-i2c: i2c IR (FusionHDTV) detected at i2c-6/6-006b/ir0 [cx23885[2]]
[   27.824771] cx23885_dvb_register() allocating 1 frontend(s)
[   27.824773] cx23885[2]: cx23885 based dvb card
[   27.825348] xc2028 6-0061: creating new instance
[   27.825350] xc2028 6-0061: type set to XCeive xc2028/xc3028 tuner
[   27.825353] DVB: registering new adapter (cx23885[2])
[   27.825355] DVB: registering adapter 4 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.825642] cx23885_dvb_register() allocating 1 frontend(s)
[   27.825644] cx23885[2]: cx23885 based dvb card
[   27.826218] xc2028 7-0061: creating new instance
[   27.826220] xc2028 7-0061: type set to XCeive xc2028/xc3028 tuner
[   27.826222] DVB: registering new adapter (cx23885[2])
[   27.826225] DVB: registering adapter 5 frontend 0 (Zarlink ZL10353 DVB-T)...
[   27.826499] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   27.826505] cx23885[2]/0: found at 0000:0c:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xde200000
[   27.826510] cx23885 0000:0c:00.0: setting latency timer to 64
[   28.745024] loop: module loaded
[   28.822744] lp: driver loaded but no devices found
[   29.023021] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k
[   29.312302] EXT3 FS on sda1, internal journal
[   30.157079] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.301087] bnx2: eth0: using MSI
[   30.653748] NET: Registered protocol family 10
[   30.654200] lo: Disabled Privacy Extensions
[   30.654624] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.987148] bnx2: eth0 NIC Copper Link is Up, 100 Mbps full duplex, receive & transmit flow control ON
[   31.987579] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.220005] eth0: no IPv6 routers present
[  873.567957] firmware: requesting xc3028-v27.fw
[  873.616733] xc2028 0-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[  873.816833] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  874.969988] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  874.983875] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  934.551431] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  935.801476] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  935.816329] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  935.851102] xc2028 0-0061: Incorrect readback of firmware version.
[  936.110026] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  937.360220] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  937.375078] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  937.411101] xc2028 0-0061: Incorrect readback of firmware version.
[  938.766612] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  940.021476] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  940.036328] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  940.071102] xc2028 0-0061: Incorrect readback of firmware version.
[  940.330027] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  941.580220] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  941.595077] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  941.631102] xc2028 0-0061: Incorrect readback of firmware version.
[  942.985932] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  944.230220] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  944.245079] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  944.281101] xc2028 0-0061: Incorrect readback of firmware version.
[  944.540027] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  945.790220] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  945.805093] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  945.841102] xc2028 0-0061: Incorrect readback of firmware version.
[  947.195682] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  948.450221] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  948.465078] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  948.501102] xc2028 0-0061: Incorrect readback of firmware version.
[  948.760027] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  950.010222] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  950.025080] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  950.061101] xc2028 0-0061: Incorrect readback of firmware version.
[  951.416613] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  952.670221] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  952.685078] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  952.721102] xc2028 0-0061: Incorrect readback of firmware version.
[  952.980026] xc2028 0-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[  954.230220] xc2028 0-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
[  954.245079] xc2028 0-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
[  954.281101] xc2028 0-0061: Incorrect readback of firmware version.

Now as you can see, it cannot read the fm correctly and provides an error!

If you can work this out, I will promise to buy you a beer... Hell no, I will get you pissed !!! I'll buy you a full case LoL

Hopefully you can help!

---

### Post by oobe-feisty on 2009-02-28
those messages regarding incorrect firmware i have seen mentioned before on the lists "subsystem: 18ac:db78, board: DViCO FusionHDTV DVB-T Dual Express [card=11,autodetected]" is useful and what i was looking for now we know specifcally what your tuner is and how to search for support. About 6 months back i think developers were posting patches for testing i am not sure if it has been merged you could try installing an older revision of v4l-dvb or checking the change logs of [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) for reference for your **specific** tuner being "DViCO FusionHDTV DVB-T Dual Express"

also googleing  18ac:db78 alone should find you many semi relavant pages on the mailing list

EDIT:

I did some digging around myself dont ask my why :P




see if this works for you 

hg clone [http://linuxtv.org/hg/~stoth/v4l-dvb/rev/d61c3d922e98](http://linuxtv.org/hg/~stoth/v4l-dvb/rev/d61c3d922e98)

cd d61c3d922e98

make && sudo make install 

then download firmware from pascoes old site [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)

sudo -i

cd /lib/firmware
    
wget [http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw](http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw)
    
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw)
    
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw)

leave the new firmware there just in case it cant do any harm if its not used by the drivers or if it is for that matter. 

then shut down the pc let it sit for 30 secs the boot back up. 

this assumes you have followed previous steps of this howto.

---

### Post by qigong888 on 2009-03-01
Hi oobe-feisty,

It works !!!

You are a legend ! and I need to shout you a boozup !!!

Let me know if you are in Melbourne next time and I will be very happy to oblige.

Thanks again, it worked a treat first go.

---

### Post by oobe-feisty on 2009-03-02
glad to hear it helped and i am in melbourne but i dont drink LOL 
small world though might see you round


> **qigong888 said:**
> Hi oobe-feisty,

It works !!!

You are a legend ! and I need to shout you a boozup !!!

Let me know if you are in Melbourne next time and I will be very happy to oblige.

Thanks again, it worked a treat first go.

---

### Post by OzDude on 2009-03-07
> **oobe-feisty said:**
> this is strange do you have mercurial installed
The repository itself was down. The day after your response, it was working again.

Got the remote working, although some of the mappings are wrong. Will post the requested remote info when I get around to fixing it.

Thanks!

OzDude

---

### Post by blau2009 on 2009-03-18
I can't seem to get hal to ignore the remote so lirc can access it. I have the Dual Digital 4 rev 2.

From a clean Mythbuntu 8.10 install, I install the drivers as instructed by OP with no problem, then follow the rest of the steps to setup the remote (don't do the symlink).

I add the /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi file and change the info.product to match IR-receiver. However after a reboot lshal still shows the remote, and irw shows remote button presses are interpreted as keyboard presses (eg left, right, enter).

I've tried a few different keys in the lirc.fdi file, such as vendor but no matter what I do, hal still picks up the remote. /var/log/daemon shows /dev/input/event6 cannot be accessed fully by lirc.

Any ideas?

One thing I have noticed is that dmesg | grep IR doesn't show "input: IR-receiver inside an USB DVB receiver as /class/input/input6" but instead shows "input: IR-receiver inside an USB DVB receiver as somelongstring /dev/input/event6" I can't remember what the exact string is, I can show output later. However I didn't think this would matter as it's the IR-receiver part that I'm using to make the ignore rule.

EDIT: I remember reading that it may be something to do with X using hal and that lirc may work properly outside of X. Should I test and does this sound likely?

---

### Post by oobe-feisty on 2009-03-18
this is what worked for me on 8.10 [http://ubuntuforums.org/showthread.php?p=6093982#post6093982](http://ubuntuforums.org/showthread.php?p=6093982#post6093982)

its worth pointing out both of us are using rev1 tuners im sure you have already tried this hopefully someone with a rev2 tuner can help you on this thread if you ask me ubuntu is moving to quickly with hal it is very buggy

this is what dmesg shows for me 
input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:04.0/0000:01:07.2/usb3/3-1/input/input6

why is it that you decided not to use the symlink maybe you should try

ps. there are a couple of guys discussing the rev 2 remote a few pages back i didnt pay attention maybe they can help you here i found it [http://ubuntuforums.org/showthread.php?t=616103&page=10](http://ubuntuforums.org/showthread.php?t=616103&page=10) its the first couple of posts on page 10


if you insist on not using a symlink you need to modify /etc/lirc/hardware.conf

REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/irremote"

and change REMOTE_DEVICE="/dev/input/irremote" to /dev/input/event6

this number can change hence making a symlink i doubt it is now a problem with hal but more likely some configuration error

---

### Post by blau2009 on 2009-03-18
I did try the symlink originally; at first I tried setting it up exactly as the instructions. Then I figured it may have been the symlink so I took it out and edited hardware.conf as you suggest but still no luck. I was using the same hardware each time so it was always detected as event6. I thought that once I got it working I would set up the symlink and make the necessary changes to reconfigure as irremote.

Tonight I will try installing again from a clean install (mucked around way too much now :) ) and post results. 

Actually I remember that when I made the symlink and rebooted, I don't think irremote was created. I'll try again and see how I go.

Thanks for the help so far. :)

---

### Post by blau2009 on 2009-03-19
Getting somewhere now - don't understand why I couldn't ignore the device before.

Everything seems to have installed ok. But now /var/log/daemon.log shows:

Mar 19 20:45:30 mythbox lircd-0.8.3[5258]: lircd(userspace) ready
Mar 19 20:45:42 mythbox lircd-0.8.3[5258]: accepted new client on /dev/lircd
Mar 19 20:45:42 mythbox lircd-0.8.3[5258]: initializing '/dev/input/irremote'
Mar 19 20:45:55 mythbox lircd-0.8.3[5258]: removed client
Mar 19 20:45:55 mythbox lircd-0.8.3[5258]: closing '/dev/input/irremote'

When I try to run irw, the same thing happens.

EDIT: Working now! Thanks all :)

---

### Post by blau2009 on 2009-03-19
> **tvars said:**
> Ok I fixed my remote.

Here's a summary of the problems I had.

1) I had to update /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi to stop my remote key-presses being interpreted as keyboard presses. Added the following match xml element.

```

     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>

```

2) I have two IR-receiver devices, event4 and event5. The rule to create a symlink /dev/input/irremote on boot was always picking up event5. "sudo cat /dev/input/eventX" and pressing buttons on the remote did not give any output for event5, but it did for event4. I switched my /etc/lirc/hardware.conf to point directly at event4 without going through the irremote symlink.

3) Lastly, the lircd.conf that is attached to this thread (lirc2.tar.bz2) did not match the codes for my remote. I had to record a new one using "sudo irrecord --driver=devinput --device=/dev/input/event4 lircd.conf". I've attached the resulting file to this post. I must have a newer version of this remote.

4) I had a problem with remote key presses being duplicated. irw showed two lines per keypress. I fixed this by setting "toggle_bit_mask 0x16000000" in the lircd.conf.

Sorry for triple post!

I had all these problems except the last, using the rev 2 remote. These fixes worked, lircd.conf is accurate. Thanks!

EDIT: Should lirc be closing the input every so often? If I run 

cat /var/log/daemon.log | grep event6


Mar 19 21:29:56 mythbox lircd-0.8.3[6977]: initializing '/dev/input/event6'
Mar 19 21:31:02 mythbox lircd-0.8.3[6977]: closing '/dev/input/event6'
Mar 19 21:33:12 mythbox lircd-0.8.3[6977]: initializing '/dev/input/event6'
Mar 19 21:33:18 mythbox lircd-0.8.3[6977]: closing '/dev/input/event6'
Mar 19 21:34:45 mythbox lircd-0.8.3[5258]: initializing '/dev/input/event6'
Mar 19 21:37:40 mythbox lircd-0.8.3[5258]: closing '/dev/input/event6'
Mar 19 21:40:47 mythbox lircd-0.8.3[5258]: initializing '/dev/input/event6'
Mar 19 21:42:17 mythbox lircd-0.8.3[5258]: closing '/dev/input/event6'
Mar 19 21:42:27 mythbox lircd-0.8.3[5258]: initializing '/dev/input/event6'
Mar 19 21:48:29 mythbox lircd-0.8.3[5258]: closing '/dev/input/event6'
Mar 19 22:00:55 mythbox lircd-0.8.3[5258]: initializing '/dev/input/event6'
Mar 19 22:06:33 mythbox lircd-0.8.3[5258]: closing '/dev/input/event6'

I wanted to try mapping the buttons but when I record it only senses some of the button presses and will time out. I'm holding the remote right next to the receiver. Changed the batteries too...

---

### Post by maniaq on 2009-03-21
hi all

well unfortunately I got through all eleven pages of this thread and I *still* can't get my remote to work properly!

I have the rev2 grey one and it partially works as far as number keys and arrows but it seems to be pretending to be a keyboard - I've most certainly got this hal issue (and I agree hal is waaay buggy not just from this but other issues with removable devices)

I had to actually create a /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi file - that directory was previously empty...

I'm sure my problem is hal getting in the way of lirc but I just can't figure out how to stop it?

only other thing that was different for me, I couldn't record any remote codes with irrecord - not on event4 (which caused a segmentation fault) or event5 ("gap not found, can't continue") - again, the remote was just being a keyboard and NOT a remote...

anyone got any suggestions?

---

### Post by oobe-feisty on 2009-03-22
you need to shutdown lircd sudo /etc/init.d/lirc stop before irrecord will work. 

I really dont know how different rev1 and rev2 are in respect to remote setup but i suspect in principle not very.

basically the mappings are different lircd.conf i tried my best to provide working lirc configs for rev 2 but am unable to do more i can say i have verified the rev2 lircd.conf to work over ssh person on other end pressed remote keys while i ran irw after install and i could see key presses how i setup the remote originally was by following the advice in one of my external links that was a setup guide for an older very different but simarly name dvico card however the principle is the same 

best of luck cheers 

P.S F.Y.I  the file /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi did not exist for me to edit either until i had configured lirc correctly then it appeard i kept the unedited version 

```
oobe@box:~$ diff /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi.old /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi
8,14c8
<      <match key="info.product" contains_ncase="IR-Receiver">
<         <merge key="info.ignore" type="bool">true</merge>
<      </match>
<      <match key="info.product" contains_ncase="cx88 IR">
<         <merge key="info.ignore" type="bool">true</merge>
<      </match>
<      <match key="info.product" contains_ncase="bttv IR">
---
>      <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
```

---

### Post by blau2009 on 2009-03-22
> **maniaq said:**
> hi all

well unfortunately I got through all eleven pages of this thread and I *still* can't get my remote to work properly!

I have the rev2 grey one and it partially works as far as number keys and arrows but it seems to be pretending to be a keyboard - I've most certainly got this hal issue (and I agree hal is waaay buggy not just from this but other issues with removable devices)

I had to actually create a /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi file - that directory was previously empty...

I'm sure my problem is hal getting in the way of lirc but I just can't figure out how to stop it?

only other thing that was different for me, I couldn't record any remote codes with irrecord - not on event4 (which caused a segmentation fault) or event5 ("gap not found, can't continue") - again, the remote was just being a keyboard and NOT a remote...

anyone got any suggestions?

I had the same problem and I just couldn't figure it out. Only way I got hal to ignore the device was to do a clean reinstall of mythbuntu. I still have a few issues but at least it's being recognised as the remote now. 

Don't know if it helps but this time around, setting up the remote was the first thing I did. Whereas the time before I had manually added the medibuntu repositories and got all the codecs etc. Wouldn't think it would make a difference but it could...

The fdi file did not exist for me either, I had to create it with info.product being IR-receiver.

Finally irrecord won't work until you've got the remote working under lirc, not hal. I used a different lircd.conf for basic testing, the one provided as lirc2 in the first post wasn't accurate for me. I can upload the lircd.conf tonight if you like. Also I will be redoing irrecord just to make sure it all works so I could upload my version too.

---

### Post by maniaq on 2009-03-22
I too tried doing a clean reinstall, but got no further...

I've had a closer look at a dump of lshal and might try messing around with that fdi file - maybe use info.udi instead of info.product?

I've got to get hal to let go of the device - or stop treating it as "hald-addon-keyboard"

---

### Post by tqft on 2009-03-23
> **maniaq said:**
> I too tried doing a clean reinstall, 

On this point if anyone had a good way of cleaning up the mess you make stuffing around with these things (especially myself) and restoring the files and configuration to something close to "normal" or "standard" I would appreciate knowing about it.

I think part of the problem some of us have is we try stuff and can never completely undo all the changes.

sudo apt-get remove <something>
or
sudo dpkg-reconfigure <something> 
might help

but with all the changes etc it can be hard to clean up after yourself.

---

### Post by maniaq on 2009-03-23
SUCCESS!!

I don't know what exactly did the trick - I took soooo many steps, some quite convoluted - but for the uninitiated, here's what I did:

*first and foremost, compeletely clean reinstall and changed the order of what I installed-
  *kubuntu (7.10 coz I was originally gonna use LinuxMCE but it's a nice, efficient little install and I like it)
  *nvidia drivers (from repos, not from nvidia)
  *mythtv (probably should have held off actually until after the next step)
  *v4l-dvb drivers from linuxtv.org
*next I configured mythtv-backend, scanning and adding channels etc...
*this I would consider extraneous, but next I configured the Mythbuntu Control Panel - LEAVING the remote section BLANK (because there's no dev/input option)
*so when this restarts I'm in xfce now which is ok - bootup time has been drastically reduced so I'm cool with it
*now the fun begins - the remote!
  *I confirm it's still behaving like a keyboard and look at lshal, as per my above post
  *once again no fdi file so I create one - initially using info.product="IR-receiver..." but changing that to info.udi - makes no difference whatsoever

(I should note at this point it *STILL* thinks the remote is a keyboard!)
  *a bit of searching led me to this:

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1076468&r=17012912#r17012912](http://forums.whirlpool.net.au/forum-replies.cfm?t=1076468&r=17012912#r17012912)

(apologies - Tinyurl doesn't like it)

  *so I follow the instructions and create the /etc/modprobe.d/usbhid file - mine says:

options usbhid quirks=0x0fe9:0xdb98:0x0004

    *I will never know if this makes any difference whatsoever - I suspect not because the driver mentioned in /proc/bus/usb/devices is dvb_usb_cxusb - NOT usbhid

  *ok so **oobe-feisty** above suggested setting up lirc properly should get that fdi file generated so let's have a look-see...
    *prob'ly a mistake but I left the hardware.conf file (in /etc/lirc) alone at this point and simply replaced the lircd.conf file (same place) with one I was pretty sure was the right one
    *a bit of mucking around with the daemon and irw - still no joy
    *a hexdump of /dev/input/event4 confirms THIS is what lirc should be looking at (as opposed to event5)
    *ok let's go back into Mythbuntu Control Center and enable the DVICO remote
    *still no joy, but I notice the lircd.conf file has been replaced - with the old one backed up
    *ok when I look at /var/log/daemon.log | grep lirc I see it's looking at hiddev0 - never did THAT before...
    *ok the hardware.conf was also changed - but not backed up - bummer - ok I back this one up as hardware.conf.dvico and edit this one
      *THIS is what I suspect did the trick - I changed the DRVIER from "dvico" to "dev/input" and the DEVICE to "dev/input/event4" (this previously did nothing but I have a fresh install now so why not) and I also changed the LIRCD_CONF from "dvico/lircd.conf.fusionHDTV" to just "lircd.conf"
      *revert the lircd.conf file
      *restart the daemon (/etc/init.d/lirc) and let's try irw again...

AND IT WORKS! I'm seeing codes! ...and they end with new-lircd.conf.conf? that's strange, but I'll take it!

ok so I went back into MythTV - but nothing...

I scratched my head briefly and then remembered the lircrc file in the (~/).mythtv folder - on my previous install I had to create that folder and manually put the file in there myself - this time the folder and the file are already there...

-and it looks a little strange - I think this was generated by mythtv when I added the DVICO remote in the control panel - so I dig out my backup of the lircrc file I got from some place on the net, what seems like many years ago now...

I drop the new file in (after backing up the old one) and restart mythtv - and now the remote is working with THAT too!


like I said, long and convoluted but somewhere in there something did the trick and I got it working

thanks for the suggestions guys - I think just getting my head around what you were saying actually led me to my answer - in a long and convoluted way...

---

### Post by blau2009 on 2009-03-23
Good to hear you got it working!

Does your remote work with the lirc2.conf provided by oobe in the first post?

Mine works but /var/log/daemon.log shows lircd initializing and closing the remote all the time. Also the buttons don't register presses all the time - sometimes some stop working, sometimes they all stop working.

I was going to try doing irrecord to create my own button mappings, not sure if this will help.

Are you having the same issues?

---

### Post by maniaq on 2009-03-23
yes I think that may well be where I got my lirc.conf file from - I remember comparing it to the Chris Pascoe one and they were pretty much identical, and matched codes from my hexdumps (as well as irw, now that it's working)

I can see lots of initialising and closing the remote in the log but I've opened and closed the program (mythtv) a number of times and for all I know these correspond exactly to those instances... or maybe there's a timeout and then a new button-press wakes it up (I must admit I actually find it a bit convenient that it can double as a keyboard!)

so far the buttons seem to work ok, but it's only been up for a few hours...


I'm now in the process of mapping out an xbmc Lircmap.xml file - would anyone be interested if I uploaded this once I got it sorted?

---

### Post by oobe-feisty on 2009-03-23
> **tqft said:**
> On this point if anyone had a good way of cleaning up the mess you make stuffing around with these things (especially myself) and restoring the files and configuration to something close to "normal" or "standard" I would appreciate knowing about it.

but with all the changes etc it can be hard to clean up after yourself.

you can back up and restore you system fairly easily using tar i have done it before performing version upgrades i can verify this [thread]("http://ubuntuforums.org/showthread.php?t=35087") works


> **tqft said:**
> I think part of the problem some of us have is we try stuff and can never completely undo all the changes.

this is somthing i have noticed with tutorials in general people copy and paste commands with out fully understanding what they are doing but of course knowing what the end result is they want to achieve
i think generally if people make an effort to understand each step they are taking you can generally restore things or atleast know when you are passing a point of no return.



> **blau2009 said:**
> 
Finally irrecord won't work until you've got the remote working under lirc, not hal. I used a different lircd.conf for basic testing, the one provided as lirc2 in the first post wasn't accurate for me. I can upload the lircd.conf tonight if you like. Also I will be redoing irrecord just to make sure it all works so I could upload my version too..

glad you got irrecord to work i will add your lircd.conf to the tutorial if you want i would appreciate you positing it



> **blau2009 said:**
> Good to hear you got it working!

Does your remote work with the lirc2.conf provided by oobe in the first post?

?

yes he is cause it says this when he does irw "AND IT WORKS! I'm seeing codes! ...and they end with new-lircd.conf.conf" the new-lircd.conf.conf is from the lircd.conf that tvars made and i updated on the links


btw the way my remote works fine and my remote appears when i type lshal 


> **maniaq said:**
> *I will never know if this makes any difference whatsoever - I suspect not because the driver mentioned in /proc/bus/usb/devices is dvb_usb_cxusb - NOT usbhid

im 101% sure it wont was that thread is for mce usb recievers


> **maniaq said:**
> *prob'ly a mistake but I left the hardware.conf file (in /etc/lirc) alone at this point and simply replaced the lircd.conf file (same place) with one I was pretty sure was the right one

yep thats a mistake as you discovered 

> **maniaq said:**
> *THIS is what I suspect did the trick - I changed the DRVIER from "dvico" to "dev/input" and the DEVICE to "dev/input/event4" (this previously did nothing but I have a fresh install now so why not) and I also changed the LIRCD_CONF from "dvico/lircd.conf.fusionHDTV" to just "lircd.conf"

thats what fixed it the idea of my tutorial is that you use all the files not just lircd.conf overwrite existing files then install the sample lircrc and modify it to your likeing saves time if you understand what your doing first

> **maniaq said:**
> *once again no fdi file so I create one - initially using info.product="IR-receiver..." but changing that to info.udi - makes no difference whatsoever

on 7.04? this is most likley not necessary as the problem only occurs in 8.10 as they are changing the way hal configures devices


> **maniaq said:**
> I scratched my head briefly and then remembered the lircrc file in the (~/).mythtv folder - on my previous install I had to create that folder and manually put the file in there myself - this time the folder and the file are already there...

thats in my guide to :P i even supply the lircrc to modify

---

### Post by maniaq on 2009-03-23
thanks **oobe-feisty** - I should note I did orginally follow your guide to the letter (and understood what I was doing too) but it simply didn't work...

as I mentioned, I had "dev/input/event4" in my hardware.conf file in my previous install as well, but it did nothing

I think the problem previously was the LinuxMCE install which took two CD's and something like 90minutes to install itself and mess with the nice fresh 7.10 Gutsy - it obviously doesn't do a proper MythTV install because there was no .mythtv directory (I had to create one) - or maybe it put one somewhere other than my home directory?

point being, even tho it didn't work for me that time, I learned much by trying to make it work and after doing a fresh, clean install, I had something of a roadmap to help me get where I wanted to go this time around - and your guide was an integral resource for this - thanks again!


btw I've got it working with xbmc too now - if anyone is interested, I'll upload the necessary Lircmap.xml and Keymap.xml files

---

### Post by oobe-feisty on 2009-03-26
> **maniaq said:**
> 
btw I've got it working with xbmc too now - if anyone is interested, I'll upload the necessary Lircmap.xml and Keymap.xml files

yeah i wouldnt mind seeing them

---

### Post by blau2009 on 2009-03-27
I just decided to do a reinstall after changing motherboards, CPU + RAM.

Following the instructions but get stuck at "hg clone http://linuxtv.org/hg/v4l-dvb"

I get 

root@mythbox:~# hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
destination directory: v4l-dvb
abort: 'http://linuxtv.org/hg/v4l-dvb' does not appear to be an hg repository!

EDIT: Appears it's working, after trying several times.


Any ideas?

---

### Post by oobe-feisty on 2009-03-27
> **blau2009 said:**
> I just decided to do a reinstall after changing motherboards, CPU + RAM.

Following the instructions but get stuck at "hg clone http://linuxtv.org/hg/v4l-dvb"

I get 

root@mythbox:~# hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
destination directory: v4l-dvb
abort: 'http://linuxtv.org/hg/v4l-dvb' does not appear to be an hg repository!

EDIT: Appears it's working, after trying several times.


Any ideas?


somthing up with the repository most likely only temporary it may have been missing the .hg directory

---

### Post by maniaq on 2009-03-27
ok the files are attached - they go in your ~/.xbmc/userdata directory

so some of the button assigments are quite arbitrary, due to what buttons are available on my (rev2) remote and what actions are available in the software...

the <remote device> attribute in Lircmap.xml (in my case "FusionREMOTE") is the name of your remote, as per what is in your /etc/lirc/lircd.conf configuration and the names of the various buttons (eg "ratio" in my case) also comes from that same configuration - you can have that file open to inspect, or what I did was just have irw running and press some buttons on the remote...

mess with the xml attributes all you like to suit your remote/preferences but the xml tags MUST be exactly what they are for the software to map properly - so for eg. in Lircmap.xml:

<display>ratio</display>

your lircd.conf might call the "ratio" button something else so you can change that to suit, but the "display" part is specific to xbmc - of course you can rearrange what buttons to map what...

same goes for Keymap.xml - the Captilised actions inside the tags can be rearranged to suit, but be careful


more info here:

[http://xbmc.org/wiki/?title=Keymap.xml#Available_actions](http://xbmc.org/wiki/?title=Keymap.xml#Available_actions)

---

### Post by wombo on 2009-03-30
I have not downloaded the latest v4l tree, I am hoping that I can just use those provided in the kernel.

> did you compile the v4l-dvb source or are you using modules in the newer kernel ?

what does "dmesg | grep dvb" say?

here you go

```
htpc@htpc:~$ dmesg | grep dvb
[   13.417770] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   13.418132] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.721795] dvb-usb: schedule remote query interval to 100 msecs.
[   13.721954] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   13.721968] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   13.722128] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.801336] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   13.801366] usbcore: registered new interface driver dvb_usb_cxusb
```

That looks ok to me?

---

### Post by oobe-feisty on 2009-03-31
maybe all you need to do is plonk in the firmware xc3028-v27.fw into /lib/firmware 

you can dload it from the attachements in the first post of this thread or you can make an identical one using a script that comes in v4l-dvb source

---

### Post by wombo on 2009-03-31
I should be heading home from work soon, I will give it a try and report back.

Thanks

---

### Post by wombo on 2009-03-31
> **oobe-feisty said:**
> maybe all you need to do is plonk in the firmware xc3028-v27.fw into /lib/firmware 

you can dload it from the attachements in the first post of this thread or you can make an identical one using a script that comes in v4l-dvb source

That fixed it.

So for anyone who is interested, currently in Mythbuntu 9.04 all you need to do to get the DD4 running is to copy the XC3028-v27.fw file into the /lib/firmware folder

---

### Post by oobe-feisty on 2009-04-01
> **wombo said:**
> That fixed it.

So for anyone who is interested, currently in Mythbuntu 9.04 all you need to do to get the DD4 running is to copy the XC3028-v27.fw file into the /lib/firmware folder

i just thought of somthing before you said you were running a rev2 i have rev1 only and i need the firmware but i was under the impression that rev 2 does not can you show me the output of "lsusb" just to satisfy my curiosity

---

### Post by wombo on 2009-04-01
This is all post adding in the firmware file


LSUSB

```
Bus 002 Device 003: ID 0fe9:db78 DVICO 
Bus 002 Device 002: ID 0fe9:db78 DVICO 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0471:0815 Philips eHome Infrared Receiver
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

dmesg | grep dvb

```
[   13.454236] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   13.454506] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.901566] dvb-usb: schedule remote query interval to 100 msecs.
[   13.901720] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   13.901734] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   13.901889] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.981475] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   13.981508] usbcore: registered new interface driver dvb_usb_cxusb

```

---

### Post by wombo on 2009-04-01
Ok im trying now to get the remote up and running.

I have tried running through the instructions but there seems to be something else wrong.

when I do a dmesg | grep IR I get this
Note that Mythfront end started automatically and I closed it at the end.
```
[   12.572399] lirc_dev: IR Remote Control driver registered, major 61 
[   12.718671] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   13.518013] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.736170] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.830055] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:02:06.2/usb2/2-1/input/input6
[   13.916603] cxusb: No IR receiver detected on this device.
[   53.784000] lirc_imon: IR port opened
[   71.401210] lirc_imon: IR port closed

```

Is there a really low level test I can do just to see if it is communicating, I have done a IRW but get nothing.


Note that I did have the MCE receiver plugged in for a little while, that has been removed now.

---

### Post by oobe-feisty on 2009-04-01
yep your using a rev1 tuner lucky i forgot rev2 doesnt need firmware when i suggested that solution 

> **wombo said:**
> This is all post adding in the firmware file


LSUSB

```
Bus 002 Device 003: ID 0fe9:db78 DVICO 
Bus 002 Device 002: ID 0fe9:db78 DVICO 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0471:0815 Philips eHome Infrared Receiver
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

dmesg | grep dvb

```
[   13.454236] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   13.454506] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.901566] dvb-usb: schedule remote query interval to 100 msecs.
[   13.901720] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   13.901734] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   13.901889] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.981475] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   13.981508] usbcore: registered new interface driver dvb_usb_cxusb

```

---

### Post by jyavenard on 2009-04-03
Hi

Two DVICO Dual Digital 4 rev 2 here...

Cards work fine (though sometimes the tuner of one isn't recognised and you need to turn the PC off for the card to re-appear).

However, every two seconds, the following message appear in the log:
Apr  3 18:43:43 hi-2-backend kernel: [160842.812070] dvb-usb: bulk message failed: -110 (6/0)

There's thousands of those ...

Any ideas the reason for this ?

Running v4l-dvb drivers I extracted on March 10th, 2009...

Thanks
Jean-Yves

---

### Post by oobe-feisty on 2009-04-03
> **jyavenard said:**
> Hi

Two DVICO Dual Digital 4 rev 2 here...

Cards work fine (though sometimes the tuner of one isn't recognised and you need to turn the PC off for the card to re-appear).

However, every two seconds, the following message appear in the log:
Apr  3 18:43:43 hi-2-backend kernel: [160842.812070] dvb-usb: bulk message failed: -110 (6/0)

There's thousands of those ...

Any ideas the reason for this ?

Running v4l-dvb drivers I extracted on March 10th, 2009...

Thanks
Jean-Yves
you are not the only one who experiences this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229879](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229879) its worth mentioning that it can be worse than just filling up the logs so you are lucky refer to above link.


I dont know the exact reason for this however someone once said it was to do with the board itself rather than the drivers which i dont believe. anyway the only way i have gotten rid of this problem on my rev1 tuner is to try different builds of the v4l-dvb tree you can browse the hg repo and look thru the recent changes, also before intrepid i always built my own vanilla kernel and that helped. 

i am not getting any problems with 2.6.27-11-generic intrepid stock kernel at all when i built a vanilla i did really bad too so you can see different kernels do make a difference. our boards are completly different so dont think 2.6.27-11-generic will automatically work for you but if you build the latest kernel from kernel.org it will already have rev2 support built in so no need to compile and install v4l-dvb.


so having said all that trial and error is the only way i used to keep a log of v4l-dvb builds that i used and had success with so i could roll back if it returned.

---

### Post by jyavenard on 2009-04-04
> **oobe-feisty said:**
> 
i am not getting any problems with 2.6.27-11-generic intrepid stock kernel at all when i built a vanilla i did really bad too so you can see different kernels do make a difference. our boards are completly different so dont think 2.6.27-11-generic will automatically work for you but if you build the latest kernel from kernel.org it will already have rev2 support built in so no need to compile and install v4l-dvb.


so having said all that trial and error is the only way i used to keep a log of v4l-dvb builds that i used and had success with so i could roll back if it returned.

I am running the latest v4l-dvb drivers (with vanilla ubuntu kernel)...
Will update to Jaunty later this month.

---

### Post by anthony_cullen on 2009-04-05
Hello,

I am hoping someone within this thread will be able to help me.  I have installed Mythbuntu 8.10 from the live CD and am trying to get this running with a Dvico Dual Digital 4 DVB-T card which is Rev 2.

I have followed the tutorial but ran into some trouble with the mercurial step and had to install it manually.

I am able to clone the v4l source and have done a make && make install however when I try to execute the test channel scan I get an error saying:

tony@tony-desktop:/dev$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-canberra 
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-canberra
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

I have tried cd'ing to /dev/dvb-t and it dow not exist and have done an las -la as root and the device does not appear.

I have tried executing the make as separate steps eg 
make all 
make install
still no /dev/dvb-t

I know the card is not fault as I have had it working under windows but this is my first myth build and chances are I am missing something obvious.

Am I better off installing ubuntu 8.10 rather than mythbuntu 8.10 ? Could this be causing my grief ?

thanks,
Tony

---

### Post by jyavenard on 2009-04-05
> **anthony_cullen said:**
> 
tony@tony-desktop:/dev$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-canberra 
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-canberra
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

I have tried cd'ing to /dev/dvb-t and it dow not exist and have done an las -la as root and the device does not appear.

I have tried executing the make as separate steps eg 
make all 
make install
still no /dev/dvb-t

I know the card is not fault as I have had it working under windows but this is my first myth build and chances are I am missing something obvious.

Am I better off installing ubuntu 8.10 rather than mythbuntu 8.10 ? Could this be causing my grief ?

thanks,
Tony

Would not make a difference running ubuntu 8.10 or mythbuntu ; they run the same core components.

BTW, I created ubuntu packages for both hardy and intrepid for v4l-dvb running using dkms..
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by oobe-feisty on 2009-04-06
> **jyavenard said:**
> BTW, I created ubuntu packages for both hardy and intrepid for v4l-dvb running using dkms..

nice one nice work

---

### Post by enchesss on 2009-04-08
I just did an update that required a restart and now myth tv no longer works. have a dual digital 4. what is the best way to udate the driver? do i need to re clone and start from scratch?
I think the drivers are ok becuase the light is on on the card

---

### Post by jyavenard on 2009-04-08
> **enchesss said:**
> I just did an update that required a restart and now myth tv no longer works. have a dual digital 4. what is the best way to udate the driver? do i need to re clone and start from scratch?
I think the drivers are ok becuase the light is on on the card

You do need to recompile the drivers.
just redo the make clean all ; make install process.

---

### Post by enchesss on 2009-04-09
thank you

this worked:

```
sudo -i
```

then password

```
cd 4vl-dvb
```

```
make distclean
```

then wait then

```
make && make install
```

then wait longer

then reboot

---

### Post by blau2009 on 2009-04-24
Anyone tried a clean install using Mythbuntu 9.04 with a rev 2 card? I'm about to do it now.

Is it true the drivers and remote support are now included in the kernel? Will 9.04 fix the hal issue where the remote is detected as a keyboard?

---

### Post by gmorris456 on 2009-04-24
I hope someone can help me, have been through this thread and still cant get the dvico device working
I hope someone can help me as I have no hair left (didnt have much to start with)
I am running mandriva 2009, have done the firmware and install which both seemed to runok, done a reboot, if I run xine or tvtime tv viewer theres no input device
I havent even started on mythtv as I had lots of problems getting it working with mysql permissioning so this is a fresh mandriva install

uname -r
2.6.27.19-desktop586-1mnb
lsusb
Bus 001 Device 003: ID 0fe9:db98 DVICO
Bus 001 Device 002: ID 0fe9:db98 DVICO
dmesg|grep dvb
usbcore: registered new interface driver dvb_usb_cxusb

have also checked under /etc and theres no vid0 or anything vid* so I dont know what to do from here


now try and remember I am a linux noob here so any advice will be appreciated but it has to take into account that I know little about linux

---

### Post by jyavenard on 2009-04-24
> **blau2009 said:**
> Anyone tried a clean install using Mythbuntu 9.04 with a rev 2 card? I'm about to do it now.

Is it true the drivers and remote support are now included in the kernel? Will 9.04 fix the hal issue where the remote is detected as a keyboard?

yep, works fine ...

---

### Post by jyavenard on 2009-04-25
> **gmorris456 said:**
> I hope someone can help me, have been through this thread and still cant get the dvico device working
I hope someone can help me as I have no hair left (didnt have much to start with)

Are you sure you did read it ?

It's in the first post.

You need to get a newer kernel > 2.6.28 or compile and install a newer version of v4l-dvb

You won't find anything in /etc

It's in /dev
After you've installed the drivers properly, you will get some new entries in /dev/dvb/
/dev/dvb/adapter0 and /dev/dvb/adapter1

Then configure your player to use a DVB adapter

> 
[snip]
now try and remember I am a linux noob here so any advice will be appreciated but it has to take into account that I know little about linux

It is a ubuntu forum BTW, so running mandriva and asking question here is rather pointless

---

### Post by blau2009 on 2009-04-25
> **jyavenard said:**
> yep, works fine ...

Yep I found the card was detected fine and displayed in Mythtv. I did have some problems with the remote, but I read and re-read what had happened in this post: [http://ubuntuforums.org/showpost.php?p=6941074&postcount=115](http://ubuntuforums.org/showpost.php?p=6941074&postcount=115) and got it to work.


So for anyone doing a clean install of 9.04 with a rev 2 tuner, here's how you get the remote working, some of this is copied from oobe-feisty's guide on page 1:

1. Configuring LIRC

in a console type

"sudo dpkg-reconfigure lirc"

scroll down to linux input layer then select it

on page 2 for IR transmitter select none

on page 3 select /dev/input/eventX (like event4 or something similar, doesn't matter too much at this stage).



2. Download the attached lirc2.tar.bz2, it should go to your desktop

cd ~/Desktop

tar xvjf lirc2.tar.bz2

cd lirc2

sudo cp -R lirc /etc


3. Install the basic lircrc config for mythtv

mv /etc/lirc/lircrc ~/.mythtv

ln -s ~/.mythtv/lircrc ~/.lircrc

sudo ln -s ~/.mythtv/lircrc /etc

sudo ln -s ~/.mythtv/lircrc /etc/lirc


4. Edit the /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi file, you will see there are already some entries. You want to edit the entries so you have these:

     <match key="input.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>

Notice how I changed "IR-Receiver" to "IR-receiver" with no capital R. Also I changed it to the full string ("IR-receiver inside an USB DVB receiver") but that might not matter.


5. I rebooted at this stage, might be necessary for the changes to hal.


6. After rebooting, type the command "dmesg|grep IR". At the end of the output, you will see two entries something like 

[    5.906622] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:02:02.2/usb2/2-1/input/input7
[    6.258893] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:02:02.2/usb2/2-2/input/input8

The first one is your remote, remember the input number (for me it's input7).

7. To make sure it's your remote, type
"sudo cat /dev/input/eventX"
Where X is the input number you just found out. So for me I type "sudo cat /dev/input/event7" because in the last step, I found my remote was input7.

Now press some buttons and you should see something appear in the terminal, doesn't matter if it looks like gibberish, as long as it corresponds with when you push the buttons.

8. OK, so now open up Mythbuntu Control Centre. In the remotes section, change your remote from Linux input layer to Dvico USB remote. Make sure to tick the box to generate the mappings. Save the changes and exit the Control centre.

9. Edit your /etc/lirc/hardware.conf file. You want it to look like this, except instead of using event7, you will use whatever event you found out your remote was detected as.

```

 # Arguments which will be used when launching lircd
 LIRCD_ARGS=""
 
 #Don't start lircmd even if there seems to be a good config file
 START_LIRCMD=false
 
 #Try to load appropriate kernel modules
 LOAD_MODULES=true
 
 # Run "lircd --driver=help" for a list of supported drivers.
 DRIVER="dev/input"
 # If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
 # automatically used instead
 DEVICE="/dev/input/event7"
 MODULES=""
 # Default configuration files for your hardware if any
 LIRCD_CONF="/etc/lircd/lircd.conf"
 LIRCMD_CONF=""
REMOTE="DViCO USB Remote"
REMOTE_MODULES=""
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_LIRCD_CONF="lircd.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"


```

Important: You need to make sure REMOTE_DRIVER="dev/input" Don't set it to devinput without the slash in the middle! This caused me problems because the hardware.conf you have before this, has it without the slash, so I changed it back mistakenly. It needs the slash in there! 


10. Now we need to copy back our lircd.conf file from the downloaded archive. Copy the lircd.conf to /etc/lirc/lircd.conf with

cp ~/Desktop/lirc2/lircd.conf /etc/lirc/lircd.conf


11. Also from the attached archive you need to copy the lircrc file to /home/yourusername/.mythbox/lircrc with

cp ~/Desktop/lirc2/lirc/lircrc ~/.mythbox/lircrc


12. Now restart the lirc daemon with

sudo /etc/init.d/lirc restart

Your remote should now be functioning. You can test it with irw and in Mythtv.


ETA: Btw, I don't know why but like oobe-feisty, my remote still shows up when I do a "lshal|grep IR". I don't know why this happens but the remote works fine. :)

pvr@mythbox:~$ lshal|grep IR
  input.product = 'IR-receiver inside an USB DVB receiver'  (string)
  input.product = 'IR-receiver inside an USB DVB receiver'  (string)


EDIT: Might clean this up with proper commands to make it easier, with straight forward commands I think someone could do it copy pasting.

---

### Post by gmorris456 on 2009-04-25
> **jyavenard said:**
> Are you sure you did read it ?

It's in the first post.

You need to get a newer kernel > 2.6.28 or compile and install a newer version of v4l-dvb

You won't find anything in /etc

It's in /dev
After you've installed the drivers properly, you will get some new entries in /dev/dvb/
/dev/dvb/adapter0 and /dev/dvb/adapter1

Then configure your player to use a DVB adapter



It is a ubuntu forum BTW, so running mandriva and asking question here is rather pointless


No I didnt read any of the entire thread, I just post on threads randomly for the heck of it!
I read it but as I said i am a noob to linux and a lot of it doesnt make any sense to me, i could go and install windoze and I have a cd with the driver but I want to try linux, mandriva seemed the best one for me to go with!
I thought this thread was about installing the dvico device and I was sent to this by another forum, so thats why I am here, there isnt much on the mandriva forum and this seemed to be a more specific forum for the issue I am having with the card!

---

### Post by blau2009 on 2009-04-25
> **gmorris456 said:**
> No I didnt read any of the entire thread, I just post on threads randomly for the heck of it!
I read it but as I said i am a noob to linux and a lot of it doesnt make any sense to me, i could go and install windoze and I have a cd with the driver but I want to try linux, mandriva seemed the best one for me to go with!
I thought this thread was about installing the dvico device and I was sent to this by another forum, so thats why I am here, there isnt much on the mandriva forum and this seemed to be a more specific forum for the issue I am having with the card!

If you have a rev 2 tuner and don't mind which distro you use, you could download mythbuntu 9.04 and follow the directions I have posted above, it is now at the stage where it's almost running out of the box, only a bit of config to do. If you need help with any of the other stuff with mythbuntu send me a PM, I have just set it up today so should be able to help.

---

### Post by gmorris456 on 2009-04-25
> **blau2009 said:**
> If you have a rev 2 tuner and don't mind which distro you use, you could download mythbuntu 9.04 and follow the directions I have posted above, it is now at the stage where it's almost running out of the box, only a bit of config to do. If you need help with any of the other stuff with mythbuntu send me a PM, I have just set it up today so should be able to help.


thanks for your help, I am going to keep trying with the mandriva distro, I tried the mythbuntu but couldnt get the video driver installed so i was stuck with 640x480 graphics which pi%%ed me off no end even after trying to install the driver from nvidea, will try and update the kernel and see what happens, thanks for understanding and posting something that doesnt put down a noob!

---

### Post by blau2009 on 2009-04-25
No problems, what video card do you have? And which version of Mythbuntu were you using, with which Nvidia drivers? Revision 180 has recently come out, which added support for a bunch of cards, you may be able to use it now.

I have installed Mythbuntu with a number of video cards, all older nvidia cards (6000 and 7000 series). They have all worked perfectly, even the open source drivers gave s-video output to the tv during install.

If you're a bit stuck with Linux in general then I'd definitely recommend Mythbuntu over other HTPC distros, it seems to have the most support, not to mention features. You could try installing it next to the Mandriva install, the partitioner in the Mythbuntu installer will take care of it. Even if it doesn't work out you can just delete it later.

Depending on the specs of the box you should be able to pick up an nvidia card for pretty cheap, I just bought an AGP 512mb geforce 6200 for about $60 australian. If Mandriva is too much hassle, maybe consider this with Mythbuntu - it might save you a couple of hours of mucking around on Mandriva and for not much money!

Depends on your system though, I am running a P4 3ghz box with that card which suits it well, if you have a newer system with PCI-e you should be able to get something fairly cheap too, just make sure it's in line with the rest of the system.

One last thing is that if you haven't got much set up on the box yet, perhaps consider installing fresh with the latest version of either distro. Upgrading the kernel probably isn't worth it, best to just start with a clean install. Like I said, the recent nvidia drivers (180) have just come out and they are included in Mythbuntu 9.04.

Hope that helps, good luck!


EDIT: Oh and by the way if anyone needs help with other config of the Dvico card in Mythbuntu, feel free to PM me. If you're in Australia I can help you set up Shepherd too, which is the app that grabs TV schedule data from various internet sources to build the program guide.

---

### Post by gmorris456 on 2009-05-06
I'm trying to get the fusion hdtv dvico dual digital 4 installed and its driving me crazy, I tried a kernel upgrade but just stuffed up my system (I guess I did something wrong), I found mandriva just put out a new version with the new kernel and that didnt get the card working either, have gone back to pclinuxos and will see what happens, I think I already mentioned it but the mythbuntu couldnt display higher than 640x480 and I couldnt get the driver to update so its back to square one again

---

### Post by blau2009 on 2009-05-06
If you're using Mythbuntu 9.04, you don't have to upgrade the driver; the latest nvidia driver is included.

What video card are you using? Pretty much any nvidia would work ok, those cards that are too old wouldn't be able to handle HD resolutions anyway.

---

### Post by gmorris456 on 2009-05-08
still trying with the dvico card, I have the driver installed ok as its showing up in control centre hardware as bluebird x 2
but if I run any tv apps theres no device, I dont know what to do so can anyone help me as the info I get from the many forums is confusing and conflicting
lsusb
Bus 001 Device 003: ID 0fe9:db98 DVICO
Bus 001 Device 002: ID 0fe9:db98 DVICO
 
I cant see anything for my card under dmesg, should there be something if so what should I see?
 
got it working at last, thanks for the above post, anyway installed 9.04 and dmesg shows the card in 'warm state' so I guess that means its working!

---

### Post by cstoh on 2009-05-14
[QUOTE=oobe-feisty;3791647]**Quick Note**

ubuntu 9.04 should support rev1 and rev2 out of the box 


**Driver Installation**

sudo -i 

apt-get update

apt-get install install mercurial build-essential linux-headers-`uname -r`

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

cd v4l-dvb

make && make install 

exit


I find that the line

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

takes along time and still do not complete. Is this normal?

---

### Post by oobe-feisty on 2009-05-19
> **cstoh said:**
> [QUOTE=oobe-feisty;3791647]**Quick Note**

ubuntu 9.04 should support rev1 and rev2 out of the box 


**Driver Installation**

sudo -i 

apt-get update

apt-get install install mercurial build-essential linux-headers-`uname -r`

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

cd v4l-dvb

make && make install 

exit


I find that the line

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

takes along time and still do not complete. Is this normal?

should take about 2 mins maybe you have a slow internet connection

---

### Post by wombo on 2009-05-23
I have been away from home for quite a while and I have just came back and tried to use Mythtv but it seemed to be broken.

The normal TV was fine watching any channels.

But in Mythtv I was getting no lock at all on any channel.

I tried a few different things to no avail.

I ended up downloading the a new v4l tree and using that but now I am just getting spammed with
```
[  373.284159] cxusb: i2c read failed
[  375.385180] dvb-usb: bulk message failed: -110 (4/0)
[  375.385189] cxusb: i2c read failed
[  377.485200] dvb-usb: bulk message failed: -110 (4/0)
[  377.485208] cxusb: i2c read failed
[  379.585104] dvb-usb: bulk message failed: -110 (4/0)
[  379.585114] cxusb: i2c read failed
[  381.685171] dvb-usb: bulk message failed: -110 (4/0)
[  381.685179] cxusb: i2c read failed
[  383.785151] dvb-usb: bulk message failed: -110 (4/0)
[  383.785160] cxusb: i2c read failed
[  385.885182] dvb-usb: bulk message failed: -110 (4/0)
[  385.885192] cxusb: i2c read failed
[  387.985082] dvb-usb: bulk message failed: -110 (4/0)
[  387.985091] cxusb: i2c read failed
[  390.085115] dvb-usb: bulk message failed: -110 (4/0)
[  390.085125] cxusb: i2c read failed
[  392.185131] dvb-usb: bulk message failed: -110 (4/0)
[  392.185140] cxusb: i2c read failed
[  394.285286] dvb-usb: bulk message failed: -110 (4/0)
[  394.285295] cxusb: i2c read failed
[  396.385086] dvb-usb: bulk message failed: -110 (4/0)
[  396.385096] cxusb: i2c read failed

```

Does anyone have any ideas?

I am running 2 x DD4 Rev1's

I am also running trunk from the mythbuntu repository.

---

### Post by oobe-feisty on 2009-05-24
I have experienced this i think it depends on what kernel and what revision of the v4l-dvb tree you are using as to how often it occurs i havent had any trouble with this latley using intrepid or juanty's stock kernels before that i used to build my own.

having said all of this a quick and fairly floorless way to get rid of this bulk message spam ( temporarily ) is to power down you computer and leave it off for 1 min the turn it back on if that doesnt work try removing the power cord while it is shutdown.

> **wombo said:**
> 
Does anyone have any ideas?

I am running 2 x DD4 Rev1's

I am also running trunk from the mythbuntu repository.

---

### Post by nkoleff on 2009-05-30
Hello there!
> 
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.517660] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15                                                                                                    )
[    0.517773] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15)                                                                                                     *0, disabled.
[    0.517885] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 9 10 11 12 14 15                                                                                                    )
[    0.517995] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15                                                                                                    )
[    0.518105] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15                                                                                                    )
[    0.518215] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15                                                                                                    )
[    0.518324] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15)                                                                                                     *0, disabled.
[    0.518435] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15                                                                                                    )
[    0.518657] PCI: Using ACPI for IRQ routing
[    0.524096] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.573907] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.665219] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.667335] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.043794] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.662419] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.680385] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.680649] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.680912] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.681193] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.940343] r8169 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.941074] eth0: RTL8169sc/8110sc at 0xf7c54000, 00:1a:4d:6b:90:b7, XID 1800                                                                                                    0000 IRQ 21
[    7.636006] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.295782] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 1                                                                                                    6
[    8.492059] cx88-mpeg driver manager 0000:02:00.2: PCI INT A -> GSI 20 (level                                                                                                    , low) -> IRQ 20
[    8.492134] cx8800 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.092169] cx88_audio 0000:02:00.1: PCI INT A -> GSI 20 (level, low) -> IRQ                                                                                                     20
[   10.276085] cx88-mpeg driver manager 0000:02:02.2: PCI INT A -> GSI 18 (level                                                                                                    , low) -> IRQ 18
[   10.276137] cx8800 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.844203] cx88_audio 0000:02:02.1: PCI INT A -> GSI 18 (level, low) -> IRQ                                                   

This is the result of my dmesg | grep IR

I cant find my remote there. Anybody know why?

I followed blau's guide

---

### Post by onehotcutey on 2009-06-10
You probably need to load the proper module with 'modprobe'.

When I originally setup my system I needed to load the proper module inorder to setup my remote.  Unfortunately my system crashed and I didn't write down the name of the module, so I am digging through the forums trying to find it again.

Once I find it I'll post a link to the post here.

Daniel

---

### Post by onehotcutey on 2009-06-10
Nkoleff,

I am using Dvico FusionHDTV7 with built in IR, the proper driver is ir_kbd_i2c.  You should be able to load it with:

sudo modprobe ir_kbd_i2c

and check to make sure it loaded with:

lsmod | grep ir

or:

dmesg | grep IR.

Daniel

---

### Post by nkoleff on 2009-06-11
> **onehotcutey said:**
> Nkoleff,

I am using Dvico FusionHDTV7 with built in IR, the proper driver is ir_kbd_i2c.  You should be able to load it with:

sudo modprobe ir_kbd_i2c

and check to make sure it loaded with:

lsmod | grep ir

or:

dmesg | grep IR.

Daniel



Thanks for the reply!

When i execute the first command this appears on the screen.

WARNING: All config files need .conf: /etc/modprobe.d/cx88xx.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.



When I do lsmod | grep ir the result is this:
 
ir_kbd_i2c             16400  0
ir_common              56068  2 ir_kbd_i2c,cx88xx



And the result of the dmesg | grep IR is 

> 

dmesg | grep IR.
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.517654] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.517766] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.517878] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.517989] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.518098] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.518208] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.518317] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.518429] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.518651] PCI: Using ACPI for IRQ routing
[    0.524096] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.573907] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.665219] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.667332] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.043602] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.637990] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.656385] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.656649] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.656912] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.657193] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.906091] r8169 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.906824] eth0: RTL8169sc/8110sc at 0xf7c54000, 00:1a:4d:6b:90:b7, XID 18000000 IRQ 21
[   18.448255] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.640487] cx8800 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.715818] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.524217] cx88-mpeg driver manager 0000:02:00.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   20.524272] cx88_audio 0000:02:00.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   20.524840] cx8800 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.276211] cx88-mpeg driver manager 0000:02:02.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.276313] cx88_audio 0000:02:02.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18



but still nothing when I

---

### Post by bhepple on 2009-06-13
Hi,

Has anyone been able to get this board running with 2.6.30-8-generic Jaunty???



I'm another sufferer of the dreaded bulk message:

[  375.385180] dvb-usb: bulk message failed: -110 (4/0)

I'm also at my wits end trying to fathom a solution. Can some kind person offer some directions?

As background: I had it working fine with Intrepid - only problem was that MythTV would often hang up when playing back a file - so I decided to upgrade to Jaunty. Cutting out the trials and tribulations of the upgrade, I am now at kernel 2.6.30-8-generic on a AMD Athlon XP 2000+. I have /lib/firmware/xc3028-v27.fw

I tried powering off, removing the power cable and taking the board out of the machine before re-trying - it made no difference.

lsusb gives:
Bus 002 Device 002: ID 0fe9:db78 DVICO FusionHDTV DVB-T Dual Digital 4 (ZL10353+xc2028/xc3028) (initialized)
Bus 002 Device 003: ID 0fe9:db78 DVICO FusionHDTV DVB-T Dual Digital 4 (ZL10353+xc2028/xc3028) (initialized)

My understanding is that the v4l-dvb drivers are now in the kernel so I haven't tried the older mercurial-based download and install method. If that's wrong, please let me know and I'll try it.

From /var/log/messages, it seems to be loading the firmware but then running into problems with writing to the zl10353: could this be hardware problems? But it was working only the other day, I only changed the OS. I suspect the drivers:

Jun 13 15:01:45 nina kernel: [   26.488234] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
Jun 13 15:01:45 nina kernel: [   26.488611] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun 13 15:01:45 nina kernel: [   26.519611] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
Jun 13 15:01:45 nina kernel: [   26.937373] cxusb: No IR receiver detected on this device.
Jun 13 15:01:45 nina kernel: [   26.937383] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
Jun 13 15:01:45 nina kernel: [   27.057256] xc2028 2-0061: creating new instance
Jun 13 15:01:45 nina kernel: [   27.057262] xc2028 2-0061: type set to XCeive xc2028/xc3028 tuner
Jun 13 15:01:45 nina kernel: [   27.057887] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
Jun 13 15:01:45 nina kernel: [   27.057913] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
Jun 13 15:01:45 nina kernel: [   27.058049] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun 13 15:01:45 nina kernel: [   27.089208] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
Jun 13 15:01:45 nina kernel: [   27.136536] cxusb: No IR receiver detected on this device.
Jun 13 15:01:45 nina kernel: [   27.136545] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...
Jun 13 15:01:45 nina kernel: [   27.136737] xc2028 3-0061: creating new instance
Jun 13 15:01:45 nina kernel: [   27.136741] xc2028 3-0061: type set to XCeive xc2028/xc3028 tuner
Jun 13 15:01:45 nina kernel: [   27.137404] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
.
.
.
Jun 13 15:02:25 nina kernel: [  118.801333] i2c-adapter i2c-2: firmware: requesting xc3028-v27.fw
Jun 13 15:02:25 nina kernel: [  118.922171] xc2028 2-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Jun 13 15:02:25 nina kernel: [  118.932344] xc2028 2-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Jun 13 15:02:27 nina kernel: [  120.659451] xc2028 2-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
Jun 13 15:02:27 nina kernel: [  120.685823] xc2028 2-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
Jun 13 15:02:27 nina kernel: [  120.989117] i2c-adapter i2c-3: firmware: requesting xc3028-v27.fw
Jun 13 15:02:27 nina kernel: [  120.993890] xc2028 3-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
Jun 13 15:02:27 nina kernel: [  121.004235] xc2028 3-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
Jun 13 15:02:29 nina kernel: [  122.735596] xc2028 3-0061: Loading firmware for type=D2633 DTV7 (90), id 0000000000000000.
Jun 13 15:02:29 nina kernel: [  122.762090] xc2028 3-0061: Loading SCODE for type=DTV6 QAM DTV7 DTV78 DTV8 ZARLINK456 SCODE HAS_IF_4760 (620003e0), id 0000000000000000.
Jun 13 15:02:30 nina kernel: [  123.853864] usbcore: registered new interface driver hiddev
Jun 13 15:02:30 nina kernel: [  123.853884] usbcore: registered new interface driver usbhid
Jun 13 15:02:30 nina kernel: [  123.853887] usbhid: v2.6:USB HID core driver
Jun 13 15:02:30 nina kernel: [  123.868170] zl10353: write to reg 62 failed (err = -121)!
Jun 13 15:02:32 nina kernel: [  125.868184] zl10353: write to reg 50 failed (err = -121)!
Jun 13 15:03:03 nina kernel: [  157.456355] IRQ 16/nvidia: IRQF_DISABLED is not guaranteed on shared IRQs
Jun 13 15:03:03 nina kernel: [  157.522631] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
Jun 13 15:03:03 nina kernel: [  157.522647] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
Jun 13 15:03:03 nina kernel: [  157.522712] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode
Jun 13 15:03:20 nina kernel: [  174.112106] zl10353_read_register: readreg error (reg=80, ret==-121)
Jun 13 15:03:22 nina kernel: [  176.112111] zl10353: write to reg 50 failed (err = -121)!
Jun 13 15:03:24 nina kernel: [  178.116116] zl10353: write to reg 55 failed (err = -121)!
Jun 13 15:03:26 nina kernel: [  180.116129] zl10353: write to reg ea failed (err = -121)!

---

### Post by bhepple on 2009-06-13
Yep - looks like there's nothing wrong with the hardware.

I found an old Fedora-10 DVD and a spare disc - installed it and it worked fine with the DViCO.
That's a 2.6.27 kernel. I used the exact same firmware too. MythBuntu-9.04 (2.6.28 kernel) also shows this failure.

Just to re-confirm the problem, I put the 2.6.30 Ubuntu Jaunty disc back in and got the same bulk error messages.

So a cautionary message to anyone using the DViCO's - don't upgrade your kernel past 2.6.27 until they fix the driver!!!

I'll try and open a bugzilla and cross-post the link here.


Bob

---

### Post by Asc3nti0n on 2009-06-20
I don know if this is a solution for some, but a case study nonetheless.  I have had a few issues, but googling and then chasing the very latest posts on the DViCO FusionHDTV DVB-T Dual Digital 4, have lead to all the answers required.

For a while there is was hard to scroll past all the doomsayers from July-November last year (2008) when there wasn´t looking like anyone was working on Linux drivers for the Revision 2 card, so-so-many posts about no drivers... eventually found the posts and threads that lead me to buy it in the first place.

Problems faced:
- the Tuner card was DOS´ing my USB control bus with the dvb-usb bulk message failed -110
- I also only had one TV tuner (DVB1) working, DVB0 could not be opened by mythtv back-end setup and the dmesg reported that the front-end could not be added.

I followed the walk-through (addy below) to download the latest v4l-dvb source and compile it locally. and I also completed the firmware file commands too listed there, then repeated the v4l-dvb ¨make install¨ line again... then I found the most important part... SHUT DOWN.  pull out power cord to make sure... then cold-start the computer again.  Low and behold I then didn´t the dmesg logfile thousands of lines long anymore, only 44seconds of computer load.

Here´s a link that details the walk-through nice and clean, for more information Google for the official site.
   [https://help.ubuntu.com/community/DViCO_Dual_Digital_4](https://help.ubuntu.com/community/DViCO_Dual_Digital_4) 

```
My Specs
Ubuntu JJ 9.04 - Mythbuntu x64 Live/Installation disk.
Linux version 2.6.28-13-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
Core2Duo E8200, Gigabyte GA-73PVM-S2H MB with 2GB of DDR2 (OCZ ReaperX)
Separate / drive and pointing MythTV data and recordings to second HDD.  nfs mounted dirs to Ubuntu media server.
Antec Fusion (with Soundgraph iMon LCD display) <-- next project to get working. 
```

```
[    8.825329] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[    8.825578] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.856638] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2))
[    9.020922] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[    9.174342] DiB0070: successfully identified
[    9.174930] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0a.0/0000:01:06.2/usb2/2-1/input/input6
[    9.200056] dvb-usb: schedule remote query interval to 100 msecs.
[    9.200059] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
[    9.200073] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[    9.200262] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.231370] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2))
[    9.387158] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[    9.538205] DiB0070: successfully identified
[    9.538775] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0a.0/0000:01:06.2/usb2/2-2/input/input7
[    9.560050] dvb-usb: schedule remote query interval to 100 msecs.
[    9.560053] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
[    9.560075] usbcore: registered new interface driver dvb_usb_cxusb

```

---

### Post by bhepple on 2009-06-20
Success !!! Here's what worked for me ...

I tried to compile v4l-dvb according to the link provided but ran into compiler errors - it couldn't find dma.h etc

To get it to compile I had to change one line in v4l/.config to this:

CONFIG_DVB_FIREDTV=n

... then make && make install worked fine.

On loading the drivers with this:

modprobe dvb-core
modprobe dvb-usb
modprobe dvb-pll
modprobe tuner-xc2028
modprobe zl10353
modprobe dvb-usb-cxusb

... I just get huge spamming of the BULK message again. 

So I tried to halt and pull the power cord for a coupla minutes - and all seems sweetness and light. At least there's no spamming at the console and /dev/dvb/adapter{01} exist. So it looks like the drivers shipped with 2.6.30 are defunct and you need to download the head-of-tree from v4l-dvb.

BTW - the firmware mentioned in the link [https://help.ubuntu.com/community/DViCO_Dual_Digital_4](https://help.ubuntu.com/community/DViCO_Dual_Digital_4) is wrong - only xc3028-v27.fw is read in by the drivers.

Hope this helps others out there ...


Cheers


Bob

---

### Post by lukejjon on 2009-06-27
Hi,
I have a rev2 tuner card, and I think I have almost got it running correctly. When I run irw i get the correct responses on the screen, however, when I go back into myth and try to nagivate around the menus I get no response from the remote - at all. Maybe I have screwed up the lircrc file...
Thanks in advance for any suggestions.

---

### Post by tvars on 2009-06-28
I upgrade to 9.04 and got everything working again. However, the responsiveness of the remote seems to have degraded drastically. I press a key and it takes around 2 seconds for the the action to occur. I tested it with irw and 'cat /dev/input/event4', the output confirms the same lag that I experience through MythTV so I'm inclined to think that this may be a driver or hardware issue. 

My syslog is full of messages like these, but I think it's unrelated.

```
Jun 28 18:04:29 mythbox kernel: [ 1769.088628] dvb-usb: bulk message failed: -110 (1/0)
```

Any ideas?

---

### Post by DisasterEC on 2009-07-01
Hi,

I have a rev 2 Dual digital 4, the the TV tuner is working fine thanks to all the help in this thread.
I am having major problem trying to get the remote work, I have mainly followed this post to get the remote working [http://ubuntuforums.org/showpost.php?p=7140656&postcount=145](http://ubuntuforums.org/showpost.php?p=7140656&postcount=145)


Doing a sudo cat /dev/input/event6 I get a response from the remote
But I don't get any response when Mythtv is running,

Any help on steps I can go through to trouble shoot and get the remote working will be appreciated, as I been reading through this thread for over a week and not getting anywhere.

I have Ubuntu 9.04 installed.

Thanks

---

### Post by spleblem on 2009-07-01
i was in the exact same position as you for about a month
and have only just got my remote to work
i finally got it to work using the thread you said you followed
maybe try again following it exactly from start to finish and post or just read all the outputs from the terminal to make sure everything that needs to happen does.

---

### Post by DisasterEC on 2009-07-02
No luck,

The only output i get is when triying to create a link, I think as I have run through the process to many times.

> Too many levels of symbolic linksAlso did you remove everything from /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi

and only input

>      <match key="info.product" contains_ncase="IR-receiver inside an USB DVB re$
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="IR-receiver inside an USB DVB re$
        <merge key="info.ignore" type="bool">true</merge>
     </match>


---

### Post by bejam on 2009-07-17
I have rev 1 of the DVICO Dual Digital 4, and have followed the instructions above to try to get rid of the bulk 110 error message. After fiddling for quite a while I found that for kernel 2.6.28-11 (Ubuntu 9.04 out of the box) everything works fine. When upgrading to current ubuntu 9.04 kernel (2.6.28-13) I get the error message. Have tried downloading and installing 2.6.30 and following the v4l-dvb compile route. Compiling the latest v4l-dvb (and powering off as suggested) does not work. I also tried the compiled v4l-dcb against 2.6.28-13 with no success. I still get the error and find the first tuner (adapter0) cannot be read. Any attempt at rescanning channels in mythtv-setup doesn't work. For now I have reverted to 2.6.28-11.

---

### Post by gfrost on 2009-07-18
I am trying to add support for the dvico dual digital 4 rev2 remote for another distro and I would like to be able to have a udev rule that creates the /dev/input/irremote symlink without the need to manually tinker to get the serial number of the first card as suggested here [http://ubuntuforums.org/showpost.php?p=6794981&postcount=92](http://ubuntuforums.org/showpost.php?p=6794981&postcount=92) (note that the posters assumption about the serial being the same for all rev2 units does not hold).

To summarise: Two IR devices appear in dmesg:
> [gfrost@devnew ~]$ dmesg | grep IR-rec
input: IR-receiver inside an USB DVB receiver as /class/input/input6
input: IR-receiver inside an USB DVB receiver as /class/input/input7
These are almost identical from a udev perspective, so it is not easy to write a rule that only applies to the first of them:
> [gfrost@devnew ~]$ udevadm info --query=all --name=/dev/input/event6 --attribute-walk > first
[gfrost@devnew ~]$ udevadm info --query=all --name=/dev/input/event7 --attribute-walk > second
[gfrost@devnew ~]$ diff first second
8,9c8,9
<   looking at device '/class/input/input6/event6':
<     KERNEL=="event6"
---
>   looking at device '/class/input/input7/event7':
>     KERNEL=="event7"
13,14c13,14
<   looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:05:01.2/usb3/3-1':
<     KERNELS=="3-1"
---
>   looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:05:01.2/usb3/3-2':
>     KERNELS=="3-2"
22c22
<     ATTRS{urbnum}=="200077"
---
>     ATTRS{urbnum}=="110805"
25c25
<     ATTRS{bcdDevice}=="be10"
---
>     ATTRS{bcdDevice}=="3e10"
33c33
<     ATTRS{devnum}=="2"
---
>     ATTRS{devnum}=="3"
40c40
<     ATTRS{serial}=="0000be10"
---
>     ATTRS{serial}=="00003e10"
I dont think that any of those differences can be used as part of a distro generic rule because they will all either vary from card to card or vary from system to system depending on which slot the cards get installed in and what other devices are present.

If you make a udev rule that matches both to create the irremote symlink, it is always the second device that it points to (exactly what we dont want).

Does anyone know enough about udev to make a rule that only applies to the first device matching the rule.

---

### Post by rajagiri5 on 2009-07-18
thank you for your useful information

[IMG]http://www.rajagiriworld.com/happy.gif[/IMG]

---

### Post by gfrost on 2009-07-18
> **gfrost said:**
> Does anyone know enough about udev to make a rule that only applies to the first device matching the rule.
Eventually, I worked this out. The following rule does it:```
# This rule is for the Dvico Dual Digital 4 Rev 2. It has 2 IR modules
# identified, only the first of which is connected to the receiver.
# The KERNELS=="*-1" part of this rule makes sure that the first
# device is the one that gets the symlink.
KERNEL=="event*", \
    KERNELS=="*-1", \
    ATTRS{manufacturer}=="Dvico", \
    ATTRS{idVendor}=="0fe9", \
    ATTRS{idProduct}=="db98", \
    SYMLINK="input/irremote"
```

---

### Post by Kevin McIsaac on 2009-07-26
I've have a Rev 2 card with a fresh install of Ubuntu 9.04 (Jaunty) and MythTV .21. The install was very simple, with the exception of the remote. 

I installed Ubuntu and MythTV,  powered down for a min (to reset the card) then rebooted. The video just works and I don't get the "bulk messages". 

The problem I'm having is with the remote. It is working  but some times the system does not respond to a button press.

I got the remote working as following by using [gfrost's udev rule , ]("http://ubuntuforums.org/showpost.php?p=7638839&postcount=173")to dynamically map the ir device to /dev/input/irremote, and I  [oobe-feisty]("http://ubuntuforums.org/member.php?u=397502")'s [Remote installation notes ]("http://ubuntuforums.org/showpost.php?p=3791647&postcount=1")to set up lirc[B].

[/B]When I run irw and ircat mythtv, I can see the remote is set up properly but if I keep pressing keys, some times a keystroke is missed. 

This seems to  happens about once in every 5 or 10 keystrokes and not always with the same key. 

I can't decided if this is the remote, the card or linux.

---

### Post by Kevin McIsaac on 2009-07-26
I thought I'd try to isolate this further so I stopped lircd, and read the IR device directly using,
```
sudo hexdump /dev/input/irremote
```This also has an occasional missing keystroke. To me this indicate the issue is either the remote, the card or the drivers/kernel.

BTW, I'm running a well spec'ed machine
AMD 5050e, dual Core
2GB memory
Ubuntu 9.04 (Jaunty)
Kernel 2.6.28-13-generic

---

### Post by Kevin McIsaac on 2009-08-16
The problem looks to be related to Xorg. 

If stop xorg, I get 100% of my keystrokes sent to the device. With xorg running about 30% are lost. It does to seem to matter what I'm running under X, i.e., I get this even if I'm not logged in, and it does not matter how the NVIDIA is set up, i.e., use the proprietor drivers, use nv, set "UseEvents" "True" etc.

BTW, by setting "UseEvents" "True" and using VDPAU, I eliminated payback issues and xorg runs at about 10% and mythfrontend at about 8%. However, still have the issue with losing keystrokes from the remote.

---

### Post by Scooter74 on 2009-09-19
**EDIT: SOLVED.** *It looks like the problem was with the lircmd.conf or lircrc files. I re-checked them and changed them as required. Now at least irw works. Getting all the key bindings correct is another matter!*

I'm still having problems with this remote despite all the posts out there. The bottom line is that the system will respond to sudo cat /dev/input/event7 with the gobbledy-gook but nothing from irw and both of the tuners work fine in MythTV.

I'm running 9.04 now but I had the same problem with 8.10. I've followed all the posts from oobe-feisty and blau2009 but no luck so far. These are my outputs:

dmeg|grep IR
```
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.398923] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.399007] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.399089] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.399171] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.399253] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.399336] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.399417] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.399499] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.399658] PCI: Using ACPI for IRQ routing
[    0.404067] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.452909] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.452919] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.300673] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.301992] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.025941] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.682981] pata_acpi 0000:03:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.683085] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.700186] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.720200] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.720388] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.720572] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.720749] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.720938] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.721121] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.225377] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.226012] eth0: RTL8168c/8111c at 0xf7c5a000, 00:1f:d0:a3:0d:af, XID 3c4000c0 IRQ 2301
[    4.282857] ohci1394 0000:03:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.332570] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e6004000-e60047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.376173] pata_it8213 0000:03:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.743274] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.252770] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.284032] cx88-mpeg driver manager 0000:03:01.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.284377] cx8800 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.683124] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/input/input7

```

lsusb
```
Bus 002 Device 003: ID 0bc2:2100 Seagate RSS LLC 
Bus 002 Device 002: ID 0bda:0103 Realtek Semiconductor Corp. USB 2.0 Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0fe9:db51 DVICO 
Bus 001 Device 004: ID 046d:09a1 Logitech, Inc. 
Bus 001 Device 003: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c513 Logitech, Inc. MX3000 Cordless Desktop Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

dmesg|grep dvb
```
[   14.950973] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in cold state, will try to load a firmware
[   14.950977] usb 1-1: firmware: requesting dvb-usb-bluebird-01.fw
[   15.031585] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'
[   15.098857] usbcore: registered new interface driver dvb_usb_cxusb
[   15.131359] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[   16.311029] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   16.311031] cx88/2: registering cx8802 driver, type: dvb access: shared
[   16.652649] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in cold state, will try to load a firmware
[   16.652653] usb 1-1: firmware: requesting dvb-usb-bluebird-01.fw
[   16.654766] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'
[   16.750555] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[   18.669600] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in warm state.
[   18.669717] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.687215] dvb-usb: schedule remote query interval to 150 msecs.
[   18.687220] dvb-usb: DViCO FusionHDTV DVB-T Dual USB successfully initialized and connected.

```

ps aux | grep lircd
```
root      4121  0.0  0.0   3116   636 ?        Ss   18:27   0:00 /usr/sbin/lircd --driver=dvico --device=/dev/lirc0
macready  5210  0.0  0.0   4404   816 pts/0    S+   18:38   0:00 grep lircd

```

The irrecord --driver=dev/input --device=/dev/input/irremote seemed to work fine.

I've edited the /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi and /etc/lirc/hardware.conf files as per post #145.

I've checked the hardware.conf, lircd.conf, lircmd.conf and lircrc files and they all seem fine.

For some reason the mythbuntu control centre didn't have any remote device set but I've now turned it on.

I've turned off the computer without power for a couple of minutes at a time.

I've run out of ideas. Please help.

Thanks, Scooter.

---

### Post by agent_kith on 2009-09-29
> **bejam said:**
> I have rev 1 of the DVICO Dual Digital 4, and have followed the instructions above to try to get rid of the bulk 110 error message.
I'm having this issue also and can't figure out a solution, anybody have any success yet?

---

### Post by madverb on 2009-10-13
I've modified the files for the Rev. 2 remote/card.

I have also created some scripts for using the TV and PC Power Buttons just need to place them in /usr/local/bin and make them executable.

I did this because I found that there were some minor annoyances with some files and some of the buttons were setup incorrectly in the lircrc file.

---

### Post by xipmix on 2009-10-15
> **bhepple said:**
> Success !!! Here's what worked for me ...

modprobe dvb-usb-cxusb

Bob
Bob, I've seen elsewhere people advocating
```

  sudo rmmod dvb_usb_cxusb

```
to stop the spamming (eg [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229879](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229879))

Have you tried this? I had a go, running 2.6.31-13-generic. 
It does deactivate the card, but it does at least stop the spam.
However if I then
```

  sudo modprobe -v dvb_usb_cxusb

```
the spam returns, and worse - at a faster rate.

---

### Post by nicoloks on 2010-01-05
I'm also having issues with the Rev 2 remote where around 1/3 of all keystrokes are lost. Haven't tried irw with Xorg stopped as yet, but I will do so tonight. Anyone else had any luck with getting all keystrokes recognised for this remote?

---

### Post by Kevin McIsaac on 2010-01-05
> **nicoloks said:**
> I'm also having issues with the Rev 2 remote where around 1/3 of all keystrokes are lost. Haven't tried irw with Xorg stopped as yet, but I will do so tonight. Anyone else had any luck with getting all keystrokes recognised for this remote?

Still a big problem for me. 

Based on an educated guess I think the problem is with the driver. On that basis I've opend a bug on launchpad here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498427](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498427)

My guess is that when the system is under some load, i.e., Xorg is running, the driver misses some interupts from the device or some such issue. 

You might also be interesed in this bug related to the "bulk message"
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459523](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459523)

---

### Post by TheMiz on 2010-01-22
I've had my tuner working for a while now.  I just tried to get my remote working tonight.  I'm not really sure where to place the ir-kbd-i2c module.  I was able to see my IR input when I ran dmesg, but only once... then it disappeared and I'm not sure if I'm getting the name right.  The first time I did see the IR input I could not create the symlink file... the 60-symlinks.rules was empty, and I created the new line, but I guess I must not be understanding what I need to do to create the irremote input file in dev/input/  I am totally new at linux.  I'm kind of surprised I have everything working on my Myth system (everything but the remote that is).  But I'd appreciate any help.  I am running Mythbuntu 9.10.

---

### Post by nicoloks on 2010-02-11
Thought I should post back as I have solved the issue I was having with around a 1/3 of all keystrokes being lost. Turned out to be some kind of incompatibility with the old Intel D915GAG motherboard I was using. As soon as I put that same card in my other system using a Nvidia 430 based Asrock motherboard it worked without a hitch.

---

### Post by Kevin McIsaac on 2010-02-20
nicoloks thanks for your post.

I did some more digging using USBmon and it seems that the problem with the missing keystrokes is that the USB events are missing too! That is sometimes when I press a remote key (about 1/3 of the time) there isn't a USB event on the USB bus as reported by USBmon.

Surprisingly when I stop gdm all keystrokes are recorded! Seems like the hardware works and that X is somehow part of the issue.  

I'm running  DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) with a ASUSTeK M3N78-VM motherboard.  I've recently upgraded the BIOS on the motherboard and I don't think the firmware on the DViCO Dual Digital 4 rev 2 can be changed.

---

### Post by gkasinath on 2010-05-08
Howdy folks, 

Has anyone had success with the DVICO Fusion DVB-T Hybrid card lately? 
I'd given up getting it running from Fiesty days.. and now, with the new Lucid (fresh install) thought I'd give it a shot.. but no cigar. 

Still stuck at 

dmesg output snippet - 

```
[   24.638997] nvidia: module license 'NVIDIA' taints kernel.
[   24.639003] Disabling lock debugging due to kernel taint
[   25.548957] Linux video capture interface: v2.00
[   25.581772] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   25.581815]   alloc irq_desc for 19 on node -1
[   25.581818]   alloc kstat_irqs on node -1
[   25.581827] cx8800 0000:03:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   25.582247] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   25.582249] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   25.582251] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   25.582252] cx88[0]: the TV card.  Best regards,
[   25.582253] cx88[0]:         -- tux
[   25.583292] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   25.583569] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   25.583755] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   25.583964] cx88[0]:    card=2 -> GDI Black Gold
[   25.584149] cx88[0]:    card=3 -> PixelView
[   25.584324] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   25.584533] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   25.584745] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   25.584946] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   25.585144] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   25.585342] cx88[0]:    card=9 -> Leadtek PVR 2000

```

lspci output: 
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Dell Device 01d2
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: ed000000-efefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01d2
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: ecf00000-ecffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 01d2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 21
	Region 4: I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 01d2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 22
	Region 4: I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 01d2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at ff40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
	Subsystem: Dell Device 01d2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 23
	Region 4: I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 01d2
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: eb000000-ecefffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01d2
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Device 01d2
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 20
	Region 0: I/O ports at fe00 [size=8]
	Region 1: I/O ports at fe10 [size=4]
	Region 2: I/O ports at fe20 [size=8]
	Region 3: I/O ports at fe30 [size=4]
	Region 4: I/O ports at fea0 [size=16]
	Region 5: Memory at c0200000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	Subsystem: Dell Device 01d2
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 9
	Region 4: I/O ports at ece0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
	Subsystem: Giga-byte Technology Device 3126
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at efe00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

03:03.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (5000ns min, 13750ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at eb000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

03:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
	Subsystem: Dell Device 01ab
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min, 14000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at eceff000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at dcc0 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

```

I've tried rebuilding from v4l, no luck.. followed the *simple* instructions in the first thread to the letter, no luck. 

Oh and BTW, dvb-utils is no longer in repo. It is called dvb-apps now (or for sometime!)

Any help would be appreciated.

Thanks

Cheers
G
(Oh and I m in Perth/Australia. Any local folks here that can help me solve this puzzle can expect a Hann 6 pack).

---

### Post by tqft on 2010-05-08
Do you boot the system with any command line parameters - you can check 
more /proc/cmdline

In particular I noticed this in the output above " Your board has no valid PCI Subsystem ID and thus can't be autodetected. "  This may be spurious/irrelevant.

I know I had some problems and ending up for a while having to add irqpoll=on to the boot cmd (you can edit the grub command at boot time for a one of).  highlight the entry and hit 'e', move to the end of the line and type irqpoll=on to see if it makes a difference.

---

### Post by Ozdemon on 2010-06-05
I have got the dvico remote working well with the Dual Digital 4 on Ubuntu 10.04 on my daughter's computer when using my account (which has root privileges).  However I set it up so she could use it.  When logged on to her account, the remote does not work.

I am guessing that it is a symlink problem, but I do not know the right method.  I am wary of tinkering blindly now that it works on my account. 

Can someone post the code to add a user account to the remote?

Thanks.

---

### Post by oobe-feisty on 2010-06-19
> **Ozdemon said:**
> I have got the dvico remote working well with the Dual Digital 4 on Ubuntu 10.04 on my daughter's computer when using my account (which has root privileges).  However I set it up so she could use it.  When logged on to her account, the remote does not work.

I am guessing that it is a symlink problem, but I do not know the right method.  I am wary of tinkering blindly now that it works on my account. 

Can someone post the code to add a user account to the remote?

Thanks.

its most likely just a matter of adding configs for lirc into her home directory i.e ~/.lirc or ~/.lircrc or ~/.mythtv/lircrc is missing you can copy them from your directory or just symlink them 

also to proove this theory you should beable to type irw from her account and get a response from the remote.

---

### Post by tvars on 2010-06-20
I've had my remote control working for ages. I just upgraded to 10.04 and now my remote control won't work. 

The symptoms are the same as I used to have when hal was interfering with lirc. If I shut down lirc and I press remote control buttons i get output from "cat /dev/input/event3" but it looks like the input is being interpreted as keyboard inputs. i.e. only half the buttons work and when I press buttons while a text editor is open on the screen I can see the key presses being applied.

When I start lirc the key presses stop being received at all.

I have the following in the file "/usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi"

```

     <match key="input.product" string="IR-receiver inside an USB DVB receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>

```

lshal shows my IR devices as being ignored. dmesg shows my device is recognised. irw shows nothing.

What's going on? Is there anything other than hal that could be getting in the way? I'm out of ideas.

---

### Post by Ozdemon on 2010-06-28
> **oobe-feisty said:**
> its most likely just a matter of adding configs for lirc into her home directory i.e ~/.lirc or ~/.lircrc or ~/.mythtv/lircrc is missing you can copy them from your directory or just symlink them 

also to proove this theory you should beable to type irw from her account and get a response from the remote.

All working well now, thanks very much oobe-feisty.  ):P

---

### Post by bhepple on 2010-07-27
Just a quick update - I tried the rev.1 card with kernel-2.6.32.16-141.fc12 (OK, it's not ubuntu, but this might still be a useful datapoint for someone).

It seems that the problems (DOS'ing the console with 'bulk message' errors and no tuning) that I encountered with 2.6.28 to .30 are a thing of the past. Kudos to the linux-media guys!!

I yet haven't tried the remote control - I use a logitech mini-keyboard using bluetooth which gives much greater functionality.

It would be interesting to know exactly what kernel rev. this got fixed but I don't have time to bisect it. Maybe someone can offer a lower upper bound ...

Now it's all clear for me to upgrade to the latest and greatest OS!!

---

### Post by nickm57 on 2010-09-08
Hi
reading through and i'm now a bit confused.
I'm running a Mythbuntu HTPC.
Set up a
Mythbuntu 10.04 64 bit
2.6.32-24 generic
Athlon x 2

Dvico Fusion dual 4. rev .1 Fusion MCE remote

tuning and have channels up  I'm pleased with the results so far.
 I have some remote function but, but the remote keys map do not seem to match and importantly have no "esc" function from the remote.
How do I go about getting the right key map for this remote or changing the lirc map?

Thanks

---

### Post by bhepple on 2010-09-08
Here's the .Xmodmap file that I use - my main motivation is to use a logitech mini keyboard which just shows up as a USB k/b, but I've been able to get _something_ out of the i/r control using this.

If you want to get the best out of the i/r remote control, you're probably better off following the LIRC instructions posted elsewhere in this chain - I've never bothered with it.

Hope this helps ...


Bob


! Use the flag key for _something_ ...
!
add mod4 = Super_L
!
! Hitting caps lock is so irritating: change it to Shift:
!
remove Lock = Caps_Lock
add Shift = Caps_Lock
!
! A fairly generic multi-media keyboard:
!
keycode 136 = Escape
keycode 144 = Left
!keycode 144 = XF86AudioPrev
!keycode 146 = XF86RockerUp
keycode 152 = XF86Back
keycode 153 = Right
!keycode 153 = XF86AudioNext
keycode 158 = XF86Stop
keycode 160 = XF86AudioMute
keycode 162 = XF86AudioPlay
keycode 164 = XF86Stop
!keycode 174 = Escape
keycode 174 = XF86AudioStop
keycode 176 = XF86AudioRaiseVolume
keycode 177 = XF86AudioRecord
keycode 178 = XF86WWW
keycode 180 = XF86Forward
keycode 187 = XF86ZoomIn
keycode 191 = XF86Clear
keycode 222 = XF86PowerOff
keycode 223 = XF86Sleep
keycode 227 = XF86WakeUp
keycode 229 = XF86Search
keycode 230 = XF86Go
keycode 232 = XF86Stop
keycode 234 = XF86Stop
keycode 236 = XF86Mail

---

### Post by philbo on 2010-10-24
Have you got the Dvico Hybrid card to work?
I am running Mythbuntu 10.04 but can't get the IR to work - if you have please let me know how you got it to work?

Thx

---

### Post by the1magoo on 2012-01-08
> **maniaq said:**
> ok the files are attached - they go in your ~/.xbmc/userdata directory

so some of the button assigments are quite arbitrary, due to what buttons are available on my (rev2) remote and what actions are available in the software...

the <remote device> attribute in Lircmap.xml (in my case "FusionREMOTE") is the name of your remote, as per what is in your /etc/lirc/lircd.conf configuration and the names of the various buttons (eg "ratio" in my case) also comes from that same configuration - you can have that file open to inspect, or what I did was just have irw running and press some buttons on the remote...

mess with the xml attributes all you like to suit your remote/preferences but the xml tags MUST be exactly what they are for the software to map properly - so for eg. in Lircmap.xml:

<display>ratio</display>

your lircd.conf might call the "ratio" button something else so you can change that to suit, but the "display" part is specific to xbmc - of course you can rearrange what buttons to map what...

same goes for Keymap.xml - the Captilised actions inside the tags can be rearranged to suit, but be careful


more info here:

[http://xbmc.org/wiki/?title=Keymap.xml#Available_actions](http://xbmc.org/wiki/?title=Keymap.xml#Available_actions)

After much searching and hair-tearing, your notes got me up and running!

Many thanks!

---

### Post by moaxey on 2012-05-06
Configuring my remote no longer works for me in ubuntu precise. ;-(

I have the revision 2 remote (lirc2 download)

Perhaps I am being a dunce... There is a vaguely similar bug here
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/934023](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/934023)

There seem to be a few differences going on, for instance:
symlinks - now I put irremote symplink in /dev/iinput/by-id/irremote as when reconfiguring lirc you can no longer select it in the original location

if I 
# cat /dev/input/by-id/irremote

I get lots of pleasing binary characters for each button press on the remote

but if I do
$ irw

only a few buttons give responses

The default layout of lirc config files has changed to be ~/.lirc/appname
with one file for each app, and I've rearranged the config in that arrangement -- but there must be more to it!

---

### Post by moaxey on 2012-05-07
fixed by forgetting about symplinking process described in post 1, and copying files attached to post 178 into /etc

---

