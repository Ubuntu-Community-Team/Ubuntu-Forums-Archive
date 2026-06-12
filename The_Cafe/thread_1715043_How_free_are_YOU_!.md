---
title: "How free are YOU !"
date: 2011-03-26
forum: The Cafe
---

### Post by MooPi on 2011-03-26
I was just perusing through synaptic investigating gnome shell components and unity dependencies when I stumbled across "vrms". It is a terminal application that displays what non-free applications are installed on your computer. Curoius as to what my level of non-free apps included , I installed . I think this is quite free for an Ubuntu desktop. I didn't even know I'd installed unrar.

---

### Post by NightwishFan on 2011-03-26
Only Skype and Opera for me, also my system runs on 100% open source drivers. :)

---

### Post by wojox on 2011-03-26
vrms (Virtual Richard M. Stallman) is a program that analyzes the set of currently-installed packages on a Debian-based system, and reports all of the packages from the non-free tree which are currently installed. :P

That's hilarious. I'm going to have to look in AUR for that.

---

### Post by Sean Moran on 2011-03-26
Lucky VRMS was only a 12.4kb downlooad, because it wasn't installled on my slimline Karmic distro, but after a few seconds, I ran it, and this is what it told me:
```

sean@lucy02:~$ vrms
               Non-free packages installed on lucy02

nvidia-185-kernel-source  NVIDIA binary kernel module source
nvidia-185-libvdpau       Video Decode and Presentation API for Unix
nvidia-glx-185            NVIDIA binary Xorg driver
skype                     Skype
sun-java6-bin             Sun Java(TM) Runtime Environment (JRE) 6 (architecture
sun-java6-jre             Sun Java(TM) Runtime Environment (JRE) 6 (architecture

               Contrib packages installed on lucy02

dosemu                    The Linux DOS Emulator
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver

    Contrib packages with status other than installed on lucy02

flashplugin-installer     ( dei)  Adobe Flash Player plugin installer

  6 non-free packages, 0.4% of 1463 installed packages.
  4 contrib packages, 0.3% of 1463 installed packages.
sean@lucy02:~$ 



```
Thanks for teaching me something new on this late Saturday night.

---

### Post by MooPi on 2011-03-26
Happy to oblige. I only have Team Viewer because I have a friend who lives quite a distance away and it's about the best way to help with his computer issues.

---

### Post by forrestcupp on 2011-03-26
I wish they would port that to Windows. :)

---

### Post by MooPi on 2011-03-26
> **forrestcupp said:**
> I wish they would port that to Windows. :)
It would run all day and burn the computer to pieces looking for that one free tidbit :) :D:? :lol:

---

### Post by Sean Moran on 2011-03-26
> **MooPi said:**
> It would run all day and burn the computer to pieces looking for that one free tidbit :) :D:? :lol:
If there was a script I could download that would remove all those useless .dlls in the \windows\system directory from my memory, and stop my mind from burning to pieces for reasons withiout purpose, I'd like to know the word/s to add to the apt-get command.

Seriously, that **vmrs** command is wonderful.  Thanks mate.  I haven't yet re-installed a standard Ubuntu distro to see, but I don't remember removing it from this little distro, and it's only 12.9 (not 12.4 my mistake) kB to include, so I'll make sure vrms gets an inclusion in all my custom distros in future.  What is the difference between 292.6 Mb and 292.62 Mb?

---

### Post by BigSilly on 2011-03-26
Blimey. I've got loads. :(

```
Non-free packages installed

nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
opera                     A fast and secure web browser and Internet suite
snes9x-gtk                GTK+ port of Snes9x - Super NES Emulator
unrar                     Unarchiver for .rar files (non-free version)

         Contrib packages installed

conky                     highly configurable system monitor (transitional packa
conky-all                 highly configurable system monitor (all features enabl
flashplugin-installer     Adobe Flash Player plugin installer
flashplugin-nonfree       Adobe Flash Player plugin installer (transitional pack
gmameui                   front-end for the arcade games emulator MAME
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
playonlinux               front-end for Wine
rocksndiamonds            arcade-style game
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  4 non-free packages, 0.2% of 1986 installed packages.
  10 contrib packages, 0.5% of 1986 installed packages.
```

/Am ashamed

Conky's non-free?

---

### Post by Spice Weasel on 2011-03-26
> **BigSilly said:**
> Blimey. I've got loads. :(

```
Non-free packages installed

nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
opera                     A fast and secure web browser and Internet suite
snes9x-gtk                GTK+ port of Snes9x - Super NES Emulator
unrar                     Unarchiver for .rar files (non-free version)

         Contrib packages installed

conky                     highly configurable system monitor (transitional packa
conky-all                 highly configurable system monitor (all features enabl
flashplugin-installer     Adobe Flash Player plugin installer
flashplugin-nonfree       Adobe Flash Player plugin installer (transitional pack
gmameui                   front-end for the arcade games emulator MAME
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
playonlinux               front-end for Wine
rocksndiamonds            arcade-style game
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  4 non-free packages, 0.2% of 1986 installed packages.
  10 contrib packages, 0.5% of 1986 installed packages.
```

/Am ashamed

Conky's non-free?

A contrib package is a package that is free, but depends on nonfree packages.

---

### Post by Quadunit404 on 2011-03-26
```
tom@tom-laptop-linux:~$ vrms
          Non-free packages installed on tom-laptop-linux

dgen                      Sega Genesis/MegaDrive emulator
doom-wad-shareware        Shareware game files for the 3D game DOOM
nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
opera                     A fast and secure web browser and Internet suite
rar                       Archiver for .rar files
unrar                     Unarchiver for .rar files (non-free version)

Non-free packages with status other than installed on tom-laptop-li

ia32-crossover-games-demo ( dei)  Play Windows games like World of Warcraft

          Contrib packages installed on tom-laptop-linux

conky-all                 highly configurable system monitor (all features enabl
flashplugin-installer     Adobe Flash Player plugin installer
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
plymouth-manager          Manage your Plymouth with ease!
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts
virtualbox-4.0            Oracle VM VirtualBox

  7 non-free packages, 0.3% of 2491 installed packages.
  7 contrib packages, 0.3% of 2491 installed packages.

```

VirtualBox 4.0 and Conky aren't free, even though I have the source code of conky-1.8.1 sitting on my computer and VirtualBox 4.0 is licensed under the GPL. That's great. Maybe it's the extension pack I installed in VBox that made it 'non-free...' (and if that's true then I dunno)

And I see it missed some other proprietary apps on my PC (VMWare Player, World of Goo, Illumination Software Creator, Skype, Google Earth.) Awesome, it failed to catch EVERYTHING :roll:

---

### Post by Spice Weasel on 2011-03-26
Only the unbranded version of Virtualbox is free. You're using the oracle version.

The unbranded version is missing a few features. (I think USB support?)

---

### Post by Rubi1200 on 2011-03-26
Very interesting and thanks for the information.

Turns out I have 0.1% non-free installed (just one package). Hope that's acceptable :confused:

---

### Post by NightwishFan on 2011-03-26
> **Rubi1200 said:**
> Turns out I have 0.1% non-free installed (just one package). Hope that's acceptable :confused:

RMS does not approve. :popcorn:

---

### Post by mmix on 2011-03-26
found 1 contrib package "nvidia-common"

removed it, and vrms.

---

### Post by Perfect Storm on 2011-03-26
```
orion@universe:~$ vrms
              Non-free packages installed on universe

googleearth               Google Earth, a 3D map/planet viewer
ia32-crossover-games-demo Play Windows games like World of Warcraft
nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
unrar                     Unarchiver for .rar files (non-free version)

              Contrib packages installed on universe

conky                     highly configurable system monitor (transitional packa
conky-all                 highly configurable system monitor (all features enabl
flashplugin64-installer   Adobe Flash Player plugin 64 bit alpha installer
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  4 non-free packages, 0.2% of 1682 installed packages.
  6 contrib packages, 0.4% of 1682 installed packages.
orion@universe:~$ 

```

I have more non-free (games etc.), but seems it didn't pick it up.

---

### Post by markp1989 on 2011-03-26
heres mine

```
mark@mark-desktop:~$ vrms 
            Non-free packages installed on mark-desktop

nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
unrar                     Unarchiver for .rar files (non-free version)

            Contrib packages installed on mark-desktop

flashplugin-installer     Adobe Flash Player plugin installer
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  2 non-free packages, 0.1% of 1784 installed packages.
  4 contrib packages, 0.2% of 1784 installed packages.
mark@mark-desktop:~$ 

```

---

### Post by Legendary_Bibo on 2011-03-26
Mine would probably be 50% :D

---

### Post by aktiwers on 2011-03-26
> 
aktiwers@HAL2:~$ vrms
                Non-free packages installed on HAL2

nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
opera                     A fast and secure web browser and Internet suite
unrar                     Unarchiver for .rar files (non-free version)

                Contrib packages installed on HAL2

conky-all                 highly configurable system monitor (all features enabl
flashplugin-installer     Adobe Flash Player plugin installer
nvidia-cg-toolkit         NVIDIA Cg Toolkit Installer
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts
virtualbox-4.0            Oracle VM VirtualBox

  3 non-free packages, 0.1% of 2199 installed packages.
  7 contrib packages, 0.3% of 2199 installed packages.


urgh..  On another system I had 0% and vrms told me "Stallman would be proud"..  lol

---

### Post by MooPi on 2011-03-26
I just noticed that I have considerably fewer installed packages. Exactly 400 fewer than the next closest person. I'm even stingy with free programs :lol:

---

### Post by KiwiNZ on 2011-03-26
It just does not bother me. I install what I need be it free of not. That is the last consideration given if considered at all. I look for the best software to do the job.

---

### Post by MooPi on 2011-03-26
> **KiwiNZ said:**
> It just does not bother me. I install what I need be it free of not. That is the last consideration given if considered at all. I look for the best software to do the job.

I don't believe I've ever seen you write that before :-)

---

### Post by KiwiNZ on 2011-03-26
> **MooPi said:**
> I don't believe I've ever seen you write that before :-)

It's a first, my crazy spontaneous personality :P

---

### Post by mrhhug on 2011-03-26
contribin

so 0.3% of my packages are non free.... i do make an effort to use the free. but .3% of the time there is no suitable alternative.

opera : i think is the best browser available
virtualbox : i work in a computer store and have to make windows images
picasa : yeah i could use the web based but it just wasn't smooth.

video encoding : alot of times im asked to convert weddings and birthdays and junk to a nice neat DVD with chapters and trim the drunk uncle, this and that. - stuff comes in lots of different formats

flash : i would love for flash to die but honestly flash 10 supports some pretty nice stuff. gnash just doesn't do it all.

---

### Post by spcwingo on 2011-03-26
Here's mine:

```
Non-free packages installed on jonathan-desktop

nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
unrar                     Unarchiver for .rar files (non-free version)
w32codecs                 win32 binary codecs

          Contrib packages installed on jonathan-desktop

gstreamer0.10-pitfdll     GStreamer plugin for using MS Windows binary codecs
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
quake2                    improved version of id Software's Quake II engine
quake2-data               Installer for Quake II data files
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts
virtualbox-4.0            Oracle VM VirtualBox

  3 non-free packages, 0.2% of 1818 installed packages.
  7 contrib packages, 0.4% of 1818 installed packages.
```

The shame...where's a facepalm when you need one?  :)

---

### Post by RiceMonster on 2011-03-26
[img]http://ompldr.org/vN3o5bA/vrms.png[/img]

am i doin it rite?

---

### Post by sydbat on 2011-03-26
> **RiceMonster said:**
> [img]http://ompldr.org/vN3o5bA/vrms.png[/img]

am i doin it rite?Oddly, yes.

Also, here's my vrms (slightly paraphrased):> "You have too many proprietary / non-free elements in your computer that actually make it usable. Remove them immediately or RMS will show up at your home / gathering / other and berate you / pick things off his body and eat them until you DO remove all proprietary / non-free elements.

Remember, only the freedom RMS dictates is what matters. Actually being able to use your computer is really far down the list."

---

### Post by Quadunit404 on 2011-03-26
> **ricemonster said:**
> [img]http://ompldr.org/vn3o5ba/vrms.png[/img]

am i doin it rite?

You win the thread.

---

### Post by Simian Man on 2011-03-26
I just found another reason to use Fedora: they don't even have such a retarded program in the repos.

> **RiceMonster said:**
> am i doin it rite?

yep :).

---

### Post by cgroza on 2011-03-26
```
 vrms

No non-free or contrib packages installed on groza-pyNerd!  rms would be proud.


```

I removed the nvdia-commons and now I'm 100% open source.

---

### Post by Legendary_Bibo on 2011-03-26
> **KiwiNZ said:**
> It just does not bother me. I install what I need be it free of not. That is the last consideration given if considered at all. I look for the best software to do the job.

Ditto. I commend the FOSS community for it's beliefs, but I don't stand by them. I got into Linux because of the failures of Microsoft (Vista), and I like it, but I also want a computer that just works, and doesn't have issues. If I can't look at the source code for an application then so be it, as long as it works, and I have a need for it, then I'll use it.

---

### Post by jwbrase on 2011-03-26
```
34 non-free packages, 1.0% of 3324 installed packages.
14 contrib packages, 0.4% of 3324 installed packages.

```

I also have a fair number of unfree programs running under Wine or Dosbox that aren't listed included in the count, as well as emulator disk images for various dinosaur systems, etc.

Still better than our family Windows system...

---

### Post by Zero2Nine on 2011-03-26
```

            Non-free packages installed on erik-desktop

crafty                    state-of-the-art chess engine, compatible with xboard
nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
**openttd-opensfx           a sound set for use with the OpenTTD game**
python-profiler           deterministic profiling of any Python programs
sauerbraten-data          Game content for the Sauerbraten game
unrar                     Unarchiver for .rar files (non-free version)

Non-free packages with status other than installed on erik-desktop

assaultcube               ( dei)  realistic first-person-shooter
googleearth               ( dei)  Google Earth, a 3D map/planet viewer

            Contrib packages installed on erik-desktop

crafty-books-medtosmall   Medium-to-small size opening books for crafty chess en
googleearth-package       utility to automatically build a Debian package of Goo
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
sauerbraten               3D first-person game engine
sauerbraten-wake6         Small but dodgy deathmatch/instagib map for the Sauerb
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

```

Non-free? :confused:

---

### Post by Zero2Nine on 2011-03-26
> **RiceMonster said:**
> [img]http://ompldr.org/vN3o5bA/vrms.png[/img]

am i doin it rite?

No, your terminal isn't purple.

---

### Post by Rasa1111 on 2011-03-26
hmmm...
Interesting, thanks moopi! 

> vrms
        Non-free packages installed on ahmose-ThinkPad-Z61t

unrar                     Unarchiver for .rar files (non-free version)

        Contrib packages installed on ahmose-ThinkPad-Z61t

conky                     highly configurable system monitor (transitional packa
conky-all                 highly configurable system monitor (all features enabl
flashplugin-installer     Adobe Flash Player plugin installer
gstreamer0.10-pitfdll     GStreamer plugin for using MS Windows binary codecs
nvidia-common             Find obsolete NVIDIA drivers
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  1 non-free packages, 0.1% of 1768 installed packages.
  6 contrib packages, 0.3% of 1768 installed packages.


only 1 huh? :)

---

### Post by Dustin2128 on 2011-03-26
> **RiceMonster said:**
> [IMG]http://ompldr.org/vN3o5bA/vrms.png[/IMG]

am i doin it rite?
If you did it under cygwin, I'm 99% sure it'd call you an infidel.

---

### Post by Copper Bezel on 2011-03-27
```
   Non-free packages installed on Sophie

opera                     A fast and secure web browser and Internet suite
picasa                    Image management application from Google
unrar                     Unarchiver for .rar files (non-free version)
virtualbox-3.2            Oracle VM VirtualBox

               Contrib packages installed on Sophie

conky                     highly configurable system monitor (transitional packa
conky-all                 highly configurable system monitor (all features enabl
doublecmd-gtk             twin-panel (commander-style) file manager
flashplugin-installer     Adobe Flash Player plugin installer
flashplugin-nonfree       Adobe Flash Player plugin installer (transitional pack
flashplugin-nonfree-extra Adobe Flash Player platform support library for Esound
gstreamer0.10-pitfdll     GStreamer plugin for using MS Windows binary codecs
nvidia-common             Find obsolete NVIDIA drivers
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  4 non-free packages, 0.2% of 2462 installed packages.
  9 contrib packages, 0.4% of 2462 installed packages.
```

Mine didn't pick up Skype, which is most definitely installed, or Google Chrome (as I really do use the branded version with the colorful icon and an app store.) Odd.

It's adorable that this exists and I'm glad it's a joke, but it would be funnier if it worked.

Edit: Oh, well damn, Adobe Reader, too. I use Evince as my default, but I have Reader installed, and it didn't come up, either.

---

### Post by vehemoth on 2011-03-27
Just one contrib package conky-all

---

### Post by ctrlmd on 2011-03-27
I use anything that works!

---

### Post by Legendary_Bibo on 2011-03-27
Not as bad as I thought. I don't know why I have Nvidia drivers though. I do have other packages that it didn't pick up on. Some of these packages (like the citrix receiver) is needed for school. I don't know why RMS thinks everyone can just stick to free software.

```

           Non-free packages installed on bibos-computer

fglrx                     Video driver for the ATI graphics accelerators
fglrx-amdcccle            Catalyst Control Center for the ATI graphics accelerat
icaclient                 Citrix Receiver for Linux
nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
opera                     A fast and secure web browser and Internet suite
snes9x-gtk                GTK+ port of Snes9x - Super NES Emulator
unrar                     Unarchiver for .rar files (non-free version)
virtualbox-3.2            Oracle VM VirtualBox

           Contrib packages installed on bibos-computer

flashplugin-installer     Adobe Flash Player plugin installer
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
playonlinux               front-end for Wine
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  8 non-free packages, 0.3% of 2296 installed packages.
  5 contrib packages, 0.2% of 2296 installed packages.

```

---

### Post by TuxLyn on 2011-03-27
My VRMS :-)

               Non-free packages installed on Quadro

libmath-random-perl       Perl collection of random number generators
libvideo-info-perl        Perl module to examine video files
nikto                     web server security scanner
nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
opera                     A fast and secure web browser and Internet suite
rar                       Archiver for .rar files
unrar                     Unarchiver for .rar files (non-free version)

               Contrib packages installed on Quadro

flashplugin-installer     Adobe Flash Player plugin installer
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  7 non-free packages, 0.3% of 2268 installed packages.
  4 contrib packages, 0.2% of 2268 installed packages.

---

### Post by StephanG on 2011-03-27
I'm more free than all of you!

Why?  Because I don't care whether my software is free is or not.  I don't care if I use proprietary drivers, and I don't care what the open source movement thinks of me for not caring.

So basically, I'm free of that annoying conscious-like voice telling me to remove software I like, just because its not free. :P

---

### Post by Legendary_Bibo on 2011-03-27
> **StephanG said:**
> I'm more free than all of you!

Why?  Because I don't care whether my software is free is or not.  I don't care if I use proprietary drivers, and I don't care what the open source movement thinks of me for not caring.

So basically, I'm free of that annoying conscious-like voice telling me to remove software I like, just because its not free. :P

Jesus Christ, how horrifying!

Yeah I'm with you, Linux is great and all, but it's software before it's a philosophy.

---

### Post by KiwiNZ on 2011-03-27
> **StephanG said:**
> I'm more free than all of you!

Why?  Because I don't care whether my software is free is or not.  I don't care if I use proprietary drivers, and I don't care what the open source movement thinks of me for not caring.

So basically, I'm free of that annoying conscious-like voice telling me to remove software I like, just because its not free. :P

No not all of us

Refer post #21 for one example :wink:

---

### Post by StephanG on 2011-03-27
Post 21:

> It just does not bother me. I install what I need be it free of not. That is the last consideration given if considered at all. I look for the best software to do the job.

Ah, sorry.  My bad.

Though, I'm still more free of you, because there are a lots of other stuff that I also don't care about. :P

Actually, come to think of it.  I'm kind of a heartless bastard.  Maybe I should start to care about some things...  But I'll start small, maybe by wearing clothes in public again.

P.S.  For those who don't get the joke, the last line refers to a chat on the radio in the game GTA Vice City.  Basically he made the statement that nudists are the most free people in the world.

---

### Post by Random_Dude on 2011-03-27
I've tried it just out of curiosity.
Found 4 or 5 things, I was expecting more actually. However, it didn't detect MATLAB, so it doesn't work very well.

I don't really see the point of this besides curiosity. If you are worried about software freedom just run gNewSense. ;)

Cheers :cool:

---

### Post by Copper Bezel on 2011-03-27
> I don't really see the point of this besides curiosity.

I was only curious to begin with, but I'm *still* curious, because vrms is missing several packages I know to be nonfree, including anything installed from Canonical partners. I certainly wouldn't take vrms seriously, one way or the other.

---

### Post by JRV on 2011-03-27
> 
Non-free packages installed on langsdown2

unrar                     Unarchiver for .rar files (non-free version)

             Contrib packages installed on langsdown2

conky                     highly configurable system monitor (transitional packa
conky-all                 highly configurable system monitor (all features enabl
flashplugin-installer     Adobe Flash Player plugin installer
nvidia-common             Find obsolete NVIDIA drivers
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  1 non-free packages, 0.1% of 1547 installed packages.
  5 contrib packages, 0.3% of 1547 installed packages.


Just Conky and ubuntu-restricted-extras

---

### Post by gnomeuser on 2011-03-27
I strive to be free by avoiding RMS, virtual or not.

---

### Post by sammiev on 2011-03-27
BitDefender is my weak spot but as I transfer files between different OS and computers I require it.


         Non-free packages installed on sam-Satellite-L650

bitdefender-common        BitDefender Antivirus solution (common components)
bitdefender-mail          BitDefender Antivirus solution (mail components)
bitdefender-scanner       Antivirus solution (Command line virus scanner)
bitdefender-scanner-gui   Antivirus solution (gui virus scanner)
unrar                     Unarchiver for .rar files (non-free version)

         Contrib packages installed on sam-Satellite-L650

flashplugin-installer     Adobe Flash Player plugin installer
nvidia-common             Find obsolete NVIDIA drivers
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  5 non-free packages, 0.3% of 1552 installed packages.
  3 contrib packages, 0.2% of 1552 installed packages.

---

### Post by wangsuda on 2011-03-27
I'm not doing too bad. I run what I need and what works.

>  Non-free packages installed on douglas-Aspire-4730Z

p7zip-rar                 non-free rar module for p7zip
unrar                     Unarchiver for .rar files (non-free version)

        Contrib packages installed on douglas-Aspire-4730Z

flashplugin-installer     Adobe Flash Player plugin installer
gstreamer0.10-pitfdll     GStreamer plugin for using MS Windows binary codecs
nvidia-common             Find obsolete NVIDIA drivers
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts
virtualbox-4.0            Oracle VM VirtualBox

  2 non-free packages, 0.1% of 1713 installed packages.
  5 contrib packages, 0.3% of 1713 installed packages.


---

### Post by Zero2Nine on 2011-03-27
> **wangsuda said:**
> I'm not doing too bad. I run what I need and what works.

Strange I also installed 7zip but vrms did not report it here.

---

### Post by wangsuda on 2011-03-27
I have a couple of things it missed (Chrome, skype). It was fun, but that's about all I'll give it!

---

### Post by MooPi on 2011-03-27
> **StephanG said:**
> Post 21:



Ah, sorry.  My bad.

Though, I'm still more free of you, because there are a lots of other stuff that I also don't care about. :P

Actually, come to think of it.  I'm kind of a heartless bastard.  Maybe I should start to care about some things...  But I'll start small, maybe by wearing clothes in public again.

P.S.  For those who don't get the joke, the last line refers to a chat on the radio in the game GTA Vice City.  Basically he made the statement that nudists are the most free people in the world.
So to be truly free I must disrobe whilst I compute ?

---

### Post by fela on 2011-03-27
Aha, Virtual Richard Stallman.

I run Linux because it works better, not because it's free.

---

### Post by alaukikyo on 2011-03-27
> **fela said:**
> Aha, Virtual Richard Stallman.

I run Linux because it works better, not because it's free.

just so you are clear rms want software to be free as in freedom and not necessarily free as in free beer .

---

### Post by Sean Moran on 2011-03-27
> **fela said:**
> Aha, Virtual Richard Stallman.

I run Linux because it works better, not because it's free.
Good call, Fela!  That one went straight over my head.  I was sitting there last night wondering what vrms stood for, and never came close.

---

### Post by alaukikyo on 2011-03-27
> **sammiev said:**
> BitDefender is my weak spot but as I transfer files between different OS and computers I require it.


         Non-free packages installed on sam-Satellite-L650

bitdefender-common        BitDefender Antivirus solution (common components)
bitdefender-mail          BitDefender Antivirus solution (mail components)
bitdefender-scanner       Antivirus solution (Command line virus scanner)
bitdefender-scanner-gui   Antivirus solution (gui virus scanner)
unrar                     Unarchiver for .rar files (non-free version)

         Contrib packages installed on sam-Satellite-L650

flashplugin-installer     Adobe Flash Player plugin installer
nvidia-common             Find obsolete NVIDIA drivers
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  5 non-free packages, 0.3% of 1552 installed packages.
  3 contrib packages, 0.2% of 1552 installed packages.


you can use clamwin .

---

### Post by RiceMonster on 2011-03-27
> **alaukikyo said:**
> just so you are clear rms want software to be free as in freedom and not necessarily free as in free beer .

Wow, that's profound. Thanks for sharing.

---

### Post by Zero2Nine on 2011-03-27
> **RiceMonster said:**
> Wow, that's profound. Thanks for sharing.

Wow a sarcastic post, that's original.

---

### Post by RiceMonster on 2011-03-27
> **Zero2Nine said:**
> Wow a sarcastic post, that's original.

Originality is what I was aiming for.

---

### Post by fela on 2011-03-27
> **alaukikyo said:**
> just so you are clear rms want software to be free as in freedom and not necessarily free as in free beer .

That's what I meant in the post though ;)

---

### Post by Legendary_Bibo on 2011-03-27
> **RiceMonster said:**
> Wow, that's profound. Thanks for sharing.

lol, I love you RiceMonster. :)

---

### Post by Rasa1111 on 2011-03-28
> **RiceMonster said:**
> Originality is what I was aiming for.

lol, chalk that one up to a 'fail' then.

---

### Post by wangsuda on 2011-03-28
+1

---

### Post by cheapodonuts on 2011-05-01
:~$ vrms
           Non-free packages installed on cheapo-desktop

gsfonts-other             Additional fonts for the ghostscript interpreter
nvidia-current            NVIDIA binary Xorg driver, kernel module and VDPAU lib
nvidia-glx-185            Transitional package for nvidia-glx-185
t1-xfree86-nonfree        non-free Postscript Type 1 fonts from XFree86
ttf-larabie-deco          Decorative fonts from [www.larabiefonts.com]("http://www.larabiefonts.com")
ttf-larabie-straight      Straight fonts from [www.larabiefonts.com]("http://www.larabiefonts.com")
ttf-larabie-uncommon      Special decorative fonts from [www.larabiefonts.com]("http://www.larabiefonts.com")
ttf-xfree86-nonfree       non-free TrueType fonts from XFree86
ttf-xfree86-nonfree-syria non-free syriac OpenType fonts from XFree86
unrar                     Unarchiver for .rar files (non-free version)

Non-free packages with status other than installed on cheapo-deskto

sun-java6-bin             ( dei)  Sun Java(TM) Runtime Environment (JRE) 6 (arch
sun-java6-jre             ( dei)  Sun Java(TM) Runtime Environment (JRE) 6 (arch

           Contrib packages installed on cheapo-desktop

flashplugin-installer     Adobe Flash Player plugin installer
googleearth-package       utility to automatically build a Debian package of Goo
nvidia-common             Find obsolete NVIDIA drivers
nvidia-settings           Tool of configuring the NVIDIA graphics driver
outrec                    Record all audio output from the sound card of your co
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts

  12 non-free packages, 0.6% of 2081 installed packages.
  6 contrib packages, 0.3% of 2081 installed packages.
-------

So what are we saying here? I'll never be persuaded to pay for any of this malarkey using money, barter or exchange. So it's in the free beer category at least. And, am I not at least as free as a young goose that has been 'imprinted' on someone that owns a microlite, and will guide me to the main flock as it migrates in the autumn? :D

---

### Post by bluelamp999 on 2011-05-01
Here's mine FWIW...

```
mike@ANTEC:~$ vrms
               Non-free packages installed on ANTEC

fglrx                     Video driver for the ATI graphics accelerators
fglrx-amdcccle            Catalyst Control Center for the ATI graphics accelerat
opera                     A fast and secure web browser and Internet suite
python-profiler           deterministic profiling of any Python programs
unrar                     Unarchiver for .rar files (non-free version)

                Contrib packages installed on ANTEC

conky                     highly configurable system monitor (transitional packa
conky-all                 highly configurable system monitor (all features enabl
nvidia-common             Find obsolete NVIDIA drivers
ttf-mscorefonts-installer Installer for Microsoft TrueType core fonts
virtualbox-4.0            Oracle VM VirtualBox

  5 non-free packages, 0.3% of 1664 installed packages.
  5 contrib packages, 0.3% of 1664 installed packages.
```

---

