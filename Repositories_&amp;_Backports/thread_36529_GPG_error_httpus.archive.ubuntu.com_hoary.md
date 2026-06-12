---
title: "GPG error: http://us.archive.ubuntu.com hoary"
date: 2005-05-23
forum: Repositories &amp; Backports
---

### Post by cyberdog on 2005-05-23
Here is my /etc/apt/sources list. I changed the sources list listed in in the Unofficial How-To. I have have these errors for about 2 weeks. Any ideas how to resolve the GPG errors. Do I need to clean out my /home/john/.gnupg/gpg.conf?

Thanks,
New to Ubuntu

```

john@jmobile:~$ sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
Password:
gpg: WARNING: unsafe enclosing directory permissions on configuration file "/hom e/john/.gnupg/gpg.conf"
gpg: key 1F41B907: "Christian Marillat <marillat@debian.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
john@jmobile:~$ sudo gpg --armor --export 1F41B907 | sudo apt-key add -
gpg: WARNING: unsafe enclosing directory permissions on configuration file "/hom e/john/.gnupg/gpg.conf"
OK
john@jmobile:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Get:5 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release [1348B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Get:6 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release [2528B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Fetched 4256B in 4s (973B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpm [email]aster@ubuntu.com[/email]>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatur es were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <f [email]tpmaster@ubuntu.com[/email]>
W: You may want to run apt-get update to correct these problems
john@jmobile:~$
```

---

### Post by antipex on 2005-06-04
I'm getting the same thing pretty much...here's my apt-get update results...

Hopefully someone can figure out what's wrong - I have no idea what's going on.  It was working fine since I installed Ubuntu about a month ago until the last week or so.



```
root@paladin:~ # apt-get update
Get:1 http://au.archive.ubuntu.com hoary Release.gpg [189B]
Ign http://backports.ubuntuforums.org hoary-backports Release.gpg
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:4 http://au.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://au.archive.ubuntu.com hoary Release
Ign http://backports.ubuntuforums.org hoary-extras Release.gpg
Get:5 http://archive.ubuntu.com hoary Release [26.2kB]
Get:6 http://security.ubuntu.com hoary-security Release [16.9kB]
Get:7 http://au.archive.ubuntu.com hoary-updates Release [16.8kB]
Ign http://backports.ubuntuforums.org hoary-backports Release
Ign http://backports.ubuntuforums.org hoary-extras Release
Ign http://backports.ubuntuforums.org hoary-backports/main Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://au.archive.ubuntu.com hoary/main Packages
Hit http://au.archive.ubuntu.com hoary/restricted Packages
Ign http://backports.ubuntuforums.org hoary-backports/universe Packages
Hit http://au.archive.ubuntu.com hoary/main Sources
Hit http://au.archive.ubuntu.com hoary/restricted Sources
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://au.archive.ubuntu.com hoary/universe Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://au.archive.ubuntu.com hoary/universe Sources
Hit http://au.archive.ubuntu.com hoary-updates/main Packages
Hit http://au.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://au.archive.ubuntu.com hoary-updates/main Sources
Hit http://au.archive.ubuntu.com hoary-updates/restricted Sources
Ign http://backports.ubuntuforums.org hoary-backports/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-backports/restricted Packages
Ign http://backports.ubuntuforums.org hoary-extras/main Packages
Ign http://backports.ubuntuforums.org hoary-extras/universe Packages
Ign http://backports.ubuntuforums.org hoary-extras/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-extras/restricted Packages
Err http://backports.ubuntuforums.org hoary-backports/main Packages
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-backports/universe Packages
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-backports/multiverse Packages
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-backports/restricted Packages
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-extras/main Packages
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-extras/universe Packages
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-extras/multiverse Packages
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-extras/restricted Packages
  401 Authorization Required
Fetched 60.3kB in 6s (9891B/s)
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz  401 Authorization Required
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by netrattler on 2005-06-05
Antipex just change the backport link in your /etc/apt/sources.list file to one of there mirrors and you should have no more trouble.

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

Joe

---

### Post by netrattler on 2005-06-05
Cyberdog do this part as normal user not sudo

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907

Then this command will be the part where sudo is used.

gpg --armor --export 1F41B907 | sudo apt-key add -

Joe

---

### Post by kuap on 2005-06-07
Netrattler...

This are the gpg keys of Christian Marillat, for the marillat repositories... not the ubuntu repositories.

---

### Post by haddad on 2005-06-16
Hello

I am getting a similar error

```
W: GPG error: http://us.archive.ubuntu.com hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
``` 

How do I fix this?

Thanks

---

### Post by dangli on 2005-06-17
I got this error quite often, what i do is to run the same command again

sudo apt-get update

then it will not complain about this BADSIG.

---

### Post by trinaryouroboros on 2005-11-07
[QUOTE=kuap]Netrattler...

This are the gpg keys of Christian Marillat, for the marillat repositories... not the ubuntu repositories.[/QUOTE]

How do you undo this? Chris's keys appear to overwrite the ubuntu repository keys...I tried sudo apt-get update over and over...tried restoring defaults in synaptic too - no dice!

---

### Post by geearf on 2005-11-07
same here :(

---

### Post by a_capp18 on 2005-11-07
I have the same problem with Breezy.
I have listed the keys with sudo apt-key list
I have a key for [email]ftpmaster@ubuntu.com[/email]
It does not match the key in the error.

I am not going to install any packages until I find out if the new key is trustworthy.

---

### Post by regular on 2005-11-13
[QUOTE=dangli]I got this error quite often, what i do is to run the same command again

sudo apt-get update

then it will not complain about this BADSIG.[/QUOTE]

hmm, same problem with breezy :( running sudo apt-get upgrade again and again doesn't help

---

### Post by aysiu on 2005-11-13
See the first link of my sig and follow the directions **exactly** as written.

---

### Post by magomago on 2005-11-14
[QUOTE=aysiu]See the first link of my sig and follow the directions **exactly** as written.[/QUOTE]
I have the same problem and that didn't fix it

---

### Post by Gtaylor on 2005-11-14
This isn't a question of following instructions correctly, this is a recent occurance. I've been using these repositories for a long time now with no problem but today I get: 

> 
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


---

### Post by dog.breath on 2005-11-16
Here's what worked for me:

[LIST]
[*]Used [source-o-matic]("http://www.ubuntulinux.nl/source-o-matic") to generate my */etc/apt/sources.list* text
[*]Created a backup of *sources.list* and touched a new one: *sudo cp sources.list sources.list.0; sudo touch sources.list*
[*]Pasted the output from source-o-matic into my new *sources.list* file
[*]Ran *sudo apt-get update*
[/LIST]

---

### Post by aysiu on 2005-11-16
[QUOTE=Gtaylor]This isn't a question of following instructions correctly, this is a recent occurance. I've been using these repositories for a long time now with no problem but today I get[/QUOTE] Actually, it is a matter of following instructions because my instructions do not have a us.archive.ubuntu.com repository in them. People are getting errors with those repositories, and I am not getting errors with the archive.ubuntu.com repositories.

---

### Post by laltopi on 2005-11-20
This is what worked for me:

> 
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo touch /etc/apt/sources.list
sudo apt-get update
sudo rm /etc/apt/sources.list
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
sudo apt-get update


Basically, use an empty sources.list to clear out some state that contains this bad signature. Then replace the sources.list. I do not have any issues with using us.archive.ubuntu.com after this.

---

### Post by paddygman on 2005-11-20
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
that link solves my problems!
Would advise trying it first from what i understand it makes sence!

---

### Post by Mogga on 2010-07-08
This worked for me. When I was creating VMs on 9.1 they all had the GPG key error

(Run as sudo)

```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

