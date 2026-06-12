---
title: "Sudoers File"
date: 2009-04-06
forum: Server Platforms
---

### Post by m3bik on 2009-04-06
I've recently tried logging into my ubuntu server. I have no problems logging in, but I can't use the sudo command anymore. I only have one user set up on the server, so I don't know what happened with it or what changed...

But when I try to sudo a command, I get the following message:

> USER is not in the sudoers file.  This incident will be reported.

How can I go about fixing this? Considering I can't write to certain files with out root permission....

---

### Post by m3bik on 2009-04-06
Better yet, how did I become removed from the file- if only I have access to the server and I didn't do it?

---

### Post by cdwillis on 2009-04-06
I don't know how it could have changed. Did you set up a password for root?

---

### Post by spiderbatdad on 2009-04-07
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by m3bik on 2009-04-07
> **spiderbatdad said:**
> [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Well right, but it's telling me I have to edit the file by using sudo... I can't do that, that's kind of the whole point of this question.

I only have one user account and didn't set anything for a root account because I was under the assumption I just needed to sudo everything and it would be fine. So how then, am I supposed to edit a system file without sudo or root account access?

---

### Post by bluefrog on 2009-04-07
do you have physical access to the server? if yes boot in recovery mode

---

### Post by cdenley on 2009-04-07
It sounds like you removed yourself from the admin group, or removed the admin group from your sudoers file.
```

groups
getent group admin

```

---

### Post by eldragon on 2009-04-07
reboot from a livecd and add yourself to the admin group:

mount the root partition from your broken install...

edit /etc/group

add your username to the end of the line that says

admin:user1,user2,user3


EDIT: removed advice due to forum policy tutorial restriction. not that i agree with it ;)

---

### Post by cdenley on 2009-04-07
> **eldragon said:**
> now to avoid these kind of problems in the future, create the root account's password, make it really hard to guess. type it (with ink) somewhere in your wallet.

Or just don't mess up your permissions, and if you do, that's what recovery mode is for.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by m3bik on 2009-04-10
Still not sure how it happened, but I have it fixed now. Thanks.

---

