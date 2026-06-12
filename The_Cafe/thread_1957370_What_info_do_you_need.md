---
title: "What info do you need?"
date: 2012-04-12
forum: The Cafe
---

### Post by roelforg on 2012-04-12
Hi!
 
While my dev-pc's are updating (4hrs remaining on the indicator)...
I dediceded to get some info...
 
I'm working on a program that should be like the bootinfoscript but is for more general use on these fora.
It helps people post the info you usually need to solve the problem.
Example:
When on "Network & Wireless" i find myself repeating the following instruction over & over again:
[quote=roelforg]
Run this and post the output:
```

sudo lshw -C networking
sudo lspci
sudo lsusb
sudo ifconfig -a
sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf

```
The first one may appear to be stuck at "PCI (SYSFS)", but it's just scanning; let it run until your prompt comes back.
[/quote]
And i see the same pattern with others on other fora.
So,
i decided to make a program that can try common fixes and produce a detailed report of the system and the state.
That way, if it becomes as wide-used as bootinfo, people will post the needed info at first post.
 
So i wanna ask you all to post the most common pieces of info you need when solving problems and also post the topic for the info (is it networking, hard-drives, etc...?).
 
Like i said, my devpc's are updating right now and i don't wanna disturb them.
So i'll get the repo and my initial code up and running asap and post the link.
 
I'm looking forward to your ideas.

---

### Post by MG&amp;TL on 2012-04-12
```
/usr/lib/nux/unity_support-_test -p
```-this tests whether the user has enough resources to run Unity3d. This can help with graphics problems, unity not loading, and issues with drivers.

Btw, remove "sudo" from each of those suggestions except lshw-they don't need it, so you shouldn't use it. If the system is messed up, fair point. ;)

Good idea, thanks for the thread!

---

### Post by roelforg on 2012-04-12
> **MG&TL said:**
> ```
/usr/lib/nux/unity_support-_test -p
```
 
When and for what types of problem do you use that? (i asked in the OP to post this info as well, i can't really do something with the commands until i know under what section to put them)
 
Edit: LOL---you edit and i post...
Well, the sudo is because sometimes the system complains when the permissions are messed up, this compensates and i don't think cat can do any harm.
ifconfig doesn't report some interfaces when run as regular.
And lspci and lsusb complain when run them as regular on my systems.

---

### Post by MG&amp;TL on 2012-04-12
> **roelforg said:**
> When and for what types of problem do you use that? (i asked in the OP to post this info as well, i can't really do something with the commands until i know under what section to put them)

Oops! edited.

---

### Post by roelforg on 2012-04-12
> **MG&TL said:**
> Oops! edited.
 
Figured that out as well,
 
i'll just assume this one goes under "GFX Problems"

---

### Post by Rodney9 on 2012-04-12
/usr/lib/nux/unity_support-_test -p

This is not in my Xubuntu 12.04 system, does it only come with Ubuntu ?

Would be good if people could test their machines to see if they can run Unity, I remember Microsoft did something similar for checking if your pc could run Seven

Rodney

---

### Post by odiseo77 on 2012-04-12
**lsmod** may be useful in some cases too, in order to get information about which modules is the system using.

---

### Post by roelforg on 2012-04-12
> **odiseo77 said:**
> **lsmod** may be useful in some cases too, in order to get information about which modules is the system using.

Noted under "driver related" and "extended info" (it's usefull, but produces a huuuge list thats hard to post)

---

### Post by MG&amp;TL on 2012-04-12
> **Rodney9 said:**
> /usr/lib/nux/unity_support-_test -p

This is not in my Xubuntu 12.04 system, does it only come with Ubuntu ?

Would be good if people could test their machines to see if they can run Unity, I remember Microsoft did something similar for checking if your pc could run Seven

Rodney

It's part of libnux, which is probably not installed with Xubuntu. :)

---

### Post by roelforg on 2012-04-12
> **MG&TL said:**
> It's part of libnux, which is probably not installed with Xubuntu. :)

True, it's the obscure gui lib unity uses for it's windows.

---

