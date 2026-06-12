---
title: "Bit Confused!"
date: 2008-11-14
forum: Server Platforms
---

### Post by happyhacker on 2008-11-14
I want to setup a server for our group of 18 PCs (windows). I go to the Ubuntu server download and am presented with two options, desktop and server. When I select the server one and start download I see it is downloading something called the desktop edition.

Can someone tell me the version I should be downloading or send me to some advice document?

---

### Post by CrucifiedEgo on 2008-11-14
Make sure when you click on the download link that you're again clicking server edition.  If you still have trouble, try starting here and see what you can find:

[http://ftp-mirror.internap.com/pub/ubuntu-releases/](http://ftp-mirror.internap.com/pub/ubuntu-releases/)

Most likely you'll want this:

[http://ftp-mirror.internap.com/pub/ubuntu-releases/8.04.1/ubuntu-8.04.1-server-i386.iso](http://ftp-mirror.internap.com/pub/ubuntu-releases/8.04.1/ubuntu-8.04.1-server-i386.iso)

---

### Post by hictio on 2008-11-14
Can you download Torrents?

The Server (latest version):
[http://releases.ubuntu.com/8.10/ubuntu-8.10-server-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-server-i386.iso.torrent)

The Desktop (latest version):
[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent)

This is for an plain vanilla Intel box, if you have other type, please tell us.

---

### Post by happyhacker on 2008-11-14
OK, thanks. I do not know why the Ubuntu site can't make it clear. Anyway I've noticed that the server edition does not have a graphical interface. This is a non starter for me! I feel as if I've gone back a step.

I want a graphical server. Can anyone tell me if I should go somewhere else (like SUSE, or Fedora)? Or can I get what I need from Ubuntu (seeing as I've spent some time hearing/reading about it)?

Thanks.

---

### Post by CrucifiedEgo on 2008-11-14
You can install a GUI on the server edition easily, or start with the desktop edition.  The server edition is designed to be lightweight, which means dropping the fancy interface.  If you want to install it, you can do sudo aptitude install ubuntu-desktop.  Or, if you want, just install the desktop version -- there's very little difference between the two for most uses.

---

### Post by happyhacker on 2008-11-14
Thanks, so really if I install the instantiate the extra graphical interface I end up with the desktop version?

Will I have to start doing network things like Samba with the desktop version?

Whilst I'm willing to have a go I do not really want to do too much nitty gritty stuff to get file sharing going!

---

### Post by CrucifiedEgo on 2008-11-14
Have to?  no.  Can you?  Yes.  The GUI is just a layer on top of the config files that you'd edit by hand.

---

### Post by happyhacker on 2008-11-14
I'm still wondering if i'm going to spend a lot of time fiddling to get a server working. I'll have a look at SUSE first and see if there are other server versions maybe easier to set up.

---

### Post by cariboo on 2008-11-14
No matter which distribution you choose, you are going to have to configure text files. If you feel that running a server without a gui is going back a step, maybe you should look at Microsofts offerings.

Most linux servers are designed to run headless, so there is no need for a gui, but there are a couple of web based server administration suites that insuilate you from the command line. have a look at:

[http://www.webmin.com/](http://www.webmin.com/)

and Ebox which is available in the repositories.

Jim

---

### Post by Philio on 2008-11-14
If you just want some basic file sharing and are not comfortable with editing the config files, then you'll save a lot of time by just installing a basic Windows server setup as cariboo said.

All our production and test servers run Linux, but when we wanted a basic file server for the office we just setup a Windows VPS on our Xen box as it was quicker.

---

### Post by CrucifiedEgo on 2008-11-14
Agreed.  We've got a variety of windows and linux servers, and our office file server runs XP Professional.  For windows file sharing, it's hard to beat windows.

---

### Post by ciscosurfer on 2008-11-14
@cantthinkofanickname,

Here is a [breakdown of the server edition]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").

Here is a [breakdown of the desktop edition]("http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition").

As you'll see, there are indeed many differences otb (hence the reason why separate products exist).

---

### Post by happyhacker on 2008-11-15
> **CrucifiedEgo said:**
> Agreed.  We've got a variety of windows and linux servers, and our office file server runs XP Professional.  For windows file sharing, it's hard to beat windows.

We do not have a copy of Pro spare so I was looking to use a Home PC (I do not think this can act as a server for file sharing) and install Linux. We do want to try an Open Source CRM somaybe the desktop version will do for that type of application.

What I'm thinking of is to install the server version to get the basic server apps going and install webmin (I have used that a bit before) and install the gui as well.

Advice welcome.

---

