---
title: "Line 6 podxt usb driver problems..."
date: 2008-05-12
forum: Ubuntu Studio
---

### Post by bobbyshane on 2008-05-12
I'm running Ubuntu Studio 8.04 Hardy with the 2.6.24-16-rt kernel. I have attempted to install the newest line6usb drivers for my Pod xt and am getting strange errors, I've tried installing 0.7.3 and 0.7.2 getting totally different errors when compiling them. I have already searched for the old podxt driver and it is not installed and I have also installed the linux headers and build essentials. Any Help would be appreciated. These are the errors I get:

When I try to compile 0.7.3 I get this: 
 
bobbyshane@bobslappy:~/line6usb/line6usb-0.7.3$ sudo make install 
make -C /lib/modules/2.6.24-16-rt/build SUBDIRS=/home/bobbyshane/line6usb/line6usb-0.7.3 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-rt' 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/audio.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/capture.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/control.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/driver.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/dumprequest.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/midi.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/midibuf.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/pcm.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/playback.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/pod.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.3/variax.o 
LD [M] /home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.o 
Building modules, stage 2. 
MODPOST 1 modules 
WARNING: "snd_pcm_period_elapsed" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_rawmidi_set_ops" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_card_disconnect" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_rawmidi_new" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_device_new" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_pcm_set_ops" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_rawmidi_transmit_peek" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_pcm_lib_free_pages" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_pcm_lib_ioctl" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_pcm_lib_malloc_pages" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_card_new" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_rawmidi_transmit_ack" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_ctl_new1" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_pcm_format_physical_width" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_card_free" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_card_register" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_pcm_new" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_ctl_add" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
WARNING: "snd_rawmidi_receive" [/home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko] undefined! 
CC /home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.mod.o 
LD [M] /home/bobbyshane/line6usb/line6usb-0.7.3/line6usb.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-rt' 
mkdir -p /lib/modules/2.6.24-16-rt/kernel/sound/usb 
cp line6usb.ko /lib/modules/2.6.24-16-rt/kernel/sound/usb 
mkdir -p /usr/bin 
cp *.sh *.pl /usr/bin 
/sbin/depmod -a 
/sbin/modprobe line6usb 
 
 
When I try to compile 0.7.2 I get this: 
 
bobbyshane@bobslappy:~/line6usb/line6usb-0.7.2$ sudo make install 
make -C /lib/modules/2.6.24-16-rt/build SUBDIRS=/home/bobbyshane/line6usb/line6usb-0.7.2 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-rt' 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.2/audio.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.2/capture.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.2/control.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.2/driver.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.2/dumprequest.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.2/midi.o 
CC [M] /home/bobbyshane/line6usb/line6usb-0.7.2/pcm.o 
/home/bobbyshane/line6usb/line6usb-0.7.2/pcm.c: In function ‘snd_pod_trigger’: 
/home/bobbyshane/line6usb/line6usb-0.7.2/pcm.c:39: error: implicit declaration of function ‘snd_pcm_group_for_each’ 
/home/bobbyshane/line6usb/line6usb-0.7.2/pcm.c:39: error: expected ‘;’ before ‘{’ token 
/home/bobbyshane/line6usb/line6usb-0.7.2/pcm.c:33: warning: unused variable ‘err’ 
/home/bobbyshane/line6usb/line6usb-0.7.2/pcm.c:32: warning: unused variable ‘s’ 
make[2]: *** [/home/bobbyshane/line6usb/line6usb-0.7.2/pcm.o] Error 1 
make[1]: *** [_module_/home/bobbyshane/line6usb/line6usb-0.7.2] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-rt' 
make: *** [default] Error 2 
bobbyshane@bobslappy:~/line6usb/line6usb-0.7.2$  

I would prefer to install 0.7.3 but will suffice with 0.7.2 if that error can be fixed. Thanks.

---

### Post by SynthesizersFTW on 2008-05-13
I could be wrong, but those functions look like they are from the ALSA driver libraries... do you have that installed yet?  You might need the sources (you can try getting them in Synaptic), then try it again.

I wasn't even aware Line6 had a linux driver for Podxt, hope you can get it running.

---

### Post by bikko on 2008-08-17
I recently ran into a VERY similar problem trying to compile the GadgetLabs WavePro 8/24 ALSA driver on Ubuntu 8.04 x86_64.

My solution was to build and run a custom mainline (NOT ubuntu/canonical) kernel with ALSA included. As far as I know, since the Ubuntu kernel does not have ALSA enabled in Hardy, building a kernel is the only way. (Whether I could get an Ubuntu kernel to build with ALSA, I do not know; I haven't really given more than a quick try yet.)

I'm including my post from [https://answers.launchpad.net/ubuntu/+question/35767](https://answers.launchpad.net/ubuntu/+question/35767) which details how I did this. A few steps are specific to the GadgetLabs driver (copying firmware files). However, the symlinking/copying steps at the end will probably be necessary for you, too.

Anyway, hope this is helpful! Let me know.

---------------------------------------

I finally got the GadgetLabs WavePro 8/24 ALSA driver to compile and insert on Ubuntu 8.04 (x86_64)! What's more, it plays and records sound! I have tested with Totem (playing mp3s) and Ardour/Jack (recording a track and playing it back).

I used this [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) for help with building the main line kernel. However, I had to fix a couple of things that came out broken in the linux-headers deb package that was generated after installing it.

I chose 2.6.24.7 as it seemed close to Ubuntu stock kernel... I'm guessing latest would work too, though. (I had tried 2.6.26.1 last week and thought it was too new, but I think now it was just showing the same two problems I had to fix with 2.6.24.7, so I may try to build 2.6.26 or 2.6.27 kernel soon too.)

Here's what I did. I'll try to keep the commands easily repeatable for others. (If you have multicore, make sure to change CONCURRENCY_LEVEL... building kernel + debs took my Athlon 64 3000+ 90 minutes...)

```
# First, pretty standard kernel building stuff
cd ~
mkdir kernel
cd kernel
wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.7.tar.bz2
tar xvjf linux-2.6.24.7.tar.bz2
cd linux-2.6.24.7
cp /boot/config-`uname -r` .config
make oldconfig

make menuconfig
```
Now we must enable ALSA in the kernel configuration.
Specifically, here are the settings I'm using. I'm not sure all of them are necessary (especially verbose procfs and dummy client).

```
Device Drivers --->
  Sound -->
    <M> Sound card support
    Advanced Linux Sound Architecture --->
      <M> Advanced Linux Sound Architecture
      <M> Sequencer support
      <M> Sequencer dummy client
      <M> OSS Mixer API
      <M> OSS PCM (digital audio) API
      [*] OSS PCM (digital audio) API
      [*] OSS Sequencer API
      [*] Support old ALSA API
      [*] Verbose procfs contents

```

```
# Now to actually make the kernel package
make-kpkg clean
CONCURRENCY_LEVEL=1 fakeroot make-kpkg --initrd
--append-to-version=-bikko kernel_image kernel_headers
cd ..
sudo dpkg -i linux-image-2.6.24.7-bikko_2.6.24.7-bikko-10.00.Custom_amd64.deb
sudo dpkg -i linux-headers-2.6.24.7-bikko_2.6.24.7-bikko-10.00.Custom_amd64.deb

sudo ln -sf /usr/src/linux-headers-2.6.24.7-bikko /usr/src/linux

# copy firmware
sudo mkdir /lib/firmware/2.6.24.7-bikko
sudo cp <wavepro src dir>/gl*_firmware.bin /lib/firmware/2.6.24.7-bikko/

# These next commands fix two problems which cause build errors
# with gl824 module... This is the part I figured out :)
sudo cp ~/kernel/linux-2.6.24.7/arch/x86/Makefile_64 /usr/src/linux/arch/x86/
sudo ln -sf /usr/src/linux/include
sudo ln -s asm-x86 asm
```

then building the driver worked. It's weird that when I built the
kernel package it botched the "asm" symlink and didn't include
Makefile_64! I had been getting "Makefile_64: No such file" errors and
similar errors for asm include files.

You will have to reboot into the new kernel of course before inserting the driver.

Note that any time you build a custom kernel, you pretty much lose restricted modules. I'll be working on trying to figure out how to get the nvidia driver back - for now I switched my xorg.conf to use the nv driver.

Good luck, everyone, and tell us how it goes!

---

