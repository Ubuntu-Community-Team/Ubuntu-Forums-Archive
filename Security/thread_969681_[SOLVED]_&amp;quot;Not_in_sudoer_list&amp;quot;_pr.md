---
title: "[SOLVED] &amp;quot;Not in sudoer list&amp;quot; problem"
date: 2008-11-03
forum: Security
---

### Post by tomrob on 2008-11-03
Hi all,

I need some help here. 

It all started with trying to get Virtualbox to work. Tried to add myself to the vboxuser group. Unfortunantely I managed to exclude myself from everything else.

So now I cant do anything that requires root privileges. I just get a mesage saying "'username' not in sudoer list". The problem is that I cant add myself to the list either without root privileges. 

Tried to boot the recovery option and to get a root prompt, but then I have to type a root password, which doesnt work....

help....

Using Linux Mint 5 'Elyssa' with KDE desktop.

---

### Post by cariboo on 2008-11-03
You shouldn't have to use a password in recovery mode. You should be at a root prompt. To add yourself to the admin group, at the prompt type:

```
useradd -G sdmin username
```

This will add your user to the admin group and allow you to use sudo again.

Jim

---

### Post by aysiu on 2008-11-03
You shouldn't need a root password unless you've set one. And this is precisely why you shouldn't set a root password.

You'll have to boot a live CD and mount your current Ubuntu partition and manually edit the /mountpoint/etc/groups file to get yourself back in, since by setting a root password you've rendered recovery mode useless.

---

### Post by tomrob on 2008-11-03
> **cariboo907 said:**
> You shouldn't have to use a password in recovery mode. You should be at a root prompt. To add yourself to the admin group, at the prompt type:

```
useradd -G sdmin username
```

This will add your user to the admin group and allow you to use sudo again.

Jim

It asks for a password when I try to go to the root prompt from the recovery menu. I have newer set any root password, this is a fresh install. 

When I try to add my usename to admin, it says that the username already exists.
 

I still cant do sudo anything. "Not in the sudoer list" and I cann't edit the sudoer file without this working?

---

### Post by aysiu on 2008-11-03
> **tomrob said:**
> It asks for a password when I try to go to the root prompt from the recovery menu. I have newer set any root password, this is a fresh install. 

When I try to add my usename to admin, it says that the username already exists.
 

I still cant do sudo anything. "Not in the sudoer list" and I cann't edit the sudoer file without this working?
I've never seen a situation in which a root password has not been set but you still get prompted for one to enter recovery mode, unless this is a new bug that has cropped up in the latest release of Ubuntu 8.10.

As I said before, you'll have to boot up a live CD, mount your drive, and then edit the /etc/groups file manually to add yourself back into the admin group.

Let's take it step by step. Do you have a Ubuntu CD?

---

### Post by aysiu on 2008-11-03
> **tomrob said:**
> It asks for a password when I try to go to the root prompt from the recovery menu. I have newer set any root password, this is a fresh install. 

When I try to add my usename to admin, it says that the username already exists.
 

I still cant do sudo anything. "Not in the sudoer list" and I cann't edit the sudoer file without this working?
I've never seen a situation in which a root password has not been set but you still get prompted for one to enter recovery mode, unless this is a new bug that has cropped up in the latest release of Ubuntu 8.10.

As I said before, you'll have to boot up a live CD, mount your drive, and then edit the /etc/groups file manually to add yourself back into the admin group.

Let's take it step by step. Do you have a Ubuntu CD?

---

### Post by sisco311 on 2008-11-03
if you can boot in recovery mode then use:
```
adduser *username* admin
```
or
```
usermod -aG admin *username*
```
to add your user to the admin group.

if you can't, then boot with a live cd and mount your root ("/") partition.  
edit the */mountpoint*/etc/group file.
gnome:
```
gksu gedit */mountpoint*/etc/group
```
kde:
```
kdesudo kate */mountpoint*/etc/group
```
xfce4:
```
gksu mousepad */mountpoint*/etc/group
```

(assuming that */mountpoint* is the mount point of the root partition)

and add your login name to the group admin.
change the line:
> admin:x:112:to
> admin:x:112:*username*save the file and reboot.

if you don't know how to mount your partition then post the output of:
```
sudo fdisk -l
```
and
```
mount
```

---

### Post by tomrob on 2008-11-03
> **sisco311 said:**
> if you can boot in recovery mode then use:
```
adduser *username* admin
```
or
```
usermod -aG admin *username*
```
to add your user to the admin group.

if you can't, then boot with a live cd and mount your root ("/") partition.  
edit the */mountpoint*/etc/group file.
gnome:
```
gksu gedit */mountpoint*/etc/group
```
kde:
```
kdesudo kate */mountpoint*/etc/group
```
xfce4:
```
gksu mousepad */mountpoint*/etc/group
```

(assuming that */mountpoint* is the mount point of the root partition)

and add your login name to the group admin.
change the line:
to
save the file and reboot.

if you don't know how to mount your partition then post the output of:
```
sudo fdisk -l
```
and
```
mount
```

Ok so I need a liveCD, the problem is that I have VERY limited bandwith out here(offshore), so I guess I have to wait until I get one. 

I dont know why it asks for a password in recoverymode, as you probably have realized i'm pretty new with all this. 

But thanks for all help, I'll try again if I can download a liveCD anytime soon.

---

### Post by sisco311 on 2008-11-04
> **tomrob said:**
> Ok so I need a liveCD, the problem is that I have VERY limited bandwith out here(offshore), so I guess I have to wait until I get one. 

I dont know why it asks for a password in recoverymode, as you probably have realized i'm pretty new with all this. 

But thanks for all help, I'll try again if I can download a liveCD anytime soon.

try this:

boot the computer.

press Esc at the grub prompt.

select the recovery mode.

press e for edit.

select the line that begins *kernel* and press e for edit.

go to the end of the line and change the *ro single* options to *rw init=/bin/bash*

> kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=87be77dc-4dba-6f4db95c7636 **ro single**

-->

> kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=87be77dc-4dba-6f4db95c7636 **rw init=/bin/bash**


press Enter then b to boot in a root shell. 

type:
```
adduser *username* admin
```to add your user to the admin group, then press Ctrl+Alt+Del to reboot.

(replace *username* with your login name)

---

### Post by tomrob on 2008-11-04
> **sisco311 said:**
> try this:

boot the computer.

press Esc at the grub prompt.

select the recovery mode.

press e for edit.

select the line that begins *kernel* and press e for edit.

go to the end of the line and change the *ro single* options to *rw init=/bin/bash*



-->




press Enter then b to boot in a root shell. 

type:
```
adduser *username* admin
```to add your user to the admin group, then press Ctrl+Alt+Del to reboot.

(replace *username* with your login name)


Thanks alot! That did the trick :) Guess I learnt something new today aswell.

---

### Post by sisco311 on 2008-11-04
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

