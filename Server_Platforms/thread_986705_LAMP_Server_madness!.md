---
title: "LAMP Server madness!"
date: 2008-11-18
forum: Server Platforms
---

### Post by nesnub on 2008-11-18
Hello, I am going completely insane.

I wanted to have a simple install of a LAMP server, so knowing how the desktop ubuntu was easy I chose to try to install the server version.

I selected the LAMP server during the installation process and it installed everything I needed. This is all in VMWare by the way.

The problems came when I tried to update the software through apt-get upgrade. I did an update followed by a few upgrades for a week or two all went well. This week, I do an apt-get upgrade and it suggests upgrading mysql-server, fine. It start installing and eventually fails, I am sorry but I can not remember which error it was then, I've had a few repeat over and over again since then.

That failure broke my mysql install, so I tried to clean and upgrade again, no luck.

The common errors I get are:

dpkg: error processing /var/cache/apt/archives/mysql-client-5.0_5.0.51a-3ubuntu5.4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive

Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
chown: cannot access `/usr/share/mysql': No such file or directory
chown: cannot access `/var/run/mysqld': No such file or directory

Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/sbin/ndb_mgmd')


I tried removing manually the corrupted files, updating and upgrading, still the same. I tried going from the ca.archive... site to the archive... as a source, same problems keep coming back.

I had enough, figured something went wrong during install. Re-installed. Same kind of problems. I did however get to repair it at some point, not know exactly how, it came down to multiple "clean", "autoremove", "purge" and reboots. But it broke again a few installs later.

At some point I thought it might have had something to do with the installer using the "mysql-server" package and then the apt-get upgrade trying to upgrade the "mysql-server-5.0" package, which somehow confused the hell out of it. They are supposed to be "aliases" of each other correct?

I tried to remove everything, but even after removing all packages through aptitude, some mysql files remain on my system. I now learned deleting /etc/init.d/mysql is a very bad thing, I thought the apt-get installer was supposed to create that file, I now get 

invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.

So here I am, asking for some help, I must have radically screwed up somewhere, I refuse to believe that such a simple type of server would get screwed up by "normal" apt-get upgrade...

Is there a rule about installing a package like "mysql-server" vs "mysql-server-5.0"? Should I be specifying something special in the apt-get upgrade? Should I use a particular source since the main one is often broken? Should I just always install from source? Is there a known problem with aptitude and VMWare?

Sorry about so many questions, but I am at my wits' end.

Thank you, I need my sanity back.

---

### Post by Philio on 2008-11-18
There are a couple of things you could try:

aptitude perge - removes packages and all config files.
aptitude reinstall - attemptes to download and reinstall a package.

---

### Post by nesnub on 2008-11-19
I tried the 

aptitude reinstall mysql-server-5.0

and I do not get corrupted archives errors. I get 

Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
chown: cannot access `/usr/share/mysql': No such file or directory
chown: cannot access `/var/run/mysqld': No such file or directory


Do you know what is supposed to install those files? It seems like they should be installed by the mysql-server package but obviously aren't...

I also tried reinstalling mysql-common, it installed without problem...

Thanks

---

