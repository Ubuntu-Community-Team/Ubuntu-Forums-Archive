---
title: "can't log in as root"
date: 2009-09-14
forum: Server Platforms
---

### Post by RFXCasey on 2009-09-14
I just install Ubuntu 9.04 server. I rebooted the machine and I have no x server started. I try to start it it says I have to log in as root. I can't log in as root, I am assuming I have to enable it but I only know how to do that with a GUI.

---

### Post by trundlenut on 2009-09-14
By defualt ubuntu server version does not include a gui, it's command line only.  Also in Ubuntu the root account is disabled, you need to use the sudo command to do things as root.

You could install something like Gnome but personally I think you're better off learning to do things via the command line.

---

### Post by abaden on 2009-09-14
Check out [this documentation article]("https://help.ubuntu.com/community/RootSudo") for more info on using sudo instead of the root user.


Alex

---

### Post by lisati on 2009-09-14
As has already been mentioned, "sudo" is the preferred method of (temporarily) gaining root privileges in Ubuntu. If you ***must*** enable root, be sure to give yourself a strong password and don't stay logged in as root for too long.

---

