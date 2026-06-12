---
title: "Latest Kernel Update Borked the Installation Beyond Repair"
date: 2012-01-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by OGpmpdog on 2012-01-28
I even doubt that Harry, Effenburg, or Paul could resurrect my T61 laptop.:)

Everything was working fine until this update (3.2.11).

The update borked my ancient Nvidia Quadro card...at least, that's what I initially thought...

I cant boot into recovery mode either...the system hangs during POST "network configuration" and after timing out, I get broken monitor displays that just hang indefinitely. Serious graphic problems!

This is my 1st bork that KO'd the entire kernels AND recovery.

I'll try again on Alpha 2, just wanted to share this info.

---

### Post by lucazade on 2012-01-28
if the issue is related to video driver try to start in recovery mode passing a dummy param to kernel avoiding the 'nvidia' module to load up:

append to linux kernel entry in grub this (after quiet single):
nvidia.dummy=1

if you can enter in recovery then rebuild nvidia dkms kernel module

sudo dpkg-reconfigure nvidia-current

and reboot

---

### Post by ventrical on 2012-01-28
> **OGpmpdog said:**
> I even doubt that Harry, Effenburg, or Paul could resurrect my T61 laptop.:)

Everything was working fine until this update (3.2.11).

The update borked my ancient Nvidia Quadro card...at least, that's what I initially thought...

I cant boot into recovery mode either...the system hangs during POST "network configuration" and after timing out, I get broken monitor displays that just hang indefinitely. Serious graphic problems!

This is my 1st bork that KO'd the entire kernels AND recovery.

I'll try again on Alpha 2, just wanted to share this info.


Here's what I got .. now I am going to reboot.

Unpacking linux-image-3.2.0-11-generic (from .../linux-image-3.2.0-11-generic_3.2.0-11.19_i386.deb) ...
Done.
E: Sub-process /usr/bin/dpkg received a segmentation fault.
A package failed to install.  Trying to recover:

---

### Post by ventrical on 2012-01-28
Completely destroyed my Dell Opti GX270 install. I got a big HUGE  arrow cursor (like an Amiga 500) and then I got blackspace ... no <Ctrl+Alt+F1> for terminal.

lemme see.. I got  few things to try here.

---

### Post by shakabra on 2012-01-28
Hey guys,

Just revert back to the old kernel. That's why GRUB keeps them there. When you boot just press <SHIFT> like a maniac until the GRUB boot options appear and then select an older kernel.

esac

---

### Post by ventrical on 2012-01-28
I tried recovery but same problem .. go to blackspace .. and there is definetly network activity going on in the background. I don't like it.  Somthings wrong here..
.

---

### Post by ventrical on 2012-01-28
> **shakabra said:**
> Hey guys,

Just revert back to the old kernel. That's why GRUB keeps them there. When you boot just press <SHIFT> like a maniac until the GRUB boot options appear and then select an older kernel.

esac

yep .. for  now thats working .. :)

---

### Post by effenberg0x0 on 2012-01-28
I had no problems with 3.2.0-11 on the i5/HD3000 laptop. The desktops using NVidia booted to the "Ubuntu is running in low graphics mode" and that is usual for me when updating Kernel in the ones that use NVidia proprietary. I just rebuild the kernel module with sudo ~/Downloads/nvidia_drivers/NVidia*<version>*.run -K and reboot. 

I may be wrong but if video is failing so soon, what you are seeing could be Plymouth related. All my machines have their Kernel command line with no "quiet splash" options to avoid Plymouth. 

Also, regarding only NVidia, I'm not using driver 290.10. I am testing with 275.36 for a while. 

Another important characteristic here is that I use no alternative PPAs. Everything is from repos default.

Regards,
Effenberg

---

### Post by Cheltspy on 2012-01-28
Same problem with nvidia-current

For some reason the hard drive is going read only.

The only way to start it is to drop to root

mount -n -o remount,rw /

startx


but, of course only root.

:confused:

---

### Post by jerrylamos on 2012-01-28
Last Sunday's precise.iso blasted boot altogether on my Acer 5253 notebook.  No Grub menu, nothing. Recovered only by Boot-Repair cd.  

I could install but running update-grub and grub-install trashed boot.  Panic, that pc has Windoze 7 which would be a 4 full DVD restore.  That's a relatively new notebook, build about Nov 2010, fastest pc I've got.

That precise .iso installed O.K. on older Thinkpad T40 that won't run Unity-3D will run Unity-2D but sparkles with Lubuntu 12.04.

Tried precise install again on the Acer.    Boot-Repair again.

Tusday's precise.iso installed O.K.  Updates since still working.

?

Anyway, Grub2 wiki and Boot-Repair saved the day.

Jerry

---

### Post by ventrical on 2012-01-28
This Dell is running the :00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)


 I'm just going to hold back a bit on my other machines with nVidia adapters.

  Must be CCSM ... :)

---

### Post by ventrical on 2012-01-28
> **effenberg0x0 said:**
> 

I may be wrong but if video is failing so soon, what you are seeing could be Plymouth related. All my machines have their Kernel command line with no "quiet splash" options to avoid Plymouth. 


Regards,
Effenberg

Nope .. not a chance .. thats not it.

thanks anyways..

---

### Post by ventrical on 2012-01-28
> **jerrylamos said:**
> Last Sunday's precise.iso blasted boot altogether on my Acer 5253 notebook.  No Grub menu, nothing. Recovered only by Boot-Repair cd.  

I could install but running update-grub and grub-install trashed boot.  Panic, that pc has Windoze 7 which would be a 4 full DVD restore.  That's a relatively new notebook, build about Nov 2010, fastest pc I've got.

That precise .iso installed O.K. on older Thinkpad T40 that won't run Unity-3D will run Unity-2D but sparkles with Lubuntu 12.04.

Jerry

  I am getting some of the same results with performance and video rendering. There is definite blacklisting process going on with Ubuntu Unity and certain classes of video adapter cards where Natty Unity 3D would work but not with Precise Unity 3D. Lubuntu takes off at warp factor 8 while Ubuntu seems to just want to hang around the Neutral Zone.

  I guess we can blame it all on compiz :) jk... ehehehe

---

### Post by QIII on 2012-01-28
Couldn't get far on my physical test machine, even by trying to shift in after updating last night.   That box runs AMD HD 5870 graphics.

But I also have Precise in VirtualBox, which I also updated last night.

Both of them froze on shut down after the update.

I was able to Shift in to the virtual machine and drop to recovery mode and continue booting in verbose mode.

It's halting/hanging at "Checking battery state" in the virtual machine (on a desktop).

I'm not going to send anything to launchpad since what I can see is on a virtual machine and is probably useless, but if you can shift in and go to recovery mode it would be interesting to see if that is happening on a physical machine.

---

### Post by jpeddicord on 2012-01-28
Stupid me did the upgrade, then several hours later I was cleaning out old packages and removed the older kernels. Reboot and... nothing. Looks like I get to boot up using a flash drive today! ;)

Hopefully I can find an older kernel in the dpkg cache.

---

### Post by paul_in_london on 2012-01-28
I was having lots of problems after some updates the other night. I could boot into recovery mode and update/upgrade, but that was about it. I spent a long time assuming it was nvidia-related because I'd inadvertently "upgraded" nvidia-current, replacing the xorg-edgers version. I got that back, still no go. Decided to purge xorg-edgers and ricotz-testing. No change. Re-enabled both of those ppas. No change.

I also thought that removing the 295.09 driver using the nvidia-installer:

```
NVIDIA-Linux-x86_64-295.09.run  --uninstall
```

had messed up the symlinks somehow and was preventing me from booting normally with any kernel. This wasn't it though.

Eventually I noticed this:

```
paul@precise-64:~$ grep unity-greeter /var/log/syslog | tail
Jan 27 19:21:34 localhost kernel: [   25.435936] unity-greeter[1287]: segfault at 18 ip 00007fcb7aa73f6c sp 00007fffb858a550 error 4 in libindicator3.so.7.0.0[7fcb7aa6f000+d000]
Jan 27 19:21:36 localhost kernel: [   28.077771] unity-greeter[1442]: segfault at 18 ip 00007fa60e30bf6c sp 00007fff95bc3320 error 4 in libindicator3.so.7.0.0[7fa60e307000+d000]
Jan 27 19:21:39 localhost kernel: [   30.625236] unity-greeter[1487]: segfault at 18 ip 00007ffa4f125f6c sp 00007fffa36930c0 error 4 in libindicator3.so.7.0.0[7ffa4f121000+d000]
Jan 27 19:21:41 localhost kernel: [   33.213575] unity-greeter[1533]: segfault at 18 ip 00007fe511644f6c sp 00007fff7ec24990 error 4 in libindicator3.so.7.0.0[7fe511640000+d000]
Jan 27 19:21:44 localhost kernel: [   35.741111] unity-greeter[1578]: segfault at 18 ip 00007f7ac7379f6c sp 00007fff38eb7620 error 4 in libindicator3.so.7.0.0[7f7ac7375000+d000]
Jan 27 19:21:47 localhost kernel: [   38.334283] unity-greeter[1623]: segfault at 18 ip 00007f9146decf6c sp 00007fff27b4b620 error 4 in libindicator3.so.7.0.0[7f9146de8000+d000]
Jan 27 23:28:08 localhost kernel: [   30.422469] unity-greeter[1268]: segfault at 18 ip 00007fba56d33f6c sp 00007fffc62b51c0 error 4 in libindicator3.so.7.0.0[7fba56d2f000+d000]
Jan 27 23:28:10 localhost kernel: [   33.122828] unity-greeter[1423]: segfault at 18 ip 00007f036840cf6c sp 00007fff12092e30 error 4 in libindicator3.so.7.0.0[7f0368408000+d000]
Jan 27 23:28:13 localhost kernel: [   35.684712] unity-greeter[1468]: segfault at 18 ip 00007fe80e969f6c sp 00007fff17bc2450 error 4 in libindicator3.so.7.0.0[7fe80e965000+d000]
Jan 27 23:28:16 localhost kernel: [   38.250476] unity-greeter[1517]: segfault at 18 ip 00007ffd9dfbef6c sp 00007fff2c0f1510 error 4 in libindicator3.so.7.0.0[7ffd9dfba000+d000]
paul@precise-64:~$
```

See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953)

So then I purged unity-greeter and switched from lightdm to slim and finally I could get to the login screen! Logged in, no desktop. Ok, started gnome-shell manually using nautilus "open in terminal" and everything was working almost normally, but...no sound! Sound settings was saying "Dummy output - No Sound Card Detected".

More googling, established that the sound modules were being loaded. Tried a few things and then I thought well I want to be able to get to the desktop normally anyway so I decided to install gdm and use that instead of slim and hey presto - all back to normal, including sound (and the sound card is shown in sound settings again). Phew. :)

---

### Post by effenberg0x0 on 2012-01-28
I have tried to break it a couple times and I couldn't. Why would this breakage affect only some user and not others? I'm trying to found out what could be different here. 

It occurred to me that I am not using HUD PPA. Is that the case for you guys?

---

### Post by ventrical on 2012-01-28
> **paul_in_london said:**
> I was having lots of problems after some updates the other night. I could boot into recovery mode and update/upgrade, but that was about it. I spent a long time assuming it was nvidia-related because I'd inadvertently "upgraded" nvidia-current, replacing the xorg-edgers version. I got that back, still no go. Decided to purge xorg-edgers and ricotz-testing. No change. Re-enabled both of those ppas. No change.

I also thought that removing the 295.09 driver using the nvidia-installer:

```
NVIDIA-Linux-x86_64-295.09.run  --uninstall
```had messed up the symlinks somehow and was preventing me from booting normally with any kernel. This wasn't it though.

Eventually I noticed this:

```
paul@precise-64:~$ grep unity-greeter /var/log/syslog | tail
Jan 27 19:21:34 localhost kernel: [   25.435936] unity-greeter[1287]: segfault at 18 ip 00007fcb7aa73f6c sp 00007fffb858a550 error 4 in libindicator3.so.7.0.0[7fcb7aa6f000+d000]
Jan 27 19:21:36 localhost kernel: [   28.077771] unity-greeter[1442]: segfault at 18 ip 00007fa60e30bf6c sp 00007fff95bc3320 error 4 in libindicator3.so.7.0.0[7fa60e307000+d000]
Jan 27 19:21:39 localhost kernel: [   30.625236] unity-greeter[1487]: segfault at 18 ip 00007ffa4f125f6c sp 00007fffa36930c0 error 4 in libindicator3.so.7.0.0[7ffa4f121000+d000]
Jan 27 19:21:41 localhost kernel: [   33.213575] unity-greeter[1533]: segfault at 18 ip 00007fe511644f6c sp 00007fff7ec24990 error 4 in libindicator3.so.7.0.0[7fe511640000+d000]
Jan 27 19:21:44 localhost kernel: [   35.741111] unity-greeter[1578]: segfault at 18 ip 00007f7ac7379f6c sp 00007fff38eb7620 error 4 in libindicator3.so.7.0.0[7f7ac7375000+d000]
Jan 27 19:21:47 localhost kernel: [   38.334283] unity-greeter[1623]: segfault at 18 ip 00007f9146decf6c sp 00007fff27b4b620 error 4 in libindicator3.so.7.0.0[7f9146de8000+d000]
Jan 27 23:28:08 localhost kernel: [   30.422469] unity-greeter[1268]: segfault at 18 ip 00007fba56d33f6c sp 00007fffc62b51c0 error 4 in libindicator3.so.7.0.0[7fba56d2f000+d000]
Jan 27 23:28:10 localhost kernel: [   33.122828] unity-greeter[1423]: segfault at 18 ip 00007f036840cf6c sp 00007fff12092e30 error 4 in libindicator3.so.7.0.0[7f0368408000+d000]
Jan 27 23:28:13 localhost kernel: [   35.684712] unity-greeter[1468]: segfault at 18 ip 00007fe80e969f6c sp 00007fff17bc2450 error 4 in libindicator3.so.7.0.0[7fe80e965000+d000]
Jan 27 23:28:16 localhost kernel: [   38.250476] unity-greeter[1517]: segfault at 18 ip 00007ffd9dfbef6c sp 00007fff2c0f1510 error 4 in libindicator3.so.7.0.0[7ffd9dfba000+d000]
paul@precise-64:~$
```See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953)

So then I purged unity-greeter and switched from lightdm to slim and finally I could get to the login screen! Logged in, no desktop. Ok, started gnome-shell manually using nautilus "open in terminal" and everything was working almost normally, but...no sound! Sound settings was saying "Dummy output - No Sound Card Detected".

More googling, established that the sound modules were being loaded. Tried a few things and then I thought well I want to be able to get to the desktop normally anyway so I decided to install gdm and use that instead of slim and hey presto - all back to normal, including sound (and the sound card is shown in sound settings again). Phew. :)

 Thanks for this Paul.... I decided to give up a machine with a nVidia card on it and see what I can capture from this latest kernel borK? episode.

  Looks like you got something pinnend down pretty well. What do they call it over there .. a 'near miss' :)

---

### Post by paul_in_london on 2012-01-28
> **effenberg0x0 said:**
> I have tried to break it a couple times and I couldn't. Why would this breakage affect only some user and not others? I'm trying to found out what could be different here. 

It occurred to me that I am not using HUD PPA. Is that the case for you guys?

I'm not using HUD (or Unity), no. This has been the only really bad breakage I've had in precise so far. I was getting so frustrated I was almost thinking of reinstalling.

---

### Post by ventrical on 2012-01-28
> **effenberg0x0 said:**
> I have tried to break it a couple times and I couldn't. Why would this breakage affect only some user and not others? I'm trying to found out what could be different here. 

It occurred to me that I am not using HUD PPA. Is that the case for you guys?

No PPAs on this machine ...

 How would we tell if we have the HUD ? I never installed it manually.

 This one is a real weird one effenberg.. Ok .. I'm off to try and bust my Edubuntu Install 12.04 with Old nVidia card..

---

### Post by ventrical on 2012-01-28
It wants to remove nvidia 96

Here goes...

EDIT:

 I also wanted to point out the the first screenshot I sent dealt with the pop-up when I pressed <Reload> in Synpatic. Haven't seen this one happen. It makes me wonder then if there is something busted upstream already! ?

---

### Post by jpeddicord on 2012-01-28
Managed to get an older kernel installed and booting, but X won't start anyway. Removed nvidia-current completely, and I can *sorta* get it to start (I get the fallback mode dialog) but it appears my system is afflicted by the greeter crash.

Going to try with the basic gtk greeter in a moment.

Edit: I was able to get lightdm to start, at least.

First, I booted kernel -9 in recovery mode, remounted r/w. Then I installed the alternate greeter:
```

start dbus      # needed for network-manager
start network-manager
apt-get install lightdm-gtk-greeter
nano /etc/lightdm/lightdm.conf   # set greeter-session to lightdm-gtk-greeter

```

At this point, exited the shell and resumed normal boot. lightdm loads! Yay! But... gnome-session dies. Watching .xsession-errors while signing in ultimately ends with something along the lines of "no GSettings schemas are installed on the system." So we'll see what I can get to from here.

---

### Post by paul_in_london on 2012-01-28
> **ventrical said:**
> Thanks for this Paul.... I decided to give up a machine with a nVidia card on it and see what I can capture from this latest kernel borK? episode.

  Looks like you got something pinnend down pretty well. What do they call it over there .. a 'near miss' :)

Thanks ventrical. :) It was a near miss in terms of reinstalling I think! Not that it would necessarily have solved the problem anyway. Like I say, I was sure it was nvidia-related to start with. Have a look to see if unity-greeter is segfaulting in your case (if you're using it).

At the moment I'm using:

```
paul@precise-64:~$ uname -a
Linux precise-64 3.2.2-030202-generic #201201252035 SMP Thu Jan 26 01:36:10 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$
```

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 290.10-0ubuntu2+xedgers~precise1
  Candidate: 290.10-0ubuntu2+xedgers~precise1
  Version table:
 *** 290.10-0ubuntu2+xedgers~precise1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     290.10-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
```

This version of 290.10 apparently includes a patch that was supposed to make it work with the 3.3-rc1 kernel. Doesn't work though - dkms install of the nvidia driver fails.

---

### Post by ventrical on 2012-01-28
Here is what I got sofar on the fly...

```
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 355855 files and directories currently installed.)
Removing nvidia-96 ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
(Reading database ... 355781 files and directories currently installed.)
Preparing to replace friendly-recovery 0.2.18ubuntu1 (using .../friendly-recovery_0.2.19_all.deb) ...
Unpacking replacement friendly-recovery ...
Preparing to replace upstart 1.4-0ubuntu2 (using .../upstart_1.4-0ubuntu4_i386.deb) ...
Unpacking replacement upstart ...
Preparing to replace libc-dev-bin 2.13-24ubuntu3 (using .../libc-dev-bin_2.13-24ubuntu4_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.13-24ubuntu3 (using .../libc6-dev_2.13-24ubuntu4_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-bin 2.13-24ubuntu3 (using .../libc-bin_2.13-24ubuntu4_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Setting up libc-bin (2.13-24ubuntu4) ...
(Reading database ... 355781 files and directories currently installed.)
Preparing to replace libc6 2.13-24ubuntu3 (using .../libc6_2.13-24ubuntu4_i386.deb) ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Unpacking replacement libc6 ...
Setting up libc6 (2.13-24ubuntu4) ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 355781 files and directories currently installed.)
Preparing to replace linux-libc-dev 3.2.0-10.17 (using .../linux-libc-dev_3.2.0-11.19_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace tzdata 2011n-1 (using .../tzdata_2011n-2_i386.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2011n-2) ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.

Current default time zone: 'America/Toronto'
Local time is now:      Sat Jan 28 11:54:14 EST 2012.
Universal Time is now:  Sat Jan 28 16:54:14 UTC 2012.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 355781 files and directories currently installed.)
Preparing to replace libdconf-dbus-1-0 0.11.2-0ubuntu1 (using .../libdconf-dbus-1-0_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement libdconf-dbus-1-0 ...
Preparing to replace dconf-gsettings-backend 0.11.2-0ubuntu1 (using .../dconf-gsettings-backend_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement dconf-gsettings-backend ...
Preparing to replace dconf-service 0.11.2-0ubuntu1 (using .../dconf-service_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement dconf-service ...
Preparing to replace libdconf0 0.11.2-0ubuntu1 (using .../libdconf0_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement libdconf0 ...
Preparing to replace libglib2.0-data 2.31.10-0ubuntu2 (using .../libglib2.0-data_2.31.12-0ubuntu1_i386.deb) ...
Unpacking replacement libglib2.0-data ...
Preparing to replace libglib2.0-bin 2.31.10-0ubuntu2 (using .../libglib2.0-bin_2.31.12-0ubuntu1_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
Preparing to replace libgail-3-0 3.3.8-0ubuntu2 (using .../libgail-3-0_3.3.10-0ubuntu3_i386.deb) ...
Unpacking replacement libgail-3-0 ...
Preparing to replace libgtk-3-bin 3.3.8-0ubuntu2 (using .../libgtk-3-bin_3.3.10-0ubuntu3_i386.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace gnome-font-viewer 3.2.1-0ubuntu2 (using .../gnome-font-viewer_3.2.1-0ubuntu3_i386.deb) ...
Unpacking replacement gnome-font-viewer ...
Preparing to replace gnome-control-center-data 1:3.2.2-2ubuntu1 (using .../gnome-control-center-data_1%3a3.2.2-2ubuntu5_all.deb) ...
Unpacking replacement gnome-control-center-data ...
Preparing to replace gnome-settings-daemon 3.2.2-0ubuntu11 (using .../gnome-settings-daemon_3.2.2-0ubuntu12_i386.deb) ...
Unpac

```

---

### Post by paul_in_london on 2012-01-28
> **ventrical said:**
> Here is what I got sofar on the fly...

```
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 406.
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 355855 files and directories currently installed.)
Removing nvidia-96 ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
(Reading database ... 355781 files and directories currently installed.)
Preparing to replace friendly-recovery 0.2.18ubuntu1 (using .../friendly-recovery_0.2.19_all.deb) ...
Unpacking replacement friendly-recovery ...
Preparing to replace upstart 1.4-0ubuntu2 (using .../upstart_1.4-0ubuntu4_i386.deb) ...
Unpacking replacement upstart ...
Preparing to replace libc-dev-bin 2.13-24ubuntu3 (using .../libc-dev-bin_2.13-24ubuntu4_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.13-24ubuntu3 (using .../libc6-dev_2.13-24ubuntu4_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-bin 2.13-24ubuntu3 (using .../libc-bin_2.13-24ubuntu4_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Setting up libc-bin (2.13-24ubuntu4) ...
(Reading database ... 355781 files and directories currently installed.)
Preparing to replace libc6 2.13-24ubuntu3 (using .../libc6_2.13-24ubuntu4_i386.deb) ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Unpacking replacement libc6 ...
Setting up libc6 (2.13-24ubuntu4) ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 355781 files and directories currently installed.)
Preparing to replace linux-libc-dev 3.2.0-10.17 (using .../linux-libc-dev_3.2.0-11.19_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace tzdata 2011n-1 (using .../tzdata_2011n-2_i386.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2011n-2) ...
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.

Current default time zone: 'America/Toronto'
Local time is now:      Sat Jan 28 11:54:14 EST 2012.
Universal Time is now:  Sat Jan 28 16:54:14 UTC 2012.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 355781 files and directories currently installed.)
Preparing to replace libdconf-dbus-1-0 0.11.2-0ubuntu1 (using .../libdconf-dbus-1-0_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement libdconf-dbus-1-0 ...
Preparing to replace dconf-gsettings-backend 0.11.2-0ubuntu1 (using .../dconf-gsettings-backend_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement dconf-gsettings-backend ...
Preparing to replace dconf-service 0.11.2-0ubuntu1 (using .../dconf-service_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement dconf-service ...
Preparing to replace libdconf0 0.11.2-0ubuntu1 (using .../libdconf0_0.11.3-0ubuntu1_i386.deb) ...
Unpacking replacement libdconf0 ...
Preparing to replace libglib2.0-data 2.31.10-0ubuntu2 (using .../libglib2.0-data_2.31.12-0ubuntu1_i386.deb) ...
Unpacking replacement libglib2.0-data ...
Preparing to replace libglib2.0-bin 2.31.10-0ubuntu2 (using .../libglib2.0-bin_2.31.12-0ubuntu1_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
Preparing to replace libgail-3-0 3.3.8-0ubuntu2 (using .../libgail-3-0_3.3.10-0ubuntu3_i386.deb) ...
Unpacking replacement libgail-3-0 ...
Preparing to replace libgtk-3-bin 3.3.8-0ubuntu2 (using .../libgtk-3-bin_3.3.10-0ubuntu3_i386.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace gnome-font-viewer 3.2.1-0ubuntu2 (using .../gnome-font-viewer_3.2.1-0ubuntu3_i386.deb) ...
Unpacking replacement gnome-font-viewer ...
Preparing to replace gnome-control-center-data 1:3.2.2-2ubuntu1 (using .../gnome-control-center-data_1%3a3.2.2-2ubuntu5_all.deb) ...
Unpacking replacement gnome-control-center-data ...
Preparing to replace gnome-settings-daemon 3.2.2-0ubuntu11 (using .../gnome-settings-daemon_3.2.2-0ubuntu12_i386.deb) ...
Unpac

```

No updates available for me at the moment. This is 64 bit btw.

Taking one of your examples:

```
paul@precise-64:~$ apt-cache policy dconf-gsettings-backend
dconf-gsettings-backend:
  Installed: 0.11.3-0ubuntu1
  Candidate: 0.11.3-0ubuntu1
  Version table:
 *** 0.11.3-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```

i.e. same as you apart from the architecture.

---

### Post by P-I H on 2012-01-28
I have a system based on the daily build from yesterday, upgraded today with the new kernel.
Compiz crashes with a normal boot and there are no Launcher or panel.

When I boot in Recovery mode and select **Resume to normal boot** in the menu, the system starts OK.
Nvidia driver 290.10 is used and Unity works fine.

---

### Post by kansasnoob on 2012-01-28
> **shakabra said:**
> Hey guys,

Just revert back to the old kernel. That's why GRUB keeps them there. When you boot just press <SHIFT> like a maniac until the GRUB boot options appear and then select an older kernel.

esac

+1! My nVidia/AMD box has been borked for a while, but today even my Intel box was borked with the latest kernel.

So goes development :D

---

### Post by jpeddicord on 2012-01-28
Got back in!

I went back to the most recent kernel in recovery and re-installed nvidia-current. Then X starts up just fine (at least with the gtk greeter). The session was still broken, but reverting gnome-settings-daemon back to 3.2.2-0ubuntu11 brought it back.

---

### Post by ventrical on 2012-01-28
> **paul_in_london said:**
> No updates available for me at the moment. This is 64 bit btw.

Taking one of your examples:

```
paul@precise-64:~$ apt-cache policy dconf-gsettings-backend
dconf-gsettings-backend:
  Installed: 0.11.3-0ubuntu1
  Candidate: 0.11.3-0ubuntu1
  Version table:
 *** 0.11.3-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```i.e. same as you apart from the architecture.


Thanks Paul...

 EDIT .. ok .. my hunch was correct...  I just stuck the old monitor back on (plug-in) and it works but will not detect.

 Ok .. the install of 3.2.0-11 on my Edubuntu tower went great despite the constant errors of "Gtk .. theme package .. etc "

  I DID however have to change video monitors. I have a few scratch LCDs laying around and there is this older one that I just like .. but sometimes Ubuntu will detect it properly and other times (as in this case of new kernel) it will not. 

  That was not the case with the Dell install. It just seemed to royally bork itself up (No offence to our QEII  :)

  So this goes back to an earlier problem with pre-alpha where I could not use this one monitor and that , I believe, was wrong  monitor detection capabilities.

What do ya know .. just had a deja vu :)

---

### Post by ventrical on 2012-01-28
Re: Undetected monitor.

---

### Post by ventrical on 2012-01-28
And this is what I had previously -Unknown but still had parameters. Now those settings are gone globally for all the kernels I have stored which leads me to believe that the problem is with X itself and not the video drivers.

---

### Post by effenberg0x0 on 2012-01-28
I am sort of lost here, sorry (I caught a cold, and can't think clearly with fever and constant sneezing). Please hep me understand, I'm slow.

Just a note to **@Ventrical**: Get rid of "Gtk-WARNING **: Unable to locate theme engine..." by running sudo apt-get install gtk2-engines-pixbuf

**Paul_In_London** pointed us to the bug described at **[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953)** which is DM/Greeter related because of libindicator3-7

```
$ sudo apt-cache rdepends libindicator3-7
libindicator3-7
Reverse Depends:
  libindicator3-7:i386
  libindicator3-tools
  indicator-network
[B]  unity-services
  unity-greeter
  unity[/B]
  ubiquity-frontend-gtk
  libunity-2d-private0
  libindicator3-dev
  libappindicator3-1
  indicator-sound
  indicator-session
  indicator-power
  indicator-messages
  indicator-datetime
  indicator-appmenu
  indicator-application

```So, there's no connection to Kernel or VGA. And downgrading the greeter causes libindicator3-7 to be replaced by the working libindicator3-**6**, thus allowing all the broken rdeps (see above) to work properly again. Is that it? 

Thanks,
Effenberg

---

### Post by ventrical on 2012-01-28
> **effenberg0x0 said:**
> I am sort of lost here, sorry (I caught a cold, and can't think clearly with fever and constant sneezing). Please hep me understand, I'm slow.

Just a note to **@Ventrical**: Get rid of "Gtk-WARNING **: Unable to locate theme engine..." by running sudo apt-get install gtk2-engines-pixbuf

**Paul_In_London** pointed us to the bug described at **[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/921953)** which is DM/Greeter related because of libindicator3-7

```
$ sudo apt-cache rdepends libindicator3-7
libindicator3-7
Reverse Depends:
  libindicator3-7:i386
  libindicator3-tools
  indicator-network
[B]  unity-services
  unity-greeter
  unity[/B]
  ubiquity-frontend-gtk
  libunity-2d-private0
  libindicator3-dev
  libappindicator3-1
  indicator-sound
  indicator-session
  indicator-power
  indicator-messages
  indicator-datetime
  indicator-appmenu
  indicator-application

```So, there's no connection to Kernel or VGA. And downgrading the greeter causes libindicator3-7 to be replaced by the working libindicator3-**6**, thus allowing all the broken rdeps (see above) to work properly again. Is that it? 

Thanks,
Effenberg

Hey .. thanks  ... the first workaround worked. So , what do you suggest we do . ie "like drop to an earlier kernel then type  dot , dot da da  in the terminal .. etc.. ??. 

Hey .. take care of yourself, have an orange or herbal tea or somethng and get some rest because we need Clippy to be in tip top shape !  :)

---

### Post by paul_in_london on 2012-01-28
> **ventrical said:**
> And this is what I had previously -Unknown but still had parameters. Now those settings are gone globally for all the kernels I have stored which leads me to believe that the problem is with X itself and not the video drivers.

Sorry you're having monitor troubles.

Here are my screenshots.

EDIT: Oops! Sorry, these are blank. Just realised I got rid of shutter a while back. It was stopping some updates or something.

Anyway, the point of the screenshots was that display settings shows no monitor info apart from the correct resolution, but nvidia xserver settings gives more monitor info.

EDIT2: shutter is actually installable again for me at the moment, but I prefer to try and stop my install getting too bloated so I'll leave it for now:

```
paul@precise-64:~$ sudo aptitude install shutter
The following NEW packages will be installed:
  libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} libbonoboui2-common{a} libgnome2-0{a} libgnome2-gconf-perl{a} libgnome2-perl{a} libgnomeui-0{a} libgnomeui-common{a} libidl0{a} liborbit2{a} shutter 
0 packages upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,469 kB of archives. After unpacking 23.1 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
```

---

### Post by OGpmpdog on 2012-01-28
Hi guys,

I'd like to thank everyone for their input...here's an update.

I tried lucaszade's suggestion of trying to bypass the nividia module during POST.  However, the system just hangs at "Setting up Network Configuration", even after plugging in the network cable.

After timing out, system hangs at login screen...bummer.

I also tried to boot into kernels 3.2.09 & 3.2.10 - no luck - same results as kernel 3.2.11.

No, I do not have the HUD PPA in my software source lists.

Looks like I took 1 for the team :)

---

### Post by effenberg0x0 on 2012-01-28
> **ventrical said:**
> Hey .. thanks  ... the first workaround worked. So , what do you suggest we do . ie "like drop to an earlier kernel then type  dot , dot da da  in the terminal .. etc.. ??. 

I don't know, cause I can't really break it here. I guess once again Clippy is manipulating reality at strings level. I want to interpret the reports in this thread into a single cause-effect situation. I'm failing to understand what the Kernel and VGA relation to libindicator and its deps/rdeps is :( 

I think I'm gonna finish work stuff, take some meds, sleep and leave this one to you guys, I'm in no condition to offer any decent help.

---

### Post by paul_in_london on 2012-01-28
I've gone back to **lightdm** now after using **Harry33**'s sugggestion here:

[http://ubuntuforums.org/showpost.php?p=11622977&postcount=9](http://ubuntuforums.org/showpost.php?p=11622977&postcount=9)

Less appealing aesthetically, but works fine.

---

### Post by masinick on 2012-01-28
I am using the 3.2.0-11-generic version of the kernel, and this version, though it will boot, does not appear to support Broadcom Wireless firmware.  Checking the log, I found this, thanks to some "heads up" reports about the 3.2 Linux kernel elsewhere.

This will be CRITICAL to fix BEFORE the release, so I hope that it's already being worked on.  I understand that it will be fixed in a future release of the kernel, but I do not know if the regression fix has been ported back to the 3.2 release or not.

Again, this is vital, critical, to fix as long before the releease as possible, so that we can get great test coverage on it.

Thanks!

2012-01-28 15:50:20,224 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-01-28 15:50:20,251 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-28 15:50:23,214 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-28 15:50:23,572 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-01-28 15:50:23,847 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

---

### Post by ventrical on 2012-01-28
> **paul_in_london said:**
> I've gone back to **lightdm** now after using **Harry33**'s sugggestion here:

[http://ubuntuforums.org/showpost.php?p=11622977&postcount=9](http://ubuntuforums.org/showpost.php?p=11622977&postcount=9)

Less appealing aesthetically, but works fine.


 Ok.. @Paul, Effenberg and all,


  What happened here to my Dell was that the last update *DID NOT* complete it's install. I was just tinkering around and  went to terminal in an earlier kernel version , type :
sudo apt-get install

 and the remaining updates were then installed. So, something along the path deferred them.

A ll is well here in Dell OptiGX270 - so far - so good.

Uninstalled Files:

```

ventrical@ventrical-OptiPlex-GX270:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  abiword abiword-plugin-grammar abiword-plugin-mathview audacious
  audacious-plugins banshee banshee-extension-soundmenu
  banshee-extension-ubuntuonemusicstore libabiword-2.9 libappindicator1
  libaudclient2 libaudcore1 linux-headers-generic linux-headers-generic-pae
  lxpanel-indicator-applet-plugin python-appindicator ttf-thai-tlwg
The following packages will be upgraded:
  abiword-common adium-theme-ubuntu baobab bind9-host binutils bluez-alsa
  bluez-cups bluez-gstreamer dnsutils firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en fonts-opensymbol gdb gedit
  gedit-common ghostscript ghostscript-cups ghostscript-x
  gir1.2-appindicator3-0.1 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 gir1.2-wnck-3.0
  gnome-bluetooth gnome-disk-utility gnome-games-data gnome-screenshot
  gnome-search-tool gnome-sudoku gnome-system-log gnomine gtk2-engines-murrine
  ibus ibus-gtk ibus-gtk3 icedtea-6-jre-cacao icedtea-6-jre-jamvm
  indicator-application indicator-appmenu indicator-datetime
  indicator-messages indicator-power indicator-session indicator-sound
  indicator-status-provider-mc5 indicator-status-provider-pidgin
  intel-gpu-tools language-selector-common language-selector-gnome
  libappindicator0.1-cil libbind9-80 libdns81 libgee2 libgnome-bluetooth8
  libgs9 libgs9-common libicu48 libindicator-messages-status-provider1
  libisc83 libisccc80 libisccfg82 libjavascriptcoregtk-1.0-0
  libjavascriptcoregtk-3.0-0 liblwres80 libnautilus-extension1a
  libpoppler-glib8 libpoppler19 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-binfilter libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-style-human libreoffice-style-tango
  libreoffice-writer libslv2-9 libsmbclient libsnmp-base libsnmp15
  libubuntuone-1.0-1 libunity-2d-private0 libunity-core-5.0-5 libutouch-frame1
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libwnck-3-0 libwnck-3-common linux-firmware
  linux-generic linux-image-3.2.0-11-generic linux-image-generic
  lubuntu-default-settings lxpanel media-player-info mplayer multiarch-support
  nautilus notify-osd openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  parted policykit-1-gnome poppler-utils pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-debian python-gi python-gi-cairo python-gobject
  python-ibus python-keyring python-lazr.uri python-uno samba-common
  samba-common-bin smbclient software-center telepathy-indicator thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us ttf-opensymbol
  ubuntu-desktop ubuntu-minimal ubuntu-restricted-addons ubuntu-standard unity
  unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread
  unity-common unity-greeter unity-services uno-libs3 update-manager
  update-manager-core ure uuid-runtime vino wpasupplicant x11-common xorg
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
197 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 0 B/333 MB of archives.
After this operation, 120 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

and just an add on here ... before I could update it told me that all the above updates could not be authenticated so there is still that authntication bug in synaptic from a while back

Anybody have any news on that??

---

### Post by paul_in_london on 2012-01-28
> **ventrical said:**
> Ok.. @Paul, Effenberg and all,


  What happened here to my Dell was that the last update *DID NOT* complete it's install. I was just tinkering around and  went to terminal in an earlier kernel version , type :
sudo apt-get install

 and the remaining updates were then installed. So, something along the path deferred them.

A ll is well here in Dell OptiGX270 - so far - so good.

Uninstalled Files:

```

ventrical@ventrical-OptiPlex-GX270:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  abiword abiword-plugin-grammar abiword-plugin-mathview audacious
  audacious-plugins banshee banshee-extension-soundmenu
  banshee-extension-ubuntuonemusicstore libabiword-2.9 libappindicator1
  libaudclient2 libaudcore1 linux-headers-generic linux-headers-generic-pae
  lxpanel-indicator-applet-plugin python-appindicator ttf-thai-tlwg
The following packages will be upgraded:
  abiword-common adium-theme-ubuntu baobab bind9-host binutils bluez-alsa
  bluez-cups bluez-gstreamer dnsutils firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en fonts-opensymbol gdb gedit
  gedit-common ghostscript ghostscript-cups ghostscript-x
  gir1.2-appindicator3-0.1 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 gir1.2-wnck-3.0
  gnome-bluetooth gnome-disk-utility gnome-games-data gnome-screenshot
  gnome-search-tool gnome-sudoku gnome-system-log gnomine gtk2-engines-murrine
  ibus ibus-gtk ibus-gtk3 icedtea-6-jre-cacao icedtea-6-jre-jamvm
  indicator-application indicator-appmenu indicator-datetime
  indicator-messages indicator-power indicator-session indicator-sound
  indicator-status-provider-mc5 indicator-status-provider-pidgin
  intel-gpu-tools language-selector-common language-selector-gnome
  libappindicator0.1-cil libbind9-80 libdns81 libgee2 libgnome-bluetooth8
  libgs9 libgs9-common libicu48 libindicator-messages-status-provider1
  libisc83 libisccc80 libisccfg82 libjavascriptcoregtk-1.0-0
  libjavascriptcoregtk-3.0-0 liblwres80 libnautilus-extension1a
  libpoppler-glib8 libpoppler19 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-binfilter libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-style-human libreoffice-style-tango
  libreoffice-writer libslv2-9 libsmbclient libsnmp-base libsnmp15
  libubuntuone-1.0-1 libunity-2d-private0 libunity-core-5.0-5 libutouch-frame1
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libwnck-3-0 libwnck-3-common linux-firmware
  linux-generic linux-image-3.2.0-11-generic linux-image-generic
  lubuntu-default-settings lxpanel media-player-info mplayer multiarch-support
  nautilus notify-osd openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  parted policykit-1-gnome poppler-utils pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-debian python-gi python-gi-cairo python-gobject
  python-ibus python-keyring python-lazr.uri python-uno samba-common
  samba-common-bin smbclient software-center telepathy-indicator thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-gb thunderbird-locale-en-us ttf-opensymbol
  ubuntu-desktop ubuntu-minimal ubuntu-restricted-addons ubuntu-standard unity
  unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread
  unity-common unity-greeter unity-services uno-libs3 update-manager
  update-manager-core ure uuid-runtime vino wpasupplicant x11-common xorg
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
197 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 0 B/333 MB of archives.
After this operation, 120 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

and just an add on here ... before I could update it told me that all the above updates could not be authenticated so there is still that authntication bug in synaptic from a while back

Anybody have any news on that??

Hi ventrical. You've got quite a few more packages on your system than I have because I started with a minimal command-line install and built it up from there.

Btw, my **linux-generic** is:

```
paul@precise-64:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 3.2.0.11.11
  Candidate: 3.2.0.11.11
  Version table:
 *** 3.2.0.11.11 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```

I wouldn't worry about the authentication messages. That happens from time to time. You can fix it by importing the keys it complains about, but I often don't bother. :)

---

### Post by ventrical on 2012-01-28
> **paul_in_london said:**
> Hi ventrical. You've got quite a few more packages on your system than I have because I started with a minimal command-line install and built it up from there.

Btw, my **linux-generic** is:

```
paul@precise-64:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 3.2.0.11.11
  Candidate: 3.2.0.11.11
  Version table:
 *** 3.2.0.11.11 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```I wouldn't worry about the authentication messages. That happens from time to time. You can fix it by importing the keys it complains about, but I often don't bother. :)


Same here Paul..

```
ventrical@ventrical-OptiPlex-GX270:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 3.2.0.11.11
  Candidate: 3.2.0.11.11
  Version table:
 *** 3.2.0.11.11 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
ventrical@ventrical-OptiPlex-GX270:~$
```

---

### Post by paul_in_london on 2012-01-28
> **ventrical said:**
> Same here Paul..

```
ventrical@ventrical-OptiPlex-GX270:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 3.2.0.11.11
  Candidate: 3.2.0.11.11
  Version table:
 *** 3.2.0.11.11 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
ventrical@ventrical-OptiPlex-GX270:~$
```

Yep, as expected. The one I'm actually using is 3.2.2 from ppa mainline. No sign of 3.3-rc2 yet (but even when it comes out it still might not work with nvidia).

---

### Post by ronacc on 2012-01-28
I just updated to the -11 amd64 generic kernel , I am running Gnome-shell and the LightDM greeter with Nvidia 290.10 driver . No problems on reboot greeter came up then desktop .

---

### Post by paul_in_london on 2012-01-28
> **ronacc said:**
> I just updated to the -11 amd64 generic kernel , I am running Gnome-shell and the LightDM greeter with Nvidia 290.10 driver . No problems on reboot greeter came up then desktop .

+1 Once I got rid of **unity-greeter** all of my boot problems went away. :)

Well not at first. Only when I switched to **gdm**, which worked well. Then I realised (thanks to **Harry33**!) that I needed to change **/etc/lightdm/lightdm.conf**:

```
#greeter-session=unity-greeter
**[COLOR="Red"]greeter-session=lightdm-gtk-greeter[/COLOR]**
```

before I could go back to using that again.

---

### Post by paul_in_london on 2012-01-28
Just made a nice discovery for those of you who are using xorg-edgers and were stuck on nvidia 290.10:

```
sudo add-apt-repository ppa:portis25/test
```

and you can then upgrade nvidia-current to 295.09.

It also builds ok against kernel 3.3-rc1. :)

```
paul@precise-64:~$ uname -a
Linux precise-64 3.3.0-030300rc1-generic #201201191835 SMP Thu Jan 19 23:36:54 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$
```

```
paul@precise-64:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.09-0
  Candidate: 295.09-0
  Version table:
 *** 295.09-0 0
        500 http://ppa.launchpad.net/portis25/test/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     290.10-0ubuntu2+xedgers~precise1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ precise/main amd64 Packages
     290.10-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages

```

---

### Post by Harry33 on 2012-01-29
> **paul_in_london said:**
> Just made a nice discovery for those of you who are using xorg-edgers and were stuck on nvidia 290.10:

```
sudo add-apt-repository ppa:portis25/test
```and you can then upgrade nvidia-current to 295.09.
It also builds ok against kernel 3.3-rc1. :)
...


Hi Paul,

Now that is interesting.
Really, that particular nvidia-current package (295.09-0) is built against xorg-video-abi-12 and xserver-xorg-core (>= 2:1.11.99), which means xserver 1.12 rc1 or newer.

It also means it cannot be installed on original Precise, which has xserver 1.11.

---

### Post by fabricator4 on 2012-01-29
> **paul_in_london said:**
> 
```
paul@precise-64:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 3.2.0.11.11
  Candidate: 3.2.0.11.11
  Version table:
 *** 3.2.0.11.11 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
``` 

Currently at 3.2.0.11-19 32 bit here and working great.

I think I dodged that bullet.

Chris

---

### Post by keithpeter on 2012-01-29
Hello All

Using an nvidia card in the recycled xeon with a fresh install of 64 bit Precise, all seems ok with the proprietary drivers as installed by Jockey:-

```
keith@xeon:~$ uname -a
Linux xeon 3.2.0-12-generic #20-Ubuntu SMP Fri Jan 27 23:13:36 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
keith@xeon:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 3.2.0.12.12
  Candidate: 3.2.0.12.12
  Version table:
 *** 3.2.0.12.12 0
keith@xeon:~$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.11.3-0ubuntu9
  Candidate: 2:1.11.3-0ubuntu9
  Version table:
 *** 2:1.11.3-0ubuntu9 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```

I installed from a USB stick made with the 28th Jan daily build and when rebooting from hard drive, I had the scrambled splash screen that others have seen. Rebooting into recovery gave a vesa style session, updated the system, rebooted without installing the proprietary drivers and got native resolution desktop ok, but no 3d.

Installing proprietary drivers using Jockey fine, have 3d desktop, and Gnome Shell is a lot less crashy with the nvidia card compared to the radeon, so assuming thats a mutter thing.

Added the HUD repro and I'm HUDing away nicely...

---

### Post by paul_in_london on 2012-01-29
> **Harry33 said:**
> Hi Paul,

Now that is interesting.
Really, that particular nvidia-current package (295.09-0) is built against xorg-video-abi-12 and xserver-xorg-core (>= 2:1.11.99), which means xserver 1.12 rc1 or newer.

It also means it cannot be installed on original Precise, which has xserver 1.11.

Hi Harry.

The version of xserver-xorg-core I'm using is::

```
...
Package: xserver-xorg-core
Source: xorg-server
Priority: optional
Section: x11
Installed-Size: 4181
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
**[COLOR="Red"]Version: 2:1.11.99.901+git20120127.02775efb-0ubuntu0sarvatt[/COLOR]**
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Provides: **[COLOR="Red"]xorg-input-abi-16, xorg-video-abi-12[/COLOR]**
...
```

nvidia-current 295.09 from that ppa does apparently depend on the correct version of xorg-video-abi:

```
...
Package: nvidia-current
Source: nvidia-graphics-drivers
Priority: optional
Section: misc
Installed-Size: 178830
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
**[COLOR="Red"]Version: 295.09-0[/COLOR]**
Recommends: nvidia-settings
Replaces: nvidia-180-modaliases, nvidia-185-modaliases, nvidia-current-modaliases
Provides: xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, \
linux-headers-generic | linux-headers, patch, acpid, libc6 (>= 2.2.5), \
libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, \
zlib1g (>= 1:1.1.4),**[COLOR="Red"] xorg-video-abi-12[/COLOR]**, \
xserver-xorg-core (>= 2:1.11.99)
```

I still have the "IgnoreABI" flag set in xorg.conf anyway and it seems to work fine. :)

---

### Post by Harry33 on 2012-01-29
> **paul_in_london said:**
> Hi Harry.

..

I still have the "IgnoreABI" flag set in xorg.conf anyway and it seems to work fine. :)

So do I.
Anyway, it never hurts to keep that line, just in case.
Of course it is always possible to add that line afterwards in recovery mode from console and with nano. ;)

---

### Post by OGpmpdog on 2012-01-30
Hi all, a quick update.

I couldnt wait for Alpha 2!!

Tried to install The 1-29-12 PP daily build, and got an installation failed error (flash plug-in failed to build 404 error?)

33 people have already submitted this "critical" bug to launchpad.

Undeterred, I successfully re-installed the original A1 build, dated 12-1-11...However, I borked the install AGAIN after trying to update to kernel 3.2.12.  I looked in the terminal, and there was an error while the system was configuring kernel 3.2.12..I got the same breakage in kernel 3.2.11.

This was frustrating because I used sudo-aptitude safe upgrade

I suppose this is just a T61-Nvidia Quadro issue? 

I also have precise installed on 3 newer hardware desktops; beyond the 3.2.11 hiccups, everything is working fine on these machines.

Ultimately, I re re-installed original A1 build:D, using kernel 3.2.02 ;), and I dont know when I will regain the courage to update.

Peace.

---

### Post by paul_in_london on 2012-01-30
> **OGpmpdog said:**
> Hi all, a quick update.

I couldnt wait for Alpha 2!!

Tried to install The 1-29-12 PP daily build, and got an installation failed error (flash plug-in failed to build 404 error?)

33 people have already submitted this "critical" bug to launchpad.

Undeterred, I successfully re-installed the original A1 build, dated 12-1-11...However, I borked the install AGAIN after trying to update to kernel 3.2.12.  I looked in the terminal, and there was an error while the system was  ..I got the same breakage in kernel 3.2.11.

This was frustrating because I used sudo-aptitude safe upgrade

I suppose this is just a T61-Nvidia Quadro issue? 

I also have precise installed on 3 newer hardware desktops; beyond the 3.2.11 hiccups, everything is working fine on these machines.

Ultimately, I re re-installed original A1 build:D, using kernel 3.2.02 ;), and I dont know when I will regain the courage to update.

Peace.

Are you able to post the error you got when the system was configuring kernel 3.2.12?

This box has:

```
paul@precise-64:~$ lspci -v | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV41GL [Quadro FX 1400] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: nVidia Corporation Device 0243
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nouveau, nvidiafb
paul@precise-64:~$
```

I'm actually using nvidia-current 295.09 from a ppa and it's working fine with the 3.2 and 3.3-rc1 kernels. I'm also using the xorg-edgers ppa. Depending on which version of xorg you're using you may need to create an xorg.conf file (if you don't already have one) with the "IgnoreABI" flag set.

I can't remember now what was happening with the 290.10 driver because I was having major boot problems caused, as it turned out, by unity-greeter segfaulting.

---

### Post by OGpmpdog on 2012-01-30
Hi and thanks for replying.

No, I cannot post output error, because I'm at work right now, chained to Windoze XP :p

Also, since I've already re re-installed :p, it's probably too late to post the error verbatim.

The errors were along the lines "crtical nvidia driver failure from oneiric to precise".

I've been stuck with Nvidia 290.10 since last Nov 16.

Heyo, I cant learn without borking...xorg ppa, X stack 1.12 here I come!

With that said, I'll probably be back real soon.

Peace.

---

### Post by paul_in_london on 2012-01-30
> **OGpmpdog said:**
> Hi and thanks for replying.

No, I cannot post output error, because I'm at work right now, chained to Windoze XP :p

Also, since I've already re re-installed :p, it's probably too late to post the error verbatim.

The errors were along the lines "crtical nvidia driver failure from oneiric to precise".

I've been stuck with Nvidia 290.10 since last Nov 16.

Heyo, I cant learn without borking...xorg ppa, X stack 1.12 here I come!

With that said, I'll probably be back real soon.

Peace.

Ok, no problem. Maybe you could test out the next couple of daily builds in a VM first? Another thing you could do is to try installing a boot-only version of the daily build from here:

```
http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/precise/main/installer-i386/current/images/netboot/
```

or here according to your architecture:

```
http://archive.ubuntu.com/ubuntu/ubuntu/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/
```

Download the mini.iso and then once you've installed a bare-bones command line system you can build it up from there. That's what I do if I'm installing from scratch. :)

---

### Post by ventrical on 2012-01-30
> **paul_in_london said:**
> Hi ventrical. You've got quite a few more packages on your system than I have because I started with a minimal command-line install and built it up from there.

Btw, my **linux-generic** is:

```
paul@precise-64:~$ apt-cache policy linux-generic
linux-generic:
  Installed: 3.2.0.11.11
  Candidate: 3.2.0.11.11
  Version table:
 *** 3.2.0.11.11 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```I wouldn't worry about the authentication messages. That happens from time to time. You can fix it by importing the keys it complains about, but I often don't bother. :)


How do we import keys ? I know it has the option in synaptic but I am not totally sure how.

---

### Post by paul_in_london on 2012-01-30
> **ventrical said:**
> How do we import keys ? I know it has the option in synaptic but I am not totally sure how.

Hi ventrical. This sort of thing:

> [http://ubuntuforums.org/showpost.php?p=11395810&postcount=3](http://ubuntuforums.org/showpost.php?p=11395810&postcount=3)

Another thing you can try:

```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update
```

except that I use aptitude. :)

EDIT: For a given key (and key server), you might need two steps like this:

```
gpg --export --armor 4F994635**4E9CFF4E** | sudo apt-key add -
gpg --keyserver wwwkeys.de.pgp.net --recv-keys **4E9CFF4E**
```

(Scroll down to the stuff about keys on this page:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)).

---

### Post by OGpmpdog on 2012-02-06
Hi all,

Just providing an update since last week...

My T61 laptop was borked after the upgrade to kernel 3.2.10.

I've re-installed Precise, using Xorg & Nvidia 295.17 PPA's.

As of today, Precise is working, but it's quite sluggish. 

Also:

1) Ubuntu Tweak(version 7?)is broken
2) Status bar Icons (wireless, Sound, Battery Indicator) are missing on Top panel (In Gnome 3 session).
3) Gnome3 shell crashes every time I press the Super button...Cinnamon, Gnome classic, and Unity all work OK.

My T61 has been bulletproof since Intrepid...but Precise has been a temperamental snob the past 7-10 days.

peace.

---

