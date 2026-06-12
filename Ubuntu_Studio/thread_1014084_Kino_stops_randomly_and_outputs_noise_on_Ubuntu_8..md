---
title: "Kino stops randomly and outputs noise on Ubuntu 8.10"
date: 2008-12-17
forum: Ubuntu Studio
---

### Post by resander on 2008-12-17
I have about 50 AVI clips that need editing and merging. I have no previous experience of video editing, Googled and decided to try Kino.

Added and edited first clip and saved on disk and exited from kino. Then reentered and inserted another AVI after the first that had been edited. The two avis had merged and behaved as one. Edited the second part and exited.
Then reentered and played to end of progress bar where kino stalled and emitted a noise somewhat akin to a pneumatic drill compressor a few houses away. Exited from kino, but the noise continued. The only way to stop it was to reboot. On restarts, I could make kino hang with noise by stopping and restarting at random positions in the two combined avis.

I have read other kino posts and one user reported kino freezing and leaving pulseaudio in a loop (the noise). 
  
Is there a workaround for this? Or could another video editor do the job?

---

### Post by emacs on 2008-12-30
I had the same problem on my HP Pavilion laptop as well as Dell Latitude D630 laptop.  It happens on kino 1.3 that I installed using ubuntu 8.10 (64-bit Desktop version) as well as kino 1.3.1 that I compiled myself.

The problem is that after a few seconds of editing, the audio driver
seems crash with constant motor boat sound coming out of the speakers.
Nothing seems to silence this other than rebooting the OS.

The problem happens with cinelerra package that I installed using ubuntu packaging system as well as latest cinelerra that I compiled myself.

Given that the problem happens on multiple hardware, and multiple applicaitons, it seemed logical to suspect something common such as the audio driver.

I did many many hours of video editing with kino about a year ago using an earlier versions of ubuntu and kino using the same hardware.

So I compiled the latest ALSA driver and related files.
This solved the problem for me.  Although kino may crash once every few minutes, at least it does not hose the audio subsystem.  I can restart kino and continue video editing.  Following is what I did on my system
with Intel sound hardware.  YMMV.

#
# These are the steps I took to install the latest ALSA driver and
# related files onto my HP Pavillion DV6000 laptop running 64-bit
# Ubuntu 8.10.  Some of the steps are from ubuntuforums.org postings
# made by others about a year ago.  -rk 12/30/2008
#

# First step was to log off from the GUI, i.e., gdm.  This was to
# assure that the sound driver could be unloaded safely.  To do this,
# I went over to one of the consoles, i.e., Control-Alt-F1,
# then logged in as root. After that I shutdown GUI altogether, i.e.,
/etc/init.d/gdm stop

# Unload all sound drivers
# This is the step I read from ubuntuforums.org.
lsmod | grep snd |cut -d" " -f1 | xargs modprobe -r

# I did not do this, because it would have also removed ubuntu-desktop package.
# apt-get remove --purge alsa-base alsa-tools

# Make sure some of the necessary packages are installed
sudo apt-get install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev

# Back up current driver
tar -zcvf original-drivers.tgz /lib/modules/`uname -r`/kernel/sound

# Replace "username" here with your actual user name
USER=username

mkdir /home/$USER/alsa
echo "made /home/$USER/alsa dir"
cd /home/$USER/alsa

# Download the alsa related source files
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.18.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.18.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2)

# Unpack
tar xvf alsa-driver-1.0.18a.tar.bz2
tar xvf alsa-lib-1.0.18.tar.bz2
tar xvf alsa-utils-1.0.18.tar.bz2
tar xvf alsa-firmware-1.0.17.tar.bz2

# Install driver
cd alsa-driver-1.0.18a
make clean
make mrproper
./configure --with-oss=yes --with-cards=hda-intel 
make
make install

# Install alsa-lib
cd alsa-lib-1.0.18
make clean
./configure
make
make install

# Install alsa-utils
cd alsa-utils-1.0.18
./configure
make clean
make 
make install

# Install alsa-firmware
cd alsa-firmware-1.0.17
./configure
make clean
make 
make install

# Activate intel driver.  This applies only if you have an intel hardware.
modprobe snd-hda-intel

---

### Post by matth1j on 2008-12-31
Same problem, trying to edit raw DV files captured off a DV camcorder. The ALSA solution looks really complicated to me - I'm not sure if I should follow the exact same steps for my setup, and if not what I should do instead.

If there is a simpler solution (eg. use another application?) I would be interested to hear it.

Cheers
John
(Abit SG-95 mb with ALC883 audio)

---

### Post by mdrmike on 2009-05-29
found the answer to the kino audio bug... VERY simple solution.  

This little problem has been irking me for two Ubuntu releases... (8.10 & 9.04), but never quite enough to look into.  ;)

The detailed answer can be found at the Kino site: [http://www.kinodv.org/article/view/173/1/13/](http://www.kinodv.org/article/view/173/1/13/)

To summarize the post, open Kino and ...
> simply set the Audio Device to "/dev/dsp" in Kino's Preferences and then run Kino using the "padsp kino" command. You can edit your desktop menu item to make that permanent (or until your package gets upgraded :-/). 

to edit your menu item, 
right click on **applications** -> **edit menus** --> (find Kino menu icon) --> click **Properties** -> add **padsp** to beginning of line.  

works like a charm!

---

