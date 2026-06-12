---
title: "Webmin Updating and Synaptic's Package Version Information"
date: 2005-07-28
forum: Server Platforms
---

### Post by kemu on 2005-07-28
I installed Webmin using Synaptic (from universe, which I don't think is supported in the Repository forum) and then upgraded Webmin to version 1.220 using Webmin's built-in upgrade process.  However, Synaptic does not recognize the upgrade, nor that I installed other modules (useradmin, etc.) from within Webmin.

How can I update Synaptic so it recognizes the currently installed version of Webmin and all the installed modules?  I tried "apt-get check" but that did not help.

I apologize if this is a simple question.  We're investigating migrating our Windows 2000 Active Directory environment to Linux, and I've been learning about Linux server issues the past two weeks.  One key part of the migration is ensuring that our limited staff can manage servers without deep knowledge of command line functions.

---

### Post by DJ_Max on 2005-07-28
There's really no reason to use a .deb package to install Webmin, because the Webmin install is just too easy. Of course your package system (apt-get) won't recognize the upgrade, because it has no way of knowning, seeing as you didn't upgrade it via apt-get. 

I don't know if there is a way around this without causing problems then to uninstall webmin via Synaptic and install Webmin manually.

---

### Post by kemu on 2005-07-28
OK, and thank you for your help.  (I'm also wanting to update Squid to STABLE10, and the latest version in the Ubuntu Repository is STABLE8.  I was asking about updating programs "outside" of apt-get in hopes that Synaptic can automatically recognize the programs' new versions.  I'm trying to make future installs and updates as easy as possible on our Windows-centric staff.)

---

