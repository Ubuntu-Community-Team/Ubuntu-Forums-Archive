---
title: "SELinux trouble"
date: 2015-05-23
forum: Security
---

### Post by denis41 on 2015-05-23
Hello everyone!

 I have trouble with SELinux under Ubuntu 14.04. 

When I installed selinux as follows:

# apt-get install selinux

the error appeared:

usr/sbin/semodule: SELinux policy is not managed or store cannot be accessed.
Error opening /etc/selinux/ubuntu/contexts/files/file_contexts.local: No such file or directory
libsemanage.sefcontext_compile: sefcontext_compile returned error code 255. Compiling /etc/selinux/ubuntu/contexts/files/file_contexts.local
libsemanage.semanage_install_active: Could not copy /etc/selinux/ubuntu/modules/active/policy.kern to /etc/selinux/ubuntu/policy/policy.29. (No such file or directory).
/usr/sbin/semodule:  Failed!
dpkg: error processing package selinux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 selinux
 E: Sub-process /usr/bin/dpkg returned an error code (1)

After reboot, the installation process had been completed.
By # sestatus or # id command the information is shown.
But command

#semanage login -l

always turn empty list.
I'm tried create and configure new user:

# useradd -c "newuser" -m -d /home/newuser -g users -s /bin/bash -u 1005 newuser
# passwd newuser

The /etc/selinux/users file is not exists. Also there is no the makefile in the folder (therefore I can't execute the command  # make -&#1057; /etc/selinux load).

How selinux can be configured under the Ubuntu 14.04 correctly?

---

### Post by HermanAB on 2015-05-23
Howdy,

If you need SELinux, then install Fedora or RedHat.  It isn't properly supported on Ubuntu.

---

### Post by denis41 on 2015-05-24
[COLOR=#000000]T[/COLOR]hanks for the information.

Unfortunately, I have to use only Ubuntu 14.04 (or earlier version) :(

However, it is necessary to do the following steps:
1. Install SELinux.
2. Switch SELinux to the enforcing mode.
3. Add new user "charlie" with user_r and sysadm_r roles.
4. Configure SELinux: [INDENT]a) If charlie login locally, then he has sysadm_r role.[/INDENT]
[INDENT]b) If charlie login via ssh, then he has user_r role.[/INDENT]

The 1 and 2 steps had done.
Is it possible to do the 3 and 4 steps under Ubuntu 14.04 or, may be, earlier version?

---

### Post by denis41 on 2015-05-31
Well, I installed Fedora 22 (x64). However, t[COLOR=#000000]he /etc/selinux/users file is not exists. Moreover, I can't execute the command # make -&#1057; /etc/selinux load.

How to set [/COLOR][COLOR=#000000]user_r and sysadm_r roles [/COLOR][COLOR=#000000]for a new user?[/COLOR]

---

### Post by oldos2er on 2015-05-31
Fedora Security and Privacy forum is [here]("http://www.forums.fedoraforum.org/forumdisplay.php?f=44").

---

### Post by Sangeetha_B on 2016-01-19
> **denis41 said:**
> [COLOR=#000000]T[/COLOR]hanks for the information.

Unfortunately, I have to use only Ubuntu 14.04 (or earlier version) :(

However, it is necessary to do the following steps:
1. Install SELinux.
2. Switch SELinux to the enforcing mode.
3. Add new user "charlie" with user_r and sysadm_r roles.
4. Configure SELinux:[INDENT]a) If charlie login locally, then he has sysadm_r role.[/INDENT]
[INDENT]b) If charlie login via ssh, then he has user_r role.[/INDENT]

The 1 and 2 steps had done.
Is it possible to do the 3 and 4 steps under Ubuntu 14.04 or, may be, earlier version?


Have you solved it? if yes, can you please share solution.

---

### Post by oldos2er on 2016-01-21
denis41 hasn't returned to the forums since last May. If you're having an Ubuntu problem please create a new thread.

Closed.

---

