---
title: "No HDMI after server reboot with TV OFF"
date: 2015-09-09
forum: Server Platforms
---

### Post by eggzenbeanz on 2015-09-09
Hello,

I have a server connected to an HDTV via HDMI in my lounge. When I reboot the server with TV off I cannot then get access to the server box, it's seemingly off line or not responding to SSH connections. If I need to reboot the machine I need to physically turn the TV on and reboot as normal. 

Is there a way to force the HDMI or make the server skip this check so I can reboot remotely? 

Running 15.04 server without desktop installed

thanks

---

### Post by MAFoElffen on 2015-09-09
When Linix layers initialize in a boot sequence, it looks at the attached hardware to determine what it needs to do. 

*** Even if you think Server is "Text," it still uses basic VGA graphics and the graphics hardware. Even if headless, a remote presentation touches parts of the original system.

If you boot and the TV is on, it sees the hardware ans keeps that port on... It not on, you need to tell it what is not there, and that even though it does not see something, that you want it to stay on...

In server, xorg Xserver is not installed by default. It is just a basic graphics layer provided by the hooks in the kernel. . You could use xrandr to turn on a port and set a mode, but then to make it persistent, you have to do it from a script called at boot, after the graphics layer is initialized. This will provide basic graphics support to a port, even if something is not turned on at boot. 

Alternately, another way is to install a minimal xorg XServer (to load/unload as an instance). If xorg Xserver does not see a monitor attached to a port, it's default is to not turn on that port... It does this by looking for the EDID in a monitor to see which modes it needs to support on that port... If, in an etc/X11/xorg.conf file, you tell it to ignore an EDID of an attached monitor abd provide one for it manually in that file via modelines, then it will keep that port active with those modes. This will provide full support to something, even if not on at boot. There is more overhead... and other trade-offs... but just when that instance is loaded.

I do it both ways (depending on the roles and their security risk), because I have 8-15 servers connected to my server console (one keyboard and monitor per bank) through KMS switches... I have to provide a mode. as my rack mount console is sort of an oddball and is squeamish about being probed for modes, so I manually tell a system to use the specific mode it likes.

If you need to ask more questions, or need additional help, just ask.

---

### Post by eggzenbeanz on 2015-09-09
Hi,

Thanks for the info, very interesting!

I'd like to avoid installing Xserver as I really don't need it and like my lean running setup.

When I run xrandr I get "can't open display" returned. Any ideas?

cheers

---

### Post by MAFoElffen on 2015-09-09
With your TV connected and turned on, boot your server. After you login, at the prompt:
```

xrandr -q 

```
You should get results similar to this:
```

$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```
You need something like that to see what it is ID'ing the port your TV is connected to, and the modes it supports. 1080p is mode resolution 1920x1080... The reason the user needs to do that command on their own hardware, is that different vendors GPU's ID the port names differently and the name has to be the exact name by character and case.

So, if you had that resolution and a port named HDMI1, then you would try the xrandr command:
```

xrandr --output HDMI1 --mode 1920x1080

```

Most docs tel you to put that in a user's /home/user_name/.xprofile or ~/.bashrc file... sort of. You want it to be global, not user. A user login would be after where you need that. So you would add a line to the end of /etc/.bashrc, or add a script to /etc/init.d/ that contains that...

What I also have to do is set my virtual term resolution in /etc/defaults/grub and update grub... you couldl just set gfx grub graphics mode to text and be done with that, but I like to set a resolution to see more on my screens...

---

### Post by eggzenbeanz on 2015-09-10
Thanks for the info. I can't get any results when running xrandr command. A fresh reboot, login locally I get "can't open display" on any xrandr commands. Weird!!

---

### Post by MAFoElffen on 2015-09-10
My bad, xrandr affects X and X is not really loaded is it... So to change KMS (Kernel mode switching) in grub , kernel and the VGA graphics layer...

For file /etc/default/grub, edit with your favorite editor. Change these lines:

This would set the virtual terminal to 1920x1080, which is 1080p... And use the first HDMI port at that mode...
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset video=HDMI1:1920x1080-32@60"
#GRUB_TERMINAL=console
#GRUB_GFXPAYLOAD_LINUX=text
GRUB_GFXMODE=1920x1080x32

```



Or this would set a straight text mode:
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_TERMINAL=console
GRUB_GFXPAYLOAD_LINUX=text
# Make sure the next line is commented out
#GRUB_GFXMODE=640x480

```


Either way you need to update your grub.cfg via this command:
```

sudo update-grub

```

I also have some custom VGA pallets for the server virtual terminal...

---

### Post by eggzenbeanz on 2015-09-14
Thank you! That's done the trick! - I'm learning lots too, cheers for your help.

---

### Post by MAFoElffen on 2015-09-15
You're welcome.

Please revisit this thread. Use the Thread Tools link on the upper right of the thread page to mark this thread as "Solved."

First, it helps members & staff to know that no further help is needed. Second, it helps members with the same question or problem to be able to find working solutions.

---

### Post by craig20 on 2015-12-18
Apologies for reviving a solved thread.

I tried this option.......


[COLOR=#000000]My bad, xrandr affects X and X is not really loaded is it... So to change KMS (Kernel mode switching) in grub , kernel and the VGA graphics layer...[/COLOR]

[COLOR=#000000]For file /etc/default/grub, edit with your favorite editor. Change these lines:[/COLOR]

[COLOR=#000000]This would set the virtual terminal to 1920x1080, which is 1080p... And use the first HDMI port at that mode...[/COLOR]
[COLOR=#000000]Code:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset video=HDMI1:1920x1080-32@60"
#GRUB_TERMINAL=console
#GRUB_GFXPAYLOAD_LINUX=text
GRUB_GFXMODE=1920x1080x32[/COLOR]


[COLOR=#000000]Or this would set a straight text mode:[/COLOR]
[COLOR=#000000]Code:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_TERMINAL=console
GRUB_GFXPAYLOAD_LINUX=text
# Make sure the next line is commented out
#GRUB_GFXMODE=640x480[/COLOR]

[COLOR=#000000]Either way you need to update your grub.cfg via this command:[/COLOR]
[COLOR=#000000]Code:
sudo update-grub[/COLOR]
[COLOR=#000000]I also have some custom VGA pallets for the server virtual terminal...[/COLOR]


but I receive 'Unable to connect to VNC server' when trying to connect by Remmina Desktop. I can ssh into the server...(but that is about the level of my skill set I am afraid!!!!)

What other options do I have? I am about to install a projector in the place of the tv and don't want turn it on each time I need to access my pc.

---

