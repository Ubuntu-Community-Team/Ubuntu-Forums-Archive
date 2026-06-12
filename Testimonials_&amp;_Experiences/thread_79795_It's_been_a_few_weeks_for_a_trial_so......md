---
title: "It's been a few weeks for a trial so....."
date: 2005-10-20
forum: Testimonials &amp; Experiences
---

### Post by mrmcctt on 2005-10-20
I've got to say I am very pleased with Ubuntu.  I have it installed on a dual boot WinXP Pro / Ubuntu Toshiba Satellite A70-S256.  (The laptop belongs to the company so I have to leave Windows on it)

Right from the start of the installation I had no problems.  I had partitioned the hard drive with Partition Magic before I realized I could do it during the installation with the partition manager included.

I created a "/", "/home" and "swap" partition on the empty partition of the hard drive, gave them mount points and then made sure the WinXP partition maintained the boot flag.  I followed the rest of the installation instructions and the installation completed without a hitch.  (Of note, I set my clock to UTC during the install, that was a mistake since it kept changing my system clock but I was able to easily fix that after the install).

Once I got the system rebooted after the install, I ran the update manager and then the "Automatix" program submitted by arnieboy [in this thread.]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix")  

Sound and display (ATI Mobility Radeon 9000) worked out of the box. I haven't found a peripheral that I own that was difficult to set up.  Wireless took a little longer since I have an integrated wifi nic with the Atheros chipset.  I was using wpa-psk for security on my router.  I finally conceded and set the router to WEP and the wireless works great.

It was a welcome sight to see how APT-GET worked for finding and installing software.  No more cryptic read-me's.  Now I have time to figure out how to use some of the new software like GIMP (was using Fireworks) NVU (was using Dreamweaver) Blender (completely new to me).  I also love the gDesklets program and have added a few "widgets" to the desktop.

I installed Wine using apt-get and used [this program]("http://sidenet.ddo.jp/winetips/config.html") to get IE 6.0 in Linux.  (I need it to access my timesheet online and I do like to get paid)

For now, the only reason I have to go back to the Windows login is for inputting work orders online for work.  They use a Citrix client to access the database and I'm not ready to tackle that one just yet.

My final take is a big thumbs up to the developers for this operating system.  Thanks.

---

### Post by bonzodog on 2005-10-22
hi, have just looked at the citrix clients homepage; there is a linux client available as an .rpm, or .tar.gz. I would get the rpm, then use at the terminal:

$alien <filename>.rpm

that will convert it to a .deb, then you just do:

$dpkg <filename>.deb

which will install it, and any dependencies.

link to clients: [http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186](http://www.citrix.com/English/SS/downloads/details.asp?dID=2755&downloadID=3323&pID=186)

---

### Post by mostwanted on 2005-10-25
You can also install it directly in alien, so you don't need to also call the dpkg command (it's done behind the scenes).

$ alien -i package.rpm

---

### Post by mrmcctt on 2005-10-25
Sorry...Don't want anyone to think I'm ignoring them.

My problem is I have no idea what to do with the client when installed.  Under windows, I install the client, go to a portal page and click a link for our work orders and they just open.  I don't know how to get this to work in Linux (yet).  

When I click the same link in Linux, all I am offered is to download the ICA.bin file which does nothing to get me into our work order database.

---

