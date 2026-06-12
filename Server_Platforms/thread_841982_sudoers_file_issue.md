---
title: "sudoers file issue"
date: 2008-06-26
forum: Server Platforms
---

### Post by rtsask on 2008-06-26
Hi

I accidentally changed the content of my sudoers file and when I going to open this file i get this error message 

sudo: parse error in /etc/sudoers near line 21

I need urgent help for this please

---

### Post by aysiu on 2008-06-26
Boot into recovery mode and type ```
cp /etc/sudoers /etc/sudoers.parse.error
nano /etc/sudoers
``` and make sure it looks like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` Then save (Control-X, Y, Enter) ```
shutdown -r now
``` Once you boot into regular mode, use only ```
sudo visudo
``` to edit the /etc/sudoers file. Do not edit it with any other command. Editing with *sudo visudo* checks for syntax errors before you save and exit.

---

### Post by rtsask on 2008-06-26
Thank you so much , but I'm fairly new to ubuntu , how can i boot to recovery mode in ubuntu server?

---

### Post by aysiu on 2008-06-27
I don't think it should be different for server from desktop.

You may have to press Esc during bootup to get the boot menu.

Once the boot menu is up, recovery mode should be the second option.

---

