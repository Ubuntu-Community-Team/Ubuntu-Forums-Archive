---
title: "GID of /etc/hosts ?"
date: 2008-07-10
forum: Security
---

### Post by Adhémar on 2008-07-10
Hello,

After some discussions on the french ubuntu forum about this recent DNS security flaw, I decided to have a closer look at my /etc/hosts. I first checked the permissions of the file, and found:

[INDENT]ls -lh /etc/hosts
-rw-r--r-- 1 root 999 236 2008-03-31 10:55 /etc/hosts[/INDENT]

The permissions are fine because only root can write in this file. But I am puzzled by the GID. Why does this file belong to the group 999 ? This group isn't actually listed in /etc/group, so I can't even see the others members of this group.

---

### Post by brian_p on 2008-07-10
> **Adhémar said:**
> Hello,

After some discussions on the french ubuntu forum about this recent DNS security flaw, I decided to have a closer look at my /etc/hosts. I first checked the permissions of the file, and found:

[INDENT]ls -lh /etc/hosts
-rw-r--r-- 1 root 999 236 2008-03-31 10:55 /etc/hosts[/INDENT]

The permissions are fine because only root can write in this file. But I am puzzled by the GID. Why does this file belong to the group 999 ? This group isn't actually listed in /etc/group, so I can't even see the others members of this group.

On this box:

[indent]-rw-r--r-- 1 root root 272 2007-08-27 18:55 /etc/hosts[/indent]

You have altered the default install file, perhaps by copying another one from elsewhere.

---

### Post by imbjr on 2008-07-10
I just noticed this myself. I think it is because I installed Ubuntu from a USB stick, because the other files in /etc that are 999 are:

console-setup
locale
00trustcdrom
sources.list
hosts
papersize
popularity-contest.conf
resume

most of which have something to do with installation. Also [http://www.linuxjournal.com/article/10076](http://www.linuxjournal.com/article/10076) suggests that 999 belongs to the Unbuntu live CD user.

---

### Post by k_grdn on 2008-07-10
Hi, 

For the security conscious use chattr +i to set the immutable bit so that this file can not be modified.

Regards,

k_grdn

---

### Post by simonapnic on 2008-07-10
I don't think it's an issue at all.
Here's my /etc/hosts info:
-rw-r--r-- 1 root root 347 2008-06-28 03:58 /etc/hosts
I don't have the group 347 either and only root has altered the file a few times.
Probably this group comes from the default system install.

---

### Post by brian_p on 2008-07-10
> **simonapnic said:**
> I don't think it's an issue at all.
Here's my /etc/hosts info:
-rw-r--r-- 1 root root 347 2008-06-28 03:58 /etc/hosts
I don't have the group 347 either and only root has altered the file a few times.
Probably this group comes from the default system install.

You had me checking I had read Adhémar's post correctly! 347 is not a group.

---

### Post by Adhémar on 2008-07-11
> **simonapnic said:**
> I don't think it's an issue at all.
[...]
Probably this group comes from the default system install.

Well, I never thought this could be a security issue. It was just puzzling, but your explanation seems to be plausible.

Thanks everybody for all your answers,

Adhémar

ps: simonapnic, 347 is not the group number, but the size of your file.

---

