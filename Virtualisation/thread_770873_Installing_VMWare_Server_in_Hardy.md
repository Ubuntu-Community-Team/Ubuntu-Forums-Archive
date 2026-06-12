---
title: "Installing VMWare Server in Hardy"
date: 2008-04-27
forum: Virtualisation
---

### Post by Kokopelli on 2008-04-27
This is a cleaned up copy of the instructions for installing the VMWare Server from tar.gz found at [http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976) with a correction thanks to forrestallen.  Since the Hardy Beta forums are now locked I thought it might be best to make a copy here to allow further discussion if needed.  


First install the packages needed by vmware.

```

sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install xinetd

```

for 64bit installs also install the ia32-libs
```

sudo apt-get install ia32-libs

```

Additionally I recommend installing the linux-header metapackage appropriate to your kernel.  "sudo apt-get install linux-headers-generic" for desktops in the standard kernel and "sudo apt-get install linux-headers-server" for server installs.  This makes it easier down the road, automatically pulling down the headers if the kernel gets updated.

next download vmware server and expand it out somewhere
```

tar -xvzf VMware-server-1.0.6-91891.tar.gz

```

then do the install
```

cd vmware-server-distrib
sudo ./vmware-install.pl

```

Answer the questions, the defaults are fine, though you may want to customize the network config.

once installed I received an error trying to launch vmware so I cheated and copied the libraries over, which seems to have resolved that issue.
```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```
(I found this tip online as well but now I can not find the link.)

if you get an error like this at the end of the compile step:
```

Unable to get the last modification timestamp of the destination file 
/etc/vmware/ssl/rui.key.

```

then create the key and cert files for vmware.  (I think, though I am not certain, this came up because I had not yet installed the ia32-libs on my 64-bit machine prior to doing the initial install.)
```

sudo touch /etc/vmware/ssl/rui.key
sudo touch /etc/vmware/ssl/rui.crt

```

If you want to install on a Hardy server without X you will still need to install a few X libraries in order for the install to work:
```

sudo apt-get install libx11-6 linxtst6 libxt6 libxrender1

```

Also note that I had a number of issues on one upgraded machine where I was using the partner repositories debs prior to the upgrade.  I would recommend backing up your VMs and then removing the VMWare install completely prior to upgrading.

EDIT 28 Apr 2008: Removed the rewriting of the libgtk2.0-0.loaders file since the incorrect lines were corrected around Hardy final.

EDIT: 30 May 2008: Update instructions to VMWare Server 1.0.6.  10.06 does not require the any-any patch so I highly recommend it.

---

### Post by Child of Wonder on 2008-04-27
Thanks for the great guide.

Question - what about running the VMWare Server Console?  I'd like to be able to manage my VMs from my main Ubuntu machine and I've followed the directions to resolve the errors during the Console install.  Now I run "vmware-server-console" and nothing happens.

Any suggestions?

---

### Post by useResa on 2008-04-28
> **Child of Wonder said:**
> Question - what about running the VMWare Server Console?  I'd like to be able to manage my VMs from my main Ubuntu machine and I've followed the directions to resolve the errors during the Console install.  Now I run &quot;vmware-server-console&quot; and nothing happens.

Any suggestions?To start the VMware Server Console from terminal, the command is```
vmware
```

BTW: Also thanks from my side, the guide worked like a charm and I have VMware Server running again ;)

---

### Post by barmaley on 2008-04-28
thank you, Kokopelli
explanation is clear, and the vmware-server works
great job

---

### Post by DanFlo on 2008-04-28
Thanks for the guide it works like a charm !

---

### Post by Child of Wonder on 2008-04-28
> **useResa said:**
> To start the VMware Server Console from terminal, the command is```
vmware
```

That command doesn't exist and a "find" doesn't locate any file with that name on the system.  The only command I have is "vmware-server-console."  I installed the 1.0.5 Console.

---

### Post by muecker on 2008-04-28
I was able to get mine working by following these instructions, but I wanted to make one addition.  If you had vmware server installed under Gutsy, you may get an error during installation that vmware is already installed.  All I had to do was rename the directory /etc/vmware to /etc/vmware-gutsy and the installer ran without a problem.

---

### Post by fjgaude on 2008-04-28
> **muecker said:**
> I was able to get mine working by following these instructions, but I wanted to make one addition.  If you had vmware server installed under Gutsy, you may get an error during installation that vmware is already installed.  All I had to do was rename the directory /etc/vmware to /etc/vmware-gutsy and the installer ran without a problem.

Good idea... many have had issues with trying to re-install vmware and couldn't... all you do is what you suggest. It's easier than trying to uninstall. After, you can simply delete the old name-changed directory if you wish, eh? Thanks!

---

### Post by Kokopelli on 2008-04-28
I think the step for 64 bit systems where we adjust the loader is no longer needed.  It seems the loader was adjusted sometime around the final release of Hardy.  Can a 64 bit user run the following command to confirm?

```

cat /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders |grep lib32
```

if you get hits then the final step for 64 bit machines is no longer needed.

---

### Post by fjgaude on 2008-04-28
Lots of hits... the final step is no longer needed.

```
frank@sunshine:~$ cat /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders |grep lib32
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-ani.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-pcx.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-pnm.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-ras.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-tga.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-tiff.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-wbmp.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xbm.so"
"/usr/lib32/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so"

```

Thanks for all your efforts to clear things up and help us running.

---

### Post by arloth on 2008-04-28
Excellent guide! Worked great.  I too had to move my /etc/vmware to /etc/vmware-gutsy and link in the libraries before it worked properly.  However, back in business.

Will recompile be necessary if the kernel ever updates with this setup?

Thanks much. :)

---

### Post by cygtoad on 2008-04-28
Fantastic guide!

I would have had to go back to Gutsy without it!

Thanks!

---

### Post by oregonbob on 2008-04-28
I think I'd never have my virtual servers running if not for this HOW-TO. Thanks very much, all steps worked, including the lib copy cheating step was needed to get vmware console working:
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

Thanks again!

---

### Post by Michaelg14 on 2008-04-28
I followed the instructions and everything seemed to work without error but when I use the vmware command I get:

greybeard@greybeard-desktop:~$ vmware
Try 'man vmware' for more information.


What do I do from here?

Thanks

---

### Post by Michaelg14 on 2008-04-28
man vmware was not very helpful.  I also tried vmware-server-console and got a lot of errors dealing with libgcc stuff.  As far as I can tell everything it asks for is installed.

---

### Post by fjgaude on 2008-04-28
> **Michaelg14 said:**
> I followed the instructions and everything seemed to work without error but when I use the vmware command I get:

greybeard@greybeard-desktop:~$ vmware
Try 'man vmware' for more information.

What do I do from here?

Thanks

Do you have a vmware icon in Applications/System Tools called VMware Server Console?

---

### Post by Michaelg14 on 2008-04-28
No, I don't  :(

---

### Post by fjgaude on 2008-04-28
I would say you haven't correctly installed, with all the items necessary, vmware server.

If you are inclined, you could start over, by simply renaming the foler where vmware is configured: /etc/vmware to somethink like vmwarebak. Re-install and carefully follow the how-to get everything right. You can delete the bak folder after you have successfully got vmware up and running.

---

### Post by Michaelg14 on 2008-04-28
I'll give it a try,  I followed the entire thread and cut and pasted everything but... who knows?

---

### Post by dbqp on 2008-04-28
:popcorn::popcorn::popcorn:

Thank you!

:guitar:

---

### Post by fjgaude on 2008-04-28
> **arloth said:**
> Excellent guide! Worked great.  I too had to move my /etc/vmware to /etc/vmware-gutsy and link in the libraries before it worked properly.  However, back in business.

Will recompile be necessary if the kernel ever updates with this setup?

Thanks much. :)

You just have to run the vmware.config.pl file when the kernel gets updated. At least that's way it has been since Feisty and Gutsy.

---

### Post by Michaelg14 on 2008-04-28
OK I am flummoxed, it works now.  I still don't have an icon in Applications/System Tools but it does work from a terminal.

Many thanks

---

### Post by eighto2 on 2008-04-28
Hey Kokopelli
I have no idea what you did different in this guide, or what i did different, but on a fresh install... worked PERFECT, THANKS SO MUCH!!!!!!:)

---

### Post by bmwman on 2008-04-28
I followed the guide and cut/paste the commands. The server installed fine and then i ran the patch and got some error. Tried to remove and do a fresh install but got the same thing. Here it is:

...........................................................................
Do you want networking for your virtual machines? (yes/no/help) [yes] 

Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0
. vmnet2 is bridged to eth1

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

The NAT network is currently configured to use the private subnet 
192.168.197.0/255.255.255.0.  Do you want to keep these settings? [yes] 

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.197.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

The host-only network is currently configured to use the private subnet 
192.168.216.0/255.255.255.0.  Do you want to keep these settings? [yes] 

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.216.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmnet-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config3/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config3/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config3/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config3/vmnet-only/bridge.o
/tmp/vmware-config3/vmnet-only/bridge.c:35:8: error: "defined" cannot be used as a macro name
make[2]: *** [/tmp/vmware-config3/vmnet-only/bridge.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
...........................................................................

After that I don't have any icons in the Applications/System menu and if I try to launch manually I get this :
..........................................................................
root@bmw-man-laptop:~/Desktop/vmware-any-any-update116# vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
...........................................................................

Do y'all know what's causing it to crash? Thanks in advance.

---

### Post by cwtech on 2008-04-28
Everything installed fine but am getting:

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


Any help would be greatly appreciated.

---

### Post by Michaelg14 on 2008-04-29
I am now getting the same message.  I had it working with a windows xp-64 as the guest.  After I shut down and logged off and back on Hardy, I started getting this message.  Even after running vmware-config successfully I get the same message.

And, I now have an icon for vmware in Applications/Other when I click of it nothing happens.  The hourglass? spins for a few moments then goes away.

very frustrating.

---

### Post by Rohaq on 2008-04-29
Hm, getting this error when running vmware, running on Ubuntu 8.04 64-bit:

```
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ff6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6ff68b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e751bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d65969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d65f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bab180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7babd2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b8824f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b87b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8e77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ca1459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c893a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c89076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ca06eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c9fd46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7ca00b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ff6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6ff681e]
#2 /usr/lib32/libX11.so.6 [0xf7e74518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e57c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d5ded7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d5c8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d5cd39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d5cec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba99b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7babd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b8824f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b87b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8e77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ca1459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c893a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c89076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

Tried the 'cheats' in the main post, but can't see how to fix it. Suggestions anyone?

---

### Post by eighto2 on 2008-04-29
> **Rohaq said:**
> Hm, getting this error when running vmware, running on Ubuntu 8.04 64-bit:

```
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ff6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6ff68b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e751bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d65969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d65f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bab180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7babd2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b8824f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b87b34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8e77e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ca1459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c893a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c89076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ca06eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c9fd46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7ca00b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ff6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6ff681e]
#2 /usr/lib32/libX11.so.6 [0xf7e74518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e57c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d5ded7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d5c8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d5cd39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d5cec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba99b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7babd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b8824f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b7bc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b87b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8c586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8e77e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ca1459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c893a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c89076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

Tried the 'cheats' in the main post, but can't see how to fix it. Suggestions anyone?

Are you using the default theme?
Try changing to a different theme and see what happens

---

### Post by Rohaq on 2008-04-29
> **eighto2 said:**
> Are you using the default theme?
Try changing to a different theme and see what happens

The default Ubuntu theme? Tried changing it and no luck.

Some kind of VMware theme? Where would I find that? I don't recall anything even remotely similar to that.

---

### Post by eighto2 on 2008-04-29
> **Rohaq said:**
> The default Ubuntu theme? Tried changing it and no luck.

Some kind of VMware theme? Where would I find that? I don't recall anything even remotely similar to that.

Yeah I meant the ubuntu theme :confused:
You on an upgrade or fresh install?

---

### Post by Rohaq on 2008-04-29
> **eighto2 said:**
> Yeah I meant the ubuntu theme :confused:
You on an upgrade or fresh install?
Fresh install.

---

### Post by beyboo on 2008-04-29
smoooooth !! :)

---

### Post by eighto2 on 2008-04-29
> **Rohaq said:**
> Fresh install.

Well after

```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install xinetd
```


and then the 

```
sudo apt-get install ia32-libs
```

I rebooted before i tried to install vmware, i hate to ask, but did you try rebooting?

---

### Post by Rohaq on 2008-04-29
Yep, tried rebooting prior to installing vmware too. Same issue :(

---

### Post by Radioman991 on 2008-04-30
Thank you to the OP.  Got it working.....except....where is my XP virtual machine?  Cannot seem to find it.  It has my music scheduler, and traffic system for my test machines for work.  Not mission critical...but a pain to get re-licensed if I have to re-install XP.

---

### Post by stell86 on 2008-05-01
Rohaq wrote regarding this error:
> .../usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@'.....

I received same - re-installed vmware-server twice according to OP.

Both times same error.

Working on system upgraded from 7.10

then ran vmware in terminal, so:
```
sudo vmware
```

And the console started :)
and I was able to see my v-m(s)

Then exit
Then tried to run it in terminal as normal
```
vmware
```
and got this:
> Unable to alloc client: Cannot open file "/home/retief/.vmware/preferences": Permission denied.

VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/retief/.vmware/preferences": Permission denied.

A log file is available in "/tmp/vmware-retief/ui-8645.log".  Please request support and include the contents of the log file.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.

then did this:
```
cd ~/.vmware/
sudo chown user:user preferences

```
(replace user with login)

and still got same error as at top of this post :confused:

will report back if I find something
(I really, really, really don't want to do a clean install...)

---

### Post by useResa on 2008-05-01
> **Radioman991 said:**
> Thank you to the OP.  Got it working.....except....where is my XP virtual machine?  Cannot seem to find it.  It has my music scheduler, and traffic system for my test machines for work.  Not mission critical...but a pain to get re-licensed if I have to re-install XP.By default VMware Server checks the /var/lib/vmware/Virtual Machines directory for existing VMs. If your original VM was not installed in this directory it will not show. However, you can choose to open a VM and simply go to it.
IIRC it will then remain in your VM list.

Hope this helps

---

### Post by torchfire on 2008-05-01
Thank you SO much for this great information.  I not only succeeded in installing VMWare Server, I didn't even have to lose my existing VM's, thanks to the last post!!

Torch

---

### Post by Misenensis on 2008-05-02
Just had alot of problems installing vmware on hardy. (ubuntu server 64). This helped alot :). Also, i found out i had to install the gtk libary:

sudo aptitude install libgtk2.0-0

Ofcourse, is not installed in a server distro. Though i was suprised vmware needed these graphic things.

---

### Post by Kokopelli on 2008-05-02
> **Rohaq said:**
> Hm, getting this error when running vmware, running on Ubuntu 8.04 64-bit:

```
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

...

/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6ff6767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6ff68b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e751bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d65969]

...

#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c89076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

Tried the 'cheats' in the main post, but can't see how to fix it. Suggestions anyone?

The l3232 suggests you ran the sed command which is not valid for the final release of Hardy.

You need to change all instances of "l3232" to "l32" (or lib32) in /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders to fix the problem

```
sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
```

I would be inclined to use lib32 vs l32 since it is more proper but I do not have a machine to test on to confirm (whereas I have tested l32).

---

### Post by ghowells on 2008-05-02
Great little guide,  I'm having trouble getting the vmon module to compile when running the "vmware-config.pl" script.  I get the following error:

```

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:48:
/tmp/vmware-config4/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for âuintptr_tâ
include/linux/types.h:40: error: previous declaration of âuintptr_tâ was here
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:49:
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:49:
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:60: error: conflicting types for âpoll_initwaitâ
include/linux/poll.h:65: error: previous declaration of âpoll_initwaitâ was here
/tmp/vmware-config4/vmmon-only/linux/driver.c:147: warning: initialisation from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c:151: warning: initialisation from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c: In function âLinuxDriver_Ioctlâ:
/tmp/vmware-config4/vmmon-only/linux/driver.c:1659: error: âstruct mm_structâ has no member named âdumpableâ
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I'm running a fairly virgin install of hardy.  All I've done since install is create a sofware RAID array with mdadm. Any help would be greatly appreciated :)

---

### Post by Kokopelli on 2008-05-02
> **ghowells said:**
> Great little guide,  I'm having trouble getting the vmon module to compile when running the "vmware-config.pl" script.  I get the following error:


Did you install the vmware-any-any-116 patch?

---

### Post by ghowells on 2008-05-02
> Did you install the vmware-any-any-116 patch?
Nope, have now and it works!

Thanks very much, feel a bit stupid but figured that was a post config thing #-o

Thanks again :)

---

### Post by Lord_Phoenix on 2008-05-02
I got the vmware server running under hardy with this tutorial, so thanks, great work.

Have a problem though, when trying to access an existing VM or create a new one, I am geting this, under vmware log file:

HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
HostDeviceInfoFindHostIDECDROMs: /proc/ide could not be explored. Unable to enumerate host IDE cdroms.

Any idea on how to get through this one ?

Thanks and keep it up.

---

### Post by Kokopelli on 2008-05-02
> **Lord_Phoenix said:**
> I got the vmware server running under hardy with this tutorial, so thanks, great work.

Have a problem though, when trying to access an existing VM or create a new one, I am geting this, under vmware log file:

HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
HostDeviceInfoFindHostIDECDROMs: /proc/ide could not be explored. Unable to enumerate host IDE cdroms.

Any idea on how to get through this one ?

Thanks and keep it up.

I did some googling and did not come up with anything conclusive.  Try rebooting and/or running ldconfig.  If that does not fix it then the next most probable guess would be apparmor or SELinux, but I am not convinced that is the problem.

---

### Post by aroddo on 2008-05-02
I followed the OP method right up to after the any-to-any-patch installation.
The first install script fails like described while the any-to-any skript works fine.

After installing that I tried to start vmware. I got this error:
> 
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
after that, i followed the OP guide and linked the libraries:

```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```afterwards, when trying to run it I get this:
```

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
root@bueno-desktop:/home/bueno/vminst/vmware-any-any-update116# sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
root@bueno-desktop:/home/bueno/vminst/vmware-any-any-update116# sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
root@bueno-desktop:/home/bueno/vminst/vmware-any-any-update116# vmware
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/console.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/upgrade-hw.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/pvn.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-not.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-new.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-add.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-remove.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-broken.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-new.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-suspended.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-broken.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-broken.png« konnte nicht erkannt werden
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6feb767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6feb8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e6a1bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d5a969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d5af4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba0180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba0d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b7d24f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b7cb34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8377e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c96459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c7e3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c7e076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c956eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c94d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7c950b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6feb767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6feb81e]
#2 /usr/lib32/libX11.so.6 [0xf7e69518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e4cc9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d52ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d518b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d51d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d51ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b9e9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba0d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b7d24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b7cb34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8377e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c96459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c7e3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c7e076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```gcc versions:
> 
# apt-show-versions  |grep gcc
gcc-4.2/hardy uptodate 4.2.3-2ubuntu7
lib32gcc1/hardy uptodate 1:4.2.3-2ubuntu7
libgcc1/hardy uptodate 1:4.2.3-2ubuntu7
gcc-4.2-base/hardy uptodate 4.2.3-2ubuntu7
gcc/hardy uptodate 4:4.2.3-1ubuntu3


by the way, this isn't the first install of vmware on this installation. It even worked once, but I uninstalled it and want to reinstall.

what now ?

---

### Post by Rohaq on 2008-05-02
> **Kokopelli said:**
> The l3232 suggests you ran the sed command which is not valid for the final release of Hardy.

You need to change all instances of "l3232" to "l32" (or lib32) in /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders to fix the problem

```
sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
```

I would be inclined to use lib32 vs l32 since it is more proper but I do not have a machine to test on to confirm (whereas I have tested l32).
Aaaaaaah! Thank you! I feel so daft for not spotting that.

---

### Post by Radioman991 on 2008-05-03
> **useResa said:**
> By default VMware Server checks the /var/lib/vmware/Virtual Machines directory for existing VMs. If your original VM was not installed in this directory it will not show. However, you can choose to open a VM and simply go to it.
IIRC it will then remain in your VM list.

Hope this helps


Perfect!  Thanks!

---

### Post by fjgaude on 2008-05-03
Bodhi.zazen placed a Sticky at the top of this Forum easing the install process of vmware server into 8.04.

Next has to be added: how-to use USBs and access files, host to guest and guest to host, eh?

---

### Post by aroddo on 2008-05-06
bump.

followed the guide - still doesn't work.

got the 64bit version of 8.04

>  vmware
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6f9c767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6f9c8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e1b1bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d0b969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d0bf4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b51180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b51d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b2e24f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b2db34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a3477e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c47459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c2f3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c2f076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c466eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c45d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7c460b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6f9c767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6f9c81e]
#2 /usr/lib32/libX11.so.6 [0xf7e1a518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7dfdc9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d03ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d028b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d02d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d02ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b4f9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b51d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b2e24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b21c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b2db34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a32586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a3477e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c47459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c2f3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c2f076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.


---

### Post by aroddo on 2008-05-06
damn ... why do I find solutions always minutes after i post the problem ....

sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
doing this eliminates the l3232 problem.

---

### Post by segid on 2008-05-07
> **aroddo said:**
> I followed the OP method right up to after the any-to-any-patch installation.
The first install script fails like described while the any-to-any skript works fine.

After installing that I tried to start vmware. I got this error:
after that, i followed the OP guide and linked the libraries:

```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```afterwards, when trying to run it I get this:
```

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib32/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
root@bueno-desktop:/home/bueno/vminst/vmware-any-any-update116# sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
root@bueno-desktop:/home/bueno/vminst/vmware-any-any-update116# sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
root@bueno-desktop:/home/bueno/vminst/vmware-any-any-update116# vmware
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/console.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/upgrade-hw.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/pvn.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vmlist-not.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-new.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-add.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-remove.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-broken.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-new.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/team-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-suspended.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-broken.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-clone-settings.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-off.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-on.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-suspend.png« konnte nicht erkannt werden
Das Format der Bilddatei »/usr/lib/vmware/share/pixmaps/vm-legacy-broken.png« konnte nicht erkannt werden
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6feb767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6feb8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e6a1bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d5a969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d5af4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba0180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba0d2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b7d24f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b7cb34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8377e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c96459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c7e3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c7e076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c956eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c94d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7c950b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6feb767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6feb81e]
#2 /usr/lib32/libX11.so.6 [0xf7e69518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e4cc9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d52ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d518b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7d51d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d51ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b9e9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba0d75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b7d24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b70c14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b7cb34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a81586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a8377e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c96459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c7e3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c7e076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```gcc versions:


by the way, this isn't the first install of vmware on this installation. It even worked once, but I uninstalled it and want to reinstall.

what now ?


Hi,
I had the same problem as you are when I installed WMWare Server in Hardy. I've got the same message with libgcc, however to resolve this I've only used the first 'ln -sf':
```

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

```
The second with 'png' is not needed. Now WMWare runs fine.
I hope this helps.

---

### Post by Duffy on 2008-05-07
Here is what is happening when I try to install:

A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

Can anyone steer me to a solution?

Thanks.

---

### Post by techno-wiz on 2008-05-07
I get the same thing due to a previous vmware installation.

---

### Post by pba on 2008-05-08
> **Duffy said:**
> Here is what is happening when I try to install:

A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

Can anyone steer me to a solution?

Thanks.

If you updated from gutsy to hardy, then there may be some left over from the vmware-server-xxxx.deb installation. Try to start Synaptic package manager and mark anything "vmware" with "Mark for complete removal". At least that worked for me.

---

### Post by maomao on 2008-05-12
I met the same problem and I got hint from your post and now it runs for me under hardy (Kernel 2.6.22 instead of 2.4.24 which I haven't heard from anyone that VMWare works for the new kernel).

I think you have gone just one step too far.  So do not use the vmware-any-any-update115 patch.  Here are my steps:

1. Make sure to reboot Ubuntu into 8.04 Kernel 2.6.22
2. Download (or probably just unzip) a fresh version of the VMware-server-1.0.5-80187
3. Because kernel 2.6.22 was built on gcc-4.1 instead of gcc-4.2, so you have to do this:
$ ln -sf /usr/bin/gcc-4.1 /usr/bin/gcc
4. Run vmware-install.pl to configure and build VMWare.
5. I was more conservative than you.  So I made a backup copy of the original /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 by
$ sudo mv libgcc_s.so.1 libgcc_s.so.1.bak
and then
/usr/lib/vmware/lib/libgcc_s.so.1$ sudo cp /lib/libgcc_s.so.1 .
6. Now Enjoy!
$ sudo vmware

---

### Post by Guevara the Pirate on 2008-05-19
Hi there,

I'm fairly new to Ubuntu and I have been trying to install VMWare Server on an AMD-64 bit computer/kernel in order to run WinXP. I've pretty much followed the guide to the letter as well as searched the forum, but I continually get the following error: 

```
 /usr/bin/ldd: line 117:  7587 Segmentation fault      LD_TRACE_LOADED_OBJECTS=1 LD_WARN= LD_BIND_NOW= LD_LIBRARY_VERSION=$verify_out LD_VERBOSE= "$@"
Segmentation fault
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6f8b767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf6f8b8b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e091bd]
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7cf9969]
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7cf9f4c]
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b3f180]
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b3fd2c]
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b0fc14]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b1c24f]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b0fc14]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b1bb34]
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a20298]
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a20586]
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a2277e]
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c36459]
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c1e3a1]
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c1e076]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c356eb]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7c34d46]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7c350b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf6f8b767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf6f8b81e]
#2 /usr/lib32/libX11.so.6 [0xf7e08518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7debc9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7cf1ed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7cf08b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7cf0d39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7cf0ec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b3d9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b3fd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b0fc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7b1c24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b0fc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7b1bb34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a20298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a20586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7a2277e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7c36459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7c1e3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c1e076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

I'm kinda baffled by the first output, and I suspected that a lot of the problem was coming from there, However I have not been able to find any information as to its cause on google or on the forums. Any help will be appreciated.

---

### Post by useResa on 2008-05-19
> **maomao said:**
> Kernel 2.6.22 instead of 2.4.24 which I haven't heard from anyone that VMWare works for the new kernel.I am assuming that you mean 2.6.24 kernel since you are referring to the new kernel.

I have VMware Server running in Hardy with the 2.6.24 kernel.
Find attached a screenshot with the terminal indicating the result of
```
uname -r
```
and a running VMware Server.

So now you have heard from someone that it works ;)

---

### Post by Rondrigo on 2008-05-20
> **useResa said:**
> I am assuming that you mean 2.6.24 kernel since you are referring to the new kernel.

I have VMware Server running in Hardy with the 2.6.24 kernel.
Find attached a screenshot with the terminal indicating the result of
```
uname -r
```
and a running VMware Server.

So now you have heard from someone that it works ;)

Is it running on 64Bit or 32Bit architecture?

---

### Post by useResa on 2008-05-21
> **Rondrigo said:**
> Is it running on 64Bit or 32Bit architecture?
32-bit architecture

---

### Post by Rondrigo on 2008-05-21
> **useResa said:**
> 32-bit architecture

Okay, that's what I thought. On 32-Bit it works, but currently not on 64-Bit machines.

---

### Post by Skeet on 2008-05-21
A silly, unrelated to installation question, but;

How do you exit full screen mode? Its not quite full screen, not sure what I clicked, but its got tabs at the top for me to select my Virtual Machines. :confused:

---

### Post by jure1873 on 2008-05-21
I've installed the new beta of vmware, but i can login only as root. Anyone knows how to change that?

---

### Post by Skeet on 2008-05-21
How do you mean, you can only login as root? Do you mean you can only run the program as root?

---

### Post by useResa on 2008-05-22
> **Skeet said:**
> A silly, unrelated to installation question, but;
 
How do you exit full screen mode? Its not quite full screen, not sure what I clicked, but its got tabs at the top for me to select my Virtual Machines. :confused:
What you have clicked is called "Quick Switch"
Pressing <F11> will take you out of this mode.
 
Another option is to move your mouse pointer all the way to the top of the screen. The regular menu will appear and you can choose another view from the menu.

---

### Post by jure1873 on 2008-05-22
> **Skeet said:**
> How do you mean, you can only login as root? Do you mean you can only run the program as root?


The initial web login page ([http://localhost:8222](http://localhost:8222)) accepts only the root login

If I login with my username & pass it says access denied. But in /var/log/messages I see that the password was accepted by the system, so it seems it's something in vmware blocking it. 

I added myself to the administrators "role" once I was in vmware, but it's still the same. 

Maybe there is a command to open the vm directly without going to the web interface, but I don't know what it is.

---

### Post by MaddMatt on 2008-05-30
I'm having this same problem: 

was getting the "you need to re-run vmware_config.pl" error, so deleted the error file and am now getting:

> 
matter@Sparta:~$ vmware
Cannot get temporary directory for log file.

VMware Server Error:
VMware Server unrecoverable error: (vmui)
Cannot get temporary directory for log file.
Please request support.  
To collect files to submit to VMware support, run vm-support.


Nothing seems to be working - tried the CHMOD that stell86 used, but no dice. Any ideas?

---

### Post by Kokopelli on 2008-05-30
> **Rondrigo said:**
> Okay, that's what I thought. On 32-Bit it works, but currently not on 64-Bit machines.

For host I have VMWare server (1.0.5 and the new 1.0.6) running on both 32 and 64 bit versions of Hardy with the 2.6.24-17 kernel.


On upgrading 1.0.5 to 1.0.6 the any-any patch is not needed either for that matter.  I did have to relink libpng and libgcc though.

---

### Post by useResa on 2008-05-31
> **Kokopelli said:**
> For host I have VMWare server (1.0.5 and the new 1.0.6) running on both 32 and 64 bit versions of Hardy with the 2.6.24-17 kernel.I can confirm the working on 32 bit version of Hardy

> **Kokopelli said:**
> On upgrading 1.0.5 to 1.0.6 the any-any patch is not needed either for that matter.  I have the same experience, but I am not sure if this is because of the fact that the any-any patch was already applied to 1.05.
I can not confirm if the any-any patch is needed if 1.0.6 is directly installed

> **Kokopelli said:**
> I did have to relink libpng and libgcc though.Same here.

---

### Post by Robor on 2008-06-15
Thanks Kokopelli for the following:

> sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

That fixed these errors:

> robor007@Home-Ubuntu:~/src/VMWare/vmware-server-distrib$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

---

### Post by jonathanhayward on 2008-06-17
I ran into the same error myself, and followed:

[http://www.robert-franz.com/cms/content/view/22/12/lang,en/](http://www.robert-franz.com/cms/content/view/22/12/lang,en/)

Specifically, I ran:

```
cd /usr/lib/vmware/lib/libgcc_s.so.1
sudo mv libgcc_s.so.1 libgcc_s.so.1.old
sudo ln -sf /lib/libgcc_s.so.1 libgcc_s.so.1
```

and vmware started up the next time I ran it.

---

### Post by iplayfast on 2008-06-23
> **Rondrigo said:**
> Okay, that's what I thought. On 32-Bit it works, but currently not on 64-Bit machines.

Just so you know, I had it working last week, (HH), and then did an Ubuntu upgrade to kernel 2.6.24-1-generic and started running into the same thing you are seeing.

So I don't know why ldd would segfault but I thought I'd send vmware over to my gentoo box to see what it said.
> chris@belford ~ $ ldd vmware
	linux-gate.so.1 =>  (0xffffe000)
	libdl.so.2 => /lib/libdl.so.2 (0xb7fda000)
	libm.so.6 => /lib/libm.so.6 (0xb7fb6000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x48568000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x48653000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x48841000)
	libexpat.so.0 => /usr/lib/libexpat.so.0 (0x4e5f6000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x48814000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x48664000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x48809000)
	libXft.so.2 => /usr/lib/libXft.so.2 (0x4899d000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x4886f000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x4897d000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x48940000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x48b33000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7f78000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb7f50000)
	libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0xb7f48000)
	libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0xb7f3b000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x48a70000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x489b9000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x48b50000)
	libgcc_s.so.1 => /usr/lib/gcc/i686-pc-linux-gnu/4.2.4/libgcc_s.so.1 (0x4e7d1000)
	libstdc++.so.5 => /usr/lib/gcc-lib/i686-pc-linux-gnu/3.3.6/libstdc++.so.5 (0xb7e80000)
	libsigc-2.0.so.0 => /usr/lib/libsigc-2.0.so.0 (0x4df11000)
	libglibmm-2.4.so.1 => /usr/lib/libglibmm-2.4.so.1 (0x48ebb000)
	libglibmm_generate_extra_defs-2.4.so.1 => /usr/lib/libglibmm_generate_extra_defs-2.4.so.1 (0xb7e79000)
	libatkmm-1.6.so.1 => /usr/lib/libatkmm-1.6.so.1 (0x4901d000)
	libpangomm-1.4.so.1 => /usr/lib/libpangomm-1.4.so.1 (0x48fa4000)
	libgdkmm-2.4.so.1 => /usr/lib/libgdkmm-2.4.so.1 (0x48fd2000)
	libgtkmm-2.4.so.1 => /usr/lib/libgtkmm-2.4.so.1 (0x49849000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0x48984000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0x486e6000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb7e5f000)
	libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb7e2e000)
	libgnomecanvasmm-2.6.so.1 => /usr/lib/libgnomecanvasmm-2.6.so.1 (0x4b6e2000)
	librsvg-2.so.2 => /usr/lib/librsvg-2.so.2 (0xb7dfc000)
	libview.so.2 => not found
	libsexy.so.1 => not found
	libsexymm.so.1 => not found
	libpthread.so.0 => /lib/libpthread.so.0 (0xb7de3000)
	libz.so.1 => /lib/libz.so.1 (0x4e66c000)
	libc.so.6 => /lib/libc.so.6 (0xb7cac000)
	/lib/ld-linux.so.2 (0xb8019000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7ca9000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7c8f000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x4e686000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7c85000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7c1f000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x4eaa1000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0xb7c19000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0xb7c11000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x4eb31000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x48861000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x4884c000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x48855000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x491b3000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x49221000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x48867000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x4e68c000)
	libstdc++.so.6 => /usr/lib/gcc/i686-pc-linux-gnu/4.2.4/libstdc++.so.6 (0x4e9b2000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x490e3000)
	libcairomm-1.0.so.1 => /usr/lib/libcairomm-1.0.so.1 (0x48a53000)
	libgailutil.so.18 => /usr/lib/libgailutil.so.18 (0x491a5000)
	libgsf-1.so.114 => /usr/lib/libgsf-1.so.114 (0xb7bdc000)
	libcroco-0.6.so.3 => /usr/lib/libcroco-0.6.so.3 (0x49227000)


Hope it helps.

---

### Post by Tristan_F on 2008-07-30
I had also the locking assertion failure related to libX problem. I solve it by finding and old version of the library and made a workaround to trick VMWare to use this library. I explaind it more [here]("http://tristan.ferroir.free.fr/index.php/2008/07/30/vmware-in-ubuntu-804-and-the-locking-assertion-failure-problem/").

Briefly you have to find an old version of the library and put it into a directory called libX11.so.6 in your VMWare installation and it works afterwards

---

### Post by tinyviking on 2008-09-15
> **Kokopelli said:**
> The l3232 suggests you ran the sed command which is not valid for the final release of Hardy.

You need to change all instances of "l3232" to "l32" (or lib32) in /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders to fix the problem

```
sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
```

I would be inclined to use lib32 vs l32 since it is more proper but I do not have a machine to test on to confirm (whereas I have tested l32).

THANK YOU!  I've had so many issues with VMWare on 8.04.1 it's just not true! Haven't managed to keep it stable long enough to create a VM!  finally have the console running, thanks to all who've contributed to this thread!

---

