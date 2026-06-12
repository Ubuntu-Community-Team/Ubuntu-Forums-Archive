---
title: "Fully functioning linux laptop?"
date: 2008-07-30
forum: The Cafe
---

### Post by phidia on 2008-07-30
I'm not going to put this out perfectly-but I'm curious about several somewhat complex laptop issues. I also think this might be useful to the community here because the question of what laptop to use with linux keeps coming up on the forums.

From being here and reading many laptop threads it appears that the consensus is that intel equipped laptops are the most trouble free and easily configured. By intel equipped I mean intel cpu, gpu, & wireless card. There are of course reports of problems with intel based laptops but generally they are easier to get _fully_ functioning*. Fully functioning here means *all* of the features the laptop supports work.

To attempt to learn more I'm creating a poll. Basically linux, not necessarily Ubuntu & variants, has worked for you on a laptop and also _honestly_ all the features of the laptop work or they don't. I know that there is a laptop testing page for Ubuntu but there is not enough specific info at that wiki IMO.

Once people, hopefully, vote on the poll I think it would be very useful if they also post comments with specific hardware that was a problem or worked well. Commenting about biases is fine too.

I have an older Apple Powerbook that I'm using right now-it just works. I also have a lot of open source on it and even ran linux on it through Apple's X11. My expectation was to get linux working on a laptop as well as my Powerbook works-trying to do just that with a HP Pavilion dv6707us it never happened.

---

### Post by sergiom99 on 2008-07-30
I voted "Linux works completely with my laptop-I will post my hardware specifics" b/c, AFAIK, the only thing that's not working is the MS card reader, but there's no kernel support for them yet, so everything is ok.

---

### Post by SpaceCowboyMA on 2008-07-30
Dell Latitude 630 (Model PP18L - A06 BIOS)

Only issue I've found is WEP via network-manager, but WiFi hardware is fine (can do Open or WPA APs no problem). 

Attached my dmesg, package and source lists...

---

### Post by jacobh on 2008-07-30
-- linux works partially, posting specific problems --

ATI Mobility Radeon X1400 graphics card doesn't really work. It works if you completely turn off desktop effects, but otherwise you get flickering graphics in OpenGL applications I think.

Sound was extremely difficult to get working correctly, and I still have problems with it. Can't play sound in games and in Songbird simultaneously. Something about my particular motherboard that doesn't work too well with ALSA.

But despite this, I managed to get Linux working on a laptop without any prior experience or excessive computer skills, and I enjoy it much more than I did Windows. Performance is way up as well.. everything loads and closes much quicker. However, battery time took quite a drop (but I think it's just because I haven't installed any power-saving options or applications - any ideas?).

---

### Post by jimv on 2008-07-30
Gateway MT3814

Problems that had to be resolved, but are fine now:

Wireless card is RTL8185, needs Ndiswrapper to work.
Brightness keys didn't work until I patched DSDT by replacing "Windows 2006" with "Linux"

---

### Post by stchman on 2008-07-30
I have the Toshiba A205-S5859.  Everything works.

---

### Post by aysiu on 2008-07-30
My previous laptop, which I've since given away worked perfectly with Ubuntu out-of-the-box. It was a Dell Inspiron 500m. The only thing I'll say is that when I bought it, it didn't have a wireless card inside. So I made sure to buy a Linux-compatible wireless card when I got one (Intel Pro Wireless 2200, thanks to recommendations from these forums).

I know run an Eee PC. Don't know if it counts as a laptop. It ran perfectly with Xandros as preconfigured by Asus. I installed eeeXubuntu on it, which included some Eee-specific tweaks, and it works almost perfectly, except that the boot time is now extremely slow, and resume from suspend doesn't work all the time any more.

---

### Post by Fire_Chief on 2008-07-30
I have a Lenovo Thinkpad T60 with Hardy running strong on it. I have not configured the fingerprint scanner or the function hotkeys and don't use the IR port so I'm not sure if it works or not. Other than that, the system is fantastic!

---

### Post by adamogardner on 2008-07-30
hi  this is my first computer and everything works great! All the troubles I had setting up were due to my ignorance and nothing with the computer or operating system.  It's a Pavillion DV6700.  Very handsome machine too.

---

### Post by tamoneya on 2008-07-30
problem free so far.  Lenovo T61.

---

### Post by silkstone on 2008-07-30
Acer 5612WLMi with Nvidia GeForce Go 7300. I've said it works perfectly but that's a slight exaggeration because the little media keys down the right hand side are not recognised, but I've never used them anyway.

---

### Post by steveneddy on 2008-07-30
Works perfectly:

System76 Serval Performance Type 1 (18 months old)
Intel Core 2 Duo
Nvidia, DVD, USB, Firewire, Sd Card reader, Intel wireless, web cam, sound
PCM-CIA cards

everything but the dial up modem

Laptop is actually a compal EL80

---

### Post by LittleLORDevil on 2008-07-30
No issues with the Dell E1505 and Ubuntu 8.04, previous versions have been hit or miss at times.

---

### Post by RiceMonster on 2008-07-30
I'm using a dell inspron 1520 and everything works, even hibernate and suspend (I'm not sure about blue tooth though, because I've never even used it in Windows).

I'm pretty much running all intel stuff - sound, graphics and wireless.

---

### Post by natarnsco on 2008-07-30
Mine has worked perfectly since I installed Ubuntu 7.10 last fall.  I switched to Ubuntu after using OpenSuSE 10.something for about six months and never getting the sound to work right and having to reconfigure the wireless card after every reboot.

Sony VAIO VGN-FS715W - Intel wireless & sound card.

---

### Post by original_jamingrit on 2008-07-30
It was also fully functional OOTB when I tried out the new Hardy release.

It's a three year old Toshiba MX40,  Intel 915 compatible graphics card.  For wireless, it uses the madwifi driver (the chipset isn't compatible with the new ath9k module Atheros recently released for free, and I haven't tried out ath5k yet).  Flawless OOTB support for graphics, sound, touchpad, USB, etc, even in Slackware.

So, yeah, everything works.  My next project for when I have time is getting the madwifi driver replaced with the free driver.  I also still need to install the drivers for the onboard winmodem, but I haven't needed to use dial-up since forever.  I also have a weird sort of infra-red thing on the side, but I don't even know what it's for.

---

### Post by billgoldberg on 2008-07-30
My 1.5 year old hp pavilion dv4000 (17 inch widescreen), works out of the box.

Everything works. Most likely because it almost completely intel based.

---

### Post by Darkade on 2008-07-30
In my Vaio laptop just the FN key don't work. anyway I worked around that and have other keyboard shortcuts like
SHIFT+ALT+UP instead of FN+F4   for volume up

---

### Post by desertboy on 2008-07-30
My HP Pavillion DV9000 (I think) works perfectly, only issue was I had to get the broadcom firmware and copy on myself (Gutsy did it for you) as broadcom restricted who could distribute the firmware. Everything else worked OOTB (I should say I run open suse on it and my experience was identical to Hardy.)

I'll post the specs as soon as my Mother gets off the bloody thing.

My EEEPC works perfectly but I downloaded a Xubuntu with drivers included so that's probably cheating.

off the top of my head

AMD64, ATI mobility graphics, broadcom wireless, intel ethernet & intel pcimodem, some AC97 sound chipset (Does that even really matter any more).

---

### Post by klange on 2008-07-30
> **silkstone said:**
> Acer 5612WLMi with Nvidia GeForce Go 7300. I've said it works perfectly but that's a slight exaggeration because the little media keys down the right hand side are not recognised, but I've never used them anyway.

Have you tried using the acerhk kernel module? I have a 5610 and all of my keys are recognized and work thanks to it. It also lets you use some of the LEDs...

The only thing that fails to function on my laptop is the card reader outside of SD and MMC cards.
Acer Aspire 5610 (US model = no camera), Intel "Centrio" (Core Duo) 1.73GHz, 120GB HDD, Intel GMA 945 graphics, Intel wireless (3945, it's a pain in the !#$ with the iwl3945 drivers, but it works), fairly standard DVD burner. Intel "HDA" audio.

All keyboard functions work except one button because I haven't taken the time to link it to anything. Had to manually build a keymap for X to get two of my keys working (a &#8364; and $ above my arrow keys). All FN keys work (except possibly my 'Switch Output Mode' key as I've never had time to thoroughly test it). S-Video out works, VGA out works, suspend/resume works. Wireless killswitch works (though under Intrepid A3 NetworkManager doesn't detect when you disable the kill switch. Regressions are annoying.) Most LEDs work fine (Caps lock, num lock, Wifi, I/O activity, power, battery) though I do have two more for Bluetooth and some other radio, while the switch works (I get "key not registered" feedback from X), the lights appear to do nothing and I can't access them with the acerhk module. All of my various audio inputs and outputs work.

So, what's that? No xD or MemoryStick and two LEDs that I have no use for.

**e**: I have a keycode registered to the otherwise functionless 'e' button, and as my display output switch button registers an unknown key in the log, I think it's safe to assume that it's just not doing anything because it expects the OS to handle it. May look into mapping that to something special.

---

### Post by imronak on 2008-07-30
Dell Vostro 1400. (No Nvidia)

With gutsy, wireless, sound (esp. mic) and sleep/wake required special tweaks.
Even after that sleep/wake didnt work

With Hardy and Intrpid, wireless and sound work very nicely and out of box.

Sleep still doesn work (why do i think, it is related to foxconn, the dedt tables interferring with the sleep process, this issues is around since ages.)

---

### Post by FuturePilot on 2008-07-30
HP Pavilion dv6500t everything works except for a bug with ehci_hcd which causes it to hang on resume from suspend. But having it automatically unload ehci_hcd before suspend and reload it afterwards fixes it. Other than that it works perfectly.

My Dell Inspiron 8200 works perfectly except that I can't use CPU scaling with it because it causes freezes with the Nvidia driver. But disabling powernowd fixes that. Everything else works perfectly.

---

### Post by Altur on 2008-07-30
My laptop (HP dv6604nr, AMD Athalon TK-55 processor, 1gb ram, nvidia integrated graphics, boradcom wireless)  The laptop is useable right out of the box with hardy, using the Restricted drivers manager, I have both wireless and full working 3D acceleration.  Pretty painless setup.  However, b43 (Broadcom driver) doesn't work for me as well as going the ndiswrapper route, but thats barely another two minutes of work.

---

### Post by bks on 2008-07-30
I checked that my laptop works partial, but it's really not that bad. The only thing that does not have full functionality is a set of four shortcut buttons located above the keyboard (web browser, email, help & user defined). I have a Gateway 400SD notebook (going on 6 years old!) so the support is pretty fantastic; I have no complaints. I just didn't want to say EVERYTHING works when technically it doesn't.

---

### Post by Jordanwb on 2008-07-30
Kubuntu works perfectly on my IBM T21

IBM Thinkpad T21
Intel P3 @ 800Mhz
256MB SDRAM PC100
20 GB Hard drive
WPC54G wifi card
S3 Savage 4 video chip

---

### Post by gn2 on 2008-07-30
[**Asus F9E-2P045C**]("http://tinyurl.com/6s3x4h") requires a line of text added to a config file for sound, replace network-manager and nm-applet with WICD to get WPA working, but that's it.
Even the webcam works.

```
sudo nano /etc/modprobe.d/alsa-base

add the following line to the end of this file:
options snd-hda-intel model=lenovo

save,and reboot.

```

---

### Post by jeremy1138 on 2008-07-30
Ubuntu works great on my laptop...  I have an HP dv5020us with the 1.8 GHz, 64 bit AMD Turion processor.  It has 1 GB of RAM, 128 MB of which is allocated to the onboard video card, an ATI Radeon Xpress 200M.  Wireless has been working great; my laptop has a Broadcom wireless card.  I have my laptop set up to dual boot with Windows XP.

---

### Post by miggols99 on 2008-07-30
The only problem I have is that Compiz and KDE 4's desktop effects don't work too well. Hoping for better Intel graphics drivers..

---

### Post by Naralas on 2008-07-30
My MSI Wind. Works great. Webcam is choppier on Ubuntu (but, believe it or not, I swear its clearer) than on XP.

Wireless requires some config, and you need to be willing to pendrive it to install, but that's easy as pie. Wiki is here [http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Option_2:_Compiling_Drivers_for_the_Supplied_Wireless_Card](http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Option_2:_Compiling_Drivers_for_the_Supplied_Wireless_Card)

I suggest following Option 2 for wireless and Option 2 for getting the OS installed. Keep in mind you will need to have a spare ethernet cable to shove into your Wind to get WiFi working, so those of you who are 100% wireless might have to take a few extra steps.

---

### Post by MaxIBoy on 2008-07-30
My only problem is that when I go into suspend, sound is disabled until I reboot. OpenGL is also glitchy as hell, but what do you expect with an Intel integrated chip?

---

### Post by Foster Grant on 2008-07-30
Modem (stupid winmodem).

And ACPI has stopped working correctly --- had it working in Hardy, but I turned on the kernel- and system-load messages and since then my laptop doesn't wake from suspend. :mad:

---

### Post by Laplace's Daemon on 2008-07-30
Mine is a Vostro 1400.  Core 2 Duo, intel Wifi, Nvidia graphics.  Everything works except the video-out, i.e., the laptop won't work with a projector.  I once posted a thread about this, but it promptly recieved 0 replies.

---

### Post by grossaffe on 2008-07-30
Everything works (that I've tried, at least) with my Dell Inspiron 1420.  I bought it before they started offering an Ubuntu version.
anyways, i've got it decked out with the following:
Core2 duo T7500 2.2 GHz
nVidia Geforce 8400GS 128MB graphics card
2 GB ram
A/B/G/N Wireless card
Bluetooth

---

### Post by phidia on 2008-07-30
I see some people even mentioned their winmodems. I wasn't trying to get that fussy when I put this up but sometimes people still do want those softmodems to work. 

IMO a laptop needs to be portable and that's why features like suspend/resume/hibernate are very appreciated. For instance I can close up my powerbook and pretty much be sure it will return to the state I left it when I open it. 

The HP Pavilion dv6707us -TK57 1.9Athlon, 2GB ram 7150M nvidia & Atheros AR5007EG wireless-that I am selling-works partially in linux. I used ndiswrapper and later on madwifi to enable the wireless fussy to get working but not a big deal. 

The big deal is that with ndiswrapper or madwifi resume fails. I spent a lot of time reading and tweaking-looked at /etc/default/acpi-support edits and other system files too but it never worked-always had to reboot after suspend. 

Although it's a small thing muting of the main speakers when headphones were plugged in never worked either. That is mains were on with headphones-looked at jack sense but that never was resolved. 

In opensuse muting of mains with headphones worked. Resume in opensuse would sometimes work but not predictably.

---

### Post by Paqman on 2008-07-30
Acer Travelmate 2420 (to be exact: 2423WMXi, Celeron 1.5GHz, 512MB RAM, Intel 915)

Original Broadcom card swapped for an Intel 2200, which works perfectly. Thoroughly recommend doing the same. 

Suspend works fine, but hibernate doesn't.

---

### Post by Kotjze on 2008-07-30
I voted "Linux works completely with my laptop-I will post my hardware specifics"

Specs are in my sig. The graphics card and wireless card don't work out of the box, but since Hardy I no longer need to follow a confusing guide that usually won't work, because of the "Pilotes de périphériques"(I think "Hardware Drivers" in English?) in the Systeme -> Administration menu :P It identifies the hardware and it installs them and they work perfectly!

---

### Post by Kingsley on 2008-07-30
Everything works perfectly on my HP 6000. 

It has an Intel processor, Intel wireless, and an Nvidia graphics card.

---

### Post by Northsider on 2008-07-30
Sony Vaio, PCGK45  As of Ubuntu 8.04 everything works flawlessly.  I had trouble with my wireless for sometime, but after the upgrade it worked great!  Currently using Kubuntu and Ubuntu 8.04

---

### Post by lisati on 2008-07-30
Toshiba A100 mostly works.

7.04: needed installation of system updates for sound to work, usb mouse and usb keyboard would stop working after a while (workaround described [here]("http://ubuntuforums.org/showthread.php?t=854684")), occasional phantom audio CD appearing on desktop (logs show hdc being "confused", haven't bothered fixing)
7.10: after upgrade to 7.10 sound stopped working, fixed by compiling & installing relevant ALSA modules (forget which for now), also the occasional phantom CD but still haven't bothered fixing.

Winmodem: Haven't had a need to test it or use it with Ubuntu, so not sure.

---

### Post by jimrz on 2008-07-30
2 ThinkPads

- T42 w/ IBM a/b/g wifi & ATI Radeon mobility 9600 vid card

- 600x  Netgear WG511T pcmia wifi card

both "just work" otb with the minor exception that the 600x, due to < year 2000 original bios date string (the currently installed bios do meet the >2000 cutoff date), requires "acpi=force" + "pci=noacpi" boot flags to get proper acpi function without losing the ability to use pcmia card slots.

---

### Post by InfinityCircuit on 2008-07-31
Thinkpad X40.  Everything works, from ethernet, to wireless, to special keys, to HDAPS hard disk head parking.

```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
02:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev 8d)
02:00.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 13)
02:01.0 Ethernet controller [0200]: Intel Corporation 82541GI Gigabit Ethernet Controller [8086:1077]
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

```

---

### Post by cdekter on 2008-07-31
Dell Inspiron 1525 - works great! Only the occasional problem with not wanting to go into suspend (about 1 in 100 times).

---

### Post by aussiedini on 2008-07-31
Toshiba L300, only issue was ethernet card, I ahd to disable it in bios to get the cd to boot and install. However wireless worked fine so I hvae no need of it.
Webcam even worked straight up. Fantastic.

---

### Post by hyper_ch on 2008-07-31
well, my boss bought an axxiv notebook and I setup ubuntu for him. Everything works - except for the fingerprint reader... I have not tried to set it up at all as the whole systsem is fully encrypted anyway. Maybe I could get the fingerprint reader to work but I did not put any effort in it at all.

---

### Post by tom66 on 2008-07-31
Dell Inspiron 1300. 

Perfect.

Intel Wireless - works out of the box
Intel Mobile Graphics - out of the box, but blur is slow
512 MB Ram - perfect for Ubuntu
Intel Pentium M 1.79GHZ works great

The only thing I see that is not working is the microphone port. But apart from that it is flawless.

---

### Post by Nepherte on 2008-07-31
My laptop is a Sony Vaio VGN-SZ61XN/C. Everything works except some fn-keys (sound fn-keys work though) and the fingerprint reader.

---

### Post by phidia on 2008-08-06
From a run through of the thread right now it seems like the Dell Inspirons require the least set up from what's been posted so far.
Anyone else want to have a go at this??

---

### Post by deanet on 2008-08-07
Got a brand new Dell 1525N from Dell direct with 4G memory, 250G HD
Out of the Box with supplied 7.10 software, did not have Ethernet, Wireless, or Sound (sound weak out of speakers, good sound from one headphone jack, other jack nothing)
Got no help from Dell support, one tech said hardware another said software, they finally agreed to send to me a box to return the laptop for repair.  After 5 days of waiting for the box, I called Customer Service and said I wanted to return the laptop and get my money back, then they agreed to exchange my laptop for another.
While waiting for the new one I installed 8.04, and then the Ethernet worked, and so did the wireless, but the sound was still low.  I followed the help on the Ubuntu forum and fixed the sound.
When I received the exchange laptop, I had the same problems with the ethernet and the wireless, but the sound worked good using supplied 7.10.
I upgraded the new one with 8.04, and had the same problems with the sound, which I fixed again using the forum.

---

### Post by doorknob60 on 2008-08-07
My laptop (old Presario 1600s) works perfectly, although there's not much that *could* go wrong with it :-P My parent's HP dv9008nr works perfect (except it doesn't work with the xD card reader, I believe there's no kernel support for it, and SD cards work fine). WIfi works on it with ndiswrapper, everything else (including the little remote that comes with it) works AFAIK. Sometimes when you unplug a USB device and plug it back in it won't work till you restart though, so I guess it's not perfect, but close.

---

### Post by geogur on 2008-08-07
my hardware 2g ram in a 4g eeepc works so slick i get free internet everywhere i go . cost was 350.00 canadian and only 43.00 for the upgrade from 512mg ram to 2g ram . asus builds good rock solid hardware it fits in my ski bag and travels well when i pull it out people are shocked as what it can do .

---

### Post by Lord Xeb on 2008-08-07
I have an IBM T43 and Linux works just fine. The only thing that I do not have working is the HDAPS (Hard Drive Active Protection System), but that isn't important.


Here are my specs:

Intel Pentium M 1.86GHz
1.5GB of RAM
ATI Radeon X300
40GB HD


Nearly everything works and it runs smoother than when I had windows :D

---

### Post by billgoldberg on 2008-08-07
> **MaxIBoy said:**
> My only problem is that when I go into suspend, sound is disabled until I reboot. OpenGL is also glitchy as hell, but what do you expect with an Intel integrated chip?

I use an intel integrated chip and opengl and compiz fusion run perfectly together.

---

### Post by abgemacht on 2008-08-07
I'm running Hardy on a T60p.

I was really happy when I got the fingerprint reader working.

What's left:

Sleep/Hibernate
Forward/Back Keys above arrow keys.

Other than that, it works great.

---

### Post by 5m0k3 on 2008-08-07
The only issue I have on my Inspiron 1525 is that my AverMedia AverTV HC82 ExpressCard TV tuner is a lost cause on linux :(

---

### Post by Old_Grey_Wolf on 2008-08-07
Linux works completely with my laptop - I will post my hardware specifics:

Inspiron 1420 - Intel® Pentium® Dual Core T2370 (1.73GHz/533Mhz FSB/1MB cache)
1GB Shared Dual Channel DDR2 at 667MHz
Glossy, high contrast, widescreen 14.1 inch display (1280x800)
Intel Graphics Media Accelerator X3100
120GB SATA Hard Drive (5400RPM)
Integrated 10/100 Network Card and Modem
CD / DVD writer (DVD+/-RW Drive)
High Definition Audio 2.0
Dell Wireless 1395 802.11g Mini Card
56Whr Lithium Ion Battery (6 cell)

---

### Post by isaacj87 on 2008-08-07
Hey,

My lappy is fully functional with Ubuntu (as far as I can see). You can see my specs in my signature. Admittedly, there's a couple things I have to tweak after a fresh install (for example, my wifi LED), but it's simple to get everything working.

---

### Post by K.Mandla on 2008-08-07
My mother bought a 1420n from Dell and it works perfectly out of the box with both 7.10 (of course) and 8.04.

---

### Post by TwiceOver on 2008-08-07
Dell Inspiron 1501
AMD x2 2ghz
2gb ram
120gb
15.1"

I said partial because I needed to us NDISWrapper for WiFi and also do the brightness keys adjustment found in the how-to forum.

Not a bad laptop for as cheap as it was.

---

### Post by Mr.Auer on 2008-08-08
My laptop is an Asus Eee pc 701, 4GB model.
At first I had Xandros on it, but it really sucked, so I installed eee-Ubuntu on it. Right after install some things didnt work right, like the quick keys with Fn combo. I applied some fixes (like reducing disk writes, tmpfs for logs, etc..) and installed a custom built kernel that enabled all the features - inbuilt mic, webcam, wireless, Fn keys now work, volume controls work, suspend works, 3G usb modem works thru wvdial - even if I unplug the device and then reconnect. Also, CPU frequency scaling works, so I can easily downclock the cpu from a panel applet when running on battery. Have Compiz as well, working beautifully on it. I just love that lappie, been using it just as much as my main desktop boxes.

So I voted "works perfectly" :)

---

### Post by Skorzen on 2008-08-08
Actually, the only thing that doesn't work out-of-the-box in my ASUS F3Sc laptop is the sound, but following somebody's tutorial out there in the forums, I made it work. You just got to add a line to a file (don't know names), restart and it's done.

---

### Post by meborc on 2008-08-08
works perfectly:

inspiron 1520

c2d 2.0 GHz
2G ram
160G HDD
1680*1050 screen - :) i'm so digging this nice resolution 
broadcom wifi (works with via jockey installed firmware)

---

### Post by BrokenKingpin on 2008-08-08
Mine works perfectly:

Compaq Presario R3000
Ubuntu x64

AMD64 3000+
768 MB RAM
NVidia G0 320
60 GB HDD
LG DVD Drive
Broadcom BCM4306 --> worked out of the box when I enabled the driver (which used fwcutter), but I switched back to Ndiswrapper for a better connection.

---

### Post by blazercist on 2008-08-08
Mine works perfectly now that I have a webcam driver, check my sig

---

### Post by Flyingjester on 2008-08-08
Works excellently here
HP pavilion ze4900
celeron M 1.4 ghz processor
512 RAM
broadcom wireless
touchpad
everything works great.

---

### Post by Sycron on 2008-08-08
My eeepc 701 runs Ubuntu out of the box ok, except microphone,camera and Wifi... but this can be solved with adam's kernel.... or by manually installing drivers..

---

### Post by macogw on 2008-08-08
My Gateway MX 6920 works perfectly, but it's 2 years old, so it's had a chance to catch up.  My ZaReason UltraLap (Asus Z37E) has a non-functioning webcam & fingerprint reader, and I don't have an Express Card to test that slot with.

---

### Post by jgrabham on 2008-08-08
Dell Vostro 1510, WPA issues, link in my sig.

---

### Post by atihimself on 2008-08-08
Protsessor Intel Core 2 Duo T5550 1.83GHz 2MB cache 
2GB DDR2 - 4GB
MB Intel GM965 + ICH8M 
Intel GMA X3100,  384MB 
Intel 3945ABG wifi, 10/100/1000 LAN, modem, 3xUSB,1 kaardilugeja (SD/MMC/MS) 
DVDRW DL 
250GB Samsung S-ATA 8MB 

Only thing what doesn't work is this puny little integrated webcam,
otherwise out-of-the-box,

---

### Post by ahaslam on 2008-08-08
Via K8M800, need I say more?

---

### Post by rldreams on 2008-08-08
Fully Functioning laptop Lenovo Thinkpad R61i,Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz,1g ram, 80G HD (partitioned 35G Linux,10g Lenovo "thinkvantage" restore ,35G xp pro sp3 for those emergency situations where due to propriatary software I NEED windows of course winxpsp3 takes up 28 of the 35g I allowed it to keep). After I spent over 3 hrs updating windows as soon as I opened the box, I imediately spent 30 minutes and partitioned the HD and installed Gutsy and let it ubdate to Hefty (since I don't have Hefty on a disk yet ) Only issue to this point was when updating Lenovo Thinkvantage it flashed the BIOS and screwed up GRUB.Running Gutsy live cd and resetting GRUB fixed that in a matter of a couple minutes once I checked the forums here and found the fix.With the fix I now even have the ThinkVantage restore option on bootup which I did not have after the initial partitioning and install.
 The only "issues" are with the system sounds ,but I have not addressed that problem yet.

---

### Post by vandorjw on 2008-08-08
FULLY FUNCTIONING

Dell Inspiron 1520
-Bluetooth
-Wifi "N"
-Nvidia 8600GT
-Intel Core 2 Duo T7500 (Santa Rosa)
-2 GB RAM
-Front Media Buttons
-WIFI CATCHER!!

--------------------------------
Actually, I lied i guess, one thing does not work. BIOS Controlled Fans.  Windows XP, temp = 40/60 Ubuntu = 60/85

That is idle/load in Celsius.

PS: I got ubuntu to drop using DellFand, however, it is very underdeveloped.
(I am going into my 2nd year Software Engineering and will look into making it run better.)

---

### Post by Windsurfer619 on 2008-08-08
Hardy on an inspiron 640m. Suspend is a bit flakey, and maximizing playing videos can crash the computer.

---

### Post by ssam on 2008-08-10
Thinkpad x31 (£150 from ebay :-) )
[http://www.thinkwiki.org/wiki/Category:X31](http://www.thinkwiki.org/wiki/Category:X31)

everything works, wireless, suspend, hibernate, CF card slot, special keys, keyboard light, sound, external VGA...

---

### Post by cetheriel on 2008-08-10
acer extensa 5620z works almost flawlessly.
needed proprietary driver for wifi, bluetooth not there yet.
wrote a thread on it.
[http://ubuntuforums.org/showthread.php?t=868841](http://ubuntuforums.org/showthread.php?t=868841)

---

### Post by Aquaman420 on 2008-08-10
I acquired a Toshiba Satellite m-55 from my girlfriend.  Everything seems to work including the built in wireless which is intel 2200, the sound which is intel ichr7 i think. and compiz with the intel 915 igp.  I have not tried the card reader but probably will never use it anyway.  Very pleased.  Got 8.04 installed and tweaking in 1 hour.  Hooray!

---

### Post by zithedragon on 2008-08-12
other then needing to go thru steps to get the WLANBroadcom bcm43xx it works 300% better then with windows (even tho its duel boot with windows :lolflag: )

---

### Post by phidia on 2008-08-23
The beauty of a poll and language is the each person gets to interpret it the way they want I guess.
Someone here said that they installed a custom kernel and yet voted their laptop works perfectly with linux.
I don't know if I posted about my hp pavilion here before so excuse me if I'm repeating myself. The pavilion doesn't resume, sound muting of mains with headphones plugged in doesn't work, flash/youtube playback mostly works but occasionally ff needs to be restarted-that's a small thing compared to resume though. I spent a lot of time with the resume issue and added scripts to /etc/default/acpi-support and other system locations to no avail. I found a thread on the sound muting issue that basically said I needed to build alsa from source.
So anyway, for me, it just doesn't work the way I expect a laptop to work.
The hp is going up for sale on craigs list or ebay soon.
I'm using an older powerbook with OS X now and if I find the right macbook pro I'll grab it.

---

### Post by epiphonygirl on 2008-08-23
I have a Lenovo R61e Thinkpad, nearly everything worked. The only issue that I have since resolved was that it did not recognize my wireless. I went through several hoops to get it to work, specifics of the issue and its resolution are [here]("http://ubuntuforums.org/showthread.php?t=873980"). Now everything works well.

---

### Post by TheSlipstream on 2008-08-23
Acer TravelMate 2400

Everything works just fine except the Broadcom Air Force One card, which has apparently been fixed in the latest kernel.

---

### Post by fwojciec on 2008-08-23
Toshiba Satellite M35.  Everything works, some things slightly hackishly but reliably, except for the SD card reader which is not supported in Linux at all.

---

### Post by damis648 on 2008-08-23
Dell XPS M1530. Running perfectly.
GeForce 8600M GT
Intel 4965agn
Intel T9300 Core 2 Duo
DVD +- RW
Card Reader
Webcam Built-In
Media Keys
Bluetooth
Sound Blaster Audigy HD
ALL WORKING!:popcorn:

---

### Post by seatex on 2008-08-23
My Gateway MP8708 works great with 8.04.

Specs:
[http://support.gateway.com/s/Mobile/Q106/SonicC/1013924Rsp5.shtml](http://support.gateway.com/s/Mobile/Q106/SonicC/1013924Rsp5.shtml)

---

### Post by zmjjmz on 2008-08-23
1st gen Macbook -- Everything works, but some of the Macbook specific "features" don't. (That is, where the Macbook relied on OSX to make up for it's lack of hardware)

---

### Post by nickgaydos on 2008-08-23
Gateway ML3109
Ubuntu Ultimate 8.04.1 32 bit
Intel Celeron M 520 @ 1.60
ATI Radeon XPress 200M EnvyNG
Realtek 8185 Wireless (Ndiswrapper)

The only problem that I have is to activate Compiz Fusion, I need to change window managers in Compiz Fusion Icon...I think it's a Ultimate thing.

---

### Post by rokytnji on 2008-08-23
Panasonic cf-48
PENTIUM M 1.6 ghz
512 mb 200 pin  sdram
Internel intel pci wireless a/b/g
100 gig ide hardrive
Ibm cdrw/Floppy combo drive
Ubuntu 8.04 2.6.24-21

Amrel Rocky EX
900 mhz
256 mb sdram
100 gig hardrive
Dlink wna 1330 PCMCIA wireless g cardbus
Hot swappable ide hardrives
Hotswappable cdrom and cdrw
Hotswappable floppy
Xubuntu/Mandriva 2008 dual boot on 100 gig drive
Custom Nimble x on other swapable 20 gig drive

Both laptops fully funtional wireless and wired
Sound works
Amarok,Totem,Xine,Flash,External USB 2.0 Liteon EZDUB DVDRW,K3b,Braserio,Audacity,Iso master,Etc... all work

No need for ndiswrapper for any wireless connections. Madwifi worked just fine.

Lexmark Z645 printer that Ubuntu considers a boat anchor works now after using Lexmark Linux driver from manufacturers site on both laptops.

---

### Post by yipperzz on 2008-08-24
Dell D600 and have no issues.  Had to use ndiswrapper for my wireless card, but it's easy.  I've had harder times on previous versions of Linux on my older machines.

---

### Post by crazyfuturamanoob on 2008-08-24
Acer Aspire 7520g with an extended RAM up to 4GB. No any problems. And I just got the graphics card drivers working too. :)

---

### Post by rax_m on 2008-08-24
Laptop works partially

Toshiba P100 with Nvidia 7600 Go
Laptop works great except for:
1. Suspend / hibernate is an issue
2. I believe that the GPU fans are constantly on at low settings, but never speed up. But I've not had any GPU overheating anyway. 

Cheers

---

### Post by kirsis on 2008-08-24
I have a HP Pavilion dv6698en

NVIDIA® GeForce™ 8400M GS - works great
DVD+- RW SuperMulti (Lightscribe burner) - works
Bluetooth - works
Infrared - works
Wifi - works
Webcam - works
Flash memory card reader - works
Suspend/resume - works
Remote control - works

Everything worked out of the box :) Havent tried hooking it up to a TV yet though, so dunno about that.

My previous laptop was also a pavilion. Gutsy ran great on it.

Pavilions seem to be a Linux friendly line of laptops.

---

### Post by pfdevil on 2008-08-24
Works great from first install.

Acer Aspire 5673WLMi Model No. ZB1

---

### Post by bomanizer on 2008-08-24
Thinkpad R50 + Hardy
--------------------

Problems:

- ultrabay device removal causes the system to freeze
- disk head parking is broken in the current kernel

---

### Post by insane_alien on 2008-08-24
dell inspiron 1525 with 4GB RAM. works perfectly.

well, except for the wifi indicator LED. i'm sure there is a quick fix for it womewhere but it doesn't bother me too much and it works fine in intrepid.

---

### Post by xeth_delta on 2008-08-24
Kubuntu Linux 8.04 with kernel 2.6.24-19-generic on a MacBook 2.1
All what is important seems to be working, including issues that used to be slightly problematic in previous releases.
Suspend, special keys, onboard isight camera, remote control, video-output, all work right now.
Atheros wireless card works with WPA after a short compilation of the madwifi driver.
Bluetooth was working in a previous release, I have not tried it yet under 8.04 since I upgraded. It will probably work.

Only issue (if it can even be called like that) is that the front LED does not light up when the screen is off to conserve power. LED does light up during suspend, however.

---

### Post by amattheson on 2008-08-24
i have a c751nr and it has a ar5007 the only problem it has is it cant do wpa. the driver was modified to get the soft switch led to work and the modifier must have took something out so it cant do wep.

---

### Post by mintochris on 2008-08-24
asus eee 900 here :), with a modified hardy install and an eee specific kernel.
The only thing that took a bit of sorting was that the boot process was knocking about 20% off the battery on every restart, but a bit of service tweaking solved that.

---

### Post by brons2 on 2008-08-24
> **phidia said:**
> I'm not going to put this out perfectly-but I'm curious about several somewhat complex laptop issues. I also think this might be useful to the community here because the question of what laptop to use with linux keeps coming up on the forums.


I have a Toshiba A205-S7442, Core2Duo T5250 1.5 Ghz/Centrino, all Intel parts, 15.4 widescreen.  Worked with the 64 bit version of Ubuntu with absolutely no fiddling with the hardware, correct resolution, wireless works, etc.  Better yet I got it on closeout for $525.  I then got 4GB of RAM from NewEgg for $74 shipped.

---

### Post by jrev on 2008-08-24
Hi, I cannot see anything wrong with my old laptop Toshiba Satellite with a 250 RAM on the 5.10, 6.06, 7.04 and 8.04 Ubuntu 

Sysinfo indicates : Intel celeron CPU 2.93 GHz L2 cache 256KB, total memory 186Mib swap total 854 MiB 

except that it's really slow on the last distribution.
I am waiting the first fault to throw it away.

But I am patient :)

---

### Post by kagashe on 2008-08-24
> **jrev said:**
> except that it's really slow on the last distribution.
I am waiting the first fault to throw it away.

But I am patient :)Use lighter Desktop/WM like LXDE, Fluxbox, JWM, IceWM and it will fly.

kagashe

---

### Post by Twitch6000 on 2008-08-24
Everything works great except my webcam and I can get it to work on my acer 9410 aspire.

---

### Post by fadumpt on 2008-08-24
> **jrev said:**
> Hi, I cannot see anything wrong with my old laptop Toshiba Satellite with a 250 RAM on the 5.10, 6.06, 7.04 and 8.04 Ubuntu 

Sysinfo indicates : Intel celeron CPU 2.93 GHz L2 cache 256KB, total memory 186Mib swap total 854 MiB 

except that it's really slow on the last distribution.
I am waiting the first fault to throw it away.

But I am patient :)
Doesn't looklike toobad of a system..give it a gig and it'll fly

---

### Post by davarse on 2008-08-25
i use laptop acer aspire 5920G,,, it works fine but my touch pad doesn't seems like working properly, like the scroll on the edges and also the multimedia touch bottom (on the right side) dont do the proper job, it became scroll page instead of multimedia button... i still dont know how to figure the audio yet...
and i had another issue, it not response when i connected to the projector (benQ MP 511+), it can found any signal...
i wish some one could help me to solve my problem,,,:(
i really like linux anyway..

---

### Post by danbuter on 2008-08-25
My Acer Aspire 3680 works perfectly with Intrepid. Wireless did not work on HH, unfortunately, thanks to that kernel.

---

### Post by Dragonbite on 2008-08-25
Dell Latitude D400
[LIST]
[*]Hibernate / Suspend does not work from my minimal testing.
[*]Wireless card (Broadcomm 4309) works fine once firmware has been installed via "Hardware Drivers" utility.
[*]Have not checked CPU scaling or anything else
[*]Touchpad sucks, but good thing for the trackpointer which works great
[/LIST]

***NOTE: except for the case of Wireless getting dropped and not re-established openSUSE is the only distribution that has successfully operated Suspend and Hibernate including on Lid Close and low battery triggers. Unfortunately I want my wireless network to be stable :). ***

---

### Post by timcredible on 2008-08-25
this works perfectly:
```


-- Vostro 1000 --
-- AMD AthlonTM 64 X2 Dual-Core processor TK-57 (1.9GHz/256KB)
-- [223-5529]
-----------------------
-- LCD Panel --
-- 15.4 inch Wide Screen XGA LCD Display with TrueLife
-- [320-5883]
-----------------------
-- Memory --
-- 2GB Shared Dual Channel DDR2 SDRAM at 533MHZ, 2 Dimm
-- [311-7344]
-----------------------
-- Video Card --
-- ATI Radeon®  Xpress 1150 256MB HyperMemory&#33922;  (integrated)
-- [320-5631]
-----------------------
-- Hard Drive --
-- 120GB 5400RPM  Hard Drive
-- [341-4971]
-----------------------
-- Operating System --
-- Genuine Windows® XP Home Edition
-- [420-7163]
-- [420-7291]
-- [420-7658]
-----------------------
-- Adobe Software --
-- Adobe® Acrobat® Reader
-- [410-1100]
-----------------------
-- Optical Drive --
-- 8X DVD+/-RW with double-layer DVD+R write capability, Cyberlink Power DVD
-- [313-5390]
-----------------------
-- Sound Card --
-- Integrated Audio
-- [313-5383]
-----------------------
-- Wireless Cards --
-- Dell Wireless 1395 802.11g Wi-Fi Internal Card
-- [430-2733]
-----------------------
-- Productivity Software --
-- Microsoft® Works 9. Does NOT Include MS Word
-- [420-8046]
-----------------------
-- Anti-Virus/Security Suite (Pre-Installed) --
-- No Pre-installed Anti-Virus/Security Software
-- [410-0982]
-----------------------
-- Primary Battery --
-- 53 WHr 6-cell Lithium Ion Primary Battery
-- [312-0569]

```

---

### Post by illu45 on 2008-08-25
> **tamoneya said:**
> problem free so far.  Lenovo T61.

Same for me... Although my printer (a lexmark c500n) works intermittently. That's not really a laptop-based problem though, and driver support for Lexmark printers has definitely improved significantly since I started using Ubuntu a few years ago.

---

### Post by mips on 2008-08-25
I would not base my purchasing dicision on what works out of the box. I would go for hardware specs. durability etc.

Thinkpad all the way!!!!

---

### Post by PurposeOfReason on 2008-08-25
I have an old Sony FS that is 100% working.

---

### Post by archer6 on 2008-08-28
**_ThinkPad T60 2007-73U_**

T2500(2GHz) 2GB RAM 
100GB Main Hard Drive running Win XP SP3
120GB Second HD in Ultrabay Ubuntu 8.04.1
15in SXGA+ 1400x1050 IPS Flexview LCD 
128MB ATI Radeon X1400 
CDRW/DVD, Intel 802.11abg wireless 
Bluetooth/Modem, 1Gb Ethernet, UltraNav
Secure chip, 6c Li-Ion battery

**_Ubuntu 8.04.1_**

Installed from DVD, everything operates perfectly.
No tweaks required.... simply outstanding!
I could not be happier!

---

### Post by Dragonbite on 2008-08-28
UPDATE: Hibernate and Suspend work just not from the shutdown menu, but from right-clicking on the battery. I dunno why, but it does.

---

### Post by jezza43 on 2008-08-28
My sound doesn't work on my Aspire One. 

Processor: Intel Atom N270 (1.6 GHz)
Chipset: Intel 82945GMS + Intel 82801GBM
Memory: 512 MB DDR2 RAM
Storage: 8 GB SSD
Wireless: 802.11b/g, Atheros AR5BXB63
and running Ubuntu Hardy 8.04.1.
 
After I installed Adobe's flash player plugin, the sound didn't work, so I did "sudo apt-get install libflashsupport"
Then it worked until the next time I booted Ubuntu.
I also tried this:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

but it didn't help. Neither did trying to configure the sound via alsamixer in the Terminal.

My Hibernate kinda works, but I only tried it to see if it would work or not. Closing the lid of the Aspire One to suspend is enough for me.

---

### Post by tdrusk on 2008-08-28
> **danbuter said:**
> My Acer Aspire 3680 works perfectly with Intrepid. Wireless did not work on HH, unfortunately, thanks to that kernel.
That's good to here. I know Mandriva found everything also.

---

### Post by saxuntu on 2008-08-28
HP Pavilion dv2109nr - everything works out of the box.

---

### Post by zoomy942 on 2008-08-28
i have an HP 2710p.  as a new linux user i am liking it so far.  i am getting dicouraged but i will keep at it.

so far what doesnt work

1. Stylus
2. Embedded MC5720 data card
3. Guild Wars via Crossover Games - but i think this is due to intel drivers

---

### Post by aaaantoine on 2008-08-28
Works partially.  Compatibility review as of Gutsy posted [here](http://www.ubuntuhcl.org/browse/product+acer_baspire_5050b5554?id=34).

I will post updated version as of the Hardy upgrade here.  First, a description of the hardware in a nutshell:

Acer Aspire 5050-5554
Processor: AMD Turion 64 1.6GHz
RAM: 1GB DDR2  (Upgraded to 4GB, its max capacity)
Video: ATI Radeon Xpress 1100
Screen: 14.1" 1280x800 Glossy
Sound: ATI SB450 HDA Audio
Hard Drive: 120GB
Optical Drive: DVD+RW
Networking:
+ Ethernet: Realtek RTL-8139/8139C/8139C+
+ Wireless: Broadcom BCM4318 [AirForce One 54g]
Other:
+ Acer OrbiCam
+ Card Reader (SD, xD, MMC, others)
+ PCMCIA slot

**Issues:**

1. Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
- Does not work out of the box; requires firmware installation. Installation requires firmware file on hand or a wired network connection.

2. Microdia OrbiCam (USB device 0c45:6260)
- Not supported as of Hardy.  Drivers currently in development.  Follow driver development [here](http://groups.google.com/group/microdia).

3. Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
- Laptop speakers are mapped to the "Surround" channel.
- Microphone does not work.
- Laptop speakers do not mute when headphones are plugged in.

4. VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
- Open source drivers offer limited function; Restricted drivers are improved but somewhat unstable.

General
- The custom Euro and Dollar keys above the directional keys do not function.
- Suspend works, but drops wifi functionality.
- Hibernation not tested since Gutsy.

---

### Post by Deinumite on 2008-08-28
I have a thinkpad T61p, and as far as i know the only thing that doesn't work is the hibernation, but i think there are ways to get around to fixing that, but i have not yet. Wifi works out of the box, and pretty much everything else does too, except for installing binary nvidia drivers, which of course Ubuntu takes care of too.

---

### Post by conundrumx on 2008-08-28
Lenovo T61p, everything but Suspend/Hibernate works.

And really, with a system that boots into a usable state in something like a minute, do I really need to shave more time off it?

---

### Post by Sycron on 2008-08-28
HP Compaq 6720s working fine.

---

### Post by cl0ckwork on 2008-08-28
works partially--
HP pavillion dv9000 series (9428nr)

had gutsy on my laptop initialy and had some issues with the broadcom card, graphics card, and the multimedia keys.
now since i upgraded to HH after a few different OS's, broadcom worked out of the box, as did nVidia.  but still nothing for the multimedia keys.

i had them working at one point but after i uninstalled some KDE packages they stopped working, even though i am working form gnome. maby someone has gotten them working? please let me know

also suspend to disk/ram doesnt work but they havent worked in the 4 other linux distros i had either

---

### Post by Dragonbite on 2008-08-28
> **conundrumx said:**
> Lenovo T61p, everything but Suspend/Hibernate works.

And really, with a system that boots into a usable state in something like a minute, do I really need to shave more time off it?
On my system it almost takes longer to restore the session from suspend/hibernate. I suspect it is partially due to only 512MB Ram available so if it is trying to store everything in RAM *and* run through the process it may be a bit much.

Best way to test that theory, though, is to max it out with 2GB of ram and see how it runs! :)

---

### Post by conundrumx on 2008-08-28
> **Dragonbite said:**
> On my system it almost takes longer to restore the session from suspend/hibernate. I suspect it is partially due to only 512MB Ram available so if it is trying to store everything in RAM *and* run through the process it may be a bit much.

Best way to test that theory, though, is to max it out with 2GB of ram and see how it runs! :)

I have 4gb of RAM, the thought never crossed my mind that I would rarely use more than 2gb at any given moment.  :)

What part of CT?  I work in the East Hartford area.  :p

---

### Post by postmodernism on 2008-08-28
Using a Dell 9300 everything works, as far as I can tell.

---

### Post by jespdj on 2008-08-28
64-bit Ubuntu 8.04 [works great on my Dell XPS M1530](http://jesperdj.pbwiki.com/Ubuntu+on+the+Dell+XPS+M1530). Some minor fixes were necessary, but nothing really difficult.

---

### Post by mudguts on 2008-09-02
so many choices...
I had 7.04 on my IBM T23 worked like a charm
7.10 on my Dell Inspiron 1520 - worked 100% EXCEPT for the video codecs causing issues when trying to play a DVD
slowly getting around to installing 8.04 on my MSI Wind.. might run it off the USB key for awhile...

---

### Post by linux5uper on 2008-09-02
HP Compaq Presario F722CA, with AMD TK53, Nvidia 6100, BCM4311 rev2... with a bit of tweaking, everything is perfect in Gutsy + Hardy.

---

### Post by kavon89 on 2008-09-02
Specs in sig, fully functioning. The built in webcam didn't work on Windows Vista fresh from the factory, yet it works fine in ubuntu. ThinkVantage doesn't work obviously but everything like the ThinkLight and volume buttons work. Mute button is a little funny but it works.

---

### Post by swoll1980 on 2008-09-02
Dell latitude 100l works perfectly. It has the intel 855 chipset broadcom 440 network adapter broadcom v.92 fax modem

---

### Post by worx101 on 2008-09-02
HP Compaq issued laptops :)

works well on all of them.

works great on my eeepc 701 too :P

---

### Post by hanzomon4 on 2008-09-02
Any fully functional mac laptop. I'm just one issue away from getting mine working 100%. Suspend/hibernate it just refuses to work.

---

### Post by david_lynch on 2008-09-03
Product Name: Presario V6000 (RG390UA#ABA)
BIOS Information
        Vendor: Hewlett-Packard
        Version: F.05
        Release Date: 10/02/2006
CPU: Intel(R) Celeron(R) M CPU  430 @ 1.73GHz
Graphics: Intel Corporation Mobile 945GM/GMS
Wireless: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
1024 MB RAM

Everything works, and no ndiswrapper needed.

---

### Post by wolfen69 on 2008-09-03
i have an acer travelmate 2420 that works perfect. i have 512 ram.

---

### Post by wolfen69 on 2008-09-03
> **hanzomon4 said:**
> Any fully functional mac laptop. **I'm just one issue away from getting mine working 100%.** Suspend/hibernate it just refuses to work.

that would not keep me from using linux full time. if you like something enough, you find a way.

---

### Post by Bragador on 2008-09-03
My laptop, and old thinkpad, works pretty well.The only problem is if I use the red dot on my keyboard (a kind of mouse/joystick), after a while the arrow gets crazy and opens tons of stuff.

So I simply use a normal usb mouse and everything is fine.

---

### Post by nvikram on 2008-09-03
Completely fine. Everything works (wi-fi, graphics, etc.)

Specs:
HP DV2600 Laptop
1.5GHz Core 2 Duo T5250
2GB RAM

Had Vista Preinstalled
Upgraded to XP
Upgraded to Ubuntu.

---

### Post by hanzomon4 on 2008-09-03
> **wolfen69 said:**
> that would not keep me from using linux full time. if you like something enough, you find a way.

Well I need something reliable

---

### Post by Sycron on 2008-09-03
> that would not keep me from using linux full time. if you like something enough, you find a way.

This is true.

---

### Post by hardyn on 2008-09-03
Asus Z71vp Barebone notebook
i2915 wifi
nvidia 6600go
p-m 2.1ghz
i945p / ICH5

Its old though, i don't think you can get these things anymore.

---

### Post by VMan on 2008-09-03
Two laptops.  Everything works fine:KS

Toshiba A135-S4467 (sound took a little bit of tinkering though)

EeePC 1000H  Found all the information needed to have everything working perfectly with minimal tinkering at eeeusers.com.  I am using a custom kernels and modules from another (adamm) user.

---

### Post by Daggo on 2008-09-03
HP Pavilion dv2845se
 
The only thing I needed to configure was to use ndiswrapper for the embedded wireless card. The documentation and support online was very easy to read and follow to get it fixed right up.

Other than that, I was absolutely astonished how well Ubuntu worked out-of-box!

---

### Post by RFScheer on 2008-09-03
New Dell Studio 1535 with pre-loaded Ubuntu 8.04 works perfectly ootb after one day testing.

---

### Post by spupy on 2008-09-03
I voted "All works", although both Ubuntu and Debian fail to function properly with my TOUCHPAD more than 10 minutes. Only Gentoo works...

Toshiba Satellite A110
Atheros Wifi (used to be problematic on earlier ubuntus)
Realtek Ethernet
ATi X200M (fglrx and radeon both OK, compiz runs outta the box)
ALPS Touchpad <- only with Gentoo; Ubuntu won't
These are the only relevant devices.

---

### Post by ginnie6 on 2008-09-03
hp dv9610 and everything works perfectly. ad to do a few fixes (broadcom wireless card) but even the webcam works.

---

### Post by Tyler H on 2008-09-03
Dell Vostro 1000. I've got more working hardware with Hardy than I do with the Windows Xp partition. It wasn't the easiest task to get everthing running like glass, but it was a good learning experience and we even managed to get a good Vostro 1000 tutorial written out of it.

---

### Post by toupeiro on 2008-09-04
HP 8710w -- Ubuntu working 100%

Lenovo T60 - Ubuntu working 100%

---

### Post by tk03759 on 2008-09-04
I have an HP Pavillion dv500

The functions that haven't worked are:
-Resume from suspend (there is a workaround, but it must be done upon each resume)
-Quick Play Keys (only the Windows Media Center Key & DVD key don't work, the volume control and playback keys work fine)
-Resolution didn't work out of the box: I had to go into Visual Effects and select Extra. It then asked me to install nVidia -Restricted Drivers, which solved any other problems.
-Wireless Card (required ndiswrapper and the CORRECT drivers, since there are many HP Pavillion dv drivers, this was a toughy to install. once installed, wireless worked perfect)

The only problem of these three that bugs me were the wireless driver and the suspend.
Now that it's set up, it runs a lot more stable than Windows Vista does on the same box. Vista recently stopped working altogether and I have no idea why, seeing I don't log onto it more than once a month. I think it's jealous haha.

---

### Post by dlm4849 on 2008-09-04
a pretty much loaded lenovo R61 working 100%

---

### Post by aikata on 2008-09-04
Dell XPS M1530 Nvidia 8400m gs intel HDA intel 4695 marvel nic creative webcam, upek fingerprint reader, ricoh SD card reader... even the top buttons work fine, just the windoze media direct button doesn't

---

### Post by SandersOnSite on 2008-09-05
I have an Asus W7S. Ubuntu runs on it almost perfect (I guess I lied a little in m poll answer because it never effects me) - the picture from the webcam comes out upside down. 

Since I never use the webcam its not really an issue for me.

Other then that - everything else worked perfectly out of the box.

---

### Post by Tindytim on 2008-09-05
I have a Compaq Series PP1020 that works fine with Xubuntu

---

### Post by hackapelite on 2008-09-06
[I'm sure I am allowed to revive this thread ;)]

My mum has an Acer Aspire 5720 lappy, I tried the LiveCD and everything seemed to work perfectly out-of-box - including wireless, LCD baclight brightness & other powersaving features. 

I can't get the backlight adjustment on my own laptop, Presario C700, to work, though (dunno if there is a fix for it, haven't really been searcing around) and for the wireless I had to get madwifi installed which was a pain, other than that it works great.

---

### Post by EdThaSlayer on 2008-09-06
I have an Asus F8 series
Specs:
Dual core T8100 2101 mhz
250 gb hard disk at 5400 rpm(not sure though...)
2 gb of ddr2 ram 
14 inch wxga screen
DVD Sup.MTI
Wireless 802.11abgn+bluetooth
nVidia graphics card 9500m 512mb of vram

thats around it :)
oh, and the webcam also works(1.3 megapixel) with Cheese but not Cameroma.

---

### Post by EViLGiMp on 2008-09-08
recently acquired a Toshiba A300 07G notebook, that has been a dream to get functioning under Hardy 8.04.1. the initial release of the distro did not wish to co-operate with both the wifi or the sata controller during the install. so my advise is, if you're going to install to this laptop, be sure to have the most current rev of the distro so as not to be faced with any installation issues. here is an lspci output for browsing, lol.

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
06:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by archer6 on 2008-09-08
> **EViLGiMp said:**
> recently acquired a Toshiba A300 07G notebook, that has been a dream to get functioning under Hardy 8.04.1. 

Ahhh yes, I have very fond memories of my Toshiba A300. In a moment of very bad judgment I sold it... the lure of $$$ when I was a college student, during the summer break. Now if only you would have provided us with more detail...:shock:...just kidding, the detail was (at least for me) educational.

Cheers!

---

### Post by mkarnicki on 2008-09-11
Glad to say - works completely.

Model: HP tx1320us
Misc:
 - webcam with r5u870 driver (something like that..)
 - wi-fi with ndiswrapper
 - touchscreen with evtouch driver

EDIT: yeah lol xD True Clanky (below), the mute button light doesn't work, but that's fine with me.

---

### Post by clanky on 2008-09-11
I have an HP Pavillion 8000, Have had Ubuntu and Fedora working fine on it, but struggled to get there with both wireless internet (broadcom 4311) and 3D Graphics (ATI Radeon)

The only thing which doesn't work now is the light on the mute button, I think I can probably live with that.

---

### Post by saffagirl on 2008-09-19
I'm a newbie Ubuntu user, I decided to bite the bullet when I got annoyed with VISTA. I'm still dual booting as there are a few too many problems to completely ditch it.

I've got a DELL VOSTRO 1310 w. realtek wired ethernet, dell wireless n 1505 (aka broadcom 4328 ), webcam, dvd writer.


What I've got fixed through the kind help of people on the forums:
wifi( using new beta driver which as long as open up net straight away is fine), sound, dvd writer (just installed codecs)....

What I still don't have working : webcam ... (occasionally restart needed when keyboard not responsive)

Other than that am enjoying ubuntu on the laptop, although has anyone else noticed a marked difference in the battery life compared to MS?

---

### Post by phoenix116 on 2008-09-19
I have recently bought my COMPAL JHL90 based notebook
I am running 64b hardy


Hardware:

C2D P9500
[COLOR="Orange"]Nvidia M 9600 GT[/COLOR]
4 GB ram
SD/MMC card reader
[COLOR="Red"]Intel Wifi Link 5300 wlan card[/COLOR]
[COLOR="Red"]some kind of webcam and fingerprint reader[/COLOR]

What does not work:

**Graphics card** works only with the driver from the Nvidia Homepage, although there is no official driver for it, it works with normal 9600 gt driver( no problem for me, but for my collegues at school much too difficult, would be great if this would be fixed with intrepid )

**WLAN** doesnt work at all, not even with compat-loaded drivers

fingerprint reader and webcam dont work, but i havent yet spent much time on getting them to work.

---

### Post by rbringh on 2008-09-19
HP Pavillion DV9910US - 64 Bit Version.  Works well except for Suspend/Hibenate on power. Everything works on battery. It did take some work to get the Brother MFC420 working, the network driver is also a pain, but all works.

---

### Post by cookieofdoom on 2008-09-19
Works completely (well, basically)

Thinkpad X61
Intel Wireless (everything works)
Intel Network (everything works)
HDA Intel Sound (everything works)
Intel Video (everything except a few Compiz features work.. will be fixed soon, I'm sure)
2.00GHZ C2D processor
Standby/Hibernate work..

Let me know if you need more info... I don't remember all the specs off the top of my head.

---

### Post by PmDematagoda on 2008-09-19
Compaq V3005TU that runs Fedora 9 perfectly on it aside from one very minor problem.

Specifications:-
1.6 Ghz Intel T2050 processor
Intel PRO/Wireless 3945ABG Network Connection
Intel 82801G (ICH7 Family) High Definition Audio Controller
Intel Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
60Gb Western Digital hard drive
1Gb Kingston RAM

The only problem? The QuickPlay media button doesn't get detected by Fedora.

---

### Post by Glucklich on 2008-09-19
Mine is a Toshiba. At first I had a sound problem, but a BIOS upgrade did the trick (thanks Ubuntu Forums). Now it's completely functional.
There's no point on uploading the specifics since it's an outdated model apparently only sold on the Portuguese market.

---

### Post by archer6 on 2008-09-19
> **Glucklich said:**
> Mine is a Toshiba. At first I had a sound problem, but a BIOS upgrade did the trick (thanks Ubuntu Forums). Now it's completely functional.
There's no point on uploading the specifics since it's an outdated model apparently only sold on the Portuguese market.
This is the beauty of Ubuntu, and Linux in general, in my opinion. You don't have to have a new computer, as it will run on nearly any computer and do very well. I've helped my friends revive many old laptops, and and desktops with Linux and in the process it's been a great opportunity for me to learn, and a great result for them. The savings alone is simply stunning.

Great to hear yours is up and running!

Cheers

---

### Post by jimi_hendrix on 2008-09-19
everything is fine except i cant use my printer or play most games...the printer i can probably fingure out but the games i cant...the screen flickers black when compiz is off

---

### Post by ARhere on 2008-09-23
HP/Compaq nx7000 w/1.6GHz CPU, ATI Mobility 9200, 512MB RAM, & 60GB HDD.

7.04, 7.10, and 8.04 works out-of-the-box.  The [u]only[/i] issue was 8.04 lost the driver that allows Compiz to work with the ATI 9200 mobility.  I have to install the Compiz icon and restart.

-AR

---

### Post by jpittack on 2008-09-23
Dell 1501
No C-states due to faulty programming in DSDT (PM if you would like to research a fix with me)
64-bit does not have dynticks working (may be fixed in 8.10, but haven't heard anything)
backlight doesn't change with later BIOS
wi-fi needs hardware driver and firmware from synaptic

---

### Post by AndyCooll on 2008-09-23
I have a couple of Dell Inspiron 6400's. They work perfectly out-of-the-box. I have been extremely pleased with them.

:cool:

---

### Post by powerpleb on 2008-09-23
I have an Acer Aspire 5315 running Arch ([this is a PDF of the specs]("www.acer.com.au/Acer/akc/rwpattach.nsf/PublicbySrc/ESS+-+AS5315-050508Mi.pdf/$file/ESS+-+AS5315-050508Mi.pdf")) and the main problems I have exist around hibernation and suspension.

Every time I try to suspend it says it failed then sends me to the [HAL quirk site]("http://people.freedesktop.org/~hughsient/quirk/"). I think it can probably be fixed, just that I haven't had the time to properly troubleshoot it yet.

Hibernate seems to work, but then when I wake it up the wireless connection doesn't work :confused:. So if I am to use the network I need to reboot anyway :(.

EDIT: When I ran Ubuntu I don't remember having these problems, which suggests that I just need to do some more setting up.

---

### Post by giosa on 2008-09-29
> **EViLGiMp said:**
> recently acquired a Toshiba A300 07G notebook, that has been a dream to get functioning under Hardy 8.04.1. the initial release of the distro did not wish to co-operate with both the wifi or the sata controller during the install. so my advise is, if you're going to install to this laptop, be sure to have the most current rev of the distro so as not to be faced with any installation issues. here is an lspci output for browsing, lol.

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
06:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

HI, could you please, look up what type or dedicated VRAM your A300-07G have DDR2 or DDR3? thanks

---

### Post by tdilworth on 2008-09-30
Fairly problem free, except:  S-video and Full functionality of UltraNav are my only problems so far

IBM R50 1830-56u
1.4GHz Centrino
1.5 Gb Ram
100 Gb HDD
Dual Boot XP

---

### Post by Karpah on 2008-09-30
Linux works completely with my laptop - stock-standard Dell Inspiron 1525 (that didn't come with Ubuntu.... none of the Dell/Ubuntu products are offered in Australia :( )

---

### Post by Dragonbite on 2008-09-30
> **Karpah said:**
> Linux works completely with my laptop - stock-standard Dell Inspiron 1525 (that didn't come with Ubuntu.... none of the Dell/Ubuntu products are offered in Australia :( )

Imagine how much money Linux users could make if they could sell Windows CDs that come with their computer with the promise they'll never install it on the computer it came with?!

---

### Post by cl0ckwork on 2008-09-30
> **Dragonbite said:**
> Imagine how much money Linux users could make if they could sell Windows CDs that come with their computer with the promise they'll never install it on the computer it came with?!

well considering that they already paid for it with their computer, technically they would just get thier money back

---

### Post by Dragonbite on 2008-09-30
> **cl0ckwork said:**
> well considering that they already paid for it with their computer, technically they would just get thier money back

Details.. details... :D

---

### Post by CrazyArcher on 2008-09-30
IBM Thinkpad T42, works pretty well with exception of Compiz. Can't get all the effects working on its ATI Radeon 7500. :(

---

### Post by NoReflex on 2008-09-30
Everything works : Dell Inspiron 1520.

---

### Post by rustybronco on 2008-09-30
HP compaq nc6000 1.8 Ghz cpu... ubuntu 8.04

specs... [http://h18000.www1.hp.com/products/quickspecs/11794_na/11794_na.HTML](http://h18000.www1.hp.com/products/quickspecs/11794_na/11794_na.HTML)

Everything works except for the sd card reader (linux driver not available from the vender)

---

### Post by artir on 2008-09-30
Works 100% on custom built (FTW) laptop; using SiS motherboard, graphic card and infrared. PIV @ 2,6 GHz yay! and 256 Mb RAM

---

### Post by keptile on 2008-10-06
Everything works on my Dell XPS M1530 (not shipped with Ubuntu)
webcam, fingerprint reader, touchpad, mic, eject button, suspend, resume, hibernate, wireless, leds etc.

---

### Post by Calmatory on 2008-10-06
Works very well, except for the wifi. This particular laptop has BCM4311 chip handling the wifi, and configuring working drivers for it seems completely impossible task(even though many have succeeded!).

Then, there are same laptops with Intel wifi controller which have been working out-of-the-box fashion since Hardy. :)

---

### Post by laffinet on 2008-10-06
Lenove Thinkpad R61i.

Main thing not working is the internal microphone. Tried all kinds of stuff and eventually gave up. Kind of annoying.

---

### Post by ruisu on 2008-10-06
Acer Aspire 5510 
What doesn't work:
[LIST=1]
[*]B43 module has to be activated once loged in, it fails while booting.
[*]Bison Camera.
[/LIST]

everything else is fine :)

---

### Post by richg on 2008-10-06
I bought this one configured with Linspire 5.1.427 about three years ago. Downside now is only about 30 minutes on battery, though I use it on mains power now. It also weighs about 4 kilograms. I maxed out the RAM.

    Elitegroup 536

    * AMD Mobile Sempron 2800 (black chassis)
    * 15" XGA 1024x768 Display
    * 256MB DDR400 RAM DDR400 PC3200 DDR 200-pin SODIMM
    * VIA K8N800 Chipset and Onboard VGA (AGP 8X, 3D Capable)
    * CDRW/DVD Combo Drive
    * 40GB Hard Drive
    * 4 x USB 2.0
    * Integrated 10/100 Mbps Ethernet, 56k v.92 modem
    * Linspire O/S + DVD Player & 1yr CNR Gold Subscription
    * Mini-PCI Wireless 802.11G 
    * Weight 7 lbs
I will upgrade it to Ubuntu if I can ever get it to connect with wireless using Live CD. I have tried with 8.04 but no joy using wireless.
If next Ubuntu does not come with a working DVD player for movies I rent, this laptop will stay with Linspire.
Definitely old stuff. 
I now use my Asus EEE 4G wireless laptop for traveling.

I have a desktop running Ubuntu 8.04 for heavy duty work.

Rich

---

### Post by Kuroyume on 2008-10-06
Sony Vaio VGN-C240FE

Intel Core 2 Duo T5500
Intel 945GM Chipset
Intel 3945ABG wireless

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Works flawlessly out of the box with 8.10. 8.04 required booting with the AC adapter unpluged or removing the "quiet" option from GRUB due to an ACPI issue on the stock kernel. A kernel upgrade got rid of the issue.

Volume Fn keys worked on 8.04 but brightness did not. 8.10 made brightness keys back.

---

### Post by reg4c on 2008-10-07
Hey,
I have Acer Aspire 5920G and I am using the last beta of Intrepid Ibex.

Everything seems to work, even the card reader.
I have not tried a couple of things though:
HDMI port
Second monitor
PCMCIA Slot

Specs:
Intel Core 2 Duo 2GHz
Nvidia 8600
2GB Ram
160GB Drive
Intel 3945BG, works completely, but had to d/l the microcode manually
Acer Crystal Eye Webcam
Dual microphones with directional recording
The launchkeys: Browser, Email, BT, Keyboard Shortcuts, help, sleep, hibernate, mute

Things that don't work:
Media Touch Keys: For this there is a tutorial for Hardy but I don't want to try it since Intrepid recognizes the touchpads correctly
Directional Microphone: The mics work, its just that there isn't the "directional" thing
Am having some problems with Skype, but I can talk and hear and see and be seen
Hibernate

Things did not try:
Suspend/Sleep
IRDA
HDMI
PCMCIA
TV/OUT

---

### Post by L815 on 2008-10-07
Sony Vaio laptop VGN-FZ240E.

Everything works with the exception of a few things.

1. SD card reader is detected, but doesn't auto mount nor give me a directory in which to manually mount.

2. Brightness is an issue. I can't lower it and it causes my battery life to cut in half when not plugged in.

3. Webcam doesn't work (i haven't really tried yet)

4. (Haven't tried with Intrepid yet) but when I plug into S-Video, nothing happens.

So far that's about it. The compiz problems with videos have been fixed with my intelgm965 which is awesome. Other than that, everything has been running great.

Using Ubuntu Intrepid Beta


PS: My WLAN light finally works now, but it flashes when it's used. Hopefully it will be changed so it just is on or off. The flashing distracts me haha.

---

### Post by herbr on 2008-10-18
Dell Inspiron 1720.
Had a little "blip" with the Nvidia driver and had to use the Nvidia binary to get dual monitor support. Even upgraded to an Atheros wireless-N card and had no trouble.
I do run VMware and WinXP as a guest OS for potential Windows  contract work (yeuch).

Herb

---

### Post by Capt. Mac on 2008-10-18
I bought one of these and Ubuntu works 100% (as you would expect with a name like LinuxCertified)

[http://linuxcertified.com/linux-laptop-lc2100s.html](http://linuxcertified.com/linux-laptop-lc2100s.html)

It's the first laptop I've owned, also the first time I've really used Linux for an extended period of time. Love it.

Edit: Even Compiz-Fusion works perfectly, despite the graphics card being on their blacklist.

---

### Post by MasterNetra on 2008-10-18
My specs are in my signature. Although on fresh install of 8.04 it doesn't have any drivers for my wireless but with the new kernal it works perfectly now. (there was a set at first you got with the previous kernel that you had to download that worked moderately but meh it works well now.) However the Kernal does panic occasionally but it doesn't do it often...And hasn't lately...prehaps a few updates passed fixed that...idk anywho so its not 100% perfect but around 95%-99% i'd say. :P

---

### Post by archer6 on 2008-10-18
> **Capt. Mac said:**
> I bought one of these and Ubuntu works 100% (as you would expect with a name like LinuxCertified)

[http://linuxcertified.com/linux-laptop-lc2100s.html](http://linuxcertified.com/linux-laptop-lc2100s.html)

It's the first laptop I've owned, also the first time I've really used Linux for an extended period of time. Love it.

Edit: Even Compiz-Fusion works perfectly, despite the graphics card being on their blacklist.
Congratulations on your new laptop!

Thanks for the link, very interesting. 

Cheers

---

### Post by t0p on 2008-10-18
Working perfectly: my Asus Eee PC 701 4G (7 inch LCD, 4GB SSD).  Perfection is due to [these tweaks]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu%20eee%20riceeey").

---

### Post by archer6 on 2008-10-19
> **t0p said:**
> Working perfectly: my Asus Eee PC 701 4G (7 inch LCD, 4GB SSD).  Perfection is due to [these tweaks]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu%20eee%20riceeey").
Nice Work! 

Thanks for the link, I just picked up a 701 today.....:)

---

### Post by Dragonbite on 2008-10-19
While troubleshooting my laptop I tried throwing my Ubuntu LiveCD into my Thinkpad T61 from work.  Everything seemed to work nicely; wireless, etc.  I didn't bother downloading the Nvidia drivers but htey were listed in the Restricted Hardware Drivers.

It also worked alright from the LiveCD 8.10 beta I put on my USB thumb drive.

Since it's been so easy and supported I've been tempted to install Ubuntu dual-boot on the laptop more and more (except I kinda like my job, or at least having one..)

---

### Post by archer6 on 2008-10-19
I have had nothing but good luck with Ubuntu 8.04 installs on my ThinkPads. I've also done a few for friends and the results (on ThinkPads) are simply stellar. I could not be happier.

---

### Post by dracule on 2008-10-19
8.04 worked w/ everything on my laptop. just the b43 driver was super slow in my room (my old room had good wifi coverage so the speed difference from windows to linux was nominal)

Compaq presario v3000


but now with 8.10, the 'wl' driver which was supposed to speed things up doesnt work. :(

---

### Post by jangari on 2008-10-19
HP Pavilion dv1000 running Intrepid beta. 

I recently bit the bullet and upgraded to Intrepid because I was due for a clean installation. Hardy was slowing down due to my being a bit apt-get trigger happy and certain things were beginning to not work, and other background processes were chewing up 95% of my CPU. In fact, for the last 3 months, I couldn't even initialise a console (via ctrl+alt+F1, F2, F3, etc.).

This time, the only problem I've come across is support for an external LCD monitor, an acer 22". If I try to enable parallel desktops using the screen resolution settings, it forces me to enable virtual resolution settings, whereas under Hardy, it at least supported my external monitor's resolution (1680x1050). At the moment I'm stuck using 1024x768 on a 22" widescreen!! I've detailed the problem - but haven't received any reply - over [here]("http://ubuntuforums.org/showthread.php?t=949997"). But basically, the parallel desktop looks as though it works in principle - my mouse can be seen going between the two desktops - but the graphics card can't seem to handle it - everything's just random vertical coloured stripes, besides the mouse.

I might just try taking a screenshot.

---

### Post by bigbrovar on 2008-10-19
i got a dell ubuntu xps m1330 couple of days ago and when i powered it on and the OS that came with it installed . everything worked out of the box. including mp3 and dvds. however that stuff that amazed me the must is the finger print reader which allows to use my finger print during
 GDM session login
 Screensaver unlock
 Sudo and gksudo prompts
 PolicyKit authorization

never knew sudoing could be soo damn easy.

however i didnt like the fact that dell didnt allow me to set my partition tables the way i wanted. so i wiped off the preinstalled ubuntu and installed ubuntu.8.04.1 but when i did this the finger print and the wifi led indicator stopped working. no sweat i installed think finger following this guide . [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger) and the finger print worked just like before .. then i installed backport modules for my kernel version which fixed the wifi LED issue.

---

### Post by umattu on 2008-10-19
kubuntu 8.04 runs perfectly on my:
Thinkpad t-40
Intel(R) Pentium(R) M processor 1300MHz
768 MB RAM
Radeon Mobility M7 LW [Radeon Mobility 7500]
Belkin 802.11 a/b/g (Atheros inc. AR5001-0000-0000)
80GB Fujitsu HDD

Haven't had any problems with ubuntu on this machine.

---

### Post by gersoid on 2008-10-20
Dell Latitude 1520 - V pleased with it. Dual boot ubuntu / vista. Everything works fine except modem - don't care - and that does not work under Vista either!

---

### Post by motang on 2008-10-20
Well I voted for "Linux works completely with my laptop-I will post my hardware specifics"
Since Ubuntu 7.10 I had really good luck.  8.04 has been the best so far as I can suspend and hibernate on my laptop and 8.10 just takes the experience ever further with the new Linux kernel.  I have an *HP dv5000z* (about two and a half years old) the specs is:
> 15.4"
AMD Turion 64 ML-32
1 gig of RAM
ATi Radeon Xpress 200M
80gig Toshiba 5400 RPM drive

Compiz works, wireless works (just a couple of clicks in the hardware driver manager), all the function buttons work, media buttons work, sound works like it suppose to, multi card reader works like a charm, and the touch pad works with the scrolling, right click and left click (all on the touch pad) work!

---

### Post by archer6 on 2008-10-20
> **gersoid said:**
> Dell Latitude 1520 - V pleased with it. Dual boot ubuntu / vista. Everything works fine except modem - don't care - and that does not work under Vista either!
What size is your hard drive and how did much space did you allocate for Ubuntu, and Vista? 

Thanks

---

### Post by derekr44 on 2008-10-20
I've got Arch running on my old Toshiba Satellite 1415 S-173.  Everything runs very well, including nVidia drivers on the GeForce 420.  The hard part was actually fixing a stupid configuration that Toshiba did for the screen.  I had to make a custom edid.bin file to force the screen to 1024x768 because of the way the hardware itself is made.

Other than that, it runs great!

---

### Post by ArdentMoth on 2008-10-20
I use an Acer Aspire 5610.

I cannot get my onboard Intel Core 2 Duo T2050, GMA 950 Graphics to work.

Xorg Intel drivers are, as of this morning, still a no-go. They don't fix what i've come to know as the "My OpenGL and DirectX both seem to think that my 3D support is nil" error.

OpenGL for some reason is disabled. I don't have a problem with that for the most part, but I can't find a graphics driver for my Intel onboard sh-t, so, therefore, I can't find a driver for OpenGL that will work either. Doubly so with DirectX.

Help?
------

I also am experiencing the common "my specialty-programmed keys aren't working" error. The volume buttons, the mail/internet/Acer "e" buttons, and my built-in bluetooth seem to be lost causes.
------
So, I voted "It works partially, and I don't have a clue why the broken stuff doesn't work."

Thoughts?

------

Lastly, If I were to build a top-o-da-line computer, I suppose it would be wise to look at the Ubuntu compatibile hardware lists that have been generated by succesful users over at whaterverthesiteis.com (ubuntuwhc orsomething?) anyway..... that's a different topic...

And having a white russian in the morning instead of a coffee is wonderful.

---

### Post by ZankerH on 2008-10-20
I've got two laptops right now, both run Linux and Linux only. Pretty much everything worked out of the box on both of them.

1. Compal FL71
-CPU: Intel C2D, 2.6GHz
-RAM: 2GB, DDR2
-HDD: 160GB
-Graphics: Nvidia 8800GT
-Display: 15.4" widescreen, 1280*800
-Distros: Ubuntu 8.04.1, Debian Lenny testing

2. Asus Eee PC 901
-CPU: Intel Atom, 1.6 GHz
-Ram: 1GB
-Storage: 20GB SSD
-Graphics: Intel GMA950 integrated graphics
-Display: 8.9" widescreen, 1024*600
-Distros: Debian Etch, Mandriva 2009.0

---

### Post by mogwai on 2008-10-20
I voted "Linux works partially with my laptop-I will post the specific problem(s)".
I have a recent Thinkpad R61/R61i (about 8 months old).
Ubuntu has been really good on this. First my WLAN light didn't work in gutsy, again in hardy. But I did notice it now works in Intrepid Beta.
Almost everything has worked out-of-the-box.
I have had problems with my audio (Conexant CX20549 Venice). Playback works but the microphone is dead.
Also, have had issues with my graphics (Intel GM965 w/ GMA X3100), not playing some 3D apps nicely (games in particular). But seeing I am not an avid gamer, this hasn't stopped my completely wiping Vista and replacing it with Ubuntu.
Haven't really tested the card-reader, but it works (out-of-the-box) with SD cards.

specs:
Lenovo/IBM Thinkpad R61 8932-A28
Intel GMA X3100 Graphics
Intel Wireless 4965AGN
2GB RAM
Conexant CX20549 (Venice) ICH8 Intel HDA Audio

---

### Post by cpetercarter on 2008-10-20
I have a Packard-Bell E4715 running Hardy. No problems at all.

---

### Post by tezer on 2008-10-21
Everything works (had some problem with sound): ASUS A6F

---

### Post by geofreitag on 2008-10-22
ubuntu mostly works for me.  Polywell something running XP and Gutsy.
Pentium M 2.13 GHz; 1GB ram; NVidia 6600; Intel 2200 wireless; card reader.

pretty sure i remember the card reader working from the get-go (dont use it much)
WiFi and 3D cards functioned right off, but needed tweaking for their full potential (although something about my wifi doesnt like it when i use any kind of encryption, it intermittently drops or wont make a connection, weird)
Hibernate/ suspend didnt work and i havent tried using them in months
multimedia keys (specifically the wireless on/off switch) dont work, nor does FN (was actually looking for a fix for those when i found this.  does anyone know of a way to map the various keys and buttons to write scripts for them?)

oddly enough, my touchpad became *more* functional with ubuntu (i didnt know it had a side slider and couldnt figure out why it would spaz until a friend figured it out)

---

### Post by xpod on 2008-10-22
Theres 4 laptops floating around here at the moment and Linux works just fine on them all.Mostly *buntu of course but they`ve all had umpteen Distro`s tried on them at one point or another.
Theres two Sony Vaio`s(PCG-GRX316MP & PCG-GRV516G) with Ubuntu & Ubuntu/XP respectively,one Dell Inspiron 6000 with Ubuntu and an ECS Elitegroup A530 with Puppy.

---

### Post by eentonig on 2008-10-22
HP Pavillion dv9540eb

So far, everything seems to work flawlessly. Suspend, Hibernate, Camera, Sound, touch buttons, ...

---

### Post by FutanariKitty on 2008-10-22
-Linux works completely with my laptop-I will post my hardware specifics-

I own a Dell Latitude D820, and every single component works out of the box, with the possible exception of the IR and maybe the EC slot, simply because I haven't actually tested either of these (and have little need to do so). Video works perfectly with the NVidia drivers with full acceleration, sound is perfect, wifi and wired are completely functioning, etc.

Dell Latitude D820-
Core 2 Duo T5500 @ 1.66GHz
2Gb RAM
100Gb SATA HDD
NVidia Quadro NVS 110M

---

### Post by wannadumpwindows on 2008-10-22
I have a Toshiba A105-S2236. It works perfectly except for one thing. 

Wireless. I know, shocker. It has the infamous AR242x chipset. I got it working easily with Madwifi, but it didn't work out of the box.

I also have an Asus Eee PC 701. It works really well after running the Riceeey script for it. But on first boot after install, it was a nightmare. But I love it now.

---

### Post by elefantcrossing on 2008-10-22
my dell xps m1530 works great with ubuntu 8.04.
bluetooth, camera, wifi, sound, standby, ir-remotecontrol, fn- and multimedia-keys worked out of the box.
fingerprint reader and nvidia drivers were easy to install.
backports-modules are only needed to get the wifi led going.

the only thing not working all of the time is touchpad scrolling

all in all the best linux on laptop experience i've had so far

specs:
intel core 2 duo cpu t9300
nvidia geforce 8600m gt
seiko wuxga (1920x1200) display
intel 4965agn wifi

---

### Post by roelpeeters on 2008-10-22
Another happy Dell XPS m1530 user. Everything except fingerprint reader works out of the box with ubuntu 8.04.1. The only things that are not so smooth are:

[LIST]
[*]adding i8042.nomux=1 as kernel parameter for the touchpad not to go crazy.
[*]installing backports to get the wifi-led working (mind you, wifi works out of the box with WPA2)
[/LIST]

For the rest I am a happy camper!

specs:
Dell XPS m1530
T9300, 2.53 Ghz, 6Mb L2
4 Gb
NVidia 8600M GT, 256Mb
400Gb HDD
15.4" 1680x1050 WSXGA screen
Intel AGN 4965 WIFI

Roel

---

### Post by johskar on 2008-10-22
Works perfectly out of the box with Ubuntu 8.04 for me :)

Dell Lattitude D610
 Intel Pentium M 1.86GHz
 1.5GB Ram
 60GB 5400rpm pata hdd
 1400x1050 display

lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by rzrgenesys187 on 2008-10-22
I have a Satellite P105-S6177 and it runs ubuntu very well now.  In the past I've always had sound problems but with each release it gets easier and easier to get sound working.  The only problem I have is that I don't get sound when resuming from suspend.  Otherwise everything works great

---

### Post by au-steve on 2008-10-23
I have a acer 5630, the problems i have are with the graphics card (Geforce Go 7300) not being able to use an external monitor or dual screens, and a wireless issue with the Intel Pro 3945ABG which is known about with a few people but i am yet to gain the expertise to fix the issue.
Other than that im extreamly happy with 8.04 and have just changed over from dual boot XP to stand alone ubuntu.

---

### Post by FutanariKitty on 2008-10-23
> **au-steve said:**
> I have a acer 5630, the problems i have are with the graphics card (Geforce Go 7300) not being able to use an external monitor or dual screens, and a wireless issue with the Intel Pro 3945ABG which is known about with a few people but i am yet to gain the expertise to fix the issue.
Other than that im extreamly happy with 8.04 and have just changed over from dual boot XP to stand alone ubuntu.

That's odd...I have exactly the same network card and it's fully functioning for me...

Good luck though! Ubuntu had out-of-the-box support for the wireless for me without a hitch.

---

### Post by SyCo123 on 2008-10-23
HP DV5215us laptop with a broadcom 4318 wireless card. I still wake up at night in cold sweats thinking about it. 

Thanks to the good people here at UbuntuForums.org it is all working great (pointless spinny cube and everything) and has been for over a year now.

I have to confess I went back to a windows partition because of netflix. Dam you netflix.

Actually that does raise something I've been meaning top post about. Ubuntu went on first over the old Win Media Edition wiping it. Then I had to move Ubuntu off the start of the drive because poor old windows just has to be first. Now kernel updates kill my grub script and I have to manually edit it each time. Bit of a pain but no problem for me. I would imagine it would be beyond a total noob and there PC would effectively be bricked until the can boot it. Maybe I should start a post about it? Yes, I think I will.

Edit: and so I did
[http://ubuntuforums.org/showthread.php?p=6020960#post6020960](http://ubuntuforums.org/showthread.php?p=6020960#post6020960)

---

### Post by ryan on 2008-10-23
Dell Vostro 1400- Everything works

Intel Core 2 Duo 1.60GHz 
14.1 inch WXGA+ TFT display 	Works, 1440 x 900
256 MB NVIDIA GeForce 8400M GS 	
2GB DDR2 SDRAM, 667MHz, 2 DIMMs 
120G 5400RPM SATA Hard Drive 
56k softmodem, part of Intel audio card 	Not tested. 	BIOS reports: Conexant HDA D330 M
8X CD/DVD Burner 
Intel PRO/Wireless 3945 802.11a/g Wi-Fi Mini Card
85 WHr 9-cell Lithium Ion Battery 
Intel 82801H (ICH8 Family) HD Audio Controller
Keyboard volume controls 	Works 
S-video TV-out 	Not tested
Firewire IEEE I394a port 	Not tested 	
ExpressCard slot 	Not tested 
8-in-1 memory card controller 	Not tested

---

### Post by Vadi on 2008-10-23
My linux came with my laptop... system76 serval 3 here.

Hardware info: [http://dl.getdropbox.com/u/84880/hardinfo_report.html](http://dl.getdropbox.com/u/84880/hardinfo_report.html)

---

### Post by bazu on 2008-10-23
i`m with fujitsu siemens amilo p 3553 and dosen`t work buttons for brightness and for wirewess and to start music player, silent mode. i hope to help me. 10x

---

### Post by rienk on 2008-10-23
Ubuntu 8.10 64-bit

compaq nw8440
ATI Mobility Fire GL V5200
Processor  	Intel Duo 2 Core T7600, 2.33 GHz
RAM 	2048 MB (667 MHz) DDR2 (1 DIMM/Module, 1 slot available)
Hard Drive 	SATA 100 GB 7200 RPM
Optical Drive 	HP MBII SuperMulti (DL) DVD+/-RW Drive, Details
Display 	15.4-inch TFT WUXGA WVA display with 1920 x 1200 max resolution
Video Card 	ATI Mobility Fire GL V5200 w/ 256MB of RAM
Network Cards 	10/100/1000 Wired, IEEE 802.11 a/b/g Wireless, Bluetooth
USB 	Three USB 2.0 ports

-fingerprint sensor not working.
-ATI fglrx proprietary video driver not working since upgrade to 8.10

/Rienk

---

### Post by zerubbabel on 2008-10-23
Ubuntu 8.04 32-bit running on Dell Latitude D830 2G RAM 160G HD Bluetooth

---

### Post by pirattrev on 2008-10-23
Thinkpad T61
Nvidia 140M Graphics Card
120gb HD
Intel a/b/g wireless
Intel turbo memory <--- doesn't work
2gb RAM

---

### Post by deftone32 on 2008-10-23
Installed 8.10 Intrepid on a Gateway M-6750. Two problems. 
    1. Wireless (Marvell TopDog) had to be installed using
       ndisgtk. Not a problem as I knew this would probably
       not work out of the box. Hopefully Ubuntu will add
       support to this hardware.
    2. Intel GM965 video is BLACKLISTED! This blew me away
       considering there's a ton of notebooks with this 
       chipset. I'm praying when Ubuntu Intrepid 8.10 finally
       goes live they have a fix for this. I would really like
       to use Compiz-Fusion and open this baby up!

Overall I love this OS. I will keep my dual boot of Vista and
Ubuntu until Ubuntu can fix this big problem with the Intel GM965.

---

### Post by kleo skywalker on 2008-10-29
I voted I'm interested in using linux on a laptop but haven't found the right laptop. 

I am trying to decide between the Dell Vostro A860 (best matches requirements and budget but new model; comes with Ubuntu pre-installed), the Dell Inspiron 1525 (concerned about overheating problems; comes with DOS), and the Lenovo Thinkpad R61i (have had a very poor experience with Lenovo; comes with DOS).

I have a thread running about this [here]("http://ubuntuforums.org/showthread.php?t=897384&page=3"). Advice is very welcome.

---

### Post by Dragonbite on 2008-10-29
My laptop has been functional for a while, running 8.04 except now the wireless card seems to have gone kaput.

In testing that my router was up and running (and thus ensuring the issue was on my laptop's end) I ran my work laptop (Thinkpad T61) under 8.04 live cd and wireless was found to work "out of the box" (though the nVidia graphics card needs proprietary drivers).

So I'm looking at getting the Intel wireless mini-PCI card for my laptop to replace the Broadcom one that is dead.  If all goes well then my laptop will be fully Ubuntu compatible "out of the box" :guitar:

---

### Post by uncibex on 2008-10-29
I think I'd call mine an almost fully functioning linux laptop.  I run ubuntu 8.10 on dual boot with windows vista (which is the reason I have linux in the first place).  I have an HP DV2000 laptop and aside from HP's own hardware issues, I have very few problems running linux.

The only problems that I frequently run into are with my wireless connection.  I never have any trouble connecting, but I often run into problems sustaining the connection.  My connection seems to drop far more easily and more frequently than those around me running windows.

The second wireless problem I have is that I haven't been able to connect to the internet with a manual connection, only roaming mode.

No major problems though, there are ways to work around both of these things.

---

### Post by 2j4ez on 2008-11-04
It was not at first

When I installed ubuntu 8.04.1 nothing worked apart from the ethernet socket

Now every thing works

Wireless
DVD Burner 
Graphics
USB
Bluetooth
Suspend 
Sound

I'm yet to find anything that does not work on my system

---

### Post by thomasboleyn on 2008-11-04
My Sony Vaio pcg-k215z (specs here [http://www0.dealtime.co.uk/xPF-Sony-Vaio-K215Z](http://www0.dealtime.co.uk/xPF-Sony-Vaio-K215Z)) will only run normally
without any issues on feisty, which I am using currently. I have had Gutsy, Hardy and Intrepid on it in the past,
but have had to use the boot option 'acpi=off', which annoyingly stops my atheros wireless card working, and doesn't allow the
laptop to shutdown. I have managed to compile the latest builds of AWN, Pidgin, Transmission, and a few other programs that I miss
using, so it is not too bad, plus compiz seems to run A LOT faster on feisty that Gutsy onwards (had to use a backport as it is not enabled by default on feisty).

Another user on here messaged me recently to say that he had the same laptop as me and had managed to get xubutu hardy working with wireless by using the boot parameters 'nohz=off' and 'highres=off', though when I tried this it 
didn't work for me. He then suggested adding 'xforcevesa' in addition to those two, which worked, but meant I would be permanently stuck with a tiny resolution screen, and no special effects whatsoever (rubbish, and not something I was willing to sacrafice just to get wireless working on the latest distro).

To be honest I am totally happy with feisty, it's just frustrating that there seems to be no way to get anything newer working on my laptop.:KS

---

### Post by borfil on 2008-11-04
Hi I think I desagree with your comment about Intel base Laptop.
I have 6 laptop working for my organization and a number of over 20 desktop.
We just migrated to Linux about 2 month ago. We order both Kubuntu and Ubuntu 8.04 from conical I downloaded a copy from the net and loaded and old laptop which my daugther was using at the house and I could not load XP so it was still using 98.
Well 35 minutes later I was happy as hell. not only did it work but all functions of the laptop were performing great and to boost it actually increase the performance of the pc. I then proceded to order both version mention earlier and now we have all our pc running, to my sorprise, all my AMD base laptop and desktop, work perfectly from moment one, nothing to do other than minor adjustment , but all my 4 PC Pentium D Dual Core 3ghz had troublew dealing with linux. I needed to bring in my programer to spend 6 days to make them work, Even a new Neo laptop which has lots stuff not normally found on any pc, work like a charm.

What we did was do a complete clean install on the intel one we use a split drive to keep windows capabilities just in case. but it work perfect and the transfer of data was like a charm. the only issue has been with the use of 4 pc that are connected to our server and the net via Dkink DWL-G122 Rev C1 uSB adpaters, which have been hard to connect, linux recognize them but they don't comunicate with the router, we just located the linux driver at Dlink Philippines server so we are now fully functional.
But the Intel Base PC were a Pain in the A--- to deal with. we are very happy and it will save use a little over $5000 in licensing fee to MS, and other upgrades from other companies.
We would not have to hire an outsider to work on the pc, for we are sending 3 of our own to take linux clases. the only headache we have now is deciding which version to keep, Ubuntu or Kubuntu, I'm more incline toward Ubuntu, it is much faster and cleaner than the kubuntu version. But that is my personal opinion, but the fact is that ubuntu perform much faster than kubuntu and as a business man, as long as I can do more and just dress the desktop some, I dont care, all that matter is the bottom line, and ubuntu just put 5 big one back in my pocket this year. I wish I had discover it a few year back I could had buy a BMW now. HE HE HE.

thanks:KS:KS  :p ):P

---

### Post by zgornel on 2008-11-04
**Compaq 6820s** - Core2 T7250, 4GB Ram, 250GB 7200rpm HDD, Intel 965PM Chipset - i3945ABG wireless, Intel E10/100MB Ehternet, ATI X1350 128MB (open source 'radeon' driver), Bluetooth, cardreader, 3xUSB -Everything works out of the box with **Ubuntu 8.10 [x86-64]**.

**Toshiba L20 - 102** - Pentium-M 740, 2GB Ram, 160GB HDD, Intel 915GM, i2200BG wireless, Realtek 8139C 10/100MB Ehternet, 3xUSB - Everything works out of the box with** Kubuntu 8.04.1 [i686]**.

---

### Post by tliotis on 2008-11-04
Hello i have acer 5021wlmi and sometimes the pc "FREEZES" and the only that works is control alt printscreen B  or the shutdown button.i think its my ram problem :/
i will buy in the future new with intel graphics e.t.c.!
linux owns :D

---

### Post by schmolch on 2008-11-04
Without control over the powersaving modes from wireless cards, there is no such thing as a fully functioning linux laptop.

---

### Post by thomasboleyn on 2008-11-04
> **schmolch said:**
> Without control over the powersaving modes from wireless cards, there is no such thing as a fully functioning linux laptop.

Do you think this what is causing the issue with Gutsy onwards then?

---

### Post by mrm48 on 2008-11-04
HP Pavilion zv6000 w/ ubuntu 8.10 64-bit version (GNOME)

-Previous-
ubuntu 7.10 (GNOME)
xubuntu 8.04 (XFCE)
ubuntu 8.04 (GNOME)

Few problems so far, but those were easily solved.

"Problems"
-Broadcom wireless card was hard to get working in 7.10, but easy since 8.04

-Conflicts between NetworkManager and my university's wireless network (uses PEAP, was hard to authenticate until I figured out the proper settings)

-Flash player is flaky 

-Browsing samba shares on the home network with xubuntu was a pain (had to restart fuse for every session, otherwise the shares would not show up in Thundar)

-Volume buttons below touchpad broken as of 8.10

---

### Post by TwiceOver on 2008-11-04
Just an update to my previous post somewhere back there...

Dell Inspiron 1501 Fully Functioning under 8.10 Intrepid.

---

### Post by Viranh on 2008-11-04
Mine is fully functioning. I have a System 76 Serval Performance.
Specs:
2.5 GHZ Core Two Duo
4 Gb RAM
Nvidia 8600M GT 512
Intel 4965 a/g/n wireless
Broadcom gigabit ethernet
webcam
bluetooth
fingerprint reader (sort of)

I guess it's a bit of a given that mine works out of the box since I bought it pre-loaded with Ubuntu.

---

### Post by archer6 on 2008-11-04
> **Viranh said:**
> Mine is fully functioning. I have a System 76 Serval Performance. I guess it's a bit of a given that mine works out of the box since I bought it pre-loaded with Ubuntu.
Nonetheless, Celebrate! You got what you paid for which is more than some "Linux Laptop Companies" provide. 

I have personal experience with that. 18 months ago, when my work schedule was relentless & I had to time no deal with an install and setup of Linux myself, I caved in a spent a boat load of money on a Linux ThinkPad from [[COLOR="RoyalBlue"]Emperor[/COLOR] Linux]("http://www.emperorlinux.com/"). Wow, what a mistake that was. It's what happens when one is in a hurry as I didn't consider others, just went with Emperor. Besides being horribly over priced, they have terrible service. The web site looks great, it's all warm and fuzzy about how they appreciate and take care of their customers. But buy one from them and the slap of reality is they are arrogant, hard to reach, and their proprietary Linux software load of any distro they offer is hard to deal with. They failed to test the setup, and when I received it hardly anything worked properly, including your basic boot process. They took it back, "repaired it" and returned it to me. Still fraught with issues. After shipping it back three times at my expense it was still not right. Result: I wrote off the $2800.00 expense. A total waste of money. 

This time around, having the time, I did it myself with Ubuntu 8.04 and could not be happier. I've installed it on four of my ThinkPads all of which have turned out great. I could not be happier.

---

### Post by swisscow on 2008-11-04
eee pc 901 running mandriva 2009

Everything works, well everything that I've tried. And out of the box too


Come to think of it the original xandros linux on it "worked" out of the box, just not very well at times.

---

### Post by spawn. on 2008-11-04
ThinkPad T61p - Nvidia 256MB OpenGL 570M, 2GB RAM, 2.6GHz Core2Duo, Ubuntu 8.04 (32 bit)

Once you get the necessary packages, updates, and programs to do your stuff, you are good to go. I can do everything I need to do.

---

### Post by moviemaniac on 2008-11-04
IBM T40 and everything works in hardy - including 3D acceleration with the open-source radeon driver :D
Not planning on updating to 8.10, though - never change a running system ;)

---

### Post by archer6 on 2008-11-04
> **moviemaniac said:**
> Not planning on updating to 8.10, though - never change a running system ;)
Very wise advice...You and I are on the same page. I have 8.04.1 running well on my ThinkPads and I'm not about to mess with a good thing...;)

---

### Post by Dragonbite on 2008-11-04
> **moviemaniac said:**
> IBM T40 and everything works in hardy - including 3D acceleration with the open-source radeon driver :D
Not planning on updating to 8.10, though - never change a running system ;)

Me too.. I'm not rushing to update to Intrepid though I did install it on a 2nd hard drive to fool around with it and there are some nice touches but nothing really driving me to upgrade.

Jaunty is supposed to have some really nice improvements (like boot time) so maybe I'll try then.

I also have to consider that right now my wife is using Ubuntu on my laptop and she's not highly technical so I best not rock-the-boat, she's just getting used to it right now :)

---

### Post by T-AA on 2008-11-04
Works perfectly on my old acer aspire 3610

---

### Post by donec on 2008-11-04
I'm running an 8Gb SSD for root and a 16Gb SDHC for home AAO (Acer Aspire One) with Mandriva 2009 Gnome. The **only** thing I have found that doesn't work right is suspend. I don't have a desire to use it and never have so it is unimportant to me except that if the option is available it should work. (Almost no OS will support suspend or hibernate correctly on every computer)

I have several computers and they run both Linux and Windows. The AAO runs better than all the rest it has better eye candy and more things work than any other Linux distro or Windows on the other computers.

---

### Post by moviemaniac on 2008-11-04
> **Dragonbite said:**
> Me too.. I'm not rushing to update to Intrepid though I did install it on a 2nd hard drive to fool around with it and there are some nice touches but nothing really driving me to upgrade.

Jaunty is supposed to have some really nice improvements (like boot time) so maybe I'll try then.

I also have to consider that right now my wife is using Ubuntu on my laptop and she's not highly technical so I best not rock-the-boat, she's just getting used to it right now :)

Actually I wanted to upgrade to Intrepid on my T40. But I use 8.10 it on my main workstation and experience many regressions compared to hardy with applications I daily use that I'm actually glad having 8.04.1 as a backup-system that "just works" on my notebook. I guess I won't replace it until support for hardy runs out and by then it'll be time to get a new notebook :D

> **archer6 said:**
> Very wise advice...You and I are on the same page. I have 8.04.1 running well on my ThinkPads and I'm not about to mess with a good thing...;)
Good to see more guys using Thinkpads - here at university most guys think you're nuts when you buy such an expensive notebook. Personally, I'll choose T-series thinkpads again and again and again. They don't look fancy (which I really like), are well made and very reliable, sturdy machines. I frequently get asked to have a look at cheap notebooks when they break down - a Thinkpad has never been amongst them. Or when guys experience issues connecting cheaper machines to the beamers when they do presentations - most of these machines (running Windows) have troubles connecting to the beamers, need restarting and changing of settings. I plug the beamer in, fire up my T40 running Ubuntu and it just works :D

---

### Post by archer6 on 2008-11-04
> **donec said:**
> The **only** thing I have found that doesn't work right is suspend. I don't have a desire to use it and never have so it is unimportant to me. (Almost no OS will support suspend or hibernate correctly on every computer)
This is exactly how I feel and it has also been my experience over the years no matter if it's a mac or pc laptop, or what OS it's running I have yet to experience a laptop that will suspend or hibernate reliably. Thus I quit trying, and I don't miss it one bit. Not only that but now with Ubuntu, the boot up and shut down times are so fast as compared to windows, it's simply no big deal....;)

---

### Post by Bölvaður on 2008-11-04
My screen resolution is way too little or way too big. I havent been using it much so I havent checked what driver it is using. But it was working perfectly on 7.10

---

### Post by zoomy942 on 2008-11-04
after some hand holding, everything works great - PC in sig

---

### Post by mkrahmeh on 2008-11-04
Acer aspire 4920 
intel core2 duo T7300 with 1 GB DDR2
intel graphics media accelerator x3100

as far as i notice, i still have some suspend issues, but its not a big deal anyway..
but i still suffer from not being able to connect through my wireless card to the net (actually its completely my fault coz i ddnt attempt to tackle this particular issue yet :redface:)

---

### Post by new2*buntu on 2008-11-04
My laptop works perfectly with Ubuntu. My specs are:
1.6 GHz Intel Duo Core Processor
512 MB RAM
80 GB HDD, partitioned with 10 GB Debian, 10 GB Ubuntu, 55 GB Documents, 1.5 GB Swap
Integrated Intel Graphics
Wireless Logitech Laser Mouse (USB)
Intel Pro Wireless 3945

---

### Post by moviemaniac on 2008-11-04
> **archer6 said:**
> This is exactly how I feel and it has also been my experience over the years no matter if it's a mac or pc laptop, or what OS it's running I have yet to experience a laptop that will suspend or hibernate reliably. Thus I quit trying, and I don't miss it one bit. Not only that but now with Ubuntu, the boot up and shut down times are so fast as compared to windows, it's simply no big deal....;)
I have yet to try hibernating on my iMac (as I don't need it) but it has always worked with hardy on my T40.

---

### Post by archer6 on 2008-11-04
> **new2*buntu said:**
> My laptop works perfectly with Ubuntu.
What brand and model is your laptop?

---

### Post by archer6 on 2008-11-04
> **moviemaniac said:**
> I have yet to try hibernating on my iMac (as I don't need it) but it has always worked with hardy on my T40.
Heh!.... as I sit here laughing at myself. I didn't bother to try it until you posted this, so then I closed the lid on my ThinkPad T60 and presto! It works... simply amazing... you gotta love Ubuntu!

---

### Post by 73ckn797 on 2008-11-04
See signature for specs.

Hardy works great. SD reader works, DVD, all USB ports, Compiz.

Desktop has also been trouble free. It is a BYOPC. I have Hardy and Intrepid running great. I use the laptop daily for work.

Intrepid is good on my son's except for the ATI HD3450. Cannot get effects to set and available restricted drivers do not work.

---

### Post by mendozaro on 2008-11-04
My laptop just works.

Also my desktop (i mention the desktop also cause its not built from pieces) works perfectly.

For specs look at my signatures.

Best regards.

---

### Post by macabro22 on 2008-11-04
Play/Pause, Forward, Reverse and the "media direct" button won't do anything in Intrepid Ibex on a Dell XPS m1730. It used to work alright Hardy Heron.

Everything else works.

---

### Post by archer6 on 2008-11-04
> **macabro22 said:**
> Play/Pause, Forward, Reverse and the "media direct" button won't do anything in Intrepid Ibex on a Dell XPS m1730. It used to work alright Hardy Heron.

Ahhh... the very reason that I left Gutsy Gibbon running perfectly on my T42 ThinkPad.
Did a clean install of Hardy Heron on my T60 ThinkPad & everything works.
As I've learned the hard way why mess with a system that's running trouble free...;)

---

### Post by Dragonbite on 2008-11-05
> **archer6 said:**
> This is exactly how I feel and it has also been my experience over the years no matter if it's a mac or pc laptop, or what OS it's running I have yet to experience a laptop that will suspend or hibernate reliably. Thus I quit trying, and I don't miss it one bit. Not only that but now with Ubuntu, the boot up and shut down times are so fast as compared to windows, it's simply no big deal....;)
Heck, my work Lenovo Laptop running Windows XP won't hibernate or suspend!
But Ubuntu does on my personal Dell.

---

### Post by Kevbert on 2008-11-05
I'm using an old Acer Travelmate 803Lci with bluetooth, ethernet and wireless. Wireless is Intel based. Display is ATI Radeon Mobility 9000.
All keyboard function keys are working.
Not everything worked out of the box, but fixes from the forums resolved these.

---

### Post by jacko999 on 2008-11-05
any know of a good how to for a alienware M17 laptop?

---

### Post by Arabiest on 2008-11-05
MOST OF MY MAJOR ISSUES WITH UBUNTU 8.10 HAVE BEEN SOLVED AND i AM ABLE TO FULLY FUNCTION MY PC AS WAS WITH 8.04. THANKS TO UBUNTU TEAM AND MANAGEMENT AND TO FORUM MEMBERS WHOM HAD BEEN OF GREAT HELP TO RESOLVE MY INSTALLATION ISSUES.

MY MAIN ISSUES ARE:
1- WIRELESS...WORKING GREAT!
2- MOBILE INTERNET SHARING....WORKING PARTIALLY...BUT ACCEPTED FOR NOW.
3- WIRED NETWORK...WORKING GREAT!
4- KEYBOARD....WORKING 90% EFFICIENT WITH SOME KEYS NOT FUNCTIONING SUCH AS ARROWS...BUT ITS OK FOR NOW.
5- BRIGHTNESS CONTROL...WORKS GREAT!
6- SOUND...WORKS GREAT!

MY PC SPECS:
VENDOR: FUJITSU SIEMENS
MODEL: T4210 (TABLET PC)...TABLET SPECIFIC FEATURES NOT EXPLORED YET SUCH PEN...ETC.
FOR MORE DETAILS, YOU VISIT VENDOR SITE.

---

### Post by Idaho Dan on 2008-11-05
Fully functioning. HP Pavilion ZV6130US, just upgraded to 8.10.

---

### Post by JohnSearle on 2008-11-05
Qosmio F10-ER (Canadian G10 equivalent - with factory replaced/upgraded motherboard, since there was a unacknowledged manufacturer fault).

Notebook is about 3 years old, and Ubuntu runs just fine on it.

- John

---

### Post by user-max on 2008-11-05
My HP dv2000 works perfect on new Ubuntu 8.10 release. That is starting with the web-cam, and ending with quick launch buttons and SD card reader. Wireless works great too, of course after installing Broadcom drivers.

Even Suspend/Hibernate work perfect.

---

### Post by BrianElliott0218 on 2008-11-06
I bought a new HP DV9000 that came with Vista (crashed IE right out of the box for no apparent reason).  For reasons that I have to say are common with dissatisfied Vista users, and after trying to get WinXP to run on the laptop (HP won't give up the XP drivers for the machine) and because I have been looking into running Ubuntu and moving to Linux in general, I did the 8.04 CD install.

Results:  This is the first machine I have been able to get CompizFusion to work with my video cards on Ubuntu.  Very cool stuff.  The machine ran after install (which took about 15mins, compared to the WinXP initial install at over 1.5hrs plus configuration time) with all the drivers from Ubuntu.  Everything ran better than on Vista and XP right away!  The 8.04 Ubuntu distro rocked on this laptop, and I was eager to move to the 8.10.  :) I did that, and here are the problems that I have been trying to resolve since the upgrade to 8.10:  :(

:confused: Sound runs fine, but the button controls are completely independent of the sounds running on Youtube, and other videos and sound applications (like Pandora.com).  This is extremely frustrating so far, as I have not been able to find a solution yet.  The sound control images come up but the sound still blasts at full volume even if I mute the controls with the sound buttons.  The sound does adjust on eeach application's sound control though, but it should do both.

:confused: The internal mic doesn't work anymore.  Not at all...  I have tried several fixes for this, but still no success.  This, of course, means I can't use Skype, which is a tool I use with my clients.  The camera does seem to work with no problems.

:confused: Oh yeah, the middle mouse button on my M$ Wireless USB mouse won't click the scroll icon on or off.  It will open a new link in a tab in Firefox though...  The mouse console in preferences does not allow any changes to the middle mouse button.

:confused: And the last issue that I have noticed, so far, is that when the system is on the Ubuntu boot screen with the bar going back and forth, it will freeze unless I hit keys on the keyboard.  It will move a bit each time a key is pressed (usually I press "Y").  I thought I was missing messages asking for an answer, and that's when I started hitting keys. When we get to the one way progress bar (instead of the back and forth), and then boots 'normally'.

Those are the four little issues I have with the Ubuntu 8.10 update.  Glad to have any resolutions sent my way on the forums, but I will continue to search for a resolution to these problems as well.  I'll update here if I find any solutions.

By the way, I am fairly new to Ubuntu, and Linux in general for that matter, but I have 30 years of tech experience repairing, building and configuring systems...  So, these are not simple issues thus far, though I am certain there are some simple answers for them.

:KS I look forward to any support available on these problems.  Please remember that each issue listed was not an issue when I installed 8.04. Just after the update to 8.10...  Thanks!:guitar:
~BrianElliott0218

---

### Post by mips on 2008-11-06
> **BrianElliott0218 said:**
> ...and after trying to get WinXP to run on the laptop (HP won't give up the XP drivers for the machine)...

You can get ALL the drivers from the chipset manufacturers. No big deal.

---

### Post by litmos95 on 2008-11-06
Ubuntu Hardy runs smoothly on my Zeptop Znote 6214W. 
Specs:
Intel Core2 Duo T7600
2 x 1 GB Hynix DDR2 Ram @ 5300 Mhz
Nvidia GeForce 7600 Go
Realtek ALC861 Sound card (S/PDIF output not supported)
Intel Pro/Wireless 3945 (802.11 a/b/g)
Built-in 3i1 cardreader (MS cards not supported)
Built-In Bluetooth

---

### Post by archer6 on 2008-11-06
> **BrianElliott0218 said:**
>  The 8.04 Ubuntu distro rocked on this laptop, and I was eager to move to the 8.10.  :) I did that, and here are the problems that I have been trying to resolve since the upgrade to 8.10:  :(

Remember that each issue listed was not an issue when I installed 8.04. Just after the update to 8.10... 
If there is one thing I've learned the hard way, as you are, is **"why upgrade"** and risk it all (time & effort) just to have the "latest". And this applies to any OS.

**Before I Upgrade ** I ask myself these questions:

1) Is my laptop running well now? 
2) Is it doing everything I need it to do? 
3) Do I really need to upgrade? 
4) What's in the upgrade? 
5) Do I need what's in the upgrade?
6) Or do I just "want" what's in the upgrade?
7) Do I have the time to do this & fix the problems that may occur? 

Only **After** I answer these questions do I decide. 

Cheers...:)

---

### Post by benhur99ph on 2008-11-06
> **PurposeOfReason said:**
> I have an old Sony FS that is 100% working.

hey! What FS model do you have? I use VGN-FS940. Everything works fine except for the Fn keys. I tried most of the fixes floating around and unfortunately up to now, still haven't managed to get them working. I installed Intrepid last night and even the brightness applet doesn't seem to work. HELP... please... :(

---

### Post by joelito on 2008-11-06
Vaio VGN FZ-220e mostly works with Intrepid, My only complain is that I can't adjust the bightnes by any means. The function appear to work fine, except the brightness that show something in the screen that makes it look like it works but doesn't actually do anything.

---

### Post by lifestream on 2008-11-06
**FULLY FUNCTIONING**

```

System information report, generated by Sysinfo: 11/6/2008 10:10:25 PM
http://sourceforge.net/projects/gsysinfo

SYSTEM INFORMATION
	Running Ubuntu Linux, the **Ubuntu 8.10** (intrepid) release.
	GNOME: 2.24.1 (Ubuntu 2008-10-24)
	Kernel version: **2.6.27-7-generic** (#1 SMP Thu Oct 30 04:18:38 UTC 2008)
	GCC: 4.3.2 (i486-linux-gnu)
	Xorg: unknown (24 October 2008  08:00:16AM) (24 October 2008  08:00:16AM)

CPU INFORMATION
	GenuineIntel, **Intel(R) Core(TM)2 CPU**         T5500  @ 1.66GHz
	Number of CPUs: 2

MEMORY INFORMATION
	Total memory: **2022 MB**
	Total swap: 3074 MB ( I actually have swap disabled *shrug*)

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  ST980825AS       
	SCSI device -  scsi1
		Vendor:  HL-DT-ST 
		Model:  DVD+-RW GSA-T11N 
	SCSI device -  scsi2 - My USB Drive
		Vendor:  Maxtor   
		Model:  3200             

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		**Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)**
		Subsystem: Dell Device 01cc
	PCI bridge(s)
		Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)

GRAPHIC CARD
	VGA controller
		**nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)**
		Subsystem: Dell Device 01cc

SOUND CARD
	Multimedia controller
		Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
		Subsystem: Dell Device 01cc

NETWORK
	Network controller
		**Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)**
		Subsystem: Intel Corporation Device 1020
	Ethernet controller
		Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
		Subsystem: Dell Device 01cc

NVIDIA GRAPHIC CARD INFORMATION
	Model name: Quadro NVS 110M
	Card Type: PCI-E 16x
	Video RAM: 256 MB
	GPU Frequency: 100 MHz
	Driver version: NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008

```

I love my baby :)

---

### Post by archer6 on 2008-11-06
> **lifestream said:**
> I love my baby :)
I enjoyed how you posted the details, and oh by the way? I love mine too, Ubuntu is the best...;)

---

### Post by lifestream on 2008-11-07
> **archer6 said:**
> I enjoyed how you posted the details, and oh by the way? I love mine too, Ubuntu is the best...;)

I've been with Linux since the days where you had to make everything on your computer work by hand, you know, pre-Red Hat popularity days *cough*
I'd spend weeks and weeks learning, and getting it to work, but I'm still horrible at the command line. So I need sysinfo x-P

Wish I had tried Debian back then.

---

### Post by archer6 on 2008-11-07
> **lifestream said:**
> I've been with Linux since the days where you had to make everything on your computer work by hand, you know, pre-Red Hat popularity days *cough*
I'd spend weeks and weeks learning, and getting it to work, but I'm still horrible at the command line. So I need sysinfo x-P
I admire what must be your vast experience with Linux. I went to the site: [http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)
Yesterday, looked at the program you used and was quite interested in installing it on my ThinkPad, however there were three bugs listed and I was unsure as to what to do. I'm such a novice at this point that I am being quite conservative in adding anything to my laptop running 8.04 as presently it's trouble free. As such, it is providing me with a terrific learning opportunity as I read the vast resources on this forum as well as the Ubuntu Documentation. 

I would value your opinion as to any suggestions you might have for a new user (3 months) such as myself in terms of moving forward and directing my attention to the proper learning path. Especially given the fact that I'm a voracious reader that loves to learn. 

Thanks
archer6

---

### Post by Flames on 2008-11-07
I recently installed Ubuntu 8.04 studio on my Acer Aspire 3050,
and it partially works. At first, just to get it to boot, i had to 
disable acpi as a "boot argument" i believe.
but it installed normally after that.
Now, i'm having trouble with the wired network connection as well as the wireless.
 this is preventing it from updating, and probably not letting ubuntu download a proprietery driver for the ati onboard graphics.
in the restricted hardware manager,the video driver  seems to be enabled,
but beside it, there is a "restart symbol" instead of a checkmark.
(i have restarted several times, so i think it must need an internet connection.)

(the restricted drivers manager says it has drivers for some sort of network hardware )
I tried plugging in an ethernet cable coming from my router (which works fine for other computers), but it wouldn't connect to the internet.


restricted drivers:
atheros hardware access layer                           In use
support for atheros 802.11 Wireless lan cards           In use
ati fire gl                             enabled but not in use.


the machine's got: 1.8Ghz Amd Sempron.(3400Mhz equivalent)
                   768Mb DDR 2
                   Ati radeon express 1100 (indirect problem)
                   802.11 wireless (problem)
                   10/100 ethernet  (problem)
                   "onboard sound" (haven't tested) probably needs driver.
                   DVD writer(works fine)
                   usb2 (works fine)
                   60 Gb harddrive (works fine)

i'm going to try installing 8.10, but i get the feeling that that might not help. lol
so, if anyone knows how to fix this sort of thing in general, please let me know! :D

---

### Post by Flames on 2008-11-07
i tried installing 8.10, and it installed, but it wont start / get past the loading screen.
(i had to put acpi=off just to install it again)
when the computer gets past the loading screen, it flashes a bunch of stuff about "pci bios error!"
among other things and disappears quickly. Then i get a black screen.
occasionally, the video comes back on and i see several lines about various system things like "checking battery".
(this is the computer mentioned in my last post)
please help me if you can. :D

---

### Post by psycosmyth on 2008-11-07
I did'nt see this before, nice.
Dell Inspiron 1200 
1.2ghz Celeron
1.2gb ram
Intel chips.
Dlink pcmcia WNA 1330

Ubuntu 8-04 
everything including hot-keys works!!

Ubuntu 8-10 sucks!!! reverted to Hardy

---

### Post by Dragonbite on 2008-11-07
> **Flames said:**
> i tried installing 8.10, and it installed, but it wont start / get past the loading screen.
(i had to put acpi=off just to install it again)
when the computer gets past the loading screen, it flashes a bunch of stuff about "pci bios error!"
among other things and disappears quickly. Then i get a black screen.
occasionally, the video comes back on and i see several lines about various system things like "checking battery".
(this is the computer mentioned in my last post)
please help me if you can. :D

First thing I would do is run an md5sum check on the downloaded ISO and make sure it matches.

Second thing I would do is check the media at whatever option it is on the bootup screen.

Usually I find big issues like that to be a bad download/burn.

Even CDs received via Shipit can sometimes be faulty.

---

### Post by Flames on 2008-11-07
the md5sum is a "check disc for defects" right? cause,
i tried "check disc for defects" after booting from the cd, and it froze for a bit, then the screen went black and stayed that way.

i don't know if this makes it any less vague but when i boot up (normally),
(before the loading screen) it says: "PnpBios error"
and wants me to restart with pnpbios=off. (which i tired)
and it says a lot of other stuff but disapears too quickly to read it all.

i guess i could try reburning the disc.

---

### Post by dusted on 2008-11-07
Ubuntu does everthing I want it to on my Alienware laptop.  I have just created a thread with my specifics and the installation here at:
[http://ubuntuforums.org/showthread.php?p=6125581#post6125581]("http://ubuntuforums.org/showthread.php?p=6125581#post6125581")

---

### Post by teddks on 2008-11-07
I have an HP DV9500.

[list]
[*]Nvidia GeForce 7150 works fine.
[*]Atheros AR5007EG: fully functioning (with packet injection) under madwifi-ng.
[*]Webcam is fully functional.
[*]Microphones are fully functional (albeit with some static) with -backports drivers.
[*]AuthenTec fingerprint scanner works with pam_fprint
[*]Synaptic Touchpad is fully functional.
[/list]

However, my laptop runs GNU/Linux, not Linux. :P

---

### Post by C4SE on 2008-11-07
2.2 Intel Core 2 Duo Macbook (2.0/2x512/120/sd dl:black)

Sound works but is tinny, headphones don't work
iSight doesn't work
2-finger right click doesn't work

Everything else is awesome!

---

### Post by benhur99ph on 2008-11-08
Sony Vaio VGN-FS940
[Tech Specs]("http://www.dealtime.com/xPF-Sony-SONY-VAIO-FS940-PENTIUM-M-740-1-73GHZ-512MB-100GB-HDD-15-4-WXGA-X-BRITE-ECO-DVD-RW-DUAL")

Everything almost works out of the box. The only thing that needs configuring are the Fn keys. But it is easily remedied. Unfortunately this fix doesn't seem to work with Intrepid so I went back to Hardy and its working fine. Hehe. :D

---

### Post by richg on 2008-11-08
I picked this one up nearly four years a go. It runs linspire 5.1.427 very well. Nice DVD player application also.
    * AMD Mobile Sempron 2800 (black chassis)
    * 15" XGA 1024x768 Display
    * 1256MB DDR400 RAM DDR400 PC3200 DDR 200-pin SODIMM
    * VIA K8N800 Chipset and Onboard VGA (AGP 8X, 3D Capable)
    * CDRW/DVD Combo Drive
    * 40GB Hard Drive
    * 4 x USB 2.0
    * Integrated 10/100 Mbps Ethernet, 56k v.92 modem
    * Linspire O/S + DVD Player & 1yr CNR Gold Subscription
    * Mini-PCI Wireless 802.11G 
    * Weight 7 lbs
    * FREE! No-Nonsense Guide to Linspire
    * 1 year warranty

I also have a wireless Asus EEE 4G PC with a 4gb SD card running the default Xandros. Very nice system. 8gb storage is plenty for this little laptop.
Both will keep the OS as long as possible. It works, don't mess with it.

Rich

---

### Post by Dragonbite on 2008-11-09
> **Flames said:**
> the md5sum is a "check disc for defects" right? cause,
i tried "check disc for defects" after booting from the cd, and it froze for a bit, then the screen went black and stayed that way.

i don't know if this makes it any less vague but when i boot up (normally),
(before the loading screen) it says: "PnpBios error"
and wants me to restart with pnpbios=off. (which i tired)
and it says a lot of other stuff but disapears too quickly to read it all.

i guess i could try reburning the disc.
I am not sure if they are the same thing or not. I always thought the md5sum covered if you downloaded it correctly while the "check disk for defects" worked with the physical disk (scratches, bad sectors, etc.)

The only thing I can think of is to do a complete re-download and reburn. I went through 3 CDs before finding out I had a bad download in the first place.  Frustrating.:redface:

---

### Post by lakersforce on 2008-11-10
I have a Medion laptop (which is really a MSI). It works almost perfectly. Only thing that's not working is the card reader. The Wireless network driver I had to compile myself (but that was as easy as downloading, make & sudo make install)

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
01:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
01:04.2 FLASH memory: ENE Technology Inc Unknown device 0720
01:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
02:00.0 Network controller: RaLink Unknown device 0781
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

---

### Post by The2DQuartet on 2008-11-10
I've just inherited (don't worry nobody died, my wife just didn't like it) a 1-day-old Fujitsu-Siemens Amilo Pa 3553 and plan to dual-boot Ubuntu 64-bit with Vista (which I don't plan on using for anything more than a bit of casual gaming!). I've heard some mostly unsubstantiated horror stories about WLAN cards not switching on so I hope I can get it to work!

I've been running Ubuntu on a Packard Bell iMedia desktop for about 2 years now with no problems that can't be traced directly back to buying a cheap computer or replacing pieces of it myself.

Needless to say if all goes well and I have internet access I'll be back on here to spread the word.

---

### Post by tvtech on 2008-11-10
Asus-m70vm-C1  Linux somebodies-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

[LIST]
[*]nvdia geforce 9600m GS 512MB
[/LIST]
[LIST]
[*]Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
[/LIST]
[LIST]
[*]USB2.0 1.3M UVC WebCam
[/LIST]
[LIST]
[*]INTEL Corporation Wireless WiFi Link 5100
[/LIST]
[LIST]
[*]82801I (ICH9 Family) HD Audio Controller  Intel Corporation (ASUSTeK Computer Inc.)
[/LIST]
[LIST]
[*]2gbX2 ram
[/LIST]


The following problems I've had
1. On initial boot horrible beep, disabling usplash fished it.
2. Infrequent boot to nothing problems, it appears that it's not mounting the hard drive properly, I haven't sorted this problem out correctly yet because the log isn't working properly, or it's failing before it can write to the log. 
3. the multimedia touchpad and remote control do not work, only as a standard track pad nothing more. 
4. the finger print reader is disabled. 
5. frequent log errors regarding the usb enumeration.
6. sometimes I have problems initiating X
7. wireless doesn't load properly all the time, for some reason network manager can't take control haven't gotten it sorted out but I've found the log errors that explain it.  
8. LCD backlight doesn't reinitialize after suspend, monitor does it's just so damn dark you can't use it! one of these days I'll blind my way to a dmesg when it happens and fix it. 

The other laptop I have is a Dell Latitude D800 it's about 8 years old

Intel Pentium M processor 1700MHz 1.2gig RAM
Nvidia NV28 [GeForce4 Ti 4200 Go AGP 8x]
Intel PRO/Wireless 2915ABG 

EVERYthing works on it except suspend hibernate and the advanced desktop effects but that is to be expected it's got a pretty light video card. it's currently running 8.04

  that's about it, other than that it works great no issues.

---

### Post by jflaker on 2008-11-10
I tried the LiveCD on a Dell Inspiron D620 and it worked.  I didn't want to dual boot as there are certain things I agreed to and that wasn't one of them.........though I was tempted.

---

### Post by archer6 on 2008-11-10
> **jflaker said:**
> I tried the LiveCD on a Dell Inspiron D620 and it worked.  I didn't want to dual boot as there are certain things I agreed to and that wasn't one of them.........though I was tempted.
I'm trying to understand this entry, perhaps I'm missing something? "you didn't want to dual boot as there are certain things you agreed to? 
I'm very curious to learn what I've missed.

Thanks

---

### Post by night_fox on 2008-11-10
AAAAAAAARRRRRRRRGGGGGGGGGHHHHHHHHHH!!!!!!!!!!!!!!!!!!!!! I want to change my answer! Having installed Ubuntu 8.10 Intrepid Ibex I now have a fully functioning linux laptop!
:guitar:

---

### Post by dizzy1kenobi on 2008-11-10
My HP Pavilion 6000 has an AMD Turion 64.  Everything works great so far, even the remote control.  It was a little tricky the first couple of days though.

---

### Post by blackened on 2008-11-10
Sony VGN-NR385E Intel T5550, Intel iwl3945 wireless, Intel GM965 graphics, Realtek ALC262 audio.

To make the backlight function keys work properly I had to add this to startup: ```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

Followed [this]("http://ubuntuforums.org/showthread.php?t=806620&highlight=sound+headphones") guide to make my headphones function properly.

I don't know if my cardreader functions or not as I haven't tested it.

Also some issues with my external display, but that's caused by Ubuntu not properly recognizing the monitor itself. Easily fixed with xrandr.

---

### Post by Dragonbite on 2008-11-11
> **jflaker said:**
> I tried the LiveCD on a Dell Inspiron D620 and it worked.  I didn't want to dual boot as there are certain things I agreed to and that wasn't one of them.........though I was tempted.

My Dell Inspiron D400 was fully functional once I got the Broadcomm wireless drivers installed (fwcutter).

Unfortunately my wireless hardware seems to have broken, so I am going to get another wireless mini-PC card when I get the money (perhaps in a few months).  

I'm looking at an Intel b/g/n like the one in my work Lenovo because the LiveCD detected it without having to do anything.

---

### Post by gjoellee on 2008-11-11
I have an old HP Pavilion ze 5500

---

### Post by Ubukicc on 2008-11-11
Hi, mine is an asus X51R, i'm attaching lspci, uname, and dmesg (of last boot only) outputs. Hope it helps. i voted "everything ok" but there's a wireless light issue... i had to put a line on rc.local to switch it on using /proc/[..] everything else and is working

---

### Post by mordak13 on 2008-11-11
Toshiba Tecra M2-S530 the only thing that seems to not work at all is the SD Card slot which is a known issue.

---

### Post by calibre97 on 2008-11-11
HP Pavilion dv5035nr
2.2GHz AMD something
1.5GB RAM
Radeaon XPress R200
Broadcom 4318

Under Mandriva and Kubuntu 8.04, everything works. Took awhile to get the Broadcom working under Mandriva, and for a little while it stopped working under Heron, but both are fine now. However, I could NOT get the Broadcom working under Ibex (Different partition for triple boot), and VMWare Server 2.0 appears to be incompatible, according to the VMWare communities, with the 2.6.27 kernel so no joy there. That's why I upgraded the drive to a 160GB so I could have plenty of partitions to try out distros and major upgrades. To get to my XP VM, I just boot into Heron. Pretty much everything else works in Ibex so I mainly live in there with occasional forays into Mandriva.

Almost forgot, to get wireless under Ibex, I use a D-Link DWA 652 PC Card and it worked on plugin.

---

### Post by jimbo99 on 2008-11-11
Wireless and sound are the big issues with Linux on a laptop!  Modems are a close 3rd.

I think many ppl are having issues because, against the tradition of Linux, companies such as Canonical have abandoned some of the older hardware.  For instance, the DV3000 series, 5000 series, etc from HP have all but been abandoned.  Canonical could do a tremendous more to accommodate these systems but they don't.  It's pretty sad, frankly.

The ndiswrapper doesn't seem to function nor does the fwcutter based firmware.

Again, Canonical could do tremendously more to resolve this once and for all but they do not.

---

### Post by mdsmedia on 2008-11-11
Mine is a HP Compaq nx6120. I'll post the specs if someone can show me the command to do so :).

I've used Ubuntu since Hoary and it all works fine for me. Suspend works (most of the time) although I do get strange messages and occasionally I'll get an error and it won't suspend first time...very occasionally.

The only fiddling I had to do was switching off the tap feature on the touchpad.

It is largely Intel hardware, including Centrino chip, so that would explain the lack of problems.

---

### Post by teddks on 2008-11-11
> **jimbo99 said:**
> Wireless and sound are the big issues with Linux on a laptop!  Modems are a close 3rd.

I think many ppl are having issues because, against the tradition of Linux, companies such as Canonical have abandoned some of the older hardware.  For instance, the DV3000 series, 5000 series, etc from HP have all but been abandoned.  Canonical could do a tremendous more to accommodate these systems but they don't.  It's pretty sad, frankly.

The ndiswrapper doesn't seem to function nor does the fwcutter based firmware.

Again, Canonical could do tremendously more to resolve this once and for all but they do not.

Canonical doesn't do much to 'abandon' anything. I used to use a DV2000, and it worked _great_. What's changed now is that the same hardware is supported under newer and better drivers, written by folks upstream in the Linux project (not canonical people).

Ndiswrapper worked for me whenever I used it, as did the bcm43xx/b43 drivers. I don't know the status of the newer drivers, as I use Atheros cards now, but I have several friends that use broadcom cards (and old HP hardware) and they work fine as far as that goes.

Maybe you could make a thread somewhere else and ask for specific help? Though typically, Jockey (System>Administration>Hardware Drivers) is all you need...

---

### Post by GeneW on 2008-11-11
> **BrianElliott0218 said:**
> 
:confused: And the last issue that I have noticed, so far, is that when the system is on the Ubuntu boot screen with the bar going back and forth, it will freeze unless I hit keys on the keyboard.  It will move a bit each time a key is pressed (usually I press "Y").  I thought I was missing messages asking for an answer, and that's when I started hitting keys. When we get to the one way progress bar (instead of the back and forth), and then boots 'normally'.


I'm seeing the same thing on my HP Pavilion dv6000.  Is there a fix for that?

---

### Post by billgoldberg on 2008-11-11
The Asus Eeepc 900 is 100% compatible.

The webcam, micro, the special keys, ... everything works OOTB.

*The distro I'm using is eeebuntu.*

---

### Post by james.wilde on 2008-11-12
Acer Extensa 5620, Intel Core 2 Duo T5550 (1.83 GHz, 667MHz FSB, 2 MB L2 cache), 15.4 WXGA Crystalbrite LCD, 2 GB SO-DDR2 memory, up to 358 MB Mobile Intel Graphics Media Accelerator, 320 GB HDD.

So incredibly sensitive keyboard and mouse plate that typing and other operations can be difficult.  Cursor has a tendency to jump randomly within text whilst I am typing.  No idea what is causing that.

Sound card (HDA Intel, 82801 AC97 depending on where you look) is not playing loud enough, neither via the loudspeakers nor the headset, and I'm trying to find out why.  The installed Vista sounds ok.

//James

---

### Post by teddks on 2008-11-12
> **james.wilde said:**
> 
So incredibly sensitive keyboard and mouse plate that typing and other operations can be difficult.  Cursor has a tendency to jump randomly within text whilst I am typing.  No idea what is causing that.

//James

Are you sure you're not accidentally hitting the touchpad? This happens to me a lot, and I ended up using syndaemon to fix it (man syndaemon for more info, it seems to be installed with the X driver for a synaptic touchpad).

---

### Post by MikeBrown on 2008-11-12
I have an HP Pavilion dv9000 Laptop with an AMD Turion 64 x2 TL-64 2.20 GHz Processor, 2 Gigs RAM, Nvidia GeForce Go 6150 Graphics card, Dual Booting Windows Vista and Ubuntu 8.10

I can give a more detailed setup description if needed.

No problems with hardware that I've noticed thus far.

---

### Post by Old_Grey_Wolf on 2008-11-12
> 
Originally Posted by james.wilde View Post
So incredibly sensitive keyboard and mouse plate that typing and other operations can be difficult. Cursor has a tendency to jump randomly within text whilst I am typing. No idea what is causing that.

> **teddks said:**
> Are you sure you're not accidentally hitting the touchpad? This happens to me a lot, and I ended up using syndaemon to fix it (man syndaemon for more info, it seems to be installed with the X driver for a synaptic touchpad).

Try going to the System >> Preferences >> Mouse menu. Go to the Touchpad Tab. Then remove the check next to Enable mouse clicks with touchpad.

---

### Post by patrickballeux on 2008-11-12
Dell Inspiron 1521, AMD Turion 64 x2, 2 Gigs of RAM, fully working.

Graphic: ATI x1200
Synaptic Touchpad
Resolution 1600x1050
Internal webcam working
Internal Bluetooth working


Not tested: Firewire device (but it is detected...)

---

### Post by teddks on 2008-11-12
> **Old_Gray_Wolf said:**
> Try going to the System >> Preferences >> Mouse menu. Go to the Touchpad Tab. Then remove the check next to Enable mouse clicks with touchpad.

I like the click via taps, though. Just not when I'm typing.

---

### Post by athaki on 2008-11-12
when I had a laptop opensuse 10.3 had everything working out of the box: power management, suspend, resume, media keys, &tc.  System specs were
Intel Pentium M 1.5 Ghz
2GB RAM
ATI Radeon X300 128mb
Dell Inspiron 6000

---

### Post by Koori23 on 2008-11-12
Toshiba SatellitePro A105

I get an error message when the system comes out of standby for a split second.. Then everything is fine.. 

I'm going to go with "My laptop works completely with Linux". The error message doesn't affect anything.

I have 512MB of Ram, an Intel Centrino processor.. I have no idea what kind of video card I have.. My laptop is pretty darn basic.

---

### Post by notsatch on 2008-11-13
HP Pavilion DV9220US
1.60 GHz C2D processor T5200
2GB DDR2 RAM
NVIDIA GeForce Go 7600 w/256MB
160GB SATA hard disk
8X DVD±R/RW
17.0" WXGA+ display (1440 x 900)
Integrated 10/100/1000 Gigabit Ethernet LAN (RJ-45 connector)
Intel® PRO/Wireless 3945ABG Network Connection

full specs here: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00847955&lc=en&dlc=en&cc=us&lang=en&product=3340202](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00847955&lc=en&dlc=en&cc=us&lang=en&product=3340202)

Just installed 8.10 x64, dual booting with XP Pro and everything works beautifully. Only thing I haven't tested yet is the media reader.  Yes, even the sound, webcam and wireless networking work ootb.  Fantastic release.

---

### Post by joe.turion64x2 on 2008-11-13
Linux works almost perfectly on my laptop (in both x86 or x86_64), the only 'problem' being the webcam not supported. I don't use it anyway so I don't care about it.

Specs.

Acer Aspire 5102WLMi.
AMD Turion 64 X2 TL50, 2.5GB DDR2 RAM, Atheros wireless card (a/b/g), ATI Radeon Xpress 1100 (256MB), 120GB SATA, DVD-RW, Many in one card reader. Running Linux Mint 5.

EDIT: Forgot to mention my smaller laptop. Linux works flawlessly on it (everything works):
Acer Aspire One.
Intel Atom N270, 512MB DDR2 RAM, Atheros wireless card, Intel GMA 950, 8GB SSD + 4GB SDHC. Running Linpus Linux Lite.

Thanks.
Joe.

---

### Post by faraz_k86 on 2008-11-13
I have a Fujitsu-Siemens V5535. Everything works except for the display driver. We dont have the 3D driver for my display chip, only the 2D driver :(

---

### Post by jflaker on 2008-11-15
> **archer6 said:**
> I'm trying to understand this entry, perhaps I'm missing something? "you didn't want to dual boot as there are certain things you agreed to? 
I'm very curious to learn what I've missed.

Thanks

Oops...Is a company laptop...part of the computer usage policies.....I can't make such changes.

---

### Post by Bartender on 2008-11-15
Acer 5920-6470.  Ubuntu 8.04.
The 5920 is a Centrino.
The card reader doesn't work.  The reader has been reported in Launchpad bugreports.  Don't know if the webcam works, never tried.  The strange little blue-lit DVD start/stop/pause controls (in Vista they work with the slightest brush across the buttons) along the right edge of the laptop don't work like they're supposed to.  Plugging in a set of headphones does not kill the chassis speakers regardless of "switch" setting in Volume Controls.  I get around this by opening volume control and clicking on the little speaker icon under "Surround" sliders.  The volume knob on front of the laptop does work.

Sound works, even the subwoofer.  Wireless works outofthebox.  Screen resolution was configured correctly with no tweaking thank goodness.  Most of the sleep/hibernate functions seem to work, as do most of the F keys.    

I've been very happy with this lappy :guitar:

---

### Post by luks911 on 2008-11-15
All works fine with my Compaq Presario F754la.

AMD Sempron Mobile 3600+
Nvidia 7000M
Wifi Atheros AR5007EG
Webcam

:lolflag:

---

### Post by dantakeoff on 2008-11-20
Acer Aspire 5315, EVErYTHING worked with 8.04, i should have left it like that. the upgrade has downgraded it to "everything apart from the internal mic works....":lolflag::lolflag:

---

### Post by x0as on 2008-11-20
Macbook 3.1
T7200 core2duo 2.0 Ghz
intel x3100 graphics
broadcom 4328 wireless

Everything appears to work with 8.10.

---

### Post by blakjesus on 2008-11-20
My Laptop:

Intel Core 2 Duo T9400 (2.53 GHz)
4GB (2x2GB) DDR2 RAM
Geforce 9600M GT (512MB RAM)
250GB 5400rpm HDD
Intel 5100AGN Wifi with Bluetooth
Lightscribe SuperMulti DVD+/-R/RW Double Layer
Built-in TV Tuner
Fingerprint Scanner

Im running 8.10 (64-bit) and it works perfectly. :) But i can't find a way to get me fingerprint scanner or my tv tuner to work. :(

---

### Post by BunnyGirlDoom on 2008-11-20
I chose the first option, that it's running fine, despite having some nvidia issues and desktop effects problems, everything seems to be running just peachy. I think I have the graphic stuff sorted out - for the longest time when I would install the latest Geforce2 GO driver, it would load up half screen - everything would be squished over to the left side. Yesterday I used EnvyNG to install the driver, and it seems to be fine now - though I think I'm going to just resign myself to the probability that the driver and my card aren't really optimal for a desktop effects and such. 

I'd say my only real present concern is how Ubuntu is managing memory and such. It seems I should be able to run Rhythmbox and Movie at the same time without one or both of them stuttering...

```
linux-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 511MiB
     *-cpu
          product: Mobile Intel(R) Celeron(R) CPU 1.50GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 15.2.7
          size: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 Go]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 78
                serial: 00:08:74:e1:6b:83
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x latency=80 maxlatency=10 mingnt=10 module=3c59x multicast=yes
           *-pcmcia
                description: CardBus bridge
                product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-network
          description: Wireless interface
          product: BCM4306 802.11b/g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 0
          bus info: pci@0000:03:00.0
          logical name: wlan0
          version: 03
          serial: 00:12:17:3a:a2:bb
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.53+The Linksys Group, Inc.,02/ ip=192.168.1.107 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:e7:a7:7b:8f:1d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by archer6 on 2008-11-20
> **dantakeoff said:**
> Acer Aspire 5315, EVErYTHING worked with 8.04, i should have left it like that. the upgrade has downgraded it to "everything apart from the internal mic works....":lolflag::lolflag:

Wow... do I belong to This Club or what? How many times have I just upgraded without giving it much thought other than the desire to "have the lastest current OS / Software, or whatever...

Slowly, I'm getting it, slowly I'm remembering to remind myself that I do not HAVE to upgrade, after all it's running perfectly... leave it alone archer.....:lolflag:

* he says while happily typing away on his (untouched after the install) Ubuntu Hardy Heron ThinkPad T60...:)

---

### Post by gerowen on 2008-11-20
Using 8.10

Compaq Presario C751NR.  Not a beast of a machine, and I did have to manually compile madwifi for the wireless to work because for some reason the default one wouldn't detect it.

2.5 GB RAM (Originally shipped with 1GB)
1.6 Ghz Intel Pentium Dual Core Processor
Integrated Intel Graphics Card (Up to 384 MB shared memory)
120 GB SATA HDD
Atheros AR5700X Wireless Card

Everything except wireless worked right out of the box, which is a long way because 8.04 wouldn't even boot on this machine.

---

### Post by _Azrael_ on 2008-11-20
Perfect on my Dell Vostro 1400
```
WARNING: you should run this program as super-user. [indeed]
incinerator               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2038MB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2001MHz
          capacity: 2001MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4310 USB Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 01
                serial: 00:16:44:83:fa:e5
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,09/20/2007, 4.170. ip=192.168.1.64 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:fe:78:39
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

---

### Post by HappyHenry on 2008-11-20
Everything works fully!
I have a compaq 6710b. The only hardware upgrade I've done is with the R.A.M. I added some because origanlly this was a Windows Vista machine. I dont understand why Compaq sold it with only 2gigs of R.A.M. Vista ate most of it just in running and the video card is onboard shared memory so you can understand why I reformated and loaded an efficent OS like Ubuntu.
Everything workes great. I did have issue with the video card at first because the Compaq folks helped MS by disabling the shared memory in the bios. MS was allowed access to allocate memory for the video card but not linux. Well some wonderful linux developer figured things out and now it works great.
Anyone with a notebook that doesnt work, keep searching for the solution. Given some patients and time I have been able to get all but one notebook working and that was only because I couldnt figure out how to apply the work-around. It was my own fault, I gave up.
I hear Acer laptops work great for Linux...? Just something I heard. It would be great if someone read through this thread in a couple months to see the most dependable systems and posted the results????

---

### Post by scliburn on 2008-11-20
Quantity	Item Number	Description	Unit Price
1	222-8603	Inspiron 1720, Intel Core 2 Duo T7500, 2.2GHz, 800Mhz, 4M L2 Cache	$1753.96
1	313-5473	Jet Black Color with Matte Finish	$0.00
1	311-7636	3GB, DDR2, 667MHz 2 Dimm	$0.00
1	320-5500	Anti-glare, widescreen 17.0 inch display (1440 x 900)	$0.00
1	320-5468	256MB NVIDIA GeForce Go 8600	$0.00
1	341-4709	160G 5400RPM SATA hard drive 5400 RPM	$0.00
1	420-6556	Microsoft Windows Vista Home Premium Edition, English	$0.00
1	313-5195	DELL RESOURCE DVD,BACK-UP,INSP1720	$0.00
1	420-5769	Internet Search and Portal	$0.00
1	420-5924	Icon Consolidation Application	$0.00
1	420-6436	Vista, PC-Restore, Dim/Insp	$0.00
1	420-6995	DELL SUPPORT 3.4,DIM/INSP	$0.00
1	463-2282	Dell Owners Manual installed on your system,click on icon after system set-up to access	$0.00
1	420-7026	Media Direct 3.5	$0.00
1	420-7244	Dell Support Center 1.0	$0.00
1	430-0493	Integrated 10/100 Network Cardand Modem, for Inspiron	$0.00
1	341-4715	24X COMBO CD-RW/DVD	$0.00
1	420-6464	Roxio Creator Basic	$0.00
1	313-4783	Integrated High Definition Audio 2.0	$0.00
1	430-2334	Intel 3945 WLAN (802.11a/g) Mini Card	$0.00
1	320-5683	NO WEBCAM OPTION	$0.00
1	420-6591	Network Associates McAfee 8.0 English, 15-Month Subscription	$0.00
1	312-0525	56 WHr 6-cell Lithium Ion Prim	$0.00
1	312-0528	85 WHr 9-cell Lithium Ion Additional Battery, for Inspiron 1520	$0.00
1	412-0148	No Internet Service Provider Requested	$0.00
1	412-1397	No Productivity Software requested	$0.00
1	950-3337	1 Year Limited Warranty	$0.00
1	412-0360	Soft Contracts - Banctec	$0.00
1	960-2780	Warranty Support,Initial Year	$0.00
1	987-8109	No Warranty, Year 2 and 3	$0.00
1	987-5447	Dell Hardware Warranty PlusOnsite Service, Initial Year	$0.00
1	983-3100	Type 3- Third Party At HomeService, 24x7 TechnicalSupport, Initial Year	$0.00
1	960-9187	CompleteCare Accidental DamageProtection, Inspiron, 1 Year	$0.00
1	412-0358	Soft Contracts - Consumer Complete Care	$0.00
1	986-3577	Bundle LoJack Theft Recovery Service - 1 Year	$20
1	466-7741	Thank you for choosing Dell	$0.00
1	310-5408	Free Recycling Kit	$0.00
1	466-1830	Thanks for supporting reforestation to offset carbondioxide emissions generated topower your system!	$1.70
1	466-3921	No Preinstalled Software	$0.00
1	320-5799	Basic Black Matte LCD back color w/o Camera Insp 1720	$0.00
1	310-9348	Intel Centrino Core Duo Processor	$0.00
1	310-8628	You have chosen a Windows Vista Premium System	$0.00
1	420-7091	DataSafe Online Dim/Ins/XPS	$0.00
1	420-7092	DataSafe Online Dim/Ins/XPS 1YR-FREE	$0.00
1	987-4817	Insp Datasafe 3GB,1YR(Incl in price),DHS	$0.00
1	988-0099	To activate your online backupaccount, go to Start, Programs, DataSafe Online	$0.00
1	600-0002	State Environmental Fee for display 15 inches, less than 35 inches	$8


Now, after all that, 1 year later (after warranty), swap out anything/everything windows, replace with open source/ubuntu. :guitar:

---

### Post by phen on 2008-11-21
ibm thinkpad x31, problems existed with the ati radeon, but now it works out of the box!

i think radeon drivers get better and better all the time..

---

### Post by archer6 on 2008-11-21
> **phen said:**
> ibm thinkpad x31, problems existed with the ati radeon, but now it works out of the box!

i think radeon drivers get better and better all the time..
As ThinkPad goes, so goes Radeon drivers.... they simply get better and better. If one wants a solid, reliable, high quality, reasonably priced laptop... it's a ThinkPad hands down, every time, period...:)

---

### Post by rich1939 on 2008-11-21
Fully functioning laptop, Toshiba Satellite Pro 4600, 512MB RAM, 20GB Hard Drive.

---

### Post by Hyper Tails on 2008-11-21
Everything works fine on my laptop

intel duo core
2gb ram
160gb hardrive
ubuntu 8.10 intrepid
acer apsire 5715z

---

### Post by Twilight in Zero on 2008-11-21
My laptop is a Gateway MT6452. I originally voted "works completely", but I need to retract that.

Ubuntu Intrepid 32-bit.
AMD Turion 64x2.
1 GB RAM.
SD Card Reader: Works perfectly.
Synaptics Touchpad: Had to change right edge, but works perfectly.
ATI Radeon Xpress 1150: fglrx works on it as of Intrepid, but I still get this nagging feeling that games are slower than they were in Windows.
S-Video Out: Last time I tried it, in Hardy, with open source ati, I couldn't get it to work. I might have better luck with fglrx, next time I try it.
Realtek RTL8187 integrated: Ditched Ubuntu's shoddy RTL8187 drivers and used Ndiswrapper + Win98 drivers.
Ethernet: Works perfectly.
Sigmatel STAC9250: This has a problem I still have yet to resolve. When the master volume is below 50%, the sound is muted. Above 50%, it works. And 100% sounds like full volume. So it's like my sound range was scrunched from 0%-100% to 50%-100%.

---

### Post by Afkpuz on 2008-11-21
Gateway m680 laptop works perfectly with two exceptions: Suspend and hibernate.  Everything else is nice and fast.  Luckily, I don't use suspend or hibernate.

---

### Post by drascus on 2008-11-21
Linux works fully with my laptop. I have a Zareason Megalap:

# Intel Core 2 Duo processor T5500
# 17" LCD display @ 1680x1050 pixels
# Nvidia GeForce GO 7700 dedicated video card with 512 MB RAM
# 4 Speakers and an integrated subwoofer for amazing sound output
# Easy WiFi connectivity with an Intel 3945 ABG card
# Custom fit carrying case (black) included
# Headphone jack + extra microphone jack has easy access below the touchpad
# 4 USB ports total -- 2 USB ports on each side
# Firewire port for high speed data transfer
# Combo CD-RW and DVD-RW drive
# 15-pin VGA and HDMI video ports
# Gigabit Ethernet port for whenever you aren't near a WiFi access point -- this machine travels extremely well
# MMC/SD slot -- download photos, anything from your phone (if it holds an SD card), your printer... extreme usability
# ExpressCard 34/54 (a newer version of PCMCIA) slot for extra expansion
# E-SATA port for an extra hard drive and more
# Bluetooth included

information came from the Zareason Website...

---

### Post by campegg on 2008-11-21
I'm pretty sure I have everything running OK -- at least I haven't run into any problems yet -- on my Dell Mini 9 under Intrepid. I had to do some minor messing about to get sound going, but the webcam, etc all worked right from that start.

---

### Post by joffeloff on 2008-11-22
Everything works (that I have tried - I'm not going to do a digital walkthrough of everything I don't use, I'm not a reviewer) on my ASUS M6800VA;

Pentium M 2GHz Dothan
1GB RAM
ATI Mobility Radeon X700
Intel Pro Wireless 2200
Other bits and bobs

Sound, WLAN, power management, ethernet, all that worked out of the box. Had to download ATI blob drivers from the repository to get Compiz to run, I guess the OSS drivers don't support 3D acceleration.

---

### Post by Arabiest on 2008-11-22
Fujitsu Siemens T4210

---

### Post by Idefix82 on 2008-11-22
Ubuntu 8.04 64bit works perfectly, after some fiddeling:

Dell Vostro 1710
[LIST]
[*]Audio works out of the box 
[*]Graphic card: nVidia GeForce 8600M GS works out of the box with the proprietary driver
[*]SD card slot works out of the box
[*]hibernate, suspend works out of the box
[*]WiFi: Broadcom card BCM4328 works with ndiswrapper without any hassle at all (two lines in the terminal)
[*]Ethernet card Realtek RTL8111/8168B only worked once I removed the default driver and installed the r8168, which Realtek provide on their website. The original one had a bug so it took me some time, but the current one should install very easily.
[/LIST]

---

### Post by crazyfuturamanoob on 2008-11-22
Everything works perfectly on my Acer 7520g laptop, here are the specs:
[list]
[*]4Gb RAM, I'm not sure can my 32-bit Ubuntu Hardy use all of it.
[*]AMD Turion x2 Mobile Technology dual core processor, 2.0GHz
[*]NVIDIA GeForce 8600GS 512Mb TurboCache, can use RAM up to 1791Mb.
[/list]
Monitor of this laptop also supports HDTV output, but haven't tested.

---

### Post by agurk on 2008-11-22
Everything works, IBM/Lenovo T60 (Intel graphics, not ATI).

---

### Post by gluefish on 2008-12-05
Ubuntu / Intrepid Ibex
Acer Aspire One 160gB HDD, 1gB Ram, 1.6gHz
Wifi didn't work at first, one download fixed it
Camera doesn't work
Microphone doesn't work
All else pretty much ok

---

### Post by magmon on 2008-12-05
Specs in my siggy, ubuntu just works for me. I do have some very minor issues with full screen 3d, but those existed in windows too, and I think its because of this infernal ATI.

---

### Post by enlightend1 on 2008-12-05
Gutsy worked for me on the second install. I screwed up the first time by not reading all of the instructions -doh! Been using it for a year now no problems to speak of:p. See my sig for some sys specs.

---

### Post by archer6 on 2008-12-05
> **enlightend1 said:**
> Gutsy worked for me on the second install. I screwed up the first time by not reading all of the instructions -doh!
Wow... so I'm not the only one huh?.....Just kidding. It's great to know that I'm in good company and you got yours up and running too!

I'm so impressed with Ubuntu, it just works so well, is very customizable (not that other distros aren't) and it's a pleasure to use. 

Cheers...:D

---

### Post by OttifantSir on 2008-12-05
I've got a Dell Inspiron 9400 / E1705 that's been used with Ubuntu from 6.10 (Edgy Eft) onwards. Now it has 8.10 Intrepid Ibex on it, and everything "just worked" (had to use jockey to install b43-fwcutter to get the Broadcom wireless working, but no hassle).

More detailed list: 1GB RAM, Intel 945GMA 128MB shared, Intel T2060 (Dual-Core 1.6GHz), 120GB 5.400 HDD (SATA), Ricoh Card Reader. Bought a Hama Mini-Bluetooth dongle, and it just worked (for sending. Needed obex-data-server to receive)

---

### Post by detroit/zero on 2008-12-05
Toshiba Satellite a135 - everything works fine out of the box - sound, network, wireless.. everything but the "plug-your-headphones-in-and-have-the-laptop-speakers-shut-off" thing, but that's easy enough to fix.

---

### Post by lightrush on 2008-12-05
DELL Vostro 1400

Chipset: PM965
VGA: NVIDIA GF8400 GS
Wireless: Intel 3945
BIOS: A09

Other specifics are unimportant.

PROBLEM:
Keyboard and Touchpad randomly seize to work on resume after suspend due to problem with i8042 driver. I do not know if this is bug related or just lack of certain implementation. At current the only solution is to use scrip to rebind the keyboard and touchpad on resume which works most of the time but still seldom it fails too. This is rather annoying but it is not too much of a problem if you have set the Power button to suspend. Then if the kb/tp seize to work - just suspend and resume again and it will mostly work. If it does not - suspend/resume until it does. :D

---

### Post by oscarossa on 2008-12-05
Works perfectly except internal Intel Modem (no idea about how to config it)


Toshiba A10-S129, Celeron M 2,4 Ghz, 1 GB Ram


Video card Intel 855GM, DVD, 2 USB ports, 10/100 MB Ethernet port, + D-Link Wireless Card PCMIA.

Ubuntu version:  8.04 LTS

---

### Post by sunoccard on 2008-12-05
Dell D800
17.7 GHz CPU
1GB RAM
20 GB HDD




only problem is the wireless card, it's DOA

---

### Post by iitywygms on 2008-12-05
Presario 2100
**Never** got suspend to work, or hibernate.  Other than that all good.

---

### Post by Brian W. on 2008-12-05
Ubuntu 8.10
Acer Extensa 5620 160GiB hdd, 3GiB Ram, 1.83gHz
Everything has been fine so far except for s-video

---

### Post by bcn17 on 2008-12-06
core2duo 2.00GHz/800MHz (T7300) 
Geforce 8600M GT 
chipset/audio/usb etc is all 82801H (ICH8 family) 
and PRO/Wireless 4965 AGN 

*I said works 100% but... sometimes audio does not work when I bring it back out of sleep, in fact funny stuff can happen. But I can run a script and bring it back! I should encorporate it in to some sort of wake-up script.

sudo /etc/init.d/alsa-utils restart

---

### Post by iimre on 2008-12-06
My Lenovo ThinkPad R61 is fully funktioning. Though the fingerprint reader (UPEK 147e:2016) is still experimental and a bit unreliable, but works. 
I think that was the last device managed to get working. All others worked fine "out of the box".
(Intrepid 64 bit)

---

### Post by lyceum on 2008-12-06
I should say UBUNTU works fully with my laptop. I am using a non-free nVidia driver. 

I have a HP Pavilion dv9000. 

Processor: Intel Core 2 Duo (1.5 GHz); 
RAM installed: 3 GB DDR2 SDRAM
One 160GB 7200rpm SATA Hard Drive dual booted w/ Ubuntu 8.04 & Kubuntu 8.10
One 350GB 7200rpm Western Digital Hard Drive w/ Vista (I upgraded it myself)
Blueray DVD+/-RW Dual Layer Burner with LightScribe
17" WXGA+ (1440x900) Display 
nVidia Graphics with 512MB
HDMI Connector and 1.3MP Webcam
v.92 56Kbps Modem, Gigabit Ethernet and 802.11a/b/g Wireless
Four USB 2.0, One FireWire, ExpressCard/54 and 5-in-1 Media Reader
15.2" x 11.7" x 1.6" @ 7.8 lbs.

I plan to buy a 500GB hard drive to replace the 160GB, then load Kubuntu and use VM ware for Vista, leaving me 350 BG for storage & I want to see if I can up the processor to at least 2.5GHz.

---

### Post by Pazin~ on 2008-12-06
Dell Inspiron 1525 working fine here.

Core 2 Duo T5800
3GB Ram
120 GB SATA
Wifi card from Intel
I didn't test S-Video.

---

### Post by josedb on 2008-12-11
Making the wireless card work was a pain in the as* but i made it.

HP dv6736 totally working, except for the microphones beside the webcam

---

### Post by kaldor on 2008-12-11
Ubuntu works 100% flawlessly on my HP Pavillion dv2000 series laptop. I did not need to tweak one thing. As soon as I installed Ubuntu, _everything_ worked out of the box.

On the other hand, other distros tend to cause problems. 
-My touchpad works horribly on openSUSE for example.
-PClinuxOS will not detect my wireless card.
-Mandriva will not boot up
-SimplyMepis does not recognize my monitor
-Opensolaris (not linux) does not recognize my sound card.
-Vector does not recognize my wireless card.


I think this may be due to HP selling Ubuntu on their laptops. I bought mine with Vista because I thought I may need it for things, but it annoyed me too much and I wiped it clean. HP has pretty good Ubuntu compatibility from what I hear.

I will post my specs later.

---

### Post by eldragon on 2008-12-11
> **bcn17 said:**
> core2duo 2.00GHz/800MHz (T7300) 
Geforce 8600M GT 
chipset/audio/usb etc is all 82801H (ICH8 family) 
and PRO/Wireless 4965 AGN 

*I said works 100% but... sometimes audio does not work when I bring it back out of sleep, in fact funny stuff can happen. But I can run a script and bring it back! I should encorporate it in to some sort of wake-up script.

sudo /etc/init.d/alsa-utils restart

to get you automated, create the file
/etc/pm/sleep.d/01alsautils
and paste in it
```

#!/bin/sh

case "$1" in
        hibernate|suspend)
                ;;
        thaw|resume)
                /etc/init.d/alsa-utils restart
                ;;
        *)
                ;;
esac

```

make it executable

that should do it :D

ive learned quite a bit trying to get my laptop to suspend....havent been able to do it yet :(

---

### Post by mattppcintel on 2008-12-12
I actually have Ubuntu installed on 3 laptops at this time but none of them are really "fully" functioning yet.

HP Pavilion ze5700 - (Intrepid Ibex) Works with some problems (mostly due to it being my 8 year old sons computer and he manages to break things pretty easily).  It worked perfectly right after install, was a little slow for some reason but I think it's because the hardware sucks and it has heat problems.  Right now it always boots into failsafe mode and I can't figure out why.

Toshiba Sattelite 5105 S501 - (Intrepid Ibex) Works pretty well.  Only problem is I can't get the nVidia GEForce drivers to work so I have no 3D but I don't really care.  I am writing this post on it so it works pretty good now and had little or no issues during install.

Powerbook G4 Titanium II (2001) - (Hardy Heron) Works pretty well but does have some issues.  Sound doesn't work at all due to a known bug.  Supposedly an upgrade from Hardy to Intrepid will fix it but I recently upgraded from Gusty to Hardy and had tons of problems so I'm a little gun shy.  It also seems to have some problems moving between being plugged in and unplugged.  Haven't quite nailed that one down yet but hoping to soon.

Overall I'm extremely happy with Ubuntu.

---

### Post by Tigershell on 2008-12-12
eeepc 701 works flawlessly under Arch

---

### Post by tuskenraider on 2008-12-13
ubuntu 8.10
acer 9410z 
1.73ghz dualcore intel t2080 
1.5 gb ram
120 gb hdd
the hated broadcomm 43XX card (works like a champ with 8.10 =)!!)

everything works very well and the lappy is super fast!!

tusken
:guitar:

---

### Post by tubbygweilo on 2008-12-13
All works, machine specifications are in my signature.

---

### Post by jfbarthe on 2008-12-16
I'm a happy camper after a clean install of 8.10 on my dell 1505.
Upgrades from 7.04 through 8.04 were smooth.

---

### Post by RPG Master on 2008-12-16
Everything on my HP Pavilion dv2000 works... well, besides the Quickplay and DVD hotkeys (They were used to launch HP's stupid media center program that came pre-installed with Vista)

AMD Turion 64 X2 TL-60 2GHz
3gigs of ram
GeForce 7150M / nForce 630M

I got all this from Sysinfo. I am not sure if any of this is true.

---

### Post by wirawan0 on 2009-01-06
Just to add: I put out the post about my laptop (Dell Inspiron D600, 768MB RAM, Pentium M 1.6 GHz) here:

[https://wiki.ubuntu.com/WirawanPurwanto](https://wiki.ubuntu.com/WirawanPurwanto)

And there are some links to the relevant bug that is plaguing this laptop with Intrepid Ibex, most notably the keyboard lock after brightness change with Fn+Up/Dn keys.

Note: the other laptop (Sony VAIO) is an older one and Ibex also works mostly, but resume from sleep is still very troubling.

Wirawan

---

### Post by cometa2k7 on 2009-01-07
Acer Aspire 5920

Works fine, no real problems. The media keys on the right don't function, but that it's too much of a problem. The card reader and webcam also don't work, but to be honest I never use them, and there are probably HOWTOs out there somewhere.

EDIT: Ok, I really hadn't noticed this problem, I don't use my USB ports much, but they currently aren't working, at all. I'm sure that there will be a fix for this somewhere.

---

### Post by rick08 on 2009-01-07
I have Ubuntu running on an HP Pavilion dv1331se.  It works perfectly except for the mute buttons LED light doesn't come on.  No biggie.

---

### Post by ELF_O8 on 2009-01-07
Ubuntu 8.10 64 bit edition
Dell Inspiron 1526
AMD Turionx2 64 ~2.0 Ghz
3 GB RAM
160 GB ATA HDD
Dell 1390 minicard (wifi)
Sigmatel Audio
ATI Radeon Express 1270 ~320 MB Shared
8X DVD+-RAM 
HDMI output

Everything "just worked" right out of the box

---

### Post by chamber on 2009-01-07
Crunchbang Linux 8.10
Dell inspiron 1200,
1.25gb RAM
30GB hard drive
Belkin Wireless card.

Its 4 years old and the only thing that I've done is add extra RAM, it was necessary in windows but not since I put linux on it exclusively, everything works perfectly, no complaints at all.

---

### Post by LowSky on 2009-01-07
Im using an old dell inspiron 8100 and a IBM thinkpad T60, both work with no issues

---

### Post by maccam94 on 2009-01-07
Dellbuntu Insprion 1420n. Almost everything worked with the original version it shipped with (7.04 I believe) but now all hardware and features work 100%.

---

### Post by Gryph3n on 2009-01-07
Compaq Presario 2100 with the Intel processor.  Works great with Linux Mint.  Even the onboard Broadcom wireless driver.

---

### Post by jojo21 on 2009-01-12
I have a Fujitsu-Seimens Amilo 1818

Everything works, including all the FN keys. Wireless required ndiswrapper to get working, but thats it. Power saving and auto dimming works fine.

---

### Post by andresmh on 2009-01-12
Ubuntu Intrepid 32-bit is working pretty well on my Thinkpad X300. I only have some issues sometimes with sound, some apps take over sound and don't release it.

---

### Post by uberdonkey5 on 2009-01-12
Intel duo core 2GB RAM Dell Inspiron. Didn't come preinstalled, but installed ubuntu on it. After a year of tweaking this and that, and 3 reinstalls, I have ubuntu working perfectly, more than perfectly...

it does exactly what I want when I want it...I have all the codecs, all the software I need, boot up is streamlined to 23 secs, modem set up, beautuful but simple desk-top, no errors, power options perfect (I can close the laptop screen and still listen to the radio/music or keep programs running), short cut keys for terminal, home and some other stuff set up.

Basically, I think most people need at least 6 months to get the system as they want it, and during this period there can be lots of hassles with wireless, codecs, software and modems etc. However after this period it is so stable and dependenable its a rock.

- also have asus eeepc with original Xandros (OK, have advanced desk-top option, but I never use it and I hate the 'start' button). Works a dream, so why change it?

---

### Post by cprofitt on 2009-01-12
IBM T42p
Lenovo T61p
Lenovo T500

All fully working that I have seen though there are parts I do not use.

---

### Post by Frantic_Earthling on 2009-01-12
I have just installed 8.10 on an Asus M70VN-7TO87C (Core 2 Duo T9400 2.5Mhz / 4Gb RAM / 2 x 320Gb HD / 1920x1200 17-inch LCD / 1 Gb GeForce 9650M GT).

Everything seems to work like a charm, with the exception of the internal webcam which I have not tried to install yet.

---

### Post by Fenris_rising on 2009-01-12
Hi all

EEE PC 904hd. Ubuntu netbook mix 8.04.1 works straight out of the box.
I have a 1G mem stick which I used to install the OS and I have gradually added back ups of my 'personnel' tweaks. Solid as a rock and I also hear that HH 8.04 run fine as well.

regards

Fenris

---

### Post by mustang on 2009-01-12
Acer 5735-4774---everything worked completely out of the box. Very impressed.

---

### Post by Macchi on 2009-01-16
Here is a short report for 3 laptops:

Vaio VGN-B1XP limitations on Ubuntu 8.10:
External VGA does not extend the desktop to an external monitor on certain resolutions, breaking x completely; Mobile Broadband through Huawei E600 doesn't work. MemoryStick reader doesn't work.
 
EEEPC 701 and EEEPC 900 limitations on Ubuntu 8.10, custom eeepc kernel:
Built in microfone doesn't work. Touchpad with limited functionality: Wireless On/Off function key doesn't work; Suspend unstable.






Tested with Ubuntu 8.10 and latest updates during jan 2009. My comparison baseline is the same hardware and configurations that otherwise work fine with the OS and software preinstalled upon acquisition of the computer. 

Experiences with ten other laptops have been omitted from the report, since two of them are not in use anymore and the others belong to friends and clients. Mostly the laptops are working ok with exceptions for eventual problems with suspend and hibernation.  

For the record, I have been a GNU-Linux desktop user since Hoary 5.04 and got to admit it's getting better all the time. (Servers since 2002).

---

### Post by markofealing on 2009-01-16
Laptop: Dell Latitude C640 running Kubuntu 8.10

Everything works except the Brightness and Contrast keys since the upgrade to 8.10. This is a known issue.

Otherwise a great Linux laptop

---

### Post by vorostatz on 2009-01-16
Dell Inspiron 6400 with 320 gig replacement drive, Intel 2.16 ghrz core 2 duo, 1 gig (soon to be 2 gigs) ram, and a bluetooth dongle. Ubuntu (Intrepid Ibex) works perfectly with my laptop, just cant say the same with all my peripherals .  So far no complaints about Ubuntu per se just some of the linux programs. Honestly I have never had a computer set up go so fast as it did with Ubuntu.  They just need to work out some of the bugs with Ubuntu (that have absolutley nothing to do with whether or not it works with my laptop).  Say if four or five iterations of the Ubuntu OS and you will  have a true replacement OS for the average person (and by average I mean not tinkerers like us).

---

### Post by TommyGalvez on 2009-01-18
Working perfectly now after getting the wifi working and editing the Xorg.conf. Thanks to this forum for all the info and help. 


Fujitsu Siemens V5535

---

### Post by forcecore on 2009-01-18
works fine but only nvidia 8200 is soooo slow 2d that window draws slowly and viewing pictures is slow in 8.10, i hope 9.04 fixes that.

---

### Post by KyleBrown on 2009-01-26
Hi, I voted the whole It works partially and I will post the problems.

Well... where to begin...

Ah, we can begin with the booting.  For some reason and no one I know is sure why... even a guy who builds computers for a living and has for 15 years... can pinpoint the reason.  Linux will continually force my computer to boots from the sound card.  It forces it through realtek boot agent which doesn't exist... at least not on my laptop it doesn't.

It also keeps freezing and crashing no mater what I've tried.  (i just got a fix on the forums which I think has done the trick. THANK YOU)  

I was hoping the fix would fix the other problem I have too, which is less explainable.  Sometimes my apps just won't work.  I will click on them and they will show up on the bar that it is open, but no window ever pops up and the bar goes away within 10 seconds... I have to restart it manually before it works because it won't open the shut down menu.

I still love ubuntu despite these problems though, because let's face it, I'M FREE!!!!!    and with the help I can get here it beats anything that you can get with windows or mac




(if anyone can help with my app problem please let me know.  Thank You)

---

### Post by HuaiDan on 2009-01-26
Out of the box or after tweaking? ;)
Kidding.

Works completely. Samsung r408, available in east Asia. Pentium Duo, intel Opel gl graphics, 2GB, 250 GB, Atheros wireless (look that up...a well documented hive of creepy crawlies that one), UVC webcam. It was a challenge getting up, and I still can't get it to dual boot. Either GRUB wipes out the windows boot record or vice-versa. Tangent, oh well.

Some of the function keys (screen dimming) won't work, but they won't in windows either without installing the Samsung utilities that came with it. None available for linux that I know of, if it becomes an issue I'll solve that problem by brute force or attrition just like every other linux issue I've encountered.

---

### Post by arm-c on 2009-02-02
My computer is an Acer Travelmate C300 Tablet.

In general, all of the basic functions worked flawlessly, however, there are a few items that bear frustration.

a.  My CAC Card Reader doesn't work.  Doesn't appear to be a functional driver available for it.  O2Micro card reader I believe.  I have given up on getting it to work under Ubuntu.  Any pointers?

b.  The tablet buttons are not functioning correctly.  The AcerHK program adds some functionality, but it just doesn't work perfectly.  Some buttons aren't aligned properly (ie Web button launches email and vice versa).  The Keytouch application provides some remedy, but under Ubuntu 8.04 that cause hang on shutdown.  Also, the buttons to turn on/off wireless/bluetooth don't work properly.  I have written a small utility to do that with a GUI ([http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net))

c.  AcerHK and keytouch are not able to support the tablet specific buttons.

d.  Tablet features require manual configuration.  Would be nice to have a program that fixes that.

e.  Screen Rotate and Auto Rotate don't function.  Also, GDM/Compiz doesn't respond well to screen rotation.

With all that said, those functions are minor.  I use a USB CAC Card Reader.  I don't rotate screen (use landscape).  and I wrote a small GUI to interact with AcerHK driver.  I'd say it is in the 95% area and that because all of the LAPTOP specific functions worked out of box, I'm at 95%+ in usability and problem free.

---

### Post by andrewpmk on 2009-02-02
A few minor problems on my Toshiba Portege M800:

- Wireless does not resume after suspend/resume. See [workaround]("http://ubuntuforums.org/showthread.php?t=1017306").
- Bluetooth does not work.

---

### Post by ramirabeau on 2009-02-02
Took a little forum hunting, but all is good. Finally got the webcam to work through Ekiga, but looking for a stand-alone webcam program that works now though. Even the SD media card reader works.
HP Pavilion DV6446us, Intel Core Duo 2GHz/2GB/160GB/Intel GM950 Video/Intel Pro Wireless

---

### Post by adamlau on 2009-02-02
No probs whatsoever on an IBM T42 2378-FZU and a Lenovo T60 6371-74U.

---

### Post by twodogsdad on 2009-02-02
Toshiba Satellite. My first laptop, $400.00 for Christmass off of Newegg!!! woo hoo. Dual booting Vista and Xubuntu. 

I have two issues that have come up since my installs, first tried Kubuntu for the first time now have xubuntu running. The first is the common WEP issue where I can connect to some WEP networks when booted to ubuntu but not all, and sometimes I can get on the network with Vista but not Xubuntu boot. I said I don't know why in the poll because none of the work arounds in the threads seem to apply to my system.

The second is that my screen now does weird things when I switch my boot os. I mean that if I've been using Xubuntu and reboot to Vista the bottom 1/4 or so of my screen is distorted for a second or two before looking normal. My screen now flickers in Vista sometimes. And when I boot into Xubuntu the screen sometimes flickers on boot up.

---

### Post by quirks on 2009-02-06
I use a HP Pavilion dv6730ec and almost everything works. I documented the details in the Ubuntu Wiki: [https://wiki.edubuntu.org/LaptopTestingTeam/HPPavilionDV6730ec](https://wiki.edubuntu.org/LaptopTestingTeam/HPPavilionDV6730ec)

HP Pavilion dvXXXXyy seem to be supported pretty well, in general. Also, they are very feature rich (fingerprint, webcam, card reader, remote control, multimedia keys, HDMI, ...) and shiny (see here: [http://images.google.com/images?oe=UTF-8&q=hp%20pavilion%20dv6700&um=1&ie=UTF-8&sa=N&hl=en&tab=wi](http://images.google.com/images?oe=UTF-8&q=hp%20pavilion%20dv6700&um=1&ie=UTF-8&sa=N&hl=en&tab=wi)). I can only recommend one of those.

---

### Post by ibutho on 2009-02-06
I use an HP G7000 and everything works out of the box for me. Ubuntu doesn't like the Atheros AR242x wireless card, but other other distros work out of the box.

---

### Post by thisllub on 2009-02-06
Nearly 2 years later this still isn't fixed

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37382](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37382)

ACPI doesn't work either.
ACER Travelmate 5610.

I have been running PC-BSD for over 6 months and just switched to open Solaris.

---

### Post by JordyD on 2009-02-06
Dell Latitude D610

Works perfectly.

---

### Post by Nicu Alecu on 2009-02-13
DELL Inspiron 1501 // Turion 64X2
2Gb RAM // 120Gb HDD

Works perfectly on Gutsy (imagine that!) except for the largely debated issue of hibernation, which I don't use anyways.
It runs so well (yeah, I did spend about 4 weeks to fine tune it back then - Nov 2007 - with a lot of help from this amazing community, thanks) that I never even considered spoiling such a smoothly running machine. In our company, we do have other laptops & desktops running Hardy, so I had other machines to satisfy my curiosity, but I never touched my good ol' Gutsy, except for the usual updates.:popcorn:

That being said, I'm in the market for a new DELL XPS, I think I'll go with 9.04 when it comes out ...

---

### Post by richg on 2009-02-13
Purchased the below laptop nearly four years ago from [http://www.gigastrand.com/](http://www.gigastrand.com/)
 Came configued from the seller with Linspire 5.1.427.Just upgraded to Mint 6. I went with Mint because the DVD application worked right out of the box. Wireless works very well also.I like green back ground rather than brown.

    * AMD Mobile Sempron 2800 (black chassis)
    * 15" XGA 1024x768 Display
    * 1256MB DDR400 RAM DDR400 PC3200 DDR 200-pin SODIMM
    * VIA K8N800 Chipset and Onboard VGA (AGP 8X, 3D Capable)
    * CDRW/DVD Combo Drive
    * 40GB Hard Drive
    * 4 x USB 2.0
    * Integrated 10/100 Mbps Ethernet, 56k v.92 modem
    * Linspire O/S + DVD Player
    * Mini-PCI Wireless 802.11G 
    * Weight 7 lbs
    
Rich

---

### Post by crunchfighter on 2009-02-13
Gateway M-6866 
64 bit
4gb RAM
Everything works great

---

### Post by Ntacman on 2009-02-13
My gift laptop, HP Pavilion N5425, No custom hardware*cept for the PCMIA Wireless card*everything worked off the live CD, and still works right now, reinstalled 2 times just to test, and kept working,except for effects...but That really doesnt matter to me.

---

### Post by not a pipe on 2009-02-13
works great.

dell m1530
A07 bios
3gb ram
t7250 2ghz dual core
intel 4965 wireless
nvidia 8600M GT 512MB

---

### Post by thisllub on 2009-02-13
> **thisllub said:**
> Nearly 2 years later this still isn't fixed

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37382](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/37382)

ACPI doesn't work either.
ACER Travelmate 5610.

I have been running PC-BSD for over 6 months and just switched to open Solaris.

Apart from filesystem compatibility issues Solaris is great.
Fast, reliable and acpi works perfectly.

---

### Post by mixtri on 2009-02-14
Hello There. I have a HP Pavilion DV7. I'm havingproblems getting the correct drivers for my onboard wireless card. Does yours have one and if so which driver are u using? I also have a netgear router which comes with a usb wireless dongle. that won't work either. I would like to get the onboard card working first before begining to fix the usb key. Please help. I believe its an Atheros AR9280 802.11a/b/g/n and/or Atheros AR2425 802.11b/g not exactly sure which of them, but they are both listed in the user manual. i'm running ubuntu 8.10

---

### Post by dgray_from_dc on 2009-02-19
As stated in the thread below, Linux saved one of my laptops from being scrapped.

Xubuntu Hardy on a Sony VAIO PCG-R505JL
Intel P3 733Mhz
128MB RAM
CD/DVD-ROM
60GB HDD

[http://ubuntuforums.org/showthread.php?t=929793](http://ubuntuforums.org/showthread.php?t=929793)

---

### Post by degmic71 on 2009-02-19
Laptop.

Dell Inspiron 600m 
Distro: Xubuntu

Fixed that did not initially work:  volume + volume manager , function keys

Video: Using open source ATI driver.  01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

------------------------------------------------------------
rest of lspci output:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

----------------------------------------------------


Email me if you need help with any hardware on a 600m or any Dell.

---

### Post by degmic71 on 2009-02-19
Double post

---

### Post by degmic71 on 2009-02-20
> **mixtri said:**
> Hello There. I have a HP Pavilion DV7. I'm havingproblems getting the correct drivers for my onboard wireless card. Does yours have one and if so which driver are u using? I also have a netgear router which comes with a usb wireless dongle. that won't work either. I would like to get the onboard card working first before begining to fix the usb key. Please help. I believe its an Atheros AR9280 802.11a/b/g/n and/or Atheros AR2425 802.11b/g not exactly sure which of them, but they are both listed in the user manual. i'm running ubuntu 8.10
Did you check your manufacter's website for linux drivers? Often if its a company like Intel , Atheros, or other, the actual webste (i.e.) Intel will have the linux driver. If not, check out this page:

[http://www.atheros.com/news/linux.html](http://www.atheros.com/news/linux.html)

or more spec.:

[https://sourceforge.net/projects/madwifi/](https://sourceforge.net/projects/madwifi/).


Nothing a 10 second google search will do you. ENJOY!

---

### Post by simonbanyard on 2009-02-20
My signature says the spec. In general (and honestly not being a Dell shill!!!) they are the best for Ubuntu, or generally linux tbh, everything works. Obviously there are a few post install tweaks (I'm looking at you pulse audio and NVidia!). I've even had OpenSolaris singing without much tinkering...

A quick tip to anyone having Wifi issues. Enable the backports repository and try installing drivers that way, worked for me on the Acer Aspire One...

---

### Post by Kareeser on 2009-02-20
Dell 700m. Working great!

Open source intel driver (I think), all function keys work. :)

---

### Post by Telekinesis on 2009-02-20
HP zd8000. Everything works, though I've had to use some tweaks to get it exactly how I want it. Updated Compiz Fusion/sphere/effects = smooth. ATI drivers, wireless, etc. No problems that can't be resolved so far. This is with Hardy 8.04 LTS.

---

### Post by calrogman on 2009-02-20
8.10+ have kernels incompatible with my USB wifi dongle, no Linux kernel drivers can turn on my laptops inbuilt wifi due to some evil kill switch that can only be flicked using Windows software (that doesn't work with WINE), there is one way to get it working which is to put a sliver of scotch tape over a pin on the wifi card, however this would A) void my warranty and B) involve me actually figuring out which pin:p.

---

### Post by dodle on 2009-02-20
Averatec 3280
80gb HD
512mb Ram
1.6ghz AMD Mobile Sempron
VIA S3 Pro Unichrome video
Broadcom BCM4306 802.11b/g

Using Ubuntu 8.04 Hardy

There are only two things that aren't fully functional.  The VIA video drivers don't work very well, so I am using vesa (which I am very happy with for now).  The other thing is my SD card reader.  

The Broadcom wireless adapter was taken out of a Dell Inspiron.  I think the model number was 1150.

---

### Post by Rotaj on 2009-02-21
Acer Aspire One 110L using Linux4One.

Almost eerything works, except right card reader won't read xD cards.

---

### Post by r m h on 2009-02-21
Over the years and through the woods from 1998 and beyond...

I've had excellent results (full functionality) from the following:

Dell Inspiron 7000 (300MHz, 386MB RAM) (RedHat)
Dell Inspiron 8100 (1.2GHz, 512MB RAM) (RedHat & Fedora)
ThinkPad T42p (2.0GHz, 2GB RAM) (RedHat, Fedora, and Ubuntu)
ThinkPad T61p (2.4GHz core 2 duo, 4GB RAM with WUXGA LCD) (Ubuntu)

My current laptop is the T61p, the backup is the T42p, the 8100 is falling apart in a bad way, and the 7000 is still rock-solid, but outdated.

I run Intrepid on the T61p, use the internal WiFi and an AT&T PCMCIA 3G card (Sierra Wireless 875) for wireless.  All function keys are working.  When I ran Hardy on the T61p, I did use the finger print reader, but do not at present.

---

### Post by mamamia88 on 2009-02-21
works great on my laptop only problem was wireless which was fixed by connecting to ethernet and downloading the broadcom driver

---

### Post by joker535 on 2009-03-15
Ned Dell Vostro 1510 C2D 1.8 / 3 Gigs DDR2/800 DVDRW/250G SATA HDD Intel ABG wireless / onboard video.

Everything works out of the box on 8.10. The wireless light flashes instead of being on solid but it doesn't hurt anything. Easy, smooth and simple. I have it dual booted with XP pro SP3 but have not had to use XP yet. If you are going to dual boot from a fresh reload, create an XP NTFS partition first, create an NTFS data partition to share files between the os', then install XP before you install ubuntu. This gives you a nice grub boot screen which will let you choose to go back to the windows boot screen, an NTFS data partition that will let you share files between the os' (via NTFS-3G), and good reliability as you can use either OS should one fail. 

Good Luck

Bob

---

### Post by grogo on 2009-03-16
2 HP laptops:

**dv6627ca:** 8.10 32bit almost everything works, minor hassles with the nvidia and broadcom wireless drivers in previous versions.  had to specify hpet=disable in the grub options to get it to boot 8.10 properly, hibernate and suspend don't work  currently on

**dv4-1117ca:** 8.10 64bit everything but the hp remote works, had to run the alsa update script and specify a couple of options in etc/modprobe.d/alsa-base to get the sound to work properly.  Hibernate works properly, haven't tried suspend yet (haven't even had it a week yet)

---

### Post by Mehall on 2009-03-16
I needed to use the proprietary drivers for nVidia and for my WiFi, but once I had done that, everything is fine.

One minor niggle (present in OpenSUSE latest and 8.10 derivatives too, but not present in 8.04, so I'm guessing it's weird kernel-ness) when i boot up, it freezes, but if I press keys, it'll boot fine. I either need to hold keys thought till gdm, or I can press the power button for a little bit, and it'll load right through.

---

### Post by mister_playboy on 2009-03-16
Sony VGN-NR430E... no problems.

---

### Post by Linux000 on 2009-03-18
Two Problems, Light Sensor on my Dell doesn't work, can't install libsmbios-bin, and back light jumps up to full brightness at about 30% then falls back, also gnome cd master won't recognize my cd drive.

---

### Post by inspired on 2009-03-19
Running 8.10 on an HP Compaq nx7010
Video: ATI Radeon 9200, 1680 x 1050 @ 60.7
Audio:  I82801DBICH4
Wireless: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
Ethernet: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
Ram: 2 GB ram

Everything works, including SD card reader, wireless, audio, etc. EXCEPT I am not able to Hibernate. Still trying to get to the bottom of that.:popcorn:
Suspend works so long as the wireless is turned off beforehand.

UPDATE: Decided to tackle this hiberation issue again.
Discovered the my swap was not loading right. My fstab uses the UUID for reference to the partitions, etc., and what I have discovered is that changing the Swap partition (it's size for instance) will cause it to get a new UUID. The fstab then needs updating to reflect this.
Sorted that out, but still no hiberation.
Next step was to add the following to my grub menu.lst file... to the end of the kernel line:
... rootflags=data=writeback resume=/dev/(swap partition goes here)

I am not sure if the rootflags bit was needed, but the person who reported that adding resume=... to this line, also had that on there, and I did not, so I added them both.
Now the computer hibernates and resumes perfectly. Beautiful.

How to change my vote? Oh well...

---

### Post by koleoptero on 2009-03-19
I have a Toshiba satellite M70, everything works perfectly. It's  a bit old so I'm not going to post specs since any laptop you might buy now will have nothing in common with it.

---

### Post by k2t0f12d on 2009-03-19
Acer Aspire 5920 running Archlinux

---

### Post by jocheem67 on 2009-03-19
Dell Inspiron 9400

Probs:

* hibernation
* multimedia buttons

No biggie.

---

### Post by canoemoose on 2009-03-19
HP Compaq nx6110.

Everything works.

Intel graphics, Broadcom BCM4318 wireless.  Used to use ndiswrapper, however an update gave me a new native driver (b43-pci-bridge) which worked but broke ndiswrapper which broke my ethernet networking.  Uninstalled ndiswrapper to try and get the wired networking working which fixed everything.

Suspend/resume is fine, hibernate would be if I could be bothered to increase the size of my swap.

Only thing is the BIOS is now dying and it doesn't always recognise the hard drive or optical drive at POST.

Hope this helps,
canoemoose

---

### Post by TVC15 on 2009-03-22
Hello,  I am running Ubuntu 8.10 on my Lenovo T61.  All works very well except for one minor issue and that is the fingerprint scanner.  This is not important for me.
More importantly: video (Nvidia), Wifi (Intel, sound, special keys, touch-pad, etc all work flawlessly and out of the box.  No fiddling with drivers needed whatsoever.

Thanks a lot, Ubuntu

---

### Post by moopet on 2009-03-22
Dell D420 ultraportable, 3GB RAM, 80GB HDD, intel gfx, synaptics touchpad, intel audio, dell 360 bluetooth, intel 465 agn wifi.

No idea if the modem works, I pulled it out before installing.
Not tested with firewire.

The only problems I get are the same as I'd get on any system.

---

### Post by cfree220 on 2009-03-22
Works Partially on the Dell XPS M1530.

One problem is the support for the integrated webcam and mic. I've followed several walk through solutions to getting this working (even for this specific model), and have not been able to get it to function properly with Skype. I am currently unable to get any input through the mic with any program... I think that's just a configuration problem though.

Occasionally I have a problem with the Compiz spherical desktop. It's a graphics error in which, instead of showing my skydome as a bacckground, it is thousands of instances of the 3D windows, which reproduce as you drag the sphere (an graphics error sometimes seen in Windows, pre-vista). I'm not sure if this is a problem with the graphics card (nVidia 8600M GT), with the video driver, or with Compiz itself. The other day I had another graphics problem where I was only getting like a frame a minute. I suspect these to be bugs in Compiz.

Another intermittent problem I have is with the sound. Occasionally, the output gets stuck on one frequency, which it emits in staccato-esque succession (almost like a beep, except you can tell the frequency came from the music you were listening too... hard to describe, really). I suspect this to be a problem with the audio driver. Unlike the graphics problems I sometimes have (this may further point to Compiz as the culprit), the error cannot be fixed by logging out and signing in again. The computer must be shut down, and the repetitive sound continues until about the halfway mark on the shutdown splash progress bar.

Another [minor] problem I have with sound is the output relative to the volume setting. When using the integrated speakers, sound becomes inaudible between 45-55%, depending on the sound file. Each jump is about twice as big as it should be, which makes fine tuning the volume difficult (annoying when trying to sleep or study).

When trying to eject a compact disk, I have to unmount the CD before I can eject it. I'm not sure if this is intentionally setup like this, but because the unmount button is right above the eject button, it makes the hardware eject button somewhat useless. This is more of an annoyance than a real issue. I'm still not convinced of the functionality of the hardware media controllers... They seem to work, but are not as responsive as they are in Windows.

Hibernation works ok, but is better if you remove any storage media from the card reader first.

Finally, I am not able to connect to my school's WPA2 encrypted secure network. Windows does this without a problem... Ubuntu will not. I tried downloading the keys and what not, and it just will not work. I believe this is either a problem with the school's specific network configuration (they only officially support Windows and Mac), or a problem with the WPA2 version (enterprise). At home, I am able to connect to a WPA2 personal network with no issues.

To be honest, I am really not that bothered by the shortcomings of Linux on this computer. Sure, it can be annoying when I have to reboot to fix a problem (I'm sure I'll eventually learn ways to fix these from command line without reboot, but either way, it boots so fast it isn't really an issue), but overall I don't feel like there are any reasons to not give it a go. My laptop dual boots Intrepid and Vista Ultimate. The only reason that I have it able to boot Windows at all was because I sometimes need to run Wiindows/Mac only programs for classes that just don't work under WINE. I recently started using VirtualBox; I have a VM for Vista Ultimate, the Windows 7 beta, Xubuntu, Kubuntu, and am working on setting one up for BackTrack3. The programs that I was using Windows for work fine in the virtualized environment. I can't even remember the last time I booted to the physical Vista partition on this computer. I feel like this shows just how great Ubuntu is that, despite the few bugs it has, I still prefer it over Windows.

To be honest, I don't think you're ever going to find a brand new computer that is going to run Ubuntu, or any other Linux distro, like a dream. The Linux community is smaller, and hardware manufacturers are going to prioritize in favor of the evil empire (I'm not talking Yankees fans). I have not tried Ubuntu on other laptops, but would definitely recommend the XPS M1530. It is a bit on the pricier side, and does run a little hot, but it's an outstanding performer. If you do need to dual boot, there's a great trick you can do using this laptop. Because dell ships some of its notebooks with an embedded, media playing OS (Dell Media Direct), the computer actually has two power buttons. On the CD that comes with the comp for reinstalling DMD, there is a program that lets you tell the Dell MBR which partition to boot depending on which button is pressed. This means that you have a hardware boot menu, instead of having to go through GRUB each time you start your system. For dual boot laptops, I'd say that the M1530 is king.

EDIT: I don't remember the detailed specs off the top of my head, but here are some of the basics:
-Intel Core2Duo T8300 2.40 GHz processor
-4GB Ram (not sure on the actual hardware)
-nVidia 8600M GT GPU (512MB discrete video ram)
-320GB HDD (WD I think)

---

### Post by mpc350 on 2009-03-22
Installed ubuntu on my Lenovo y530 and it mostly works great.  Getting sound out of the subwoofer took a little bit of effort.  The display brightness is in reverse but not really a problem.  Webcam works perfectly.  My only ongoing problem is making it suspend to ram.  Have tried a few fixes but to no avail.  Had an old toshiba satellite that wouldn't suspend either.  Once I tried fedora and it suspended brilliantly.  

Overall, am quite happy with how well it works.

---

### Post by BackwardsDown on 2009-03-22
I've got a dell latitude d830, it works completely. Except for the network-switch, but I don't use it anyways.

---

### Post by Onesimus on 2009-03-22
I have a Dell Inspiron 6400.

Everything works !  (Even suspend and hibernate)

The only issues were the load-cycle-count and the fans; which were both sorted.

---

### Post by mpc350 on 2009-03-22
on my asus eee pc 900a, everything works perfectly using eeebuntu netbook remix.  not a single glitch.  i would like to see if I can clear out some unnecessary files from the installation.  my tiny 4Gb SSD is nearly full.  wouldn't mind if startup was a little faster.

I really like the UI for the netbook remix desktop.  It makes the correct assumtion that netbooks are not for "serious" computing, but makes it easy to deal with the small handful of apps that I play with on the couch in front of the tv or while travelling.  But I can work with the traditional desktop if I want to get serious with my $170 laptop.

---

### Post by Froodolt on 2009-03-22
Linux works completely with my laptop.

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

$ sudo lshw
description: Notebook
product: Pavilion ze5500 (DP863E)
vendor: Hewlett-Packard
....
description: CPU
product: Mobile Intel(R) Pentium(R) 4     CPU 2.66GHz
....
description: VGA compatible controller
product: Radeon IGP 330M/340M/350M
vendor: ATI Technologies Inc
....
etc...

```

---

### Post by the8thstar on 2009-03-22
In this version of Ubuntu (8.10 as I write), everything is working out of the box. The specs are in my signature below.

---

### Post by Daisuke_Aramaki on 2009-03-22
Lenovo3000N200
Dual boots FreeBSD7.1 and Lunar Linux. There are some acpi related issues with FreeBSD. But my Lunar Linux partition works great! Everything works, wireless, acpi, hotkeys, fingerprint reader, to name a few.

EEEPC1000H
Powered by Lunar Linux. No issues, after a lot of post configuration, almost all the features are recognized.

---

### Post by Delvien on 2009-03-22
Dell Latitude D820 1.67 ghz dual core, 2gb ram 667mhz, 80gb 7200 sata, hotplug cd/dvd. Everything works, minus IR, which I haven't tried to set up. No need :)

---

### Post by novafluxx on 2009-03-23
I'm using a Dell Inspiron 1318, only proprietary driver needed is BCM4312 for my wireless card. So far no disto (that I've tried [openSUSE, Fedora]) has included it besides Ubuntu.

---

### Post by wyliepops on 2009-03-23
Jilted by the Jaunty Jackalope!

   As far as functioning goes, everything works on my Dell Inspiron 9400 with Intel everything, except for Network Manager with a D-Link wireless N router. I can connect to the University open network using wireless B without a hitch. Is it my Intel 4965AGN card, my driver (installing that in Intrepid only worked temporarily until an update killed the WIFI), or a _bug in the Network Manager_?

   Oh, the joys of configuring Ubuntu 64! The Flash, the repositories, the Skype, the wireless! Practice makes perfect. ;)
There are also no plans for support (according to Creative Technologies) for drivers on 64-bit linux for my Creative Audio Soundcard either!:(

---

### Post by k2t0f12d on 2009-03-23
Fully functional Acer Aspire 5920:

--------------------------------------------------------
This is what will be sent to the Linux Counter if you
run the program with the -m switch. Now, NOTHING IS SENT
--------------------------------------------------------
From: k2t0f12d
To: [email]machine-registration@counter.li.org[/email]
Subject: machine-update for ZEITGEIST

Mail program that sent this email: /usr/bin/mail
Perl version used to run machine-update: 5.010000

//MACHINE
accounts: 2
cpu_uname: i686
kcoresize: 931131392
kernel: 2.6.28-ARCH
key: 398515
mailer: postfix
method: machine-update version 0.31
name: ZEITGEIST
os: Linux
uptime_1:  19:41:48 up 3 days,  1:06,  2 users,  load average: 0.16, 0.07, 0.02
uptime_2: runlevel (to lvl 3)                    Fri Mar 20 18:35 - 19:41 (3+01:06)   
users: 0
//END
//FILE /proc/meminfo
MemTotal:        2065780 kB
MemFree:         1378568 kB
Buffers:           36020 kB
Cached:           266080 kB
SwapCached:        29176 kB
Active:           292232 kB
Inactive:         277880 kB
Active(anon):     199648 kB
Inactive(anon):    79640 kB
Active(file):      92584 kB
Inactive(file):   198240 kB
Unevictable:        2260 kB
Mlocked:              80 kB
HighTotal:       1178440 kB
HighFree:         647020 kB
LowTotal:         887340 kB
LowFree:          731548 kB
SwapTotal:       2096472 kB
SwapFree:        1990044 kB
Dirty:                44 kB
Writeback:             0 kB
AnonPages:        267996 kB
Mapped:            77648 kB
Slab:              30412 kB
SReclaimable:      21864 kB
SUnreclaim:         8548 kB
PageTables:         3488 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3129360 kB
Committed_AS:    1020236 kB
VmallocTotal:     122880 kB
VmallocUsed:        9088 kB
VmallocChunk:     107992 kB
DirectMap4k:       90104 kB
DirectMap4M:      819200 kB
//EOF
//FILE /proc/version
Linux version 2.6.28-ARCH (root@T-POWA-LX) (gcc version 4.3.3 (GCC) ) #1 SMP PREEMPT Sun Mar 8 10:18:28 UTC 2009
//EOF
//FILE /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3668.73
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping	: 13
cpu MHz		: 1833.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3668.78
clflush size	: 64
power management:

//EOF

**CAVEAT: using cpu throttling, both cores are 1.83GHZ

---

### Post by mgw2008 on 2009-03-23
I'm running on Lenovo T60. Speed and operability is much better than Windos. 

Issues remain with:
WiFi (ATH9K is a must!), 
font resolution (I'm running now on "Segoe" for desktop font and "Linux Libertine" for serif font)and
hardware support (eg the ThinkPad's "Trackpoint").

In my opinion, the "dummy" end user will not be able to handle the installation of WiFi drivers (requires compilation), OO 3.0 (requires change of package source with an APT commandline that is mostly unknown) and fonts (needs deeper understanding of the concepts).

---

### Post by MGaddict2000 on 2009-03-23
I have a Gateway M275 Tablet PC. 

I think I had a bad install because the things I can't get working, other people with the same laptop have had no issues with. The tablet is the hardest thing to configure but in doing so you learn a lot about Linux and how Ubuntu works. Everything can be configured to work with the right scripts but several of those features, like screen rotation, I never use so have never bothered to set up. The screen calibration is something I can't get working correctly, but other M275 owners have not had this problem. Otherwise, this is an awesome laptop to install Ubuntu Linux on. It takes some work, and there are specific M275 HOW TO pages out there to step you through it. If you can get your hands on one of these and are wanting to learn Linux, I highly recommend it.

---

### Post by JackieChan on 2009-03-23
> **aysiu said:**
> My previous laptop, which I've since given away worked perfectly with Ubuntu out-of-the-box. It was a Dell Inspiron 500m. The only thing I'll say is that when I bought it, it didn't have a wireless card inside. So I made sure to buy a Linux-compatible wireless card when I got one (Intel Pro Wireless 2200, thanks to recommendations from these forums).

I know run an Eee PC. Don't know if it counts as a laptop. It ran perfectly with Xandros as preconfigured by Asus. I installed eeeXubuntu on it, which included some Eee-specific tweaks, and it works almost perfectly, except that the boot time is now extremely slow, and resume from suspend doesn't work all the time any more.
This, only it was a different Laptop.

---

### Post by Dragonbite on 2009-03-23
I just tried Intrepid on my Dell D400 laptop and, as expected, everything works out of the box except the Wi-Fi which requires the proprietary drivers and cutter which Ubuntu makes the easiest to accomplish (I've tried with openSUSE and Fedora).

Also, my Microsoft webcam works with Cheese better than Fedora 10, which was the only other distro I could get it to work with. It even included more menu choices than Fedora's version.  Hardy could never connect to it.

---

### Post by argie on 2009-03-23
Dell XPS M1330. Everything works, including Intel 4965 AGN wireless. Graphics are slower than expected on Hardy.

---

### Post by jelle_ on 2009-03-23
sony vaio vng-nr38m

ubuntu runs well, exept my wireless card. now i have internet trough an usb-device

---

### Post by rolandrock on 2009-03-23
I have Asus eeepc 900 with 2G RAM running eeebuntu 2.0 (Intrepid) - everything works perfectly (as far as I can tell).
And, Acer 5920G 3G RAM running vanilla Hardy - works perfectly.

---

### Post by Irihapeti on 2009-03-23
I have an EeePC 900 running standard Ubuntu 8.04. I did a number of tweaks to get webcam, wireless and hotkeys to work. As far as I know, the only things that don't work are touchpad configuration and the onboard microphone. I get around the last one by using an external microphone. As I prefer to use a mouse rather than the touchpad, I've disabled the touchpad altogether, though I can turn it on manually if I need it.

---

### Post by Blou_Aap on 2009-03-24
Toshiba Qosmio x300-11T
Everything works with some of the things you have to do little work a rounds and tweaks (Sound issues and BT).
With Blue-tooth I use external for now till that works.

The only things I wish that would work is the red lights on the top speakers and the strip of light above the Touch pad. Those lights make this lappy look really good.

---

### Post by Ferb on 2009-03-24
I have a dell vostro 860. Everything works except the led when I connect with wireless. I had to compile the drivers for the wireless though. Everything else (card reader) works

---

### Post by White Rasta on 2009-04-09
Dell Inspiron 1525 [name: Rita]
intel dual core t2370@1.79/533 [thinkin' about a t8300]
4gb 667 ddr2 [org 2gb]
500gb/3.0Gb/s scorpio blue [org 160gb/1.5Gb/s w/ vista home premiem]

everything works

rating:
Da'****!    [SWEET!]    OK    Sucks!

vista would freeze, and explorer would crash frequently on this machine
issue w/ mouseover on some pages in internet explorer triggering a loop that would open "about blank" pages untill i killed the process
cd/dvd drive was flaky [burned a lot of coasters]

installed 8.10 almost a month ago

did i say everything works? [and stable]

it does everything i need it to do very well

in the past 6-7 yrs ago i tried several differnt distros on my desktops but couldn't produce a viable environment [my stoner brain couldn't handle the "command liney thing" when dealing with drivers and apps]

the apps i installed are impressive, and the fact that they are free blows my mind

it looks like the the commercial software companys will have a harder time of "farming the masses for wealth" with their "junk software"

ok, you got me

the revolution will not be televised, it will be on the internet

---

### Post by N_Nick on 2009-04-09
Macbook Pro (Penryn i think)

It needed some tweaking but eventually everything works.  Everything I tried that is - I never use some of the things like bluetooth etc, so I can't be sure.

---

### Post by Shadowclaw on 2009-04-09
I had no problems installing and running 8.10 x64 on my laptop with kernel version 2.6.27-11

Compaq V6000
AMD Turion64 X2-TL60 2.0GHz
500GB WD HDD -- Dual Boot with Windows XP Pro SP3
nVidia Geforce GO 6150
2GB of RAM
Broadcom Wireless (works with no issues)
Bluetooth (works with no issues)

---

### Post by Jpardue on 2009-04-10
I have a Sony vaio vgn-fz240e/b laptop and my volume button and pause on my laptop case are actually more functional in Ubuntu. When I have Windows installed an am using iTunes my iTunes window has to be focused for the volume and play/pause buttons to work. Though in Ubuntu using Rhythmbox my window does not have to be selected for my play/pause and volume buttons to work. Yay for more functionality in linux!

---

### Post by arkmundi on 2009-04-12
Have Dell Inspiron 1525n - the version that came preloaded, worked great out of the box.  I since upgraded to 8.04.  That upgrade caused certain problems - notably sound issues - that I subsequently resolved (with Canonical help).  I purchased the support package from Dell, which is from Canonical.

---

### Post by donovan1983 on 2009-04-12
I put that it works completely, although there are some minor issues on my Acer Aspire One AOD150 (the 10" model) with the Ubuntu 9.04 beta. The WiFi LED indicator doesn't work and neither does the switch. The brightness controls are wonky and every time my system boots it resets the brightness. The onscreen brightness control display is completely useless. But these are minor issues. Impressively everything that I really depend on works great, and Ubuntu is the only OS I have on here.

---

### Post by avilella on 2009-04-13
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

If you have access to any of the laptops below and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

Sony Vaio Z-series (intel/nvidia)
Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
BenQ Joybook S42 (intel/nvidia)
ASUS N10J (intel/nvidia)
Dell Studio XPS 13 (nvidia/nvidia)
ASUS Intros G71Gx (?/nvidia GeForce 260M)
MSI GT628 (?/nvidia GeForce 160M)
LG Xnote P510 Laptop (?/nvidia GeForce GT 130M)
HP HDX 18t (?/nvidia GeForce GT 130M)
Dell XPS M1730 (nvidia/nvidia)
MSI EX630 (nvidia/nvidia -- )
Toshiba Qosmio X305-Q706/Q708 (nvidia/nvidia -- 9400m + 2x9800m GTS)
Acer Aspire 7530 (nvidia/nvidia -- 9100M G + GeForce 9300M GS)
ASUS X83Vm-X1 (?/nvidia)
+ Clevo M860TU (?/nvidia GeForce 9800M GTS)
+ Acer Aspire 8930G (?/nvidia GeForce 9700M GT)
+ Asus G50V (?/nvidia GeForce 9700M GT)
+ Zepto Mythos A15 (?/nvidia)
+ Asus M70VN (?/nvidia GeForce 9650M GT)
Lenovo ThinkPad T500 (intel/ati)
Lenovo ThinkPad T400 (intel/ati)
ASUS M51Ta (intel/ati)
Fujitsu-Siemens Amilo Sa 3650 (intel/ati)
MSI PX211 12'' (intel/ati)
HP Pavilion tx2500 (intel/ati)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

### Post by franklynb on 2009-04-15
Apple 12" G4 Powerbook, running Gutsy.. It just works, including OpenGL acceleration.

--frankb

Desktop: HP X4000 P4-2800 x 2, 2gB rdram, ATI FireGL-X256, 7.10 <Gutsy>
Laptop, Daily Driver: Apple 12" Powerbook, 1.25gB SDRAM, 7.10 <Gutsy>

---

### Post by tom66 on 2009-04-15
Dell Studio 15 with ATI Mobility Radeon 3450 HD (requires proprietary fglrx). Everything works AFAIK.

---

### Post by ponchojuan on 2009-04-15
I'm also running a D630 but with A13 bios.  I had no trouble with ver.8.10 install.  WEP worked out of the box.  No problems yet.  The partitioning is always tricky, the partioner is terrible...I usually use another piece of software or manually through Gparted booted off the CD.

My Old Thinkpad 240 was another thing all together........

---

### Post by m3topaz on 2009-04-15
Dell Inspiron 6400 with Bluetooth and WiFI
It's really, seriously good

---

### Post by 0per4t0r on 2009-04-15
Ubuntu works fine on my laptop.

Using Compaq Presario CQ50 Notebook
Ubuntu 8.10 and Vista Home Premium Dual-boot
AMD Athlon X2 Dual-Core Processor
Nvidia Graphics
Built-in wifi

---

### Post by Statik on 2009-04-19
Installed Intrepid on two HP Pavillion laptops with AMD Turion 64, NVidia GO 7160 (I think thats the number) Graphics, Lightscribe DVD-RW. Everything works out of the box. Even the media keys are recognized . . . just not connected to any program.

One is a DV2310CA - 14.1" the other is a DV9005CA - 17"

I love these beautiful machines. Flawless installation process and work awesome. As a matter of fact, my experience with the DV2310CA is what convinced me to search for another DV series for my wife's PC. She gets the 17". :)

Statik

---

### Post by Carl Hamlin on 2009-04-19
Ubuntu has worked beautifully on my Acer Extensa 5620 through three upgrades now, and the only issue I've had (and still have) is that the microphone doesn't pickup.

---

### Post by lindis on 2009-04-19
i have  an fs 1425 laptop modell g , and it works just great,install was easy as pie,and all works just fine with compiz.
:D

---

### Post by WhiskyChris on 2009-04-19
I've got ubuntu (intrepid and now jaunty) installed on a Dell Inspiron 6400 and it mostly works fine. It does however complain and give bad performance with opengl stuff (I think) - opengl screensavers are slow, applications with any sort of opengl animation flicker etc. I believe the culprit is the Intel 945GM integrated graphics controller and I've not found any fixes yet (though I have found plently of similar problems on google/the forums which all have this or a similar chipset in common).

---

### Post by dmm1983 on 2009-04-19
Acer Travelmate 2410 series
Intel(R) Celeron(R) M processor         1.50GHz
2.GB DDR2 RAM 
15.4" wXGA Wide TFT LCD
DVD-R Burner
802.11b/g wireless LAN

USB PRODUCTS
Telstra Pre-Paid Wireless Broadband
Pinnacle PCTV Dual DVB-T Diversity Stick

---

### Post by teh603 on 2009-04-19
Acer Aspire One, with the obligatory card reader and sound issues.

---

### Post by alienchickenpie on 2009-05-08
I use an HP Pavilion 9750ej.
Wireless networking, Bluetooth and Ethernet worked perfectly out of the box.
The sound card works, but it's very messy when it comes to recognizing and respecting headphones.
The video card worked out of the box, but I added an official Nvidia driver to make everything as smooth as it should be.
The touchpad works, but needs some adjusting to make it less click-happy.
The touch buttons don't seem to work, except for the volume slider and mute button.
The touch buttons don't seem to work, except for mute and the volume bar. Amarok recognizes the rest when setting up keyboard shortcuts, but they don't work after that.

---

### Post by perpetualcacophany on 2009-05-08
I use a MacBook 4.1 and it works great with Ubuntu. I'm also in the process of making it work with a Gentoo install which is taking a bit more work, but it still isn't too hard. 

It's actually nice using Linux on a MacBook because any other owner can answer the question since they all have the same hardware configuration.

---

### Post by gerowen on 2009-05-08
Just thought I'd update this, I recently bought a new computer.  It's a Toshiba Satellite L355D with the following specs.  All of the hardware worked out of the box, to include the built-in webcam.  Only thing was I had to choose to use the proprietary video driver, it defaulted to the open source ATI driver.

Toshiba Satellite L355D-S7829
256 MB ATI Radeon 3100 Graphics
2.1 Ghz AMD Turion X2 64
4GB DDR2 RAM
Ubuntu 9.04 Jaunty 64 bit

---

### Post by tonsai on 2009-05-08
hp nc6320, works like a charm, apart from the buiilt in Texas Instruments card reader, this may help: [http://ubuntuforums.org/showthread.php?t=797031&referrerid=830476](http://ubuntuforums.org/showthread.php?t=797031&referrerid=830476)

---

### Post by Rackstar on 2009-05-08
Everything working on my Acer Aspire 9420.

Since 9.04 fully working bluetooth, which was impossible in the past. Great job!
Everything else always has worked out of the box.

Only the kill bluetooth/wireless buttons don't work, but that's ok.

---

### Post by will1911a1 on 2009-05-08
Running Arch on an Asus Eee PC 701 flawlessly.

---

### Post by pastalavista on 2009-05-08
Everything's working to my satisfaction. My graphics aren't as strong as they used to be with 3D rendering, but I never use that anyway.

Acer Aspire laptop - AMD Sempron 1.6Ghz - 1 GB Ram ATI Xpress 200M

---

### Post by markusf21 on 2009-05-08
I have a dell studio 1735. everything works except the fingerprint reader. not important to me, so I have not even tried to get it working

---

### Post by some_random_noob on 2009-05-08
Look up "ThinkPad SL500" on the forums here if you want a good mid-range laptop where it works out of the box with almost no problems. I've wrote about it already, and it's listed on the laptop testing team page.

---

### Post by wirepuller134 on 2009-05-08
IBM 2611(1400) yes that's the 300mhz one, Dell cpx.  Both with xircom wired ethernet, Cisco wireless, and zurotech analog capture card work flawlessly.  They both dual boot Windows 2k and Debian. Dell inspiron pp04pl (something like that), dual boots Windows XP and Ubuntu 8.04 with no problems at all. The inspiron uses the built in wired ethernet, with a Cisco wireless card, same analog capture card.

---

### Post by dimxanthis on 2009-05-10
I have a dual boot (vista-ubuntu) clevo m765tu (rebranded as turbo-x something) and I have constant problems with my nvidia 9300m gs (when I aply the nvidia drivers) since ubuntu 8.04 (I have no idea before that). No matter how many drivers I have changed-no matter how many times I asked for help both in greek and official forums-no matter the pain, I still work with VESA drivers. When I try to use the nvidia drivers the next button I shall push is the reset button and that's the standard procedure. Anything else works just fine.

(btw do you know that "clevo"(&#954;&#955;&#941;&#946;&#969;) means "to steal" in greek? As time goes by, more and more I tend to believe I was mugged by those clevo guys when I bought this machine)

If you happen to know the solution to my problem-except the obvious like:change computer or something- please pm me
 
Dimitris , Greece

---

### Post by starcannon on 2009-05-10
Works Perfectly:

Dell Inspiron | 5100
HP dv2600 w/Nvidia 8400m GS option
Dell 1420n w/Nvidia 8400m GS option
Dell Mini 9n
MSi Wind w/2gb and Intel 3495 Pro WiFi upgrades
Asus Eee 701 4g w/2gb RAM and 16gb SDHC MMC upgrades
Asus Eee 702 8g w/2gb RAM and 16gb SDHC MMC upgrades
Asus Eee 700 2g w/8gb SDHC MMC upgrade.

Works with issues:
Everex Cloudbook

---

### Post by rpwdh on 2009-05-10
"Linux (Jaunty) works completely with my laptop-I will post my hardware specifics" 

Compaq Presario V5000T (3 years old)

Intel Celeron M processor

2GB RAM

Intel integrated graphics

Broadcom Wireless

CD/DVD Writer

Everything works GREAT!

---

### Post by JC Cheloven on 2009-05-10
Jaunty 9.04 works ok in three popular mini-notebooks I've tried. I dropped a [brief report here]("http://ubuntuforums.org/showthread.php?t=1123926").

Note.- Recording from internal mic doesn't work in any case with jaunty. Only Dell mini 9 with the factory preinstalled hardy 8.04 LTS makes it to work.

---

### Post by edhayden on 2009-05-19
Wireless does not work on my HP dv5000 (dv5215us).  It has a Broadcom BCM4318 Modem [Airforce One 54g], 802.11g Wireless Controller (rev 02)).  I've looked at all of the posts on how to fix the problem but it's way over my head.

I've come to the conclusion that Linux is not for non DOS/Terminal folks.

Oh well, another PC to add to the pile in the basement as there is apparently no way to get the machine back to Windows.  Sigh.

---

### Post by Dragonbite on 2009-05-19
> **edhayden said:**
> Wireless does not work on my HP dv5000 (dv5215us).  It has a Broadcom BCM4318 Modem [Airforce One 54g], 802.11g Wireless Controller (rev 02)).  I've looked at all of the posts on how to fix the problem but it's way over my head.

I've come to the conclusion that Linux is not for non DOS/Terminal folks.

Oh well, another PC to add to the pile in the basement as there is apparently no way to get the machine back to Windows.  Sigh.

You're giving up on a laptop because you cannot get wireless working?  There is a good thread in the forums for getting Broadcomm working and my Dell D400 has a Broadcomm wireless card.

Also, not all distributions are created equal and neither is their documentation. Look around Fedora and openSUSE. There are times when one will install completely and others will not on systems (plus that changes from version to version).

---

### Post by edhayden on 2009-05-19
I had posted a comment regarding difficulty getting the wireless card in my HP Pavilion dv5000 to work.  I found that by connecting with an ethernet cable and running the hardware tool in Ubuntu 9.04 it found the software I needed and installed it with no pain.

---

### Post by MGaddict2000 on 2009-05-19
You have a few options, 2 are listed directly under your link. If you really want to get it back to windows, you have two routs...

1) If you have you original restore disks, boot to a live CD such as those that came with Ubuntu, turn off swap (a quick search will show you how to do this) delete your partitions and then use your restore disk.

2) IF you have a full windows CD you'll need to wipe the disk first. I use Ultimate Boot CD. It's a bootable CD with loads of apps for formating, partitioning, and wiping out hard drives. There is a program called, Boot and Nuke. It will clear the hard drive back to a clean state with absolutely nothing on it. This will remove anything and everything on it. Back up all personal data before use. After running it, reinstall windows like it's a new computer.

One suggestion you received was to try connecting to without the wireless just use a lan cable. This is a good idea anytime you're installing and setting up a new OS because no install CD has drivers or configurations for every possible wireless card and just connecting a system to a lan while installing fixes most issues since it will go online and find anything it's missing.

Good luck, hope this helped. Just remember, Boot and Nuke wipes out everything on the Hard Drive and the program it's self will warn you about this a few times before it starts. There also may be other options, but I find these work the easiest for me.

Also, public notice, you should always run a wipe tool on a hard drive before getting rid of it. You have no idea how many computer's I've found which people threw out that had tons of personal data. DELETE doesn't get rid of anything.

---

### Post by archer6 on 2009-05-20
> **edhayden said:**
> Wireless does not work on my HP dv5000 (dv5215us).  It has a Broadcom BCM4318 Modem [Airforce One 54g], 802.11g Wireless Controller (rev 02)).  I've looked at all of the posts on how to fix the problem but it's way over my head.

I've come to the conclusion that Linux is not for non DOS/Terminal folks.

Oh well, another PC to add to the pile in the basement as there is apparently no way to get the machine back to Windows.  Sigh.
Linux is no different than Windows from one very important standpoint...

We first had to learn how to use Windows, and now if we want to use Linux we must do the same thing... learn how to use it. 

Windows should not be compared to Linux as they are completely different. If they were the same there would be little reason to use one over the other. 

Here's a link to a great article that puts one in the right frame of mind for working with Linux. 
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

If you read this, then ask for help here on the forum. You will find that your problem may be much easier to solve than you think at the present moment. 

I highly encourage you to be patient and give it a try, you've gone this far, why not get it up and running. Once you do, you will find how enjoyable and usable Ubuntu Linux is. I started with no clue about Linux and now I find it far better than Windows for 95% of what I use my computer for. The 5% remaining is on applications that are proprietary windows apps, and that's why I have a few dual boot ThinkPads, just for that purpose. If not for work I would use Ubuntu 100%, it's that good. 

Cheers...

---

### Post by richg on 2009-05-20
Just received my new Acer 5515 laptop that comes with Vista Basic. Got it off ebay for $325.00, free shipping. Still in original packing like the one my stepson bought from Walmart for $348, plus sales tax. 

In searching the 'Net for this laptop, I have been finding out some people are buying from their source and re-selling it on the 'Net or ebay.
The seller had good specs. I could have bid on it but chose "Buy It Now".
No, I did not need it. I wanted it.

The Acer box it came in looks like it came directly out of the "factory".

I am so remembering how difficult Windows can be. Been almost five years.
 
I have been running it on Live CD using wireless. Mint 6 & Mint 7 both like wireless. Not using it right now though. Will consider dual boot.
Still not sure if I want to keep Vista. In a way, I hate to throw something away that might prove useful at some time. WAG. Yes, I have wandered onto the dark side.

Cheers

Rich

---

### Post by pookiebear on 2009-05-20
Dell Latitude C610 (ebay special)
Fully working. Didn't have to load 1 driver.
PIII 1ghz
512 megs of Ram 
20 gb hard drive.
CD
Cisco aironet 350  pcmcia wireless card. (no wpa support in the card)

running xubuntu 9.04


Only thing I need is to speed up Firefox 3.... (will be searching for that answer next)

Install took about 20 minutes. 
Touchpad on the laptop is not working. But doesn't work with any OS I think it is dead. I use a cheap little old optical usb mouse.

oh yea first post!

---

### Post by djdarrin91 on 2009-05-20
I have a HP NC6000 and everything works fine out of the box:) bluetooth,wifi,etc..

---

### Post by utnubuuser on 2009-05-20
Thinkpad X31 1gb ram  --

---

### Post by Ceiber Boy on 2009-05-20
HP Pavilion ZE2000 NO CHANCE!

---

### Post by mamamia88 on 2009-05-20
dv9000 and mint 6 working great

---

### Post by starcannon on 2009-05-20
```
starcannon                
    description: Portable Computer
    product: Inspiron 910
    vendor: Dell Inc.
    version: A00
    serial: 951B6H1
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=portable cpus=1
  *-core
       description: Motherboard
       product: CN0J14
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: .951B6H1.ppppppppppppppd
       slot: &#65533;
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: A00 (08/05/2008)
          size: 100KiB
          capacity: 1984KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: U1
          size: 1600MHz
          capacity: 2048MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 4MiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: SODIMM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: M1
             size: 2GiB
             width: 32 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-system:0 UNCLAIMED
                description: System peripheral
                product: JMicron Technologies, Inc.
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-system:1
                description: SD Host controller
                product: JMicron Technologies, Inc.
                vendor: JMicron Technologies, Inc.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci latency=0 module=sdhci
           *-system:2
                description: System peripheral
                product: JMicron Technologies, Inc.
                vendor: JMicron Technologies, Inc.
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0 module=jmb38x_ms
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 00:23:08:1c:ec:ee
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.2.106 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:21:70:ca:4d:95
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: STEC PATA 16GB
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: C522
                serial: STM00004A47C
                size: 14GiB (15GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Windows FAT volume
                   vendor: Dell 8.0
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: 07d8-071d
                   size: 15EiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 3d9c6b1b-b040-49bf-ae72-b382cd31b5ea
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-16 23:40:12 filesystem=ext3 modified=2009-05-20 17:07:29 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2009-05-20 17:07:29 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       product: Dell
       vendor: Dell
       physical id: 1
       slot: Rear
       capacity: 22000mWh
       configuration: voltage=14.8V
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: sms
       serial: 00:53:49:41:4e:4f
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by mhpathfinder on 2009-05-20
HP L2005US Special Edition, Turion 64 1.6ghz, 2 gb RAM, 15.4 WXGA screen, 80Gb HDD, three USB2.0 and one SD card slot, ALSA sound, Synaptics Touchpad.  BroadCom BCM4328 wireless

Gateway E4100 Intel Pentium4 2.8ghz, 4gb RAM, ethernet, Vison 19-inch flat panel diaplay, NVidia 128 mg video. Intel onboard sound.

Gateway E2100 Intel Pentium4 2.8ghz, 2gb RAM, ethernet, Acer 19-inch flat panel display, NVidia 128 mg video.  Intel onboard sound.


Running Jaunty 9.04 smoothly on all three machines.   Had two post-install glitches on my HP Special Edition laptop.  Broadcom wasn't recognized or installed.  Had to reinstall Jaunty with wired ethernet connection, then Jaunty recognized, provided option for installing Broadcom proprietary drivers and activated.  OK.  Next, Synaptics touchpad--jumping cursor whenever typing, not related to palm contact with touchpad.  I added a line of code to one of the touchpad .conf files via a suggestion from another forum member.  Problem solved.

I have one more of our 5 home/business systems to de-Microsoft, when my wife feels brave enough to learn another operating system for her laptop.  Until that time, I have the Gateway E2100 set up with a full Jaunty system and copied all of her documents to it, so she could experience the joy for herself.

Amen.
MH Pathfinder

---

### Post by Mason Whitaker on 2009-05-20
Dell Inspiron 1525 Laptop

I swear, Ubuntu is the only distro that has completely worked "out of the box" on this machine! :D

---

### Post by Dragonbite on 2009-05-21
Quick update. Dell Latitude D400 with Ubuntu 9.04 Jaunty Jackalope works 99% out of the box.

Only caveat is the Broadcomm wireless card, which the Hardware Drivers fixed with just a couple of clicks.

Took me less than an hour and that includes bootup time.

It took me a night with Windows and it still wasn't perfect (and didn't include any software)!  Was a royal pain until I found the CD of drivers specific for this laptop and even then it had issues.

---

### Post by meganox on 2009-05-21
Advent 6001 with Intel bits.

Cannot burn CDs, can't find an answer why, very frustrated, not a total noob but don't know where to start with this and can't find anything but static on google or the forums, and no-one ever answers me on irc.

Bluetooth doesn't work, nothing shows up in lspci / lsmod / lsusb, don't know where to start with that either, not that I would use it much but I'd still like to have the option.

Haven't tried using the card reader but I know that shows up at least.

Pretty sure internal microphone doesn't work.

But not being able to burn CDs, that's just *so embarrasing*.  Help appreciated.

---

### Post by JC Cheloven on 2009-05-23
> **meganox said:**
> Advent 6001 with Intel bits.

Cannot burn CDs, can't find an answer why, very frustrated, not a total noob but don't know where to start with this and can't find anything but static on google or the forums, and no-one ever answers me on irc.

...

But not being able to burn CDs, that's just *so embarrasing*.  Help appreciated.
I had problems with brasero in the past. Solved using cd/dvd creator (you'll find it under the places menu, and also right clicking on a copy-able media). Or using k3b instead.

---

### Post by eerror on 2009-05-24
Toshiba Satellite L300D-044 is great.
AMD Athlon 64 X2, 4GB RAM, 250GB hd, ATI Radeon 3100, Atheros 9280 wireless.
9.04 detected all the hardware correctly.  Webcam and wireless worked right away.  Minor tweaking was required to get find the right settings for the microphone.
If you're not hungry for Compiz eyecandy then this laptop works just fine.  I say that because the ATI driver did cause me grief and I had to remove it.

Cheers everyone!

---

### Post by Zeronline on 2009-05-24
Everything works fine except my graphics drivers. Ever since I upgraded to 9.04, Jaunty Jackalope, my ATI drivers were removed and can no longer be installed.

The video card I've got on this laptop is an ATI Mobility Radeon X1600.

When I try to install the ATI drivers manually it spits back that the current version of XORG on the machine isn't supported as their drivers support up to xorg 1.7, and Jaunty currently has xorg 1.8 built into it (haha...).

I haven't really had too much problems with the builtin default gfx driver with Jaunty. It's the first ready-to-go GUI system where i didn't have to install 3rd party drivers to get compiz to work, but some minor graphic bugs are noticable.

---

### Post by Dragonbite on 2009-05-26
Is it me, or does Jaunty have some wireless issues? I keep loosing my connection and this is in places where I should be able to maintain the connection!

Ultimately I had to sit right next to the router to be connected (about 2 feet away = 90% strength?!)

---

### Post by Salamancero on 2009-06-19
I have satellite a100-s2211td running a celeron m 1.6ghz and express radeon x200M.  Everything seems to work except that after running for a few hours, sound starts stutters and takes forever to clear up.  A restart fixes that though. :)

---

### Post by royc on 2009-06-19
I have an old ThinkPad R31 running 8.04. My only problems are browser-based (Flash never works? Ruby-on Rails/AJAX sites barely/rarely work? No idea...). Other than that, it's perfect out-of-the-box.

I've been browsing this forum because I want to upgrade. I have a MacBook as well, and I want to convert it, but when I did a test run of the installation, my touchpad wasn't working. It spooked me. Is that okay? I mean does it work once it's installed?

---

### Post by defenestratos on 2009-06-21
-my benq joybook r23 doesn't have network on return from hibernate or suspend. Since Dapper. 
-Login window resolution is wrong and I can't fix it (Been with me since 8.01). 
-Since 8.01 Desktop resolution detected wrong and hz rate unadjustable(Stuck at 0hz, which is impossible)

I use it anyway because it is very fast and I can do everything anyway. Feel a bit dumb when logging in in front of friends and not seeing what I am typing but there you are.

---

### Post by uweklosa on 2009-06-21
I use a Thinkpad T42 and have no problems at all besides that it's getting old :)

Uwe

---

### Post by Screwdriver0815 on 2009-06-21
I have a Lenovo 3000 N200 with Nvidia graphics (there are also some of these machines with Intel GMA out in the wild).

It works nearly perfect. Just with Intrepid Ibex it has a flicker-bug of the graphics driver and the cardreader does not work without additional work.

In Jaunty it works out of the box - everything works, except two FN-Buttons: FN + F5 and FN + F7 and the fingerprint-reader. And it also doesn't have the flicker-bug anymore.

---

### Post by Bachstelze on 2009-06-21
> **uweklosa said:**
> I use a Thinkpad T42 and have no problems at all besides that it's getting old :)

Same thing with my Asus A6JM. There's a lot of stuff that I simply never use, so couldn't tell whether it's really working or not, though (suspend/hibernate, for example). So everything *I use* is working perfectly.

---

### Post by PaulClarke on 2009-07-05
Hello,

I have two Lenovo R61e s and they both work very well I have them dual booted with XP (Linux does not have a functional replacement to MS Project).  9.04 worked so well that I moved them from Fedora.

The main difference was that the video GLXGEARs for F11 was mid 400s and for Ubuntu was mid 700 for the two gb one and mid 1100s for the four gb.  The weak video performance is the only shortfall I have with thewse machines.

Ubuntu took about 1/8 of the time to set up compared to XP.

Well done

Paul

---

### Post by Pratt on 2009-07-06
Acer 8930g with no sound, but I think I have to learn more about Linux before I can do anything with it!  Any help offers for a complete beginner, please?

---

### Post by gjoellee on 2009-07-06
Linux works great on my computer, but when it comes to Linux distributions it is only Arch, PCLinuxOS and Ubuntu that just works.

---

### Post by AlexDudko on 2009-07-08
Old ASUS A9RPseries. Everything works (including wireless) except suspend and hibernate, though I don't use these functions.

---

### Post by Lateforgym on 2009-07-08
How well it worked with my laptop is what push me to Ubunu.

Dell Latitude. 

The only problem I had was getting You tube videos to work. This is a piss me off as non-laptops run into this also. 

I have loaded Ubuntu on 4 different computers all have sound problems with You tube. Its the first thing I do when loading Ubuntu to deal with you tube not working. FIX IT!

---

### Post by KegHead on 2009-07-08
works perfectly

KegHead

---

### Post by Dragonbite on 2009-07-08
> **Lateforgym said:**
> How well it worked with my laptop is what push me to Ubunu.

Dell Latitude. 

The only problem I had was getting You tube videos to work. This is a piss me off as non-laptops run into this also. 

I have loaded Ubuntu on 4 different computers all have sound problems with You tube. Its the first thing I do when loading Ubuntu to deal with you tube not working. FIX IT!

I have no problems with YouTube.

---

### Post by Kalex12 on 2009-07-08
A shiny new HP Elitebook 8730w Quad core, 320 gig 7200 rpm, with Nvidia Quadro FX 2700M, DVD burner, standard wireless and blue tooth, 4 gigs mem. I am very proud but my wallet is very light now.

Running 9.04 64 bit

I had to do a quick fix on the audio {single file edit, that is posted else where in this forum} works good now.

The single Biggest problem is the DVD drive. It functions fine after the system is booted up and running in both Ubuntu and XP. But I can no longer boot from this device in either XP or in Ubuntu, the BIOS no longer sees it on boot. I have checked the bios settings multiple times, to no avail. I have noticed this behavoir on other laptops {Lenovo N200 series} I do have external CD drives that I use when I need to boot via a CD or DVD {It recognizses usb boot drives just fine}.

The video required a download from Nvidia {would be nicer if that was a more seamless process} but it works fine after install. I am working now to configure dual monitors at work {a little more complicated to get it to do exactly what I wish.}

I have not configured the fingerprint reader yet, not sure if I will or not under Ubuntu. This machine is also a dual boot into XP and I am trying out the fingerprint reader there.

Wireless network and Bluetooth both worked with no problems.

Even the fancy touch sensitive options control bar is functioning which impressed me!

The card reader works fine.


One Sideline note: The only challahge I had during setup was adjusting partition sizes to install Unbuntu, I used the Ubuntu LIVE cd to do what I needed.

Ubuntu ROCKS!:guitar:

---

### Post by zerhacke on 2009-08-04
Generic IC Power laptop from Wal Mart about a year and a half ago.

Everything but the modem works which was broken on a kernel update.  The onboard RT2500 wireless works out of the box but I blacklisted rt2500pci so that I can use my PCMCIA Airforce One card with ndiswrapper.

---

### Post by OldGnome on 2009-08-06
I just installed Ubuntu 9.04 onto my Acer laptop. Everything seems to be working fine except:

- the monitor dims on an irregular schedule. I can immediately re-brighten the screen, but I haven't found the cure yet. I am also looking at a few other threads hereabouts discussing the same thing.

I am also having trouble with sound - however, I have spent the entire day using Sound Converter to convert my iTunes library, so I am going to wait before I call this a problem.

---

### Post by magmon on 2009-08-06
I have two laptops running linux, and they work (mostly). The only thing is the graphics card is ATI, and therefor not supported by (x)ubuntu 9.04, so I can't do 3D stuff.

---

### Post by BslBryan on 2009-08-06
HP DV6446us/2GHz AMD64 Turion Dual Core/2GB/nVidia GeForce 7150M/160GB/Ubuntu 8.04 32-bit

The Broadcom wireless chipset was very hard to configure, and the nVidia graphics card had some problems at first.  Also, the internal mic was a mess, as well as the built-in webcam.  The system sounds were hard to enable and caused me to lose a sound (login-ready "question" sound).  Now, however, it is a stunning example of what is possible with an Ubuntu install. :-)

---

### Post by sjelliott on 2009-08-06
Dell Mini 9, "out of the box" Mint installed on a USB pen drive run perfect complete with Compiz. Skype with working camera and microphone. Love to impress my friends who think I actually know something about computers.

---

### Post by stickystuff361 on 2009-08-06
Running Ubuntu 9.04 on an Dell Inspiron 1525 and as far as I know every-things working as it would on Windows Vista that it came with. Only problem being screen tearing with full-screen video not so sure about that.

---

### Post by DeadSuperHero on 2009-08-06
I have a Compaq Presario r3000 with an AMD 32-bit processor, 512 Mb of memory, and an Nvidia Go 440 or something like that. For my wireless, I use a Netgear WGv3 511 via ndiswrapper.

Ubuntu works very well on this crappy laptop, and KDE 4.2.9 ran admirably on it, but some more RAM would make it far more suited to KDE.

Eventually, it'd be nice to get a more powerful laptop. It's nice to have a laptop at all, though!

---

### Post by SamJosRob on 2009-08-06
As far as I know, the only thing that didn't work right away was the graphics card didn't work well. Downloaded the Nvidia driver and everything was set.

Another abnormality is a LED light that is blue when WiFi is on and orange when it is off. It worked that way in Windows. In Linux, when WiFi is on the light will flicker between blue and orange when wifi is on and either blue or orange solid when it is off. This doesn't bother me much because frankly I think it's groovy. :cool:

---

### Post by giggins on 2009-08-06
I use a Dell Latitude D820 here at work. Its a Centrino Duo (Intel Core 2 Duo), 2GB of RAM, 200GB 7200 RPM Hitatchi HDD, using a Dell dock. It has a nVidia GeForce Go 7400 (512MB), with both the laptop display and an HP LP2465 running at 1920x1200 each (3840x1200 pixels in TwinView for X Screen 0). Uses an Intel 802.11abg wifi card (works great with kismet). I am running Ubuntu 9.04 and have ZERO problems. All keyboard function keys work, suspend / hibernate / resume work great. VERY FAST. Runs great.

---

### Post by lukeiamyourfather on 2009-08-06
Lenovo ThinkPad X61 works with Ubuntu quite well. Only thing I've not got to work is the fingerprint reader. I'm sure there are ways of using it but haven't tried very hard. Cheers!

---

### Post by khelben1979 on 2009-08-07
Crashed harddrive on the powerbook. No more Linux on the laptop.

---

### Post by joelgsf on 2009-08-07
I have a DELL Vostro 1510 with Jaunty AMD64 installed. It works fine, except that I cannot use the full features of the Intel GM965/GL960 Graphics Controller, which seems to have no adequate driver for it available till now.

---

### Post by Nburnes on 2009-08-07
I have a Acer Extensa 5420-5038 with 9.10 Alpha 3 on it and everything is working fine.

ATI Radeon X1250 graphics even work better than in 9.04.

---

### Post by hobo14 on 2009-08-08
8.10 works great on my Toshiba Portege M500, didn't have to search for drivers online like I did for XP.

Fingerprint scanner doesn't work now, but haven't bothered trying to find a driver, because I never used it before anyway.

---

### Post by ryaxnb on 2009-08-08
in the past, linux has been iffy on my laptops. But i think that's resolved now, and my new EEE 901 proudly sports a fully-working linux install, except the webcam, which i haven't even seen if it works yet. :) Of course this machine was **designed** for linux, which is nice. I've had better and better luck on my other machines through the years. I'm pretty confident linux on laptops is now a mature and realistic proposition.

---

### Post by Liolikas on 2009-08-08
Dell C 400 Pentium III 866Mhz 512 RAM Intel 915 video (2.8.0 drivers work, 2.7.* and 2.6.* versions have some problems) Intel audio, Lucent wireless. blue tooth over USB: Everything work.

---

### Post by JDShu on 2009-08-08
Partially - Samsung q310 on 64 bit, 2.4 Ghz, Nvidia 9200 GS graphics card, 4gb ram

For the most part, its fine. However the brightness keys lock up the keyboard if pressed and apparently the computer doesn't like it when I have 4GB RAM as the acpi doesn't work unless I limit the memory in grub. Might be a problem with Samsung and not Linux though.

---

### Post by admiralspark on 2009-08-08
I'm using a Compaq Presario V5000 (v5005us) that's a few years old, and everything is working great now! Specs:
AMD Mobile Sempron 2.0ghz
ATI Radeon Xpress 200M
Broadcom 802.11 Wireless card (BCM 4318, worked after I used the guide on this site located in my sig)

Problems: wireless didn't work at first (common problem with that card). That's it, I think. Flash/Music/DVD playback etc all work. Games I haven't tested yet, but the ones I have should work no problem

---

### Post by Johii on 2009-08-09
Every thing I use on my laptop works 100% I'm not sure about the card reader and the GSM/modem, but i cant get that to work under windows so..

Laptop Dell Latitude D620 - core2 Duo with Nvidia gfx

---

### Post by dawnlove on 2009-08-09
I have 2 fully functioning laptops
 #1 eeepc 1000 with xubuntu 9.04
 #2 MSI x340 x-slim with 64g ssd hard drive upgrade
  with crunchbang 9.04
   maybe some hotkeys will need mapping ie: vol

---

### Post by Schendje on 2009-08-09
I voted partially but there's only small things that don't work.

There's a fingerprint reader which didn't work "straight-away" but it's working, just not configured to login. I really don't care enough about it to configure it. :)

There's also the brightness keys (Fn+f9/f10). Both of them don't work, but this is due to the Nvidia driver, I believe. Pressing them shows the brightness notification, but the screen just doesn't change. I've got a work-around though!

The rest of the computer works great!

My laptop is an HP 8510w. A fine piece of technology. :)

---

### Post by frt975 on 2009-08-09
My microphone doesn't work

---

### Post by J A Smith on 2009-08-09
Partially. Acer Aspire 5720z.

Intel x3100 Graphics Accelerator doesn't work, and I can't find a HOWTO or thread that has fixed it. 

Almost everything else works as far as I can tell, the function buttons (wireless etc.) don't work, but it's a minor issue. I tend not to use them anyway.

---

### Post by BigCityCat on 2009-08-09
I have an HP dv9700. Everything works but it took some effort to get there. Also a person from this website.... chili something, hooked up with me on messenger and helped me fix my wireless. There wasn't a lot of info on the problem and I probably would not have gotten it working myself. I still don't even know what he did. It had something to do with adding a wl to the end of a file and I think he blacklisted a b4 something or other. lol He was really smart. It had something to do with broadcom driver. I would love to see a tutorial in case I have to do it again, because I pre ordered windows seven and I am afraid installing it will wipe out my kubuntu install.

As far as it goes everything else works. Of course I had to install the restricted extras and I can't get rythmbox to work on Kubuntu but that's not much.

---

### Post by kazuya on 2009-08-09
asus X83vb - nvidia graphics dedicated card
Everything works great on this laptop.
bought it from best buy.

---

### Post by HermanAB on 2009-08-09
I haven't found a Dell that doesn't work with Linux.

---

### Post by sandy8925 on 2009-08-10
My laptop works well with Jaunty. It's a Fujitsu C1321. The specs are :

P4 1.73 Ghz , 533 Mhz FSB
512 MB DDR2 RAM , 533 Mhz
Intel 910/915 graphics card

All the hardware worked fine without any problems including wifi. I think I might have had a problem with sound but don't remember.

I've got to mention that some of the desktop effects don't work smoothly (seeing as how it's an Intel graphics card and an old one at that). Actually the only thing that doesn't work smoothly is the Desktop Wall effect (or whatever it is that happens when you press windows + E )

---

### Post by pootle1 on 2009-08-10
Got an Acer Aspire 6930G in May.  After a lot of troubles initially it now mostly works very well, only remaining issue now is WiFi performance is still rubbush - WiFi only works if I'm a couple of feet from the hub.

Graphics performance is good with the more recent nvidia drivers (originally installed the hard way, now available through envyng)

Sound took a bit of sorting out - but fetched more up to date alsa software and it all works well now (including the Tuba speaker which makes a big difference)

Have found that CF cards plugged into a Delkin expresscard adapter don't pick up unless I reboot although  SD cards plugged into the the slot in the front work fine.

esata port also works really well.

Haven't used the webcam or microphone.

---

### Post by markbuntu on 2009-08-11
Everything works on my aspire one running kuki linux with the new 2.6.30rc kernel.

Kuki is a jaunty remix aimed specifically at aspire ones. They are a very small group but are very focused and the result shines.

I think more of this sort of effort would be very beneficial for everyone and laptop/netbook users more specifically. UNR is good but I think they try to cover too much ground and so must make many compromises.

---

### Post by privatejarhead on 2009-08-16
Toshiba Satellite L505
intel pentium t4200 2.0ghz
3gb ram
320 gb hard drive
intel gma4500
insydeh20 BIOS (urgh...)
vista home (main os) with ubuntu 9.04 (wubi - 30gb)


Wireless worked perfectly OOTB! =). Strangely, it broke my vista wireless after i rebooted and when i fixed that, ubuntu's wireless went out. this cycle repeated for the next 2 days after i installed ubuntu, but even since it never happened again. strange......


linux mostly works with my laptop, but a few problems:


java will not work. tried sun's download, ubuntu-restricted-extras, and some other codes. my linux will not run it. (not too important for me though, i would just like to have it if i need)


youtube vids in full screen are choppy (still trying to fix.....it's bugging me alot since i like to watch tv shows on there, like good eats :))


>>i dont think it is really ubuntu's fault, but im not sure<<
ubuntu recognizes my hard drive (duh), but i cannot access my files from windows (docs, pics, etc). it will see the windows os and the drivers for it, but not the program files, users, etc. this really kills me :(


the fan has problems running at times. for example, if i boot into ubuntu from a dead start (ie the computer is cold/room temp and hasnt been used in an hour or so), the system detects that the temp, but wont update itself. thats just my guess, but the result is that my laptop will overheat, forcing me to quit what im doing and shut down asap so that i dont melt the core :lolflag:. now, if i restart the computer soon after while the system is still hot, the computer recognizes that its HOT and will spin the fan at 100%, but will keep doing so throughout the entire time the computer is turned on. i did a bit of research on this and from what i found, it's something to do with the BIOS. seeing that i have a little known BIOS (i wish i had phoenix!!!!), i dont see a way around this major problem.


thats about it for my problems with ubuntu for the 2-3 weeks ive owned this toshiba. i love ubuntu and linux in general and i want it on my computer(s), but for now i cant really do anything except toy around with it for about an hour or two at a time.

also, ive heard something about ubuntu giving shorter charge times than oem installs. my toshiba is rated at 2 hours 30 minutes give or take with vista. not sure if i suffer from the lack of linux battery efficiency, but i might test it out later.

---

### Post by cmay on 2009-08-16
my laptop is this one : [http://www.linuxshoppen.dk/products.php?showvariant_id=6787](http://www.linuxshoppen.dk/products.php?showvariant_id=6787)
i got it six month ago and everything works out of the box on jaunty . (9.04)

---

### Post by tacantara on 2009-08-16
Computer specs are in my signature

With a few minor tweaks I was able to get Ubuntu up and running nearly perfectly.  I ran Compiz-Check and discovered why I occasionally still have problems with the higher-end eye candy stuff.

```
 Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   KDE4
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz. 
```

I run both GNOME and KDE DE's.  I totally wrecked GNOME while trying to go extreme with the eye candy.  I switched back to KDE and use it's settings (rather than Compiz) for the cool stuff.  I still get the occasional "running to slow" message if I'm doing heavy-duty stuff, and compositing shuts down.  Not a deal breaker though.  I suppose I could upgrade the video card :-k

---

### Post by ZankerH on 2009-08-16
Yeah, I've got three laptops and they all work perfectly fine with GNU/Linux. I've got a Compal FL71 running Arch, an Eeepc 901 running eeebuntu, and an ancient IBM thinkpad (pentium 1, 128mb ram) running Damn Small Linux.

---

### Post by niteshifter on 2009-08-16
I cheated :) It's a 1420n from Dell. Original OS was 7.10. Everything worked. First kernel update broke sound, but fixed by rolling back sound driver (instruction on Dell's site).

Upgraded to 8.04.1 via Update Manager - everything still works. And no more driver rollbacks needed. Now 8.04.3 and still A-OK.

Wireless adpater is Intel 3945. Nvidia 8400M GS for video w/ 1440x900 panel.

---

### Post by Richard9795 on 2009-09-12
My Eee PC is working fine, its just when it boots, the screen turns off. when it finishes booting, the screen turns back on, and lets me log in. But other than that, everything works.

Ubuntu 9.04; xserver-xorg-video-intel 2.8.1; Kernel 2.6.31

---

### Post by RabbitWho on 2009-09-12
I have a
 Dell Inspiron 1545
intel pentium Dual Core processor 
intel integrated graphics card of some kind
4GB of ram

You can get it with almost any specs, and in some countries with Ubuntu, but not where I live. The default specs change every month. 

It works perfectly with Ubuntu, I haven't had a single problem (that wasn't related to my own inexperience.


However with Kubuntu I suffered nothing but crashes and graphics glitches. :sad:

---

### Post by NormanFLinux on 2009-09-12
No problems with my hardware. My Dell Mini 10's Poulsbo chip is not currently supported. Everything else on all my laptops work out of the box.

---

### Post by bodyharvester on 2009-09-12
never had an issue

dell mini 9
1.6GHz
2GB RAM (upgraded from 1GB)
Intel GMA 950 (graphics media accelerator)
8GB SSD (solid state drive)

500GB external HDD which also works fine although its still NTFS from my Windows days

vodafone mobile(cellular) broadband thing built in - detected instantly upon first boot!
Ubuntu 9.04 jaunty, first i had desktop edition but now the netbook edition with Gnome desktop

---

### Post by NormanFLinux on 2009-09-12
Winmodems are obsolete. All you need to connect on the road today is a wireless card and Linux can see the cards. The connection is more reliable and faster than with the old winmodems.

---

### Post by monkeyslayer56 on 2009-09-12
fully functional Toshiba satellite A15 laptop with intel celeron CPU and Toshiba integrated wifi. runs a little slow but thats do to hardware not ubuntu

---

### Post by misfitpierce on 2009-09-12
HP DV8315NR - Works 100%... ATI video card and AMD 64 Turion with remote and Broadcom wireless... Everything works 100% in Ubuntu Jaunty and worked in past 4 releases or so 100% fine.

---

### Post by chriskin on 2009-09-12
as of karmic, the Fujitsu Siemens Amilo Xi 2428 works perfectly
till Jaunty, sound and camera were problematic
in Jaunty, sound was fixed but not the camera
Karmic fixed the camera problem as well

---

### Post by Tamalin on 2009-09-12
Lenovo z60t: working flawlessly.
2GB RAM, 100GB HD

---

### Post by sgosnell on 2009-09-12
Asus EEE PC 900, Ubuntu 9.04, Linux 2.6.30 kernel.  Previous kernels didn't completely work, but the .30 version does.  As far as I can tell, everything works as well as the original Xandros, if not better.

---

### Post by Philip550c on 2009-09-14
I have the netbook Gateway lt3114u [http://www.bestbuy.com/site/olspage.jsp?skuId=9396824&type=product&id=1218099043959]("http://www.bestbuy.com/site/olspage.jsp?skuId=9396824&type=product&id=1218099043959").
Installation of the newest OS is a little annoying but Ubuntu 8.10 (Intrepid Ibex) 64bit installs very easily. After adding the backports the wifi works (switch and all). The camera works, everything works except the microphone but since I dont care I have not tried to fix it. The 3d card works and with the 64bit version it is much faster than vista which it came with (dual booting now). Its a nice little netbook since it has a ati card, amd 64, 250gb harddrive and 2 gb of ram. I recommend it to anyone looking for a little bit larger and more powerful linux netbook.

---

### Post by Dragonbite on 2009-09-15
My issues, so far, I believe are hardware issues yet I managed to install Ubuntu 9.04 on a Thinkpad T40 and have wireless and such working out-of-the-box.

I haven't tried Suspend or Hibernate yet (partially related to hardware issues).

---

### Post by Random-Dude on 2009-09-15
Toshiba satellite 2410. Everything did work until I &quot;upgraded&quot; the nvidia driver. I uninstalled it & everything is fine now. The media player buttons on the front never worked on xp & they're fine now. I also had a black stripe down the right side of the screen with xp & the only way to get rid of it was to revert to sp2. The only time I've seen the black stripe on Ubuntu was when I was installed the nvidia driver. I've just realised from a completely unrelated conversation that the &quot;fn&quot; button doesn't seem do anything but I'd never noticed the button was there before so I'm not sure if it worked with xp or not. Overall I'm massively impressed with Ubuntu, before I installed it all I'd heard was that you have to be a computer expert to be able to use Linux. I've found the opposite is true, things that I had to play with in xp to get working &quot;just work&quot; with Ubuntu which I feel is proven by the fact that I've been using it for about 3 months & this is my 1st post in these forums.

---

### Post by keplerspeed on 2009-09-15
Eee PC 701SD. Everything works out of the box. Wireless, hotkeys, intel graphics. Standard 9.04, not UNR.

---

### Post by dmglouis on 2009-09-15
Toshiba A305-S6864. Almost everything works. The video card drivers (ATI Radeon HD3470) do not work for hi-def video being played from the computer, though online flash videos work well.

Also, the wireless card (Atheros AR928X) does not have a very robust driver. It drops connection constantly, especially when connected to a WPA network.

---

### Post by ChrT on 2009-09-15
Compal IFL91, all hardware recognised and working perfectly in Arch, Debian and Ubuntu
Eee pc 901, vanilla ubuntu and debian kernels don't support the wifi and bluetooth. Arch works perfectly, Eeebuntu works perfectly out of the box.

---

### Post by ve4cib on 2009-09-15
I've got two laptops...

**Toshiba Satellite A70**
Vote: Mostly-working (and been in that state since 5.04)

Specific Issues:

1- open-source ATI drivers (for the video card) aren't great; 3d apps (games, compiz) are choopy at best and unusable at worst.  The old proprietary ATI drivers (from Dapper-era) were solid though.  I'm sure with more tweaking and such I could make it better, but the machine's been largely reduced to "auxilliary server & general-purpose family machine" that I can't be bothered

2- SD card reader does not work.  I don't recall the manufacturer, but it's never, ever worked.  And last I checked the manufacturer does not make a Linux driver, and no one's bothered making an open-source one that I've found

3- CPU frequency scaling used to go from 400MHz all the way up to 3.5GHz.  A year back (give or take) something happened and now the slowest the CPU will go is about 1GHz.  Might be a hardware fault; nothing I've tried can give me my super-slow frequencies anymore.  This results in the machine running loud and hot, even when idle.  I've taken to simply killing X and using it as a CL-system most of the time just to keep the fan noise down.

All in all the A70 is a piece of crap computer I would never buy again.  But Ubuntu mostly works on it.


**HP Pavillion dv6000ca-series, 64-bit**
Vote: Works completely (and has been since about 7.04)

Not much to say other than everything (including the microphone, webcam, SD card reader, Broadcom wi-fi, and nVidia GPU all work as I would expect them to.  nVidia could maybe make better drivers, but I can play Urban Terror, D2X-XL, Dawn of War (w/ Wine), and run Compiz with no difficulties.  Might need to get more RAM though (1GB standard); Compiz + background/tray apps + Docky + assorted daemons can make it pretty sluggish to change apps sometimes.

---

### Post by acorey on 2009-09-15
I have an HP Pavilion Entertainment PC dv2000 laptop. I just loaded Ubuntu 9.04 Jaunty and I couldn't be happier. 

I tried 64 bit about three years ago and couldn't get wireless, video, or audio working properly. So I used the Feisty 32 bit instead. Even with that, I spent hours and hours, days really, of hair pulling and gnashing of teeth to get everything working properly.

I have some time on my hands (devils playground) and decided to bite the bullet with Jaunty. That was last night at about 7:30 pm. Being fully prepared to spend at least a couple of days fighting. To my great surprise, I had wireless working and most of the apps I use installed. Firefox had flash and plugins. By this morning I had Virtual Box installed and migrated my settings and drives over from my old /home backed up on a usb drive. It was WAY too easy. Amazing! Fully converted over to 64 bit and mostly pain free!

I really am amazed and glad to see Ubuntu has turned a corner. Windows and OsX at this point are not any easier to deal with IMO. At least for the medium to medium-advanced user. A beginner would be boned anyway no matter what platform he/she uses. With Ubuntu/Linux, at least it's free and they stand to learn something useful.

Thank you Ubuntu, and Ubuntu community for doing such a great job on this release!

---

### Post by Firestem4 on 2009-09-15
I have a Dell XPS M1210 and everything works perfectly. I have never tried the bluetooth though so I can't say anything about that.

Running Kubuntu 9.04

---

### Post by balingupjer on 2009-09-18
All running well here, except a few custom buttons toshtools hasnt picked up.

Toshiba Portege M700 Core 2 duo 2.4 Ghz, 2 Gb Ram, Wacom 12" touchscreen (needed Wacom tools and setup rotate screen button, , SD Card Reader, Firewire (needed a bit of work in term) Webcam, Mic, onboard Wireless Broadband (sim card - have Vodaphone prepaid in Australia - needed to recompile for that Modem!!)

---

### Post by Zoot7 on 2009-09-18
My Dell XPS M1530 has ran like a champ with Ubuntu since day 1. 
First thing I did was boot up the Gutsy liveCD and wipe the Vista partition, didn't even boot into it once. :p

The only issues I ran into were nVidia related, but using a slightly older driver cleared that up for me.

---

### Post by bhishan on 2009-09-18
Dell Inspiron 1525
Everything works, except for the faulty Intel driver.

---

### Post by ronrut on 2009-09-18
HP Pavilion dv 9000.  Don't know about the IR port; never used it anyway.  Installed vendor drivers for Nvidia and wireless (b43).  Lost the use of the F11 key to boot into recovery for Vista, but grub automagically put a choice for that into its menu.

Ron

---

### Post by LostInHelix on 2009-09-19
Works MOSTLY. I have an acer Timeline 5810TZ laptop. Everything works, save for the Mic, Webcam, and HDMI output. Under Windows this laptop was advertised to get 8 hours, and did, actually a bit over with wireless off (on Windows 7 RC), and about 6 hours as I normally used it. Ubuntu, it lasts maybe 2 and a half or 3, still pretty good.

I have not yet looked into the problems I have, I never use the mic, and rarely the webcam so it's not necessarily important to me. The HDMI not working kinda sucks, but I need to look into it still :)

---

### Post by bikodog on 2009-09-19
Laptop 1 - Dell D830 - Puppy Linux installed to external USB drive (work pc)

Laptop 2 - Toshiba A65-S1762 - Xubuntu dual boot with wubi

---

### Post by Docaltmed on 2009-09-19
HP TX2500 (tablet PC). All the bells and whistles:

Automatic screen rotation? check
Compositing? check
Handwriting recognition? check
Networking? check
Video/audio? check (even Skype!)

This is a production computer, it is used all day, every day, in a busy clinic. It rocks!

Pen and touch were initially a PITA, and still are a bit, as I have to recompile the wacom driver every time a kernel update comes out. Other than that, frankly, I like Ubuntu handwriting recognition (Cellwriter) much better than the bloviated interface that came with Vista. 

And I will never ever never ever buy another computer with ATI graphics. The whole fglrx/radeon thing is a bit of a train wreck, mostly, as I understand it, because of ATI's recalcitrance. 

Kudos and humble thanks to some amazing participants on this forum (Favux comes to mind) who provided me with the insight and direction to get it all up to speed.

Even with the hiccups, I can safely say that moving to Linux was one of the best business decisions I have made.

---

### Post by gfxfreak on 2009-09-27
HP Compaq 6710b here

Everything works as expected, including fingerprint reader

---

### Post by raineater on 2009-09-29
HP Dv9005ca, AMD T64 running Jaunty.
 
 Issues - I've heard that most will be fixed with Karmic Koala...
  = syndaemon can't seem to find the touchpad
  = integral webcam - nothing works with it
  = multi-reader doesn't handle xD cards

 
That's about it.  I think the 32 bit version would solve the first two issues.

---

### Post by ssri on 2009-09-30
works partially/mostly:

HP Compaq 6910p:
Running Kubuntu Jaunty, KDE 4.3.1

audio: check (after ripping out the horrendous pulseaudio that came with medibuntu and reinstalling alsa)

video: check (after downgrading to xserver 1.5.2 and installing catalyst 9.3)

compositing: check (after installing compatible proprietary drivers for my card.  The opensource ati drivers that came with jaunty, or the ones checked out from git, had redraw bugs when moving menus around, unacceptable)

suspend/resume: nope (when the weather is right or when I'm feeling lucky.  Translation: a crapshoot)

freezing: every once in awhile when playing an audio file.  Again, this is unacceptable.

multimedia experience: horrific out of the box.  Installing mediabuntu was a snap, especially since I've done it before.  However, the rest was poor.  Amarok 2.x was just plain bad, so I had to install 1.4.10.  FLACs did not work with the xine engine due to a regression, so I had to downgrade it to intrepid's version.  MPlayer froze constantly, taking down X along with it until I installed a svn build from a ppa *sigh*

Hardware peripherals: Printer support has been excellent mainly due to the fact that my laboratory uses HP printers exclusively.

Office productivity: Fair, as openoffice replicated most of the functionality of MSOffice 2003.  However, when sharing documents from my research group who uses MSOffice 2007, Openoffice rendered data graphs incorrectly.  Thus, it disrupted collaborative projects.  Again, for my interests, this was unacceptable.  In addition, I had to resort to using foxit in wine in order to read and markup scientific papers due to lack of column recognition/support ([https://bugs.kde.org/show_bug.cgi?id=161324](https://bugs.kde.org/show_bug.cgi?id=161324)), a problem that is further exacerbated by the rude maintainer, and the fact that acrobat-gtk is extremely sluggish in a qt environment, duh.

---

### Post by X1R1 on 2009-09-30
At first the cd drive didnt work on my aspire 5810TZ, but after updating ubuntu just after I installed it it worked  great.

Only thing that does not work at all is the Crystal eye webcam, would be glad if someone could help me out with this.

---

### Post by zeroseven0183 on 2009-09-30
I'm using [HP Compaq nc6400]("http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html") with fingerprint sensor that does not work.

Any help will do.

---

### Post by icelord on 2009-10-28
Laptop1:
Lenovo S9, Atom270,2gb ram,160hdd,GMA950, intel 5350 wifi+wimax

Laptop2:
HP Mini 311, Atom270, 3Gb ram, 160hdd. Nvidia ION, 7G :) (Intel 5150 wifi+ 4G wimax + Sierra 3G mini pci-e modem)

all runs with Karmik, all works (except not-100% battery support at mini - can't read present discharge rate)

---

### Post by bkuhns on 2009-10-28
Dell Inspiron 1545. Works beautifully in Ubuntu 9.10 AMD-64. I've been stuck on a Compaq C300 laptop for the last 3 years that had ACPI issues that wouldn't allow Suspend to work. Now everything works great on my Inspiron without a hitch, I love it! :D

---

### Post by afeasfaerw23231233 on 2009-10-29
Hasee Fu417/F1600. There's no 3D driver for the integrated graphic processor Mirage 3+ (chipsets SiS M672). As far as I know SiS doesn't provide any linux drivers for their graphic products. I installed the 2D driver with the help of this forum.

---

### Post by Lord Stig on 2009-11-01
> **sergiom99 said:**
> I voted "Linux works completely with my laptop-I will post my hardware specifics" b/c, AFAIK, the only thing that's not working is the MS card reader, but there's no kernel support for them yet, so everything is ok.

Exactly the same for me.
Curious to know when there will be this support... ???

---

### Post by frprovis on 2009-11-01
Dell mini10v running Karmic 9.10.

Pulseaudio was causing all sorts of problems with Jaunty 9.04, but these appear to be completely fixed in 9.10.  And there are all sorts of other things that work better. I'm quite impressed. My original intention with Ubuntu was just to install it on a small partition and only use it for a few programs that weren't available on WinXP. But now that karmic is working so well, I changed my mind and put WinXP on the small partition and am going to use Ubuntu for most of my work. (Can't get rid of WinXP since I still have some apps that don't run under Wine.) 

Only problem was that the Broadcom 4322 driver (STA driver package) was not part of the .ISO download. So I couldn't use wireless until the hardwire drivers applet downloaded that package using a WIRED connection. In other words, it would be impossible (given my low level of linux expertise) to install Karmic using just a wireless connection. This is an issue for me since I might have to cancel my cable service to save money and hence my only connectivity will be wireless, unless I can find someone with a wired connection to borrow while doing my next upgrade.

---

### Post by Fife3951 on 2009-11-07
Problem free with Karmic on both HP Pavilion DV2500t and an HP Pavilion DV4-1143cl.

HP DV4-1143cl:
Intel Core 2 Duo T5800@2.0 GHz
4 gigs RAM
Mobile Intel 4 Series Express chipset


HP DV2500t:
Intel Core 2 Duo T7100@1.8GHz/2MB L2Cache
2 gig DDR2 RAM
NVidia graphics

I had sound issued which were both solved due to the sound auto-shutting off on the notebooks to save power.  Both are now flawless.

---

### Post by rapha on 2009-11-11
I voted "works fully" and I have a ThinkPad T61 with Intel graphics. TBH I don't really know about the fingerprint sensor as IMO stuff like that is the devil's right hand and have thus disabled it in the BIOS but read somewhere that it works if one wants to use it.

The really cool thing about this laptop is that you have *everything* working right out of the box. No driver installations, no nothing. Originally it had Vista Professional Edition on it which lasted about 3 hours after which my curiosity was satisfied and it was wiped off the harddrive. And boy, was the "Add/Remove Software" list full of things, including drivers. I'm pretty convinced no casual computer user would have been able to install Vista on this laptop without "expert" help.

(Ubuntu 9.04 up until two days ago and now 9.10 - both work like a charm)

---

### Post by beefjerkymonster on 2009-11-11
I'm using an Asus F50SV-X1, everything works perfectly!

There was one small issue I had with the wifi hardware. It worked out of the box, but with some connection issues, all I had to do to fix it was install some kernel module package (like backports or something), don't remember for sure what it was though.

But it's very relieving, because I couldn't find any Ubuntu users using this laptop when I bought it.

---

### Post by McMichael96 on 2009-11-11
Ubuntu works 100% my specs are 4GB RAM and Intel Dual-Core 2000 MHz Intel Integrated card

---

### Post by Nexus6 on 2009-11-11
I have a Lenovo R400 ThinkPad and so far so good. The only thing i wish was better is the battery savings, power management and stuff like that. 
When i ran the preinstalled windows the battery lasted much longer, so if someone have tip to fix that i would be glad.

---

### Post by mudguts on 2009-11-11
MDG (a.k.a Microstar INTL) Visionbook 17"
Dual-Core 1.66ghz
2GB ram
120GB SATA ii

9.10 works.
wireless worked out of the box
DVD player required some tweaking
DVD burner, haven't tested yet.
SUSPEND DOES NOT WORK!!!!

but it's certainly livable!

---

### Post by coldReactive on 2009-11-11
- ThinkPad T41 -
1.6 GHz Celeron Processor (Single Core Pentium M.)
512 MB RAM
ATI Mobility Radeon FireGL 9000 (No longer listed on the ATI Website)
40 GB HDD (ATA)
CD-RW/DVD Read Drive

----
Problems:

Flash can't run with full resolution at full screen. Have to set monitor to 1024x768 and use a webkit browser such as midori. DO NOT use Kubuntu, it won't work, the graphics glitch, etc.

Setting to 1024x768 causes the following problems:
-- HV Expansion Enabled: Dead Pixels form a 3 pixel width blue line that goes from top to bottom of the lcd on the right side.
-- Without HV Expansion: A thin line of dead pixels forms at the very bottom, 1 px in height and goes from left to right.

Function Keys (Most of them) Do not work at all.

Audio will not play out of the box in 9.10 (In 5.10 however, it will) to work around this, press the volume up button at the top of the keyboard, if this button fails and you have to reinstall, you will NEVER get audio to work in new releases.

May not be able to connect to any wireless networks that force certain authentication (IE: iMacs) (Need to be able to turn off IEEE Auth.)

None of these problems exist in windows of course, with the appropriate drivers.

---

### Post by ubuntu-freak on 2009-11-11
No problems here. My laptop is a Lenovo N500 3000, with an Intel X4500 GPU and Intel WiFi Link 5100 WNA.

---

### Post by nishant.singh28 on 2009-11-11
Studio 1555 : No problems at all-just a small change in the grub configuration  to enable brightness control keys but that's all...sound works out of the box, ATI propreitary driver is fine..

---

### Post by mwalimu54 on 2009-11-11
My only issue is (and has been from day one) suspend/hibernate.

---

### Post by 23dornot23d on 2009-11-11
I have a Acer Aspire Laptop 1355 LC ....... everything works great with Kanotix .... as my OS

I have a Acer Aspire Laptop 7730 ZG ....... evertyhing works great on UBUNTU 9.04 except sound 
which works fine once the latest ALSA conf is added and run ..... (webcam and mic are a problem)
but never use ...

---

### Post by subdivision on 2009-11-11
I run Arch on an Asus 701 EEE Pc (4G).

Everything works.

---

### Post by rapha on 2009-11-11
Hadn't thought of suspend/hibernate when I wrote my post ... that one is interesting indeed as I haven't owned a box to date (either desktop or laptop) where suspend/hibernate worked properly. I've pretty much considered this broken in Ubuntu ever since Warty Warthog, if anybody remembers the old fella :D ... actually to a point where I don't even bother checking if it works when a new release comes out. Usually after some weeks you'll press the button for it by accident and notice it's as broken as ever. Kinda sad though...

---

### Post by perspectoff on 2009-11-11
HP G60-440US

Using Kubuntu Karmic Koala 9.10.

Everything working perfectly:

Built-in Webcam/mic (with Skype 64-bit for Linux)
Wireless with Network Manager (autodetects connections and connects quickly)

All graphics
Power options

I love this laptop with Kubuntu! It came with 32-bit Windows Vista Home Premium (free upgrade to Windows 7), but the 64-bit Kubuntu flies in comparison!

Windows Vista SP2 still froze intermittently. 

Jaunty Jackalope's Network Manager didn't work so well with it, but since upgrading to Karmic, it's perfect!

---

### Post by samh785 on 2009-11-11
it works perfectly, but that's because it's a system76 Pangolin Performance (panp6)

---

### Post by Windows Nerd on 2009-11-11
Mine works perfect, albiet with some tweaks. Suspend/Hibernate: It hardly every has worked out of the box, but with some tweaks kindly given to me by a certain user, it works great now. Sound just worked, geven the problems some have. All the keys work, and everything but my built-in card reader works (which apparently is yet to be supported by Ubuntu, but this is not a bother as I never have to use the reader anyways). That and bluetooth, which it apparently has (it has a manual for it and a hardware switch for it) but it never worked even back when I used Windows the day I got my laptop. I understand that the bluetooth not working is a hardware fault, as the display LED does not turn on when I try to turn bluetooth on, as compared to it being Linux's problem.

If anyone wants to know how I fixed suspend/hibernate, I made a guide [here]("http://ubuntuforums.org/showthread.php?t=1242156").

Scott

---

### Post by loudog23 on 2009-11-11
Fully Working :P
Toshibe Tecra 8100
600mhz, 512mb ram.
Ubuntu Server 9.04 + Gnome & some stuff to make it look good. (using less than 100mb ram :D )
pcmcia card for wireless connection using wicd
usb port functional

I don't recommend it to people with recent computer since this istall might be lacking hardware support for recent technoligies. but here is my HOWTO: Minimal install + Gnome core + wicd :[http://ubuntuforums.org/showthread.php?t=1281934](http://ubuntuforums.org/showthread.php?t=1281934)

---

### Post by ventper on 2009-11-11
compaq presario v5208TU, 
intel mobile 945GM/PM/GMS 943/940GML
        celeron M 410 @1.46GHz, 1.24G ram
        Broadcom BCM94311MCG wlan mini-PCI (rev 01)
        #! 9.04(solid!) and karmic kubu

---

### Post by slakkie on 2009-11-11
```

eniac                                               
    description: Portable Computer                  
    product: Latitude D630                          
    vendor: Dell Inc.                               
    serial: 7Y3204J                                 
    width: 32 bits                                  
    capabilities: smbios-2.4 dmi-2.4                
    configuration: boot=normal chassis=portable uuid=44454C4C-5900-1033-8032-B7C04F30344A
  *-core                                                                                 
       description: Motherboard                                                          
       product: 0KU184                                                                   
       vendor: Dell Inc.                                                                 
       physical id: 0                                                                    
       serial: .7Y3204J.CN1296187ECBF9.                                                  
     *-firmware                                                                          
          description: BIOS                                                              
          vendor: Dell Inc.                                                              
          physical id: 0                                                                 
          version: A13 (07/28/2008)                                                      
          size: 64KiB                                                                    
          capacity: 1984KiB                                                              
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot                                                                                                                                                
     *-cpu                                                                                                                                                                         
          description: CPU                                                                                                                                                         
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz                                                                                                                 
          vendor: Intel Corp.                                                                                                                                                      
          physical id: 400                                                                                                                                                         
          bus info: cpu@0                                                                                                                                                          
          version: 6.15.13                                                                                                                                                         
          serial: 0000-06FD-0000-0000-0000-0000                                                                                                                                    
          slot: Microprocessor                                                                                                                                                     
          size: 2001MHz                                                                                                                                                            
          capacity: 2001MHz                                                                                                                                                        
          width: 64 bits                                                                                                                                                           
          clock: 200MHz                                                                                                                                                            
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq                                      
          configuration: id=1                                                                                                                                                      
        *-cache:0                                                                                                                                                                  
             description: L1 cache                                                                                                                                                 
             physical id: 700                                                                                                                                                      
             size: 32KiB                                                                                                                                                           
             capacity: 32KiB                                                                                                                                                       
             capabilities: internal write-back data                                                                                                                                
        *-cache:1                                                                                                                                                                  
             description: L2 cache                                                                                                                                                 
             physical id: 701                                                                                                                                                      
             size: 2MiB                                                                                                                                                            
             capacity: 2MiB                                                                                                                                                        
             clock: 66MHz (15.0ns)                                                                                                                                                 
             capabilities: pipeline-burst internal varies unified                                                                                                                  
        *-logicalcpu:0                                                                                                                                                             
             description: Logical CPU                                                                                                                                              
             physical id: 1.1                                                                                                                                                      
             width: 64 bits                                                                                                                                                        
             capabilities: logical                                                                                                                                                 
        *-logicalcpu:1                                                                                                                                                             
             description: Logical CPU                                                                                                                                              
             physical id: 1.2                                                                                                                                                      
             width: 64 bits                                                                                                                                                        
             capabilities: logical                                                                                                                                                 
     *-memory                                                                                                                                                                      
          description: System Memory                                                                                                                                               
          physical id: 1000                                                                                                                                                        
          slot: System board or motherboard                                                                                                                                        
          size: 1GiB                                                                                                                                                               
        *-bank:0                                                                                                                                                                   
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)                                                                                                                    
             product: HYMP112S64CP6-S6                                                                                                                                             
             vendor: AD00000000000000                                                                                                                                              
             physical id: 0                                                                                                                                                        
             serial: 02008032                                                                                                                                                      
             slot: DIMM_A                                                                                                                                                          
             size: 1GiB                                                                                                                                                            
             width: 64 bits                                                                                                                                                        
             clock: 667MHz (1.5ns)                                                                                                                                                 
        *-bank:1                                                                                                                                                                   
             description: DIMM DDR Synchronous [empty]                                                                                                                             
             physical id: 1                                                                                                                                                        
             slot: DIMM_B                                                                                                                                                          
             width: 64 bits                                                                                                                                                        
     *-pci                                                                                                                                                                         
          description: Host bridge                                                                                                                                                 
          product: Mobile PM965/GM965/GL960 Memory Controller Hub                                                                                                                  
          vendor: Intel Corporation                                                                                                                                                
          physical id: 100                                                                                                                                                         
          bus info: pci@0000:00:00.0                                                                                                                                               
          version: 0c                                                                                                                                                              
          width: 32 bits                                                                                                                                                           
          clock: 33MHz                                                                                                                                                             
          configuration: driver=agpgart-intel                                                                                                                                      
          resources: irq:0                                                                                                                                                         
        *-display:0                                                                                                                                                                
             description: VGA compatible controller                                                                                                                                
             product: Mobile GM965/GL960 Integrated Graphics Controller                                                                                                            
             vendor: Intel Corporation                                                                                                                                             
             physical id: 2                                                                                                                                                        
             bus info: pci@0000:00:02.0                                                                                                                                            
             version: 0c                                                                                                                                                           
             width: 64 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: msi pm bus_master cap_list rom                                                                                                                          
             configuration: driver=i915 latency=0                                                                                                                                  
             resources: irq:27 memory:f6e00000-f6efffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)                                                                 
        *-display:1 UNCLAIMED                                                                                                                                                      
             description: Display controller                                                                                                                                       
             product: Mobile GM965/GL960 Integrated Graphics Controller                                                                                                            
             vendor: Intel Corporation                                                                                                                                             
             physical id: 2.1                                                                                                                                                      
             bus info: pci@0000:00:02.1                                                                                                                                            
             version: 0c                                                                                                                                                           
             width: 64 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm bus_master cap_list                                                                                                                                  
             configuration: latency=0                                                                                                                                              
             resources: memory:f6f00000-f6ffffff                                                                                                                                   
        *-usb:0                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #4                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1a                                                                                                                                                       
             bus info: pci@0000:00:1a.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:20 ioport:6f20(size=32)                                                                                                                                
        *-usb:1                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #5                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1a.1                                                                                                                                                     
             bus info: pci@0000:00:1a.1                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:21 ioport:6f00(size=32)                                                                                                                                
        *-usb:2                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2                                                                                                                 
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1a.7                                                                                                                                                     
             bus info: pci@0000:00:1a.7                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm debug bus_master cap_list                                                                                                                            
             configuration: driver=ehci_hcd latency=0                                                                                                                              
             resources: irq:22 memory:fed1c400-fed1c7ff                                                                                                                            
        *-multimedia                                                                                                                                                               
             description: Audio device                                                                                                                                             
             product: 82801H (ICH8 Family) HD Audio Controller                                                                                                                     
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1b                                                                                                                                                       
             bus info: pci@0000:00:1b.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 64 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm msi pciexpress bus_master cap_list                                                                                                                   
             configuration: driver=HDA Intel latency=0                                                                                                                             
             resources: irq:21 memory:f6dfc000-f6dfffff                                                                                                                            
        *-pci:0                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801H (ICH8 Family) PCI Express Port 1                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1c                                                                                                                                                       
             bus info: pci@0000:00:1c.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                                                               
             configuration: driver=pcieport                                                                                                                                        
             resources: irq:24 ioport:2000(size=4096) memory:44000000-441fffff memory:44200000-443fffff(prefetchable)                                                              
        *-pci:1                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801H (ICH8 Family) PCI Express Port 2                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1c.1                                                                                                                                                     
             bus info: pci@0000:00:1c.1                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                                                               
             configuration: driver=pcieport                                                                                                                                        
             resources: irq:25 ioport:3000(size=4096) memory:f6c00000-f6cfffff memory:44400000-445fffff(prefetchable)                                                              
           *-network                                                                                                                                                               
                description: Wireless interface                                                                                                                                    
                product: PRO/Wireless 3945ABG [Golan] Network Connection                                                                                                           
                vendor: Intel Corporation                                                                                                                                          
                physical id: 0                                                                                                                                                     
                bus info: pci@0000:0c:00.0                                                                                                                                         
                logical name: wlan0                                                                                                                                                
                version: 02                                                                                                                                                        
                serial: 00:1f:3c:b1:66:62                                                                                                                                          
                width: 32 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                                                                                     
                configuration: broadcast=yes driver=iwl3945 ip=194.134.63.12 latency=0 multicast=yes wireless=IEEE 802.11abg                                                       
                resources: irq:28 memory:f6cff000-f6cfffff                                                                                                                         
        *-pci:2                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801H (ICH8 Family) PCI Express Port 6                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1c.5                                                                                                                                                     
             bus info: pci@0000:00:1c.5                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                                                               
             configuration: driver=pcieport                                                                                                                                        
             resources: irq:26 ioport:4000(size=4096) memory:f6b00000-f6bfffff memory:44600000-447fffff(prefetchable)                                                              
           *-network                                                                                                                                                               
                description: Ethernet interface                                                                                                                                    
                product: NetXtreme BCM5755M Gigabit Ethernet PCI Express                                                                                                           
                vendor: Broadcom Corporation                                                                                                                                       
                physical id: 0                                                                                                                                                     
                bus info: pci@0000:09:00.0                                                                                                                                         
                logical name: eth0                                                                                                                                                 
                version: 02                                                                                                                                                        
                serial: 00:21:70:a5:35:ef                                                                                                                                          
                size: 1GB/s                                                                                                                                                        
                capacity: 1GB/s                                                                                                                                                    
                width: 64 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                          
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5755m-v3.29 ip=194.134.32.189 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s                                                                                                                                                      
                resources: irq:29 memory:f6bf0000-f6bfffff                                                                                                                         
        *-usb:3                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #1                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d                                                                                                                                                       
             bus info: pci@0000:00:1d.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:20 ioport:6f80(size=32)                                                                                                                                
        *-usb:4                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #2                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d.1                                                                                                                                                     
             bus info: pci@0000:00:1d.1                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:21 ioport:6f60(size=32)                                                                                                                                
        *-usb:5                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #3                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d.2                                                                                                                                                     
             bus info: pci@0000:00:1d.2                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:22 ioport:6f40(size=32)                                                                                                                                
        *-usb:6                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1                                                                                                                 
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d.7                                                                                                                                                     
             bus info: pci@0000:00:1d.7                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm debug bus_master cap_list                                                                                                                            
             configuration: driver=ehci_hcd latency=0                                                                                                                              
             resources: irq:20 memory:fed1c000-fed1c3ff                                                                                                                            
        *-pci:3                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801 Mobile PCI Bridge                                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1e                                                                                                                                                       
             bus info: pci@0000:00:1e.0                                                                                                                                            
             version: f2                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci bus_master cap_list                                                                                                                                 
             resources: ioport:5000(size=4096) memory:f6a00000-f6afffff memory:40000000-43ffffff(prefetchable)                                                                     
           *-pcmcia                                                                                                                                                                
                description: CardBus bridge                                                                                                                                        
                product: Cardbus bridge                                                                                                                                            
                vendor: O2 Micro, Inc.                                                                                                                                             
                physical id: 1                                                                                                                                                     
                bus info: pci@0000:03:01.0                                                                                                                                         
                version: 21                                                                                                                                                        
                width: 32 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pcmcia bus_master cap_list                                                                                                                           
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192                                                                                            
                resources: irq:19 memory:f6a00000-f6a00fff ioport:5000(size=256) ioport:5400(size=256) memory:40000000-43ffffff(prefetchable) memory:48000000-4bffffff             
           *-firewire                                                                                                                                                              
                description: FireWire (IEEE 1394)                                                                                                                                  
                product: Firewire (IEEE 1394)                                                                                                                                      
                vendor: O2 Micro, Inc.                                                                                                                                             
                physical id: 1.4                                                                                                                                                   
                bus info: pci@0000:03:01.4                                                                                                                                         
                version: 02                                                                                                                                                        
                width: 32 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pm bus_master cap_list                                                                                                                               
                configuration: driver=ohci1394 latency=64                                                                                                                          
                resources: irq:19 memory:f6aff000-f6afffff memory:f6afe800-f6afefff                                                                                                
        *-isa                                                                                                                                                                      
             description: ISA bridge                                                                                                                                               
             product: 82801HEM (ICH8M) LPC Interface Controller                                                                                                                    
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1f                                                                                                                                                       
             bus info: pci@0000:00:1f.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: isa bus_master cap_list                                                                                                                                 
             configuration: latency=0                                                                                                                                              
        *-ide:0                                                                                                                                                                    
             description: IDE interface                                                                                                                                            
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1f.1                                                                                                                                                     
             bus info: pci@0000:00:1f.1                                                                                                                                            
             logical name: scsi0                                                                                                                                                   
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: ide bus_master emulated                                                                                                                                 
             configuration: driver=ata_piix latency=0                                                                                                                              
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)                                                                    
           *-cdrom                                                                                                                                                                 
                description: DVD reader                                                                                                                                            
                product: CDRW/DVD GCCT10N                                                                                                                                          
                vendor: HL-DT-ST                                                                                                                                                   
                physical id: 0.0.0                                                                                                                                                 
                bus info: scsi@0:0.0.0                                                                                                                                             
                logical name: /dev/cdrom                                                                                                                                           
                logical name: /dev/cdrw                                                                                                                                            
                logical name: /dev/dvd                                                                                                                                             
                logical name: /dev/scd0                                                                                                                                            
                logical name: /dev/sr0                                                                                                                                             
                version: A104                                                                                                                                                      
                capabilities: removable audio cd-r cd-rw dvd                                                                                                                       
                configuration: ansiversion=5 status=ready                                                                                                                          
              *-medium                                                                                                                                                             
                   physical id: 0                                                                                                                                                  
                   logical name: /dev/cdrom                                                                                                                                        
        *-ide:1                                                                                                                                                                    
             description: IDE interface                                                                                                                                            
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller                                                                                                             
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1f.2                                                                                                                                                     
             bus info: pci@0000:00:1f.2                                                                                                                                            
             logical name: scsi2                                                                                                                                                   
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 66MHz                                                                                                                                                          
             capabilities: ide pm bus_master cap_list emulated                                                                                                                     
             configuration: driver=ata_piix latency=0                                                                                                                              
             resources: irq:18 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=16) ioport:eff0(size=16)                           
           *-disk                                                                                                                                                                  
                description: ATA Disk                                                                                                                                              
                product: ST980310AS                                                                                                                                                
                vendor: Seagate                                                                                                                                                    
                physical id: 0.0.0                                                                                                                                                 
                bus info: scsi@2:0.0.0                                                                                                                                             
                logical name: /dev/sda                                                                                                                                             
                version: DE04                                                                                                                                                      
                serial: 5ST045RD                                                                                                                                                   
                size: 74GiB (80GB)                                                                                                                                                 
                capabilities: partitioned partitioned:dos                                                                                                                          
                configuration: ansiversion=5 signature=f6c5f6c5                                                                                                                    
              *-volume:0                                                                                                                                                           
                   description: EXT3 volume                                                                                                                                        
                   vendor: Linux                                                                                                                                                   
                   physical id: 1                                                                                                                                                  
                   bus info: scsi@2:0.0.0,1                                                                                                                                        
                   logical name: /dev/sda1                                                                                                                                         
                   version: 1.0                                                                                                                                                    
                   serial: e4510d0b-62e9-4f5b-9e2e-255c34a0c48f                                                                                                                    
                   size: 62MiB                                                                                                                                                     
                   capacity: 62MiB                                                                                                                                                 
                   capabilities: primary journaled extended_attributes ext3 ext2 initialized                                                                                       
                   configuration: created=2009-10-27 23:46:26 filesystem=ext3 label=grub modified=2009-11-11 23:23:25 mounted=2009-11-11 22:46:58 state=clean                      
              *-volume:1                                                                                                                                                           
                   description: EXT4 volume                                                                                                                                        
                   vendor: Linux                                                                                                                                                   
                   physical id: 2                                                                                                                                                  
                   bus info: scsi@2:0.0.0,2                                                                                                                                        
                   logical name: /dev/sda2                                                                                                                                         
                   logical name: /                                                                                                                                                 
                   version: 1.0                                                                                                                                                    
                   serial: ec8ce521-7f42-481b-981c-36357abf559c                                                                                                                    
                   size: 8001MiB                                                                                                                                                   
                   capacity: 8001MiB                                                                                                                                               
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                                      
                   configuration: created=2009-10-28 22:22:26 filesystem=ext4 lastmountpoint=/P7&#65533;&#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#329;&#65533;&#65533;>&#65533;&#65533;&#65533;M&#65533;G5&#65533;&#65533;-&#65533;&#65533;>&#65533;&#65533;!&#65533;&#65533;!&#65533;&#65533;}&#65533;&#65533;&#65533;>&#65533;&#65533;>&#65533;&#65533;uP modified=2009-11-10 18:03:00 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-11 23:24:06 state=mounted                                                          
              *-volume:2                                                                                                                                                           
                   description: EXT3 volume                                                                                                                                        
                   vendor: Linux                                                                                                                                                   
                   physical id: 3                                                                                                                                                  
                   bus info: scsi@2:0.0.0,3                                                                                                                                        
                   logical name: /dev/sda3                                                                                                                                         
                   version: 1.0                                                                                                                                                    
                   serial: fcdc06c1-729c-4991-817d-e7f94ce69dc6                                                                                                                    
                   size: 8001MiB                                                                                                                                                   
                   capacity: 8001MiB                                                                                                                                               
                   capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized                                                                           
                   configuration: created=2009-11-01 15:34:59 filesystem=ext3 modified=2009-11-11 23:23:25 mounted=2009-11-11 22:46:56 state=clean                                 
              *-volume:3                                                                                                                                                           
                   description: Extended partition                                                                                                                                 
                   physical id: 4                                                                                                                                                  
                   bus info: scsi@2:0.0.0,4                                                                                                                                        
                   logical name: /dev/sda4                                                                                                                                         
                   size: 58GiB                                                                                                                                                     
                   capacity: 58GiB                                                                                                                                                 
                   capabilities: primary extended partitioned partitioned:extended                                                                                                 
                 *-logicalvolume:0                                                                                                                                                 
                      description: Linux filesystem partition                                                                                                                      
                      physical id: 5                                                                                                                                               
                      logical name: /dev/sda5                                                                                                                                      
                      capacity: 8001MiB                                                                                                                                            
                      capabilities: bootable                                                                                                                                       
                 *-logicalvolume:1                                                                                                                                                 
                      description: Linux swap / Solaris partition                                                                                                                  
                      physical id: 6                                                                                                                                               
                      logical name: /dev/sda6                                                                                                                                      
                      capacity: 2000MiB                                                                                                                                            
                      capabilities: nofs                                                                                                                                           
                 *-logicalvolume:2                                                                                                                                                 
                      description: Linux filesystem partition                                                                                                                      
                      physical id: 7                                                                                                                                               
                      logical name: /dev/sda7                                                                                                                                      
                      logical name: /var/log                                                                                                                                       
                      capacity: 298MiB                                                                                                                                             
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /opt
                      capacity: 1498MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /home
                      capacity: 47GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6dfbf00-f6dfbfff ioport:10c0(size=32)
  *-battery
       product: DELL NT37789
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by recluce on 2009-11-12
I have a Dell Latitude D830 with the following specs:

2.2 GHz Core2 Duo
4 GB RAM
NVidia Quadro NVS 140 Graphics
Intel 3945 ABG WiFi
Toshiba Bluetooth
Dell D/Dock

Ubuntu 9.04 x64

Laptop is fully functional. Only the modem would require a commercial driver, which I didn't bother with - I haven't used the modem in more than a year anyway...

Beware if you have the Dell-branded Broadcom Wifi module. These may not work correctly under 64bit Ubuntu, but did work fine for me with the 32bit Dell Install DVD. Also, Intel chipset graphics might give you grieve under 9.04.

---

### Post by Ampi on 2009-11-12
Acer Aspire One ZG5

I posted "Linux works completely with my laptop-I will post my hardware specifics" though my built-in webcam doesn't work.

Because the laptop is second hand, the webcam never did work, and after all I've tried it looks like it's a hardware problem. So it's not the fault of linux most probably :).

---

### Post by Neezer on 2009-11-12
Well, I am mostly up and running, but I have an HP Pavilion dv6. I had sound problems to begin with (no sound), but now I have sound. The only problem that I have now is that my speakers on the laptop don't turn off when I plug in headphones.

I have a workaround going with alsamixer where I just turn the speaker volume to 0 when I plug in headphones, but it isn't working perfectly at the moment.

That is number 2 or 3 on my to do list.

Other than that everything worked great, including my wireless which I was worried about needlessly.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-11-12
Acer Aspire 5737Z

Everything works, except the internal card reader and the internal microphone

---

### Post by Windows Nerd on 2009-11-12
> **slakkie said:**
> ```

eniac                                               
    description: Portable Computer                  
    product: Latitude D630                          
    vendor: Dell Inc.                               
    serial: 7Y3204J                                 
    width: 32 bits                                  
    capabilities: smbios-2.4 dmi-2.4                
    configuration: boot=normal chassis=portable uuid=44454C4C-5900-1033-8032-B7C04F30344A
  *-core                                                                                 
       description: Motherboard                                                          
       product: 0KU184                                                                   
       vendor: Dell Inc.                                                                 
       physical id: 0                                                                    
       serial: .7Y3204J.CN1296187ECBF9.                                                  
     *-firmware                                                                          
          description: BIOS                                                              
          vendor: Dell Inc.                                                              
          physical id: 0                                                                 
          version: A13 (07/28/2008)                                                      
          size: 64KiB                                                                    
          capacity: 1984KiB                                                              
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot                                                                                                                                                
     *-cpu                                                                                                                                                                         
          description: CPU                                                                                                                                                         
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz                                                                                                                 
          vendor: Intel Corp.                                                                                                                                                      
          physical id: 400                                                                                                                                                         
          bus info: cpu@0                                                                                                                                                          
          version: 6.15.13                                                                                                                                                         
          serial: 0000-06FD-0000-0000-0000-0000                                                                                                                                    
          slot: Microprocessor                                                                                                                                                     
          size: 2001MHz                                                                                                                                                            
          capacity: 2001MHz                                                                                                                                                        
          width: 64 bits                                                                                                                                                           
          clock: 200MHz                                                                                                                                                            
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq                                      
          configuration: id=1                                                                                                                                                      
        *-cache:0                                                                                                                                                                  
             description: L1 cache                                                                                                                                                 
             physical id: 700                                                                                                                                                      
             size: 32KiB                                                                                                                                                           
             capacity: 32KiB                                                                                                                                                       
             capabilities: internal write-back data                                                                                                                                
        *-cache:1                                                                                                                                                                  
             description: L2 cache                                                                                                                                                 
             physical id: 701                                                                                                                                                      
             size: 2MiB                                                                                                                                                            
             capacity: 2MiB                                                                                                                                                        
             clock: 66MHz (15.0ns)                                                                                                                                                 
             capabilities: pipeline-burst internal varies unified                                                                                                                  
        *-logicalcpu:0                                                                                                                                                             
             description: Logical CPU                                                                                                                                              
             physical id: 1.1                                                                                                                                                      
             width: 64 bits                                                                                                                                                        
             capabilities: logical                                                                                                                                                 
        *-logicalcpu:1                                                                                                                                                             
             description: Logical CPU                                                                                                                                              
             physical id: 1.2                                                                                                                                                      
             width: 64 bits                                                                                                                                                        
             capabilities: logical                                                                                                                                                 
     *-memory                                                                                                                                                                      
          description: System Memory                                                                                                                                               
          physical id: 1000                                                                                                                                                        
          slot: System board or motherboard                                                                                                                                        
          size: 1GiB                                                                                                                                                               
        *-bank:0                                                                                                                                                                   
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)                                                                                                                    
             product: HYMP112S64CP6-S6                                                                                                                                             
             vendor: AD00000000000000                                                                                                                                              
             physical id: 0                                                                                                                                                        
             serial: 02008032                                                                                                                                                      
             slot: DIMM_A                                                                                                                                                          
             size: 1GiB                                                                                                                                                            
             width: 64 bits                                                                                                                                                        
             clock: 667MHz (1.5ns)                                                                                                                                                 
        *-bank:1                                                                                                                                                                   
             description: DIMM DDR Synchronous [empty]                                                                                                                             
             physical id: 1                                                                                                                                                        
             slot: DIMM_B                                                                                                                                                          
             width: 64 bits                                                                                                                                                        
     *-pci                                                                                                                                                                         
          description: Host bridge                                                                                                                                                 
          product: Mobile PM965/GM965/GL960 Memory Controller Hub                                                                                                                  
          vendor: Intel Corporation                                                                                                                                                
          physical id: 100                                                                                                                                                         
          bus info: pci@0000:00:00.0                                                                                                                                               
          version: 0c                                                                                                                                                              
          width: 32 bits                                                                                                                                                           
          clock: 33MHz                                                                                                                                                             
          configuration: driver=agpgart-intel                                                                                                                                      
          resources: irq:0                                                                                                                                                         
        *-display:0                                                                                                                                                                
             description: VGA compatible controller                                                                                                                                
             product: Mobile GM965/GL960 Integrated Graphics Controller                                                                                                            
             vendor: Intel Corporation                                                                                                                                             
             physical id: 2                                                                                                                                                        
             bus info: pci@0000:00:02.0                                                                                                                                            
             version: 0c                                                                                                                                                           
             width: 64 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: msi pm bus_master cap_list rom                                                                                                                          
             configuration: driver=i915 latency=0                                                                                                                                  
             resources: irq:27 memory:f6e00000-f6efffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)                                                                 
        *-display:1 UNCLAIMED                                                                                                                                                      
             description: Display controller                                                                                                                                       
             product: Mobile GM965/GL960 Integrated Graphics Controller                                                                                                            
             vendor: Intel Corporation                                                                                                                                             
             physical id: 2.1                                                                                                                                                      
             bus info: pci@0000:00:02.1                                                                                                                                            
             version: 0c                                                                                                                                                           
             width: 64 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm bus_master cap_list                                                                                                                                  
             configuration: latency=0                                                                                                                                              
             resources: memory:f6f00000-f6ffffff                                                                                                                                   
        *-usb:0                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #4                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1a                                                                                                                                                       
             bus info: pci@0000:00:1a.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:20 ioport:6f20(size=32)                                                                                                                                
        *-usb:1                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #5                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1a.1                                                                                                                                                     
             bus info: pci@0000:00:1a.1                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:21 ioport:6f00(size=32)                                                                                                                                
        *-usb:2                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2                                                                                                                 
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1a.7                                                                                                                                                     
             bus info: pci@0000:00:1a.7                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm debug bus_master cap_list                                                                                                                            
             configuration: driver=ehci_hcd latency=0                                                                                                                              
             resources: irq:22 memory:fed1c400-fed1c7ff                                                                                                                            
        *-multimedia                                                                                                                                                               
             description: Audio device                                                                                                                                             
             product: 82801H (ICH8 Family) HD Audio Controller                                                                                                                     
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1b                                                                                                                                                       
             bus info: pci@0000:00:1b.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 64 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm msi pciexpress bus_master cap_list                                                                                                                   
             configuration: driver=HDA Intel latency=0                                                                                                                             
             resources: irq:21 memory:f6dfc000-f6dfffff                                                                                                                            
        *-pci:0                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801H (ICH8 Family) PCI Express Port 1                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1c                                                                                                                                                       
             bus info: pci@0000:00:1c.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                                                               
             configuration: driver=pcieport                                                                                                                                        
             resources: irq:24 ioport:2000(size=4096) memory:44000000-441fffff memory:44200000-443fffff(prefetchable)                                                              
        *-pci:1                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801H (ICH8 Family) PCI Express Port 2                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1c.1                                                                                                                                                     
             bus info: pci@0000:00:1c.1                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                                                               
             configuration: driver=pcieport                                                                                                                                        
             resources: irq:25 ioport:3000(size=4096) memory:f6c00000-f6cfffff memory:44400000-445fffff(prefetchable)                                                              
           *-network                                                                                                                                                               
                description: Wireless interface                                                                                                                                    
                product: PRO/Wireless 3945ABG [Golan] Network Connection                                                                                                           
                vendor: Intel Corporation                                                                                                                                          
                physical id: 0                                                                                                                                                     
                bus info: pci@0000:0c:00.0                                                                                                                                         
                logical name: wlan0                                                                                                                                                
                version: 02                                                                                                                                                        
                serial: 00:1f:3c:b1:66:62                                                                                                                                          
                width: 32 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                                                                                     
                configuration: broadcast=yes driver=iwl3945 ip=194.134.63.12 latency=0 multicast=yes wireless=IEEE 802.11abg                                                       
                resources: irq:28 memory:f6cff000-f6cfffff                                                                                                                         
        *-pci:2                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801H (ICH8 Family) PCI Express Port 6                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1c.5                                                                                                                                                     
             bus info: pci@0000:00:1c.5                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                                                               
             configuration: driver=pcieport                                                                                                                                        
             resources: irq:26 ioport:4000(size=4096) memory:f6b00000-f6bfffff memory:44600000-447fffff(prefetchable)                                                              
           *-network                                                                                                                                                               
                description: Ethernet interface                                                                                                                                    
                product: NetXtreme BCM5755M Gigabit Ethernet PCI Express                                                                                                           
                vendor: Broadcom Corporation                                                                                                                                       
                physical id: 0                                                                                                                                                     
                bus info: pci@0000:09:00.0                                                                                                                                         
                logical name: eth0                                                                                                                                                 
                version: 02                                                                                                                                                        
                serial: 00:21:70:a5:35:ef                                                                                                                                          
                size: 1GB/s                                                                                                                                                        
                capacity: 1GB/s                                                                                                                                                    
                width: 64 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                          
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5755m-v3.29 ip=194.134.32.189 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s                                                                                                                                                      
                resources: irq:29 memory:f6bf0000-f6bfffff                                                                                                                         
        *-usb:3                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #1                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d                                                                                                                                                       
             bus info: pci@0000:00:1d.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:20 ioport:6f80(size=32)                                                                                                                                
        *-usb:4                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #2                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d.1                                                                                                                                                     
             bus info: pci@0000:00:1d.1                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:21 ioport:6f60(size=32)                                                                                                                                
        *-usb:5                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB UHCI Controller #3                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d.2                                                                                                                                                     
             bus info: pci@0000:00:1d.2                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: bus_master                                                                                                                                              
             configuration: driver=uhci_hcd latency=0                                                                                                                              
             resources: irq:22 ioport:6f40(size=32)                                                                                                                                
        *-usb:6                                                                                                                                                                    
             description: USB Controller                                                                                                                                           
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1                                                                                                                 
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1d.7                                                                                                                                                     
             bus info: pci@0000:00:1d.7                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pm debug bus_master cap_list                                                                                                                            
             configuration: driver=ehci_hcd latency=0                                                                                                                              
             resources: irq:20 memory:fed1c000-fed1c3ff                                                                                                                            
        *-pci:3                                                                                                                                                                    
             description: PCI bridge                                                                                                                                               
             product: 82801 Mobile PCI Bridge                                                                                                                                      
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1e                                                                                                                                                       
             bus info: pci@0000:00:1e.0                                                                                                                                            
             version: f2                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: pci bus_master cap_list                                                                                                                                 
             resources: ioport:5000(size=4096) memory:f6a00000-f6afffff memory:40000000-43ffffff(prefetchable)                                                                     
           *-pcmcia                                                                                                                                                                
                description: CardBus bridge                                                                                                                                        
                product: Cardbus bridge                                                                                                                                            
                vendor: O2 Micro, Inc.                                                                                                                                             
                physical id: 1                                                                                                                                                     
                bus info: pci@0000:03:01.0                                                                                                                                         
                version: 21                                                                                                                                                        
                width: 32 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pcmcia bus_master cap_list                                                                                                                           
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192                                                                                            
                resources: irq:19 memory:f6a00000-f6a00fff ioport:5000(size=256) ioport:5400(size=256) memory:40000000-43ffffff(prefetchable) memory:48000000-4bffffff             
           *-firewire                                                                                                                                                              
                description: FireWire (IEEE 1394)                                                                                                                                  
                product: Firewire (IEEE 1394)                                                                                                                                      
                vendor: O2 Micro, Inc.                                                                                                                                             
                physical id: 1.4                                                                                                                                                   
                bus info: pci@0000:03:01.4                                                                                                                                         
                version: 02                                                                                                                                                        
                width: 32 bits                                                                                                                                                     
                clock: 33MHz                                                                                                                                                       
                capabilities: pm bus_master cap_list                                                                                                                               
                configuration: driver=ohci1394 latency=64                                                                                                                          
                resources: irq:19 memory:f6aff000-f6afffff memory:f6afe800-f6afefff                                                                                                
        *-isa                                                                                                                                                                      
             description: ISA bridge                                                                                                                                               
             product: 82801HEM (ICH8M) LPC Interface Controller                                                                                                                    
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1f                                                                                                                                                       
             bus info: pci@0000:00:1f.0                                                                                                                                            
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: isa bus_master cap_list                                                                                                                                 
             configuration: latency=0                                                                                                                                              
        *-ide:0                                                                                                                                                                    
             description: IDE interface                                                                                                                                            
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller                                                                                                                  
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1f.1                                                                                                                                                     
             bus info: pci@0000:00:1f.1                                                                                                                                            
             logical name: scsi0                                                                                                                                                   
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 33MHz                                                                                                                                                          
             capabilities: ide bus_master emulated                                                                                                                                 
             configuration: driver=ata_piix latency=0                                                                                                                              
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)                                                                    
           *-cdrom                                                                                                                                                                 
                description: DVD reader                                                                                                                                            
                product: CDRW/DVD GCCT10N                                                                                                                                          
                vendor: HL-DT-ST                                                                                                                                                   
                physical id: 0.0.0                                                                                                                                                 
                bus info: scsi@0:0.0.0                                                                                                                                             
                logical name: /dev/cdrom                                                                                                                                           
                logical name: /dev/cdrw                                                                                                                                            
                logical name: /dev/dvd                                                                                                                                             
                logical name: /dev/scd0                                                                                                                                            
                logical name: /dev/sr0                                                                                                                                             
                version: A104                                                                                                                                                      
                capabilities: removable audio cd-r cd-rw dvd                                                                                                                       
                configuration: ansiversion=5 status=ready                                                                                                                          
              *-medium                                                                                                                                                             
                   physical id: 0                                                                                                                                                  
                   logical name: /dev/cdrom                                                                                                                                        
        *-ide:1                                                                                                                                                                    
             description: IDE interface                                                                                                                                            
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller                                                                                                             
             vendor: Intel Corporation                                                                                                                                             
             physical id: 1f.2                                                                                                                                                     
             bus info: pci@0000:00:1f.2                                                                                                                                            
             logical name: scsi2                                                                                                                                                   
             version: 02                                                                                                                                                           
             width: 32 bits                                                                                                                                                        
             clock: 66MHz                                                                                                                                                          
             capabilities: ide pm bus_master cap_list emulated                                                                                                                     
             configuration: driver=ata_piix latency=0                                                                                                                              
             resources: irq:18 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=16) ioport:eff0(size=16)                           
           *-disk                                                                                                                                                                  
                description: ATA Disk                                                                                                                                              
                product: ST980310AS                                                                                                                                                
                vendor: Seagate                                                                                                                                                    
                physical id: 0.0.0                                                                                                                                                 
                bus info: scsi@2:0.0.0                                                                                                                                             
                logical name: /dev/sda                                                                                                                                             
                version: DE04                                                                                                                                                      
                serial: 5ST045RD                                                                                                                                                   
                size: 74GiB (80GB)                                                                                                                                                 
                capabilities: partitioned partitioned:dos                                                                                                                          
                configuration: ansiversion=5 signature=f6c5f6c5                                                                                                                    
              *-volume:0                                                                                                                                                           
                   description: EXT3 volume                                                                                                                                        
                   vendor: Linux                                                                                                                                                   
                   physical id: 1                                                                                                                                                  
                   bus info: scsi@2:0.0.0,1                                                                                                                                        
                   logical name: /dev/sda1                                                                                                                                         
                   version: 1.0                                                                                                                                                    
                   serial: e4510d0b-62e9-4f5b-9e2e-255c34a0c48f                                                                                                                    
                   size: 62MiB                                                                                                                                                     
                   capacity: 62MiB                                                                                                                                                 
                   capabilities: primary journaled extended_attributes ext3 ext2 initialized                                                                                       
                   configuration: created=2009-10-27 23:46:26 filesystem=ext3 label=grub modified=2009-11-11 23:23:25 mounted=2009-11-11 22:46:58 state=clean                      
              *-volume:1                                                                                                                                                           
                   description: EXT4 volume                                                                                                                                        
                   vendor: Linux                                                                                                                                                   
                   physical id: 2                                                                                                                                                  
                   bus info: scsi@2:0.0.0,2                                                                                                                                        
                   logical name: /dev/sda2                                                                                                                                         
                   logical name: /                                                                                                                                                 
                   version: 1.0                                                                                                                                                    
                   serial: ec8ce521-7f42-481b-981c-36357abf559c                                                                                                                    
                   size: 8001MiB                                                                                                                                                   
                   capacity: 8001MiB                                                                                                                                               
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                                      
                   configuration: created=2009-10-28 22:22:26 filesystem=ext4 lastmountpoint=/P7&#65533;&#65533;}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#329;&#65533;&#65533;>&#65533;&#65533;&#65533;M&#65533;G5&#65533;&#65533;-&#65533;&#65533;>&#65533;&#65533;!&#65533;&#65533;!&#65533;&#65533;}&#65533;&#65533;&#65533;>&#65533;&#65533;>&#65533;&#65533;uP modified=2009-11-10 18:03:00 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-11 23:24:06 state=mounted                                                          
              *-volume:2                                                                                                                                                           
                   description: EXT3 volume                                                                                                                                        
                   vendor: Linux                                                                                                                                                   
                   physical id: 3                                                                                                                                                  
                   bus info: scsi@2:0.0.0,3                                                                                                                                        
                   logical name: /dev/sda3                                                                                                                                         
                   version: 1.0                                                                                                                                                    
                   serial: fcdc06c1-729c-4991-817d-e7f94ce69dc6                                                                                                                    
                   size: 8001MiB                                                                                                                                                   
                   capacity: 8001MiB                                                                                                                                               
                   capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized                                                                           
                   configuration: created=2009-11-01 15:34:59 filesystem=ext3 modified=2009-11-11 23:23:25 mounted=2009-11-11 22:46:56 state=clean                                 
              *-volume:3                                                                                                                                                           
                   description: Extended partition                                                                                                                                 
                   physical id: 4                                                                                                                                                  
                   bus info: scsi@2:0.0.0,4                                                                                                                                        
                   logical name: /dev/sda4                                                                                                                                         
                   size: 58GiB                                                                                                                                                     
                   capacity: 58GiB                                                                                                                                                 
                   capabilities: primary extended partitioned partitioned:extended                                                                                                 
                 *-logicalvolume:0                                                                                                                                                 
                      description: Linux filesystem partition                                                                                                                      
                      physical id: 5                                                                                                                                               
                      logical name: /dev/sda5                                                                                                                                      
                      capacity: 8001MiB                                                                                                                                            
                      capabilities: bootable                                                                                                                                       
                 *-logicalvolume:1                                                                                                                                                 
                      description: Linux swap / Solaris partition                                                                                                                  
                      physical id: 6                                                                                                                                               
                      logical name: /dev/sda6                                                                                                                                      
                      capacity: 2000MiB                                                                                                                                            
                      capabilities: nofs                                                                                                                                           
                 *-logicalvolume:2                                                                                                                                                 
                      description: Linux filesystem partition                                                                                                                      
                      physical id: 7                                                                                                                                               
                      logical name: /dev/sda7                                                                                                                                      
                      logical name: /var/log                                                                                                                                       
                      capacity: 298MiB                                                                                                                                             
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /opt
                      capacity: 1498MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /home
                      capacity: 47GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6dfbf00-f6dfbfff ioport:10c0(size=32)
  *-battery
       product: DELL NT37789
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```
Could you tell me the command you used to find all this out?

Thanks, 

Scott

---

### Post by buffalojr on 2009-11-13
Running Beautifully. Only having one problem with Firefox and Java but no hardware issues

Dell Precision m6300
Intel Core2 x7900
4gb ddr2
Nvidia 256mb g84

---

### Post by Sven6210 on 2009-11-16
Asus EeePC 900a with

Atom 1,6 MHz
2 GB RAM (extended)
8 GB SSD
Atheros WiFi

---

### Post by Defiant Rat on 2009-11-16
Fresh install of Ubuntu 9.10 and everything works perfectly out of the box, apart from desktop effects which was easily sorted by installing the ATI drivers, which was quick and easy. I'm new to Linux, and very impressed :D.

My laptop is a Toshiba L300D - [http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&highlightOption=131600&com.broadvision.session.new=Yes&PRODUCT_ID=1059357#0](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&highlightOption=131600&com.broadvision.session.new=Yes&PRODUCT_ID=1059357#0)

---

### Post by cmay on 2009-11-16
output of lspci. my lappy works perfect with debian lenny and ubuntu from jaunty and up to karmic. other distros might not work and belenix and open solaris is too messy to deal with. 
I had troubles with getting textbased installers to work but everything with hardware support and a graphical installer works. all things works out of box if systems installs when it comes to linux I think. 
> 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
00:09.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
00:09.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10) 



---

### Post by cwarner7_11 on 2009-11-16
A Toshiba Satellite 505, Intel dual core 64-bit,Intel 4 Series Chip Set, 3 Meg memory, 380 gig hard drive.  Running 9.04 (32 bit) and 9.10 (64-bit).  Everything worked from first boot.  I have one application (Salome-MECA) that has been optimized for NVIDIA graphics that gives me an issue, but everything else works fine.

---

### Post by Cathhsmom on 2009-11-16
The laptop itself works completely with Ubuntu 9.10.  I have a Toshiba P205-6337.   My HP TV tuner express card, not part of the laptop per say,  does not work.

---

### Post by witeshark17 on 2009-11-16
Fully functioning Dell here. Credit to Dell; it was factory preloaded with Ubutnu 9.04 :popcorn:

---

### Post by Kojans on 2009-12-04
HP compaq nc6000 laptop; Ubuntu 9.10.
Everyting (As far as I tried it out!) is working; except wireless. Obiously the hardware is broken: didn't work in Windows XP, the led stays out when I push the button.
So now I'm trying to install wireless USB-adaptor (Linksys WUSB54GC-version3) which I'm still working on....

Greetings!

---

### Post by ok_dr on 2009-12-05
Gateway M6848
Generally works well apart from not being able to use the microphone first only the internal one, now with Karmic the external also. Tried so many possible suggestions in the forums but haven't worked out. I use Skype daily so obviously a big issue for me.

---

### Post by crazyone on 2009-12-06
i have a compaq presario f750us. everything works on it except for the 5in1 card reader. has to be at ubuntu 9.10 to get it working that much. only i dont really care for the way ubuntu is now setup sadly. i feel it has messed up big time in this release on the software side. but hardware acutely works for once.

---

### Post by winjeel on 2009-12-06
1. Dell Mini v10, shipped with 8.04 and Dell Ubuntu software kit. Cost: Priceless
2. Dell Latitude D520, installed on a partition after a few years with XP. Cost: a few bufferin for a couple of headaches months ago. Now, only the external microphone doesn't work, and the printer can't handle B5 paper.

---

### Post by Zoot7 on 2009-12-06
I've a Dell XPS M1530 with the Linux friendly options (Intel Wireless, nVidia GPU), and it's been pretty near flawless with Ubuntu and openSUSE for 2 years now.

---

### Post by Kimm on 2009-12-06
Ubuntu works perfectly on my eeePC 1000HE

---

### Post by dkhajavi on 2009-12-06
Alienware M17 (NVIDIA)

Sounds works
90% or keyboard (no WiFi on/off, speed control, brightness, light effects)
Can't engage NVIDIA drivers as it causes a black screen on boot.
Suspend and hibernate will not recover requiring a hard shutdown
9/10 boots are successful, others lock-up
Two to three times a week the computer locks during normal operation.
Once a week the wireless acts like the drivers are not loaded during boot
Battery use is accelerated with Ubuntu


The big issue for me is the NVIDIA drivers not working as it is like having a Ferrari with a Yugo engine!

---

### Post by OwNeD on 2009-12-06
Linux works completely with my laptop-I will post my hardware specifics. 

So far i have had no problems at all,everything works. 

 i use a HP PAVILION DV7 NOTEBOOK PC

---

### Post by opnickc on 2009-12-26
I'm running an Averatec 2573

AMD Turion 64 x2 2GHz (TL-60 I think)
3GB DDR2
ATI Radeon X270

Everything runs out-of-the-box with Ubuntu with one exception.  Audio works, but headphone out does not mute the internal speakers.  That is, sound plays back through the speakers, and through the headphone jack, but there is no way to mute the internal speakers without also muting the headphone-out.

I have tried several guides for similar problems on other laptops (nothing specific to this machine) and those solutions always muted both speakers and headphones or neither.  The only suitable workaround I've found (besides not using headphones or cracking the machine open and disconnecting the speakers) is to use an external USB sound card and disable the internal one.  Not fun.

I think my next lappy will be System76.  For now, I'm putting up with Win7 (for games) on my laptop and only using Ubuntu (for real work :P ) on my desktop.

[edit] I forgot to mention I also had some quirky power management issues.  Sometimes the battery would show no charge when fully charged, sometimes the machine would think it was on AC power while on battery, and visa versa.  This meant I got unwanted screen dimming and other power management features when plugged in, and no idea how much charge I had remaining when on battery.  This, more than the headphone issue, is why I chose to stick with Windows on this machine. :(


My wife is running an older IBM Thinkpad, don't remember the exact model, but I know it's got a 1.6GHz Pentium (either 4 or m), a gig of RAM, and a Radeon 7000 series graphics chip (7500 maybe?).  Everything works perfectly out-of-the-box with Ubuntu 9.04 :) (haven't updated to 9.10 yet. . . might just wait for 10.04).

---

### Post by wavery on 2009-12-26
Two problems:
1. The laptop won't always come out of hibernation forcing me to do a hard re-boot.
2. When it does come out of hibernation, it won't find the wireless network (that it was using just fine before going into hibernation).

---

### Post by crimesaucer on 2009-12-27
HP Pavilion dv9920us (cheap laptop from a year and a half back).

What doesn't work is:

1.) webcam's microphone
2.) BCM4322 pre-n (there are finally workarounds now)
3.) a couple of the multimedia keys (like the quickstart and dvd buttons)
4.) suspend and hibernate have issues. Suspend finally works for me with xfce4, but hibernate doesn't.

... I never tired bluetooth or the remote control that comes with it but I doubt they work. (maybe bluetooth?)

---

### Post by SchizmWolf on 2009-12-27
Voted that it mostly works. I have only two problems, only one of which is my Kubuntu's fault (though, by proxy, my own as well) 1) sleep and hibernate won't work; it'll shut down but won't boot back up, will just initialize the disk but not the screen, and 2) my 3D graphics acceleration is shoddy for some programs, though I think that's cuz my laptop just kinda sucks.

---

### Post by Geezer60 on 2009-12-27
HP Pavillion dv6000 2 GB ram, pretty generic machine.  Ran 9.04 dual with vista for 6 months, finally got brave enough to install 9.10 full format.  I'm free of windows.  (Except at work.)

---

### Post by Jekshadow on 2009-12-27
Everything works, but the b43 driver keeps giving me a fatal DMA error with the 14e4:4315 chipset, so I am forced to use an external wifi adapter that uses the p54-usb driver, but that one drops the connection every few hours.

---

### Post by Ginsu543 on 2009-12-29
Dell Mini 9 and Vostro A90. Everything in Jaunty worked perfectly out of the box. I've since upgraded to Karmic on both machines and everything works in Karmic as well, although I've had to tweak/work around some issues. The only thing I have not yet been able to fix completely to my heart's content is minor hissing when recording through the built-in mic (for example, in Skype). The built-in mic worked flawlessly in Jaunty, but this may have to do with the default implementation of PulseAudio in Karmic over and against ALSA is Jaunty.

---

### Post by margazhang on 2009-12-29
I am running Kubuntu 9.10 on Acer 3620 laptop and Linex Mint (based on Ubuntu but looks like Windows in appearance and functionalities) on a brand new Gateway NV54 laptop. Everything is OK except for wireless connections. In the case of Acer 3620, I had to install wicd via Synpaptic to replace Gnome Network Manager (NM) to connect it wireless right after a clean install. In the case of Gateway NV54, the NM worked in the beginning, but when I connected it through a network cable (wired connection) then the wireless network greyed out and would not let me pick any connections. So I had to install wicd via Synaptic to replace NM.

I wonder if Ubuntu (and all its variations Kubuntu, Edubuntu, Linex Mint, etc) can make wicd the default network manager, then we will have less issues with wireless connections. 

Only when wicd does not work for some machines, then giving the choice to use another utility like NM. What do you think?

---

### Post by Khakilang on 2009-12-29
Intel Pentium M 1.6Ghz, 512MB RAM, 20GB Hard disk, Intel graphic card built in and 14" LCD screen. Aztech wireless USB adapter.

---

### Post by Vignesh S on 2009-12-29
Right, a fair bit of "Ubuntu on laptop" experience.

Dell Inspiron 1527: Everything works out of the box (didn't install it, but used it by LiveUSB).
4GB DDR3 RAM, Intel Centrino (dunno about GHz though its probably >2.0GHz), Dell wifi card.

IBM Thinkpad R31: Everything also worked out of the box.
1GB RAM, Intel Celeron 1.06GHz, Atheros AR5BMB-44 wifi card, 

Medion Akoya mini E1210: Everything but the wifi, webcam and microphone (the last 2 don't really matter though) worked, and being somewhat of a noob at Linux at that time, it took forever getting it to work, though I could probably get it working in 5 mins :-D

Toshiba Satellite T110/00D: Most troublesome of the lot, though not as bad as it could be. Wifi, Ethernet, screen brightness, microphone and webcam didn't work. Of these, got the first 3 fixed up.

---

### Post by avacado on 2009-12-29
Dell inspiron 1520 4GB RAM Broadcom Wifi Ricoh Card reader
Dell laptops do not come with linux installed in australia, so I had to do it myself amid warnings from Dell that I had voided my warranty and future laptops will be hard wired for windows only.
The Ricoh card reader does not read SONY memory stick and the problem is a known bug with licensing from SONY the issue. Reads all other cards fine. I get around this by using the camera and cable.
The wi-fi switch drove me nuts but basically disables wireless if you switch it either on or off after boot.
Suspend resume button does nothing. Windows button does nothing. Media control buttons all work well.
Sometimes I would love to know more, but not sure how to learn- every search I make for support brings up that thread "How many of you have really switched to ubuntu?". Sometimes I just want convenience.

---

### Post by Dragonbite on 2009-12-29
Good and bad news...

The good news is that when I installed Linux on my Dell D400, it detected my Broadcom wireless card out of the box and I was able to connect to the network even while I was running a LiveCD!

The "bad" news is that it was Fedora 12, which is using, from my understanding, [[COLOR="Blue"]OpenFWWF[/COLOR]]("http://www.ing.unibs.it/openfwwf/") which Ubuntu does not use.

Great thing is that it works even better than Windows does!  I've had good, usable connections and haven't been dropped once yet!  I think if Ubuntu started using it, I think I would come back to Ubuntu in a heartbeat!

---

### Post by ElevenWarrior on 2009-12-29
Acer Aspire 6530
AMD ANthlon X2, 2.1ghz
Acer nplify b/g/n wireles (works fine, even supports packet injection!)
ATI HD Radeon 3200 mobile, (works great, has some problems with cairo-dock in OpenGL mode in ubuntu. BackTrack 4 works flawlessly)
the light up buttons on the top of the laptop work. (sound, play/pause/fastforward/rewind) all work. the internet button dosen't though. (turn of the wireless card)
The sound ports now all FINALLY work, (headphone, mic, SPDIF)
WebCam works, built in Mic works, HDMI port works,VGA port works, DVD works, LAN works, haven't tried eSATA yet, nor PCI port, nor modem.
everything else works fine.

---

### Post by Ibidem on 2009-12-31
Working perfectly (at least what I use):
Acer Aspire One ZG5 (Xp version), 1.4 GHz Atom (dual core), 1 GB RAM, 160 gig HDD, webcam works, AR5007 wireless /ath5k (WEP & open+hidden essid tested) working fine, Realtek 8102E working, Realtek audio works, intel 945 graphics
 Kuki Linux (Jaunty + 2.6.31 kernel) w/ Firefox 3.5 + Icewm + xpdf installed & tons of stuff (xfce, Thunar, Zim, epdfview...) removed.
Don't even have a flash card, so I don't know how that would work.
Web: I only have Shiretoko unofficial build, so it takes 1 trick--about:config, set
general.useragent.extra.firefox       to     Firefox/3.5.5
Kuki worked OOB, apart from Midori (crashes, no ftp...-->install FireFox)
By now, this is NOT Kuki linux.
Also working: 
TinyCore Linux, AntiX (doesn't autoload ath5k)
So... 
I'm happy.

---

### Post by Mahngiel on 2009-12-31
Works partially- until i worked around:

fwcutter to install wireless drivers
can't use hibernate

---

### Post by peakpc on 2009-12-31
Compac v5000 AMD Turion64 2.2, 2gb ram ATI Xpress200m.  9.04 works really good (with broadcom drivers for wireless)  9.10 has suspend/hibernate resume video black screen issues and broadcom drivers did not auto detect without tweaking. All of my Ubuntu issues from 7.04 seem to be either ATI or broadcom related. Almost time for a new laptop I think this time around I will stick with mainstream intel stuff for compatibility.

---

### Post by witeshark17 on 2009-12-31
No windows partition, everything works fine on my Dell 1545 :popcorn:

---

### Post by Revolutionary101 on 2009-12-31
I have a Sony Vaio FS500 with a Pentium M 1.6 GHz single core processor. My laptop has an Intel Mobile 915GM/GMS/910GML Express Graphics Card. The sound card is an Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Card. Finally, my network card is an Intel PRO/Wireless 2200BG. I also have a Hitachi 80 GB hard drive and I have a total of 1 GB of RAM.

---

### Post by curioshop on 2009-12-31
hibernate may still be a bit buggy, but wireless, suspend, and everything else work perfectly, though i had to install and configure kerberos myself.

---

### Post by Catboy~ on 2010-01-01
My Dell mini 10v works perfectly with linux because I opted for the "preinstall ubuntu on my computer" option.

---

### Post by Dragonbite on 2010-01-02
Just put on 9.10 on my Dell Latitude D400, and a couple of things stand out.

Just like previous versions, most everything is detected out of the box, except for the Broadcom wireless. I wish Ubuntu would include the [[COLOR="Blue"]OpenFWWF[/COLOR]]("http://www.ing.unibs.it/openfwwf/") which Fedora 12 does.. makes Broadcom work out of the box and BETTER than Ubuntu's fwcutter OR Windows!!  Haven't had it drop a connection yet.

Other than that, so far so good!

---

### Post by TnJ on 2010-01-10
I have a Dell Latitude D610.  Everything works fine except for the blutooth module.  It will connect to my phone, but I get an error every time I try to browse it's files.  The error says "The folder contents could not be displayed.  Operation forbidden."  Then Nautilus will seem to hang, and phone displays "Not supported by receiving device".

T

---

### Post by Maheriano on 2010-01-10
Dell Studio 15, sometimes
- CD will constantly try to eject for 5 minutes straight but there's no CD in there. It's a slot load so it just keeps ejecting over and over and over.....
- Sometimes the volume up/down touch buttons above the keyboard aren't responsive but WATCH OUT! Don't keep hitting them because the next time you reboot it'll cache them all and you'll spend 15 minutes watching the volume bar spasm at the top of your screen.
- My keyboard still has Windows keys on it no matter how often I format and reinstall Ubuntu.

Dell D600 installed perfectly. Worked fine for me, sent it to my brother, 6 months later now he's complaining it's sloooooooooow. Very slow. He formatted and reinstalled Ubuntu twice, still slow. Otherwise great.

---

### Post by Maheriano on 2010-01-10
> **TnJ said:**
> I have a Dell Latitude D610.  Everything works fine except for the blutooth module.  It will connect to my phone, but I get an error every time I try to browse it's files.  The error says "The folder contents could not be displayed.  Operation forbidden."  Then Nautilus will seem to hang, and phone displays "Not supported by receiving device".

TAre you with Verizon? They block the ObEX protocol in the bluetooth stack so ya, that's not going to work. Don't even try.

---

### Post by kyuubi777 on 2010-01-10
works flawlessly.. absolutely no issues

Lenovo 3000 N100

intel core 2 duo 1.66Ghz
ipw card 
intel integrated graphics card
1G ddr2 sdram
3945 or so chip-set

---

### Post by Dark_Stang on 2010-01-10
Linux works perfectly on my laptop.

Laptop Specs
Model: HP DV6636NR
Processor: AMD TurionX2 TL-58
GPU: nVidia 7150m (integrated)
Networking: nVidia hardwired, Broadcom BCM4311 wireless
Memory: 4GB DDR2 (was 2GB stock)
USB ports all work
Firewire port works
Card reader works
All media controls work
Webcam works (Suyin webcam)
Optical drive works
Suspend and hibernate both work
CPU throttling works.
SVideo and VGA out work
PCMCIA Express slot works
The only two things I have not tested are the dial-up modem and the expansion port, because I have no use for them.

Linux Specs
Started with Ubuntu Minimal and went from there. 7.10, 8.04, 9.04, and 9.10 all worked.

---

### Post by lawenlerk on 2010-01-10
Mine's a Dell Studio Xps 1340.

this laptop has heat issues so the first two times it shutdown suddenly during installation of ubuntu.

after that, i placed my laptop under an air conditioner and it ran thru the whole thing.

wireless, sound, cd, media keys work well although u'll have to install restricted hardware drivers for wireless and graphic card (nvidia 9400m)

I had dell replace my heatsink once but temperature problems are still bothering me. now i run my laptop on a cooling pad and monitor the temperature constantly.

somehow windows 7 allows the laptop to run until 70+ Celsius but ubuntu (and other non-windows systems such as the dell diagnostic test cd) shutdown automatically at around 55-60 celsius. I know this isnt my thread but any idea why this happens?

---

### Post by shadow of the locust on 2010-01-10
i have an acer aspire one a150l running fedora 12 and as far as i can tell, everything works completely.

---

### Post by sandyd on 2010-01-10
> **Maheriano said:**
> <snip>
- Sometimes the volume up/down touch buttons above the keyboard aren't responsive but WATCH OUT! Don't keep hitting them because the next time you reboot it'll cache them all and you'll spend 15 minutes watching the volume bar spasm at the top of your screen.
<snip>.
 
if that ever happens, just shut down the computer and pull out the ac adaptor, and battery, wait for a while, then plug everything back in. ill then be fixed.
that happened with my media key thingy. It would occasionally simply non-stop light up and open a million rythmboxes....

---

### Post by Roasted on 2010-01-10
I'm running a Dell Latitude E5500 at work. I have tested multiple distributions on it.

With the following distros, everything worked 100%, including wifi with WPA2 enterprise:

Kubuntu/Ubuntu 9.10
OpenSuSE 11.2
Mandriva 2010

I also tried Fedora 12. It seems as if Fedora 12 (being as bleeding edge as it is) uses plymouth at the boot screen, which no other distros have. It is often problematic with Intel video cards. It would hang for me at boot about 9/10 times I booted.

Despite Fedora 12 being in a constant "beta" stage it feels like since they test all new software, I figured it was worth noting. I'm sure by the time it gets fixed, other distros will pick it up too. But for the E5500, I had no issues.

I also previously ran a Dell Precision M4300 and I ran Ubuntu on it just fine with no issues.



> **carlee said:**
> if that ever happens, just shut down the computer and pull out the ac adaptor, and battery, wait for a while, then plug everything back in. ill then be fixed.
that happened with my media key thingy. It would occasionally simply non-stop light up and open a million rythmboxes....

It's also worth noting that while doing this method, you can also press the power button several times. By pressing the power button without AC power plugged in or the battery in, it will thereby drain the charge that the capacitors on the board might be retaining. I've had that method fix some very strange issues. Quick example: Vista on my rig was set to auto-hibernate after 1 hr, well it did. I couldn't get it turned back on. Power button was dead, etc. Had to pull AC power and hit power button 8-10 times. All was well then, and hibernation was disabled.

---

### Post by mamamia88 on 2010-01-10
the only thing that has never worked out of the box for me is wireless.  and that is really easily fixed in most cases so yeah i would say it's possible.  if you have a broadcom card try sabayon worked out of box for me

---

### Post by TnJ on 2010-01-10
> **Maheriano said:**
> Are you with Verizon? They block the ObEX protocol in the bluetooth stack so ya, that's not going to work. Don't even try.

I am with Verizon, using an LG VX10000.  So the D610 is perfect otherwise. :cool:

T

---

### Post by squilookle on 2010-01-10
Toshiba Equium, 1.6ghz Pentium M, 512mb ram, 64mb ati radeon mobility graphics card, 70gb hard disc. 

It works very smoothly with Linux. The only issues I have is that suspend and resume don't work on any distribution.

---

### Post by kay-man on 2010-01-10
The laptop is a HP Pavilion DV6-2030SD.

Almost everything works, I just have 1 problem: no sound whatsoever.

The sound card is ATI Technologies Inc SBx00 Azalia (Intel HDA), which it seems many people have problems with getting it to work in Linux. I've found some possible solutions, but I haven't tried them yet.

Most everything worked straigh away, I only had some issues gettin the card reader to work, which turned out to be caused by a BIOS setting.

I'm running Gentoo, by the way. I used to use kubuntu, but I've been unhappy since the karmic upgrade. But that's a different story...

---

### Post by TheNessus on 2010-01-10
Fujutsu Siemens v6501 (or something)
everything works fine only with Karmic. in Jaunty you cannot reduce backlight.
Nvidia 8400 heats up to 70 MINIMUM all the time though, crappy card...

---

### Post by Cyberponcho on 2010-01-11
Reporting a 100% Linux compatible HP nc4200 running Hardy LTS, the only issue is hibernating but i'll get around to it :-)
Hardware specs and install procedure are [here.]("http://cyberponcho.blogspot.com/2009/02/ubuntu-on-hp-nc-4200.html")

---

### Post by shuttleworthwannabe on 2010-01-11
> **Fire_Chief said:**
> I have a Lenovo Thinkpad T60 with Hardy running strong on it. I have not configured the fingerprint scanner or the function hotkeys and don't use the IR port so I'm not sure if it works or not. Other than that, the system is fantastic!

What about the fan noise? I have Thinkpad X200--everything works fine out of the box (have not configured Fn keys and card reader yet). My fan runs at level 3-4 all the time even on idle. I have tried all sorts of solutions on the thinkpad fan control site, but alas, I was not successful. if you know a simple HOWTO (step by step), will appreciate the help.

---

### Post by sledge73 on 2010-01-11
Linux works perfectly OOTB with my IBM R51 laptop. No problems at all. :cool:

---

### Post by Groucho Marxist on 2010-01-11
I'm running Ubuntu Linux 9.10 x86_64 on a System76 Pangolin Performance laptop with the following specs:


[LIST]
[*] Intel Core 2 Duo 3.07 GHz CPU
[*]8 GB RAM
[*]GeForce G 105M Graphics Card
[/LIST]

---

### Post by Dragonbite on 2010-01-11
> **Maheriano said:**
> Are you with Verizon? They block the ObEX protocol in the bluetooth stack so ya, that's not going to work. Don't even try.

Is there any way around that? That may explain some things...

For the record, I installed Ubuntu 9.10 on my Dell Latitude D400 Laptop and everything, except wireless, works out of the box.

While it detected the Broadcom wireless card running as a LiveCD, when I installed it the system failed to detect it under "Hardware Drivers".  I had to "manually" install it (run the command myself).

I wish they would include OpenFWWF in Lucid so I don't have to worry about it again.

---

### Post by johnjust on 2010-01-11
Lenovo Thinkpad SL500 Elite, Ubuntu 9.10 working great, not a single problem.

Of course, I had to play with it a little to get everything running perfectly (it doesn't have the "real" Thinkpad firmware, which I didn't know until after I bought it...), but most of that was back in Jaunty.  Since I freshly installed Karmic, everything is perfect.  I still see a lot of people having issues with Karmic, but I (seriously) didn't have a single problem.

In fact, even updating the kernel seems a lot easier (with Jaunty I would sometimes have to re-install the Nvidia drivers a couple times to get it to work, but with Karmic they work first time every time).

Occasionally running WoW will crash Compiz, but that's not a big deal at all.

---

### Post by DrHyde on 2010-01-11
Why on my Gateway laptop, do I get a distorted,dual screen when I try to install 9.1. My Compaq laptop loaded without a single problem. 
The Gateway has windows xp and I am trying to set up dual booting as I did on my Compaq.

---

### Post by Maheriano on 2010-01-11
> **Dragonbite said:**
> Is there any way around that? That may explain some things...
haha ya, get a Sprint phone!
I moved to the USA for a year and first got a phone with Sprint because it's not locked up but just could not stand the terrible service so I ended up switching to Verizon within the 30 days and just as I suspected, it was disabled to old hell. As far as I know, there's no way around it unless you get some sort of crack/hack for it which probably can't be mentioned here. I even talked to a girl at the customer support for Verizon and she confirmed it, she sounded like a super geek, I was very impressed. She knew everything I was talking about.

If you want to see what the uninhibited Bluetooth 2.0 stack is capable of, go [here]("http://en.wikipedia.org/wiki/Bluetooth") and look under Technical Information for all the protocols available in the stack. Then if you want to see what they've enabled on your phone (mine's a Blackberry 8330), go to Bluetooth and click Options. It's listed there under Services. Mine has:
- Headset
- Handsfree
- Serial Port Profile
-- Desktop Connectivity
-- Wireless Bypass
-- Data Transfer
- Dial Up Networking
- Audio Source
- A/V Remote Control Target

Notice the lack of ObEX, AVRCP and A2DP. It's all blocked. As well as being able to synchronize your phone with your Bluetooth capable home phone to receive calls on your Blackberry while at home. Ya, if they can't make money off it, it's blocked.

---

### Post by TimelessRogue on 2010-01-12
[FONT=Comic Sans MS]All's well with Ubuntu 10.04 Lucid (after running Karmic, Jaunty and Intrepid ... all on the leading edge of Alpha releases) ... as far as I've actually tested, anyway ... on my HP Pavilion DV9623CL rigged as follows:

AMD Turion(tm) X2 Dual-Core 64-bit Mobile w/ 4 gigs memory, ATI Radeon HD 3200 graphics, ATI Azalia/[/FONT]Altec Lansing[FONT=Comic Sans MS] sound, Realtec Ethernet networking plus integrated [/FONT]802.11a/b/g WLAN & Bluetooth (Bluetooth not tested yet)

There've been a few minor tweaks ... some to suit my own quirks and some that were actually Linux related ... but nothing extreme and nothing that was absolutely necessary to keep Ubuntu, Lucid or otherwise, up and running ...
[FONT=Comic Sans MS]


.  

[/FONT]

---

### Post by gandgcomputer on 2010-01-12
I've taken the plunge and devoted an entire ACER Aspire 5517 to linux. I'm dual booting Ubuntu 9.10 x64 with Mint 8 x64. Both work great.

---

### Post by gradinaruvasile on 2010-01-12
Dell D630 / Core2Duo T7300@2.0 GHz/2 GB RAM/Nvidia Quadro NVS 135M 
- Ubuntu 8.04, 8.10, 9.04, Xubuntu 9.10 Everything working. I used the Bluetooth recently (9.10) even with PulseAudio/handsfree (blueman) - worked well. The external headphones are not detected, have to switch manually (external mic is switched on jack insert automatically).

Only thing is that it _seems_ it has a built in 3G modem that i never used - it isnt visible for Ubuntu and dellWirelessCtl reports that is not installed - but neither Windows XP sees it with drivers installed so maybe only the SIM card socket is in place and really doesnt have the rest installed.

Dell C640 / Pentium4 M/1.8 GHz/512 MB RAM/Ati Mobility 7500 
-Ubuntu 8.04, 8.10 - all features working - i used even Compiz + cube + virtualboxed Windoze.

---

### Post by nerdy_kid on 2010-01-12
Vostro 1500 intel core two due @1.4 ghz
Nvidia geforce 8600M
HD Intel audio
Broadcom BCM wireless
3Gb of RAM


lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```everything works perfect except for my modem which i havnt tested cause i have FIOS not dial-up ;)

---

### Post by SlickRick on 2010-01-12
Toshiba Satellite L300-18E
Worked great with Jaunty and even better with Karmic. Here's a [_link_]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&com.broadvision.session.new=Yes&PRODUCT_ID=1056299") to the full specs.
Only problem I encountered was when trying to make it play a sound when I open/close the lid. Ubuntu had problems detecting the event or I was doing something wrong but not a real problem.

---

### Post by l-x-l on 2010-01-12
Dell Inspiron E1705 running Karmic perfectly after some tweaking.

System:    Kernel 2.6.31-16-generic i686 (32 bit) Distro Ubuntu 9.10 karmic
CPU:       Dual core Intel Core2 T7200 (SMP) cache 4096 KB flags (sse3 nx lm vmx) bmips 7988.48 
           Clock Speeds: (1) 1000.00 MHz (2) 2000.00 MHz
Graphics:  Card nVidia G71 [GeForce Go 7900 GS] X.Org 1.6.4 Res: 1440x900@60.0hz 
           GLX Renderer GeForce Go 7900 GS/PCI/SSE2 GLX Version 2.1.2 NVIDIA 190.42 Direct Rendering Yes
Audio:     Card Intel 82801G (ICH7 Family) High Definition Audio Controller driver HDA Intel
           Sound: Advanced Linux Sound Architecture Version 1.0.21
Network:   Card-1 Broadcom BCM4401-B0 100Base-TX driver b44 v: 2.0
           Card-2 Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection driver iwlagn v: 1.3.27k
Disks:     HDD Total Size: 160.0GB (64.6% used) 1: /dev/sda SAMSUNG HM160JI 160.0GB

---

### Post by nanotube on 2010-02-02
dell vostro a90 
working perfect with karmic after a few tweaks, as described in this forum thread:
[http://ubuntuforums.org/showthread.php?t=1389877](http://ubuntuforums.org/showthread.php?t=1389877)

dell inspiron 5150:
working perfect on ubuntu intrepid - should work fine with karmic too, just haven't gotten to upgrading it.

---

### Post by unkelmarkmark on 2010-02-03
don't try and install ubuntu on any laptop that has the ATI radeon 7500 series gfx because it won't work.
and nobody so far has a fix.   several people have partial fixes.

---

### Post by aeon.flux on 2010-02-06
HP Pavilion dv6000, intel DC 1,73, nvidia go 7400

currently no problems. In jaunty i had to install graphic drivers and 9.10 used to crash without latest updates, but after install everything is great.

---

### Post by JakaBac on 2010-02-06
> **toupeiro said:**
> HP 8710w -- Ubuntu working 100%

Lenovo T60 - Ubuntu working 100%

Well the 8710w is not working 100% but 90% :)
I did not manage to get the SPDIF digital output through the HDMI port yet...

---

### Post by Coreo on 2010-02-24
[**Dell Latitude D610:** Pentium M 1.6Ghz, 2GB of fasterthanstock RAM, 64mb Radeon x300, 60gb HD]

Everything works great for me, and I've used everything that this laptop can do.
All keyboard shortcuts and power/suspend/volume buttons work.  :-\"

Only issues that I've had:
[LIST]
[*]Bit of a trick getting the wireless set up in Karmic when I did a fresh install.
[*]Wireless refreshes really slow. With Intrepid, it sometimes took up to 5 minutes to realize I had walked away from my connection.
[*]Wireless signal strength indicator is really slow, and doesn't have a very good scale. Never indicates less than 50%, but is still sometimes unable to connect because the signal isn't strong enough.
[*]Video driver has had trouble in the past, but seems to be working fine in Karmic. I can enable full visual effects without adding extra drivers.
[*]Dual monitors: Could never get it working with Intrepid, haven't tried with Karmic yet.
[*]IR and LIRC: Spent a bit of time with it, but couldn't get it working perfectly. Not sure if it's a machine specific problem.
[*]Heat: Sometimes gets really hot for apparently no reason. I've installed the i8kutils and some other Dell packages, but they don't seem to help much.
[/LIST]

I think that's everything...other than that I've been liking it. It's been my daily-driver for a couple years now, and it's done everything that I want it to do. Could do with a bit more video ram though. :-({|=

---

### Post by t.rei on 2010-02-25
I said before that my ubuntu works nicely. Well. In lucid it doesnt anymore. It crashes on resume from suspend and the transition from usplash to plymouth leaves me with the ugliest text-fallback there is.

I might try to install lucid over again, when its stable. But right now the core feature "suspend" is broken.

---

### Post by texpat on 2010-02-25
HP tc4200 tablet pc running Jaunty
Some of the nice tablet features don't work:
[LIST]
[*]when in tablet mode it doesn't invert the screen/mouse, so you'd have to move in mirror image of what you intend to (hope this makes sense).
[*]the pen's buttons don't work.
[/LIST]
The former is not much of a problem, since it doesn't really get used in tablet mode, the latter is a royal pain in the neck.

The machine also hangs sometimes when trying to switch users or when logging out. This is a weird behaviour that I haven't been able to reproduce reliably.

I also installed Karmic on a Medion laptop (can't remember which model) recently for a friend. This machine has a 'switch' to turn wifi on or off which is a 2-key combination (something like [fn]+F5). This doesn't work, whereas the keyboard combination to do other things (change sound volume etc.) does.

---

### Post by Mark Phelps on 2010-02-25
Several laptops ...

1) Fujitsu Liefbook T4020 Tablet PC
5 years old, came with XP Tablet version preinstalled
512MB original memory, upgraded to 2GB
Installed Hardy. Took a little work to get the stylus and manual screen rotation working.  Autorotation never worked.
Tried 8.10, 9.04, 9.l0 -- none can be fixed to sense the bezel keys -- an absolute necessity for a tablet PC
Upgraded to Win7 -- everything works, runs as fast as with Hardy.
Use Win7 all the time now -- since newer Ubuntu's won't work
Extensive forum posting failed to produce any solutions that worked.

2) Compaq Presario 2580US laptop
7 years old, came with WinXP Home preinstalled
512MB original memory, upgraded to 1GB
Installed Hardy.  Wireless, modem would not work.  Fixed wireless (partially) using WiCD.  Never able to get modem to work.
Needing to have reliable wireless, eventually removed Ubuntu and went back to using XP Home fulltime.

3) Older HP (Don't remember the model) laptop
10 years old, came with Win98 installed, upgraded to WinXP Home
256MB original memory, not upgradeable
Tried multiple distros.  Ubuntu versions not able to get screen over 800X600 no matter what.  PC Linux OS (2007) and OpenSUSE both able to get 1024x768 screen without problems.  No internal networking.  Able to get PCMIA netbus card partially working -- but needed wireless to use it regularly.
Eventually removed Linux distros and went back to XP Home -- where the wireless works reliably.
Installed Hardy.  Wireless wouldn't work.  Modem wouldn't work.

So, basically, of the three laptops, I'm one-for-three, with even that one being not upgradeable to anything newer than Hardy.

---

### Post by recluce on 2010-02-25
> **Coreo said:**
> [**Dell Latitude D610:** Pentium M 1.6Ghz, 2GB of fasterthanstock RAM, 64mb Radeon x300, 60gb HD]

Everything works great for me, and I've used everything that this laptop can do.
All keyboard shortcuts and power/suspend/volume buttons work.  :-\"

Only issues that I've had:

[LIST]

[*]Heat: Sometimes gets really hot for apparently no reason. I've installed the i8kutils and some other Dell packages, but they don't seem to help much.
[/LIST]

I think that's everything...other than that I've been liking it. It's been my daily-driver for a couple years now, and it's done everything that I want it to do. Could do with a bit more video ram though. :-({|=

I only have one D610 left to administrate (much more a year or two ago) - and from my experience, the D610 always had heat issues, no matter which OS. The one system still left is running XP and gets to about 55°C on the underside of the machine. A poor system design, as far as heat dissipation is concerned. The D620 and D630 are much better in that regards,

---

### Post by WinterMadness on 2010-02-25
no problems. not posting specs though

---

### Post by bunburya on 2010-02-26
I voted "works perfectly". I do have a problem with sound in games, but there used to be sound in games so I'm presuming that it was something I did which caused the problem (if only I knew what!)

I think I have a Lenovo N500.

---

### Post by SoFl W on 2010-02-26
When I first got my Dell Inspiron 1300 I installed W2Kpro over the WinXP Home and eventually put dual boot OpenSUSE on it.  Was never able to get the wireless to work under SUSE and was never impressed with the SUSE experience.  The DVD player stopped working on the machine and thought maybe it was time for a netbook.   I only use the laptop for travel.  About a month ago I decided to try 9.10 32bit on it installing from a boot stick.  Worked like a charm, although I am not exactly sure how charms are suppose to work.   My biggest problem was the wireless but found the solution very quickly.  Ubuntu breathed new life into the old machine and I learned a lot about ubuntu.  I don't use it often, but I have used it a lot lately and so far no major problems.

---

### Post by beetleman64 on 2010-02-26
Linux works completely on my cheap Tesco Fujitsu special (astoundingly). The only issue was trying to get the wireless card working, but a couple of lines in the terminal fixed the problem.

---

### Post by dragonboss on 2010-02-26
The media keys, the empowering technology, mail notify, program launcher, browser launcher,special euro and $ buttons above the arrow keys don't work

---

### Post by Private_Ops on 2010-02-26
I voted works fully.

Specs:

Lenovo G530: Intel Pentium Dual core (2.4GHz I think)
             2GBs of RAM
             160GB Hard Drive
             Onboard Intel Graphics
             Broadcom wireless (not sure which chip)
             6 cell battery (about 2 and half hours)
             Ubuntu 9.04

---

### Post by HalfWord on 2010-02-26
Although I'm actually very satisfied how my laptop works with Ubuntu, I had to vote "works partially"
1) The embedded winmodem doesn't work (I know, I know, but anyway...)
2) I always have an annoying problem, different with any release: In Karmic I lose sound from time to time (reported this in another thread), in Jaunty I lost 3D acceleration (not that I need it much, but Compiz stopped working), and in Hardy I lost backlight control (a bug report was filed for that issue). What's interesting is that each new install worked fine at first, and mentioned problems occured later in the release's lifetime, to be corrected again in a new release... then another problem would arrive etc. :???:

During the times between the problems, everything worked perfectly :p

The machine is Thinkpad R61i with AMD64 (x86_64) distribution.

---

### Post by gjoellee on 2010-02-26
Ubuntu crash if I suspend or hibernate. The wireless driver does not work after the first boot into Ubuntu after having used Windows (Dual boot). At the second boot the wireless driver work fine.

---

### Post by themacmeister on 2010-02-26
100% working, sleep on close lid, wake on open-lid, suspend, all notebook specific function keys working. Actually, the only things that don't work or compile are those projects using hardware specific assembly code - such as ZSNES and MPlayer, but there are plenty of alternatives to these. The PPC movie codecs are poorly represented, but VLC is available for Slackintosh - so all is good.

:D

---

### Post by Ian dewhurst on 2010-02-27
Everything works on my laptop.
Sleep works all hot keys work it is using an ATI chip but thats not an issue I don't need 3D.
HP Compaq 6715s
AMD turionx2 64 1.9GHZ CPU
Broadcom BCM4311 WLAN
Bluetooth
140GB SATA HD
2GB RAM
Battery that lasts 2 hours at best
Ubuntu 9.10

---

### Post by DownTown22 on 2010-02-27
ASUS M51Sn

Intel Core 2 Duo T5750 2.00GHZ
3GB RAM
Nvidia GeForce 9500M GS 512MB
Intel Wireless WiFi Link 4965AGN, Bluetooth
15.4" display
250 GB SATA HDD
8-in-1 Card Reader
Integrated web cam
Dual booting Windows Vista and Ubuntu 9.10

---

### Post by dakilla on 2010-02-28
ASUS UL30VT

Hybrid graphics

nvidia Gforce g210m
intel GMA 4500MHD


everything works except nvidia graphics..
and hw accel on intel GMA 4500MHD

running ubuntu 10.04 (it was worse on 9.10)

---

### Post by PeteUplink on 2010-02-28
My laptop is a rather old Toshiba Satellite Pro 2100 with a 2Ghz Intel Celeron processor, 40GB HD, 512MB RAM and a 32MB nvidia go graphics card. 

Most everything has worked fine except I can't install the nvidia drivers for it because when I restart all I get back is a flashing desktop image, but no icons or bars.

---

### Post by desnaike on 2010-02-28
No problems with Ubuntu 8.04,8.10,9.04,9.10 Mepis 7,8 Xubuntu, Puppy PClinuxos all work.


Sony Vaio PCG V505BX
Intel Pentium m 2ghz
512 ram
120 gig hdd (added after 40 gig died)
wifi
cd/rw dvd drive
pcmia
Ethernet
12.1 tft
ati mobile radeon

works great.

HP G61-429WM
everything works.

---

### Post by TusharG on 2010-02-28
I'm having trouble with Intel HD Sound and Video. However the laptop is brand new and the new i3 processor was launched on 7 Jan 2010. Ubuntu does not support most of the hardware out of the box. Infact I'm unable to hear sound and decent resolution on it. However I'm sure it will be fixed in 10.4 release. I'm waiting for 10.4 release. 
I know sound, video and web camera do not work but hope it will be fixed soon. My laptop model is HP Pavilion dv6-2150us 

My hardware configuration is as follows:

00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

---

### Post by tjwoosta on 2010-02-28
Everything has worked fine since I started using linux back around the time of ubuntu 7.10

Gateway ml6720

rtl8187b wireless card
intel gm965 integrated graphics
rtl8101e ethernet adapter
cd/dvd burner

---

### Post by cap10Ibraim on 2010-02-28
[CENTER][SIZE=4][COLOR=Red]Fully functioning with no problems [/COLOR][/SIZE]

     _**  [COLOR=RoyalBlue]TOSHIBA SATELLITE U405-S2911[/COLOR]**_
[/CENTER]

[LIST]
[*][SIZE=3]Intel Core 2 Duo Processor T6400 , 2.0GHz, 2MB L2, 800MHz FSB[/SIZE]
[/LIST]

[LIST]
[*][SIZE=3]Memory 4GB PC6400[/SIZE]
[*][SIZE=3]Storage Device : 250GB (5400RPM) Serial ATA hard disk drive[/SIZE]
[*][SIZE=3]DVD SuperMulti(+/-R double layer) with label flash [/SIZE]
[*][SIZE=3]Graphics : Intel Graphics Media Accerlerator 4500MHD with 128MB-1759MB[/SIZE] dynamically allocated shared graphics memory
[*][SIZE=3]Webcam and microphone built into LCD[/SIZE]
[*][SIZE=3]Intel Wi-Fi Link 5100AGN(802.11a/g/n)[/SIZE]
[*][SIZE=3]10/100 Ethernet[/SIZE]

[SIZE=3][I]but this list make me think is there a Labelflash application for Linux 
I use 64 bit windows7 but 32 bit Ubuntu9.10 , should I consider 64 bit Ubuntu ?![/I][/SIZE]
[/LIST]

---

### Post by Malakai on 2010-02-28
Asus 1000he is the hardware, fully updated Ubuntu Karmic is the OS. 


I have one single annoying issue but everything else works fine, Wifi and bluetooth both function perfect with multple types of devices and networks, all power management and suspend functions work basically the same as windows, and the battery lasts about the same time on Win7 & Ubuntu.

My one issue is the speaker volume is a bit low compared to windows, even pumped up to the max 115% or so in the control panel. I've been searching various sources for a fix for weeks, still no luck.

---

### Post by tjwoosta on 2010-02-28
> but this list make me think is there a Labelflash application for Linux 
I use 64 bit windows7 but 32 bit Ubuntu9.10 , should I consider 64 bit Ubuntu ?!


Actually thats a good point that I forgot about on my machine. As far as I know there is no native labelflash support in linux, but it might work through wine.

Yes, you should look into 64bit ubuntu :) Its probably not going to make a huge noticable difference, but it just makes since to take full advantage of your hardware. Certain things that require heavy processor usage will perform noticably better.

---

### Post by neu5eeCh on 2010-03-01
Running Ubuntu on Three laptops. 

One for the family (HP ZD7000): Suspend and Hibernation both fail though it works with 9.04. Mic doesn't work.

HP Paviliion DV1000 Laptop: Mic doesn't work.
HP Mini 1000: Mic doesn't work in any Ubuntu distro.

I've tried sleuthing the mic issue (following a variety of solutions), but it's a serious bug and beyond my abilities - for now.

Would love to know if the issues has been resolved in 10.04?

[**Edit:** Of all the folks who have said their computers have no issues with 9.10, I bet fully half or more can't use their mics.]

---

### Post by whiskeylover on 2010-03-01
Works completely with my Dell Inspiron 17. But it didn't work "out of the box". The wireless card's driver had to be installed by first plugging in the ethernet cord and downloading it.

Other than that, everything was good.

---

### Post by neu5eeCh on 2010-03-01
> **whiskeylover said:**
> Works completely with my Dell Inspiron 17. But it didn't work "out of the box". The wireless card's driver had to be installed by first plugging in the ethernet cord and downloading it.

Other than that, everything was good.

Have you tried a mic? I'm not trying to be a pain, just genuinely curious.

---

### Post by whiskeylover on 2010-03-01
> **VTPoet said:**
> Have you tried a mic? I'm not trying to be a pain, just genuinely curious.

You mean the inbuilt microphone? No, I haven't tried it. But the inbuilt webcam works. I'll give the microphone a try when I go home.

---

### Post by fewt on 2010-03-01
Where is the "I had to hack the crap out of it to make it work on my laptop(s)" vote option?

I pick that one.

---

### Post by undecim on 2010-03-01
Running 64 bit karmic on an HP TouchSmart tx2. After enabling proprietary drivers for the ATI, it works perectly.

Only thing I haven't tried is the fingerprint scanner, but since I use an encrypted home directory, it doesn't do me any good anyways.

---

### Post by breley on 2010-03-01
Everything seems to be working on my Dell XPS 1640 with 64-bit Karmic, though I installed the proprietary ATI drivers.  The one exception is the Ricoh Multicard reader, as described at [https://bugs.launchpad.net/ubuntu/+bug/311781](https://bugs.launchpad.net/ubuntu/+bug/311781). Referring to this blog, [http://intr.overt.org/blog/?p=59](http://intr.overt.org/blog/?p=59), I tried 

**setpci -s &#8216;09:01.0&#8242; 0xCA=0×57** (Write Enable)
**setpci -s &#8216;09:01.0&#8242; 0xCB=0×02** (MMC Disable)
**setpci -s &#8216;09:01.0&#8242; 0xCA=0×00** (Write Disable)

after doing an* lspci* but this did not work for me.

---

### Post by sideaway on 2010-03-03
Just bought a new Laptop Dell e4300 [http://www1.ap.dell.com/content/products/productdetails.aspx/laptop_latitude_e4300?c=nz&l=en&s=bsd&cs=nzbsd1](http://www1.ap.dell.com/content/products/productdetails.aspx/laptop_latitude_e4300?c=nz&l=en&s=bsd&cs=nzbsd1)

Inbuilt mic does not work
Two finger scrolling does not work
Finger print scanner does not work

But everything else did! :P

Anyone that can help me with the above, will be greatly appreciated :)

---

### Post by Ralph Hinkley on 2010-03-03
I chose "linux works perfectly on my laptop"

I've got an old Thinkpad (T-40? maybe???)
PentiumIII mobile CPU 933 MHz
Netgear wireless network card

I got the computer used, so I'm unsure about the rest.

---

### Post by fatdaddy on 2010-03-04
Dell Latitude D610  blue tooth wifi all good

---

### Post by Keith1212 on 2010-03-04
"Linux works completely with my laptop" 

Dell Latitude D520 
Genuine Intel(R) CPU           T2300  @ 1.66GHz (Dual-Core)
1GB Ram

---

### Post by teh603 on 2010-03-04
> **TusharG said:**
> I'm having trouble with Intel HD Sound and Video. However the laptop is brand new and the new i3 processor was launched on 7 Jan 2010. Ubuntu does not support most of the hardware out of the box. Infact I'm unable to hear sound and decent resolution on it. However I'm sure it will be fixed in 10.4 release. I'm waiting for 10.4 release. 
I know sound, video and web camera do not work but hope it will be fixed soon. My laptop model is HP Pavilion dv6-2150us 

My hardware configuration is as follows:ker-snippity!
> 00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 02)

Welcome to the Arrandale club!

Yes, we do get better support in 10.04. I'm testing the alpha on my Dell Inspiron 1564, and things get better with each set of updates.

Don't try Jaunty or Karmic on the Inspiron 1564, though. Jaunty goes into Vesa, while Karmic gives a black screen of death unless you use the Vesa driver.

---

### Post by conmat on 2010-03-06
[I]Linux works partially and I don't know why somethings don't work

[/I]Ubuntu 9.10 64-bit
Lenovo T400
Intel/ATI switchable graphics
8GB RAM

My biggest problem is random crashing.  Crashing seems to be completely random.  I can run an application for several days and everything is fine then my system will start crashing every 15 minutes.

I would like to be able to switch graphics.  ATI graphics drivers broke my first installation so I am afraid to install them.  I just run the Intel graphics with the native Ubuntu drivers.

I would like better  battery life.

Keyboard mapping still has problems.

I have lots of problems trying to compile programs from source.  I thought it would be nice to compile programs for 64-bit but I have never sucessfully installed a program from source.

---

### Post by mvalenti on 2010-03-08
I have not tried my mic jack or built in mic yet so I am unsure of these. My capacitive touch controls for volume and play,pause, etc do not work.  External headphone jack does not work either.

Acer Aspire 8730-6951
Ubuntu 9.04

-Mark

---

### Post by diogenes_3 on 2010-03-21
Just test driving Lucid 10.04 Beta 1 NRE on my Medion Akoya E1210 Netbook. Most stuff works nicely, but I can't seem to get WLAN (with WPA2) to work. The wheel keeps spinning, but no connection can be established.

Previous Ubuntus, as well as Easy Peasy have worked on the same hardware, as does Windows XP.

Ideas?

---

### Post by wizard10000 on 2010-03-21
Compaq (HP) Mini 110c netbook.  Everything works.

---

### Post by nettobr on 2010-03-25
kUBUNTU 9.10 working great on LENOVO 3000 G530 but HDMI

---

### Post by bosyber on 2010-03-25
Ubuntu karmic working pretty well on my laptop, and acer 6292. There are two non-working things, as far as I can tell: the fingerprint reader (I think for this chip
there are no working drivers yet); and somehow I have trouble getting the internal
mic to work, let alone get skype to use it. ... but I haven't recently tried to get it to work anymore.

---

### Post by Robin_216 on 2010-03-28
I have a Dell Inspiron 1750, Intel Core 2 Duo CPU P7450 @ 2.13GHz.

Standby and hibernate don´t work, although i don use those functions.

---

### Post by tica vun on 2010-03-28
Compal IFL91 with a broken screen - ubuntu server 10.04 beta. Ethernet works, and that's the only thing I need working on it.
Asus EeePC 901 - ubuntu netbook remix 10.04 beta - everything works out of the box.

---

### Post by Indroth on 2010-03-28
Linux works partially with my laptop-I will post the specific problem(s)

HP Compaq tc4400 (tablet)

Proprietary modem drivers cause sound to stop working (don't care... who uses a modem any more ;) )
Not all stylus functions work

---

### Post by bobin on 2010-03-28
HCL laptop with intel Dualcore chipset and nvidia GPU. Works out-of-the-box

---

### Post by rockwel on 2010-03-28
I have a Dell M90 with an ATI X1400. It works great. But I had huge graphics card problems with Ndivia FX2500. The FX2500 hardware actually died on me twice, third time round I switched to ATI X1400. And so happy I did. The 3D rendering will not be nearly as capable, but at least it works. Also, I was trying to get ubuntu 9.10 running on a older Dell Inspiron 2250. But it was not stable at all. More trouble that it was worth. That's why I went to the M90.

---

### Post by Random_Dude on 2010-03-28
When I was running Ubuntu 8.4 I had a lot of problems, including no sound and no wireless internet.
But since I installed 9.10 I only have 2:

[LIST]
[*]The disable touchpad button doesn't work.
[*]The camera is up-side down on skype.
[/LIST]

Apart from that, everything works fine.:biggrin:

---

### Post by Trinity33 on 2010-03-28
sure it does:) ubuntu 9.10 work perfect dont have anymore any problems:) there was one with my graphic its sorted then with sound card then mousse cursor after kernel update so i didnt know that i need to reinstall graphic driver and mousse work again.

laptop spec msi gt725
q9000 quad core 2ghz ddr2 4gb graphic ati hd4850 hdd 500gb sound  work too but need reconfiguration before it will work perfectly.

to be honest im very happy that i discovered ubuntu and generally linux. have much more fun then with win7, sometimes i boot up win7 just cos my tv doesnt work in ubuntu 9.10

---

### Post by MCVenom on 2010-03-28
Sorry, too lazy to post specifics :p

Everything works perfectly though -- webcam, microphone, flash player, etc. My laptop is an Acer Aspire 5520-5912. :D

---

### Post by dnairb on 2010-03-28
@Random_Dude

I had this issue on my Dell lappy (I think it is a very common issue). I dealt with it by disabling the driver for the touchpad-thingy as I never use it anyway.

In /etc/modprobe.d/blacklist.conf (you need gksudo priveleges to edit the file) add the following:

```
blacklist psmouse
```

---

### Post by Random_Dude on 2010-03-28
> **dnairb said:**
> @Random_Dude

I had this issue on my Dell lappy (I think it is a very common issue). I dealt with it by disabling the driver for the touchpad-thingy as I never use it anyway.

In /etc/modprobe.d/blacklist.conf (you need gksudo priveleges to edit the file) add the following:

```
blacklist psmouse
```

Does it solve the disable touchpad button problem?

The touchpad works fine, it's just the disable button. I don't use it anyway, the more important issue is the up-side down camera on skype (just skype, it works fine on cheese).

---

### Post by Hman242 on 2010-03-28
I have an HP Pavilion dv4 laptop and it work's without any problems. It's a little over one year old. My specs are as follows
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```

---

### Post by redrac on 2010-03-28
works perfectly acer 5516- 1.6 ghz athlon 64 tf-20  2 gb ram Radeon Xpress 1200 video. atheros chipset wifi.

not the fastest laptop but runs ubuntu great.

---

### Post by crucialhoax on 2010-03-29
HP Pavilion dv4 Laptop

Ethernet: Realtek 10/100 adapter
WLAN: Intel Wifi Link 5100 w/ script for LEDS
Graphics: Intel integrated -- supports compiz and extra appearance
Touchpad: Synaptics -- using syndaemon for touch control for typing
Card Reader: JMicron -- works correctly and recognizes all cards I have inserted correctly.
CD-Rom: Panasonic CD / DVD / Lightscribe drive: Tested all but Lightscribe.
- Supports all the touch buttons above the keyboard.
- IIRC all FN keys operate correctly.
- Display is wonderful.

Linux on this laptop has worked wonders. Vista used 1GB of RAM just to idle, sometimes more; Ubuntu 400MB :)

---

### Post by Ichido on 2010-03-29
Dell inspiron 1525n working very well.
Sound, Wifi "G", DVDs (VLC), SD Card Reader all working.
Minor problems now and then but the Forum Members are a great help in solving them.

---

### Post by Naggobot on 2010-03-29
Laptop model HP550

Only thing I have been bothered recently has been

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/458290](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/458290)

Now I voted that everything works, since I have not always been bothered by that particular bug. My system was originally installed with 8.10 and is now upgraded up to 9.10. 

I also have ACER5021WMLi but the bluetooth does not work on that model. I do not know if it is possible to make work. 

Then there is of course also mini laptop Acer aspire one with Linpus and 8gb SSD and yes despite what someone might say it does work perfectly.

---

### Post by user1397 on 2010-03-29
I'm using a Dell Mini 10v netbook and it runs ubuntu 9.10 perfectly...no problems whatsoever.

---

### Post by Wee_Guy on 2010-03-29
Not sure if this counts but Suspend has never worked on my custom built desktop PC, and I have had issues with graphics and the DVD drive before.

---

### Post by dnairb on 2010-03-29
> **Random_Dude said:**
> Does it solve the disable touchpad button problem?

The touchpad works fine, it's just the disable button. I don't use it anyway, the more important issue is the up-side down camera on skype (just skype, it works fine on cheese).

The blacklist psmouse code stops the touchpad working at all (my preferred behaviour) - I may have misunderstood your meaning re. disabling the touchpad.

Actually you can do this manually:

```
sudo rmmod psmouse
``` to unload the psmouse module and disable the touchpad, and ```
sudo modprobe psmouse
``` to reload and enable the touchpad.

---

### Post by Random_Dude on 2010-03-29
Thanks dnairb.

Like I said, the touchpad thing is not a big deal, it doesn't bother me.
The camera is the issue that I'll try to solve one day.

But I'll follow your advice if I ever need to disable the touchpad.
Thanks again!

---

### Post by eyeofreason on 2010-03-29
Satellite ,Intel , Ubuntu never a problem!

---

### Post by madjr on 2010-03-30
just wanted to mention that almost every Asus laptop that comes with expressgate (an instant-on linux) is 99% compatible with most modern distros.

i got one and works really well.

so aside from system76 and zareason, Asus is a good option (specially if you're outside the states where the guarantee may be hard to cover).

---

### Post by aklo on 2010-03-30
I have an Acer aspire one netbook. Everything works but recently the touchpad fail...i have no idea if it is spoilt or it is ubuntu netbook remix fault...i strongly believe is ubuntu's fault...

this is my only problem and since i use a mouse i don't really give a damn.

---

### Post by mgw2008 on 2010-04-21
Converted 2 Thinkpad T60's to Kubuntu now. Cold start-up time down to 25 sec vs several minutes under Windos. Have been using OO3 Firefox and TB for some time - the performance is considerable better now. 

Had to fiddle a little with WINE to get EAC running but works perfect now (of course the WINE1.2 installation under Karmic is still flawed. 

Also some minutes and forum browsing to get Squeezebox up and running.

I originally started with Ubuntu and switched from GNOME to KDE recently.

Trackpoint support is a bit dodgy.

---

### Post by Ravernomina on 2010-04-21
LOL SORRY POSTED IN WRONG THREAD xD

---

### Post by forcecore on 2010-04-21
HP DV 2525en, basically all Intel hardware almost. Ubuntu works out of box. Just avoid bad hardware laptops like with SIS video or others who make closed hardware devices.

1.67 GHz Intel Core2 Duo processor T5450
Intel Graphics Media Accelerator X3100
Intel PRO/Wireless 4965 802.11a/g/n
5-in-1 card reader (Ricoh)
14.1 LCD screen

Only fingerprint reader do not work but i do not need this so no problem.
I got this used laptop very cheaply too.

---

### Post by Guglielmo90 on 2010-04-23
[I]Linux works partially with my laptop-I will post the specific problem(s). Resume from suspend doesn't work on my vaio vgn-cs21s. Keyboard freezes on resume.
[/I]

---

### Post by tilixibr on 2010-04-23
The only thing that doesn't work on Linux with my Compaq CQ60 is the wireless light (it's constantly orange instead of blue when active) and the button to lock the touchpad (pretty damn useless.
The rest is pretty much working great!:D

---

### Post by FlapBags on 2010-05-06
> **aysiu said:**
> My previous laptop, which I've since given away worked perfectly with Ubuntu out-of-the-box. It was a Dell Inspiron 500m. The only thing I'll say is that when I bought it, it didn't have a wireless card inside. So I made sure to buy a Linux-compatible wireless card when I got one (Intel Pro Wireless 2200, thanks to recommendations from these forums).

I know run an Eee PC. Don't know if it counts as a laptop. It ran perfectly with Xandros as preconfigured by Asus. I installed eeeXubuntu on it, which included some Eee-specific tweaks, and it works almost perfectly, except that the boot time is now extremely slow, and resume from suspend doesn't work all the time any more.


Any ATHEROS based card will work with Linux, when it comes to wifi, dont buy intel crap, they are not the best at wifi. but  Atheros IS.

---

### Post by danciac on 2010-05-08
Hi everybody!
I am using an ASUS X59GLseries laptop with the latest 10.04 lucid. It is almost fully functionable but for one annoying problem I've been having. I am experiencing some trouble with the volume up/down and volume mute keys. The problem is that the effect of pressed keys is being felt after a lag of about ~20 seconds, and that's when the volume meter appears on the screen. Any ideas?

Thank you.

---

### Post by Shakz on 2010-05-08
I have a Dell XPS M1530 and Ubuntu works great on it. My only issue is that the sound when I got HDMI to the TV does not work. I have not taken the time to fix it yet but I am sure there is a way. Everything else works. 
It has a 256m Nvidia 8600 GT
500MB HDD
4gb of ram  3.4 as I am running 32 bit Lucid
Intel Core 2 duo T8300 @2.4ghz per core

I
LOVE
THIS
MACHINE!
Worth every penny and I would buy another in a heartbeat. Wish nix came preinstalled.

---

### Post by lashram on 2010-05-08
Ubuntu 10.04 Lucid as well as the previous release Karmic 9.10 both worked right out the box on my custom built laptop. Here are my specs:
 
[LIST]
[*]Based on NVIDIA® GeForce MCP79
[*]Intel Core 2 Duo T9400 processor
[*]4GB RAM
[*]NVIDIA® GeForce 8200M Graphics discreet w 256MB memory
[*]17" WXGA+ ( 1440 x 900 )
[/LIST]:guitar:

---

### Post by mamamia88 on 2010-05-08
everything in my laptop works fine.  it's compatability of public wireless networks that you should worry about.  i know my school you need to go out and  manually download the certificate to get you online.

---

### Post by smdeep on 2010-05-08
I have a Sony Vaio CR (VGN-CR23G). Everything works.

---

### Post by screaminj3sus on 2010-05-08
I still have two problems with my laptop:

By default my headphone jack does not work at all, but that is fixed by adding one line to alsa-base.conf (options snd-hda-intel model=eapd probe_mask=1 position_fix=1)

And I have an ati card. FGLRX is just awful, videos wont play without tearing no matter what and other issues. I am now using oss drivers and they are a b it better but power management sucks (its a little better using 2.6.34 kernel and enabling dynamic power management but it still sucks)


> **FlapBags said:**
> Any ATHEROS based card will work with Linux, when it comes to wifi, dont buy intel crap, they are not the best at wifi. but  Atheros IS.

My intel 4965 wireless works absolutely flawlessly in any disro out of the box.

---

### Post by rfry11 on 2010-05-08
> Linux works completely with my laptop-I will post my hardware specifics

My laptop is actually getting so long in the tooth, the only version of Windows that works even halfway is Windows 7, and the keyboard doesn't even work on it.

On Ubuntu, everything works, from the trackpad to the keyboard, wifi, and frustratingly the buggy wifi shut-off button.

---

### Post by andradelipe on 2010-05-14
Always have been a problem to upgrade my acer aspire 5520-1912. In all new upgrades nVidia stops! why? It's not common sense that if a hardware work in one version, the new version have to keep the support to it? i'll never know the reasons for this anoying thing...

---

### Post by dolphinsonar on 2010-05-16
With the new laptop I just bought everything worked, 'cept the built in microphone.  I just had to plug into the wall and run sudo apt-get update&&sudo apt-get upgrade from the terminal and restart a few times.

The built in microphone was a pain to fix, but I stumbled upon a year old post on ubuntu forums that fixed it.

Ten other unanswered posts about the same problem [-X  

I dutifully went back to all of those left hanging and linked to my solution.  Now I feel all warm and fuzzy for contributing back (at least a little) to the FOSS community!  Here is the solution to the built in mic problem, if you are one needing it:

[http://ubuntuforums.org/showthread.php?p=9307284](http://ubuntuforums.org/showthread.php?p=9307284)

---

### Post by chessnerd on 2010-05-16
Linux works partially on my laptop, here are the specific problems:

Back-light does not work without [this fix]("http://ubuntuforums.org/showthread.php?t=1331709"), which then causes Plymouth to look crappy.

GUI sometimes needs to be rebooted because GDM starts with black lines all over it (don't understand this problem)

Occasional full system freezing (this happened regularly with Karmic, has yet to happen under Lucid).

Overall, Linux is usable on my laptop and its benefits outweigh the problems.

EDIT: Lucid has now frozen four times in two days... Guess the problem remains. *Sits back and hopes for 10.10 to fix it*

---

### Post by Dragonbite on 2010-05-16
I'll have to remove my Dell Latitude D400 from the list temporarily, at least with Lucid.

I'm caught by the Intel Graphic 8xx issue. I should feel lucky, though, that this is really the first lasting issue I've run across with Linux installs on this machine.

I will be watching to see if Fedora has any improvement or work-around that works out of the box. If they do, I've noticed that Ubuntu is usually only 1 or 0.1 releases behind when something doesn't work in Ubuntu and does in Fedora.

---

### Post by parn on 2010-05-16
Acer TravelMate 8100

Intel 1.67 GHz Pentium M
2 GB System RAM
ATI Radeon Moblity X700 (128 MB RAM)
80GB HDD

Fedora 12, Ubuntu 9.10 - Works very well.
Ubuntu 10.04 - Works well.

Pros:
Installation is smooth, all hardware detected correctly. Performance is good running Open Office, Netbeans, etc.

Cons:
Video & Graphics performance is average. Video performance deteriorated  after upgrading to 10.04. Cannot watch movies (HD) with too many application running in the background.

Conclusion:
If you have one of these older notebooks and wish to get rid of Windows XP, just grab a live CD and fire away.

---

### Post by purelinuxuser on 2010-05-16
I've got a Dell Vostro 1000- there are plenty of problems to go around! :)

[LIST]
[*]Network - Broadcom BCM4328 - not supported natively by Linux, have to use ndiswrapper.  So, all I have to do is install ndiswrapper and the Windows driver, right?  Wrong.  The Ethernet card driver, b44 (which controls a Broadcom 4401), automatically loads ssb, which in turn automatically tries to control my wireless- which does NOT work at all :mad:.  So I have to make a boot script that unloads b44, then ssb, then ndiswrapper, and then RELOAD ndiswrapper and b44 in that specific order.
[*]Graphics - ATI Radeon Xpress 200M - believe me, I have FAR too many problems with this card.  For one thing, ATI dropped support for this card back in '08, so I have to rely on the open-source radeon driver- which is buggy in my experience.  KMS/modesetting problems on boot that render X unusable, perspective views screwed up in quite a few applications, low frame rates (not surprised though), Plymouth not appearing in some instances... the list could go on and on.
[*]BIOS - my system logs were being constantly filled with "unknown key pressed..." messages not so long ago, but they appeared to have suddenly stopped :confused:.
[*]Dial-up Modem - Conexant HSF Softmodem - I know, who the heck uses dial-up anymore?  Well, it can be useful if you are on vacation.  Unfortunately just TRYING to establish a connection using this thing usually ends up with a messed- up system and a broken Linuxant driver.
[/LIST]
So as you can see, my laptop has the best Linux support EVER!!!!!!!!!!!! :P

---

### Post by Dragonbite on 2010-05-16
> **purelinuxuser said:**
> 
Network - Broadcom BCM4328 - not supported natively by Linux, have to use ndiswrapper.  So, all I have to do is install ndiswrapper and the Windows driver, right?  Wrong.  The Ethernet card driver, b44 (which controls a Broadcom 4401), automatically loads ssb, which in turn automatically tries to control my wireless- which does NOT work at all :mad:.  So I have to make a boot script that unloads b44, then ssb, then ndiswrapper, and then RELOAD ndiswrapper and b44 in that specific order.


Could give Fedora 12 a try; they include the OpenFWWF drivers which allowed my Broadcom wireless card to work out-of-the-box.

---

### Post by lklk on 2010-05-19
Everything except the SD card reader seems to work on my ThinkPad x61t. Modem, PC card/cardbus/what ever the external expansion slot is, and sim card slot,  were never tested.

---

### Post by Chrisco66 on 2010-05-19
I was running 9.10 on my laptop, and my g/f MSI Wind 100.  Both were working perfectly.  When I did the upgrade on my laptop, everything seemed fine.  I used it for a few hours and put it away.

Soon after, I did the upgrade on the g/f wind, and the wireless card will not connect to encrypted networks (like mine).  When I turned on my notebook, the video was moving about 1/4 of normal speed.  Very annoying.

After doing some research, I found instructions on how to install the drivers for my video that were no longer included in Ubuntu.  

The wireless problem remains.

I dont like to complain about things, but these are two problems that leave a laptop pretty much useless.  I heard numerous complaints about 10.04 before I upgraded.  I know that sometimes people complain about anything new, so I ignored most of the complaints.

However, it seems to me that 10.04 is not as solid as a LTR should be?  Foe example, and this is not laptop related, but I just found that Brasero, software that I have used since 7.04, no longer works with 10.04.  

I am left with two partially functioning computers.  I will try to find answers to these problems, but if I cant, now what?  Back to Windows?

---

### Post by sacredpotato on 2010-05-20
I have an HP Touchsmart tx2-1025d everyhthing works with just a little work ... at least everything I use (I haven't looked into the thumbprint reader) I'm working with some guys in another thread to nail down my last nagging issue (rotating the touchscreen input when the display roatate and we almost have it working ^_^


I gotta say I couldn't have done any of it without the help and support of this community. the ubuntu community above all other is just amazing thank you to all of you that contribute on a daily basis to help noobs like me make the conversion. I have been playing with ubuntu on my tablet since 8.04 and Lucid has finally allowed me to completely replace windows on here ^_^. not only does Lucid reboot, shut down and boot up faster than win 7 everything is faster including hulu and youtube in full screen. The system also run A LOT cooler (doesn't even get very warm after HEAVY use were as idling for too long in win 7 caused the underside to get hot to the touch).


ok that is enough sleepy rambling tl;dr I LOVE LUCID AND THIS COMMUNITY!!!!

---

### Post by koolblue3 on 2010-05-20
Everything works on my Eee PC 1000 with UNE 10.04. I know this is a netbook but it is kinda like a laptop.

---

### Post by apuglisi on 2010-05-21
Hi there,
my laptop is an Acer Aspire 5720-Z:
Intel T2390 dual core CPU (i think it's 1.8GHz)
Intel GMA 965 video
2Gb RAM
160Gb HDD

and my only unsolved problem was (and still is) the suspend to ram thing. I've never been able to suspend to ram my laptop, with any of the ubuntu distros I've used.

The rest works flawlessly: audio, internal mic and webcam, SD card reader, DVD, multimedia keys, wireless, etc.

---

### Post by forrestcupp on 2010-05-21
Where's the option for "Linux works completely with my laptop, but I will not post my specs"? :)

---

### Post by lvleph on 2010-05-21
Gateway LT3103u

```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f0000000-f01fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: 80000000-800fffff
	Prefetchable memory behind bridge: 00000000cfd00000-00000000cfdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: f0200000-f02fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8440 [size=8]
	I/O ports at 8434 [size=4]
	I/O ports at 8438 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8400 [size=16]
	Memory at f0508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: 66MHz, medium devsel
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8420 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=64

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9000 [size=256]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel modules: radeon

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:028c]
	Flags: bus master, fast devsel, latency 0, IRQ 26
	I/O ports at a000 [size=256]
	Memory at cfdef000 (64-bit, prefetchable) [size=4K]
	Memory at cfdf0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at cfd00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e016]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

---

### Post by Objekt on 2010-05-21
Oops, I meant to also vote "works perfectly" in addition to one "partial."  Details:

-Acer Aspire One D150 netbook.  Everything works, except for the "wireless on/off" switch.  A minor point, as it is very easy to turn wireless on/off in NetworkManager.  With a recent BIOS update, power management works perfectly, and I get just as good battery life in either Ubuntu Netbook Remix 9.10 or Windows XP.  Mega-win here.

-I also put Ubuntu Netbook Remix 9.10 on a Toshiba Satellite U405D-S2850.  As far as I know, everything works, although I haven't tried burning a DVD or CD.  The Satellite has a built-in ATI Radeon 3100 3D accelerator.  I was able to install the proprietary ATI driver package.  Not sure whether battery life is as good as with the supplied, OEM OS (Vista Home Premium 32-bit).

So there you are.

---

### Post by Chesamo on 2010-05-21
"Linux works completely with my laptop-I will post my hardware specifics"

IBM Thinkpad T60
Intel Core Duo 2.4 GHz
1 GB DDR2 RAM
ATi GPU (Don't remember the specifics right now)

---

### Post by Shazzam6999 on 2010-05-21
Everything works fully!
Arch Linux

Acer Aspire 5515
AMD Processor 2650e 
ATi x1300
Broadcom 4312 something or other.

That's just off the top of my head since I'm on my desktop. Astonishingly, I don't even really have to configure anything.

---

### Post by quinne on 2010-05-21
Hi all, I'm new to Ubuntu and the forum, but not to Linux.  I've been using another OS on my desktop for many years.  I recently bought a laptop, but my old OS just couldn't hack it.  I tried half a dozen other Linux flavors before trying the Lucid Lynx 64-bit.  It was able to work from the get-go on video and wireless internet (thank you, Ubuntu!!!!, I'm impressed!)

As for remaining issues...

My machine is an HP DV7 3165dx.  Issues still remaining (and I will delve into in the appropriate forum sections in an effort to get them resolved):

--Even though I've got the power settings to suspend 'never', it still goes into suspend after a few minutes of inactivity, and I have to log back in again.

--I used Unixmen's great tutorial on how to get the sound working (using Linux backports).  I'm happy to say the sound works now, however, the pc speakers won't mute when I have the headphones in.  

Most important of the remaining problems, is trying to get the my HP All-In-One (model C4795), which works flawlessly over USB, to work wirelessly with the laptop.  I've read through reams of material, and have made partial progress (in that I've at least filled in all the missing dependencies that came up in the terminal HP-check), but at this point, the laptop still can't see the printer on the network.  I know this has been an issue for others, and no doubt some sort of fix is in the works.

As I say, given the herculean task of tailoring an OS to work with so many different hardware configs, I'm very impressed with this newest incarnation of Ubuntu.  Thanks to all involved for all of your excellent work.

---

### Post by Shining Arcanine on 2010-05-21
Why is this a multiple option poll? I voted all 5 options by the way.

---

### Post by cph05a on 2010-05-21
I have a dell XPS M1330. Everything works out of the box (and it should because it was an Open Source PC that was supposedly built for linux)

I also have a macbook pro 5, 5. Everything works now, but not out of the box. The trackpad driver that came with ubuntu was no good, so I wrote one. I also had some trouble with the nvidia video card, but it was solved by downloading it from the nvidia website and letting their tool built the kernel module. Everything works great now!

---

### Post by barretme on 2010-05-27
I have a black Macbook 3,1.

Only things I cannot get to work are the Bluetooth and the iSight camera. I tried installing the isight firmware through the software directory but still no go. Any help would be great.

---

### Post by clgy15 on 2010-05-27
Compaq Presario, 2GB DDR2, 2 AMD Turion 64, Nvidia gforce
Perfect in all aspects

---

### Post by TheSqueak on 2010-05-27
Toshiba Tecra M10 with Lucid

Everything, including the inbuilt bluetooth, worked immediately after installing Kubuntu

---

### Post by libssd on 2010-05-27
Ubuntu 9.04 running on an Acer Aspire One D150, generic netbook hardware. Had to update BIOS to resolve a suspend problem, and go to kernel 2.6.30-020630 to make the WiFi indicator LED blink properly, both extremely minor problems. Rock solid.

---

### Post by shcherbak on 2010-05-27
Sony Vaio VGN-FW11M

Only Counter-Strike 1.6 crash from time to time on fglrx driver
or wine issue... and do not hibernate (or rather de-hibernate) 

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
0a:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

---

### Post by fredbird67 on 2010-05-27
We have a 2005 Dell Inspiron 6000 that works perfectly under Linux -- but NOT Ubuntu.  At least not without all sorts of fooling around with the command line, anyways.  It can be done under Ubuntu or Mint (I pulled it off once on Xubuntu, in fact), but it's a ROYAL pain to do so.

The only hardware specs I know right off the top of my head about that laptop are that it has 512 MB of RAM and a Broadcom 4311 "AirForce" wireless card.  Like I said, that Broadcom wireless card is a PAIN to configure to get it to work with Ubuntu.

However, about a month ago, I discovered two distributions that properly detect the Broadcom right off the bat.  Mepis does, but it comes with KDE 4, which was too much for the Dell's 512 MB of RAM, and the live CD soon ground to a halt after connecting wirelessly.

The only other distro I've tried with it that properly detects the Broadcom card is PC/OS.  And since PC/OS comes with Xfce (which is my desktop environment of choice, anyways), it doesn't bog down one bit, making me a VERY happy camper! B-)

Like I said, using PC/OS on it instead of Ubuntu is my secret to turning the Dell into a fully functional Linux laptop.  BTW, PC/OS is based on Ubuntu, so it'll sort of be like running Xubuntu -- except that PC/OS automatically detects the wireless card out of the box and Xubuntu doesn't.  If you have a laptop with a Broadcom wireless card, I'd definitely recommend giving PC/OS a try.  I think you'll be happy you did.

---

### Post by ibuclaw on 2010-05-27
Fully functional laptop.

Model is Samsung N110, and had flashed the BIOS prior to installing Linux on it ... something to do with fixing vertical scrolling if my memory retains correctly...

```

BIOS Information
	Vendor: Phoenix Technologies Ltd.
	Version: 07D0.M012.20090908.RHU
	Release Date: 09/08/2009
	Address: 0xE6640
	Runtime Size: 104896 bytes
	ROM Size: 2048 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		ACPI is supported
		USB legacy is supported
		Smart battery is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 7.0

System Information
	Manufacturer: SAMSUNG ELECTRONICS CO., LTD.
	Product Name: NC10/N110                  
	Version: Not Applicable

```

Regards
Iain

---

### Post by bigseb on 2010-05-28
Acer Aspire 7720G

Works perfectly :)

---

### Post by R Clemons on 2010-05-28
Acer Aspire 5740G-6979 works perfectly even with the ati driver in the repos.

I have always bad luck getting 3d graphics to work, but with this ATI mobility radeon HD 5650 and Ubuntu 10.04 it worked right out of the box.

---

### Post by sirthomas711 on 2010-05-28
Dell Inspiron E1505 with Intel Core 2 Duo, Sigmatel Audio card(not sure specifically), ATI Mobile Radeon X1400, Dell Wireless-N Card(once again not sure specifically).  Everthing works just fine, except that I can get Ubuntu to recognize my HDTV from the VGA port, even so far as being able to determine that it's a Sony HDTV and the available resolutions, however, it will not send a signal to it.  I just installed 2 days ago, and have had limited time to tinker, and have never used any Linux distro before, so I may run into more problems later.

---

### Post by cgb on 2010-05-28
Dell Latitude E6400, NVIDIA Quadro NVS 160M, Intel Wireless WiFi Link 5100..  Everything appears to be working great in Ubuntu for almost a year..  Currently running Jaunty on this machine but have ran live cd of Lucid and also appears to work fine..

---

### Post by randumnumber on 2010-08-05
Both of my systems specs are listed below, i have had no trouble with either machine. When i first set up my Laptop i had to configure the ALSA because my microphone jack was turned all the way up causing a weird buzzing noise in my speakers. This option was not available in the GUI so i had to do it at command line. But, since then the options have been moved to the GUI.

Ive had my laptop for 4 years running ubuntu it still purrs like a kitten.

---

### Post by Veracruz290 on 2010-08-06
[I]Linux works partially with my laptop-I will post the specific problem(s)
**Toshiba Satallite L505 ES5025 Installed Ubuntu 10.04**
Problems: 
1) Numeric Key Pad Not Operational.
2) Mic is buggy. Sound routes thru speakers but not present on a video audio conference?
Otherwise this has been a great first experience for me with Linux. Ubuntu seems fairly straight forward.
Does anyone know of a fix for either the Keypad or the Microphone?[/I]

---

### Post by TNT1 on 2010-08-06
HP 6730b (dual core 2.26ghz, 4GB RAM) - Everything works perfectly... (the built-in 3G didn't work in Fedora 13 untill I recompiled the kernel, currently running Lucid, all works (after adding gobiloader etal...)
Lenovo T63 - Everything works perfectly (excepet the touchpad, but that's cause my wife spilt a glass of red wine on the laptop... Damn thing didn't start up for a month, I replaced it with a Toshiba, and the the Lenovo decided to fire up again...)
Toshiba M400(dual core 1.8ghz, 2GB RAM & an awesome graphics card - dunno what it is, but in windows in can display 1400x1050, and running Lucid it goes up to 1600x1200... On a 12.1" screen... It's staggeringly good quality...) )  - Everything works perfectly (needed to install toshiba utils to get the hardware buttons to work, even the touch screen worked straight away with Lucid install...)
I previously used a HP8710, Kubuntu 9.10, worked fine...

---

### Post by Mike BFD on 2010-08-06
Toshiba Satellite U300 works perfectly.
Compaq Presario A970 was overheating until newer kernels were released.

---

### Post by TNT1 on 2010-08-06
Oh, wait, currently my windoze button doesn't work, but I think I selected the wrong keyboard layout during installation... (I never used it even during windows days, so no loss...)

---

### Post by What Rights on 2010-08-06
HP G60-121WM

Terrible Graphics Quality, Tearing.
Lag When Playing Video
Slower then normal Boot
Audio Pauses and Skips (there is fix)

---

### Post by Cabalbl4 on 2010-08-06
Toshiba satellite A210P works perfectly with 9.10, the only thing that does not work out of the box - bluetooth drivers (with phoenix bios). To get bluetooth working omnibook module must be compiled.
10.04, however, has a lot of issues with ath5k wlan driver, so I've rolled back to 9.10.

---

### Post by dazndom on 2010-08-06
i voted that everything works outa da box.....

i bought 2 Hp computers, one laptop, one desk top

laptop :-)HP Pavilion dv6-2144TX
Intel Core i3-330M ((Dual Core) 2.13GHz/3MB L3 Cache)
4GB DDR3 RAM
500GB 7200rpm SATA HDD
DVD+/-RW dual layer with LightScribe drive
15.6 inch HD (1366 x 768) High Definition BrightView display
nVIDIA GeForce GT 230M (1GB dedicated)
10/100/1000 LAN, 802.11 a/b/g/n WLAN, 56k modem
SRS Premium Sound with Altec Lansing speakers, webcam, 5-in-1 media card reader, Express Card slot

everything works, webcam and mic even on skype, sound volume slider, 3d graphics and wirless  NO PROBLEM
1 small problem with touchpad LOCK, it would not UNLOCK - ubuntu forums fix !!!!!!

desktop ;
HP Pavilion Slimline s3880a media desktop.

Slimline Tower Form Factor
Intel Core 2 Duo E7400 ((Dual Core) 2.8GHz/3MB L2 Cache/1066MHz FSB)
2GB DDR2 RAM
500GB HDD
DVD+/-RW dual layer with LightScribe drive
NVIDIA GeForce G100 with 256MB dedicated video memory
Integrated 10/100 LAN, 802.11 b/g WLAN
HP DVB-T TV Tuner, integrated audio, 15-in-1 media card reader

everythings works except keys for playing music

NO COMPLAINTS at ALL with my HP computers
ALSO HP printer works perfectly
;) :D

---

### Post by Zorgoth on 2010-08-06
Dell Studio 15
Intel Core i7-720QM
4 GB DDR3
ATI Mobility Radeon HD 5470

Linux works great (although I still have to get the drivers from ATI's website for full support of my card)!

---

### Post by paultowlson on 2010-08-08
I have a Dell Inspiron 1750 which worked fine with Kubuntu 9.04 but since 9.10, 10.04 the Broadcom wireless card is not supported. I have tried many solutions offered on various websites but with no success. With Wicd I can see wireless routers but get a password error, or unable to find IP address if an open network. SuSE has the same problem, so for present I am staying with Kubuntu 9.04 until a solution turns up. Why does Broadcom have to be so difficult??

---

### Post by gvernold on 2010-08-12
Dell C640 laptop - worst Linux experience I've had since I started using it in 1996. I'm on 10.04 and it's very, very unstable. The hard drive access is slow, USB access is slow, I get screen corruption in many terminal programs, the wireless card doesn't work properly with it and the machine freezes and crashes and random intervals about 4 times a day. Looks like for the first time ever I'm actually going to be forced into a hardware upgrade which was the main reason I walked away from Windows 14 years ago.

I really object to having to ditch equipment which still works perfectly well because software dictates it. Ubuntu has been by far the best distro for laptop support that I have used but Fedora seems to have a bit more flexibility for supporting some of my older hardware and it's easier to strip down for optimization.

---

### Post by Fludizz on 2010-08-12
Lenovo ThinkPad w510 works like a charm under 10.04, just the fingerprint reader isn't supported yet. It is too recent, the support is in the development version of the fingerprint software but not in the stable release yet.

---

### Post by lz1dsb on 2010-08-12
Dell Studio 15 running Ubuntu 9.10. Works fine. I don't have any complaints. Even the functional keys work after finding a little tweak on that forum...

---

### Post by admiralspark on 2010-08-12
LAptop running Linux Mint 9 x64 (ubuntu-based but better) with first gnome and now KDE. Everything works 100% as I've found happens on most Lenovo's (in fact, the only comp I had a problem with was an IBM R51 with a i8xx graphics card). My specs:
***Lenovo Y560***
**Core**--Intel i7 Q720 with working hardware virtualization! Virtualbox loves using the other four cores! haha
**Graphics**--ATi Radeon 5730 1GB dedicated with fglrx driver--100% 3D
**Screen**--15.8" HD Widescreen. EXCELLENT color and clarity, bit of glare but the backlight works good enough to cover most of that.
**Wireless**--Intel Wifi Link 1000 with zero problems.
**RAM**--8GB Ram, again, for virtualbox
**Physical Memory**--500gb harddrive, only problem I had here was my windows install had three primary's and one extended partition due to one-touch backup, I had to put all my linux distros in the extended partition. Works great though.
**Sound**-- This worked perfectly fine in GNOME, in KDE for some reason you have to go in and move all of the volume sliders over to active, and turn em up. Took me all of 5 minutes because I've done it before every time I've used KDE, but still stupid that it's not done by default. Audio quality in both is pretty good through the JBL speakers this thing comes with, though the windows driver in Win7 sounds more concert/stereo-like. I'm looking for a mixer to fix that. Still a VAST improvement over my old compaq. 

I use a split Mint 9 KDE x64/Windows 7 x64 install, both boot fine from grub with no issues. If you can afford the $1000 price tag on one of these, I recommend it 100%. And if you deny the Win7 license you can get like a $200 credit too.

EDIT: forgot to add, CD/DVD playback and burning works great, so does bluetooth and SD card reader. And all plug ports such as Ethernet, HDMI, all USB's, mic and headphone plugins. Also, webcam and built in mic's works OOTB in Gnome and KDE.

---

### Post by sgtslwilson on 2010-08-13
> **koolblue3 said:**
> Everything works on my Eee PC 1000 with UNE 10.04. I know this is a netbook but it is kinda like a laptop.

I also have an ASUS Eee PC 1000HE. Everything works right out of the box with UNE 10.04

I am very impressed and I don't even dual boot anymore. Pure Linux now.

---

### Post by frogo on 2010-08-13
I have a Dell Latitude E4310 

I have problems with multimedia and sound which I'm done trying to figure out, I just don't use the machine for multimedia & sound task, including VoIP

The major problems for which I can find no solutions and make me doubt whether ubuntu is sustainable on this machine are:

- batteries are drained in stupid fast time which make me doubt that i have a laptop rather than a compact desktop considering the fact i have to be hooked up on power outlet all the time

- doesn't resume from suspend or hibernation which is a real pain when all is said even if I'm trying to take it easy and not be too grumpy when I have to close all my active tasks because i need to shutdown the computer instead of suspending/hibernating

---

### Post by ceref on 2010-08-13
Ubuntu 10.04 Lucid works like the dreams we had when working in binary :popcorn: I became a corporate enforced windows user. I am free of work now and scrapped windows XP on this old acer travelmate 4400 that had been made redundant by gates & co. It has an AMD Turion 64 ML 28 and only 496 MB memory. After the end of a loving relationship with FireFox on Windows XP, Vista and Sorrowful 7 and till recently on Ubuntu 10.04 I kicked it out for Opera. 
Its still early days for me and still getting used to all that Ubuntu has to offer.  I can even get back onto Guild Wars ... 

I now say great name Microsoft because by comparison a body can do so very little with micro freedom compared to the massive size of Windows software.   

We are flying high .. its all great .... Thanks Ubuntu you have put joy back into human development and potential:popcorn:.

---

### Post by x-shaney-x on 2010-08-13
When I was looking around for a new laptop, I did note the hardware and my aim was to find something that would work 100% with current open source drivers.

As it turned out, the only hardware problem I have had is regarding sound which is fully supported in newer alsa versions.

In the real world I have found my soundcard is problematic or doesn't work at all in any debian based distro tried but works 100% in every rpm distro tried.

---

### Post by sheepo on 2010-08-13
Linux almost works perfectly on my laptop. The only problem is that the wireless doesn't work, so I simply plugged in a usb wireless.

---

### Post by MooPi on 2010-08-15
Not my laptop but my bosses. Compaq Presario F700 with a borked Vista install. It was so borked that the recovery partition wouldn't work. Very nice laptop for under 300$ a couple of years ago. Fully works no issues.

```
H/W path      Device      Class       Description
=================================================
                          system      Compaq Presario F700 Notebook PC
/0                        bus         30EA
/0/0                      memory      109KiB BIOS
/0/3                      processor   AMD Turion(tm) 64 X2 Mobile Technology TL-58
/0/3/5                    memory      128KiB L1 cache
/0/3/6                    memory      512KiB L2 cache
/0/b                      memory      2GiB System Memory
/0/b/0                    memory      1GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/b/1                    memory      1GiB DIMM DDR2 667 MHz (1.5 ns)
/0/4                      processor   
/0/4/0                    memory      128KiB L1 cache
/0/4/1                    memory      512KiB L2 cache
/0/5                      memory      RAM memory
/0/1                      bridge      MCP67 ISA Bridge
/0/1.1                    bus         MCP67 SMBus
/0/1.2                    memory      RAM memory
/0/1.3                    processor   MCP67 Co-processor
/0/2                      bus         MCP67 OHCI USB 1.1 Controller
/0/2.1                    bus         MCP67 EHCI USB 2.0 Controller
/0/e                      bus         MCP67 OHCI USB 1.1 Controller
/0/4.1                    bus         MCP67 EHCI USB 2.0 Controller
/0/6          scsi0       storage     MCP67 IDE Controller
/0/6/0.0.0    /dev/cdrom  disk        DVDRAM GSA-T20L
/0/7                      multimedia  MCP67 High Definition Audio
/0/8                      bridge      MCP67 PCI Bridge
/0/8/5                    generic     R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
/0/8/5.1                  generic     R5C843 MMC Host Controller
/0/8/5.2                  generic     R5C592 Memory Stick Bus Host Adapter
/0/8/5.3                  generic     xD-Picture Card Controller
/0/9          scsi2       storage     MCP67 AHCI Controller
/0/9/0.0.0    /dev/sda    disk        160GB WDC WD1600BEVT-0
/0/9/0.0.0/1  /dev/sda1   volume      29GiB EXT4 volume
/0/9/0.0.0/2  /dev/sda2   volume      117GiB EXT4 volume
/0/9/0.0.0/3  /dev/sda3   volume      2047MiB Linux swap volume
/0/a          eth0        network     MCP67 Ethernet
/0/c                      bridge      MCP67 PCI Express Bridge
/0/d                      bridge      MCP67 PCI Express Bridge
/0/d/0        wlan0       network     AR5001 Wireless Network Adapter
/0/12                     display     C67 [GeForce 7000M / nForce 610M]
/0/100                    bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration
/0/101                    bridge      K8 [Athlon64/Opteron] Address Map
/0/102                    bridge      K8 [Athlon64/Opteron] DRAM Controller
/0/103                    bridge      K8 [Athlon64/Opteron] Miscellaneous Control

```

---

### Post by dewdrop_world on 2010-08-20
Ubuntu 10.04 on a MSI A6200 (Intel Core i3). It's running great! except...

- WiFi can't authenticate to WPA networks after waking from suspend. Google showed me a thread on these boards that might help, but I don't have time to digest it now.

- I've tried a number of mail clients, and they all make my machine blow up -- apps randomly crashing or failing to start. [http://ubuntuforums.org/showthread.php?t=1555602](http://ubuntuforums.org/showthread.php?t=1555602)

Those were minuses - here's a plus:

+ Dragon NaturallySpeaking 10 with WINE. Possible to crash it but it works pretty well.

Yet to try: ExpressCard firewire + ffado drivers for a MOTU UltraLite. That scares me a bit... postponing until a big project is done.

James

---

### Post by lordhaworth on 2010-08-20
My issues are:

webcam - doesnt work (picked up in cheese but thats it)
wireless - works mostly, but I have had problems with certain router


other than that, nothing too much - it may be that my issues above could be fixed too... but i have never figured out how.

Running Jaunty on a dell inspiron 15something

---

### Post by V for Vincent on 2010-08-20
Asus eee 1201N. Works perfectly, AFAIK, with a few tweaks and the right wireless driver. There seems to be an issue with the 2.6.32-24 kernel, but -23 works fine.

---

### Post by Johnsie on 2010-08-20
Another wifi issue.. There seems to be alot of people with wifi problems in Ubuntu.

Ubuntu doesn't support the RA3090 wifi card in EEEPC 1001HA machines. There is a ppa with a driver but that driver only supports WEP. WPA doesn't work at all. I had to install Windows on those machines to get proper wifi connectivity.

---

### Post by blchinezu on 2010-08-20
[[IMG]http://www.notebookcheck.net/typo3temp/pics/b471e1a352.jpg[/IMG]]("http://www.notebookcheck.net/uploads/tx_nbc2/310142.jpg")
**Notebook:** Asus X55SV
**Processor:** [Intel Core 2 Duo T9300]("http://www.notebookcheck.net/Intel-Core-2-Duo-T9300-Notebook-Processor.26538.0.html")
**Graphics Adapter:** [NVIDIA GeForce 9500M GS]("http://www.notebookcheck.net/NVIDIA-GeForce-9500M-GS.8167.0.html")
**Display:** 15.4 inch, 16:10, 1440x900 pixels

Works flawlessly with Ubuntu. There was a sound problem with Karmic which was not present in Intrepid but got fixed in Lucid.

---

### Post by Daletec on 2010-08-20
Ubuntu 9.04, 9.10 and 10.04LTS work fine on my Dell Latitude D620.  I did have to connect to the net via LAN and then enable proprietary drivers to download the WLAN drivers for my Broadcom internal wireless adapter.  Desktop effects work fine with the Intel graphics, I haven't tested the smartcard reader, no need for it, really.  I haven't used Windoze on this laptop in two years, I won't go back!  Ubuntu for life!!!

---

### Post by del_diablo on 2010-08-20
Fujitsu Siemens Pa 3553:
*Wlan is shady, some distroes got it out of the box and others do not. (The kernel) Recently got kernel support for the randomly updated driver.
*I got the Turion X2 model, the BIOS got a complete lack of ACPI support

Other than these 2 issues: It is a quite enjoyable experience.

---

### Post by kevinatkins on 2010-08-20
IBM ThinkPad T60. Everything works, except that with a default install, the on-screen display of volume doesn't show when the volume keys are pressed, but it's easy to sort. Even the fingerprint reader can be made to work (although I don't bother with it)...

Compared to the Windows XP Pro also installed on the machine, Ubuntu absolutely flies - it's genuinely quick!

---

### Post by snip3r8 on 2010-08-20
I got Karmic running on an old AMILO D 7850,the system is dodgy because the hdd is failing  but linux pressures on,it's the only OS this thing will accept.It doesn't even want to read the Windows XP disk half the time ,the other half it takes one look at it,goes "screw this" and shuts down.

---

### Post by tjktyler on 2010-08-20
HP dv5t 2000 series: 
 * Touchpad is really sensitive, i.e. only the very bottom won't register touch for clicking. Very annoying, because this makes clicking and dragging nearly impossible (without an external mouse). Also, the upper left corner of the touchpad has an LED indicator which shows if the touchpad is activated or not. This doesn't work, nor does double-tapping the area, which is meant to activate/deactivate the touchpad (as appropriate)
 * Broadcom 43224 chipset (dual-band wireless-N and Bluetooth) has iffy support, but this an issue with Broadcom, not Ubuntu. 

Apart from those two issues, Ubuntu has been more than pleasant. Installation went smoothly, laptop-mode-tools helped tune everything for power savings, I'm getting solid battery life. It's a good computer, but next time I'm sticking with the Intel wireless adapter.

---

### Post by loxety on 2010-08-20
10.04 works great on my ASUS G50VT-x5

---

### Post by khelben1979 on 2010-08-20
OS: Debian 6.0 "Squeeze"
Desktop: uses LXDE

Hardware: Powerbook G3 Lombard
RAM: 128 MB
Harddrive: 4.9 GB

Everything works okay about the software. The hardware got some defects, but Debian works just fine. Some smaller software crashes due to low RAM and the monitor screen flickers at times, but when it's stable it's quite good against my eyes.

I've been running Debian on it since Woody (released in 2002) on this Powerbook. Before that it was Slink on the m68k architecture on an A4000. It's been a while..

---

### Post by Austin25 on 2010-08-20
There are a couple of proprietary drivers for the wifi and the graphics card, as well as I had to install drivers for the touchscreen, but all in all, it works.

---

### Post by Dustin2128 on 2010-08-20
worked 100% out of the box since 9.04

---

### Post by Papagaulo on 2011-03-07
I have a fujitsu t4020 that doesnt even function properly in xp or vista screen doesnt rotate no sound in vista, yet everything works 100 percent in ubuntu 10.04 touchscreen sound rotation screen buttons everything even onboard keyboard pops up when I rotate the screen I am the type that roots for the under dog and I have seen linux grow by leaps and over the last three years and I don't think we are the underdog anymore.

---

### Post by teward on 2011-03-07
Hardware specs are in the link in my sig, since i dont have the energy to repost multiple systems' specs ;)

And it works epicly on both systems. :cool:  One's Dell, one's HP.

---

### Post by mmsmc on 2011-03-07
i have all compiz affects enabled, screenlets, and 100's of programs on my 5 year old computer, and it works like its brand new
Intel(R) Pentium(R) M processor 2.13GHz, my graphics card is in the screen shot

---

### Post by Rasa1111 on 2011-03-07
Linux works perfectly on my laptop. 
IBM Thinkpad Z61t. with 2 GB RAM.

All other laptops Ive installed Ubuntu on works perfectly also. 
Too many to remember each one.

---

### Post by bford16 on 2011-03-09
My machine is an HP dv7-1232NR.  It runs great on Ubuntu 10.10, with no special tweaks.  This machine has a 2.2GHz 64-bit processor, and the ATI Radeon HD 3200 built-in graphics.  I have 4 GB of RAM installed.  I just tried hooking up a bluetooth dongle and some Plantronics Backbeat 903+ headphones, and I can happily report that both work perfectly.

Suspend works fine, but hibernation is pretty much a bust.  I wouldn't use hiberate anyway, because resume is very very slow.

---

### Post by sffvba[e0rt on 2011-03-09
HP 530 works great! (Google it, to lazy to find and post the specs now myself :p)


404

---

### Post by wgarider on 2011-03-09
Inspiron M5030 - [install was interesting]("http://ubuntuforums.org/showthread.php?t=1653959")....had to do some editing to grub to get everything working right but otherwise, its very capable and the price was right.... ;-)

---

### Post by sprocket10 on 2011-03-09
Linux works completely with my laptop!
Hardware specs:
Dell E1505
1.66Ghz Intel Dual Core Processors
2 GB Ram
320 GB Western Digital HD @ 7200rpm
Windows 7 & Ubuntu 10.04 (Lucid Lynx) Dual Boot - Both 32 bit
DVD drive stopped working but I'm not sure if that's related to linux issues
Broadcom wireless card
ATI Radeon Mobility X1300 (128MB)

*Install windows first, then use windows tool to shrink partition. THEN install Ubuntu!

---

### Post by ShaneNZ on 2011-03-10
Toshiba P105 SS9337 (with the NVidia 7900GS card)
Only thing that doesn't work is the fingerprint scanner and the smart-touch touchpad (has application 'spots' and a volume slider)  Not too bothered about that though as I mainly use it in a desktop config.

Since installing Ubuntu I have had issues with the GPU overheating and the CPU fan running full tilt...

To solve both issues:

[http://ubuntuforums.org/showthread.php?t=771223](http://ubuntuforums.org/showthread.php?t=771223)
(Follow this one yourself...it's a bit much to regurgitate the whole instruction)
This has fixed the GPU overheating problem.  Previous to this fix, the Sensors applet ([http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)) was showing it running upwards of 114 deg C...in fact I could smell the thing cooking!

One thing I have noticed since going to 10.10...If I boot the laptop and not logon immediately, it starts to overheat again as if it has loaded an unmodified dsdt.aml file.  Still googling that little beastie.

After applying the above fix, post 10.10 install, and after several updates, the CPU fan started running at full speed.  The GPU fan auto adjusts according to temp, but the CPU fan just won't shut up!...until now.

[http://ubuntuforums.org/showpost.php?p=9197545&postcount=24](http://ubuntuforums.org/showpost.php?p=9197545&postcount=24) (big ups to ashima for this one)

<quote>
sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.
<end quote>

Hope this helps...

---

### Post by disabledaccount on 2011-03-10
Dell Latitude E5500 - everything works OOTB (Fn keys, Volume+/-, Card reader, Wi-Fi, etc), at least up to 10.04 which is currently installed :)

Dell M5010 15R - U10.04 - needed upgrade of WiFi drivers, but after that everything works Perfectly :)

Two old Toshiba laptops: SP6000 and SP6100 - despite that these are the most faulty laptops in history of electronics, after some DIY work to fix HW issues, both are running flawlessly with U9.04, including Card Readers and WiFi

---

### Post by frankbooth on 2011-03-10
Linux works partially with my laptop-I will post the specific problem(s).

**Laptop:**
ASUS EEE PC 1001PX

**Problems: **
Combined microphone/headphone jack doesn't work.
Built-in microphone works after a suspend & resume.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-03-10
Linux works completely with my laptop-I will post my hardware specifics

Asus EEE PC 1018P, gNewSense GNU/Linux

---

### Post by texla on 2011-03-10
ASUS X3-VB2  dual core, quadruple boot (three Linux OS's and one windoze), 4gb RAM, wireless N, Lightscribe DVD burner, firewire = all work fantastic with Linux.

---

### Post by Cabalbl4 on 2011-03-10
Linux works partially with my laptop:

Acer Aspire 3820 TG (64 bit) with ubuntu 10.10 (kernel 2.6.35-27-generic #48-Ubuntu SMP):

The main problem is the hard drive power management bug. HDD must be set to IDE mode in bios to avoid problems on power cable plug/unplug. According to launchpad, it will be fixed soon.
Also there must be done some small workarounds to make bluetooth work.
Ath9k wireless driver must be upgraded, the out-of-the-box version works, but causes random freezes (rarely).
And the last thing is the video driver. IMHO ATI proprietary driver preforms better than the open source one. The driver must be downloaded from ATI page to support the latest video card. And you can not switch the built-in cards easily using vgaswitcheroo when the proprietary driver is enabled, so you must configure your xorg.conf and reboot each time you need to switch, or you can set video mode to discrete in bios (disable built-in intel vga). 

Generally, it works, but it can be better.

---

### Post by MarcusW on 2011-03-10
Asus UL30A works with kernel >= 2.6.37, fully open drivers. Everything I've tried anyways. :P (including, but not limited to, 3D graphics, suspend/hibernate, webcam and "special buttons" on the keyboard)

It does work with older kernels as well, but the newer ones adds awesome configuration for the touch pad. :)

---

### Post by dh04000 on 2011-03-10
> **sprocket10 said:**
> Linux works completely with my laptop!
Hardware specs:
Dell E1505
1.66Ghz Intel Dual Core Processors
2 GB Ram
320 GB Western Digital HD @ 7200rpm
Windows 7 & Ubuntu 10.04 (Lucid Lynx) Dual Boot - Both 32 bit
DVD drive stopped working but I'm not sure if that's related to linux issues
Broadcom wireless card
ATI Radeon Mobility X1300 (128MB)

*Install windows first, then use windows tool to shrink partition. THEN install Ubuntu!


Same here with e1705, except mine is a x1400.

---

### Post by aysiu on 2011-03-10
Ironically, Ubuntu's wireless has been super buggy on my **Ubuntu-preinstalled** netbook since 8.10 (including 9.04, 9.10, 10.04, 10.10, and 11.04 alphas). I've filed and updated a bug report to no avail.

But my Macbook Pro is fully compatible with Ubuntu and has been for at least the last three releases. Suspend, wireless, hotkeys, etc.... all work without any tweaking.

---

### Post by rbishop on 2011-03-10
I installed Ubuntu 9.10 and have upgraded with no problems.  I am currently running 10.04.

Acer Aspire 5517
AMD Athlon 1.6Ghz
3GB Ram
160GB HD
DVD-+RW DL
Multi Card Reader

I am able to use all functions of my laptop right out of the box with Ubuntu.  It even told me my battery was starting to die on me.  That is epic to me.  Really helps when you know your battery is starting to go and it's not just a surprise, like with Windows.

---

### Post by matt_symes on 2011-03-10
acer aspire 7540

Only problem. Hit disable touchpad button to disable the touch pad. No problem. Hit the button again to enable and it does not enable it.

Such a small issue i never bother to fix it. Maybe now i will.

---

### Post by daniel.cotter on 2011-03-14
I just bought a laptop from System 76, preloaded with Ubuntu 10.10, 64-bit


15.6 LED
ATI Radion Display w/ 512MB  memory
320GB SATA 7200 RPM HDD
8GB DDR3 main memory
i7-640 processor, 2.8 GHz

I replaced a 20 year old Gateway with w2k installed (upgraded from the original win95).  I am in the Navy Reserve, so I have need to access many .gov DoD sites, and with very little research, I have been able to configure the laptop for flawless operation, for all my needs.  I have no need and no desire to use Windows for anything anymore.

I have used OpenOffice and Firefox for years, so I was halfway there.

---

### Post by ramjet_1953 on 2011-03-14
I have an Acer 4101WNLCi and everything works perfectly with both Linux and BSD.

This laptop is now 5 years old and has been running Linux for 4.

Regards,
Roger

---

### Post by PC_load_letter on 2011-03-14
I have Ubuntu installed on 3 laptops in my household:

1- ThinkPad T43 (ancient) w/ 1.5GB RAM, ATI graphics and Intel wireless running Ubuntu 10.10 32bit. Everything works - can't set up a mic for Skype, apparently I'm not the only one as it seems many T43 users have the same problem.

2- A 3yr-old Dell Vostro 1400: Dual core2, 4GB RAM, Nvidia graphics, Intel wireless, web cam, running Ubuntu 10.10 64bit. Everything works and it's pretty darn fast. Webcam, mic, 3D gfx acceleration works seamlessly. 

3- HP tc4200 tablet, single core, Intel chipset, probably a Brodcom wireless, running Linux Mint 9 like a champ.

---

### Post by rvchari on 2011-03-14
laptop = lenovo T500, P8400 2.26 GHz C2D, 3gb RAM, Intel 4500 Graphics.
almost everything within my knowledge works.
=>handycam connects to the firewire and is configured with ease.
=>card reader functions perfect (had some glitches when i was using jaunty, now maverick detects on its own)
Sound / Wireless / integrated cam works perfect.
=> external web cam / mic / speakers seem to be working perfect too

i think thats about all i can say within my usable knowledge base. is there anything i left out ?

---

### Post by pinballwizard on 2011-03-15
Two new laptops here, Lenovo G550, everything works great (except wireless on PAE kernel)
and Compaq CQ56. Both built in webcams work, everything works 100%.

Compaq running UE2.8, and Lenovo running Ubuntu 10.04.1 LTS

---

### Post by rmayer32 on 2011-03-15
Ubuntu works perfectly on this laptop Dell Insprion E1505 with 512MB of RAM. It also works perfectly on my Compaq Presario Laptop C700 with 2GB of RAM. (Currently running Mandriva however on that one)

All of my desktops run it as well perfectly. I will have to grab specs off them, one is a new HP with 8 GB of RAM and 10.10 flies to say the least. :D

---

### Post by Papa-san on 2011-03-16
I have a Dell Latitude D610. For the most part, Ubuntu was plug -n- play. This is a COMPLETELY DIFFERENT story compared to my older Latitude C610. That one almost had me give up on Ubuntu a half dozen times.

I ran sudo lshw:
```
john@john-latitude:~$ sudo lshw
[sudo] password for john: 
john-latitude             
    description: Portable Computer
    product: Latitude D610
    vendor: Dell Inc.
    serial: *******
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-****-104B-8044-************
  *-core
       description: Motherboard
       product: 0C4708
       vendor: Dell Inc.
       physical id: 0
       serial: .7TKDH91.C**********13.
       slot: MiniPCI
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (10/02/2005)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.86GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 1862MHz
          capacity: 1866MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: CE00000000000000
             physical id: 0
             serial: F7146DEA
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: CE00000000000000
             physical id: 1
             serial: F7146DDF
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:14:22:d5:7a:d0
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI6515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-communication UNCLAIMED
                description: Communication controller
                product: PCI6515 SmartCard Controller
                vendor: Texas Instruments
                physical id: 1.5
                bus info: pci@0000:03:01.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-network
                description: Network controller
                product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: TOSHIBA MK4026GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PA10
                serial: 45F89314T
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9661abd6
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 78e4d8f7-367a-0046-a149-e4f1c8e9da53
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-05-03 01:49:15 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 9a4d69e2-319e-47a7-b461-8ede12c8c053
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-12-31 11:29:33 filesystem=ext3 modified=2011-03-16 10:45:59 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2011-03-16 10:45:59 state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 3354d3f0-eb2b-4531-9382-7aee51b8c265
                   size: 7624MiB
                   capacity: 7624MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-12-31 11:29:43 filesystem=ext3 modified=2011-03-16 10:46:00 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2011-03-16 10:46:00 state=mounted
              *-volume:3
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 658f57d1-2201-43c9-abce-8b2c08991ee7
                   size: 956MiB
                   capacity: 956MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SCB5265
                vendor: PHILIPS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TD15
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
  *-battery
       product: DELL 4P89463
       vendor: Panasonic
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 47000mWh
       configuration: voltage=11.1V
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:5e:ab:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.123 multicast=yes wireless=IEEE 802.11g
john@john-latitude:~$ 
```
It seems like an excessive list to post, but I have a few issues to resolve. 
1 - I cannot get my older printer to work in any way, shape, or form. It is a Brother MFC 4800. I HAT that I have to re-boot into my WinXP partition in order to print. MAJOR PIA...
2 - Occasionally, my wireless quits working for no apparent reason, and I have to manually reconfigure it. Once I enter all my info again, it will work for a while. (Sometimes less than a day, sometimes more than 6 months.)
3 - My earbuds/headphones run at full volume, even if I have muted the sound with the gui/gizmo (at the top right, next to the clock.) Any volume control is done from inside the application / webpage I'm using / at.
There are other things, but I use them so infrequently, I can't remember them. I'll edit this post when I run across them.

---

### Post by eljonny on 2011-03-16
My laptop has worked great with Linux for more than a year. After configuration everything worked and still works perfectly =) Full model name is G60-120US. I dual-boot between xubuntu 10.10 and Vista SP2 (Don't use it unless I have to) and use GRUB2 as a boot loader and GAG([http://gag.sourceforge.net/index.html](http://gag.sourceforge.net/index.html)) as a boot partition chooser (Had to do this to get Vista to boot correctly). My laptop has 3GB RAM, 250GB WD Scorpio Blue HDD, AMD Turion X2 64, and a discrete nVidia 256MB 8200M video device. It also has nVidia nForce HD Audio and an HDMI port. It uses the nForce MCP78S chipset. For wireless networking it uses an Atheros AR928* series card.

Here is my full lshw:
```

description: Notebook
    product: HP G60 Notebook PC
    vendor: Hewlett-Packard
    version: F.54
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 
  *-core
       description: Motherboard
       product: 303C
       vendor: Wistron
       physical id: 0
       version: 08.60
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.54 (08/18/2009)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Turion Dual-Core RM-70
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 2GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 500MHz
          capacity: 500MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1a00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:c0080000-c00fffff
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0006000-c0006fff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0007000-c00070ff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0008000-c0008fff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0007400-c00074ff
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:c0000000-c0003fff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:41 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:c0004000-c0005fff
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633L
             vendor: TSSTcorp
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0400
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: WDC WD2500BEVT-6
             vendor: Western Digital
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 13.0
             serial: WD-WXH908378280
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=fd03d783
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /ntfs
                version: 3.1
                serial: 56bf5922-843f-4042-bff3-f7c62be6530c
                size: 195GiB
                capacity: 195GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-11-18 08:26:01 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 12885644-2b55-4399-b0e8-9eab2a8bfb36
                size: 21GiB
                capacity: 21GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-08-15 17:45:24 filesystem=ext4 lastmountpoint=/&#65533;u&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;XO&#65533;&#65533;v&#65533;&#65533;P~&#65533;&#65533;&#65533;u!&#65533;XO&#65533;@~&#65533;&#65533;Y&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;h~&#65533;&#65533;Yx!&#65533;o modified=2011-03-05 16:13:57 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-16 10:46:43 state=mounted
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sda3
                size: 6549MiB
                capacity: 6549MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1027MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: W95 FAT32 partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /transfer
                   capacity: 5522MiB
                   configuration: mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:3
                description: Windows NTFS volume
                physical id: 4
                bus info: scsi@4:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 3a581441-1359-7046-a325-bdf0c51bd603
                size: 10061MiB
                capacity: 10091MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2008-12-11 11:06:15 filesystem=ntfs label=HP_RECOVERY state=clean
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1f:16:58:81:d6
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht normal_decode bus_master cap_list
          resources: ioport:4000(size=4096) memory:c1000000-c1ffffff ioport:c4000000(size=469762048)
        *-display
             description: VGA compatible controller
             product: C77 [GeForce 8200M G]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:19 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 memory:c2000000-c20fffff
        *-network
             description: Wireless interface
             product: AR928X Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:23:4e:47:42:cb
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath9k driverversion=2.6.35-27-generic firmware=N/A ip=192.168.1.67 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
             resources: irq:23 memory:c2000000-c200ffff
     *-pci:3
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: d
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb

```

---

### Post by Austin25 on 2011-03-16
Everything works perfectly with Knoppix, now.

---

### Post by daniel.cotter on 2011-03-17
> **ramjet_1953 said:**
> There are only two things in life that are mandatory. 
Birth and Death...
Regards,
Roger

I wish it were so.  Many of our brothers and sisters who are alive never live 'til birth.

---

### Post by lifeisamystery on 2011-03-18
I have a Dell Inspiron 1420 with a 250gb hard drive and intel core 2 duo processor, all innerds are stock from dell. Ubuntu 10.10 works flawlessly on my laptop! I had to of coarse get some additional drivers installed in order to get the 2 or 3 things that werent working (i.e wireless interent, dvd reader and web cam) to run, but that was an easy command line away! Before I bought this laptop, I had done alot of research as to which laptop best supports ubuntu (or linux in general, but specifically ubuntu) and the resounding answer was a dell insipron. hope this helps

---

### Post by jcmarini on 2011-03-28
the only reason my dell d620 laptop doesn't work completely with Lucid Lynx 10.04 is that the broadband usb mobile modem by telstra only has *vvindose support. but i'm hunting for a workaround... back to the forum. cheers. Ubuntu diehard.*

---

### Post by spcwingo on 2011-03-28
HP DV4000 [Works perfectly (DV4420US)].

---

### Post by elektra on 2011-04-16
Acer Aspire 5315, Intel Celeron 530, 1gb DDR2, Intel mobile GM965 integrated graphics. 

While my laptop does now work fully running Lucid (10.04) it's been a long hard slog that's included, among many other annoying things, 2 BIOS upgrades. And that was just to stop the laptop overheating every time I booted it up. 

So yeah, kudos to everyone who writes code and everyone on here who helps out lost noobs like me (cause I wouldn't have got my system working AT ALL without you guys) but I definitely DO NOT recommend this model laptop.

---

### Post by binoy4linux on 2011-04-17
I have a Samsung Netbook (N145-JP02), you can see the spec's on the Samsung website. The only change from "off the shelf" is that I upgraded to 2GB Ram. I installed Ubuntu 10.10 and obliterated Win7 Starter that it came with. Works real nice.
 
Edit: Ubuntu 10.10 Desktop Edition, I didn't like the Ubuntu Netbook Remix (UNR) because I didn't care for Unity!

---

### Post by F.G. on 2011-04-18
so, I've got a Toshiba satellite pro l300-pslb1e as far as I can tell everything works fine out of the box.
with jackalope jaunty i used to have issues with the rlt8189b wifi card, full screen flash (and flash in general), mic input with skype, and oddly the wireless (having fixed it) on, off switch didn't turn it off.

All these have disappeared with the current release (though I've not tried the mic yet), also the my Epson stylus printer is now natively supported. the only thing i've had to do is manually make the org.conf file, to use two monitors, as it doesn't automatically have one.

i also recently put ubuntu on my netbook, Asus-1005px.  so far everything seems to work great.

so, well done canonical and the ubuntu folks.

ps while i'm here, if any of the team are reading, the 'ubuntu software center' seems a bit buggy on my installation, i click 'install' and things just don't. not a big deal, i like synaptic and 'apt'. anyway, the hardware all seems to work fine, with Meerkat.

---

### Post by Lizard_King on 2011-04-18
I installed Ubuntu on my HP Pavilion tx2500z and it ran great.

12.1 Inch Touch Screen AMD Turion X2 Ultra Dual-Core Mobile Processor 
ZM-80 2.1 GHz, 7GB RAM, Bluetooth, Camera, Finger Print Reader.

---

### Post by sudoCrushMS on 2011-04-18
I have not had any major problems running Linux on my laptop (most of my prior problems were caused by Windows... thus, Linux is the only OS on my laptop now). Imust applaud Dell, this has to be one of the most impressive configurations i've ever seen in a laptop, I've had this thing running a VM (Windows 7 32-bit Pro, with programs running), while simultaneously running Banshee, an IDE, OpenOffice, Evolution, and a Skype call without even flinching... I can handle the crap I take from friends for "overpaying" for Dell hardware... I boot up, they shut up.

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping    : 10
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
bogomips    : 4788.33
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping    : 10
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dts tpr_shadow vnmi flexpriority
bogomips    : 4787.97
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

MemTotal:        4078900 kB
MemFree:         2891748 kB
Buffers:          110316 kB
Cached:           626052 kB
SwapCached:            0 kB
Active:           640960 kB
Inactive:         462396 kB
Active(anon):     367484 kB
Inactive(anon):    56196 kB
Active(file):     273476 kB
Inactive(file):   406200 kB
Unevictable:          48 kB
Mlocked:              48 kB
HighTotal:       3235388 kB
HighFree:        2228632 kB
LowTotal:         843512 kB
LowFree:          663116 kB
SwapTotal:       6384636 kB
SwapFree:        6384636 kB
Dirty:                 8 kB
Writeback:             0 kB
AnonPages:        367048 kB
Mapped:           110708 kB
Shmem:             56680 kB
Slab:              40344 kB
SReclaimable:      27700 kB
SUnreclaim:        12644 kB
KernelStack:        2496 kB
PageTables:         5280 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     8424084 kB
Committed_AS:    1467144 kB
VmallocTotal:     122880 kB
VmallocUsed:       38020 kB
VmallocChunk:      78152 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       10232 kB
DirectMap2M:      903168 kB
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

---

### Post by pslat on 2011-05-07
Compaq Presario CQ56 working great with Kubuntu on 10.10 :P

---

### Post by JRV on 2011-05-07
Acer Aspire 5515 - Natty with Unity works completely.

Asus EeePC 901 - Lucid works completely.

---

### Post by PhilGil on 2011-05-07
Eee PC 1000h, stock configuration. I don't use the hard buttons (except for power) so I'm not sure if all of them work, but the soft buttons all work.
[U]
Ubuntu 10.04[/U]
Mostly worked. However, wireless did not connect to secured networks out of the box. I fixed it by using a newer kernel. Looks like there's a patch released now [https://bugs.launchpad.net/bugs/496093](https://bugs.launchpad.net/bugs/496093) .

_Lubuntu 10.10_
Worked out of the box. Needed to muck with the synaptics touchpad configuration file to get tap-to-click and two finger scrolling working. That's not a Linux problem, though, LXDE just doesn't have a configuration tool.

_Debian Squeeze (Gnome)_
Needed to install the *firmware-ralink* package after installing the OS (Debian does not include any non-free firmware in their default install). Once that was taken care of everything worked perfectly.

---

### Post by spcwingo on 2011-05-08
Everex Stepnote nm3900w.  It mostly works OOTB.  The only thing I had to do is compile the openchrome module from SVN (I think it was rev. 915) source.  Now everything works beautifully.  If anyone else needs the how to on the openchrome module...here ya go:

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

Look in the "Manual Installation" section.

EDIT:  The openchrome version was 945 if that helps anyone.

---

### Post by d3v1150m471c on 2011-05-08
Works Completely on a Toshiba L-305 and Acer Aspire 5515. On the acer I had to install the driver for the wireless card after installation, which was very easy using an ethernet connection. I later switched the driver for it to allow the aircrack-ng suite. Other than that, everything works fine.

---

### Post by Oxwivi on 2011-05-11
eMachines E727, works perfectly except for Broadcom BCM4313 wireless chipset I need proprietary driver for. And yes, Intel CPU and GPU, unfortunately missing on the wireless. Intel open-source drivers FTW!

---

### Post by JASONFUSARO on 2011-06-16
==================================================  =========
jasonfusaro@jasonfusaro-ML6720:~$ sudo lshw -short -quiet
H/W path               Device       Class       Description
==================================================  =========
                                    system      ML6720 ()                                        [COLOR=DarkOrange] ie. GATEWAY LAPTOP[/COLOR]
/0                                  bus         Motherboard
/0/0                                memory      108KiB BIOS
/0/4                                processor   Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.
/0/4/5                              memory      64KiB L1 cache
/0/4/6                              memory      1MiB L2 cache
/0/f                                memory      3GiB System Memory
/0/f/0                              memory      1GiB DIMM DDR2 Synchronous 533 MHz (1.9 ns
/0/f/1                              memory      2GiB DIMM DDR2 Synchronous 533 MHz (1.9 ns
/0/100                              bridge      Mobile PM965/GM965/GL960 Memory Controller
/0/100/2                            display     Mobile GM965/GL960 Integrated Graphics Con
/0/100/2.1                          display     Mobile GM965/GL960 Integrated Graphics Con
/0/100/1a                           bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1a.1                         bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1a.7                         bus         82801H (ICH8 Family) USB2 EHCI Controller 
/0/100/1b                           multimedia  82801H (ICH8 Family) HD Audio Controller
/0/100/1c                           bridge      82801H (ICH8 Family) PCI Express Port 1
/0/100/1c.2                         bridge      82801H (ICH8 Family) PCI Express Port 3
/0/100/1d                           bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1d.1                         bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1d.2                         bus         82801H (ICH8 Family) USB UHCI Controller #
/0/100/1d.7                         bus         82801H (ICH8 Family) USB2 EHCI Controller 
/0/100/1e                           bridge      82801 Mobile PCI Bridge
/0/100/1f                           bridge      82801HEM (ICH8M) LPC Interface Controller
/0/100/1f.1            scsi0        storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE Controlle
/0/100/1f.1/0.0.0      /dev/cdrom1  disk        DVDRAM GSA-T20F
/0/100/1f.1/0.0.0/0    /dev/cdrom1  disk        
/0/100/1f.2            scsi2        storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Con
/0/100/1f.2/0.0.0      /dev/sda     disk        500GB WDC WD5000BEVT-0
/0/100/1f.2/0.0.0/1    /dev/sda1    volume      378GiB Extended partition
/0/100/1f.2/0.0.0/1/5  /dev/sda5    volume      375GiB Linux filesystem partition
/0/100/1f.2/0.0.0/1/6  /dev/sda6    volume      3061MiB HPFS/NTFS partition
/0/100/1f.2/0.0.0/2    /dev/sda2    volume      87GiB Windows NTFS volume
/0/100/1f.3                         bus         82801H (ICH8 Family) SMBus Controller
/0/1                   scsi5        storage     
/0/1/0.0.0             /dev/sdb     disk        500GB My Passport 071A
/0/1/0.0.0/1           /dev/sdb1    volume      465GiB Windows NTFS volume
/0/1/0.0.1                          generic     SES Device
/0/2                   scsi6        storage     
/0/2/0.0.0             /dev/sdc     disk        319GB External HDD
/0/2/0.0.0/1           /dev/sdc1    volume      297GiB Windows NTFS volume
/0/2/0.0.1             /dev/cdrom   disk        Virtual CD 4507
/0/2/0.0.1/0           /dev/cdrom   disk        
/0/2/0.0.1/0/1                      volume      1KiB Apple partition map
/0/2/0.0.1/0/2                      volume      881KiB Apple HFS
/0/3                   scsi7        storage     
/0/3/0.0.0             /dev/sdd     disk        7969MB SCSI Disk
/0/3/0.0.0/1           /dev/sdd1    volume      7596MiB Windows NTFS volume
/1                                  power       Lithium Ion Battery
[B][COLOR=#ff0000]/2                     wlan0        network     Wireless interface
/3                     wlan1        network     Wireless interface[/COLOR][/B]

[COLOR=Red]

**jasonfusaro@jasonfusaro-ML6720:~$ lsusb**
[/COLOR]

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 0458:00cc KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
**[COLOR=Red]Bus 002 Device 006: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader[/COLOR]**
Bus 002 Device 005: ID 03f0:4507 Hewlett-Packard 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
**[COLOR=Purple]Bus 002 Device 003: ID 0846:9030 NetGear, Inc. [/COLOR]**
Bus 002 Device 002: ID 1058:071a Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**[COLOR=#ff0000]Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter[/COLOR]**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




jasonfusaro@jasonfusaro-ML6720:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"270guest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E2:91:F5:70:B1:0F   
         [COLOR=#ff0000] **Bit Rate=54 Mb/s**[/COLOR]   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:0ff   Fragment thr:0ff
          Power Management:0ff
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2719  Invalid misc:2749   Missed beacon:0

[COLOR=DarkRed]**^REALTEK I GUESS??^**[/COLOR]

wlan1     IEEE 802.11bgn ESSID:"270guest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E2:91:F5:70:B1:0F   
          **[COLOR=Red]Bit Rate=1 Mb/s[/COLOR]   **Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:0ff   Fragment thr:0ff
          Power Management:0ff
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

[COLOR=DarkRed]**^NETGEAR WNA1100^**[/COLOR]


vboxnet0  no wireless extensions.


Everything is working fine, dual boot to Vista or Ubuntu. Spending most of my time on Linux. Running Vista in Virtualbox, but had problems with Virtualbox OSE as opposed to Oracle Virtualbox which seemed to have no problems in the process of switching back. Network running fine but at the speed of my realtek RTL8187b onboard adapter. Running Ubuntustudio 11.04 with no problems, have made ISO disks of Parted magic, Gparted, Linux sytem rescue disk just in case! Currently researching on how to get my NETGEAR ADAPTER running at 150Gb/s instead of the sluggish 56Gb/s. 

System is functioning ok, no problems other than the network speed everything is AOK, and probably won't be dual booting into Vista, hate waiting around for stuff to happen over there!! Once I get Wine down pat and Virtuabox It will probably be so long Windows for good, and free up that drive space. :p

Is there any rule to how large a post can be??


MHILL

Much Happier In Linux Land:D:p

---

### Post by silex89 on 2011-06-16
Never been happier :D, Laptop Acer Aspire 4552, including an ATI Mobility Radeon GPU and a Broadcom wireless card, full functionalities.

---

### Post by collisionystm on 2011-06-16
Dell Vostro 1014. Everything worked perfect.

In fact, every dell laptop I have ever had worked perfect.

---

### Post by fuduntu on 2011-06-16
Asus Eee PC 1015PEM - 100%

Caveats:
WIFI - Uses the Broadcom driver.

Working: Webcam, Card reader, WIFI, Bluetooth, Touchpad (including multitouch), Video (Compositing, video, etc all work fine).

There are no devices that don't work.

Suspends, and Hibernates resuming just fine.  I suspend it 5-10 times a day, and it hasn't panic'ed yet.

Lasts close to 11 hours on battery using [Fuduntu 14.10](http://www.fuduntu.org) w/ [Jupiter 0.0.50](http://www.jupiterapplet.org).  WIFI, and Bluetooth off and the brightness on lowest setting.  Kernel 2.6.39.

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
```

---

### Post by David D. on 2011-06-16
Laptop specifications are in signature.  I marked fully functioning even though I had to add a line to the alsa-base.conf file to get the headphone jacks to sense the headphones when plugged into the jack.  This was an expected action as I have had to do this with clean installs of the last several versions of Ubuntu.

---

### Post by JustinR on 2011-06-16
> **collisionystm said:**
> Dell Vostro 1014. Everything worked perfect.

In fact, every dell laptop I have ever had worked perfect.

+1

Dell Inspiron 1720
Dell Inspiron E1705
Dell Inspiron 1545

All work perfectly except for some issues on the first one.

---

### Post by sanderd17 on 2011-06-16
Clevo E7130 (assembled by Ahtec). Bought it without OS and everything worked out of the box on Ubuntu. Except for brightness control. For that I have to add the acpi_osi= option to the boot command.

On some other distros I also needed to install the wireless driver.

---

### Post by HermanAB on 2011-06-16
Lenovo S10e netbook.

Works purrrrrrfectly.

---

### Post by rjs1064 on 2011-06-16
i have had a few problems with sandy bridge integrated graphics, freezes won't render games properly etc. Hopefully driver support will improve with time.

---

### Post by Anuovis on 2011-06-16
Good old Dell Inspiron 6400.
2 GHz Intel Centrino Duo with 2 GB of RAM.

I might not be using it to the fullest potential (never bothered to test SD card reader working, for example) but everything I need seems to be working just fine.

ATI x1400 video card, no resolution problems there. 3D acceleration is there but honestly I never tried to push it to test the performance fully. Might not be the best for games but this isn't a suitable machine for them anyway.

I have Intel Wireless card which had issues a few years ago but now works flawlessly out of the box.

No sound issues and the multimedia buttons seem to work without any additional configuration.

---

### Post by damnated on 2011-06-16
Hannspree 12" laptop with 2GB DDR3 RAM, 1.2 GHz Dual Core CPU, webcam, bluetooth, microphone, speakers, wifi, sd card. 
I use Crunchbang, a lightweight Debian 6 derivative as the OS (it occupies about 60 MB at startup =D) and almost everything worked out of the box. 
The one thing that caused some headaches was the bluetooth, but after a couple of months of searching, I was able to get that working as well. Now I'm a happy camper.

---

### Post by ojdon on 2011-06-16
Ubuntu is working great on my Acer Aspire 5739G specs are:

2.2GHz Intel Core 2 Duo Processor
4GB DDR3 RAM
Nvidia GeForce GT 240M
320GB Hard Drive

Everything works out of the box, including little things like Microphone even the little touch sensitive hotkeys at the top of the Laptop. Like the volume scroll-thingy (<--- Official technical name for it.)

---

### Post by xpluto on 2011-06-17
sony vaio vgn-cs325j 
fully work's  with linux
problem's :
1. i can't suspend or put PC sleep  after wake keyboard don't work
2.in older version's of linux i didn't have this problem but in newer version it appears : when touch pad is enabled  some times mouse won't click . i disable touch pad and use external mouse and there is no problem
3.  little touch sensitive hotkeys at the top of the Laptop  won't work ( don care ;))
it's not a big deal  I'm using Linux now.:popcorn:

---

### Post by Veren on 2011-07-12
Asus EEE PC 1015pd, I haven't even seen the word error on it (: Except for Crunchbang, where I in no possible way could get wireless to work.

---

### Post by Bachstelze on 2011-07-12
MacBook Pro 5,5 like a boss.

---

### Post by dave01945 on 2011-08-15
hp g60 100 working perfectly out the box
amd anthlonX2 1.9ghz 64
nvidia gforce 8200
4 GB RAM

---

### Post by al1x on 2011-09-08
I have encountered no problems so far with Asus Eeepc 1005HA running ubuntu 10.04LTS and other previous versions.

---

### Post by lpwaqas on 2011-09-15
> **aysiu said:**
> My previous laptop, which I've since given away worked perfectly with Ubuntu out-of-the-box. It was a Dell Inspiron 500m. The only thing I'll say is that when I bought it, it didn't have a wireless card inside. So I made sure to buy a Linux-compatible wireless card when I got one (Intel Pro Wireless 2200, thanks to recommendations from these forums).

I know run an Eee PC. Don't know if it counts as a laptop. It ran perfectly with Xandros as preconfigured by Asus. I installed eeeXubuntu on it, which included some Eee-specific tweaks, and it works almost perfectly, except that the boot time is now extremely slow, and resume from suspend doesn't work all the time any more.
Dell XPS-1640 - kinda My Desktop 
With previous versions of the ubuntu (before MeerKat) there was a VGA   driver issue the compiz was slow and some other issues, but with the   MeerKat (thankgod Dell paid a pile of  cash to whoever, lol ) it fixed  the issue and now one only has to just  goto System > Administration  > Additional Drivers and activate  the propreitery Driver and  everything else run just fine out of the  box.

Dell Latitude D630
It had the same issue with the VGA niVidia Graphics card and the issue   was fixed by the same trick as above Do note that I am talking about   MeerKat here not the older versions of ubuntu. This my fav. 14' machine I   have had it for lo000ng time and I use it on my lap :wink: my first wife so  to speak and it just runs fine thanks to Ubuntu Devs. Good job guys :grin:

Dell Vostro 1400
It just runs out of the Box no drivers no additional thingies required at all :wink:


root@Kirky:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86M [Quadro NVS 135M] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by jjer on 2011-10-30
I have now installed Ubuntu 11.10 (32-bit) on my Acer Aspire 7720G laptop. This works very well.

The only issue is using net-bank with BankID. This may be a problem outside the laptop itself due to poor linux support from the bank. 

Using Google, I see that many has solved this problem. I have installed the recommended Sun Java, and followed the other tips for the browser plugins, but yet with little success. 

Therefore I reported that there are some issues and I don't know why. Most likely it has nothing to do with linux itself, but more with the support from the bank.

Edit: 
- Nettbank'ing with BankID in Firefox now works. (It was a symbolic link that was missing to the java plugin.)
- Experienced a crash using the compiz software (compizconfig-settings-manager) that upset the GUI. Had to reinstall everything. Experienced it again but was prepared with back-up of the hidden folders and files in ~/, and restoring these solved the problem.

---

### Post by rojaasensei on 2011-10-30
Xubuntu 11.10 fully operational on Samsung N150 Plus

---

### Post by &#23389;&#36154;&#22674; on 2011-12-13
Gateway Nv47ho2c 
    Intel CORE i7 2630QM  

But,i don't think it works well. Sometimes it works very slow.

My system is Ubuntu 11.10.

---

### Post by w1d3 on 2011-12-14
screen tearing, bluetooth doesn't work and the camera im on a Lenovo Y550

---

### Post by smattiuz on 2011-12-14
Linux works perfectly on my late 2010 13" macbook pro (2.4 ghz, 4gb ram, geforce 320m with 256 mb ram)

---

### Post by nderic77 on 2011-12-14
Dell Studio laptop with 15 inch LED
core i7
8 GB RAM
1 GB Video RAM
500 GB HDD - 100 of which is a dedicated Win7 partition
Ubuntu 10.04 LTS 64-bit

I have gotten everything I need to work; even Tweetdeck and Skype. I still have a Virtualbox VM of Win7 just for iTunes and occasional use of MS Office 2010. The Virtualbox hardware optimizations work like a champ.

---

### Post by sunfromhere on 2011-12-14
Everything works perfectly on [HP Pavilion g7]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02884779&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5141935"), even the built-in camera and mic; all of the printers I've plugged in so far were plug and print in matter of seconds. The only driver that needed manual installation was the proprietary graphic card driver.

Hardware installation was probably the Ubuntu selling point for me - everything just worked.

---

### Post by techvish81 on 2011-12-14
Ubuntu 11.10 worked out of the box, only thing different is you have to tap two fingers to get right click on the touchpad.

My laptop is hp mini 210-1000. With intel atom processor.

---

### Post by neo_1in on 2011-12-14
Lenovo G570 (15.5in, 1366x768 Max)
Pentium B950 2.1GHz
2 GB RAM
500 GB WDC HDD
Intel SandyBridge Mobile Graphics
Broadcom Wireless
Intel HD Audio
Bison WebCam
Sanyo Batteries
.... (Cost: &#8377;23500 ~ $437)
Running Kubuntu 11.10 64bit

95% problem free. Issues like crash (very rare, but not zero) and absence of monitor brightness notification (only the absence of popup, not the whole function), are particular to kde, as the same things work fine on unity. No -ive performance lag compared to windows 7 (also installed).

I am putting it down as perfect.

---

### Post by matt_mccarron on 2011-12-14
lenovo b575  just got it, working on wireless issues right now...
tohiba satellite circa 2003 no problems
acer aspire no problems

But i have often read the Dell XPS series work best with ubuntu, and second best was Lenovo.  So I just bought this lenovo at future shop.  Very happy.. when I can get the wireless solved.

---

### Post by epicoder on 2011-12-14
Linux works completely on my laptop. I use Ubuntu 11.10 64 bit.

Dell Inspiron 1545
Intel Core 2 Duo at 2.55 GHz, 3 MB L2 (upgraded, original was Pentium 4 at 2.00 GHz, ,1 MB L2)
4 GB DDR2 ram (upgraded, originally was 2 GB)
640 GB hard drive (upgraded, originally was 160 GB)
Intel GM45 integrated graphics. Unity 3d and 2d work fine.

Ubuntu 10.10 also worked excellently on the original hardware.

---

### Post by CheapXJ on 2012-01-04
I have more than one, I think I deserve more than one vote!

Dell XPS M1730, had to install via external display but after installing nvidia drivers everything was awesome. took a little bit of digging to get the gamer LCD above the keyboard to do more than be a clock, but that wasn't difficult either. Windows7 wouldn't even recognize all the hardware properly. linux doesn't seem to take advantage of the Aegia PhysX engine but it does recognize its existence.

compaq F710, everything worked out of the box, no issues whatsoever.

acer aspire one aoa-150, usb install, worked great once I got a usb stick that wasn't crap.

compaq presario 810us - my first linux laptop ran mandrake 9.0 on it when i was in college. kept sending this machine back 'cause windows never worked properly on it but linux never failed. i eventually punched it in the screen while running simulations on the windows side (prof made me use the same exact thing everyone else was using) and now it's dead.

---

### Post by tlcstat on 2012-01-04
Greetings,
Couldn't be more pleased to have Oneiric Ocelot running on two Toshiba Laptops.
Toshiba L305-S5616 Celeron 2.2 Gh, 4Gig Ram, Intel Mobile 4 Chipset. lOGear USB Bluetooth Adapter, Atheros Wifi. Running Unity 3D Desktop. 

Toshiba NB505 Netbook, Intel Atom 1.6Gh, Intel Chipset, 2gig Ram, IOGear USB Bluetooth, Atheros Wifi, Running Unity 3d Desktop.

---

### Post by sanderella on 2012-01-04
I have a Dell Inspiron 1300, and upgraded the RAM. Works fine.:)

---

### Post by aaaantoine on 2012-01-04
> **aaaantoine said:**
> Works partially.  Compatibility review as of Gutsy posted [here](http://www.ubuntuhcl.org/browse/product+acer_baspire_5050b5554?id=34).

I will post updated version as of the Hardy upgrade here.  First, a description of the hardware in a nutshell:

Acer Aspire 5050-5554
Processor: AMD Turion 64 1.6GHz
RAM: 1GB DDR2  (Upgraded to 4GB, its max capacity)
Video: ATI Radeon Xpress 1100
Screen: 14.1" 1280x800 Glossy
Sound: ATI SB450 HDA Audio
Hard Drive: 120GB
Optical Drive: DVD+RW
Networking:
+ Ethernet: Realtek RTL-8139/8139C/8139C+
+ Wireless: Broadcom BCM4318 [AirForce One 54g]
Other:
+ Acer OrbiCam
+ Card Reader (SD, xD, MMC, others)
+ PCMCIA slot

**Issues:**

1. Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
- Does not work out of the box; requires firmware installation. Installation requires firmware file on hand or a wired network connection.

2. Microdia OrbiCam (USB device 0c45:6260)
- Not supported as of Hardy.  Drivers currently in development.  Follow driver development [here](http://groups.google.com/group/microdia).

3. Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
- Laptop speakers are mapped to the "Surround" channel.
- Microphone does not work.
- Laptop speakers do not mute when headphones are plugged in.

4. VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
- Open source drivers offer limited function; Restricted drivers are improved but somewhat unstable.

General
- The custom Euro and Dollar keys above the directional keys do not function.
- Suspend works, but drops wifi functionality.
- Hibernation not tested since Gutsy.

So... It's been 3 1/2 years.  Here's my update.

1. Still an issue as described.  In fact, getting wireless to work during the installation of 11.04 was actually more difficult than 8.04.

2. Camera is now functional, but the color data is mapped incorrectly.  Also, rotating the camera to face behind the laptop disconnects the camera for the duration of the session, but I attribute this to a hardware issue since it behaved similarly under Windows.

3. Sound situation is much improved...
- The sound channel appears to be mapped correctly, but as of 11.10 the volume slider range is off by an order of magnitude.  That is, the slider at the 10% position gives 100% volume; at the 5% position it gives 50%.
- Microphone seems to work.  Sound settings indicate that it is picking up sound.  Have not tested thoroughly.
- As of 11.10, the headphone jack actually switches the audio channel.  Just tested this now, and was surprised by the result.

4. The FOSS video stack has had a complete overhaul since 2008.  On the flip side, AMD no longer supports the 1100, and so the last fglrx drivers are incredibly outdated.  Hardware limitations make "proper" gaming nearly impossible on this machine anyway, but at least it's not as buggy about it as it used to be.

All in all, it took long enough, but things are generally getting better.

Also, Suspend works fine as of last test.  I don't think I've gotten hibernate to work on Linux ever, so I'm not concerned about that.

---

### Post by del_diablo on 2012-01-05
aaaantoine: You said Amd Turion, does it actually have ACPI support? As in power managment related to clocking up and down?

---

### Post by stalkingwolf on 2012-01-09
At present i am running linux on 3 laptop and had it on a fourth before i sold it.
They are an asus EEE 1005ah, An Ibm t42p, a Compaq nc8000, and an hp zt3300, this one i installed xpsp3 on it because that is what everyone that was calling asked for.  I ended up selling it to a guy who immediately
installed linux on it.

---

### Post by wolfen69 on 2012-01-09
> **stalkingwolf said:**
> i installed xpsp3 on it because that is what everyone that was calling asked for.  I ended up selling it to a guy who immediately
installed linux on it.

That happened to me too. I had one of the first netbooks and had Debian on it. I wiped it and installed XP on it so I could sell it quicker, but the person I sold it to was a linux user and wished I had left it on. :confused:

---

### Post by Basher101 on 2012-01-09
My ubuntu 11.04 install worked flawlessly on my eMachines E725 Laptop with integrated Intel 4 Chipset Family graphics.

Only issue was no backlight. Fixed that easily though.

---

### Post by VCoolio on 2012-01-09
Samsung NF310 works fine. Screen brightness buttons a bit hit-and-miss, easily scripted around though with custom keybindings. And it's linux-only, you can't repartition to dual-boot. I consider that a feature.

---

### Post by gleedadswell on 2012-01-26
HP 2000 laptop with dual AMD E-350 processors and ATI AMD Radeon HD 6310 Graphics.  It's running 11.10.  Everything works beautifully including the webcam and microphones.  Suspend and hibernate are even about as trouble free as they ever are (I think I've had one hibernate that failed to wake up).

---

### Post by thotz on 2012-02-23
Hello, I have a 15,6" Sony Vaio Notebook with Intel i3 processor with the Intel graphics card in use. Everything works perfectly.

---

### Post by junaid_572 on 2012-02-23
hp 3230us there was some problem with touch pad after update but were easily solved with a simple fix
:)

---

### Post by philinux on 2012-02-23
Acer 1410 excellent. [http://www.laptop-software.com/acer-software/acer-aspire-1410-notebook-technical-specifications/](http://www.laptop-software.com/acer-software/acer-aspire-1410-notebook-technical-specifications/)

---

### Post by piperbarb on 2012-03-05
Yup.  Now I can actually say that.  I have a Dell XPS 17 (L702X) which arrived last week.  Day 2, I installed Ubuntu 11.10 and it worked very well.  There were a few things that needed tweaking (video - using Bumblebee because of the nvidia optimus card; internal SD card reader).  Now everything is working as it should. I'm absolutely loving how it works now.

---

### Post by sefs on 2012-03-05
1/
Acer Aspire One w/ Ubuntu 10.04 
- works perfectly as far as I know.

2/
Lenovo B570 w/ Ubuntu 10.04
- Works partially
- Native resolution not supported as there is no drive for the card in this release. I needed to update with a custom kernel with the video drivers in it.
- Updating to the custom kernel in turn broke the wireless.  There is suppose to be a fix for that too but I stopped right there and just used an Ethernet cable.
- 12.04 is supposed to have the video drivers this laptop needs by default so this release is important for me. 
- Other than the video and the wireless, everything else is ok as far as I can tell.

---

### Post by omael on 2012-03-05
HP DV7 still with troubles with the remote control and HDMI out

---

### Post by milkboy007 on 2012-03-10
perfect on my 5yrs old laptop, 2nd yr running on ubuntu& then till now xubuntu

nec versa e6200
intel T2250 @ 1.73ghz
GMA 950
intel 945 chipset(i think)
1gb ram
Samsung 160gb IDE HDD
realtek RL8139 & intel 3945abg, LAN & wifi respectively
TI PCIxx12 cardbus and firewire
TI (built in) card reader
BT ??

---

### Post by kelvinator on 2012-03-16
This week I bought a DELL Inspiron 17 laptop.
Ubuntu 11.10 installed without me needing to do anything but pop in the disk and follow the various prompts. All hardware features are working without the need for any tweaking.

---

### Post by viperdvman on 2012-03-24
I run Ubuntu 11.10 on an Asus EeePC 1015T

It's an AMD V-105 powered netbook with an integrated AMD Radeon HD 4250/4270 chip installed. So it's a very powerful single-core netbook... embarasses ANY single-core Atom (Only the NVidia ION-powered dual-core Atoms are faster... as well as the AMD C-50's and E-series)

Everything runs great on it. However, the only problem I've run into is that Flash videos (YouTube, Hulu, and other websites that use Flash to play videos) have low frame rates when I'm using the proprietary AMD graphics driver. However, the open-source Radeon driver works great with it, and everything tuns perfectly smooth on the netbook.

I will go ahead and vote "works completely", despite AMD's Catalyst Linux driver not playing flash worth a crap.

---

### Post by ubunbu on 2012-03-24
I have a 100% Ubuntu laptop which I use as a main computer but, the caveat to that is I have been unable to install a proprietary video card driver.

Because I have two video cards.

But everything works.

---

### Post by S2UIRR3L on 2012-03-24
Linux works partially with my laptop-I will post the specific problem(s)

Gateway MX6214

Wireless didn't work. I connected via CAT-5 and downloaded the Broadcom drivers. Everything else worked out of the box. This happened with both Jaunty Jackalope and Lucid Lynx. Not a real problem, more of a minor, one time, inconvenience is all.

---

### Post by Arunomi on 2012-04-24
I have a Lg R405 and i have ubuntu on it and every thing works exept the mouse pad. But then it did not work in windows all so.

---

### Post by stalkingwolf on 2012-04-24
i have run various flavors and releases of ubuntu on several laptops.

3 HPs two ran 8.04
1 compaq  the same
an EEEPC that ran the EEE version and 8.04
all those ran perfectly. I will admit that one of the HPs the wireless didnt work with 7.10 but that was an easy fix with a netgear wv111.v.2 adapter.

currently 2 HPs another EEE run flawlessly. also a dell with a broadcom card
that doesnt work.

---

### Post by sunfromhere on 2012-04-24
I would like to add something to my vote:

I voted yes, hp Pavilion g7 is fully functioning on Linux.

BUT - switchable graphics don't work. However, considering that on this model sg doesn't work on Windows either (HP and AMD shifting responsibility), it could be considered fully functional.

---

### Post by nutpants on 2012-04-24
my Toshiba nb100 net book works flawless.

---

### Post by LillyDragon on 2012-04-24
This topic is kinda old. Is the original poster still accepting community input on the subject?

Anyway, my HP 2000-239WM laptop (Mostly Intel-based with a few Realtek parts in the mix.) is cooperating with the Precise Pangolin Beta far better than the last LTS. Even my realtek SD card slot and built-in speakers are working! Suspend mode seems a bit flaky on Xubuntu, however, (It only suspends successfully every other time.) but works just fine in Unity or Gnome.

Still can't reduce the brightness on its back-light, though, but from what I've read through a Google search, the next kernel version could fix that, so I'll probably just wait until the next few updates and see if that resolves it without getting my hands dirty. =P

---

### Post by rich52x on 2012-04-24
The only problems I'm having at the moment is the battery only lasting around 2 hours when at the same level of usage I get 4 hours on windows :/

Also whenever I play video the thing heats up to the point where I feel the viability of me having children is under threat.

And Unity runs slow despite 4GB RAM and a dual core processor, but I use GNOME Shell anyway, so no biggie 

Although apart from that, problem free :D

---

### Post by RichardCain on 2012-04-26
*Linux works partially with my laptop-I will post the specific problem(s)*

_Lenovo Ideapad Z470_

Nvidia GeForce GT520M Graphics Card - wouldn't work, proprietary driver messed up the system.  I disabled the card in BIOS and it's now running perfectly well on the Intel card.

Battery life is less than 2 hours, but I rarely use it on battery anyway.

WiFi, Sound and everything else works perfectly.

---

### Post by kevbuntu on 2012-04-26
Dell Vostro 1000, Athlon 64 X2 (TK-53) 1.70 GHz, 2 GB RAM, 500 GB HDD.

I voted "Linux works partially with my laptop-I will post the specific problem" due to slight issues over the years with insalls. Fan, screen dimming, key functions, but that was 5 years ago. Distro installs have come a long way.

Only issue that is still a factor if I'm not hardwired for the install is the bcm43xx broadcom driver. When I was new to linux this was a struggle, now it's just a simple step.

Fedora is the only distro that I've used that has it installed already.
Ubuntu makes the process extremely simple by recognizing the restricted driver and offering to install it. Mint also borrows that function. 
Suse, and the rest I just go to terminal.

---

### Post by Mathor on 2012-04-26
Ubuntu and Mint (since it's based on Ubuntu) out of the box for me everytime. Other distro's like Fedora and Debian everything works but I always have to connect to an ethernet and find my wireless drivers, but that's not THAT terrible. It is nice not having to do that with Ubuntu though. ;)

Gateway Turion Dual Processor AMD64 1.70 GHZ 4GB RAM 320GB HD laptop

---

### Post by kimda on 2012-04-26
Everything works (Precise) on a Acer Aspire 1810T.

---

### Post by mamamia88 on 2012-04-26
Debain 6 on a samsung n130 netbook runs great

---

### Post by mitsi on 2012-04-26
My laptop is running better than when it was in windows um . installed is Ubuntu 11.10 alone  no windows os at all on a Compaq Pressario CQ60 , now my printer works and works a lot faster maybe a bit noisier but faster and for some reason the speakers for my music are clearer and also much louder , music played through Amarok , did not get new hearing aid batteries ha ha ha . Very happy I made a switch to Ubuntu ,All problems and errors all were mainly because of me fixing things until it needed fixing um...

---

### Post by davidgypsy on 2012-04-27
My Acer 5542G works great with a new install of 12.04, and it runs a lot cooler than Win7 as well!

\\:D/\\:D/\\:D/

---

### Post by sudodus on 2012-04-27
This aging laptop works well with Lubuntu Precise

[[COLOR="Red"]_http://reviews.cnet.com/laptops/lenovo-thinkpad-t41-2379/4507-3121_7-30567436.html_[/COLOR]]("http://reviews.cnet.com/laptops/lenovo-thinkpad-t41-2379/4507-3121_7-30567436.html")

Right now the default video player mplayer2 crashes, but VLC is easy to install with
```
sudo apt-get install vlc
``` and provides good multimedia performance (considering the old hardware).

---

### Post by AwesomeTux on 2012-04-28
My Acer Aspire works perfectly, 3D acceleration (well GNOME Shell runs, so...), and WiFi even works.

My specs.:

> Processor:
AMD Quad-Core 1.5GHz A6-3420M

Graphics:
1GB DDR3 AMD Radeon HD 7670M Dedicated Graphics

Audio:
Integrated High-Definition Audio with Built-in Stereo Speakers

Drives & Readers:
320GB 5400 RPM Hard Drive, DVD Super Multi Dual Layer Burner, Card Reader (SD, CF, MS, MiniMMC)

Memory:
4GB DDR3 1066MHz PC3-8500 (2GB x 2)

Mouse & Keyboard:
Multi-Gesture Touchpad, Full-QWERTY Keyboard with Numberpad

Networking:
Integrated Gigabit Network Adapter, 802.11b/g/n Wireless

Battery:
6-Cell Lithium-ion, up to 4.0 hours battery-life

Dimensions:
Width: 15", Height: 0.99" - 1.3", Depth: 9.96", Weight: 5.74 lbs

Screen:
15.6" HD Widescreen CineCrystal LED-backlit Display

Integrated Webcam:
1.3MP

Miscellaneous:
HDMI Port with HDCP, 3 USB 2.0 Ports, LAN Port, Headphone Jack, Microphone Jack, VGA Port, Kensington Security Lock Slot

Warranty:
Limited 1 Year Parts & Labor

Source: [http://www.inatux.com/?p=sys09](http://www.inatux.com/?p=sys09)

---

### Post by farrinux on 2012-04-28
Gateway LT20 Netbook running 11.10 unity 3D.  Works perfectly.

---

### Post by MIJ-VI on 2012-05-12
```
john@john:~$ sudo lshw
[sudo] password for john: 
john                      
    description: Notebook
    product: Aspire 5517 (123456789)
    vendor: Acer
    version: V1.09
    serial: LXPGZ020320034805B1601
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=Type1Family sku=123456789 uuid=66626132-3538-3735-6466-705AB62286B6
  *-core
       description: Motherboard
       product: Aspire 5517
       vendor: Acer
       physical id: 0
       version: V1.09
       serial: LXPGZ020320034805B1601
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.09
          date: 11/30/2009
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor TF-20
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 20
          bus info: cpu@0
          version: AMD Athlon(tm) Processor TF-20
          serial: NotSupport
          slot: Socket S1G1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow up rep_good nopl extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
          configuration: enabledcores=1 threads=1
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 21
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal write-through unified
        *-cache:1
             description: L1 cache
             physical id: 22
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             vendor: Kingston
             physical id: 0
             serial: 7F98000000000000060B32921BE926
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             vendor: Kingston
             physical id: 1
             serial: 7F98000000000000060B32931BE226
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR2 [empty]
             physical id: 2
             slot: DIMM2
        *-bank:3
             description: DIMM DDR2 [empty]
             physical id: 3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:f2100000-f22fffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:e0000000-efffffff ioport:7000(size=256) memory:f2200000-f220ffff memory:f2100000-f21fffff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=16384) memory:f1100000-f20fffff ioport:f0000000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth2
                version: 01
                serial: c4:17:fe:67:f3:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.2.24 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:f1100000-f1103fff
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:f1000000-f10fffff
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: c0
                serial: 70:5a:b6:22:86:b6
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:f1000000-f103ffff ioport:2000(size=128)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:8038(size=8) ioport:804c(size=4) ioport:8030(size=8) ioport:8048(size=4) ioport:8010(size=16) memory:f2306000-f23063ff
           *-disk
                description: ATA Disk
                product: ST9500325AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0001
                serial: 6VE8VH0H
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008d587
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 23bc7d4d-58f2-41c8-b05f-0ba8a66b053e
                   size: 32GiB
                   capacity: 32GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-05-10 20:24:48 filesystem=ext4 lastmountpoint=/ modified=2012-05-10 15:53:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-05-11 20:01:29 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: ac6718c9-d0cf-46e2-821f-da9720034b8a
                   size: 5000MiB
                   capacity: 5000MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 02600d59-c2ec-4a67-a321-68fd2d6bf819
                   size: 428GiB
                   capacity: 428GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-04-28 18:18:07 filesystem=ext4 lastmountpoint=/home modified=2012-05-11 20:06:51 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-05-11 20:06:51 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7700S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.B0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f2305000-f2305fff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f2304000-f2304fff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f2306400-f23064ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f2300000-f2303fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:1000(size=4096)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
john@john:~$ 

```Two minor snags:

- The Broadcom BCM4312 Wi-Fi card requires a proprietary driver.
- The Mobility Radeon HD 3200 Graphics works best under Gnome Classic (without effects) via the Open Source Radeon driver.

---

### Post by craig10x on 2012-05-12
Only thing that won't work on my 3 month old Toshiba 17" laptop with i3 core intel processor and intel graphics is the webcam...

My friend has the same model laptop with amd instead and the webcam works fine...

We are both using ubuntu 12.04 with unity

---

### Post by MiXor on 2012-05-12
Macbook pro 7.1 with Oneiric Ocelot. Everything works fine, found all fixes on forums.

---

### Post by georgelappies on 2012-05-12
Dell Studio 1558

Works perfectly.

Intel i5
ATI 4570HD Mobile
4GB RAM
500GB HDD
Built-in 3G modem
Broadcom wifi (This is only hardware not working fully directly after an install as the firmware needs to be downloaded via Jockey)

---

### Post by oldrocker99 on 2012-05-30
Acer Aspire 5516 (about 4 or so years old, which wasn't booting when rescued from the trash). No problems, after an hour or three of wireless disconnects, which eventually went away. Using (of course) the OSS "radeon" driver. Running Mint 13 (12.04 and MATE), which, at least, didn't require a reinstall of GRUB](*,) the way Kubuntu 12.04 did on installation:???:.

---

### Post by chili555 on 2012-05-30
My Lenovo T410i runs ...almost... perfectly. Once in a great while, if I suspend by simply closing the lid, it won't resume properly and a hard reset is required. If I use Fn+F4, it suspends and resumes perfectly. I picked the specific model because of the wireless card. Some of the Realtek cards offered in T-series Thinkpads are tricky; the Intel is trouble free, although some only become trouble free when N speeds are disabled.

Lenovo Thinkpad T410i
Intel Core i3 M 370
4 GB RAM
Intel Integrated Graphics Controller
Intel Centrino Advanced-N 6200 wireless

Ubuntu 12.04 32-bit PAE kernel

---

### Post by ibozzie on 2012-06-01
So Precise runs delightfully well on my Dell XPS 15 (L502x). Here are the specs:

Processor: i7-2630QM
RAM: 6GB
Display: 15.6", HD
DVD-RW
Hard Drive: 500GB, 7200RPM
Video cards: Nvidia GeForce GT 540M / Intel Integrated Graphics
Wireless: Intel Centrino Wireless-N 1000

The only trick is switching between the two video cards, which I use [Bumblebee]("http://bumblebee-project.org/") for. Basically to save power there is this "Optimus" technology for Windows that automatically switches between the high-performance video card and the craptastic integrated one. Bumblebee is a project that replicates that in Linux.

---

### Post by Max Blyss on 2012-06-01
Asus K52f
2.13 Ghz Intel DualCore P6000
Intel HM55 Espress Chipset
Intel GMA HD integrated graphics
3GB RAM
500G Seagate HDD

Purchased in April of 2011 just in time for Ubuntu release.
This particular model has run Xubuntu or Ubuntu 11.04 through 12.04 with no issues whatsoever.  Nice and snappy all the time.

---

### Post by Frankiewizard on 2012-06-11
1 - Toshiba Qosmio G20 - 147 (32 BIT)

2 - Asus Eee-pc 1000H        (32 BIT)

3 - Compaq Presario CQ - 62 (64 BIT)

All of these computers run on 12.04

:lolflag:

---

### Post by HappinessNow on 2012-06-12
> **phidia said:**
> 

Once people, hopefully, vote on the poll I think it would be very useful if they also post comments with specific hardware that was a problem or worked well. Commenting about biases is fine too.


voted: Linux works completely with my laptop-I will post my hardware specifics

Google CR-48 running ChromeOS with Aura

Version 20.0.1132.15 dev
Platform 2268.23.0 (Official Build) dev-channel x86-mario
Firmware Mario.03.60.1120.0038G5.0018d

Dev Channel

WebKit:
536.11 (@117876)

V8:
3.10.8.10

User Agent:
Mozilla/5.0 (X11; CrOS i686 2268.23.0) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.15 Safari/536.11

Command Line:
/opt/google/chrome/chrome --apps-gallery-title=Web Store --apps-gallery-url=https://chrome.google.com/webstore/ --compress-sys-feedback --device-management-url=https://m.google.com/devicemanagement/data/api --disable-seccomp-sandbox --enable-accelerated-plugins --enable-device-policy --enable-gview --enable-in-browser-thumbnailing --enable-logging --enable-onc-policy --enable-partial-swap --enable-per-tile-painting --enable-smooth-scrolling --enable-sync-tabs --enable-sync-tabs-for-other-clients --enable-threaded-compositing --enterprise-enrollment-initial-modulus=5 --enterprise-enrollment-modulus-limit=12 --force-compositing-mode --load-opencryptoki --log-level=1 --login-manager --login-profile=user --no-first-run --ppapi-flash-args=enable_stagevideo_auto=0 --reload-killed-tabs --scroll-pixels=3 --ui-enable-partial-swap --ui-enable-per-tile-painting --ui-use-gpu-process --use-cras --user-data-dir=/home/chronos --no-protector --disable-seccomp-filter-sandbox --register-pepper-plugins=/opt/google/chrome/pepper/libnetflixplugin2.so#Netflix#Netflix 2.0.2#2.0.2;application/x-ppapi-netflix2 --enable-accelerated-layers --disable-login-animations --ppapi-flash-path=/opt/google/chrome/pepper/libpepflashplayer.so --ppapi-flash-version=11.3.31.104 --flag-switches-begin --aura-google-dialog-frames --enable-panels --enable-sync-tabs --flag-switches-end

Last Updated:
Tuesday, May 22, 2012

---

### Post by millhouse513 on 2012-06-27
Hardware:  Asus G51JX  (8GB RAM, i7 720QM, HM55 chipset, nvidia 360m w/1GB RAM)

Notes:  For the most part everything works very well.  My biggest issue is hibernation.  I've tried a few different approaches to getting hibernation to work (can't think of them off the top of my head right now).  Hibernation always seems to work perfectly the first time I try.  About 60% that it'll work a second time, but after that it doesn't seem to work going in and out of hibernation.

---

### Post by greenfrog on 2012-06-27
HP g7-1329wm   ):P):P

---

### Post by sudodus on 2012-06-28
> **millhouse513 said:**
> Hardware:  Asus G51JX  (8GB RAM, i7 720QM, HM55 chipset, nvidia 360m w/1GB RAM)

Notes:  For the most part everything works very well.  My biggest issue is hibernation.  I've tried a few different approaches to getting hibernation to work (can't think of them off the top of my head right now).  Hibernation always seems to work perfectly the first time I try.  About 60% that it'll work a second time, but after that it doesn't seem to work going in and out of hibernation.
How much swap do you have? It should be a little bigger (in GiBi-bytes) than the RAM for hibernation.

---

### Post by stalkingwolf on 2012-06-28
I have installed ubuntu on several laptops with most everything works.

Starting with 8.04 the graphics card didnt work on the everex l7 ****  that was the card it was a pain across the board.

The most recent have been my EEE 1005ah all works
an HP zw something all worked
a Dell M6300 couldnt get the broadcom wireless to work.
a Dell d 800    all works.
an IBM t42p  all works

in between there have been several HPs and a compaq.

---

### Post by OldAdamUser2 on 2012-08-12
Ubuntu 11.10 (using fluxbox desktop) works exceptionally well on my Asus Eeepc 900. Some tweaks were necessary to make that happen. Details here--

[http://lakenorforkadventures.blogspot.com/2012/08/installing-ubuntu-1110-on-asus-eee-900.html](http://lakenorforkadventures.blogspot.com/2012/08/installing-ubuntu-1110-on-asus-eee-900.html)

---

### Post by cbennett926 on 2012-08-12
The specs are in my signature, however, to further explain, I just have to switch my graphics card to dedicated, and then it works flawlessly!

---

### Post by hank22077 on 2012-08-17
I recently purchased a Dell Inspiron Mini Duo 3487FNT Convertible Laptop/Tablet. The specs: 

Intel Atom N550 Processor (1.5GHz); 2GB RAM; 320GB Hard Drive; Wireless 802.11n / Bluetooth Combo Card; 10.1" Widescreen HD (1366X768) Multi-Touch Display; Integrated Intel NM10 Express graphics; and Windows 7 Home Premium pre-installed.

I partitioned my hard drive to allocate space for Ubuntu 12.04LTS.
Booted using USB port/flash drive. 
Was prompted during install to connect to my wireless router; and, everything went well, for a few days.

Now, however, each time I try to use Ubuntu the signal goes in and out, I'll have to re-enter the passcode, etc.
The wireless connection on Windows 7 has no issues; and, my kids share an old laptop with Windows XP, which has no issues.

I'm not real keen on this, but it seemed that Ubuntu had saved my wireless connection during install, and was automatically connecting to it just fine for the first few days. Now, I can't keep the connection.

Any insight out there?
Thanks!

---

### Post by Jakin on 2012-08-17
I've used the same laptop since 10.04amd (32bit versions worked fine as well) everything works right out of the box.

HP g56-127nr, the original processor was a AMD v140 (worked fine) and later i wanted to boost it abit for video authoring, so i dropped in a Mobile Turion p540, no blips.

I have maxed it out to 8gb ddr3 1066mhz
Replaced the 5400rpm WD HDD with a seagate momentus XT

(Stock) webcam, synaptic touchpad, video chip(ATi 880g), audio i/o chip (ALC270) and Broadcom network chip all works out of box, even on a LIVE CD. And when installed sleep/resume all works fine.

The machine worked flawless with Ubuntu (and variants)even before the enhancements though ;) 

Only one "issue" was on 11.10amd 64; The Broadcom button turned wireless on and off fine, but always lite up orange as if off- its of no consequence to me though.

---

### Post by Mikeb85 on 2012-08-17
I have a Thinkpad T530 with Intel Graphics and Intel Wireless, and works nearly flawlessly with openSUSE 12.2.  The only thing I haven't got working yet is the fingerprint sensor and smartcard reader, everything else including function keys, brightness control, suspend, etc..., works out of the box.  

Ubuntu was a different story, function keys and brightness control don't work, but wireless, suspend, etc..., still worked very well.

---

### Post by hank22077 on 2012-08-21
Would ANYONE care to help. please?

> **hank22077 said:**
> I recently purchased a Dell Inspiron Mini Duo 3487FNT Convertible Laptop/Tablet. The specs: 

Intel Atom N550 Processor (1.5GHz); 2GB RAM; 320GB Hard Drive; Wireless 802.11n / Bluetooth Combo Card; 10.1" Widescreen HD (1366X768) Multi-Touch Display; Integrated Intel NM10 Express graphics; and Windows 7 Home Premium pre-installed.

I partitioned my hard drive to allocate space for Ubuntu 12.04LTS.
Booted using USB port/flash drive. 
Was prompted during install to connect to my wireless router; and, everything went well, for a few days.

Now, however, each time I try to use Ubuntu the signal goes in and out, I'll have to re-enter the passcode, etc.
The wireless connection on Windows 7 has no issues; and, my kids share an old laptop with Windows XP, which has no issues.

I'm not real keen on this, but it seemed that Ubuntu had saved my wireless connection during install, and was automatically connecting to it just fine for the first few days. Now, I can't keep the connection.

Any insight out there?
Thanks!

---

### Post by TeamRocket1233c on 2012-08-22
Should I ever end up getting a laptop, I sorta wanna put a base command-line install on it, and then build up a desktop from there.

---

### Post by pqwoerituytrueiwoq on 2012-08-22
only thing that does not work is the touchpad off/on button
can't turn it off with the button, everything else works
HP Compaq CQ60-215DX

---

### Post by manvvip on 2012-08-23
Macbook 2,1

---

### Post by Bachstelze on 2012-08-23
MacBook Pro 5,5 (mid 2009) now works completely out of the box with 12.04. :) The only thing I had to install from the Mactel PPA was the fan control daemon.

---

