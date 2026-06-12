---
title: "problem using sudo command"
date: 2009-04-15
forum: Security
---

### Post by get2shashank on 2009-04-15
hello there,
            i have ubuntu7.10 installed on my system. With my default user(one created during installation) logged in, i am unable to carry out tasks which require password (like synaptic package manager, login window screen, software sources etc).
            In GUI whenever i double click any of such applications, i get no response. The system just doesn't do anything. This translates to not being able to use 'sudo' at the terminal. I get the following error whenever i try to use sudo :
"_______/etc/sudoers : Permission denied" [i am skeptical about that blank part:it said something like cannot access. Will make it sure in the next post]
            Result: I cannot do administrative tasks except dumping in as root user at any one of 'tty'.
            Please help me out. I guess there is some problem in sudoers file. how can i edit it (remember i dont have root privileges as given by sudo)

---

### Post by _Purple_ on 2009-04-15
Please post the exact error message.

---

### Post by Bakon Jarser on 2009-04-15
You can always edit files using a live disk.  Are you a member of the admin group?

```
groups (your user name here)
```

---

### Post by get2shashank on 2009-04-15
> **_Purple_ said:**
> Please post the exact error message.

The exact message goes like this...:
**sudo: can't open /etc/sudoers: Permission Denied**

---

### Post by _Purple_ on 2009-04-15
> **get2shashank said:**
> The exact message goes like this...:
**sudo: can't open /etc/sudoers: Permission Denied**

As Bakon Jarser has mentioned, can you please post the output of

```
groups your_username
```

---

### Post by get2shashank on 2009-04-15
currently i am not on my machine. i can reply to this after i reach it.
can you help me with:
1) if i am in admin group
2) if i am not in admin group

---

### Post by _Purple_ on 2009-04-15
> **get2shashank said:**
> currently i am not on my machine. i can reply to this after i reach it.
can you help me with:
1) if i am in admin group
2) if i am not in admin group

If you are not in the admin group, you can add yourself to the admin group by following the steps given [here](http://www.psychocats.net/ubuntu/sudo).

---

### Post by get2shashank on 2009-04-16
this is what i get by "groups *username*"
*username* : *username* adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev

"this is listed in my /etc/groups file"
admin : x : 110 : *username*

by all this i think for sure that i am a member of the admin group...

**[read above by substituting *username* with my actual username]**

---

### Post by sisco311 on 2009-04-16
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

