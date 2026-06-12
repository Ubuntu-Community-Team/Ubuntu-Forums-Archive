---
title: "ubuntu server no gui virtualbox 3d"
date: 2012-05-17
forum: Server Platforms
---

### Post by johnnylocke on 2012-05-17
I have ubuntu 12.10 server with no gui, and i plan to keep it that way. I have a virtualbox running in headless mode. I cannot get virtualbox to recognize my 3d graphics card. Most of the forums that i searched on, people installed the gui to get the 3d graphics drivers running. Is there anyway to install that 3d graphics card so that virtualbox will recognize it without a gui?

Hardware
Shuttle 
sh61r4 
intel h61 chipset.

I think it is a intel hd graphics 3000 but the website doesnt say.

---

### Post by Cheesemill on 2012-05-17
VM's don't ever see or have access to the graphics card on your host machine.

Instead they have a virtual graphics card that is presented to them by the VirtualBox software.
To install the drivers for the virtual graphics card you just need to install the VirtualBox Guest Additions.

---

### Post by CharlesA on 2012-05-17
> **Cheesemill said:**
> VM's don't ever see or have access to the graphics card on your host machine.

Instead they have a virtual graphics card that is presented to them by the VirtualBox software.
To install the drivers for the virtual graphics card you just need to install the VirtualBox Guest Additions.
Pretty much this.

Install the VirtualBox Guest Additions and it has the option of installing a 3D driver, but it is still experimental.

---

### Post by johnnylocke on 2012-05-17
That is now what virtualbox says.

VBoxManage: error: This VM was configured to use 3D acceleration. However, the 3D support of the host is not working properly and the VM cannot be started. To fix this problem, either fix the host 3D support (update the host graphics driver?) or disable 3D acceleration in the VM settings (VERR_NOT_AVAILABLE)
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component Console, interface IConsole, callee

Its like my system has no 3d graphics driver virtualbox can detect.

---

### Post by CharlesA on 2012-05-17
Question - why do you want to have 3d acceleration installed on a VM?

---

### Post by johnnylocke on 2012-05-17
Customer who i sell cloud comps to wants to play minecraft on a ipad.

Also forgot to mention. I have guest additions installed also with the extension pack.

---

### Post by CharlesA on 2012-05-17
> **johnnylocke said:**
> Customer who i sell cloud comps to wants to play minecraft on a ipad.

Also forgot to mention. I have guest additions installed also with the extension pack.
It would be easier just to use OnLive to do that:
[http://www.minecraftforum.net/topic/948405-play-on-full-minecraft-from-ipad/](http://www.minecraftforum.net/topic/948405-play-on-full-minecraft-from-ipad/)

Trying to get a 3d game running on virtualbox is not the best thing to do - even if you are able to get it working, accessing it remotely will make the game unplayable.

---

