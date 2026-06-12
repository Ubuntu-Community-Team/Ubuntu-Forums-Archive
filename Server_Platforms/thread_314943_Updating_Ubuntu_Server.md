---
title: "Updating Ubuntu Server"
date: 2006-12-08
forum: Server Platforms
---

### Post by dbqp on 2006-12-08
Hi All,

I have installed Ubuntu Server 6.06 using the Perfect setup on HowToForge.  This includes ISPConfig, Webmail, quota, etc...

My question is if I do an apt-get install update, will my system break or will all neccessary upgrades get applied?  Should I do this at root? Any other advice to pass along for server upgrades through the repository?

Any feedback is worthwhile!

Thank you.

---

### Post by brt on 2006-12-08
first do you really need to upgrade? as dapper has longterm support  its safe to stay with dapper.

my experience is that on a server upgrades are much painless as on desktops where you have lots of more packages to replace.

at first make backups of all you important configuration files!

then i recommend using:

sudo aptitude update
sudo aptitude dist-upgrade

before upgrading just to be sure everything is uptodate, then:

replace dapper with edgy in your /etc/apt/sources.list and again:

sudo aptitude update
sudo aptitude dist-upgrade

on desktop systems i just had to repeat the last command a couple of times until all dependency issues had been resolved.

when asked by the installer what to do with a new configuration file, have look at the difference and then decide. if you replace it with the new one, be sure to add needed configuration lines for ispconfig.

i am not sure, but it could be wise to do an ispconfig update after the upgrade, so everything gets compiled within the new enviroment.

---

### Post by dbqp on 2006-12-08
Thank you brt, but I am not looking to upgrade, just update.

I agree - I want to stay on the supported 6.06 platform. But I do want to keep my server up to date with any security fixes. If I do the update, will I need to update ISPConfig, Webmail, and other packages or if I have my multiverse repositories added to my sources all will be good?

Thanks!

---

### Post by brt on 2006-12-08
no. if you just want to update, its very unlikely that you may run into problems. however its always a good idea to backup your confguration, so if you overwrite any configfile you will be able to fix the new config easyly. (but the update will also do a backup whenever you decide to overwrite a configfile, during such an update)

i am sure all will be good, you won't need to reinstall ispconfig if you stay with dapper, as you will just recieve security updates and no new versions of software.

if needed, the update process will ask you, what to do with a new config file, so you will have the opportunity to watch the differnces of the two files so you will be able to decide what to do, either replace or keep the old config.

so just use:

sudo aptitude update
sudo aptitude dist-upgrade

---

### Post by az on 2006-12-08
If you have installed everything from the Dapper repositories, you will be able to update just fine.

If you compiled stuff from source of have gotten them from other repos, you're on your own.

---

### Post by technodigifreak on 2006-12-11
I haven't encountered a problem with applying updates to my ISPconfig machine.  However, I do make a full backup before I begin the update and then watch it closely for a day or two afterwords.  Guess I'm paranoid like that. Think of a backup kind of like a condom, you'd rather have it and not need it, than need it and not have it. :D

---

