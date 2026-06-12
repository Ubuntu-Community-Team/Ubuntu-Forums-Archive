---
title: "su/gksu don't work, sudo/gksudo do."
date: 2010-11-29
forum: Security
---

### Post by MadnessRed on 2010-11-29
If I try and run a program as admin, sometimes it won't except me root password.
If I run su, or gksu, then it won't accept my password whilst with gksudo or gksu it will.

Any ideas?

---

### Post by bodhi.zazen on 2010-11-29
I suspect it is because you are not using the proper syntax with sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

ubuntu does not use su :p

could be you are mis-typing the password.

---

### Post by cariboo on 2010-11-29
Su does work, but only for switch to a different user other than root. For instance I have two users on my system, one for the forum and one for personal business. If I need to do something as the other user than I just issue the following command:

```
su <otheruser>
```

I get asked for the other users password and off I go as the other user.

---

### Post by MadnessRed on 2010-12-01
> **bodhi.zazen said:**
> I suspect it is because you are not using the proper syntax with sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

ubuntu does not use su :p

could be you are mis-typing the password.

My main issue is that gksu doesn't work. So any programs like synaptic, which I may run as root from the main menu won't work. I have to go into terminal and type sudo synaptic.

---

### Post by CharlesA on 2010-12-01
> **MadnessRed said:**
> My main issue is that gksu doesn't work. So any programs like synaptic, which I may run as root from the main menu won't work. I have to go into terminal and type sudo synaptic.

How do you mean?

```
charles@lucid:~$ ls -al $(which gksu)
-rwxr-xr-x 1 root root 26752 2010-03-04 20:23 [COLOR="Blue"]/usr/bin/gksu[/COLOR]
charles@lucid:~$ ls -al $(which gksudo)
lrwxrwxrwx 1 root root 4 2010-09-12 06:22 [COLOR="Red"]/usr/bin/gksudo -> gksu[/COLOR]

```

What happens when you run ***gksu synaptic*** ?

I tried it on my install of 10.04 and it worked as expected.

---

### Post by bodhi.zazen on 2010-12-01
> **MadnessRed said:**
> My main issue is that gksu doesn't work. So any programs like synaptic, which I may run as root from the main menu won't work. I have to go into terminal and type sudo synaptic.

Open a terminal and enter 

```
gksu synaptic
```

report any error messages. You may need to file a bug report on Launchpad.

---

### Post by MadnessRed on 2010-12-02
> **bodhi.zazen said:**
> Open a terminal and enter 

```
gksu synaptic
```

report any error messages. You may need to file a bug report on Launchpad.

gksu doesn't work. It won't accept my password. This is my problem, I cannot run any program as root, except using sudo which requires terminal to be open for every program.

---

### Post by CharlesA on 2010-12-02
> **MadnessRed said:**
> gksu doesn't work. It won't accept my password. This is my problem, I cannot run any program as root, except using sudo which requires terminal to be open for every program.
Have you tried changing your password in System > Preferences > About Me?

---

### Post by bodhi.zazen on 2010-12-02
> **MadnessRed said:**
> gksu doesn't work. It won't accept my password. This is my problem, I cannot run any program as root, except using sudo which requires terminal to be open for every program.

Are you entering your login password or root password ?

Also you will need to provide more details then simply stating that it is not working.

If you are not getting any messages when you run gksu from your terminal you will need to file a bug report.

---

### Post by MadnessRed on 2010-12-03
> **bodhi.zazen said:**
> Are you entering your login password or root password ?

Also you will need to provide more details then simply stating that it is not working.

If you are not getting any messages when you run gksu from your terminal you will need to file a bug report.

Hi, I gave up an re-installed in the end. It seemed easier as there were a collection of other annoyances too. Everything works fine now.

---

### Post by MadnessRed on 2010-12-03
> **bodhi.zazen said:**
> Are you entering your login password or root password ?

Also you will need to provide more details then simply stating that it is not working.

If you are not getting any messages when you run gksu from your terminal you will need to file a bug report.

Hi, I gave up an re-installed in the end. It seemed easier as there were a collection of other annoyances too. Everything works fine now.

Thanks for all the advice though.

---

### Post by freaxtux on 2011-03-31
Hi, I also experience this problem.
I'm on minimal xubuntu(installed ubuntu with minilmal install CD, and used "sudo aptitude install --without-recommend xubuntu-desktop")
gksudo and sudo works, but gksu and su don't
when I use gksu in terminal, there's no message. the gksu window just dissapears after writing my password. When I write a wrong password, it also closes.
```

park@ubuntu:~$ gksu synaptic
park@ubuntu:~$ 

```
when I use su, it says "authentication failed"(I don't know the exact message since I'm not using English, but it must be a simmilar one.) whether I type the correct password or not.
```

park@ubuntu:~$ su
&#50516;&#54840;:                                //it means "password:"
su: &#51064;&#51613; &#49892;&#54056;                    //it means "su: authentication failed"
park@ubuntu:~$ 

```
I installed minimal xubuntu twice, and the problem occured both time.

---

### Post by CharlesA on 2011-03-31
su won't work by default in Ubuntu since the root account is locked.

You'd use sudo or gksudo to run commands with Gnome. I'm not quite sure if it's the same XFDE.

---

### Post by bodhi.zazen on 2011-04-01
> **CharlesA said:**
> You'd use sudo or gksudo to run commands with Gnome. I'm not quite sure if it's the same XFDE.

It is the same in XFCE ;)

---

### Post by freaxtux on 2011-04-01
su doesn't work on default? well, I almost never used su before, so maybe I misremembered about that. Then, what about gksu? I've always used gksu to run programs superuser mode with Alt+F2, both on Xubuntu(default install) and Ubuntu. And also, I can't run superuser-requiring programs from menu because of the gksu problem.

---

### Post by freaxtux on 2011-04-01
gksu works now that I installed 'menu' package
if gksu works only when the 'menu' package is installed, then shouldn't gksu depend on menu? but menu only suggests gksu, and gksu has no dependency, recommendation, or even a suggestion on menu.
[http://packages.ubuntu.com/maverick/menu](http://packages.ubuntu.com/maverick/menu)
[http://packages.ubuntu.com/maverick/gksu](http://packages.ubuntu.com/maverick/gksu)

---

### Post by Hakunka-Matata on 2011-04-01
You said it works, ....................................... so you had to install the requisites, doh.  Glad  you got that far.  If it's SOLVED, please indicate.

---

