---
title: "Envy24cntrol stuck on s/pdif output"
date: 2011-05-14
forum: Ubuntu Studio
---

### Post by Jay105 on 2011-05-14
hi guys  having some trouble setting up my terratec dmx6fire as posted on another thread. having gone into envy24control and pressed on a few things, my output is now stuck on s/pdif and i cannot change it back (under actual rate). ive noticed online that a few people have encountered this but no real solution has been posted.  ive removed asl-tools-gui, ive physically removed the card and started again. nothing works!  any help is appreciated

---

### Post by sgx on 2011-05-14
do you have this text file?

/home/username/envy24control/profiles.conf

If so, I would delete it and reboot. You can create several profiles later, for different audio needs.

You can also use alsamixergui, in its gui, there should be two groups of controls for DAC and two DAC1. 2 pairs of sliders for DAC, and 2 pairs for DAC1. Click and drag the right side of these pairs, to move
the volume up or down. All four (both pairs) will move at once.

Arrow keys and the tab key can also be used to navigate this gui.

Cheers

Did you use synaptic to install and remove alsa-tools-gui?
There is a version here that may be better/newer/working
if the above ideas don't help. Uninstall current version using synaptic,, then download and this one

[http://packages.debian.org/unstable/sound/alsa-tools-gui](http://packages.debian.org/unstable/sound/alsa-tools-gui)

and install with

sudo dpkg -i alsaxxxxxx.deb

Cheers

---

### Post by Jay105 on 2011-05-15
hi  unfortunately, while being excellent suggestions, nothing has worked for me. i may do a purge of all studio applications and start from scratch and see if this helps.

---

### Post by sgx on 2011-05-15
updated version of envy24control:

[http://code.google.com/p/mudita24/](http://code.google.com/p/mudita24/)



Hi, the lsmod command output should include either

snd_ice1712  or snd_ice1724 kernel modules used on envy24 chipsets

If it does, and you still have no luck, you can try to use the
other module, so these two commands would replace an existing 1712 with 1724

sudo rmmod snd_ice1712   then
modprobe snd_ice1724

(Maybe request a debian package of Mudita, in the Falk PPA thread?)

---

### Post by sgx on 2011-05-15
Mudita24 is included in AVLinux 4.2, might be good
to test this audio distro by live dvd, or install on a spare drive, or usbstick.

When AVlinux is booted, you can set synaptic preferences to save your downloaded files in the cache, uninstall and reinstall mudita, thus caching it, then copy it to your current setup, and install it manually with
sudo dpkg -i mudita24xxx.deb

/var/cache/apt/archives or similar, is where such files reside

[http://bandshed.net/AVLinux.html](http://bandshed.net/AVLinux.html)
[http://www.remastersys.com/forums/index.php?board=19.0](http://www.remastersys.com/forums/index.php?board=19.0)

Cheers

---

### Post by cchhrriiss121212 on 2011-05-15
I found this a while ago, unfortunately I don't remember what I did to fix it, but I know I did not have to remove any packages or install any new ones.
I'm pretty sure I just deleted /home/chris/.config/envy24control then rebooted.

---

### Post by sgx on 2011-05-15
That's what one would think, mine is this, for a different
envy24 based card, just

[mixer]
stereo=true;false;false;false;false;false;false;false;false;false;false;false;false;false;false;false;false;false;false;false;

no mention of details, while the profiles.conf is like a .asoundrc

Maybe delete those two files,

/home/username/envy24control/profiles.conf
/home/username/.config/envy24control


then uninstall envy24 control,
run the ubuntu audio hardware configurator,
then reinstall envy24control

Cheers

---

### Post by RaumTrug on 2011-05-16
I've got an 2496 under 10.04 without pulseadio, and I can select s/pdif in under "master clock" and select one of the rates above it with no problems...is it that option that is stuck? is under "patchbay/router" an s/pdif input maybe selected as source for some output? the card is built to must run at rate of s/pdif input, if it is used anyhow. change the option(s) back to one of the pcm's, digital mix or h/w in's, and try to change rate again.

maybe you need to kill all applications using the pcm of the card, find the processes by doing "lsof | grep pcm"

if rate is still stuck, you might try something like:

```

amixer set Multi\ Track\ Internal\ Clock 44100

```with the _[COLOR=black]backslashes being important[/COLOR]_.

(edit, hmm could do "amixer set 'Multi Track Internal Clock' 44100", too...)

to bypass envy24control in ruling alsa. if I do so, envy24control just follows what rate I set. envy24control is just a specialised alsa-mixer, by the way, so uninstalling or deleting its profiles won't help, the settings are saved at lower levels in the alsa mixer interface. so an alsa reset, using the "alsa-utils" script might work, too (if amixer doesn't work).

if it still won't work, run the command "amixer" _without_ any parameters and show the output here :-P

---

