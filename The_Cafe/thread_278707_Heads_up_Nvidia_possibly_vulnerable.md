---
title: "Heads up: Nvidia possibly vulnerable"
date: 2006-10-16
forum: The Cafe
---

### Post by towsonu2003 on 2006-10-16
I'm directly copy pasting: 
> 
The NVIDIA Binary Graphics Driver for Linux is vulnerable to a
   buffer overflow that allows an attacker to run arbitrary code as
   root.

from [http://download2.rapid7.com/r7-0025/](http://download2.rapid7.com/r7-0025/)

just wanted to make sure you know :)

[SIZE="1"]PS. yes, I saw it on slashdot ;) [/SIZE]

Note: this is being tracked as a bug at [https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034)
Note2: the open source nv driver is fine. 
Note3: if nvidia has this, I can't imagine what fglrx has... ouch...

---

### Post by Animortis on 2006-10-17
Rapid7 posted [this flaw]("http://download2.rapid7.com/r7-0025/") today, along with how to do it, and it appeared in [OSnews.com]("http://www.osnews.com/") as a security exploit. 

It's an exploit that allows the takeover and root access of a system running nvidia drivers. It's an old exploit that nvidia had never gotten around to fixing.

So, how seriously should we be taking this exploit? I have switched to nv drivers for now, and while I prefer open-source stuff whenever possible, the performance of the proprietary drivers cannot be ignored. Should we wait for the fixed drivers to update in the repos (Could take weeks, months) or should we ignore this exploit since it's been out since 2004 and it's not caused any problems before? (Though posting the exploit should encourage faster fixing, it'll also encourage more exploitation.)

I miss my linux-based games that require 3d accelleration.

I am looking for non-FUD-based opinions. The site OSNews links, Kernel Trap, has discussion areas and they're full of trolls and flames. I am looking for real opinions here.

I am not the most technical user, but I know some things. Let's try to keep it in (complex) English, please.

---

### Post by kerry_s on 2006-10-17
I use nvidia and i ain't worried. Also linux is not on the list->

PROBABLY VULNERABLE:
    o NVIDIA Driver for FreeBSD
    o NVIDIA Driver for Solaris
    o Earlier versions

FreeBSD and Solaris is different than what ubuntu uses.

---

### Post by Zeddicus on 2006-10-17
> **kerry_s said:**
> I use nvidia and i ain't worried. Also linux is not on the list->

PROBABLY VULNERABLE:
    o NVIDIA Driver for FreeBSD
    o NVIDIA Driver for Solaris
    o Earlier versions


   KNOWN VULNERABLE:
    o NVIDIA Driver For Linux v8774
    o NVIDIA Driver For Linux v8762

;)

---

### Post by kerry_s on 2006-10-17
Da, i really gotta start reading instead of skimming through ](*,) or start just doing one thing at a time.LOL I've got duel monitors and i use them :mrgreen:

---

### Post by peter07 on 2006-10-17
I think switching to "nv" is good idea ( that means changing the xorg.conf file or I need to change something else too  :confused: ?)

---

### Post by chaosgeisterchen on 2006-10-17
Doesn't seem all too good what one is reading here...

but how come that nVidia drivers act as they seem to do?

---

### Post by kerry_s on 2006-10-17
I don't know i took the test but didn't get no crash.

-> [http://nvidia.com/content/license/location_0605.asp?url=';a='a';i=18;while(i--)a%2b=a;location=a;//]("http://nvidia.com/content/license/location_0605.asp?url=';a='a';i=18;while(i--)a%2b=a;location=a;//")

---

### Post by deepwave on 2006-10-17
A buffer overflow security flaw for any software is a VERY serious issue.  It doesn't take much to exploit, and compromise the system.  All you need is a shellcode to overwrite the buffer, and poff!  One remote shell running.  And the shell will run the permissions of the compromised program.

In this case since the nvidia driver runs as root, so a shell run from this exploit would run with root's permissions.

---

### Post by woedend on 2006-10-17
is the 9xxx series affected?  its not listed, and what im using.

---

### Post by Zeddicus on 2006-10-17
> **woedend said:**
> is the 9xxx series affected?  its not listed, and what im using.

Supposedly, it's fixed in the beta 9xxx drivers.

---

### Post by JamesB on 2006-10-17
This link seems to show that it has been fixed in the Beta version 9xxx.
Beware, there is a link on this page that could crash your X if you are using firefox, not so opera:

[http://kerneltrap.org/node/7228#comment-200983](http://kerneltrap.org/node/7228#comment-200983)

Here there is a suggested work around:

[http://www.nvnews.net/vbulletin/showthread.php?t=78322](http://www.nvnews.net/vbulletin/showthread.php?t=78322)

also however as most distros have X remote session disabled by default, then unless you are using it, you are safe.

---

### Post by asimon on 2006-10-17
> **Zeddicus said:**
> Supposedly, it's fixed in the beta 9xxx drivers.
But what about updated legacy drivers? There are still machines with older NVIDIA cards in use. How NVIDIA deals with this issue doesn't impress me. I am disappointed.

---

### Post by zenwhen on 2006-10-17
> **kerry_s said:**
> I don't know i took the test but didn't get no crash.

-> [http://nvidia.com/content/license/location_0605.asp?url=';a='a';i=18;while(i--)a%2b=a;location=a;//]("http://nvidia.com/content/license/location_0605.asp?url=';a='a';i=18;while(i--)a%2b=a;location=a;//")

I can confirm that this test crashed my X server when I used Firefox, and did not crash my X server after I updated to the beta driver. If we are going to  keep the proprietary driver in the repos, the beta driver should be used.

The fact that this worked in Firefox and not Opera with this link does not mean that there is no way to exploit this in Opera.

---

### Post by jamespi on 2006-10-17
Does anyone know if this (WARNING! SEE BELOW* BEFORE CLICKING THIS LINK: [http://kerneltrap.org/node/7228](http://kerneltrap.org/node/7228)) affects the Repo versions of the Nvidia drivers? I have Dapper, but I imagine this will need to be checked for other releases too. 

Apparently Nvidia have released fixed drivers ([http://www.nvidia.com/object/linux_display_ia32_1.0-9626.html)](http://www.nvidia.com/object/linux_display_ia32_1.0-9626.html)). Can these be added to the Repo's then pushed out as a update, or will we have to manually install them?

*[B]Someone added a comment to that article with a link to an exploit for a firefox bug. the comment reads:
 "Here is nice special link the authors of the advisory have shown a few people who say this "this vuln is primarily local". 
DONT CLICK IT.[/B]

---

### Post by bastiegast on 2006-10-17
> **woedend said:**
> is the 9xxx series affected?  its not listed, and what im using.

I use them too, When are these drivers gonna be out of beta? Cant seem to find it anywhere.

---

### Post by MKR. on 2006-10-17
Why is the noscript plugin not included in a default Firefox install?

So handy. :confused:

---

### Post by aurelieng on 2006-10-17
Is the nvidia beta driver available as a deb package for dapper ?

---

### Post by not-a-bot on 2006-10-17
@MKR

You are aware, that NoScript wouldn't change anything at all? This is not a Javascript issue!

@all

This is a very serious flaw and I personally would hope that the 9xxx-series drivers, that have this vulnerability fixed, will be made available in the repositories (and included in Edgy) as soon as possible. Most known bugs in these beta-drivers are related to the new features that cannot be used with Xorg 7.0 (and therefor in the default Dapper setup) anyways.

For the legacy driver ... I have no idea ...

---

### Post by Polygon on 2006-10-17
> **MKR. said:**
> Why is the noscript plugin not included in a default Firefox install?

So handy. :confused:

noscript couldent prevent against that, as i believe the point is that if the drivers render the text in that url, which is a line of code supposedly creating a bufferoverflow, its exploiting the exploit that we are talking about in this topic

---

### Post by not-a-bot on 2006-10-17
> **aurelieng said:**
> Is the nvidia beta driver available as a deb package for dapper ?

As far as I know ... they aren't any packages, at least not officially. And using the nvidia-installer or unofficial packages is a royal pain in the rectum because they need to be updated or reinstalled after every kernelupdate and may conflict with other closed-source-kernel-add-ons e.g. for wireless adapters.
I wish there would be officially maintained 9xxx-drivers for Ubuntu.

---

### Post by DoctorMO on 2006-10-17
This problem shows us the problems with propritory drivers. people keep on harping on about how including propritory code isn't so bad.

But it _is_ bad because no one here no matter how good their skill can fix this issue.

We should write to nVidia to get them to open source their drivers so we can make use of it and make it safe. no way would this kind of bug exist in an open sourced version for so long.

---

### Post by dannyboy79 on 2006-10-17
can some1 tell me how to quickly identify which version of the nvidia driver I am running? I have a GeForce 6200. is that using the newest beta driver? is there a way to tell me by typing something into a terminal? cause when I go into my xorg.conf, all it says is driver: nvidia, I think. ( i am not at home?)

---

### Post by aurelieng on 2006-10-17
@dannyboy79: type in a terminal :

grep "NVIDIA X Driver" /var/log/Xorg.0.log

---

### Post by carlgm on 2006-10-17
> **DoctorMO said:**
> We should write to nVidia to get them to open source their drivers so we can make use of it and make it safe. no way would this kind of bug exist in an open sourced version for so long.

Send the letter to yourself, first class stamp. It would be more useful.

I wish people would stop going on about the fact that the main nvidia drivers are closed source. There is an optional open source driver available, although still without 3D acceleration I believe.

Are you using the drivers from nvidia.com or apt-get?

---

### Post by evilghost on 2006-10-17
Yes it affects the drivers in the Repo.  It's only patched in the 1.0.9XXX series.  You can mitigate the vulnerability by setting RenderAccel to false.

[http://www.nvnews.net/vbulletin/showpost.php?p=1027960&postcount=2](http://www.nvnews.net/vbulletin/showpost.php?p=1027960&postcount=2)

---

### Post by Perfect Storm on 2006-10-17
> **not-a-bot said:**
> As far as I know ... they aren't any packages, at least not officially. And using the nvidia-installer or unofficial packages is a royal pain in the rectum because they need to be updated or reinstalled after every kernelupdate and may conflict with other closed-source-kernel-add-ons e.g. for wireless adapters.
I wish there would be officially maintained 9xxx-drivers for Ubuntu.

9xxx drivers are only for card specifically for Quadro Plex setups, ofcause if you have such card I envy you :mrgreen:

---

### Post by PriceChild on 2006-10-17
> **Artificial Intelligence said:**
> 9xxx drivers are only for card specifically for Quadro Plex setups, ofcause if you have such card I envy you :mrgreen:That's the official release... 9626

9625 betas can be found here for all: [http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html)

---

### Post by evilghost on 2006-10-17
> **Artificial Intelligence said:**
> 9xxx drivers are only for card specifically for Quadro Plex setups, ofcause if you have such card I envy you :mrgreen:

This is simply not true, I am running a Go FX5700 with 1.0.9626.  As mentioned before disabling RenderAccel will mitigate this vulnerability or you can upgrade to the 1.0.9XXX series driver.  

1.0.9626 Changelog:
    * Adds support for NVIDIA Quadro Plex configurations"

1.0.9525 Changelog:
    * Added initial support for GLX_EXT_texture_from_pixmap.
    * Added new "Display Configuration" page in nvidia-settings.
    * Improved workstation OpenGL performance in Xinerama.
    * Added support for NVIDIA Quadro Plex.
    * Added support for Quad SLI.
    * Improved X driver error recovery.
    * Improved workstation overlay performance.
    * Added SMBus functionality to the Linux/i2c interface.
    * Fixed DFP scaling support.
    * Added support for OpenGL 2.1.
    * Added new "TwinViewXineramaInfoOrder" X configuration option to control the order of display devices when in TwinView. 

The 1.0.9626 driver is available here:  [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9626](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9626)

The ReadMe located at [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/README.txt) clearly states the following cards are supported:

```

NVIDIA chip name                      Device PCI ID
    ----------------------------------    ----------------------------------
    GeForce 6800 Ultra                    0x0040
    GeForce 6800                          0x0041
    GeForce 6800 XE                       0x0043
    GeForce 6800 XT                       0x0044
    GeForce 6800 GT                       0x0045
    GeForce 6800 GT                       0x0046
    GeForce 6800 GS                       0x0047
    GeForce 6800 XT                       0x0048
    Quadro FX 4000                        0x004E
    GeForce 7800 GTX                      0x0090
    GeForce 7800 GTX                      0x0091
    GeForce 7800 GT                       0x0092
    GeForce 7800 GS                       0x0093
    GeForce Go 7800                       0x0098
    GeForce Go 7800 GTX                   0x0099
    Quadro FX 4500                        0x009D
    GeForce 6800 GS                       0x00C0
    GeForce 6800                          0x00C1
    GeForce 6800 LE                       0x00C2
    GeForce 6800 XT                       0x00C3
    GeForce Go 6800                       0x00C8
    GeForce Go 6800 Ultra                 0x00C9
    Quadro FX Go1400                      0x00CC
    Quadro FX 3450/4000 SDI               0x00CD
    Quadro FX 1400                        0x00CE
    GeForce 6800/GeForce 6800 Ultra       0x00F0
    GeForce 6600/GeForce 6600 GT          0x00F1
    GeForce 6600                          0x00F2
    GeForce 6200                          0x00F3
    GeForce 6600 LE                       0x00F4
    GeForce 7800 GS                       0x00F5
    GeForce 6800 GS                       0x00F6
    Quadro FX 3400/4400                   0x00F8
    GeForce 6800 Ultra                    0x00F9
    GeForce PCX 5750                      0x00FA
    GeForce PCX 5900                      0x00FB
    Quadro FX 330/GeForce PCX 5300        0x00FC
    Quadro NVS 280 PCI-E/Quadro FX 330    0x00FD
    Quadro FX 1300                        0x00FE
    GeForce PCX 4300                      0x00FF
    GeForce2 MX/MX 400                    0x0110
    GeForce2 MX 100/200                   0x0111
    GeForce2 Go                           0x0112
    Quadro2 MXR/EX/Go                     0x0113
    GeForce 6600 GT                       0x0140
    GeForce 6600                          0x0141
    GeForce 6600 LE                       0x0142
    GeForce 6600 VE                       0x0143
    GeForce Go 6600                       0x0144
    GeForce 6610 XL                       0x0145
    GeForce Go 6600 TE/6200 TE            0x0146
    GeForce Go 6600                       0x0148
    GeForce Go 6600 GT                    0x0149
    Quadro NVS 440                        0x014A
    Quadro FX 550                         0x014C
    Quadro FX 540                         0x014E
    GeForce 6200                          0x014F
    GeForce 6500                          0x0160
    GeForce 6200 TurboCache(TM)           0x0161
    GeForce Go 6200                       0x0164
    Quadro NVS 285                        0x0165
    GeForce Go 6400                       0x0166
    GeForce Go 6200                       0x0167
    GeForce Go 6400                       0x0168
    GeForce4 MX 460                       0x0170
    GeForce4 MX 440                       0x0171
    GeForce4 MX 420                       0x0172
    GeForce4 MX 440-SE                    0x0173
    GeForce4 440 Go                       0x0174
    GeForce4 420 Go                       0x0175
    GeForce4 420 Go 32M                   0x0176
    GeForce4 460 Go                       0x0177
    Quadro4 550 XGL                       0x0178
    GeForce4 440 Go 64M                   0x0179
    Quadro NVS                            0x017A
    Quadro4 500 GoGL                      0x017C
    GeForce4 410 Go 16M                   0x017D
    GeForce4 MX 440 with AGP8X            0x0181
    GeForce4 MX 440SE with AGP8X          0x0182
    GeForce4 MX 420 with AGP8X            0x0183
    GeForce4 MX 4000                      0x0185
    Quadro4 580 XGL                       0x0188
    Quadro NVS with AGP8X                 0x018A
    Quadro4 380 XGL                       0x018B
    Quadro NVS 50 PCI                     0x018C
    GeForce2 Integrated GPU               0x01A0
    GeForce 7300 LE                       0x01D1
    Quadro NVS 110M                       0x01D7
    GeForce Go 7300                       0x01D7
    GeForce Go 7400                       0x01D8
    Quadro NVS 110M                       0x01DA
    Quadro NVS 120M                       0x01DB
    Quadro FX 350M                        0x01DC
    Quadro FX 350                         0x01DE
    GeForce 7300 GS                       0x01DF
    GeForce4 MX Integrated GPU            0x01F0
    GeForce3                              0x0200
    GeForce3 Ti 200                       0x0201
    GeForce3 Ti 500                       0x0202
    Quadro DCC                            0x0203
    GeForce 6800                          0x0211
    GeForce 6800 LE                       0x0212
    GeForce 6800 GT                       0x0215
    GeForce 6800 XT                       0x0218
    GeForce 6150                          0x0240
    GeForce 6150 LE                       0x0241
    GeForce 6100                          0x0242
    GeForce4 Ti 4600                      0x0250
    GeForce4 Ti 4400                      0x0251
    GeForce4 Ti 4200                      0x0253
    Quadro4 900 XGL                       0x0258
    Quadro4 750 XGL                       0x0259
    Quadro4 700 XGL                       0x025B
    GeForce4 Ti 4800                      0x0280
    GeForce4 Ti 4200 with AGP8X           0x0281
    GeForce4 Ti 4800 SE                   0x0282
    GeForce4 4200 Go                      0x0286
    Quadro4 980 XGL                       0x0288
    Quadro4 780 XGL                       0x0289
    Quadro4 700 GoGL                      0x028C
    GeForce 7900 GTX                      0x0290
    GeForce 7900 GT                       0x0291
    GeForce Go 7900 GS                    0x0298
    GeForce Go 7900 GTX                   0x0299
    Quadro FX 2500M                       0x029A
    Quadro FX 1500M                       0x029B
    Quadro FX 5500                        0x029C
    Quadro FX 3500                        0x029D
    Quadro FX 1500                        0x029E
    Quadro FX 4500 X2                     0x029F
    GeForce 7600 GS                       0x02E1
    GeForce FX 5800 Ultra                 0x0301
    GeForce FX 5800                       0x0302
    Quadro FX 2000                        0x0308
    Quadro FX 1000                        0x0309
    GeForce FX 5600 Ultra                 0x0311
    GeForce FX 5600                       0x0312
    GeForce FX 5600XT                     0x0314
    GeForce FX Go5600                     0x031A
    GeForce FX Go5650                     0x031B
    Quadro FX Go700                       0x031C
    GeForce FX 5200                       0x0320
    GeForce FX 5200 Ultra                 0x0321
    GeForce FX 5200                       0x0322
    GeForce FX 5200LE                     0x0323
    GeForce FX Go5200                     0x0324
    GeForce FX Go5250                     0x0325
    GeForce FX 5500                       0x0326
    GeForce FX 5100                       0x0327
    GeForce FX Go5200 32M/64M             0x0328
    Quadro NVS 280 PCI                    0x032A
    Quadro FX 500/600 PCI                 0x032B
    GeForce FX Go53xx                     0x032C
    GeForce FX Go5100                     0x032D
    GeForce FX 5900 Ultra                 0x0330
    GeForce FX 5900                       0x0331
    GeForce FX 5900XT                     0x0332
    GeForce FX 5950 Ultra                 0x0333
    GeForce FX 5900ZT                     0x0334
    Quadro FX 3000                        0x0338
    Quadro FX 700                         0x033F
    GeForce FX 5700 Ultra                 0x0341
    GeForce FX 5700                       0x0342
    GeForce FX 5700LE                     0x0343
    GeForce FX 5700VE                     0x0344
    GeForce FX Go5700                     0x0347
    GeForce FX Go5700                     0x0348
    Quadro FX Go1000                      0x034C
    Quadro FX 1100                        0x034E
    GeForce 7600 GT                       0x0391
    GeForce 7600 GS                       0x0392
    GeForce Go 7600                       0x0398
    Quadro FX 560                         0x039E


Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.


    NVIDIA chip name                      Device PCI ID
    ----------------------------------    ----------------------------------
    RIVA TNT                              0x0020
    RIVA TNT2/TNT2 Pro                    0x0028
    RIVA TNT2 Ultra                       0x0029
    Vanta/Vanta LT                        0x002C
    RIVA TNT2 Model 64/Model 64 Pro       0x002D
    Aladdin TNT2                          0x00A0
    GeForce 256                           0x0100
    GeForce DDR                           0x0101
    Quadro                                0x0103
    GeForce2 GTS/GeForce2 Pro             0x0150
    GeForce2 Ti                           0x0151
    GeForce2 Ultra                        0x0152
    Quadro2 Pro                           0x0153

```

---

### Post by Perfect Storm on 2006-10-17
Ah, okay. Then I misunderstood the release note.

---

### Post by evilghost on 2006-10-17
> **Artificial Intelligence said:**
> Ah, okay. Then I misunderstood the release note.

No problem, I just wanted to ensure everyone fully understood the situation, there seems to be a fair amount of FUD around this issue. :)

---

### Post by PriceChild on 2006-10-17
> **not-a-bot said:**
> I wish there would be officially maintained 9xxx-drivers for Ubuntu.One could argue this is a serious security fix which should be added :P Doubt you'd win though ;)

---

### Post by OffHand on 2006-10-17
I just tried the link on a up-to-date Edgy install with Firefox.
Nothing happened. I am not running the beta drives and direct rendering is enabled.

$ grep "NVIDIA X Driver" /var/log/Xorg.0.log
NVIDIA X Driver  1.0-8774  Tue Aug  1 20:56:50 PDT 2006

$ glxinfo | grep rendering
direct rendering: Yes

---

### Post by dannyboy79 on 2006-10-17
WOW, I am running the 8762 driver and my sudo lspci -v states:
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc.: Unknown device 2144
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 169
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0
Could I run the latest and greatest like evilghost is since he has an older card than i do? I think i merely installed what was in Synaptic! :-(

---

### Post by evilghost on 2006-10-17
> **dannyboy79 said:**
> WOW, I am running the 8762 driver and my sudo lspci -v states:
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc.: Unknown device 2144
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 169
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0
Could I run the latest and greatest like evilghost is since he has an older card than i do? I think i merely installed what was in Synaptic! :-(

Yes, you can run 1.0.9626.  I compiled mine from the nVidia package.

---

### Post by not-a-bot on 2006-10-17
> **PriceChild said:**
> One could argue this is a serious security fix which should be added :P Doubt you'd win though ;)

Well, facts are that the currently used binary drivers in Dapper and Edgy have a very, very serious security flaw. Since they are not open source this cannot be easily be fixed.
There are only two possible options for Edgy before shipping it, if security is taken seriously by the developers:
* Remove the affected nvidia-package and ship it without the binary driver.
* Replace it with a driver from the 9xxx-series that does NOT have this security flaw.

I can see only one satisfactory option for Dapper:
* Update the affected package to the current 9xxx-drivers as soon as possible to close this gaping hole!


I understand why you are laughing about this issue, god beware that we get a feature update together with a security update. But currently there seems to be no good way around that.

I don't really see a big problem in issuing a security update to the 9xxx-drivers, they don't seem to be less stable than the currently used drivers in most cases and even bring optional functionality that users can benefit from if they want.

---

### Post by Colonel Kilkenny on 2006-10-17
Can someone explain what code in browser url has to do with Nvidia? What is the mechanism behind that exploit? I understand that browsers with unsufficient security measures can execute that code but how can it crash X? Why doesn't it crash just the browser?

As you can see, I'm quite out of these sort of things...

Btw. I think Opera scans url's for exploits (mainly because SQL injection I think) and that's why it won't work at least in that form in Opera.

---

### Post by brt on 2006-10-17
does anyone know when we can expect this driver in the repos?

---

### Post by dabdine on 2006-10-17
FireFox doesn't properly sanitize (in other words, clip to a certain length) strings entered in its controls, or even text rendered in html input fields, etc.  This is why you can use FireFox as an attack vector and not Konqueror (or Opera).  One could argue this is an unnecessary risk that Mozilla could easily remove from the browser, but it is not a vulnerability in the browser itself.

-Derek

---

### Post by OffHand on 2006-10-17
> **dabdine said:**
> FireFox doesn't properly sanitize (in other words, clip to a certain length) strings entered in its controls, or even text rendered in html input fields, etc.  This is why you can use FireFox as an attack vector and not Konqueror (or Opera).  One could argue this is an unnecessary risk that Mozilla could easily remove from the browser, but it is not a vulnerability in the browser itself.

-Derek

So why didn't the test page do anything at all on my machine using Firefox?

---

### Post by dabdine on 2006-10-17
Either:
  * You are not using the 8774 or 8762 driver.  Check nvidia-settings.
  * You (for some reason) do not have glyph rendering acceleration enabled.

---

### Post by OffHand on 2006-10-17
> **dabdine said:**
> Either:
  * You are not using the 8774 or 8762 driver.  Check nvidia-settings.
  * You (for some reason) do not have glyph rendering acceleration enabled.

$ grep "NVIDIA X Driver" /var/log/Xorg.0.log
NVIDIA X Driver 1.0-8774 Tue Aug 1 20:56:50 PDT 2006

$ glxinfo | grep rendering
direct rendering: Yes

What is glyph rendering?

---

### Post by glotz on 2006-10-18
And what about legacy card users?

---

### Post by evilghost on 2006-10-18
> **glotz said:**
> And what about legacy card users?

Legacy card users are only affected if RenderAccel is explicitly enabled.

Basically, this bug can be mitigated by turning off RenderAccel.

1.0.9XXX - The bug is corrected.
1.0.8XXX - RenderAccel is on by default.
1.0.7XXX - RenderAccess is off by default.

See:
[http://www.nvnews.net/vbulletin/showpost.php?p=1028769&postcount=13](http://www.nvnews.net/vbulletin/showpost.php?p=1028769&postcount=13)
[http://www.nvnews.net/vbulletin/showpost.php?p=1030689&postcount=15](http://www.nvnews.net/vbulletin/showpost.php?p=1030689&postcount=15)

---

### Post by PriceChild on 2006-10-18
I'm expecting the fixed packages to make it to the dapper repos because it is such a huge vulnerability...

Hope so anyway ;)

---

### Post by evilghost on 2006-10-18
> **PriceChild said:**
> I'm expecting the fixed packages to make it to the dapper repos because it is such a huge vulnerability...

Hope so anyway ;)

AFAIK NVIDIA doesn't have a patch for the legacy or 1.0.8XXX drivers as 1.0.9625+ patches this.  When you say "fixed package" do you mean the **Beta** 1.0.9626?  Either way, the new 1.0.9XXX drivers aren't without bugs:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by glotz on 2006-10-18
> **evilghost said:**
> Legacy card users are only affected if RenderAccel is explicitly enabled.Thank you for your answer!

Helping out newbies and not pirating software? Maybe you're not so evil after all? :mrgreen:

---

### Post by evilghost on 2006-10-18
> **glotz said:**
> Thank you for your answer!

Helping out newbies and not pirating software? Maybe you're not so evil after all? :mrgreen:

Hahaha, I'm just glad to help.  :mrgreen:

---

### Post by jamespi on 2006-10-19
i dont play games on ubuntu or do any 3d stuff, so i assume turning off render accel will not impact anything i do, or am i wrong? still its a bit of a drag for those that do, so hopefully nvidia will get there asses in gear and get those beta drivers finished. certainly when edgy comes out and people want to have the 3d desktop....

---

### Post by dr_d on 2006-10-19
woah...

the first really big vulnerability i've ever experienced with ubuntu and it just happened to occur in the *one* piece of closed-source software in my entire system. the mind boggles.

---

### Post by manatawady on 2006-10-20
Heres nVidias answer to the the questions asked about the exploit:
[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=1971](http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=1971)

Within that they say:
"We encourage users of NVIDIA graphics driver version 1.0-8762  or 1.0-8774 to upgrade to 1.0-8776, available here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)            "

So rather update repo with stable release of the driver with bugfix than the beta.

Cheers, mana

---

### Post by ice60 on 2006-10-20
there's a patched update now. just follow the link for your system.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by towsonu2003 on 2006-10-21
and it seems Edgy will come with an updated nvidia driver that is not vulnerable. if that happens, the fix may be backported to dapper and other supported releases.

---

### Post by John.Michael.Kane on 2006-10-22
So has anyone seen the patch ice60 linked to in the dapper/edgy repo's?

---

### Post by towsonu2003 on 2006-10-22
> **SD-Plissken said:**
> So has anyone seen the patch ice60 linked to in the dapper/edgy repo's?

see [https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034/comments/37](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034/comments/37)

---

### Post by John.Michael.Kane on 2006-10-22
Thanks towsonu2003..

---

### Post by ebutton on 2006-10-25
Would Ubuntu be vulnerable to this one?  I don't know for certain, but I didn't risk it.  When I checked my /etc/X11/xorg.conf, I see that I'm using driver "nv".  I hope that means I'm safe.

Security Threat Watch
   Number 154
   Monday, October 23, 2006
   Created for you by Network Computing & Neohapsis


This week, an interesting vulnerability in nVidia's Linux graphics
driver was released. The vulnerability could allow a remote attacker to
gain root access to any system using this driver and a carefully crafted
Web page. It is interesting because the only thing required for
exploitation is the ability to force the victim's graphics driver to
render a certain string of graphics that can be triggered by a malicious
font, flash movie or Java applet hosted by a Web page, e-mail or local
file. The most obvious avenue of remote attack is a malicious Web site
hosting the string of exploit graphics. By using a cross-site scripting
vulnerability, an attacker could even exploit victims through trusted
Web sites. Security professionals often hold the class of
vulnerabilities known as cross-site scripting, or XSS, in contempt. This
week, however, these vulnerabilities could prove to be one of the
primary exploitation methods against the nVidia driver. It is
recommended that nVidia users either install the recently released
nVidia beta drivers (version 1.0.9625) or use the default nv driver
included with the Linux kernel.

---

### Post by ~LoKe on 2006-10-25
Hasn't this been known since 2004?  Anyways, I use the beta driver, so...

---

### Post by ebutton on 2006-10-25
Hi!  No, this one is new.  Regretfully, I didn't check the "Servers and Security" forum until AFTER I posted.  They are all over it.

I hope to have some redemption from having made reference to the xorg.conf file as a way to check one's system for the safe "nv" driver.

Good for you on being OK, too.

Regards,
EdB

---

### Post by John.Michael.Kane on 2006-10-26
Heres where they stand on this issue [https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034)

---

### Post by RJARRRPCGP on 2006-11-26
Can I be attacked just by being connected to the internet?

---

### Post by darkhatter on 2006-11-26
Ubuntu is going to come with Nvidia drivers default, then news of possible exploits comes up. Compaines start producing Mac OS X virus programs news about OS X virus start popping up everywhere. Something smells fishy ;)

---

### Post by towsonu2003 on 2006-11-26
Seems like the fix is already released for Dapper and Edgy: [https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/46034) (see status) so you shouldn't have any problems if you recently updated your system. Anyhow, assuming you still have the vulnerable driver:

> **RJARRRPCGP said:**
> Can I be attacked **just** by being connected to the internet?

probably no if you don't accept remote X connections: 
> 
   It is important to note that glyph data is supplied to the X server
   by the X client. Any remote X client can gain root privileges on
   the X server using the proof of concept program attached.

   It is also trivial to exploit this vulnerability as a DoS by causing
   an existing X client program (such as Firefox) to render a long text
   string. It may be possible to use Flash movies, Java applets, or
   embedded web fonts to supply the custom glyph data necessary for
   reliable remote code execution.

   A simple HTML page containing an INPUT field with a long value is
   sufficient to demonstrate the DoS.

I don't think anyone out there could send some glyph data to your X client just because you're online. But then again, I don't really know what I'm talking about...

---

