---
title: "apt-get stuck in limbo"
date: 2012-02-24
forum: Server Platforms
---

### Post by VanJr on 2012-02-24
How do we get *apt-get* out of a failed installation limbo?

An admin accidentally attempted to install an application (cacti) on one of our servers via *apt-get*. He typed the command on the wrong server. The application (cacti) requires *mysql-server* to be installed. Unfortunately the server the command was issued on is a MySQL server running a 5.5.x Oracle/MySQL distribution and not the Ubuntu 5.1.x distribution. Consequently *apt-get* didn't think MySQL was installed and attempted to install it. If failed. Now apt-get is stuck with the message:
```

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:

```Unfortunately, *apt-get* won't let us remove the application (cacti) because it's not fully installed. We can't install it because the installation of MySQL server fails. Now we can't install or remove anything. Kind of a catch-22.

**What can we do to fix *apt-get*?**

---

### Post by roelforg on 2012-02-24
What's the error while installing?

---

### Post by VanJr on 2012-02-24
When we attempt a: **apt-get -f install**

```

Preconfiguring packages ...
(Reading database ... 118906 files and directories currently installed.)
Unpacking mysql-client-core-5.1 (from .../mysql-client-core-5.1_5.1.58-1ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-client-core-5.1_5.1.58-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mysql', which is also in package mysql-client 5.5.16-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.58-1ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-client-5.1_5.1.58-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/mysqlaccess', which is also in package mysql-client 5.5.16-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.58-1ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.58-1ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/msql2mysql', which is also in package mysql-client 5.5.16-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-core-5.1_5.1.58-1ubuntu1_amd64.deb
 /var/cache/apt/archives/mysql-client-5.1_5.1.58-1ubuntu1_amd64.deb
 /var/cache/apt/archives/mysql-server-5.1_5.1.58-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by roelforg on 2012-02-24
Try running:
```

sudo apt-get clean
sudo apt-get update

```
I'm suspecting broken download; the clean will force apt-get to redownload.
The update will check for newer ones (sometimes the issue as well).

---

### Post by VanJr on 2012-02-24
Thank you. Already tried that but did it again.

apt-get is stuck in the middle of an installation.

If I try this: **sudo apt-get install apache2**

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cacti : Depends: virtual-mysql-client
 mysql-server : Depends: mysql-server-5.1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

What we need is a: **sudo apt-get abort**

---

### Post by roelforg on 2012-02-24
> **VanJr said:**
> Thank you. Already tried that but did it again.

apt-get is stuck in the middle of an installation.

If I try this: **sudo apt-get install apache2**

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cacti : Depends: virtual-mysql-client
 mysql-server : Depends: mysql-server-5.1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```What we need is a: **sudo apt-get abort**

You could try to download the .deb manually and manually running through dpkg.
Now apt-get shouldn't complain.
It worked with my friends pc whose Xorg had the same after an update (well, he couldn't remove it after an upgrade that didn't work out).

---

### Post by matt_symes on 2012-02-24
Hi

> Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.58-1ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.58-1ubuntu1_amd64.deb (--unpack):
 **trying to overwrite '/usr/bin/msql2mysql', which is also in package mysql-client 5.5.16-2**
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

Try this.

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/mysql-server-5.1_5.1.58-1ubuntu1_amd64.deb
```

Kind regards

---

### Post by VanJr on 2012-02-24
Thanks to everyone for the help. This is a great community.

However, we do **NOT** want to over-write the 5.5.x installation on this production server. We actually want to **ABORT** the installation (not perform it). How do we stop it? Clean-it up?

---

### Post by roelforg on 2012-02-24
> **VanJr said:**
> Thanks to everyone for the help. This is a great community.

However, we do **NOT** want to over-write the 5.5.x installation on this production server. We actually want to **ABORT** the installation (not perform it). How do we stop it? Clean-it up?
To remove the install, one must finish it.

---

### Post by VanJr on 2012-02-24
> **roelforg said:**
> To remove the install, one must finish it.


Yea, I was afraid that. I see a ruined weekend ahead. :(

---

### Post by matt_symes on 2012-02-24
Hi

Let's try to work through the problem.

What's the output of these commands.

```
sudo dpkg -l mysql-server-5.1
sudo dpkg -l virtual-mysql-client
sudo dpkg -l cacti
```

Post back the results.

There are ways to remove packages manually if required and, depending on what is the problem with the system, it may be fixable.

Kind regards

---

### Post by iponeverything on 2012-02-24
backup and open:

```
/var/lib/dpkg/status
```

search for and remove the cacti section.

then all should be good.

---

### Post by matt_symes on 2012-02-24
Hi

> **iponeverything said:**
> backup and open:

```
/var/lib/dpkg/status
```

search for and remove the cacti section.

then all should be good.

What you have suggested was going to be part of what i was going to suggest.

As an addendum to this

```
dpkg -L <package_name>
``` 

will list all the files installed for that package.

Using that you can find out what files have been installed and remove the files as well as the references to the packages.

That way you can manually remove a package and any files it may have partly installed.

But as this is a production server, i though the softly, softly approach would be better to find the current state of each package.

Kind regards

---

### Post by iponeverything on 2012-02-24
agreed -- a manual cleaning of cacti detritus is good idea for a production box.

---

### Post by VanJr on 2012-02-27
> **iponeverything said:**
> backup and open:

```
/var/lib/dpkg/status
```search for and remove the cacti section.

then all should be good.

Thank you! That did it.

FYI, I also had to remove the section for *mysql-server* too.

---

### Post by tridentblack on 2013-03-17
Hey, I got caught in this same catch 22. What I had done was I had erased the file /etc/init.d/mysql . I replaced the file with a file empty except for the line 
#hi
And then ran the line from above

sudo dpkg -i --force-overwrite /var/cache/apt/archives/mysql-server-5...

(except with the name of the mysql server deb actually matching the one my computer had in /var/cache/apt/archives/ )
And it fixed it.

---

