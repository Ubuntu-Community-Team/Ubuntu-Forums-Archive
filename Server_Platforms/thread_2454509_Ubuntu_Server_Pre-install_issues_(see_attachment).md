---
title: "Ubuntu Server Pre-install issues (see attachment)"
date: 2020-11-30
forum: Server Platforms
---

### Post by bmiles2001 on 2020-11-30
So, my goal was to mess with Kubernetes and I was planning on installing it on top of Ubuntu Server. 

I have several servers in my garage running Windows Server 2012 and one running ESXi 6. As I have always done, I used my idrac (v6) to attach the ISO and begin the installation process as I don't have the attached monitor/keyboard for them any longer. I haven't used Ubuntu since around 11/12, however, I never had any issues installing it before. It has always been seamless. If you look at the attached pictures, you'll see two. The first, I have no idea what it means. Maybe a complaint about a keyboard not being attached 

Secondly, you'll see errors regarding SPCR and no drives being found. Is this something I should be worried about?

I saw [another]("https://askubuntu.com/questions/1250194/acpi-spcr-unexpected-spcr-access-width-error-on-boot") ubuntu post and my bios version is 1.8.2

---

### Post by LHammonds on 2020-12-01
I assume you are using the "live" ISO image you get by default when downloading Ubuntu Server 20.04 LTS.

Try the [legacy image](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/) that uses the Debian-based installer to see if you get different results.

LHammonds

---

### Post by bmiles2001 on 2020-12-01
The legacy image was flawless and meets what my expectations were from before. Not sure why I got the issues with the other installer, but doesn't really matter now.. 

I checked the journal and I still see the ACPI: SPCR: Unexpected SPCR Access Width. Defaulting to byte size issue, but I believe I can ignore that.

---

