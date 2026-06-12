---
title: "Jail SSH"
date: 2013-04-08
forum: Server Platforms
---

### Post by pedrommone on 2013-04-08
Hello, Im new at linux and Im trying to deny any user intertact when he's connected into my server SSH. I just want display some information on SSH Terminal, but if the user press ctrl + C, it closes my bash script. The point is, I want remove all users permission so he cant "stop" my bash. Thank you.

---

### Post by darkod on 2013-04-08
But you do want to allow users to connect by SSH?

---

### Post by pedrommone on 2013-04-08
Yea, they are connecting normally, my bash is running for every user! I just want to 'freeze' this interaction with shell.

---

### Post by CharlesA on 2013-04-08
What is the purpose of allowing them SSH access?

---

### Post by pedrommone on 2013-04-08
SSH Tunneling

---

### Post by CharlesA on 2013-04-08
> **pedrommone said:**
> SSH Tunneling

Thought so.

[http://ubuntuforums.org/showthread.php?t=1809338](http://ubuntuforums.org/showthread.php?t=1809338)

---

### Post by pedrommone on 2013-04-08
Do you know something can help me?

---

### Post by CharlesA on 2013-04-08
> **pedrommone said:**
> Do you know something can help me?

In the link I posted above there are three different ways to control what a user has access to. I have an application that I run headless but sometimes I need to access a GUI for it via SSH, so I use a shell script for the user's shell.

Otherwise check this page out, which uses rbash:
[http://www.ab-weblog.com/en/creating-a-restricted-ssh-user-for-ssh-tunneling-only/](http://www.ab-weblog.com/en/creating-a-restricted-ssh-user-for-ssh-tunneling-only/)

---

### Post by pedrommone on 2013-04-08
Currently Im using pam-mysql for user authentication, it will work for it too?

---

### Post by CharlesA on 2013-04-08
> **pedrommone said:**
> Currently Im using pam-mysql for user authentication, it will work for it too?

I haven't tried that configuration before. Does that mean your users are stored in a database?

If so, this might help (maybe).
[http://www.spencerstirling.com/computergeek/mysqluser.html](http://www.spencerstirling.com/computergeek/mysqluser.html)

You would just need to change whatever shell the user you are allowing to tunnel is using.

---

### Post by pedrommone on 2013-04-08
Yep

---

### Post by CharlesA on 2013-04-08
> **pedrommone said:**
> Yep

Ok, since that is the case, you would just need to update the shell column in SQL, but how to do that depends on how you have it set up, and you would need to install rbash if it isn't already installed.

```
sudo apt-get install rbash
```

---

### Post by pedrommone on 2013-04-08
The pam-mysql is working well, my user check-in is working well too, my only problem is the that the users can press ctrl + c and stop my bash and access the whole system..

---

### Post by CharlesA on 2013-04-08
> **pedrommone said:**
> The pam-mysql is working well, my user check-in is working well too, my only problem is the that the users can press ctrl + c and stop my bash and access the whole system..

Ah ok.

Check this out:
[http://www.cyberciti.biz/faq/unix-linux-shell-scripting-disable-controlc/](http://www.cyberciti.biz/faq/unix-linux-shell-scripting-disable-controlc/)

If they can access the whole system, are they not confined to their home directories via rbash, or another means?

---

### Post by pedrommone on 2013-04-08
Reading package lists... Done
ubuntu@ip-10-252-146-2:~$ sudo apt-get install rbash
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package rbash

Little problem here >.<

---

### Post by pedrommone on 2013-04-08
> **CharlesA said:**
> Ah ok.

Check this out:
[http://www.cyberciti.biz/faq/unix-linux-shell-scripting-disable-controlc/](http://www.cyberciti.biz/faq/unix-linux-shell-scripting-disable-controlc/)

If they can access the whole system, are they not confined to their home directories via rbash, or another means?

Thank you, worked very well! Now, how can I disable this green ****?

[IMG]http://i.imgur.com/QzlJROy.jpg[/IMG]

---

### Post by CharlesA on 2013-04-08
> **pedrommone said:**
> Thank you, worked very well! Now, how can I disable this green ****?

[IMG]http://i.imgur.com/QzlJROy.jpg[/IMG]

Is that where the cursor is? I don't think you can get rid of it.

---

### Post by pedrommone on 2013-04-08
Yes, it is, btw, how to disable all user key binds from start of the session?

---

