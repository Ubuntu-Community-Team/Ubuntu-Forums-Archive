---
title: "Linux 3.4.0 rc7"
date: 2012-05-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-05-15
Linux kernel 3.4.0 rc7 is about to hit the Quantal repos.

See here:
[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.4](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.4)

---

### Post by JMB74 on 2012-05-15
Failed to build for i386 for some reason. Others built OK.

---

### Post by JMB74 on 2012-05-15
[http://voices.canonical.com/kernelteam/2012/05/15/kernel-team-meeting-minutes-may-15-2012/](http://voices.canonical.com/kernelteam/2012/05/15/kernel-team-meeting-minutes-may-15-2012/)

> **Status: Quantal Development Kernel **

  a few things…
 Work items are beginning to populate the blueprints.  I’ll start calling
 out specific work items in upcoming meetings.
 We’ve rebased the Quantal kernel to upstream v3.4-rc7.  We uploaded but
 ran into a build failure on i386.  Test builds are currently underway
 and we will re-upload shortly.  We also have the quantal kernel building
 in precise.  We are getting a PPA set up so that testing can commence.
 Important upcoming dates:

---

### Post by JMB74 on 2012-05-15
The fresh try mentioned above.

[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.5](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.5)

---

### Post by Miykel on 2012-05-15
G'Day guys, I'm in desperate need of some help, I've downloaded the tar.gz and extracted it, tried to read the readme as to compiling the kernel but it may as well be written in Marsian, I tried some of the things it says but no good, is there somewhere I can learn more about compiling, in plain English, so for everything I've read assumes you know most of the stuff already, or is there a simple way to do it ??
Regards Miykel

---

### Post by cariboo on 2012-05-15
You may want to have a look at [this]("https://help.ubuntu.com/community/Kernel/Compile") wiki page before trying to compile the kernel yourself.

---

### Post by Miykel on 2012-05-16
Thanks for that Cariboo, I had a read but it seems to be talking about customizing the kernel,that might happen a long way down the track, for me, right now I'd just like to learn how to install the kernel from the tar.gz package, I tried the deb packages but I couldn't boot into the new kernel so I thought if I could do it via tar.gz packages it might work.......or not.
Regards Miykel

---

### Post by Harry33 on 2012-05-16
> **Miykel said:**
> Thanks for that Cariboo, I had a read but it seems to be talking about customizing the kernel,that might happen a long way down the track, for me, right now I'd just like to learn how to install the kernel from the tar.gz package, I tried the deb packages but I couldn't boot into the new kernel so I thought if I could do it via tar.gz packages it might work.......or not.
Regards Miykel

Did you tried the 3.4.0 rc7?
These ought to be installed (manual installation without meta packages):

32-bit
[linux-libc-dev_3.4.0-2.5_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491629/+files/linux-libc-dev_3.4.0-2.5_i386.deb")
[linux-headers-3.4.0-2_3.4.0-2.5_all.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491629/+files/linux-headers-3.4.0-2_3.4.0-2.5_all.deb")
[linux-headers-3.4.0-2-generic-pae_3.4.0-2.5_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491629/+files/linux-headers-3.4.0-2-generic-pae_3.4.0-2.5_i386.deb")
[linux-image-3.4.0-2-generic-pae_3.4.0-2.5_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491629/+files/linux-image-3.4.0-2-generic-pae_3.4.0-2.5_i386.deb")

64-bit
[linux-libc-dev_3.4.0-2.5_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491626/+files/linux-libc-dev_3.4.0-2.5_amd64.deb")
[linux-headers-3.4.0-2_3.4.0-2.5_all.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491629/+files/linux-headers-3.4.0-2_3.4.0-2.5_all.deb")
[linux-headers-3.4.0-2-generic_3.4.0-2.5_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491626/+files/linux-headers-3.4.0-2-generic_3.4.0-2.5_amd64.deb")
[linux-image-3.4.0-2-generic_3.4.0-2.5_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5/+build/3491626/+files/linux-image-3.4.0-2-generic_3.4.0-2.5_amd64.deb")

---

### Post by VinDSL on 2012-05-16
> **Harry33 said:**
> Did you tried the 3.4.0 rc7?

Hrm...

I went to the link, at the top of this thread:
[INDENT]
[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.4](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.4)[/INDENT]

> * Rebase to v3.4-rc7


...and everything appears to have been rejected and/or failed to build.  :confused:

---

### Post by VinDSL on 2012-05-16
n/m

Figured it out... been superseded:

[INDENT][“linux” 3.4.0-**[COLOR="DarkRed"]2.5[/COLOR]** source package in Ubuntu]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5")[/INDENT]

---

### Post by Harry33 on 2012-05-16
> **VinDSL said:**
> n/m

Figured it out... been superseded:
[INDENT][“linux” 3.4.0-**[COLOR=DarkRed]2.5[/COLOR]** source package in Ubuntu]("https://launchpad.net/ubuntu/+source/linux/3.4.0-2.5")[/INDENT]

Yes and it is working fine here with nvidia-current_302.07 and xserver 1.12.2 rc.

---

### Post by VinDSL on 2012-05-16
> **Harry33 said:**
> Yes and it is working fine here with nvidia-current_302.07 and xserver 1.12.2 rc.
Dittos!  ;)

---

### Post by JMB74 on 2012-05-16
Yet another newer revision just uploaded.

[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.6](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.6)

---

### Post by VinDSL on 2012-05-16
> **JMB74 said:**
> Yet another newer revision just uploaded.

[https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.6](https://launchpad.net/ubuntu/quantal/+source/linux/3.4.0-2.6)
Oh, joy!  Really!  :)

I'm experiencing (may be related or not):

[LIST]
[*]Adobe Flash issues
[*]Lost all SSH/SFTP auth
[*]Saved passwords in Chromium are toast
[*]Ubu Forums is "radiation orange" now (j/k)
[/LIST]
3.4.0-2.5 may be the shortest lived kernel I've ever run...  LoL!

---

### Post by VinDSL on 2012-05-16
Bwahahahaha!

This is like waiting for a baby to be born...  :D

> [SIZE="+1"]Build status[/SIZE]
 Currently building on roseapple

Build score:2505 ([What's this?]("https://help.launchpad.net/Packaging/BuildScores"))
Started 1 hour ago

---

### Post by VinDSL on 2012-05-16
Ah!  That's better...  :)


[[IMG]http://vindsl.com/images/vindsl-desktop-16-may-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-16-may-2012-2.png")


```
vindsl@Zuul:~$ echo && echo -n "Date/Time: " && date && echo -n "Release: " && lsb_release -sd && echo -n "Kernel: " || cat /etc/*release && uname -s -r && echo -n "Unity: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo &&  dpkg -s mesa-utils && echo || echo && echo "Xserver xorg core:" && apt-cache policy xserver-xorg-core | grep Installed && echo

Date/Time: Wed May 16 16:42:39 MST 2012
Release: Ubuntu quantal (development branch)
Kernel: Linux 3.4.0-2-generic-pae
Unity: unity 5.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 302.07

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver xorg core:
  Installed: 2:1.12.1.901+git20120510+server-1.12-branch.58dfb139-0ubuntu0ricotz

vindsl@Zuul:~$ 
```

---

### Post by pressureman on 2012-05-17
This is taking a looong time to land in the official repos... I'm hoping it's going to fix the problems I have with 3.4.0-1.3 (hangs on boot about 90% of the time, just before lightdm screen should appear).

---

### Post by VinDSL on 2012-05-17
> **pressureman said:**
> This is taking a looong time to land in the official repos... I'm hoping it's going to fix the problems I have with 3.4.0-1.3 (hangs on boot about 90% of the time, just before lightdm screen should appear).
Working fine here...  ;)

```
vindsl@Zuul:~$ dmesg

<SNIP>

[   23.058933] type=1400 audit(1337282483.825:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=858 comm="apparmor_parser"
[   23.066593] type=1400 audit(1337282483.833:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=858 comm="apparmor_parser"
[   23.067015] type=1400 audit(1337282483.833:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
**[COLOR="DarkRed"][   23.068501] type=1400 audit(1337282483.837:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=857 comm="apparmor_parser"[/COLOR]**
[   23.100446] type=1400 audit(1337282483.869:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=864 comm="apparmor_parser"
[   23.911032] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   23.911058] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   23.911113] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   26.152221] net eth0: Setting full-duplex based on MII#1 link partner capability of 45e1
[   33.392009] eth0: no IPv6 routers present
vindsl@Zuul:~$ 
```

---

### Post by pressureman on 2012-05-17
Running 3.4.0-2.6 now... booted fine. Hopefully it's going to stay that way.

---

### Post by VinDSL on 2012-05-17
> **pressureman said:**
> Running 3.4.0-2.6 now... booted fine. Hopefully it's going to stay that way.
Heh!  I'm running 3.3.0-6.dmz.1-liquorix-686 right now...

Surprisingly, Plymouth is working too!  :D


[[IMG]http://vindsl.com/images/vindsl-desktop-17-may-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-17-may-2012-1.png")

```
vindsl@Zuul:~$ uname -a
Linux Zuul 3.3.0-6.dmz.1-liquorix-686 #1 ZEN SMP PREEMPT Mon May 14 04:24:53 UTC 2012 i686 i686 i686 GNU/Linux

```

```
vindsl@Zuul:~$ echo && echo -n "Date/Time: " && date && echo -n "Release: " && lsb_release -sd && echo -n "Kernel: " || cat /etc/*release && uname -s -r && echo -n "Unity: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo &&  dpkg -s mesa-utils && echo || echo && echo "Xserver xorg core:" && apt-cache policy xserver-xorg-core | grep Installed && echo
f && echo || echo &&  dpkg -s mesa-utils && echo || echo && echo "Xserver xorg cDate/Time: Thu May 17 15:48:20 MST 2012
Release: Ubuntu quantal (development branch)
Kernel: Linux 3.3.0-6.dmz.1-liquorix-686
Unity: unity 5.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 302.07

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver xorg core:
  Installed: 2:1.12.1.901+git20120510+server-1.12-branch.58dfb139-0ubuntu0ricotz

vindsl@Zuul:~$ 
```

---

### Post by pressureman on 2012-05-18
I spoke too soon. Two out of three boots hung before lightdm appeared. Reverting to 3.2 kernel again.

---

### Post by 3vi1 on 2012-05-18
No joy here.  My main system (i980x CPU, Intel DX58SO MB) hates both 3.4 kernels so far.

```
May 13 08:31:43 saturn kernel: [    7.740175] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
May 13 08:31:43 saturn kernel: [    7.742924] BUG: unable to handle kernel NULL pointer dereference at           (null)
May 13 08:31:43 saturn kernel: [    7.742927] IP: [<ffffffffa10cd1ae>] rpc_pipefs_event+0xae/0x220 [nfs]
May 13 08:31:43 saturn kernel: [    7.742939] PGD 318601067 PUD 318504067 PMD 0 
May 13 08:31:43 saturn kernel: [    7.742941] Oops: 0000 [#1] SMP 
May 13 08:31:43 saturn kernel: [    7.742943] CPU 8 
May 13 08:31:43 saturn kernel: [    7.742943] Modules linked in: nfsd binfmt_misc snd_hda_codec_hdmi nfs lockd fscache auth_rpcgss nfs_acl sunrpc asc7621 i2c_i801 lp parport nvidia(PO+) snd_hda_codec_realtek snd_hda_intel(+) mxm_wmi uvcvideo snd_hda_codec videobuf2_core videodev wmi videobuf2_vmalloc coretemp snd_usb_audio videobuf2_memops i7core_edac edac_core snd_seq_midi snd_seq_midi_event snd_pcm snd_seq psmouse snd_hwdep snd_usbmidi_lib snd_page_alloc snd_rawmidi snd_timer snd_seq_device serio_raw snd soundcore joydev mac_hid microcode btrfs zlib_deflate libcrc32c vesafb usbhid hid firewire_ohci firewire_core ghash_clmulni_intel aesni_intel cryptd aes_x86_64 crc_itu_t pata_marvell e1000e usb_storage
```

and later...

```
May 13 08:31:43 saturn kernel: [    8.210490] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 13 08:31:45 saturn kernel: [    9.841397] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
May 13 08:31:45 saturn kernel: [    9.841401] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
May 13 08:31:45 saturn kernel: [    9.842398] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 13 08:31:56 saturn kernel: [   20.560261] eth0: no IPv6 routers present
May 13 08:33:08 saturn kernel: [   96.142204] BUG: soft lockup - CPU#0 stuck for 22s! [mount.nfs:1403]
```

and more...

```
May 13 08:33:08 saturn kernel: [   96.178270] BUG: soft lockup - CPU#3 stuck for 22s! [mount.nfs:1410]
```

and the fun keeps coming...

```
May 13 08:33:42 saturn kernel: [  130.356610] INFO: rcu_sched self-detected stall on CPU { 0}  (t=15000 jiffies)
May 13 08:33:42 saturn kernel: [  130.356613] sending NMI to all CPUs:
May 13 08:33:42 saturn kernel: [  130.356660] NMI backtrace for cpu 0

```

Oddly, it seems to work fine on another system with NFS shares.  :\  So, I'm not sure of the real culprit yet.

---

### Post by fjgaude on 2012-05-18
Quantal is moving along quickly. I'm up to kernel 3.4.0-1 on my Dell mini-10n (gma500):

```
frank@sweetie:~$ echo && echo -n "Date/Time: " && date && echo -n "Release: " && lsb_release -sd && echo -n "Kernel: " || cat /etc/*release && uname -s -r && echo -n "Unity: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo &&  dpkg -s mesa-utils && echo || echo && echo "Xserver xorg core:" && apt-cache policy xserver-xorg-core | grep Installed && echo

Date/Time: Fri May 18 10:09:50 PDT 2012
Release: Ubuntu quantal (development branch)
Kernel: Linux 3.4.0-1-generic-pae
Unity: unity 5.12.0

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver xorg core:
  Installed: 2:1.11.4-0ubuntu11
```

Interestingly, Unity 2, but using:

```
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
```

Even this early there's a way for limited systems to use Unity. Don't understand where VMware fits into the picture? VMware into the kernel but using LLVM as compiler instead of GCC?

---

### Post by effenberg0x0 on 2012-05-18
(Keep in mind I'm not a specialist and actually need to find the time to study more). As far as I could understand: LLVM is capable of creating architecture-optimized code in run-time (not from source code, but from an intermediary state object code). So while it will look like a standard module, from the kernel perspective, it is somewhat more dynamic in the way it will execute the calls.

About VMware: Gallium3D was a project of Tungsten Graphics. VMware acquired Tungsten planning to turn Gallium3D into a solution for 3D acceleration in its Virtual Machines (VMs can't can't have hardware accelerated graphics*). Later it transferred it to the Mesa project, but apparently is still a contributor.

So, we know software rendering of GL is not new: mesa can do it if you set dri to off in X config. But it can be done better and reach a superior performance with Gallium3D and llvmpipe. So the thing stops being interesting only in the Virtualization scenario and also becomes a viable alternative to render OpenGL in PCs with weak GPUs but reasonably powerful CPUs.

(*) Except for Xen and (probably soon) KVM, which are not working on improved 3D graphics for VMs but instead on VGA PCI-Passthrough. Xen already did it and, in this case, the VGA performs very close to 100% in a virtualized environment (little overhead - it gets dedicated to the guest OS).

Regards,
Effenberg

---

### Post by grahammechanical on 2012-05-19
I have this

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

No Nvidia driver. No VM.  Nouveau is 1:0.0.16

Regards.

---

### Post by fjgaude on 2012-05-19
Well, you provide more than expected, Effenberg. Thank you for clearing somethings up for me. Cool!

---

### Post by VinDSL on 2012-05-19
> **fjgaude said:**
> Well, you provide more than expected, Effenberg. Thank you for clearing somethings up for me. Cool!
Wake me up, when they fix these forums...  LoL!  :D

OMG!!!  This is painful!  30 seconds to refresh/draw the screen.

Ahem!  Just saying...

---

### Post by fjgaude on 2012-05-19
> **VinDSL said:**
> Wake me up, when they fix these forums...  LoL!  :D

OMG!!!  This is painful!  30 seconds to refresh/draw the screen.

Ahem!  Just saying...

That long... I don't seem to have any issues with Forum speed.

---

### Post by dnewkirk on 2012-05-19
> **VinDSL said:**
> Wake me up, when they fix these forums...  LoL!  :D

OMG!!!  This is painful!  30 seconds to refresh/draw the screen.

Ahem!  Just saying...

If you want it to clear the screen faster, you can always turn it upside down and shake it :D. Drawing the screen never was easy...

---

### Post by VinDSL on 2012-05-19
Massive packet loss, here...


[INDENT][[IMG]http://vindsl.com/images/vindsl-packet-loss-19-may-2012(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-packet-loss-19-may-2012.png")[/INDENT]


All other web sites are working fine.

Maybe it's the "radiation orange" theme.  LoL!  :D

---

### Post by fjgaude on 2012-05-19
My ping without retries:

```
frank@cutie:~$ ping ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=43 time=147 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=43 time=147 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=43 time=147 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=4 ttl=43 time=148 ms
```

Can't say what your issue is, but Forums works as usual for me.

---

### Post by cariboo on 2012-05-19
The problem has nothing to do with the new theme. I don't see a slow down here, or any packet lose.

---

### Post by VinDSL on 2012-05-20
Problem ain't on *MY* end, boyz!  :D


[INDENT][IMG]http://vindsl.com/images/vindsl-packet-loss-2.png[/IMG][/INDENT]


Oh, well.  This, too, shall pass...  ;)

---

### Post by VinDSL on 2012-05-20
> **cariboo907 said:**
> The problem has nothing to do with the new theme.
Yeah, I know.  That was a logical absurdity, e.g. a joke...

Seriously, it looks like you guys got a bad switch in your NOC, or a flaky edge router.  ;)

---

### Post by jerrylamos on 2012-05-20
Well, ubuntu kernels since Narwhal, Ocelot, Precise, Quetzal fail on IBM Thinkpad T40 wireless:
AIRONET Wireless Communications Cisco Aironet Wireless 802.11b 

ubuntu kernels connect, a few seconds later disconnect, connect, a few seconds later disconnect, repeat. I can turn it off by manually disconnecting in the network applet.  Every time I boot.  Boring.

I've written bugs on each release to no effect.  I've tried some of the forum suggestions but haven't had any luck.

Simplest -fast!- solution for me is Lynx which I'm using here now.  I'm testing quetzal on other pc's.  Another solution is to plug in a pc card Realtek wireless, which works fine, but I still get quetzal kernel messages about the Aironet.  On every boot.  I usually have the Realtek in another notebook that doesn't have any built in wireless.

Jerry

---

### Post by VinDSL on 2012-05-20
> **VinDSL said:**
> This, too, shall pass...  ;)
w00t!  The forums (and the repos) are flying like the wind, now.  :guitar:

Looks like they switched to Level3 network. 0% packet loss!

Got a slight amount of packet loss <= 1% on my ISP's border router, between Los Angeles & Phoenix... but, that's my problem.

Anyway, working great now!

Okay, back on topic... sorry for the diversion!  :)

---

### Post by pressureman on 2012-05-21
> **3vi1 said:**
> No joy here.  My main system (i980x CPU, Intel DX58SO MB) hates both 3.4 kernels so far.

```
May 13 08:31:43 saturn kernel: [    7.740175] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
May 13 08:31:43 saturn kernel: [    7.742924] BUG: unable to handle kernel NULL pointer dereference at           (null)
May 13 08:31:43 saturn kernel: [    7.742927] IP: [<ffffffffa10cd1ae>] rpc_pipefs_event+0xae/0x220 [nfs]
May 13 08:31:43 saturn kernel: [    7.742939] PGD 318601067 PUD 318504067 PMD 0 
May 13 08:31:43 saturn kernel: [    7.742941] Oops: 0000 [#1] SMP 
May 13 08:31:43 saturn kernel: [    7.742943] CPU 8 
May 13 08:31:43 saturn kernel: [    7.742943] Modules linked in: nfsd binfmt_misc snd_hda_codec_hdmi nfs lockd fscache auth_rpcgss nfs_acl sunrpc asc7621 i2c_i801 lp parport nvidia(PO+) snd_hda_codec_realtek snd_hda_intel(+) mxm_wmi uvcvideo snd_hda_codec videobuf2_core videodev wmi videobuf2_vmalloc coretemp snd_usb_audio videobuf2_memops i7core_edac edac_core snd_seq_midi snd_seq_midi_event snd_pcm snd_seq psmouse snd_hwdep snd_usbmidi_lib snd_page_alloc snd_rawmidi snd_timer snd_seq_device serio_raw snd soundcore joydev mac_hid microcode btrfs zlib_deflate libcrc32c vesafb usbhid hid firewire_ohci firewire_core ghash_clmulni_intel aesni_intel cryptd aes_x86_64 crc_itu_t pata_marvell e1000e usb_storage
```



I got my first usable kernel oops just now. Instead of my notebook simply hanging, it switched back to a framebuf console showing the kernel oops. I got the same "unable to handle kernel NULL pointer dereference" bug, and the process at the time was lightdm. This sorta makes sense, since the symptoms are that it usually hangs just as Plymouth hands over to LightDM.

---

