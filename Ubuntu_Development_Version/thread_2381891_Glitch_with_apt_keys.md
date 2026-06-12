---
title: "Glitch with apt keys"
date: 2018-01-06
forum: Ubuntu Development Version
---

### Post by zika on 2018-01-06
```
The key(s) in the keyring /etc/apt/trusted.gpg.d/freesh-keyring.gpg are ignored as the file is not readable by user '_apt' executing apt-key.
```
I'm getting this for _all_ repos... ;)
```
:~$ cat /var/log/apt/term.log
...
Log started: 2018-01-05  15:26:40
Unpacking freesh-keyring (1.6) over (1.5)
...
```It'll be fun to install new version of freesh-keyring... ;)
Update&#8321;: Old hack with:```
cd /var/lib/apt
ls -alt
mv lists lists.old
mkdir -p lists/partial
apt clean
```did not work... Back to the minning shaft...```
:~$ ls -alt /etc/apt/trusted.gpg.d/freesh-keyring.gpg
-rw------- 1 uname uname 3530 jan  6 17:10 /etc/apt/trusted.gpg.d/freesh-keyring.gpg
```while others are```
-rw-r--r-- 1 root root 1340 nov 25 07:48 libreoffice_ubuntu_libreoffice-prereleases.gpg
```
Update&#8322;: Solved:```
sudo chmod 664 /etc/apt/trusted.gpg.d/freesh-keyring.gpg
```
It seems that the trouble will persist until freesh-keyring package is not patched to assign permissions properly...```
:/etc/apt/trusted.gpg.d$ ls -alt f*
-rw------- 1 root root 3530 jan  6 18:35 freesh-keyring.gpg~.backup
-rw------- 1 root root 3530 jan  6 18:35 freesh-keyring.gpg.backup
-rw-rw-r-- 1 uname uname 3530 jan  6 17:10 freesh-keyring.gpg
-rw------- 1 uname uname 3530 jan  6 17:10 freesh-keyring.gpg~
```I might be wrong but it works for now... ;)
[SIZE=1]In retrospective I was really dumb not to address what is clearly stated in warning given by apt but to try well-paved way that was solution for earlier glitches... Silly me... ;)[/SIZE]

---

