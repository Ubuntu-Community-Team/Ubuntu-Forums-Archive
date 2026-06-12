---
title: "I can not login as root via SSH,but local login works (PermitRootLogin is set to yes)"
date: 2014-06-04
forum: Server Platforms
---

### Post by aliyevzaur1989 on 2014-06-04
Hi. I am new to this forum, so if asked question to wrong section please, do not judge me. And i am not from English-speaking country. So forgive my mistakes.

Here is my problem.

I can login to "root" on machine locally, which runs Ubuntu 14.04.  I type in root and then password and viola. I logged in as expected. Bur when i try to login from another Linux machine (Mint) i can not log in with root user. Strangely i can log in with another accounts from ssh. And as the title says, PermitRootLogin is set to yes.. What is the problem here? Can anyone help me?

---

### Post by sudodus on 2014-06-04
In order to avoid

- destroying important data files or
- Ubuntu itself by mistake or
- making it easier than necessary for intruders,

 we do not encourage logging in a root.

Instead we run as regular users, and when necessary, raise the privileges temporarily with sudo (for command line programs) or gksudo (for graphical user interface programs).

I suggest that you try to run your Ubuntu like that too.

---

### Post by coffeecat on 2014-06-04
@aliyevzaur1989, you need to read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **aliyevzaur1989 said:**
> 
I can login to "root" on machine locally, which runs Ubuntu 14.04.  I type in root and then password and viola. I logged in as expected. 

Please clarify. Do you mean that you have configured your system to log into a graphical desktop as root, or that you are logging into a terminal session as root?

---

### Post by nothingspecial on 2014-06-04
Why are you logging in to the root account?

```
sudo -i
``` will give you a root shell. Don't forget to switch back and don't do anything if you don't know exactly what it's going to do.

---

### Post by aliyevzaur1989 on 2014-06-04
> **coffeecat said:**
> @aliyevzaur1989, you need to read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)



Please clarify. Do you mean that you have configured your system to log into a graphical desktop as root, or that you are logging into a terminal session as root?


I am not sure if i can log in into graphical desktop (i am now far away from that computer) but i am completely sure that i have logged in with CLI as root.

---

### Post by coffeecat on 2014-06-05
> **aliyevzaur1989 said:**
> I am not sure if i can log in into graphical desktop (i am now far away from that computer) but i am completely sure that i have logged in with CLI as root.

The way you worded your original post sounded as though you were logging into a root graphical desktop, which is very inadvisable and not supported on this forum. The link I posted tells you how to enable the root account so that you can log into a root shell (not a root graphical desktop) but also cautions that this is unnecessary because, as nothingspecial has pointed out, you can get a root shell simply by using "sudo -i". However, your "I type in root and then password" suggests that you have configured your system in a different way from the default. As whatever you have done may affect your ability to login via ssh, you need to clarify all these points so that people can help you.

---

### Post by aliyevzaur1989 on 2014-06-06
Thank you all. I figured out what was the problem. Thanks

---

