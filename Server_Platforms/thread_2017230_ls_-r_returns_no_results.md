---
title: "ls -r returns no results"
date: 2012-07-04
forum: Server Platforms
---

### Post by nat45928 on 2012-07-04
Hi,

Im using ubuntu 11.04 server edition and when i run the command "ls -r" as a root user after jsut calling "cd" it simply returns nothing, if i call "cd /etc" then "ls -r" it returns all the files and folders in the etc directory, i tried a restart, what is going on???

Nat

---

### Post by cryptotheslow on 2012-07-05
If you are genuinely logging in as root or su'ing on Ubuntu then your current directory will be changed to root's home directory which is /root.

There are no files in that directory that will show up in a normal ls result. Try using ls -ar to show hidden files/directories also.

This should give you an idea:

```

crypto@ubuserver:~$ sudo su -    **## take an interactive root session**

root@ubuserver:~# ls             **## N.B. dir is now ~ (home) for user root**

root@ubuserver:~# pwd            **## Where is root's home?**
/root

root@ubuserver:~# ls -ar         **## no output from the above ls use -a with ls to include hidden**
.VirtualBox  .profile  .debtags  .bashrc  .bash_history  .aptitude  ..  .

root@ubuserver:~# ls -r /etc     **## ls /etc without cd'ing there first without -a**
zsh_command_not_found  popularity-contest.conf  hosts.allow
xml                    pm                       hosts
X11                    perl                     hostname
wpa_supplicant         passwd-                  host.conf
wgetrc                 passwd                   hdparm.conf
w3m                    pam.d                    gshadow-
vim                    pam.conf                 gshadow
vbox                   opt                      grub.d
.......... <snipped>

```You don't need to cd to a directory to ls it.

---

### Post by nat45928 on 2012-07-05
sorry if that message was a little confusing, i know that if i am in the root directory( / ) of the server there should be a list of directories (Eg: etc, home, etc.) and files yet running the ls command returns nothing even though i know it should return something. Why is this the main problem here is i cant look up a directory that i know exists (/Shares/web) but i know it does exits because my web servers files are in that directory and my websites come up fine.

---

### Post by cryptotheslow on 2012-07-05
But what directory are you in when you try the initial cd and ls ? The cd command with no arguments does nothing - it's like saying "change directory nowhere" so you go nowhere - remain where you are.

If you just logged in or su'd to root then you are in /root **not** the root directory of the filesystem /

Use the pwd command to work out where you are or:
```

cd / && ls -r

```

or

```

ls -r /

```Remember the user "root" has their home directory in /root not in the root of the filesystem which is /

---

### Post by drmrgd on 2012-07-05
> **cryptotheslow said:**
> But what directory are you in when you try the initial cd and ls ? The cd command with no arguments does nothing - it's like saying "change directory nowhere" so you go nowhere - remain where you are.

If you just logged in or su'd to root then you are in /root **not** the root directory of the filesystem /

Use the pwd command to work out where you are or:
```

cd / && ls -r

```

or

```

ls -r /

```Remember the user "root" has their home directory in /root not in the root of the filesystem which is /

Actually, if you just type 'cd', it's a shortcut to the user's home directory, which in the case of root would be /root.  So, if you're running:

```
1.  cd
2.  ls -r
```

you'll probably not see anything (unless of course you put something in root's home directory). 

cryptotheslow is correct in saying that '/root' is not at all the same as '/', and if you are trying to list the contents of '/' in this way, you can either run:

```
ls -r /
```

or if you really need to change directory, then run this before you run your 'ls -r' command:

```
cd /
``` 

Again, as cryptotheslow says, verify where you are by running 'pwd'.  That will help you clear up confusion in terms of where you are in the file system when you're running these commands.

---

