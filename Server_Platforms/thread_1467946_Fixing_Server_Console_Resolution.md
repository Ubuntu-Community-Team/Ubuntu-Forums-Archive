---
title: "Fixing Server Console Resolution"
date: 2010-05-01
forum: Server Platforms
---

### Post by mkabala on 2010-05-01
Hi all. I just upgraded my Ubuntu Server to 10.04 and I'm having a big problem with one of the "features" of the upgrade. I'm using this server as a test site for web development and have not installed a graphic desktop onto the machine. However, the console is suddenly using a much higher screen resolution than previously and the type is absolutely tiny! Is there a way to set the machine to boot up into a lower resolution so that I can read the console screen again without having to open a remote console on another machine? Remember, I don't have X installed, so I need a solution that doesn't depend on a graphic desktop. modifying /etc/default/grub has absolutely no effect even after I run update-grub and reboot.
 
Thanks for your help.

---

### Post by Mirko Scurk on 2010-05-09
I posted similar question long ago at the time 09.10 was released and still haven't find answer. Yesterday I installed 10.04 and problem is still there.  Console text is so small it's painful to read. Who got this brilliant idea to change something that should be default - standard console without fb or whatever mumbo-jumbo?

Anyone please?

---

### Post by Mirko Scurk on 2010-05-09
Here on forums mentioned workaround is to run

#sudo dpkg-reconfigure console-setup

and find some font that is better suited but that doesn't change fact that you are still running framebuffer in some crazy resolution (maximum supported by your monitor).

Don't know how to turn that damn thing off and return to simple text mode.

How to show students via projector what you are doing in shell when installation adjusted FB to monitor's resolution which is usually not supported by projector?

---

### Post by Queue29 on 2010-05-09
Ironic, adjusting the console resolution and/or font in Windows is trivial.

---

### Post by TheFuturian on 2010-05-10
I'd describe this as a feature rather then a bug, however if you want to control the native console resolution you must append the correct kernel option to /boot/grub/menu.lst, i.e. :-

```
title           Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-27-generic root=UUID=cce0f258-846e-43ab-96bb-74291e2a2cd4 ro quiet splash **vga=795**
initrd          /boot/initrd.img-2.6.24-27-generic
quiet

```

The option can be specified in either Hex or Binary, i.e. vga=795 is the same as vga=0x31B. There is a chart with some possible options within the link below:-

[http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html)

---

### Post by TheFuturian on 2010-05-10
**_Better Chart_**

```
FRAMEBUFFER RESOLUTION SETTINGS
+-------------------------------------------------+
     | 640x480    800x600    1024x768   1280x1024
 ----+--------------------------------------------
 256 | 0x301=769  0x303=771  0x305=773   0x307=775
 32K | 0x310=784  0x313=787  0x316=790   0x319=793
 64K | 0x311=785  0x314=788  0x317=791   0x31A=794
 16M | 0x312=786  0x315=789  0x318=792   0x31B=795
+-------------------------------------------------+
```

---

### Post by TheFuturian on 2010-05-11
**_Yet even better info_**

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by CharlesA on 2010-05-11
Thanks for the info, I'll be bookmarking this thread. :)

I kinda like how it adjusts the size of the text to run at the native res of the monitor, but it does make it a bit of a pain if the text is too small.

---

### Post by gobbledigook on 2010-05-11
hi! this is a problem which has niggled at me for a while too, but i have just lived with it....

another console related query is, how do you see the text which has gone off the top of the screen? page up does nothing and we all know what the up arrow key does ;)

---

### Post by CharlesA on 2010-05-11
> **gobbledigook said:**
> hi! this is a problem which has niggled at me for a while too, but i have just lived with it....

another console related query is, how do you see the text which has gone off the top of the screen? page up does nothing and we all know what the up arrow key does ;)

As far as I know, you cannot see it. I usually pipe stuff that floods the screen to either less or more.

```
ls -l | less
```

---

### Post by nyquist1 on 2010-05-17
> **gobbledigook said:**
> hi! this is a problem which has niggled at me for a while too, but i have just lived with it....

another console related query is, how do you see the text which has gone off the top of the screen? page up does nothing and we all know what the up arrow key does ;)

Hi, you should try "SHIFT+PageUp" "SHIFT+PageDown".

Regards,

---

### Post by CharlesA on 2010-05-17
> **nyquist1 said:**
> Hi, you should try "SHIFT+PageUp" "SHIFT+PageDown".

Regards,

Great. Thanks for the tip!

---

### Post by laytek on 2010-07-09
This procedure fixed my console resolution in Ubuntu 10.04 server.

Restart computer. Press and hold shift key until GRUB loads and diplays menu.
Press c to open a command line terminal.
Enter vbeinfo to display (BIOS) supported video modes.
Choose desired resolution from list (1024x768 in my case).
Press ECS to return to menu.
Press ENTER and boot computer.
Log in to computer.

Change to the /etc/default directory
```
user@arcturus:~$ cd /etc/default/
```
Make a copy of /etc/default/grub
```
user@arcturus:/etc/default/$ sudo cp grub grub.orig
```
Edit /etc/default/grub to reflect changes shown in diff below
```
user@arcturus:/etc/default$ diff -u grub grub.orig
--- grub	2010-07-09 21:56:38.300144137 -0400
+++ grub.orig	2010-04-13 09:40:04.000000000 -0400
@@ -6,7 +6,7 @@
 GRUB_HIDDEN_TIMEOUT_QUIET=true
 GRUB_TIMEOUT=10
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
-GRUB_CMDLINE_LINUX_DEFAULT="quiet"
+GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 GRUB_CMDLINE_LINUX=""
 
 # Uncomment to disable graphical terminal (grub-pc only)
@@ -15,7 +15,7 @@
 # The resolution used on graphical terminal
 # note that you can use only modes which your graphic card supports via VBE
 # you can see them in real GRUB with the command `vbeinfo'
-GRUB_GFXMODE=1024x768
+#GRUB_GFXMODE=640x480
 
 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
 #GRUB_DISABLE_LINUX_UUID=true
```
Change to the /etc/grub.d directory
```
user@arcturus:/etc/default$ cd /etc/grub.d/
```
Make a copy of /etc/grub.d/00_header
```
user@arcturus:/etc/grub.d$ sudo cp 00_header 00_header.orig
```
Edit /etc/grub.d/00_header to reflect changes shown in diff below
```
user@arcturus:/etc/grub.d$ diff -u 00_header 00_header.orig 
--- 00_header		2010-07-09 21:14:36.126521341 -0400
+++ 00_header.orig	2010-04-13 09:59:26.000000000 -0400
@@ -101,7 +101,6 @@
     cat << EOF
 if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
   set gfxmode=${GRUB_GFXMODE}
-  set gfxpayload=keep
   insmod gfxterm
   insmod ${GRUB_VIDEO_BACKEND}
   if terminal_output gfxterm ; then true ; else
```
Run update-grub to build new grub.cfg
```
user@arcturus:/etc/grub.d$ sudo update-grub
```
Reboot

Although the console is not at the highest resolution of my monitor (1440x900), it is at the highest supported resolution and is much better than original. YMMV

Laytek

---

### Post by Tamás Kiss on 2010-12-10
Thank you for posting this solution, laytek, I'll try it soon. In exchange I'd like to give you an advice you might find useful: :)

I noticed that you use the diff utility the other way around compared to how it is meant to be used. You keep writing "diff -u newfile oldfile", so the resulting diffs tell us how to change the newer version of the file to get back the original version. If you'd try "diff -u oldfile newfile", the diffs would show how to edit the _old_ version to get the _new_ one. Hope that helps. :)

---

### Post by sgoran on 2010-12-27
I do this and nothing change. One question why you enter grub mode on startup. Just to see modes for your VGA or I did't understand well.

---

### Post by cariboo on 2010-12-27
Why not just access the server via ssh from your desktop, either use a terminal when running Ubuntu, or PuTTY when running windows. You can zoom the text in a terminal for better readability.

---

### Post by saivert on 2010-12-27
this also helps for us running Ubuntu Server in VMWare Workstation and wanting a bit more screen estate. the default 80x25 display is very annoying.

too bad the guest tools don't auto-adjust the display.

a decent tip is also to add this to /etc/rc.local before exit 0
/usr/bin/setterm -powersave off -blank 0

---

### Post by Eric106 on 2011-01-10
I wanted to pass on a little information I learned while struggling through this issue.

The short answer is that passing a modeset=0 option to the video driver keeps it from switching modes and it will then honor the vga= option and not change resolutions.

In my case I append radeon.modeset=0 vga=791 to my Linux kernel boot options in GRUB and the system will then stay in the mode I choose.  

Nothing else I did would keep the video driver module from changing the resolution when it loaded.  No changes in /etc/default/grub would persist once the radeon module loaded; it would always maximize the resolution.

You can execute modinfo radeon | grep parm to see if your video driver module supports the modeset parameter.  Just replace radeon with the name of your video driver.

See also my other post on this issue [here]("http://art.ubuntuforums.org/showthread.php?p=10340556#post10340556") for more information.

-Eric

---

### Post by TheFuturian on 2011-05-06
This information worked for me on 10.04:-

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by MAFoElffen on 2011-05-06
> **TheFuturian said:**
> I'd describe this as a feature rather then a bug, however if you want to control the native console resolution you must append the correct kernel option to /boot/grub/menu.lst, i.e. :-

```
title           Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-27-generic root=UUID=cce0f258-846e-43ab-96bb-74291e2a2cd4 ro quiet splash **vga=795**
initrd          /boot/initrd.img-2.6.24-27-generic
quiet

```The option can be specified in either Hex or Binary, i.e. vga=795 is the same as vga=0x31B. There is a chart with some possible options within the link below:-

[http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html)
>>> KMS (Kernel Mode Set) for both tty and GUI...  Is supposed to take whatever the kernel is set to (and go from there).  My sticky (link below) has a lot of info on how to figure out what modes your hardware supports and how to use kernel boot switched and grub gfxmode sets to implement them.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by MAFoElffen on 2011-05-06
> **Eric106 said:**
> I wanted to pass on a little information I learned while struggling through this issue.

The short answer is that passing a modeset=0 option to the video driver keeps it from switching modes and it will then honor the vga= option and not change resolutions.

In my case I append radeon.modeset=0 vga=791 to my Linux kernel boot options in GRUB and the system will then stay in the mode I choose.  

Nothing else I did would keep the video driver module from changing the resolution when it loaded.  No changes in /etc/default/grub would persist once the radeon module loaded; it would always maximize the resolution.

You can execute modinfo radeon | grep parm to see if your video driver module supports the modeset parameter.  Just replace radeon with the name of your video driver.

See also my other post on this issue [here]("http://art.ubuntuforums.org/showthread.php?p=10340556#post10340556") for more information.

-Eric
You can also 
[code]
[SIZE=1]# ATI Radeon: 
 echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf  
[code]
Or for other cards... basicall add you edits to the _video_driver_type_-kms.conf  files in /etc/modeprobe...d/ and use... (from the KMS wiki)

[/SIZE][SIZE=1] For  some users (particularly users with encrypted volumes) KMS is  enabled  very early in the boot process and in order to pick up these  changes you  need to run 
[code]
sudo update-initramfs -u. [/SIZE]
[code] This does seem to help out allot with natty and these new kernel versions of late..

---

