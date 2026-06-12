---
title: "Not a superuser?"
date: 2010-03-25
forum: Security
---

### Post by Tethyrian on 2010-03-25
So I just installed ubuntu 9.04 and I am loving it so far. Only one problem though.... For some reason the first account I created is not in the sudo list... Therefor I cannot add another user, or really anything that requires administrative privileges. I need a way to get the first user that I create (during the ubuntu install) to become a superuser without the access to a separate superuser account, either that or to enable root without access to a superuser.

No I am not trying to get into someone else's computer's root account... I am trying to get into my own, for some reason it didn't give me superuser access when I installed ubuntu.  Also if it does affect this in any way, I installed it on a playstation.

Any help is much appreciated.

---

### Post by rory526 on 2010-03-25
In Ubuntu, your user login password grants you root privileges.
The root account is not used unlike many other Linux distributions.

Does this solve your problem?

---

### Post by wojox on 2010-03-25
May need to add yourself: [http://ubuntuforums.org/showpost.php?p=7196198&postcount=5](http://ubuntuforums.org/showpost.php?p=7196198&postcount=5)

---

### Post by Tethyrian on 2010-03-25
I know, and when I am on the only account that is on ubuntu, I type in sudo adduser, it asks for my password and I type it in (the one I use to log into ubuntu am I right? or is it a different one?) and it says I am not in the sudoers list...

---

### Post by aysiu on 2010-03-25
> **Tethyrian said:**
> I know, and when I am on the only account that is on ubuntu, I type in sudo adduser, it asks for my password and I type it in (the one I use to log into ubuntu am I right? or is it a different one?) and it says I am not in the sudoers list...
This should help you out:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by sisco311 on 2010-03-25
Is your user in the admin group?

Open a Terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
id
```

EDIT: 
> **Tethyrian said:**
>  Also if it does affect this in any way, I installed it on a playstation.



Yes, it does.
Are you using kboot or petitboot?


EDIT2:

If you are using kboot, then try this:
[http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7](http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7)

---

### Post by rory526 on 2010-03-25
Sorry, I misunderstood.

---

### Post by Tethyrian on 2010-03-25
> **sisco311 said:**
> Is your user in the admin group?

Open a Terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
id
```EDIT: 


Yes, it does.
Are you using kboot or petitboot?


EDIT2:

If you are using kboot, then try this:
[http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7](http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7)
It looks like kboot, but for some reason that still didn't work, feel like I am getting closer though, I will copy and paste a terminal window of me trying to add a user with sudo in a terminal.

Anyways, do you have a fix for petitboot that I could try also I just tried the kboot one you gave me and I am not really sure which I am using. :o?

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ian@ps3ubunty:~$ sudo adduser
[sudo] password for ian: 
ian is not in the sudoers file.  This incident will be reported.
ian@ps3ubunty:~$ id
uid=1000(ian) gid=1000(ian) groups=118(admin),1000(ian)
ian@ps3ubunty:~$ 
ian@ps3ubunty:~$ 


---

### Post by sisco311 on 2010-03-25
kboot is the boot loader. i don't own a ps3, so i don't know exactly how, but when you reboot you should be able to access the kboot prompt, then try  

[http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7](http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7)

or try this forum:
[http://psubuntu.com/forums/viewforum.php?f=1](http://psubuntu.com/forums/viewforum.php?f=1)
I hope they can help you better...

---

### Post by Tethyrian on 2010-03-25
> **sisco311 said:**
> kboot is the boot loader. i don't own a ps3, so i don't know exactly how, but when you reboot you should be able to access the kboot prompt, then try  

[http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7](http://georgia.ubuntuforums.org/showpost.php?p=7360938&postcount=7)

or try this forum:
[http://psubuntu.com/forums/viewforum.php?f=1](http://psubuntu.com/forums/viewforum.php?f=1)
I hope they can help you better...

I got it by following those steps, that guide should include the steps to adding the line in the sudoers file to give the user sudo access. I found it out myself but it would be nice if that included it.

---

### Post by sisco311 on 2010-03-25
nm

---

