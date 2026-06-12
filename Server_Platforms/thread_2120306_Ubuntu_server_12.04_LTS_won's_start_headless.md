---
title: "Ubuntu server 12.04 LTS won's start headless"
date: 2013-02-26
forum: Server Platforms
---

### Post by habrys on 2013-02-26
I just installed Ubuntu server 12.04 LTS, configured SSH server, keys etc. It's accessible remotely over ssh, everything works.

But if I remove video card (which I don't need anymore, since it's supposed to run headless and consume as little power as possible), the server is not accessible via SSH anymore after reboot. When I insert the video card again and reboot, everything works as expected again.

I browsed a little bit through log files, but didn't find anything so far. Any advices? It's probably something common and easy...

---

### Post by TheFu on 2013-02-26
Could it be that your BIOS is set to not boot if there isn't a video card?  It is often shown as "break on errors: None"  video, keyboard are other common options.

I haven't tried booting without a cheapo video card inside any physical Linux box in over 10 yrs, but back then - it was Redhat something - it worked and ran as a headless server for over a year between reboots.  That box worked for about 3 yrs before the cheap capacitors exploded. It was an early dual CPU Celeron SMP box when SMP Linux was new to home users.

Virtual machines, including Ubuntu VMs, boot without a video card attached all the time. They just need a tty assigned should something bad happen and network connectivity fail.  I have a few 8.04, 10.04 and 12.04 VMs running this way right now.

If that isn't it - and I have no real idea, just brainstorming here.

---

### Post by habrys on 2013-02-26
> **TheFu said:**
> Could it be that your BIOS is set to not boot if there isn't a video card?  It is often shown as "break on errors: None"  video, keyboard are other common options.

Nope. The same machine was running Ubuntu Server 12.04 LTS before and it started without video card. A few days ago HDD broke, so I decided to install Ubuntu fresh. But apart from the disk the hardware and BIOS configuration is the same as before.

I do recall having the same problem the first time around (installed in April 2012) and doing something on the system level, but sadly cannot recall the details. Stupid... Kinda hoped it's some common trick and a quick answer pops up here.

Ok, time to do some serious digging in the log files.

Thanks for your advice, TheFu. And if someone has had similar problems, please share solution.

---

### Post by habrys on 2013-02-26
The problem was Grub2 expecting to have a video card to render its menu in graphic mode. To switch to text mode uncomment following line in /etc/default/grub
```
GRUB_TERMINAL=console
```

Afterwards don't forget to generate the actual grub config file with:
```
sudo update-grub
```

That's it, the server starts without video card now.

There is a default behavior of Grub2, which added to confusion during analyzing of the problem: after ungraceful system shutdown (power failure or just switching off as in my case), during next startup Grub waits for keyboard input forever (instead of the default 2 seconds). It can be kinda confusing, without video card inserted to see what actually happens...

To disable it and force booting the default OS after 2 seconds add following line to the /etc/default/grub (undocumented, but works):
```
GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT
```
Of course, do it **after** setting the GRUB_TIMEOUT.

Also it's helpful to switch on the Grub beep sound if you run in headless mode. To do so, uncomment following line in /etc/default/grub
```
GRUB_INIT_TUNE="480 440 1"
```

As usually, after performing your changes, don't forget to:
```
sudo update-grub
```

Here is my /etc/default/grub file after all changes:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"
```

Hope it helps somebody to spare some time.

---

### Post by sudodus on 2013-02-26
I was following this thread but had nothing to contribute until now: Thank you for sharing your result :KS
:-)

---

### Post by Brendon_Wolff-Piggott on 2013-10-14
Thanks for this.  For some reason making the changes individually didn't force starting after hard power down, but closely copying your /etc/default/grub has done the trick :D

---

