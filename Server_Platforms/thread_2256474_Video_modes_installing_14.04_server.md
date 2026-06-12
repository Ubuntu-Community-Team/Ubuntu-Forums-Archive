---
title: "Video modes installing 14.04 server"
date: 2014-12-12
forum: Server Platforms
---

### Post by cearlp on 2014-12-12
I am installing Ubuntu Server on an older PC that has an HP 2011x monitor (normal resolution is 1600x900). Immediately after I select the 'Install Ubuntu Server' option I get a screen displaying 'Undefined video mode number: 314.  Press <Enter> to see video modes available, ...'.
I selected Enter and from the list of available modes I have installed three different times selecting one of each types, VGA, VESA and BIOS (one with the x25 resolution) each time. The installations succeed, but when the reboot occurs the screen is completely white with all sorts of black marks instead of readable characters. I can't bring up a terminal to do any of the video mode adjustments that I have seen Googling the subject and would appreciate any suggestions.
Thank in advance.

---

### Post by MAFoElffen on 2014-12-12
The mode of the install, has nothing to do with the video mode setting of the installed system after the install is finished. Before getting to the montior, it has to go through the display.

Even though you will get a text-like screen in server, the console is actually virual tty consoles in a VGA paltte, so the default display in server is graphical. If you would like to keep using VGA graphics (I would recommend that), when it boot's right as the BIOS messages finsih, start pressing the left shift key for the Grub Boot menu to display... then quickly press the <down-arrow> key. That will keep the menu displayed (and keep it from continuing on).

At the grub menu, first move the highlighted selection to the Rescue mode option. Press "e" to get into an edit mode. Move the cursor down to the line that starts with "linux". Move to th end of that line and delete "quite splash". In it's place, type "nomodeset". Press <cntrl><X> to boot that editted "Rescue" option. 

The system will boot into rescue mode to it's Rescue Menu. Select "enable networking"... That will enable networking, but more importantly, it also mounts the filesystem in rw mode. Then select "drop to root prompt".

At the root prompt:
```

lspci -vnn | grep -i VGA

```
Note what it says and post it here. Then:
```

vi /etc/default/grub

```
Press <Insert> to go into an insert edit mode
At the lines that start with the following headers, change to these values for now...
```

#This at default has a blank value, use the generic KMS off flag for now... may change later to be more specific to your video card
GRUB_CMDLINE_LINUX_DEFAULLT='[COLOR=#ff0000]nomodeset[/COLOR]'
# set the console resolution here, default is comment out 
GRUB_GFXMODE=[COLOR=#ff0000]1024x768x16[/COLOR]

```
After the changes, press <ESC>, <ESC> (twice), then tpye thse characters to save and exit:
```

:wq

```
then <Enter>

Then:
```

update-grub
shutdown -r now

```

Tell me how it goes...

If you jwant a just a true text console, then add this line to the end of that same file, then running update-grub:
```

GRUB_GFXPAYLOAD_LINUX=text

```

---

### Post by cearlp on 2014-12-13
Thank You MAFoElffen.
I'll try to explain what I did following your instructions.
On the GRUB screen I didn't get a 'Rescue' mode but I got an 'Advanced options for Ubuntu' and selected that. That gave me two other options to boot generic or boot in recovery mode, which I selected.
After that booted I got the Recovery Menu screen which included the network enable and the drop to root shell prompt options.
First, I selected the remount network enable option and and got the  'mount  filesystem in R/W mode' screen.
Accepting that screen it dropped out of graphical mode and the system did a fsck and a clean of the partition.
After quite some time with nothing happening (no disk activity) I hit cntrl-c and after a screen of activity statements scrolled by I got a login prompt.
After logging in I went thru your editing instructions of the GRUB file using the sudo command on each one.
here is the output of the lspci command:

00:02.0 VGA compatible controller [0300]: Intel Corporation 82815 Chipset Graphics Controller (CGS) [8086:1132] (rev 02) (prog-if 00 [VGA controller)

I found the lines in GRUB you said to change and that was pretty straight forward, I thought.
However, on the reboot after shutdown the same white screens with all sorts of what appears to be black distorted characters are all that appear during the startup process.
I didn't do the last suggestion about true text console, but I am going to try that  next.

---

### Post by cearlp on 2014-12-13
After adding the GRUB_GFXPAYLOAD_LINUX= text line to the GRUB configuration no more white screen,,,just a text console.  Which is fine for me for a server machine.

---

