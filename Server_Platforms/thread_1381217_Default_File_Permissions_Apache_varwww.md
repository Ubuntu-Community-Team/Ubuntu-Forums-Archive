---
title: "Default File Permissions Apache /var/www/"
date: 2010-01-14
forum: Server Platforms
---

### Post by tprzepiorka on 2010-01-14
Hi,
This is probably a pretty basic question seeing as I'm pretty new to Ubuntu Server. I'm running a simple website from my Ubuntu Server machine with Apache installed ([www.parkourwarsaw.com](www.parkourwarsaw.com)). The files are all stored in /var/www/ and then subdirectories. The problem is that when I add files through FTP I need to go and change all of the file permissions since by default they do not have read access so can't be accessed through a web browser on another machine.

How can I make the default permissions readable for the directory and all new files that will be moved in it.

Thanks in advance. :)

---

### Post by tprzepiorka on 2010-01-16
Anyone know?

---

### Post by Tuliku on 2010-01-16
Try this:

Make sure the group is www-data on '/var/www'.
```
sudo chgrp www-data /var/www
```

Make '/var/www' writable for the group.
```
sudo chmod 775 /var/www
```

Set the GID for www-data for all sub-folders.
```
sudo chmod g+s /var/www
```

Your directory should look like this on an 'ls -l' output.
drwxrwsr-x

Last, add your user name to the www-data group (secondary group).
```
sudo useradd -G www-data [USERNAME]
```

```
sudo chown [USERNAME] /var/www/
```

You should now be able to SFTP to your server as your user name and upload to '/var/www' with no problems.

---

### Post by tprzepiorka on 2010-01-17
Thanks for the reply. I got through all the first steps and checked and the www folder did have "drwxrwsr-x" on an ls -l output. The second to last step didn't work (sudo useradd -G www-data [USERNAME]) and it told me:
```

useradd: user [USERNAME] already exists

```
I went ahead and did the last step, but still when I access files that I have put up through FTP to the www or subdirectories are still not visible. (wwww.parkourwarsaw.com/pg_back.gif as an example). Unless I manually go through and change the permissions of each file everytime they are uploaded they aren't visible. 
Not sure what else I can do.

---

### Post by distratios on 2010-07-30
> **tprzepiorka said:**
> Thanks for the reply. I got through all the first steps and checked and the www folder did have "drwxrwsr-x" on an ls -l output. The second to last step didn't work (sudo useradd -G www-data [USERNAME]) and it told me:
```

useradd: user [USERNAME] already exists

```

It may be a little late, but since someone else could read it:
```

usermod -a -G www-data [USERNAME] 
```is the command to add an *existing *user to an *existing *group.
At least I think so ... ;)

---

### Post by Trismegister on 2010-08-13
I suppose it is all based on the fact that an Apache web server can access any file that is owned by any [username] in the group www-data.

Alternatively, if she logs in as www-data, then new directories and files she creates will immediately be accessible to apache without her having to *chown* and *chgrp* the newly-uploaded files every time she creates them as [username].

But I suppose, by doing the alternative above, you'd lose the whole point of several website maintainers taking ownership of their own files in the website. Even though this wouldn't be an issue in a single-person shop, when two or more people could take the blame for screwing the website up, then individual file ownership is an issue (providing that the permissions are set so that anyone (including Apache) can read, but not write any file in the website).

i.e. you *could*: 
[LIST=1]
[*]give www-data a unix password on the web server.
[*]from the client ssh -l www-data [webserver URI] 
[*] similarly the ftp client to use sftp and login as user www-data with www-data's unix password)
[*]change www-data to use a bash shell as well so that ssh www-data@[webserver URL] gives a usable terminal experience.
[/LIST]

Perhaps this explains why it is conventional not to ssh and sftp directly as  www-data to get web server work done. Although it would work.

---

