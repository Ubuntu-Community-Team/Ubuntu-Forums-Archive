---
title: "cant reach repo (i think)"
date: 2007-03-08
forum: Repositories &amp; Backports
---

### Post by Balinsky on 2007-03-08
well when i try to use anything that accesses repositories i get the following message.

```
E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
```
that is the message for synaptic

the source list at /etc/apt/sources.list.d/edgy-universe.list is as follows
```
# automatically added by gnome-app-install on 2007-02-08 21:32:49.709563
deb http://archive.ubuntu.com/ubuntu/ edgy universe main
deb http://archive.ubuntu.com/ubuntu/ edgy-updates

```

any help would be awsome

---

### Post by bruenig on 2007-03-08
> **Balinsky said:**
> well when i try to use anything that accesses repositories i get the following message.

```
E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
```
that is the message for synaptic

the source list at /etc/apt/sources.list.d/edgy-universe.list is as follows
```
# automatically added by gnome-app-install on 2007-02-08 21:32:49.709563
deb http://archive.ubuntu.com/ubuntu/ edgy universe main
deb http://archive.ubuntu.com/ubuntu/ edgy-updates

```

any help would be awsome

There needs to be something after the edgy-updates like in the one above it

```
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
```
You can pick all of those or some of those. Or you can just remove the line completely if you want.

---

### Post by Balinsky on 2007-03-08
i changed the line now i get what was my original problem (i think)

```
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.bz2: Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages - open (2 No such file or directory)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.bz2: Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages - open (2 No such file or directory)
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.bz2: Could not open file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages - open (2 No such file or directory)

```

and as it says i dont have the files

---

### Post by bruenig on 2007-03-08
There is no reason that error should be there, did you sudo apt-get update. Paste your new list.

---

### Post by Balinsky on 2007-03-09
```
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US       
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Get:2 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US
Get:3 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US
Get:4 http://security.ubuntu.com edgy-security/main Packages [63.5kB]
99% [4 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com edgy-security/main Packages
  Sub-process bzip2 returned an error code (2)
Get:5 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/restricted Packages
Get:6 http://security.ubuntu.com edgy-security/main Packages [63.5kB]
99% [6 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://security.ubuntu.com edgy-security/main Packages
  Sub-process bzip2 returned an error code (2)
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US
Get:7 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/universe Translation-en_US
Ign http://archive.ubuntu.com edgy/main Translation-en_US
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy-proposed Release
Hit http://archive.ubuntu.com edgy Release    
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages
Hit http://archive.ubuntu.com edgy-proposed/main Packages
Hit http://archive.ubuntu.com edgy-proposed/universe Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/main Packages
Fetched 7B in 1s (5B/s)  
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com edgy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com edgy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com edgy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
this is what i get when i do a sudo apt-get update

i dont know exactly what i am lookin at so i just posted it all

---

### Post by bruenig on 2007-03-09
Paste your /etc/apt/sources.list. You probably had automatix or something else install stuff and since by design that makes you not know what is going on, didn't realize that it enabled repos and so you enabled them yourselves, which gives you duplicate entries.

---

