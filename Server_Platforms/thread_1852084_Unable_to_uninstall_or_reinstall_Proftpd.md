---
title: "Unable to uninstall or reinstall Proftpd"
date: 2011-09-29
forum: Server Platforms
---

### Post by rickyble on 2011-09-29
I upgraded my ubuntu server to Ubuntu 10.04.3 LTS .  After upgrade I was trying to install proftpd.  I get the following....

Reading package lists... Done
Building dependency tree
Reading state information... Done
proftpd is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  proftpd: Depends: libmysqlclient15off (>= 5.0.27-1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I did run apt-get -f install 
also apt-get update
I have looked on the forums and google and have no idea what to try.  I can try to do an uninstall of proftpd and it fails with:

Removing proftpd ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd (--remove):
 subprocess installed pre-removal script returned error exit status 100
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am out of ideas.  I tried to install vsftpd and it fails with dependencies  


Help please...thanks

---

### Post by stlsaint on 2011-09-29
For starters try running this:

```

sudo dpkg --configure -a
sudo apt-get clean all
sudo apt-get update

```

---

### Post by rickyble on 2011-09-29
Got it.  Edit the dpkg/status file and removed the proftpd section.  Ran the apt-get update and then installed the proftpd program again.  Runs like a charm.  Somehow it got stuck in the status file.

---

