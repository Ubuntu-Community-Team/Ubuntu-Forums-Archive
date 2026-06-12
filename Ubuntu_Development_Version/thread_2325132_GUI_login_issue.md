---
title: "GUI login issue"
date: 2016-05-19
forum: Ubuntu Development Version
---

### Post by ubername on 2016-05-19
Hi
Following updates c 15/5 I found I could not login through lightdm - I was simply sent straight back to the login screen (logging in via tty was fine). I created a new user with sudo roles and can login through lightdm fine with that. I have done all sorts of things (following google advice) like changing permissions on my entire home folder for the broken login, also reinstalled lightdm, but to no avail. 

Any clues? I get some messages in auth.log along the lines of 'lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory'.
Further examination via google suggests I needed to edit lines out of /etc/pam.d/lightdm, so I have commented out as below


#auth    optional        pam_kwallet.so
#auth    optional        pam_kwallet5.so

Still no joy. 

But my gut feeling is that this may be  a red herring - unfortunately I can't access auth.log backups older than 15/5 (or at least I don't know how to, if I can). Can anyone help?


Specifically:
If anyone else has this issue and has fixed it that would be great.
If anyone knows where I could look to see more detailed info on what is failing that would be great.

It should be said that I am running 16.10 based on innumerable upgrades from previous versions, most of which have also been upgraded from an earlier version via editing the sources.list as soon as the new tool chain came out, so I fully acknowledge this is all my fault!

---

### Post by ventrical on 2016-05-19
Try this.

[http://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959](http://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959)

regards

---

### Post by ventrical on 2016-05-19
> **ubername said:**
> Hi
Specifically:
If anyone else has this issue and has fixed it that would be great.
If anyone knows where I could look to see more detailed info on what is failing that would be great.

It should be said that I am running 16.10 based on innumerable upgrades from previous versions, most of which have also been upgraded from an earlier version via editing the sources.list as soon as the new tool chain came out, so I fully acknowledge this is all my fault!

This had happened to me a few times during last 2 cycles with long-standing rolling release installs. I think it has to do with systemd.

Some of the things I would try were:

```

sudo dpkg --configure -a
sudo apt-get -f install

```

this would fix any broken packages or install packages that may have got lost during updates.

Another method I use is install another desktop, ie;

```

sudo apt-get install xubuntu-desktop

```

and this would usually never fail.

Regards..

---

### Post by goofprog on 2016-05-19
You could always install a different login manager like gdm or kdm and then go back and reinstall lightdm.  Maybe that will help instead of installing a whole other window manager.

---

### Post by DougieFresh4U on 2016-05-20
For about a week I have been getting the following:

[HTML]Job for lightdm.service failed because the control process exited with error code. See "systemctl status lightdm.service" and "journalctl -xe" for details.
invoke-rc.d: initscript lightdm, action "start" failed.
dpkg: error processing package lightdm (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on lightdm; however:
  Package lightdm is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 lightdm
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]
I do not have any problem login in/out or restarting.

---

### Post by ubername on 2016-05-20
> **ventrical said:**
> Try this.

[http://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959](http://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959)

regards

Thanks ventrical, that did the trick.

Cut'n'paste from the linked thread:

sudo mv ~/.Xauthority ~/.Xauthority.old
sudo service lightdm restart

for easy access for others.

---

