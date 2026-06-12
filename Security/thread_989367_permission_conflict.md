---
title: "permission conflict"
date: 2008-11-21
forum: Security
---

### Post by rosswell59 on 2008-11-21
I just installed GOS gadgets on an Everex gbook laptop. I'm trying to get the computer to see my wireless router. I opened the network settings utility and it needs to be unlocked so I can use it. When I enter my normal user password it rejects it. I have no root password set so I tried using sudo and that didn't work either. I also launched it as sudo from a terminal and that didn't work. Do I need to set a root password and then enter it to make it work?
Thanks,
Ross

---

### Post by rosswell59 on 2008-11-21
I just tried setting a root password and that didn't work either.

---

### Post by cariboo on 2008-11-21
Does your user have admin rights? To find out, in a terminal type:

```
groups
```

you should get something like this:

```
 groups
jim adm dialout cdrom plugdev lpadmin admin sambashare vboxusers
```

As you can see I am part of the adm and admin groups.

Jim

---

### Post by rosswell59 on 2008-11-21
I tried simply typing groups at the prompt and it didn't recognize it. Do I need a path or command to open groups?

---

### Post by Sarmacid on 2008-11-21
The command works for me, maybe you can try which```
# which groups
/usr/bin/groups

```

---

### Post by rosswell59 on 2008-11-21
Thanks, I did that and it showed up just as it should. I am included in adm and admin. I tried authenticatiaon in network manager again and an error came up and it said that it was unable to authenticate

---

### Post by cariboo on 2008-11-22
Can you use sudo? Are you using the right password, the one you set up when you installed Ubuntu?

Jim

---

### Post by rosswell59 on 2008-11-22
Yes I can use sudo. I installed ubuntu 8.04 last night and the password worked fine there. I would still like to try getting gos going if we can solve this.

---

### Post by rosswell59 on 2008-11-23
I tried doing "upgrade" with my old working g os which I kept on the first partition and it was rendered unbootable. The factory restore disk turned out to be bad so I reloaded gos gadgets and it is still giving me the same problem. I get an error message when the authorization fails. It looks like the problem is a bug with network manager.

---

### Post by rosswell59 on 2008-11-23
I've done some web searching and found the following which verifies that the problem is inherent with gos3 gadgets and offers a workaround:

[http://groups.google.com/group/goslinux/browse_thread/thread/f634aac2c9bcf827]("http://groups.google.com/group/goslinux/browse_thread/thread/f634aac2c9bcf827")

---

