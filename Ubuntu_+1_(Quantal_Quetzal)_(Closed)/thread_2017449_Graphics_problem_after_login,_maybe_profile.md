---
title: "Graphics problem after login, maybe profile?"
date: 2012-07-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Rallg on 2012-07-05
QQ 32-bit PC, standard Unity desktop, netbook (1024x600), up to date as of yesterday:

At the login screen, all appears normal. But after logging in, the desktop has problems. At top, the menu bar disappears. At left, the Unity launcher disappears. If I manage to open a window, it is not properly decorated (no bar at top, other decorations missing at periphery). This behavior is repeatable. If I check the Appearance settings, it shows 1024x600 as expected.

If I change to failsafe graphics mode, then all looks OK (except that the pixel dimensions are different, but that is expected).

Since the problem arises only after I login, I conclude that there is something in my /etc/profile or other initialization file, which is somehow incompatible with recent updates.

Has anyone else seen this behavior?

---

### Post by dino99 on 2012-07-05
maybe you're right, but have you switched to an other theme into Appearance settings to know if it is related ? or do you have some ppa installed ?

the last config "reset" is to rename (or delete if you does not care): .gconf , .config , .gnome2 & .local folders. They will be cleanly recreated after logout/in, but you then need to re-custom as you like.

---

### Post by Rallg on 2012-07-05
@dino99: I didn't try another theme (seems unlikely), but I did try a Guest session, and had the same problem. Presumably Guest doesn't read the same /etc/profile as my normal username, so that can't be the problem.

I'll try cleaning and re-creating some files, as you suggested.

But I've noticed here on the forum, that others are having problems with Nautilus. These things may be related. It may be that whatever problems appear with Nautilus are made worse with 1024x600 resolution. Once the problem appears, changing to 800x600 doesn't fix it. But if I login to failsafe graphics, the situation is fixed.

My primary use of QQ is for some graphics programs that cannot be compiled in PP, but can be compiled in QQ. These programs are not the problem (they are in /opt, which is not in my PATH). No PPAs. I'm not doing any graphics right now, so I'll wait a week or two to see what happens in the beta testing. I can always update from command line.

---

### Post by dino99 on 2012-07-05
Thats all u+1 fun :lolflag:  the breakages yard  ):P

---

### Post by ventrical on 2012-07-05
> **Rallg said:**
> QQ 32-bit PC, standard Unity desktop, netbook (1024x600), up to date as of yesterday:

At the login screen, all appears normal. But after logging in, the desktop has problems. At top, the menu bar disappears. At left, the Unity launcher disappears. If I manage to open a window, it is not properly decorated (no bar at top, other decorations missing at periphery). This behavior is repeatable. If I check the Appearance settings, it shows 1024x600 as expected.

If I change to failsafe graphics mode, then all looks OK (except that the pixel dimensions are different, but that is expected).

Since the problem arises only after I login, I conclude that there is something in my /etc/profile or other initialization file, which is somehow incompatible with recent updates.

Has anyone else seen this behavior?

"standard unity desktop"

Do you mean Unity 2D? or 3D

What is your graphics adapter?

---

### Post by Rallg on 2012-07-05
1. The problem is in default Ubuntu, which I guess is 3D. Understand that the problem appeared recently, presumably due to an update.

2. Logging in with 2D: no problem. Slightly different visual effects, of course. But all functional.

3. After re-naming .gconf .config .gnome2 and .local: Does not fix 3D.

4. Graphics adapter is generic "Intel Graphics" as usual. No proprietary drivers.

I'll remain in 2D for awhile. Sooner or later there will be an update that fixes the problem. Can't mark it "solved" yet.

---

### Post by ventrical on 2012-07-05
I have one of my machines which is a Dell Optiplex GX27G with Intel Chipset (graphics) but that graphics adapter is not capable of Unity 3D. My Dell Dimension 3100 ,on the otherhand, works just great.

Some of the Intell graphics cards were obosleted during the Oneric phase of Unity.

However, I can run Kubuntu and comiz, rotating cube . etc .. works just great. Unity 3D is looking for a lot of resources. At least 256Mb of Dram on the adapter card or AGP card. For the most part, 512 is best but Iv'e seen Unity 3D work with 128MB.

Could you run:

lspci

from terminal and post those results here.

---

### Post by Rallg on 2012-07-05
Understand that until recently, 3D ran just fine. I have 2G RAM and plenty of room on the hard drive. NOTE: I am using a WUBI installation to drive D: rather than a fully-dedicated partition; but I don't think that's the problem (seeing as how 3D worked until now).

Here is my lspci, made while I was in 2D (not 3D):

00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by ventrical on 2012-07-05
Here is a link you might find interesting.

[http://askubuntu.com/questions/122339/how-to-enable-unity-3d-support-in-12-04-using-open-source-drivers-for-radeonhd-c](http://askubuntu.com/questions/122339/how-to-enable-unity-3d-support-in-12-04-using-open-source-drivers-for-radeonhd-c)

Here is  a paste:

        I have the same result with Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03) – [int_ua]("http://askubuntu.com/users/20275/int-ua") [May 2 at 17:42]("http://askubuntu.com/questions/122339/how-to-enable-unity-3d-support-in-12-04-using-open-source-drivers-for-radeonhd-c#comment155265_122339")
                                
        FYI: sudo apt-get install xserver-xorg-video-intel fixed my problem. – [int_ua]("http://askubuntu.com/users/20275/int-ua") [May 2 at 18:20]("http://askubuntu.com/questions/122339/how-to-enable-unity-3d-support-in-12-04-using-open-source-drivers-for-radeonhd-c#comment155321_122339")

---

### Post by Rallg on 2012-07-05
xserver-xorg-video-intel is already installed, latest version. I do not know if there was a recent change to that package.

Anyway, I'm getting used to 2D. If it has a little less eye-candy than 3D, I can live with that. Otherwise, it seems to work the same as 3D (or whatever was default) did before.

Such is beta testing. Incidentally, the reason I'm in QQ is so that I could compile Gimp 2.9 (development version, with 16-bit graphics support) without going to backports in PP. But that has nothing to do with this thread (gimp-2.9 is in /opt and is not loaded).

---

### Post by Alex Harrowell on 2012-07-11
I've got this one. Got QQ updates (presumably to Alpha 2 status) last week. Eventually got around to rebooting yesterday.

No Launcher, toolbar, or window management. Everything works up to the point of logging in or launching a guest session. Trying to relaunch Unity from the command line gives you a message that unity-panel-services isn't running (you can't start it, it cnfs.)

Apparently related issue: the first time it happened, I also got a Nautilus crash message telling me as an UnreportableReason to update nautilus, libcups2, libgtk-3-0, libgail3, libgtk-3-common. A "trap int3" from nautilus was in syslog.

Upgrading those packages got rid of the nautilus crash, but nothing else.

After a reboot or two I got a crash message from compiz which seems to be this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1020075](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1020075)

I tried upgrading compiz, removing a bunch of cached stuff (although not all of gconf , .config , .gnome2 & .local). No dice.

Machine: ThinkPad X200S, 8GB RAM, Intel 945.

---

### Post by Alex Harrowell on 2012-07-11
And I can report that the workaround works. rm -rf the following

./.gconf/ ./.gnome2/ ./.local/ ./config/

and reboot.

---

