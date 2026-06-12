---
title: "sudo /etc/init.d/ssh reload sudo: /etc/init.d/ssh: command not found"
date: 2014-07-30
forum: Security
---

### Post by Miss_Nails on 2014-07-30
Hello,

I know that this issue has already been discussed, but I cannot find an answer to my question. I updated the file (/etc/ssh/sshd_config) by typing code:

```
PermitRootLogin no
AllowUsers user1
```

But then I tried and got:

```
sudo /etc/init.d/ssh reload
sudo: /etc/init.d/ssh: command not found

```

I've even tried it with the sshd option and have the same problems. I've been using Ubuntu for many years now, and I still feel like a newbie. :) Can somebody help me step-by-step? It would be greatly appreciated.

---

### Post by ian-weisser on 2014-07-30
> **Miss_Nails said:**
> 
But then I tried and got:

```
sudo /etc/init.d/ssh reload
sudo: /etc/init.d/ssh: command not found

```

Indeed, that's not how you reload the ssh server config file anymore.
Try:
```
sudo service ssh restart
```

---

### Post by Miss_Nails on 2014-07-31
Hello ian-weisser,

I tried the above command and got: 

```

sudo service ssh restart
ssh: unrecognized service
 
```

I'm using OS Ubuntu 12.04 LTS.

---

### Post by ian-weisser on 2014-07-31
Okay, so ...er, you *do* have openssh-server installed?
If you try the command the following command, is ssh listed?
 ```
service --status-all
```

---

### Post by Miss_Nails on 2014-07-31
Nope. It isn't even listed. Do I type:

```
sudo apt-get install openssh-server 
``` 

And then can I modify my settings? Told you I'm a perpetual newbie. :D

---

### Post by CharlesA on 2014-07-31
Yes. That will get openssh-server installed. :)

---

### Post by Miss_Nails on 2014-08-02
So, I tried to install it, but I'm supposedly having a "cup" problem. 

```

Setting up cups (1.5.3-0ubuntu8.4) ...
AppArmor parser error for /etc/apparmor.d/usr.sbin.cupsd in /etc/apparmor.d/usr.sbin.cupsd at line 17: Invalid capability block_suspend.
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on printer-driver-hpcups (= 3.12.2-1ubuntu3.4); however:
  Package printer-driver-hpcups is not configured yet.
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.12.2-1ubuntu3.4); however:
  Package hplip is not configured yet.
dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cupsNo apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                               No apport report written because the error message indicates its a followup error from a previous failure.
         No apport report written because the error message indicates its a followup error from a previous failure.
                                    depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing bluez-cups (--configure):
 dependency problems - leaving unconfigured
Setting up openssh-server (1:5.9p1-5ubuntu1.4) ...
Creating SSH1 key; this may take some time ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
Creating SSH2 ECDSA key; this may take some time ...
ssh start/running, process 3614
Setting up ssh-import-id (2.10-0ubuntu1) ...
Errors were encountered while processing:
 cups
 printer-driver-hpcups
 hplip
 printer-driver-postscript-hp
 bluez-cups
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Should I start a brand new thread for this problem? 

Cheers!

---

### Post by Miss_Nails on 2014-08-02
Well, ssh now shows up as one of my programs, but I'm a bit concerned... Should I even have ssh installed on my system if I'm such a noob? Couldn't somebody else with more knowledge use it against me? I'm sorry for being paranoid, but I was one of the first that got hacked into some years back. I noticed that they came in through my ssh server. They could have come through my cups as well, but I'm not too sure. Is there a way I could set my permissions for only me to get on the ssh server?

---

### Post by ubudog on 2014-08-02
Looks like you did get openssh-server installed there, post the output of this command again:
```
service --status-all
```

Try this command to fix your broken packages (maybe you shutdown during an update or something?):
```
sudo dpkg --configure -a
```

**Edit:**
Ubuntu comes with the ssh client installed, which is what you use to ssh to a server, but you have to install openssh-server if you want an ssh server to be running.  You don't need to have openssh-server installed if you are not going to be ssh'ing into your machine, but if you are behind a router/firewall then you should be fine - but there is no reason to have it installed if you are not going to be using it.

If you are in fact expecting to be ssh'ing to your machine over the Internet, have a look at this wiki page to set up key based authentication, as opposed to password based authentication.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by Miss_Nails on 2014-08-03
Thanks everyone for helping me! I consider my first problem in this forum solved! I just needed to install certain software and then use the newer command for reboot or restart. I'm still having "cups" problems, even when I typed sudo dpkg --configure -a. That might go into a another discussion if it hasn't been solved elsewhere on the forums.

Thanks alot! :D

---

