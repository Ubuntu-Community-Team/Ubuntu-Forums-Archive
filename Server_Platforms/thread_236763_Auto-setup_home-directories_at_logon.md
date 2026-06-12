---
title: "Auto-setup home-directories at logon"
date: 2006-08-15
forum: Server Platforms
---

### Post by bpreindl on 2006-08-15
Hi,

I'm running an 6.06 LTS as LTSP-server. My user accounts are located in a mySQL-Database accessed by nscd/nss. This works very well with one exception: There are no home directories for the users on the local machine.

So is there any way to auto-create a home-directory with predefined access permissions (700) when a user logs on the first time and to copy a "skeleton" there and running some scripts (e.g. to pre-configure the mail-client...) considering that the user only logs on in a graphical way via X (gdm)?

How would you solve this?

Thank you very much

Bastian

---

### Post by lamego on 2006-08-15
I would create a script on /etc/X11/Xsession.d (It should be called for evert user login).
On the script I would check wether the home directory was found or not, if not it would be created.

Note: To create an home directory you need to be root (becase of the write permission on /home), to work this script would need to be owned by root and have the setuid bit set.

---

### Post by LordHunter317 on 2006-08-15
No, /etc/X11/Xsession.d will not be called for all logins.

It will be called for all X/K/GDM logins.  But it won't be called if the home directory doesn't exist, because the login process will fail.

You have a few options:[list][*]pam_mkhomedir.  [This one has some security issues.](http://www.tldp.org/HOWTO/Autodir-HOWTO/x80.html)[*]Autodir.  This one is a PITA to setup.[*]Frankly, my best advice is to create a script that reads at bootup (anytime after you have the connection to MySQL) /etc/passwd and creates home directories for users who don't already have them.[/list]

---

