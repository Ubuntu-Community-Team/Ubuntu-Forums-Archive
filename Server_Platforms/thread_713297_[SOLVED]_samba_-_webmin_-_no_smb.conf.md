---
title: "[SOLVED] samba - webmin - no smb.conf"
date: 2008-03-02
forum: Server Platforms
---

### Post by jimmy the saint on 2008-03-02
I think I am missing something here.  I Ubuntu server and chose the LAMP option, but nothing installed as far as LAMP is concerned.  Rather than try to figure that out I just moved on and installed everything manually.

The current issue is that there is no smb.conf in /etc/samba.  Instead there is gdbcommands.dpkg-new.  I plugged that into google and found nothing.  I have been searching everywhere for a solution, but finally I am here.  I installed Samba through Webmin if that matters.  Also, etc/init.d/samba restart and start comes up as an unkown command.  

Am I missing a step here?  

Thanks for your help!

---

### Post by jimmy the saint on 2008-03-02
Also, in init.d, there is only "samba.dpkg-new"   When I attempt to start or restart that service, I get "Starting Samba daemons" [fail].   There is no Samba to run.  Did a step fail in installation?  Am I missing something simple?

---

### Post by jimmy the saint on 2008-03-02
Well I figured it out!!  DON'T use webmin to install software, even though it kindly offers!!   I have no idea what goes wrong, but it didn't complete the installation.  I completely removed Samba and reinstalled via apt and now it works fine.

---

### Post by ung/xunil on 2008-03-02
Yes, webmin has some problem with installing packages in Debian/Ubuntu. Do not use it.

Webmin don't deal with the output and input to apt-get. It works "fine" (no output, we really don't know if it worked fine) if apt-get doesn't ask nothing, but is some question is asked (installing a LAMP asks many questions), end-of-story. You can't type, you can't do anything to stop apt-get (kill? is that good while a package is being installed?) and apt-get is stuck in a infinite loop...

Install packages with the console (webmin has one, I think) or with SSH.

About samba, I think you have to install some more packages - samba - to be able to share files and - smbfs - to read windows shares. I don't use it, so maybe this link helps: [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

