---
title: "Configuring a LAMP"
date: 2008-06-06
forum: Server Platforms
---

### Post by Force Flow on 2008-06-06
Howdy...this is the first time I've attempted to setup a linux webserver, and I've got a couple things I ran into along the way.

First, I installed ubuntu 8.04 server with LAMP and SSH (installed during the installation), and KDE 3.x as the GUI.  All the updates have been installed.

I also installed webmin as the apache admin tool, although I will look into switching to something else once I know what the heck I'm doing. I also installed proftpd, but haven't yet looked into how to make it work or add users.

The idea is to have vhost directories like this: /var/www/vhosts/subdomain.domain.com

and allow users to FTP to the vhost directory.



So, first question:  The apache user installed as root (I think).  The /var/www/ directory lists the owner as root.

How can I add and change this to a different user?  I've seen on the webhost used at work that the web directories are owned by an "apache" username and group.


Seeing as the web directory is owned as root, I can't make any changes or additions from the GUI or command line unless I log in a root, which is a pain in the rear.



What would be the best way to go about these things without compromising security (although running the webservices as root makes me wary)


Thanks :)

---

### Post by quelx on 2008-06-06
> So, first question:  The apache user installed as root (I think).  The /var/www/ directory lists the owner as root.

How can I add and change this to a different user?  I've seen on the webhost used at work that the web directories are owned by an "apache" username and group.

the apache2 user is **www-data**

The permissions are normal, so long as the directories are **drwxr--r--** (mod 744) and the files **-r--r--r--** (mod 644) the **www-data** user can read the files it needs to without actually owning them.  This is a good thing, the webserver can't change the filesystem.

> Seeing as the web directory is owned as root, I can't make any changes or additions from the GUI or command line unless I log in a root, which is a pain in the rear.

It is designed to be a pain, normally system users shouldn't have direct access to server files.  If one of those accounts is compromised they could wipe out the apache2 pages.  If you want to let others read and write subfolders of */var/www/*, create folders belonging to a group you create for that purpose and make sure the permissions are **664** so the webserver can still read the files.

> What would be the best way to go about these things without compromising security (although running the webservices as root makes me wary)

I could be wrong about this, but I'm pretty sure the root user only kicks off apache2, the child processes (and actual web services) are run as the **www-data** user.  If you do ```
ps aux|grep apache2
pstree|less
``` you'll see the main process and subprocesses.

---

### Post by kamaji792 on 2008-06-07
> **Force Flow said:**
> 
Seeing as the web directory is owned as root, I can't make any changes or additions from the GUI or command line unless I log in a root, which is a pain in the rear.

Try:
```
cd /var/www
sudo md vhost
sudo chown <your_name>:<your_group> vhost
cd vhost
md some.domain.com
chown <their_name>:<your_group> some.domain.com
```
If this is a load of rubbish I am sure someone will tell you :/

**man chown** for details on the chown command.

All the best

---

### Post by Nythain on 2008-06-07
i would highly advise following the first followups advice... things are owned by who thier owned by for a reason...
The problem is, as already mentioned, as soon as you let the webserver itself start editing files and directory structures, or give this privilage to a non root user, your server becomes considerably more compromised...

you could look into configuring apaching with virtual domains<?> and set one up in your home... that should be a viable alternative, or you could just live with sudo/gksu to do what you need to do...

the best practice i've seen is to do any and all creation/edits/testing from a folder in yoru home directory, then just copy over when things are complete

---

### Post by Force Flow on 2008-06-08
I will be using virtual hosts, and managing with webmin.

So, if I'm understanding this correctly, the best practice would be to create /var/www/vhosts/myvirtualhost

and the "myvirtualhost" directory would be owned by a seperate user.

I'm assuming the user can be created with the KDE user management panel.  What would be the "correct" permissions settings for an owner of a vhost directory?

---

### Post by quelx on 2008-06-08
If there will be one person managing the website then change the ownership of the vhost subdirectory to that user (**o+rwx g+rx a+rx**).

If there will be more, create a group and leave the owner as root and change the group to that group which will be managing the subfolder and make sure the permissions are **o+rwx g+rwx a+rx** for the subfolder.

---

### Post by Force Flow on 2008-06-08
ok, good, that takes care of the directory permissions...what about O/S permissions?

---

