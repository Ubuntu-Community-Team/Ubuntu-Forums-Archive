---
title: "ALC892 No surround option Xubuntu 20.04"
date: 2020-02-10
forum: Ubuntu Development Version
---

### Post by montyadex on 2020-02-10
Chip ALC892 (hd audio 17h family model 00h-0fh) it's supposed to support 7.1 channels but in pulseaudio mixer i have no option to choose as previous versions, just analog stereo is present.
Motherboard: MSI B450M-A PRO MAX Gen1

I downloaded the driver from  realtek [https://www.realtek.com/en/component/zoo/category/pc-audio-codecs-high-definition-audio-codecs-software](https://www.realtek.com/en/component/zoo/category/pc-audio-codecs-high-definition-audio-codecs-software), and follow the instructions on this page  [https://community.linuxmint.com/tutorial/view/1236 to install the driver]("https://community.linuxmint.com/tutorial/view/1236") and follow the instruction on this page to install the driver.
I was missing flex and bison (after build-essential installation), and i got this error that i'm not skilled enough to understand to solve: 
after make command i got this error:
```
scripts/kconfig/conf  --syncconfig Kconfig
make[2]: *** No rule to make target 'arch/x86/tools/relocs_32.c', needed by 'arch/x86/tools/relocs_32.o'.  Stop.
make[1]: *** [arch/x86/Makefile:232: archscripts] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-12-generic'
make: *** [Makefile:167: compile] Error 2

```
It's a 2 yerars or more hardware so i suppose it was already supported from the kernel but looks like not.
I just need the ability to enable 4.0 surround system but i cannot install the realtek driver and i dunno what install from synaptic.
I should have enabled both sets of library (32 and 64 bit) after the installation of "steam runtime" that need 32 compatibility.
Thanks for any suggestion or to simply fix the problem natively as because this should be a really common hardware out there.
At your service for test some solution that will not force me to reinstall the os.
Thanks again

[update]
I wasn't able to get surround neither in windows 10 but after installed the motherboard driver  i had all options to get surround. 
Sadly MSI is not providing linux driver and i have no skill for reverse engineer that so hoping in some angel that is able to do this job i can only offer my time to test it.
(official realtek driver didn't provide surround option on windows 10)

I need to mention that even the network card is giving me trouble sometimes on boot i need to remove and reinsert the ethernet cable to get network working, not sure if it's a driver problem or a faulty hardware btw.


[SOLVED] With installing alsa-tools-gui --> Running  hdajackretask --> Change inline to rear output --> setup boot override
Also edit > $ sudo nano /etc/pulse/daemon.conf 
then testing with > $ speaker-test -c4 -twav

This process made analog surround 4.0 Output + analog stereo input appear on pavcontrol

---

