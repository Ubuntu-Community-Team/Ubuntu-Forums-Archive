---
title: "HOWTO: play amiga games with E-UAE emulator"
date: 2006-06-21
forum: Tutorials
---

### Post by rune_kg on 2006-06-21
Hi folks

Does Supercars II, Kickoff II, Superfrog, Gravity Force, Medal of Honor and Alien Breed ring a bell. Well now you can play all your favorite Amiga games, right here in your favorite OS. I'm using an clevo d470k AMD3200, 256MB laptop and everything is working 100%, with a nice smooth visual performance and great sound.

Do this and you should be in business.

1)Go to terminal

2)Open sources.list in gedit
```
sudo gedit /etc/apt/sources.list
```
And add the following lines to the end:
```
#E-UAE and other funky Amiga stuff
deb http://morgoth.free.fr/ubuntu dapper-backports main
```
3)Update apt-get:
```
sudo apt-get update
```
4)Install E-UAE:
```
sudo apt-get install e-uae
```
5)Now you have the emulator installed, but still need the kickstart. This can only be downloaded legally for free if you own an old Amiga with the adequate (in this case version 1.3) Kickstart Rom. 
```
wget "http://www.theoldcomputer.com/Libarary's/Emulation/BIOS_Roms/Kickstart1.3.zip"
```
Alternatively you can buy the full range of Amiga Kickstart's here: [http://www.amigaforever.com/](http://www.amigaforever.com/) or roll one of your own using your old Amiga and Workbench Floppy (see [http://ale.emuunlim.com/guides/get-kick-rom.shtml](http://ale.emuunlim.com/guides/get-kick-rom.shtml) and [http://www.pcguru.plus.com/linux_uae_faq.html)](http://www.pcguru.plus.com/linux_uae_faq.html)).

6)Unpack and copy the kickstart.roms into a folder in your home directory fx. to:```
/home/johndoe/amiga/roms
```
7)Go to terminal

8)Make sure you are user and not root

9)Type:
```
uae
```
10)And lo and behold, the E-UAE control panel is opening.

11)Ok time to get some games. Go here: ```
[http://amiga.nvg.org/warlock/adf/search.phtml](http://amiga.nvg.org/warlock/adf/search.phtml)
```
and download whatever you want or search google for 'amiga adf'.

12)Unpack the .adf files you just downloaded to fx. 
```
/home/johndoe/amiga/games
```
13)Now get back to he E-UAE control panel and lets play a game god dammit. But first we have to make a few settings:
[LIST=1][*]click Memory/change Kickstart ROM file and set it to the Amiga rom you want to use. fx. /home/johndoe/amiga/roms/KICK13.ROM, for standard Amiga 500 rom.
[*]click Gameports and make sure the selection here is to your liking. And now finally.[/LIST]
14) Fire up a game by:
[LIST=1][*]Click Floppy Disk and insert the .adf file of your liking into DF0: 
[*]If the game has more disks you can insert disk2 in DF1:
[*]Unactivate Pause button[/LIST]
15)Watch and weep while your favorite game ever loads. Use F12+s to toggle fullscreen view.

The performance is incredible and I would like to thanks the guys behind the e-uae emulator and the linux-port for doing a truly outstanding job! Please let me know how it goes if anyone tries this. If more than 3 people asks for it, I will make this howto into a selfinstalling script, that sets everything up, including 10 favorite games.

CYA

Rune Kaagaard
Copenhagen

---

### Post by rune_kg on 2006-06-22
delete this...

---

### Post by yaztromo on 2006-06-22
What is the difference between UAE in the dapper repos and E-UAE in the dapper-backports repo?

---

### Post by rune_kg on 2006-06-22
Somebody correct me if i'm wrong, but as far as I know is E-UAE a fork of UAE, where a lot of the code is ported from winUAE. Most people seem to think that E-UAE performs better and is more stable.

Rune Kaagaard
Copenhagen

---

### Post by yaztromo on 2006-06-23
I should have googled this. I'm lazy!

You are right [http://sourceforge.net/projects/uaedev/](http://sourceforge.net/projects/uaedev/)

I have UAE installed presently, will be nice to upgrade.

---

### Post by rune_kg on 2006-06-24
Ahh you have the UAE. Interesting. How is that running for you? Did you by any chance come up with a good solution for making custom keyboard maps?

Rune Kaagaard
Copenhagen

---

### Post by mulperi on 2006-06-24
I have seen it somewhere but could you please tell me how to get the new repostory authenticated?

---

### Post by yaztromo on 2006-06-24
[QUOTE=rune_kg]Ahh you have the UAE. Interesting. How is that running for you? Did you by any chance come up with a good solution for making custom keyboard maps?

Rune Kaagaard
Copenhagen[/QUOTE]

I never got far with the original UAE so I couldnt tell you mate.

I got the new E-UAE installed from your repository without hitch and other than the sound stuttering problem which was also in the other one it works flawlessly.

---

### Post by rune_kg on 2006-06-24
Hey yaztromo

Just to set things straight. The great dude who did the .deb package is Morgoth. Visit Morgoth here [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/).

Regarding the sound stuttering, what's the specs of your box? My sound only stutters when I am opening something big in the background (i.e. Open Office). Otherwise it works 100%.

Hey mulperi

Morgoth supplies the solution to that. See: [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/) to see how to import signing key to apt.

Take care guys.

Rune Kaagaard
Copenhagen

---

### Post by mulperi on 2006-06-25
Thanks Rune!

---

### Post by yaztromo on 2006-06-25
[QUOTE=rune_kg]Hey yaztromo

Just to set things straight. The great dude who did the .deb package is Morgoth. Visit Morgoth here [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/).

Regarding the sound stuttering, what's the specs of your box? My sound only stutters when I am opening something big in the background (i.e. Open Office). Otherwise it works 100%.

Rune Kaagaard
Copenhagen[/QUOTE]

I'm running an athlon XP 1500 with a geforce2 mx using the nv driver.

Strangely if another window is brought to focus (even if it doesnt cover the emulator window), the sound problem will go away. It only happens when the emulator window has focus. :-?

---

### Post by rune_kg on 2006-06-25
hmm interesting. It also stutters in fullscreen (f12+s)???

Rune Kaagaard
Copenhagen

---

### Post by rune_kg on 2006-07-01
Try to change these lines in .uaerc (which is located in your users home dir)
to:
```
sound_max_buff=16384
sound_frequency=22050
```

Rune Kaagaard
Copenhagen

---

### Post by leech on 2006-07-09
No GTK2 version?  I know it's out there, I was playing around with it about a month ago.  It's still not quite up to WinUAE as far as features go, but it is quite usable.

Leech

---

### Post by handy on 2006-07-10
I'll have to check this out! The Amiga was where I started on this never ending computer obsession.

I've still got one kicking around here somewhere, & some software & games too!

It's a shame I can't google for things that I've lost in my house!

Actually that is a scary thought!

---

### Post by rune_kg on 2006-07-12
For those having problems with sound, there is now a new improved version avaiable that has an imphasis on sound. Get the build here:
```
[http://www.rcdrummond.net/uae/test/20060711/e-uae-0.8.29-CVS.tar.bz2]("http://www.rcdrummond.net/uae/test/20060711/e-uae-0.8.29-CVS.tar.bz2")
```
See the changelog here:
```
[http://www.rcdrummond.net/uae/test/20060711/ChangeLog]("http://www.rcdrummond.net/uae/test/20060711/ChangeLog")
```
OH and be sure to read the /docs/compiling.txt inside the .tar file for a little guidance and you can check out this little guide on compiling ```
[http://giuliogiuseppecarlo.interfree.it/uae/en/index.html]("http://giuliogiuseppecarlo.interfree.it/uae/en/index.html")
```
About a gtk+ 2 version...No idea??????0:D

Take care guys.

Rune Kaagaard
Copenhagen

---

### Post by phalab on 2006-07-13
Hi All,

wanted to try this, and got all installed, downloaded 'Walker' from that site (which originally was 3 disks), but it was a HD installable version. Installed unlzx, and unlzx-ed it, and now I have a bunch of files (not disk files), and I don't know how to start it up. Anyone have any experience with this?  :)

Help much appreciated...

---

### Post by rune_kg on 2006-07-13
> **phalab said:**
> Hi All,

wanted to try this, and got all installed, downloaded 'Walker' from that site (which originally was 3 disks), but it was a HD installable version. Installed unlzx, and unlzx-ed it, and now I have a bunch of files (not disk files), and I don't know how to start it up. Anyone have any experience with this?  :)

Help much appreciated...

Hey phalab

Will post a little something on how to do just that soon. Stay Tuned.

Rune Kaagaard
Copenhagen.

---

### Post by mafutha on 2006-07-13
How does one install AmigaOS in a directory on the harddrive? I have Amigados on cd (Totally legal...I own an amiga).

---

### Post by handy on 2006-07-14
> **mafutha said:**
> How does one install AmigaOS in a directory on the harddrive? I have Amigados on cd (Totally legal...I own an amiga).

You do need AmigaDOS 1.3.  Most games will run on that one. If you have a CD it is probably AmigaDOS 3.0+.  Unless you have a after market CD that someone has put together.

Does anyone know the legalities of the AmigaDOS distribution?  Does anyone care anymore?

---

### Post by rune_kg on 2006-07-14
Hey phallab

Well the basic steps to use the amiga app. WHDload files are:

1)Install a WorkBench to HD
2)Install WHDload in the Workbench
3)Run the game inside the workbench

Found a great howto for uae, will try it out later and let you know how it goes:

[http://www.amiga.hu/amigos/ancientoys/whdload_setup1.html]("http://www.amiga.hu/amigos/ancientoys/whdload_setup1.html") 

Stay loose!

Rune Kaagaard
Copenhagen

---

### Post by rune_kg on 2006-07-15
So you gotten hold of a .hdf file for a game but who you gonna call. Well if the line at ghostbusters is busy, you might wanna try this little howto. Worked great for me.

AIAB is a ready compiled workbench with a tons of features, including the - for this use - essential 'whdload' which is an amigaOS app that allows you to play converted floppy .hdf files directly from the workbench.

So listen up and stay sharp guys!

1) get AIAB here: [http://aiab.emuunlim.com/r10.5/](http://aiab.emuunlim.com/r10.5/)
2) extract it to fx /home/<username>/uae/aiab
3) copy a 3.1 kickrom to /home/<username>/uae/aiab/Roms and name it kick.rom
4) create this dir /home/<username>/uae/conf
5) and create a file called aiab.conf containing this setup. Search and replace 'rune' with your own username
```
config_description=E-UAE and AIAB configuration
config_version=0.8.25
unix.rom_path=./
unix.floppy_path=./
unix.hardfile_path=./
sdl.map_raw_keys=true
use_gui=yes
use_debugger=false
kickstart_rom_file=/home/rune/uae/aiab/Roms/kick.rom
kickstart_ext_rom_file=
kickstart_key_file=
flash_file=
cart_file=
kickshifter=false
floppy0=
floppy0type=0
floppy0sound=0
floppy1=
floppy1type=0
floppy1sound=0
floppy2=
floppy2type=-1
floppy2sound=0
floppy3=
floppy3type=-1
floppy3sound=0
nr_floppies=2
floppy_speed=100
floppy_volume=33
parallel_on_demand=false
serial_on_demand=false
serial_hardware_ctsrts=true
serial_direct=false
scsi=false
sound_output=normal
sound_bits=16
sound_channels=stereo
sound_max_buff=16384
sound_frequency=44100
sound_interpol=none
sound_adjust=0
sound_filter=off
sound_volume=0
comp_trustbyte=indirect
comp_trustword=indirect
comp_trustlong=indirect
comp_trustnaddr=indirect
comp_nf=true
comp_constjump=true
comp_oldsegv=false
comp_flushmode=soft
compforcesettings=false
compfpu=true
comp_midopt=false
comp_lowopt=false
avoid_cmov=false
cachesize=16383
joyport0=mouse
joyport1=joy0
bsdsocket_emu=false
synchronize_clock=no
maprom=0x0
gfx_display=0
gfx_framerate=1
gfx_width=768
gfx_height=576
gfx_width_windowed=768
gfx_height_windowed=576
gfx_width_fullscreen=768
gfx_height_fullscreen=576
gfx_refreshrate=0
gfx_vsync=false
gfx_lores=false
gfx_linemode=double
gfx_correct_aspect=false
gfx_fullscreen_amiga=true
gfx_fullscreen_picasso=false
gfx_center_horizontal=none
gfx_center_vertical=none
gfx_colour_mode=15bit
immediate_blits=false
ntsc=false
show_leds=false
keyboard_leds=numlock:none,capslock:none,scrolllock:none
chipset=ecs_agnus
collision_level=sprites
fastmem_size=0
a3000mem_size=0
z3mem_size=16
bogomem_size=0
gfxcard_size=4
chipmem_size=4
cpu_speed=max
cpu_type=68040
cpu_compatible=false
cpu_cycle_exact=false
blitter_cycle_exact=false
log_illegal_mem=false
catweasel_io=0x0
kbd_lang=it
state_replay=no
state_replay_rate=250
state_replay_buffer=20971520
filesystem2=rw,dh0:Workbench:/home/rune/uae/aiab/Harddrives/Workbench/,0
filesystem=rw,Workbench:/home/rune/uae/aiab/Harddrives/Workbench/
filesystem2=rw,dh1:Applications:/home/rune/uae/aiab/Harddrives/Applications/,0
filesystem=rw,Applications:/home/rune/uae/aiab/Harddrives/Applications/
filesystem2=rw,dh2:Games:/home/rune/uae/aiab/Harddrives/HD-Games/,0
filesystem=rw,Games:/home/rune/uae/aiab/Harddrives/HD-Games/
input.config=0
input.joymouse_speed_analog=20
input.joymouse_speed_digital=10
input.joymouse_deadzone=33
input.joystick_deadzone=33
input.mouse_speed=100
input.autofire=10

```
6) Get your harddisk file fx: Walker.lzx
7) install unlzx with apt-get install unlzx (you need the morgoth repository in your sources.list)
7) unlzx to /home/<username>/uae/aiab/Harddrives/HD-Games/
8) chmod -R 777 /home/<username>/uae/aiab
9) cd to /home/<username>/uae/conf
10) run uae -f aiab.conf
11) follow instructions and insert workbench 3.1 disk 2 when asked for it
12) select your resolution and press save
13) AIAB should now boot
14) Right click desktop and select 'Shell Promt'
15) DH2:
16) Cd to where the Walker.Slave file is located
17) whdload Walker.Slave

And lo and behold... the game is starting. If anyone tries this howto, let me know. 

Take care!

Rune Kaagaard
Copenhagen

---

### Post by mafutha on 2006-07-15
I have a bought copy of 1.3, 2.0, 3.0, 3.1, and 3.9. My amiga still works. In fact my rom image is from the amiga. I just need to know if you can install the AmigaOs in a directory on the harddrive and how to set up the cdrom to work with uae. Or do you have to use disk files.

---

### Post by phalab on 2006-07-17
Thanks a lot!  :)  I'll have a look at it as soon as I can (hopefully by wednesday).
Kind regards,

---

### Post by rune_kg on 2006-07-17
> **mafutha said:**
> I have a bought copy of 1.3, 2.0, 3.0, 3.1, and 3.9. My amiga still works. In fact my rom image is from the amiga. I just need to know if you can install the AmigaOs in a directory on the harddrive and how to set up the cdrom to work with uae. Or do you have to use disk files.
AIAB has some support for cdrom. What do you want to accomplish?

Cheers

Rune Kaagaard
Copenhagen

---

### Post by Malcolm on 2006-07-19
I had the sound stuttering problem. Playing around with frequency and buffer size values didn't solve it, so I decided to try the newest version, as suggested by rune_kg, compiling it myself. Well, it works flawlessly! Excellent emulator, and it's getting close to WinUAE (which unfortunately is still the best version).

So if you have sound stuttering problem, give the newest release a try, or wait for the version in the repositories to be updated. It's worth your time in any case. :)

---

### Post by rune_kg on 2006-07-21
> **Malcolm said:**
> I had the sound stuttering problem. Playing around with frequency and buffer size values didn't solve it, so I decided to try the newest version, as suggested by rune_kg, compiling it myself. Well, it works flawlessly! Excellent emulator, and it's getting close to WinUAE (which unfortunately is still the best version).

So if you have sound stuttering problem, give the newest release a try, or wait for the version in the repositories to be updated. It's worth your time in any case. :)

Hey Malcolm

Good to know, will try it soon, but as I don't have any problems with the current debian package im not in a hurry. Yeah and I too  thinks it's closing in on WinUAE, what we need most now is a better gui and easy keymapping.

Ciao

Rune Kaagaard
Copenhagen

---

### Post by mafutha on 2006-07-26
> **rune_kg said:**
> AIAB has some support for cdrom. What do you want to accomplish?

Cheers

Rune Kaagaard
Copenhagen

I just wondering on how to get it setup under Ubuntu. I have it running under windows but like to get it installed under Ubuntu. Do you have to use disk files or can you install it in a directory on the harddrive?

---

### Post by rune_kg on 2006-07-26
> **mafutha said:**
> I just wondering on how to get it setup under Ubuntu. I have it running under windows but like to get it installed under Ubuntu. Do you have to use disk files or can you install it in a directory on the harddrive?Hey mafutha

Well its possible to have e-uae access an actual physical cd-rom drive, using the scsi=true setting and the uaescsi.device. Never tried this though. But you apparently want to have access from inside the emulated amigaOS to an emulated cd-rom drive thats placed somewhere on your hdd? This should be possible with something like this in your config file: ```
filesystem=ro,CD0:/home/username/uae/cdrom
```
I haven't tried that either.

C YA

Rune Kaagaard
Copenhagen

---

### Post by tsagas on 2006-08-08
Regarding the sound issue, I had the same problem while playing my favourite Addam's Family. I tried different sound settings but nothing worked. Then I went to CPU -> Emulation Speed and set it to 'Maximum" and the sound was fixed.

---

### Post by kingmob on 2006-08-24
I'm hoping anyone can help me here. I'm using e-uae with mythtv, but the two don't mix well.  I have to enter a command line and a rom directory in mythtv, my command line basicly just mounts the floppy that was selected in the mythtv interface.
This poses problems, since most games have multiple floppies and mythtv is supposed to be used without much user input.

- The first thing i would like to solve is a way to get the gui back after i start with the use_gui=no option
- even better, a shortcut key to be able to mount other floppies directly
- and the big one, a way to get e-uae to mount a whole folder full of .adf files

So now my command is like: uae -s floppy0=%s
where %s will be the selected file.
So 'all' i need is for a way to make a folder full of single files, that somehow can tell uae to mount all the floppies in a certain directory.

I apologize if there is a comprehensive list somewhere with the shortcut keys and the works, but i couldn't find it anywhere. There doesn't even seem to be a man-entry.

---

### Post by rune_kg on 2006-08-24
Hey kingmob

> The first thing i would like to solve is a way to get the gui back after i start with the use_gui=no option
Well been looking through the e-uae maillist, and I think no gui means just that: no gui.

> - even better, a shortcut key to be able to mount other floppies directly
Not possible you are stuck with the gui. Theres it not to my knowledge any other way to mount a floppy once u-ae i running

> - and the big one, a way to get e-uae to mount a whole folder full of .adf filesWell first of all, ofcourse you can't mount any more floppies than the emulated chipset allows. Maximum four. But that should be enough for most games:) But otherwise this can be done very easy by making a script that creates a copy of your .uaerc and inserts the .adf files into it as floppy0=$(FILE_PATH)/uae/adf/superfrog_disk1.Adf, floppy1=$(FILE_PATH)/uae/adf/superfrog_disk2.Adf and so on and so forth. Then it runs it with uae -f superfrog.conf.

But the problem here is that many games (more than half i think) doesn't support more than one diskdrive. So I dont think that is feasible.

The best bet would be to use something like devilspie to minimize the gui and then assign a shortcut to it to toggle it on and off.

Otherwise the only other solution I can think of is to install a workbench (like aiab) on your harddisk and then use whdload to start the .hdf file games from inside the workbench. That should get you over the whole need to change disks. But if it was be i've go with the gui. It's not that bad:)

Good luck, and please share any revelations that you may find!!!!

Take care!

Rune Kaagaard
Copenhagen
[http://runelyd.dk](http://runelyd.dk)

---

### Post by kingmob on 2006-08-25
Thanks for the reply. Last night (very late :|) i got the same relevation that i can ofcourse just simply load a custom config file. I'm not that much of a linux guru that i can write an automatic script though, so i've been doing it by hand for the games i like. I was planning on cutting down the list of games anyway ;).

The problem is not the gui itself, but the fact that i'm not meant to be sitting in front of my TV with a mouse and keyboard to get the games to play. Personally i don't have that big a problem with it, but it's against the mythtv belief ;).
Also, it's good for the GF acceptance factor if everything works with a few simple keypresses :)

But for now, this method seems to work fine for most games.


I have an unrelated problem though, all my games seem terribly slow in loading. Much slower than my original A500 i'm sure. CPU is at max, but that doesn't seem to help.

---

### Post by rune_kg on 2006-08-26
> I have an unrelated problem though, all my games seem terribly slow in loading. Much slower than my original A500 i'm sure. CPU is at max, but that doesn't seem to help.

Hmm. Mine is about the same as an original A500. The first thing I would try is try to compile the latest build from scratch. Theres a LOT of bugfixes compared to the deb. See how to compile earlier in this thread. Make sure the emulation speed is set to max.

C YA

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by kingmob on 2006-09-05
Compiling sadly doesn't seem to work for me. it doesn't work for me and the errors are too complicated :(. Does anyone know a release date for 0.8.29? Since hopefully then someone will build a working package.

---

### Post by leech on 2006-09-10
Hey, you're in luck, I found a fairly easy way to build the newest version (currently 0.8.29-WIP3).  Basically you just download the CVS version, and the source for 0.8.29-WIP3.  Copy the 'debian' directory from the CVS version to the release source tree, then run 'fakeroot dpkg-buildpackage' if it fails, it will tell you what dependencies it needs.  If you have the repositories for the source at the beginning of this thread, you should be able to 'sudo apt-get build-dep e-uae' and it'll get everything you need to build the package.

Now onto my problem.  I can't seem to get the Picasso96 graphics emulation to work.  I'm not sure if I'm just missing something, or what?  I have it set up in the GUI, and I installed workbench 3.1 to a folder that I mounted as the hard drive, but still it only allows the AGA resolutions.  Any ideas?  I know I could probably install that AIAB, but I kind of wanted to do everything from scratch.

Leech

---

### Post by kingmob on 2006-09-19
Thanks for the tip, i will try it. Does anyone know why it takes so long for packages to be updated, even though they are universe/multiverse?
Is there a place you can upload them to or something, so that they'll get added eventually?

---

### Post by lukew on 2006-12-18
Hi,

This nearly worked a treat. I can get 1 disc games to work but more than that they seem to get stuck in a cycle, almost like the second disc does not want to be loaded. The graphics and titles all load correctly but just wont let me play!!!

I have tried with disk two in DF1 from the start and also placing disc two into in DF0 but nothing works.

Any ideas would be greatly apreciated. 

Thanks

Luke

---

### Post by rune_kg on 2006-12-20
Hi Luke

Hmmm interesting. Many games does not support extra floppydrives so changing the disk in DF0 when asked for it should be the safe bet.

Which games did you try that it did'nt work on?

Sometimes you have to press fire/enter to start loading, but you probably tried that allready:)

[http://www.freelists.org/archives/uae/](http://www.freelists.org/archives/uae/) - the archives of the mailinglist is a good place to start

CYA

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by lukew on 2006-12-20
Hay Rune,

Thanks for the help.

I have tried Super Frog and Alien Breed again with even more fire pressing and general any key pressing....

Alien Breed asks me for the 2nd disc but wont change from that screen.

Superfrog does not ask me for a second disc but displays a few screens which cycle when i press fire. I change the discs anyway and the graphics cycle around but this time slightly scrambled.

Luke

---

### Post by lukew on 2006-12-22
> **lukew said:**
> Hay Rune,

Thanks for the help.

I have tried Super Frog and Alien Breed again with even more fire pressing and general any key pressing....

Alien Breed asks me for the 2nd disc but wont change from that screen.

Superfrog does not ask me for a second disc but displays a few screens which cycle when i press fire. I change the discs anyway and the graphics cycle around but this time slightly scrambled.

Luke

Hi,

Not sure what fixed it but..

1. tried differnet kick start
2. Fiddled with 1 and 2 joystick options.....

Excellent.. Alien Breed, Super Frog and here we come...

---

### Post by mistermax on 2007-01-11
Rather than start another thread, it seemed like this was a place for good uae advice....

I've got E-UAE installed, it loads up games fine, but the problem I get is dark horizontal lines across the screen?

Also, I've got a load of configurations on file- how do I load them in? E-UAE seems to have a way to save configurations, but I want to load them.

---

### Post by marx2k on 2007-01-11
I cannot figure out how to get this to go fullscreen! I am using E-UAE 0.8.29-WIP3 and F12 + S does nothing

---

### Post by marx2k on 2007-01-11
> **rune_kg said:**
> 
[...]
6) Get a harddisk file fx: [http://amigos.amiga.hu/ancientoys/gamefiles/whd/Walker.lzx](http://amigos.amiga.hu/ancientoys/gamefiles/whd/Walker.lzx)
[...]


Broken link-- please advise

---

### Post by unabatedshagie on 2007-01-13
> [...]
7) unlzx to /home/<username>/uae/aiab/Harddrives/HD-Games/
[...]

I'm not sure what you mean by this step, do I have to type something into the terminal?

---

### Post by marx2k on 2007-01-13
> **unabatedshagie said:**
> I'm not sure what you mean by this step, do I have to type something into the terminal?

Basically that means to unpackage the LHA or LZH archive into that directory that you were supposed to have made in step 1 or 2 .. replacing <username> with your username

---

### Post by unabatedshagie on 2007-01-14
Nope, I'm still lost, I have installed unizx so how do I unpackage it?

---

### Post by blastradius on 2007-01-17
Thanks for this, everything works except the 'get some games' link.  Any alternatives?

---

### Post by lukew on 2007-02-07
There is a edgy version available.

Repo:

```
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) edgy-backports main

```

Add Key:


```
wget [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc)
sudo apt-key add morgoth-signkey.gpg.asc
```

---

### Post by rune_kg on 2007-03-10
Hi

Haven't checked in for a while. Yes it's true, the amigos adf repository is down. Try here instead:

[http://amiga.nvg.org/warlock/adf/search.phtml](http://amiga.nvg.org/warlock/adf/search.phtml)

Rune

---

### Post by Sotar on 2007-09-17
Hey. I have installed the emulator from the repositories, tossed in the proper kickstart and all... tired to load one of the games I had downloaded... and it crashed.
Which happens very often. Very few games I can even run without the program crashing to desktop, and only Pirates! I can actually play. Games like Utopia, Powermonger, Mega Lo Mania... they all will crash with some messages like: 

```
JIT: can't handle access!
JIT: instruction byte  0 is 89
JIT: instruction byte  1 is 48
JIT: instruction byte  2 is 08
JIT: instruction byte  3 is 8d
JIT: instruction byte  4 is 83
JIT: instruction byte  5 is 2c
JIT: instruction byte  6 is 11
JIT: instruction byte  7 is 00
JIT: instruction byte  8 is 00
JIT: instruction byte  9 is 39
Segmentation fault (core dumped)
```

It usually happens when I try to Alt+Tab to another window, but not only then.

Any idea what could be wrong?
I am going to try and compile the newer version tonight and see if that helps.

---

### Post by williambertram on 2008-07-26
Anyone get sound to work?  No sound on mine.

> **williambertram said:**
> Anyone get sound to work?  No sound on mine.

Fixed with the following:
 libsdl1.2debian-pulseaudio

I guess the version of E-UAE from this article uses SDL sound, and Pulseaudio is blocking SDL sound (according to what I've read) until you install this package.  Worked automatically after installing this.

By the way, if you are using this to play the old SSI "Gold Box" AD&D games, the Amiga versions are MUCH better than the dos versions.  :)  Absolutely kills playing the DOS version in dosbox.

F12 + S for fullscreen

---

### Post by rrrobles on 2008-10-26
E-UAE runs very fine almost the games in my computer, but specially Shadow of The Beast 1 hangs in opening, before call the second disk. There are any trick to run it?

---

### Post by lernatix on 2008-12-22
Hi peeps,

I had downloaded UAE to my Ubuntu Hardy install.

Then I followed OP to get E-UAE

When I type UAE - I GET UAE!!!

WTF?

And how do I make a desktop shortcut to UAE?

EDIT: Also...

I get this error when loading up games.

```
Trying to use Kickstart replacement.
Building CPU table for configuration: 68020
1866 CPU functions
Building CPU function table (2 0).
Using 24 bit visual, 32 bits per pixel
Using normal image buffer.
Segmentation fault

```

---

### Post by rrrobles on 2008-12-23
> **lernatix said:**
> Hi peeps,

I had downloaded UAE to my Ubuntu Hardy install.

Then I followed OP to get E-UAE

When I type UAE - I GET UAE!!!

WTF?

And how do I make a desktop shortcut to UAE?

EDIT: Also...

I get this error when loading up games.

```
Trying to use Kickstart replacement.
Building CPU table for configuration: 68020
1866 CPU functions
Building CPU function table (2 0).
Using 24 bit visual, 32 bits per pixel
Using normal image buffer.
Segmentation fault

```

If you install E-UAE, you doen't need to install UAE.
If you correct install E-UAE, the About folder will show E-UAE.
If typing UAE launches the old UAE, I suggest you remove the packages you installed e try to install only E-UAE.
To make a desktop shortcut just right-click in desktop and choose the "create launcher" option.

---

### Post by stillious on 2009-01-21
Anyone know hot to re-map a joypad? Currently I have directional control through the analogue stick instead of the d-pad and it's a bit useless :/

---

### Post by Devport on 2009-01-21
This site is wonderful - it has many many Amiga games, quite a lot of them in higher resolution versions for newer Amiga graphic chips and all of those games are legal because the companies gave their permission :

> Many Companies are supporting this site by giving us permission to upload their old commercial titles, and so you will find some of the best Amiga Games here, for download at no cost. Many sections are dedicated to both demo scenes - the Amiga and the PC scene, such as Pictures, Music and of course a lot of the best Demos which were ever made.

[www.back2roots.org](www.back2roots.org)

There are superb titles like Super Cars, Wonderboy, Leisure Suit Larry and the famous Lotus series !

Enjoy.

---

### Post by Gregormo on 2009-06-14
I was stoked when I found this thread. Sadly the mouse doesn't work properly. How are your "Game ports" settings? 

The mouse moves like my hands were shaking and it lags. Doesn't do what I want it to do.

Any ideads?

---

### Post by Gregormo on 2009-06-16
I don't have sound as well. Installing libsdl1.2debian-pulseaudio didn't help.

---

### Post by paulh1974 on 2009-06-25
HI guys can any1 tell me how 2 SAVE the games using the amiga emulator?? having played cannonfodder it asks me 2 insert a blank floppy disc, which obiously i cant.also with playing the settlers it doesnt require 2 insert a blank disc BUT the write protection is still on so i cant overwrite 2 save the game. any1 know a way round this???? cheers

---

### Post by kartal on 2009-11-30
I am using e-uae under xubuntu and I have no sound-mouse at all. Previously I was using uae and I had mouse btu no sound. Does anyone know how to make the sound work?


thanks

---

### Post by mocha on 2010-01-10
> **kartal said:**
> I am using e-uae under xubuntu and I have no sound-mouse at all. Previously I was using uae and I had mouse btu no sound. Does anyone know how to make the sound work?


thanks

Seems like maybe a build error in the Ubuntu packaged version?  Maybe there is a bug filed, in any case, just compile it from source:

Download from [http://www.rcdrummond.net/uae/]("http://www.rcdrummond.net/uae/") and extract to /usr/src as root.

```
sudo -i
cd /usr/src/e-uae...
apt-get build-dep e-uae
./configure --enable-cd32 --with-alsa --with-sdl-sound
make
make install
```

---

### Post by krizze on 2010-01-22
You'd probably want to add --with-sdl-gl, for opengl support also.

---

### Post by schneil on 2010-08-02
I couldn't get it to build, but I downloaded the latest executable off the authors website and sound works perfect (ALSA)

---

### Post by Bugsy_malone 666 on 2010-08-04
I'm a bit new to Linux and have stumbled across this thread, originally I was under the impression that amigas used similar programing language to linux?

So anyway I have installed e-uae onto my linux laptop and tried some games, have hit a coupld of small problems that I dont know how to get round:

1: decided to play the classic game of cannon fodder, however on some screens as you move the pointer up the screen, the pointer seems to become out of sync with the actual pointind device, so while the pointer is at 3/4 of the UAE screen, the linux pointer has reappeared outside of the UAE window!

2: is there a way to mount a physical DF0: drive? I have a usb diskdrive for the laptop and have a box of old software, some of which I'd like to try out again and wondered how I could get the kickrom of E-UAE to read the diskdrive as its own like the old Amiga would - you insert a disk it recognises theres one there reads it and runs the programe!

Any pointers?

of is there a website that tells you have to get it working for UAE?

I'd be interested in making an install of an Amiga OS too, I only ever played with workbench 1.3 on my amiga 500 (with its whole 1mb of memory!) and was wondering if newer ones could be downloaded and installed to hard drive?

I still think amigas are cool, especially for some video titling and also more over music sequencing!

---

### Post by mocha on 2010-08-06
Press and hold F12 while pressing G to capture or release the mouse, F12-S fullscreen, F12-Q quit.

Lots of good stuff here, [http://eab.abime.net/index.php]("http://eab.abime.net/index.php") related to e-uae and a few unofficial Linux variants.

---

### Post by WubiN00bie on 2013-02-15
I love retro games,:D Amiga has some of the best ports of games from the 80s. The only downside of the amiga is the load times. Since it is an emulator, is there anyway of speeding up the load times to games? 
I was testing different games out and Mortal kombat took so long to load!

---

