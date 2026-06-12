---
title: "Plymouth Not Displaying Properly?"
date: 2013-08-22
forum: Ubuntu Studio
---

### Post by Jamie_Edwards on 2013-08-22
Hi guys,

OK, so I know there are a lot of posts out there about this type of issue, but I couldn't find anything about the issue I'm having in specific.

So, I installed the Nvidia 313.30 proprietary driver and low and behold Plymouth goes awry. Fair enough I thought, I'll just fix it by installing "Grub-Customizer" and cycle through the available resolutions till Plymouth plays ball again. To no avail.

Which is why I've posted this. My setup is as follows:

OS: Ubuntu Studio 13.04 64bit,
Screen 1: 1024x768 VGA-DVI
Screen 2: 1360x768 HDMI-DVI

My question is this... Is there a way to make my Plymouth look all nice again?

Thanks.

Jamie

---

### Post by Jamie_Edwards on 2013-08-23
bump

---

### Post by gdesilva on 2013-08-23
Hi, 

I have had similar problems with my Nvidia cards with 32-bit versions of almost all Ubuntu releases. Each time I upgrade the driver, Plymouth goes into a gaga mode....

Try this first...

[http://askubuntu.com/questions/96616/purple-start-screen-no-splash-screen](http://askubuntu.com/questions/96616/purple-start-screen-no-splash-screen)

If that does not work try this...

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

Good luck.

---

### Post by Jamie_Edwards on 2013-08-24
neither one worked?

---

### Post by gdesilva on 2013-08-25
You should have;

1. $ cat /etc/initramfs-tools/conf.d/splash
FRAMEBUFFER=y

2. cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR=#0000ff]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-16,mtrr=3,scroll=ywrap"[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

This is my 32 bit 13.04 system.

Note the [COLOR=#0000ff]GRUB_CMDLINE_LINUX_DEFAULT [/COLOR]line in the /etc/default/grub file which is what would have been modified by running fixplymouth command. In my case I had to set the resolution to 1280x1024 with a color depth of 16 (ie. 1280x1024-16) and with color depth of 24 I had problems. Not sure what resolutions you are running at but just as a test I would use 1280x1024-16 here and if you are successful experiment with other resolutions.

Once you make the changes, make sure to run

1. sudo update-initramfs -u

2. sudo update-grub

and reboot.

Note that they warn not to run fixplymouth twice - I have seen somewhere another script which will undo changes made by fixplymouth but unfortunately cannot remember where - do a Google search if you want to try out fixplymouth again.

---

### Post by Jamie_Edwards on 2013-08-25
OK, so that worked ( I had to manually change to grub file ), but it only displays on my 1024x768 screen ( Screen 1 ). Is there any way that I can get plymouth to display two different resolutions for the two screens separately?

---

### Post by gdesilva on 2013-08-26
Well done!

With regards to dual screen, I am not sure whether grub will display on both screens or not as at the time when plymouth is started the video card drivers will not be loaded yet. Once the system is booted, I guess you can use nVidia settings to activate the second scree but this will not solve your problem with plymouth.

If you do find the solution please post it here, I am curious to know the solution, if there is any.


EDIT: A cursory check shows that my assumption above was incorrect and that it should be possible to run plymouth on dual screen settings. Check out the following links....


[http://askubuntu.com/questions/309999/no-boot-screendual-screen-and-dual-boot](http://askubuntu.com/questions/309999/no-boot-screendual-screen-and-dual-boot)
[http://ubuntuforums.org/showthread.php?t=2036238](http://ubuntuforums.org/showthread.php?t=2036238)
[https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth)

---

### Post by Jamie_Edwards on 2013-09-18
I know that I'm pretty much opening an old thread again, but I'd managed to figure out why it was displaying on my vga monitor rather than my HDMI monitor.

The reason behind it is because there is a primary and secondary display adapter on my graphics card ( I think this is the case for both nVidia and ATi cards ) and at the time I had my VGA in the primary output. So I changed them around so my HDMI is not in the primary and it's displaying on my 1360x1024 monitor ( which is the one I wanted )

---

