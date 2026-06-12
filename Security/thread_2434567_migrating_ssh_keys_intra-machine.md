---
title: "migrating ssh keys intra-machine"
date: 2020-01-07
forum: Security
---

### Post by shu2462 on 2020-01-07
Desire to migrate (copy) ssh keys to another op-sys on the same machine.  More specifically, have Lubuntu 18.04 on partition 1.  Then installed Debian 9 on partition 2 and Debian 10 on partition 3.  Same computer, same hostname, same domainname, same login name, same passwords.  Have copied Lubuntu  /home/me/.ssh/*  into /home/me/.ssh of other partitions.  Desire to ssh to<>from other machines around the LAN without regard to what op-sys is active on this machine.  Do not mind presenting password for login, but having to wipe the known_hosts is becoming a major bother.

Have stumbled/searched around the web on this issue but - rather surprisingly - found nothing that seems to address it.    - shu

---

### Post by SeijiSensei on 2020-01-08
Usually having the same .ssh directory is all you need. Are you getting errors?

---

### Post by shu2462 on 2020-01-08
Thanks for the reply, Sensei.  

//charlie is the machine at issue.  //bravo is my Win10 principal machine, running WSL bash.
Desired outcome is ssh from //bravo to //charlie regardless of what op-sys is running on //charlie.

booted //charlie to well established install of Lubuntu 18.04
then at //bravo:
$ rm  ~/.ssh/known_hosts ............#to start clean
$ ssh charlie .............#ordinary first-time ssh procedure, no problem    

boot //charlie to fresh install of Debian 9.9
[create mount point; mount Lubuntu partition; copy Lubuntu/home/rick/.ssh/* to Debian/home/rick/.ssh]

back at //bravo:
rick@BRAVO:~$ ssh charlie
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:BbqaAgZE1fBiMp+XgO5tlftwNIxg97pkXkN1pPikv+s.
Please contact your system administrator.
Add correct host key in /home/rick/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/rick/.ssh/known_hosts:1
  remove with:
  ssh-keygen -f "/home/rick/.ssh/known_hosts" -R "charlie"
ECDSA host key for charlie has changed and you have requested strict checking.
Host key verification failed.
rick@BRAVO:~$

To clear the error I can either 
do the suggested "ssh-keygen -f ...."        or simply 
rm ~/.ssh/known_hosts.

---

### Post by The Cog on 2020-01-08
I think maybe the host id is in /etc/ssh. You could try copying these across, but make sure you keep the originals to restore if it doesn't work.

---

### Post by shu2462 on 2020-01-08
Indeed!  Fixdit!  

Per usual practice, made a safety fallback copy at //charlie
$ sudo cp -r /etc/ssh /etc/ssh.af ................#(=as found)

Two config files in the new Debian /etc/ssh were different from those in the established Lubuntu partition.  Those I left intact.  Copied from the established Lubuntu partition to the new Debian partition
..all /etc/ssh/ssh_host*
..an /etc/ssh/ssh_import_id ............#for no password login to the Synology NAS

Done, and thank you.  -shu

---

