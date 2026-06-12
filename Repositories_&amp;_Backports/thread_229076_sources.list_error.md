---
title: "sources.list error"
date: 2006-08-03
forum: Repositories &amp; Backports
---

### Post by cardude on 2006-08-03
I am new to Linux and Ubuntu so please bear with me. i keep recieving an error when i try to reload synaptic package manager. 

E:Malformed line 40 in source list /etc/apt/sources.list (dist)
E:The list of sources could not be read

What does it mean/how can i fix it? Any help appreciated!

---

### Post by catlett on 2006-08-03
This is the Dapper Guide's list. It has all the necessary repositories enabled for mp3, dvd etc.
So open your list in a text editor and erase everything in it.
This is the command to open it```
 sudo gedit /etc/apt/sources.list
```After you cut ecerythung out, copy/paste this list in.

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```Make sure to save it. Then run```
 sudo apt-get update
```

---

### Post by cardude on 2006-08-03
Thanks ill have to try that.

---

### Post by cardude on 2006-08-04
Problem solved!!! Thanks catlett.

---

### Post by Sh8kR on 2006-08-04
On a related issue: I get the GPG error when I try to use the Debian Source list below.
 
 I know these are trusted sources list I used them when I was running Debian Sarge. I had been using Debian before I switched over to K/Edu/Ubuntu Dapper 6.06. I am trying to get used to the differences between the builds and the way apt-get works. 
 
 Any advice on getting the GPG keys for Debian?
 
 Rumptz 
 
 W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: GPG error: [http://secure-testing.debian.net](http://secure-testing.debian.net) testing/security-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 946AA6E18722E71E
 W: GPG error: [http://security.debian.org](http://security.debian.org) stable/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: You may want to run apt-get update to correct these problems

---

### Post by cardude on 2006-08-04
See Dapper Guides list [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by catlett on 2006-08-04
> **Sh8kR said:**
> On a related issue: I get the GPG error when I try to use the Debian Source list below.
 
 I know these are trusted sources list I used them when I was running Debian Sarge. I had been using Debian before I switched over to K/Edu/Ubuntu Dapper 6.06. I am trying to get used to the differences between the builds and the way apt-get works. 
 
 Any advice on getting the GPG keys for Debian?
 
 Rumptz 
 
 W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: GPG error: [http://secure-testing.debian.net](http://secure-testing.debian.net) testing/security-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 946AA6E18722E71E
 W: GPG error: [http://security.debian.org](http://security.debian.org) stable/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
 W: You may want to run apt-get update to correct these problems
The key process is a little different. The wording of it, You need sudo in the second command and export and armor are switched.
Anyways when you see the key error, take the number in the eror and add it into this formula where KEY is replaced with the key from the error (or the key you want if you know it without an error)
```
      gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

```
For example the first error is looking for key  010908312D230C5F 
So the commands will be
```
gpg --keyserver subkeys.pgp.net --recv 010908312D230C5F
 gpg --export --armor 010908312D230C5F | sudo apt-key add -
```
The output of the terminal will look like this
```
catlett@ubuntu:~$ gpg --keyserver subkeys.pgp.net --recv 010908312D230C5F
gpg: requesting key 2D230C5F from hkp server subkeys.pgp.net
gpg: key 2D230C5F: public key "Debian Archive Automatic Signing Key (2006) <ftpmaster@debian.org>" imported
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: Total number processed: 1
gpg:               imported: 1
tj@ubuntu:~$    gpg --export --armor 010908312D230C5F | sudo apt-key add -
Password:
gpg: no ultimately trusted keys found
OK
catlett@ubuntu:~$
```You actually only neeed that key and this one 

```
gpg --keyserver subkeys.pgp.net --recv 946AA6E18722E71E
   gpg --export --armor  946AA6E18722E71E | sudo apt-key add -
```

---

### Post by Dinerty on 2006-08-04
> **catlett said:**
> The key process is a little different. The wording of it, You need sudo in the second command and export and armor are switched.
Anyways when you see the key error, take the number in the eror and add it into this formula where KEY is replaced with the key from the error (or the key you want if you know it without an error)
```
      gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

```
For example the first error is looking for key  010908312D230C5F 
So the commands will be
```
gpg --keyserver subkeys.pgp.net --recv 010908312D230C5F
 gpg --export --armor 010908312D230C5F | sudo apt-key add -
```
The output of the terminal will look like this
```
catlett@ubuntu:~$ gpg --keyserver subkeys.pgp.net --recv 010908312D230C5F
gpg: requesting key 2D230C5F from hkp server subkeys.pgp.net
gpg: key 2D230C5F: public key "Debian Archive Automatic Signing Key (2006) <ftpmaster@debian.org>" imported
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
gpg: Total number processed: 1
gpg:               imported: 1
tj@ubuntu:~$    gpg --export --armor 010908312D230C5F | sudo apt-key add -
Password:
gpg: no ultimately trusted keys found
OK
catlett@ubuntu:~$
```You actually only neeed that key and this one 

```
gpg --keyserver subkeys.pgp.net --recv 946AA6E18722E71E
   gpg --export --armor  946AA6E18722E71E | sudo apt-key add -
```

Thank you for this brilliant guide it worked for me also !

---

### Post by shooshy on 2011-06-13
> **cardude said:**
> Thanks ill have to try that.

hi i have a problem in repository.i cant update use update manager;and i cant open synaptic  manager when i try to open synaptic manager in ubuntu 10.04 it show error message with this mean :E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
please help me to solve this problem in my system ubuntu 10.04

---

