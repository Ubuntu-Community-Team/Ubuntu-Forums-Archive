---
title: "Alow non-privileged users to connect to wireless networks"
date: 2012-02-02
forum: Security
---

### Post by Mercedes300 on 2012-02-02
Hello friendly forum.

I want to allow a non privileged user connect to wireless networks, but still be non-privileged in the sense that he has no sudo rights. I this possible?

Perhaps I can give him sudoers rights, but only let him access this portion of the system with sudo? In other words, only let his sudo privileges allow him to change the wireless network.

As it is now, I get the error: "System policy prevents modification of network settings for all users"  -- prompting me for the password of one of the users with sudo rights.

They reference "all usres". Can I make it so it only connects to this wireless network for just this user?

Any help is appreciated.

Regards,

John

---

### Post by CharlesA on 2012-02-02
You can limit whast someone does with sudo by editing the sudoers file.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I think Ubuntu still uses network manager, and there should be a box to check that says "allow to all users" or some such thing.

---

### Post by Mercedes300 on 2012-02-03
I've found that this message is produced by policykit, and is configurable. 

The user is only in his own group. I would like him to not be prompted for an administrators password when connecting to a wireless network. The default ubuntu user (the one setup at install time) doesn't need to enter a password, this is the functionality I desire.

I have this so far in /etc/polkit-1/localauthority/60-custom.d/10-network-manager.pkla

Identify=unix-user:<USER>
Action=org.freedesktop.NetworkManager.settings.modify.system
ResultAny=yes
ResultInactive=yes
ResultActive=yes

However, running pkaction --action-id org.freedesktop.NetworkManager.settings.modify.system --verbose
yields:
         ...
         implicit active:     auth_admin_keep

How can I make this rule "stick"?

Thanks,

John

---

### Post by Mercedes300 on 2012-02-03
I'm still interested in the real fix for this. But I just went ahed and edited the /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy file line 587 to say "yes" insted of admin-auth-keep or whatever.

Still listening...

John

---

### Post by OpSecShellshock on 2012-02-03
I'm pretty sure CharlesA is correct about Network Manager. Just checked my other machine, and yes it is. So here's what you do:

As the primary/administrative user, click on the network icon in the bar up top. From the list that drops down go to Edit Network Connections, then choose the Wireless tab, and highlight your wireless network and hit Edit. In the new window that opens, there is a box to check in the bottom left that will make the wireless available for all users.

---

