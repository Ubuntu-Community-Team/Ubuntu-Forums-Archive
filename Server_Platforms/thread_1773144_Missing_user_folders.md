---
title: "Missing user folders"
date: 2011-06-01
forum: Server Platforms
---

### Post by Z.K. on 2011-06-01
I created a new user and when I went to use that user, I noticed that even after logging in, the normal default folders are missing.  The only thing there is the examples.desktop file.  How do I recreate the default folders without recreating the user.  

:?:

---

### Post by Z.K. on 2011-06-01
> **Z.K. said:**
> I created a new user and when I went to use that user, I noticed that even after logging in, the normal default folders are missing.  The only thing there is the examples.desktop file.  How do I recreate the default folders without recreating the user.  

:?:

I figured it out. 

> usermod -d /path/to/new/homedir/ username

:D

---

### Post by Z.K. on 2011-06-01
> **Z.K. said:**
> I figured it out. 



:D

Well, I thought I did.  I tried > sudo usermod -d /home/username username and it came back with > usermod: no changes.  Anyone have any ideas?

:(

---

### Post by ruffEdgz on 2011-06-01
Actually. After re-reading this post and remembering which category I am in, when creating a new user on Ubuntu Server, you should only get the following in the directory:
```

drwxr-xr-x  2 testuser testuser 4096 2011-06-01 17:21 ./
drwxr-xr-x 14 root     root     4096 2011-06-01 17:21 ../
-rw-r--r--  1 testuser testuser  220 2010-04-18 22:15 .bash_logout
-rw-r--r--  1 testuser testuser 3103 2010-04-18 22:15 .bashrc
-rw-r--r--  1 testuser testuser  675 2010-04-18 22:15 .profile

```
If you are talking about the extra directories like **Pictures**, **Music**, etc... You can make those yourself if you like but shouldn't be needed on the server edition of Ubuntu.
```

sudo mkdir -f ~/Music
sudo mkdir -f ~/Pictures
...
...

```

---

### Post by Z.K. on 2011-06-01
> **ruffEdgz said:**
> Actually. After re-reading this post and remembering which category I am in, when creating a new user on Ubuntu Server, you should only get the following in the directory:
```

drwxr-xr-x  2 testuser testuser 4096 2011-06-01 17:21 ./
drwxr-xr-x 14 root     root     4096 2011-06-01 17:21 ../
-rw-r--r--  1 testuser testuser  220 2010-04-18 22:15 .bash_logout
-rw-r--r--  1 testuser testuser 3103 2010-04-18 22:15 .bashrc
-rw-r--r--  1 testuser testuser  675 2010-04-18 22:15 .profile

```
If you are talking about the extra directories like **Pictures**, **Music**, etc... You can make those yourself if you like but shouldn't be needed on the server edition of Ubuntu.
```

sudo mkdir -f ~/Music
sudo mkdir -f ~/Pictures
...
...

```

Yes, that is what I was talking about such as the Downloads directory and all the hidden files you get.  We are using Gnome desktop on top of the server edition.  I guess I should ask this in the desktop forum then.  I am not really concerned about folders I do not use, but there are some hidden folders like the .config and autostart folders that I use to automatically start a script that I use to check for an Internet connection.  

:?:

---

### Post by Z.K. on 2011-06-02
> **Z.K. said:**
> Yes, that is what I was talking about such as the Downloads directory and all the hidden files you get.  We are using Gnome desktop on top of the server edition.  I guess I should ask this in the desktop forum then.  I am not really concerned about folders I do not use, but there are some hidden folders like the .config and autostart folders that I use to automatically start a script that I use to check for an Internet connection.  

:?:

Well I found a solution of a sort.  Since I have more than one identical machine, I just copied the contents of the directory including hidden files and folders and reran my script that needed the autostart directory.  It seems to work okay.

:)

---

### Post by ruffEdgz on 2011-06-02
You could place the contents you want for any new users to be in the /etc/skel/ directory

That directory is what useradd uses by default.

---

