---
title: "private home directories accessible by Apache and PHP"
date: 2011-11-26
forum: Server Platforms
---

### Post by nrodes on 2011-11-26
Hello,

I have Ubuntu Server Edition 11.10:

I am trying to setup a server that my friends and I can use to host our various websites. I have Apache and vsFTP setup to work with a bunch of home directories as the DocumentRoot directories for a respective bunch of websites. Each user can access his/her website via FTP.

Unfortunately there's a bit of a security problem. In order for Apache not to give me a file permission error I have to set the permissions for the entire /home/ directory to 777. Users can't access each other's home directories via FTP because the file root is the home directory. If, on the other hand, one user logged into my server with a remote shell client then he/she could totally destroy the other users' websites.

A failed solution: I tried to get around this by setting the permission on all home directories to 774. Apache couldn't serve the directories anymore. I then added the user www-data to the groups of all of my other users. I gave each user and it's associated group ownership of it's home directory. Apache still gave me the permission error even though www-data had read/write/execute permission for the files in question.

Any ideas?

Thanks,
Naji

---

### Post by Corporation on 2011-11-27
The best fix would surely be to use something other than the home directories for the websites.

---

### Post by kamaji792 on 2011-11-28
I'm not an expert on this sort of thing.  You want to do something like this:

Create a **htdocs** directory in the users home folder.

Set the permissions so the users owns the directory and the group is set to **www-data**.  e.g.
```
chown bill:www-data htodcs
```

You may need to use **sudo**
```
sudo chown bill:www-data htodcs
```

I'm sure www-data (Apache) does not need write permissions, but probably needs execute permissions so:
```
chmod 750 htdocs
```

Files should be set up like (so they don't have execute permissions):
```
chown bill:www-data htdocs/*
chmod 640 htdocs/*
```

All the best k

---

### Post by nrodes on 2011-11-29
Hmm. I have done almost everything you guys said and Apache still can't access the directories. The one thing I don't understand is why the home directories are unsuitable for DocumentRoot. I left the home directories as the DocumentRoots. Is this causing my problems? If so, then how? Is there a way I can keep using the home directories?

The main reason that I want to keep them is that they are the default location for vsFTPd's FTP roots. I need the web root and FTP root to be the same to allow people to update their websites using an FTP client. I'm willing to change the web roots, but that means I have to deal with the problem of customizing vsFTPd. Since I'm a newbie in general, I don't want to make things more complicated than they need to be. I shall test out a non-home directory for Apache and see what happens.

---

### Post by rsvancara on 2011-11-29
If permissions are giving you an issue you could consider creating your virtual hosting directories in /var/www and then binding those directories in /home like this:

mkdir /var/www/bill
chown bill:www-data /var/www/bill
chmod 750 /var/www/bill

mkdir /home/bill/htdocs
mount --bind /var/www/bill /home/bill/htdocs

That is a "WAY".  

I think your problem is just that you are missing something simple.  You could also consider ACL (Access Control Lists) using setfacl and getfacl.  

setfacl -m u:www-data:rx /home
setfacl -m u:www-data:rx /home/bill
setfacl -m u:www-data:rx /home/bill/htdocs

That is another "WAY"

You could also assume the role of www-data like this:

sudo su - www-data and attempt to access those directories.  That way you can perform trial and error and actually see the permissions from the viewpoint of www-data.

Another thing I tried to look into is Apparmor.  I am not sure if has the ability to lock users out of certain directories.  

--svan
[http://www.knowyourlinux.com/]("http://www.knowyourlinux.com/content/virtualization-lxc-ubuntu-centos-guest")

---

### Post by nrodes on 2011-11-30
Thanks, svan. Moving my web roots out of /home/ and to /var/ made all the difference. Next I'll make an FTP virtual user for every website. If that doesn't work then I'll try your bind solution.

---

