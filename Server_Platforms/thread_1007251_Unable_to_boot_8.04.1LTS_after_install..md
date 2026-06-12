---
title: "Unable to boot 8.04.1LTS after install."
date: 2008-12-10
forum: Server Platforms
---

### Post by Robstarusa on 2008-12-10
Trying an 8.04 x86 server cd:

The thing installs & upon first reboot I get:

Starting up ...
This kernel requires the following features not present on the CPU:
0:6 0:8
Unable to boot - please use a kernel appropriate for your CPU.

Box is a Via C3 1ghz mini-itx w/ 256 ram.

---

### Post by Calmor on 2008-12-10
Looking on launchpad, one person installing in VMWare and Virtualbox had this same problem with the 8.04 server disc.  Using the desktop disc (which runs the generic kernel instead of the server kernel) worked fine.  

Can you try an alternate-install desktop CD instead of the server CD and see if that changes anything?

The launchpad issue I found was:

[https://answers.launchpad.net/ubuntu/+question/31405]("https://answers.launchpad.net/ubuntu/+question/31405")

---

### Post by Robstarusa on 2008-12-10
I will give that a shot, thanks.

You'd think that with the hardware encryption stuff (RNG, AES, or more) they'd at least test it on a really nice low power small server platform :)

---

### Post by Calmor on 2008-12-10
> **Robstarusa said:**
> I will give that a shot, thanks.

You'd think that with the hardware encryption stuff (RNG, AES, or more) they'd at least test it on a really nice low power small server platform :)

One would imagine, but I suppose they haven't looked at the VIA chips much for servers, and instead were looking at more mainstream server hardware.  I have a VIA C3 1GHz mini-itx board myself, but decommissioned it as a (Windows XP Pro) server.  It was "fast enough" for its purposes, but I am also running a full-time Mythbuntu box, and just migrated everything to it to avoid having two machines up.  Even the mini-itx's power requirements are greater than zero.

I was always impressed with the power requirements of that little board though.  I ran it for a year off of a 200W power supply that had burnt up (literally, smoke everywhere) in a normal PC, and never had any problems with it.

Good luck with your install.  What kind of server are you planning to run?

---

### Post by Robstarusa on 2008-12-10
OpenVPN

---

