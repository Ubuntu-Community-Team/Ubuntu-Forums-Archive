---
title: "Hi guys need help with VST on Rosegarden"
date: 2011-10-10
forum: Ubuntu Studio
---

### Post by shantiq on 2011-10-10
Been using Rosegarden for the last 2 years to compose midi which i then convert to wave with Timidity on Natty 64-bit



prior to that i used Cubase and loved those [**ethnic VST**]("http://smatni.tripod.com/safwanmatnivstplugins/") by Safwan matni especially the drums one called takim.dll


I hear that it is possible to add them to rosegarden but do not know how to

I am seeking clear step by step information from someone who has done this .  I want it for Rosegarden SPECIFICALLY so I can add those to the already immense panoply of sounds


I have read around a bit but do not really fully understand how to do this


Found [**this**]("http://osdir.com/ml/audio.rosegarden.user/2004-09/msg00099.html") but it is a bit over my head and is out of date

i have installed this dssi-vst [**here**]("http://packages.ubuntu.com/maverick/dssi-vst")


How do i proceed ?



PS   This here is the [**kind of music**]("http://shan.bandcamp.com/track/the-late-cubase-years-shan-songs-part-1-flac") that i make


PS2   short [**video guide**]("http://www.youtube.com/watch?v=0-X6_q1iRzc") to midi composition on Rosegarden

---

### Post by beefheartvliet on 2011-10-10
This in not much of a help, But if you get "festige" from the software centre, then you should be able to load your VSTi into festige, then in turn use it in Rosegarden. you might want to get something called a2jmidid as well. It's not got a gui but, it can be run from the terminal by simply typing a2midid. It creates a set of virtual in and outs which can be useful sometimes. Look I know it's a bit of a crap explanation, but I'm sure if you do a little bit of playing around with festige you will get to where you want to be.

PS, Been listening to your album for the last twenty od mins, here's some stuff me and a few mates get up to as a trippy side project to other stuff we do ;-)

[http://soundcloud.com/trips-and-blips/tracks?page=1](http://soundcloud.com/trips-and-blips/tracks?page=1)

---

### Post by sgx on 2011-10-10
Hi, check in /etc/profile.d folder, and see if there is a file
vst.sh or similar, this establishes where system apps look for vsts, so you should copy your vsts there. Rosegarden should find them,
perhaps a menu option exists to choose a vst folder exists?


# Set VST_PATH for Bash shell
if [ -n "\$VST_PATH" ]; then
   # Set VST_PATH for Bash shell
   export "VST_PATH=/usr/lib/vst"
fi

reality check warning:popcorn:

Reaper DAW using wine and wineasio is the way to proceed. The linux
native options are improving, but are so far behind the proven working solution, (and it's noteworthy features), that it's going to be years before there is parity.

If you must make the native linux attempt, festige from the falk PPA, along with the latest version of wine, will work for some vsts, but if preset access is not part of the vst gui, you will be hogtied. This festige may help with rosegarden, but I don't use rosegarden,
so hopefully someone else can shed some light.
Cheers
starting rosegarden from a terminal may show clues when vsts are loaded,
sometimes a microsoft .dll or other file needs a copy placed in 
the proper folder in .wine

---

### Post by shantiq on 2011-10-11
not good guys installed festige PPA which removed my wine 1.2 and installed wine 1.3


now nothing works on wine looks like falk PPA broke something or changed some settings

i get ```
wine: virtual memory exhausted

```   and nothing works  !!

so not a good start...


How do i get out of this/?


==================================================

Ok and let us not think that i am not grateful for the pointers but tthis wretched PPA takes over and dictates what happens with wine it seems not what i expected

I had to remove it remove wine and reload all my EAC Foobar etc with all settings ; 5 hours or more of toil

SO personally i would say stay clear of this PPA
Maybe it is just on my setup but it created havoc

So has anyone got a less fraught route?
I really want these VSTs on my system

---

### Post by sgx on 2011-10-11
Hi, the .wine folder created by starting wine, or using winecfg, can be renamed, and any other version of wine reinstalled, then copy back the 'good parts' from the .wine folder you renamed, like the drive_c folder, or Program Files folder, or just your Steinberg/VstPlugins folder. The wine binary and lib files are separate, in /usr folders. I keep good .wine folders on a usbstick, dvd, and external hardisk, for good luck

run winecfg, and choose alsa, not jack, in the audio panel.
Some apps now can utilize jack midi, install a2jmidid and use
the command

a2jmidid -j default   to place midi ports in the qjackctl midi tab.

For vsts in general, install wineasio, and issue the command  

regsvr32 wineasio.dll

Then install reaper, a 6meg download, in your home folder.

[http://www.reaper.fm/](http://www.reaper.fm/)

Almost all vst plugins work.
Those using pace, ilok, macromedia, and some Synthmaker plugins won't work. Native Instruments, IK Multimedia, and Wusikstation products, all have ethnic soundsets available, and are known to work well with reaper and wineasio, nvidia videocards/chips, and alsa supported souncards/chips.

The reaper daw output can be routed with, or to, any linux audio apps, like rakarrack or calf plugins or jamin, for detailed fx
and mastering.

Sorry that you lost so many hours in the process!

---

### Post by shantiq on 2011-10-12
ok Sgx thanx for detailed info. Will investigate. :KS


PS good tip on backing up .wine    had never though of doing that :::))
PS2 **still would not mind a Rosegarden specific how-to** if anyone has gone down that particular route...


Now using Jack is something i will never do; do not mind using it with Ardour as i do not have to see it   :)  It is to my mind a vile piece of kit :)



So solutions which involve Jack i will probably spurn; please excuse my prejudice but i simply do not like it.



I am confused here are you suggesting different routes one with jack one with alsa ?



PROBLEM tho on my newly installed wine1.3 [positive outcome of yesterday's fiasco i now have 1.3 instead of 1.2] when i click on audio on winecfg i do not see the options not sure how to see them  see attached image




Reaper looks interesting will check that


Ok so as i said will investigate.   Might need a little more detailed info.

---

### Post by sgx on 2011-10-13
Yikes! No wine audio tab? Try this, start regedit

wine /home/you/.wine/drive_c/windows/regedit.exe

find this key:  HKEY_CURRENT_USER\Software\Wine\Drivers\Audio

and edit the key to be alsa.

Reboot or logout/in, and try winecfg again.
If that does not work, delete the whole key itself.
If it still fails to show the audio tab, install
another wine version.

As for jackd, there is nothing there to hate, it is just
virtual cables between your software and hardware :popcorn:

start qjackctl, click the main Connect button on the lower left,
the connection panel appears (with its own 'connect' button.)
Select a midi item in the alsa tab, on the right side,
that you want to hear/use,
then select it's destination on the left, and press the
secondary connect button, not the one on the main gui.
The connection is now drawn. Do this for the audio tab.
System capture is on the left, System playback on the right.
select the desired items, and press connect.

Patchage, and jp1 from linuxdsp, draw these same connections, but in very different ways, so you can have them
all open, and choose which you need and prefer for various tasks.
jp1 requires fewer clicks to connect, but lacks the advanced configurations found in qjackctl. Patchage draws floating docks
for audio and midi items, easy to drag onscreen where you like,
with colored i/o connectors.
Reaper, hydrogen drum machine, and phasex synth, all connect
automatically in the qjackctl audio tab. Reaper DAW
output can be disconnected, and re-connected to more linux fx,
for further processing. I often send it to rakarrack multi-fx
for the finishing touch.

When you install wineasio for reaper, fst, dssi-vst etc
issue the command    regsvr32 wineasio.dll
It will tell you if successful. Then in a DAW preferences,
wineasio can be chosen as the vst device. Midi devices also
require to be enabled per your daw requirements.
Cheers

---

### Post by shantiq on 2011-10-17
ok Sgx so i got there the Reaper route   see image


so cool there thaNk you

But not a linux solution and i see Reaper [ a very nice program indeed ] is not free after a month ; altho very nice to have it free for a month


DIARY   :) :)
=====


 had to move back down to wine 1.2

and this time lost not my EAC and Foobar actually backed it up as suggested but did not need back up as reconfiguration worked .  Maybe only wipes everything going up   ??????    or maybe one of these things..........

Also found out Alsa seems to be the default audio choice in wine
but back in 1.2 all the options reappeared     so picked alsa well left it as was :)


Installed wineasio64

attached here from Falk 32-bit also included

ran ```
regsvr32 wineasio.dll
``` as advised


and got 
```
Successfully registered DLL wineasio.dll

```


also installed dssi-vst for good measure


Anyway all good but still not cracked Rosegarden and VST  :)


In my [**travels**]("http://en.wikipedia.org/wiki/Comparison_of_multitrack_recording_software") also found a really good program called[** Qtractor**]("http://qtractor.sourceforge.net/qtractor-index.html") which handles dssi plugins but i do not see as yet dssi-vst showing up in there


**SO** to complete this journey here **i still** call out to anyone who knows how to activate those VSTs in rosegarden or in Qtractor since it is a free Linux program


Learnt a few thngs and really great to hear those Safwan Matni dll plugins  love their sound

---

### Post by sgx on 2011-10-17
I can use the fst command, and qjackctl connections to use some windows synthesizers from a terminal. Link the .dll file from its
.wine location, to save typing :)

fst ZebraCM.dll On the Computer Music Magazine dvd
fst Triple*Cheese.dll  (fill in spaces with a *  )
fst Zebralette (now free in the main Zebra2 archive download!

These are good U-he instruments, with extra soundsets online, but they all have built-in preset loading/saving!

Ones that fail using fst, are not likely to work in other native linux settings. But probably do fine in Reaper. (No luck to be had with plugins requiring ilok, pace, or dongles.


You may be able/lucky enough to compile an ardour-vst package. The licensing detail is explained here:

[http://www.remastersys.com/forums/index.php?topic=1691.0](http://www.remastersys.com/forums/index.php?topic=1691.0)

Apparently Arch Linux has this natively:

[http://pkgs.org/download/ardour](http://pkgs.org/download/ardour)

and Arch may be a good long term option as a DAW environment.



ladspa/lv2 plugins for ardour, a general list:

[http://ardour.org/plugins](http://ardour.org/plugins)

Cheers

---

### Post by shantiq on 2011-10-18
thanx but what is fst from    it does not get recognized on my system

```
fst Oud.dll
No command 'fst' found, did you mean:
 Command 'lst' from package 'lustre-utils' (universe)
 Command 'tst' from package 'pvm-examples' (universe)
 Command 'pst' from package 'prismstumbler' (universe)
 Command 'fts' from package 'fts' (universe)
 Command 'fmt' from package 'coreutils' (main)
 Command 'fet' from package 'fet' (universe)
 Command 'fs' from package 'openafs-client' (universe)
 Command 'fsc' from package 'scala' (universe)
 Command 'st' from package 'swift' (universe)
 Command 'st' from package 'suckless-tools' (universe)
fst: command not found

```



As regards compiling ardour from source that might be asking for a headache in my case   :)

---

### Post by sgx on 2011-10-18
fst is a little command, should be in rpm repositories like this

[http://rpm.pbone.net/index.php3/stat/4/idpl/13870954/dir/pclinuxos/com/fst-1.9-1pclos2007.i586.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/13870954/dir/pclinuxos/com/fst-1.9-1pclos2007.i586.rpm.html)

so use the alien command to convert the .rpm to .deb,
then the dpkg command to install it.

sudo alien -d fstxxxx.rpm
sudo dpkg -i fstxxxx.deb

festige is a gui for fst and dssi-vst:

[https://launchpad.net/~falk-t-j/+archive/festige/+packages](https://launchpad.net/~falk-t-j/+archive/festige/+packages)

Cheers

---

### Post by mossontherock on 2011-11-03
I am also on a quest to get vst working in Rosegarden 11.06.  I'm using Kubuntu 11.10 and have installed kxstudio repositories using synaptic to install kxstudio related items.  Kxstudio does a great job at putting together a whole range of audio tools including Festige VST audio loader in various distros.

I have dssi-vst, wine, wineasio installed as part of the kxstudio installation, but I'm still not getting the windows vsts visible.  Several years back I had it working, and one important factor was to have the vsts available in your home directory eg /home/user/vst, as this is one of the default places Rosegarden looks for vst plugins.

This time round it hasn't worked, hence my quest to find a solution. 

By the way, if you upgrade the Kernel to PPA, and wine refuses to work and complains about virtual memory, try adding your username to the "audio" group: System Setting > (System Administration) User Management > Groups tab - Show system Groups.

---

### Post by sgx on 2011-11-03
# Set VST_PATH for Bash shell
if [ -n "\$VST_PATH" ]; then
   # Set VST_PATH for Bash shell
   export "VST_PATH=/usr/lib/vst"
fi


I have this path and name in /etc/profile.d/vst.sh
and copy some vsts there, and both user and
group root have permissions to read/write the /usr/lib/vst
folder contents.

A proper vst host/daw like reaper or energyXT using wineasio,
and installed in your  /home/user folder is still going to be far better than a linux app at using such plugins to their full potential. You can route the reaper output to your other linux apps, when you like what you hear.
If you get vst enabled versions of qtractor or ardour, they might
find the vsts using

# Set DSSI_VST_PATH for Bash shell
if [ -n "\$DSSI_VST_VST_PATH" ]; then
   export DSSI_VST_VST_PATH="/usr/lib/dssi/dssi-vst"
fi

named dssi-vst.sh in /etc/profile.d

Maybe rosegarden will look there too.
Cheers

---

