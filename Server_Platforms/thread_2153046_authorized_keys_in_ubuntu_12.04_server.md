---
title: "authorized_keys in ubuntu 12.04 server"
date: 2013-06-09
forum: Server Platforms
---

### Post by n8nt on 2013-06-09
I am trying to configure gitolite but one of the first steps is to create a private/public key pair on my local machine then copy it down to the root's ~/.ssh folder. I successfully created the two keys and used the scp command to copy the .pub file to the server. The second step is to go to the server and copy that pub key to the gitolite .ssh folder.

Problem is I can't find the .ssh folder in either the gitolite or my root folder.

To be somewhat clearer, when I say "root folder" I'm talking about my default server user which I configured when I installed the server. That user is bobt. Here are the steps I took:

on my local machine I generated the two key files:
**ssh-keygen -t rsa -f gitolite**

this generated 2 files called gitolite and gitolite.pub

Next I used scp to copy these files to my server:

**scp gitolite.pub bobt@myserver **

I got no error when this completed.

Next I went to the server and logged in with my default account of bobt

I did a change directory to get to my home folder.
[B]cd
[/B] 
from here I did an ls to see what was there:

**ls -l -a**

but all I get is:

bobt@datv:~$ bobt@datv:~$ ls -l -a
total 36
drwxr-xr-x 4 bobt bobt 4096 Jun  9 23:33 .
drwxr-xr-x 5 root root 4096 Jun  9 23:00 ..
-rw------- 1 bobt bobt 1743 Jun  9 22:49 .bash_history
-rw-r--r-- 1 bobt bobt  220 Jun  9 17:49 .bash_logout
-rw-r--r-- 1 bobt bobt 3486 Jun  9 17:49 .bashrc
drwx------ 2 bobt bobt 4096 Jun  9 17:50 .cache
-rw-r--r-- 1 bobt bobt  675 Jun  9 17:49 .profile
drwxr-xr-x 2 bobt bobt 4096 Jun  9 22:35 .vim
-rw------- 1 root root 3572 Jun  9 23:33 .viminfo
bobt@datv:~$

there is no .ssh folder to be found.
So, where did the file go that I copied with the scp?


When I installed the server I answered "NO" to the question that came up asking if I wanted to encrypt the home directory. But, this is acting as if the HOME DIrectory is encrypted. How do I tell if it is? Or do I have to create the .ssh folder underneath in the first place?

Thanks,
Bob

---

### Post by newbie-user on 2013-06-11
The .ssh folder is created when you SSH from the server to another computer.

When using scp, you need to specify a destination folder:
```
scp gitolite.pub bobt@myserver:/path/to/folder/ 
```

To get to the root folder,
```
sudo su
```
then type in your password. You'll end up in the root account. Then:
```
cd ~
```
to get to root's home folder. SSH from root to another computer to create the .ssh folder for root. Then create the authorized_keys file:
```
cat /path/to/gitolite.pub > /root/.ssh/authorized_keys
```


Edit:
Sorry didn't read your post carefully enough. SSH out from your bobt account on your server to create the .ssh folder. Then:
```
scp gitolite.pub bobt@myserver:/home/bobt/.ssh/
```
Now on the server, use the .pub file to create the authorized_keys file:
```
cat /home/bobt/.ssh/gitolite.pub > /home/bobt/.ssh/authorized_keys
```

---

