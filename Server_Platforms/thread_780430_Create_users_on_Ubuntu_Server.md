---
title: "Create users on Ubuntu Server"
date: 2008-05-03
forum: Server Platforms
---

### Post by dJnEvS on 2008-05-03
Hello,

I have created a new user on my Ubuntu Server 7.10
using the following commands:
```

sudo useradd -d /home/username -m username
sudo passwd username

```

but when I logon to the new user
The only thing i see is the $
I can do anything
But i dont see the path of where i'm at currently
and when pressing arrow up i'm scrolling lines..
```

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
$ _

```

arrow up:
```

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
ap_p_licable law.
$ 

```


But when i login as administrator I get this:
```

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail
administrator@server:~$ _

```
How can I fix this?

Thanks in advance
djnevs

---

### Post by PseudoOne on 2008-05-03
I followed your exact steps on my server:

```

webmaster@wikifiles.ath.cx:/var/www$ sudo useradd -d /home/username -m username
[sudo] password for webmaster:
webmaster@wikifiles.ath.cx:/var/www$ sudo passwd username
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
webmaster@wikifiles.ath.cx:/var/www$ su username
Password:
$

```

and then everything I type after that, such as:

```

$ ls
[...]files[...]
$

```

do you get anything similar? Perhaps you may upgrade your version of Ubuntu, preferably to Gutsy -> Hardy.

Else what I tried for a wizard based console was: ```
adduser username
```
instead of useradd username.

I found that this command is much more efficient than it's reciprocal.

---

### Post by dJnEvS on 2008-05-03
Yea thats exactly what I get!
But I want all my users to be able to do and see anything..
Like, now I only see the $ in command line
and I would like it to be user@server:/path/where/they/are$

---

### Post by PseudoOne on 2008-05-03
I am able to get 
```

username@wikifiles.ath.cx:/var/www$

```

after using the adduser command.  Are you able to confirm this?

---

### Post by dJnEvS on 2008-05-03
No, I only see the dollar sign
```

$

```

---

### Post by dJnEvS on 2008-05-03
> **PseudoOne said:**
> Else what I tried for a wizard based console was: ```
adduser username
```
instead of useradd username.

I found that this command is much more efficient than it's reciprocal.

Ahh, that was the problem
I didnt read this post correctly until now.


It's fixed now.
Thank you!

---

### Post by JasonFWard on 2010-12-05
I know this is an ancient thread, but I have exactly the same problem.

I created a new user based on this [http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

But the command history, coloured file listings, tab key all don't work as you would expect them to.

How do I fix it so that a newly created user works exactly like the original user created by the setup?

---

### Post by CharlesA on 2010-12-05
It's likely that you didn't create the home directory when you added the user.

You can create it yourself, or just delete that user and create it again with adduser:

```
sudo adduser username
```

---

### Post by JasonFWard on 2010-12-05
No, created with

```
sudo useradd -d /home/gt -m gt
``` and when I login ```
$ pwd
/home/gt
```But if this isn't what you expect then maybe its something the [Turnkey](http://www.turnkeylinux.org/) guys have done.  I'll ask on their forums.

---

### Post by CharlesA on 2010-12-05
When using useradd -d, it only sets where the user's home directory is going to be. It doesn't create it. You'd have to create it manually from /etc/skel:

```
sudo cp -a /etc/skel /home/gt
sudo chown user:user -R /home/gt
```

I use adduser since it creates the home directory automagically. :)

---

### Post by JasonFWard on 2010-12-05
Very strange, the command created the directory for me.

Over on the [Turnkey forums](http://www.turnkeylinux.org/forum/support/20101205/lamp-new-user-problem) they have suggested I use ```
useradd --create-home --shell=/bin/bash gt
```and that seems to be working great. :p

---

### Post by CharlesA on 2010-12-05
Hrm. Interesting.

Glad you got it working. :)

---

### Post by sisco311 on 2010-12-05
> **JasonFWard said:**
> Very strange, the command created the directory for me.

Over on the [Turnkey forums](http://www.turnkeylinux.org/forum/support/20101205/lamp-new-user-problem) they have suggested I use ```
useradd --create-home --shell=/bin/bash gt
```and that seems to be working great. :p

Yep, if no shell is specified useradd defaults to /bin/sh (which is a symbolic link to /bin/dash - [Debian Almquist shell]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"))

---

### Post by egpetrich on 2010-12-06
Special shell prompts and colored directory listings need to be defined in special login scripts. For most users, the files are "~/.bashrc" and "~/.profile". (You won't see these files unless you use the command "ls -a".)

Someone talked about "/etc/skel". This is a "skeleton" directory with default copies of useful files. I guess the "adduser" command is supposed to populate a new directory from "/etc/skel". My "/etc/skel" directory looks like this (10.04.1 LTS):
```

user@server:~$ ls -la /etc/skel
total 28
drwxr-xr-x   2 root root  4096 2010-11-23 21:53 .
drwxr-xr-x 101 root root 12288 2010-12-02 14:41 ..
-rw-r--r--   1 root root   220 2009-09-13 22:09 .bash_logout
-rw-r--r--   1 root root  3103 2010-04-18 18:51 .bashrc
-rw-r--r--   1 root root   675 2009-09-13 22:09 .profile

```

---

