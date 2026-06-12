---
title: "sound stopped upgrade to 10.04"
date: 2010-07-29
forum: System76 Support
---

### Post by dgermann on 2010-07-29
Hi--

Upgraded last night from 8.04 to 10.04 on gazv4.

My sound stopped working. I see nothing wrong in alsamixer, although I am not sure what I'm looking at there.

I enabled lucid proposed, also re-checked planet76 which had been disabled on upgrade. Then I installed the system76 driver and get a message that "All drivers are provided by Ubuntu." Rebooted.

There is no speaker icon in the panel as there was in 8.04.

I have checked to make sure it is not muted (Fn F6). Have also increased the volume to about 80% (Fn F8).

I have no sound whatsoever. Nothing on arriving at the login screen, nothing on logging in.

How do I get sound back?

Thanks!

---

### Post by ranch hand on 2010-07-30
It should be there.  I believe that you can get it by installing "indicator-sound".

---

### Post by dgermann on 2010-07-30
ranch hand--

Many thanks!

Via synaptic, I reinstalled indicator-sound, and nothing. Still nothing after uninstalling and reinstalling. And nothing after logging out and back in.

Not sure what else to try. Any ideas?

Thanks!

---

### Post by j0eb0b on 2010-07-30
Are you using the sound chip on your motherboard or a separate sound card?  I use an Audigy sound card and have disabled the sound chip on my motherboard.  When I upgraded to 10.04 from 9.04 the install defaulted to the motherboard sound chip rather than the Audigy and hence no sound.  When set back to the Audigy, all is well.  If you don't have multiple sound devices than I guess this suggest won't help.

---

### Post by dgermann on 2010-07-30
j0eb0b--

Thank you for helping me.

Just the plain vanilla 'puter here--no special sound cards or anything installed.

Is there a way to get to the sound applet running without clicking an icon?

I just went to the terminal and did a sudo updatedb and then locate indicator-sound. Then ran /usr/lib/indicator-sound/indicator-sound-service. Got a bunch of DEBUG responses that ended with "I just closed communication with Pulse". Same thing running the command with sudo. Here's the output:

```
doug@ubuntu:~$ sudo /usr/lib/indicator-sound/indicator-sound-service 
** (process:4783): DEBUG: Root ID: 1
** (process:4783): DEBUG: update pa state with state 0, availability of 0, mute value of 0 and a volume percent is 0.000000
** (process:4783): DEBUG: Building new Slider Menu Item
** (process:4783): DEBUG: !!!!!!**in the rebuild sound menu - slider active = 0
** (process:4783): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 0
** (process:4783): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 0.000000
** (process:4783): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 0
** (process:4783): DEBUG: connecting - waiting for the server to become available
** (process:4783): DEBUG: authorizing
** (process:4783): DEBUG: context setting name
** (process:4783): DEBUG: PA daemon is ready
** (process:4783): DEBUG: server info callback
** (process:4783): DEBUG: Just set the default sink index to 0

** (process:4783): WARNING **: Default Sink info callback failure
** (process:4783): DEBUG: About to add an item to our hash
** (process:4783): DEBUG: After adding an item to our hash
** (process:4783): DEBUG: About to test for to see if the available sink is null - s->name = alsa_output.pci-0000_00_1b.0.analog-stereo
** (process:4783): DEBUG: PA_Manager ->  determine_sink_availability: 1
** (process:4783): DEBUG: software volume = 92.233276
** (process:4783): DEBUG: update pa state with state 1, availability of 1, mute value of 0 and a volume percent is 92.233276
** (process:4783): DEBUG: in the refresh menu method
** (process:4783): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 1
** (process:4783): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 92.233276
** (process:4783): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 0

(process:4783): libindicator-WARNING **: No watchers, service timing out.
** (process:4783): DEBUG: Service shutdown !
** (process:4783): DEBUG: freeing the pulse context
** (process:4783): DEBUG: I just closed communication with Pulse
doug@ubuntu:~$ 

```

Any ideas?

Thanks!

---

### Post by isantop on 2010-07-30
You can get the same functionality as the sound icon by going to System > Preferences > Sound. You can check which device is set for output and what profile you have.

Go ahead and open that, then take a screenshot by pressing Alt+PrtSc. Post the screenshot here so i can check the settings.

---

### Post by kostkon on 2010-07-30
Try deleting the *.pulse* folder in your home. To access it, press Ctrl+H or select *View &#8594; Show Hidden Files* in the nautilus window. Alternatively, open a terminal and give
```
rm -rf ~/.pulse
```
logout and login again. Then, try to setup your sound in *System &#8594; Preferences &#8594; Sound* as *isantop* suggested.

---

### Post by dgermann on 2010-07-30
isantop--

Thanks. Screenshot attached.

---

### Post by dgermann on 2010-07-30
kostkon--

OK, I did as you suggested and there is no joy. Still no sound, nor sound icon in the panel.

Next thing to try? <grin>

---

### Post by ranch hand on 2010-07-30
This really is a bugger.  Did you check ALL the options in the Sys>Pref>Sound gui?  You really should be able to get sound from there.

If that doesn't do it how about sending the out put from;
```

lspci

```
That is a lower case L in that command.

---

### Post by dgermann on 2010-07-30
ranch hand--

Thanks for hanging in there with me, ranch hand!

I have no idea what I'm looking at in that gui--nothing looks amiss. There are a couple of places where it allows for checking a box that says mute--I even checked and then unchecked them. Other than that, maybe someone can tell me what the settings usually are. For instance on the Hardware tab I have "Analog stero input." Input was muted; i just changed that. Output says "Dummy output stereo." And Applications shows none currently using it.

Here's the output:

```
doug@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
doug@ubuntu:~$ 

```

Any clues there?

Thanks for helping me.

---

### Post by ranch hand on 2010-07-30
Well, you do appear to only have the one audio controller.

There is this post from a while back, I scanned through it and it might inspire you in some different direction of thought or action.

[http://ubuntuforums.org/showthread.php?t=1467387](http://ubuntuforums.org/showthread.php?t=1467387)

If you have more than one user this may be a problem;

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654)

If so you should log in there and add your "effects me too" to the bug.

One thing I always try is the gnome-alsamixer.  I like it better than the vanilla alsamixer and it helps that it supports my audio card the best (another creative labs product like the Sound Blaster mentioned earlier).  The nicest thing is that the gnome-alsamixer gives you everything in an editable gui that alsamixer gives you in terminal.  This means that if you do not have all the features they do not need to be there at all.  Saves time.

If you install it it will show  up in the Applications>Sound & Video menu.

EDIT
I took the liberty of sending a PM to the one guy on the thread linked above that seemed to actually know something about your controller with a link to this thread.  Don't know if he has time for this or not.

---

### Post by lidex on 2010-07-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
These as well:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by dgermann on 2010-07-31
lidex--

Thank you for helping me.

My computer is a System76 GAZV4.

```
doug@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
doug@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
doug@ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                                                1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                               1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                               4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                          0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                       0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                             0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
rc  libsdl1.2debian-alsa                                     1.2.13-1ubuntu1                                 Simple DirectMedia Layer (with X11 and ALSA options)
doug@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices AD1986A

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa
doug@ubuntu:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for doug: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  doug       5732 F.... pulseaudio
/dev/snd/pcmC0D0c:   doug       5732 F...m pulseaudio
doug@ubuntu:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
[   34.914346] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   34.914395] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   34.914421] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   34.920484] vga16fb: initializing
--
[   35.360152] CIFS: Unknown mount option mand
[   35.360381] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   35.364644]  CIFS VFS: Error connecting to socket. Aborting operation

[148778.519330] type=1503 audit(1280605612.677:27):  operation="open" pid=10523 parent=2353 profile="/usr/sbin/cupsd" requested_mask="::r" denied_mask="::r" fsuid=7 ouid=0 name="/var/run/samba/gencache.tdb"
[149311.210135] hda_codec: invalid CONNECT_LIST verb 12[2]:2100
doug@ubuntu:~$ 

```

Seeing any clues here?

Thanks lidex!

---

### Post by lidex on 2010-07-31
OK. Can you post this output also:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```
Did you have to tweak anything previously for sound - any alsaconf files, etc?

---

### Post by dgermann on 2010-08-01
lidex--

Sounds like you are on the track of something....

You should know that I had sound before the upgrade.

```
doug@ubuntu:~$ sudo dmidecode -t bios
[sudo] password for doug: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 205    
	Release Date: 02/05/2007
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 1.124
	Firmware Revision: 168.153

Handle 0x0019, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

doug@ubuntu:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer Inc.        
	Product Name: Z62FM     
	Version: 2.1       
	Serial Number: BSN12345[partially blanked]
	Asset Tag: ATN1234[partially blanked]
	Features:
		Board is a hosting board
		Board requires at least one daughter board
		Board is replaceable
	Location In Chassis: MIDDLE              
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0015, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: AGP VGA controller

Handle 0x0016, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Ethernet controller

Handle 0x0017, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Audio controller

Handle 0x0018, DMI type 10, 6 bytes
On Board Device Information
	Type: Other
	Status: Enabled
	Description: Modem controller

doug@ubuntu:~$ 

```

So what are you suspecting?

Thanks for your help, lidex!

---

### Post by lidex on 2010-08-01
Another thread I'm working with the same issue has an AMI bios as well. Not sure if that's the problem but it may be helpful to update yours as it is 3 years old. And this from dmesg:
```
[149311.210135] hda_codec: invalid CONNECT_LIST verb 12[2]:2100

```
I would recommend an alsa upgrade via the link in my sig after flashing your bios.

---

### Post by dgermann on 2010-08-02
lidex--

Thanks for helping me.

I've never flashed a bios. Is it risky? Is there a good howto someplace?

Thanks!

---

### Post by kostkon on 2010-08-02
> **dgermann said:**
> My sound stopped working. I see nothing wrong in alsamixer, although I am not sure what I'm looking at there.
You could run alsamixer again, press F6 and select your card from the list to make sure that you are viewing the volume levels of your card (and not PulseAudio's volume levels).

---

### Post by hudsonl on 2010-08-02
I had the same problem after the upgrade to 10.04 from 9.10.

It DID work for quite a while ... and just noticed it stopped working after one of the recent updates.

Tried numerous things ... but I kept noticing that when I would reboot or log off, I would get a message that a program was still running and did I want to reboot anyway, cancel, etc. type of message. (it was pulse-audio).

So I assumed there was some conflicts with pulse and alsa ... nothing to lose, so **I removed the PulseAudio Sound Server and rebooted and it works now.**

Go into Synaptic Package Manager ...
Select "**pulseaudio**" (PulseAudio sound server) - **Mark for Complete Removal**
- Select OK for all the dependencies
- Select Apply

- Reboot after removal is completed.

If it doesn't work ... re-install using Synaptic Package Manager

One thing that I did (saw on the forums) that help sound work consistently for me on 9.10 was disabling the sound on the BIOS. If you have a sound card and integrated sound on your motherboard ... multiple "cards" seemed to make it "flaky"

Good luck.

---

### Post by simosx on 2010-08-02
When sound stops working or is misbehaving in general, the first thing to do is produce the alsa-info.sh settings file. This is pure Alsa settings, that can indicate if Alsa is to blame (for example, if there is a regression).

To do so, run

> wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh


You will be prompted to send the details to the alsa-project.org website. Select Yes and write down the URL for your data. 
Finally, post that URL here.

Killing pulseaudio, reinstalling pulseaudio or the alsa packages is too much of Windows troubleshooting.

See SoundTroubleshooting at the UBuntu Wiki for more,
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by ranch hand on 2010-08-02
> **simosx said:**
> When sound stops working or is misbehaving in general, the first thing to do is produce the alsa-info.sh settings file. This is pure Alsa settings, that can indicate if Alsa is to blame (for example, if there is a regression).

To do so, run



You will be prompted to send the details to the alsa-project.org website. Select Yes and write down the URL for your data. 
Finally, post that URL here.

Killing pulseaudio, reinstalling pulseaudio or the alsa packages is too much of Windows troubleshooting.

See SoundTroubleshooting at the UBuntu Wiki for more,
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Thank you for this information.  I have no trouble at all with my sound but that is a great wiki page.

I completely agree with your thinking on deleting/installing.  Way too much like MS.

We can get real information about a real OS using Ubuntu or any Linux distro.  No need to act like a bad auto mechanic and just start swapping parts out.

---

### Post by dgermann on 2010-08-02
kostkon--

Thanks. I did as you said, but I still don't know what I'm looking at there. The output stuff all has the volume turned up and nothing muted, as far as I can see.

All--

I do not even get a system beep (ctrl-G).

hudsonl--

Thanks. I tried that and no joy. So I put it back.

simosx--

Wow! What a script! Is it safe? There is a lot going on there and I don't know enough to judge its safety.

I did work my way about half way down the Ubuntu sound troubleshooting page--all the way till they got to that wget script. Nothing up to that point turned up a problem.

I am too tired at the moment to do a good job following the rest of the instructions, so I will have to come back to this.

Say, would it make sense for me just to do a clean install?

ranch hand--

I still have your suggestion from the other day to try those things on another page, and I intend to get to them. Thanks!

---

### Post by ranch hand on 2010-08-02
I do not see that a clean install is going to help you that much.  I would hang in there a bit.  Give lidex the info he wants.

Do a little research on flashing your bios under Linux.  This might be a help.

Rather than a fresh install I would look inside your box and see if you have an extra pci slot.  Old audigy cards like mine are well supported.  They are also pretty cheap on ebay.  Audigy 2 should work well too.

You would need different speakers I would think.  This is a 5.1 surround sound card and I got an Altec Lansing speaker system (ebay) for 50 bucks including shipping.  Sounds great with everything from country through rock and on to classical (broad taste in music).

I would look into that if you like to listen to music.  I would also try to get what you have working though.

That script should be safe and posting the result url here may help clear up your problem.

Back to the clean install.  I would not even think about it right now.  10.04.1 (point release for LTS versions - 8.04.4 came out just before 10.04 was released) was supposed to be out 7-29.  This would be a new ISO including, of coarse, all the upgrades and the fresh release bug fixes.  The bug fixes are not done, you have probably noticed the large amount of upgrades.

10.04.1 is now scheduled for 8-19.  I do not see any reason to do a thing until then at least.  My wife has a Pangolin that we got late last year running 9.10.  It will keep running 9.10 until I think that 10.04 is not too buggy.

I can't even run the bugger on my desktop.  I am on 9.04 right now but during the day I run 10.10-testing (alpha3 due on thursday) and it is a better OS than 10.04.  I can boot it and it will actually shut down.

---

### Post by isantop on 2010-08-03
> **dgermann said:**
> 
Wow! What a script! Is it safe? There is a lot going on there and I don't know enough to judge its safety.

Good for you! There are indeed a lot of "Scripts of questionable orign or legitimacy" floating about, and you knew to check!:)

This is a good one. All it does is collect information about your system and post it on a website. It's perfectly safe for you to run, and it will give the alsa devs some more evidence to work with.

---

### Post by dgermann on 2010-08-03
simosx--

OK, here is the url:
[http://www.alsa-project.org/db/?f=9d5fcc02c32017e2f9ee5cfb2aecc3646671746c]("http://www.alsa-project.org/db/?f=9d5fcc02c32017e2f9ee5cfb2aecc3646671746c")

isantop--

Many thanks for quelling my fears!

Do you have any safe place to look for a howto on flashing my bios for a System76 GAZV4? Everything I see out there in my research says if you botch it, the whole box goes up in blue smoke visible for miles around....

ranch hand--

This box is a laptop, so I do not know how to get inside it (if the user is even supposed to be able to! :) )

Thanks everyone. Perhaps more a little later....

---

### Post by dgermann on 2010-08-03
Hi--

Further report: I went into alsamixer and found that beep and one of the S/PDIF sections were muted. I unmuted those and still no sound, not even system beep (ctrl-G).

The sound troubleshooting page suggests this--anybody got one? "# Get a working /var/lib/alsa/asound.state from someone who has similar hardware"

OK, so I went to the page Ranch Hand suggested in post #12 above. I did what was suggested in # 4 & # 7 of this thread: [http://ubuntuforums.org/showthread.php?t=1467387]("http://ubuntuforums.org/showthread.php?t=1467387")

In #7 it points me to Part A of this thread: [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

When I did that, step 4 results in not being able to open System>Preferences>Sound. It spins a bit, and nothing happens.

Then when I do step 5, I end up with the screenshot attached. Notice that the little speaker icon has a red x next to it, but I cannot click on it.

The stuff under the Volume control reads: 
```
doug@ubuntu:~$ pavucontrol

(pavucontrol:3415): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
doug@ubuntu:~$ sudo pavucontrol

(pavucontrol:3422): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
doug@ubuntu:~$ pulseaudio & pavucontrol
[1] 3426
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:3427): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
doug@ubuntu:~$ pulseaudio & pavucontrol
[1] 3434
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:3435): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
doug@ubuntu:~$ 

```

(Some place in this process, the panels turned from dark grey background to the light grey you see here--what happened? Also, everything now seems too small to read! Can it be fixed?)

I see I have a new applet in the panel for pulseaudio. I start it but it reports "Failure: connection refused."

gnome-volume-manager is not installed and synaptic says there is no available version.

OK, I think I have tried about everything anybody has suggested but the alsa upgrade script and flashing my bios.

So, does any of this give us any clues?

I can do a lot of things under linux, but sound is foreign territory for me! :(

---

### Post by simosx on 2010-08-04
> **dgermann said:**
> simosx--

OK, here is the url:
[http://www.alsa-project.org/db/?f=9d5fcc02c32017e2f9ee5cfb2aecc3646671746c]("http://www.alsa-project.org/db/?f=9d5fcc02c32017e2f9ee5cfb2aecc3646671746c")


Your Alsa-info output says,

1. you are running the stock sound drivers for Ubuntu 10.04 ('Alsa version')
=> You can try to install the latest Alsa version by compiling it. The process is described at 
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
The latest Alsa version is 1.0.23.

2. your codec is 'Analog Devices AD1986A'
=> You may specify a model name in your /etc/modprobe.d/alsa-base.conf from the list 
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#237](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#237)
For help, see [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

3. At the 'APLAY' section, you have two output devices, an analog one and a digital one. The Analog is the laptop speakers (or headset, if you plug them in) and the Digital is your HDMI port. If you do not have an HDMI, please tell us. In some cases it is possible that your computer tries to output to HDMI while you have nothing connected there. In the Sound preferences you can make sure which output is active (Make it 'Analog').

4. At the ARECORD section, you have one input device. You can try to record something, then play it with a program that shows the histogram of the audio. One such tool is Audacity. This should show if recording works but playback is not.

5. Your 'dmesg' section (at the end of the file) says

[76232.011780] hda_codec: invalid CONNECT_LIST verb 12[2]:2100

This is the most worrying error, which may cause the problems. I googled about it and I saw other people who have issues having this message. I found the page where the code for the message was added to Alsa,
[http://kerneltrap.org/mailarchive/git-commits-head/2009/7/22/23](http://kerneltrap.org/mailarchive/git-commits-head/2009/7/22/23)
I do not make sense of it, but then I did not try to delve too much deeper.

6. There are tools that can help analyse the connections shown in Alsa-info.sh. It's somewhat for experts only (for the interpretation of the output). In any case, the link is [http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA](http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA)

What you can do?
a. Check Step [3] above and select Analog output. Test.
b. If you do not have an HDMI port on your laptop, try Step [2] above and specify some different models. If it still does not work, you can remove any reference to models you did and continue to the next step.
c. Now you can try Step [1] and compile the latest Alsa version. This will upgrade the Alsa kernel modules and the Alsa libraries. You can revert back if you reinstall the kernel and the Alsa libraries.
If you do this, create a new alsa-info.sh file and post here.

The end result would be to find what makes Alsa work so that we submit it to the Alsa project. And newer Ubuntus will work out of the box.

(I am quick-replying; if you did not upgrade your BIOS to the latest, you may want to do this first).

---

### Post by dgermann on 2010-08-04
simosx--

Thank you for working so hard to help me! Wow, you have really gone out of your way....

3. I do not know what HDMI is. The Wikipedia entry shows plugs that look kind of like USB plugs, but narrower on one edge. I do not have anything like that. The only thing currently plugged into my laptop is the power cable and the ethernet cable. I plugged speakers into it a year ago or so. I think I plugged a microphone in at one time, too.

System > Preferences > Sound still does not come up. In the lower panel it shows "starting Sound" for a few seconds and then disappears. I think in the terminal the entry was pavucontrol & pulseaudio, but that does not start either. So I am unable to make the changes you suggest here, unless there is something else to try.

2. This one is very confusing--not what you posted, but what all the referred pages want me to look up and find, and I have no idea what that is all about.

No, I have not yet flashed my bios. I was hoping someone here could point me to a howto specific for System76, so I don't have to reinvent the wheel and possibly blow up my machine.

I will do some more checking and reading and get back as I make sense of any of the rest of this. :(

---

### Post by dgermann on 2010-08-04
Hi--

OK, reporting:

In this line in the instructions
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

There is both an alsa-base and an alsa-base.conf file. I edited the one with .conf. Correct choice?

time passes....

I guess it must have been. Editing that file and using "laptop" as the MODEL seems to have fixed it. I have the sound on login, have sound in a movie, and ctrl-G gives me an annoying little sound like tapping with a coin on a glass window. Youtube is not working--flash plugin crashed, but I have seen that before, so I think I can probably find my way back to that. Yes, got that fixed, and that video and my local news channel videos are playing and they have sound!

So it looks like I have dodged the bullet of figuring out how to flash my bios, yes?

Thanks everybody for all your help. It looks like it is working now. But it was a lot of blood and pain for all of us, right?

Thanks!

---

### Post by simosx on 2010-08-05
Yep, it's the *.conf file you need to edit.

It's great that we established that it's the 'laptop' model for your computer.
I looked into the Alsa source code and I found the relevant section (bear with me, it's not so scary!),

[FONT="Courier New"]static const char *ad1986a_models[AD1986A_MODELS] = {
        [AD1986A_6STACK]        = "6stack",
        [AD1986A_3STACK]        = "3stack",
*        [AD1986A_LAPTOP]        = "laptop",*
**        [AD1986A_LAPTOP_EAPD]   = "laptop-eapd",**
        [AD1986A_LAPTOP_AUTOMUTE] = "laptop-automute",
        [AD1986A_ULTRA]         = "ultra",
        [AD1986A_SAMSUNG]       = "samsung",
        [AD1986A_SAMSUNG_P50]   = "samsung-p50",
};

static struct snd_pci_quirk ad1986a_cfg_tbl[] = {
        SND_PCI_QUIRK(0x103c, 0x30af, "HP B2800", AD1986A_LAPTOP_EAPD),
        SND_PCI_QUIRK(0x1043, 0x1153, "ASUS M9", AD1986A_LAPTOP_EAPD),
        SND_PCI_QUIRK(0x1043, 0x11f7, "ASUS U5A", AD1986A_LAPTOP_EAPD),
        SND_PCI_QUIRK(0x1043, 0x1213, "ASUS A6J", AD1986A_LAPTOP_EAPD),
        SND_PCI_QUIRK(0x1043, 0x1263, "ASUS U5F", AD1986A_LAPTOP_EAPD),
**_        SND_PCI_QUIRK(0x1043, 0x1297, "ASUS Z62F", AD1986A_LAPTOP_EAPD),_**
        SND_PCI_QUIRK(0x1043, 0x12b3, "ASUS V1j", AD1986A_LAPTOP_EAPD),
        SND_PCI_QUIRK(0x1043, 0x1302, "ASUS W3j", AD1986A_LAPTOP_EAPD),
[/FONT]

[Source]("http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=sound/pci/hda/patch_analog.c;hb=HEAD#l1071")

Your Alsa-info.sh file mentions the device IDs:

[FONT="Century Gothic"]00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 1043:1297
[/FONT]

which can be rewritten as '0x1043, 0x1297'. These correspond to the 'quirk' line shown as bold and underline above, which automatically configures for your laptop the model to 'laptop-eapd' instead of 'laptop'.

If there is a System76 engineer reading this, then what needs to be done is verify whether the line 

[FONT="Courier New"]SND_PCI_QUIRK(0x1043, 0x1297, "ASUS Z62F", AD1986A_LAPTOP_EAPD),[/FONT]

is really right.

Because for your case with your laptop, it should be

[FONT="Courier New"]SND_PCI_QUIRK(0x1043, 0x1297, "ASUS Z62F", AD1986A_LAPTOP),[/FONT]

---

### Post by dgermann on 2010-08-05
simosx--

Well, I just changed it to "laptop-eapd" and rebooted, and I still have sound. So they both seem to work. Question then is, which is the preferred entry?

Thanks for continuing to follow up on this.

Does System76 already have this solution logged somewhere?

---

### Post by isantop on 2010-08-06
We haven't seen this issue before, and it doesn't appear to be an across-the-board issue, so I think it's a bit localized to your machine. However, we'll keep this in mind in case another user has this issue.

---

### Post by dgermann on 2010-08-07
isantop--

Thanks! Hopefully it will help others.

Which of the two entries (or of all 6 that might work) is the preferred one to choose?

Thank you, isantop!

---

### Post by thomasaaron on 2010-08-09
We'll image a machine and see what line it uses by default. My help is on vacation this week, so if you don't hear from us by Monday, please bump.

---

### Post by dgermann on 2010-08-09
Thanks, Tom!

---

### Post by dgermann on 2010-08-17
Tom--

You wanted to be bumped about this, this week. ):P

---

