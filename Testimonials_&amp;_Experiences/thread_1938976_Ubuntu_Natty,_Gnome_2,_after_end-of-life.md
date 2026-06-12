---
title: "Ubuntu Natty, Gnome 2, after end-of-life"
date: 2012-03-10
forum: Testimonials &amp; Experiences
---

### Post by fritzman on 2012-03-10
I abandoned MS Windows in 2003 and haven't looked back.  I bounced around quite a bit, and settled on Ubuntu 9.04, and upgraded progressively until 11.10 arrived.  Choke!  Gasp!  

I'm sure that I could, eventually, get used to Ubuntu Unity.  Perhaps, after enough time passed, I suppose I might eventually grow to like it.  And, I suppose that I could, eventually, get used to Gnome 3, and, perhaps, even grow to like it as well.
However, my wife and I share the one computer that we have.  She hates computers, and has just learned to navigate around the Internet with Firefox pretty well, and can handle her email very well with Thunderbird.  And she can use Quicken 2009, which we have installed using CrossOver by Code Weavers.  On occasion, she can even use Libreoffice.  The three week period during which we both attempted to learn our way around Unity, and to cope with Gnome 3 was excruciating for both of us.
So, I decided that we would convert back to Ubuntu 11.04 &#8220;Natty!&#8221;  And we have decided to stay with &#8220;Natty&#8221; just as long as we possibly can, only upgrading when and if there is no other choice.  

What follows is my plan for doing this.  I must offer this disclaimer.  This is NOT recommended officially, and, when &#8220;Natty&#8221; reaches end-of-life this October 2012, anyone who does this will be completely without support.  We understand this.  If you do this, you too must understand and accept this.

I learned how to build, using git, the upstream kernels for both Oneiric, and Precise, and run them on Natty.  The guide found here [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) and this one as well, [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)  .  And this guide is also very interesting.  It worked using the Oneiric kernel, but choked using the Precise kernel.  [http://tiagohillebrandt.eti.br/blog/2011/09/installing-kernel-3-0-via-ppa-on-ubuntu-11-04-natty-narwhal/](http://tiagohillebrandt.eti.br/blog/2011/09/installing-kernel-3-0-via-ppa-on-ubuntu-11-04-natty-narwhal/)

I experienced problems with installing the .deb packages after the build because I was using the Nvidia driver.  Reverting back to the Nouveau driver actually required that I re-install Natty from scratch.  I never did figure out where the offending Nvidia residual files were lurking, but several attempts resulted in enough frustration for me to just bag that method completely, and install from scratch.
From that point on, however, everything has gone quite smoothly.  I have discovered that I can keep all the programs which we actually use, Libreoffice, Firefox, Thunderbird, CrossOver, and VirtualBox up-to-date from source, and not rely on upgrades from Ubuntu after Natty is put to rest.  And, combined with the ability to keep the most important part of this project, the kernel, up-to-date makes us fairly comfortable that we can go on with Natty for quite some time.  Perhaps Ubuntu will have understood by then that there are many folks like us who don't have and probably won't have the cute little hand-held devices that Unity is designed to keep sync with.  Perhaps, as well, Gnome will have matured enough by then that we might feel comfortable using Gnome 3.  Perhaps!  Perhaps not!  Time will tell, I suppose.   I'm 69.  Maybe I'll just keep using Natty till I drop.

$ uname -a
Linux uglybox 3.2.6-natty-precise+ #1 SMP Tue Mar 6 15:55:27 MST 2012 x86_64 x86_64 x86_64 GNU/Linux

$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
nls_iso8859_1          12713  3 
udf                    93513  1 
crc_itu_t              12707  1 udf
nls_cp437              16991  3 
vfat                   21575  3 
fat                    61194  1 vfat
binfmt_misc            17456  1 
pci_stub               12622  1 
vboxpci                23190  0 
vboxnetadp             13382  0 
vboxnetflt             23435  0 
vboxdrv               286917  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_realtek   222648  1 
nouveau               766956  2 
snd_hda_intel          33209  2 
snd_hda_codec         122811  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96427  2 snd_hda_intel,snd_hda_codec
ttm                    76403  1 nouveau
joydev                 17412  0 
drm_kms_helper         42140  1 nouveau
drm                   236644  4 nouveau,ttm,drm_kms_helper
snd_seq_midi           13324  0 
usbhid                 46696  0 
snd_rawmidi            30374  1 snd_seq_midi
edac_core              53309  0 
ses                    17321  0 
edac_mce_amd           23414  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_algo_bit           13281  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19070  1 mxm_wmi
usblp                  18170  0 
snd_seq                61397  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29396  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19176  1 nouveau
snd                    68188  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
enclosure              15217  1 ses
hid                    99102  1 usbhid
psmouse                81578  0 
i2c_nforce2            13013  0 
ppdev                  17069  0 
k10temp                13119  0 
parport_pc             32727  1 
serio_raw              13211  0 
lp                     17825  0 
parport                46251  3 ppdev,parport_pc,lp
usb_storage            53285  4 
uas                    17815  0 
pata_jmicron           12747  0 
ahci                   25720  2 
forcedeth              63068  0 
libahci                26984  1 ahci
pata_amd               14127  0 
sata_nv                31786  0 

owa

---

### Post by Version Dependency on 2012-03-10
> **fritzman said:**
> Maybe I'll just keep using Natty till I drop.

Or you could use the [Gnome Classic session]("http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html") in the upcoming 12.04 LTS.

---

### Post by fritzman on 2012-03-10
From all that I could gather about this, Clear-looks is still not available, and there are some other issues that we weren't happy with which I can't remember off hand.  Does this latest fix address the Clear-looks issue?

owa

---

### Post by Myrddin Emrys on 2012-03-10
The MATE desktop project allows you to install the Gnome 2 desktop (renamed and updated) on 11.10, and will work with 12.04:

[http://mate-desktop.org/](http://mate-desktop.org/)
[http://wiki.mate-desktop.org/download#ubuntu](http://wiki.mate-desktop.org/download#ubuntu)

Isn't this much less work than downgrading to a release that will stop receiving updates for everything else later in the year?

Edit: I'm using MATE with Clearlooks.

---

### Post by fritzman on 2012-03-10
Thanks, both, for your replies.  I just might try using Mate.  Maybe I'll do an upgrade on a separate partition to Oneiric, and give Mate a try.  I should probably spend some time with Becky before I dive into another project, as she often refers to the computer as "The ****!"  (Oooops!  Think of a word starting with S, which refers to a woman of ill-repute!)
But this is definitely worth taking a shot at.
Thanks, again.

owa

---

### Post by Myrddin Emrys on 2012-03-10
One other thing I'd suggest is installing a test copy of (e.g.) 11.10 in a VirtualBox VM. I've done most of my experimenting with alternative desktops this way - if you don't like a particular setup, you can very quickly and easily roll back to the previous version and try again (maybe with Xfce, or Cinnamon).

---

### Post by 3rdalbum on 2012-03-11
I don't know about Clearlooks having any issues. Gnome 3 is GTK 3, so it can't use old themes. However I think having a different set of window and control colours is a pretty small change to adjust to, if you install Gnome Session Fallback (also known as Gnome Classic).

Your current workaround won't last much longer; it becomes progressively harder to get new software working on older distros as time goes by, due to library changes and dependencies on newer versions of system utilities.

Unity and Gnome 3 are good environments if you don't mind a week of refamiliarising yourself. More advanced than Gnome 2. More practical features. You can potentially run Unity on a touchscreen device, but it's also a classical Windows Menus Pointer desktop; Gnome 2 just couldn't be both of those things, and it's interesting to note that neither can Windows 8 (it's their touhscreen phone UI on a bigger screen, with every program maximised).

---

### Post by mastablasta on 2012-03-12
I think clearlooks or very similar them is in Xubuntu.

---

### Post by VoodooLoveDog on 2012-03-15
If you dig on Gnome2 like a lot of us do, then check out either Mate (which was mentioned) or Cinnamon 1.3.1 (which is based off of Gnome3).

The problem with both of the desktops above is that they are both under heavy development right now and are fairly buggy. There is also a way to make Gnome fallback behave similar to Gnome2 in this article:

[http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/](http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/)

I'm not sure which route I'm heading now. I've got about 2 months to decide. However, I think like many of us, I'll be jumping ship to LinuxMint.

---

### Post by click4851 on 2012-03-15
or heck load Mint, all the parts of Ubuntu/Debian you like, with out the parts you don't.

---

### Post by rmayer32 on 2012-03-16
Mint is always a good remedy but really, Unity and Gnome 3 aren't bad at all. Once you get the hang of it anyway.

---

