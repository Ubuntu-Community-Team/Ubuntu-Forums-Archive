---
title: "video drivers on vmware?"
date: 2012-02-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prusswan on 2012-02-09
Anyone running this on vmware with no obvious issues? I find Unity 3D to be extremely choppy (with artifacts?), just wondering if this could be a driver issue.

---

### Post by prusswan on 2012-02-09
some quick questions:

is 3d acceleration used in Gnome Classic (gnome-session-fallback) at all? any good way to test 3d graphics capability? I am only seeing glitches in Unity 3D session so that is a suspected cause, and not too surprising since I'm running on Vmware Workstation 7.1.5 which does not even support 11.04 officially

---

### Post by drmrgd on 2012-02-09
I'm using VMware Player on my work computer, and I've not been able to run Unity 3D or Gnome3 under that environment.  Each time I try, I get sent back to fallback mode (which is Gnome Classic).  So, I think that it may not be possible currently, although if you hack away at it long enough, you might find a solution.  The one problem with this computer is that I don't have admin rights on the host side, and so installing newer versions of VMware player or other patches is really difficult.

---

### Post by prusswan on 2012-02-09
hmm, what's the difference between Gnome3 and Gnome Classic (which I understand to be the fallback option, and also some form of Gnome3)?

---

### Post by drmrgd on 2012-02-09
Might have to have a Gnome expert correct me here as I run KDE usually.  But, if I understand correctly, Gnome3 is the latest 3D version of Gnome.

---

### Post by MoreOrLess on 2012-02-09
> **prusswan said:**
> hmm, what's the difference between Gnome3 and Gnome Classic (which I understand to be the fallback option, and also some form of Gnome3)?
Gnome (3) fallback (which Ubuntu confusingly calls Gnome Classic after using the same name for gnome2 in older Ubuntu releases) uses the old metacity window manager, which doesn't require 3D hardware acceleration.

VMWare recently made major improvements to 3D acceleration, but it requires VMWare Workstation 8.0.2 [http://www.phoronix.com/scan.php?page=news_item&px=MTA0MzE](http://www.phoronix.com/scan.php?page=news_item&px=MTA0MzE)

---

### Post by mebomechanicno1 on 2012-02-09
> **MoreOrLess said:**
> Gnome (3) fallback (which Ubuntu confusingly calls Gnome Classic after using the same name for gnome2 in older Ubuntu releases) uses the old metacity window manager, which doesn't require 3D hardware acceleration.
 
VMWare recently made major improvements to 3D acceleration, but it requires VMWare Workstation 8.0.2 [http://www.phoronix.com/scan.php?page=news_item&px=MTA0MzE](http://www.phoronix.com/scan.php?page=news_item&px=MTA0MzE)
 
Useful article, thanks.

---

### Post by prusswan on 2012-02-09
> **MoreOrLess said:**
> Gnome (3) fallback (which Ubuntu confusingly calls Gnome Classic after using the same name for gnome2 in older Ubuntu releases) uses the old metacity window manager, which doesn't require 3D hardware acceleration.

VMWare recently made major improvements to 3D acceleration, but it requires VMWare Workstation 8.0.2 [http://www.phoronix.com/scan.php?page=news_item&px=MTA0MzE](http://www.phoronix.com/scan.php?page=news_item&px=MTA0MzE)

so it does seem to be a 3d hardware issue, thanks for the info

---

### Post by effenberg0x0 on 2012-02-09
You can try [this]("http://cgit.freedesktop.org/mesa/mesa/commit/?id=27915708ed4519cc5606e81fb789e8427501f355"), which translates into this:

cd && mkdir vmware && sudo apt-get install git-core automake libtool libpthread-stubs0-dev xserver-xorg-dev x11proto-xinerama-dev && sudo apt-get build-dep libgl1-mesa-dri libxcb-glx0-dev && export TOP=$PWD && git clone git://anongit.freedesktop.org/git/mesa/mesa && git clone git://anongit.freedesktop.org/git/mesa/vmwgfx && git clone git://anongit.freedesktop.org/git/mesa/drm && git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-vmware && cd $TOP/drm && ./autogen.sh --prefix=/usr --enable-vmwgfx-experimental-api --libdir=/usr/lib64 && make && sudo make install && cd $TOP/mesa && ./autogen.sh --prefix=/usr --libdir=/usr/lib64 --with-gallium-drivers=svga --with-dri-drivers= --enable-xa && make && sudo make install && cd $TOP/xf86-video-vmware && ./autogen.sh --prefix=/usr --libdir=/usr/lib64 && make && sudo make install && sudo rm /lib/modules/`uname -r`/kernel/drivers/gpu/drm/vmwgfx.ko* && cd $TOP/vmwgfx && make && sudo make install && sudo cp 00-vmwgfx.rules /etc/udev/rules.d && sudo depmod -a && sudo modprobe vmwgfx

I'm still studying it, as I can't really explain why it works sometimes and not others.
I have tested a couple machines with mixed results. No Unity yet here (GLX_EXT). 

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-02-09
Actually I was wrong and the thing is a beauty. See the screenshots. It's self explanatory. Happy Happy Joy Joy!!

See Gallium3D there:
[ATTACH]212404[/ATTACH]

That's enough frames for a VM... I am running on "ondemand" 800MHz, 2cores at 80% cap with 256 Virt. VGA RAM and 2GB for the VM.
[ATTACH]212405[/ATTACH]

And unity_support_test too:
[ATTACH]212406[/ATTACH]

So, no need for workstation paid license and capability for OpenGL GLX_EXT_texture_from_bitmap working. Full Compiz/Unity :)


Regards,
Effenberg

---

### Post by prusswan on 2012-02-10
Actually, the point of the workstation is really for the use of snapshots. Not that I am expecting a lot of 3D functionality on a VM, but is there some kind of dxdiag or 3DMark for ubuntu?

---

### Post by dcstar on 2012-02-12
> **prusswan said:**
> Anyone running this on vmware with no obvious issues? I find Unity 3D to be extremely choppy (with artifacts?), just wondering if this could be a driver issue.

On VMware Player 4.0.1 the 12.04 graphics are rubbish until you install VMware Tools in the VM (which installs the VMware video drivers) - then they seem to work correctly.

Until 12.04 is officially released then VMware will (eventually) update their products to officially support it, so there are no guarantees until that occurs. Best to run 12.04 without effects until then.

---

