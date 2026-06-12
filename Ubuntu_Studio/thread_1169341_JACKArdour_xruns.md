---
title: "JACK/Ardour xruns"
date: 2009-05-25
forum: Ubuntu Studio
---

### Post by seanlano on 2009-05-25
I know it's been asked a million times, but how can I reduce my xrun errors? I couldn't find anything relating to my problem anywhere. 

I am using Jaunty with the 2.6.30rc4 kernel from the ubuntu kernel site (the included kernel was very, very buggy on my laptop), which seems to have RT support (if I select "realtime" from the JACK set-up, it works). I have set the latency to about as high as it will go (it's at 557ms!) and I am recording at 44.1khz. I am doing the sound mixing for my school's musical production, and I am trying to record the show using a Presonus FP10. It records just fine, but every now and then I get an enormous bout of xruns (over 200 over the space of 20 minutes), which basically make that take unusable. As we only have 4 more shows to go, I would like to get it right, and soon! I'll attach a screenshot of Ardour and qJACKctl. I've tried recording fewer channels, but it doesn't seem to help, so I don't think that its because of a data-overload for the HDD. The xruns are at regular intervals, about 1 every second. 

Any ideas?

---

### Post by dawiba on 2009-05-25
I'll apologise in advance if I'm stating the obvious or if I'm completely wrong, but the two attachments show two different sample rates (the ardour window shows 48khz).

Someone who knows will be along shortly :)

---

### Post by seanlano on 2009-05-25
Mmm, thats because I started Ardour without starting JACK, so I could take the screenshot. I should have done it better, oops. It normally says the same value.

---

### Post by StudioDave on 2009-05-25
> **seanlano said:**
> I know it's been asked a million times, but how can I reduce my xrun errors?...I am using Jaunty with the 2.6.30rc4 kernel from the ubuntu kernel site (the included kernel was very, very buggy on my laptop), which seems to have RT support (if I select "realtime" from the JACK set-up, it works)...a Presonus FP10... records just fine, but every now and then I get an enormous bout of xruns (over 200 over the space of 20 minutes), which basically make that take unusable.... The xruns are at regular intervals, about 1 every second. 


I've not used a Firewire interface yet so my suggestions may be unusable, but here goes. First, you should contact Pieter Palmers at the FFADO project, he knows more about this topic than I do.

[http://www.ffado.org/](http://www.ffado.org/)

The FP10 is listed as working with the FFADO driver.

Next you should run 'uname -a' and report its output. QJackCtl may say that realtime is working, but the kernel you indicated doesn't appear to be an rt-enabled kernel.

What does your /etc/security/limits.conf look like ?

Do you have HAL polling enabled for any devices ? You can check for its operation with the top or htop utilities (htop is much nicer).

A sudden string of xruns points to a possible IRQ conflict. Run 'cat /proc/interrupts' and note what line your Presonus is on. Check to see if anything else is on that line.

The xruns also point to a priority problem. Something else gets priority over your audio device at some point, we need to figure what it is and why it's causing the problem. Try running top and watching it while the xruns occur. The offending device may show up there.

HTH,

dp

---

### Post by thorgal on 2009-05-25
Dave, close to RT operations are possible on a non preemptable kernel. It's just that the RT patch makes the kernel close to a hard RT system, at least soft RT. Without this patch, one cannot strictly qualify the system to be RT.

What the -R option to jack means is that you enable jack (and jack apps) to access scheduling priorities that normal users have no access to usually. For normal desktop operations, you don't necessarily need to. But for a low latency audio server, it becomes necessary to elevate the user privilege regarding task scheduling policies. That's the role of the PAM security thing, which is not the same thing as an RT patched kernel.
Indeed, you could have an RT kernel and yet, not provide the user with elevated privileges to use it ;)

---

### Post by seanlano on 2009-05-26
OK, thanks a bunch. 

```
sudo uname -a
Linux ubuntu-laptop 2.6.30-020630rc4-generic #020630rc4 SMP Fri May 1 09:06:03 UTC 2009 i686 GNU/Linux

```

And the limits.conf:
```

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio          -       rtprio          99

@audio - memlock 1837616unlimited

# End of file
```

and 

```
sudo cat /proc/interrupts
          CPU0       CPU1       
  0:    1097863    1081968   IO-APIC-edge      timer
  1:        334        298   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:        722        739   IO-APIC-fasteoi   acpi
 12:         57         52   IO-APIC-edge      i8042
 14:       3681       3671   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:       5460       5699   IO-APIC-fasteoi   uhci_hcd:usb5, yenta
 17:     229344     245189   IO-APIC-fasteoi   uhci_hcd:usb6, ohci1394, HDA Intel
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb7, mmc0
 19:          1          1   IO-APIC-fasteoi   ehci_hcd:usb2
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1
 27:          0          0   PCI-MSI-edge      pciehp
 29:      23089      22821   PCI-MSI-edge      ahci
 30:          0          0   PCI-MSI-edge      iwl3945
 31:      22483      22005   PCI-MSI-edge      i915@pci:0000:00:02.0
 32:        873        914   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:    1633535    2213735   Local timer interrupts
SPU:          0          0   Spurious interrupts
RES:     306715     310492   Rescheduling interrupts
CAL:         68         63   Function call interrupts
TLB:       1233        542   TLB shootdowns
ERR:          0
MIS:          0

```

I'm not sure about the HAL polling (I don't know what it is, unless it can be changed by other programs installing, then it should be at default values). 

I know that FFADO is the new FREEBoB, but I was definitely using FREEBoB not the FFADO driver when I was recording. I am playing back something through the FP10 now, using the FFADO driver, and there seems to be now xruns yet, but I'll leave it for a few hours to see. Then I'll record for a while (but just silence, I don't have anything to put into it here at home). Maybe whatever the problem is has been fixed in the FFADO driver, and I'm just a fool for not using it upfront.

---

### Post by seanlano on 2009-05-26
I've tried it with the FFADO driver, and I have noticed an interesting bug/error. Firstly, FFADO seems to so far run without any xruns, I can record 6 channels from the FP10 without a single xrun (at least for the 20 minutes I tried it), but if I close the lid on my laptop and then open it again it the JACK messages window reports: ```
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
16:42:47.952 JACK connection graph change.
03357721557: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_1...
03357721581: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_1...
03357721592: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_2...
03357721602: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_2...
03357721612: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_3...
03357721622: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_3...
03357721632: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_Volume_4...
03357721641: Debug (bebob_mixer.cpp)[  81] ~Mixer: deleting Feature_LRBalance_4...
16:42:48.073 JACK connection change.
jack main caught signal 12
no message buffer overruns
16:42:48.165 Shutdown notification.
16:42:48.166 JACK is stopping...
16:42:48.167 JACK is being forced...
zombified - calling shutdown handler
16:42:48.442 JACK was stopped successfully.
16:42:48.443 Post-shutdown script...
16:42:48.444 killall jackd
jackd: no process killed
16:42:48.925 Post-shutdown script terminated with exit status=256.
```

This only happens when I open up the lid again, and I have no idea why. I notice that in normal operation, Jaunty will "refresh" my windows (i.e. Compiz/Metacity will re-draw them) every time I open the lid, which seems to coincide with this error, but it may not be the window managers fault, perhaps the refresh is also caused by whatever causes the FFADO driver to die. I will try again for a while with the lid open to see if the xruns are a problem.

---

### Post by thorgal on 2009-05-26
hey!

you have a "funny" /etc/security/limits.conf. The interesting part for RT priority looks like this in my file:

```

@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

```

Regarding the lid closing, does your power management (probably the acpid daemon) turn off DPMS ? or do you have the laptop put to sleep ? as far as I know, jack does not have any power management feature. It may happen in the future and that would be welcome, in my humble opinion.


Anyway, I am not familiar with gnome or GUIs for admin system tasks, but you can always apt-get install an app called sysv-rc-conf and run it in a terminal with sudo in front
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

```

then you can scroll down with pressing Ctrl-n until you find the hal service. You can then uncheck the service startup at all run levels (most likely 2,3,4,5 by default). Doing so will prevent the init scripts to start HAL when you boot.

To turn it off ponctually, just do

```

sudo /etc/init.d/hal stop

```


Turning off HAL may affect certain hardware events like powersaving and others. In KDE, I know that an app like kpowersave depends on the HAL daemon running.

You can also turn off the whole DBUS stuff if you don't care about DBUS (see dbus in sysv-rc-conf).

---

### Post by seanlano on 2009-05-29
Well, I recorded using the FFADO driver, and I got the whole show (with 8 channels) and only ~40msec of latency, WITHOUT A SINGLE XRUN! I'm not sure what was wrong with the FREEBoB driver, but the only advantage I can see in having it is that the FFADO driver I have doesn't let me use the MIDI ports on the FP10 (but that's not so bad, as I haven't needed them yet). The MIDI I/O's show up in blue instead of green in patchage. 

Anyway, I'm not sure whats going on with Jaunty when I open the lid on my laptop, but it's a bit weird. Thankfully it's completely avoidable.

---

### Post by StudioDave on 2009-05-29
Hi thorgal,

> **thorgal said:**
> Dave, close to RT operations are possible on a non preemptable kernel. It's just that the RT patch makes the kernel close to a hard RT system, at least soft RT. Without this patch, one cannot strictly qualify the system to be RT.

Yes, I know this. However, I've never been satisfied with the performance  from a non-rt kernel. That's just been my experience.

> ... you could have an RT kernel and yet, not provide the user with elevated privileges to use it.

That is, just like Ubuntu Studio does by default. :(

US does not create an audio group, nor does it fully modify limits.conf. Why do these oversights exist in a distribution designed for advanced multimedia production ? The group and the limits.conf entries are advised with the same values for every user, so why not make it happen at the installation/configuration stages ?

---

### Post by raboofje on 2009-05-29
> **StudioDave said:**
> US does not create an audio group, nor does it fully modify limits.conf. Why do these oversights exist in a distribution designed for advanced multimedia production? The group and the limits.conf entries are advised with the same values for every user, so why not make it happen at the installation/configuration stages?

Let me dump this link again:

[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)

---

### Post by StudioDave on 2009-05-30
> **raboofje said:**
> Let me dump this link again:

[https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)

I know that link and found it helpful. However, it also confirms my statement. Given that the suggested values will be identical across new installations, why doesn't the installer simply create the required group and associated values ?

---

### Post by raboofje on 2009-05-30
> **StudioDave said:**
> US does not create an audio group

That's odd: the 'master' group file in base-passwd 3.5.21 does include the audio group. [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support) only mentions the 'audio' group being missing in 'Jaunty Beta', perhaps this has been fixed since?

> **StudioDave said:**
> nor does it fully modify limits.conf

I submitted [https://bugs.launchpad.net/ubuntu/+source/pam/+bug/381937](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/381937)

---

### Post by StudioDave on 2009-05-31
> **raboofje said:**
> That's odd: the 'master' group file in base-passwd 3.5.21 does include the audio group. [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support) only mentions the 'audio' group being missing in 'Jaunty Beta', perhaps this has been fixed since?

I install only the public final releases of Ubuntu, and I've tried Hardy, Intrepid, and Jaunty. Given the number of problems I encounter in those releases there's no way I'll try using an Ubuntu beta release. And yes, all the troubles I've experienced with Jaunty are troubles I already encountered in Intrepid. Their continued presence does not bode well for US 9.04 as a recommendable system for audio production.

Btw, I thought that my troubles were due to the rather new hardware on my HP G60 notebook, but the same problems occur on my older desktop box too (running the latest US/Jaunty). Grrrr....

---

### Post by seanlano on 2009-06-03
I'm using the FFADO driver (v 1.999.40, the version in the Jaunty repos) with my PreSonus FP10, and it works great. I recorded hours without a single xrun. The only problem is that the MIDI input doesn't show up in Patchage like it does with the FREEBoB driver. 

Any ideas?

---

### Post by raboofje on 2009-06-03
> **seanlano said:**
> I'm using the FFADO driver (v 1.999.40, the version in the Jaunty repos) with my PreSonus FP10, and it works great. I recorded hours without a single xrun. The only problem is that the MIDI input doesn't show up in Patchage like it does with the FREEBoB driver. 

You might want to post that as a new thread :)

---

### Post by dawiba on 2009-06-03
> **seanlano said:**
> I'm using the FFADO driver (v 1.999.40, the version in the Jaunty repos) with my PreSonus FP10, and it works great. I recorded hours without a single xrun. The only problem is that the MIDI input doesn't show up in Patchage like it does with the FREEBoB driver. 

Any ideas?

Midi will only work with jack-midi which means installing a2jmidi as midi through alsa will not work using ffado.

I think you can find out some more on the ffado website or by looking here [http://home.gna.org/a2jmidid/](http://home.gna.org/a2jmidid/)

---

### Post by thorgal on 2009-06-03
maybe you need to tell jack to start with the -X seq option ?
It's an option you can choose in qjackctl's setup window.

---

### Post by seanlano on 2009-08-30
Installing "a2jmidid" and running it with ```
a2jmidid
```each time I use Patchage has fixed the MIDI problem. And with the FFADO driver it works great. Not a single xrun. 

I love Ubuntu!

---

### Post by ElectricJake on 2009-11-07
my added lines to limits.conf are:

@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

and I get no xruns on an inspiron 2560 and a Fast Track USB (not offically supported) using jack settings:

priority: 70
frames: 64 
sample: 4800
periods: 2

leading to a latency of 2.67 ms

this is a near-clean install, mind you, but generally when a new version comes out I make sure rt kernel is working before I even adjust the clock and menus, or watch a youtube video ;P

I hope to inspire people with the fact that (practically) realtime multitracking is possible with only slight tweaking, little knowledge,  and with obsolete and barely supported hardware (and now, even Pulse!) because UbuntuStudio is that awesome. Though I do agree some of these basic tweaks should be clean install defaults, since they are necessary and universal.

My only advice: make sure your ACPI, LAPIC, and APIC are functioning. Disabling these will cripple performance, so shouldn't be considered an option.

---

### Post by elnormeo on 2010-02-08
Hi,
I'm quite read ALL the infos regarding Ubuntu Studio, presonus FP 10 and tried every audio distri, i could find.
My conclusion:
Not a single audio distribution are capable of getting the Presonus FP10, Jack and Ardour starting without getting the arms deep into the oily gear of the kernel by yourself. Thats so unbelievable frustrating.
Now my config:
Dell D630, Ubuntu Studio 9.10 and 2x daisychained FP10.

What i already did:
- changed the 1394 cables a dozen times
- tried only one fp10
- Ubuntu Preparations ([https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time-Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time-Support))
- Tweaking the limits.conf, blacklist-firewire, tuning the rules-permission for the Kernel and the firewie support,
- adding the group issue
- tried Freebob & FFado.
Ffado was installed like windows , 5 libs were missing, i had to install them manually)
-gscanbus was unable to install (lots of missing libs, which coul dnot be installed)
- Getting the RT Kernel (of course)

Right now:
I get the FP10 with freebob started for a couple of minutes, then it died.
I get the FP10 with ffado started for a couple of minutes and also Ardour is starting (It won't start with the Freebob driver-wtf) and after a few minutes, jack just died.
Also looking with ffado-test, my FP10's are coming...and going, usually they go after jack died.
This is sooo frustrating;-)
The FP10's are working like busy bees under windows xp and cubase sx. No Probs there. On the same machine! So its not hardware related.
If any of you, have a D630, please, please with sugar on top, what is your configuration steps to get them running?????

#-o


Thanks for any hint, girls & guys,

Nomek

---

### Post by trulan on 2010-02-08
Well, here is the setup process I've used:
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Works with one or two firepods on my Dell inspiron E1505.

The only other issue I have seen that the guide doesn't cover is the CPU scaling issue.  It's a good idea to set your CPU(s) to performance mode, or maximum frequency.  There are several ways to do this.  The simplest, IMO, is using the gnome panel CPU scaling applet - use one for each CPU core.

---

### Post by mrufino1 on 2010-02-09
I have had very good luck with av linux. Trulan helped me with some small firewire issues but things are running really well. I have a phonic firewire mixer, but I use3d to have firepods 
(fp10's after firmware upgrades) and they worked fine under linux. I now have my system set up as dual boot with ubuntu karmic as my everyday computer and av linux for production on an IBM laptop and things are working great. > **elnormeo said:**
> Hi,
I'm quite read ALL the infos regarding Ubuntu Studio, presonus FP 10 and tried every audio distri, i could find.
My conclusion:
Not a single audio distribution are capable of getting the Presonus FP10, Jack and Ardour starting without getting the arms deep into the oily gear of the kernel by yourself. Thats so unbelievable frustrating.
Now my config:
Dell D630, Ubuntu Studio 9.10 and 2x daisychained FP10.

What i already did:
- changed the 1394 cables a dozen times
- tried only one fp10
- Ubuntu Preparations ([https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time-Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time-Support))
- Tweaking the limits.conf, blacklist-firewire, tuning the rules-permission for the Kernel and the firewie support,
- adding the group issue
- tried Freebob & FFado.
Ffado was installed like windows , 5 libs were missing, i had to install them manually)
-gscanbus was unable to install (lots of missing libs, which coul dnot be installed)
- Getting the RT Kernel (of course)

Right now:
I get the FP10 with freebob started for a couple of minutes, then it died.
I get the FP10 with ffado started for a couple of minutes and also Ardour is starting (It won't start with the Freebob driver-wtf) and after a few minutes, jack just died.
Also looking with ffado-test, my FP10's are coming...and going, usually they go after jack died.
This is sooo frustrating;-)
The FP10's are working like busy bees under windows xp and cubase sx. No Probs there. On the same machine! So its not hardware related.
If any of you, have a D630, please, please with sugar on top, what is your configuration steps to get them running?????

#-o


Thanks for any hint, girls & guys,

Nomek

---

