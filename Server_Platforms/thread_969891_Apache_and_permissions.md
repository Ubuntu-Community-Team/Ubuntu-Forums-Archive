---
title: "Apache and permissions"
date: 2008-11-03
forum: Server Platforms
---

### Post by flip79 on 2008-11-03
Hello and sorry for my english, but I'm Italian... ):P

I have a couple of... academic doubts about the management of my web server  (it's a CentOS server, but anyway our Ubuntu desktops are from the same happy family :KS):

- I have this CentOS server in a webfarm, pre-partitioned with its big /home and the rest of the system (/) in a little partition of about 4Gb. Well, let's start from the presupposition that I don't want to re-partition the machine... this morning I discovered that the root partition was near to be full: it's normal, because I didn't think that I have to put the files of the sites I'm hosting in /home partition. So, I moved "www" directory from /var to /home/flip79/ (my home directory), and I updated the Apache configuration file, so now it looks for the files of the sites there. It works, but... Is it formally right that they're in my home folder? Is it "more" right if I put them in the "apache" folder of "apache" user (that doesn't currently exists on my server because (I thing) it's not enabled to SSH login)?

- Sites' files have "various" permissions and owners, depending from their born (I directly created some of them as root user, and so they're owned by root as user and as group, some others was uploaded as user "flip79", some others are owned by "apache" user....). In effect, sometimes I have some permission problem and I've to change them with chown apache filename and chgrp apache filename... sometimes I've to CHMODD'em with 775. I don't understand which is the "right" action: which is the right owner? apache/apache? And what about permissions? Which is the right permission pattern for the files that must be written by web user, for example for upload directories?

Thanks in advance for the responses!!!

---

### Post by Vegan on 2008-11-03
whats da madder for you

you need to let apache have access

chmod 

capeesh

---

### Post by cariboo on 2008-11-04
It really doesn't matter where the files are located, I usually use symlinks from /var/www like this:

```
sudo ln -s /home/ussr/website /var/www/website
```

What this does is create a symbolic link to /var/www. All the files are in /home/usr/website, but when you look in /var/www/website you see all the files. I usually have either root or www-data as owners of the files with a write permission of 755.

For more info have a look at:

```
man symlink
```

and

```
man ln
```

Jim

---

### Post by y@w on 2008-11-04
What's "right" really depends upon your situation. If the files are commonly edited by you and it's "your" site, then it's probably more correct to have them in your home directory, though it really doesn't matter. I usually try to keep my web files separate from any home directories just so I don't forget they are there, though in a web hosting situation, you may have several clients on one system and each need to access to their files and their files only. In that case, having them in home directories would be "correct".

As far as permissions go, unless you're using the suexec module for Apache, it works best if the files are owned by the same user that the web server runs as. In Ubuntu it's www-data. I forget what it runs as by default in CentOS. You can run 'ps aux | grep apache' to find out what user it's running as. If you don't know whether or not you are using suexec, you are probably not. 

Hope that helps :)

---

### Post by flip79 on 2008-11-05
Thank you very much guys! :)

---

