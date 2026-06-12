---
title: "how can i access system administration"
date: 2008-12-13
forum: Security
---

### Post by oma54r on 2008-12-13
Hello i use ubuntu 8.10 and i have a problem that i can't access to synaptic package manager  when i try to open it its give me this: Failed to run usr/sbin/synaptic as user root.
the underlining authorization mechanism(sudo) does not allow you to run this program.contact the system administrator.

and when i try to open users and groups gives me this message: the configuration could not be loaded.
you are not allowed to access the system configuration 
 
please i need some help i don't want to uninstall it

---

### Post by prshah on 2008-12-13
> **oma54r said:**
> 
the underlining authorization mechanism(sudo) does not allow you to run this program.contact the system administrator.


Looks like a problem with your /etc/sudoers file; did you try to edit it?

To repair, boot into recovery mode; give the command ```
visudo
``` This will open up the file in either nano editor or vi (vim) editor.

Look for lines similar to > # User privilege specification
root    ALL=(ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


If the lines look different from the above, change them to exactly match the above.

Then save and exit (if you're using nano press, Ctrl+o, Ctrl+x, if you are using vim type :wq).

Also give the additional commands```

cp /etc/sudoers /root/sudoers
chmod o+r /root/sudoers
```

Now reboot into regular mode and check if sudo is working. If it still isn't post the result of the command```
cat /root/sudoers
```

---

### Post by oma54r on 2008-12-13
i write visudo on recovery mode and give me the same lines with another lines and i delete the other lines and i write the additional commands but nothing happened. i check with the terminal with this command cat /root/sudoers and give me what in visudo and still i can't access

by the way i use this command before this happened gksudo nautilus

---

### Post by bodhi.zazen on 2008-12-13
Ubuntu uses sudo to give admin access.

so

sudo visudo 

See also : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by prshah on 2008-12-13
> **oma54r said:**
> check with the terminal with this command cat /root/sudoers and give me what in visudo and still i can't access


Please post the output of the command (Need to see your sudoers file)```
cat /root/sudoers
```

---

### Post by oma54r on 2008-12-13
this is what shown in cat /root/sudoers

---

### Post by oma54r on 2008-12-13
```
 # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password 
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```
ths is what in cat /root/sudoers

---

### Post by cariboo on 2008-12-14
I hope you realize that prshah's comment has a typo the correct command is:

```
sudo cat /etc/sudoers
```

Jim

---

### Post by oma54r on 2008-12-14
i found it for this u can add this command 
```

adduser username admin

```
username should be ur username

---

### Post by prshah on 2008-12-14
> **prshah said:**
> Also give the additional commands```

cp /etc/sudoers /root/sudoers
chmod o+r /root/sudoers
```

post the result of the command```
cat /root/sudoers
```

> **cariboo907 said:**
> I hope you realize that prshah's comment has a typo the correct command is:
```
sudo cat /etc/sudoers
```


Nope; you need to follow the thread from the beginning:

Points to note for _this_ thread:
a)"sudo" is locked out for him.
b) the /etc/sudoers file is +r for root:root only. So, in regular mode, he cannot access the file in any way (even to read / cat) since his sudo is broken. 
c) Which is why I asked him to make a copy of the /etc/sudoers file to /root when in Recovery Mode (root prompt), as well as change the permissions to allow other users to read the file.
d) Then, if the suggested change does not work, he is to post the copy of the sudoers file which he has placed in /root and made world readable.

Thus he cannot use the command you have given him, and has to stick with what I've given him.

---

### Post by prshah on 2008-12-14
> **oma54r said:**
> ```

Defaults	env_reset

```


.. change to ```

Defaults	!lecture,tty_tickets,!fqdn

```

Obviously you need to do this using "visudo" from Recovery Mode. (_NOT_ "sudo visudo")

---

