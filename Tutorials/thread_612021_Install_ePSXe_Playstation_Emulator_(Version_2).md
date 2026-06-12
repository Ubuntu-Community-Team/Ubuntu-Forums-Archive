---
title: "Install ePSXe Playstation Emulator (Version 2)"
date: 2007-11-13
forum: Tutorials
---

### Post by Felson on 2007-11-13
This is a guide to install the freeware Playstation 1 emulator [ePSXe]("http://www.epsxe.com/") in Ubuntu. It is an updated replacement for [this]("http://ubuntuforums.org/showthread.php?t=95835") guide, which is based on [this]("http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/") guide.

ePSXe is made for x86 only. If you use powerpc it probably won't work. You might want to try another emulator instead, for example [PCSX]("http://www.pcsx.net/") ([Guide]("http://ubuntuforums.org/showthread.php?t=159987")) or pSX ([Guide]("http://ubuntuforums.org/showthread.php?t=394097")) which is in the repository.

Legal note: The installation and use of this emulator requires a Sony Playstation BIOS file. You may not use such a file to play games in a PSX emulator if you do not own a Sony Playstation, Sony PSOne or Sony Playstation 2 console. Owning the BIOS image without owning the actual console is a violation of copyright law. You have been warned. Do NOT ask in this thread, or message me, where to find the BIOS file or game images. Any such messages will be ignored and possibly reported.

Note: This guide is provided as is. I have not personally tested Feisty or other earlier versions of Ubuntu, so your mileage may vary. Although there are no issues caused by this guide that I know of, use at your own risk.

Installation
Common changes:
```

sudo aptitude install unzip
cd ~
mkdir ePSXe_install
cd ePSXe_install
wget http://www.epsxe.com/files/epsxe160lin.zip

wget http://www.pbernert.com/gpupetemesagl176.tar.gz
wget http://www.pbernert.com/gpupetexgl208.tar.gz
wget http://www.pbernert.com/gpupeopssoftx117.tar.gz
wget http://www.pbernert.com/gpupeopssoftsdl116.tar.gz

wget http://www.myte.ca/files/spupeopsoss-alsa109.tar.gz
wget http://www.pbernert.com/spupetenull101.tar.gz

wget http://www.myte.ca/files/omnijoy-1.0.0-bin32.tar.gz
wget http://members.chello.at/erich.kitzmueller/ammoq/down/padJoy082.tgz

wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb

sudo dpkg -i getlibs-all.deb

export EPSXE='/usr/local/games/epsxe'
sudo mkdir $EPSXE
sudo unzip -d $EPSXE epsxe160lin.zip
sudo tar xfz gpupetemesagl176.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupetexgl208.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupeopssoftx117.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupeopssoftsdl116.tar.gz -C $EPSXE/plugins/

sudo tar xfz spupeopsoss-alsa109.tar.gz -C $EPSXE/plugins/
sudo tar xfz spupetenull101.tar.gz -C $EPSXE/plugins/

sudo tar xfz omnijoy-1.0.0-bin32.tar.gz -C $EPSXE/plugins/
sudo tar xfz padJoy082.tgz -C $EPSXE/plugins/

cd $EPSXE/plugins/
sudo mv padJoy/bin/* . 
sudo rm -rf padJoy
sudo mv cfg* ../cfg/
sudo mv *.cfg ../cfg/
sudo chmod 666 ../cfg/*.cfg

cd $EPSXE
sudo chmod 777 cfg sstates snap memcards
sudo touch memcards/epsxe000.mcr memcards/epsxe001.mcr .epsxerc
sudo chmod 666 memcards/*
sudo chmod 666 .epsxerc

```

(note, "upx-ucl-beta" may be "upx-ucl" on Hardy)
```

sudo aptitude install upx-ucl-beta

cd $EPSXE
sudo cp epsxe epsxe_bak
sudo upx -d epsxe

sudo getlibs $EPSXE/epsxe

cd ~
rm -rf ePSXe_install
```

Create a shell script that will start ePSXe:
```
sudo gedit /usr/local/bin/epsxe
```

and paste this:
```

#!/bin/bash

export EPSXE='/usr/local/games/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe $*
chmod 666 $EPSXE/cfg/*.cfg $EPSXE/sstates/* $EPSXE/memcards/*.mcr $EPSXE/snap/* 2>/dev/null
```

Save/Close, and change permissions for the new file:
```
sudo chmod 755 /usr/local/bin/epsxe
```

You can now start by typing "epsxe" in the terminal (without "").

[LIST]
[*]In the menu, open "Config -> BIOS", and set it to /usr/local/games/epsxe/bios/SCPH1001.BIN, click OK. (You must find and obtain ths file yourself. Once you have a copy of it, put it in /usr/local/games/epsxe/bios/)
[*]Open "Config -> Video", and select either "Pete's MesaGL Driver 1.76", "Pete's XGL2 Driver 2.8" or "P.E.Op.S. Softx Driver 1.17". Click configure, then OK to write a config file. Verify that it is working by clicking the Test button, then OK. (Which one you use depends on your computer.)
[*]In "Config -> Sound" select "P.E.Op.S. OSS Audio Driver", "P.E.Op.S. ALSA Audio Driver" or "Eternal SPU Plugin", Configure, then OK. Verify that it is working by clicking the Test button, then OK. (The "NULL" driver are for those few games that just don't seem to work with sound. Or if you have a slow computer, and figure you don't care for the sound.)
[*]In Config -> CDROM, set the path to your CD/DVD-ROM. In most cases it should be /dev/cdrom but in my case /dev/hdc. You can check your path by typing "mount |grep cd" in a console.
[*]In Config -> Game Pad -> Pad 1 menu, you can set up the controls with the keyboard. If you have a real controller, use the "Config -> Ext. Game Pad" option, and pick either omnipad or padjoy, click configre, and set your buttons where you want them.
[/LIST]

**Useful Links**
[Original Thread]("http://ubuntuforums.org/showthread.php?t=95835")
[Icon]("http://www.myte.ca/files/epsxe.png")
[Another How-To]("http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html")
[Petes Home Page]("http://www.pbernert.com/index.htm")
[Petes Forum]("http://www.razyboard.com/system/user_Pete_Bernert.html")
[NightCrawler03Xs How-To/Installer]("http://ubuntuforums.org/showthread.php?t=550304") (Handy little installer that does most of the work for you. Read the script, and it was safe as of the reading. You will still need to do the "upx -d" fix if you are using Gutsy.)
[getlibs]("http://ubuntuforums.org/showthread.php?t=474790") A really cool script that may removed about 45 lines from this how-to.

---

### Post by dfreer on 2007-11-14
Nice Felson! I'll give this a try on a pure gutsy AMD64 install, and if I get around to it I'll do feisty as well.

---

### Post by Felson on 2007-11-14
Perfect.

---

### Post by dennisharrison on 2007-11-15
Alrighty!

First of all, thank you very much for writing this :)

Now, I have followed this to the tee, when I try to execute epsxe (in any fashion)

I get nothing:

No epsxe
No error message
No feedback whatsoever in term
No epsxe in ps aux

Gutsty, binary nvidia drivers, single x screen on two monitors using twin view.

A little confused on where to go from here to try and find something to fiddle with :)

On a side note, I do have pSX running.  Just, missing all the great features from petes graphics plugins!

Any pointers on debugging this thing would be greatly appreciated.

Again, thanks for you time :)

---

### Post by Felson on 2007-11-15
@dennisharrison
Did you do the 
```

sudo aptitude install upx-ucl-beta

cd /path/to/epsxe/
cp epsxe epsxe_bak
upx -d epsxe

```
?
Because what you described sounds exactly like the problem that fixes.

---

### Post by dennisharrison on 2007-11-15
> **Felson said:**
> @dennisharrison
Did you do the 
```

sudo aptitude install upx-ucl-beta

cd /path/to/epsxe/
cp epsxe epsxe_bak
upx -d epsxe

```
?
Because what you described sounds exactly like the problem that fixes.

Worked like a charm :)

Thank you very much!

---

### Post by Felson on 2007-11-15
What OS are you running? you said Gutsy, but is it 32 bit or 64? Just wanting to make sure the problem isn't in both. If it is, then I need to correct my how-to

---

### Post by dennisharrison on 2007-11-15
> **Felson said:**
> What OS are you running? you said Gutsy, but is it 32 bit or 64? Just wanting to make sure the problem isn't in both. If it is, then I need to correct my how-to

This was on 32bit Gutsy.  Sorry, should have mentioned that.

---

### Post by NightCrawler03X on 2007-11-15
Alternative to Felsons guide, you can use my installer. Click here for the thread I posted it on:
[http://ubuntuforums.org/showthread.php?t=550304&highlight=epsxe](http://ubuntuforums.org/showthread.php?t=550304&highlight=epsxe)

Direct link to file:
[http://www.freewebtown.com/franky06/installepsxe.tar.gz](http://www.freewebtown.com/franky06/installepsxe.tar.gz)

```

tar -xf installepsxe.tar.gz
rm installepsxe.tar.gz
sh installepsxe
sudo apt-get install upx-ucl-beta
upx -d ~/epsxe/epsxe

```

This will NOT download the bios, you'll have to do that yourself, as Felson also stated.

I even made this script so that it creates an alias for running epsxe.
Once you've used the installer, exit your terminal then open it again (to register the changes made to ~/.bashrc), then all you need to do is type "epsxe" to run it.

It even downloads all the correct plugins and put everything in the right place for you, all you have to do then is configure them ([guide](http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html))

With my installer, there's also no need to fuss about with permissions because everything is installed to /home/user/epsxe

This installer works on many distributions of GNU/Linux. Though keep in mind that I myself do not support 64-bit GNU/Linux systems in this script. However, the script itself merely downloads everything and puts it in the right places, so if you follow Felsons guide on installing all of the correct libraries for using ePSXe on 64-bit system, you should be fine with my installer.

---

### Post by Felson on 2007-11-15
Thanks. Fixed the how-to. Seems that it didn't matter if it was 32 or 64 bit.

---

### Post by JacksonDane on 2007-11-23
I'm getting black screens loading FFVII (Only game I've tried)

Terminal stops at "Open SPU" and it seems like nothing is happening after that. I've tried every configuration of every plugin it feels like.

Any ideas?

Followed the guide exactly, everything is reporting working and seems installed correctly

I got BIOS

I'm on Gutsy 32bit using a nVidia 7300GS

---

### Post by Felson on 2007-11-23
I haven't tried to play that in quite some time. After I get how from work, I will give it a quick try and see if it has issues for me as well. 
It might be worth it to try PcSX or PSX and see if you have the same kind of problems.

Edit:
For typos

---

### Post by F-3582 on 2007-11-25
You should definitely add a link to SPU Eternal! There's simply no audio plugin that matches its quality, especially after hearing the horrible work PEOpS SPU does with the PSX noise generator :mrgreen: Ever listened to Bahamut's Megaflare sounding like a starting engine in FFIX? Games like Vagrant Story or Xenogears sound horrible, too.

Anyway, SPU Eternal is superior to PEOpS in any aspect and should therefore be included in your guide. I can also provide you with some configuration advice, if you want.

The link you might wanna use is:

[http://www.emuxhaven.net/emuxhaven/psx/plugin/spuEternal141_linux.tgz](http://www.emuxhaven.net/emuxhaven/psx/plugin/spuEternal141_linux.tgz)

---

### Post by F-3582 on 2007-11-26
Oh, I might add that SPU Eternal needs the following command to be entered before trying to install it:

```
sudo aptitude install libstdc++2.10-glibc2.2
```

If it's missing, ePSXe will exit everytime it tries to access the plugins complaining that "/usr/lib/libstdc++-libc6.2-2.so.3" is missing.

---

### Post by Felson on 2007-11-26
@JacksonDane
Sorry I didn't get back to you on the weekend. I couldn't find my CD for that game. I must have lent it out or something (Probably never see it again :p ) Anyway, have you had any luck yet?

@F-3582
Thanks. I will add that one to the How-To once I have a bit of time. (Or when the boss isn't looking :D )

Edit: typos

---

### Post by F-3582 on 2007-11-26
> **JacksonDane said:**
> I'm getting black screens loading FFVII (Only game I've tried)

Terminal stops at "Open SPU" and it seems like nothing is happening after that. I've tried every configuration of every plugin it feels like.

Any ideas?

Followed the guide exactly, everything is reporting working and seems installed correctly

I got BIOS

I'm on Gutsy 32bit using a nVidia 7300GS
Sounds like a bad image/CD to me. "Open spu[0]" is the last thing ePSXe displays before starting a game. Try the "Run BIOS" command and see if ePSXe is at least able to start the BIOS up.

---

### Post by element42 on 2007-11-28
Hi there,
I'm having trouble getting any joypad ePSXe joypad plugins to work. I've followed the guide and everything works nicely except that I dont' get omnijoy or padjoy in the external gamepad config dialog box. I've checked that they're in the plugins folder. Can anoyone help?

thanks!

PS: I know my joypad works because I've used it with zsnes and pcsx (which I would use but I just can't seem to get my games running at the right speed, whereas ePSXe does it right straight off...)

---

### Post by F-3582 on 2007-11-28
Doesn't it work with the standard ePSXe joypad configuration?

---

### Post by element42 on 2007-11-29
no :(

---

### Post by F-3582 on 2007-11-29
Okay, I think the guide doesn't mention that you have to build at least OmniJoy. Are the *.so files directly inside the plugin folder? I don't think that ePSXe recognizes sub-folders in the plugin folder.

---

### Post by element42 on 2007-11-29
ah. got it. should have read the readmes.
have padjoy working nicely now.

thanks!

---

### Post by Felson on 2007-11-29
It looks like a screwed up in my how-to (Will fix it right after I type this.) OmniJoy is a source distribution, so it would need to be build first. If you are on a 64bit OS, I am unsure how to compile 32bit binaries on it. I got lucky in that I already had a copy of them from before my last reinstall. I will tar those up and drop them on my website for download. as for PadJoy, it untared in a sub directory, so do the following to fix that one.

```

cd /usr/local/games/epsxe/plugins/
mv padJoy/bin/* .  
mv cfg* ../cfg/

```

I will post the link to the binary for omni joy in a bit (After I make it)

EDIT:
LOL better late then never.
Sorry I didn't get back to you faster.

---

### Post by Felson on 2007-11-29
Ok, Fixed the these bugs int he how-to, as well as a few others I found when fixing these ones.

The link to get the 32bit binary copies of OmniJoy is [here]("http://www.myte.ca/pub/omnijoy-1.0.0-bin32.tar.gz")

As usual, if you find anymore bugs in this how-to, please let me know.

---

### Post by Felson on 2007-11-29
@F-3582
Added Eternal SPU to the how-to. Thanks. I remember that I used to use that one back in winblows.

---

### Post by Scooter7 on 2007-11-29
Hi,

I've got everything working perfectly except my gamepad.   I'm using a Logitech Dual Action, with the OmniPad plugin.

My problem is that pressing left (or what seems to be left - could be the diagonal left), it 'sticks' - the only game I have for testing right now is FFVII, so it could just be an issue with that game, but I doubt it.   I've run the same game on a different computer with the same gamepad and emulator with no problems, only in Windows.

By 'sticks', I mean the pointer (or the playable character) will repeatedly continue moving in the one direction, unless I move the stick in a different direction.   If I leave the stick in a neutral position, the character moves in the one direction again.

This also happens with the direction pad, although it seems to occur more when I press up.

---

### Post by dfreer on 2007-11-29
@Scooter7
I had this same issue with omnijoy, with the logitech dual action. Try using the padjoy plugin instead.

---

### Post by Felson on 2007-11-29
@Scooter7
There are a few options to fix that. It sounds like your controller has a bit of a "drift" to it. Mine does the same thing. 
Option 1 is to install jscalibrator, run it and set a dead zone. Then cross your fingers and hope that OmniJoy uses your calibration.
Option 2 is to switch to PadJoy (Configure with epsxe first), then edit the "padJoy.cfg" in a text editor and set the "minzero" and "maxzero" to some number higher then the default, try your game, then rinse and repeat until it works right. (mine is minzero = -5000 maxzero = 5000)

---

### Post by F-3582 on 2007-11-29
> **Felson said:**
> @F-3582
Added Eternal SPU to the how-to. Thanks. I remember that I used to use that one back in winblows.
Good. You might also want to add it as an option to the short instructions at the bottom of your guide or else people won't know why they actually downloaded it ;)

---

### Post by Scooter7 on 2007-11-29
Thanks.   Using PadJoy fixed it.   I would have tried it already, but I couldn't find PadJoy before - I must have missed downloading it when I followed your guide.

Speaking of your guide, good job!   It was helpful. ^_^

Btw, I had trouble configuring the joystick with the config gui - for some reason, setting one direction then setting another would clear the one already set.   I had to manually configure it in the config file.   Just a heads-up to anyone who has trouble.

---

### Post by dfreer on 2007-11-29
I'll have to grab my USB controllers and load up ePSXe again, but I know I configured my controllers using the Padjoy GUI. Did you try setting each control twice? Like Map L2 to the joypad's L2, and then immediately map L2 to the joypad's L2 again instead of moving on to R2?
Like I said, I'll try it again here when I get the chance.

---

### Post by Scooter7 on 2007-11-30
> Did you try setting each control twice? Like Map L2 to the joypad's L2, and then immediately map L2 to the joypad's L2 again instead of moving on to R2?

Ahh, no, I didn't.   Now you mention it, though, it seems like the solution.   For some reason ePSXe won't start for me right now (probably OSS and the one-app-using-sound-at-a-time thing), so I can't confirm right now, but I will when I get the chance.

---

### Post by F-3582 on 2007-11-30
> **Scooter7 said:**
> Ahh, no, I didn't.   Now you mention it, though, it seems like the solution.   For some reason ePSXe won't start for me right now (probably OSS and the one-app-using-sound-at-a-time thing), so I can't confirm right now, but I will when I get the chance.
Start ePSXe from command line and see what it outputs. By the way, you can compile PEOpS SPU plugin for ALSA, also. Or start using SPU Eternal right away and select SDL as output.

---

### Post by Felson on 2007-11-30
@F-3582
:) ya, good point. Added to the configuration section.

---

### Post by Scooter7 on 2007-11-30
Thanks - there was a blackout last night, so my computer was off, and I didn't get a chance to try running ePSXe from the terminal, but it runs fine now.   After obtaining the dev libraries for SDL, I have Eternal SPU working.

Arigatou!

---

### Post by Felson on 2007-11-30
I am trying to build a 32 bit version of PEOpS ALSA SPU. I get the .so file just fine, but I can't seem to get the cfgPeopsALSA to compile. Anyone know how too make this work?
To start with, it was filled with DOS files (in a directory called linuxcfg) so I did a good old dos2unix on it. If I run configure, it tells me if can't find an install.sh. If I run make, it can't find gtk.h. libgtk1.2-dev (and 2.0-dev) are installed.
I feel like I am missing something obvious, but for the life of me, I just can't find it. Any help with this would be awesome. If I can get it to compile, I will put a tar in my pub dir, and add it to the how-to.

---

### Post by Felson on 2007-11-30
ok... never mind.... Seems that it uses cfgPeopsOSS with both the ALSA and OSS plugins. Same config file too. Will be adding this to my How-To shortly.
Still can't get it to build the cfg program, but, I don't really need it to ATM, since the one that comes with it seems to work fine so far (at work, so can't test the actual sound).

---

### Post by dfreer on 2007-11-30
> **dfreer said:**
> I'll have to grab my USB controllers and load up ePSXe again, but I know I configured my controllers using the Padjoy GUI. Did you try setting each control twice? Like Map L2 to the joypad's L2, and then immediately map L2 to the joypad's L2 again instead of moving on to R2?
Like I said, I'll try it again here when I get the chance.

The problem, I just tested in ePSXe/pcsx using padjoy, seems to be limited only to mapping the joysticks. Mapping the buttons seem to work normally. Anyways, the actual workaround is like this:

Press the button to map "Up", and then press the joystick up. It should map to the correct axis. Then just press the button to map "Up" **once**. Move on to the next button and repeat.

---

### Post by Kymus on 2007-12-04
Thank you for this how-to!

I'm having a few small problems, however:

1) once I have the BIOS file, how do I move it to the appropriate folder? 
2) how can I add epsxe to the games folder in my applications menu?

---

### Post by F-3582 on 2007-12-04
1.: I'm not sure about the user privileges in the $EPSXE folder. Anyway, if in doubt, just type the following:

```
sudo mv yourbios.bin $EPSXE/bios
```

2.: In the menu System -> Preferences -> Main Menu there's an option called "New Item". Just select the Games category and add the epsxe launcher there.

---

### Post by Kymus on 2007-12-04
> **F-3582 said:**
> 1.: I'm not sure about the user privileges in the $EPSXE folder. Anyway, if in doubt, just type the following:

```
sudo mv yourbios.bin $EPSXE/bios
```

2.: In the menu System -> Preferences -> Main Menu there's an option called "New Item". Just select the Games category and add the epsxe launcher there.
I'll try that, thanks :D

---

### Post by Kymus on 2007-12-04
I did mv *scph1001.bin $EPSXE/bios* and the file did move, but to where I dunno cause I can't find the file in a search, it's no longer in the folder it was in, and it's not in /usr/local/games/epsxe/bios either.

---

### Post by Felson on 2007-12-04
You are going to have a file in your root directory called "bios"
To fix it, just do this.
```

mv /bios /usr/local/games/epsxe/bios/scph1001.bin

```

Edit:
Figure I should explain what happened to ya :)
$EPSXE was a var set in the How-To that would resolved to '/usr/local/games/epsxe/bios'. Once you closed the shell you were working in, it wouldn't have been set anymore. So '$EPSXE/bios' = '/bios'. Since there is no directory in '/' named bios, it would rename your file to bios, and put it in the directory '/'.

---

### Post by Kymus on 2007-12-04
that worked great, thank you :)

---

### Post by F-3582 on 2007-12-04
Shoulda mentioned that, sorry.

---

### Post by Kymus on 2007-12-05
Oh boy, now I'm having more problems. I can't seem to get anything to run correctly. I've configured everything, but, when I try to run a game (from a burned disk) nothing works.. just a big black screen. When I run the BIOS, it's almost the same as well. I get almost a full black screen and then in the upper left corner there's a small square of an area where I can see a bit of the BIOS screen. For the hell of it, I fiddled with the joystick to see if it was responsive and it interacts with the BIOS menu fine, but I just can't see 90% of it :confused:

---

### Post by Felson on 2007-12-05
What plugins are you using, and what are they set to.

---

### Post by Kymus on 2007-12-05
Yanno Felson, I'm glad that one of us here is paying attention :D

I totally forgot that I could switch the video plugin! I 

I changed the video plugin from *P.E.Op.S. SoftX Driver 1.17* to Pete's MesaGL Driver 1.76 and ran the bios and so far so good! I will test out gameplay a little later *crosses fingers*.

---

### Post by F-3582 on 2007-12-05
Looks like you forgot to enable stretching the image to the screen. Which resolution did you use?

EDIT: Did you visit [www.emuforums.com](www.emuforums.com) ? They host the main ePSXe support forum and they might know more than we do here.

---

### Post by Kymus on 2007-12-05
> Looks like you forgot to enable stretching the image to the screen. Which resolution did you use?

oh no, I tried that. I ran it at 640x480 with the P.E.Op.S. SoftX Driver 1.17 in full screen and I got a black screen and when I pushed *escape*, my resolution was all messed up and I was forced to reset :-\

---

### Post by Kymus on 2007-12-05
Alright, I loaded up Alundra (disk burned from an image) and here's what happened:

[LIST]
[*]** P.E.Op.S. SoftX Driver 1.17** goes to a black screen
[*]**Pete's MesaGL driver 1.76** goes to a black screen
[*]**Pete's XGL2 Driver 2.8 **will just crash
[/LIST]

---

### Post by Felson on 2007-12-05
ya, I don't trust the full screen option. Never had much luck with it. What I do, is set the resolution to the same as my screen, and run [this]("http://www.myte.ca/pub/wmctrl_fs_target") script on it. I made an icon on my tool bar to run it. You will also need to make sure you have wmctrl installed.
```

sudo aptitude install wmctrl

```

---

### Post by F-3582 on 2007-12-05
This stuff never happened to me, yet. The only thing I find annoying is the top panel which always gets in the way when switching to 640x480. Interesting thing is that this is the only resolution this happens...

---

### Post by Felson on 2007-12-05
The added bonus of using wmctrl to do fullscreen, is that you can still switch workspaces. Mine is mapped to (ctrl-alt-ArrowKey) to change which one I am looking at. Plus you never have to worry about a crash screwing up your screen res. Some Emulators (eg: Zsnes) even have a "Scale" mode where they stretch the output to what you want automatically.

---

### Post by F-3582 on 2007-12-05
Hmmm... Doesn't seem to work with X Windows. PEOpS SoftX plugin seems to be unaffected by the script.

---

### Post by Felson on 2007-12-05
The plugin shouldn't matter. The script works on any window at all, has nothing to do with ePSXe. (Try your calculator) Remember though, if the res isn't the same as your screen res, all it will do is put it in the top left corner, and get rid of the window controls.

EDIT:
Thought.... Are you using Gnome or KDE for your window manager?

---

### Post by Kymus on 2007-12-05
For the heck of it, I tried to run the same game in PCSX, and it's still giving me that blasted black screen that ePSXe is giving me. Given, PCSX confuses me a bit :confused: but still... arg.

---

### Post by F-3582 on 2007-12-06
> **Felson said:**
> The plugin shouldn't matter. The script works on any window at all, has nothing to do with ePSXe. (Try your calculator) Remember though, if the res isn't the same as your screen res, all it will do is put it in the top left corner, and get rid of the window controls.

EDIT:
Thought.... Are you using Gnome or KDE for your window manager?
Ok, that explains a lot...

Oh, and I use Gnome.

---

### Post by Felson on 2007-12-06
@Kymus
Have you tried not running it fullscreen? I personally have a problem where many standard fullscreen apps won't work with my LCD monitor. For instance, I have to run Regnum in windowed mode, or my monitor goes black. 
@F-3582
Ya, should work fine with Gnome. I am pretty sure KDE would be fine to. some people use different window managers, and I am not sure about those ones.

---

### Post by F-3582 on 2007-12-06
Well, anyway, I don't need it.

I found out that I just have to move my mouse pointer to the bottom and continue until the top panel vanishes from sight.

---

### Post by Felson on 2007-12-06
You could also set the panel to auto hide I would think. Or set it so you can manually hide it. I would "think" that should work too.

---

### Post by Kymus on 2007-12-06
> **Felson said:**
> @Kymus
Have you tried not running it fullscreen? I personally have a problem where many standard fullscreen apps won't work with my LCD monitor. For instance, I have to run Regnum in windowed mode, or my monitor goes black. 

I have tried both, yes. Right now, I'm trying to run everything (in epsxe) in windowed mode, or else it'll just give me an unmanageable black screen of doom :eek:.

---

### Post by Felson on 2007-12-06
the 'esc' key should get you out of the black screen of death if that happens :) . I am at a loss at this point. I would suggest that the MesaGL plugin is probably best. It's the one that works best for me. Take a screen shot of the config screen for that one, and PM it to me so I can take a look at your settings. Print Screen should let you save a screen shot by default. If you can load it into gimp and crop out the rest of your desktop to make it smaller, it would help.

Edit:
Oh ya, what game are you trying to play?

---

### Post by Kymus on 2007-12-06
Hi Felson,

Well, all day I've been fiddling with this thing because Star Ocean on ZSNES, well, I think my copy is a bad dump and it's being funky and I can't beat that game so I want to play a small handful of PSX games I never got to play (Alundra, Lunar 2, Suikoden, Star Ocean) and I'll be damned if I can't play something new :P.

I went over to my windoze partition and tried the disks I burned and... nothing. Ok, that may tell us something. So then, I popped in a commercial disk that I knew worked (Azure Dreams) and it did indeed work. So, more fiddling... I converted the CCD images to ISO and threw the burned CD's in the trash and tried running the ISOs and they all ran! Well, some of them did have a similar black screen upon loading and I knew the bios did, so I went over to my Ubuntu partition and I loaded an ISO and waited......... first darkness, then I see the little FPS bar come up and then the game slowly loaded. It seems  that the problem was that the FPS was too slow and so it got me to believe that it just wasn't working. So, I forced the frame skip and so far everything seems to be going good (*phew* I *hate* using my windoze partition). Thanks for all the help :D.

btw, you wouldn't happen to have a clue as to why I get no audio during FMV sequences in  Lunar, would you? I figured maybe I need to play with the audio plugins maybe :confused: (edit: figured it out :D)

edit: btw, think you can outline for me in noob-speak what I should do with that script you linked to? as I understand it, that will potentially fix the resolution issues I was having with full screen mode?

---

### Post by F-3582 on 2007-12-06
> **Felson said:**
> You could also set the panel to auto hide I would think. Or set it so you can manually hide it. I would "think" that should work too.
Did that until I figured out the mouse "trick". It still left a small portion visible.

Oh, and one more thing: Kymus, you do know that epsxe wants the .img file of CloneCD images, don't you? Anything else will produce black screens. You should of course keep the .sub file for the Libcrypt-protected ones.

---

### Post by Kymus on 2007-12-06
> **F-3582 said:**
> Oh, and one more thing: Kymus, you do know that epsxe wants the .img file of CloneCD images, don't you? Anything else will produce black screens. You should of course keep the .sub file for the Libcrypt-protected ones.

Yeah, it's just that earlier I wasn't able to get it to locate any of the image files. Though now I think I know why. Thanks though :D

---

### Post by Kymus on 2007-12-06
Some people have all the luck.. I don't believe I am one of them.

I've encountered a puzzling problem this time. When playing Lunar 2: Eternal Blue, the game pad will work in the menu and to skip FMV sequences if desired, but once that fades and I get up to a text dialog where I must press a button so that the text will continue... nothing happens.

I've used this same game pad fine just minutes ago playing Alundra and I've re-input the d-pad button configuration numerous times all for naught. I've also tried using the keyboard and that hasn't responded either (though maybe there's something I am not understanding with that?).

If it isn't one thing, it's another :(

---

### Post by F-3582 on 2007-12-07
Some games don't support analog pad mode. Try switching to digital mode.

---

### Post by Kymus on 2007-12-07
Thanks for the feedback

It was already set to digital, so I tried switching it to analoge, and still no luck :(

---

### Post by Sarteck on 2007-12-10
Hey, just installed using your guide.  :)  THere were a few things off, though.
First, the line ```
wget http://www.pbernert.com/gpupeopssoftsdl116.tar.gz
``` is totally missing.  I am sure it's supposed to be there, because you tell us this:```
sudo tar xfz gpupeopssoftsdl116.tar.gz -C $EPSXE/plugins/
```No biggie, easy to figure out, but I thought you'd want to know so you can fixt it.



Next was```
rm -rf padJoy
```I don't know about anyone else, but I had to add "sudo" in order to do this, else I got "Permission denied."  The same thing with these two lines:```
cp epsxe epsxe_bak
upx -d epsxe
```I needed to "sudo" them both as well.

{These were all on Kubuntu Gutsy, AMD64, of course.}



One thing I was going to ask...  Is there an "official"-type Icon for ePSXe?  If so, I was going to use it for the link on my K-Menu.

---

### Post by Kymus on 2007-12-10
> **Sarteck said:**
> One thing I was going to ask...  Is there an "official"-type Icon for ePSXe?  If so, I was going to use it for the link on my K-Menu.

There is for the Windoze version, I know. Dunno if that helps much though :P

---

### Post by Sarteck on 2007-12-10
Well, mebbe I can google it somewhere, it's not really a big deal, heh.

However, I was going to ask the OP (and anyone else who might know for that matter) if I would have to jump through hoops and hurdles to install ePSXe 1.52 alongside ePSXe (and just execute using the commandline "epsxe152").

The reason I ask is because, after reading several posts in other forums, I have learned that FF7 will actually run better in the old version than 1.60.

I'll see if I can do it myself first, and post my results here if I'm able to.  :)

---

### Post by Sarteck on 2007-12-10
Yep!  It worked.  :)  I basically followed the exact same instructions the OP gave, renaming epsxe to epsxe152, used the upx command, created the file in /usr/local/bin, and chmodded it.  It works great!  (And, yes, FF7 in 1.52 -does- run more smoothly, particularly the post-battle sequence, which was getting slowed up in 1.60.)

---

### Post by Felson on 2007-12-11
@Sarteck
Hey. Thanks for the bug report. I fixed those. Also, I lifted the icon from the Winblows executable. You get get it [here]("http://www.myte.ca/pub/epsxe.png"). I never asked if this was ok, so I may have to remove this link if someone complains.
As for epsxe 1.52, I think I may add that to my How-To at some point. It seems to be the standard fix for a few games.

---

### Post by Sarteck on 2007-12-11
Hey, great!  The icon's just what I needed.  ^_^

And thanks for the FAQ...  I thought pSX was cool, since I didn't have to do any tweaking, but when I tried ePSXe, I was completely stunned by the difference in graphics.  :D So this FAQ == "teh cool."

---

### Post by Felson on 2007-12-11
:) Thanks. Glad I could help.

---

### Post by ACLBandit on 2007-12-11
> **Felson said:**
> @dennisharrison
Did you do the 
```

sudo aptitude install upx-ucl-beta

cd /path/to/epsxe/
cp epsxe epsxe_bak
upx -d epsxe

```
?
Because what you described sounds exactly like the problem that fixes.

Ah, I was terrified that my ePSXe was broken forever, so thanks a bunch. I would have been quite sad if I had no emulation.

Out of random curiosity, what is upx -d? It worked, but I don't know precisely what it did?

---

### Post by Felson on 2007-12-12
@ACLBandit
UPX is a program to compress executables and still have them run without having to decompress them. Turns out there is a bug in Gutsy in regards to those compressed executables. the "upx -d" extracted the real executable from the compressed file. If you look at epsxe_bak VS your new epsxe you will see a fairly major size difference.

---

### Post by whitesky on 2007-12-12
When I try to play a game it doesn't load and it appears:

> * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(141,20,9) read ioctl failed (25)
CD(141,20,10) read ioctl failed (25)
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsSoftX.so.1.0.17] 
 * Open gpu[0] 
CD(0,2,16) read ioctl failed (25)
CD(0,2,0) read ioctl failed (25)


Can someone help me? I have no idea how to fix it.

---

### Post by Felson on 2007-12-13
@whitesky
Need a better definition of "Doesn't Run". 
Are you getting a black screen?
I see you are using the Soft GPU, so how long did you wait? It could take a while before a screen comes up. And by a while, I mean a really LONG while, depending on your settings. 
What are your settings in your GPU (Video Plugin)?
Have you tried running the game with pSX? It's always a good double check to make sure you don't have a bad copy of the game that way.

EDIT:
Oh ya, What are your hardware specs? CPU Speed, Memory & Video Card.

---

### Post by whitesky on 2007-12-13
My screen gets transparent... I just move it around the screen and everything behind the window appears.
I waited four 5 minutes maximum, nothing happened.
I don't know how to see my settings on my GPU. How do I do this?
I tried running pSX and another copy of epsxe too, same error.

ASUS A7V8X-X
GeForce FX 5200 128MB
768RAM 333Mhz Samsung
AMD Athlon XP 2400+
Ubuntu 7.10

---

### Post by Felson on 2007-12-13
@whitesky
If pSX didn't run it, there is a good chance that the game doesn't work. That aside, looking at your hardware, it would be a good idea to switch the GPU to the MESAGL plugin, since your Video card will support Open GL for sure. Much much faster then software rendering. 
To change your Video plugin goto
Config->Video
Click the "Down Arrow" and pick "Pete's MesaGL Driver"
to configure it, click the "Configure" button

Under the "Special Game Fixes" you generally don't want anything checked, unless the game you are trying to use is listed in there.
Under "am size", since you have a 128MB Video card, set it to 128
From there, you are going to have to play with setting on your own. The one bit of advice I can give here though, is to start low and work your way up.

---

### Post by whitesky on 2007-12-13
Well, I left the window opened and loading the game with the configuration you gave me for 30 minutes and nothing happened.

That's really strange because I remember of playing epsxe on Ubuntu 5.10 some months ago.

---

### Post by F-3582 on 2007-12-13
Maybe whitesky's a hardcore retro PSX nerd just like me. Looking at his CPU it is pretty certain that PEOpS SoftX driver should run without problems.

Anyway, it looks like your CD is defunct. Did you try making an ISO? The easiest way to test if the CD is recognized correctly would be the -slowboot command line option. Unfortunately it doesn't seem to work with the Linux ePSXe version...

---

### Post by whitesky on 2007-12-13
I made it... Finally.
Not with epsxe, but with pSX... The problem was the bios, it had a windows virus inside and not worked like it was supposed to.

Thank you very much anyway, people.

And I'm not a hardcore nerd, haha.. But almost becoming one.

---

### Post by -MoonDoggie- on 2007-12-15
thought i might inform that the dfreers link on the first page is broke. page doesn't load. also a quick ?:

i'm a total noob at linux and the Terminal still. with that in mind, is all that suppose to be done is copy and paste the code from the first page in the termial window?

Edit: ok, got passed a portion of my terminal noobness and got epsxe working. thanks for the guide felson. and thanks to dfreer for looking into the site problem. you guys rock.

---

### Post by dfreer on 2007-12-16
> **-MoonDoggie- said:**
> thought i might inform that the dfreers link on the first page is broke. page doesn't load.

Thanks for the info MoonDoggie... as of right now, the website should be accessible, I'm currently looking into why it went down in the first place. Sorry about that :(

EDIT: Still working on the cause, but I highly suspect the problem lies within ddclient. Anyways, if anyone is having further problems with the dfreer.org site, please just send me a PM or post in the following thread, so that we don't clutter up this one ;) :
[http://ubuntuforums.org/showthread.php?t=432642](http://ubuntuforums.org/showthread.php?t=432642)

---

### Post by @vijay@ on 2008-01-20
i have installed everything need but still cant see the menus in epsxe

---

### Post by Felson on 2008-01-21
Can you describe what you see when you try and run it? also try running it from a terminal and see what output you get.

---

### Post by Kecman87 on 2008-01-24
hi, i installed epsxe, just like you described in first page in first comment. it works but it has some kind of glitch...skippin' 2 the problem:-> sometimes epsxe shutdown itself (e.g. in the middle of a game),and then it put me back to desktop with epsxe closed, like i've never started it... why?

---

### Post by Felson on 2008-01-24
I have never seen that before. It sounds like it might be seg-faulting. Try running it from terminal to see what the output is when in crashes. Then maybe we could narrow it down a bit.

---

### Post by Kecman87 on 2008-01-25
i've found that a rom was causing that kind of program shutdown. rom was bad. with other rom (iso) working, epsxe works just fine.

---

### Post by F-3582 on 2008-01-25
By the way: In case someone already upgraded to Hardy, he/she will have noticed that ePSXe has stopped working if spuEternal is installed. The reason is that Hardy doesn't include libstdc++2.10-glibc2.2 anymore, partially because GCC 2.95 has been failing to build from source since Feisty. Anyway, at the moment the only choice you have is installing the Gutsy deb found [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fg%2Fgcc-2.95%2Flibstdc%2B%2B2.10-glibc2.2_2.95.4-24_i386.deb&md5sum=b2da87d562dc2078c8244e980a4722b4&arch=i386&type=main"). A bug report has already been [filed]("https://bugs.launchpad.net/ubuntu/+source/gcc-2.95/+bug/185698").

---

### Post by MagicTom on 2008-01-27
There hasn't been much talk in this thread about Analog stick support.  Onmijoy doesn't seem to support it at all, and while padjoy has a box to enable analog support, my analog sticks aren't working at all in any game I try.  One of which is Final Fantasy 8, which most certainly supports it.  Running 'jstest', my analog sticks work quite well, and ePSXe under windows with a different pad plugin works fantastically.

Has anyone else gotten this to work?

(Another funny glitch: ePSXe somehow turns my keyboard repeating off.  For example, I can't hold down backspace and have it delete any more than one character without releasing it and pressing it again.  Does anyone know of something I can add to the epsxe launcher script to restore that functionality once the emulator is turned off?)

---

### Post by Felson on 2008-01-27
No idea about the keyboard, but for the joystick, try setting padjoy to think it's using PCSX instead of ePSXe. I have heard that it "helps" but don't quote me on it later :p

---

### Post by civilized on 2008-01-28
Hey guys I need a little help... Sorry if this has been solved I've been searching but couldn't find anything I installed epsxe loads up but when I start from CDROM I get an error

```

 * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/civilized/epsxe/bios/erase.me].
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
                                                         Error: couldn't get fbconfig
     Segmentation fault (core dumped)

```

any thoughts thanks

---

### Post by F-3582 on 2008-01-28
You aren't running Compiz via XGL by any chance, are you?

---

### Post by Felson on 2008-01-28
You don't have a BIOS file. You need that to run the emulator. Unfortunately, I can not tell you where to get one.

---

### Post by civilized on 2008-01-28
ok I got a bios but still having the error

```
* Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/civilized/epsxe/bios//SCPH1001.BIN].
 * Init internal cdrom ... ok
 * First/Last track: 1 1
 * Track 1:  (DATA) - Start 0: (00,02,00)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
                                                         Error: couldn't get fbconfig
     Segmentation fault (core dumped)

```

---

### Post by F-3582 on 2008-01-28
And you still didn't give me an answer regarding XGL. Are you running Compiz or Beryl via XGL? If yes, this is the problem. If not, tell us, please, which graphics card you you have and which drivers are you using.

---

### Post by civilized on 2008-01-28
Hi sorry I didn't see your post Yes I am running Compiz and XGL my video card is the Raedon X700 Mobile do I have to stop compiz to run the epsxe??

---

### Post by F-3582 on 2008-01-28
Well, you have to stop XGL entirely in order to make this work. The only problem: I really don't know how to do that in newer versions of XGL. And I don't know which version of Ubuntu you are using. You might wanna do some research yourself ;)

---

### Post by civilized on 2008-01-29
i'll have a look i'm on 710 Gusty thanks for the help

---

### Post by Zzzach on 2008-02-01
I'm having the same problem and I'm running compiz too. I try loading an iso and epsxe just disappears. :confused:

---

### Post by F-3582 on 2008-02-01
You should look for two things: Are you running XGL? If yes, this might be your problem. If not, start ePSXe from console and post the error message here.

---

### Post by civilized on 2008-02-04
Can anyone help me out with thes bios problem??
```

civilized@civilized-laptop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/civilized/Documents/bios/Scph1001.bin]. 
 * Loading ISO Format  * Closing ISO system. 
 * Error loading cdrombin [/usr/local/games/epsxe/bios/scph1001.bin]

```

---

### Post by F-3582 on 2008-02-05
What did you try to do? Loading a BIOS file as CDROM image is apparently a bad idea. If you want to run the BIOS directly, select the "Run BIOS" command.

---

### Post by civilized on 2008-02-05
I don't know what I did I was just trying to config the bios under the config option so I can load an ISO but I keep getting an error saying config bios...

---

### Post by F-3582 on 2008-02-05
Well, according to the terminal output the BIOS has been found and got loaded correctly. The last line, however, indicates that you tried to load another BIOS image as CDROM image which is pretty moch nonsense, because CDROM ,bin images have absolutely nothing to do with BIOS .bin images.

---

### Post by civilized on 2008-02-05
How do I fix that??

---

### Post by Felson on 2008-02-05
Try loading a real game. It looks like you are trying to run the BIOS as a CD image.

---

### Post by F-3582 on 2008-02-05
What did you do to produce this error? Please disclose all steps as detailed as possible.

---

### Post by civilized on 2008-02-05
I think I was doing a config on the bios and was actually doing the CDrom and now I don't know how to put it back to normal and I also configed the bios correct but when I try to run an ISO it says I still need to config the bios witch I already did

---

### Post by @vijay@ on 2008-02-06
why can't i see menu items in epsxe ; 
here is the screenshot ; i have followed every thig in this guide ;
im running gutsy

edit:
sorry added the screenshot

---

### Post by F-3582 on 2008-02-06
Screenshot please.

---

### Post by @vijay@ on 2008-02-06
u can see the terminal output; it shows no error

---

### Post by Koiti on 2008-02-07
It seems like your system is missing some fonts, I guess, or maybe the gtk engine isn't being able to display them.

Anyway, for anyone having problems to make the Eternal SPU Plugin work in a Gutsy x86_64 environment because the "libSDL.so" is missing in /usr/lib32, I attached the file in this post.

Strangely, I couldn't install it from the repos (downloaded a i386 version) using the commands "sudo dpkg -x "name of.deb" ." and moving the file to /usr/lib32. The file wasn't extracted when I made this input. It just kept deleting itself over and over :confused: , so I had to copy it from another machine running a 32bit version of Gutsy, and it worked flawlessly.

:guitar:

Cheers from Japan.

---

### Post by @vijay@ on 2008-02-07
hmmm; is there anyway to fix it ; and i installed my gutsy recently ;
so i haven't messed with it :lolflag: , that much to cause the problem

---

### Post by F-3582 on 2008-02-08
> **Koiti said:**
> It seems like your system is missing some fonts, I guess, or maybe the gtk engine isn't being able to display them.

Anyway, for anyone having problems to make the Eternal SPU Plugin work in a Gutsy x86_64 environment because the "libSDL.so" is missing in /usr/lib32, I attached the file in this post.

Strangely, I couldn't install it from the repos (downloaded a i386 version) using the commands "sudo dpkg -x "name of.deb" ." and moving the file to /usr/lib32. The file wasn't extracted when I made this input. It just kept deleting itself over and over :confused: , so I had to copy it from another machine running a 32bit version of Gutsy, and it worked flawlessly.

:guitar:

Cheers from Japan.
libSDL.so is inside libsdl1.2-dev for some strange reason. I already filed a bug about it, but no one seems to care.

---

### Post by Koiti on 2008-02-08
> **F-3582 said:**
> libSDL.so is inside libsdl1.2-dev for some strange reason. I already filed a bug about it, but no one seems to care.

[-X

The library inside this package is an x86_64 type. Symlinking didn't work. I had to use an i368 instead.

@vijay@

About the fonts, I just took another look in your screenshot and noticed that you "may" be using some different fonts/encoding because of your native language (Hindi?). Is your Ubuntu running in english?

Cheers

---

### Post by @vijay@ on 2008-02-08
yes its in english only;

---

### Post by Koiti on 2008-02-09
Now this is weird.

Try installing some packages to configure the gtk apps (gkt-theme-switch) and changing the fonts displayed.

Cheers.

---

### Post by F-3582 on 2008-02-09
Note that ePSXe is a Gtk1.2 app.

---

### Post by @vijay@ on 2008-02-09
i have already installed the required gtk 1.2 libraries
see the screenshot

and i also tried changing the font with gtk-theme-switcher2
but no use;which font should i select any idea;
and just for the info i haven't changed the default font after installation

---

### Post by ZOOstation on 2008-02-14
"upx: command not found"

help?

---

### Post by Felson on 2008-02-14
```

sudo aptitude install upx-ucl-beta

```

If you did that before, what does it return?

---

### Post by ZOOstation on 2008-02-14
Nevermind, it worked today. Weird. Sometimes I think I just shouldn't code at night.

Thanks for the howto: much more appropriate to my system than the previous.

---

### Post by ZOOstation on 2008-02-14
Okay, FF8 is pulling up a black screen. The BIOS runs fine. Here's what the terminal has to say when I try to run the CD:

```
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(174,47,17) read ioctl failed (25)
CD(174,47,18) read ioctl failed (25)
 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
ATI Technologies Inc.
ATI MOBILITY RADEON X600
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
 * Open spu[0] 
CD(0,2,16) read ioctl failed (25)
CD(0,2,0) read ioctl failed (25)

```

---

### Post by F-3582 on 2008-02-15
Hmm... I don't remember FF8 having audio tracks. Are you sure this is the right CD? Anyway, if yes (originals do best, by the way), try two things:

- Enable Subchannel reading and caching (FF8 uses an additional copy protection called Libcrypt which relies on bogus subchannel data)
- Try making an ISO (which will make the game much more playable, by the way)

---

### Post by Koiti on 2008-02-15
> **F-3582 said:**
> 
- Try making an ISO (which will make the game much more playable, by the way)

I'll second that.

Still trying to figure out why the fonts doesn't show with the other guy.

Weird...

---

### Post by ZOOstation on 2008-02-15
> **F-3582 said:**
> - Enable Subchannel reading and caching (FF8 uses an additional copy protection called Libcrypt which relies on bogus subchannel data)

How? (i'm = n00b)

Yes, it's the original CD. I'll get on the ISO thing pronto.

---

### Post by F-3582 on 2008-02-15
Subchannel reading and caching can be enabled in the ePSXe CDROM options (Configure -> CDROM). Most games that don't display that green "The unauthorized reproduction of all or any part of..." nag screen need that option.

---

### Post by ZOOstation on 2008-02-15
Config --> Cdrom doesn't have any options for me. Just an input line to specify the device location. Then the OK and Cancel buttons.

---

### Post by ZOOstation on 2008-02-15
UPDATE: Used genisoimage. The created ISO still produces just a black screen.

```
* Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
ATI Technologies Inc.
ATI MOBILITY RADEON X600
 * Open gpu[0] 
 * Init spu[0][libspuPeopsOSS.so.1.0.9] 
 * Open spu[0] 

```

Then nothing. Can't even disable the stupid text at the top (frame rate, etc.).

---

### Post by ZOOstation on 2008-02-17
New research shows this response to all my PSX games. I hadn't thought to try other games because I wasn't planning on playing any other games. But their discs and ISOs get the same respective inactivity.

---

### Post by F-3582 on 2008-02-18
Sorry about that config thing. I had forgotten that ePSXe had this only in Windows.

Anyway, did you try any other programs to make those images? It is highly important that you make that program read the subchannel data. Dunno if genisoimage is the right software for this.

---

### Post by ZOOstation on 2008-02-18
Any other ways of activating subchannel reading? And what iso program would you suggest?

---

### Post by F-3582 on 2008-02-18
Actually, had always used CloneCD for this job... And in the last two years while I've been using Linux, there weren't any new games to make ISO files of.

---

### Post by Felson on 2008-02-18
If you are having problems with more then just 1 game, my guess is that it isn't the image. I would sugest that you try PcSX and PSX projects and see if they work while this one doesn't. If they do, It may be time to play with the plugins. It might be worth your while to try a software rendering plugin to see if it might be an issue with your video.

---

### Post by F-3582 on 2008-02-18
He said that the BIOS screen ran fine. This must be a CDROM issue.

Did you try asking a friend to make a CloeCD image of one of those CDs. Your drive might not be able to extract those CDs properly. Don't forget to activate subchannel reading.

---

### Post by ZOOstation on 2008-02-18
I made a CloneCD and it didn't do anything differently. I didn't find any instructions how to make an ISO using CloneCD, so I tried Alcohol120%. Again, no success. The filetype attached to it is .mdf, but I read that it's the same thing as an iso. Any advice? Please give directions to creating ideal iso files if necessary. Maybe I will investigate other emulators.

This is so damn frustrating.

---

### Post by F-3582 on 2008-02-19
Do you see those profiles when making an image? Either edit one of them or make a new one. The most important part is the Data track options which contains the subchannel settings. ePSXe can then read the produced .img file. And don't forget to put the .sub file into the same directory.

---

### Post by ZOOstation on 2008-02-23
Took Felson's advice. pSX works like a charm. Case closed.

---

### Post by miansaab on 2008-02-23
Hi,

I am getting the following error when I try to run ePSXe:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

During the installation progress, when I pasted the following line:

sudo aptitude install ia32-libs lib32glib1.2 lib32gtk1.2

The terminal just stood at the following line and didn't move forward:

0% [Connecting to packages.dfreer.org (71.127.72.162)]

Is there any other way to get those files?

Thanks

---

### Post by Felson on 2008-02-25
Try changing which mirror you are using to get your packages. I have to do that sometimes as well.

---

### Post by Elrian on 2008-02-27
Hello,

I tried to create a launcher for ePSXe in the gnome panel adding  a new item and typing epsxe in the command box but it doesn't work nothing happens when i start it that way...

Note that typing epsxe in the terminal as user works though...

Also as user i cannot launch epsxe in the install directory by double-clicking it but i can as root (with sudo nautilus)... I don't know if it has anything to do with it...

Can someone help me with my launcher issue?

Thanks

PS: Im on Gutsy and i did the upx -d  step

---

### Post by Felson on 2008-02-28
Try creating a shell script to do it like this:

```

#!/bin/bash

export EPSXE='/usr/local/games/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe -analog

```
Then create a shortcut to the script instead. This is the one I use myself. Remove the "-analog" if you don't have an analog game pad.

---

### Post by Elrian on 2008-02-29
> **Felson said:**
> Try creating a shell script to do it like this:

```

#!/bin/bash

export EPSXE='/usr/local/games/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe -analog

```
Then create a shortcut to the script instead. This is the one I use myself. Remove the "-analog" if you don't have an analog game pad.

I did that still doesn't work... forgot to mention i use epsxe 1.5.2 not 1.6.0 (with which the launcher works...)...

---

### Post by Felson on 2008-02-29
Shouldn't matter if it's 1.5.2 or 1.6 really. I am at a loss now though. The only issue I had with it was a pathing issue before, which is why I made the script.

---

### Post by Elrian on 2008-02-29
> **Felson said:**
> Shouldn't matter if it's 1.5.2 or 1.6 really. I am at a loss now though. The only issue I had with it was a pathing issue before, which is why I made the script.

I reinstalled my entire system still cannot launch epsxe 1.5.2 as user via nautilus only via the console or as root...

---

### Post by dfreer on 2008-03-01
> **miansaab said:**
> Hi,

I am getting the following error when I try to run ePSXe:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

During the installation progress, when I pasted the following line:

sudo aptitude install ia32-libs lib32glib1.2 lib32gtk1.2

The terminal just stood at the following line and didn't move forward:

0% [Connecting to packages.dfreer.org (71.127.72.162)]

Is there any other way to get those files?

Thanks

This is an error on my end. Firstly, the site has been up/down periodically the last month. Secondly, due to my new ISP who blocks port 80, you'll need to edit one line in your /etc/apt/sources.list from this:
```
deb http://packages.dfreer.org gutsy main
```
to this:
```
deb http://packages.dfreer.org**:8080** gutsy main
```

No need to re-download the GPG key. You can also download the .deb files you need using HTTP:
[http://packages.dfreer.org:8080/pool/gutsy/main/binary-amd64/lib32/](http://packages.dfreer.org:8080/pool/gutsy/main/binary-amd64/lib32/)

Finally, if neither of those options sound good to you, I can post any requested packages in the forums here. Just let me know what you need.

EDIT: @ Felson - You might want to change the link on the front page to this:
[http://packages.dfreer.org:8080/#secondary_main_column](http://packages.dfreer.org:8080/#secondary_main_column)

---

### Post by Felson on 2008-03-03
@dfreer
Thanks. I forgot about that.

@Elrian
IF it will start via console, but not by the script I gave you, there is probably some environment variable that it is expecting that it isn't finding. Not really sure how that is possible though. I am also not sure which ones it would be. To add an environment variable to the script do the following:

```
VARIABLE=value of var; export VARIABLE
```

To see what ones are set in your console, type
```
env
```

I would go through and see what is in your environment. I would start with "LANG" and "PATH" after that, I have no idea.

---

### Post by DoktorSeven on 2008-03-09
Any Hardy users having an issue running ePSXe?  Trying to run it just gives me the prompt back:

```

$ ./epsxe
$

```
It worked fine on this system in Gutsy.  Even a clean download of ePSXe doesn't work at all.

And don't tell me to use pSX, please.  I have several issues with that emulator that puts me off of it.

Edit: never mind, upx got me going.  Odd thing is that I didn't have to do that on Gutsy at all, epsxe worked just fine out of the box there.

---

### Post by F-3582 on 2008-03-09
Read the first post of this thread. There's a passage reading "For Gutsy users:" with a few lines of code afterwards. This applies on Hardy, as well, although you might have to install upx-ucl instead of the beta (it has gone stable, in the meantime).

Apparently, ePSXe has to be unpacked with upx, first.

---

### Post by Felson on 2008-03-10
@F-3582
Added that to the how-to now. 

Can anyone confirm that this how-to is 99% or better in Hardy? I don't use that yet, so can't confirm myself.

---

### Post by rf277 on 2008-03-11
sorry i'm kinda new to ubuntu, but i did your whole install process and it starts up just fine, but when i go to configure the video, it just closes, no error or anything, it just closes, could you tell me why and how to fix it, thanks :D

---

### Post by Felson on 2008-03-11
Run from the terminal, and post any terminal messages you might get here. There could be something useful in there.

---

### Post by StateS on 2008-03-22
> **dfreer said:**
> This is an error on my end. Firstly, the site has been up/down periodically the last month. Secondly, due to my new ISP who blocks port 80, you'll need to edit one line in your /etc/apt/sources.list from this:
```
deb http://packages.dfreer.org gutsy main
```
to this:
```
deb http://packages.dfreer.org**:8080** gutsy main
```

No need to re-download the GPG key. You can also download the .deb files you need using HTTP:
[http://packages.dfreer.org:8080/pool/gutsy/main/binary-amd64/lib32/](http://packages.dfreer.org:8080/pool/gutsy/main/binary-amd64/lib32/)

Finally, if neither of those options sound good to you, I can post any requested packages in the forums here. Just let me know what you need.

EDIT: @ Felson - You might want to change the link on the front page to this:
[http://packages.dfreer.org:8080/#secondary_main_column](http://packages.dfreer.org:8080/#secondary_main_column)

Hi, would it be possible for you to upload the i386 files of psx for gutsy to rapidshare or something and post the link here? I am unable to access your server :S

Thanks in advance :)

---

### Post by StateS on 2008-03-22
never mind, I found a post of yours with the files as an attachment. Sorry bout that. Thanks for uploading them, and sorry for not searching in the forums before asking... whoops :)

---

### Post by ASULutzy on 2008-03-25
I can not get epsxe working in my clean install of 64 bit hardy. It was working in 32 bit gutsy.

ryan@ryan-desktop:/$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ryan@ryan-desktop:/$ epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
ryan@ryan-desktop:/$

---

### Post by woahitsmatt on 2008-03-25
> **ASULutzy said:**
> I can not get epsxe working in my clean install of 64 bit hardy. It was working in 32 bit gutsy.

ryan@ryan-desktop:/$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ryan@ryan-desktop:/$ epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
ryan@ryan-desktop:/$

I have the same issue.

---

### Post by dfreer on 2008-03-26
> **ASULutzy said:**
> I can not get epsxe working in my clean install of 64 bit hardy. It was working in 32 bit gutsy.

ryan@ryan-desktop:/$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ryan@ryan-desktop:/$ epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
ryan@ryan-desktop:/$

It's likely that the problem here is that you have installed the 64-bit gtk library, and what is required is the 32-bit gtk library. Since ePSXe is a 32-bit application it will use the 32-bit libraries. 

You can try using the package that I have attached to this post, it may require additional dependencies (if it does just let me know and I'll grab them for you).

---

### Post by Felson on 2008-03-27
Try the part of the How-To for "Gutsy64". That may be what you are missing.

---

### Post by xjgnsdof on 2008-03-30
I get this when trying to set my Logitech Dual Action controller:

padJoy: could not open /dev/input/js0, errno=2
padJoy: no useable input received

Any ideas?

---

### Post by captain candy on 2008-04-03
Could someone kindly upload lib32glib1.2 since who knows when defreers rep will be back up? I can't get epsxe running without it...

---

### Post by dfreer on 2008-04-04
I know when it's coming back up :D

Here's the file:

---

### Post by captain candy on 2008-04-04
Thanks! I really appreciate it.

---

### Post by jlacroix on 2008-04-05
Going into the configuration crashes pSX for me every time. I tried deleting the ini file. Here is the output:

```
(pSX:6702): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(pSX:6702): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(pSX:6702): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6702): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6702): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6702): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6702): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6702): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6702): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6702): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6702): Gtk-WARNING **: Error loading theme icon 'gtk-delete' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(pSX:6702): Gtk-WARNING **: Error loading theme icon 'gtk-delete' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
pad=0

(pSX:6702): GdkGLExt-WARNING **: Cannot open 

(pSX:6702): Gtk-CRITICAL **: gtk_image_set_from_pixbuf: assertion `pixbuf == NULL || GDK_IS_PIXBUF (pixbuf)' failed

(pSX:6702): Gtk-CRITICAL **: gtk_image_set_from_pixbuf: assertion `pixbuf == NULL || GDK_IS_PIXBUF (pixbuf)' failed

(pSX:6702): Gtk-CRITICAL **: gtk_image_set_from_pixbuf: assertion `pixbuf == NULL || GDK_IS_PIXBUF (pixbuf)' failed

(pSX:6702): Gtk-CRITICAL **: gtk_image_set_from_pixbuf: assertion `pixbuf == NULL || GDK_IS_PIXBUF (pixbuf)' failed
Segmentation fault (core dumped)

```

---

### Post by knegil on 2008-04-08
Getting an error when I try to run bios or cd-rom, I have a bios, and I get the same error with all video drivers.

```
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/home/knegil/Downloads/BIOS PSX/SCPH5000.BIN]. 
 * Init gpu[0][libgpuPeteMesaGL.so.1.0.76] 
Tungsten Graphics, Inc
Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
 * Open gpu[0] 
plugins/libspu.so: cannot open shared object file: No such file or directory 

```

---

### Post by F-3582 on 2008-04-08
Looks like your problem lies within he SPU. Which SPU plugin are you using?

---

### Post by andycapps on 2008-04-11
epsxe isn't able to see my plugins, how can i direct it in where to look for the plugins? i can get to the bios find, since you browse for it; but when I  go configure-->video (audio, etc), it doesnt show any possible plugins

---

### Post by Flaming Helios on 2008-04-12
Well I got everything to work except my controller I have installed OmniJoy now when I go to configure I get Error Opening Device /dev/js0 Please double check yourself! Any way o fix this?

---

### Post by choujin7 on 2008-04-12
great guide and great emulator

---

### Post by skinnie on 2008-04-16
I just did everything in this guide but I get this message when tryping epsxe in the console:
bash: /usr/local/bin/epsxe: Permissão negada (in english something like not permited)
what can I do?
I am using Ubuntu 8.04 32bits

---

### Post by Felson on 2008-04-16
try 
```

sudo chmod 755 /usr/local/bin/epsxe

```

---

### Post by kaens on 2008-04-16
Hey, first off many thanks to Felson for this little guide - made getting epsxe a snap, didn't have to fiddle around forever.

Quick addition though - adding ```
$*
``` to the epsxe launch script right after the call to epsxe will pass any command line args to epsxe (say that 10 times fast).

This is useful when you need to fiddle with epsxes settings a bit - for instance, the infamous ff9 dali FMV crash can be gotten around by turning off the frame limiter in the video plugin, and starting epsxe with ```
epsxe -fl
```.

There are a ton of command line switches, viewable through```
epsxe -help
``` that can be rather invaluable.

Again, thanks!

---

### Post by adlin5000 on 2008-04-16
Followed the instructions and everything seemed fine until:

```
sudo aptitude install libgtk1.2-common libgtk1.2 libstdc++2.10-glibc2.2
```

It seems there is no libstdc++2.10-glibc2.2 for Hardy. I tried continuing without it and it worked until I tried to open the configs, then it crashed saying:

```
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

any help with this? I'm running Hardy 32bit btw.

Thanks.

---

### Post by Felson on 2008-04-17
@kaens
Thanks, that is a bash variable I was trying to remember not 3 days ago for another little script. Will add that.

@adlin5000
Sorry, I haven't installed Hardy on any computers so far, So I have no idea what is in the repos. All I can suggest, is to search the repos for the stdc++ stuff, and see if it is installed/renamed. If you find it, rerun the gtk stuff, and try again.

---

### Post by skinnie on 2008-04-17
> **Felson said:**
> try 
```

sudo chmod 755 /usr/local/bin/epsxe

```

it works now..thank you :D

---

### Post by adlin5000 on 2008-04-22
Well I answered my own question. The problem is that libstdc++2.10-glibc2.2 has not been able to compile on the last two versions and they decided to drop it from Hardy. So if you want to run anything (namely the Eternal SPU) you have to install it manually. 


You can get the package here:

```
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
```

I installed it by using GDebi package installer, maybe someone can post the commands to install it.

64bit versions should be ok because they have to install it manually anyway.

---

### Post by Uruz on 2008-05-01
Hey, I'm running Gutsy Gibbon 7.10 and am a bit of a noob.

I've tried both tutorials and neither of them worked, I have all the stuff but when I type ePSXe in the console nothing happens. Going and clicking the icon for the program does nothing either.

Sorry to be a bother...

---

### Post by -siGGi- on 2008-05-02
i'm on ubuntu 8.04:

this is what i get when i want to run a cd-rom or iso:

```
siggi@desktop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN]. 
 * Loading ISO Format [NRG2336] ok
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsSDL.so.1.0.16] 
/usr/local/bin/epsxe: line 6:  6306 Segmentation fault      ./epsxe $*
```


i pasted this in terminal to install epsxe on ubuntu 8.04:
```
sudo aptitude install unzip
cd ~
mkdir ePSXe_install
cd ePSXe_install
wget http://www.epsxe.com/files/epsxe160lin.zip

wget http://www.pbernert.com/gpupetemesagl176.tar.gz
wget http://www.pbernert.com/gpupetexgl208.tar.gz
wget http://www.pbernert.com/gpupeopssoftx117.tar.gz
wget http://www.pbernert.com/gpupeopssoftsdl116.tar.gz

wget http://www.myte.ca/pub/spupeopsoss-alsa109.tar.gz
wget http://www.pbernert.com/spupetenull101.tar.gz
wget http://www.emuxhaven.net/emuxhaven/psx/plugin/spuEternal141_linux.tgz

wget http://www.myte.ca/pub/omnijoy-1.0.0-bin32.tar.gz
wget http://members.chello.at/erich.kitzmueller/ammoq/down/padJoy082.tgz

export EPSXE='/usr/local/games/epsxe'
sudo mkdir $EPSXE
sudo unzip -d $EPSXE epsxe160lin.zip
sudo tar xfz gpupetemesagl176.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupetexgl208.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupeopssoftx117.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupeopssoftsdl116.tar.gz -C $EPSXE/plugins/

sudo tar xfz spupeopsoss-alsa109.tar.gz -C $EPSXE/plugins/
sudo tar xfz spupetenull101.tar.gz -C $EPSXE/plugins/
sudo tar xfz spuEternal141_linux.tgz -C $EPSXE/plugins/

sudo tar xfz omnijoy-1.0.0-bin32.tar.gz -C $EPSXE/plugins/
sudo tar xfz padJoy082.tgz -C $EPSXE/plugins/

cd $EPSXE/plugins/
sudo mv padJoy/bin/* . 
sudo rm -rf padJoy
sudo mv cfg* ../cfg/
sudo mv *.cfg ../cfg/
sudo chmod 666 ../cfg/*.cfg

cd $EPSXE
sudo chmod 777 cfg sstates snap memcards
sudo touch memcards/epsxe000.mcr memcards/epsxe001.mcr .epsxerc
sudo chmod 666 memcards/*
sudo chmod 666 .epsxerc

sudo aptitude install upx-ucl
sudo aptitude install upx-ucl-beta

cd $EPSXE
sudo cp epsxe epsxe_bak
sudo upx -d epsxe

sudo aptitude install libgtk1.2-common libgtk1.2 

wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

sudo gdebi libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

sudo rm -rf libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

cd ~
rm -rf ePSXe_install

sudo gedit /usr/local/bin/epsxe
```

pasted this:

```
#!/bin/bash

export EPSXE='/usr/local/games/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe $*
chmod 666 $EPSXE/cfg/*.cfg $EPSXE/sstates/* $EPSXE/memcards/*.mcr $EPSXE/snap/* 2>/dev/null
```

and set the permissions:

```
sudo chmod 755 /usr/local/bin/epsxe
```

---

### Post by Felson on 2008-05-02
@Uruz
This sounds like the UPX problem. Try redoing this:

```

sudo aptitude install upx-ucl-beta

cd /usr/local/games/epsxe 
sudo cp epsxe epsxe_bak 
sudo upx -d epsxe

```

---

### Post by Felson on 2008-05-02
@-siGGi-
Not really sure what the problem is there. Try using the software Video plugin instead. I know you don't really want to try playing a game with that, it's just a check to see if it is having a problem with libgpuPeopsSDL.

---

### Post by -siGGi- on 2008-05-02
when i use Pete's MesaGL Driver it doesnt work every video plugin in the settings is not working i tried some isos and even original disks all i get is this:
[[IMG]http://img204.imageshack.us/img204/5457/bildschirmfoto2po6.th.png[/IMG]](http://img204.imageshack.us/my.php?image=bildschirmfoto2po6.png)

---

### Post by Felson on 2008-05-02
@-siGGi-
sorry, I am all out of ideas. I was going to say you should ask at ngemu, but they seem to be down or gone. The other place to try would be Petes Forum. [here]("http://www.razyboard.com/system/user_Pete_Bernert.html")

---

### Post by Uruz on 2008-05-02
> **Felson said:**
> @Uruz
This sounds like the UPX problem. Try redoing this:

```

sudo aptitude install upx-ucl-beta

cd /usr/local/games/epsxe 
sudo cp epsxe epsxe_bak 
sudo upx -d epsxe

```

Aha! Thank you!

While your advice did not directly help me, I went back and found the problem!
I had previously tried to install it myself and was clicking that folder, not this one.

Now I just need to locate scph1000.bin. I had it let's see...

Thanks again, I'll check back if I have any problems.

**EDIT**
Uh, typing 'sudo chmod 755 /usr/local/bin/epsxe' in the terminal didn't seem to change it, I still can't write to it. Do I need to log into root? If so, how?

sux - asks me for a password, giving it my own does not work.

---

### Post by kaens on 2008-05-03
nevermind

---

### Post by Felson on 2008-05-05
@Uruz
755 = RWXR-XR-X
This means:
User: Read write execute
Group: Read Execute
World: Read Execute
Since the file will be owned my root, it can only be changed by root, but anyone can execute the script. So, if you run that script, it will start epsxe.

---

### Post by Ioky on 2008-05-15
I try to start video / sound confg but I get this:

ioky@BiTuX:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

and epsxe close


Oh nvm, the apt-get tool can't found libstdc++-libc6.2-2.so.3, so I manually download it and installed. work well. 

Thanks, hope that help everything have the similar problem

---

### Post by wallowinthemire on 2008-05-17
I've gotten epsxe to launch fine, and I can configure the controllers, memcards, and bios. But when I try to config video or sound, the program just  exits, which also happens when I try to run any iso or cd. Running it from terminal, I get this error.

```
/lib/tls/i686/cmov/librt.so.1: symbol __pthread_clock_gettime, version GLIBC_PRIVATE not defined in file libpthread.so.0 with link time reference
```

I dont know if this was addressed already, but I'm kind of on a time squeeze I just wanted to get this question out there in case it hasn't.

Thanks

---

### Post by wraithoffire on 2008-05-24
Hello.  Whenever I try to run epsxe, I get 
```
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//scph1001.zip]. 
 * Init internal cdrom ... ok
CD read toc header failed (22)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (22)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (22)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (22)
CD(185,28,74) read ioctl failed (22)
CD(185,29,0) read ioctl failed (22)
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteMesaGL.so.1.0.76] 
ATI Technologies Inc.
Radeon X1550 Series
 * Open gpu[0] 
plugins/libspu.so: cannot open shared object file: No such file or directory
```
and then it quits.  Any help would be appreciated.

---

### Post by Felson on 2008-05-25
Make sure that the sound plug in is installed correctly, or try using a different one to see what happens.

---

### Post by Trixilver on 2008-05-29
Please Help!

I can run ePSXe all OK - but when I try to set video plug-ins I get this from the terminal:

```
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or direct
```

I **have** entered all the code for installation, but I did notice that when I try:

```
sudo aptitude install libgtk1.2-common libgtk1.2 libstdc++2.10-glibc2.2
```

I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
[B]Couldn't find any package whose name or description matched "libstdc++2.10-glibc2.2"
Couldn't find any package whose name or description matched "libstdc++2.10-glibc2.2"[/B]
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
```

So any ideas on why this failed...?

---

### Post by Felson on 2008-05-29
I am going to guess that you are using 32bit Hardy. Try the following, and if it works, let me know and I can add it to the how-to

```

cd ~/ePSXe_install
mkdir tmp_libs
cd tmp_libs

wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
dpkg -x libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
sudo cp usr/lib/* /usr/lib/

```

---

### Post by cha0s on 2008-05-30
Thanks much, excellent guide. 

I had the same problem with libstdc++-libc6.2-2.so.3.

Your solution is correct except for 2 slight oversights.

1) Your old script deleted that directory on the home directory, so ~/ePSXe_install won't exist anymore. Your new little script should create it.

2) The dkpg command needs a directory output argument. It should be:

dpkg -x libstdc++2.10-glibc2.2_2.95.4-24_i386.deb .

When making those corrections, then config->video does not fail as it did before... Thanks!

P.S. Sorry if it seems like I'm being pedantic, just trying to help people that might not be able to figure it out...

---

### Post by Trixilver on 2008-05-30
Thanks Felson! That worked for me too, **but**, when I did:

```
dpkg -x libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

```

It had a bit of a problem. I forget what the problem was exactly, but I think it asked for an output directory or something. Anyway, I ended up changing it to:

```
sudo dpkg install libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
```

And it worked perfect. Also, the "sudo cp usr/lib/* /usr/lib/" didn't work for me either, but I discovered I was able to change the plugins fine after the dpkg install.


But now I have another problem. When I try to run a game (from a .bin image), ePSXe quits and I get this from the terminal:
```
/usr/local/bin/epsxe: line 6: 24378 Segmentation fault      ./epsxe $*
```

---

### Post by Felson on 2008-05-30
@Trixilver
ya, if the "-x" line didn't work, the next one would fail for sure. I never thought about actually doing a proper install of an old package. Good call on that. That is better, because if they ever make it work and add it back to the repos, it should update. I am not really sure on your seg fault though. Not much to go on there. Does it work with other games?

@cha0s
Ya, you are right, I forgot the "." at the end of that line. 


The change has been added to the how-to now.

---

### Post by mocha on 2008-06-01
cfgPeteXGL2 not found!
cfgPeteMesaGL not found!


I keep getting the above messages when trying to configure the Pete's video plugins.  Here is my cfg dir:

-rwxr-xr-x 1 mocha mocha 194898 2007-11-29 09:50 cfgOmniJoy
-rwxr-xr-x 1 mocha mocha  41258 2003-11-21 17:21 cfgPadJoy
-rwxr-xr-x 1 mocha mocha  22736 2004-09-19 12:23 cfgPeopsOSS
-rwxr-xr-x 1 mocha mocha  56476 2004-03-13 14:50 cfgPeopsSoft
-rw-rw-rw- 1 mocha mocha   1202 2008-06-01 01:45 gpuPeopsSoftX.cfg
-rw-rw-rw- 1 mocha mocha   2315 2008-04-27 04:44 gpuPeteMesaGL.cfg
-rw-rw-rw- 1 mocha mocha   2386 2008-04-27 05:36 gpuPeteXGL2.cfg
-rw-rw-rw- 1 mocha mocha    268 2008-06-01 01:43 spuEternal.cfg
-rw-rw-rw- 1 mocha mocha    690 2008-06-01 01:43 spuPeopsOSS.cfg

---

### Post by Nazty_Nayt on 2008-06-24
Can someone help me out here, I've been trying to get a PSX emulator working for a week now, and to no avail.  I've followed all the steps to where "things are a bit more complex.."  I'm supposed to click the "here" link, but firefox can't establish a connection.  So now I've pretty much gone through the first half only to be let down, this is what' I've been going through all week, is there another link or anything, I have Ubuntu 8.04 64bit.  Please help.

---

### Post by Felson on 2008-06-24
@Nazty_Nayt
Sorry, I didn't notice that dfreers site is toast. I will have to spend some time at it to remove the use of his repositories. In the mean time, try using the Feisty64 instruction. useing
```

sudo aptitude install ia32-libs

```
at the start instead of the gtk one. If that line fails, run the Hardy32 section just above as well, then just try and continue through the rest of the Feisty64 section.
Also, let me know how it goes. Could save me some time on updating the how-to

---

### Post by Nazty_Nayt on 2008-06-24
> **Felson said:**
> @Nazty_Nayt
Sorry, I didn't notice that dfreers site is toast. I will have to spend some time at it to remove the use of his repositories. In the mean time, try using the Feisty64 instruction. useing
```

sudo aptitude install ia32-libs

```
at the start instead of the gtk one. If that line fails, run the Hardy32 section just above as well, then just try and continue through the rest of the Feisty64 section.
Also, let me know how it goes. Could save me some time on updating the how-to

Thanks Felson, will do.  I won't be turning my computer off till I get it working, cause I'm not going through all those commands again, lol.  Got the whole day off, so I'll let you know.  Thanks again, for the quick response.


EDIT:  Ok, well I followed everything, made the shell script.  Went to launch EPSXE, and it just says bash: EPSXE: command not found.


EDIT: Cancel last edit/Thank you so much man, it works.  I just needed to lowercase "epsxe" and it works fine, I put a game in, and it works, it starts off kind of slow, can I change the FPS or anything to make it faster?

PS: Is there a guide anywhere for using a PS3 controller?  Thanks again!! :guitar:

---

### Post by Felson on 2008-06-24
No, I have no idea about the controller how-to. Never tried using one, always just used a computer controller.

By the way, Which steps worked, and which didn't? That way I can update the how-to.

---

### Post by Nazty_Nayt on 2008-06-24
Sure I ran the feisty 64 script, then the common usage script, followed by the shell script, bash script, and then the chmod 755 permissions.  And that's it really, I'm still messing with the configuration, so far the games are either too fast, or too slow, but other than that it's working, so I just got to tinker with it a little bit.  Thanks again man, I can rest easy tonight, lol  \\:D/

---

### Post by dfreer on 2008-06-24
> **Felson said:**
> @Nazty_Nayt
Sorry, I didn't notice that dfreers site is toast. I will have to spend some time at it to remove the use of his repositories.

The packages still exist. If you let me know what's needed, I can upload them to this forum and you can change your guide to point to those files instead.

---

### Post by Felson on 2008-06-25
It would be lib32glib1.2 lib32gtk1.2 and any dependencies they have from your repositories. 

I think I may just go with the Fiesty64 instructions for all of them though. That way the only difference is what the ia32 libs are called.

---

### Post by talesworld on 2008-06-25
i have that but when I want to play the game xenogears and I extracted the file and go to run the iso it does not show it there and it works with final fantasy 7 disc 1 and that is the only game I have so please help. or give me info

---

### Post by dfreer on 2008-06-26
> **Felson said:**
> It would be lib32glib1.2 lib32gtk1.2 and any dependencies they have from your repositories. 

I think I may just go with the Fiesty64 instructions for all of them though. That way the only difference is what the ia32 libs are called.

Either way; here's those two AMD64 packages for gutsy (latest versions I have). Not sure on the dependencies as I'm on windows right now. The entire repository pool can still be accessed here for now:

[http://packages.dfreer.org/pool/](http://packages.dfreer.org/pool/)

---

### Post by Nazty_Nayt on 2008-07-05
Hey can someone tell me how to change the audio driver.  Somehow I had the wrong one in there, I got the P.E.Op.S. OSS Audio Driver 1.9 unless that is the right one, I'm not too sure, but I do know I'm not getting any sound. :(  Other than that works like a charm.  I do got to get a usb controller since I can't find a guide for a PS3 controller on here though.

---

### Post by F-3582 on 2008-07-06
> **Nazty_Nayt said:**
> Hey can someone tell me how to change the audio driver.  Somehow I had the wrong one in there, I got the P.E.Op.S. OSS Audio Driver 1.9 unless that is the right one, I'm not too sure, but I do know I'm not getting any sound. :(  Other than that works like a charm.  I do got to get a usb controller since I can't find a guide for a PS3 controller on here though.
PEOpS SPU is certainly not right, because of some serieous noise processor issues. The guide should have mentioned how to get Eternal SPU 1.41 which would be the one for you to use. Just select it in the Config -> Sound menu. A configuring guide should be somewhere in this thread, as well.

---

### Post by Nazty_Nayt on 2008-07-06
Ok, well I did a complete re install and I'm still getting the same driver :(

One thing I did notice is that when I'm installing the drivers the first wget that's at myte.ca cannot be located.  Other than that I had no errors.

---

### Post by F-3582 on 2008-07-07
Do you get any audio plugins other than that? The PEOpS ALSA driver isn't any better than the OSS driver.

---

### Post by Felson on 2008-07-07
@Nazty_Nayt
Which wget was giving you trouble? I just tried the 2 of them, and they seem to work, so if you got an error on them, can you let me know what it was so I can chase after godady? Myte.ca is my site, so if it is acting up, I should be able to do something about it.

---

### Post by andyhowington on 2008-07-07
> **Felson said:**
> I am going to guess that you are using 32bit Hardy. Try the following, and if it works, let me know and I can add it to the how-to

```

cd ~/ePSXe_install
mkdir tmp_libs
cd tmp_libs

wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
dpkg -x libstdc++2.10-glibc2.2_2.95.4-24_i386.deb .
sudo cp usr/lib/* /usr/lib/

```

HERO STATUS! Thank you so much, I'm a nube and finally you make a guide that works and is easy to follow!! I also had this above problem (*"libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory"*), and this indeed fixed it (Hardy32)

---

### Post by andyhowington on 2008-07-08
I need some more instruction, apparently. I now have ePSXe installed, and I have a bunch of stuff I don't know what to do with in terms of running my games. 

I run Hardy 32.

I have a game that is on 4 discs, and each disc is an .ISO file. When I try from ePSXe > File > Run ISO... and select the iso file from its directory on my desktop, it doesn't work. (after tinkering with Config I managed to get it to where now it opens up a GUI that is all black except for some empty FPS stats along the top.)

What do I do with the ISO? Do I mount it? I have Gmount and can use it but I don't really know what directory I'm supposed to mount them in, or even how it works or what it is doing. Would that change where I need to set my CD-ROM config to in ePSXe? What are my options here with this ISO file?


I appreciate your patience with us new folks, hey maybe one day we'll be pro at this too ;-)

---

### Post by andyhowington on 2008-07-08
> **andyhowington said:**
> I need some more instruction, apparently. I now have ePSXe installed, and I have a bunch of stuff I don't know what to do with in terms of running my games. 

I run Hardy 32.

I have a game that is on 4 discs, and each disc is an .ISO file. When I try from ePSXe > File > Run ISO... and select the iso file from its directory on my desktop, it doesn't work. (after tinkering with Config I managed to get it to where now it opens up a GUI that is all black except for some empty FPS stats along the top.)

What do I do with the ISO? Do I mount it? I have Gmount and can use it but I don't really know what directory I'm supposed to mount them in, or even how it works or what it is doing. Would that change where I need to set my CD-ROM config to in ePSXe? What are my options here with this ISO file?


I appreciate your patience with us new folks, hey maybe one day we'll be pro at this too ;-)

WAIT ok now I run it and it goes to the end credits...I have Final Fantasy 8 on ISO and FF7 on CDROM, and both of them, upon launch, show the end credits to the game! what the?

---

### Post by Nazty_Nayt on 2008-07-08
> **F-3582 said:**
> Do you get any audio plugins other than that? The PEOpS ALSA driver isn't any better than the OSS driver.
Nope, it's just the one driver, that's the only one it gives me, and it doesn't run sound on any of my games.  I click test, and it does say it's working correctly.


> **Felson said:**
> @Nazty_Nayt
Which wget was giving you trouble? I just tried the 2 of them, and they seem to work, so if you got an error on them, can you let me know what it was so I can chase after godady? Myte.ca is my site, so if it is acting up, I should be able to do something about it.

I tried it again just now Felson, and this time it worked.  I can't remember what the error was exactly, I think it just wasn't connecting.  But the second one worked fine.  I'm still stuck though after pushing it through, it doesn't give me the sound driver I'm supposed to have, I'm confused.

---

### Post by F-3582 on 2008-07-08
> **andyhowington said:**
> WAIT ok now I run it and it goes to the end credits...I have Final Fantasy 8 on ISO and FF7 on CDROM, and both of them, upon launch, show the end credits to the game! what the?
Are you sure those aren't the start-up credits?

Nazty_Nayt: Make sure the plugin (libspuEternal.so) is in your ePSXe plugin directory.

---

### Post by Nazty_Nayt on 2008-07-09
> **F-3582 said:**
> Are you sure those aren't the start-up credits?

Nazty_Nayt: Make sure the plugin (libspuEternal.so) is in your ePSXe plugin directory.

That one I don't have in my directory, I've re-installed felson's script.  I'm going to look through it again here.

Yeah I'm not seeing that plugin, in the script.  Could you post the code please?

---

### Post by F-3582 on 2008-07-09
> **Nazty_Nayt said:**
> That one I don't have in my directory, I've re-installed felson's script.  I'm going to look through it again here.

Yeah I'm not seeing that plugin, in the script.  Could you post the code please?

The plugin is in the script, but apparently doesn't get unpacked. Strange... Then you might have to download and unpack it manually. Just fetch it from [here]("http://www.emuxhaven.net/emuxhaven/psx/plugin/spuEternal141_linux.tgz").

Unpack it and copy it into the ePSXe plugin directory (you might need root privileges for that).

---

### Post by Felson on 2008-07-09
Strange that it didn't unpack. There is a command to do so in the how-to.
```

sudo tar xfz spuEternal141_linux.tgz -C $EPSXE/plugins/

```

---

### Post by Nazty_Nayt on 2008-07-10
Errr, I got it working I guess, I can select it in the config menu, I click test, and it says it's working properly.  But I'm still not getting any sound :(  I've tried a few different games so I know it's not the games I'm running.  Just to make sure I didn't mess anything else up I'm going to post the other plugins I have.

For my video plugin I have P.E.Op.S SoftX Driver 1.17 tested, and working properly, I have 2 others to choose from that are Pete's MesaGL Driver 2.76, and Pete's XGL2 Driver 2.8.

For sound I have the Eternal SPU Plugin 1.41 tested and working properly (at least it says it is anyways.)

CDrom is /dev/cdrom

The Bios is set up correctly too obviously otherwise I wouldn't be able to load the games.  Errr, what am I doing wrong?

BTW thanks for all the help so far.

---

### Post by fotakou on 2008-07-10
Hello there

I am new to the forums and relatively new to linux.I have ubuntu 8.04 installed and recently decided to get some ps games but i had some questions regarding the emulator.If they have been answered in this thread please let me know so that i can search for them later ;)

First of all i would like to know if i can use a controller with the linux edition of epsxe.I have plugged it and tried to configure the buttons but it did not work :S Any ideas on what i should do?

I have installed epsxe on windows as well and i was wondering if there is any way to transfer the saved games from one operating system to another(i would really like to play every game on linux ;) )

Last but not least i have some .iso or some .img files but i cant seem to play them with the linux version of epsxe.So i would like to know if there is any way to do it

Thanks in advance :guitar:

---

### Post by Felson on 2008-07-10
@fotakou
1) Yes, you can use a controller in the Linux EPSXe. I can not really help you past that on this issue though, because I have never really had to fight with it. It's always just worked for me. Did you install using this how-to? If not, maybe you just need to install the plugins.
2) Yup. Just copy them over. No problem at all. All you need to do is put them in your memcards folder, and select them using EPSXe.
3) I tend to use the actual CDs, but from what I understand, EPSXe prefers bin/que sets. I am told that AcetoneISO is good for that. It isn't in the repos, so here is a short [how-to]("http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html") and [here]("http://www.acetoneiso.netsons.org/") is the Acetone site.


@Nazty_Nayt
Crazy question.... Do you have sound anywhere else? I am wondering if it is your mixer settings. With my last sound card, I had a hell of a time with it when anything else was running. I would check to make sure you don't have some other app locking your sound card.

---

### Post by fotakou on 2008-07-10
Many many thanks my friend
I am now using a joystick with no problem
The thing is that i have the same problem with the sound.I cant get any :S I do not have any other application running and i am using peops oss audio driver 1.9
Any ideas ???

---

### Post by Felson on 2008-07-10
Other then what we already tried with Nazty_Nayt, not really. I am kinda at the end of what I can think of on that one.

---

### Post by Scooter7 on 2008-07-10
I had the same problem, I think I ended up just using a different sound plugin.   I don't have access to my Ubuntu installation right now, though, so I can't check.

---

### Post by Nazty_Nayt on 2008-07-13
Sorry for the delay in replying felson.  Yeah, all my other apps use sound perfectly.  This is the only program I have a problem with.  I mean for now it's OK, I can at least play, and hum to myself ;)

If anyone does find a solution please post it, or PM me, I'd greatly appreciate it.  thanks

:guitar:

---

### Post by F-3582 on 2008-07-13
You're on PulseAudio, aren't you? There are two options:

- Make SPUEternal (which I suppose you're using right now) use SDL as output method and install the PulseAudio version of SDL ('libsdl1.2debian-pulseaudio'). Unfortunately I didn't test that one, because I now switched to OSS4.
- Invoke ePSXe with 'padsp epsxe' and make SPUEternal use OSS instead. This worked for me, but had some serious audio lags on m machine.

As I said, I recently switched to OSS4 which I recommend to everyone who is seriously interested in emulation. Most emulators work best on OSS, anyway (except for the Ubuntu version of ZSNES - install the latest beta, instead). A nice guide can be found [here]("http://ohioloco.ubuntuforums.org/showpost.php?p=4874981&postcount=2").

---

### Post by Uruz on 2008-07-29
Hey, I upgraded to hardy(this may be unrelated, I had not played in a while beforehand) and now when I click to Configure Audio or Video ePSXE crashes. It's not major, It's just now that I've upgraded some of my video problems have fixed and I wanna see if I can get the Battle Cursor to work in FF7

---

### Post by Nazty_Nayt on 2008-07-30
My sound works awesome!!!!  Honestly I think all I needed to do was restart my computer, because I hadn't played anything since I installed it, been busy playing MGO online.  Anyways it works, Metal Gear Solid kinda lags a bit, I think it's my copy though, cause my other games play perfectly.  Thanks for this guide, and all the help Felson, waiting on my gamepad to come then I can kill some time :)

Quick question about the emulator, is there a way where i can make the screen larger?  Also, how do you save the state while playing, because once I load an ISO, the default epsxe menu with the blue background disappears, and lastly, if I want to play a different game, how do I do that also?  Thanks again for everything, happy gaming everyone

:guitar:

---

### Post by F-3582 on 2008-07-30
Did you activate the special game fixes for MGS (I gather you are still using SPUEternal)? You might want to fiddle around with the buffer size (smaller means less lags, but more stuttering - try to find a compromise).

To get the ePSXe main menu back, press Escape. Saving states was F3, IIRC and loading them was F5, although I recommend using memory cards, instead. Save states can break things, you know.

Playing a different game means restarting ePSXe. There's no way around it.

---

### Post by wingnux on 2008-07-30
> **mocha said:**
> cfgPeteXGL2 not found!
cfgPeteMesaGL not found!


I keep getting the above messages when trying to configure the Pete's video plugins.  Here is my cfg dir:

-rwxr-xr-x 1 mocha mocha 194898 2007-11-29 09:50 cfgOmniJoy
-rwxr-xr-x 1 mocha mocha  41258 2003-11-21 17:21 cfgPadJoy
-rwxr-xr-x 1 mocha mocha  22736 2004-09-19 12:23 cfgPeopsOSS
-rwxr-xr-x 1 mocha mocha  56476 2004-03-13 14:50 cfgPeopsSoft
-rw-rw-rw- 1 mocha mocha   1202 2008-06-01 01:45 gpuPeopsSoftX.cfg
-rw-rw-rw- 1 mocha mocha   2315 2008-04-27 04:44 gpuPeteMesaGL.cfg
-rw-rw-rw- 1 mocha mocha   2386 2008-04-27 05:36 gpuPeteXGL2.cfg
-rw-rw-rw- 1 mocha mocha    268 2008-06-01 01:43 spuEternal.cfg
-rw-rw-rw- 1 mocha mocha    690 2008-06-01 01:43 spuPeopsOSS.cfg

I have the same problem but only with Pete's XGL2, MesaGL works just fine.
Any help?

---

### Post by F-3582 on 2008-07-30
Those two files (cfgPeteXGL2 and cfgPeteMesaGL) are apparently not there. They are configuration tools for the XGL and MesaGL plugins and should have been compiled together with the plugins.

---

### Post by wingnux on 2008-07-30
I've downloaded the plugins from Pete's website so the packages should be complete :P

---

### Post by F-3582 on 2008-07-30
Yup, but the cfgPeteXGL2 is missing, even though the readme states otherwise. Weird...

---

### Post by Nazty_Nayt on 2008-07-30
Hey F-3582, I got everything working up to par except 1 thing.  And that's the gamepad.  I originally wanted to use a PS3 sixaxis, but that's a whole nother level.  So right now I'm going with an Xbox usb controller till I get a new one.  The problem is, I can't assign the buttons to it.  I can assign the L2, L1, R2, and R1 buttons.  When I go to the D-Pad, and X ^ S O it won't input, the error I get in the terminal is

```
padJoy: no useable input received
```

The plugin that's in there is ammoQ's padjoy Joy Device Driver 0.8

---

### Post by F-3582 on 2008-07-31
Sorry, I'm not very good with controllers in Linux, but I'm glad that everything else works for you.

---

### Post by mocha on 2008-07-31
> **F-3582 said:**
> Those two files (cfgPeteXGL2 and cfgPeteMesaGL) are apparently not there. They are configuration tools for the XGL and MesaGL plugins and should have been compiled together with the plugins.


I ended up using the files from an older version of the plugins.  I attached them here.

---

### Post by mentaluproar on 2008-07-31
I am getting thsi error when trying to launch epsxe.

sean@elec-tard:~$ epsxe
/home/sean/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I have tried everything in this thread and others to remedy this and still I get nothing. :'(

I am running Ubuntu Hardy 64 bit.

---

### Post by Felson on 2008-07-31
Try the doing the section marked "For Feisty64". I think that should fix your problem.

---

### Post by mentaluproar on 2008-07-31
...I think I love you.

It's 1.5.2, but I should be able to run megaman Legends 2 on this.  THANKS!
-------edit to resume whining---------
I now get this...
CD read toc header failed (22)
 * First/Last track: 0 1
 * Track 1: CD get track start failed (22)
 (DATA) - Start 0: (100,201,178)
CD(0,2,16) read ioctl failed (22)
CD(0,2,0) read ioctl failed (22)
CD(0,2,1) read ioctl failed (22)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
NVIDIA Corporation
                  GeForce 6150SE nForce 430/PCI/SSE2
                                                     * Open gpu[0]
 * Init spu[0][libspuPeopsOSS.so.1.0.9]
Sound device not available!
                            * Open spu[0]
 * Init pad[0][libpadJoy-0.8.so]
padJoy: trying to start a thread; if it hangs, you must disable multithreading
                                                                               * Open pad[0]
CD(0,2,16) read ioctl failed (22)
CD(0,2,0) read ioctl failed (22)
Gdk-ERROR **: Fatal IO error 22 (Invalid argument) on X server :0.0.

-_-

---

### Post by F-3582 on 2008-08-03
You might wanna extract an ISO.

Also, try using spuEternal and gpuPEOpSSpftX instead.

---

### Post by dystheria on 2008-08-08
I have to give a massive thanks to this guide.
I'm running Hardy 8.04 on an AMD64 dualcore system, so using PCSX was basically out of the question for me (ran way too fast, sound skipped a lot)

This guide helped me build and install epsxe with a lot of ease.
You have no idea how thankful I am. (I even registered with the ubuntu forums just to give thanks.)

So yeah

This guide DOES work for Hardy on AMD64

---

### Post by Cochise on 2008-08-10
Thanks for the guide, worked first time. Cheers :-D

---

### Post by booster614 on 2008-08-12
hello all. i followed all the steps that we're given for hardy 8.04, and when i open terminal and type in epsxe the gui loads just fine, but when i try to config the graphics and sound i get this error 




 * Running ePSXe emulator version 1.6.0. 
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directorybooster@booster-desktop:~$ 


any ideas on were i went wrong ???

---

### Post by TonkaToy on 2008-08-23
> **Felson said:**
> ya, I don't trust the full screen option. Never had much luck with it. What I do, is set the resolution to the same as my screen, and run [this]("http://www.myte.ca/pub/wmctrl_fs_target") script on it. I made an icon on my tool bar to run it. You will also need to make sure you have wmctrl installed.
```

sudo aptitude install wmctrl

```

hey Felson first of all thanks so much for all of your hard work. I was just wondering, i followed your instructions for the script and puts everything i click into fullscreen except for epsxe while it is playing a game. I was just wondering how i could get it to work your help is greatly apprectiated! thx :)

---

### Post by tasos on 2008-08-23
Some issues have been reported in multi-cpu systems and on cpus with HyperThreading regarding slowdowns

From the [EmuparadiseForums]("http://www.epforums.org/epsxe-does-not-t44752/index.html?p=898433") :
> ePSXe wasn't designed to work on dual-core computers.
That's why if you try to play it on a dual-core computer that's running WinXP, the image and sound will stutter and not play smoothly.

This problem seems to affect linux too (at least mine :P) and it is fixed in version 1.7.0 of epsxe (windowz only, yet)
There is a workaround in linux though, just replase at your epsxe start script the > ./epsxe with > taskset -c 0 ./epsxe
So that the scheduler run the epsxe process only on one cpu

From the taskset man page:
> taskset  is  used  to set or retrieve the CPU affinity of a running process given its PID or to launch a new COMMAND with a given CPU affinity.  CPU affinity is a scheduler
       property that "bonds" a process to a given set of CPUs on the system.

---

### Post by Garratt on 2008-08-23
laadeedaa

---

### Post by TonkaToy on 2008-08-23
> **Garratt said:**
> i really don't get the point to these emulators, no offense to the poster, but do you seriously mean or believe all the crap you wrote on the front page... rediculus... do you want us to sign a EULA as well?... just incase.

why get an emulator that will only emulate games you already own. how about using the ps2? on your big *** tv rather than sitting in front of a measly 22inch lcd or whatever..

I have every sega, sms, and megasis game known to man, and good arcade emulator with about 100 games, if anyone wants copies let me know... 

cause frankly i'm sick to death of endlessly looking at emulator pages that ignore ppl who ask for games or tell me they are going to report me...

but yea good install guide apart from the typical restraint.

well actually garratt some people (like me) lose all their games or get them all scratched up and their playstations say freaking "disc read error" when you try to play a disc (I hate that so much) and i actually like just being able to relax and play all my old games in front of my comp and not have to shuffle through all my crap to find an old copy of dino crisis 2 ;). But i do, in a way, see where you are coming from i guess.

---

### Post by dfreer on 2008-08-24
> **Garratt said:**
> i really don't get the point to these emulators, no offense to the poster, but do you seriously mean or believe all the crap you wrote on the front page... rediculus... do you want us to sign a EULA as well?... just incase.

Because it's the against the rules of this community, and it's tiring to sort through 20 emails/posts for people asking how to get illegal games. If you wish to use an emulator for illegal purposes, that's up to you.

I have my own feelings/views about downloading video games, although I'm not stupid enough to try to get a legal forum shutdown simply because people can't do illegal activities without someone to guide their hands.

> **Garratt said:**
> why get an emulator that will only emulate games you already own. how about using the ps2? on your big *** tv rather than sitting in front of a measly 22inch lcd or whatever..

You can play emulators on your big tv, so I don't really see what you are complaining about. Not having to reach behind and hook up each console every time you want to play, not to mention original hardware issues and using emulator graphic filters for fun.

> **Garratt said:**
> 
I have every sega, sms, and megasis game known to man, and good arcade emulator with about 100 games, if anyone wants copies let me know...

cause frankly i'm sick to death of endlessly looking at emulator pages that ignore ppl who ask for games or tell me they are going to report me...

but yea good install guide apart from the typical restraint.

The "typical restraint" is because sites can be sued/shutdown when you post links to download illegal games. Which is fine for a site that exists to only serve illegal content, they accept that risk. But it would suck if Ubuntu Forums or ZSNES was shutdown and all development stopped simply because you are "sick to death".

---

### Post by Felson on 2008-08-25
@TonkaToy
I am afraid all I do is set the window size to be the same as my screen res, and then click on it once the game starts. It won't stretch the window, because epsxe doesn't auto scale, but it does get rid of all the window decorations and set it to be on top.

---

### Post by fordfairmont on 2008-08-27
Ok read thru the 100 odd posts on this thread and the old one still didnt find anyone with my problem or anything anwhere else to fix it.

All installed fine except when i try to run a cd or even then bios (startup screen with out a disc inserted) a black screen pops up then promptly closes the emulator again...

Being new to Ubuntu wouldn't have a clue what to do now... Took me long enough to get the install right...

HELP.?.?

---

### Post by Felson on 2008-08-28
Run that in a terminal and post what it returns. Might be something telling in the error message, if there is one, when it crashes.

---

### Post by Felson on 2008-09-03
Made a huge change to the how-to. It now makes use of [getlibs]("http://ubuntuforums.org/showthread.php?t=474790"). If a few other people could give this a try, I would like to make sure I didn't pooch this how-to. Change works for me, but it is a change that removed 40+ lines.

---

### Post by CyberCod on 2008-09-13
I can't seem to get gamepad recognized in this.  Everything works fine if I use the keyboard.  I've got a PSX>USB converter and it works fine for mupen64 and other things, but not for this.  Any help?  The ext.gamepad configurations don't seem to work.  I can't configure them.  Is there something special I need to do?

---

### Post by Jack87 on 2008-09-16
Hello, when I try to play with any game I have this message:
```
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//scph1001.bin]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * PAL cdrom detected. 
 * Init gpu[0][libgpuPeopsSDL.so.1.0.16] 
/usr/local/bin/epsxe: line 6: 20371 Segmentation fault      ./epsxe $*

```
the number of "Segmentation fault" change for every game... if I try to load the BIOS, i have this message:
```
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//scph1001.bin]. 
 * Init gpu[0][libgpuPeopsSDL.so.1.0.16] 
/usr/local/bin/epsxe: line 6: 20535 Segmentation fault      ./epsxe $*

```

What can I do?? Thanks!!

---

### Post by Felson on 2008-09-16
Try using a different a different GPU (Graphics Plugin) It looks like it is crashing trying to load that. If that works, make sure that everything that you needed for the libgpuPeopsSDL is there.

Also, can you do a ldd on your libgpuPeopsSDL and past the output.

```

ldd /usr/local/games/epsxe/plugins/libgpuPeopsSDL.so.1.0.16

```

---

### Post by Jack87 on 2008-09-16
That's the ldd's output:

```
linux-gate.so.1 =>  (0xb7f96000)
libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7e8a000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d3b000)
libasound.so.2 => /usr/lib/libasound.so.2 (0xb7c77000)
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c52000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c4e000)
libdirectfb-1.0.so.0 => /usr/lib/libdirectfb-1.0.so.0 (0xb7beb000)
libfusion-1.0.so.0 => /usr/lib/libfusion-1.0.so.0 (0xb7be3000)
libdirect-1.0.so.0 => /usr/lib/libdirect-1.0.so.0 (0xb7bd0000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7bb7000)
/lib/ld-linux.so.2 (0xb7f97000)
```

[QUOTE=Felson]Try using a different a different GPU (Graphics Plugin) It looks like it is crashing trying to load that.[/QUOTE]
Can you suggest me another one??

---

### Post by Felson on 2008-09-16
For a test, I would try the gpupeopssoftx, but you are not going to want to use that one long term. If that works, and you can't find a way to get SDL to work, try gpupetexgl or gpupetemesagl.

---

### Post by rfrayer on 2008-09-29
I hope you dont mind but i took your tutorial and wrapped it into a debian binary
**removed repository because of server overload**

> **Felson said:**
> This is a guide to install the freeware Playstation 1 emulator [ePSXe]("http://www.epsxe.com/") in Ubuntu. It is an updated replacement for [this]("http://ubuntuforums.org/showthread.php?t=95835") guide, which is based on [this]("http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/") guide.

ePSXe is made for x86 only. If you use powerpc it probably won't work. You might want to try another emulator instead, for example [PCSX]("http://www.pcsx.net/") ([Guide]("http://ubuntuforums.org/showthread.php?t=159987")) or pSX ([Guide]("http://ubuntuforums.org/showthread.php?t=394097")) which is in the repository.

Legal note: The installation and use of this emulator requires a Sony Playstation BIOS file. You may not use such a file to play games in a PSX emulator if you do not own a Sony Playstation, Sony PSOne or Sony Playstation 2 console. Owning the BIOS image without owning the actual console is a violation of copyright law. You have been warned. Do NOT ask in this thread, or message me, where to find the BIOS file or game images. Any such messages will be ignored and possibly reported.

Note: This guide is provided as is. I have not personally tested Feisty or other earlier versions of Ubuntu, so your mileage may vary. Although there are no issues caused by this guide that I know of, use at your own risk.

Installation
Common changes:
```

sudo aptitude install unzip
cd ~
mkdir ePSXe_install
cd ePSXe_install
wget http://www.epsxe.com/files/epsxe160lin.zip

wget http://www.pbernert.com/gpupetemesagl176.tar.gz
wget http://www.pbernert.com/gpupetexgl208.tar.gz
wget http://www.pbernert.com/gpupeopssoftx117.tar.gz
wget http://www.pbernert.com/gpupeopssoftsdl116.tar.gz

wget http://www.myte.ca/files/spupeopsoss-alsa109.tar.gz
wget http://www.pbernert.com/spupetenull101.tar.gz
wget http://www.emuxhaven.net/emuxhaven/psx/plugin/spuEternal141_linux.tgz

wget http://www.myte.ca/files/omnijoy-1.0.0-bin32.tar.gz
wget http://members.chello.at/erich.kitzmueller/ammoq/down/padJoy082.tgz

wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb

sudo dpkg -i getlibs-all.deb

export EPSXE='/usr/local/games/epsxe'
sudo mkdir $EPSXE
sudo unzip -d $EPSXE epsxe160lin.zip
sudo tar xfz gpupetemesagl176.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupetexgl208.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupeopssoftx117.tar.gz -C $EPSXE/plugins/
sudo tar xfz gpupeopssoftsdl116.tar.gz -C $EPSXE/plugins/

sudo tar xfz spupeopsoss-alsa109.tar.gz -C $EPSXE/plugins/
sudo tar xfz spupetenull101.tar.gz -C $EPSXE/plugins/
sudo tar xfz spuEternal141_linux.tgz -C $EPSXE/plugins/

sudo tar xfz omnijoy-1.0.0-bin32.tar.gz -C $EPSXE/plugins/
sudo tar xfz padJoy082.tgz -C $EPSXE/plugins/

cd $EPSXE/plugins/
sudo mv padJoy/bin/* . 
sudo rm -rf padJoy
sudo mv cfg* ../cfg/
sudo mv *.cfg ../cfg/
sudo chmod 666 ../cfg/*.cfg

cd $EPSXE
sudo chmod 777 cfg sstates snap memcards
sudo touch memcards/epsxe000.mcr memcards/epsxe001.mcr .epsxerc
sudo chmod 666 memcards/*
sudo chmod 666 .epsxerc

```(note, "upx-ucl-beta" may be "upx-ucl" on Hardy)
```

sudo aptitude install upx-ucl-beta

cd $EPSXE
sudo cp epsxe epsxe_bak
sudo upx -d epsxe

sudo getlibs $EPSXE/epsxe

cd ~
rm -rf ePSXe_install
```Create a shell script that will start ePSXe:
```
sudo gedit /usr/local/bin/epsxe
```and paste this:
```

#!/bin/bash

export EPSXE='/usr/local/games/epsxe'
export LD_LIBRARY_PATH=$EPSXE
cd $EPSXE
./epsxe $*
chmod 666 $EPSXE/cfg/*.cfg $EPSXE/sstates/* $EPSXE/memcards/*.mcr $EPSXE/snap/* 2>/dev/null
```Save/Close, and change permissions for the new file:
```
sudo chmod 755 /usr/local/bin/epsxe
```You can now start by typing "epsxe" in the terminal (without "").

[LIST]
[*]In the menu, open "Config -> BIOS", and set it to /usr/local/games/epsxe/bios/SCPH1001.BIN, click OK. (You must find and obtain ths file yourself. Once you have a copy of it, put it in /usr/local/games/epsxe/bios/)
[*]Open "Config -> Video", and select either "Pete's MesaGL Driver 1.76", "Pete's XGL2 Driver 2.8" or "P.E.Op.S. Softx Driver 1.17". Click configure, then OK to write a config file. Verify that it is working by clicking the Test button, then OK. (Which one you use depends on your computer.)
[*]In "Config -> Sound" select "P.E.Op.S. OSS Audio Driver", "P.E.Op.S. ALSA Audio Driver" or "Eternal SPU Plugin", Configure, then OK. Verify that it is working by clicking the Test button, then OK. (The "NULL" driver are for those few games that just don't seem to work with sound. Or if you have a slow computer, and figure you don't care for the sound.)
[*]In Config -> CDROM, set the path to your CD/DVD-ROM. In most cases it should be /dev/cdrom but in my case /dev/hdc. You can check your path by typing "mount |grep cd" in a console.
[*]In Config -> Game Pad -> Pad 1 menu, you can set up the controls with the keyboard. If you have a real controller, use the "Config -> Ext. Game Pad" option, and pick either omnipad or padjoy, click configre, and set your buttons where you want them.
[/LIST]

**Useful Links**
[Original Thread]("http://ubuntuforums.org/showthread.php?t=95835")
[Icon]("http://www.myte.ca/files/epsxe.png")
[Another How-To]("http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html")
[Petes Home Page]("http://www.pbernert.com/index.htm")
[Petes Forum]("http://www.razyboard.com/system/user_Pete_Bernert.html")
[NightCrawler03Xs How-To/Installer]("http://ubuntuforums.org/showthread.php?t=550304") (Handy little installer that does most of the work for you. Read the script, and it was safe as of the reading. You will still need to do the "upx -d" fix if you are using Gutsy.)
[getlibs]("http://ubuntuforums.org/showthread.php?t=474790") A really cool script that may removed about 45 lines from this how-to.

---

### Post by Felson on 2008-09-29
Don't mind at all. Nice job.

---

### Post by rfrayer on 2008-09-29
Yeah i gave ya credit to on the home page [http://ubuntu.global-web.us/](http://ubuntu.global-web.us/)
> **Felson said:**
> Don't mind at all. Nice job.

---

### Post by Meizulo on 2008-09-30
I have followed the install instructions and everything went well all the way up the point where I tried to configure video. Actually anytime I try and do anything i get this response and ePSXe closes

libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Can anyone shed some light?

---

### Post by Felson on 2008-09-30
try doing the following. If it doesn't work, post the error. Also, make sure you still have getlibs.

```

sudo getlibs --binary /usr/local/games/epsxe/plugins/libspuEternal.so.1.41

```

---

### Post by Meizulo on 2008-09-30
this is the error I get

```
No match for libstdc++-libc6.2-2.so.3
No packages to install

```

---

### Post by Felson on 2008-09-30
hmmm odd. Try using Peops ALSA or OSS sound plugin instead of eternal. Not sure why the lib isn't found.

---

### Post by Meizulo on 2008-09-30
ASLA is already installed and i can't configure in ePSXe becuase it closes as soon as I click on VIDEO, SOUND, or NETPLAY under CONFIG. Does the same thing for RUN CDROM under FILE

---

### Post by rfrayer on 2008-09-30
with mine its the down button. that is slightly sluggish. other than that it works gr8. Yea i was allready on that with the spu in the deb and making a sim link to the other one ( and ended up removing the spu 160) may end up rebuilding the deb in a wile possibly tonight

> **Felson said:**
> @Scooter7
There are a few options to fix that. It sounds like your controller has a bit of a "drift" to it. Mine does the same thing. 
Option 1 is to install jscalibrator, run it and set a dead zone. Then cross your fingers and hope that OmniJoy uses your calibration.
Option 2 is to switch to PadJoy (Configure with epsxe first), then edit the "padJoy.cfg" in a text editor and set the "minzero" and "maxzero" to some number higher then the default, try your game, then rinse and repeat until it works right. (mine is minzero = -5000 maxzero = 5000)

---

### Post by rfrayer on 2008-09-30
try this  
sudo apt-get install libstdc++2.10-glibc2.2


> **Meizulo said:**
> ASLA is already installed and i can't configure in ePSXe becuase it closes as soon as I click on VIDEO, SOUND, or NETPLAY under CONFIG. Does the same thing for RUN CDROM under FILE

---

### Post by Meizulo on 2008-09-30
> try this
sudo apt-get install libstdc++2.10-glibc2.2

when I try that I get

```
E: Couldn't find package libstdc++2.10-glibc2.2

```]

and now I am getting

```
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

---

### Post by Felson on 2008-09-30
Try deleteing the Eternal SPU. That is the only file I could find in there that ldd says want that lib.

---

### Post by kesman on 2008-10-05
[http://packages.ubuntu.com/gutsy/i386/libstdc++2.10-glibc2.2/download](http://packages.ubuntu.com/gutsy/i386/libstdc++2.10-glibc2.2/download)

Download it from there (32-bit ubuntu only!!) and install. That's how I got ePSXe working.

Note that this isn't really very good solution, since the package is designed to work with gutsy, but hey, I didn't get any dependence problems yet, so it should be safe :P

---

### Post by archman on 2008-10-26
> **dfreer said:**
> @Scooter7
I had this same issue with omnijoy, with the logitech dual action. Try using the padjoy plugin instead.

That solved my problem!

Thank you, buddy!

arch

---

### Post by echineon on 2008-10-28
hello, this is my 1st post n im totally a noob in ubuntu,
i can open the epsxe by typing it in terminal but whenever i run an iso (particularly FFVII) it close so suddenly. what has describe in the terminal as follows:
```
jack@jack-laptop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * PAL cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.9] 
Shader effects: missing custom file!NVIDIA Corporation
GeForce 8400M GS/PCI/SSE2
 * Open gpu[0] 
plugins/libspu.so: cannot open shared object file: No such file or directoryjack@jack-laptop:~$ 

```
can anyone help me? thanks in advance :)

---

### Post by lifestream on 2008-11-06
Same here. been searching for ~2.5 hrs  >_>

---

### Post by Loïc2 on 2008-11-20
Felson, thanks a lot for your great howto!

I couldn't find the Thanks button, I had to do it on another post of yours ;)

While I could get ePSXe to work in Dapper and old releases like that, I couldn't manage to run it in Intrepid amd64 (didn't try playing PSX games for a long while), but your howto worked perfectly (+ get-libs is really good).

Thanks for keeping your howto up to date, it's nice to be able to find such good documentation.

Now if somebody could package the instruction in a .deb and get it uploaded in universe...

BTW, I also had to remove the Eternal plugin to get the emulator to launch - maybe that's worth including in the howto (unless someone can figure how to get it to work).

**@echineon** try not using shaders at all in the plugin configuration, then if it work try enabling it bit by bit.

---

### Post by lsp432 on 2008-11-21
'evening all, I find myself in a bit of a jam. With the help of this excellent thread I have ePSXe up and running on 8.10, but I'd like to play using my keyboard, and when my up/down/left/right PSX pad buttons are mapped to my up/down/left/right keys on my keyboard, they don't work at all. I did some searching and found only [this]("http://forums.ngemu.com/epsxe-discussion/113975-keyboard-epsxe-linux-arrows-dont-work.html")

The proposed solution of mapping them to letter keys is problematic for two reasons. One, it's uncomfortable for my hand, and two, it doesn't work either: while I can use the buttons if I map them to letter keys, this causes my framerate to drop from 60 to 15, and I have no idea why. 

I know I can grab the actual scancodes for my arrow keys with xev, so what I need to know is how to change the scancode configuration for ePSXe, if it's even possible. I know there's a keycodes.lst in the ePSXe directory, but the header comment for that says it's for spanish keycodes, I tried changing them anyway and predictably it didn't work.

Many thanks to any and all who can help me,
cheers

---

### Post by shokushu on 2008-11-23
When I try to use Eternal SPU it says that it can't find /dev/dsp. Anyone know what I can do to fix that? I'm using the peops alsa plugin, but the quality is really poor.

---

### Post by Ghaban on 2008-11-30
When i press config -> video i get an error

libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

what does this mean? :/

---

### Post by hcaleman on 2008-12-06
Epsxe works great for me now with the exception of my controller.  Keyboard is fine and have been playing FF7 happily for a few weeks.  When I hook up my controller with ammoq's joypad plugin though I get nothing.  

I have an xbox 360 wireless controller via the wireless gaming receiver.  It works fine in ZSNES and other emulators I have, but EPSXE always tells me "no input" when trying to configure it's plugins.  Anyone have an idea as to where I'm going wrong.

---

### Post by EnderEcho on 2008-12-09
Im running Intrepid 64 bit. I ran the installer because I'm incompetent. I have a BIOS file in the right directory and I have all the other configs in the right places (methinks).

I keep getting this error:

 error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Felson on 2008-12-10
Get rid of all the files for Eternal SPU. I think that should fix your issue.

---

### Post by EnderEcho on 2008-12-10
I think I deleted the SPU files. Is there one called "Eternal SPU" because I couldnt find it.

Thanks for the great how to and all your other help Felson.

---

### Post by EnderEcho on 2008-12-10
I tried to download the package that was linked to a few posts earlier, but it says architectural error .

---

### Post by EnderEcho on 2008-12-10
Ok. I went through the whole process again from the beginning. Everything works great. The only problem I encounter is that the directional keys do not work for me. I had some problems when I was installing the joypad package so I just left it uninstalled.

Would that prevent my directional keys from working for some reason?

It also runs a bit choppy with the FPS tracker in the top left.

Thanks again.

---

### Post by Felson on 2008-12-11
I removed "Eternal SPU" from the how to because it just seems to cause problems.

@EnderEcho
No, the direction keys on the keyboard should work fine without a joy pad plugin. Loading EPSXe, and going to "Config->Game Pad->Pad 1" in the menu. You should be able to set the keys there for the keyboard. If you want to use a game pad, you will need to install one of the game pad extensions. 
As for your chopy issue, all I can sugest there is play with the graphics settings a little bit. Some times sound settings can help too, but usualy not.

---

### Post by dfreer on 2008-12-11
> **EnderEcho said:**
> The only problem I encounter is that the directional keys do not work for me. 

Have you used jscalibrator/jscal at all? It's been known to cause problems similar to yours.

---

### Post by ironslave on 2008-12-12
Ok, i just followed the guide, but with no luck i still get this error. 

can anyone help?
```
james@LinuxMode: * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios/SCPH1001.BIN]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
NVIDIA Corporation
GeForce 8800 GS/PCI/SSE2/3DNOW!
 * Open gpu[0] 
plugins/libspu.so: cannot open shared object file: No such file or directoryjames@LinuxMode:~$ 
```

---

### Post by EnderEcho on 2008-12-14
> **dfreer said:**
> Have you used jscalibrator/jscal at all? It's been known to cause problems similar to yours.

No I haven't used jscalibrator at all. I haven't played with the settings yet. I'll post when i figure stuff out... or have anymore questions.

---

### Post by EnderEcho on 2008-12-18
I've got the video working smoothly now. I just messed with the options on the right side of the configuration.

I'm still having problems with the controls. If I set everything to the up down left right keypad it doesnt work. If I set it to any other keys it works fine. Unfortunately I cant figure out a set up that is comfortable without the directional pad. Any suggestions would be great.

EPSXE doesnt register any sound plugins. I don't know if I missed them or what, but I want to hear that sweet Final Fantasy Tactics and Chrono Cross music!

---

### Post by trendyabinash on 2008-12-27
```
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

This is the error which I am getting please help me out

---

### Post by Ioky on 2008-12-31
The reason why the Eternal SPU Plugin 1.41 are causing all the problem is that the "libstdc++2.10-glibc2.2" package is is no long available since ubuntu 8.04. However, it come with ubuntu 7.10. So simply go to ubuntu package search, then download and install the package manually, will do. 

After that my Eternal SPU Plugin is now working. and it is the best sound plugin. (I think)

I don't know why this package is no long available, it might because problem? it might because conflict? it might because out of date. and is no long needed. well I don't know, but it is sure needed with few software out there. As it is not official supported, use your as your own risk. 

All I can tell you is that it work for me, and it is only available with x86 not x86_64.

here is the link of the package.
[http://packages.ubuntu.com/gutsy/libstdc++2.10-glibc2.2](http://packages.ubuntu.com/gutsy/libstdc++2.10-glibc2.2) 

If anyone know how to make it work on 64bit system, please share your HOW-TO,

---

### Post by joebrueske on 2009-02-25
I've been trying to find someone else with the same problem and a solution that will solve this, but I haven't. I have a post on the emuforoms.com and I'm hoping someone there will be able to help too.

ePSXe installed just fine and I was able to configure everything just fine. The bios I dumped on my old PS2 works just fine too. However, and this only happens in Ubuntu Hardy and not Windows, video flickers regardless as to which plugin I use. This happens with all games.

I thought by turning vsync on my Radeon Mobility card would fix the issue. It does not. Thoughts anyone?

Since it works fine in Windows I'll just keep using it in there, but I'd like to have it up in Ubuntu so I have one more reason NOT to use Windows! hahaha

---

### Post by psycho45 on 2009-03-08
I've followed the steps and everything is working fine, including the plugins, but i have a problem with the bios. i have the file but when i try to drop it into the /usr/local/game/epsxe/bios it tells me permission is denied. how do i move the bios file into the appropriate folder?

i'm a total noob, by the way... T_T

[solved]

---

### Post by psycho45 on 2009-03-09
so i read on a forum that i should be able to save normally for ffix without resorting to savestate. which did not work for me. how do i configure the memory cards and save? i get the feeling it might be because i did not configure the memory cards correctly but i don't know. i'm a noob on emulators and a beginner on ubuntu. can anybody help me on this (without making me feel like an idiot, cuz i sure feel like one)...

---

### Post by myromance123 on 2009-03-17
Hey there, thanks for the tutorial.
  I have come across a problem I need help with.
It has to do with the cdrom. the "mount |grep cd" command brings back nothing.
  I am running 8.04 ubuntu.
I am trying to run the games from CDs since my ps1 is just too old now it wont get past the loading screen except for a few games. My CDs have no scratches.

 Since I couldn't use the "mount |grep cd", I tried the /dev/cdrom/ but it did not work (just  crashes) and so I tried just /cdrom/ since checking / I see that cdrom is under /  . Same problem, it crashes.
 Heres what the terminal spews forth, do you know whats wrong?

```
yusuf@yusuf-desktop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH1001.BIN]. 
 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 7 2
 * Track 1: CD get track start failed (25)
 (AUDIO) - Start 0: (00,00,00) 
 * Track 2: CD get track start failed (25)
 (AUDIO) - Start 1: (00,00,00) 
CD(0,2,16) read ioctl failed (25)
CD(0,17,59) read ioctl failed (25)
CD(0,17,60) read ioctl failed (25)
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeopsSDL.so.1.0.16] 
/usr/local/bin/epsxe: line 6: 15451 Segmentation fault      ./epsxe $*
yusuf@yusuf-desktop:~$ 

```
  Thats the stuff it gives from beginning to end.
Any help would be great!  I have been trying for 3 months now to get it to work...

---

### Post by SweetBrains on 2009-03-22
I installed it according to the first page (that is basically copy pasting most of it) and it works great except for the shortcut.
Originally I had it where the tutorial says to have it, but moved it to my .scripts directory. NEither works.

If I go into /usr/local/games/epsxe and run it it works, or if I call ~/.scripts/epsxe it works, but I'm apparently not allowed to use just epsxe.
Any suggestions?

```
[matt@sweethews:~]$ which epsxe
/usr/local/bin/epsxe
[matt@sweethews:~]$ epsxe
bash: /home/matt/epsxe/epsxe: No such file or directory
[matt@sweethews:~]$ /usr/local/bin/epsxe
/usr/local/games/epsxe
 * Running ePSXe emulator version 1.6.0. 
{..........}
[matt@sweethews:~]$ echo $PATH
.:/home/matt/.scripts:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by SweetBrains on 2009-03-22
I installed it according to the first page (that is basically copy pasting most of it) and it works great except for the shortcut.
Originally I had it where the tutorial says to have it, but moved it to my .scripts directory. NEither works.

If I go into /usr/local/games/epsxe and run it it works, or if I call ~/.scripts/epsxe it works, but I'm apparently not allowed to use just epsxe.
Any suggestions?

```
[matt@sweethews:~]$ which epsxe
/usr/local/bin/epsxe
[matt@sweethews:~]$ epsxe
bash: /home/matt/epsxe/epsxe: No such file or directory
[matt@sweethews:~]$ /usr/local/bin/epsxe
/usr/local/games/epsxe
 * Running ePSXe emulator version 1.6.0. 
{..........}
[matt@sweethews:~]$ echo $PATH
.:/home/matt/.scripts:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```


Alright problem solved. when I attempted to install before I found this guide I made an alias to epsxe that I had forgotten about.....

---

### Post by regulusirius on 2009-04-03
Hi, i installed epxse following the first page, but whena i try to load a .iso file tha program crash, and in the terminal they said:

```
/usr/local/bin/epsxe: line 6:  9425 Segmentation fault      ./epsxe $*

```

How can i solve this problem? I searched it with google  but i didn't find anything

EDIT: by the way, i have Ubuntu 8.04 hardy 64 bit, and an ATI Radeon X1900, (drivers already intalled)

---

### Post by Pkadjipag on 2009-04-06
Hello there, 

I'm kind of new to Ubuntu (which means I have some experience but am still a newb) and I've been able to install and configure everything video and bios for this emulator but the sound just doesn't want to work. I even tried the libspuEternal.so.1.41 but even then I kept getting the same error over and over again which is the one with the libraries. After installing the libraries, I could go in the sound configuration and set up the audio plugin to Eternal, which didn't do anything else at all. I still get no sound and this is what terminal tells me:

 * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/phthewater/epsxe/bios//SCPH1001.BIN].
 * Init ISO code ... ok
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
NVIDIA Corporation
                  GeForce 8600M GS/PCI/SSE2
                                            * Open gpu[0]
 * Init spu[0][libspuEternal.so.1.41]
SPU: open("/dev/dsp", O_WRONLY): Device or resource busy
SPU: AudioDevice Disabled.
 * Open spu[0]
Segmentation fault


I am running Ubuntu on a HP Pavilion dv9000, 2 gb ram, dual core 1.6667 gb, 512 mb video card Geforce 8600 ms and I've got no idea what my sound card is. 

Thanks in advance.

-Pkad.

Ps : I tried configuring it to stop working in OSS and put in the SDL but it says i'm missing libSDL.so.

---

### Post by dragon99 on 2009-05-01
Pkad,

I have installed this emu on both XP and Ubuntu. Been using it for years, and generally it works pretty well for most games on either platform. I have had some installs that caused considerable grief, some versions work better than others. I would suggest you try a fresh install with the latest release for linux (v1.6 I think). This version works well in Hardy, and I'm about to try installing in Jaunty over the weekend.

dragon

---

### Post by joebrueske on 2009-05-02
> **joebrueske said:**
> I've been trying to find someone else with the same problem and a solution that will solve this, but I haven't. I have a post on the emuforoms.com and I'm hoping someone there will be able to help too.

ePSXe installed just fine and I was able to configure everything just fine. The bios I dumped on my old PS2 works just fine too. However, and this only happens in Ubuntu Hardy and not Windows, video flickers regardless as to which plugin I use. This happens with all games.

I thought by turning vsync on my Radeon Mobility card would fix the issue. It does not. Thoughts anyone?

Since it works fine in Windows I'll just keep using it in there, but I'd like to have it up in Ubuntu so I have one more reason NOT to use Windows! hahaha
So, I fixed this. I upgraded to Ubuntu 9.04 and the flickering is completely gone. I also changed the video settings to Best. It doesn't look as good as it does in Windows under the same setting, but it actually runs a LOT faster, which is nice.

---

### Post by joebrueske on 2009-05-02
> **dragon99 said:**
> This version works well in Hardy, and I'm about to try installing in Jaunty over the weekend.

dragon
Let me know what you do for the audio plugin, because I'm having a tough time with OSS. Runs exceptionally smooth, just no sound. I put the 1.41 Eternal SPU plugin (since it's the one I use in XP) in the plugin folder, and now ePSXe crashes with this output.
                                                                       
```
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

It also starts up with this output

```
[code] * Running ePSXe emulator version 1.5.2.

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": 
libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
```

Now, I don't understand why I get this output because those packages are installed. If anyone has any knowledge as to why I'm getting this output, that'd be awesome.

---

### Post by murderslastcrow on 2009-05-10
Hey, saw your post on ngemu and I've got the same issue as far as the output claiming I have no libcanberra gtk module when I totally do and have it installed properly.

A bit of an annoyance since this is the last lil' piece for my friend to feel comfortable with his Ubuntu experience.

---

### Post by joebrueske on 2009-05-12
> **murderslastcrow said:**
> Hey, saw your post on ngemu and I've got the same issue as far as the output claiming I have no libcanberra gtk module when I totally do and have it installed properly.

A bit of an annoyance since this is the last lil' piece for my friend to feel comfortable with his Ubuntu experience.
For those of you having a tough time with ePSXe in Jaunty, you'll need to get upx, which will decompress the executable ePSXe file. Below is the code. This worked for me.
```
sudo apt-get install upx-ucl
cd epsxe(or your dir)
cp epsxe epsxe.bak
upx -d epsxe
epsxe
```

The only challenge I now have is with the O.S.S. sound plugin. I haven't figured out why it's not communicating properly with OSS.

---

### Post by Dark Aspect on 2009-05-19
Ok I am having a hard time loading epsxe on ubuntu jauntry jackalope, I have tired everything, I have all of the required libraries but it gives me a segment fault no matter what I do.

```
administrator@Asus-A8N-E:~/epsxe$ ldd epsxe
	linux-gate.so.1 =>  (0xf7fae000)
	libncurses.so.5 => /lib32/libncurses.so.5 (0xf7f55000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7f51000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7efd000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7ee7000)
	libgtk-1.2.so.0 => /usr/lib32/libgtk-1.2.so.0 (0xf7da0000)
	libgdk-1.2.so.0 => /usr/lib32/libgdk-1.2.so.0 (0xf7d67000)
	libgmodule-1.2.so.0 => /usr/lib32/libgmodule-1.2.so.0 (0xf7d64000)
	libglib-1.2.so.0 => /usr/lib32/libglib-1.2.so.0 (0xf7d3d000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf7d33000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7d23000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7c34000)
	libm.so.6 => /lib32/libm.so.6 (0xf7c0e000)
	libc.so.6 => /lib32/libc.so.6 (0xf7aab000)
	/lib/ld-linux.so.2 (0xf7faf000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7aa1000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7a9d000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7a83000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7a6b000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf7a66000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7a60000)
```

After playing around and coping probably more x86 libraries in my lib32 folder than what I really need, I finally gave up until today when I ran it through a debugger:

```

Program received signal SIGSEGV, Segmentation fault.
0xf7f8d0df in ?? () from /lib/ld-linux.so.2

```

I have tired it with and without a compressed executable and I get the same error, so what is wrong with my ld-linux.so.2? Thanks for any suggestions.

---

### Post by freecs on 2009-06-11
I'm a newbie in using Jaunty. I already follow the how to install [step by step here]("http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/"). but when I start epsxe script, I always get this response.

```
line 6:  4014 Segmentation fault
```After some try, the epsxe start successfully. But i don't get sound and got message that libcanberra is missing. I already install that and still got that message. But now i already solved this problem with a little experiment:D. I dont know this will work or not in your computer, but this work in mine.

In the step by step ePSXe installation, there is a script to execute ePSXe. 

This is the script:
```
                                  [B]
#!/bin/bash[/B]
 
**export EPSXE='/usr/local/games/epsxe'**
**export LD_LIBRARY_PATH=$EPSXE**
**cd $EPSXE**
**./epsxe**
**chmod 666 $EPSXE/cfg/*.cfg $EPSXE/sstates/* \**
**$EPSXE/memcards/*.mcr $EPSXE/snap/* 2>/dev/null ** 

```and for example, you will save it in a place (usually /usr/local/bin) with name 'script_name.sh' and **chmod** it (If you already make this, you don't need to do this step). But when i run it in my jaunty, it always "segmentation fault". So, make new script to repair this.

```

[SIZE=2][B]#!/bin/bash

sudo -u [your_username] [script_name.sh][/B][/SIZE]

```And for example, save this new script with any name with extension '.sh'. you can chmod it if you want. And execute it.
[SIZE=2][B]
PS:You must already [/B]**chmod the 'script_name.sh'. You can also change the 'script_name.sh' with your script directory. Write your username and the script name without bracket.**[/SIZE]

Hope this help:D

---

### Post by QuicksilverPrince on 2009-07-23
Awesome Tutorial, getlibs has been removed though, I found it on another site, I don't know if I am or am not allowed to post sites but, please just remove this if I'm not, I just used 
```
 wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb 
```

---

### Post by BernoulliFire on 2009-09-14
I am a newbie to Ubuntu 9.04, and after following the how-to and trying to run "epsxe" i get this error in the terminal.

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

In my ignorance i'm not sure what this means, but I would like to figure it out.

As quicksilverprince mentioned, the getlibs have been removed; I used the provided code.

Any help would be great or a shove in the right direction. I'm new at this. Sorry if it's something terribly obvious.

thx

---

### Post by Felson on 2009-10-04
It seems the location of the getlibs download changed. use the following instead.

```

wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb

```

The problem you had is because the getlibs lines are needed.

---

### Post by hossdozero on 2009-10-23
> **BernoulliFire said:**
> I am a newbie to Ubuntu 9.04, and after following the how-to and trying to run "epsxe" i get this error in the terminal.

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

In my ignorance i'm not sure what this means, but I would like to figure it out.

As quicksilverprince mentioned, the getlibs have been removed; I used the provided code.

Any help would be great or a shove in the right direction. I'm new at this. Sorry if it's something terribly obvious.

thx

I'm also having trouble with this.
If anyone has the solution, your help would be greatly appreciated.

---

### Post by bigmace on 2010-01-21
> Ok. I went through the whole process again from the beginning. Everything works great. The only problem I encounter is that the directional keys do not work for me.

I have this problem too, if i assign different keyboard keys for directions it works, but not with arrows any ideas fixes?

---

### Post by anonSam on 2010-05-22
I tried this on Lucid and it completely failed as well as ruined my clean install.

---

### Post by Devi 710 on 2010-05-22
If you are really having problems, just install ePSXe v1.7 in Wine. 

Its a newer version and works great in Wine. The only thing I had to do was copy the ZLIB1.DLL to the same folder I had epsxe in.

---

### Post by Efaustus9 on 2010-05-25
The installer worked but I cant seem to find where it put the executable. I want to use epsxe in wahcade as it preforms much better the pcsx. the which epsxe command does not work.

---

### Post by enkilo on 2010-06-03
they got the keycodes wrong in keycodes.lst
change the 4 keycodes for Left, Up, Right, Down to:

Left 0xFF51 0x71
Up 0xFF52 0x6F
Right 0xFF53 0x72
Down 0xFF54 0x74 		 	 		 		 		 		 		 		 		 		 		 	 	
   	 		  [IMG]http://forums.ngemu.com/images/statusicon/user_online.gif[/IMG]   						 		 		[[IMG]http://forums.ngemu.com/images/buttons/report.gif[/IMG]]("http://forums.ngemu.com/report.php?p=1864413") 		 		  	 	 	 	 		  		 			[IMG]http://forums.ngemu.com/images/misc/progress.gif[/IMG] 			[[IMG]http://forums.ngemu.com/images/buttons/edit.gif[/IMG]]("http://forums.ngemu.com/editpost.php?do=editpost&p=1864413")

---

### Post by Oxidized on 2010-08-11
> **enkilo said:**
> they got the keycodes wrong in keycodes.lst
change the 4 keycodes for Left, Up, Right, Down to:

Left 0xFF51 0x71
Up 0xFF52 0x6F
Right 0xFF53 0x72
Down 0xFF54 0x74 		 	 		 		 		 		 		 		 		 		 		 	 	
   	 		

Just got my system running Chrono Cross with this.  The key issue was my only one!  Thanks mucho to all!

---

### Post by dan-420 on 2010-09-04
Hi, i tried this guide and every time i try to open epsxe i get a crash report that my kernel is unstable and my system may become unresponsive. WTF?

---

### Post by MestreLion on 2011-05-14
Using Linux Mint 10, which uses Ubuntu Maverick repositories.

Ive installed the "updated" getlibs .deb file, but it looks like libgtk1-2 was removed from repositories. Here is the output of getlibs:

```
a@b /usr/local/games/epsxe $ sudo getlibs $EPSXE/epsxe
libgtk-1.2.so.0: libgtk1.2
No match for libgdk-1.2.so.0
libgmodule-1.2.so.0: libglib1.2
No match for libglib-1.2.so.0
The following i386 packages will be installed:
libglib1.2
libgtk1.2
Continue [Y/n]? y
E: No packages found
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
E: No packages found
libgtk1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

```

And, as expected, epsxe gives the following error:
```
epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Ive checked libgtk1-2 using Synaptics, and its not there. Not even listed or avaliable for downliad/install. Only libgtk2. Are they compatible? Would a symlink work?

**Any ideias on how or where to get libgtk1-2 on Maverick?**

---

### Post by MestreLion on 2011-05-14
Nevermind... thats too much trouble for a 2003 software... hard to believe that an 8 years old version is still the best / recommended PSX emulator for Linux.

Anyway, searching a lil harder, ive found this: **PCSX-Reloaded **

[http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)

Theres a .DEB file that installed as easily as a double-click. Installer creates a nice icon at menu (Games sectioon). and has a cute GUI. Didint tamper with settings yet, but it run out-of-the-box  flawleslly a 5-minute test i did with a Final Fantasy VII .BIN image i created myself (have the original game)

---

### Post by tetrisalphabet on 2011-12-25
PCSX-R sure is easy to install, but it freezes my computer when I try playing anything.

So between that and libgtk1.2 being basically impossible to find, are there any other PSX emulators that don't suck?

---

### Post by F-3582 on 2011-12-25
> **tetrisalphabet said:**
> PCSX-R sure is easy to install, but it freezes my computer when I try playing anything.

So between that and libgtk1.2 being basically impossible to find, are there any other PSX emulators that don't suck?

pSX hasn't been updated for a while, but might work. PCSX-R is probably the only actively developed emulator left. Try some of the nightly builds.

---

### Post by Yfrwlf on 2012-07-04
> **F-3582 said:**
> pSX hasn't been updated for a while, but might work. PCSX-R is probably the only actively developed emulator left. Try some of the nightly builds.

The nightly build had an error and wouldn't even generate the configure script correctly.

I can't believe in 2012 there's no good PS1 emulator for Linux still.  Most games I try won't even load correctly in version 1.9.92 of pcsxr.  I have tried every BIOS (I have like 10 of them) as well as the emulated included BIOS with no luck.  If ePSXe works well, it would have been really great if they included the libraries with it and/or used a universal Linux installer for it like Zero Install so it wouldn't be made of failure when users of newer distros tried to run it.  I would love to find a simple download of libgtk1.2, but most everything I found was stupid packages instead of just giving the library file, instead of like in Windows where you can download DLL libraries easily from numerous websites.  It never ceases to amaze me how a community that cares about openness has such a severe lack of standards that basic freedom like being able to download and run a program is so impossible for normal (and often even advanced) users.

I know libgtk1.2 is in some old repo someplace or bundled in some old distro someplace.  If I find a good link I'll add it to this thread.

---

### Post by Yfrwlf on 2012-07-04
And don't even get me started on Microsoft's Codeplex site where PCSXR currently resides and how much it sucks.  Reading your user agent browser string to detect your OS?  Screw that, lets just recommend the Windows version for everything!  Lets also not even have a "platform type" for any of the files, so you have to read the file names and try to guess what platform they are for.

Brilliant!

---

### Post by balisto on 2012-07-24
I wish i could install epsxe on ubuntu 64 bits

---

### Post by TOMBSTONEV2 on 2013-03-18
To install ePSXe on 12.04 32 or 64 bit you need the following:

- i386/32-bit

cd /tmp
wget -O libglib1.2ldbl_i386.deb [http://goo.gl/8ghqY](http://goo.gl/8ghqY)
sudo dpkg -i libglib1.2ldbl_i386.deb
wget -O libgtk1.2-common_all.deb [http://goo.gl/snRd1](http://goo.gl/snRd1)
sudo dpkg -i libgtk1.2-common_all.deb
wget -O libgtk1.2_i386.deb [http://goo.gl/HB04M](http://goo.gl/HB04M)
sudo dpkg -i libgtk1.2_i386.deb

- amd64/64-bit


cd /tmp
wget -O libglib1.2ldbl_amd64.deb [http://goo.gl/ZEHVg](http://goo.gl/ZEHVg)
sudo dpkg -i libglib1.2ldbl_amd64.deb
wget -O libgtk1.2-common_all.deb [http://goo.gl/snRd1](http://goo.gl/snRd1)
sudo dpkg -i libgtk1.2-common_all.deb
wget -O libgtk1.2_amd64.deb [http://goo.gl/lxFZj](http://goo.gl/lxFZj)
sudo dpkg -i libgtk1.2_amd64.deb

This will locate and solve libgtk1.2 problems..

---

### Post by DizzyThermal on 2013-03-24
Thanks for the post guys!

I'm still having an issue getting this working though :(

I followed the main post and then TOMBSTONEV2's last post..

I'm not getting a libgtk1.2 error anymore, however, I AM getting this error:

```
./epsxe: error while loading shared libraries: libgmodule-1.2.so.0: wrong ELF class: ELFCLASS64
```

I am on Ubuntu 12.10 (64 bit)

Any help would be greatly appreciated! Thanks in advance :)

---

### Post by kesman on 2013-08-25
Hey!

After reading about this and fiddling around on my Ubuntu 13.04 (64bit), I have to admit that looks like there's only two ways to make epsxe work:

Either install the 32-bit modules by TOMBSTONEV2:s last post's first paragrahp. This will make epsxe work, but will also create a dependency problem with apt-get. You'll have to remove the package libgtk1.2-common every time you want to perform an update and then install it back. ****** solution, but works.

The other solution is to run it in Wine. I've heard it runs just fine.

---

