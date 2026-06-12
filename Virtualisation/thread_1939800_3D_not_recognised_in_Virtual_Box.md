---
title: "3D not recognised in Virtual Box"
date: 2012-03-12
forum: Virtualisation
---

### Post by Paddy Landau on 2012-03-12
My set-up:

[LIST]
[*]Host: Ubuntu 11.04 (fully updated), with standard Unity 3D.
[*]Virtual Box: latest version [noparse](4.1.8).[/noparse]
[*]Guest: Ubuntu 12.04 Beta (fully updated) with 3D enabled, and Guest Additions installed.
[/LIST]
The problem is that the guest 12.04 does not recognise 3D, so I cannot run 3D with 12.04. My host 11.04 runs 3D without any problem.

Here are the results from three commands in the guest:
```
**echo ${DESKTOP_SESSION}**
ubuntu-2d
``````
**/usr/lib/nux/unity_support_test -p**
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.1

Not software rendered:    [COLOR=Red]no[/COLOR]
Not blacklisted:          [COLOR=SeaGreen]yes[/COLOR]
GLX fbconfig:             [COLOR=SeaGreen]yes[/COLOR]
GLX texture from pixmap:  [COLOR=SeaGreen]yes[/COLOR]
GL npot or rect textures: [COLOR=SeaGreen]yes[/COLOR]
GL vertex program:        [COLOR=SeaGreen]yes[/COLOR]
GL fragment program:      [COLOR=SeaGreen]yes[/COLOR]
GL vertex buffer object:  [COLOR=SeaGreen]yes[/COLOR]
GL framebuffer object:    [COLOR=SeaGreen]yes[/COLOR]
GL version is 1.4+:       [COLOR=SeaGreen]yes[/COLOR]

Unity 3D supported:       [COLOR=Red]no[/COLOR]
``````
**sudo lshw -C display**
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=64
       resources: memory:e0000000-e3ffffff
```Any idea how I can get the guest to recognise 3D?

---

### Post by Paddy Landau on 2012-03-13
Bump?

---

### Post by cpatrick08 on 2012-03-13
> **Paddy Landau said:**
> My set-up:

[LIST]
[*]Host: Ubuntu 11.04 (fully updated), with standard Unity 3D.
[*]Virtual Box: latest version [noparse](4.1.8).[/noparse]
[*]Guest: Ubuntu 12.04 Beta (fully updated) with 3D enabled, and Guest Additions installed.
[/LIST]
The problem is that the guest 12.04 does not recognise 3D, so I cannot run 3D with 12.04. My host 11.04 runs 3D without any problem.

Here are the results from three commands in the guest:
```
**echo ${DESKTOP_SESSION}**
ubuntu-2d
``````
**/usr/lib/nux/unity_support_test -p**
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.1

Not software rendered:    [COLOR=Red]no[/COLOR]
Not blacklisted:          [COLOR=SeaGreen]yes[/COLOR]
GLX fbconfig:             [COLOR=SeaGreen]yes[/COLOR]
GLX texture from pixmap:  [COLOR=SeaGreen]yes[/COLOR]
GL npot or rect textures: [COLOR=SeaGreen]yes[/COLOR]
GL vertex program:        [COLOR=SeaGreen]yes[/COLOR]
GL fragment program:      [COLOR=SeaGreen]yes[/COLOR]
GL vertex buffer object:  [COLOR=SeaGreen]yes[/COLOR]
GL framebuffer object:    [COLOR=SeaGreen]yes[/COLOR]
GL version is 1.4+:       [COLOR=SeaGreen]yes[/COLOR]

Unity 3D supported:       [COLOR=Red]no[/COLOR]
``````
**sudo lshw -C display**
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=64
       resources: memory:e0000000-e3ffffff
```Any idea how I can get the guest to recognise 3D?
try giving it more video memory and see if that works

---

### Post by Paddy Landau on 2012-03-13
> **cpatrick08 said:**
> try giving it more video memory and see if that works
I gave it the maximum, 128Mb, but it made no difference. :(

---

### Post by cpatrick08 on 2012-03-13
> **Paddy Landau said:**
> I gave it the maximum, 128Mb, but it made no difference. :(
try the steps at [http://www.sysprobs.com/install-virtualbox-guest-additions-on-ubuntu-11-10-2d-and-3d-unity-issues](http://www.sysprobs.com/install-virtualbox-guest-additions-on-ubuntu-11-10-2d-and-3d-unity-issues) and see if it works for you

---

### Post by Paddy Landau on 2012-03-14
> **cpatrick08 said:**
> try the steps at [http://www.sysprobs.com/install-virtualbox-guest-additions-on-ubuntu-11-10-2d-and-3d-unity-issues](http://www.sysprobs.com/install-virtualbox-guest-additions-on-ubuntu-11-10-2d-and-3d-unity-issues) and see if it works for you
Thank you.

Before I could try your suggestion, Virtual Box came out with a new version, 4.1.10.

I upgraded Virtual Box; installed the lasted Guest Additions; and after a couple of reboots (including the latest updates for 12.04), it works now.

So, it seems to have been a problem with Virtual Box.

---

### Post by cpatrick08 on 2012-03-14
> **Paddy Landau said:**
> Thank you.

Before I could try your suggestion, Virtual Box came out with a new version, 4.1.10.

I upgraded Virtual Box; installed the lasted Guest Additions; and after a couple of reboots (including the latest updates for 12.04), it works now.

So, it seems to have been a problem with Virtual Box.
glad your problem is fixed you should mark your problem as solved

---

### Post by Paddy Landau on 2012-03-14
> **cpatrick08 said:**
> ... you should mark your problem as solved
I already did :)

---

### Post by andrew.46 on 2012-03-16
I hope the latest also fixes the lack of 3d support I have experienced with VirtualBox... [Changelog for 4.1.10]("https://www.virtualbox.org/wiki/Changelog") looks promising.

---

