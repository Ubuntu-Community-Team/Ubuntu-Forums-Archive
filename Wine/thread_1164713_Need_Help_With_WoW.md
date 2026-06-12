---
title: "Need Help With WoW"
date: 2009-05-19
forum: Wine
---

### Post by r3l3ntl35 on 2009-05-19
ive been trying for like 4 days now to get wow on installed under wine, and i was having a problem even getting the wow to intall, but i got past that. now when i open the wow launcher to click on "PLAY" the critical error message comes up n wow crashes. i  cant even get to my character page. i can still hear sound playing in the background. ive tried looking all over the forums for a solution n i just cant find anything to help... please help! im running ubuntu jaunty

---

### Post by jualin on 2009-05-20
> **r3l3ntl35 said:**
> ive been trying for like 4 days now to get wow on installed under wine, and i was having a problem even getting the wow to intall, but i got past that. now when i open the wow launcher to click on "PLAY" the critical error message comes up n wow crashes. i  cant even get to my character page. i can still hear sound playing in the background. ive tried looking all over the forums for a solution n i just cant find anything to help... please help! im running ubuntu jaunty

Try [this website]("http://www.wowwiki.com/Wine") ):P

---

### Post by Frostsniper on 2009-05-20
> **r3l3ntl35 said:**
> ive been trying for like 4 days now to get wow on installed under wine, and i was having a problem even getting the wow to intall, but i got past that. now when i open the wow launcher to click on "PLAY" the critical error message comes up n wow crashes. i  cant even get to my character page. i can still hear sound playing in the background. ive tried looking all over the forums for a solution n i just cant find anything to help... please help! im running ubuntu jaunty


EASY FIX!!! dude just add this to the command line (right click- properties) of the icon (for WOW) on your desk top for example mine WAS

env WINEPREFIX="/home/Frost/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"

Just add              -opengl                   so is should be after like this 

env WINEPREFIX="/home/Frost/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl 

that fixed it for me =)! hope it helps!   (errr not sure if the space matters between the " *here* -opengl if some one could enlighten me i don't think it does though but w/e mine still has the space =) )

Also Yes i know this is launching the news, and not the game so if you wanted to skip the news you probably have to change what .exe its opening maybe to wow.exe? i don't know =/

---

### Post by r3l3ntl35 on 2009-05-21
ok i added -opengl to the command, this gets me a little further. i can actually see and hear the cinematic intro to the game. but after the cinematics, the login screen that should appear after that doesnt show up right. its like split into 3 sections. no mouse shows up and i cant do anything. all i can do is rotate my cube to the next desktop over and open  up a process manager and end the wow.exe process... any help?

---

### Post by Frostsniper on 2009-05-21
> **r3l3ntl35 said:**
> ok i added -opengl to the command, this gets me a little further. i can actually see and hear the cinematic intro to the game. but after the cinematics, the login screen that should appear after that doesnt show up right. its like split into 3 sections. no mouse shows up and i cant do anything. all i can do is rotate my cube to the next desktop over and open  up a process manager and end the wow.exe process... any help?

ahhhhh  that's your problem the rotating cube. I have no fancy desktop add-ons at all, non-in fact . So try getting rid of them or turning them off and see if that helps. I read that they can seriously mess up gaming and such. ( i could be wrong though) eh give it a shot?

---

### Post by r3l3ntl35 on 2009-05-21
just tried that, no difference... my whole computer freezes when i try 2 run this, have to maually turn off and back on... i have a feeling it may be some sort of problem with a grafix driver...? idk what i have for a grafix card

---

### Post by random_hypocrisy on 2009-05-21
> **r3l3ntl35 said:**
> just tried that, no difference... my whole computer freezes when i try 2 run this, have to maually turn off and back on... i have a feeling it may be some sort of problem with a grafix driver...? idk what i have for a grafix card

Run this command in Terminal. 

**lspci -v**

Then copy and paste the result back here.

---

### Post by r3l3ntl35 on 2009-05-21
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

---

### Post by random_hypocrisy on 2009-05-21
> **r3l3ntl35 said:**
> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

What version of Ubuntu are you using?

---

### Post by r3l3ntl35 on 2009-05-21
jaunty

---

### Post by Frostsniper on 2009-05-21
> **r3l3ntl35 said:**
> jaunty

9.04?  right?

---

### Post by random_hypocrisy on 2009-05-21
> **r3l3ntl35 said:**
> jaunty

Jaunty has a major bug regarding Intel graphics chips, which is what you have. 

Download Hardy Heron, heres the ISO;

[http://releases.ubuntu.com/8.04/ubuntu-8.04.2-desktop-i386.iso](http://releases.ubuntu.com/8.04/ubuntu-8.04.2-desktop-i386.iso)

And you should be ok.

---

### Post by themusicalduck on 2009-05-22
Open your Wow Config.wtf file at which will be in the WTF folder of your Wow install in a text editor.

Add these 3 lines onto the end of it:

SET gxApi "OpenGL"
SET ffxGlow "0"
SET ffxSpecial "0"

Now install simple-ccsm 

```
sudo apt-get install simple-ccsm
```

Type that into a terminal.

Then go to system > preferences > Appearance

On the visual effects tab set effects to 'none'

Now Wow should run fine.

If it doesn't for some reason, try opening WoW in a terminal.

```
wine /path/to/Wow.exe
```

and put the output up here.

To get your compiz effects back on, on the same tab in appearance set it to 'Custom'

Hope that helps a bit.

---

### Post by sesheron on 2009-05-23
Turning on nothing for special effects worked at first for me too..but almost right after logging in all the text on the screen started flying around in jagged lighting bolts...  quite weird considering everything else works great at near 60 fps

---

### Post by r3l3ntl35 on 2009-05-23
> **themusicalduck said:**
> Open your Wow Config.wtf file at which will be in the WTF folder of your Wow install in a text editor.

Add these 3 lines onto the end of it:

SET gxApi "OpenGL"
SET ffxGlow "0"
SET ffxSpecial "0"

Now install simple-ccsm 

```
sudo apt-get install simple-ccsm
```Type that into a terminal.

Then go to system > preferences > Appearance

On the visual effects tab set effects to 'none'

Now Wow should run fine.

If it doesn't for some reason, try opening WoW in a terminal.

```
wine /path/to/Wow.exe
```and put the output up here.

To get your compiz effects back on, on the same tab in appearance set it to 'Custom'

Hope that helps a bit.


i cant open up the config.wtf yet bc it doesnt exist yet. at least i think anyway, i still cant get it up

---

### Post by random_hypocrisy on 2009-05-23
> **r3l3ntl35 said:**
> i cant open up the config.wtf yet bc it doesnt exist yet. at least i think anyway, i still cant get it up

**If you have an Intel graphics chip**, **YOU DO NOT WANT TO USE JAUNTY**. **Install Hardy Heron instead**!

---

