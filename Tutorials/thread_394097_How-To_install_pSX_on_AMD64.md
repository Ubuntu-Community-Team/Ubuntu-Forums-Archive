---
title: "How-To: install pSX on AMD64"
date: 2007-03-26
forum: Tutorials
---

### Post by dfreer on 2007-03-26
**Version 1.13, along with some new changes! Also check out Ultima's pSX frontend!**
**F.A.Q.**
[LIST]
[*]***What is pSX?*** - Originally a windows Playstation 1 Emulator, it has recently been ported over to linux. The website can be found at [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/) Please note that I did not create this software, only this how-to :D
[*]***Is pSX open-source?*** - No. It is free to use as in free beer, but pSX author has prefered to not open up the source code. I simply repackage the executable, which also means that as long as you install the correct libraries, you don't even need to use my package. I just provide them for ease of use.
[*]***Ok, so why should I use this instead of ePSXe, pcsx, etc?*** - pSX has all plugins built into the emulator, so there is no need to find plugin's and configure them. Also, I was experiencing low framerates when using ePSXe (one of the best Playstation emulators for i386 IMO) on my AMD64 system, so I looked around for an alternative. Works great on both systems!
[*]***Can I play PS2 games on this emulator?*** - Although it does have an option to load a PS2 BIOS in the configuration, the bottom line is you can't. You can check the official pSX forums for exactly what you can accomplish PS2 wise, in the meantime check out PCSX2.
[*]***Why don't you include these packages in the official Debian/Ubuntu repositories?*** - Short answer: I do not want to. There are several reasons for this, but the main thing is pSX is not quite up to par with debian/ubuntu package requirements, and I'm not nearly adept at actually making the debian packages, I hack mine together using sudo dpkg -b *foldername* *filename.deb* which is pretty much on par with using checkinstall. **EDIT:** pSX as of version 1.13 has been changed to conform more to linux guidelines. It may very well be possible to include pSX in the non-free repository, although ATM I am not interested in dealing with that mess. Anyone who wishes to do so has my full support.
[*]***pSX refuses to accept controller input, wtf?*** - Make sure you are using controller type SCPH-1010, and see if that fixes the problem. Dual-shock SCPH-1200 works AFAICT in games that *support* it, games that don't will often refuse to accept the controller input. Also, SCPH-1150 does not appear to work at all from my limited testing.
[*]***I use Nvidia, and when I run psx32 in terminal I get a segmentation fault. What should I do?*** - This as been reported to happen occasionally [http://psxemulator.proboards54.com/index.cgi?board=bugreports&action=display&thread=1187624682](http://psxemulator.proboards54.com/index.cgi?board=bugreports&action=display&thread=1187624682)
One bit of advise is to make sure you are running the latest nvidia drivers. If this still doesn't solve the problem, you may need to check with the psx forums for further answers. One good thing about pSX is that there have been 3 new versions just in the last year or so, all of which actively fix bugs and add features.
[*]***pSX, mupen64, and/or ZSNES segfault and I can't figure out why!*** - [rcsdnj]("http://ubuntuforums.org/member.php?u=135017") reports that the "Data execute prevention" on x86_64 processors may be the cause of a segmentation fault. I haven't tried this myself, so proceed with caution:
> **rcsdnj said:**
> 
To stop , I first did it by going to the BIOS and disabled the "XD Technology" option. Since I didn't want to disable it globally, I looked for a way to disable and I found this:

- install prelink package ( sudo aptitude install prelink - I'm not sure about the package name, I'm not in my Ubuntu machine right now)

- run the executable you want to disable the XD technology by using:

execstack -s program_name

I'm not saying this is the solution for the problem, but it's maybe a good test.
[*]***I'm having XYZ problem with the emulator...*** - In general, almost all problems people have been having have to do with the way I packaged the files, and not the emulator itself. This includes memory cards not saving information, the emulator asks for the location to the BIOS each time, screenshots not saving at all, etc. The following method will solve these problems almost everytime (be sure to **BACKUP** all of your saved games somewhere before you follow this method!!!!):
```
sudo dpkg -p psx # 32-bit users only
sudo dpkg -p psx32 # 64-bit users only
sudo rm -Rv /usr/local/games/psx/ # 32-bit users only
sudo rm -Rv /usr/local/games/psx32/ # 64-bit users only
sudo apt-get clean
sudo apt-get update
sudo apt-get install psx # 32-bit users only
sudo apt-get install psx32 # 64-bit users only
```
[/list]

**Installation Instructions**
Copy the following into *Applications > Accessories > Terminal*:
Ubuntu 7.10 "Gutsy" AMD64 & i386:
```
echo "deb http://packages.dfreer.org gutsy main" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```

Ubuntu 7.04 "Feisty" AMD64 & i386:
```
echo "deb http://packages.dfreer.org feisty main" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```

All AMD64 Users:
```
sudo apt-get install psx32
sudo apt-get install psx32frontend
```

All i386 Users:
```
sudo apt-get install psx
sudo apt-get install psxfrontend
```

**How to uninstall**
```
sudo apt-get remove psx #32-bit users only
sudo apt-get remove psx32 #64-bit users only
```







**(OLD)** AMD64 Manual How to Install:
```
sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk
cd ~/
wget -c http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.0.6-2.1ubuntu1_i386.deb
sudo dpkg -x libgtkglext1_1.0.6-2.1ubuntu1_i386.deb libgtkglext
sudo mv -v libgtkglext/usr/lib/* /usr/lib32/
sudo rm -Rv libgtkglext
sudo rm -v libgtkglext1_1.0.6-2.1ubuntu1_i386.deb
wget -c http://psxemulator.gazaxian.com/pSX_linux_1_11.tar.bz2
tar xvf pSX_linux_1_11.tar.bz2
sudo rm -v pSX_linux_1_11.tar.bz2
cd pSX/
./pSX
```

How-to uninstall pSX (**AND** the 32-bit libraries):
```
sudo rm -Rv ~/pSX
sudo rm -v /usr/lib32/libgtkglext*
sudo rm -v /usr/lib32/libgdkglext*
sudo apt-get remove ia32-libs ia32-libs-sdl ia32-libs-gtk
```

Let me know if you have any problems!!

---

### Post by Ossot on 2007-04-01
You sir, are my hero. 

Installed ubuntu for the first time saturday after years of not using linux. Tried every tutorial I could find on getting pcsx and the other to work, neither would. Tried downloading pSX from their site and running it. After apt-getting 300+ megs of random gtk files it still wouldn't run.. that is until I happened upon this. 

I can finally 100% do away with windows. Thanks again bro.

---

### Post by dfreer on 2007-04-02
You're welcome! At least I helped somebody out :D
I actually like ePSXe (not pcsx too much, the GUI left much to be desired IMO), but getting all the plugins for it is a pain, and then configuring the video to run decently... 
As far as I have tested, haven't had any problems running any game on pSX (only tested on around 10-20 games). Let me know if you have any problems!

---

### Post by dfreer on 2007-04-03
Well, to make things easier I created two .deb files, one to install the 32-bit libgtkglext libraries, and the other to install pSX itself. I will include the links in the how-to above, and any help in testing the *.debs would be much appreciated!

---

### Post by dfreer on 2007-04-11
I have now included a i386 .deb for anyone who wants to try pSX. I added a changes.txt to the website, so now I will keep the website up-to-date with changes and just keep the links and install instructions here updated as needed.

---

### Post by RobinOfSweden on 2007-04-22
God i love you mate!
Finaly i can play my FFTactics again xD (my psx is so old it no longers loads my games *cries*)
Still having my shelf full off ps1 games i felt it such a waste!

And all the PCSX and ePSXe never worked for me on my Ubuntu Edgy 64 AMD64 DCore >_<
Then you show up like a knight in shining dark armor and saves my games! weee! thanks!

Regards from RobinOfSweden!

---

### Post by eponymous on 2007-04-23
sweet howto!
i'm playing dragon warrior 7 as i type this. thanks alot man.

---

### Post by dfreer on 2007-04-24
final fantasy tactics = awesome.
I'll have a new version out soon, should let you keep your conf files so that if you uninstall you don't lose all your settings.

---

### Post by eponymous on 2007-04-24
> **dfreer said:**
> final fantasy tactics = awesome.
I'll have a new version out soon, should let you keep your conf files so that if you uninstall you don't lose all your settings.

i'm reaching the end of my rope trying to get epsxe to work in x64 feisty so i'll keep an eye on this thread for your new version. thanks!

---

### Post by dfreer on 2007-04-25
Well, today is my birthday. So I decided to give you guys a birthday present. my 1.2 release of pSX 1.11 is now available to [_*download*_]("http://www.dfreer.org/~dfreer/pSX/pSX_latest_amd64.deb"). I'll update the how-to above, but it should be fairly simple to install. Fixed A LOT of things, so make sure you download it!

Note: make sure to backup any and all save files (memory cards, save states, configuration files, etc) BEFORE you uninstall. I should have things fixed now, but for awhile there it was deleting the memory cards on each uninstall :(

Please, let the creator of pSX know if you like this emulator. Only saying this so that credit is given where it's due (I just repackage the program :D ). [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

---

### Post by eponymous on 2007-04-25
thanks alot gonna give this a whirl tomorrow. epsxe "works" but is a pain, had to copy manually all the i386 files from my 32 bit computer to get it to run, i didn't know what i needed so i had to just keep running it and seeing what it asked for one file at a time. and after all that i don't have sound and got tired of messing with it.

and happy birthday!

---

### Post by eddyr on 2007-04-25
Hey, nice How-To

i'm having problems when i run pSX

"./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory"

I tried entering some of the commands for the i386 and i'm getting errors?

---

### Post by dfreer on 2007-04-25
Hmmm. That file is owned by libgtkglext1. You will need to install that with (in i386): 
```
sudo apt-get install libgtkglext1
``` 

Are you using my .deb files, or are you following the manual method? The newest i386 .deb should've depended on the libgtkglext1 package and installed it when it installed pSX...

---

### Post by eddyr on 2007-04-26
I tried both methods and no luck

I'm on a 32bit system by the way.

This is what i get when i use that command

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtkglext1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtkglext1 has no installation candidate
```

---

### Post by eponymous on 2007-04-26
it's probably looking in lib32 for it but for you it would just be in lib?
just a guess, since this is specifically a howto for 64 bit machines the folders are different.

---

### Post by dfreer on 2007-04-26
actually, it seems that it can't find libgtkglext1 in the repos. The i386 .deb has only been tested on feisty and edgy... tell you what. here's a direct link to [_*libgtkglext1*_]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkglext/libgtkglext1_1.0.6-2.1ubuntu1_i386.deb") from mirrors.kernel.org, and here's a link to the same file on [my site]("http://www.dfreer.org/~dfreer/pSX/libgtkglext1_1.0.6-2.1ubuntu1_i386.deb"). BTW, I am installing a new hard drive in the server today, so it may be down for an hour at tops.

> it's probably looking in lib32 for it but for you it would just be in lib?
just a guess, since this is specifically a howto for 64 bit machines the folders are different.

Good point. This how-to now covers pSX for AMD64 and i386... any ideas how to change the thread name to say as much?

---

### Post by GoBieN on 2007-04-26
Maybe its in universe/multiverse and he hasn't enbaled them ...

---

### Post by eponymous on 2007-04-26
so i'm getting the same errors as eddyr. except i'm on a 64 bit system.
when i try to install the libgtkglext1 package i get this error
```
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.0.6-2.1ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/share/doc/libgtkglext1/copyright', which is also in package ia32-lib-gtkglext1
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.0.6-2.1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dfreer on 2007-04-26
hmm. Looks like you might have a older version of my ia32-libs-gtkglext1 package. This is probably due to my changing the name of the package names around, confusing as to which file to download. I'll make some needed changes on the server for you guys, really sorry about that. The current version should only have 4 files to install, as shown here:
```
$ dpkg -c ia32-libs-gtkglext1_latest_amd64.deb 
drwxr-xr-x root/root         0 2007-04-21 02:31 ./
drwxr-xr-x root/root         0 2007-04-22 13:34 ./usr/
drwxr-xr-x root/root         0 2007-04-21 02:56 ./usr/lib32/
-rw-r--r-- root/root    314244 2007-04-21 02:56 ./usr/lib32/libgdkglext-x11-1.0.so.0.2.4
-rw-r--r-- root/root      9912 2007-04-21 02:56 ./usr/lib32/libgtkglext-x11-1.0.so.0.2.4
lrwxrwxrwx root/root         0 2007-04-21 02:56 ./usr/lib32/libgtkglext-x11-1.0.so.0 -> libgtkglext-x11-1.0.so.0.2.4
lrwxrwxrwx root/root         0 2007-04-21 02:56 ./usr/lib32/libgdkglext-x11-1.0.so.0 -> libgdkglext-x11-1.0.so.0.2.4
```

Also, the package libgtkglext1 for AMD64 WILL NOT work for pSX. What I have done with the AMD64 .deb was take the original 32 bit pSX binary, and repackage it so that AMD64 users can install it without having to use --force-architecture argument to dpkg. It is still a 32-bit binary, so it needs 32-bit libraries to run. So I also had to create a new package for libgtkglext1, taking the 32-bit libaries and putting them in a AMD64 package called ia32-libs-gtkglext1. You definitely would want to use this package to install the 32-bit libraries, because if you use --force-architecture it will install 32-bit libraries in the 64-bit library folder (/usr/lib instead of /usr/lib32), which would then BREAK any 64 bit application that depends on 64 bit gtkglext libraries.

Ok. so let's get things straightened out. If you are currently having problems, please backup all of your memcards, save states, screenshots, and BIOS files somewhere other than the /usr/local/games/psx/
Then do the following instructions to completely remove psx and files and then reinstall.


*Note: Since I did change the package names around, these commands to remove the old packages may not be exactly right. I kept track of all of the changes I did here: [http://www.dfreer.org/~dfreer/pSX/changes.txt](http://www.dfreer.org/~dfreer/pSX/changes.txt)

AMD64
```
sudo dpkg -P psx
sudo dpkg -P ia32-libs-gtkglext1 **[B]# In your case, eponymous, use *sudo dpkg -P ia32-lib-gtkglext1***[/B]
wget -c http://www.dfreer.org/~dfreer/pSX/ia32-libs-gtkglext1_latest_amd64.deb
wget -c http://www.dfreer.org/~dfreer/pSX/pSX_latest_amd64.deb
sudo dpkg -i ia32-libs-gtkglext1_latest_amd64.deb
sudo dpkg -i pSX_latest_amd64.deb

```

i386
```
sudo dpkg -P psx
sudo dpkg -r libgtkglext1
wget -c http://www.dfreer.org/~dfreer/pSX/libgtkglext1_1.0.6-2.1ubuntu1_i386.deb
wget -c http://www.dfreer.org/~dfreer/pSX/pSX_latest_i386.deb
sudo dpkg -i libgtkglext1_1.0.6-2.1ubuntu1_i386.deb
sudo dpkg -i pSX_latest_i386.deb
```

Again, sorry about the mess I made of the package names. I'm new to making debian packages, but these are the final package names (once I decide to become a developer and upload them to the ubuntu repositories, the names will have to change slightly but I'll keep the ones on my local server the same. Of course, if you use apt-get the .deb name won't mean a thing anyways since you would install it with sudo apt-get install psx ;) )

---

### Post by dfreer on 2007-04-27
feel free to remove post #20, oops.

---

### Post by eponymous on 2007-04-27
thanks alot hopefully i can try it out this weekend.

---

### Post by eponymous on 2007-04-28
i had to run some of the commands as sudo (was getting write permission denied with wget for your packages)
and it did not actually remove my folders for bios/memcards/etc

but i just did a real quick test and i got the boot screen from the Metal Slug X disc image, and it saved my two preferences that i set (sound card selection and bios file)

so bravo! thanks alot for your hard work, this is great. now to go get a gamepad!

---

### Post by dfreer on 2007-04-28
> **eponymous said:**
> i had to run some of the commands as sudo (was getting write permission denied with wget for your packages)

That's probably due to you running the command from a folder you do not have write permission to [e.g. /usr/local/games or something). Most users start terminal in their home folder, which is writable, so a regular wget *should* work. Either way, it makes no difference since you have to be root anyways to install the package.

> **eponymous said:**
> and it did not actually remove my folders for bios/memcards/etc

hmmm. dunno why it wouldn't, unless the folders weren't empty? i dunno, but it shouldn't be anything to be concerned about. 

> **eponymous said:**
> but i just did a real quick test and i got the boot screen from the Metal Slug X disc image, and it saved my two preferences that i set (sound card selection and bios file) so bravo! thanks alot for your hard work, this is great. now to go get a gamepad!

Awesome :D unless there is anything major that crops up, there should be only one more release (2.0 I should think). In that release I'll make a custom psx.png file (since the one it's currently using I found on google :-\" ), and create symbolic links in /usr/bin so that you can run pSX from the commandline simply by typing "pSX". But don't expect release 2.0 for awhile, I've got tons of other stuff to work on too lol.

---

### Post by dfreer on 2007-04-28
> **eddyr said:**
> Hey, nice How-To

i'm having problems when i run pSX

"./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory"

I tried entering some of the commands for the i386 and i'm getting errors?

eddyr, did you ever get it working?

---

### Post by geokker on 2007-04-28
I think I'm missing something. I want to play ps2 games on my LCD monitor but I can't find any sort of device that converts the tv-out on the box to 15-pin VGA. So, I thought I'd try this emulator. I assumed it would be a case of installing your goodies then slapping in a PS2 game disk into a drive. Instead, I run .psx and get:

"This emulator requires a BIOS image which must be installed in the bios folder."

Then a file browser appears with 'scph1001.bin' listed.

What gives? This isn't something ridiculous like digging a hardware component out of the console I hope.

---

### Post by JKing on 2007-04-28
> **geokker said:**
> I assumed it would be a case of installing your goodies then slapping in a PS2 game disk into a drive.
pSX is a PlayStation emulator, not a PlayStation 2 emulator (yet?).


> "This emulator requires a BIOS image which must be installed in the bios folder."
What gives? This isn't something ridiculous like digging a hardware component out of the console I hope.
More or less, yes.  You can dig up instruction on how to produce a BIOS image, or you can hunt down an image on the Web.  They're not that hard to come by, but they are illegal to distribute since the BIOS is copyrighted software.  That's just how it is, unfortunately.  All free PlayStation emulators are like this.

---

### Post by eddyr on 2007-04-29
> **dfreer said:**
> eddyr, did you ever get it working?


Yes it works perfectly now on my 32bit machine thanks!

One question tho, will this emulator allow you to swap disc( cd image ) when playing games which have 2 or more cds?

---

### Post by dfreer on 2007-04-29
> **eddyr said:**
> Yes it works perfectly now on my 32bit machine thanks!

One question tho, will this emulator allow you to swap disc( cd image ) when playing games which have 2 or more cds?

hmmm... good question!! I have yet to get far enough in my multi-disc games to try it out... ummm I guess the easiest test would be to break out Riven for PSX, since each disc was a world and you could teleport between worlds fairly quickly in the game. Lemme get back to you after I find my Riven game and a Skip Dr :D. 

I assume it would support it. at very least if it doesn't you could save state when the dialog tells you to insert a game disc, power off pSX, insert disc 2, load state and hit "ok". That *should* work, although I'm just guessing here.

> **geokker said:**
> I think I'm missing something. I want to play ps2 games on my LCD monitor but I can't find any sort of device that converts the tv-out on the box to 15-pin VGA. So, I thought I'd try this emulator. I assumed it would be a case of installing your goodies then slapping in a PS2 game disk into a drive. Instead, I run .psx and get:

"This emulator requires a BIOS image which must be installed in the bios folder."

Then a file browser appears with 'scph1001.bin' listed.

What gives? This isn't something ridiculous like digging a hardware component out of the console I hope.

scph1001.bin is the BIOS for the original playstation, often-times referred to as PSX (not to be confused with PSOne). You are on your own on how to obtain one, as it is quite illegal here in the US (dunno about other countries but even so, like living in another country has stopped the US from busting in doors and taking your **** before). Remember, google is your friend. Also, I know the xbox had a cord to connect it to a VGA monitor, but once again I dunno about the PS2, try google. Once you have that BIOS, it pretty much is a "case of installing my goodies and slapping in a PS1 game disk (or image)".

I asked the pSX author about this awhile ago, here's his response regarding the option to load a PS2 bios in the configuration:
[QUOTE=me]Ok, sounds good. I'll try to get the howto up in about a week, I want to try
installing it on a vanilla AMD64 install to make sure it works. Also, I'll
probably add an entry to ubuntuforums.org, it seemed like some other people
were having problems with getting an Playstation emulator working. It isn't
too hard at all to install.
BTW, I noticed that in the configuration you can point to a Playstation 2
bios, but I couldn't seem to get it to work at all. Is there PS2 support in
pSX?[/QUOTE]
[QUOTE=psx_author]It does have PS2 support but it doesn't run any games yet...[/QUOTE]
Short and sweet. Hopefully PS2 will be supported in future versions.

---

### Post by eponymous on 2007-04-30
if you own a ps2 and want to play through your computer monitor the easiest way (which in linux isn't easy at all) is to get a TV tuner and run your ps2 through that, until there's a working emulator for ps2 games.

---

### Post by eddyr on 2007-04-30
> **dfreer said:**
> hmmm... good question!! I have yet to get far enough in my multi-disc games to try it out... ummm I guess the easiest test would be to break out Riven for PSX, since each disc was a world and you could teleport between worlds fairly quickly in the game. Lemme get back to you after I find my Riven game and a Skip Dr :D. 
.

I inserted disc 2 in just so it prompts me for disc 1 ( haven't completed disc 1) and have yet to make a successful image swap.

just curious.

---

### Post by dfreer on 2007-04-30
> **eddyr said:**
> I inserted disc 2 in just so it prompts me for disc 1 ( haven't completed disc 1) and have yet to make a successful image swap.

just curious.

it sounds like you were unable to make a image swap? my Riven discs are virtual unusable, so I tried your method of inserting the original disc 2 (of FFVIII, btw) until I came to the prompt where it told me to please insert disc 1. pressing eject on the CD drive resulted in a "Unable to eject medium" error, and so I went to File > Eject CD in pSX. Then I pressed eject on my drive tray again and it ejected the CD. Inserted the original Disc 1, went to File > Insert CD Drive and then waited about 1 min (about 30 secs for ubuntu to load disc, and then another 30 or so for pSX to spin up and recognize disc). It worked fine, the opening FMV started playing. I will try to make an image of FFVII discs 1+2, and see whether using images is your problem. What format is your game CD in, like .bin, .ccd, .cdz, .iso, etc?

For those of you interested, a new .deb will soon be released with Ultima's (from pSX forums) [pSX Frontend for linux]("http://hostfile.org/psxfrontendv110linuxwip4tar.gz"). This frontend basically allows you to reach the undocumented commandline switches for pSX (like enabling the debugger), and also things like making custom settings for each game, and the ability to autoload the last saved state. It probably does more but I have yet to test it out fully. You can install the frontend alongside of pSX, and it makes absolutely NO changes to the original pSX binary or psx.ini file (so basically it will not mess up your settings). It IS a work in progress build, so anyone using it should report any bugs on [Ultima's thread]("http://psxemulator.proboards54.com/index.cgi?action=display&board=support&thread=1155421460&page=27#1177859745").

---

### Post by eponymous on 2007-04-30
this may be a dumb question but i don't see keymapping for quick save state, only quick load. am i missing it?

---

### Post by dfreer on 2007-04-30
the default keys are F1-F5 for quick load 1-5, and F6-F10 for quick save 1-5.
They are both listed under the "Quicksave" section on the default frontend, so you prolly just missed it.
It doesn't look like you can modify these keys (I looked through the psx.ini file and the configuration options).

BTW, if you have a PS2 BIOS you can run it through pSX, although you will need to know the commandline switch or Ultima's pSX frontend to do so. However, it sounds like running the BIOS is about all pSX can accomplish ATM, you may want to look into [pcsx2]("http://www.pcsx2.net/") for PS2 emulation.

Gotta go back to work, still gotta get the frontend and links fixed in the post above... *sigh*

---

### Post by dfreer on 2007-05-01
[http://www.dfreer.org/~dfreer/pSX/pSX-frontend_latest_all.deb](http://www.dfreer.org/~dfreer/pSX/pSX-frontend_latest_all.deb)

Here's ultima's frontend. Try it out see if you like it. It will install on top of the original pSX, and you can install/remove it without messing up pSX at all.

---

### Post by eddyr on 2007-05-01
> **dfreer said:**
> it sounds like you were unable to make a image swap? my Riven discs are virtual unusable, so I tried your method of inserting the original disc 2 (of FFVIII, btw) until I came to the prompt where it told me to please insert disc 1. pressing eject on the CD drive resulted in a "Unable to eject medium" error, and so I went to File > Eject CD in pSX. Then I pressed eject on my drive tray again and it ejected the CD. Inserted the original Disc 1, went to File > Insert CD Drive and then waited about 1 min (about 30 secs for ubuntu to load disc, and then another 30 or so for pSX to spin up and recognize disc). It worked fine, the opening FMV started playing. I will try to make an image of FFVII discs 1+2, and see whether using images is your problem. What format is your game CD in, like .bin, .ccd, .cdz, .iso, etc?

For those of you interested, a new .deb will soon be released with Ultima's (from pSX forums) [pSX Frontend for linux]("http://hostfile.org/psxfrontendv110linuxwip4tar.gz"). This frontend basically allows you to reach the undocumented commandline switches for pSX (like enabling the debugger), and also things like making custom settings for each game, and the ability to autoload the last saved state. It probably does more but I have yet to test it out fully. You can install the frontend alongside of pSX, and it makes absolutely NO changes to the original pSX binary or psx.ini file (so basically it will not mess up your settings). It IS a work in progress build, so anyone using it should report any bugs on [Ultima's thread]("http://psxemulator.proboards54.com/index.cgi?action=display&board=support&thread=1155421460&page=27#1177859745").

it's a .img file. Judging from your results, i believe it should work. I didn't really test it out....might  try it tonight.

---

### Post by allspiritseve on 2007-05-01
ok, I got everything working, but one last question: do I need actual ps1 discs to play? Or are they available online somewhere. All my old games are at home...

Cory

---

### Post by dfreer on 2007-05-01
well the actual ps1 discs that you own will work fine. and pSX can play images stored on the hard drive in .bin/.cdz image formats. We here at ubuntu forums will not condone the sharing of playstation games online, much less provide you with the means to find playstations CD's online, as we are upstanding citizens and blah blah blah. 

on a completely unrelated side note, here is my favorite bittorrent search engine site:
[http://www.isohunt.com](http://www.isohunt.com)
and my favorite online search engine:
[http://www.google.com](http://www.google.com)
and here is what I use to burn .ccd images to disc in windows:
[http://www.slysoft.com/en/download.html](http://www.slysoft.com/en/download.html)

---

### Post by eponymous on 2007-05-02
i'm pretty sure i've seen a disc or two in .img and other formats *magically* work in pSX. they are probably just misnamed.
basically a .bin file is the only thing you can be confident you'll work.

hmm yes [www.isohunt.com](www.isohunt.com) is a great place to get lots of public domain content. i hear some people use it for illegal stuff, shame on them.

i like utorrent (through wine) for a client. search these forums for the howto.

---

### Post by RobinOfSweden on 2007-05-04
Dfreer:
Hey there again, i updated to Feisty and it seems i have both problem updating and removing the old one :D
However the previus version (the one i used first and also wrote the reply about) still works perfectly fine :D:D

So well... wish i could update and test your new but it seems i cant :(
especialy since you mentioned that you had more fixes in it.
On the subject i have noticed that my configuration doesnt save my joypads settings. i need to reset the settings on the controllers everytime i start pSX.
If you know why please do tell me and if the solution is in the new version then i guess i am pretty screwd for a while :D

---

### Post by dfreer on 2007-05-04
hmmm. well, to begin with the problem with the settings can be fixed in the old one with this command:
```
sudo chmod a+w /usr/local/games/psx/psx.ini
```
But the new version is probably best. So what problem are you having with removing the old one? If nothing else works, you should be able to do a:
```
sudo dpkg -p psx
sudo dpkg -p ia32-libs-gtkglext1
sudo rm -Rv /usr/local/games/psx/
sudo rm -v  /usr/lib32/libgtkglext*
sudo rm -v /usr/lib32/libgdkglext*
```
That should get rid of EVERYTHING, so make sure to backup any memory cards/save states/BIOS/etc. Then try installing the new packages according to the how-to. Let me know if there are any problems!

(p.s. if there is an error on this command *sudo dpkg -p ia32-libs-gtkglext1*, try *sudo dpkg -p ia32-lib-gtkglext1* the package name got changed around once or twice.)

---

### Post by dfreer on 2007-05-06
ok, well you think this is easy to install? give me a couple more days, and I'll post instructions on how to add packages.dfreer.org as a repository. So no more having to manually download and install the newest version from my website (like it was that hard in the first place ;) ).

---

### Post by dfreer on 2007-05-08
it's up and running pretty smoothly. AFAIK, you shouldn't need to uninstall psx before you use this repository. just follow the newly updated how-to to add the repo, and then as soon as I get new versions out you will be able to apt-get update/upgrade to the newest version. also, zsnes 1.51 for i386 (because you can only get version 1.420 in the ubuntu repos) and amd64 (because I <3 amd64) is available from my repo as well.

---

### Post by dfreer on 2007-05-11
just to let anyone know who is using the repository:
the package name has changed once again, plus the default install directory because I like messing around with things. the howto at the beginning is once again updated. 

also release 2.0 is out!! everything i said would be there is there other than a custom psx.png. because, once again, I'm lazy and involved in too many other projects.

---

### Post by acoustibop on 2007-05-22
BTW dfreer, you might like to know that Ultima has just released the first full Linux version of his [frontend, v1.10]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263"). ;)

---

### Post by dfreer on 2007-05-22
> **acoustibop said:**
> BTW dfreer, you might like to know that Ultima has just released the first full Linux version of his [frontend, v1.10]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263"). ;)

Thanks! I had his thread bookmarked but evidently I missed the info. I'll see how it works and create a .deb on the repo ASAP. 

BTW, pretty much everyone should be using the repository now, I'm only updating packages on it (although I haven't changed too much lately).

---

### Post by dfreer on 2007-06-04
I'm thinking since pSX is pretty much stable now, with release 2.5, I'm not going to mess with the package anymore unless someone comes to me with a fix.
Right now, the AMD64 version works the best, you can launch it from either the commandline (psx32) or from the Gnome Menu (doubt it appears in KDE menu, if anyone has KDE and wants to test?). the 32-bit version is soon to follow. Just remember all new packages have been going to the repository, I haven't updated the [http://www.dfreer.org/~dfreer/pSX/](http://www.dfreer.org/~dfreer/pSX/) folder in quite awhile.

For some reason I have yet been able to get Ultima's frontend working on AMD64, python 32 is being too rough on me :(

---

### Post by fabertawe on 2007-06-05
Hi,

Any ideas on how to get an *.img.bz to work with pSX? I've bunzipped to an *.img and tried creating a corresponding *.cue with AceToneISO but pSX hangs when trying to open them. These images work fine with PCSX by the way.

Cheers ... Paul

---

### Post by dfreer on 2007-06-05
Sorry, I don't have any *.img files to try, much less a bunzipped one. The best place to find out would be to check the pSX forums:
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)
Unless someone who uses pSX here has tried this. Does the original .img file work (without bz)?

---

### Post by fabertawe on 2007-06-06
Nope, it tries to determine the format of the *.img but fails. I shall investigate further! Thanks for your help.

Paul

---

### Post by dfreer on 2007-06-06
[http://en.wikipedia.org/wiki/PSX_emulator#Supported_CD_Image_Formats](http://en.wikipedia.org/wiki/PSX_emulator#Supported_CD_Image_Formats)
hmmm dunno if this is true for the linux side, I don't see why not.

EDIT: you could just burn it to a disc, probably inconvenient but at least it would work!

---

### Post by fabertawe on 2007-06-07
I had a load of PS1 games which I donated to a charity shop to reclaim some space! I did however take images of some of my favourites to keep on a DVD (I'm obsessed with space it would seem ;)) for testing the emulators. So I'm stuck with these *.img.bz images now. I shall try your burning to disc idea when I get a chance and post back.

Cheers ... Paul

---

### Post by kekc on 2007-06-07
Sorry dfreer,

But why don't you going to maintain it in ubuntu team?
You could do much more if you propose it to Gutsy instead of buggy pcsx.

What is the license of PSX BTW?

PS sorry for my english.

---

### Post by dfreer on 2007-06-07
Hmmm. not a bad idea. I can't seem to find the license for pSX, other than the FAQ that states it is not open source (yet!). I send an email to the author asking him for permission to include it in the official repos, and details of the license pSX is listed under.

---

### Post by kekc on 2007-06-07
Oh, you are making zsnes also..
It would be also better then current gsnes9x.

Thanks for your job,
It would be a great pleasure for me to see them both in gutsy(7.10) or maybe next release.
I mean repository of course...

---

### Post by dfreer on 2007-06-07
zsnes is a bit of a different issue I think.
I haven't done much in the way of making packages, and although I seem to have done alright so far (except when I mess around with new things, sorry guys :) ), I'll have to modify the packages to go to the official repos. Not really much of a problem, just saying I don't have much experience.
Then there is the issue of the current zsnes 1.42 in the official repos. I don't know why the original maintainer hasn't felt the need to upgrade to 1.51 (because it is a LOT better, no more scratchy sound!), but I'll probably need to get in contact with him and get his permission, and then get the ZSNES developer's permission as well (great software, just not a friendly lot, IMO).

I can look into it, we've got a couple months before gutsy comes out. No promises though :)
In the meantime, how has my repository and the pSX/zsnes packages working? anyone have any problems? I'm particularly interested if the new updates are getting pushed out via apt-get update/upgrade.

EDIT: totally agree with gsnes9x... is it that hard to just copy zsnes UI? 
I really need to set my eyes into finding a good NES emulator for linux. I always thought the windows version of FCEUltra was pretty good, but the linux port is horrendous. Even with the guys working on gfceultra, it's UI is not that good. Too bad I don't have any programming skills myself :(

---

### Post by kekc on 2007-06-08
dfreer,

I'd like to wish you a good luck!
I think all ubuntu users that enjoy emulation will really appreciate you job.
For this moment we REALLY need good nes, snes and psx emulators.

I think you can start from here:
[https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)
[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

And don't forget, that it's better to merge debian package, than doing it yourself. So look on zsnes and psx in debian repository first.

And.. Don't forget abot dates [GutsyReleaseSchedule]("https://wiki.ubuntu.com/GutsyReleaseSchedule"):
June 21st DebianImportFreeze
...
August 16th FeatureFreeze, UpstreamVersionFreeze
...
August 30th NewPackagesFreezeUniverse

PS Sorry, if i'm trying tell you, that you already know

---

### Post by dfreer on 2007-06-08
Oh wow! Thanks for the info, didn't know anything about it. Yeah, lemme check on a few things...

I'm going to try to get pSX into Debian, but I don't know if it is possible without the source code. And I'll give the maintainer of zsnes for Debian an email, it looks like 1.51 made it to debian unstable, but x86 only :(

---

### Post by kekc on 2007-06-09
Hmmm,

I don't think you should create PSX debian package, if it doesn't exist.
It's better to create our own. Anyway, please, ask any questions in IRC or Ubuntu Development forum.
It could be also usefull to contact other emu packages maintainer.

Good luck!

---

### Post by dfreer on 2007-06-09
> **kekc said:**
> Hmmm,

I don't think you should create PSX debian package, if it doesn't exist.
It's better to create our own. Anyway, please, ask any questions in IRC or Ubuntu Development forum.
It could be also usefull to contact other emu packages maintainer.

Good luck!

I don't see why not? Ubuntu owes a lot of things to debian, it only helps the community to add it to both debian and ubuntu.

---

### Post by kekc on 2007-06-09
1) Because our aim is Ubuntu.
2) Because it could take some additional helpful time and energy.
3) Because you should wait for approval from Debian team also.
4) Because in future you should maintain them both.

IMHO maximum you can help debian community is create Ubuntu package as soon as possible and then post id Debian form (or somewhere else) request for this package in Debian repository. Debian community will include it if they like it. It's quite clear I think.

Another thing if you a Debian user first of all...

---

### Post by kingmob on 2007-06-10
I'm having trouble contacting your server. The update request as well as the key request are timing out. Is this temporary (in other words a known problem) or is it on my side?

---

### Post by dfreer on 2007-06-10
It looks like my router went down sometime last night, I'm looking into why. But the server should be ok now, go ahead and try it :) I tested it from the LAN and from a proxy on the internet, it's up now. Thanks for letting me know!

---

### Post by Drpwn on 2007-06-17
errors on dapper, amd64.

bash: ./pSX: No such file or directory

Has anyone gotten this to work?

---

### Post by dfreer on 2007-06-18
I'll grab a AMD64 Dapper Live CD and give it a try here ASAP. Note that on an AMD64 system, the program is located in /usr/local/games/psx32/ and has a system link to /usr/bin/

---

### Post by A_POET on 2007-06-21
hi ive installed 32bit pSX successfully, but, it doesnt recognize the "buttons" on my interact axispad controller  for some reason...it recognized the d-pad part, but i cant configure the buttons and nothing helps. anyone have any ideas? pad is working with mednafen and the like


any help is highly appreciated :) i really wanna play osme intelligent Qube ;)

---

### Post by wingnux on 2007-06-22
After selecting the bios (1st run) the emu crashes and I get this error on terminal:

"(pSX:5450): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:5450): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault (core dumped)"

If I try to run pSX after that my system freezes and I have to reset =/

---

### Post by dfreer on 2007-06-22
@wingnux 
can you tell me what you are running (AMD64/i386), what version of ubuntu you have, and how you installed pSX (from the repository or manual download)?

@A_POET
sorry, I don't have that gamepad. I know my logitech dual action works great, maybe someone else here or on the pSX forums can help you out :(

---

### Post by wingnux on 2007-06-22
I'm running the i386 build which I've downloaded/installed manually because when I try to install it using your tutorial I get the following error after "sudo apt-get install psx":

Package psx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package psx has no installation candidate

---

### Post by dfreer on 2007-06-22
hmmm. looks like another problem for me to look into. gah. try downloading the linux build of pSX from [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/). Just extract the files, and then in terminal cd into the folder and try running pSX from there. If that doesn't work, then I won't be able to help you :( you will most likely need to contact the pSX author. 

if it does work, it means there is a problem with my packaging, which I can definitely help you out with.

---

### Post by Thermal_unit_alpha on 2007-06-27
dfreer your tutorial is great. Thank you for your time and effort. I have been using Linux since kernel version 2.0, and I remember how difficult it was back then. These are the sort of projects that are turning Linux into "viable alternative" to Windows and OSX for desktop users. :guitar:

edit: wingnux, what version of Ubuntu are you running? Feisty, Edgy... Check your repository settings under /etc/apt/sources.list, make sure you are set using the right repository for your version  of Ubuntu (IE: deb [http://packages.dfreer.org](http://packages.dfreer.org) [your version of Ubuntu] main...). Good luck, I hope this helps you.

---

### Post by iceolate on 2007-07-04
Connecting to packages.dfreer.org|66.209.138.18|:80... failed: Connection timed out.

---

### Post by dfreer on 2007-07-04
> **iceolate said:**
> Connecting to packages.dfreer.org|66.209.138.18|:80... failed: Connection timed out.

That issue has been dealt with, thanks for noticing. I basically thumped my server with a fist. Specific details in this thread for the overly curious:
[http://ubuntuforums.org/showpost.php?p=2964155&postcount=81](http://ubuntuforums.org/showpost.php?p=2964155&postcount=81)

> **Thermal_unit_alpha said:**
> dfreer your tutorial is great. Thank you for your time and effort. I have been using Linux since kernel version 2.0, and I remember how difficult it was back then. These are the sort of projects that are turning Linux into "viable alternative" to Windows and OSX for desktop users. :guitar:

edit: wingnux, what version of Ubuntu are you running? Feisty, Edgy... Check your repository settings under /etc/apt/sources.list, make sure you are set using the right repository for your version  of Ubuntu (IE: deb [http://packages.dfreer.org](http://packages.dfreer.org) [your version of Ubuntu] main...). Good luck, I hope this helps you.

Thanks! :D yeah, I'm really floored how popular this thread became, I did a google for pSX and dfreer and found tons of copies of my guide. Also even when my server goes down for a couple of hours people pick up on it really quickly and let me know, which is a big help! 

As for Thermal_unit_alpha's advice for wingnux, actually all I have is a feisty pool, I can add edgy and dapper packages if the pSX package doesn't install in those distros and I find the appropriate fix. So the above advice is invalid :( for now at least. BTW, anyone who wants to help out can easily drop me a message!

---

### Post by Thermal_unit_alpha on 2007-07-05
Good to know. :o I apologize if I have misled anyone. :oops:

---

### Post by misterflibble on 2007-07-13
Thanks for the AMD64 packages for both zsnes and psx32, Dfreer!  No more fiddling around with chroots to fix zsnes's scratchy sound!  I have to confess though: I'm a Debian user, but your packages work great with it.  Maybe you should become the Debian maintainer for these, and they can be pushed down to Ubuntu ;)

I have one just one question though.  Ultima's frontend mentions that it allows access to command-line functions.  Just what are these functions?  Can I load a drive or an image from the commandline?  I can't find any documentation anywhere about this and this emulator's name does not lend itself well to google searches for info...

---

### Post by bluemech on 2007-07-13
**dfreer**, thanks for taking the time out to create a 64-bit package of this. :D I've tried ePSXe and I have to agree, pSX is much simpler and faster in its approach.

That being said, I have two questions:
1. You said you had a Logitech Dual Action controller. Does it work with any other gamepad type other than SCPH-1010 (the normal one) in pSX's controller configuration? Does using SCPH-1200 (the dualshock mode) suddenly render the pad unreadable? IIRC, I've read Linux PlayStation emulators cannot really utilize analog control, so I'm just wondering if it's really like that or if it's just me.

Ubuntu can read and detect both digital and analog pads just fine, it's the plugins in the emulators that are the problem I think. This was also my problem with ePSXe.

2. pSX doesn't save my configurations. Everytime I load it up it asks for the language I want to use. Directory paths are back to their defaults, and the controller buttons and sticks are not set. Again, is it really like this or is it just me?

Other than that, excellent work. Thanks again!

---

### Post by dfreer on 2007-07-13
> **bluemech said:**
> **dfreer**, thanks for taking the time out to create a 64-bit package of this. :D I've tried ePSXe and I have to agree, pSX is much simpler and faster in its approach.

That being said, I have two questions:
1. You said you had a Logitech Dual Action controller. Does it work with any other gamepad type other than SCPH-1010 (the normal one) in pSX's controller configuration? Does using SCPH-1200 (the dualshock mode) suddenly render the pad unreadable? IIRC, I've read Linux PlayStation emulators cannot really utilize analog control, so I'm just wondering if it's really like that or if it's just me.

Ubuntu can read and detect both digital and analog pads just fine, it's the plugins in the emulators that are the problem I think. This was also my problem with ePSXe.

2. pSX doesn't save my configurations. Everytime I load it up it asks for the language I want to use. Directory paths are back to their defaults, and the controller buttons and sticks are not set. Again, is it really like this or is it just me?

Other than that, excellent work. Thanks again!

(1) Hmmm. Lemme get back to you after I run some tests. AFAIK it should work, but I don't think I've tried it yet.

(2). May be from an older version. Since it is a configuration file it doesn't get removed/replaced when installing a new version of a package, and I hosed up some earlier versions. Simple fix:
```
sudo chmod a+rw /usr/local/games/psx32/psx.ini
```
This should fix things, if not try backing up all your save information and remove my pSX package with sudo apt-get remove --purge psx32, then reinstall normally.

Other things to check for, since you've had this problem. Make sure all of the directories (memcards, cdimages, etc) are chmod 755 and owned by yourself, or chmod 777. Whichever, the main thing is the screenshots and savestates on the older packages won't save unless you do this.

---

### Post by bluemech on 2007-07-13
> **dfreer said:**
> This should fix things, if not try backing up all your save information and remove my pSX package with sudo apt-get remove --purge psx32, then reinstall normally.

The purge fixed it, thanks.

Still wanting to see whether the dualshock mode works though (for now, I've been mapping the left analog joystick on the gamepad to the emulated digital gamepad, so I can "fake" the experience. haha :p)

---

### Post by misterflibble on 2007-07-15
I discovered why I couldn't get any commandline options; it's because the /usr/bin/psx32 command is a script that just calls /usr/local/games/psx32/pSX, and doesn't pass through any options.  I see why you can't just put a symlink in too, because pSX wants its config file in the same directory as the executable.  I'll just run the executable directly.

---

### Post by dfreer on 2007-07-15
> **misterflibble said:**
> Thanks for the AMD64 packages for both zsnes and psx32, Dfreer!  No more fiddling around with chroots to fix zsnes's scratchy sound! 

Thanks a lot! I'm really glad zsnes32 helped, because that was the hardest problem I encountered. Well, that's not quite true cuz I still need to get Ultima's Frontend working for AMD64 users :(

> **misterflibble said:**
> Maybe you should become the Debian maintainer for these, and they can be pushed down to Ubuntu ;) 

This has been discussed earlier. The problem I ran into was that whereas I can hack together a .deb, it isn't really the proper way of making packages, and I would also need to follow strict guidelines in order for the packages to get accepted into the official repositories. I would really like to see this happen, and I can definitely help someone who knows what they are doing, I just don't myself. So for now, I guess the answer is I can't.

> **misterflibble said:**
> I have one just one question though.  Ultima's frontend mentions that it allows access to command-line functions.  Just what are these functions?  Can I load a drive or an image from the commandline?  I can't find any documentation anywhere about this and this emulator's name does not lend itself well to google searches for info...

AFAIK, the linux version of pSX does not support many of the commandline functions included in the windows port. Here's what I can give you right now, but you probably have already seen this:
[http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263](http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263)

> **misterflibble said:**
> I discovered why I couldn't get any commandline options; it's because the /usr/bin/psx32 command is a script that just calls /usr/local/games/psx32/pSX, and doesn't pass through any options.  I see why you can't just put a symlink in too, because pSX wants its config file in the same directory as the executable.

Yep, sorry about that. It was a script I hacked together, just trying to get it to work. If anyone can improve the script it would be appreciated of course.

---

### Post by bluemech on 2007-07-16
So **dfreer**, tested dualshock mode on pSX yet? :)

---

### Post by dfreer on 2007-07-16
> **bluemech said:**
> So **dfreer**, tested dualshock mode on pSX yet? :)

Thanks for reminding me, so often I get caught up in other projects I forgot to do stuff I said I'd do :(
So here's my results:

Short Version
The logitech dual action controller works perfectly in linux, however pSX controller mode SCPH-1150 appears broken, and SCPH-1200 works in games that support Dual Shock (I tested Star Ocean). However, games that do not support dual shock will refuse to accept ANY input (I believe the original Playstation would do this as well).

Long Version:
```

 First, for those of you who don't know, the logitech dual action USB controller looks almost identical to a Standard PS2 Controller/Playstation dual shock, 
although it does not have any rumble capabilities. There is 1 extra button located just below where the <select> button on a PS2 controller is, 
this serves to "switch" the axes on the controller, actually making the left joystick map to the same axes as the left Dpad, and vive versa 
(note the right joypad is not affected in any way).

 I first tested the controller in ZSNES just to make sure it is fully compatible with linux, and it passed with flying colors. 
Each and every button/axes is recognized, down to pushing the joysticks "in" similiar to Playstations L3/R3 buttions. 
I can use that special button to switch between the axes mid game play, and play SNES games using just the axes themselves. 

 Now to pSX. In the configuration, pSX detected the controller correctly, and I was able to map every key on the joystick to it's appropriate function. 
The regular SCPH-1010 works just fine in with the standard keys mapped. I then tried mapping the joysticks to the regular keypad presses 
(right joystick UP = Triangle, left joystick DOWN = Left D-pad DOWN etc), and it worked beautifully, along with using the "Special" key to switch axes.

When switching to SCPH-1150 Analog+Rumble, I can no longer see a cursor in the BIOS menu and can't select anything :( Furthermore, 
on the games I tested with (Breath of Fire 3 and Star Ocean), I was unable to get either game to recognize input. It appears that this particular controller is "broken" in pSX...

Finally, I tried the SCPH-1200 Dual Shock mode. It works perfectly in Star Ocean, using the left joystick to control running and the D-pad controls walking speed, 
which is normal behaviour. Too bad I don't have a game that REALLY uses the dual shock functions (right joystick and L3/R3), 
there aren't too many regular playstation games that require it (That monkey game would've been a great test :D ). However, 
Breath of Fire 3 refused to accept input from this mode as well. I'm pretty sure this is due to BOF3 not supporting dual shock controllers, 
although without the game case (my sister at college stole it :( ), it's hard to tell.
```

---

### Post by misterflibble on 2007-07-16
I would change the script to this:
```
#!/bin/sh
/usr/local/games/psx32/pSX "$@"
```

It just spits back out all the command line options you give it to pSX.  Run psx32 -h to get a list of commandline switches.  Note that you need to pass the full path of an image or drive in order for pSX to open it properly, this is a limitation of pSX, not the script.

I can see there's really no way this program would be allowed in either Debian or Ubuntu any time in the near future, with its one-folder approach requiring config files in the same directory as the executable, and the problems with permissions and multiple users that causes.

---

### Post by dfreer on 2007-07-16
> **misterflibble said:**
> I would change the script to this:
```
#!/bin/sh
/usr/local/games/psx32/pSX "$@"
```

It just spits back out all the command line options you give it to pSX.  Run psx32 -h to get a list of commandline switches.  Note that you need to pass the full path of an image or drive in order for pSX to open it properly, this is a limitation of pSX, not the script.

Thanks for the suggestion, I hope to get a new version out soon (the x86 packages really need updated as well), and it will have this fix incorporated!

---

### Post by bluemech on 2007-07-17
> **dfreer said:**
> Thanks for reminding me, so often I get caught up in other projects I forgot to do stuff I said I'd do :(
So here's my results:

Short Version
The logitech dual action controller works perfectly in linux, however pSX controller mode SCPH-1150 appears broken, and SCPH-1200 works in games that support Dual Shock (I tested Star Ocean). However, games that do not support dual shock will refuse to accept ANY input (I believe the original Playstation would do this as well).

Long Version
...
...

You rock my good sir. That really cleared some things up. It seems, however, that you have a bit of a different Logitech controller than mine, as I don't have the switch mode button you described. That must be what's keeping me from being able to use dualshock mode (even in the PS BIOS I don't get the cursor for SCPH-1200).

I will have to find my copy of Star Ocean to see if that works for me. For now though, I guess my workaround of using the analog sticks in place of the digital pad will work fine. Haven't run into any problems playing FF Tactics, Symphony of the Night and Vagrant Story so far. :D

---

### Post by dfreer on 2007-07-17
Ah, doing a little google image searching pops up a bunch of pictures like this:
[IMG]http://www.kustompcs.co.uk/acatalog/4707.jpg[/IMG]

However, this picture is identical to the one I have:
[IMG]http://i17.ebayimg.com/04/i/000/86/f2/0839_1.JPG[/IMG]

---

### Post by bluemech on 2007-07-22
Heads up! v1.12 is here!

[http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1185147621](http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1185147621)

Found it while I was looking for a fix for that darned CD image load bug. ;)

---

### Post by dfreer on 2007-07-23
> **bluemech said:**
> Heads up! v1.12 is here!

[http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1185147621](http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1185147621)

Found it while I was looking for a fix for that darned CD image load bug. ;)

w00t! Thanks for letting me know, I'll get right on it!

EDIT: changelog (fixes I'm particularly interested in are highlighted in **bold**)
v1.12 **Fixed crash on startup with -f command line option**
      Fixed SPU bug that caused FF8 FMV audio to stop sometimes
      Fixed bug that prevented some keys being mapped to controllers
      Fixed bug where window size/position was reset when using fast forward
      **Added support for Alcohol 120% MDF/MDS images**
      Fake subcode in track gaps (required for TombRaider1)
      Fixed Syphon Filter boot hang
      Fixed infinite loop in Tekken3 and Deception3
      Changed 384 mode to 364 which seems to be correct (based on TombRaider)
      Fixed aspect ratio correction for 5:4

EDIT: Ok, I have an AMD64 package of pSX32 ready for public testing. I'm going to place it in the testing repository, that way it won't be pushed onto regular users until I know for sure it works. The main thing here is:
(1) will the new version overwrite existing psx.ini config file?
(2) will the new version delete old save files/memory cards/screenshots/bios/etc.
To add the testing repo:
Edit the line in your /etc/apt/sources.list from this:
```
deb http://packages.dfreer.org feisty main
```
to this:
```
deb http://packages.dfreer.org feisty testing
```

anyways, you can either add the testing repository, or download the 1.12 AMD64 .deb here:
[http://packages.dfreer.org/pool/feisty/testing/binary-amd64/P/pSX32_1.12-0.5_amd64.deb](http://packages.dfreer.org/pool/feisty/testing/binary-amd64/P/pSX32_1.12-0.5_amd64.deb)

Lemme know if there are any issues updating, specifically using apt-get upgrade. I'm going to get to work on the i386 release, and hopefully we can get both versions into the main repo soon.
MORE EDITING: i386 package is also in the testing repo, you can find it manually here:
[http://packages.dfreer.org/pool/feisty/testing/binary-i386/P/pSX_1.12-0.5_i386.deb](http://packages.dfreer.org/pool/feisty/testing/binary-i386/P/pSX_1.12-0.5_i386.deb)

---

### Post by bluemech on 2007-07-23
> **dfreer said:**
> Ok, I have an AMD64 package of pSX32 ready for public testing.

anyways, you can either add the testing repository, or download the 1.12 AMD64 .deb here:
[http://packages.dfreer.org/pool/feisty/testing/binary-amd64/P/pSX32_1.12-0.5_amd64.deb](http://packages.dfreer.org/pool/feisty/testing/binary-amd64/P/pSX32_1.12-0.5_amd64.deb)

Well that was fast, haha.

I tried grabbing the archive yesterday from the site, and it seems that the only thing that has changed is the executable itself. Will just copying that executable into the old pSX directory work as well, since it contains all the plugins already anyway?

---

### Post by dfreer on 2007-07-23
well, there are no plugins for pSX, one of the beauties of it. Yes, just copying the executable will work, make sure it has 755 permissions otherwise it won't want to run. 

And you can use the old savestates/memory cards/BIOS/config file with the new version, so just dropping the new executable in *should* work just fine (it may prevent future upgrades using my repository though, because the file was manually changed). 

The new debian package simply incorporated a few other fixes I had been meaning to get to:
[list]
[*]Updated the script in /usr/bin, so that you can pass commandline arguments (thanks misterflibble!)
[*]Caught the i386 package up to the AMD64 package (i386 was missing several things)
[*]**Ensured** that the permissions on all of the needed files/folders are set correctly
[/list]

I believe I will have 1.12 out in the main repository tonight anyways. A simply apt-get update/upgrade will grab it for you then :) Hopefully my ramblings made sense lol

---

### Post by Jeek Elemental on 2007-07-23
thanks for making the packages, Im having abit of trouble running it tho:

(pSX:24736): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:24736): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:24736): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:24736): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:24736): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:24736): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:24736): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:24736): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault (core dumped)

this is on an otherwise fully functioning Ubuntu 7.04 32bit machine with latest nvidia drivers (ut2k4 runs fine). I get to select a bios image, then it exits with the seg fault above.

Any ideas what to try, am I missing some package?

---

### Post by dfreer on 2007-07-24
Can you let me know which version of pSX you are using (when installing, look for 1.1X-X.X)? Also, the output of the following command:
```
ls -l /usr/local/games/psx/
```
In general, the Glib errors happen on both AMD64 and i386, I have yet to determine what causes that to happen, although it shouldn't be the cause of a segmentation fault.

---

### Post by Jeek Elemental on 2007-07-24
yes sorry should have said, its the latest 1.12-1.0

total 2272
drwxr-xr-x 2 root root    4096 2007-07-23 19:36 bios
drwxr-xr-x 2 root root    4096 2007-07-23 19:36 cdimages
drwxr-xr-x 2 root root    4096 2007-07-23 19:36 memcards
-rwxr-xr-x 1 root root 2277145 2007-07-23 19:36 pSX
-rw-rw-rw- 1 root root    2958 2007-07-23 19:36 psx.ini
-rw-r--r-- 1 root root   16544 2007-07-23 19:36 readme.txt
drwxr-xr-x 2 root root    4096 2007-07-23 19:36 saves
drwxr-xr-x 2 root root    4096 2007-07-23 19:36 screenshots
jeek@ubuntu1:~$ 

I see the files need root access, however I tried grabbing the emulator from its website aswell and unpacked to /home, with exact same result.
The glib errors come first, then the bios file requester, and then seg fault after selecting bios.
cpu is amd64x2 4600, nvidia 8600, usb sound (alsa).

---

### Post by dfreer on 2007-07-24
the files actually don't need root access, although they are owned by root they should be readable (and in some cases writable) by all. just to make sure, try doing the following:
```
cd /usr/local/games/psx/
sudo rm psx.ini
sudo touch psx.ini
sudo chmod a+w psx.ini
./pSX
```
If that doesn't work, you can try the full uninstall/reinstall listed in the F.A.Q.'s at the beginning of this post, in the meantime I will get a feisty 7.04 32-bit Live CD out and try to duplicate your errors (I'm running nvidia as well, and if UT2k4 works for ya I doubt it is a video card issue).

EDIT: I just booted to my feisty 7.04 i386 live cd, and after performing a few tasks (installed nvidia drivers via restricted drivers manager, restarted the X server, added the dfreer main repository) I did a sudo apt-get install psx. Other than one complaint about not being able to find libgtkglext1 (which is in the official repos, not sure why it doesn't grab it from there. I added a local copy to my repository to fix this), it installed without a hitch, and proceeded to run perfectly. Perhaps you have a corrupted BIOS file? That might explain why it seg faults immediately after asking for the BIOS file location. It could be a permission error on your BIOS file also, so make sure to do an ls -l on it.
finally, like i said try the full uninstall/reinstall of pSX.

FURTHER EDIT: I did happen to get this error:
> pSX: pcm_params.c:2276: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted (core dumped)
It seems if the sound is misconfigured (for some reason, the second user has broken sound on the live CD), psx will abort (but not segfault, so I don't think these two problems are related.
Also, having looked at the ls -l info you provided, I realize that once again permissions aren't set right, (those folders really should be 777  drwxrwxrwx). I have fixed this in the new package, this only effects the i386 package btw. I don't think this was part of your problem but you never know...

---

### Post by dfreer on 2007-07-24
Ultima, being awesome, has released new versions of the pSXFrontend for linux, including *gasp* 32/64 bit versions. Be on the lookout....

---

### Post by misterflibble on 2007-07-26
Hooray, the -f switch now works for linux! :)

I have a tip for anyone having difficulties with fullscreen mode:  Fullscreen mode does not seem to play well with certain window managers; so far evilwm and fluxbox have both given the same squashed fullscreen mode that doesn't cover the screen properly.  Kwin works perfectly, and I assume metacity does as well as nobody has yet mentioned a problem here.

Now I just have to figure out why pSX has scratchy sound on my onboard sound but not my soundblaster, just like zsnes used to.

---

### Post by dfreer on 2007-07-27
> **misterflibble said:**
> I have a tip for anyone having difficulties with fullscreen mode:  Fullscreen mode does not seem to play well with certain window managers; so far evilwm and fluxbox have both given the same squashed fullscreen mode that doesn't cover the screen properly.  Kwin works perfectly, and I assume metacity does as well as nobody has yet mentioned a problem here.

Hmmm, since I don't use anything other than metacity, kwin, and emerald I haven't experienced those issues myself. it's not an aspect ratio problem, is it?

> **misterflibble said:**
> Now I just have to figure out why pSX has scratchy sound on my onboard sound but not my soundblaster, just like zsnes used to.

Try fiddling with your latency settings and change the frequency values around, if not we might have to do a little investigating into what sound system pSX uses (OSS, ALSA, etc), and what we can do to fix it ;)

---

### Post by misterflibble on 2007-07-27
I don't believe it's an aspect ratio problem.  Only part of the screen ends up painted, with a strip on the right where you can see the desktop and other programs still.  Within the painted part it's both squashed and off the screen.  This was at a pretty high 16:9 resolution (1920x1080), but I tried other standard 4:3 resolutions, and they had the same problem.

The sound is probably related to the fact that I have the lousy HDA onboard sound, as I've found other reports of it being scratchy with SDL and other things.  The latency settings don't change anything, and curiously, it gets scratchier when in fullscreen, than when in a tiny window, even though its not even close to maxing out my CPU.  I might just stick my soundblaster back in there to see how that works.

---

### Post by dfreer on 2007-07-27
> **misterflibble said:**
> I don't believe it's an aspect ratio problem.  Only part of the screen ends up painted, with a strip on the right where you can see the desktop and other programs still.  Within the painted part it's both squashed and off the screen.  This was at a pretty high 16:9 resolution (1920x1080), but I tried other standard 4:3 resolutions, and they had the same problem.

This sounds like a problem with the emulator itself, it would be beneficial if you could post your issues on the psxforums (link is here: [http://psxemulator.proboards54.com/](http://psxemulator.proboards54.com/) ), I know they have been issues with fullscreen modes in the past.

> **misterflibble said:**
> The sound is probably related to the fact that I have the lousy HDA onboard sound, as I've found other reports of it being scratchy with SDL and other things.  The latency settings don't change anything, and curiously, it gets scratchier when in fullscreen, than when in a tiny window, even though its not even close to maxing out my CPU.  I might just stick my soundblaster back in there to see how that works.
This blog by one of the developer's of ZSNES may help explain why your soundblaster card works better with OSS/SDL than the onboard, it's a good read in any case:
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

EDIT: Do you have the low resolutions specified in your /etc/X11/xorg.conf file for all bpp levels (specifically 640x480)? I do not believe this is part of the problem you are having (since you say it only occurs with certain WM's), but you might want to check it out.

---

### Post by misterflibble on 2007-07-28
I'll post my findings on the fullscreen problem to the list.  I did do some fiddling with the resolutions in my Xorg.conf, which included paring down all the resolutions available to X to just 1920x1080, and defining that for 16bpp as well as 24.  I had also tried the other resolutions that had been defined, and they showed exactly the same problems, just smaller, with the alternate window managers.  One thing I forgot to mention is that this is using Component Out of the Nvidia card to an HDTV, although I doubt the program would see anything except that I have a rather large monitor.

That was a very informative blog post, Dfree, thanks!  I knew that the inclusion of libao was why zsnes finally worked with my onboard sound properly, but prior to your packages I was annoyed that that was the ONE part of zsnes that prevented its proper compilation and running in my AMD64 environment.  Ironically, I've always had the opposite view that ALSA is better than OSS because programs using OSS wouldn't cooperate with the sound mixing, while ALSA ones would.  I hadn't thought to try the new (improved?) OSS drivers that were released recently.  It's certainly worth a shot!

---

### Post by misterflibble on 2007-07-28
I successfully compiled and installed the OSS drivers (GPL btw, even though some of the download pages still claim you would need a license number), only to realize that pSX is ALSA-based, and the ALSA emulation layer is 64-bit, not the 32-bit that pSX is linked against...curse my 32 extra bits!

---

### Post by dfreer on 2007-07-30
ATM dfreer.org is down, sorry everyone! Don't fret, it will be back soon (hopefully tonight, at worse a couple of days). The manual installation method will still work, if you absolutely need it installed today.
The reason why is I had to switch out some hardware, and I may need to order some new parts. :(

---

### Post by newlinux on 2007-07-31
This has worked wonderfully. Thank you. Now if I could just get psx and mythgame to play nice...

---

### Post by dfreer on 2007-07-31
> **newlinux said:**
> This has worked wonderfully. Thank you. Now if I could just get psx and mythgame to play nice...

I managed it to work beautifully "once", but most of the time I can't seem to get pSX to pop up "on top" of MythGame, I have to <Alt>+<Tab> over to it. Is this the problem you are having?

---

### Post by newlinux on 2007-07-31
no, for some reason I can't get mythtv to properly scan the "roms." It always hangs when it scans the playstation folder.

---

### Post by bebop_tango on 2007-07-31
> **dfreer said:**
> I don't see why not? Ubuntu owes a lot of things to debian, it only helps the community to add it to both debian and ubuntu.

I can't run pSX on Debian Etch... I get the devilish 'Segmentation Fault' right after the 'pick your language' menu... in both v1.11 and v1.12 releases.

A working Debian package would be wonderful. In fact, any info on this issue would... is it because the libs required are so much older in Etch...?

---

### Post by dfreer on 2007-07-31
@newlinux
I believe you have to specify your file extensions (.iso, .cue, .ccd, etc) so it knows what to look for. I'll post a screenshot of what my setup looks like ASAP
EDIT: Ok, here's the screenshots:
[http://www.dfreer.org/~dfreer/mythtv/Screenshot.png](http://www.dfreer.org/~dfreer/mythtv/Screenshot.png)
On this screen, make sure "Indepth Game Scan" is unchecked, that seemed to lag up my system.

[http://www.dfreer.org/~dfreer/mythtv/Screenshot-1.png](http://www.dfreer.org/~dfreer/mythtv/Screenshot-1.png)
Here, I am using pSX 1.12 (1.12 let's you do the -f (fullscreen) switch). I only have .iso, .bin, and .cue images right now, most of my pSX games are on CD's. After saving these settings, try "Clearing Game Data" and then "Scan for Games/ROMS". Also, make sure your path to the ROM folder is correct (note you do not have to escape whitespaces in folder names).

[http://www.dfreer.org/~dfreer/mythtv/Screenshot-2.png](http://www.dfreer.org/~dfreer/mythtv/Screenshot-2.png)
Just confirmation that the games DO show up for me.

@bebop_tango 
I'll check it out, I run Debian etch but without the GUI, so I'll need to get a virtual machine going on my ubuntu system or something. What arch are you running (32-bit or 64-bit)?

@everyone
The server is backup! If it goes down again it will probably be just for reboots, so just try again after a few minutes.

---

### Post by gentine on 2007-08-02
Wow, I got to tell you after trying to get epsxe working this is a dream come true.

---

### Post by bebop_tango on 2007-08-02
@bebop_tango 
I'll check it out, I run Debian etch but without the GUI, so I'll need to get a virtual machine going on my ubuntu system or something. What arch are you running (32-bit or 64-bit)?

My arch is 32-bit.

[This guy]("http://psxemulator.proboards54.com/index.cgi?action=display&board=support&thread=1172647738&page=1") has similar problems. In fact, I also ran gdb and got basically the same output.

---

### Post by dfreer on 2007-08-02
> **bebop_tango said:**
> 
My arch is 32-bit.

[This guy]("http://psxemulator.proboards54.com/index.cgi?action=display&board=support&thread=1172647738&page=1") has similar problems. In fact, I also ran gdb and got basically the same output.

I'll try and see what I can do, but it seems to be a problem with pSX itself, and not a dependency/package issue, which is what I do. Best thing is to try to get in contact with pSX author/pSX forums/linux guru and see if they can interpret your gdb output. 
I wish you the best of luck, and like I said I'll see if I can reproduce the error on my debian system.

---

### Post by jw5801 on 2007-08-03
I dunno whether it was the upgrade to v1.12 or something else that I've done recently, but now whenever I try to go fullscreen everything goes black and locks up my system. Hmm... I'll try going back to 11 and see what happens.

EDIT: Ok the v1.11 .deb isn't there anymore. I have absolutely no idea what happened or even where to start on how to fix it! Can anyone point me in the right direction? Normally I'd look at the terminal output whilst running the buggy program, but that doesn't really work when my display stops displaying and I can't do anything...

EDIT 2: Well... I recently installed Compiz-Fusion, which apparently doesn't agree with the full-screen output of pSX. Not entirely sure why, but it runs fine under Metacity so I figure that's a logical assumption. When in Compiz pSX doesn't run very well either (graphics are really jumpy and the frame-rate is bad), I thought that may have been an issue with the game I was playing (FF Tactics) but it runs fine when I'm using metacity.

---

### Post by dfreer on 2007-08-03
1.11 Debs can be found here:
[http://packages.dfreer.org/pool/feisty/main/binary-amd64/P/](http://packages.dfreer.org/pool/feisty/main/binary-amd64/P/)
[http://packages.dfreer.org/pool/feisty/main/binary-i386/P/](http://packages.dfreer.org/pool/feisty/main/binary-i386/P/)
You'll need to tell apt-get not to upgrade to the latest version if you want to continue using 1.11 and upgrade your system.

Hmmm. When you are using compiz, are you using XGL or AIGLX? Generally, XGL will not allow you to play 3D games. I use nvidia + AIGLX + beryl + pSX 1.12 fullscreen and I haven't noticed any problems.

---

### Post by newlinux on 2007-08-03
I ended up getting it to work fine with mythgame. Was a file permission and filename character issue.

---

### Post by jw5801 on 2007-08-03
Well I ruled out a problem with pSX so downgrading won't help.
I am running XGL, but when I switch to metacity I'm still logged in with the XGL session and it works.
So basically:
ATi + XGL + Compiz + pSX 1.12 fullscreen = Bad
but:
ATi + XGL + Metacity + pSX 1.12 fullscreen = Good

Oh well so long as I have a workaround I'm happy. I already have to switch out of Compiz to run Java apps, so I'll just leave it until Gutsy comes out. Then I'll get everything running properly.

---

### Post by dfreer on 2007-08-04
@jw5801
I don't know if you have already tried this, or if you even want to spend the time messing with it. But here goes:
You may be able to use AIGLX with your ATI card, if you switch from using the "fglrx" driver and use the open-source "radeon" driver. In most cases, this will not work as the open-source driver is not nearly up to par, but in some cases (my sister's ATI 9550 Radeon supported this) it works wonderfully. She is able to use beryl + AIGLX and play video games, and hasn't had any problems so far.
I find it's eaiser than having her log out and select an XGL session to use beryl, then logout and use a regular X session to use direct rendering.

---

### Post by jw5801 on 2007-08-04
> **dfreer said:**
> @jw5801
I don't know if you have already tried this, or if you even want to spend the time messing with it. But here goes:
You may be able to use AIGLX with your ATI card, if you switch from using the "fglrx" driver and use the open-source "radeon" driver. In most cases, this will not work as the open-source driver is not nearly up to par, but in some cases (my sister's ATI 9550 Radeon supported this) it works wonderfully. She is able to use beryl + AIGLX and play video games, and hasn't had any problems so far.
I find it's eaiser than having her log out and select an XGL session to use beryl, then logout and use a regular X session to use direct rendering.

I'll give it a shot when I have some time but I don't have to log out, all I have to do is run ```
metacity --replace
``` to be able to run it, which is irritating, but not as bad as it could be.

---

### Post by dfreer on 2007-08-27
If anyone has been having problems with running my package on Debian Lenny/Testing AMD64, there is now a package in the repository just for you ;) I haven't been slacking off *entirely*, you see...

EDIT: ...Neither has pSX Author, it appears ;) pSX 1.13 is out, along with several new goodies for us linux users:
```
v1.13 Added Korean, Bosian, Serbian and Icelandic translations
**      Added some missing translations to Linux build**
      Debugger DMA capture buffer now autoresizes
      Fixed streaming music in Jikkyou Oshaberi Parodius
      Fixed bug when setting sound frequency in Windows
**      Implemented volume and mute in Linux**
      Fixed "missing body parts" bug in Deception 3
      Fixed bug that caused XA audio in Deception 3 to not stop correctly
      Fixed random crash in Road Rash: Jailbreak
      Fixed debugger crash when emulator is reading from CD
      Fixed hang opening CD images in Linux
**      Per-user settings for Linux (.ini file is now stored in ~/.pSX)**
      Removed SSE instructions used during init (should fix crash on AMD CPUs)
**      Fixed GTK warnings when clicking window close button in Linux**
```

One thing to look into, for those of you that were having segmentation faults, although I do not know if this is related):
```
Removed SSE instructions used during init (should fix crash on AMD CPUs)
```

One thing: if you are using my packages to upgrade, please note that pSX can now use a psx.ini located in the current directory, OR use one located in your home directories. Either method is acceptable, although in general I'm going to assume that you use ~/.pSX/psx.ini

FURTHER EDITING:
For those of you absolutely anxious to try pSX 1.13, but are deathly allergic to *.tar.bz2 packages, I have a solution:
**Ubuntu Feisty AMD64 Users** = Just apt-get update/upgrade, or if you've never used this before: [http://packages.dfreer.org](http://packages.dfreer.org)
**Debian Lenny/Testing AMD64 Users** = Follow the instructions at the bottom of this page to add a new repository just for you!: [http://packages.dfreer.org](http://packages.dfreer.org)

---

### Post by Babets on 2007-08-30
I tried psx, unfortunately it crash with "segmentation fault" after selecting language and bios.
I tried both versions (tar.bz2 and repository package), same problem.

I use feisty 32 on amd64.

Now i'm using the old epsxe :(
```
Removed SSE instructions used during init (should fix crash on AMD CPUs)
```

Maybe they don't completely fixes this bug :confused:

edit: i see in the previous pages that i'm not the only with this problem. :)

---

### Post by dfreer on 2007-08-30
@babets
I'd encourage you to post your problem, along with full CPU info to the pSX forums, as it probably isn't a problem with my packages. Here's the link in case you don't already have it: [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

---

### Post by bluemech on 2007-09-02
Version 1.13 rocks man. I haven't reproduced a single crash or hang from the previous version, which happened quite often when I tried to load an image. Kudos to the devs.

---

### Post by Babets on 2007-09-03
@dfreer [http://psxemulator.proboards54.com/index.cgi?board=bugreports&action=display&thread=1187624682](http://psxemulator.proboards54.com/index.cgi?board=bugreports&action=display&thread=1187624682)

---

### Post by dfreer on 2007-09-03
@babets
I'm going to put a notice on the front page of this thread linking to the pSX thread about this issue. This is definitely not something I can help out with, other than to make new packages of lib32gtkglext1 or psx32 (if the segmentation fault is fixed in later versions). Thanks for posting, and hope it works out for you!

---

### Post by Mochtroid-X on 2007-09-27
Running Gutsy Beta here and having a problem (though probably because I'm using a Feisty repo), I cannot install psx32 because when it tries to install **lib32gtkglext1_1.0.6-1.5_amd64.deb** it exits because **ia32-libs-gtkglext1_1.0.6-1.2_amd64.deb** contains the same exact **libgdkglext-x11-1.0.so.0.2.4** file inside of it and it will not overwrite. Is there any way I can edit the deb file for psx32 so that it doesn't require lib32gtkglext1_1.0.6-1.5_amd64.deb at all since I already have the required lib?

---

### Post by dfreer on 2007-09-28
Well, you can certainly edit the .deb file, the dependency is listed in the control file. Or, since that is really the only dependency, you might as well just download the latest version from pSX website.
I'm more interested in your dependency conflict. Both of those packages you mentioned look like they game from my website. **ia32-libs-gtkglext1** was an older name for the package, before I changed it to **lib32gtkglext1**. They both contain the exact same files, so yes there would be a conflict. 
A normal *sudo apt-get install psx32* shouldn't have pulled the ia32-libs-gtkglext1 file, so I'm kinda curious as to why it's even on your system. :confused:

I'm in the process of getting a gutsy repo up, as soon as everything is tested throughly.

---

### Post by Mochtroid-X on 2007-09-28
ZSNES32 I believe. It has ia32-libs as a dependency, which I assume installs all IA.32 libraries

---

### Post by berlinbrown on 2007-10-16
Anybody know why when I run pscx, it just locks up and nothing happens.

At least from the one from ubuntu, it ran but I couldnt save.

I too am running final fantasy tactics.

---

### Post by dfreer on 2007-10-16
I don't, but I do know that pSX runs tactics just fine ;)

---

### Post by dfreer on 2007-10-22
Just to let people know, there is a gutsy repository now, with (hopefully) clean and mistake-free packages!

Also, to fufill a promise I made myself when I first started this project...

My pSX packages no longer use that ugly playstation logo that I shamelessly ripped off of a playstation fan site.
Now, my pSX packages feature a nice looking playstation image that I shamelessly ripped from the official pSX windows .exe! :D

---

### Post by dfreer on 2007-10-23
> **Mochtroid-X said:**
> ZSNES32 I believe. It has ia32-libs as a dependency, which I assume installs all IA.32 libraries

Took me a while to realize I missed this post. A 32-bit version of gtkglext1 hasn't been repackaged for AMD64 upstream, which means it probably came from me. ia32-libs wouldn't have installed it, although I very well could've messed up a dependency on an earlier version of zsnes32. 

In any case, updating to the latest package should resolve all issues, as feisty and gutsy have proper dependencies now.

EDIT: I know I triple-posted, but it's my thread and I don't care! :p

---

### Post by thebrandon on 2007-10-25
I am having a lot of trouble getting this to work for me.  No matter how I configure the frontend when I click "run psx" it doesnt do anything.  I have tried using different bios, I dont have any of the switches checked, Under the BASIC tab I have "pSX : /usr/bin/psx " and "Disc : location of my img file" and a save location for memory card 1.

Also, when I run the psx command in the terminal i get this : "(psx:17882): GdkGLExt-WARNING **: Window system doesn't support OpenGL."

What am I doing wrong?

---

### Post by dfreer on 2007-10-25
Try changing your path to /usr/local/games/psx/pSX instead of /usr/bin/psx. It shouldn't make a difference, but it won't hurt any either. But of course, if psx isn't working the psxfrontend won't launch it correctly, so let's look into that:

Doing some google footwork:
[http://www.archlinux.org/pipermail/arch-ports/2007-July/000492.html](http://www.archlinux.org/pipermail/arch-ports/2007-July/000492.html)
[http://www.unixadmintalk.com/f41/gnash-freebsd-opengl-usable-19055/](http://www.unixadmintalk.com/f41/gnash-freebsd-opengl-usable-19055/)
[http://permalink.gmane.org/gmane.linux.ubuntu.user.spanish/19636](http://permalink.gmane.org/gmane.linux.ubuntu.user.spanish/19636)

confirms to me, that you just need to install your video card drivers correctly, and make sure the "glx" module is being loaded in your xorg.conf. There are plenty of guides on how to do this, but I'm willing to help out if you can tell me what video card you are currently using, and the contents of your /etc/X11/xorg.conf

---

### Post by thebrandon on 2007-10-26
Well, I tried changing the path but it still didnt respond when I hit run.

I thought my video card was installed properly, I used Envy to install it but maybe something got thrown off when I upgraded to 7.10.

Here is my xorg.conf :

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 4000]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SDM-M51"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX 4000]"
	Monitor		"SDM-M51"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "720x400" "640x480" "640x400"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection


Thanks for the help!

---

### Post by dfreer on 2007-10-26
> **thebrandon said:**
> Well, I tried changing the path but it still didnt respond when I hit run.

I expected that, because your video card needs set up still. But, once you get it up, that should work correctly.

> **thebrandon said:**
> I thought my video card was installed properly, I used Envy to install it but maybe something got thrown off when I upgraded to 7.10.

Did you try using the Restricted Drivers Manager? System > Administration > Restricted Drivers Manager. I find it works rather well, although it doesn't always detect the card, if it does detect it does a great job of downloading everything and setting it up for you. 
Of course, if not doesn't work, we can try to set up your card manually. 

Before you go any further, backup your /etc/X11/xorg.conf like so:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
If at any point you have problems setting up the X server, you can restore your backup with this command:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Now, as to which driver to use, I'm pretty positive that you will need the nvidia-glx-legacy driver, due to the older nvidia model you have (If your card isn't actually an MX 4000, let me know. I think anything older than the 6xxx series needs the legacy driver). 

So to install that nvidia driver:
```
sudo apt-get install nvidia-glx-legacy
```

Now, you'll need to modify a few lines in your /etc/X11/xorg.conf in order to use the new driver:

```

Section "Device"
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 4000]"
	**Driver	"nvidia"**
	BusID		"PCI:1:0:0"
EndSection

```

Now, reboot your computer. You should be able to login like normal, although if there's an error just restore that backup like I said earlier.

You might be able to run psx now, for a test try this command:
```
glxgears
```
You should see some spinning gears, and after about 5 secs it should give you some FPS readings. If it's not working, post the output of this command to me:
```
glxinfo | head
```

Beyond that, You may need to add the following line to your /etc/X11/xorg.conf as well:

```

Section "Files"
**Load "glx"**
EndSection

```


You can always look up a guide on how to configure your /etc/X11/xorg.conf for your specific chipset, as well. The goal here is to have the output of this command look something like this:
```
$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
**server glx vendor string: NVIDIA Corporation**
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float

```

---

### Post by thebrandon on 2007-10-27
Well I installed the legacy driver and everything got a bit screwy, which is kinda like it was before I settled for the settings I had previously.

Here is the output of glxgears & glxinfo | head :

brandon@brandon-desktop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
brandon@brandon-desktop:~$ glxinfo | head
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
name of display: :0.0

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Also, the Nvidia splash screen doesnt come up anymore when I reboot.  So I decided to mess around with the xorg.conf and I got some settings from here : [http://ubuntuforums.org/archive/index.php/t-54956.html](http://ubuntuforums.org/archive/index.php/t-54956.html)

Now here is what my xorg.conf looks like :

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"

Section "Device"
	Identifier "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver "nvidia"
	BusID "PCI:1:0:0"
	Option "NoDCC"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "UseInternalAGPGART" "no"
	Option "NvAGP" "3"
	Option "RenderAccel" "true"
	Option "Coolbits" "1"
	Option "NoLogo"
	VideoRam 131072
EndSection

Section "Monitor"
	Identifier	"SDM-M51"
	Option          "DPMS"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"800x600@60"	"1024x768@60"	"800x600@56"	"1280x960@60"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by dfreer on 2007-10-27
> **thebrandon said:**
> 
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

Yepp, that would be from xorg not loading the glx module. But from the new /etc/X11/xorg.conf that you posted, it looks it is specified correctly. I'm not sure, but I think the other error can be solved by placing this line in your Section "Screen"
```
        Option          "AddARGBGLXVisuals" "True"

```

> **thebrandon said:**
> 
Also, the Nvidia splash screen doesnt come up anymore when I reboot.  


That's handled by the following line in your /etc/X11/xorg.conf
```
Option       "NoLogo"
```

> **thebrandon said:**
> 
So I decided to mess around with the xorg.conf and I got some settings from here : [http://ubuntuforums.org/archive/index.php/t-54956.html](http://ubuntuforums.org/archive/index.php/t-54956.html)


Now that you have done all of the above, I don't see why glxgears and subsequently, pSX shouldn't work for you. I'm not really an expert in getting legacy nvidia drivers set up, if I were you I'd create a new thread describing your issues in getting 3D acceleration working.

---

### Post by thebrandon on 2007-10-28
well even after adding that option I still could not get glxgears to run properly so I just restored my original setup which I hadnt run glxgears in.  I guess I had it set up properly from the beginning!  So anyway, I run the glxinfo | head command and here is what it says :

brandon@brandon-desktop:~$ glxgears
X connection to :0.0 broken (explicit kill or server shutdown).
brandon@brandon-desktop:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer


The part about direct rendering, setting LIBGL_DEBUG=verbose?  Is that where my problem lies and if so, how do i set it to =verbose?

---

### Post by dfreer on 2007-10-28
I'm not sure anymore... you might need to create a thread about this, or post in that existing mx 4000. hope you get this working!

---

### Post by thebrandon on 2007-10-28
So I tried running it again and now its running, my only problem now is that the playstations load / splash screen is really slow and choppy.  Any suggestions on how I can speed it up to normal?

Thanks for your help!

---

### Post by dfreer on 2007-10-28
That would be due to lack of 3D acceleration. You're basically getting horrible FPS (try running glxgears and let it set for a few minutes, you should see it reporting some framerates). I'm not entirely sure about the legacy driver, but for newer nvidia cards this is solved by installing the nvidia driver, which has support for direct rendering/3D acceration.

Any other 3D game will require this as well, so basically until you get your driver installed correctly, or get a newer model (in the case that your particular card won't support 3D acceration), you won't be able to play 3D games in linux.

---

### Post by thebrandon on 2007-10-28
I let glxgears run for a minute and got these results but I dont know what to make of them. 

brandon@brandon-desktop:~$ glxgears
935 frames in 5.3 seconds = 175.766 FPS
904 frames in 5.5 seconds = 163.056 FPS
904 frames in 5.4 seconds = 166.408 FPS
904 frames in 5.4 seconds = 166.438 FPS
904 frames in 5.4 seconds = 166.428 FPS
904 frames in 5.4 seconds = 166.355 FPS
1469 frames in 5.1 seconds = 289.712 FPS
3729 frames in 5.1 seconds = 732.118 FPS
3729 frames in 5.0 seconds = 739.805 FPS
3729 frames in 5.0 seconds = 742.808 FPS
3729 frames in 5.0 seconds = 741.123 FPS
3729 frames in 5.0 seconds = 743.882 FPS
3729 frames in 5.0 seconds = 742.183 FPS
3699 frames in 5.2 seconds = 716.126 FPS
1017 frames in 5.2 seconds = 196.440 FPS
1243 frames in 5.4 seconds = 229.092 FPS
1130 frames in 5.7 seconds = 198.420 FPS
904 frames in 5.5 seconds = 162.948 FPS
904 frames in 5.3 seconds = 171.173 FPS
3729 frames in 5.1 seconds = 726.725 FPS
3616 frames in 5.1 seconds = 709.204 FPS
3729 frames in 5.1 seconds = 732.036 FPS
3729 frames in 5.0 seconds = 742.960 FPS
3616 frames in 5.1 seconds = 715.579 FPS

---

### Post by thebrandon on 2007-10-29
Well I finally got everything working!  The only problem now is that since desktop effects kicked on I seem to have lost my titlebar and thus my min, max, and close buttons.  Also, terminal is now just a white block that doesnt seem to do anything so I am off to tackle this problem now.  Thanks for all the help!

---

### Post by thebrandon on 2007-10-29
Ok, one final question, I have an elcheapo little logitech usb gamepad but I cant figure out how to make work in psx.

Under the BASIC tab I have the box beside Pad Mode checked and the drop down box set to 0 - SCPH-1010: Normal Pad.

I assume it should not be set to analog+rumble or dualshock as it has none of the characteristics of either.  Do I need another driver?

As a side note, the pad works perfectly in GFCE as well as ZSNES so I know for a fact that it is functioning.

Thanks again!

---

### Post by dfreer on 2007-10-29
Knowing the model of "elcheapo" USB controller would help here, logitech has currently has about 5 different models, not to mention older discontinued models. 

> **thebrandon said:**
> Under the BASIC tab I have the box beside Pad Mode checked and the drop down box set to 0 - SCPH-1010: Normal Pad.

This sounds like you are trying to configure it in Ultima's frontend, as pSX doesn't have a "Basic" Tab. Try configuring it in there first, and then if it's working come back and use the frontend. Does it recognize keypresses when you are mapping them? Does it see the Joystick under "Controllers > Device"?

> **thebrandon said:**
> I assume it should not be set to analog+rumble or dualshock as it has none of the characteristics of either.  Do I need another driver?

Always start with the SCPH-1010 mode for new controllers on games known to be good. Some older Playstation games will refuse to accept input from the newer controllers, and I don't believe the rumble feature will work in any linux USB controller right now. So basically, only user SCPH-1010 and SCPH-1200, and only the 1200 on games you know can use it ;) I'm guessing if it works in zsnes, it should work in pSX.

> **thebrandon said:**
> Well I finally got everything working!  The only problem now is that since desktop effects kicked on I seem to have lost my titlebar and thus my min, max, and close buttons.  Also, terminal is now just a white block that doesnt seem to do anything so I am off to tackle this problem now.  Thanks for all the help!

On my NVIDIA 7400, if I don't have this line in my "Screen" section, I experience your problem of not having any titlebars:
```
        Option          "AddARGBGLXVisuals" "True"
```
You can always disable desktop effects by hitting <Alt>+F2 and entering this command:
```
metacity --replace
```
And you might get some useful error output if you try to start compiz in terminal like so:
```
compiz --replace
```
<Ctrl>+C to kill it, or the metacity --replace command again.

---

### Post by thebrandon on 2007-10-29
Well, I tried it under the 1010 and 1200 a couple of times each and it still wont detect.  Under applications > other > joystick it detects it as Logitech Logitech(R) Precision(TM) Gamepad (/dev/input/js0) but it responds in the little test window and it detects all button presses.

Wait, nevermind, I was going to erase all of this above because after re-reading what you had written I finally comprehended.  I was using Ultima's frontend as I assumed that it was the only way to configure.  When I loaded psx I realized that it has configuration options as well and blah blah blah.  Needless to say, it works perfectly!  Thanks again!

As far as the desktop effects go I have them shut off for now but I will definitely try your suggestion!

---

### Post by thebrandon on 2007-10-29
Well, I feel as if I have spoke too soon once again!  When I really sat down to play one of my games I found that even after setting the buttons on the directional pad multiple times (under both 1010 and 1200, the latter of which didnt work at all) they dont seem to work.  All of the other buttons function but it does me little good if I cant move.  I tried with an img file I had on the hd as well as an old game that I dug out of a box and got the same result with both!  Any suggestions?

Also, how well do those usb adapters for ps2 controllers that I see for sale on amazon work?  Especially the ones that have two pads that plug into one cord, does is not just recognize that as one controller?

---

### Post by thebrandon on 2007-10-29
Nevermind!!  I am being a stupd head again!  I screwed up the settings for the joystick when I was messing around with it.  I should have figured as much!

Thanks!

---

### Post by kinkdxm on 2007-11-03
Is it possible to play a 2 player game on 2 different computers?

I really really like driver 2 multiplayer and would love to play it with my friend at the same time but he lives far away.

---

### Post by dfreer on 2007-11-03
Not yet with pSX, kinkdxm :( But this emulator is under active development, so that may change in the future.

EDIT: Just tried out ePSXe and PCSX, on 64-bit Gutsy. Here's my thoughts if anyone is interested:
[http://ubuntuforums.org/showpost.php?p=3714766&postcount=135](http://ubuntuforums.org/showpost.php?p=3714766&postcount=135)

---

### Post by likemindead on 2007-12-10
Thank you so much for what you're doing here! And with that being said....

(1) Install went great! No problems.

(2) When I run pSX, the Sony screen is very slow/choppy. Both audio & video. Then when I try to access menus, they're choppy/barely there.

(3) If I try to insert a Castlevania: SOTN .iso, it says "Error: CD Not usable: Mixed sector sizez found - not supported."

(4) I can't figure out how to use Ultima's Frontend.

(5) Are there any config helps anywhere?

(6) Thanks in advance!!!

---

### Post by dfreer on 2007-12-11
> **likemindead said:**
> Thank you so much for what you're doing here! And with that being said....

(1) Install went great! No problems.

(2) When I run pSX, the Sony screen is very slow/choppy. Both audio & video. Then when I try to access menus, they're choppy/barely there.

(3) If I try to insert a Castlevania: SOTN .iso, it says "Error: CD Not usable: Mixed sector sizez found - not supported."

(4) I can't figure out how to use Ultima's Frontend.

(5) Are there any config helps anywhere?

(6) Thanks in advance!!!

(1). Awesome!

(2). Can you tell me what kind of video card you have, and post the output of the following commands:
```
glxgears   ## Just wanna see what kind of FPS you are getting

glxinfo | grep rendering

glxinfo | head
```

(2.a.) For the menu issues, try turning off compiz while running pSX, and see if that makes an improvement.

(3). For starters, I believe Castlevania: SOTN has been known to have problems in pSX (see [http://psxemulator.proboards54.com/index.cgi?board=gamecompatibility&action=display&thread=1162339727&page=1](http://psxemulator.proboards54.com/index.cgi?board=gamecompatibility&action=display&thread=1162339727&page=1)).
The pSX forums are pretty active, so if you are having problems with this game I'd recommend posting about it there (I don't have it so I can't help myself). However note that if you are using an .iso image, do not expect support unless you own the original game, and the .iso image was made from your own copy of the disc. Mentioning that you downloaded an iso of the game will get your thread locked quite quickly.

(4). I'd recommend setting up pSX first, it has it's own frontend that works quite well. Once that is done, then try setting up the frontend. Basically, you just need to give it the paths to the executable (on AMD64 it's */usr/local/games/psx32/pSX*), the disc (can be a disc image, or your CD Drive),  and the BIOS. The other options are not required, although they can be useful.

Once that is done, you should be able to save your profile (if you wish to keep those settings), and then click on the "Run pSX" button at the bottom.

(5). Ummm like manually editing the configuration file? The best place for that would be the official pSX forums:
[http://psxemulator.proboards54.com/](http://psxemulator.proboards54.com/)

(6). No problems, hope this helps!

---

### Post by likemindead on 2007-12-11
Thanks for the reply and help. You make this community the great place it is!

My video card is an Intel 82845G/GL, I have 1264MB system memory, and a 1.8GHz Celeron processor. Also:

```
owner@owner-desktop:~$ glxgears
1578 frames in 5.0 seconds = 315.477 FPS
owner@owner-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
owner@owner-desktop:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
owner@owner-desktop:~$
```

Thanks again!

---

### Post by likemindead on 2007-12-11
Hahaha.... I've fixed it! My problem was (possibly) threefold: (1) My computer was using the wrong graphics driver, (2) I had compiz enabled, (3) my .iso was bad. I changed the driver, disabled compiz, and got a new disc image, and BAM! I'm in business!!!

:biggrin:

Thanks so very, very much again. I'll be back if I need more advice. Blessings....

---

### Post by dfreer on 2007-12-11
Lol, yeah that happens some times. Glad pSX is working for you! :D

---

### Post by tenchu77491 on 2007-12-19
For some stupid reason.... pSX worked fine on my old Ubuntu install. Now the only one that works is the repackaged version of 1.11 you posted. Yet the graphics are still a bit choppy and frame skippy. I got it running pretty good. The bios load slow and choppy but the games run okay. I also play with Compiz and everything on.

---

### Post by dfreer on 2007-12-19
Things to try tenchu77491:
(1) Different BIOS image, could be your copy is corrupt in some way.
(2) Turn off compiz ;)
(3) Check if your video card drivers are correctly installed, direct rendering is working, and check if you are getting a decent FPS:
```
glxinfo | head
glxinfo | grep rendering
glxgears
```
(4) Try an original Playstation CD that is in good condition if you are currently using a CD Image. 

Just generic troubleshooting. But I guess the old saying applies here:
"If it works, don't fix it!" Kind of weird that 1.11 works but 1.13 doesn't...

---

### Post by tenchu77491 on 2007-12-19
On ATI card with Compiz on it always says Direct Rendering NO but it is actually working. I play with Compiz on and the games themself run fine (some minor lag when loading a movie or something some times). I have the sound working almost perfect. 

I just downloaded the scph7502 bios because I am playing Japanese games, but it works the same as the 1001 bios. I have no idea why the bios are laggy. 

By the way, I am running Metal Gear Solid Integral (Japanese). I have a whole mess of actual Japanese games, they seem to work the same.  I own all of the games, I rip the iso and use it because it runs a little faster than the CD. I just tested the Japanese Valkyrie Profile game disc and it runs fine. I had thought the .iso would be faster but it seems the actual game disc run the same. I may be mistaken. It seems like the games run fine **(sometimes if I hit alt+enter to go fullscreen it kills my xserver..... I don't know why)** *Maybe because I have Compiz+Emerald on.* Also, the bios launch doesn't even display correctly and yet the games run fine. When you first load a game and it says Playstation and shows the symbol, mine is just a grey screen but I can hear everything loading fine (sound of the launch)._ The reason I complain about the bios (I know the game works fine) is I have to GUESS where my cursor is in the memory cards, and it makes deleting things scary because I have to go by memory of the locations for the buttons and commands, and hope I delete the correct game etc. _

PS, the pSX says it's version 1.12 even though I installed your 1.11 and did not update it. I tried to update it but it wouldn't work if I updated it, so I locked the version. When I used the updated, 1.13 and type pSX /path/to/game it does not recognize the command pSX. I even used it from the pSX folder and it can't find it. I didn't try double clicking the pSX from the folder on the 1.13 version because at that time I didn't know where it was and 1.13 did not install a menu shortcut for the emulator. Maybe if I installed 1.13 and tried to create a new shortcut to the emulator????? Why the hell are the bios laggy? Games only lag if I move the window around and use Compiz effects while playing (like shaking the window in wobbly mode will make the game skip a little, but the game will not crash or anything.) 

PSS, the sound in Metal Gear Solid has a slight hum on the reverb (I think). I know it is not natural, but that may be due to the difficult of emulating MGS, I know it was a hard game for emulators to run correctly. No one would notice it unless you played it on a Playstation and know what it is suppose to sound like, because it is a faint hum sound that happens about every 4 seconds when you run around the game. What do you think?

The emulator start up sound is graphically weird and sounds weird. I made a recording of he in game sound and emulator sound. Maybe you can explain the weirdness....

[http://download.yousendit.com/F2D0CF21247ED138](http://download.yousendit.com/F2D0CF21247ED138)

3 small mp3 files~

Here is a video of the start up and gameplay, I recorded at 50% video quality to save space, it is a little jumpy; that is because of the recording not because of the emulator. The emulator start up is ALWAYS like that though. . Figured it may help if you can see the start up. The video is a .ogg file

[http://download.yousendit.com/5E26C6DA7A2ECE34](http://download.yousendit.com/5E26C6DA7A2ECE34)

More Info - 

FPS Test
8520 frames in 5.0 seconds = 1698.667 FPS
8490 frames in 5.0 seconds = 1697.773 FPS
8520 frames in 5.0 seconds = 1697.179 FPS

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig




**Pick for proof and inspiration to others out there~~ **
[http://img213.imageshack.us/img213/5346/screenshotne3.jpg](http://img213.imageshack.us/img213/5346/screenshotne3.jpg)

---

### Post by dfreer on 2007-12-19
As your games appear to run fine, I don't think it's a case of "incorrectly installed video drivers".

For the other issues, like the sound quality of MGS, I can be of no help (I only repackage the pSX binaries for installation on 32/64 bit debian-based linux distros, and I don't even have that game). This is the point where I'd redirect you to the pSX forums, just make sure you don't post anything about downloading ANY game/BIOS (not that you would ;) ) and you'll be fine.

What I can help you with is the pSX packages themselves. From the testing I've done and the people I've talked to, there hasn't been any major issues with using the newer pSX releases in linux (other than game compatibility, which isn't your problem).

So if you are up for it, I'd like to try properly wiping pSX from your system, installing 1.13 to see if it works correctly, if not then install 1.11 correctly (I haven't updated my 1.11 packages for the longest time, so there's bound to be some things we can fix). Of course we would backup your ISO's, memory cards, BIOS, etc first.

It may help out, so let me know if you wanna try reinstall pSX correctly! If you do, I'll need to know the following:
[list]
[*]What release of Ubuntu are you using?
[*]32 or 64 bit?
[/list]

---

### Post by tenchu77491 on 2007-12-19
AMD64, Ubuntu 7.10~

I'll give it a shot. I changed the path to my memory cards, so when it uninstalls it should not remove the folder I made, right? I made a new one inside a totally different folder (in a totally different directory).

---

### Post by tenchu77491 on 2007-12-20
I uninstalled yours by removing it from synoptic, then I did 

sudo apt-get autoremove, which got rid of more stuff from it. 

I then installed version 1.13, made a custom launcher because it didn't appear in my menu. 

NOW, it still works the exact same as your 1.11 version.... the bios work the same, but the sound of the bios loading is a little better.

Is there more of it installed somewhere? Did I not remove it all?

PS, sorry for double post

---

### Post by dfreer on 2007-12-20
> **tenchu77491 said:**
> AMD64, Ubuntu 7.10~

I'll give it a shot. I changed the path to my memory cards, so when it uninstalls it should not remove the folder I made, right? I made a new one inside a totally different folder (in a totally different directory).

It should never remove the memory cards, it should really only remove files that came with the original package. However, in one version of 1.11 I did include the memory cards (so removing pSX = deleting memory cards :( ), so not knowing which version you have it's good to move the memory cards, then delete pSX. And it's always good to back things up when doing something to your system ;)

If you have your stuff backed up (including your original configuration file if you want to keep it), this is what you should do to make sure it is fully gone:
```
sudo apt-get remove --purge psx32 psx lib32gtkglext1
sudo rm -Rv /usr/local/games/psx*
rm -Rv ~/.pSX/
```

Then, make sure your repository list is clean (there should only be one line concerning my repository, and it should be the gutsy repository):
```
cat /etc/apt/sources.list | grep dfreer
```

Then, to reinstall correctly if the repository above checks out:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install psx32
```

Normally, removing pSX isn't anywhere near that complicated. But again, not knowing exactly which package you had and the files included in it, it's entirely possible that you got a version that I didn't make properly.

The latest 1.13 version should have a correct menu entry (that's been the case since at least feisty, so unless your gnome menu is somehow messed up...) as well. Also, not sure if we tried this yet, but try launching pSX from the commandline, and see if it gives you any errors when loading the BIOS:
```
psx32
```


p.s. If at any time you feel the need, you can always install pSX from the official website instead of using my package. Mainly, all I do is add a menu entry, and repackage the 32-bit libraries it needs, so as long as you have install pSX from my repos at least once, you should be set. I just think it's easier to use the repo ;)

---

### Post by tenchu77491 on 2007-12-21
I did everything and updated my launch command after I reinstalled. It still works the exact same. After I reinstalled and launched it for the first time it created an old directory I used (so somehow it knew, although I moved my config file and erased it with the commands). What does that mean? Is there another config somewhere? The bios work the same.....

---

### Post by dfreer on 2007-12-21
pSX 1.11 & 1.12 store the configuration file in the same directory as pSX. pSX 1.13 will check if there is a configuration file in the same directory, if not, then it will store it's settings in ~/.pSX/

---

### Post by kokomonjo on 2007-12-23
Hi all I was wondering how to install the playstation bios. I have the emulator psx32. Also does anyone have the package and commands to install a playstation 2 emulator? i would rather have that. i am really new to ubuntu and do not totally understand the whole installation process so as much detail as possible would be greatly appreciated.

---

### Post by dfreer on 2007-12-23
Once you have the playstation BIOS file (don't ask where to get it ;) ), you can start pSX and it will ask you where your BIOS is located. Just point it to the BIOS and it should work.

[PCSX2]("http://www.pcsx2.net/") is currently the only PS2 emulator for linux that I know of. It needs quite a beefy system to run, as well as it's own BIOS file. There are several threads here regarding PCSX2 that people more knowledgable than me are watching, as well as google.

---

### Post by kokomonjo on 2007-12-23
Hi I was just reading this on another site and it made this comment
"PS2 mode that can be accessed via the command line" about the version of the playstation emulator that i have PSX v 1.13. does anyone know anything about this?

---

### Post by dfreer on 2007-12-23
> **kokomonjo said:**
> Hi I was just reading this on another site and it made this comment
"PS2 mode that can be accessed via the command line" about the version of the playstation emulator that i have PSX v 1.13. does anyone know anything about this?

Yepp, check the end of this post out:
[http://ubuntuforums.org/showpost.php?p=2557614&postcount=28](http://ubuntuforums.org/showpost.php?p=2557614&postcount=28)
Basically, it has PS2 support, but it doesn't run any games yet.

---

### Post by sambucuself on 2007-12-28
THAAANK YOUUUU!

it works perfectly. oh what more did I try, this is great!

---

### Post by RyanKage on 2008-01-03
Hi,
I'm on 32 bit Ubuntu Gutsy Gibbon. I followed your 32 bit guide, and I have a couple of questions. First, is there any way to get an icon instead of having to always use the terminal to open the emu (terminal: sudo psx)? And, whenever I open it via terminal I always get: Warning. Desktop/psx bios is not a valid BIOS image. I then click OK and I can go into the PSX v1.13 screen and it's black... I did download and extracted the Playstation BIOS onto my desktop. I'm a complete noob when it comes to emu's on the Linux platform, a little help would be nice ;).

---

### Post by dfreer on 2008-01-03
Hi RyanKage,

  There should already be an icon/shortcut for pSX, try looking in Applications > Games > pSX. If there isn't, you could create one yourself, I'll post more instructions on how to do that later.

  Another thing is that if you are launching pSX from the terminal, you should never run pSX with sudo, try just launching it like so:
```
psx
```
Note however, if you previous configured pSX using sudo, your user settings are likely to be stored in root's folder, instead of your home folder. So basically you will need to configure everything once again.

  As for the BIOS problem, it sounds like the BIOS image you have is a bad image. pSX tends to be a bit picky with that. You may need another BIOS image.

@sambucuself - You're welcome!

---

### Post by RyanKage on 2008-01-03
Awesome, thank you so much! I'm guilty of never looking in the Games folder lol. But it's wieird though, it did the BIOS thing again... I did fix it via sudo psx through the terminal lol... Ah the joy of learning a new OS :). I'll start poking around psx again haha. I was playing with it earlier at work and I did manage to play Final Fantasy Tactics perfectly with it. Again, thanks!

---

### Post by RyanKage on 2008-01-03
I don't know what it is, but everything is working perfectly via: sudo psx lol... I'm saving and loading Final Fantasy Tactics perfectly that way.

---

### Post by RyanKage on 2008-01-03
Crap, now it's stating: Core dumped lol... fun fun fun.

---

### Post by dfreer on 2008-01-04
> **RyanKage said:**
> I don't know what it is, but everything is working perfectly via: sudo psx lol... I'm saving and loading Final Fantasy Tactics perfectly that way.

It's totally up to you if you want to run it with sudo. It just means it has potential to fsk up your system, but whatever works :D

> **RyanKage said:**
> Crap, now it's stating: Core dumped lol... fun fun fun.

Does it do it just on startup, or with certain games? Also, try running it from the terminal to see if it outputs any useful messages besides core dumped.

---

### Post by RyanKage on 2008-01-04
Hm, it happened twice in: Final Fantasy Tactics, but it seems fine now... I also just tried Mega Man 8 and that's running really smoothly. If I have any other weird problems I'll let you know :). In the meantime thanks for your help! :biggrin:

---

### Post by GSF1200S on 2008-01-13
After fighting war to get a PSone emulator working, this neat little thread has me playing FF VII. Thanks alot for this ;)

---

### Post by anjilslaire on 2008-01-18
Sorry, posted in wrong thread. Misposted.

---

### Post by |Jasp| on 2008-01-19
Hello.  I have read many posts regarding PSX.  I have got everything under control except the following:
Memory Cards:
     Is there a way to configure them with the Terminal?  I thought I saw some code for that out there.  But I can't find it now that I am looking for it.  
File Menu:
     When I start PSX and click File, in order to load the game from CD, I can't see the menu.  It's like the menu layer is behind opening screens.  When I scroll the mouse up and down where the menu should be I can see flashes of the text.  I can estimate how far down on the menu the "load from CD" option is and select it to play the game.  However, I can't accurately find the Configuration option or other menu options near the bottom.  

Note:  I have installed libgtkglext1 (latest version), PSX (latest Version), and PSX Frontend.

Thank you all for any help you can provide.

---

### Post by dfreer on 2008-01-22
> **|Jasp| said:**
> Hello.  I have read many posts regarding PSX.  I have got everything under control except the following:
Memory Cards:
     Is there a way to configure them with the Terminal?  I thought I saw some code for that out there.  But I can't find it now that I am looking for it.  
File Menu:
     When I start PSX and click File, in order to load the game from CD, I can't see the menu.  It's like the menu layer is behind opening screens.  When I scroll the mouse up and down where the menu should be I can see flashes of the text.  I can estimate how far down on the menu the "load from CD" option is and select it to play the game.  However, I can't accurately find the Configuration option or other menu options near the bottom.  

Note:  I have installed libgtkglext1 (latest version), PSX (latest Version), and PSX Frontend.

Thank you all for any help you can provide.

I haven't been around much, sorry everyone. Anyways, regarding the issue with not being able to see the menus, about the only thing I can suggest is try turning off desktop effects/compiz fusion if you are running it.
As for configuring memory cards, I haven't heard of any way to manage them via terminal (by manage I assume you mean copy/deleting saves on the memory card), but the BIOS should work just like the original playstation. Just start pSX without a CD/Image, and then manage your saves through the BIOS.

---

### Post by jw5801 on 2008-01-22
> **|Jasp| said:**
> Hello.  I have read many posts regarding PSX.  I have got everything under control except the following:
Memory Cards:
     Is there a way to configure them with the Terminal?  I thought I saw some code for that out there.  But I can't find it now that I am looking for it.  
File Menu:
     When I start PSX and click File, in order to load the game from CD, I can't see the menu.  It's like the menu layer is behind opening screens.  When I scroll the mouse up and down where the menu should be I can see flashes of the text.  I can estimate how far down on the menu the "load from CD" option is and select it to play the game.  However, I can't accurately find the Configuration option or other menu options near the bottom.  

Note:  I have installed libgtkglext1 (latest version), PSX (latest Version), and PSX Frontend.
 
Thank you all for any help you can provide.

If he just means specify which memory cards to use from the commandline (ie. to avoid menus which aren't working) then the -a switch will do it: ```
psx32 -help

psx [options] <path to cd> [<ppf file>] [<save state>]
Options: -w                 Windowed
         -f                 Full screen
         -c{i/r}            R3000 CPU mode (interpreter/recompiler)
         -C{i/r}            R5900 CPU mode
         -r                 Enable event rescheduling
         -s                 Disable frame skipping
         -2                 PS2 mode
         -t                 Start with status display enabled
         -F                 Disable pause
         -a<slot>,<fname>   Insert memory card
         -p-                No pad in port 0
         -A                 Disable async cd access (always block)
         -P                 Disable 50hz (always use 60hz)
         -p<mode>           Pad mode
                            0 - SCPH-1010: Normal pad
                            1 - SCPH-1150: Analog+rumble
                            2 - SCPH-1200: Dualshock

#So, the following will run it specifying a memory card to use in slot 1:

psx32 -a1,~/memcard
```

---

### Post by teslarage on 2008-01-28
> **|Jasp| said:**
> 
File Menu:
     When I start PSX and click File, in order to load the game from CD, I can't see the menu.  It's like the menu layer is behind opening screens.  When I scroll the mouse up and down where the menu should be I can see flashes of the text.  I can estimate how far down on the menu the "load from CD" option is and select it to play the game.  However, I can't accurately find the Configuration option or other menu options near the bottom.  


I had this issue before and the solution is really very simple.

Turn OFF Compiz desktop effects :D

---

### Post by dfreer on 2008-02-12
Server is down for an extended while. I just moved and need to get a new ISP, so it may be awhile. Sorry guys :(

---

### Post by jw5801 on 2008-02-15
You wouldn't be able to attach the latest psx32 .deb to the initial post or host it somewhere would you? I wound up doing a fresh install only to realise that I'd cleaned out  /var/cache/apt/archives/ before I made a backup of my old install :( I'm not enjoying being without an emulator!

---

### Post by dfreer on 2008-02-16
Here's some packages for ya:
I included the pSX Frontend in each package. And, lib32gtkglext1 for the amd64 package.

Hopefully the server will be back online within the month.

---

### Post by jw5801 on 2008-02-16
Legend!

---

### Post by jw5801 on 2008-02-16
This is much nicer when the server is up...

```
jw5801@jw5801:~/.install$ sudo dpkg -i psx32_1.13-3.1_gutsy-amd64.deb 
Selecting previously deselected package psx32.
(Reading database ... 99330 files and directories currently installed.)
Unpacking psx32 (from psx32_1.13-3.1_gutsy-amd64.deb) ...
dpkg: dependency problems prevent configuration of psx32:
 psx32 depends on lib32rsvg2-2 (>= 2.18.2); however:
  Package lib32rsvg2-2 is not installed.
 psx32 depends on lib32gsf-1-114 (>= 1.14.7-3.0); however:
  Package lib32gsf-1-114 is not installed.
 psx32 depends on lib32croco3 (>= 0.6.1); however:
  Package lib32croco3 is not installed.
dpkg: error processing psx32 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 psx32
```

None of those are available using apt...

---

### Post by mohbana on 2008-02-16
hey keep up the good work, can you please inform us when the server is back up.

---

### Post by dfreer on 2008-02-17
I'll let you guys know when the server is back up. Calling the new ISP on Monday to get hooked up, and then I estimate a couple of days for that to happen. As long as I don't have any major issues like ports being blocked, I should be up and running again within 2 weeks I hope.

As for the packages that are needed, here they are :( I have quite a couple of packages in the repo, trying to remember everything that my pSX packages depended on.

---

### Post by jw5801 on 2008-02-17
Rockin'! That gets everything up and running. Cheers dfreer!

---

### Post by dfreer on 2008-02-19
> **jw5801 said:**
> Rockin'! That gets everything up and running. Cheers dfreer!

Great to know :D

@ Everyone - ISP is installing our new FIOS on thursday, and as long as I don't have any issues with ports the server will be back up and running soon! 
Not only that, but with 15 Mbps up/15 Mbps down ;)
In comparison, the server was previously hooked up to a 2.5 Mbps down/1 Mbps up connection.

---

### Post by dfreer on 2008-02-22
So as of now, **the server is up and running on port 8080**. However, I need to test and see whether that's going to affect people using apt-get, and then of course update all of the old links/how-to's. 

Example usage would be to go to [http://packages.dfreer.org:8080/pool/](http://packages.dfreer.org:8080/pool/) and download any packages you may need.

But the optimal solution would be to get a web redirect working where all traffic to the dfreer.org domain is routed to port 8080, so that all the old links would still work. I'm struggling with that right now, hopefully I will figure it out soon. In the meantime, use port 8080.

---

### Post by MakLeod on 2008-02-28
I'm not able to load neither the page nor the repository...is anyone else experiencing the same thing?

---

### Post by jw5801 on 2008-02-28
```
echo "deb http://packages.dfreer.org:8080 gutsy main" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org:8080/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
```

If you've still got the old sources.list line that didn't include the reference to port 8080, then you'll want to remove that entry and run the commands above. Then it should be working fine!

---

### Post by mab1376 on 2008-03-13
it appears the server is down...

---

### Post by CraymelCage on 2008-03-14
Hi I've used this guide before and it worked flawlessly. I reinstalled ubuntu 7.10 and tried to install psx again but when ever I try entering 

echo "deb [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080) gutsy main" | sudo tee -a /etc/apt/sources.list
wget [http://packages.dfreer.org:8080/7572013D.gpg](http://packages.dfreer.org:8080/7572013D.gpg) -O- | sudo apt-key add -
sudo apt-get update

my terminal gives me this

deb [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080) gutsy main
$ echo "deb [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080) gutsy main" | sudo tee -a /etc/apt/sources.list
deb [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080) gutsy main
$ wget [http://packages.dfreer.org:8080/7572013D.gpg](http://packages.dfreer.org:8080/7572013D.gpg) -O- | sudo apt-key add -
--15:00:31--  [http://packages.dfreer.org:8080/7572013D.gpg](http://packages.dfreer.org:8080/7572013D.gpg)
           => `-'
Resolving packages.dfreer.org... failed: Name or service not known.
gpg: no valid OpenPGP data found.

I really like this psx emulator so if anyone can help me with this I'd really appreciate it.

---

### Post by dfreer on 2008-03-15
[http://ubuntuforums.org/showpost.php?p=4340576&postcount=182](http://ubuntuforums.org/showpost.php?p=4340576&postcount=182)
[http://ubuntuforums.org/showpost.php?p=4346682&postcount=186](http://ubuntuforums.org/showpost.php?p=4346682&postcount=186)

Repository to be up again soon.

---

### Post by mrflashpants on 2008-04-08
THANK YOU, THANK YOU, THANK YOU!!!

Now I can play Final Fantasies VII - IX again!

This is great b/c I just finished the GBA and DS versions of FF I - VI  :)

---

### Post by TWO on 2008-04-11
> **dfreer said:**
> [http://ubuntuforums.org/showpost.php?p=4340576&postcount=182](http://ubuntuforums.org/showpost.php?p=4340576&postcount=182)
[http://ubuntuforums.org/showpost.php?p=4346682&postcount=186](http://ubuntuforums.org/showpost.php?p=4346682&postcount=186)

Repository to be up again soon.

Thanks for the download links. However, the 'additional packages' zip file was empty but I don't think it matters though, as the other debs have installed without a problem.

---

### Post by skroops on 2008-04-23
I haven't been able to get pSX to install on hardy using this guide, even by downloading the packages since the repo is still down. Can someone give me a quick guide how to get this running on Hardy?

---

### Post by Grishka on 2008-04-23
> **skroops said:**
> I haven't been able to get pSX to install on hardy using this guide, even by downloading the packages since the repo is still down. Can someone give me a quick guide how to get this running on Hardy?

just get it from the homepage, unpack and run. you'll need ia32-libs package to run it on a 64-bit system.

---

### Post by skroops on 2008-04-23
I found a guide for this at the pSX forums, courtesy of andrebait.  It works great and in my opinion much simpler than dfreer's guide (still props to dfreer for his method). I'll copy and paste it here for anyone else who tries to get this working.

[quoted from andrebait at [http://psxemulator.proboards54.com/index.cgi?action=display&board=feedback&thread=1202&page=1]]("http://psxemulator.proboards54.com/index.cgi?action=display&board=feedback&thread=1202&page=1%5D")


[I][FONT=Arial]"[/FONT][SIZE=2][FONT=Arial]Making distribution specifica packages is great, but I like the "generic" way ^^'
I mean... generic if you use Debian based distros...

Well...
My way is:

 - Download pSX 1.13 from the website
 - Extract anywhere
- Install getlibs. It's a program written specifically to those who use x86-64 linux and face incompatibility due to the lack of 32-bit libraries. You can use it in many ways (read in this post [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ).

My preferred way it to use it to autodetect the libraries needed and install them automatically.
So... save the file anywhere and install getlibs
[/FONT]    [/SIZE][SIZE=2][INDENT]```
cd /home/user/
tar jxf pSX_linux_1_13.tar.bz2
```[/INDENT][FONT=Arial]A folder named pSX will be created, so...
[/FONT] [/SIZE][/I][INDENT][I]```
cd pSX
getlibs pSX
```[/I][/INDENT][SIZE=2][I][FONT=Arial]It will find any 32-bit libraries pSX needs and are not present and install them. It'll ask you for the sudo password too.

After that, just run pSX "[/FONT][/I] 
[/SIZE]

---

### Post by skroops on 2008-04-23
@Grishka:  I tried that and it didn't work for me for whatever reason, anyway I found a solution. Thanks

---

### Post by dfreer on 2008-04-24
> **skroops said:**
> I found a guide for this at the pSX forums, courtesy of andrebait.  It works great and in my opinion much simpler than dfreer's guide (still props to dfreer for his method). I'll copy and paste it here for anyone else who tries to get this working.

[quoted from andrebait at [http://psxemulator.proboards54.com/index.cgi?action=display&board=feedback&thread=1202&page=1]]("http://psxemulator.proboards54.com/index.cgi?action=display&board=feedback&thread=1202&page=1%5D")


[I][FONT=Arial]"[/FONT][SIZE=2][FONT=Arial]Making distribution specifica packages is great, but I like the "generic" way ^^'
I mean... generic if you use Debian based distros...

Well...
My way is:

 - Download pSX 1.13 from the website
 - Extract anywhere
- Install getlibs. It's a program written specifically to those who use x86-64 linux and face incompatibility due to the lack of 32-bit libraries. You can use it in many ways (read in this post [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ).

My preferred way it to use it to autodetect the libraries needed and install them automatically.
So... save the file anywhere and install getlibs
[/FONT]    [/SIZE][SIZE=2][INDENT]```
cd /home/user/
tar jxf pSX_linux_1_13.tar.bz2
```[/INDENT][FONT=Arial]A folder named pSX will be created, so...
[/FONT] [/SIZE][/I][INDENT][I]```
cd pSX
getlibs pSX
```[/I][/INDENT][SIZE=2][I][FONT=Arial]It will find any 32-bit libraries pSX needs and are not present and install them. It'll ask you for the sudo password too.

After that, just run pSX "[/FONT][/I] 
[/SIZE]

I like the idea of getlibs, it seems like a well written script that does it's job. I really need to play around with it, the only things I'd be concerned about would be:

Does it track what changes it makes to the system and offer a way to undo changes?
Does it correctly deal with libraries that rely on other packages? Can't remember any off the top of my head, but I know I dealt with a few before.

But to each his own... I really hate being down for so long, there's nothing wrong with the actual website/server/domain name itself. Basically I just need to finish up with the webhop, offering access via the original port 80 and port 8080, and fix the virtual name server part of apache. 

Some clever people may be able to actually download packages, more power to you! And of course Hardy packages are coming soon as well!

---

### Post by mohbana on 2008-04-29
what's the current status of this? the first post seems to have been updated some time in feb!  Well how does one install this on 64bit hardy? thanks in advance

---

### Post by drunkmatador on 2008-05-06
Is this working for Hardy Heron? I'm having problems installing and am not sure if that's why.

---

### Post by drunkmatador on 2008-05-06
Haha whoops didn't read your post. You asked pretty much the same thing.

Well I installed it using getlibs and as soon as I told it where my bios was located, it started up VERY choppy. So much that I could harldy stand waiting through the startup screen. Now it is stuck on the logo only it's all black, with the SONY in blue letters. Weird, huh? Also it's noticably slowing my computer to where everything I'm typing is a little lagged.

pcsx seems to run fine, though. Other than I haven't figured out how to work the menu and it won't find any video drivers but the one it was downloaded with (from repos).

---

### Post by drunkmatador on 2008-05-06
Ok sorry about posting again.. but I downloaded dfreer's amd64 package for pSX, and installed lib32gtk just fine. Now when I try to open the psx32 deb included it says that I need lib32rsvg2-2 and when i run a google I cannot find anything on that file.

Hmm...

---

### Post by dfreer on 2008-05-07
> **drunkmatador said:**
> Ok sorry about posting again.. but I downloaded dfreer's amd64 package for pSX, and installed lib32gtk just fine. Now when I try to open the psx32 deb included it says that I need lib32rsvg2-2 and when i run a google I cannot find anything on that file.

Hmm...

I've attached those .deb files in my post, hopefully that's all you need. Currently I've been working on the zsnes solution :(

BTW, choppy BIOS loading screen is often because you don't have your 3D acceleration working for your video card. Try running glxgears and see what kind of FPS you get, and make sure that glxgears --info reports that 3D rendering is turned on.

---

### Post by drunkmatador on 2008-05-08
When attempting to install lib32rsvg2-common I get:

> mozzles@mozzles-laptop:~/Desktop$ sudo dpkg -i lib32rsvg2-common_2.18.2-3.0_gutsy-amd64.deb 
(Reading database ... 137890 files and directories currently installed.)
Unpacking lib32rsvg2-common (from lib32rsvg2-common_2.18.2-3.0_gutsy-amd64.deb) ...
dpkg: error processing lib32rsvg2-common_2.18.2-3.0_gutsy-amd64.deb (--install):
 trying to overwrite `/usr/lib32/gtk-2.0/2.10.0/loader-files.d/librsvg2-common.loaders', which is also in package ia32-libs
Errors were encountered while processing:
 lib32rsvg2-common_2.18.2-3.0_gutsy-amd64.deb   


I got a program that will let me install 32 bit programs on my x64 but I can't remember what it's called now. It'd be convenient if there's somewhere I can find out what packages I've added recently, through apt-get and synaptic both. Know of a thing?

---

### Post by drunkmatador on 2008-05-08
Ok so.. I ran pSX again and it ran fine now. Maybe just needed a restart from messing with things.. I actually didn't get my video card fully configured until sometime yesterday so I might not have tried afterwards.. haha.

Well I'm glad to have it working again but a couple questions.. are pcsx save state files or memory card files compatible with pSX? My girlfriend and I started a game on FF7 last night and don't really want to start it over but this emulator runs much smoother.

Wonder if I should find out what's up with those packages anyways? Could be a bug.

---

### Post by dfreer on 2008-05-08
> **drunkmatador said:**
> Ok so.. I ran pSX again and it ran fine now. Maybe just needed a restart from messing with things.. I actually didn't get my video card fully configured until sometime yesterday so I might not have tried afterwards.. haha.

Well I'm glad to have it working again but a couple questions.. are pcsx save state files or memory card files compatible with pSX? My girlfriend and I started a game on FF7 last night and don't really want to start it over but this emulator runs much smoother.

Wonder if I should find out what's up with those packages anyways? Could be a bug.

The reason for the file conflict is that the pSX package you installed was developed for Gutsy, not Hardy. pSX required several 32-bit libraries to be installed which simply were not available as 64-bit packages from the main ubuntu repos. So I repackaged the 32-bit libs, packaged the 32-bit psx, and everyone's happy. To make sure things ran smoothly from my repo, I made pSX depend on *my* specific 32-bit library packages so that they would get installed when psx was installed.

Now, in Hardy, they have taken ia32-libs and placed a WHOLE ton of new 32-bit libraries, including several that I had already repackaged. When you tried to use my pSX gutsy package, it complained about not having my 32-bit libs installed, whether they were installed with ia32-libs or not.

I can't remember what the solution for transfering saved games from different emulators was, you may want to check with the official pSX forums for that issue. I do believe that all the pSX emulators save memory cards in the same way (the *.bin files), so they should be compatible (make backups first!!!).

Try creating a new memory card in pSX, load the old pcsx memory card into slot 1 and the new pSX memory card in slot 2 and load the pSX BIOS up (without a game inserted). If you can see the contents of the old pcsx card, try copying the saved games from the old to the new and just use it. As long as you use a copy of the original pcsx card, who cares if you accidently corrupt it?

---

### Post by drunkmatador on 2008-05-08
Thank you very much.. It sounds like you went through a bit of work to get it all set up for us x64 users, and it runs great so good job. How is zsnes coming along? I'd offer to help but I don't know anything about coding yet.

Oh and I got the memory card issue solved.. just had to point pSX to the files that I used in pcsx and they work fine.

---

### Post by dfreer on 2008-05-08
> **drunkmatador said:**
> Thank you very much.. It sounds like you went through a bit of work to get it all set up for us x64 users, and it runs great so good job. How is zsnes coming along? I'd offer to help but I don't know anything about coding yet.

Oh and I got the memory card issue solved.. just had to point pSX to the files that I used in pcsx and they work fine.

No coding needed :D just need to figure out a way for zsnes to output sound with this newfangled pulseaudio thingy, especially in 64-bit hardy.

---

### Post by drunkmatador on 2008-05-08
I have no idea what pulseaudio is but I've read the name a few times on here. Some new standard that's in hardy, right? Or something like that.

Had another question, if I'm making a link to automatically start up a game in pSX, what command would I put in? It would be something like ./pSX and then path to the rom, right?

---

### Post by drunkmatador on 2008-05-08
Nevermind, I just went ahead and tried the command ./pSX with path to rom afterwards, booted up fine! Now I have a dedicated link to FF7 in my Games menu, with an icon and everything! Cool, huh?

---

### Post by dfreer on 2008-05-09
@Everyone who has waited so long...

Try [http://packages.dfreer.org](http://packages.dfreer.org) :D
You should be able to use the repository once more, without the port 8080.

Still working on hardy though...

---

### Post by savethewabbit on 2008-05-09
i've just installed pSX... but it's not working quite well - 
as soon as it opens, the terminal gets flooded with these messages:
```

r3000: executed illegal opcode ffffffff
r3000: executed illegal opcode bfc0df4a
r3000: executed illegal opcode 00002cdc
r3000: executed illegal opcode ffffffff
r3000: executed illegal opcode ffffffff
r3000: executed illegal opcode bfc0df4a
r3000: executed illegal opcode 00002cdc
r3000: executed illegal opcode bfc0df3b
r3000: executed illegal opcode 00008674
r3000: executed illegal opcode 00000001
r3000: executed illegal opcode 00008674
```
and when i click to open a menu 
```

sound: underrun
sound: underrun

```

and i can't open the menus to try out a game because they just appear and disappear in the blink of an eye as soon as i click.
anyone knows what this is caused by?

eta: i just managed to click "insert cd drive" and loaded a game. the pSX window stays black though and the terminal keeps getting "sound: underrun" messages. :\

---

### Post by dfreer on 2008-05-10
What are you running, gutsy or hardy? I haven't made a hardy package, but the gutsy packages should work just fine (for gutsy).

Are your video card 3D drivers correctly installed? Also try increasing the sound latencies within the options about 10 ms.

---

### Post by Mangust22 on 2008-05-12
I'm using Ubuntu 8.04 and pSX 1.13. After last updates (maybe week ago) my second USB gamepad was broken (work only Up, Down, Left and Right buttons). I tested /dev/input/js1 - all works fine (turbo, analog, etc). It's not a hardware's problem or driver's (gamepads are equal). I think it's a problem between some gnomelib and pSX. Did anybody face that challenge? Any idea to resolve this problem? I changed gamepad's - normal works only js0. :(

---

### Post by dfreer on 2008-05-13
> **Mangust22 said:**
> I'm using Ubuntu 8.04 and pSX 1.13. After last updates (maybe week ago) my second USB gamepad was broken (work only Up, Down, Left and Right buttons). I tested /dev/input/js1 - all works fine (turbo, analog, etc). It's not a hardware's problem or driver's (gamepads are equal). I think it's a problem between some gnomelib and pSX. Did anybody face that challenge? Any idea to resolve this problem? I changed gamepad's - normal works only js0. :(

You may want to try the official pSX forums for this question, mangust.

---

### Post by Ryuki_NdranC on 2008-05-13
> **dfreer said:**
> @Everyone who has waited so long...

Try [http://packages.dfreer.org](http://packages.dfreer.org) :D
You should be able to use the repository once more, without the port 8080.

Still working on hardy though...

i added the gutsy repositories  and i get ERROR 302 not found :(

I don't use gutsy, i have hardy but somewhere in the forum i reed someone installed gutsy deb and it worked just fine :)

Any updates in the repos status? or hardy AMD64 debs? o.O?

Thanks a lot for the support :)

---

### Post by dfreer on 2008-05-13
> **Ryuki_NdranC said:**
> i added the gutsy repositories  and i get ERROR 302 not found :(

I don't use gutsy, i have hardy but somewhere in the forum i reed someone installed gutsy deb and it worked just fine :)

Any updates in the repos status? or hardy AMD64 debs? o.O?

Thanks a lot for the support :)

Can you copy + paste the exact output? The website itself [http://packages.dfreer.org](http://packages.dfreer.org) seems to be working as far as I can tell. It's gotta be a problem with the repository itself then.

EDIT: No need to post output, I'm getting similar error reports from the zsnes thread. le sigh...

---

### Post by Ryuki_NdranC on 2008-05-14
Just in case, here is the output:

> W: Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by cjb5089 on 2008-05-16
Hey, im running hardy 64 on a dual core amd, i tried installing psx, couldnt get it to work, then i tried ur "old" instructions and i got all the way to the bottom, but then its giving me errors when i type in "./pSX" and then it says something about the bios. heres the terminal output...

(pSX:9551): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:9551): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:9551): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:9551): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:9551): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:9551): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:9551): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:9551): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

then it opens up a dialogue box... bios not found.    This emulator requires a BIOS image which must be installed in the bios folder.  

if you could help me out, id be much appreciated, ive been having nothing but problems trying to game game emulators to work, both for pcsx and znes and now im taking a crack at this one

---

### Post by dfreer on 2008-05-16
> **cjb5089 said:**
> if you could help me out, id be much appreciated, ive been having nothing but problems trying to game game emulators to work, both for pcsx and znes and now im taking a crack at this one

Playstation Emulators are different from say a SNES or NES emulator, in the sense that they have a BIOS (when you turn on a SNES, if there is no cart in the system nothing happens. When you turn on a playstation without a game, the BIOS loads and you can configure your memory cards among other things).

The whole point of this is, in order to actually use the emulator, you will need a playstation BIOS. And it is against the rules of this forum (not to mention legal issues) for us to give or otherwise tell you how to obtain the playstation BIOS.

---

### Post by Ryuki_NdranC on 2008-05-16
> **dfreer said:**
> Playstation Emulators are different from say a SNES or NES emulator, in the sense that they have a BIOS (when you turn on a SNES, if there is no cart in the system nothing happens. When you turn on a playstation without a game, the BIOS loads and you can configure your memory cards among other things).

The whole point of this is, in order to actually use the emulator, you will need a playstation BIOS. And it is against the rules of this forum (not to mention legal issues) for us to give or otherwise tell you how to obtain the playstation BIOS.

does this mean that the old instructions work for hardy amd64? cos i being waiting for some updates on the broken repos but if i can make it work now it would be great.

---

### Post by dfreer on 2008-07-14
> **Ryuki_NdranC said:**
> does this mean that the old instructions work for hardy amd64? cos i being waiting for some updates on the broken repos but if i can make it work now it would be great.

Hmmm they should in theory; generally the issue with running 32-bit programs in a 64-bit Linux is that the program needs 32-bit libraries as well. The only 32-bit libraries that pSX needs besides those provided in ia32-libs is libgtkglext, IIRC.

The problem with Hardy was that even WITH all the needed 32-bit libraries, myself and others couldn't get pSX to work. I believe it has to do with changes in the Ubuntu sound system, and since pSX refuses to function without sound...

Anyways, I'm going to be working on this now that my repository is back online. Hopefully I can either figure it out and get pSX working, or perhaps if it's a problem with pSX itself (zsnes dev's released a new version of zsnes due to changes in Debian/Ubuntu) pSXAuthor will be willing to recompile pSX for us.

---

### Post by riokushen on 2008-07-29
Your guide works well and pSX runs. 

But its window is always flickering, whats wrong with my system?

---

### Post by dfreer on 2008-08-01
> **riokushen said:**
> Your guide works well and pSX runs. 

But its window is always flickering, whats wrong with my system?

Not entirely sure. It may be a refresh rate issue, or you may want to enable triple buffering/vsync.

---

### Post by Starlight on 2008-08-10
I have a problem :( when I use the packages.dfreer.org repository, I get the same error as Ryuki_NdranC, and when I use the rowdy.dfreer.org:8080 I don't get any errors, but it seems there's no psx or psx32 package there... at least a search in synaptic doesn't find it...

edit: I looked at the website which opens when I go to packages.dfreer.org, and it seems that there are no psx packages for hardy... do the packages from gutsy work?

edit2: I've just checked, they aren't working :(

---

### Post by dfreer on 2008-08-10
> **Starlight said:**
> I have a problem :( when I use the packages.dfreer.org repository, I get the same error as Ryuki_NdranC, and when I use the rowdy.dfreer.org:8080 I don't get any errors, but it seems there's no psx or psx32 package there... at least a search in synaptic doesn't find it...

edit: I looked at the website which opens when I go to packages.dfreer.org, and it seems that there are no psx packages for hardy... do the packages from gutsy work?

edit2: I've just checked, they aren't working :(

Firstly, packages.dfreer.org will redirect to rowdy.dfreer.org:8080. I just checked it via proxy and it still works using the web browser.

Next, if you are using apt-get, you need to have rowdy.dfreer.org:8080 in your /etc/apt/sources.list. For some reason apt-get can't handle web redirects.

Last, I haven't made a psx package for hardy, sorry :( So far, I've been having limited success getting it to work on my system. I'd recommended manually downloading pSX from the official website:
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

Then run ldd on it to make sure you have the needed libraries:
```
cd */path/to/pSX/here/*
ldd ./pSX
```

If any of them are missing (it will most likely be libgtkglext1), you will need to obtain those 32-bit libraries and place them in your /usr/lib32/ folder. My gutsy package *may* work for this, or you may manually download the libraries here:
[http://packages.ubuntu.com/hardy/i386/libgtkglext1/download](http://packages.ubuntu.com/hardy/i386/libgtkglext1/download)

Extract the .deb by right-clicking on it and manually place the 4 following files in /usr/lib32/
libgdkglext-x11-1.0.so.0
libgdkglext-x11-1.0.so.0.0.0
libgtkglext-x11-1.0.so.0
libgtkglext-x11-1.0.so.0.0.0

Beyond that, all other 32-bit libraries should already be installed in the ia32-libs package. Good luck with getting pSX to run, I'm of the opinion that either pulseaudio has drastically changed the ALSA sound system such that pSX is unable to use it, or that the pSX binary needs to be recompiled for Hardy. I honestly don't know.

---

### Post by feenicks on 2008-08-13
YOU SO ROCK!!

Thanks for putting this together in a package.  I had downloaded the tar from psxemulator.gazaxian.com but I don't know how to install that.  Can someone enlighten me?  Just for my own education, how do you install from the tar.bz2 files?

---

### Post by dfreer on 2008-08-13
> **feenicks said:**
> YOU SO ROCK!!

Thanks for putting this together in a package.  I had downloaded the tar from psxemulator.gazaxian.com but I don't know how to install that.  Can someone enlighten me?  Just for my own education, how do you install from the tar.bz2 files?

A tar.bz2 file isn't quite like an .exe in that it's an installable program. It's really just a compressed folder just like .rar and .zip. Also remember, it's really two compressed folders, the .tar and the .bz2. Like a *.rar.zip file.

So the proper way to install it would be to right-click on the .tar.gz archive and select "Extract here" in nautilus. You could also double-click it which opens it with an archive manager.

You'll end up with a couple files, the main one being a binary file called pSX. This is the actual program, you'll need to make sure it is executable and then launch it. Through the terminal you can launch executables simply by calling it's name, like so:
```
cd ~/Desktop/pSX/
./pSX   ## The ./ means "in this directory"
```

---

### Post by speedy55555 on 2008-09-06
I might use this some time when there is some play station game that I want:smile:; although I'm wandering if there would be an play station 3 emulator.:?

---

### Post by dfreer on 2008-09-07
> **speedy55555 said:**
> I might use this some time when there is some play station game that I want:smile:; although I'm wandering if there would be an play station 3 emulator.:?

Not for quite some time. PS2 Emulation has just barely got off the ground, and it requires a Dual Core 2.4 Ghz or more.

---

### Post by master_d on 2008-10-15
for anyone interested here's how i got pSX working in hardy:

```

mkdir test
cd ./test
wget http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkglextlibgtkglext1_1.2.0-0ubuntu1_i386.deb
ar vx ./libgtkglext1_1.2.0-0ubuntu1_i386.deb 
tar -xvzf ./data.tar.gz
sudo cp ./usr/lib/libg* /usr/lib32/
tar -xvjpf ./pSX_linux_1_13.tar.bz2 
./pSX/pSX

```

you also have to put a copy of the bios file in ./pSX/bios but other than that the binary fired right up and I was able to play games right away.

One thing I was kind of unsure about was dfreer said to download the gtkglextlib manually and unpack it and move the libraries to /usr/lib32.  Is there a reason why it is done this way and gtkglextlib isn't installed through apt-get?  just curious




[/CODE]

---

### Post by dfreer on 2008-10-15
> **master_d said:**
> for anyone interested here's how i got pSX working in hardy:

```

mkdir test
cd ./test
wget http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gtkglextlibgtkglext1_1.2.0-0ubuntu1_i386.deb
ar vx ./libgtkglext1_1.2.0-0ubuntu1_i386.deb 
tar -xvzf ./data.tar.gz
sudo cp ./usr/lib/libg* /usr/lib32/
tar -xvjpf ./pSX_linux_1_13.tar.bz2 
./pSX/pSX

```

you also have to put a copy of the bios file in ./pSX/bios but other than that the binary fired right up and I was able to play games right away.

One thing I was kind of unsure about was dfreer said to download the gtkglextlib manually and unpack it and move the libraries to /usr/lib32.  Is there a reason why it is done this way and gtkglextlib isn't installed through apt-get?  just curious

The method you posted is pretty much exactly what happens when you install my pSX .deb, only I install pSX in a global location (/usr/local/games/pSX/), and I include a .desktop file for the Menu. 

The problem other hardy users are experiencing is sound related, pSX is unable to output to ALSA, and without sound pSX refuses to run.

As for why you manually need to install the 32-bit lib of pSX:
pSX is a 32-bit application, and in order to run pSX on a 64-bit OS you need to have all the 32-bit libraries that pSX uses installed. You can see what libraries pSX uses with the ldd command:
```
ldd ./pSX
```

Ubuntu and Debian aren't truly multi-arch; even though the processor and kernel are capable of running 32-bit code in a 64-bit enviroment, it isn't set up right (for example, on 32-bit Ubuntu most 32-bit libraries are installed at /usr/lib/. So 32-bit programs look for them there. In 64-bit, most 64-bit libraries are ALSO installed at /usr/lib/. This causes problems for 32-bit apps looking for 32-bit libraries only to find 64-bit ones instead).

The package ia32-libs (installed by default in Hardy I do believe), tries to solve this problem by installing the most common 32-bit libraries in /usr/lib32/, and updates ldd to search both /usr/lib/ and /usr/lib32. This works for most 32-bit applications, but is not an optimal solution.

The 32-bit libgtkglext1 libraries are not included in ia32-libs, nor are they anywhere to be found in Hardy's 64-bit repositories. Therefore, one most either manually install the libgtkglext1 libraries.

You could use --force-architecture to install the 32-bit package, but then it will install it's libraries into /usr/lib/, which is where all the 64-bit libraries. Worse, it can cause problems for 64-bit applications looking for 64-bit libs in /usr/lib/.

Anyways, hopefully that answers your question :D

---

### Post by master_d on 2008-10-15
wow if that isn't one of the best explanations I've ever seen... thanks dfreer!  I've never had a 64-bit chip until just recently so I'm a little uncertain on how everything works on a 64-bit arch but that makes perfect sense.  I'm still not sure why the compiler cannot compile C source code into 32-bit or 64-bit binaries based on the flags passed to the compiler but that's for another thread :P

about the sound issues people are having.... I'm new to ubuntu myself so perhaps I won't be of much help, but I noticed these problems with dosbox and zsnes immediately after installing hardy over an old gentoo installation.  I did some research and found a webpage that said pulseaudio may be to blame so I uninstalled it and set everything in the sound preferences to ALSA.(under system->preferences->sound)   I also disabled 'Play system sounds' and enabled 'enable software sound mixing (ESD) under the sounds menu of the same gui.  after that I uninstalled pulse-audio with apt-get and ever since then I've had no more sound problems.

edit: just for reference my hardware:
 AMD phenom 9600
 Biostar TA790GX mb
 onboard ALC888 audio
 onboard radeon 3300HD video

---

### Post by dfreer on 2008-10-16
> **master_d said:**
> wow if that isn't one of the best explanations I've ever seen... thanks dfreer!  I've never had a 64-bit chip until just recently so I'm a little uncertain on how everything works on a 64-bit arch but that makes perfect sense.  I'm still not sure why the compiler cannot compile C source code into 32-bit or 64-bit binaries based on the flags passed to the compiler but that's for another thread :P

You should be able to compile 32-bit binaries on a 64-bit OS, although I've had issues trying to do so with ZSNES. I was able to compile ZSNES using a 32-bit chroot, if you don't know what that is, it's basically a fake root partition, in which you can install a 32-bit OS and execute code from it.

> **master_d said:**
> about the sound issues people are having.... I'm new to ubuntu myself so perhaps I won't be of much help, but I noticed these problems with dosbox and zsnes immediately after installing hardy over an old gentoo installation.  I did some research and found a webpage that said pulseaudio may be to blame so I uninstalled it and set everything in the sound preferences to ALSA.(under system->preferences->sound)   I also disabled 'Play system sounds' and enabled 'enable software sound mixing (ESD) under the sounds menu of the same gui.  after that I uninstalled pulse-audio with apt-get and ever since then I've had no more sound problems.

It very well could be an issue with pulseaudio. pSX worked fine for most users (including myself) in every version of Ubuntu since Dapper, but stopped working in Hardy (which is when they introduced pulseaudio). It also works just fine on my Debian Lenny AMD64 install.

---

### Post by mocha on 2008-10-16
Just wanted to point out that you can get pSX to work in Hardy with pulseaudio by temporairly disabiling 2 files.  Rename the 2 files ~/.asoundrc and/or /etc/asound.conf  pSX should work with sound after that.

---

### Post by master_d on 2008-10-16
> You should be able to compile 32-bit binaries on a 64-bit OS, although I've had issues trying to do so with ZSNES. I was able to compile ZSNES using a 32-bit chroot, if you don't know what that is, it's basically a fake root partition, in which you can install a 32-bit OS and execute code from it.

I think zsnes may be a special case because it's partially written in assembly and I don't know if nasm (the assembler) can generate 64-bit instructions.  I guess pSX is a special case too because we don't have the source available.

---

### Post by dfreer on 2008-10-16
> **master_d said:**
> I think zsnes may be a special case because it's partially written in assembly and I don't know if nasm (the assembler) can generate 64-bit instructions.  I guess pSX is a special case too because we don't have the source available.

Note I wasn't talking about compiling a 64-bit binary of ZSNES. In that case you are correct, ZSNES is written in x86 assembly code and therefore it can only be a 32-bit binary (as of now). I was talking about compiling a 32-bit binary on a 64-bit OS, which certainly should be possible.

Hopefully pSX Author will either release a new version, or if he discontinues the project publishes the source code soon. Because it's a great emulator and I'd hate to see it die.

> **mocha said:**
> Just wanted to point out that you can get pSX to work in Hardy with pulseaudio by temporairly disabiling 2 files.  Rename the 2 files ~/.asoundrc and/or /etc/asound.conf  pSX should work with sound after that.

Thanks for this, when I get a chance I'll have to check it out.

---

### Post by BetterSense on 2008-10-29
> Just wanted to point out that you can get pSX to work in Hardy with pulseaudio by temporairly disabiling 2 files. Rename the 2 files ~/.asoundrc and/or /etc/asound.conf pSX should work with sound after that.

That definitely works on my work computer. I'll have to try it on my laptop later. I was pretty disappointed last time I tried to run pSX and it didn't work because of the pulseaudio thing. I can't get epsxe to work and I can't get pcsx to read ISO files (laptop has no CD drive).

---

### Post by mocha on 2008-10-29
Yeah, pulseaudio seems to be a kludge.  It works really nice if you have it setup properly and know how to tweak the .asoundrc file (and when to disable it).  I was trying to get SDLMAME working the other day and was having garbled sound.  Then I found a post where someone had a totally different .asoundrc file for SDL programs, and when I used it the garbled audio went away.  So now, I have 2 .asoundrc files on my system that I need to rename when I want to use them!  Stupid!!

---

### Post by BetterSense on 2008-10-29
I tried the workaround on my laptop with Intrepid and I actually couldn't find any .asoundrc or asound.conf to rename. Lame.

---

### Post by bornagainpenguin on 2008-11-03
> **BetterSense said:**
> I tried the workaround on my laptop with Intrepid and I actually couldn't find any .asoundrc or asound.conf to rename. Lame.

I'm getting errors now too since I installed Intrepid on my EeePC.

```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument' pad=0
```

Since PCSX seems to be under the mistaken idea that *every* computer has an optical drive I'm going to have to give ePSXe a try and hopefully that one will work.  If not I'll have to evaluate whether it would be worth dropping back to Hardy for the benefit of playing PSX games...

--bornagainpenguin

PS: I already did a [search](http://psxemulator.proboards54.com/index.cgi?action=display&board=support&thread=2752&page=1) but the results were inconclusive, because I did a clean install.

---

### Post by xnevermore on 2008-11-03
How about updating this guide for intrepid? I'm having problems with AMD64 (your repositories don't even work).

---

### Post by dfreer on 2008-11-07
I would really appreciate some feedback on this, as I only run Ubuntu Hardy/Intrepid through Live CD's:

**I believe this will solve the problems for most people unable to launch pSX in Ubuntu Hardy/Intrepid**. Try the following packages and see if they work for you in Ubuntu Hardy/Intrepid 32-bit/64-bit. If you don't feel like installing a new package, all I did was add a script to stop pulseaudio, launch pSX, then start pulseaudio once pSX is done running. Rather simple solution that I should have thought of back when Hardy was released, thanks for the help everyone!

Here's the content of the script:
```
#!/bin/bash
# A script to disable pulseaudio, run pSX, then renable pulseaudio

gksu /etc/init.d/pulseaudio stop
sleep 1
gksu killall pulseaudio         # Forcefully ends pulseaudio if still running
sleep 1
exec /usr/local/games/psx/pSX
sleep 1
gksu /etc/init.d/pulseaudio start
```

Will be updating the repository and the front page ASAP, thanks a lot everyone!

---

### Post by dfreer on 2008-11-07
Last package, can only upload 5 at a time :(

---

### Post by emptiness on 2008-11-08
Okay I just tried your packages dfreer...

The emu runs better than pcsx on my macbook 3,1 running intrepid 64 bit.
Audio is glitchy and cutscene video has some probs but overall better performance than pcsx :)

Looking foward to any more improvements...

EDIT: I forgot to add it does not work well with compiz running :(

---

### Post by dfreer on 2008-11-09
> **emptiness said:**
> Okay I just tried your packages dfreer...

The emu runs better than pcsx on my macbook 3,1 running intrepid 64 bit.
Audio is glitchy and cutscene video has some probs but overall better performance than pcsx :)

Looking foward to any more improvements...

EDIT: I forgot to add it does not work well with compiz running :(

The problem I'm attempting to workaround is that pSX will not start up at all, so if it actually runs for you then that is a success. If you wish, you could also add the following to the script to disable/renable compiz:
```

metacity --replace &

compiz --replace &

```

Note that as I merely repackage the official binary, I can't actually improve the emulator itself. Thanks for testing!

EDIT: You could also try increasing the latency in the Audio configuration by a couple ms to see if that helps with the audio "glitchiness". I'd say no more than 10 ms to each slider, but I'm not really an expert.

---

### Post by Luksion Knight on 2008-11-10
hey im running 64-bit interpeid and tried all your packages for amd64 itrepid, but i get a box with this read out > /tmp/lib32gtkglext1_1.2.0-3.2_intrepid-amd64-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

---

### Post by dfreer on 2008-11-10
Sounds like Gdebi or whatever Ubuntu is using now to install packages isn't correctly associated with .deb files in Firefox. Instead of clicking on the download link and "running" the file, try downloading it to your desktop and then install it :D

---

### Post by emptiness on 2008-11-11
Thanks, the latency thing fixed sound for me.Honestly pcsx gave really weird speed and other issues.This is much better.

---

### Post by DancemasterGlenn on 2008-11-16
dfreer, thanks a lot for finding the workaround, pulse was giving me problems with a couple of programs, and your script helped with making them run at normal speed/starting up. I am still having a problem... although this script effectively kills pulse when run, pulse doesn't come back afterwards. Any idea why this could be? If this can be figured out, I'll have a foolproof way to get in and out of pulse as I please, which would be very good indeed. Thanks in advance for any help you can give me!

---

### Post by cshaobu830633 on 2008-11-16
how can i make [runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php) fast??

---

### Post by zero777zero on 2008-11-19
hmmm, still requires me to reboot after using psx to get pulseaudio back

---

### Post by dfreer on 2008-11-19
I'll try to figure out how to properly start/stop pulseaudio, since using the daemon start/stop doesn't always appear to work *sigh*. Right now I just started a new job, pulling a double shift tomorrow so I'll try it out some other time. 

Try just running the command "pulseaudio", see if that works.

---

### Post by mocha on 2008-11-20
I just do a "killall pulseaudio" before running pSX, then "pulseaudio -D" after I'm finished playing with it.

---

### Post by dfreer on 2008-12-02
> **mocha said:**
> I just do a "killall pulseaudio" before running pSX, then "pulseaudio -D" after I'm finished playing with it.

Thanks for that suggestion mocha, if that properly starts pulseaudio again then I can modify the script. 

BTW, if anyone comes up with any better ways to start/stop pulseaudio, preferably ways that doesn't require root permission, feel free to let me know, as I run Debian I don't use pulseaudio at all.

---

### Post by twice on 2009-01-19
Thanks a lot for all your work with this, dfreer.

> **dfreer said:**
> BTW, if anyone comes up with any better ways to start/stop pulseaudio, preferably ways that doesn't require root permission, feel free to let me know, as I run Debian I don't use pulseaudio at all.

The ideal way is to use pasuspender, but it doesn't seem to work for me here.  I get the same error message that I get when running under pulse.

One thing that might help, though, is dropping the 'exec' from the psx32 script.  As I understand it, exec replaces the shell with the process it's running, so nothing under that line gets executed.  Also, appending $@ to the same line would let command line arguments through.

This is my psx32:
```

#!/bin/bash
killall pulseaudio
sleep 1
/usr/local/games/psx32/pSX $@
sleep 1
pulseaudio -D --log-target=syslog
```

---

### Post by riminicat on 2009-01-27
Are there instructions for Ubuntu 8.10 64 bit yet?

---

### Post by dfreer on 2009-01-28
> **riminicat said:**
> Are there instructions for Ubuntu 8.10 64 bit yet?

Yes, there is in this thread, although not quite sure where you might have to do some digging. I can help you further if needed.

---

### Post by water_foul on 2009-02-15
If anyone is still watching this thread I cant get pSX to work :( I have figured out that the problem is
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
but I have the 32 bit libs installed....

---

### Post by marmel on 2009-03-02
> **twice said:**
> 
This is my psx32:
```

#!/bin/bash
killall pulseaudio
sleep 1
/usr/local/games/psx32/pSX $@
sleep 1
pulseaudio -D --log-target=syslog
```

I am using a script like yours since the script by dfreer doesn't restart pulseaudio here on my system (it looks like such solution only works when pulseaudio has been loaded during the system initialisation, not by gnome).
I have also replaced "killall pulseaudio" with "pulseaudio -k" and removed the sleep commands. It's working like a charm here! \\:D/

---

### Post by paintonhisface on 2009-03-26
I am running x86_64 Intrepid on my machine, and have followed your guide but still can't get pSX to run.  Specifically, I've downloaded dfreer's two packages for intrepid-amd64, and installed them.  It didn't work, so I installed and ran getlibs on pSX several times, but getlibs still won't correctly install the last two libraries.  

What getlibs does is match libX11.so.6: captury and libcairo.so.2: libcairo-directfb2, then this ouput:
```

libcairo.so.2: libcairo-directfb2
libX11.so.6: captury
The following i386 packages will be installed:
captury
libcairo-directfb2
Continue [Y/n]? Y
Downloading ...
Installing libraries ...


```

But with pSX I still get a shared libraries issue.  Help

---

### Post by dfreer on 2009-03-26
> **paintonhisface said:**
> I am running x86_64 Intrepid on my machine, and have followed your guide but still can't get pSX to run.  Specifically, I've downloaded dfreer's two packages for intrepid-amd64, and installed them.  It didn't work, so I installed and ran getlibs on pSX several times, but getlibs still won't correctly install the last two libraries.  

What getlibs does is match libX11.so.6: captury and libcairo.so.2: libcairo-directfb2, then this ouput:
```

libcairo.so.2: libcairo-directfb2
libX11.so.6: captury
The following i386 packages will be installed:
captury
libcairo-directfb2
Continue [Y/n]? Y
Downloading ...
Installing libraries ...


```

But with pSX I still get a shared libraries issue.  Help

Can you post your exact error message, and the outputs of this command:
```
ldd /path/to/psx/binary/pSX
```

---

### Post by paintonhisface on 2009-03-27
Error:
```
/usr/local/games/psx32$ ./pSX
./pSX: error while loading shared libraries: libcairo.so.2: cannot open shared object file: No such file or directory
```
ldd:
```
$ ldd ./pSX
	linux-gate.so.1 =>  (0xf7f45000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7ea2000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7e8c000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7dc3000)
	libgtkglext-x11-1.0.so.0 => /usr/lib32/libgtkglext-x11-1.0.so.0 (0xf7dc0000)
	libgdkglext-x11-1.0.so.0 => /usr/lib32/libgdkglext-x11-1.0.so.0 (0xf7d73000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7d02000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7cec000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7c9b000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7c91000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7c79000)
	libpangox-1.0.so.0 => /usr/lib32/libpangox-1.0.so.0 (0xf7c6c000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf7c66000)
	librt.so.1 => /lib32/librt.so.1 (0xf7c5d000)
	libglade-2.0.so.0 => /usr/lib32/libglade-2.0.so.0 (0xf7c46000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf78a7000)
	libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf776b000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf76df000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf76c3000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf76a9000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf769d000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf765a000)
	libcairo.so.2 => not found
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf761c000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7617000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7613000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf755b000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf746c000)
	libm.so.6 => /lib32/libm.so.6 (0xf7446000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7437000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf741e000)
	libc.so.6 => /lib32/libc.so.6 (0xf72c0000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf72b0000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf7283000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7279000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7276000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf726c000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf7264000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf725b000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf7256000)
	/lib/ld-linux.so.2 (0xf7f46000)
	libcairo.so.2 => not found
	libX11.so.6 => not found
	libcairo.so.2 => not found
	libX11.so.6 => not found
	libX11.so.6 => not found
	libX11.so.6 => not found
	libX11.so.6 => not found
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf722c000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf71c4000)
	libcairo.so.2 => not found
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf714e000)
	libX11.so.6 => not found
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf7149000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf7146000)
	libcairo.so.2 => not found
	libcairo.so.2 => not found
	libX11.so.6 => not found
	libcairo.so.2 => not found
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf711b000)
	libX11.so.6 => not found
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7117000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf70f0000)
	libX11.so.6 => not found
	libX11.so.6 => not found
	libX11.so.6 => not found
	libX11.so.6 => not found
	libX11.so.6 => not found
	libX11.so.6 => not found
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf70d5000)
	libX11.so.6 => not found
	libX11.so.6 => not found

```

---

### Post by dfreer on 2009-03-28
> ```

**	libatk-1.0.so.0** => /usr/lib32/libatk-1.0.so.0 (0xf76c3000)
	libcairo.so.2 => not found
	libX11.so.6 => not found

```
You have some sort of borked system. libatk-1.0.so.0 is provided in the ia32-libs package shown here:
[http://packages.ubuntu.com/search?searchon=contents&keywords=libatk-1.0.so.0&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libatk-1.0.so.0&mode=exactfilename&suite=intrepid&arch=any)

And both of the files you are "missing" are **also** provided by ia32-libs:
[http://packages.ubuntu.com/search?searchon=contents&keywords=libcairo.so.2&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libcairo.so.2&mode=exactfilename&suite=intrepid&arch=any)
[http://packages.ubuntu.com/search?searchon=contents&keywords=libX11.so.6&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libX11.so.6&mode=exactfilename&suite=intrepid&arch=any)

It could either be that the files are simply not installed, or that ldd is misconfigured and is looking in the wrong place for them (doubtful considering it finds every other .so file).

---

### Post by zoze on 2009-03-29
I'm trying to run pSX on ubuntu inteprid but i miss 
libgtkglext-x11-1.0.so.0 => not found
how can i install it? i tdid some things but not working .

```
	linux-gate.so.1 =>  (0xf7fab000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7eef000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7ed9000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7e10000)
	libgtkglext-x11-1.0.so.0 => not found
	libgdkglext-x11-1.0.so.0 => not found
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7d9f000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7d89000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7d37000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7d2e000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7d16000)
	libpangox-1.0.so.0 => /usr/lib32/libpangox-1.0.so.0 (0xf7d09000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf7d03000)
	librt.so.1 => /lib32/librt.so.1 (0xf7cfa000)
	libglade-2.0.so.0 => /usr/lib32/libglade-2.0.so.0 (0xf7ce2000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf7944000)
	libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf7808000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf777c000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf7760000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf7745000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf773a000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf76f7000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf7684000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7646000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7641000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf763c000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7585000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7496000)
	libm.so.6 => /lib32/libm.so.6 (0xf7470000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7461000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7448000)
	libc.so.6 => /lib32/libc.so.6 (0xf72e9000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf6572000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6570000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6561000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6472000)
	/lib/ld-linux.so.2 (0xf7fac000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf6449000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf63e1000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf636b000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf633e000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf633a000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf6336000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6331000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6327000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6324000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf631a000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6312000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf6309000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf62c7000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf62a1000)
	libxcb-render-util.so.0 => /usr/lib32/libxcb-render-util.so.0 (0xf629c000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf6293000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf627a000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf6250000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf624d000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf624a000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf622f000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf6208000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6203000)

```

---

### Post by dfreer on 2009-03-29
> **zoze said:**
> I'm trying to run pSX on ubuntu inteprid but i miss 
libgtkglext-x11-1.0.so.0 => not found
how can i install it? i tdid some things but not working .


Grab a 32-bit libgtkglext library. I've created several packages of this library and you can download them from attachments within this very thread.

---

### Post by zoze on 2009-03-31
i cannot connect to your server time out the messages i get.

---

### Post by dfreer on 2009-03-31
> **zoze said:**
> i cannot connect to your server time out the messages i get.

> **dfreer said:**
> ...you can download them from attachments within this very thread.

Server is currently down; the packages are attached within this thread. You can also use getlibs to obtain the files you need.

---

### Post by jedinerd on 2009-04-10
When i try and run pSX it crashes out with this error

The program 'pSX' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadDrawable'.
  (Details: serial 1053 error_code 173 request_code 155 minor_code 11)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf602f7c7]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf602f96e]
#2 /usr/lib32/libX11.so.6 [0xf6298619]
#3 /usr/lib32/libX11.so.6(XESetCloseDisplay+0x44) [0xf627a294]
#4 /usr/lib32/libGL.so.1 [0xf7f29049]

What have i done wrong?

---

### Post by dfreer on 2009-04-10
Looks like a new error to me, perhaps something unique to the version of Ubuntu you are running?

In any case, pSX will segfault if pulseaudio is running, but I don't think this is the same error. Wouldn't hurt to try; make sure to kill pulseaudio then try running pSX again.

---

### Post by afrodeity on 2009-04-25
I have lib32gtkglext1_1.2.0-3.1_hardy-amd64.deb installed and have downloaded pSX_linux_1_13.tar.bz2

afrodeity@afrodeity-desktop:/media/Gaia/Downloads/PSX/pSX$ ./pSX
./pSX: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

what must I do?

---

### Post by gerowen on 2009-05-01
I'm trying to do this on 9.04 Jaunty 64 bit, and when trying to import the key for dfreer.org I can't reach it.  When I try to ping dfreer.org I get "unknown host".

---

### Post by sultanoswing on 2009-05-01
Followed the guides, installed the 2 .deb files (on Jaunty 64-bit) - the psx32 deb and the lib32gtkglext deb.

Program loads and runs, but only as root.

Running as regular user, I get:

```

 * PulseAudio configured for per-user sessions
pulseaudio: no process killedGtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
mcm@taniwha-laptop:~/Desktop$ psx32
 * PulseAudio configured for per-user sessions
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

Any thoughts on how to resolve this obvious permissions issue, so it'll run as a regular user??

Thanks for the packages and assistance to date, dfreer!

---

### Post by Sarteck on 2009-05-02
I have a DualShock 2 (SCPH-10010) controller that I've been using for pSX.  Unfortunately, pSX only has options for SCPH-1010, 1150, and 1200.  This might be why I must choose between using EITHER the joysticks OR the directional pad, but cannot use both at the same time.

Has anyone else encountered this problem when using a DualShock2 controller for pSX?

I am running on a 64-bit system, if that matters.

---

### Post by epsilon72 on 2009-05-06
> **sultanoswing said:**
> Followed the guides, installed the 2 .deb files (on Jaunty 64-bit) - the psx32 deb and the lib32gtkglext deb.

Program loads and runs, but only as root.

Running as regular user, I get:

```

 * PulseAudio configured for per-user sessions
pulseaudio: no process killedGtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
mcm@taniwha-laptop:~/Desktop$ psx32
 * PulseAudio configured for per-user sessions
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

Any thoughts on how to resolve this obvious permissions issue, so it'll run as a regular user??

Thanks for the packages and assistance to date, dfreer!
I get segfaults as well, but I'm on Debian squeeze.
Interestingly enough though, if I borrow my gentoo-compiled zsnes binary, it loads just fine, but the sound quality is very poor because it doesn't use libao (and it can't, because gentoo doesn't have a 32-bit libao compatibility package)

---

### Post by afrodeity on 2009-05-08
```
afrodeity@afrodeity-desktop:~$ sudo apt-get install psx32frontend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package psx32frontend
afrodeity@afrodeity-desktop:~$ 
```

Do you mean psxfrontend?

I have Ubuntu 64 Hardy

---

### Post by TrueLugia121 on 2009-05-09
i'm sorry but the link to your pre-made DEB files ins dead. can you repost these please?

---

### Post by dfreer on 2009-05-10
> **afrodeity said:**
> I have lib32gtkglext1_1.2.0-3.1_hardy-amd64.deb installed and have downloaded pSX_linux_1_13.tar.bz2

afrodeity@afrodeity-desktop:/media/Gaia/Downloads/PSX/pSX$ ./pSX
./pSX: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

what must I do?

Make sure ia32-libs is installed? That lib should be included in that package, otherwise I always get it installed when I install my nvidia drivers. Possibly your video card drivers are not correctly installed?

> **marcusdean.adams said:**
> I'm trying to do this on 9.04 Jaunty 64 bit, and when trying to import the key for dfreer.org I can't reach it.  When I try to ping dfreer.org I get "unknown host".

My repository is currently down and it is highly unlikely it will be resurrected before it becomes forgotten/obsolete. I uploaded the packages to this forum several pages ago.

> **sultanoswing said:**
> 
```
$ psx32
 * PulseAudio configured for per-user sessions
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

Any thoughts on how to resolve this obvious permissions issue, so it'll run as a regular user??

Thanks for the packages and assistance to date, dfreer!

Haven't gotten around to playing with Ubuntu 9.04; some new stuff here I haven't seen. The old solution was that pulseaudio needed to be killed before pSX would run, as the two seemed to conflict. Have you tried that yet?

That's about the only advice I can currently offer: if it runs correctly as root, I'd hazard a guess that 9.04 will disable pulseaudio if it detects an conflict, but only root has permission to do so? Another option (not the greatest) would be to create a script/launcher that executes pSX as root, then modify your sudoers file so that it can do so without needing authentication.

> **Sarteck said:**
> I have a DualShock 2 (SCPH-10010) controller that I've been using for pSX.  Unfortunately, pSX only has options for SCPH-1010, 1150, and 1200.  This might be why I must choose between using EITHER the joysticks OR the directional pad, but cannot use both at the same time.

Has anyone else encountered this problem when using a DualShock2 controller for pSX?

Well the original hardware wouldn't allow you to use a PS2 controller on the original Playstation IIRC, not that it matters when emulating. Can't help much, other than to recommend my all time favorite logitech dual actions.

> **epsilon72 said:**
> I get segfaults as well, but I'm on Debian squeeze.
Interestingly enough though, if I borrow my gentoo-compiled zsnes binary, it loads just fine, but the sound quality is very poor because it doesn't use libao (and it can't, because gentoo doesn't have a 32-bit libao compatibility package)

I'm guessing you got your threads confused :D Check out my response in the pSX thread, and if you would like I could probably help you with getting 32-bit libao libs installed on your gentoo system (might be tricky IIRC gentoo doesn't have **any** precompiled libs? so we would have to cross compile or use non-gentoo binaries).

If Getlibs is available for gentoo that would probably be easiest.

> **afrodeity said:**
> ```
afrodeity@afrodeity-desktop:~$ sudo apt-get install psx32frontend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package psx32frontend
afrodeity@afrodeity-desktop:~$ 
```

Do you mean psxfrontend?

I have Ubuntu 64 Hardy

Not entirely sure what *you* mean, as far as I know, I'm the only one that packaged Ultima's pSX Frontend, and you cannot apt-get the package since my repository is done. It's really easy to install it manually by checking the pSX Official Forums, or just look further down in my post.

> **TrueLugia121 said:**
> i'm sorry but the link to your pre-made DEB files ins dead. can you repost these please?

I'm assuming you are talking about my repository links? I have already reposted them here in these forums, hopefully these aren't dead as well:
[http://ubuntuforums.org/showpost.php?p=4340576&postcount=182](http://ubuntuforums.org/showpost.php?p=4340576&postcount=182)
[http://ubuntuforums.org/showpost.php?p=4346682&postcount=186](http://ubuntuforums.org/showpost.php?p=4346682&postcount=186)
[http://ubuntuforums.org/showpost.php?p=4902438&postcount=206](http://ubuntuforums.org/showpost.php?p=4902438&postcount=206)
[http://ubuntuforums.org/showpost.php?p=6127662&postcount=246](http://ubuntuforums.org/showpost.php?p=6127662&postcount=246)
[http://ubuntuforums.org/showpost.php?p=6127662&postcount=247](http://ubuntuforums.org/showpost.php?p=6127662&postcount=247)

I believe those are all the packages I uploaded, I have a backup of pretty much every .deb I've created if these don't work for you, just let me know.

---

### Post by sultanoswing on 2009-05-16
Thanks dfreer. This solution from another thread solved the permissions problem, and I can now launch as a regular user (thanks to Grishka):

```

1. kill pulseaudio (sudo killall pulseaudio)
2. run pSX as root (sudo ./pSX)
3. find the "sound" tab in the configuration and switch the "device" setting from "default" to your soundcard (plughw:0,0 in my case). apply. close pSX.
4 open /root/.pSX/psx.ini in a text editor (gksudo gedit /root/.pSX/psx.ini). find the "device" string under [Sound] section (I have "b7d317a4" there).
5. paste this string into the relevant section in ~/.pSX/psx.ini, in place of all zeroes. save. if you don't have this file in your user directory, run pSX and cancel just after choosing language, on the bios selection screen. pSX should save settings then.

now pSX runs fine even after reboot.

```

This answer also solved my 'error while loading shared libraries: libGL.so.1' problem:

```

Try this only after verifying that you do in fact have the identified files in the stated locations.
sudo unlink /usr/lib/libGL.so.1
sudo unlink /usr/lib32/libGL.so.1
sudo rm /usr/lib/libGL.so.1.2
sudo synaptic

From there I reinstalled IA32 libraries using synaptic.

```

---

### Post by afrodeity on 2009-05-18
Thank you for the new links, I installed psx32frontend_1.11-3.1_gutsy-amd64 and it's now working :)

---

### Post by bikodog on 2009-05-23
Thanks for the great work dfreer. It took some work (not bad for a saturday afternoon) but pSX is working great now.

Here's a question...does anyone know of a way to copy "my precious" saves off of psx memory cards to USB on the PS2?

I would love to access my saves.

---

### Post by gerowen on 2009-05-24
PSX is working great for me too, but only as root.  I followed the directions in the earlier post about copying the sound device info into ~HOME/.pSX/psx.ini, but that didn't work.  Whenever I try to run it as a normal user I get the following:
```

 * PulseAudio configured for per-user sessions
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Device or resource busy'
pSX: ../../../src/pcm/pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

```

---

### Post by jordan420 on 2009-05-28
First of all i would like to say that this truly is the best emulator out their for linux that i've tried. at least for my system. the video is sooo much smoother and it uses literally half the resources. props to the author and dfreer for the packages. I was however posting for another reason than to extend my thanks... i get horrible sound. when i run from the command line i get "sound: underrun" repeating. any suggestions?

---

### Post by dfreer on 2009-05-28
You can try increasing the sound latency within pSX by 10 MS or so, I wouldn't recommend increasing it by any more than that. Beyond that, I don't have any suggestions, sorry :(

---

### Post by jordan420 on 2009-05-28
yeah... I've tried that. and a few other tweaks involving sound and graphics. i got the biggest difference by turning the display off of 32 bit. but still pretty choppy. if anyone else might know anything i would be grateful. BTW thanks dfreer for the quick reply.

---

### Post by ezekiel000 on 2009-05-29
Try increasing the nice setting, when I had my old pc I used to set the nice setting higher than usual to fix the sound choppiness.
You can do this through the system monitor or using the command:
"nice -n -12 psx" or "nice -n -12 psx32"
I only ever used to change it through the priority setting in system monitor, but recently I have been running Myst with wine and was recomended to run it with "nice -n #" in front so I guess it should work here too.

---

### Post by Jordan777 on 2009-06-03
I've tried to install pSX but when I run it all i get is this ./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

I can't seem to fix the problem.  I'm using Jaunty 64 bit.

---

### Post by BwackNinja on 2009-06-03
> **marcusdean.adams said:**
> PSX is working great for me too, but only as root.  I followed the directions in the earlier post about copying the sound device info into ~HOME/.pSX/psx.ini, but that didn't work.  Whenever I try to run it as a normal user I get the following:
```

 * PulseAudio configured for per-user sessions
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Device or resource busy'
pSX: ../../../src/pcm/pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

```
Try using pasuspender. Pulseaudio is taking up the sound card and it works with root because root has higher preference with the sound card than pulseaudio which is run by your user.

---

### Post by BwackNinja on 2009-06-03
> **Jordan777 said:**
> I've tried to install pSX but when I run it all i get is this ./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

I can't seem to fix the problem.  I'm using Jaunty 64 bit.

Previous in the thread, this should help explain for you:
[http://ubuntuforums.org/showpost.php?p=2543861&postcount=19](http://ubuntuforums.org/showpost.php?p=2543861&postcount=19)

---

### Post by mikeym on 2009-06-12
Just wondering of there's any way of installing this on Jaunty? (AMD64 with 64 bit Ubuntu in this case.)

It would seem a shame to see this die.

---

### Post by ezekiel000 on 2009-06-12
I have installed pSX on 9.04 (Jaunty) 64bit but it seems to crash out with this:
ezekiel@alice:~/Desktop$ psx32
 * PulseAudio configured for per-user sessions
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault

I hope that this can be fixed maybe in version 1.14 that's meant to be released soon... sometime in the next few years =)

---

### Post by mikeym on 2009-06-12
> **ezekiel000 said:**
> 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault

I hope that this can be fixed maybe in version 1.14 that's meant to be released soon... sometime in the next few years =)

This error is to do with a clash with pulse audio. See the first bit of [this post]("http://ubuntuforums.org/showpost.php?p=7289090&postcount=281") to see how to fix it.

I gave up trying to install the debs on this thread as none seemed to be available / compatible with Jaunty 64 bit. However installing yourself is easy as it's mostly just a case of downloading and running. The files can be downloaded from [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/) and [http://psxemulator.proboards.com/index.cgi?board=news&action=display&thread=1080](http://psxemulator.proboards.com/index.cgi?board=news&action=display&thread=1080).

You can use *getlibs* on hte psx executable to find any missing 32 bit dependencies.

However I found that the Audio was buggy (with sound underruns) even when I'd got it running and messed about with the settings.

I've switched to ePSXe which seems to be running better.

---

### Post by jw5801 on 2009-06-12
> **jamiyoel said:**
> i want to install Bleem for Playstation. Can I install it same as current instructions?

No... and I can't see why you would want to? Bleem is a long long dead emulator.

Aside from that, it was released for Windows and then later to run on the Sega Dreamcast. There was never a Linux release, so no you can't run it on Linux using the same method as for pSX. You could try running it under wine, but it would be hit and miss and I honestly have no idea why you would bother.

---

### Post by ahndoruuu on 2009-07-24
I'm getting this error, I've installed pSX and the libgtkglext libraries:

```
andrew@4XKB91:~/pSX$ ./pSX
get fences failed: -1
param: 6, val: 0
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

---

### Post by skaldicpoet9 on 2009-08-12
> **BwackNinja said:**
> Previous in the thread, this should help explain for you:
[http://ubuntuforums.org/showpost.php?p=2543861&postcount=19](http://ubuntuforums.org/showpost.php?p=2543861&postcount=19)

I am having this same problem but I am not quite sure how the post you linked to solves the problem. I downloaded pSX from the website (v 1.13) and got the same error message. However, the post that you link to assumes that pSX was installed through some other method (all I did was unzip mine into /home/user/Documents). I have read through this thread and it seems like some of the info might be outdated...

Does anyone know how to get this up and running using Jaunty and pSX 1.13? I would really love to be able to play me some PSX on Ubuntu.

---

### Post by Cygoku on 2009-09-15
> **skaldicpoet9 said:**
> I am having this same problem but I am not quite sure how the post you linked to solves the problem. I downloaded pSX from the website (v 1.13) and got the same error message. However, the post that you link to assumes that pSX was installed through some other method (all I did was unzip mine into /home/user/Documents). I have read through this thread and it seems like some of the info might be outdated...

Does anyone know how to get this up and running using Jaunty and pSX 1.13? I would really love to be able to play me some PSX on Ubuntu.I have the same segmentation fault, please help us under Jaunty.  

Cygoku

---

### Post by ezekiel000 on 2009-09-15
I got pSX working in Jaunty by first running pSX as admin then opening the settings and set the sound device to my sound card (not default). Once that's done I closed pSX and copied the contents /root/.pSX/psx.ini to /home/username/.pSX/psx.ini and then run pSX with this: /usr/local/games/psx32/pSX.

---

### Post by amor0fati on 2009-09-17
I got pSX32 working nearly perfectly on Jaunty simply by installing from the .deb's posted for intrepid in this thread, apart from a good deal of flickering making it almost unplayable.  Vsync didn't fix this, either.  I can't seem to find much info about this apart from the fact that others sometimes have this problem too.

Also, I can't seem to find how to get it in full-screen (I was hoping that might remedy the flickering as a temporary solution).  I can configure the resolution for full screen but can't see an option to actually use it.

---

### Post by amor0fati on 2009-09-17
I tried uninstalling everything (as per this thread) and reinstalling again with the .deb for intrepid amd64.  I've already removed pulseaudio.

```
~$ cd /usr/local/games/psx32/
/usr/local/games/psx32$ ./pSX
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
sound: underrun
sound: underrun
sound: underrun

```

```
/usr/local/games/psx32$ sudo ./pSX
sound: underrun
sound: underrun
sound: underrun

```

Neither running it normally or with sudo fixed the flickering, otherwise both work fine.  Vsync seems to be the only thing that reduces the flickering, but not by much.

---

### Post by bikodog on 2009-10-06
> **amor0fati said:**
> I got pSX32 working nearly perfectly on Jaunty simply by installing from the .deb's posted for intrepid in this thread, apart from a good deal of flickering making it almost unplayable.  Vsync didn't fix this, either.  I can't seem to find much info about this apart from the fact that others sometimes have this problem too.

Also, I can't seem to find how to get it in full-screen (I was hoping that might remedy the flickering as a temporary solution).  I can configure the resolution for full screen but can't see an option to actually use it.

OK..so I have been tinkering with this and am having the same flickering problem.

I had psx32 working perfect in Intrepid. I did a dpkg-repack of my installation, as I wanted to reconfig my partitions before installing Jaunty. I reformatted and partitioned my drives and did a fresh install of JJ. Using the .deb file that was packed for my configuration, I am now getting this annoying flicker. Once again...i have absolutely no hardware changes. This makes me think that the problem lies in Jaunty itself.

So a little more experimentation and I have found this interesting phenomena. When pSX is the active window the screen flickers. If another window is brought to front, the graphics bleed through perfect.

I'm not sure where to go from here. Any direction would be welcome.

---

### Post by Cygoku on 2009-10-19
> **dfreer said:**
> I would really appreciate some feedback on this, as I only run Ubuntu Hardy/Intrepid through Live CD's:

**I believe this will solve the problems for most people unable to launch pSX in Ubuntu Hardy/Intrepid**. Try the following packages and see if they work for you in Ubuntu Hardy/Intrepid 32-bit/64-bit. If you don't feel like installing a new package, all I did was add a script to stop pulseaudio, launch pSX, then start pulseaudio once pSX is done running. Rather simple solution that I should have thought of back when Hardy was released, thanks for the help everyone!

Here's the content of the script:
```
#!/bin/bash
# A script to disable pulseaudio, run pSX, then renable pulseaudio

gksu /etc/init.d/pulseaudio stop
sleep 1
gksu killall pulseaudio         # Forcefully ends pulseaudio if still running
sleep 1
exec /usr/local/games/psx/pSX
sleep 1
gksu /etc/init.d/pulseaudio start
```

Will be updating the repository and the front page ASAP, thanks a lot everyone!Help, this still segfault in both jaunty and karmic !! 

HELP !! :P

Cygoku

---

### Post by italomaia on 2009-10-31
Getting this error all the time in my AMD64 Xubuntu Karmic :

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

---

### Post by octesian on 2009-12-12
Still segfaulting.

---

### Post by xxGrenxx on 2010-02-12
i keep getting a file not found error installing psx and i just want to get ff7 working on a ps1 emulator is there one that will work with open gl that is easier to install or is there someone who can help me cause ive gone through this whole thread n cant seem to make it happen plz help:confused:

---

### Post by eaterjolly on 2010-04-10
sorry im getting a headache reading this thread just sumurize in one post what do i do to compile this stupid file

---

### Post by natking24 on 2010-04-30
> **octesian said:**
> Still segfaulting.

I too was segfaulting, however I jumped from segmentation faults to 'resource busy' to pulseaudio issues. I removed pulseaidio, which caused nothing but seg faults. 

What actually made psx work besides removing pulseaudio was downgrading ia32-libs. I remembered initially that karmic had trouble with psx because of ia32-libs, same with lucid. 
Once I downgraded to ia32-libs_2.7ubuntu6.1_amd64.deb and removed pulseaudio, psx finally worked.

My issue now is how lousy the sound is from psx (with a lot of sound: underrun). Could be esound, could be the acceleration of the graphic drivers, could be anything.

---

### Post by ifraser on 2010-05-06
To all 64-bit users bashing their brains in trying to get PSX emulation to work - the thread's OP told me his methods won't work in newer versions of Ubuntu.  My solution is to go get "PCSX Reloaded", which is designed for 64-bit and is based on PCSX itself.  Worked immediately for me and runs perfect with very little tinkering necessary (though you can do so if you wish and it's all GUI-based).

---

### Post by gerowen on 2010-05-06
**Edit:** I got PCSX-R working, but so far I have yet to get a game working perfectly, even trying to use both the built in BIOS and the actual PSX bios.  Final Fantasy tactics stops receiving commands from my controller when the first battle starts.  I'm able to navigate the menus, close speech bubbles and everything, but as soon as the battle actually starts I'm stuck like chuck.  Metal Gear Solid disc 1 won't go past the opening logo unless I turn off the frame limiter, and then it runs stupidly fast.  Crash Bandicoot Warped has my guy constantly running to one side for some reason, even though I "know" the controller is configured properly.  I'm going to try and get PSX working on my 64 bit system.

---

### Post by krymz on 2011-08-30
Hi, I'm trying to find an alternative to PCSX, so far I'm getting a bit of problem with it, I.E. in shadow madness I can't get out of town (get a eternal black screen) and in legend of legaia it keeps ******* up (as in game stops and has to be restarted) when I try to do the -> -> <- special combo....

can't figure out how to install these programs though (pSX and ePSXe)... I tried the comands in the first post and got this...

```
 krymz@FreedomStation1 ~/ePSXe_install $ sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk
[sudo] password for krymz: 
Sorry, try again.
[sudo] password for krymz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs
E: Unable to locate package ia32-libs-sdl
E: Unable to locate package ia32-libs-gtk
krymz@FreedomStation1 ~/ePSXe_install $ sudo dpkg -p psx # 32-bit users only
Package `psx' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
krymz@FreedomStation1 ~/ePSXe_install $ sudo dpkg -p psx # 32-bit users only
Package `psx' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
krymz@FreedomStation1 ~/ePSXe_install $ sudo dpkg -p psx32 # 64-bit users only
Package `psx32' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
krymz@FreedomStation1 ~/ePSXe_install $ sudo rm -Rv /usr/local/games/psx/ # 32-bit users only
rm: cannot remove `/usr/local/games/psx/': No such file or directory
krymz@FreedomStation1 ~/ePSXe_install $ sudo rm -Rv /usr/local/games/psx32/ # 64-bit users only
rm: cannot remove `/usr/local/games/psx32/': No such file or directory
krymz@FreedomStation1 ~/ePSXe_install $ sudo apt-get clean
krymz@FreedomStation1 ~/ePSXe_install $ sudo apt-get update
Ign file: binary/ InRelease
Ign file: binary/ Release.gpg                                                  
Ign file: binary/ Release                                                      
Ign file: binary/ Translation-en_CA                                            
Ign file: binary/ Translation-en                                               
Ign http://packages.dfreer.org gutsy InRelease                                 
Err http://packages.dfreer.org gutsy Release.gpg                               
  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Ign http://packages.linuxmint.com katya InRelease                              
Ign http://packages.dfreer.org gutsy Release                                   
Ign http://packages.dfreer.org gutsy/main TranslationIndex                     
Get:1 http://packages.linuxmint.com katya Release.gpg [198 B]                  
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                          
Get:2 http://packages.linuxmint.com katya Release [16.5 kB]                    
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://security.ubuntu.com natty-security Release.gpg                      
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://extras.ubuntu.com natty Release.gpg                                 
Get:3 http://packages.linuxmint.com katya/main i386 Packages [8,538 B]         
Hit http://security.ubuntu.com natty-security Release                          
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Hit http://archive.ubuntu.com natty Release.gpg                                
Get:4 http://packages.linuxmint.com katya/upstream i386 Packages [16.0 kB]     
Hit http://archive.ubuntu.com natty-updates Release.gpg                        
Hit http://extras.ubuntu.com natty Release                                     
Get:5 http://packages.linuxmint.com katya/import i386 Packages [5,910 B]       
Ign http://packages.linuxmint.com katya/import TranslationIndex                
Ign http://packages.linuxmint.com katya/main TranslationIndex                  
Ign http://packages.linuxmint.com katya/upstream TranslationIndex              
Hit http://archive.ubuntu.com natty Release                                    
Ign http://archive.getdeb.net natty-getdeb InRelease                           
Hit http://archive.ubuntu.com natty-updates Release                            
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.ubuntu.com natty/main i386 Packages                         
Hit http://archive.ubuntu.com natty/restricted i386 Packages                   
Hit http://archive.ubuntu.com natty/universe i386 Packages                     
Hit http://archive.ubuntu.com natty/multiverse i386 Packages                   
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Hit http://archive.ubuntu.com natty-updates/main i386 Packages                 
Hit http://archive.ubuntu.com natty-updates/restricted i386 Packages           
Hit http://archive.ubuntu.com natty-updates/universe i386 Packages             
Hit http://archive.ubuntu.com natty-updates/multiverse i386 Packages           
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://packages.linuxmint.com katya/import Translation-en_CA               
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty/main Translation-en_CA                     
Hit http://archive.ubuntu.com natty/restricted Translation-en_CA               
Err http://packages.dfreer.org gutsy/main i386 Packages                        
  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Err http://packages.dfreer.org gutsy/main Translation-en_CA                    
  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Err http://packages.dfreer.org gutsy/main Translation-en                       
  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://extras.ubuntu.com natty/main Translation-en_CA                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.ubuntu.com natty/main Translation-en                        
Ign http://archive.ubuntu.com natty/multiverse Translation-en_CA               
Ign http://archive.ubuntu.com natty/multiverse Translation-en                  
Ign http://archive.ubuntu.com natty/restricted Translation-en                  
Ign http://archive.ubuntu.com natty/universe Translation-en_CA                 
Ign http://archive.ubuntu.com natty/universe Translation-en                    
Ign http://archive.ubuntu.com natty-updates/main Translation-en_CA             
Ign http://archive.ubuntu.com natty-updates/main Translation-en                
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_CA       
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en          
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_CA       
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en          
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_CA         
Ign http://archive.ubuntu.com natty-updates/universe Translation-en            
Hit http://archive.getdeb.net natty-getdeb Release.gpg                         
Ign http://packages.linuxmint.com katya/import Translation-en                  
Ign http://packages.linuxmint.com katya/main Translation-en_CA                 
Ign http://packages.linuxmint.com katya/main Translation-en                    
Ign http://packages.linuxmint.com katya/upstream Translation-en_CA             
Ign http://packages.linuxmint.com katya/upstream Translation-en                
Hit http://archive.getdeb.net natty-getdeb Release                             
Hit http://archive.getdeb.net natty-getdeb/games i386 Packages                 
Ign http://security.ubuntu.com natty-security/main Translation-en_CA           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_CA     
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_CA     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Ign http://security.ubuntu.com natty-security/universe Translation-en_CA       
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://archive.getdeb.net natty-getdeb/games TranslationIndex              
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://archive.canonical.com natty Release                                 
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://archive.canonical.com natty/partner Translation-en_CA               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://packages.medibuntu.org natty/free Translation-en_CA                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_CA             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Ign http://archive.getdeb.net natty-getdeb/games Translation-en_CA             
Ign http://archive.getdeb.net natty-getdeb/games Translation-en
Fetched 47.1 kB in 3min 39s (215 B/s)
W: Failed to fetch http://packages.dfreer.org/dists/gutsy/Release.gpg  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en_CA  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.dfreer.org/dists/gutsy/main/i18n/Translation-en  Something wicked happened resolving 'packages.dfreer.org:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
krymz@FreedomStation1 ~/ePSXe_install $ sudo apt-get install psx # 32-bit users only
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package psx
krymz@FreedomStation1 ~/ePSXe_install $ sudo apt-get install psx32 # 64-bit users onlyReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package psx32

 
```help?!:(:P

---

### Post by dfreer on 2011-08-30
You have a bunch of things wrong here.
(1). You have my packages.dfreer.org in your repository list, which has been shutdown for 2-3 years now. You should remove those entries from your list of software repositories.

(2). You are running commands from my how-to, which is rather old itself. If you want to try using my manual install guide (which is for **64-bit users only**, you can try the instructions found here, at the bottom of my first post, the part that says *(OLD) AMD64 Manual How to Install*:
[http://ubuntuforums.org/showpost.php?p=2357284&postcount=1](http://ubuntuforums.org/showpost.php?p=2357284&postcount=1)

(3) Finally, I get the impression you are running a 32-bit install of ubuntu (you can determine this with a *uname -a* command. In which case you should try downloading pSX straight from the pSX website and install it that way instead of any of the above.

---

### Post by daemonicon on 2012-01-29
Hey.

First of all, sorry for my bad english. not my native language. ^^

i'm using ubuntu 11.10

 so, i followed the instructions in the first post for amd64 users.
everything works allright but when i try to start pSX the old error message appears..

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: wrong ELF class: ELFCLASS64

any idea?

---

### Post by dfreer on 2012-01-29
Please enter the following two commands into a terminal/console window, and post the output of the two commands here:
```
uname -a
```
```
ldd ./pSX
```

My first guess is that you need the 32-bit libgtkglext library installed. Unfortunately this requires manual installation. This is how to install it:
```
cd ~/
wget -c http://mirror.anl.gov/pub/ubuntu//pool/universe/g/gtkglext/libgtkglext1_1.2.0-1.2fakesync1_i386.deb
sudo dpkg -x libgtkglext1_1.2.0-1.2fakesync1_i386.deb libgtkglext
sudo mv -v libgtkglext/usr/lib/* /usr/lib32/

```

---

### Post by daemonicon on 2012-01-29
> kojak@kreissaege:~$ uname -a
Linux kreissaege 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

> kojak@kreissaege:~/pSX$ ldd ./pSX
    linux-gate.so.1 =>  (0xf778f000)
    libGL.so.1 => /usr/lib32/fglrx/libGL.so.1 (0xf7681000)
    libz.so.1 => /usr/lib32/libz.so.1 (0xf766c000)
    libasound.so.2 => /usr/lib32/libasound.so.2 (0xf757a000)
    libgtkglext-x11-1.0.so.0 => not found
    libgdkglext-x11-1.0.so.0 => not found
    libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7508000)
    libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf74ef000)
    libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7492000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7489000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf746f000)
    libpangox-1.0.so.0 => /usr/lib32/libpangox-1.0.so.0 (0xf7462000)
    libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf745c000)
    libglade-2.0.so.0 => not found
    libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf6ff2000)
    libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf6ea5000)
    libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf6df7000)
    libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf6dd7000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf6db7000)
    libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf6da9000)
    libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf6d60000)
    libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf6c95000)
    libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf6c46000)
    libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf6c41000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf6c3b000)
    libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf6b42000)
    libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf6a57000)
    libm.so.6 => /lib32/libm.so.6 (0xf6a2d000)
    libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf6a0f000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf69f4000)
    libc.so.6 => /lib32/libc.so.6 (0xf6879000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6866000)
    librt.so.1 => /lib32/librt.so.1 (0xf685d000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6727000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf6721000)
    libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf671a000)
    libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf65d4000)
    libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf65a7000)
    libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6572000)
    libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6567000)
    libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6562000)
    libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6552000)
    libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6549000)
    libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf653e000)
    libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf653a000)
    libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf6535000)
    libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf649e000)
    libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf641b000)
    libpng12.so.0 => /lib32/libpng12.so.0 (0xf63f1000)
    libxcb-shm.so.0 => /usr/lib32/libxcb-shm.so.0 (0xf63ed000)
    libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf63e2000)
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf63c3000)
    libffi.so.6 => /usr/lib32/libffi.so.6 (0xf63bc000)
    /lib/ld-linux.so.2 (0xf7790000)
    libpcre.so.3 => /lib32/libpcre.so.3 (0xf637d000)
    libselinux.so.1 => /lib32/libselinux.so.1 (0xf635f000)
    libresolv.so.2 => /lib32/libresolv.so.2 (0xf6347000)
    libexpat.so.1 => /lib32/libexpat.so.1 (0xf631d000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6319000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6312000)
i installed it manually, like you described but it still shows
> 
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: wrong ELF class: ELFCLASS64

---

### Post by dfreer on 2012-01-30
According to ldd, it looks like this libgtkglext library is the only one you are missing. I think the issue is that I failed to have you run ldconfig after installing the libraries manually. Still, let's check and make sure that the files were installed.

Verify that the files have been installed in the right location:
```
ls -l /usr/lib32/ | grep libgtkglext
```

And also make sure that the newly installed libraries are visible to the dynamic linker:
```
ldconfig -v
```

And then try running pSX again.

---

### Post by daemonicon on 2012-01-30
thank you. :)


buuut... wooohoo, a new error appears :

./pSX: error while loading shared libraries: libglade-2.0.so.0: cannot open shared object file: No such file or directory


:/

---

### Post by daemonicon on 2012-02-01
sorry for double post... but,

no idea anyone? :(

---

### Post by dfreer on 2012-02-02
```
cd ~/
wget -c http://mirror.anl.gov/pub/ubuntu//pool/main/libg/libglade2/libglade2-0_2.6.4-1build1_i386.deb
sudo dpkg -x libglade2-0_2.6.4-1build1_i386.deb libglade2
sudo mv -v libglade2/usr/lib/* /usr/lib32/
sudo ldconfig
```

You might want to check out [http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/)
I don't have the time to explain it in detail now, but you can search for libraries you are missing (like libglade-2.0.so.0) and find the 32-bit package you need to install. From there, it's a matter of opening the package and manually installing the 32-bit libraries.

---

### Post by memzak on 2012-02-12
Lol, First post. Well needed though.

I've done a couple things from this thread to try and get my pSX working. Here's the current situation. (Error code at the top, uname -a next and then ldd)

```
NONEEDTOKNOW@NONEEDTOKNOW:/opt/pSX$ ./pSX 
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: wrong ELF class: ELFCLASS64
NONEEDTOKNOW@NONEEDTOKNOW:/opt/pSX$ uname -a
Linux NONEEDTOKNOW 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
NONEEDTOKNOW@NONEEDTOKNOW/opt/pSX$ ldd ./pSX 
    linux-gate.so.1 =>  (0xf77ae000)
    libGL.so.1 => /usr/lib32/fglrx/libGL.so.1 (0xf76a2000)
    libz.so.1 => /usr/lib32/libz.so.1 (0xf768d000)
    libasound.so.2 => /usr/lib32/libasound.so.2 (0xf759b000)
    libgtkglext-x11-1.0.so.0 => not found
    libgdkglext-x11-1.0.so.0 => not found
    libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7529000)
    libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7510000)
    libXt.so.6 => /usr/lib32/libXt.so.6 (0xf74b3000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf74aa000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7490000)
    libpangox-1.0.so.0 => /usr/lib32/libpangox-1.0.so.0 (0xf7483000)
    libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf747d000)
    libglade-2.0.so.0 => not found
    libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf7013000)
    libxml2.so.2 => /usr/lib32/libxml2.so.2 (0xf6ec6000)
    libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf6e18000)
    libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf6df8000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf6dd8000)
    libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf6dca000)
    libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf6d81000)
    libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf6cb6000)
    libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf6c67000)
    libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf6c62000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf6c5c000)
    libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf6b63000)
    libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf6a78000)
    libm.so.6 => /lib32/libm.so.6 (0xf6a4e000)
    libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf6a30000)
    libpthread.so.0 => /lib32/libpthread.so.0 (0xf6a15000)
    libc.so.6 => /lib32/libc.so.6 (0xf689a000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6887000)
    librt.so.1 => /lib32/librt.so.1 (0xf687e000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6748000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf6742000)
    libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf673b000)
    libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf65f5000)
    libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf65c8000)
    libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6593000)
    libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6588000)
    libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6583000)
    libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6573000)
    libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf656a000)
    libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf655f000)
    libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf655b000)
    libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf6556000)
    libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf64bf000)
    libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf643c000)
    libpng12.so.0 => /lib32/libpng12.so.0 (0xf6412000)
    libxcb-shm.so.0 => /usr/lib32/libxcb-shm.so.0 (0xf640e000)
    libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf6403000)
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf63e4000)
    libffi.so.6 => /usr/lib32/libffi.so.6 (0xf63dd000)
    /lib/ld-linux.so.2 (0xf77af000)
    libpcre.so.3 => /lib32/libpcre.so.3 (0xf639e000)
    libselinux.so.1 => /lib32/libselinux.so.1 (0xf6380000)
    libresolv.so.2 => /lib32/libresolv.so.2 (0xf6368000)
    libexpat.so.1 => /lib32/libexpat.so.1 (0xf633e000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf633a000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6333000)

```Yes, I did censor the usernme. Anyway, I have already tried:
```
cd ~/ wget -c [http://mirror.anl.gov/pub/ubuntu//pool/universe/g/gtkglext/libgtkglext1_1.2.0-1.2fakesync1_i386.deb](http://mirror.anl.gov/pub/ubuntu//pool/universe/g/gtkglext/libgtkglext1_1.2.0-1.2fakesync1_i386.deb) sudo dpkg -x libgtkglext1_1.2.0-1.2fakesync1_i386.deb libgtkglext sudo mv -v libgtkglext/usr/lib/* /usr/lib32/
```
I have also updated the dynamic link thing... yet STILL it gives me the error that I have the 64bit version installed. Currently running ubuntu 11:10, amd64 version. (if it doesn't work I'll be forced to get the WINDOWS version of pSX and run it through wine, which does work, but is slow, mute and clunky)

Any help would be much appreciated. :)

---

