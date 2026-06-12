---
title: "HOWTO: Install Mupen64"
date: 2007-06-04
forum: Tutorials
---

### Post by thegreenblob on 2007-06-04
2009 EDIT: I completely forgot about this thread. :P Sorry for all the un-answered replies, but I'm editing this thread to recommend [Mupen64Plus]("http://code.google.com/p/mupen64plus/") instead of using this script since that is what I use now and it seems that Mupen64 has not been updated since 2005 and Mupen64Plus has been updated much more recently. (Seems like a lot of people already recommended this in the thread but putting it up here to be more noticeable). If for some reason you want the regular mupen64 instead of Plus this script should still work but I'm recommending plus now. :)


I wrote a simple script that will install mupen64 for you if you don't know how.

Tested on: Ubuntu Feisty

This script is ment for it to just be done not really for learning or nothing so if you wanna know how I did it just open up the script so... here goes.

**1.** Download my script. (the attachment below)
**2.** Run the script. Open the terminal and do this command.
```
sudo sh <The Script Location>
```
**3.** Wait for the script to get done. And then run mupen64 Applications>Games>Mupen64

**To Uninstall**

**1.** Just run these 3 commands in the terminal:

```
sudo rm -r /usr/local/games/mupen64-0.5
sudo rm /usr/share/applications/mupen64.desktop
sudo rm /usr/local/bin/mupen64
```

So... thats about it. Hope it helps some people. :D

Comments Welcome.

---

### Post by Faust942 on 2007-06-22
It came back with this output:

joel@TANGENTRA:~/Desktop$ sudo sh Mupen64-Script-thegreenblob.sh
Password:
--16:38:45--  [http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2](http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2)
           => `mupen64-0.5.tar.bz2.1'
Resolving mupen64.emulation64.com... 62.75.221.236
Connecting to mupen64.emulation64.com|62.75.221.236|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,880,623 (1.8M) [application/x-tar]

100%[====================================>] 1,880,623    145.66K/s    ETA 00:00

16:39:00 (129.22 KB/s) - `mupen64-0.5.tar.bz2.1' saved [1880623/1880623]

mupen64-0.5/
mupen64-0.5/mupen64
mupen64-0.5/mupen64.ini

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
#!/bin/bash 
/usr/local/games/mupen64-0.5/mupen64
rm: cannot remove `mupen64-0.5.tar.bz2': No such file or directory
[Desktop Entry]
Type=Application
Name=Mupen64
Exec=mupen64
Comment=An N64 Emulator.
Icon=/usr/local/games/mupen64-0.5/mupen64_icon.png
Terminal=false
Categories=Application;Game;ActionGame;GameAction;ActionGames;GamesAction;

I am a newbie at scripts and command line errors. Please help.:(

---

### Post by thegreenblob on 2007-06-30
By the look of it, it just looks like the file got corrupt while downloading.

Running the script again should fix it.

---

### Post by Contrast on 2007-07-01
Worked fine here. Thanks a lot! I spent all day trying to install Mupen64 without success. Wish I'd looked here first. :-D

---

### Post by Faust942 on 2007-07-01
Yup got it working perfectly! Thanks!

---

### Post by andytof47 on 2007-07-08
Cheeeeeers,

Works great just can't configure the gamepads????

I press configure and nothing happens on both

the system recognizes my pads --- logitech(cheapo) precision pads


any Ideas?


great script -- games are working just fine apart from this

---

### Post by thegreenblob on 2007-07-09
Thanks for the comments all.

And @ andytof47, I'm not really sure :/ Cause I have cheap logitech precision game pad too and it works fine, sorry.

---

### Post by NEMESIS0744 on 2007-07-12
I Downloaded the script and ran everything, and it seamed like it worked fine. But, when I go to Applications>Games>Mupen64 nothing happens. Please Help!!

---

### Post by thegreenblob on 2007-07-12
Does it run when you try to run it in the terminal? Command: mupen64

If not give me the output. But, it may have just got corrupt while downloading also so running the script again may fix it.

---

### Post by NEMESIS0744 on 2007-07-13
I uninstalled it and deleted the script, and re downloaded to script and ran the command, and it still didn't work . so I opened a terminal and typed "mupen64" (without the quotes), and it gave me this, 
/usr/local/bin/mupen64: line 2: /usr/local/games/mupen64-0.5/mupen64
: cannot execute binary file
and it doesn't open.

---

### Post by stmiller on 2007-07-13
Thanks for the script works great in Feisty 64bit.

---

### Post by Armman on 2007-07-14
Thank you, worked perfectly.

---

### Post by abarabas on 2007-07-16
Hi, thx for the script, but when i run mupen64 in the terminal i get this error:

/usr/local/bin/mupen64: line 2: /usr/local/games/mupen64-0.5/mupen64: No such file or directory
/usr/local/bin/mupen64: line 4: /usr/local/games/mupen64-0.5/mupen64: No such file or directory
(yes, twice)

What could be wrong?

edit: It does exist

---

### Post by thegreenblob on 2007-07-16
@NEMESIS0744, Hmm... I'm not really sure why it would be doing that, my guess would be its corrupt, but, you tried reinstalling it so I'm not really sure. But, might wanna try "sudo mupen64" to see if its a permissions problem for some reason.

@abarabas, might wanna just try "/usr/local/games/mupen64-0.5/mupen64" in the terminal and see if that works. If it don't might want to try reinstalling mupen64 with the script or try "sudo mupen64".

---

### Post by jaffamuffin on 2007-07-19
I got the same error:

line 2: /usr/local/games/mupen64-0.5/mupen64: No such file or directory

I then installed apt-get install ia32-libs
and it in turn installed all this:
```

root@jigglypuff:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386
Suggested packages:
  libasound2-plugins
The following NEW packages will be installed
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1
  libc6-i386
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.9MB of archives.
After unpacking 82.3MB of additional disk space will be used.

```

Now it works :) YAY

---

### Post by doomster on 2007-07-20
flawless install. ty

---

### Post by xjoelx on 2007-07-21
anyplace to download the source file? website is down for me so the script cannot download it.

---

### Post by jaffamuffin on 2007-07-21
[http://mupen64.emulation64.com/down.htm](http://mupen64.emulation64.com/down.htm)

---

### Post by vsegers on 2007-07-30
thank you thegreenblob, this is really amazing.

---

### Post by Drunken Swagger on 2007-07-31
I used the script and Mupen opens perfectly and I can load ROMS & change settings, bet when I start the emulation, my screen flashes and then Mupen disappears.

---

### Post by thegreenblob on 2007-08-01
> **Drunken Swagger said:**
> I used the script and Mupen opens perfectly and I can load ROMS & change settings, bet when I start the emulation, my screen flashes and then Mupen disappears.

Try changing the plugins in the settings. May be caused by one of them.

---

### Post by Drunken Swagger on 2007-08-01
I tried all the combos I could think of...

Could it be that I don't have the proper drivers installed? I was using a GeForce2 MX200 when I installed Ubuntu, and now I have switched to a FX5600. Also, I don't have the real drivers installed, just the included basic driver.

---

### Post by thegreenblob on 2007-08-02
It may be I guess. Though not really sure.

---

### Post by Xx_Isaac_xX on 2007-08-04
Whenever i get in mupen64 it will run just fine and the rom will load just fine but when i play the rom it will play for a minute then it will lock my whole computer up and i have to hit the restart button. Ive tried 2 diffrent mupen64 emulators and my zsnes works. I've also tried a few diffrent roms from diffrent sites. My video card also is working fully its a ATI Radeon x1600 pro. My other 3d games work like open arena. PLZ HELP ME !!!!!!!!!!!!!!!!!!

---

### Post by stewy.23 on 2007-08-05
this is what happens for me. Im using xubuntu

adam@adam-desktop:~$ sudo sh Mupen64-Script-thegreenblob.sh
sh: Can't open Mupen64-Script-thegreenblob.sh

---

### Post by thegreenblob on 2007-08-07
> **stewy.23 said:**
> this is what happens for me. Im using xubuntu

adam@adam-desktop:~$ sudo sh Mupen64-Script-thegreenblob.sh
sh: Can't open Mupen64-Script-thegreenblob.sh

Are you sure thats the right location? Maybe try doing a "sudo sh (then just drag the script in the terminal)"... That may work.

Though if it is the right location... I'm not entirely sure..

And @Xx_Isaac_xX, I'm not really sure of the problem :/ But, I see you already made a thread asking for help.

---

### Post by leveliv on 2007-08-25
What do I do..it installed wrong

> failed to execute child process "mupen64" (No such file or directory) 
A dialogue box pops up.

---

### Post by thegreenblob on 2007-08-30
> **leveliv said:**
> What do I do..it installed wrong

 
A dialogue box pops up.

I suppose try reinstalling. Not really sure of the problem here. :???:

---

### Post by orko3001 on 2007-09-08
Hmm my computer won't read my gc disks. Do I have to download the roms?

Cheers

---

### Post by Merritt.kr on 2007-09-10
Ehh.. you mean gc= GameCube? Mupen emulates Nintendo 64, not GameCube, and if your computer is actually set up to hold the tiny GC disks, wow...

get yourself some N64 roms mate!

---

### Post by orko3001 on 2007-09-11
Yes sussed that out myself eventually :)

---

### Post by aphirst on 2007-09-20
Excellent. Best tarball-extracting script I've seen in days. Slick and smooth. I was far too lazy to work out how to allocate time between manually typing commands and writing AS Chemistry papers, but it seems all that has been delayed by another 3 1/2 seconds :P .

Surprisingly enough (!) it worked on my 64 bit box, but that figures since I already have all of the 32 bit libraries.

Thanks again.

Edit: Even works perfectly in Gutsy! Well done!

---

### Post by Azzco on 2007-11-02
The install script rus perfectly for me aswell in gutsy, the only problem I have is some setting in mupen. I'm not sure if this is the correct place to ask for help but still.

The first 2-3 minutes of gameplay is perfect, but after that everything starts to lag stopping the emulation with the esc button is not possible and I have to kill the proccess. Any ideas?

---

### Post by emreywiley on 2007-11-11
I am currently running Gutsy, and this script ran perfectly. Thanks again!

---

### Post by Ricky_G on 2007-11-14
This script worked perfectly and mupen64 runs just fine on my P4 computer running gutsy.  However, when i tried running it on my PS3, also running gutsy, the script completes without error, but when i click on the icon a terminal window flashes on the screen for a split second then disappears.

i'm wondering if maybe this is a problem with the PPC vs ix86 processor architecture, because the cell in the PS3 runs PPC Ubuntu?  i'm not sure just throwing it out there.

anyone able to confirm or deny this?  or is there anyone who knows how to make mupen64 work on PS3 running gutsy?

---

### Post by tab0u on 2007-11-18
This script worked perfectly.I have a strange problem with mupen.I cant choose another video plugin in configure except from TR64 OpenGL v0.7.8.I have checked the plugins folder.Any ideas?

---

### Post by lift28 on 2007-11-28
could you please  make up a "mupen64_nogui" - i been trying to compile it for days can not seem to get it right:( --or give me a clue

the script work great thanks

---

### Post by compsariomike on 2007-11-29
Alright, 

So I got Mupen64 to install and it ran two or three times and worked fine...almost.  I'm new to emulators and Linux.  I have the rom for Ocarina of time.  I loaded it and ran it and it worked like twice but it flashed "no controller" at the bottom of the screen.  So I stopped the emulation and configured the controller to use my keyboard.  Now, everytime i try to emulate, it freezes.  

WHAT CAN I DO!!!  ME WANT ZELDA!!!!

thanks

---

### Post by lift28 on 2007-12-13
Here is a link [http://www.emutalk.net/showthread.php?t=42770]("http://www.emutalk.net/showthread.php?t=42770")to a nice build works fine after you install SDL_ttf (use adept_manager - search for "SDL_ttf " )
also has mupen64_nogui. thier is a build for amd64 :)

---

### Post by Moonfrost on 2007-12-14
Ok first of all hi everybody! second of all...I have an issue...every time I try to start a rom (I double-click it or just go to play rom) and every time I try that Mupen closes itself...anyone know what might be causing this? I'm kinda new to Linux and specially to Ubuntu so if anybody could give me any detailed help it would be greatly appreciated!

---

### Post by Dwiman89 on 2007-12-15
where do you get games at?

---

### Post by Marfish on 2007-12-16
Heya, I tried it the way you explained, but it says it cant move it to a sudirectory of itself. Im new to linux and I dont know what to do. Heres the report, any help wouls be much appreciated:
marlon@marlon-laptop:~/Desktop$ sudo sh Mupen64-Script-thegreenblob.sh
[sudo] password for marlon:
--09:33:28--  [http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2](http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2)
           => `mupen64-0.5.tar.bz2'
Resolving mupen64.emulation64.com... 62.75.221.236
Connecting to mupen64.emulation64.com|62.75.221.236|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,880,623 (1.8M) [application/x-tar]

100%[====================================>] 1,880,623     58.18K/s    ETA 00:00

09:33:58 (60.46 KB/s) - `mupen64-0.5.tar.bz2' saved [1880623/1880623]

mupen64-0.5/
mupen64-0.5/mupen64
mupen64-0.5/mupen64.ini
mupen64-0.5/whatsnew.txt
mupen64-0.5/save/
mupen64-0.5/save/empty
mupen64-0.5/doc/
mupen64-0.5/doc/readme.pdf
mupen64-0.5/doc/HiRezTexture.txt
mupen64-0.5/lang/
mupen64-0.5/lang/catalan.lng
mupen64-0.5/lang/pt_BR.lng
mupen64-0.5/lang/german.lng
mupen64-0.5/lang/spanish.lng
mupen64-0.5/lang/dutch.lng
mupen64-0.5/lang/italian.lng
mupen64-0.5/lang/english.lng
mupen64-0.5/lang/french.lng
mupen64-0.5/plugins/
mupen64-0.5/plugins/blight_input.so
mupen64-0.5/plugins/dummyaudio.so
mupen64-0.5/plugins/glN64.so
mupen64-0.5/plugins/jttl_audio.so
mupen64-0.5/plugins/mupen64_audio.so
mupen64-0.5/plugins/mupen64_input.so
mupen64-0.5/plugins/mupen64_soft_gfx.so
mupen64-0.5/plugins/mupen64_hle_rsp_azimer.so
mupen64-0.5/plugins/ricevideo.so
mupen64-0.5/plugins/RiceVideo6.1.0.ini
mupen64-0.5/plugins/Glide64.so
mupen64-0.5/plugins/Glide64.ini
mupen64-0.5/plugins/tr64gl.so
mupen64-0.5/jttl_audio.conf
mupen64-0.5/mupen64_icon.png
mv: cannot move `mupen64-0.5' to a subdirectory of itself, `/usr/local/games/mupen64-0.5'
#!/bin/bash 
/usr/local/games/mupen64-0.5/mupen64
rm: cannot remove `mupen64-0.5.tar.bz2': No such file or directory
[Desktop Entry]
Type=Application
Name=Mupen64
Exec=mupen64
Comment=An N64 Emulator.
Icon=/usr/local/games/mupen64-0.5/mupen64_icon.png
Terminal=false
Categories=Application;Game;ActionGame;GameAction;ActionGames;GamesAction;

---

### Post by DaH-RaT on 2007-12-25
Thank you, this works great in Gutsy :)

---

### Post by dave00001 on 2008-01-02
I am having a similar problem to yours, Marfish.... has anybody else experienced problems like this??

---

### Post by Intuvati on 2008-01-04
ok so i have all the ".so"s in the plugins folder, but apparently it doesn't like them very much. i have the same problem when i get the tarball from the webiste.

--------------

ryan@ryan:~$ mupen64
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/Glide64.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/mupen64_soft_gfx.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/ricevideo.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/mupen64_hle_rsp_azimer.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/glN64.so': libstdc++.so.5: cannot open shared object file: No such file or directory

-----------

i googled this problem but the only other report of it was some russian person so..... any ideas? i'm running a fresh install of gutsy (gnome) and i just started playing roms a little while ago (legend of zelda). oh yeah, great script, works great.

---

### Post by Intuvati on 2008-01-04
oh nvm i just hadnt installed libstdc++5  but after a quick search in synaptic, all is fine now :D

---

### Post by hankhendrix on 2008-01-08
if anyone is still havin the problem of mupen64 not loading roms after good installation try going into the configure and changing your cpu core from Dynamic Recompiler to Interpreter.
hank

---

### Post by kranky on 2008-01-12
Hi,

I ran the installer without problems, but when I try and start mupen64 from the command line I get the following error:
   error while loading shared libraries: libSDL-1.2.so.0: wrong ELF class: ELFCLASS64


I also tried directly downloading mupen from the website, and when I try running that one I get this error:
   error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I tried the solution suggested here - [http://ubuntuforums.org/showthread.php?t=650823&highlight=libgtk](http://ubuntuforums.org/showthread.php?t=650823&highlight=libgtk) - but I apparently have those packages installed already.


Could someone help with this?  I'm running Feisty Fawn.  Thanks in advance!

---

### Post by aphirst on 2008-01-28
This looks like the libSDL-1.2.so.0 is the 64-bit version. The 32-bit version is needed in either /lib32/* or /usr/lib32/* . You can get the 32-bit version from the ubuntu package resource on t'interweb. OR, you can use a script on these forums called "getlibs" (the URL eludes me for the time being...) to get the 32-bit libraries.

*wishes luck*

---

### Post by casper911ca on 2008-03-16
Is anyone having problems getting thier USB contoller to work.

Yes, I've hit the "plugged button" on Blights plugin, and i have linked the files, and i have installed joystick controllers, and all that jazz.

Im using a PS2 to USB adapter, and it works fine in Frets on Fire and other games that allow external inputs; the joystick controllers sense the device just fine, what could i be missing...

7.10 Gutsy
Mupen64 v.0.5

---

### Post by drgnfang on 2008-03-26
i'm an ubuntu noob, but when i tried to open the script it said:

drgnfang@drgnfang-desktop:~$ sudo sh Mupen64-Script-thegreenblob.sh
[sudo] password for drgnfang:
sh: Can't open Mupen64-Script-thegreenblob.sh

what am i doing wrong???

---

### Post by petey220 on 2008-03-30
OK i installed mupen64 works perfectly until i tried to open up a ROM, it just crashes, what am i doing wrong? the ROM is a zip file which i used on project 64 on windows:confused:

---

### Post by Tobi-fp on 2008-04-08
You are brilliant, thanks a lot from a noob :D

---

### Post by weapon273 on 2008-04-22
I have the same problem as Marfish. Has anyone been able to figure out how to get mupen64 to appear insudirectory?

---

### Post by DirtDawg on 2008-04-22
For the interested, there is also mupen64 plus found here: [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

Simply download the version you need (Mupen64Plus-1-3-bin-32.zip for example), extract the zip wherever you like, then double-click the mupen64plus binary to run.

---

### Post by Aeph on 2008-04-27
> **drgnfang said:**
> i'm an ubuntu noob, but when i tried to open the script it said:

drgnfang@drgnfang-desktop:~$ sudo sh Mupen64-Script-thegreenblob.sh
[sudo] password for drgnfang:
sh: Can't open Mupen64-Script-thegreenblob.sh

what am i doing wrong???

Try sudo sh ~/Desktop/Mupen64-Script-thegreenblob.sh or wherever you have the file.

---

### Post by Marti9 on 2008-05-29
I installed it, and found it in "Advanced mode" (Applications->Games->Mupen64). I started it, it looked like it should start, but then it suddenly dissappear.

What can I do?

---

### Post by inportb on 2008-05-29
> **DirtDawg said:**
> For the interested, there is also mupen64 plus found here: [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

Simply download the version you need (Mupen64Plus-1-3-bin-32.zip for example), extract the zip wherever you like, then double-click the mupen64plus binary to run.

Indeed, mupen64plus is the way to go. It works... period. You can get the deb package at [http://www.getdeb.net/app/Mupen64Plus](http://www.getdeb.net/app/Mupen64Plus)

---

### Post by Marti9 on 2008-05-29
Now i could start it, but when I loads a rom, nothing happens.

I tried mupen64plus too, but I couldn't open the mupen64plus-file when I had extracted.

---

### Post by bsatchmo on 2008-06-22
> **Marti9 said:**
> Now i could start it, but when I loads a rom, nothing happens.

I tried mupen64plus too, but I couldn't open the mupen64plus-file when I had extracted.

Same for me, I have it open a rom and nothing happens. I just end up having to force quit.

---

### Post by fordfairmont on 2008-08-27
Ok install worked a treat great :)

But now when i open a rom then game screen pops up but remains black.....

HELP NOSTAGLIC NOOB NEEDS ASSITANCE

---

### Post by InfinityCircuit on 2008-08-28
Mupen64Plus is also in my PPA for Hardy if people want it.  If you have video troubles you should try a different video plugin.

---

### Post by tjaisgay69 on 2008-09-19
Mine worked perfectly well but when i click start emulation, it gives me heaps of choices and no matter which one i click, the emulation screen goes black and doesnt change.:confused:

---

### Post by Joshua Wells on 2008-11-26
i am having a... different problem... i run mupen64 fine, i load conkers bad fur day fine, i run it, and it all wierd when it plays. the characters are all mushed up, and they are all triangley. i need help:confused:

---

### Post by chocolate_sk8er on 2008-12-23
austin@austin-desktop:~$ sudo sh Mupen64-Script-thegreenblob.sh
[sudo] password for austin: 
sh: Mupen64-Script-thegreenblob.sh: No such file or directory
austin@austin-desktop:~$ 

can someone help me? please?

---

### Post by chocolate_sk8er on 2008-12-23
austin@austin-desktop:~$ sudo tar xvfj mupen64-0.5.tar.bz2
[sudo] password for austin: 
tar: mupen64-0.5.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
austin@austin-desktop:~$ 



what should i do

---

### Post by rennikz on 2009-01-01
i got the same problem as nemesis or whoever his name is it install but nothing happens when i click on mupen

---

### Post by Danoz on 2009-01-01
Is it okay to bump this?

I'm having trouble getting Mupen64 to work correctly. I've tried an installation scrip (which didn't work) and I also tried running it from my home directory. It *opens*, but when I try to play something (testing with Mario64) the program either goes to black screen or crashes. Am I missing critical info?

Just a sidenote, I run a Windows Vista partition and can play Project 64 flawlessly. However, I'd very much like it if I didn't have to load Vista to use this program :).

Thanks!

---

### Post by DirtDawg on 2009-01-02
> **Danoz said:**
> Is it okay to bump this?

I'm having trouble getting Mupen64 to work correctly. I've tried an installation scrip (which didn't work) and I also tried running it from my home directory. It *opens*, but when I try to play something (testing with Mario64) the program either goes to black screen or crashes. Am I missing critical info?

Just a sidenote, I run a Windows Vista partition and can play Project 64 flawlessly. However, I'd very much like it if I didn't have to load Vista to use this program :).

Thanks!

If you haven't already, try [Mupen64 Plus]("http://code.google.com/p/mupen64plus/"). The original Mupen64 is, I think, a dead project, but this fork continues to be developed. You may have more luck with it.

---

### Post by Wilabob on 2009-01-09
I used the script as described and I have the mupen64 icon in my games but when I try to run it (click on it) it doesn't start and I have no idea what to do.. Any ideas?

Justin

---

### Post by Magical Tiger on 2009-04-26
Great script, thanks.

---

### Post by easeee on 2009-06-01
Same problem as Marfish. Dayum.

---

### Post by DirtDawg on 2009-06-01
> **easeee said:**
> Same problem as Marfish. Dayum.

Use [Mupen64 Plus]("http://code.google.com/p/mupen64plus/"). It's actively developed and there's no need for any scripts. Simply download, unzip and run.

Maybe it's time for a "HOWTO: Install Mupen64 Plus" thread since Mupen64 is deader than dirt.

---

### Post by Kenny301 on 2009-06-19
im having the same problem with [B]Danoz. i start the rom and the emuulator starts and stays blank then crashes.
[/B]

---

### Post by afroman10496 on 2009-07-12
Yeah! Thanks! Super Smash Bros. and Super Mario 64!

---

### Post by kcit5 on 2009-07-29
Thanks a lot for your mini-guide, it worked brilliantly for me.

---

### Post by unimatrix on 2009-09-27
On Ubuntu 9.10 Karmic the sound doesn't work right. Because of pulseaudio the sound is skipping and is all jittery.

Any solutions for that?

---

### Post by afroman10496 on 2009-09-27
> **unimatrix said:**
> On Ubuntu 9.10 Karmic the sound doesn't work right. Because of pulseaudio the sound is skipping and is all jittery.

Any solutions for that?
how about switching to alsa or oss (click the sound icon on the panel and open volume control) or using a diferent driver for mupen64?

---

### Post by unimatrix on 2009-09-27
> **Afroman10496 said:**
> how about switching to alsa or oss (click the sound icon on the panel and open volume control) or using a diferent driver for mupen64?

I can't switch to ALSA/OSS in Ubuntu without breaking pretty much everything else.

And where do I get a different audio driver for mupen? I could only find "JttL's SDL Audio".

---

### Post by Roco1211 on 2009-10-01
Help please! I downloaded the script, opened the terminal, and put in the code, and nothing happens. I've tried this about 30 different times all with different punctuation so it's not that....
Help!

---

### Post by DirtDawg on 2009-10-02
> **Roco1211 said:**
> Help please! I downloaded the script, opened the terminal, and put in the code, and nothing happens. I've tried this about 30 different times all with different punctuation so it's not that....
Help!

In the first few sentences of the 2009 edit in the original post, there's a link for Mupen64Plus. Click it, download it, unzip it, use it. No script needed.

---

### Post by TwoToneSpirit on 2009-11-06
I was having audio problems in karmic and installing the following packages fixed it:

libsdl1.2debian-pulseaudio

---

### Post by Cenoforums on 2009-12-01
The sound I get is also choppy. I instaled the pulseaudio package, ending up with these installed (alsa had to be removed)

i   libsdl1.2debian - Simple DirectMedia Layer
c   libsdl1.2debian-allv- ...           
c   libsdl1.2debian-alsa - ...
p   libsdl1.2debian-esd   - ....            
p   libsdl1.2debian-nas- .....
p   libsdl1.2debian-oss  -...
i   libsdl1.2debian-pulseaudio  -...

and the problem is still the same.Anything I'm missing? What in-program settings are you using?

Godamnit pulseaudio never works, it's beyond description

---

### Post by ccphilly1984 on 2010-01-30
> **DirtDawg said:**
> In the first few sentences of the 2009 edit in the original post, there's a link for Mupen64Plus. Click it, download it, unzip it, use it. No script needed.


ummm... do i have to ruin it from terminal? or can i run it from the file manager? can i make a menu icon for it?

---

### Post by thegreenblob on 2010-02-07
> **ccphilly1984 said:**
> ummm... do i have to ruin it from terminal? or can i run it from the file manager? can i make a menu icon for it?

The latest version of mupen64plus actually doesn't come with a GUI, so you'll have to run it from the terminal, however you can still get the last version which comes with a GUI still.

[http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-64.tar.gz](http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-64.tar.gz) for 64 bit.
[http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-32.tar.gz](http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-32.tar.gz) for 32 bit.

That one comes with an install script which makes a menu icon and what not, or you can just run it from a folder. I actually still use 1.5 since the newest one doesn't seem to support my controller.

---

### Post by RDilus on 2010-02-17
works good thanks ^^ installed on my EEE pc 4G

---

### Post by jackhynes on 2010-04-03
This is a GTK GUI frontend I believe, though I haven't tried it yet: [http://www.emutalk.net/showthread.php?t=50438](http://www.emutalk.net/showthread.php?t=50438)

---

### Post by Axolotl9250 on 2010-05-23
When I used the script and typed in ```
mupen64
``` in the teminal I got the following: ```
Couldn't read config file '/usr/local/games/mupen64-0.5//mupen64.conf': No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/ricevideo.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/Glide64.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/glN64.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/mupen64_soft_gfx.so': libstdc++.so.5: cannot open shared object file: No such file or directory
Couldn't load plugin '/usr/local/games/mupen64-0.5/plugins/mupen64_hle_rsp_azimer.so': libstdc++.so.5: cannot open shared object file: No such file or directory

```
Then a GUI came up anyway, I try to load a ROM and I get: ```
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
rom size: 16777216 bytes (or 16 Mb or 128 Megabits)
file found
rom size: 16777216 bytes (or 16 Mb or 128 Megabits)
rom loaded succesfully
80 37 12 40
ClockRate=f
Version:1448
CRC: a4bf9306 bf0cdfd1
name: Banjo-Kazooie       
Manufacturer: Nintendo
Cartridge_ID: 4b42
Country : United States
size: 4096
PC= 80100400
md5 code:B29599651A13F681C9923D69354BF4A3
eeprom type:0
init timer!

```
I click play and it says ```
memory initialized

``` and then tells me to select a UCode (non of which are the game I wanted to play - Banjo-Kazooie) I select the first one anyway and I get ```
TR64GL : (II) Getting video info..TR64GL : (II) Setting video mode 640x480x32..demarrage r4300
dynamic recompiler
Signal number 11 caught:
    errno = 0 (Success)

```
I try it again and it doesn't even tell me to select UCode this time. :confused:

I'm a newbie(ish) to linux as it is and complete newbie to how these emulators work so any help is greatly appecited.
Thanks.

---

### Post by Axolotl9250 on 2010-05-23
Sorry, Forget the above post by me - I'm going to try and install mupen64plus instead.

---

### Post by David-IT on 2010-08-10
thank you worked flawless on ubuntu 10.04 :D and for anyone having problems using the script just copy mine but save the file to your desktop :D 
> sudo sh /home/david/Desktop/Mupen64-Script-thegreenblob.sh also in the /home/youraccname/desktop etc.. :DD

---

### Post by ncwalker2010 on 2010-11-13
This is interesting.

I have a home PC that I administer and my kids use.  I (on my logon) installed Mupen64Plus from the software center.  Then I logged out, and my son logged in to play it with HIS logon.

He runs it just fine.  No problems.

But now when I try and run it - no go.

His config screen in Mupen comes up filled in.  When I mimic his settings on my logon, I get the "Unable to read ini file from disk" error with Rice's 1.5.

I have looked through the Mupen directories looking for perhaps my son as the owner, but no. It's all set up to root and looks fine.  Any advice?

(I tried uninstalling and reinstalling from my logon, then me running first.  Same thing.  Hates all the logons but my sons who FIRST ran it).

---

### Post by ncwalker2010 on 2010-11-13
Well I solved my own problem.

In .config\mupen64plus are all the config files.

I had them all, but they were all 0 bytes in size.  (No idea why).

In all the other logons, they were NOT zero length files.  So I copied someone else's directory into mine and everything worked fine.

---

### Post by ctballer_52 on 2011-02-04
Hi I understand this is a VERY old thread but I am extremely new to linux and the whole command line and need some help installing this.  When I go to type it all in it says Permission Denied.  Could someone spell this out step by step so that I can just type it into the terminal and download?  I have linux mint 9, and I have downloaded the script in my Downloads file.  Thanks!

---

### Post by masterrob213 on 2011-02-23
im having a little trouble im trying to do sudo sh Mupen64-Script-thegreenblob.sh but it says it can't open it where did i mess up at?

---

### Post by mips on 2011-03-01
@masterrob213 & ctballer_52
See [http://ubuntuforums.org/showthread.php?t=1686384](http://ubuntuforums.org/showthread.php?t=1686384)

---

### Post by TheSmartestGuyYouKnow on 2011-09-02
thnx this helped so much

---

### Post by dukevoytek on 2011-10-17
For those of you who are still confused its available in the software center! Took me two hours to try that one :p

works perfectly, not the same thing using a keyboard though!

---

### Post by colostomeboy on 2012-02-01
i feel really dumb, but I'm not sure what you mean by running the script and opening the terminal, if anyone could post some more details or a video that could help that would be great, I am using a mac version 10.6.8, maybe about 6 or 7 years old.

---

### Post by maidenman on 2012-02-10
Works fine! Tks!

---

### Post by soryu on 2012-06-14
which one in the software center do i install?

---

