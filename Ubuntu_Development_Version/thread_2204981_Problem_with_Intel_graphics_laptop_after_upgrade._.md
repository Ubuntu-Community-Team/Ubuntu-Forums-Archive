---
title: "Problem with Intel graphics laptop after upgrade. No login screen &amp; low graphics mode"
date: 2014-02-11
forum: Ubuntu Development Version
---

### Post by philinux on 2014-02-11
Upgraded this acer 1410 again and got some trouble. This is fully up to date by the way.

No login screen so tried recovery. Resumed normal boot. Got low graphucs mode but no mouse to choose option. 

Using tty1 can login then using startx get a desktop. Indicator applet stuff is missing.

Any advice appreciated. Cheers.

```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.0.1

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
```

---

### Post by ajgreeny on 2014-02-11
I don't know if my situation is similar to yours but I have Xubuntu Trusty 64bit as a VM in virtualbox (Oracle PUEL version) and for the past few days, about a week, when I boot it goes to a command line login for a minute or so then automatically starts up lightdm and moves to the GUI login screen.

Just before the command line login appears I get a error message saying** intel-rapl: no valid rapl domain found in package 0** which occurs three times.  Once running the system seems fine and fast, though after many updates to packages it often requires a reinstall of the various virtualbox-guest-dkms packages in order to get full screen working properly again.

---

### Post by philinux on 2014-02-11
Booting normally gets a black screen for a while then the purple ubuntu logo screen with the dots etc. Then finally a black screen with static cursor top left. No login screen at all. Total freeze up as cant get a tty either. 

Can get to desktop only through recovery as in first post.

[edit] I'm in the process of installing gdm.

---

### Post by philinux on 2014-02-11
Installed GDM and boots normally to desktop if a bit slow. And wireless now works. All appears normal including resolution.

There was a some errors with regard to modem-manager. Could this be borking lightdm. How to debug?

It seems like lightdm not starting at all.

---

### Post by grahammechanical on 2014-02-11
It is normal to get llvmpipe when running Recovery>Resume. If we can get to a terminal we can run

```
sudo software-properties-gtk
```

and that will load Software and Updates which will allow us to change video drivers. I have found on occasion that although the mouse pointer is missing as well as the app indicators it is still possible to click the usual mouse sensitive areas such as the power/cog. The menu may not appear but 3 imaginary lines down is System Settings. 9 lines down is Restart and 10 lines down is Shutdown.

This is supposed to restart Compiz

```
dconf reset -f /org/compiz/
```

this is supposed to restart Unity

```
setsid unity
```

Things change so I am not so confident that earlier solutions still work. Oh, lightdm should start long before we get to the login screen. 

Regards.

---

### Post by philinux on 2014-02-11
Hi Graham,

I purged lightdm then reinstalled. Result same as post one. GDM works as normal. Posting this from gdm enabled laptop.

It looks like lightdm or other is failing to start early on.  Intead of progress dots under the ubuntu logo finishing with all 5 lit, only 1 or two get lit then crash. No errors onscreen either.

---

### Post by ventrical on 2014-02-11
My Intel SandyBridge is working exceptionally here with lighdm.

 Will check other Intel Graphics basedmachines.

```

        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

---

### Post by philinux on 2014-02-11
The acer 1410 is intel mobile 4 integrated. It will most likely get a clean install in a week or two.

with gdm working 100% it must be an upgrade/lightdm problem.

---

### Post by ventrical on 2014-02-11
Just checked an older Intel graphics. lightdm/logon works just fine.

---

### Post by QDR06VV9 on 2014-02-11
I share Ventrical's luck my Acer 5750 lappy with Intel HD graphics 3000
works a treat.:)
Sorry to hear things got mucked up for you Phillinux, but you needed something to do
Right?:rolleyes:
Another thought probably not related to yours but worth a try [here]("http://ubuntuforums.org/showthread.php?t=2183483&page=2") post #19 The part where it starts
"You might want to try this, if you already haven't."
it has worked great for me and has with stood kernel changes and all upgrades..

Thanks VinDSL.

---

### Post by philinux on 2014-02-12
> **runrickus said:**
> 
Sorry to hear things got mucked up for you Phillinux, but you needed something to do
Right?:rolleyes:


Yep I got bored. Solved this with a clean install from live daily.

---

### Post by QDR06VV9 on 2014-02-12
Had my first hitch in my giddy up LOL
Was doing my regular update & upgrade when I lost my desktop in the middle of the upgrade
went to text mode but I patiently waited for my hard drive indicator light to calm down then did a
<control+alt+F1>  Re login and finally a <startx> Back to my Desktop.;)
After Cold reboot it still held.
```
!193
cat /var/log/Xorg.0.log | grep -i uxa
[    27.892] (**) intel(0): Option "AccelMethod" "uxa"
[    28.034] (II) UXA(0): Driver registered support for the following operations
```

DE Gnome Shell & Cinnamon
```
lightdm --versionThe program 'lightdm' is currently not installed. You can install it by typing:
sudo apt-get install lightdm



```

---

