---
title: "installation hosed with latest updates"
date: 2012-02-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-02-26
This morning I booted into my 12.04 test install for the first time in a few days, and update manager reported a large number of updates - new kernel, xorg, etc, etc. After installing the updates and restarting, I get the greeter screen ok, but after login I just have a blank black screen with a mouse pointer. If I move the mouse pointer over to the left-hand edge of the screen, where the Unity bar should appear, I get a vertical bar of green speckles on the black background, but nothing discernible at all.

Using Ctrl+Alt+F1 to try to get to a text login doesn't do anything. All that happens is that the mouse pointer disappears and the screen remains black, and at that point the only recourse is to power cycle the machine.

Prior to applying these updates, this 12.04 installation was working pretty well.

---

### Post by exploder on 2012-02-26
You might try grabbing a daily build and see what happens.

---

### Post by effenberg0x0 on 2012-02-26
This is equal to "My car has a defect. What is the solution?". 

Some details could make it possible for us to at least try to provide some help. 

Hardware: Laptop or desktop, VGA Card Brand/Model, etc.
Software: Fresh Install from Alpha? Beta? Upgraded from Oneiric? Running non-stock software from PPAs? Which VGA Driver?

Effenberg

---

### Post by alphacrucis2 on 2012-02-26
> **Nick Payne said:**
> This morning I booted into my 12.04 test install for the first time in a few days, and update manager reported a large number of updates - new kernel, xorg, etc, etc. After installing the updates and restarting, I get the greeter screen ok, but after login I just have a blank black screen with a mouse pointer. If I move the mouse pointer over to the left-hand edge of the screen, where the Unity bar should appear, I get a vertical bar of green speckles on the black background, but nothing discernible at all.

Using Ctrl+Alt+F1 to try to get to a text login doesn't do anything. All that happens is that the mouse pointer disappears and the screen remains black, and at that point the only recourse is to power cycle the machine.

Prior to applying these updates, this 12.04 installation was working pretty well.


Late last week a partial upgrade offering to remove most of the desktop packages was showing up due to some unresolved dependencies. This has now sorted itself but maybe you did a dreaded partial upgrade without reviewing what it was going to do.

---

### Post by Nick Payne on 2012-02-26
> Late last week a partial upgrade offering to remove most of the desktop packages was showing up due to some unresolved dependencies. This has now sorted itself but maybe you did a dreaded partial upgrade

No, I booted again and did Ctrl+Alt+F1 at the login screen to perform a text login. Running sudo apt-get update / upgrade showed nothing amiss and no updates to install. I then Ctrl+Alt+F7 and tried a GUI login, which this time seemed to work ok, however, after a couple of minutes the machine froze for a couple of seconds and the screen then went completely black except for the mouse pointer, with the same behaviour as before. However, this time I was able to Ctrl+Alt+F1 back to the text screen, and found the following messages cycling up the screen (this is just a subset of what is in syslog):
```
Feb 27 10:43:14 1204Test kernel: [  205.761219] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP_MP - TP0: Unhandled ustatus 0x00020000
Feb 27 10:43:14 1204Test kernel: [  205.761227] [drm] nouveau 0000:02:00.0: PGRAPH_TRAP_MP_EXEC - TP 1 MP 0: INVALID_OPCODE at 07fe00 warp 4, opcode 00f0c9de 00f1cadf
Feb 27 10:43:14 1204Test kernel: [  205.761239] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP
Feb 27 10:43:14 1204Test kernel: [  205.761242] [drm] nouveau 0000:02:00.0: PGRAPH - ch 4 (0x0003450000) subc 5 class 0x8297 mthd 0x0f04 data 0x00000000
Feb 27 10:43:14 1204Test kernel: [  205.761252] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP_MP - TP0: Unhandled ustatus 0x00020000
Feb 27 10:43:14 1204Test kernel: [  205.761256] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP_MP - TP1: Unhandled ustatus 0x00020000
Feb 27 10:43:14 1204Test kernel: [  205.761263] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP
Feb 27 10:43:14 1204Test kernel: [  205.761267] [drm] nouveau 0000:02:00.0: PGRAPH - ch 4 (0x0003450000) subc 5 class 0x8297 mthd 0x1b0c data 0x1000f010
Feb 27 10:43:22 1204Test kernel: [  213.128724] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:24 1204Test kernel: [  215.128566] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:29 1204Test kernel: [  220.130226] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:31 1204Test kernel: [  222.130280] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:31 1204Test kernel: [  222.717619] [drm] nouveau 0000:02:00.0: GPU lockup - switching to software fbcon
Feb 27 10:43:33 1204Test kernel: [  224.722106] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:35 1204Test kernel: [  226.723166] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:37 1204Test kernel: [  228.724255] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000

```
The machine is an ASUS P6T mobo with a 920 i7 CPU, 12Gb RAM, nVidia GTS250 video card, and 12.04 was a fresh install from precise-desktop-amd64.iso downloaded on 17 Feb, and updated a couple of times since with apt-get update / upgrade. The only PPAs are those for Ubuntu Tweak and Google Chrome. Video driver is nouveau - see log output above.

---

### Post by effenberg0x0 on 2012-02-26
> **Nick Payne said:**
> No, I booted again and did Ctrl+Alt+F1 at the login screen to perform a text login. Running sudo apt-get update / upgrade showed nothing amiss and no updates to install. I then Ctrl+Alt+F7 and tried a GUI login, which this time seemed to work ok, however, after a couple of minutes the machine froze for a couple of seconds and the screen then went completely black except for the mouse pointer, with the same behaviour as before. However, this time I was able to Ctrl+Alt+F1 back to the text screen, and found the following messages cycling up the screen (this is just a subset of what is in syslog):
```
Feb 27 10:43:14 1204Test kernel: [  205.761219] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP_MP - TP0: Unhandled ustatus 0x00020000
Feb 27 10:43:14 1204Test kernel: [  205.761227] [drm] nouveau 0000:02:00.0: PGRAPH_TRAP_MP_EXEC - TP 1 MP 0: INVALID_OPCODE at 07fe00 warp 4, opcode 00f0c9de 00f1cadf
Feb 27 10:43:14 1204Test kernel: [  205.761239] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP
Feb 27 10:43:14 1204Test kernel: [  205.761242] [drm] nouveau 0000:02:00.0: PGRAPH - ch 4 (0x0003450000) subc 5 class 0x8297 mthd 0x0f04 data 0x00000000
Feb 27 10:43:14 1204Test kernel: [  205.761252] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP_MP - TP0: Unhandled ustatus 0x00020000
Feb 27 10:43:14 1204Test kernel: [  205.761256] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP_MP - TP1: Unhandled ustatus 0x00020000
Feb 27 10:43:14 1204Test kernel: [  205.761263] [drm] nouveau 0000:02:00.0: PGRAPH - TRAP
Feb 27 10:43:14 1204Test kernel: [  205.761267] [drm] nouveau 0000:02:00.0: PGRAPH - ch 4 (0x0003450000) subc 5 class 0x8297 mthd 0x1b0c data 0x1000f010
Feb 27 10:43:22 1204Test kernel: [  213.128724] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:24 1204Test kernel: [  215.128566] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:29 1204Test kernel: [  220.130226] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:31 1204Test kernel: [  222.130280] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:31 1204Test kernel: [  222.717619] [drm] nouveau 0000:02:00.0: GPU lockup - switching to software fbcon
Feb 27 10:43:33 1204Test kernel: [  224.722106] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:35 1204Test kernel: [  226.723166] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000
Feb 27 10:43:37 1204Test kernel: [  228.724255] [drm] nouveau 0000:02:00.0: PGRAPH TLB flush idle timeout fail: 0x01900403 0x00000008 0x00005028 0x00200000

```The machine is an ASUS P6T mobo with a 920 i7 CPU, 12Gb RAM, nVidia GTS250 video card, and 12.04 was a fresh install from precise-desktop-amd64.iso downloaded on 17 Feb, and updated a couple of times since with apt-get update / upgrade. The only PPAs are those for Ubuntu Tweak and Google Chrome. Video driver is nouveau - see log output above.

Ok, you're using nouveau. Maybe you could try to reinstall it on the new kernel with...
```
sudo apt-get install --reinstall xserver-xorg-video-nouveau
```...or if that doesn't work, try to see if there's a new nouveau build from xorg-edgers:
```
sudo add-apt-repository ppa:xorg-edgers/nouveau 
sudo aptitude update && sudo aptitude install xserver-xorg-video-nouveau
```Regards,
Effenberg

---

### Post by P-I H on 2012-02-27
I updated yesterday. Compiz crashed after the update and there was only the purple background. According to Synaptic nothing should be removed, so I did not expect any problems with the update.

However the Ubuntu 2D login is working OK with Nvidia current.
When in Ubuntu 2D I also uninstalled Nvidia current, rebooted and installed Nvidia current with Jockey. This did not help.

I have also a Geforce GTS250 card and Noveau doesn't work that well with this card as the used resolution is wrong.

---

### Post by lucazade on 2012-02-27
> **P-I H said:**
> 
I have also a Geforce GTS250 card and Noveau doesn't work that well with this card as the used resolution is wrong.

Nouveau works well with the GTS250, I don't have any problem with resolutions or anything.

---

