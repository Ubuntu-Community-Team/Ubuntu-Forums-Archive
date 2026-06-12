---
title: "Root vs Sudo [costumization/tweaking]"
date: 2006-03-21
forum: The Cafe
---

### Post by towsonu2003 on 2006-03-21
I saw this on slashdot, and it seems to be relevant to Ubuntu very much, although it's talking about OS X: [http://linuxboxadmin.com/articles/sudo-vs-root.php](http://linuxboxadmin.com/articles/sudo-vs-root.php)

Just to let people know that there seems to be ways to secure sudo more efficiently. For any questions about Ubuntu's root/sudo, go to [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ssam on 2006-03-21
the article seems to imply that its easier to guess/steal a user password than a root password. and that having sudo require a different password from your user password makes it more secure.

i dont really see how this is true.

what would make sudo more secure is not using you sudo enabled account for everyday computing.

also does changing the root shell to /usr/bin/false really stop people loggin in? can't you bypass that with
```
ssh root@hostname /bin/bash
```

---

### Post by towsonu2003 on 2006-03-21
I was more interested in the ideas of "configuring sudo so that some commands are sudo-able while others aren't" + "use passwd other than user's"

So, 
0. leave first created user as the Admin
1. add second user (you)
2. give second user sudo use for commonly used commands (wvdial, apt-get and the like)
3. Use Admin + Other Pass for root stuff. 

This way, second user's pass is no good, Admin's pass is no good, second user can maintain the box, Admin can do its own stuff etc. Layers of protection. 

Have no idea how it would work...

---

### Post by ssam on 2006-03-21
also be careful about what you allow the second user to use. for example if you let them use gedit then they could edit any file. if you allow any shell, or program with a built in shell then they can do anything.

---

### Post by Jucato on 2006-03-21
If sudo is such a risk, then root is also such a risk. They're *almost* the same thing. But which is easier to hack or which one is more likely to be hacked in a Linux system: user password or root password? Won't hackers (the bad kind) immediately try to hack the root password? But since Ubuntu has the root disabled by default, there will be nothing to hack. (Unless of course I'm wrong and hackers target user passwords more than root passwords).

But one thing that still bothers me after I've read the article. How will you be able to log the actions done by "sudo -s"?

---

### Post by engla on 2006-03-21
[QUOTE=Fenyx]But one thing that still bothers me after I've read the article. How will you be able to log the actions done by "sudo -s"?[/QUOTE]
You can look in the file /root/.bash_history Root can of course delete that file, use like root can delete any other log or file on the system.

---

### Post by Jucato on 2006-03-21
just checked that, might be doing something wrong but...
/root/.bash_history only contains commands you used as "sudo su". where do the commands that you use as "sudo -s" go?

EDIT: and what's the difference between sudo su and sudo -s? they give me two different prompts.  sudo su gives me a username@hostname:~#. while sudo -s gives me root@hostname:/home/username#

---

### Post by ssam on 2006-03-21
[QUOTE=Fenyx]and what's the difference between sudo su and sudo -s? they give me two different prompts.  sudo su gives me a username@hostname:~#. while sudo -s gives me root@hostname:/home/username#[/QUOTE]

i think
```
sudo su
```
just changes your user, whereas
```
sudo -s
```
starts a new shell.

i think there are slight difference in terms of environmental variables.

there is also 
```
sudo su -
```
which gives a shell as if the root user had logged in.

i emailed the writer of the original article, and he suggests that having sudo use a different password would slow someone down who had to first break into your user account, and then have to find a second password to get root access.

---

