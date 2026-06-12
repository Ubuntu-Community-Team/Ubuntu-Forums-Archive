---
title: "jailkit issue"
date: 2010-06-06
forum: Security
---

### Post by gs69azza on 2010-06-06
Hi Guys

I have been having a few issues with the jailkit ([http://olivier.sessink.nl/jailkit/jailkit-2.10.tar.gz](http://olivier.sessink.nl/jailkit/jailkit-2.10.tar.gz))
I have created the environment and added a user.

Environment location:
/home/jail

tail /etc/passwd:
> test:x:1002:1002::/home/jail/./home/test:/usr/sbin/jk_chrootshtail /home/jail/etc/passwd
> test:x:1002:1002::/home/test:/bin/bash/usr/sbin/jk_chrootsh is included in /etc/shells

but as you can see below I am unable to run anything as the jailed user, even after I have used the jk_cp script

> root@server:~# su test
bash: groups: command not found
test@server:~$ nano
Error opening terminal: unknown.
test@server:~$ echo $TERM
dumbHas anyone else had this issue?

---

### Post by gs69azza on 2011-04-19
So after about a year, I have returned to attempt to install jailkit again.  I ran into some issues such as, SSH dropping once logged in as the jailed user, I also had some permission issues with the users home directory.  Also had some bash shell issues. But the biggest issue was with the users in the jail couldn't change the password due to a PAM issue.  The locate command down below seems to have fixed it.  I have pasted my entire process

> 
## Download jailkit and install
cd /tmp
wget [http://olivier.sessink.nl/jailkit/jailkit-2.10.tar.gz](http://olivier.sessink.nl/jailkit/jailkit-2.10.tar.gz)
tar xvfz jailkit-2.10.tar.gz
cd jailkit-2.10
./configure
make
make install
cd ..
rm -rf jailkit-2.10*
cd

## Create jail
jk_init -v -j /jail ssh
vi /etc/passwd
## Add to /etc/passwd
j a i l u s e r : x : 2 0 0 0 : 1 0 0 : : / j a i l / . / h o m e / j a i l u s e r : / u s r / s b i n / j k _ c h r o o t s h 

jk_init -v -f /jail jk_lsh
jk_cp -v -f /jail /bin/bash
jk_cp -v -f /jail /bin/ls
jk_cp -v -f /jail /bin/ps
jk_cp -v -f /jail /bin/su
jk_cp -v -f /jail /etc/bash.bashrc
jk_cp -v -f /jail /usr/bin/cc
jk_cp -v -f /jail /etc/environment
jk_cp -v -f /jail /etc/profile
jk_cp -v -f /jail /etc/sudoers
jk_cp -v -f /jail /usr/bin/dircolors
jk_cp -v -f /jail /usr/bin/g++
jk_cp -v -f /jail /usr/bin/gcc
jk_cp -v -f /jail /usr/bin/groups
jk_cp -v -f /jail /usr/bin/id
jk_cp -v -f /jail /usr/bin/irssi
jk_cp -v -f /jail /usr/bin/passwd
jk_cp -v -f /jail /usr/bin/perl
jk_cp -v -f /jail /usr/bin/pork
jk_cp -v -f /jail /usr/bin/python
jk_cp -v -f /jail /usr/bin/screen
jk_cp -v -f /jail /usr/bin/sudo
jk_cp -v -f /jail /usr/sbin/usermod
jk_cp -v -f /jail /usr/share/perl/5.10.0/strict.pm
jk_cp -v -f /jail /var/lib/pam/account
jk_cp -v -f /jail /var/lib/pam/auth
jk_cp -v -f /jail /var/lib/pam/password
jk_cp -v -f /jail /var/lib/pam/seen
jk_cp -v -f /jail /var/lib/pam/session
jk_init -f -v /jail basicshell
jk_init -f -v /jail editors 
jk_init -f -v /jail extendedshell
jk_init -f -v /jail logbasics
jk_init -f -v /jail netbasics
jk_init -f -v /jail netutils 
jk_init -f -v /jail scp
jk_init -f -v /jail uidbasics

## Run locate for all PAM mods
## Remove all thats alread in the jail
## Pipe back into xargs for jk_cp
locate pam | sed 's/^.*jail//' | xargs jk_cp -v -f /jail

## Setup user in jail
vi /jail/etc/passwd
## Add to /etc/passwd in jail
j a i l u s e r : x : 2 0 0 0 : 1 0 0 : : / h o m e / j a i l u s e r : / b i n / b a s h 

vi /jail/etc/group
## Add to /etc/group in jail
u s e r s : x : 1 0 0 :

## edit /etc/shadow for password auth
vi /etc/shadow
jailuser::11302:0:99999:7:::

## Set password for jailuser
passwd jailuser

## Copy password files to jail
jk_cp -v -f /jail /etc/shadow
jk_cp -v -f /jail /etc/shadow-

## Create new user home environment
cd /jail/
mkdir home
cd home/
## Make users home directory
mkdir jailuser
chown 2000:100 jail
ls -la
cd ..

## Create /proc in jail for ps to work
cd /jail/
mkdir proc
mount -t proc none /jail/proc

## Set permissions for sudo to work
chown root:root /jail/usr/bin/sudo
chmod 4755 /jail/usr/bin/sudo
chmod u+s /jail/usr/bin/passwd

## Edit config for jail
vi /jail/etc/jailkit/jk_lsh.ini
#[test]
#paths= /usr/lib/
#executables= /usr/lib/sftp-server
#allow_word_expansion = 0
#umask = 002
#
##example for a group, there should be only 1 space inbetween the words!
#[group users]
#paths = /usr/bin
#executables = /usr/bin/cvs
#allow_word_expansion = 0
#environment= HELIX_PATH=/opt/RealPlayer/, TMP=/tmp/
[jailuser]
paths= /usr/bin
executables= /usr/bin/ssh

## Edit config for jail
/etc/jailkit/jk_chrootsh.ini

## example for a user
#[test]
#env= DISPLAY, XAUTHORITY
#
##example for a group, there should be only 1 space inbetween the words!
#[group users]
#env = DISPLAY, XAUTHORITY, TERM
[DEFAULT]
env = TERM

## Restart jailkit socket daemon
killall jk_socketd ; jk_socketd

## Switch to jailed user and check any errors
su jailuser
tail /var/log/auth.log
Please note that the 3 lines 

j a i l u s e r : x : 2 0 0 0 : 1 0 0 : : / j a i l / . / h o m e / j a i l u s e r : / u s r / s b i n / j k _ c h r o o t s h 
j a i l u s e r : x : 2 0 0 0 : 1 0 0 : : / h o m e / j a i l u s e r : / b i n / b a s h
u s e r s : x : 1 0 0 :

have added spaces between each character, please remove each space

---

