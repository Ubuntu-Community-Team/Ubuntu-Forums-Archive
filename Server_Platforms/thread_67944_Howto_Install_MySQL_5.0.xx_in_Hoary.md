---
title: "Howto Install MySQL 5.0.xx in Hoary"
date: 2005-09-21
forum: Server Platforms
---

### Post by jalanbuntu on 2005-09-21
Could anyone tell me please....... howto install MySQL 5.0.xx in Hoary??????
I've visited [mysql.com](http://mysql.com), there are so many mysql source that I don't know which file to download and install. I don't know which source/package should be run well on Hoary???????????

---

### Post by phrozen on 2005-09-22
i think you may want the release that is first on the list for linux distros, but im not sure on that one myself, i havent goten round to trying it yet

---

### Post by jalanbuntu on 2005-09-23
I've just download the file on the first list from [mysql.com download page for version 5.0.12](http://dev.mysql.com/downloads/mysql/5.0.html). May be I should try it by my self :D ........ wish it could be installed without any problem

---

### Post by jalanbuntu on 2005-09-27
I've just got MySQL 5.0.11 works in my Hoary. That's great that the [http://packages.dotdeb.org/]("http://packages.dotdeb.org/") has debian packages for MySQL 5.0.11.

I did some steps below to upgrading MySQL 4 to MySQL 5.0.11 in my Hoary

- Download the .deb files for MySQL from [http://packages.dotdeb.org/dists/stable/mysql-5.0/binary-i386/]("http://packages.dotdeb.org/dists/stable/mysql-5.0/binary-i386/")
```
wget http://packages.dotdeb.org/dists/stable/mysql-5.0/binary-i386/mysql-common_5.0.11beta-2.dotdeb.1_all.deb
wget http://packages.dotdeb.org/dists/stable/mysql-5.0/binary-i386/libmysqlclient15_5.0.11beta-2.dotdeb.1_i386.deb
wget http://packages.dotdeb.org/dists/stable/mysql-5.0/binary-i386/mysql-client-5.0_5.0.11beta-2.dotdeb.1_i386.deb
wget http://packages.dotdeb.org/dists/stable/mysql-5.0/binary-i386/mysql-server-5.0_5.0.11beta-2.dotdeb.1_i386.deb

```
- Download the libc6 packages
```
wget http://http.us.debian.org/debian/pool/main/g/glibc/libc6_2.3.2.ds1-22_i386.deb
```

- Installing all of the packages above.
```
sudo dpkg -i mysql-common_5.0.11beta-2.dotdeb.1_all.deb
sudo dpkg -i libc6_2.3.2.ds1-22_i386.deb
sudo dpkg -i libmysqlclient15_5.0.11beta-2.dotdeb.1_i386.deb
sudo dpkg -i mysql-client-5.0_5.0.11beta-2.dotdeb.1_i386.deb
sudo dpkg -i mysql-server-5.0_5.0.11beta-2.dotdeb.1_i386.deb
```

That's all.........

Now, we can have a great challenges with some  MySQL 5 new feature...... like Stored Procedures, Triggers, Views, etc :mrgreen:

I also see that MySQL has just release the MySQL 5.0.13 (Release Candidate version 5.0 of the MySQL database server), so may be the ubuntu packages for MySQL 5 will be available soon...... I hope so.....

---

### Post by jalanbuntu on 2005-09-28
I've just noticed that there are some broken dependencies because of upgrading libc6 :(

```
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-22 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-22 is to be installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

My dekstop still runs normally, but I can't install any other program using apt. Is there any solution that i can resolve this problem????????? ](*,)

---

### Post by mlomker on 2005-09-29
I guess your options are to do a dist-upgrade to Breezy or to attempt a downgrade of libc6.  In either case you'll want to back everything valuable up first.  I made this mistake on my first linux install and I ended up reloading the machine (I was running Linspire at the time).

Grab the older .deb file from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then try **dpkg -i *packagename.deb***

You might have to add the **--force-all** switch, if it gives you an error.

Instructions for upgrading to Breezy are around as well.  That upgrade has its own problems, but if you find yourself with nothing to lose...

---

### Post by jalanbuntu on 2005-09-30
Thanks....... mlomker
I've just downgrade my libc6..... and the old dependencies problem has gone.
After I downgrade the libc6 packages....... i try to fix the dependencies problem with
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
libmysqlclient15 mysql-client-5.0 mysql-server-5.0
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 49.0MB disk space will be freed.

```
So, I have to remove the MySQL 5 installation to solve the problem :( 
Untill now, I still don't remove the installation of MySQL and it still runs without any problem.
So I guess that MySQL 5 could work without any problem even if I use the old libc6.
Is there any way that I could keep the MySQL 5 works without have to face the dependencies problem?????? :-k 
About Breezy..... I don't know..... but I'm still doubt to upgrade using apt-get dist-upgrade :mrgreen:
Maybe one day I'll install Breezy using fresh installation from the Breezy CD

---

### Post by mlomker on 2005-09-30
> Maybe one day I'll install Breezy using fresh installation from the Breezy CD

That is the best way.  

In Synaptic you can select the *lock* option, which tells it to never upgrade a package.  You could try locking both of your mysql packages and see if it keeps it from trying to remove them.

I haven't figured out how to manually edit dpkg information to 'adjust' the dependencies.  I know that you could manually extract the mysql .debs to a directory and then repackage it, adjusting the dependencies list (involves a bit of work) or install it from source (then dpkg won't know about it).

---

### Post by lsald on 2005-10-24
Does anyone know when the offical 'production' version of MySQL 5.0 will be made available in a pre-existing apt source? I know it was just released today, but usually there are people on top of this.

---

