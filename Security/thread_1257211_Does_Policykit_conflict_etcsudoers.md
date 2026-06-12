---
title: "Does Policykit conflict /etc/sudoers?"
date: 2009-09-03
forum: Security
---

### Post by Bendemann on 2009-09-03
First, excuse my poor english.


I'm using for various reasons a root account. This is my /etc/sudoers.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

#Defaults       env_reset
Defaults        !lecture,tty_tickets,!fqdn,targetpw,timestamp_timeout = 0

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
# root  ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

This means, that each action, which requires admin rights, needs the root password ("kdesu blablabla" or in xterm "sudo blablabla").

The problem is the Policykit in KDE's systemsettings. In each module are two general types of authentification methods: "Admin Authentication" and "Authentication". When "Admin Authentication" is enabled, Policykit wants my user password. 

Why does Policykit not request the root password? Okay, I'm still in admin group, but each other programm that needs root privilege asks for root password, too.

---

### Post by sisco311 on 2009-09-03
> **Bendemann said:**
> 

Why does Policykit not request the root password? Okay, I'm still in admin group, but each other programm that needs root privilege asks for root password, too.

You can change the authentication mode by editing /etc/PolicyKit/PolicyKit.conf
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth **user="root"**/>
</config>


```

---

### Post by Bendemann on 2009-09-03
Great. Thanks for your advice.

Greetings from Germany to Romania.

---

### Post by Bendemann on 2009-09-03
According to this solution, systemsettings freezes, when you try to edit the Policykit. Kpackagekit also, when the authentification method for kpackagekit is set to "Admin authentification".

The german Arch Linux board gave the following hint. The configuration of /etc/PolicyKit/PolicyKit.conf must be this:

```
<config version="0.1">
</config>

```

Nothing else.

Now, I'm able to install local packages with root's password, edit Policykit in systemsettings as root and so on.

I'm not a pro. Is this the final solution?

---

