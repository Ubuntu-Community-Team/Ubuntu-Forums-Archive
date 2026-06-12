---
title: "vmware-server in Hardy"
date: 2008-04-24
forum: Virtualisation
---

### Post by insert_name_here on 2008-04-24
Just updated to Hardy, and vmware-server was removed by the "removing obsolete software" dealie.

I'm trying to reinstall via: [http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976), but I'm getting this when I try to install from the downloaded vmware package:```
$ sudo ./vmware-install.pl 
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

```

I have no packages with "vmware" in their names still installed, so I don't know what's going on.  Help?

---

### Post by andi1984 on 2008-04-26
Same problem here. Very annoyed by the fact that Hardy removed vmware-server. By the looks of it, has also deleted the XP image file. Doh! Any suggestions

---

### Post by gtdaqua on 2008-04-26
> **andi1984 said:**
> Same problem here. Very annoyed by the fact that Hardy removed vmware-server. By the looks of it, has also deleted the XP image file. Doh! Any suggestions

Can you confirm this? Image file has been deleted because of an upgrade?? This is a serious issue. I upgraded a 64 bit Gutsy to Hardy but did not have any problems. Had to apply the 'any-any' VMWare patch for the VMWare Server to run. But image files were intact.

---

### Post by eighto2 on 2008-04-26
Even after applying the any-any patch, i still cant get vmware-server to run, I'm afraid I'll have to go back to gutsy

---

### Post by Sand Lee on 2008-04-26
Try these instructions, they worked for me!
[http://ubuntuforums.org/showthread.php?t=613976#10](http://ubuntuforums.org/showthread.php?t=613976#10)

---

### Post by insert_name_here on 2008-04-26
At first, after I followed those instructions, VMware server didn't work for me either, saying that it wasn't configured correctly, and to run a shell script again.  I did that, and it behaved the same way.  Eventuaully, I found that if you delete /etc/vmware/not_configured, VMware will work.

---

### Post by eighto2 on 2008-04-26
> **Sand Lee said:**
> Try these instructions, they worked for me!
[http://ubuntuforums.org/showthread.php?t=613976#10](http://ubuntuforums.org/showthread.php?t=613976#10)

No luck following these instructions, i even dug through all 7 pages on this topic...

---

### Post by fjgaude on 2008-04-26
> **eighto2 said:**
> No luck following these instructions, i even dug through all 7 pages on this topic...

Here they are in compressed form... make sure you have done everything here:

VMware Server
The Player isn't for 64-bit. Here's what I suggest:

1. Get latest version, 1.0.5, of vmware server from vmware.com website. Log-in and get at the same time your free license number.

2. Install linux headers matching your kernel version, xinetd, and build-essential using apt-get or Synaptic, if they are not already on your system.

3. Unpack the software

4. Then run

```
sudo ./vmware-install.pl
```

5. follow the guide using mostly the defaults, then

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:

```
    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Good to add this line into your guest .vmx file using text editor:

```
mainMem.useNamedFile=FALSE
```

You will have full copy, paste from host to and from guest, and USB device handling capability, drives, scanners, printers, etc.

Let us know how you are doing.

```
sudo ./vmware-server-distrib/bin/vmware-uninstall.pl
sudo /usr/bin vmware-config.pl
```

/var/lib/vmware/Virtual Machines # where the .vmx file is

---
**For Hardy**

Taken from this thread:

[http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976) post #47

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

and additionally for 64 bit systems:

```
sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
```

---

### Post by eighto2 on 2008-04-26
Thanks for the reply, still no luck tho :confused:

It install fine, it runs fine, i guess its just the actual console thats giving me the problems, 

If i type: sudo /etc/init.d/vmware start i get:

```
 sudo /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done

```
But when i try to load up the console, it just sort of spins for a couple seconds and thats it

---

### Post by Kokopelli on 2008-04-27
> **eighto2 said:**
> 
But when i try to load up the console, it just sort of spins for a couple seconds and thats it

Can you try and start the console from the command line and see if any error shows up there?

---

### Post by amorangi on 2008-04-27
I can't get the console working either, on 64bit Hardy (after much prodding and poking I have it working on 32bit though). I've tried the usual suggestions, but now I'm getting:

```
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

```
repeated on for a while, followed by:
```
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:41: error: unexpected character `@', expected string constant
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7016767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf70168b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7e951bd]
#3 /usr/lib/vmware-server-console/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7d85969]
#4 /usr/lib/vmware-server-console/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7d85f4c]
#5 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bcb180]
#6 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bcbd2c]
#7 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b9bc14]
#8 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba824f]
#9 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b9bc14]
#10 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7ba7b34]
#11 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aac298]
#12 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aac586]
#13 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aae77e]
#14 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cc1459]
#15 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ca93a1]
#16 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7ca9076]
#17 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cc06eb]
#18 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7cbfd46]
#19 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7cc00b8]
Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7016767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf701681e]
#2 /usr/lib32/libX11.so.6 [0xf7e94518]
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7e77c9c]
#4 /usr/lib/vmware-server-console/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7d7ded7]
#5 /usr/lib/vmware-server-console/lib/libXft.so.2/libXft.so.2 [0xf7d7c8b1]
#6 /usr/lib/vmware-server-console/lib/libXft.so.2/libXft.so.2 [0xf7d7cd39]
#7 /usr/lib/vmware-server-console/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7d7cec0]
#8 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bc99b6]
#9 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bcbd75]
#10 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b9bc14]
#11 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7ba824f]
#12 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7b9bc14]
#13 /usr/lib/vmware-server-console/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7ba7b34]
#14 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aac298]
#15 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aac586]
#16 /usr/lib/vmware-server-console/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7aae77e]
#17 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7cc1459]
#18 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7ca93a1]
#19 /usr/lib/vmware-server-console/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7ca9076]
vmware-server-console: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

Any suggestions?

---

### Post by Child of Wonder on 2008-04-27
> **eighto2 said:**
> 
But when i try to load up the console, it just sort of spins for a couple seconds and thats it

I have the same problem.  VMWare Server is installed on a different box but after resolving the issues with VMWare Console by following the last 5 steps for my 64 bit system, the command "vmware-server-console" does nothing.  No errors, no windows, nothing.

---

### Post by Kokopelli on 2008-04-28
> **amorangi said:**
> I can't get the console working either, on 64bit Hardy (after much prodding and poking I have it working on 32bit though). I've tried the usual suggestions, but now I'm getting:

```
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

```

Any suggestions?
 "l3232" is incorrect.

It looks like the loader issue that was present in Hardy betas was corrected somewhere down the line and now the "fix" is breaking things.

```

sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders

```

should get it operational again.

---

### Post by andi1984 on 2008-04-28
Sorry people. False alarm! The installation of Hardy Heron did not delete the XP image file. I just found it completely intact. I'm still though having problems installing vmware-server. Synaptic seems to be completely useless for this at the moment. Someone pointed out deleting the various folders (the old) vmware created, will solve the problem although I'm having trouble locating all the folders at the moment. Will post back!

---

### Post by fjgaude on 2008-04-28
> **andi1984 said:**
> Sorry people. False alarm! The installation of Hardy Heron did not delete the XP image file. I just found it completely intact. I'm still though having problems installing vmware-server. Synaptic seems to be completely useless for this at the moment. Someone pointed out deleting the various folders (the old) vmware created, will solve the problem although I'm having trouble locating all the folders at the moment. Will post back!

I've come to believe the easiest way to re-install vmware is to go to /etc/vmware and rename the vmware folder to something else, like vmwarebak. Then do the re-install, which will create a new vmware folder in /etc/vmware. Then if you wish you can delete the old bak folder.

Such seems easier than any other way I've tried.

Let us know how you do.

---

### Post by ahuffman on 2008-05-04
Thank you this has fixed the last piece I couldn't get going on my 64bit OS.  As for getting the rest going, I used this post here, which had everything right except for the pixbuffer piece:

[http://ubuntuforums.org/showthread.php?p=4815962]("http://ubuntuforums.org/showthread.php?p=4815962")


:guitar:

---

### Post by fjgaude on 2008-05-04
We now have a Sticky that could get most folks into installing VMware server easily:

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934) #1

We learn day-by-day.

---

