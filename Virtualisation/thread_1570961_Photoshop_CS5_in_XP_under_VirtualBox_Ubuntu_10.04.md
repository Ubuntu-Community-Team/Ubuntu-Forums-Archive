---
title: "Photoshop CS5 in XP under VirtualBox Ubuntu 10.04"
date: 2010-09-08
forum: Virtualisation
---

### Post by jawb on 2010-09-08
Hello , I am asking if I can install Photoshop CS5 if I installed XP in VirtualBox.
Please help me and help ubuntu because if I can't run photoshop i will remove it :cry:

---

### Post by jawb on 2010-09-09
up

---

### Post by robbiemacg on 2010-09-10
Did you encounter a problem trying to install the application or are you asking if it's, theoretically, possible?

In my experience, so long as the virtual PC you create meets an application's system requirements, and you provide the guest OS access to the appropriate drives/folders, you should be good to go.

System requirements for windows machines are as follows for Photoshop CS5:
> 
[LIST]
[*]Intel® Pentium® 4 or AMD Athlon® 64 processor
[*]Microsoft® Windows® XP with Service Pack 3; Windows  Vista® Home Premium, Business, Ultimate, or Enterprise with Service Pack  1 (Service Pack 2 recommended); or Windows 7
[*]1GB of RAM
[*]1GB of available hard-disk space for installation;  additional free space required during installation (cannot install on  removable flash-based storage devices)
[*]1024x768 display (1280x800 recommended) with qualified  hardware-accelerated OpenGL graphics card, 16-bit color, and 256MB of  VRAM
[*]Some GPU-accelerated features require graphics support for Shader Model 3.0 and OpenGL 2.0
[*]DVD-ROM drive
[*]QuickTime 7.6.2 software required for multimedia features
[*]Broadband Internet connection required for online services*
[/LIST]
      Any virtual machine you create will function to spec. You just need to make sure you get the settings right for the job you want to accomplish. If you take the time to set up your virtual machine correctly (check out tutorials and videos), you'll save yourself a ton of hassle. I think I had to make, like three useless virtual machines before I learned my lesson and read the manual... (o_O)

---

### Post by robbiemacg on 2010-09-11
I've a bit of additional time left on my lunch break, so, here's how I read those system requirements...

Presuming your processor performs at 1.3 GHz or better, and you can spare 1GB of memory while running your virtual PC (if you have 3 or 4 GB total, you should be fine), you should be able to build an appropriate system.

I'd probably choose to install windows 7, rather than muck about with xp + updates, but maybe you're comfortable with that stuff.

I'd suggest allotting 20 GB of dynamically expanding storage (to permit future experimentation and allow to save some working files), permitting access to you system's optical drive and sharing your Desktop with the Guest OS (to make accessing ISOs and retrieving files easy).

Do these things and you should have no issue installing Photoshop CS5.

---

### Post by fantastic on 2010-10-06
I'm not sure if you resolved this, but this issue I'm facing with installing Abode Creative Suite 5 Web Premium (photoshop, dreamweaver, flash, illustrator, fireworks, etc...) is the video ram minimum requirement. 

Photoshop requires at least 256MB of VRAM:

> 1024x768 display (1280x800 recommended) with qualified hardware-accelerated OpenGL graphics card, 16-bit color, and 256MB of VRAM

VirtualBox, to my knowledge, is only capable 128MB VRAM.

I tried to install just Dreamweaver and Contribute on a Windows 7 VM but the because of the dependencies associated with the Web Premium CS5 suite, it fails as well.

If you have figured out how to install in, please post your solution. I would be interested in it as well.

---

### Post by ddCool on 2010-11-13
Here is a little trick to solve that:

1. Get the latest VirtualBox (3.2.10).

2. Open your virtual machines Settings, navigate to Display view, and increase Monitor count to 8 (you'll notiec available VRAM increasing to 256).

3. Increase VRAM to 256 (leave the Monitor Count at 8 ), click OK to save.

4.Re-open Settings, Display, and reduce Monitor Count to 8. The VRAM should stay at 256Mb.

Plz tell us how it went.

Cheers

---

### Post by FerdaS on 2010-11-17
I have same problem (XP with SP4, VirtualBox 3.2.10).
I try to do it, but CS5 doesn't work :sad:.
Tn'x for next idea :eek:)

---

### Post by pagemaker on 2010-12-07
I have Ubuntu 10.10 64bit installed on my laptop and I have created a virtual machine with VirtualBox 3.2.12 running Windows XP 32bit. I've used the trick with the VRAM (had already found it elsewhere) and also gave the virtual system a fair amount of 2 GB ram (my laptop has 4 GB) and Photoshop CS5 runs good. It's not THAT fast (probably because of my laptop's cpu) but I can work with it just fine...

---

