---
title: "is not in the subdoers file"
date: 2007-08-30
forum: Server Platforms
---

### Post by nwlcoc on 2007-08-30
Hi All,

I have a version 7.04 x64 server installed.  Recently I added my default user into a group but now everytime I try to use sudo it tells me '[myuser] is not in the sudoers file.'

Google does not seem to have the answer as to how I resolve this.  Any help gratefully recieved.

--
Marc

---

### Post by Seti on 2007-08-30
If I'm not mistaken all you need to do is make sure you're in the admin group, right?

make sure you're in this group, 
/etc/group
and you should be good to go.

---

### Post by nwlcoc on 2007-08-30
The problem is how to get my user into this group - without sudo I'm stuffed?

---

### Post by bodhi.zazen on 2007-08-30
1. Boot to the recovery mode and in a terminal :

```
adduser <username> admin
```

2. Or boot to either recovery mode or a live cd and edit /etc/group adding your user to the admin group.

Then reboot & you should be good to go ...

---

### Post by nwlcoc on 2007-08-31
Cool...
Many thanks!

---

