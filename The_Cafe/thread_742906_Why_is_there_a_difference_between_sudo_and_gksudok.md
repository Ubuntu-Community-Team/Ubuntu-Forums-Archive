---
title: "Why is there a difference between sudo and gksudo/kdesudo?"
date: 2008-04-02
forum: The Cafe
---

### Post by johann_p on 2008-04-02
**Why is there a difference between sudo and gksudo/kdesudo and what exactly are these differences?**

There are several posts that warn that there are differences between using sudo and gksudo/kdesudo for graphical applications. 
People usually link to [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) when they warn about using sudo for graphical applications.

But I have not seen any explanation why there is a difference in the effects in the first place. The only reason for gksudo according to its documentation is that it makes it possible to start a graphical application without having a terminal first. 
Nowhere in its documentation does it state that there is any difference in its effect.

So -- what *exactly* is the difference and why does it exist? Is this a bug? Shouldn't these commands do absolutely identical things when starting a graphical application from the command line?

---

### Post by justleen on 2008-04-02
uh,.. i might me wrong, but there is no difference in effect. Both give sudo rights.

The difference is the terminal, as you say. gksudo gives the nice gnome-popup, sudo needs to be run from a terminal - and then has to be detached from that terminal to prevent the app closing when you close the terminal..
pressing alt-f2 and running sudo just will not work.


AFAIK that is the only diffecerence..

---

### Post by johann_p on 2008-04-02
Well this is what I would have expected, but there are various threads on this forum and the web page I gate ([http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)) which claim the contrary: for example they claim it does make a difference if you use "sudo firefox" or "gksudo firefox" and they claim that using sudo for kde apps could mess up the permissions on some KDE file that even makes it impossible to log in again.

I have never experienced any problem (I always use sudo from the terminal) and I would not have expected any. And I would think that any difference should be regarded as a bug, no?

---

### Post by mozetti on 2008-04-02
The explanation is given right on the page you've linked to twice: sometimes if you use sudo it could changes the permissions to 'root'. So, before using sudo the user could run the program, but after using sudo the user can't run the program correctly because the permissions were changed to 'root'. I would guess that it's a good idea to provide the safest method when giving a tutorial, so gksu/gksudo would be that safest method.

Also, the gksu/gksudo man page says the purpose of the tool is to be able to run GUI applications with root access without the need for a terminal. I guess this would infer that the permissions problem would be a bug.

---

### Post by justleen on 2008-04-02
hmm. reading that [thread,]("http://www.mail-archive.com/arch@archlinux.org/msg04963.html") i boils down to
> ..  sudo is unaware of X permissions, and g/k sudo are... 
thus, sudo just grabs whatever it needs, and that can mean chaning ownership.

g/k sudo use root's settings/config files, thus not changing permissions (they are already root's)
hmm... though i never had any problems with this, it is good to know.

---

### Post by johann_p on 2008-04-02
> **mozetti said:**
> The explanation is given right on the page you've linked to twice: sometimes if you use sudo it could changes the permissions to 'root'.


OK, I have read this, but it is more a description of a symptom than an explanation of why this difference exists.

Conceptually I think that either sudo or (less likely) gksudo are doing something wrong here. From the user's perspective both SHOULD do exactly the same thing and only differ in that dksudo can run an application without a terminal. I think it is extremely bad for the users having to be aware of such subtle differences.

> 
Also, the gksu/gksudo man page says the purpose of the tool is to be able to run GUI applications with root access without the need for a terminal. I guess this would infer that the permissions problem would be a bug.

Yes, that is what I thought too.

---

### Post by anaconda on 2008-04-02
I always thought that the only difference is that gksudo/kdesudo does have a graphical way to aks for a sudo password. Sudo doesn't have that option.

If needed you could always get the same effect with:
```
sudo ls
sudio xxxxxxx
```
so that when you run the second command sudo wont need password anymore and so it wont need a graphical way to ask sudo password either..

---

### Post by justleen on 2008-04-02
well.. the difference is in the fact that gksudo knows you want to do something as root, and links all "X activity" to /root/
sudo doenst, it will use your /home/user/ files 
Hence the described problem with ICEauth, sudo just grabs the /home/user/.ICEauth file, and changes it onwership (since the file is rw by owner only). 
gksudo takes this into account, and redirects to /root/.ICEauth

what i've read so far (since your post :) ) is that gksudo is "slighty more advanced" then sudo when in X,  to prevent this scenario. 
Sudo is working as designed, gksudo is an extenstion to prevent some "working as designed" habbits of sudo.

---

### Post by johann_p on 2008-04-02
> **justleen said:**
> hmm. reading that [thread,]("http://www.mail-archive.com/arch@archlinux.org/msg04963.html") i boils down to

thus, sudo just grabs whatever it needs, and that can mean chaning ownership.

g/k sudo use root's settings/config files, thus not changing permissions (they are already root's)
hmm... though i never had any problems with this, it is good to know.

I am afraid I still do not get it: what is so special or what exactly are "X permissions"? I thought there just are file pemissions (as everything in linux is essentially a file) and that the problem described is an issue of setting some file permissions wrongly. So why do sudo and gksudo deal with this differently?

Both commands execute another command in the context of the root user, no?
If I do "sudo whoami" I get root and if I do "gksudo whoami" I also get root.
Why then would a command run under sudo change permissions to root and the same command run under gksudo/kdesudo not do this?

I know that the traditional explanation for this is "because thats how it is", but I must say, that explanation does not really satisfy me.

---

### Post by justleen on 2008-04-02
ok, i've said that wrong..
Not X perrmissions, but X enviorment variables. 

when you startx, it will need a .Xauth to be user owned, rw by the user.
when you start X with sudo startx, the ownership of that file will change, thus not allowing you to start X as a user..

```

sudo env > sudo_env.txt
gksudo env > gksudo_env.txt
diff  sudo_env.txt  gksudo_env.txt

```

---

### Post by johann_p on 2008-04-02
> **justleen said:**
> well.. the difference is in the fact that gksudo knows you want to do something as root, and links all "X activity" to /root/
sudo doenst, it will use your /home/user/ files 
Hence the described problem with ICEauth, sudo just grabs the /home/user/.ICEauth file, and changes it onwership (since the file is rw by owner only). 
gksudo takes this into account, and redirects to /root/.ICEauth

what i've read so far (since your post :) ) is that gksudo is "slighty more advanced" then sudo when in X,  to prevent this scenario. 
Sudo is working as designed, gksudo is an extenstion to prevent some "working as designed" habbits of sudo.

Thank you -- I think I understand that now. I wrote a little script with these lines:
```

#!/bin/bash

echo ~
echo $HOME
whoami

```and then I run it with sudo and gksudo/kdesudo:
```

sudo ./t1.sh
/home/johann
/home/johann
root

gksudo ./t1.sh
/root
/root
root

kdesudo ./t1.sh
/root
/root
root

```So sudo simply does not change the homedirectory. I think this is not only relevant for X/graphical applications: any program that changes stuff based on a home directory will do stuff wrong if run with sudo, no? So any program that creates files or changes permissions might do this in the user's directory instead of the root home directory.

How is this not a bug in sudo?
That difference is rather subtle though because if some program would simply change the permission of any file in

---

### Post by johann_p on 2008-04-02
> **justleen said:**
> ok, i've said that wrong..
Not X perrmissions, but X enviorment variables. 

when you startx, it will need a .Xauth to be user owned, rw by the user.
when you start X with sudo startx, the ownership of that file will change, thus not allowing you to start X as a user..

```

sudo env > sudo_env.txt
gksudo env > gksudo_env.txt
diff  sudo_env.txt  gksudo_env.txt

```

Ah ok .. that provides even more insight than my little script, thanks!

---

### Post by justleen on 2008-04-02
yea that is what i've come to realize as well, any prog that modifies permission in $HOME (which is user or root..) might break when change from user to root

if you run without X (in a "real" terminal) and do the diff of the env variables, you will see $HOME is set both to /home/leen (in mycase)
the username is diffent though. So yea, any modifcation in $HOME done by root, will be done in /home/leen

solution: sudo su :)


this does bring to mind: the usefullnes of sudo as "safety feature"

rm -rf / as root is bad..
sudo rm -rf /  is just as bad.. 

if you know my useraccount + passwd, you got root rights (sudo passwd root).. why would that be safer then no sudo and seperate root account (plus a wheel group for admins rights..)?

---

### Post by cdenley on 2008-04-02
```

cdenley@ubuntu:~$ sudo ./home.sh
/home/cdenley
/home/cdenley
root
cdenley@ubuntu:~$ sudo -H ./home.sh
/root
/root
root

```

---

### Post by justleen on 2008-04-02
Ahhhhh Cheers for that cdenley!

(the man page actually states this quite obviously.. Dough!)

---

### Post by bodhi.zazen on 2008-04-02
You all seem on the correct track. The difference is not root (admin) access per se, but the environmental variables.

Look at the difference between sudo -s and sudo -i.

Both give you root. sudo -s uses your User (Bash) Environmental Variables, such as $HOME and alises (anythig in ~/.bashrc). sudo -i uses root's Environmental Variables (/root/.bashrc for example). gksu / kdesu is similar to sudo -i.

BUT, in addition, gksu / kdesu give access to X. You can of course access X via sudo, but you may need to configure sudo options if you have problems. (This has to do with security of X and limiting access prevents key loggers for example).

If you use sudo to access X applications you may need to add this option at the end of the "Defaults" line in /etc/sudoers (edit with sudo visudo) :

> env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

So, gksu / kdesu give: 
1. Root access.
2. Root's environmental variables.
3. Access to X (in a more sane and secure way).

HTH

---

