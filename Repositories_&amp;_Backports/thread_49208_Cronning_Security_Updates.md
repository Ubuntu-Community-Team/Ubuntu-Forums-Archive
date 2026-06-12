---
title: "Cronning Security Updates"
date: 2005-07-15
forum: Repositories &amp; Backports
---

### Post by tom purl on 2005-07-15
I would like to set up a cron job that does security-only updates on my Ubuntu desktop.  As far as I know, my only mature option for doing updates of every program is the following command:

```
apt-get upgrade
```


This is great for automatically upgrading Firefox from 1.0.4 to 1.0.5 while I'm sleeping or at work.  The problem (and this is a hypothetical example) is that it might also upgrade Zope from 2.7.6 to 2.7.7, which could wreck some web pages that I would be hosting.  Basically, the "upgrade" command upgrades everything, not just the program that have fixed security patches.  

If I remember correctly, this wasn't an issue if you used Debian stable because new packages were only introduced if they fixed security problems, not if they fixed bugs or introduced new functionality.  However, most Debian users used Debian testing or unstable, or a mix of various versions, which meant that the "upgrade" command could very well install packages with new functionality.

I'm using the "multiverse", "universe", and "???" package sites on my system so I can install mp3 players and mplayer and such.  I'm therefore assuming that the "upgrade" command could very well install new versions of packages that could break my system.  

Does anyone know of a command that would only install security updates to my computer?  I certainly don't mind installing new packages on occasion.  I just don't want to cron a job like that because I could break my system and not even know what was installed.  

Any help would be greatly appreciated!

Tom Purl

---

### Post by zeroK on 2005-07-15
[QUOTE=tom purl]I would like to set up a cron job that does security-only updates on my Ubuntu desktop.  As far as I know, my only mature option for doing updates of every program is the following command:

```
apt-get upgrade
```


This is great for automatically upgrading Firefox from 1.0.4 to 1.0.5 while I'm sleeping or at work.  The problem (and this is a hypothetical example) is that it might also upgrade Zope from 2.7.6 to 2.7.7, which could wreck some web pages that I would be hosting.  Basically, the "upgrade" command upgrades everything, not just the program that have fixed security patches.  

If I remember correctly, this wasn't an issue if you used Debian stable because new packages were only introduced if they fixed security problems, not if they fixed bugs or introduced new functionality.  However, most Debian users used Debian testing or unstable, or a mix of various versions, which meant that the "upgrade" command could very well install packages with new functionality.

I'm using the "multiverse", "universe", and "???" package sites on my system so I can install mp3 players and mplayer and such.  I'm therefore assuming that the "upgrade" command could very well install new versions of packages that could break my system.  

Does anyone know of a command that would only install security updates to my computer?  I certainly don't mind installing new packages on occasion.  I just don't want to cron a job like that because I could break my system and not even know what was installed.  

Any help would be greatly appreciated!

Tom Purl[/QUOTE]
 I'm not sure, but perhaps pinning will help you here :)
[https://wiki.ubuntu.com/PinningHowto](https://wiki.ubuntu.com/PinningHowto)

---

### Post by Juergen on 2005-07-15
> This is great for automatically upgrading Firefox from 1.0.4 to 1.0.5
What's the current version of firefox if you don't use backports?
I always thought new versions only come with a new release, but I can see only Firefox 1.0.4 in the repository/pool - and that would be newer than that when Hoary came out, no?
> it might also upgrade Zope from 2.7.6 to 2.7.7AFAIK the only time this should happen with the official repositories is after changing the release, e.g. from Warty to Hoary. Only bugfixes otherwise.
But this firefox thing makes me unsure...

---

### Post by tom purl on 2005-07-15
Thanks a **ton** for the help, Juergen!

[QUOTE=Juergen]But this firefox thing makes me unsure...[/QUOTE]

What I meant to say was that I wanted the new security updates from 1.0.5 to be applied to my machine automatically.  I forgot that Ubuntu uses backports, so I wouldn't actually be using 1.0.5, just the 1.0.4 version plus the 1.0.5 security fixes.  

[QUOTE=Juergen]AFAIK the only time this should happen with the official repositories is after changing the release, e.g. from Warty to Hoary.[/QUOTE]

What's the definition of official repositories?  I'm using all of the ones that were available in Synaptic, including multiverse, universe, superduper-nonfree-verse, etc. Would all of the "standard" Debian repositories be considered non-official by the Ubuntu community in this respect?

Thanks again!

Tom Purl

---

### Post by Juergen on 2005-07-16
I use firefox from 'Backports' so I can't be sure, but AFAIK with the 'official' packages you should have something like 1.0.2_ubuntuxy where xy means a internal ubuntu version xy of 1.0.2 with backported security patches.
So it shouldn't be different to 1.0.4 security-wise, but new features are missing.
But, as I said, FTPing into the repositories I can only see 1.0.4 which is to new for what I thought.

> What's the definition of official repositories?All 4 usually in synaptic, main, restricted, multiverse, universe.
AFAIK you'd need to upgrade to 'Breezy' if you'd want new versions.

And Debian repositories are unofficial in that respect.
AFAIK Ubuntu and debian packages can differ a lot, some time after ubuntu branches its release.
The Ubuntu-people might compile their libs with different flags and Debian 'unstable' is evolving continously...

---

### Post by t2kburl on 2005-07-18
how do you add something like this to cron?

---

### Post by Juergen on 2005-07-18
Write a script, make it executable and put it in '/etc/cron.daily'

---

### Post by t2kburl on 2005-07-18
I'm very much a programming nOOb ...

what would the script need to be?

Would this work?

```
#!/bin/bash
apt-get update && upgrade
```

---

### Post by jcohen on 2005-07-18
If you're running hoary all updates will either be critical bug fixes or security updates so it should be safe to just setup cron-apt to install updates for you. If you have unofficial sources like Backports enabled, you'll want to use the method I outline below. If you don't have any unofficial repositories you don't need to uncomment "# OPTIONS="-q -o Dir::Etc::SourceList=/etc/apt/security.sources.list" and you don't need to create security.sources.list. 

This actually isn't that difficult to do. I've done the same thing on Debian Sarge. You'll first need to install cron-apt:

sudo apt-get install cron-apt

Then, you'll need to edit /etc/apt/cron-apt/config 

sudo gedit /etc/apt/cron-apt/config

If you want to receive emails of the upgrades on your regular email account chnage

# MAILTO="root" to
MAILTO="myemailaddress@myisp.com"

Change #MAILON="error" to
MAILON="upgrade"

Now, this is the important part. Find this line 
# OPTIONS="-q -o Dir::Etc::SourceList=/etc/apt/security.sources.list" and change it to:

OPTIONS="-q -o Dir::Etc::SourceList=/etc/apt/security.sources.list"

Then you'll need to create the new security.sources.list

sudo gedit /etc/apt/security.sources.list

Add these lines to the new file:

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse

If you're just using main & restricted, remove multiverse and universe. 

Now you'll need to edit /etc/cron-apt/action.d/3-download so that cron-apt downloads & installs upgrades. Otherwise it'll just download the updates and you'll need to install them yourself

sudo gedit /etc/cron-apt/action.d/3-download

Change "dist-upgrade -d -u -y" to
upgrade -u -y

Then run "sudo apt-get update" Cron-apt will run every morning at 4 am. you can change this setting by editing /etc/cron.d/cron-apt.

This is my setting which runs cron-apt and 12 noon and 6 PM every day. 

0 12,18	* * *	root	test -x /usr/sbin/cron-apt

---

### Post by berserker on 2005-07-18
[QUOTE=jcohen]Then, you'll need to edit /etc/apt/cron-apt/config 

sudo gedit /etc/apt/cron-apt/config[/QUOTE]

Thank you for this.

However, the above should be "/etc/cron-apt/config"

---

### Post by geearf on 2005-07-27
Hello thanks for this helpfull howto.

I still have a little question, how is mailto supposed to work ?

Cause it is not send me anymail I can check from Thunderbird, though it exists in /var/log/cron-apt .

But i thought it was possible to send a real mail, if I give it a real mail adress, is there something else needed to be done ?

Thanks,

---

### Post by geearf on 2005-07-28
no ideas on this please ?

---

