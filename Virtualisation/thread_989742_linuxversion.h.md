---
title: "linux/version.h"
date: 2008-11-21
forum: Virtualisation
---

### Post by quikone8 on 2008-11-21
Hi I am installing vmware and it is telling me I need linux/version.h.  What is it, where do I find it or how do I install it.  I assume it is part of the kernel.

---

### Post by pytheas22 on 2008-11-21
You should have a file called version.h at /usr/src/linux-headers-**[kernel version]**/include/linux/version.h  Type 'locate version.h | grep linux' if you want the exact path.

But I'm also wondering what exactly you're trying to do.  There should be packages available for installing VMware player (not sure about the full version, but there are probably packages for that as well), so you probably don't need to be working as hard as you are to get VMware installed.

Maybe you know about the packages and have a specific reason for installing VMware in the way you are, but if you're new to Ubuntu and want more information on the normal way to install VMware, let me know.

---

### Post by quikone8 on 2008-11-24
What I am trying to accomplish is a way to run both a mail server and a web server on the same machine.  Since they both want the use of localhost, I thought the only way to accomplish this is to install and operate the web server on a virtual host and leave the mail server on the physical host were it is currently running.

Thanks for any advice.

---

### Post by pytheas22 on 2008-11-25
I've never set up a mail server on Ubuntu (I have installed Apache), but you should definitely be able to have both mail and http running on the same machine--no need for virtualization.  Just install the mail and web servers:
```

sudo apt-get install apache postfix
```

(you don't necessarily need to use apache and postfix; you can use whichever web and mail-server applications you want).  Then configure them, and you should be all set.  They can both use localhost at the same time; this is not a problem, as far as I know.

You could also try posting about this in the server section of this site, where you'll find people who know more about configuring mail and web servers than I do.

---

### Post by quikone8 on 2008-11-25
Thanks,

So far I have not received much help there, I wonder if the problem I am having is due to the fact that I am using a packaged mail server, Citadel.  I have had that running for about a year now with very few problems, but when I try to install and run LAMP for some reason I can't get MYSQL to cooperate.  Even if I try something like Webmin I run into a problem with localhost and 127.0.0.1.  I try to configure MYSQL but instead I get into the web host for Citadel.  I am going to sign off for the night, but if you have any further ideas, I would love to try them.

Ron

---

### Post by pytheas22 on 2008-11-25
I don't have experience with Webmin so I'm not sure why it doesn't want to let you configure MySQL.  But maybe you'd have better luck if you tried entering a MySQL shell from the command line?  In other words, what happens if you just type 'sudo mysql'?

---

### Post by quikone8 on 2008-11-25
> **pytheas22 said:**
> I don't have experience with Webmin so I'm not sure why it doesn't want to let you configure MySQL.  But maybe you'd have better luck if you tried entering a MySQL shell from the command line?  In other words, what happens if you just type 'sudo mysql'?

I get this: sudo mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by pytheas22 on 2008-11-26
When you installed mysql, did you set it up for root to have access?  If not, you must have a created a different user account to access it.  In that case, you should open a shell by typing:
```

mysql -u *username* -p
```

It will prompt you for that user's password.

It might also work to type:
```

sudo mysql -p
```

and give it your normal user password when asked.

But again, I don't know very much about these things.  You'd have a better shot in the server subforum, if you can get a response there.  Otherwise I'm happy to keep helping; I'm just worried that I'm not the most qualified to give you the advice you need.

---

