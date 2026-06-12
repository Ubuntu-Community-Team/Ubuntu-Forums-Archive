---
title: "cant configure Horde3 on Ubuntu Server"
date: 2012-03-16
forum: Server Platforms
---

### Post by kustomjs on 2012-03-16
Hi Guys
I can not configure horde3 on my ubuntu server and this is the error I got:

A fatal error has occurred
Failed to import configuration file "/usr/share/horde3/config/conf.php": Horde3 configuration disabled by default because the administration/install wizard gives the whole world too much access to the system. Read /usr/share/doc/horde3/README.Debian.gz on how to allow access.

I took out that exit (0); in the configuration to allow me to do the webgui install and that is when I get that error.

---

### Post by kustomjs on 2012-03-16
anybody?

---

### Post by kustomjs on 2012-03-17
16 hours and after 101 views and still no help?

---

### Post by alepot on 2012-03-27
> **kustomjs said:**
> Hi Guys
I can not configure horde3 on my ubuntu server and this is the error I got:

A fatal error has occurred
Failed to import configuration file "/usr/share/horde3/config/conf.php": Horde3 configuration disabled by default because the administration/install wizard gives the whole world too much access to the system. Read /usr/share/doc/horde3/README.Debian.gz on how to allow access.

I took out that exit (0); in the configuration to allow me to do the webgui install and that is when I get that error.

From the README:

3. Configuring Horde

   To configure horde3 use the web configuration wizard. It is disabled
   by default for security reasons. To enable it remove the exit (0) directive
   and the echo line above it in /etc/horde/horde3/conf.php file. To let the
   configuration wizard write to the configuration files you have to change
   the owner of the /etc/horde/horde3 dir and config files to be owned by
   www-data.

---

