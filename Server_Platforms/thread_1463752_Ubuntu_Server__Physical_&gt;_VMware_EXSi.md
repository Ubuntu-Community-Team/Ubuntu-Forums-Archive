---
title: "Ubuntu Server  Physical &gt; VMware EXSi"
date: 2010-04-27
forum: Server Platforms
---

### Post by quietas on 2010-04-27
I've got a physical server running Ubuntu Server 9.10 what I looking at moving to a newer faster server running VMware ESXi. While I have used ESXi in the past, it has always been installs from scratch and never a P2V setup. I've looked at VMware Converter and have it installed on my Win7 box. Supposedly it will work from Ubuntu physical to ESXi Virtual via Converter.

How would I do this? Has anyone seen a good writeup or have some insight into using Ubuntu as the OS being virtualized on ESXi 4?  (or even 3.5)

Yes, I understand I could just copy my data and reinstall, but this is a test run for a much larger conversion of one a Redhat and later Windows servers. My Ubuntu box is the one which should be the easiest as it has the least data.

---

### Post by BobVila on 2010-04-27
You probably haven't seen a writeup because there's not much to write about; the wizard is straightforward enough once you get to the conversion wizard - launch the application, (I'm running it on Ubuntu - YMMV), click "Convert Machine". A conversion window will open - for "select source type", choose "Powered-on machine".

Enter the IP address, credentials, choose Linux for OS family, click next, specify the destination filename, choose your options, and wait out the conversion.

One caveat - you need to enable root access via SSH for the converter to successfully convert an Ubuntu box; this is disabled by default.

---

### Post by quietas on 2010-04-27
Thanks for the info and you are right, there isn't much info out there. Also, thanks for the tip about enabling Root, I'm sure that would have taken a few minutes and a headache to figure out. I had wondered if there was a client I was missing, but SSH is so much easier.

---

