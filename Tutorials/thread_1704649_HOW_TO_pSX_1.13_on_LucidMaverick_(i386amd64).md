---
title: "HOW TO: pSX 1.13 on Lucid/Maverick (i386/amd64)"
date: 2011-03-10
forum: Tutorials
---

### Post by Mystro256 on 2011-03-10
[COLOR="Red"][B]THIS WILL NOT WORK ON NATTY (11.04). PSX DOESN'T SEEM TO WANT TO WORK ON NATTY AND BEYOND. YOU CAN TRY SOMETHING ELSE, SUCH AS PCSXR, FOUND HERE: [http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)
PLEASE DON'T ASK ANY QUESTIONS ABOUT THIS PACKAGE ON NATTY OR ANY QUESTIONS ABOUT PCSXR ON THIS THREAD.[/B]
*Thank you*[/COLOR]

This is download thread to install playstation emulation (with pSX 1.13) on 10.04/10.10/11.04 (Lucid/Maverick/Natty) for 32 bit/64 bit (i386/amd64)

***_Last Updated (April 12th)_* The package should work on Natty but the Software claims it's bad quality. Just hit ignore and install it anyway, I don't see any issue, though you may have to run ***sudo apt-get -f install*** after installing.**

A while ago [dfreer posted a thread]("http://ubuntuforums.org/showpost.php?p=6127662&postcount=246") with pSX packages to install and make pSX 1.13 work on hardy and intrepid , but these are out of date and do not work on Lucid nor Maverick. After about an hour of playing with it, I got it working. I directly modified his packages, so kudos to dfreer.

Anyway, I uploaded the deb files for both i386 (32bit) and amd64 (64bit), I compressed them because the forums didn't let me post the deb files directly. Let me know either don't work. **If you have issues with the debs, I uploaded another tar thats just the pSX folder (*pSX_1.13-3.3.tar.gz*). Just extract it and run the pSX-launcher.sh**

Please also note that lib32gtkglext1_1.2.0-3.2-amd64.deb (included in amd64 compressed file) ***must*** be installed for 64bit/amd64 systems. This is not needed for 32bit systems. If it says you can't install libgtkglext1-dev (Similar to Rytron's post), download the deb here: [>click here<]("http://launchpadlibrarian.net/15535318/libgtkglext1-dev_1.2.0-1ubuntu1_i386.deb"), or find it on launchpad

**[COLOR="Red"]PLEASE READ IF YOU HAVE SOUND ISSUES: **pSX requires having a playstation bios file to run. I can't legally supply you with one, so just google it. Also while running, due to a conflict with pSX and pulseaudio, pulseaudio is disabled while running pSX. This may make any program using it crash and will probably make the mixer/sound volume control unavailable while pSX is running. It should return to normal when pSX is closed. If not, close any program currently using sound. If that doesn't work, hit alt+f2 and type in "pulseaudio" (without quotes).[/COLOR]

Enjoy! :p

---

### Post by dave00001 on 2011-03-12
Worked perfectly.  Thanks.

---

### Post by crash123 on 2011-03-13
Been looking for this for awhile. Thanks!

---

### Post by jao_madn on 2011-03-13
Hi when i installed in my ubuntu maverick i got the following photos. Please see attach photos

[http://img857.imageshack.us/i/psxerrorinmaverick.png/](http://img857.imageshack.us/i/psxerrorinmaverick.png/)

---

### Post by Rytron on 2011-03-14
Hi Mystro256. I went to install deb package and got message 'Cannot install '[COLOR="Red"]libgtkglext1-dev[/COLOR]' I went to install that item in synaptic but could not.

---

### Post by shade82000 on 2011-03-16
Hi all...

I've been trying to use psx over the last couple of days on my 32/64-bit boxes.

It doesn't work on the 32-bit - I get the same messages as jao_madn reported in the above post, although I have no trouble installing other packages so I am guessing either there is something wrong with this 32-bit package or I do not know enough to fix it (probably the latter).

It works on the 64-bit but not so good that I want to keep it.  I have removed the package but every time I restart the computer, pulseaudio does not start (and the associated 'speaker' icon in the tray does not appear) so I have to manually do ALT+F2 and load pulseaudio.

I have 6 Ubuntu boxes and I have compared the contents of their Startup Applications; it seems that all the right entries are present and enabled but it looks like installing psx has changed something else that was not put right when it was removed.

Anyone know what has happened and how to fix it?

These are the only two entries relating to pulseaudio that are present on every computer I have:
[IMG]http://i439.photobucket.com/albums/qq119/shade82000/Screenshot-PulseAudio.png[/IMG]

[IMG]http://i439.photobucket.com/albums/qq119/shade82000/Screenshot-PulseAudioKDE.png[/IMG]

THANKS!

---

### Post by Mystro256 on 2011-03-16
@shade82000

Yeah, I've noticed it randomly installs broken on some systems. I have no idea why because it works on both my 64 bit and 32 bit system (maverick and lucid respectively).

As well as I said specifically in my first post in red. **If pulse audio does not start, you must add a new entry to the start up programs with the command "pulse audio"** (i'll edit the first post to reduce confusion). The launch script for psx kills pulse audio while running psx and disables autospawn functionity to pulseaudio, thus must be started manually. You can always re-enable autospawn by typing this in the terminal: ```
gedit ~/.pulse/client.conf
``` (or replace gedit with kwrite for KDE and mousepad for XFCE) and remove the line that states "autospawn = no" (this is a per user setting)

**EDIT: I uploaded another archive that's not an package, for those who have issues with installing the packages.**



@Rytron

Try googling the package and find the deb file via the internet. If you're using 64 bit, I included it with the 64bit download.

---

### Post by shade82000 on 2011-03-17
Thanks for your help Mystro.

Changing the autospawn setting makes the volume control appear without having to add any additional entries into Startup Applications.

I figured that the workaround you suggested in your first post was good if people want to keep psx installed but in my case I wanted to remove it and return my system back to how it was and did not see that I should need to add additional Startup Applications that weren't there prior to installing psx.

Thanks for your help!

---

### Post by mattwren88 on 2011-03-19
I got the same problem as jao_madn so I tried the .bz2 file and tried running it and it warns me that I have a BIOS problem. Any suggestions to remedy these issues?

---

### Post by Mystro256 on 2011-03-19
Unfortunately the emulator requires a PS1 bios to run. Due to legality issues, I probably can't tell you where to find one on these forums, but remember, google is your friend :p

---

### Post by Mystro256 on 2011-03-20
I updated the original post with a better workaround than I had before, along with fixed deb's (I hope).

Hopefully this works for everyone.
Let me know if there's further problems! :P

---

### Post by Brigit Lemanski on 2011-03-20
> **Mystro256 said:**
> I updated the original post with a better workaround than I had before, along with fixed deb's (I hope).

Hopefully this works for everyone.
Let me know if there's further problems! :P

I just tried the i386 .deb and it claims it can't install all dependencies.  Same error as [http://img857.imageshack.us/i/psxerrorinmaverick.png/](http://img857.imageshack.us/i/psxerrorinmaverick.png/)

---

### Post by Mystro256 on 2011-03-20
Well I honestly can't figure out what's wrong and I just tested the packages, I'm not getting any errors... So I can't really fix anything because I don't know the cause.

Unfortunately you'll have figure out what you're missing and install them manually. If you can't find it in synaptic, look on launchpad. Alternatively, you could try and use the non-deb version I posted.

These are the dependencies:
```
zlib1g (>= 1:1.2.3.3)
libasound2 (>= 1.0.14)
libgtkglext1 (>= 1.2.0)
libglu1-mesa (>= 7.0.1)
libxmu6 (>= 2:1.0.3)
libxt6 (>= 1:1.0.5)
libsm6 (>= 2:1.0.3)
libice6 (>= 2:1.0.3)
libpango1.0-0 (>= 1.18.2)
libglib2.0-0 (>= 2.14.1)
libc6-i686 (>= 2.6.1)
libglade2-0 (>= 1:2.6.2)
libgtk2.0-0 (>= 2.12.0)
libxml2 (>= 2.6.30)
libatk1.0-0 (>= 1.20.0)
libcairo2 (>= 1.4.10)
libstdc++6 (>= 4.2.1)
libgcc1 (>= 1:4.2.1)
libx11-6 (>= 2:1.1.1)
libxext6 (>= 2:1.0.3)
libxxf86vm1 (>= 1:1.0.1)
libxdamage1 (>= 1:1.1.1)
libxfixes3 (>= 1:4.0.3)
libdrm2 (>= 2.3.0)
libfontconfig1 (>= 2.4.2)
libxrender1 (>= 1:0.9.2)
libxinerama1 (>= 2:1.0.2)
libxi6 (>= 2:1.1.2)
libxrandr2 (>= 2:1.2.1)
libxcursor1 (>= 1:1.1.8)
libxcomposite1 (>= 1:0.4.0)
libfreetype6 (>= 2.3.5)
libpng12-0 (>= 1.2.15~beta5-2build1)
libxau6 (>= 1:1.0.3)
libxdmcp6 (>= 1:1.0.2)
libexpat1 (>= 1.95.8)
libgtkglext1-dev (>= 1.2.0)
```

---

### Post by Tripmonkey_uk on 2011-03-22
I'm getting the same errors unfortunately. PSX installs and runs great but it screws up the package manager whilst it's at it and I can't update anything else on the system until PSX is un-installed.

I've been through the list of dependencies and the only one that I can see a problem with is **libc6-i686 (>= 2.6.1)**. This should be **libc6 (>= 2.6.1)**, minus the -i686 part. I updated this by itself and tried to re-install PSX but still got the same errors.

The problem could be in the way that the package is communicating with the package manager. I'm using the 32bit version by the way so I'll try the version now that doesn't need to be installed.

Cheers for the work so far. At least I got it running enough to test that the bios file and games work ok :D

EDIT: I un-installed (not completely removed) the deb version, dropped the non-deb versions program file and launch script into the hidden PSX folder in my home folder, set up a game menu's shortcut to point to the new location for the launch script (had to change one line of the script to point it to the new location of the program file) and fired it up. Not a problem with it and my package managers back to working again :D

Cheers once again Mystro256 it still saved me a lot of hassle :)

---

### Post by Mystro256 on 2011-03-22
No problem, glad to help! :D

Unfortunately my package making skills are a little lacking, so this is the best I can do, especially because I can't reproduce the error on any of my installs of lucid or maverick... I'll change the libc6-i686 to libc6 and repost the debs, hopefully it fixes it.

But glad to hear people are enjoying it! :)

**EDIT: Finished, reposted on first post**

---

### Post by thesteaIth on 2011-03-30
Thank you for this installer/package.  I've been unsuccessful getting pSX to run for whatever reason and had almost given up.  



Thanks again,

thestealth

---

### Post by Mystro256 on 2011-03-30
I take that means it works?

I've heard from another, whom I gave it to, that it now works, opposed to the one he tried before. So I would assume it's finally fixed.

---

### Post by parry_all on 2011-04-10
Thank you, Mystro256!

I got this working alright, but there is a small problem - when I close pSX, the console reads like this:

```
Terminating processes: 2903.
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
nohup: ignoring input and appending output to `nohup.out'

```and just freeze forever, I have to close the terminal before I use 'ctrl + c'. Alternatively, if running by the soft link on the desktop, (I mean created a link - ```
bash -c "cd ~/Desktop/pSX/ && ./pSX-launcher.sh"
```) when I close pSX, it disappears, but there is always a process in the system called 'bash', just takes up some system resource. I was wondering if there is a way of closing every relevant when I close pSX.

Could you give me some idea on this ?

Thanks

---

### Post by Mystro256 on 2011-04-10
The first issue is either an ALSA bug or just a warning that doesn't effect the PSX launcher functionality.

The second issue of bash or sh still running after closing is something I'm trying to figure out. You can try opening the launcher in gedit and replacing the code with this:
```
#!/bin/bash
#disable pulseaudio first
#disables auto

echo "autospawn = no" > ~/.pulse/client.conf
sleep 1

alsa force-reload
sleep 1
./pSX
sleep 1
rm ~/.pulse/client.conf
pulseaudio &
disown

exit
```

Let me know if it fixes it, and if so, I'll put it into the files in the first post.

---

### Post by parry_all on 2011-04-11
You are great, Mystro256!

The problem solved, many thanks!

---

### Post by Mystro256 on 2011-04-12
Cool cool, I'll update the launcher in the deb's and tarball, and upload in the first post. Just need to repackage the debs, so I'll post it when I'm done. I'll also change the version number of the debs, so it's regarded as an upgrade.

---

### Post by tnanek on 2011-05-05
When I start the program, my computer goes silent. The game I have seems to play fine, but no sound. Also, the configuration screen is not accessible. When I go to the config option, the window closes instantly. I made an account at the developer's forum to report it there, but it needs to be manually approved of, so I'm posting here in the meantime.

In regards to the sound though, I have a bash script that is always playing a music file generally. When the pSX program starts up, my bash script is terminated in the middle of a mplayer call (playing all the .mp3 files in that directory in a random order), and it seems to hang. I usually just go back to that terminal after I've closed pSX and ctrl+c out of it and start it up again afterwards.

I'm also not sure if this is related or not, but I use an HDMI device for my sound, not the standard output; so its potentially possible for the sound to be correctly output, just not through the HDMI cable, and thus I'm not hearing it.

On another side note, I haven't been able to run it from the command line, but the launcher seems to work just fine. The command line output is below.

```
$: /usr/local/games/psx32/pSX
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:14596): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:14596): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:14596): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
Segmentation fault
$:

```

---

### Post by Mystro256 on 2011-05-05
I'm not sure if I can make it work with the configuration screen to be honest, it seems really hit and miss :(

The sound issue is because either alsa isn't installed or does not work properly.

---

### Post by rimmmer on 2011-05-09
running natty amd64 and cant get to run. deb doesn't run on my machine and tarball brings this```
./pSX-launcher.sh
lsof: WARNING: can't opendir(/dev/vboxusb): Permission denied
Terminating processes: 1639lsof: WARNING: can't opendir(/dev/vboxusb): Permission denied
lsof: WARNING: can't opendir(/dev/vboxusb): Permission denied
.
lsof: WARNING: can't opendir(/dev/vboxusb): Permission denied
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hda-codec-hdmi snd-hda-codec-conexant snd-seq-midi snd-hda-intel snd-rawmidi snd-seq-midi-event snd-hda-codec snd-hwdep snd-seq snd-seq-device snd-pcm snd-timer snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:6576): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:6576): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:6576): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

pad=0
./pSX-launcher.sh: line 10:  6576 Segmentation fault      ./pSX

```
or this
```
sh pSX-launcher.sh
lsof: WARNING: can't opendir(/dev/vboxusb): Permission denied
lsof: WARNING: can't opendir(/dev/vboxusb): Permission denied
/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Permission denied
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:6869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:6869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:6869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

pad=0
Segmentation fault
pSX-launcher.sh: 14: disown: not found

```
running as sudo gets the language box to show up but no further.

---

### Post by leomeloxp on 2011-07-05
Hey there everyone, I have a (at least I suppose to be) different error here... =X

What I did was to try to install the 32 bits version of libgtkg using dpkg -i --force-architecture, but it didn't allow me because of broken dependencies... Now, when I tried to install the package on the Archive for AMD64, it gives me this error...

```
installArchives() failed: dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-1.1ubuntu1_amd64.deb (--unpack): 
 libgtkglext1: 1.2.0-1.1ubuntu1 (Multi-Arch: no) is not co-installable with libgtkglext1:i386 1.2.0-1ubuntu1 (Multi-Arch: no) which is currently installed 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libgtkglext1_1.2.0-1.1ubuntu1_amd64.deb 
dpkg: dependency problems prevent configuration of libgtkglext1:i386: 
 libgtkglext1:i386 depends on libatk1.0-0 (>= 1.20.0). 
 libgtkglext1:i386 depends on libc6 (>= 2.1.3). 
 libgtkglext1:i386 depends on libcairo2 (>= 1.2.4). 
 libgtkglext1:i386 depends on libfontconfig1 (>= 2.4.0). 
 libgtkglext1:i386 depends on libfreetype6 (>= 2.3.5). 
 libgtkglext1:i386 depends on libglib2.0-0 (>= 2.16.0). 
 libgtkglext1:i386 depends on libgtk2.0-0 (>= 2.13.3). 
 libgtkglext1:i386 depends on libice6 (>= 1:1.0.0). 
 libgtkglext1:i386 depends on libpango1.0-0 (>= 1.21.3). 
 libgtkglext1:i386 depends on libsm6. 
 libgtkglext1:i386 depends on libx11-6. 
 libgtkglext1:i386 depends on libxmu6. 
 libgtkglext1:i386 depends on libxt6. 
 libgtkglext1:i386 depends on zlib1g (>= 1:1.1.4). 
dpkg: error processing libgtkglext1:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of lib32gtkglext1: 
 lib32gtkglext1 depends on libgtkglext1 (>= 1.2.0); however: 
  Package libgtkglext1 is not installed. 
dpkg: error processing lib32gtkglext1 (--configure): 
 dependency problems - leaving unconfigured 
```If you guys can help me, I tried using aptitude remove(purge) libgtkg... but it didn't work =/

I'm on Ubuntu Natty 64bits on a Dell Laptop (which I was able to run the emulator before formatting the computer T-T)

Thanks in advance o/

---

### Post by Mystro256 on 2011-07-09
I'm not surprised, it doesn't seem to work on Natty too well (hence "Lucid/Maverick" in the title).

One reason is due to the new version of alsa seems to have broke my script because of one of the commands needs sudo privileges. I would implement this but it's a bad idea, as no one should ever run something as sudo unless they know exactly what it does.

If you still want to run it on Natty, get the tarball off my first post (pSX_1.13-3.3.tar.gz) and change the launcher script to this:

```
#!/bin/bash
#disable pulseaudio first
#disables auto

echo "autospawn = no" > ~/.pulse/client.conf
sleep 1

**gksudo** alsa force-reload
sleep 1
./pSX
sleep 1
rm ~/.pulse/client.conf
pulseaudio &
disown

exit
```


**Use at your own risk**: Now just run the script, though I can't guarantee it to work.** Oneiric will have gnome 3, which seem uncombatible with pSX, so I doubt I'll be about to make another work around**. PSX works with wine though, it's not perfect but better than nothing. Feel free to contact the creator of pSX to bug him to fix these issues or at least release the source code: [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

---

### Post by leomeloxp on 2011-07-10
[LEFT]I was able to run PSXfin with this fix you said... The only thing is, it had no sound (I think that was expected xD) and if I ever try to open the configuration window, it gives a segmentation fault and closes the emulator =X

About wine, I tried to open my windows version, and I got this error in a pop up window:
[/LEFT]
[CENTER][LEFT] ```
 ERROR Failed to find a valid mode (perhaps you need to switch your desktop to 32bit mode?) 
```

Would it be worth it to install a VM with Maverick to have it running fine? When I was on Maverick I was able to make it run by myself, just by preventing pulse from re-spawning XD
[/LEFT]
[/CENTER]

---

### Post by Mystro256 on 2011-07-10
Yeah that's what my script does, but it seems like its no good for Natty, and I can't get it working with gnome 3, so I doubt I can help get it working for Oneiric either. As for the sound issue you mentioned, you need to make sure ALSA is running properly, but else wise I would give up on it.

Also, I can't seem to get it working in wine too well either, way too many issues :S
You could try ePSXe via wine, but I never got that working all that well in windows, let alone wine, so I can't be much help.

Anyway, I ran it in Virtualbox OSE, and seems to work just fine, but I can't figure out how to get my gamepad working with virtualbox, so it doesn't help too much for me personally. Although there are way's around that, which I haven't looked into, but I haven't done any research quite yet.

---

### Post by leomeloxp on 2011-07-11
Virtualbox OSE? What's that? XD

Anyway, thanks for all the replies and the information, even if it wasn't a solution, at least now I know more about this PSX case on Linux.

---

### Post by Mystro256 on 2011-07-11
No problem!

As for Virtualbox OSE, it's a VM program made by oracle, which is FOSS/GNU, or at least for the most part. I'm told it's very popular on Linux, and it's available in Ubuntu's Software Centre. Here's the website: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by manguelpr on 2011-07-29
can someone help me a little bit, i never has write here or in any ubuntu forum I'm new user but i get it work as my old OS very well and i like it, but one of my favorite application is psx because i play Final Fantasy 7.

ok here is what i did, i download the package for 64 bits, i also are running it in ubuntu 11.04 x64 and thats why i download the 64 package....

anyway i install the 2 tools which come in this package ( pSX_1.13-3.3-amd64.tar.gz ) and works great the installation but...

after i install it, i get my psx icon in apps center and i also are able to run it, then ask me for language and after for **bios**, i also had the **Bios SCPH1001.BIN** and there is the problem.... after i click bios its doing nothing just closed all..

1.install psx package
2.run it and selected language 
3.select bios  < im stuck at this point.

its asking me for a bios in the folder:

/usr/local/games/psx32/bios

i also try to create the new file in that area for be able to put the bios there but i get nothing, its just telling me that i have no permission anyway what im doing wrong?... 

im not a brain user but i love the linux and i wanted to work with that application... TY

---

### Post by Mystro256 on 2011-07-29
Well I'll say it once, and I'll say it again, this post is for Lucid/Maverick, **not Natty**, ie 10.04 and 10.10, not 11.04.

The workaround present in this package ***will not work on Natty** and beyond*. Your best bet for PSOne emulation for Ubuntu for Natty, etc. would be PCSXR, although it's not complete and will not run all games.

You can find PCSXR here: [http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)
but please don't ask questions in this thread for PCSXR or pSX on Natty, etc.

---

### Post by manguelpr on 2011-07-29
ops okay, ty again for the link, my bad i was reading information about the psx from like 4-5 sites and i miss that part, sry and good luck.):P

---

### Post by tech-hero on 2011-08-15
It worked well on my 10.04 laptop. Will check it's performance after i ripped my CDS.

BTW, I have noticed, PSX disable your system sounds when it is running. but after closing it, the sounds just come back. Is it how it is used to be? thanks.

---

### Post by RoastedBeef on 2011-09-18
I have the BIOS problem also.

I have Ubuntu 10.04 10.04 LTS, and Installed psx32 perfectly, not problems at all.

I run it and asks for language, then for the BIOS file, I choose the SPCH1001.bin file (assuming this is the correct bios file) and nothing happens. 

Not sure what the problem is, any help is appreciated.

---

### Post by Mystro256 on 2011-09-18
I would just suggest just using [the SVN of PCSXR]("http://pcsxr.codeplex.com/documentation") instead. pSX seems to temperamental for mostly the same results.

---

### Post by RoastedBeef on 2011-09-18
Wow, worked perfectly. Thanks!

---

### Post by tctvn on 2011-11-20
on ubuntu 11.10?

---

### Post by satanselbow on 2011-11-20
> **tctvn said:**
> on ubuntu 11.10?



```

Install PCSX Reloaded (SVN) on Ubuntu 11.10

sudo apt-get install gawk mawk gcc gcc-multilib intltool intltool-debian gettext gettext-base liblocale-gettext-perl libgettext-ruby1.8 perl perl-base perl-modules libperl5.12 pkg-config libxml2 libxml2-dev libxml2-utils python-libxml2 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common python-gtk2 libgtk2.0-dev libglade2-0 libglade2-dev python-glade2 libsdl-sge-dev libsdl-perl libsdl-ruby libsdl-ruby1.8 libsdl-gfx1.2-dev libsdl-ttf2.0-dev libsdl-console-dev libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libsdl-sound1.2-dev gstreamer0.10-sdl libsdl-ocaml-dev libsdl-pango-dev libguichan-sdl-0.8.1-1 zlib-bin zlib1g zlib1g-dev libxvmc1 libxv-dev libxv1 libxcb-xv0 libxcb-xtest0 subversion libtool nasm libbz2-dev automake autoconf libxxf86vm-dev x11proto-record-dev libxtst-dev libgmp3-dev libcdio-dev libsndfile1-dev && sudo apt-get update && sudo apt-get upgrade

cd ~

mkdir svn && cd svn

svn co https://pcsxr.svn.codeplex.com/svn pcsxr && cd pcsxr/pcsxr/

autoreconf -f -i && ./configure --prefix=/usr --enable-libcdio --enable-opengl && make && sudo make install && sudo ldconfig && 

pcsxr

```

---

### Post by moacir.souza on 2011-12-27
Everything working fine so far, thank you so much for this package. I was making almost the same thing myself, then I found this thread and suddenly all my work was already (very well) done =).

Kudos!

---

