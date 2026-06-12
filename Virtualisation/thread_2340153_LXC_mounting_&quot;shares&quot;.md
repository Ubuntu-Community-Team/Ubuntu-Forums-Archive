---
title: "LXC mounting &quot;shares&quot;"
date: 2016-10-16
forum: Virtualisation
---

### Post by izznogooood on 2016-10-16
When you create a new LXC in 16.04 with an ubuntu system you get an 16.04 with a default user named ubuntu.

When you add the line:

```
lxc.mount.entry = /path/to/share /relative/path/to/lxc/fs none bind 0 0

```

to lxc config the share is mounted with user:group ubuntu:ubuntu and not the propper owner.

Why?

EDIT: 

I should ad I´ve googled and read for hours without finding any documentation as to why it chooses the user "ubuntu".

---

### Post by redger on 2016-10-16
what are you trying to achieve ie. what would you like to occur ? Do you want write access to the share ?
Basically the kernel is remapping the share into the new cgroups space, with appropriate permissions.
To be able to write to the mapped data see this post [https://ubuntuforums.org/showthread.php?t=2322924]("https://ubuntuforums.org/showthread.php?t=2322924")

---

### Post by izznogooood on 2016-10-17
I just want to understand, I can write just fine.

But the whole thing doesn't make sense. Mainly because I cant find documentation on why it's like this.

Lets say i make a new directory in my share:

```
anders@lenox:~$ sudo lxc-console -n mediaserver


Connected to tty 1
                  Type <Ctrl+a q> to exit the console, <Ctrl+a Ctrl+a> to enter Ctrl+a itself


Ubuntu 16.04.1 LTS mediaserver pts/0


mediaserver login: ubuntu
Password: 
Last login: Sun Oct 16 22:20:20 CEST 2016 from 10.0.1.52 on pts/4
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.8.1-040801-generic x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

ubuntu@mediaserver:~$ lls /media
total 40K
drwxr-xr-x  4 ubuntu ubuntu 4.0K Oct 16 19:27 Downloads
drwx------  2 root   root   4.0K Apr  8  2016 lost+found
drwxrwxr-x  5 ubuntu ubuntu 4.0K Oct 16 19:17 Manual Backup
drwxrwxr-x  3 ubuntu ubuntu 4.0K Oct 16 12:14 mediaserver
drwxr-xr-x  8 ubuntu ubuntu  12K Oct 15 14:46 movies
drwxrwxr-x 10 ubuntu ubuntu 4.0K Oct 14 19:24 Software
drwxrwxrwx  2 ubuntu ubuntu 4.0K Oct 16 12:34 tmp
drwxr-xr-x 23 ubuntu ubuntu 4.0K Oct 16 19:05 tvshows
ubuntu@mediaserver:~$ mkdir /media/test
ubuntu@mediaserver:~$ lls /media
total 44K
drwxr-xr-x  4 ubuntu ubuntu 4.0K Oct 16 19:27 Downloads
drwx------  2 root   root   4.0K Apr  8  2016 lost+found
drwxrwxr-x  5 ubuntu ubuntu 4.0K Oct 16 19:17 Manual Backup
drwxrwxr-x  3 ubuntu ubuntu 4.0K Oct 16 12:14 mediaserver
drwxr-xr-x  8 ubuntu ubuntu  12K Oct 15 14:46 movies
drwxrwxr-x 10 ubuntu ubuntu 4.0K Oct 14 19:24 Software
***_drwxrwxr-x  2 ubuntu ubuntu 4.0K Oct 17 17:47 test_***
drwxrwxrwx  2 ubuntu ubuntu 4.0K Oct 16 12:34 tmp
drwxr-xr-x 23 ubuntu ubuntu 4.0K Oct 16 19:05 tvshows
ubuntu@mediaserver:~$ exit
logout


Ubuntu 16.04.1 LTS mediaserver pts/0


mediaserver login: anders@lenox:~$ 
anders@lenox:~$ lls /media/2TB/
total 44K
drwxr-xr-x  4 anders anders 4,0K okt.  16 19:27 Downloads
drwx------  2 root   root   4,0K april  8  2016 lost+found
drwxrwxr-x  5 anders anders 4,0K okt.  16 19:17 Manual Backup
drwxrwxr-x  3 anders anders 4,0K okt.  16 12:14 mediaserver
drwxr-xr-x  8 anders anders  12K okt.  15 14:46 movies
drwxrwxr-x 10 anders anders 4,0K okt.  14 19:24 Software
**_*drwxrwxr-x  2 anders anders 4,0K okt.  17 17:47 test*_**
drwxrwxrwx  2 anders anders 4,0K okt.  16 12:34 tmp
drwxr-xr-x 23 anders anders 4,0K okt.  16 19:05 tvshows
_***anders@lenox:~$ rm -fr /media/2TB/test***_
anders@lenox:~$
```

When I exit my share It's owned by my user. I just want to understand.
I also tried making a different user in my lxc and create a directory. When I restart the container the ownership on the share is still "ubuntu".

Edit: Could it be that ubuntu and myuser is both user nr #1 on each respective system?

---

### Post by izznogooood on 2016-10-25
So, I´ve been digging and digging and cant find suitable documentation on LXC at all.

Does anyone have any experience with LXC and shares with the host system, or should I move on to LXD?

To clarify the problem: I have some idea how LXC decides ownership of the shares i add, but that will always differ from the user nr on the host thus never giving me wanted control.

Right now I´ve moved a S*** load of servers in one LXC and was planning on making this my "travelbag" to 16.10, but now I´m not so sure...

---

