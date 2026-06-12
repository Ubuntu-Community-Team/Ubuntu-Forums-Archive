---
title: "Sudoers File"
date: 2011-12-06
forum: The Cafe
---

### Post by dRounse on 2011-12-06
Just a quick question.... I just went from Lubuntu 11.10 to Debian 6 to try it, now when I try to run as sudo through the terminal I get this message?
```
david is not in the sudoers file.  This incident will be reported.

```

I've used Debian 6 before and never has this problem, but its kind of a big deal if I can't run as root, so any help would be appreciated.


Sorry I'm not sure how to take this down, I fixed this problem, I went into the sudoers file with visudo from the root terminal and then added the line 
```
david ALL=(ALL) ALL
```

and that allowed me to run as sudo from the normal terminal.

---

### Post by papibe on 2011-12-06
I'm pretty sure that is not the default behavior.

Could you post the result of this command:
```
groups
```
Regards.

---

### Post by dRounse on 2011-12-06
> **papibe said:**
> I'm pretty sure that is not the default behavior.

Could you post the result of this command:
```
groups
```Regards.

```
david adm dialout fax cdrom floppy tape audio dip video plugdev netdev bluetooth lpadmin fuse scanner

```

This also after I changed it, That was weird though because I have installe it using the same DVD 3 or 4 times never an issue, but also once when I installed Lubuntu 11.10 it installed Lubuntu 11.10 but instead of LXDE programs it installed LXDE, Gnome, and KDE programs, it took me an hour to get it back to normal

---

### Post by zeljkojagust on 2011-12-06
I'm pretty shure it is the default bahevior for Debian and Ubuntu Server installations. Unlike Ubuntu Desktop, those two do not add initial user to sudoers, and you have to do it yourself.

---

### Post by jjex22 on 2011-12-06
I shall tread carefully now, as in my linuxforum days this subject always had the tendencies of a tinderbox.

Just to explain - as I'm sure you're all too familiar 'sudo' gives a user the abilitiy to run a program with the security privileges of the root user. The way to perform a similar task is to switch user to root and then run the program in a root shell using 'su'

Seems simple enough? well it is for ubuntu and similar, but the problem is to do with what people see as correct Unix operation - sudo let's you use a program with the privileges of the root user only knowing your password, from your account. su will open a root shell (unless you add a different users name afer it) and let you run as that user - but with their password. 

Many people see this as the correct way of doing things as it maintains the hierarchy of users, is the original unix way, and reduces errors by forcing a switch to root, which, in theory will make them act more responsible. However; supporters of sudo argue that having to switch out of the root shell afterwards is more likely to cause errors, as you may continue running as root for some time by accident.

As debian is one of the oldest linux, it caters to both types of user. You may not have been aware, but in the eyes of debian, you chose not to have full sudoer rights when you entered a root password  at the installer. If you give it a root password, it assumes you want to use su and you'll have to manually add your sudoer rights. If you don't give it a root password, it'll set you up with full sudoer privilages.

Phew! I think I weighed them both up evenly... I hold no personal opinion on the matter :|

---

