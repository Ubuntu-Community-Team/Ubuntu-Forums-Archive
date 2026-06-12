---
title: "Effect of do-release-upgrade on 11.04 version."
date: 2013-08-02
forum: Server Platforms
---

### Post by vincent4 on 2013-08-02
Hello,

I got few month ago a old server with 11.04 version of Ubuntu:
```
root@ve:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```

I installed Apache (PHP, MySQL) Apache-SSL and postfix for the mail server.

In order to avoid re-installing all the server from scratch I would like to make an upgrade. So, in source.list I have put:
```
root@ve:~# cat /etc/apt/sources.list
#


# deb cdrom:[Ubuntu-Server 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted


## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ natty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse


# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ CODENAME-backports main restricted universe multiverse

```

Thanks to these links on old-releases I could install update-manager-core:
```
apt-get install update-manager-core
```

Now I have to launch[FONT=UbuntuMono, courier, monospace][COLOR=#333333] [/COLOR][/FONT][B]do-release-upgrade.

[/B]Will do-release-upgrade do an upgrade to 11.10 ? I want to make an upgrade to 11.10 before making an upgrade to 12.04.

I do everything by SSH and I can't have a physical access to the server. Will it cause a problem, a problem like it will prompt a question at the reboot of the server to continue the upgrade ?

Thanks.

---

### Post by TheFu on 2013-08-02
From 11.04 the only upgrade path is 11.10, then 12.04 - which is where most people should stop for another18 months - until 14.04 is released.

Nobody can answer the question about reboot questions before networking comes up for you. We don't know.  Your hardware, the drivers, your packages, all sorts of things can go wrong.  In 12.04, networking changed too. I had to relearn NOT to touch the /etc/resolve.conf and do DNS settings inside the interfaces file.  That could make the remote connection post-upgrade fail.

I was maintaining a remote system 3 states away. I waited until the day before traveling there to attempt the 10.04 to 12.04 upgrade.  It worked, BTW., but I didn't expect that it would and was prepared with perfect backups to restore from, if necessary.

---

### Post by vincent4 on 2013-08-02
> **TheFu said:**
> From 11.04 the only upgrade path is 11.10, then 12.04 - which is where most people should stop for another18 months - until 14.04 is released.

Nobody can answer the question about reboot questions before networking comes up for you. We don't know.  Your hardware, the drivers, your packages, all sorts of things can go wrong.  In 12.04, networking changed too. I had to relearn NOT to touch the /etc/resolve.conf and do DNS settings inside the interfaces file.  That could make the remote connection post-upgrade fail.

I was maintaining a remote system 3 states away. I waited until the day before traveling there to attempt the 10.04 to 12.04 upgrade.  It worked, BTW., but I didn't expect that it would and was prepared with perfect backups to restore from, if necessary.

OK done. Now the server is running 11.10 Ubuntu, everything looks working fine except the mail server. Apache does not send mails and I don't receive any mails anymore on [email]mymail@mydomain.com[/email] 
I don't understand why. It was so difficult to install postfix. :-(

---

### Post by TheFu on 2013-08-02
I don't think there have been many changes to postfix in a while that matters in most configs.  I'd make a backup of the new directory, then restore the directory from the pre-upgrade version, and do the same with /etc/aliases and /etc/mailhost ... might also need /etc/hosts.

I install satellite postfix systems here all the time ... probably a few times a month. That is easy.  Setting up the main system can be easy for normal installs too, but you might have some unusual needs.

Do you really let Apache send emails? Seems scary to me.

To troubleshoot more about postfix, it would probably be best to start a new question and provide more specifics on the config.  However, I'd recommend getting to 12.04 before you do that.  11.10 has not been supported for over a year - having that system on the internet is not safe.

---

