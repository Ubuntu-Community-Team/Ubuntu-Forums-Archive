---
title: "Ubuntu 14.04 ldap users with automounted homes can't login via lightdm"
date: 2014-09-05
forum: Server Platforms
---

### Post by mamnmamn on 2014-09-05
My issue is based aroung ldap users who have automounted NFS homes. 

These users can login via SSH and local command line. Local users and ldap users with local homes can login via ssh, localcommand line and lightdm GUI.

ldap users with automounted homs cannot login via lightdm GUI. They authenticate but just get an Ubuntu purple background and working mouse. There is no unity bar or launcher. 

This is the same as mentioned here [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1228079](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1228079) accept this turned into a Power Broker / likewise bug and the solution was changing the power broker pam entry in common_session from sufficient to optional. The pam_sss.so line in my common_session is already at optional.
> # here are the per-package modules (the "Primary" block)
session [default=1]                     pam_permit.so
# here's the fallback if no module succeeds
session requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session required                        pam_permit.so
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session optional                        pam_umask.so
# and here are more per-package modules (the "Additional" block)
session required        pam_unix.so
session optional                        pam_sss.so
session optional        pam_systemd.so
# end of pam-auth-update config


In ~/.xsession-errors I have
> Script for ibus started at run_im.
init: dbus pre-start process (7814) terminated with status 1

I should add that in syslog automount shows that my home was mounted.

Any ideas?

---

### Post by richard51 on 2014-09-05
Sorry I don't have an answer for you, but all that the pre-start process of dbus does is:

[LIST=1]
[*]Creates the /var/run/dbus directory. 
[*]Changes the owner & group of said directory to **messagebus**. 
[*]Ensures that /var/lib/dbus/machine-id exists. 
[/LIST]
 It may not be a lightdm problem or pam, try installing    ***NSCD** (name service caching daemon)* on the client machines, this used to fix the hanging problem in 12.04. If it doesn't work, remove it... no harm, no foul.
```
**sudo apt-get install nscd**
```

**Additional:** Is this a **VM**? I set up a **VM**, copied a working 14.04 desktop image to it, and received the same results (*as you described*). The physical machines with 14.04 desktop installed (*same set-up*), worked fine. My pam set-up is nothing like yours, and I didn't have time to debug it. Although, after a couple of minutes, the unity-bar and launcher finally decided to show.

---

### Post by mamnmamn on 2014-09-08
Hi,

thanks for your reply. Yes, nscd is already installed and running. It is not a VM but installed on a HP ML310e.

---

### Post by mamnmamn on 2014-09-08
I have created a new users with a new, empty NFS home. This user can login and his home is mounted. I have found that this is completely my fault. One user was worried about having an automounted home with a quota because his .cache and .local was massive. I had been experimenting with these and symlinked .cache to elsewhere not accessible to the ubuntu installation. Once I deleted the .cache symlink and let ubuntu create it on login I could log in.

Thanks for you help and sorry it was due to my own experiments!!

---

