---
title: "Stuck on &quot;Monitor input timing not supported&quot;"
date: 2011-09-27
forum: Server Platforms
---

### Post by paul1149 on 2011-09-27
Hi,

I've just installed Ubuntu server 11.04 x86, on older hardware, but with a widescreen monitor. The install disk had no problem dealing with my 1366 x 768 x 60Hz display, but the install did not pick up monitor resolution? Consequently I get the error:

The current input timing is not supported by the monitor....

and I cannot see what, if anything, is happening in the background.

I'm on a multiboot disk, so I guess I can get into the grub config or the resolution settings. Does anyone have any clues where to start?

---

### Post by paul1149 on 2011-09-27
I don't want to start off on the wrong foot here, but this is a heck of a thing. This is a multiboot disk, and unless and until I can somehow change Grub2, from outside the partition - which is no small thing from my point of view - or install a different MBR boot manager that actually works, all the installs on the disk are hosed. More is on the line here than just this new install - which would be bad enough. This, quite frankly, is a load of hooey.

---

### Post by bzoromski on 2013-04-07
I don't have an answer for you sorry. I have the same problem. I upgraded to the newest version and now my monitor settings aren't compatable and I can't access windows 7 since it's on a partition with unbuntu. I can still get on unbuntu. I need to know how to fix my monitor resolution and get back into windows.

---

### Post by MAFoElffen on 2013-04-08
At boot up, just past the BIOS POST messages, press the left shift key and look for the Grub menu to show. Be quick and hit a down arrow key. The grub menu only displays 2 seconds in a default server install. 

Once you hit aan arrow key while that menu is up, it will stay there. Arrow back to the top menu item. Press the <e> key to get into an edit mode on that menu entry. Press the <c> key and get to a grub commandline, tye in
```

vbeinfo

```
That will display the frame buffer info on your boxes graphics hardware. Write down the resolutions and the refresh rate for the default modes. Like at your monitor specs for the lower resolutions and refresh rates.

Type 
```

exit

```
to get back to the menu edit mode in that default menu item. <Arrow-Down> until you get to the line that starts with "linux"... then <Right-Arrow> until you get to the end of that line.

Look at your reslution and refresh rates. Select one that your GPU and monitor can both do. For instance, I use a KVM switch with an HP KVM rack mount console, but it only uses a 60Hz refresh rate and the best resolution is 1024x768. Fine for servers, but must GPU's default refresh rates are 50Hz... Anyways, at the end of that boot line, using my example specs, append/add:
```

nomodeset video=VGA:1024x768@60m

```
which translates to turn off modesetting/no KMS, set the VGA port to 1024x768, set vert refresh at 60Hz and add a margin. Adjust that to a port you are using (was noted by vbeinfo), to a usable resolution (also in vbeinfo), and at a sensible refresh rate (also in vbeinfo).

Then press <F10> to boot. If you find something that works for you, you can make that persistent in grub editing the /etc/default/grub file... by adding it to the GRUB_CMDLINE_LINUX_DEFAULT entry. To set resolutions of the VT consoles, you can set them in 
the GRUB_GFXMODE entry. I usually set mine to 1024x768x24. Or you can turn off KMS and use a total text only mode by adding a line to the end saying
```

GRUB_GFXPAYLOAD_LINUX=text

```
At the end of the file. Of course after editting that file, you have to run
```

sudo update-grub

```
to pickup any changes in that file to the grub menu. If you need more refrence, look at posts 1&2 of my sticky (link in my sig line).

---

### Post by MAFoElffen on 2013-04-08
> **bzoromski said:**
> I don't have an answer for you sorry. I have the same problem. I upgraded to the newest version and now my monitor settings aren't compatable and I can't access windows 7 since it's on a partition with unbuntu. I can still get on unbuntu. I need to know how to fix my monitor resolution and get back into windows.
If you are having problems getting back to Windows graphics, from a Linux exit... your GPU or Monitor are stuck in a mode. If you shutdown, turn off the PSU, unplug the power from the CPU and montior and remove the video cable to the monitor... Le it sit disconnected a few, then connect everything back together... It should work again. Long term fix is set your graphics mode in Ubuntu closer to what you are using in Windows.

Pay attention to what the mode is in the Grub Default file, if any... on shutdown from graphics modes (server console also is now basic VGA framebuffer graphical VT sessions) the exit graphic modes are set by whatever is set in that same /etc/default/grub file.

---

