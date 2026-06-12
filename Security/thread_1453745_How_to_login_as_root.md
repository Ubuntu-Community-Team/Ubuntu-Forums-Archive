---
title: "How to login as root?"
date: 2010-04-13
forum: Security
---

### Post by officiallyme on 2010-04-13
Hi all,

I know, I know, security reasons, no root login. No user is root etc.

But I am running an isolated Linux kUbuntu VM, so security isn't an issue :)

I have created a user and wanted to make that user "officiallyme" a root user. Full access, full root priviliges etc.

So I altered the /etc/passwd and set everything to 0 for officiallyme.

But then of course I couldn't login afterwards :lolflag:

So I am now setting up kUbuntu again as a new VM and would really like to know how I can make the user "officiallyme" root and be able to login.

Hope you guys'll help me :)

---

### Post by trig on 2010-04-13
Try in the terminal Nautilus.

---

### Post by mick222 on 2010-04-13
Use Google as this discussion is not allowed. See here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by officiallyme on 2010-04-13
how come it's not permitted?
i'm not trying to hack a system. I would just like to change my running system to which I have full access.

problem with the whole sudo thing or rather sudo su is simply, that you either have to keep typing sudo (which means adjusting dozens of scripts) or you use sudo su and then the normal user cannot access the files anymore.

i just need one user and like in windows, i would like him to have full access to everything.


google didn't really help as the only thing I found usefull for kubuntu is from 2005.

would really like to know if there is a decent and quick way to do this in kubuntu 10.04.

---

### Post by sisco311 on 2010-04-13
As an admin user you have full access to the system. policykit & sudo/gsku allows you to run apps as root.

[thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by officiallyme on 2010-04-13
i know what root access is and what sudo etc. do :)

and I don't want the actual root account. well, basically i do. but i rather want the user "officiallyme" to be root.

i read the forums policy now. but i am surprised because what i did find via google was from this forum. hence i asked here because i found info on it here.

shame really. guess i'll have to keep trying because some of my scripts are a real pain if i have to keep compiling and building without root priviliges or build something as root and then want to edit as normal user.

---

### Post by sisco311 on 2010-04-13
> **officiallyme said:**
> 
shame really. guess i'll have to keep trying because some of my scripts are a real pain if i have to keep compiling and building without root priviliges or build something as root and then want to edit as normal user.

Then it's something wrong with your scripts. Compiling does not require root privileges & you can use fakeroot to build a package.

---

### Post by mkvnmtr on 2010-04-13
I haave a pen testing distro in virtual box that runs as root out of the box. It is no advantage and I believe every user opens thier own account before using the distro. In other words you are wasting your time.
I kind of feel that if you have to ask how to enable the root account you do not know enough to use it.
Desides it is contra to the policy of these forums. Good luck.

---

### Post by officiallyme on 2010-04-13
i compile multiple gits and svns and logically I don't want to alter them :D

anyway. so no support here. ok, i respect that. don't understand it, but i respect that :) 8-)

---

