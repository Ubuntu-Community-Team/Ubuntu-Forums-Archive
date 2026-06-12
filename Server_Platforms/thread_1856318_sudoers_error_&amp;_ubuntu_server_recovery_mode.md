---
title: "sudoers error &amp; ubuntu server recovery mode"
date: 2011-10-08
forum: Server Platforms
---

### Post by doctorproctor on 2011-10-08
Greetings --  I (and all other admin group members) can no longer run sudo on Ubuntu Server 10.04 LTS as we receive the following group ID error:

 "/etc/sudoers is owned by gid 113, should be 0"

How can we replace the file sudoers with one with correct permissions? A quick search suggests that recovery mode is the only way, though I'd need to convey appropriate instructions to my IT people as I don't have physical access to the (virtual) server and have no idea how it's done in Ubuntu Server.

Many thanks,

Jim

---

### Post by bbqroast on 2011-10-08
Only possible with physical access, UNLESS you can find someone who is a member of group 113 and do it from their account (they should have SUDO access).

---

### Post by matt_symes on 2011-10-08
Hi

> **doctorproctor said:**
> Greetings --  I (and all other admin group members) can no longer run sudo on Ubuntu Server 10.04 LTS as we receive the following group ID error:

 "/etc/sudoers is owned by gid 113, should be 0"

How can we replace the file sudoers with one with correct permissions? A quick search suggests that recovery mode is the only way, though I'd need to convey appropriate instructions to my IT people as I don't have physical access to the (virtual) server and have no idea how it's done in Ubuntu Server.

Many thanks,

Jim

Did somebody chown the sudoers files ? Did they change the ownership of any other system files ?

I would be concerned what other system files may have changed.

You may need to boot into a LiveCD/USB to change it back after mounting it .

```
chown 0:0 <mount_point>/etc/sudoers
```Make sure the permissions are 440

```
chmod 440 <mount_point>/etc/sudoers
```As i said before though, have the permissions of any other system file changed ?
You need to find out how this happened.

Out of interest which group is 113 ?

```
grep 113 /etc/group
```Kind regards

---

### Post by doctorproctor on 2011-10-08
Thanks for your replies so far. Group id 113, I believe, is admin: I and one other user are in 113, there are no other users, and neither of us can use sudo at present; apparently, /etc/sudoers requires owner and group to be root and root (0:0) in order for sudo to work (!).

This mistake was made via an errant recursive chgrp applied to /etc/; not sure how critical this is for other files in /etc/ in addition to sudoers (presumably it stopped after sudoers file changed?). We see no other problems to the system, nothing in the error logs, etc. so far.

I studied [info on LiveCD booting]("https://help.ubuntu.com/community/LiveCD"), but this seems to apply to desktop vs. server Ubuntu: will this work for server?  (I believe our IT people are running virtual servers.)

Thanks again,

Jim

---

### Post by CharlesA on 2011-10-08
Depending on who you chgrp'd them to, it could cause problems down the road.

Anyhow - boot into recovery mode (hold down shift at the grub screen and select recovery mode) and chown it back to root:

```
chown root:root /etc/sudoers
```

---

### Post by doctorproctor on 2011-10-08
Thanks again. So, is there an Ubuntu utility to check/fix file permissions (including owner/group)? Alternatively, would these permissions be updated during upgrade to 11.04?

Regards,

Jim

---

### Post by CharlesA on 2011-10-08
I don't know of any utility to fix the permissions. I'd say so a reinstall so you know the permissions are correct and be more careful in the future.

---

