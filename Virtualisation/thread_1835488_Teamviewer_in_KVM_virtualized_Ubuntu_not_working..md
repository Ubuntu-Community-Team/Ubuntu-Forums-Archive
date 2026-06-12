---
title: "Teamviewer in KVM virtualized Ubuntu not working."
date: 2011-08-29
forum: Virtualisation
---

### Post by buskatten on 2011-08-29
Hello! First time poster, long time lurker.

I am using Ubuntu 11.04 to virtualize Ubuntu 11.04 through KVM (I have also tried Debian, Fedora and Mandriva). I'm using teamviewer so I can remotely access the virtual machines and this is what it looks like. It works flawless on the host, but like this on the guest.

If I have windows XP as guest, it works flawless too.

The reason I want to use Teamviewer on the virtual machines is for the easy network settings.

---

### Post by Alfagulf on 2011-09-09
[Solved]
I had the same problem!
I installed MINT OEM in a Proxmox KVM and then installed Teamviewer in Mint.
When I tried to access the Mint desktop from a teamviewer client, I got the same messy screen as you had.
I then opened the terminal and did "lspci" and found that the VGA adapter was "Cirrus Logic GD 5446".
I then shut down the KVM and went to the Proxmox Virtual Machine configuration under Options and changed the "Video Graphic Adapter" from "Default" to "Standard VGA".
After booting Mint again, I checked the "lspci" output and found that it changed to:
VGA compatible controller "Technical Corp. Devices 1111"

Teamviewer client is now able to view the server properly.
:)

---

### Post by buskatten on 2011-09-28
Wonderful!

However the VESA driver that standard VGA uses is incredibly slow! Or is this just because of the guest system I'm using? I've googled it and Debian/Ubuntu seems to have very slow VESA drivers in the latest releases.

---

### Post by DFLiddle on 2012-10-26
Thank you for posting this solution to your remote viewing problem with Proxmox. I had the same issue using Bomgar.


> **Alfagulf said:**
> [Solved]
I had the same problem!
I installed MINT OEM in a Proxmox KVM and then installed Teamviewer in Mint.
When I tried to access the Mint desktop from a teamviewer client, I got the same messy screen as you had.
I then opened the terminal and did "lspci" and found that the VGA adapter was "Cirrus Logic GD 5446".
I then shut down the KVM and went to the Proxmox Virtual Machine configuration under Options and changed the "Video Graphic Adapter" from "Default" to "Standard VGA".
After booting Mint again, I checked the "lspci" output and found that it changed to:
VGA compatible controller "Technical Corp. Devices 1111"

Teamviewer client is now able to view the server properly.
:)

---

