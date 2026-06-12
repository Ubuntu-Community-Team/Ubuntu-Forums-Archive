---
title: "Digigram VX882 HR Driver"
date: 2014-09-27
forum: Ubuntu Studio
---

### Post by patrickfrog on 2014-09-27
Hello eneryone,

I recently aquired a Digigram VX882 HR PCI soundcard to use in a studio computer I am building.  These cards are designed for broadcast use and have alarge array of inputs and outputs.  I contacted Digigram to get the drivers for the card and they directed me to this site: [http://www.alsa-project.org/main/index.php/Matrix:Module-pcxhr](http://www.alsa-project.org/main/index.php/Matrix:Module-pcxhr).

I have attempted to follow all of the instructions listed here, however, as I have done further research, it appears that these drivers are already embedded into Ubuntu Studio.  This issue is, they are not working.

I "verified" that the dirvers are installed by running the command **lsmod**:
cuse                   13445  3 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395387  10 bnep,rfcomm
nvidia              11334886  40 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          52306  6 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
**snd_pcxhr              56745  0 **
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102040  3 snd_pcxhr,snd_hda_codec,snd_hda_intel

As you can see, the driver appears to be installed and the card is recognized because this module disaapears when the card is unplugged.


I first attempted to figure out if the device is recognised at all by running the **lspci** command.  The soundcard appears as the following:
[B]
01:0a.0 Multimedia audio controller: PLX Technology, Inc. PCI9656 PCI <-> IOBus Bridge (rev 01)[/B]

I verified that this was the correct device by restarting the computer without the card plugged in.  I am unsure why this card is listed as PLX.  According to most websites, I then should be able to use **alsamixer** to control the card.  However, when the card is plugged in, I receive this message: 
[B]
cannot open mixer: No such file or directory[/B]

This does not occur when the card is unplugged.

If anyone has a clue to what is going on, your advice would be appreciated.  If I am incorrect about the drivers being installed already and you know how to get them working pleas share.  If you need any more information, just ask and hopefully I will be able to provide it.

Thanks in advance,
Patrick

---

### Post by tgalati4 on 2014-09-27
What version of Ubuntu?

Open a terminal:

```
uname -a
cat /etc/issue
lsb_release -a

```

What version of the module?

> tgalati4@Mint14-Extensa ~ $ modinfo snd_pcxhr
filename:       /lib/modules/3.5.0-51-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
license:        GPL
**description:    Digigram pcxhr 0.9.6**
author:         Markus Bollinger <bollinger@digigram.com>, Marc Titinger <titinger@digigram.com>
firmware:       pcxhr/dspd222.d56
firmware:       pcxhr/dspb924.b56
firmware:       pcxhr/dspe924.e56
firmware:       pcxhr/xlxc924.dat
firmware:       pcxhr/xlxc222.dat
firmware:       pcxhr/dspd1222.d56
firmware:       pcxhr/dspb1222e.b56
firmware:       pcxhr/dspb1222hr.b56
firmware:       pcxhr/xlxc1222e.dat
firmware:       pcxhr/xlxc1222hr.dat
firmware:       pcxhr/dspd882.d56
firmware:       pcxhr/dspb882e.b56
firmware:       pcxhr/dspb882hr.b56
firmware:       pcxhr/dspe882.e56
firmware:       pcxhr/xlxc882e.dat
firmware:       pcxhr/xlxc882hr.dat
firmware:       pcxhr/xlxint.dat
srcversion:     66740984A22CEE7D37A6BC5
alias:          pci:v000010B5d00009056sv00001369sd0000BF21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BF01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BB21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BB01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BC21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BC01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BD21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BD01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BA21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BA01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B721bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B621bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B521bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B421bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B701bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B601bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B501bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B401bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B321bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B221bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B121bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B021bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B301bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B201bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B101bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B001bc*sc*i*
depends:        snd,snd-pcm,snd-page-alloc
intree:         Y
vermagic:       3.5.0-51-generic SMP mod_unload modversions 
parm:           index:Index value for Digigram pcxhr soundcard (array of int)
parm:           id:ID string for Digigram pcxhr soundcard (array of charp)
**parm:           enable:Enable Digigram pcxhr soundcard (array of bool)**
parm:           mono:Mono capture mode (default is stereo) (array of bool)


Make sure it is enabled using a switch or turning off the onboard sound in BIOS.

---

### Post by patrickfrog on 2014-09-27
Thanks for the quick reply.  Here is the information about my system you requested:

```

Linux Patrick-Ubuntu-Studio 3.13.0-36-lowlatency #63-Ubuntu SMP PREEMPT Wed Sep 3 21:56:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu 14.04.1 LTS \n \l

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

```

patrick@Patrick-Ubuntu-Studio:~$ modinfo snd_pcxhr
filename:       /lib/modules/3.13.0-36-lowlatency/kernel/sound/pci/pcxhr/snd-pcxhr.ko
license:        GPL
description:    Digigram pcxhr 0.9.6
author:         Markus Bollinger <bollinger@digigram.com>, Marc Titinger <titinger@digigram.com>
firmware:       pcxhr/dspd222.d56
firmware:       pcxhr/dspb924.b56
firmware:       pcxhr/dspe924.e56
firmware:       pcxhr/xlxc924.dat
firmware:       pcxhr/xlxc222.dat
firmware:       pcxhr/dspd1222.d56
firmware:       pcxhr/dspb1222e.b56
firmware:       pcxhr/dspb1222hr.b56
firmware:       pcxhr/xlxc1222e.dat
firmware:       pcxhr/xlxc1222hr.dat
firmware:       pcxhr/dspd882.d56
firmware:       pcxhr/dspb882e.b56
firmware:       pcxhr/dspb882hr.b56
firmware:       pcxhr/dspe882.e56
firmware:       pcxhr/xlxc882e.dat
firmware:       pcxhr/xlxc882hr.dat
firmware:       pcxhr/xlxint.dat
srcversion:     A87A9E95568565A60066EF9
alias:          pci:v000010B5d00009056sv00001369sd0000D321bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000D221bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D301bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D201bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000D121bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000D021bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D101bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D001bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BF21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BF01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BB21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BB01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BC21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BC01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BD21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BD01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BA21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BA01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B721bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B621bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B521bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B421bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B701bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B601bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B501bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B401bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B321bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B221bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B121bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B021bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B301bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B201bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B101bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B001bc*sc*i*
depends:        snd,snd-pcm,snd-page-alloc
intree:         Y
vermagic:       3.13.0-36-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7C:2C:CA:CB:65:45:21:D7:4E:48:54:56:A8:BD:C0:DE:11:AF:70:5D
sig_hashalgo:   sha512
parm:           index:Index value for Digigram pcxhr soundcard (array of int)
parm:           id:ID string for Digigram pcxhr soundcard (array of charp)
parm:           enable:Enable Digigram pcxhr soundcard (array of bool)
parm:           mono:Mono capture mode (default is stereo) (array of bool)

```

---

### Post by patrickfrog on 2014-09-27
Thanks for the quick reply.  Here is the information about my system you requested:

```

Linux Patrick-Ubuntu-Studio 3.13.0-36-lowlatency #63-Ubuntu SMP PREEMPT Wed Sep 3 21:56:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu 14.04.1 LTS \n \l

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

```

patrick@Patrick-Ubuntu-Studio:~$ modinfo snd_pcxhr
filename:       /lib/modules/3.13.0-36-lowlatency/kernel/sound/pci/pcxhr/snd-pcxhr.ko
license:        GPL
description:    Digigram pcxhr 0.9.6
author:         Markus Bollinger <bollinger@digigram.com>, Marc Titinger <titinger@digigram.com>
firmware:       pcxhr/dspd222.d56
firmware:       pcxhr/dspb924.b56
firmware:       pcxhr/dspe924.e56
firmware:       pcxhr/xlxc924.dat
firmware:       pcxhr/xlxc222.dat
firmware:       pcxhr/dspd1222.d56
firmware:       pcxhr/dspb1222e.b56
firmware:       pcxhr/dspb1222hr.b56
firmware:       pcxhr/xlxc1222e.dat
firmware:       pcxhr/xlxc1222hr.dat
firmware:       pcxhr/dspd882.d56
firmware:       pcxhr/dspb882e.b56
firmware:       pcxhr/dspb882hr.b56
firmware:       pcxhr/dspe882.e56
firmware:       pcxhr/xlxc882e.dat
firmware:       pcxhr/xlxc882hr.dat
firmware:       pcxhr/xlxint.dat
srcversion:     A87A9E95568565A60066EF9
alias:          pci:v000010B5d00009056sv00001369sd0000D321bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000D221bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D301bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D201bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000D121bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000D021bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D101bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000D001bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BF21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BF01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BB21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BB01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BC21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BC01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BD21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BD01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BA21bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000BA01bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B721bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B621bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B521bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B421bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B701bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B601bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B501bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B401bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B321bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B221bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B121bc*sc*i*
alias:          pci:v000010B5d00009056sv00001369sd0000B021bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B301bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B201bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B101bc*sc*i*
alias:          pci:v000010B5d00009656sv00001369sd0000B001bc*sc*i*
depends:        snd,snd-pcm,snd-page-alloc
intree:         Y
vermagic:       3.13.0-36-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7C:2C:CA:CB:65:45:21:D7:4E:48:54:56:A8:BD:C0:DE:11:AF:70:5D
sig_hashalgo:   sha512
parm:           index:Index value for Digigram pcxhr soundcard (array of int)
parm:           id:ID string for Digigram pcxhr soundcard (array of charp)
parm:           enable:Enable Digigram pcxhr soundcard (array of bool)
parm:           mono:Mono capture mode (default is stereo) (array of bool)

```

---

### Post by patrickfrog on 2014-12-14
Does anyone have any ideas why this is not working for me?  It has been a little while.

Thanks,
Patrick

---

### Post by tgalati4 on 2014-12-15
I have a couple of Digigram streaming products, but not that particular sound card.  I know with other high-end sound cards,  you need to make software patches using the configuration files, otherwise you get no sound.  

Have you tried setting up the configuration as described:  [http://www.alsa-project.org/main/index.php/Matrix:Module-pcxhr](http://www.alsa-project.org/main/index.php/Matrix:Module-pcxhr)

---

### Post by patrickfrog on 2014-12-15
Hi,

Actually, what you mentioned above is part of the problem.  I have attemptedt to follow the instructions given by ALSA.  It appears that Ubuntu Studio comes pre-installed with the pcxhr module however it does not detect the device.  I thought this may be an issue with the version that comes with Studio so I attempted to recomiple ALSA as suggested (I actually contacted Digigram and they sent me to the same link).  The problem is, I receive the following output when running the configuration script:

```

checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/patrick/git/alsa-driver-1.0.9
checking cross compile... 
checking for directory with kernel source... /lib/modules/3.13.0-43-lowlatency/build
checking for directory with kernel build... 
checking for kernel version... The file /lib/modules/3.13.0-43-lowlatency/build/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/3.13.0-43-lowlatency/build).
make all-deps
make[1]: Entering directory `/home/patrick/git/alsa-driver-1.0.9'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/patrick/git/alsa-driver-1.0.9'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/home/patrick/git/alsa-driver-1.0.9/acore'
Makefile:6: /home/patrick/git/alsa-driver-1.0.9/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/home/patrick/git/alsa-driver-1.0.9/Makefile.conf'.  Stop.
make[1]: Leaving directory `/home/patrick/git/alsa-driver-1.0.9/acore'
make: *** [install-modules] Error 1

```

It appears that anything having to do with the kernel's version.h header file is missing in Ubuntu Studio.  I have attempted to install the header packages as suggested by Google, however I still do not end up with the version.h file.

What is odd, is that the pcxhr driver is technically operating according to lsmod, but the device is not recognised by the driver.  I have even tried reloading the module and re-installing the entire OS with the card installed to no avail.

Patrick

---

### Post by tgalati4 on 2014-12-15
Does the card work under Windows?  It's possible that it is defective.  Usually, bad hardware does not get detected, nor are there any error messages.  If you are recompiling alsa (which shouldn't be needed) you need *build-essential *installed.

---

### Post by patrickfrog on 2014-12-15
I just plugged it into a Windows 7 computer and installed the drivers.  The device is recognized right away and workds perfectly for recording.  When plugged into the Studio computer, issuing lspci shows that the device is there and recgnized, however the driver seems to not attach to the pci device.  If there some configuration file I need to edit?

Thanks,
Patrick

---

### Post by tgalati4 on 2014-12-16
```
cat /etc/modules.conf
```

---

### Post by patrickfrog on 2014-12-16
No such file or directory

---

### Post by tgalati4 on 2014-12-16
Put stuff in it.

---

### Post by patrickfrog on 2014-12-16
I receive a "No such file or directory" error. It appears I do not have a module config file.

---

### Post by patrickfrog on 2014-12-16
Parden my ignorance (and duplicate reply), but what "stuff" would actually accomplish the goal of getting the drivers to recognize the attached card?

Thanks

---

### Post by patrickfrog on 2014-12-16
I may have discovered part of the problem.  I looked at my kernal logs during boot time and there is one section which appears to be causing a problem:

```

Dec 14 21:27:36 PATRICK-STUDIO kernel: [   12.125038] snd_pcxhr 0000:01:0a.0: Direct firmware load failed with error -2
Dec 14 21:27:36 PATRICK-STUDIO kernel: [   12.125042] snd_pcxhr 0000:01:0a.0: Falling back to user helper
Dec 14 21:27:36 PATRICK-STUDIO kernel: [   12.125589] pcxhr: can't load firmware pcxhr/xlxint.dat
Dec 14 21:27:36 PATRICK-STUDIO kernel: [   12.126376] snd_pcxhr: probe of 0000:01:0a.0 failed with error -2

```

I am not sure what "error -2" is referring to but I will take a look at the file it mentions.

---

### Post by patrickfrog on 2014-12-19
Hi again,

Does anyone out there now what the above error could be caused by?  I end up contacting the people who develop ALSA to see if they have any advice.

Thanks,
Patrick

---

### Post by tgalati4 on 2014-12-19
The alsa link in the previous post lists the settings that need to be put in /etc/modules.conf

Perhaps your xlxint.dat file is broken or there is a bug preventing it from loading.  [http://modules.libres.ch/browse/linux/v2.6.31/x86_64/snd-pcxhr/](http://modules.libres.ch/browse/linux/v2.6.31/x86_64/snd-pcxhr/)

> tgalati4@Mint17 ~ $ locate snd-pcxhr
/lib/modules/3.13.0-24-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko

It looks like the firmware is part of the *snd-pcxhr* driver:

```
modinfo snd-pcxhr
```

> tgalati4@Mint17 /lib/modules/3.13.0-24-generic/kernel/sound/pci/pcxhr $ ls -la
total 100
drwxr-xr-x  2 root root  4096 Dec 19 12:28 .
drwxr-xr-x 27 root root  4096 Dec 19 12:28 ..
-rw-r--r--  1 root root 92548 May  2  2014 snd-pcxhr.ko


It should be 92,548 bytes.

---

### Post by patrickfrog on 2014-12-20
Ok, for anyone else who has this same problem on a Ubuntu Studio machine, it appears that the kernal driver is installed by default but not the firmware; go figure.  To fix the issue, download the alsa-firmware source and copy the contents of the pcxhrloader folder into /lib/firmware/pcxhr (you will need to create the pcxhr folder and it **cannot** be named pcxhrloader).  Once this is done, reload the module using:
```

sudo modprobe -r snd-pcxhr
sudo modprobe -v snd-pcxhr

```
Once the module was reloaded, the sound devices appeared in alsa!

Big thanks to tgalati4 for all of the help!

One last (hopefully quick) question.  The soundcard I am using has 8 inout channels and 8 output channels.  In JACK, this card appears as 4 different devices each with two inputs/outputs.  Is there a way to make JACK use the entire sound card instead of only a quarter of it so I may take advantage of multitrack stuff?

Thanks again,
Patrick

---

### Post by tgalati4 on 2014-12-20
I don't have that particular sound card.  So JACK is presenting 4 stereo inputs and 4 stereo outputs?  That is the same as 8 in and 8 out.  I haven't used JACK in a while, but to use all of the channels, you typically need to make patches.  An example is making patches in *rosegarden*.  [https://help.ubuntu.com/community/UbuntuStudio/JackQuickStart](https://help.ubuntu.com/community/UbuntuStudio/JackQuickStart)

Try clicking on the patchbay button in *qjackctl* and making some connections between channels.  You should be able to use all 8 inputs and 8 outputs, but latency will increase as you use more channels.  Latency is not a problem, until it becomes a problem.

---

### Post by patrickfrog on 2015-01-13
Hello again,

I'm sorry that it has been a while since my last reply.  The curious thing about this sound card, or at least the was it is handled by ALSA, is that it appears as four individual hardware devices (8 channels in all since each device is stero). This is a problem if I want to use the card for multitrack recording and playback since jack and any other program requires that you select a device.
[IMG]http://www.mediafire.com/view/96ppbno4wxe4894/fr_834_size400.jpg[/IMG]
Image URL: [http://www.mediafire.com/view/96ppbno4wxe4894/fr_834_size400.jpg](http://www.mediafire.com/view/96ppbno4wxe4894/fr_834_size400.jpg)

The above image (sorry for the quality, I was not able to take a screen shot for some reason) shows what jack sees. There are four individual hardware devices that I cannot use all at once.  I read about pseudo devices and am wondering if that work work in this situation. Variances in the clock are not an issue because it really is one physical device with the same clock.  If you have any ideas, they would be greatly appreciated.

Thanks again,
Patrick

---

### Post by tgalati4 on 2015-01-13
Yes, it does appear that each stereo pair is treated as a separate device.  

Some things to try:  [http://jackaudio.org/faq/multiple_devices.html](http://jackaudio.org/faq/multiple_devices.html)

---

### Post by patrickfrog on 2015-01-18
Hello,

I read the information on the link you gaveme and attempted to constuct a pseudo device containing all of the stereo pairs.  When running an aplay-L command, I see the device listed (I am not sure if it is correct however), but I still cannot use the device in Jack.

My .asoundrc file:
```

pcm.pcxhrpseudo {
    type multi;
    slaves.a.pcm hw:VX882HR0
    slaves.a.channels 2;
    
    slaves.b.pcm hw:VX882HR1
    slaves.b.channels 2;
    
    slaves.c.pcm hw:VX882HR2
    slaves.c.channels 2;
    
    slaves.d.pcm hw:VX882HR3
    slaves.d.channels 2;

    bindings.0.slave a;
    bindings.0.channel 0;
    bindings.1.slave a;
    bindings.1.channel 1;

    bindings.2.slave b;
        bindings.2.channel 0;
        bindings.3.slave b;
        bindings.3.channel 1;

    bindings.4.slave c;
        bindings.4.channel 0;
        bindings.5.slave c;
        bindings.5.channel 1;

    bindings.6.slave d;
        bindings.6.channel 0;
        bindings.7.slave d;
        bindings.7.channel 1;

}

ctl.pcxhrpseudo {
    type hw
    card 6
}

```

I assigned the card as hw 6 simply to keep out out of the range of the other devices.


I am not sure whythis is not working since I followed the instructions according to Jack.  If I am making a stupid mistake, please tell me.

Thanks,
Patrick

---

### Post by patrickfrog on 2015-01-18
Hi,

Never mind, I just figured it out.  The pseudo device does not appear as a traditional device, but if you simply type it in manually as the device you wish to use, it works fine.

Patrick

---

### Post by tgalati4 on 2015-01-19
Let us know how well your multitrack recording works with this arrangement.

---

