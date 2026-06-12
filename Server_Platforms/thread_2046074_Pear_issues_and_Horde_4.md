---
title: "Pear issues and Horde 4"
date: 2012-08-22
forum: Server Platforms
---

### Post by dotchristopher on 2012-08-22
Hi all!

Sorry to have to ask but this is quite literally my last step to server perfection and I've been tearing my hair out! I've been trying to get activesync working from a groupware solution for a small office. Originally I'd installed eGroupware, which works very well but requires z-push for activesync. But Horde to the rescue- Horde 4 already does this! Fantastic! Now to install it...

Following the published instructions I came across an issue that a few people have already experienced ([http://pear.php.net/bugs/bug.php?id=18450](http://pear.php.net/bugs/bug.php?id=18450)) which points to the fact that I probably have a broken/custom pear installation, although I'm sure I don't. Trying to specify/hardlink to the correct pear config file (my system shows pear.conf at /etc/pear/pear.conf although pear config-show states /etc/pear.conf) however still fails with the same error ```
Could not save horde_dir configuration value to PEAR config.
```

No worries then, let's just reinstall PEAR I thought.. ```
apt-get remove --purge and apt-get install php-pear
``` (also php-log, which seemingly got caught as dependent). I already have a working PEAR setup (including, amongst many others HTTP_Download), but not to worry- a quick re-install should sort everything out. 

Thing is, the apt-get remove --purge seems to have left PEAR in an inconsistent state.
When I tried to go back and start from step 1 of the Horde install docs ([http://www.horde.org/apps/webmail/docs/INSTALL#quick-install](http://www.horde.org/apps/webmail/docs/INSTALL#quick-install)) I was told that the horde pear channel pear.horde.org already existed. Hold on... what about --purge?! No matter, I tried to run the install script to install the horde_role, which failed complaining that the files didn't exist (fair enough, really), but that doesn't help. I can't re-init the horde_role because it's marked as already installed. Clearly not so --purge.

Never mind, let's just remove the channel. ```
 pear channel-delete pear.horde.org
``` tells me ```
Channel "pear.horde.org" has installed packages, cannot delete
```
What?! --purge?!

Never mind, let's find the packages so we can remove them:
```
root@alt:/etc/echonest-server/util# pear list -c pear.horde.org
Installed packages, channel pear.horde.org:
===========================================
Package    Version State
Horde_Role 1.0.0   stable
root@a:/etc/# pear uninstall horde_role
pear/horde_role not installed

```
PEAR seems to make distinction between upper and lower case
```
root@a:/etc/# pear uninstall Horde_Role
pear/Horde_Role not installed

```

WHAT?! 

Ok then, what about HTTP_Download?
```
root@a:/etc/# pear install HTTP_Download
pear/HTTP_Download is already installed and is the same as the released version 1.1.4
```

Strange... although even that seems to be a lie... attempting to use my known good HTTP_Download app hangs when it tries to, er, perform a http file download. In fact it crashed my browser when I was half way through posting this.

Please, has anyone got any suggestions? Preferably, I'd love to trash *everything* belonging to PEAR and start again. Although I'm sure this was just a stock 12.04x64 (dist-upgrade from 10.04) installation originally via apt-get install php-pear.

Has anyone else experienced this config issue with Horde 4? Has anyone successfully setup Horde 4 on Ubuntu 12.04? 

Thanks in advance for all your help or suggestions!

---

