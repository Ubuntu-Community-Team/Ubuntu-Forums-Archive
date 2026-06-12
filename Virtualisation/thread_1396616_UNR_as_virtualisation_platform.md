---
title: "UNR as virtualisation platform?"
date: 2010-02-02
forum: Virtualisation
---

### Post by jsoellner on 2010-02-02
Hi all

I have inherited an old Dell Poweredge 600sc at work and we want to use it as a development virtualisation platform.  I am obviously not expecting anything super speedy when it comes to performance.

I want the host OS to have as small a footprint as possible, leaving more resources available to the guest OS (probably will only run one at any given time).

Just wanted to get an idea for whether UNR is suitable for use as the host OS.  The host needs to be easy to use as not everyone on our team is familiar with Linux, so a nice GUI would be good.

Any feedback or ideas would be welcomed!

---

### Post by Guanglin.Du on 2010-02-06
I'd rather recommend using Xubuntu or Ubuntu since Remix is designed for Netbooks. Xubuntu is lighter than Ubuntu.

---

### Post by mkvnmtr on 2010-02-07
I have a guest running that I think will be very good for a host. I used the minimal install and installed the LXDE in 9.10. At idle it uses about 45Mb of ram and little cpu. I installed no sound just the apps I wanted to play with. It seems very stable and I believe I will use something like it in the future as a host for several systems. I tried the Lubuntu 10.04 alpha2 but it was using 40% more ram than my normal Ubuntu and it was not yet very stable. It might be a good base later but I like a stripped down distro for  what you have in mind with nothing installed but what has to be installed to make the virtual system work.

---

### Post by snowpine on 2010-02-07
No. Netbook Remix is not "lightweight" at all, I actually find it a little slower than "regular" Ubuntu. I'd recommend instead starting with a Minimal Install and adding only what you need: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by tipiglen on 2010-02-07
I have UNR as host with a UNR and an XP guest.  All three run fine together.

total RAM 2GB; each guest 512MB
I have tried with both guests cut down to 256MB to see if any difference, and it seems the XP is a bit troubled, but the UNR guest seems unperturbed.
Asus 1005HA (as in sidebar)

Not doing any games or the like, but with multible tabs open in browsers in all three simultaneously....

;-)

---

### Post by NightwishFan on 2010-02-07
The clutter library (Netbook Launcher) currently does not play well as a guest but it should be fine as a host.

---

