---
title: "Debian Question Regarding Sudo."
date: 2010-05-14
forum: The Cafe
---

### Post by Roasted on 2010-05-14
Say I have a Debian box and I want it to act just like Ubuntu in terms of how sudo works. How would I do that?

I googled a bit and some guides say I have to install a package. Others say I have to just edit a few config files. Others say I have to do everything.

What's the smartest way to go about this?

---

### Post by Zoot7 on 2010-05-14
Assuming you've sudo installed, adding this to /etc/sudoers should do the job.
```
username ALL=(ALL) ALL
```

---

### Post by harlan on 2010-05-14
In order to edit /etc/sudoers
1- gain root privileges
$su
2- edit the file
#visudo -f /etc/sudoers

---

### Post by NightwishFan on 2010-05-14
If you do not choose a root password when prompted during the installation, it will set you up as sudo. Though it caused some menu issues for me, it might not for you.

---

### Post by sisco311 on 2010-05-14
> **NightwishFan said:**
> Though it caused some menu issues for me, it might not for you.

May I ask what kind of issues?

---

### Post by aysiu on 2010-05-14
I think the smartest thing to do would be to implement it the way Ubuntu does.

First of all, make sure the *sudo* package is installed.

Then add your user to the *admin* group.

Then make sure the /etc/sudoers file in Debian looks the same as the one in Ubuntu, which makes anyone in the *admin* group able to *sudo* up to root privileges. ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

You may have to change some of the commands associated with certain launchers, as they may still be configured to ask for the root password instead of the user *sudo* password.

---

### Post by NightwishFan on 2010-05-14
I do not remember much but I know that Synaptic complained about needing root access or something. I think you just have to manually edit the entry to be gksudo synaptic and not gksu synaptic.

---

### Post by sisco311 on 2010-05-14
> **NightwishFan said:**
> I do not remember much but I know that Synaptic complained about needing root access or something. I think you just have to manually edit the entry to be gksudo synaptic and not gksu synaptic.

gksu is a GUI frontend for su and sudo. gksudo is just a symbolic link to gksu. You can set the authentication mode via gksu-properties or by setting the /apps/gksu/sudo-mode gconf key to true.

I downloaded and extracted the debian gksu package. It seems that they don't provide gksu-properties.

---

### Post by NightwishFan on 2010-05-14
I see, well I have no idea, I just learn as I go. :) I remember there being some issues with the method I used, so I just stuck to the default Debian way. It is worth a try though as it set up sudo automatically.

---

### Post by sisco311 on 2010-05-14
> **aysiu said:**
> 
Then add your user to the *admin* group.


The admin group, by default, does not exist in some distributions. They use the wheel group to allow the members of the group to su to root.  

In Arch, by default, the users from wheel group are allowed to sudo as well.

---

### Post by sisco311 on 2010-05-14
@OP

If you use GUI apps like NetworkManager or users-admin, then you may have to configure policykit too.

/etc/polkit-1/localauthority.conf.d/51-admin.conf:
```
 
[Configuration]
AdminIdentities=unix-group:**admin**

```

Replace **admin** with the name of the group you want to allow to run apps as another user.

---

