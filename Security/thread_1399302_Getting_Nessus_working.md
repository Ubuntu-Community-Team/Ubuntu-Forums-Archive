---
title: "Getting Nessus working?"
date: 2010-02-05
forum: Security
---

### Post by fallenshadow on 2010-02-05
I have installed the latest version of Nessus and looked at guides to getting it working but they don't work.

Most guides are for older releases of Nessus and from the Ubuntu repos. 

Mine is manually installed with a .deb from the website. Can anyone help me get it working?

---

### Post by Sarmacid on 2010-02-05
Which plugin feed are you using, and what's the output when you try to run it?

---

### Post by Soul-Sing on 2010-02-05
great howto: [http://linuxbasement.com/content/installing-nessus-using-apt](http://linuxbasement.com/content/installing-nessus-using-apt)

---

### Post by fallenshadow on 2010-02-05
> **Sarmacid said:**
> Which plugin feed are you using, and what's the output when you try to run it?

I have no idea what you are even asking... :confused:

I try to run it and it does not run!

As stated in my first post it is the NON-APT version. These kind of guides do not work.

---

### Post by hackertarget on 2012-07-16
Try this quick guide. I only did it last night so its pretty current. :)

[http://hackertarget.com/nessus-5-on-ubuntu-12-04-install-and-mini-review/](http://hackertarget.com/nessus-5-on-ubuntu-12-04-install-and-mini-review/)

After you install with "sudo dpkg -i Downloads/Nessus-5.0.1-ubuntu1110_amd64.deb"

It is simply a matter of going to [https://your.IP:8834/](https://your.IP:8834/) to start the wizard, register key and download the plugins.

Make sure you download the correct version (32bit or 64bit).

Edit: Just noticed the thread is pretty old. Quick post before coffee. Oh well, it is still relevant.

---

