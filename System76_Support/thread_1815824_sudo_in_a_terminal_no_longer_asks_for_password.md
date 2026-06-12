---
title: "sudo in a terminal no longer asks for password"
date: 2011-08-01
forum: System76 Support
---

### Post by Tank Jr on 2011-08-01
Hi all,
I noticed yesterday that when I  do a sudo *something* at the terminal I no longer get prompted for a password. 
Any ideas?

---

### Post by lisati on 2011-08-01
There is a period after entering a password for sudo (usually about 15 minutes or so) that you don't have to enter a password each time you use sudo.

---

### Post by Tank Jr on 2011-08-01
Last had to put in a password two days ago.

---

### Post by jdb on 2011-08-01
> **Tank Jr said:**
> Hi all,
I noticed yesterday that when I  do a sudo *something* at the terminal I no longer get prompted for a password. 
Any ideas?

To see what options are set:
sudo -l
that is -l as in list

To change them:
sudo visudo

To learn about them:
man sudo

jdb

---

### Post by Tank Jr on 2011-08-03
I am not familiar with the sudoer settings, and hence I am reluctant to touch them. I can post the contents if that helps.

---

### Post by jdb on 2011-08-03
> **Tank Jr said:**
> I am not familiar with the sudoer settings, and hence I am reluctant to touch them. I can post the contents if that helps.

If you just post the output of sudo -l it may show something.

This is what mine looks like:
```
15:42:32 ~ sudo -l
Matching Defaults entries for dad on this host:
    !env_reset, !secure_path, timestamp_timeout=60

User dad may run the following commands on this host:
    (ALL) ALL
    (ALL : ALL) ALL

```

I've modified them some but the one of interest here is "timeout".

Other entries with names different than these are also of interest.

jdb

---

### Post by Tank Jr on 2011-08-04
Thanks for replying.
Here is the output:
```
Matching Defaults entries for MyName on this host:
    env_reset

User MyName may run the following commands on this host:
    (ALL) ALL
    (ALL) NOPASSWD: ALL
```

---

### Post by Dave_L on 2011-08-04
> **Tank Jr said:**
> (ALL) NOPASSWD: ALL

That's probably why you're not asked for a password.

---

### Post by jdb on 2011-08-04
> **Dave_L said:**
> That's probably why you're not asked for a password.

I agree with Dave.

The big question is how did it get changed.
You can fix it easily, but make sure you know your password
or you won't be able to use sudo after you fix it.

Use
```
sudo visudo
```
to fix it.

edit your permissions to look like this
```
# User privilege specification
root  ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo ALL=(ALL:ALL) ALL

```

Edit:
Make sure you are the only one in the sudo group.
You can grep /etc/group to check.
This is what mine looks looks like:
```
14:56:36 ~ grep sudo /etc/group
sudo:x:27:dad

```

You should also be the only one in the admin group:
```
14:58:37 ~ grep admin /etc/group
lpadmin:x:112:dad
admin:x:118:dad

```
jdb

---

### Post by Tank Jr on 2011-08-06
Hi,
I already have the three lines you mentioned. Should I post the whole sudoers file for you to look at?

---

### Post by jdb on 2011-08-07
> **Tank Jr said:**
> Hi,
I already have the three lines you mentioned. Should I post the whole sudoers file for you to look at?

Sure.

But I think if you look closely, one of them is:
(ALL) NOPASSWD: ALL

That is from your earlier post.

That line should be:
(ALL : ALL) ALL

jdb

---

