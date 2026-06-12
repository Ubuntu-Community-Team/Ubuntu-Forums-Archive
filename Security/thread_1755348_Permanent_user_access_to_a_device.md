---
title: "Permanent user access to a device?"
date: 2011-05-11
forum: Security
---

### Post by Marco.75 on 2011-05-11
Hi,
I managed to make an old parallel port scanner work in ubuntu 11.04 with SANE.
Everything's perfect but one thing: scanner applications work only if they are executed as a root.
After further researching, I've found the cause is that only the root has read and write permissions on the device  **/dev/parport0** which is my parallel port.

If I set the right permissions giving   **sudo chmod a+rw /dev/parport0** I solve my problem, but just untill next reboot... the system resets root only permissions at each restart.

I would like to make that change permanent... what can I do?
Somewhere I read that I must put myself into the group which has access to the device...but I'm quite a newbie and I don't understand what I have to do.

---

### Post by Lars Noodén on 2011-05-11
> **Marco.75 said:**
> ...I've found the cause is that only the root has read and write permissions on the device  **/dev/parport0** which is my parallel port.

What group does **/dev/parport0** belong to?  
Try adding your account to that group, logout and then log in again.

---

### Post by Marco.75 on 2011-05-11
I don't know... as I said I'm quite new to linux. How can I find what group does **/dev/parport0** belong to?

---

### Post by irv on 2011-05-11
Go to Users Settings unders System. Select "Manage Groups", Find the the right group in the list of groups, select "Properties" and see if the only user is "root", if it is than you need to add yourself to the list. you may need to do this with "root" access. 
[ATTACH]191831[/ATTACH]

---

### Post by Lars Noodén on 2011-05-11
> **Marco.75 said:**
> How can I find what group does **/dev/parport0** belong to?

```

ls -la **/dev/parport0**

groups *marco*

```

---

### Post by irv on 2011-05-11
You need to use the useradd command to add new users to existing group (or create a new group and then add user). If group does not exist, create it. The syntax is as follows:

```
sudo useradd -G {group-name} username
```

---

### Post by Marco.75 on 2011-05-11
Problem solved!
I used the **ls -l** command, and discovered that the device **parport0** belongs to the group named **lp**.
Then used the GUI approach to add myself to that group...
Many thanks for your help!:guitar:

---

