---
title: "Two folders seem to be one"
date: 2009-04-13
forum: Server Platforms
---

### Post by wooska on 2009-04-13
I somehow got two of my folders linked together in an odd way.  My /var/www and /home/'user' directories are connected.  If I change the contents in one, the contents of the other change.  I can't figure out what I did to make this happen nor can I figure out how to change it back.  Any help would be appreciated.  BTW, I'm using LAMP with Ubuntu 8.10.

---

### Post by blindmist on 2009-04-13
almost sounds like one is setup as a symbolic link to the other.

if you are on a windows machine, use WinSCP to ftp into it and take a look in the /home/ directory. If the folder has a different icon than the others, almost like a shortcut icon, then there is a symbolic link.

im still a newbie, and i am sure there is a better way, but i know this works. if that seems to be the case, delete which everfolder the link is, and make an actual folder where it should be.

---

### Post by wooska on 2009-04-14
There doesn't seem to be anything different in WinSCP, there was a short time when I had a link (though I think I used a command more like 'bind') from /home/'user' to /var/www/, but when I restarted the server, that went away.  I'm wondering if maybe it is connected to my Samba server.

---

### Post by ad_267 on 2009-04-14
Probably easier to do:

```
ls -l /home/user
ls -l /var/www
```

If one of the directories is a symbolic link it will show this.

---

### Post by wooska on 2009-04-14
Not sure what to look for when doing the ls -l.  I see the permissions and think I have a grasp on them, but don't know what a symbolic link would look like.  I am fairly confident that symbolic links are not my current problem, they may have caused it, but I think there is something deeper going on.

---

### Post by BkkBonanza on 2009-04-14
If it's a symbolic link the permissions will start with **l** rather than **d**. But also a symbolic link will usually show the link rather than the contents of the link unless you add the extra **/** to the end - then it shows the contents.

To remove the link you use **rm /path/of/link** and it will get rid of it. If it's actually a directory it will tell you it cannot remove a directory.

---

### Post by wooska on 2009-04-14
They both seem to be their own folders, I can't remove either one, the permissions are set up so that they appear to be their own, but somehow, they are still connected.

Even the permissions are connected, I change one, and the other changes with it.

---

### Post by bab1 on 2009-04-14
They could be hard linked instead.  A sym link is a reference to the real inode (file table).  A hard link is a second link to the same inode.

Post a listing of:```
ls -l /home
```
and ```
ls -l /var |grep www
```

Here is what a link looks like:```
**[COLOR="Magenta"][COLOR="Blue"]l[/COLOR][/COLOR]**rwxrwxrwx 1 bab bab       11 2008-12-22 10:58 [COLOR="Blue"]rincon -> /smb/rincon[/COLOR]
```

You can read about hard and soft links at:
```
man ln
```

---

### Post by ad_267 on 2009-04-14
You can't have a hard link to a directory, only a file, so that can't be the problem.

---

### Post by wooska on 2009-04-14
Here is the response from ls -l /var |grep www

drwxrwxr-x  2 root karl  4096 2009-04-13 21:34 www

Don't know if this is at all helpful, wondering if there is something even stranger going on.

---

### Post by cariboo on 2009-04-14
You would prpbably be better off cd-ing into /var/www
and then run ls -la in the directory. A sym-linked file will look something like this:

```
lrwxrwxrwx  1 root root     24 2009-02-26 13:51 knowledgeroot -> /usr/share/knowledgeroot
```

Jim

---

### Post by blindmist on 2009-04-14
> **wooska said:**
> Here is the response from ls -l /var
drwxrwxr-x  2 root karl  4096 2009-04-13 21:34 www

Don't know if this is at all helpful, wondering if there is something even stranger going on.

Whats the output for:

```

ls -l /home

```

---

### Post by wooska on 2009-04-14
Well, I tried setting up a mail server, which messed up my web server, and then after removing all the packages I installed for the mail server, the web server had reverted to an earlier version that didn't have this problem, so, I don't know what caused it, but it seems to be working now, thanks for your help.

---

