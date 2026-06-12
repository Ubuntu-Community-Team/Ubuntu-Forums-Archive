---
title: "Looking for info on modprobe.d, modules.conf etc."
date: 2005-10-29
forum: The Cafe
---

### Post by abovett on 2005-10-29
Hi

I'm finding it hard to understand the relationships between the various files involved in loading kernel modules under Ubuntu (and Debian) - /etc/modules, /etc/modprobe.d/* , /etc/modulils etc. Can anyone point me to some up to date documentation? 

I recently had a problem with sound on a laptop and by googling around and hacking about I managed to get it to work (added a file to /etc/modprobe.d/ and some lines to /etc/modules), but I'm none too sure whether what I did was right and would like to understand _why_ it worked.

Some of the information I've seen appears to  be out of date (references to modules.conf and conf.modules). I've also seen people advise adding settings to  files in /etc/modprobe.d/ and then running update-modules - but when I do "man update-modules" it says the command is obsolete.

So all in all  I'm a bit confused, and I'm not sure where to find the "proper" documentation to understand it all. Can anyone help?

Andy B

---

### Post by mo_x on 2005-10-29
Have you tried the manual pages:
man modules
man modprobe
man modepobe.conf

The modules to be loaded at boot time are put in /etc/modules. The additional options for modules when they are loaded are put in files in the /etc/modprobe.d directory (used to be /etc/modprobe.conf I think). A lot of modules are loaded by the hotplug system but I don't know very much about that.

Mo

---

### Post by abovett on 2005-10-29
[QUOTE=mo_x]Have you tried the manual pages:[/QUOTE]
Yes - but I'm looking for a bit more detail than they provide. They are useful but leave a lot of questions unanswered - for example:

* An explanation of when the various /etc/modprobe.d/* files are processed
* The syntax of the /etc/modprobe.d files - is it the same as modprobe.conf?
* What is the /etc/modutils directory for?
* If update-modules is obsolete, but still included, when should it be used and what does it actually _do_?

I'd really like a good explanation of the whole module loading process - each distro seems to have a different combination of /etc/mod* directories and files and I don't really understand why. What actually processes these files - is it one of the startup scripts?

Thanks

Andy B

---

