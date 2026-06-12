---
title: "remove proftpd need /etc/init.d/proftpd"
date: 2010-03-16
forum: Server Platforms
---

### Post by ragit on 2010-03-16
can sombody post me the /etc/init.d/proftpd file for ubuntu 9.10

I would like to remove proftpd completely but i get an error.

root@ip13-241:/# apt-get remove proftpd-basic
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
De status informatie wordt gelezen... Klaar
De volgende pakketten zullen VERWIJDERD worden:
  proftpd-basic
0 pakketten opgewaardeerd, 0 pakketten nieuw geÃ¯nstalleerd, 1 te verwijderen en 7 niet opgewaardeerd.
1 pakketten niet volledig geÃ¯nstalleerd of verwijderd.
Door deze operatie zal er 2056kB schijfruimte vrijkomen.
Wilt u doorgaan [J/n]? j
(Database inlezen ... 75868 bestanden en mappen geÃ¯nstalleerd.)
proftpd-basic wordt verwijderd ...
/etc/init.d/proftpd: regel 48: syntaxfout nabij onverwacht symbool 'fi'
/etc/init.d/proftpd: regel 48: `    fi fi'
invoke-rc.d: initscript proftpd, action "stop" failed.
dpkg: fout bij afhandelen van proftpd-basic (--remove):
 subproces installed pre-removal script gaf een foutwaarde 2 terug
update-rc.d: warning: /etc/init.d/proftpd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/proftpd: regel 48: syntaxfout nabij onverwacht symbool 'fi'
/etc/init.d/proftpd: regel 48: `    fi fi'
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: fout tijdens opruimen:
 subproces installed post-installation script gaf een foutwaarde 2 terug
Fouten gevonden tijdens behandelen van:
 proftpd-basic
E: Sub-process /usr/bin/dpkg returned an error code (1)

thanks !

---

### Post by ragit on 2010-03-16
[http://forums.proftpd.org/smf/index.php?topic=1442.0](http://forums.proftpd.org/smf/index.php?topic=1442.0)

here is the solution

---

### Post by ReturnPrivacy on 2011-04-14
Hi, I have the same problem. I tried to install proftp, but I never could get it to work on Ubuntu 10.04? Anyway, now I keep getting updates for it, and they won't install. So, I tried to use the software uninstaller to remove proftp, but it goes most of the way and then errors out by saying it needs the "/etc/init.d/proftpd" file and it can't find it on the system. I went to the link that was posted here but that does not work on Ubuntu. Can anyone help me to remove proftp from my system? 
I am new, and don't know much about Terminal, so speak very "s l o w l y"..
.....LOL.
I appreciate any help for this,
-RT

---

### Post by tgm4883 on 2011-04-14
> **ReturnPrivacy said:**
> Hi, I have the same problem. I tried to install proftp, but I never could get it to work on Ubuntu 10.04? Anyway, now I keep getting updates for it, and they won't install. So, I tried to use the software uninstaller to remove proftp, but it goes most of the way and then errors out by saying it needs the "/etc/init.d/proftpd" file and it can't find it on the system. I went to the link that was posted here but that does not work on Ubuntu. Can anyone help me to remove proftp from my system? 
I am new, and don't know much about Terminal, so speak very "s l o w l y"..
.....LOL.
I appreciate any help for this,
-RT

Can you just do 

```
sudo touch /etc/init.d/proftpd
```

---

### Post by ReturnPrivacy on 2011-04-20
Hi I did that command "sudo touch /etc/init.d/proftpd" and nothing happened?
It just returned to the "desktop:~$" again?
Does that mean it did the command? 
-RT

---

### Post by tgm4883 on 2011-04-20
> **ReturnPrivacy said:**
> Hi I did that command "sudo touch /etc/init.d/proftpd" and nothing happened?
It just returned to the "desktop:~$" again?
Does that mean it did the command? 
-RT

Yep, now can you remove proftpd with apt-get?

---

