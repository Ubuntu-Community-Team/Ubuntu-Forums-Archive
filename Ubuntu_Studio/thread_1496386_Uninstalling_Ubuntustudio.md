---
title: "Uninstalling Ubuntustudio"
date: 2010-05-29
forum: Ubuntu Studio
---

### Post by C.Raman on 2010-05-29
Hi,

Here's what I did while trying to uninstall ubuntu studio 9.10 and its put me in a pickle. Could someone please help me out.

1. I first removed the -rt kernel as explained here: [http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

2. With that done I removed all ubuntustudio packages using synaptic. That gave an error saying
 > E: ubuntustudio-audio: subprocess installed pre-removal script returned error exit status 13. So I tried apt-get -f install which installed ubuntustudio-controls again and repeated the above step giving the same error.

Could someone please help me out?

Thanks
Chirag

---

### Post by zettberlin on 2010-05-29
Uninstalling Ubuntu Studio is complicated at best if not impossible - and there is nothing surprising about that since US is a set of packages and settings interwoven into Ubuntu.

It should be absolutely no problem though, to install one of the other flavours of Ubuntu and thus overwrite the UbuntuStudio-Installation.

So, if you install ubuntu-desktop or kubuntu-desktop, the Ubuntu Studio-Settings should be gone. You may or may not want to uninstall the packages that came with Ubuntu Studio such as the rt-kernel, its wallpapers, themes and apps like Denemo, Genpo and the like.
At the other hand: hd-storage is cheap nowadays and nerves are precious ;-)
So as long as the packages are just installed and not started, they will silently sit in the menu and do no harm.

Only timidity should always be uninstalled since it acts as a server eating cycles in the background.

---

### Post by C.Raman on 2010-05-30
Ah, so Ive got to live with it :) But dont the wide array of unnecessary applications take up precious space? Uhm if I upgrade to lusty linx wont the packages get overwritten? If not, there is actually no way to start over with a pristine lusty install?

---

### Post by sgx on 2010-05-30
> **C.Raman said:**
> Ah, so Ive got to live with it :) But dont the wide array of unnecessary applications take up precious space? Uhm if I upgrade to lusty linx wont the packages get overwritten? If not, there is actually no way to start over with a pristine lusty install?

Hi, I usually use synaptic to remove the undesired apps, and useless firmware. Once you are familiar with things, a new release is a good time to do a fresh install based on your findings. The studio collection is
not large, so if you use nautilus to view and to sort /usr/bin by size,
you'll see which of the apps you don't actually use, that might be large enough to warrant their removal. But there is little point unless you made your root partition too small, in which case you should repartition, and do a proper install, with a separate  /home partition, so future reinstalls can preserve your settings by not formatting  /home next time around.

I do 12 gig for root partition
double the ram amount for the swap partition,
and all but 300 meg of the rest, for /home
The 300 meg is for an emergency rescue distribution install.

Configure synaptic to save newly downloaded files in its cache,
and burn them to media, a hedge against future bad luck.

Another reason not to uninstall, is someone is always finding new
ways to use and do things, and sooner or later, your needs, and skills will cross paths with new information, well worth a hundred meg of apps
you haven't used yet :) It happens to me on a regular basis.
Cheers

---

### Post by C.Raman on 2010-05-30
Hey thanks for the reply, but Im afraid I didnt understand it completely :-k New to ubuntu and linux..Could you please elaborate a bit? Even if i dont uninstall there's got to be something i can do to resolve the dependancy issue right? If its giving an error ive got to at least fix that..

---

### Post by sgx on 2010-05-30
> **C.Raman said:**
> Hey thanks for the reply, but Im afraid I didnt understand it completely :-k New to ubuntu and linux..Could you please elaborate a bit? Even if i dont uninstall there's got to be something i can do to resolve the dependancy issue right? If its giving an error ive got to at least fix that..

When I get an odd problem, it is always better to reinstall. Linux is too
complex, and linux distributions are always in rolling alpha/beta, regardless of how the devs may label or market their efforts. I can happily accept that.
It is what it be.

So ask yourself what you need, and look at what you have. You need to create art, and you have a computer, a hard drive, a linux you can install, and an existing linux that has gone bad. Which one do you want
to get rid of? ;)

The road ahead branches 3 ways.
1. Do you have a separate /home partition now?
2. Do you have different install media, or fast download ability?
3. Are you flexible?
Partitioning in linux installers is easy, but backup your data, its all
a chalkboard after that, nothing is carved in stone
 
Delete all your partitions (not windows partitions, unless you are
willing and able to do without!) 

New partitions need 

a size
a type of filesystem
a mountpoint  (its sort of a nikname the filesystem will recognize)

Arrow widgets or sliders, or numeric entry, are used for choosing size

You need a root partition, its mountpoint is shown as a single right-slash  /

The filesysytem will be ext3

The size 12 gig if your drive is at least 20 gig

---------------------------------------------------------------------
You need a swap partition, and swap will be its mountpoint

swap will also be its filesystem, it may be an odd color on the gui

size = double the computers ram

---------------------------------------------------------------------
You need a /home partition,   /home will be its mountpoint

The filesystem will be ext3

Its size will be 'what is still left'

(If your hardisk is 40 gig or more, leave a few hundred meg unallocated,
in the very rare event a professional data rescue was needed) Your choice
------------------------------------------------------------------------
Now what linux versions are at your disposal? The new ones are almost
always a train wreck that takes a few months to fix. So for someone new
to this, last years stable version has high priority, while not locking you out of certain new and excellent individual softwares you can still use in the stable linux.

I'll assume you have ubuntu 9.10, you've installed with a separate /home
partition, at your next reinstall, be sure to choose not to format it. Its probably the default setup, when the installer finds extra partitions, to make YOU issue the order to format them. So don't :)

What to install? Assuming you'll create, record and play your music,

ardour, audacity, and timemachine for recording/editing

qjackctl, jackd, qtractor, and patchage to connect/control instruments,
hardware, and software

Hydrogen to make drum parts, and rythmic sequences of sampled instruments

zynnadsubfx and phasex two excellent and deep synthesizers.

ladspa and all the ladspa fx you find, tap, vco, swf, 

jackrack, a gui to hold them (audacity will also place them in its menu)

I would focus your efforts on setting up jackd/qjackctl, then using them
to connect zynaddsubfx to the recorder app 'timemachine'. Record some fine new music, then use audacity to import the timemachine  w64 files for editing and conversion to mp3, wav, and flac formats

For playback, vlc, xine, and mplayer, will all play audio and video.

Cheers

---

### Post by C.Raman on 2010-05-30
Thanks you so much for the detailed reply :) Really helps a newbie like me..

---

