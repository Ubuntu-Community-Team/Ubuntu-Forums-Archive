---
title: "postfix install problem"
date: 2008-05-21
forum: Server Platforms
---

### Post by tmilam on 2008-05-21
Hi, I'm trying to install postfix, but am unable to do so due to a dependency problem with rkhunter....

With rkhunter installed using exim4 as a dependency, apt produces an error message saying that rkhunter depends on exim4 and because of this postfix can't be installed. 

I removed rkhunter and tried again, but am still having the same issue. The following output explains the problem better than I can:

```
root@hemo:~# apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  postfix-cdb postfix-ldap postfix-mysql postfix-pcre postfix-pgsql resolvconf
  sasl2-bin
The following packages will be REMOVED:
  exim4-base exim4-config exim4-daemon-light
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 3 to remove and 3 not upgraded.
Need to get 0B/1160kB of archives.
After this operation, 926kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: exim4-base: dependency problems, but removing anyway as you request:
 exim4-daemon-light depends on exim4-base (>= 4.69).
(Reading database ... 24810 files and directories currently installed.)
Removing exim4-base ...
 * Stopping MTA                                                          [ OK ]
Removing exim4-config ...
dpkg: exim4-daemon-light: dependency problems, but removing anyway as you request:
 rkhunter depends on exim4 | postfix | sendmail | mail-transport-agent; however:
  Package exim4 is not installed.
  Package postfix is not installed.
  Package sendmail is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
 mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
Removing exim4-daemon-light ...
 * Stopping MTA                                                                 /sbin/start-stop-daemon: warning: failed to kill 16969: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-daemon-light (--remove):
 subprocess pre-removal script returned error exit status 3
Errors were encountered while processing:
 exim4-daemon-light
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Running apt-get -f install did not solve this problem, and I'm not sure how to proceed.

---

### Post by tmilam on 2008-05-21
I seem to have fixed this by reinstalling rkhunter and then running the following command

```
apt-get remove --purge rkhunter
```

After doing this the installation of postfix proceeds without errors.

---

### Post by Wim Feijen on 2008-09-24
Hmm.. I believe I'm experiencing the same problem:
1. postfix will not install
2. removing mail-transport agent won't work.

I've no idea if I have anything like rkhunter installed?

Any help will be very much appreciated.

Wim Feijen

I apologize for this output being in Dutch, but I hope you are able to figure it out:


logout
root@h1419524:~# apt-get install postfix
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
U wilt waarschijnlijk 'apt-get -f install' uitvoeren om volgende op te lossen:
De volgende pakketten hebben niet-voldane vereisten:
  exim4-daemon-light: Vereisten: exim4-base (>= 4.69) maar het zal niet geïnst
leerd worden
                      Conflicteert met: mail-transport-agent
  postfix: Conflicteert met: mail-transport-agent
E: Er zijn niet-voldane vereisten. U kunt best 'apt-get -f install' uitvoeren 
nder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@h1419524:~# apt-get -f install postfix
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
U wilt waarschijnlijk 'apt-get -f install' uitvoeren om volgende op te lossen:
De volgende pakketten hebben niet-voldane vereisten:
  exim4-daemon-light: Vereisten: exim4-base (>= 4.69) maar het zal niet geïnst
leerd worden
                      Conflicteert met: mail-transport-agent
  postfix: Conflicteert met: mail-transport-agent
E: Er zijn niet-voldane vereisten. U kunt best 'apt-get -f install' uitvoeren 
nder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@h1419524:~# sudo apt-get remove mail-transport-agent
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
Pakket mail-transport-agent is niet geïnstalleerd, en wordt dus niet verwijder
U wilt waarschijnlijk 'apt-get -f install' uitvoeren om volgende op te lossen:
De volgende pakketten hebben niet-voldane vereisten:
  exim4-daemon-light: Vereisten: exim4-base (>= 4.69) maar het zal niet geïnst
lleerd worden
E: Er zijn niet-voldane vereisten.

---

