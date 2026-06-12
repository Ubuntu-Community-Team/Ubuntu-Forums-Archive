---
title: "issues restoring fail2ban and logwatch config after server reinstall"
date: 2015-08-20
forum: Server Platforms
---

### Post by Scrumps on 2015-08-20
See post three (scroll down) for issues


Ignore below, original thread:
After deciding to upgade today from 14.04 LTS to 15.04, however, since then, I have been running into all sorts of issues.

1) KDE no longer loads correctly, at the moment, I can't use a mouse on the desktop, tasbar fails to load, can't load any applications, etc.
2) some services are no longer starting on certain run levels, etc.
3) apps that rely on certain databases seem to be having issues, I can manually fix them, but on reboot, they break again

I am not sure what to do here, as I don't have the time (or the energy to reinstall Ubuntu Server edition completely, and then install KDE to see if the issues with the KDE problems have fixed themselves)

I was wondering if I could get some help, or if there was a way to verify if all the files and config files needed for applications to run are setup correcrtly. As of right now, I have ran dist-upgrade, apt-get update && apt-get upgrade, and do-release-upgrade and have no more updates to install.

---

### Post by SeijiSensei on 2015-08-21
Last time I looked at Kubuntu 15.04 it was most definitely "not-ready-for-prime-time."  KDE5 is still pretty flaky and some basic programs like Gwenview do not work as well they do on the KDE4 platform.  Also why are you starting from the server base and adding KDE?  Just install Kubuntu.  You can always add the server programs to a desktop installation.

As for servers, any production server should be running on a version with long-term support.  I'd never install anything but an LTS version, or something like CentOS, on a production server.

I'd just bite the bullet and reinstall 14.04.

---

### Post by Scrumps on 2015-08-23
Hey, thanks, yeah, I decided after messing with 15.04 for three days, that it just wasn't worth the trouble of setting everything back up.

Right now the only remaining things I need to setup (if I remember everything anyways) is groups, users, logwatch, fail2ban, postgresql, tt-rss (going to need help with these two).

But for now, fail2ban and logwatch are having issues. I restored my config from the ubuntu 14.04 install. Right now fail2ban only seems to be loading ssh on fail2ban even though others should be and are enabled according to the config file. 
For logwatch, if I run the follwing command:

root@server:/# logwatch
postdrop: warning: unable to look up public/pickup: No such file or directory

I receive this message. Logwatch's /etc/ files were copied over as well, and prior to the upgrade and screw up, this was e-mailing me daily messages from an e-mail address at @gmail.com, and also sending an e-mail to a different @gmail.com account. I am pretty sure that this was using postfix + sendmail, but I am not sure. I noticed now, that you can't have postfix and sendmail installed at the same time (I did have it at one point, not sure why no longer). I am also not sure if there are any packages or automated things that rely on postfix.  So I am not sure how to resolve this issue to use smtp.gmail.com with sendmail. Or how to setup postfix to send logwatch's mail instead. If I use sendmail, I receive email that will eventually get blocked, because it is not authorized to be a mail server.

---

### Post by mastablasta on 2015-08-25
would sSMTP work for you? : [https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)
it's just for sending messages. and super easy to setup with gmail. for some reason when I ran it on debian it got blocked and it spammed a lot, so google disabled the account. second time around I set it up with Ubuntu. works ok now.


I don't know about logwatch. but for fail2ban would it be ok to see the setup file?

if you are restoring, make sure you have the correct groups and permissions set on files. 

 fail2ban - it's good to setup permanent jail (life without parole :) ). I used this option: [http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/](http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/)

---

### Post by Habitual on 2015-08-27
> **Scrumps said:**
> Right now fail2ban only seems to be loading ssh on fail2ban even though others should be and are enabled according to the config file. 
Is that /etc/fail2ban/jail.conf or are you using /etc/fail2ban/jail.local?

You can and should check out
```
fail2ban-client status 
```
and additionally,
```
fail2ban-client status <jail>
```

It is advised that you copy /etc/fail2ban/jail.conf to  /etc/fail2ban/jail.local and edit /etc/fail2ban/jail.local to suit your preferences.

For me to continue, 
Please show us the "according to the config file" contents and identify "the config file" please by name and its location.

Thank you,

---

