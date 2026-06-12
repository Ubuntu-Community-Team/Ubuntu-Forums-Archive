---
title: "permissions for some programs"
date: 2012-10-24
forum: Security
---

### Post by Leo Matheus on 2012-10-24
im not sure if this is the beast place to put thias thread, but how it is related to security...

Well, i need to put some limits to some users of a machine. This people can acess the machine, but they can't run most of the program as adimin, but for some of this program i need to have this privilege.
So this accounts can only run some of the programs as root, and the rest not. 
how can i do that?:?:

---

### Post by snowpine on 2012-10-24
See here: 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In particular the section "Allowing other users to run sudo." Users who are in the "sudo" group will be able to run programs with admin/root privileges; while users not in the "sudo" group cannot.

If you want to get advanced with it, you can learn how to edit sudoers to fine-tune exactly which users can run which apps with sudo privileges.

---

### Post by Stonecold1995 on 2012-10-28
> **snowpine said:**
> If you want to get advanced with it, you can learn how to edit sudoers to fine-tune exactly which users can run which apps with sudo privileges.
You shouldn't edit the sodoers file directly.  It's easier to use the command "visudo".

---

### Post by Leo Matheus on 2012-10-29
thanks, i have make ome of the programs that i need to run using hte sudoers file. And i have take note of the visudo comanda, next time i will use it.

Now, just for curiosity, what is the directories/files to give the permision to the Network Manager?:-k

---

### Post by Leo Matheus on 2012-11-08
well, i will mark this thread as solved, since you have ansewer my main inssue

---

