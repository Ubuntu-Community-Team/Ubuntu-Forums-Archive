---
title: "cant upgrade 9.04 to 9.10 at all"
date: 2012-01-31
forum: Server Platforms
---

### Post by kustomjs on 2012-01-31
Hi Guys
I am still running 9.04 on my webserver and I would like to upgrade it to 9.10 then to 10.04lts and I cant upgrade it and fresh install is out of the option.

Thanks.

---

### Post by lisati on 2012-01-31
9.04 has passed its end of life, and in order to do an upgrade, you will likely need to tinker with your sources.list file. You might find the information at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) helpful.

---

### Post by Wayne_V on 2012-01-31
no more online updates .....

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

---

### Post by kustomjs on 2012-01-31
I get this when I try to update it:


Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
tar: Removing leading `/' from member names

Reading cache

Checking package manager

Can not upgrade

An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

---

### Post by Cheesemill on 2012-01-31
See Wayne_V's post above.

You need to use a CD to upgrade.
[https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD](https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD)

---

### Post by kustomjs on 2012-01-31
If I use the cd will it clean the information off the disc or not? because clean install is not a option.

---

### Post by Cheesemill on 2012-01-31
> **kustomjs said:**
> If I use the cd will it clean the information off the disc or not? because clean install is not a option.

No, it's an upgrade.

But do make sure you have a backup as upgrades can sometimes go wrong.

---

### Post by snowpine on 2012-01-31
> **kustomjs said:**
> I get this when I try to update it:


Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
tar: Removing leading `/' from member names

Reading cache

Checking package manager

Can not upgrade

An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

You have to upgrade to Karmic first, then Karmic to Lucid.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by kustomjs on 2012-01-31
Alright so how do I make a back up?

---

### Post by kustomjs on 2012-01-31
Alright I tried to do the upgrade via command line and I get this error:

sudo mount -o loop /media/cdrom0/ubuntu-10.04.3-alternate-i386.iso /mnt/alternate
/media/cdrom0/ubuntu-10.04.3-alternate-i386.iso: No such file or directory

what do I need to do fix this error?

---

### Post by Cheesemill on 2012-01-31
Read the page that I posted above.

If you have burnt the CD then you don't have to mount the ISO image, just do:
```
cd /media/cdrom0
sudo ./cdromupgrade --frontend=DistUpgradeViewText
```

If you haven't burnt the ISO to a CD then do:
```
mkdir /mnt/alternate
sudo mount -o loop /path/to/alternate-cd.iso /mnt/alternate
cd /mnt/alternate
sudo ./cdromupgrade --frontend=DistUpgradeViewText
```

---

### Post by kustomjs on 2012-01-31
when I do this: 
cd /media/cdrom0
sudo ./cdromupgrade --frontend=DistUpgradeViewText

I get command not found

yes I have the cd burnt.

---

### Post by Cheesemill on 2012-01-31
What's the output of:
```
ls -l /media/cdrom0
```

---

### Post by kustomjs on 2012-01-31
tim@server1:~$ ls -l /media/cdrom0
total 0
tim@server1:~$

and if I do:

tim@server1:~$ ls -l /media/cdrom
lrwxrwxrwx 1 root root 6 2008-07-07 21:50 /media/cdrom -> cdrom0
tim@server1:~$

---

### Post by Cheesemill on 2012-01-31
You need to mount the CD first.

Also make sure you are using the ubuntu-9.10-alternate-i386.iso CD.

I'm signing off for the night now, but just follow the instructions in the links I posted, I can't really explain it any better than they do.

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)
[https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD](https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD)

---

### Post by kustomjs on 2012-01-31
Alright I will do that.

---

### Post by Cheesemill on 2012-01-31
[http://old-releases.ubuntu.com/releases/karmic/](http://old-releases.ubuntu.com/releases/karmic/)

---

### Post by lisati on 2012-01-31
> **kustomjs said:**
> Alright I will do that.

Try here: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by kustomjs on 2012-01-31
Alright so when I do this part what do I point path to? like /media/cdrom/ or media/cdrom0/ then is it ubuntu-9.10-alternate-cd.iso or is it just alternate-cd.iso ?

sudo mount -o loop /path/to/alternate-cd.iso /mnt/alternate

---

### Post by arrrghhh on 2012-01-31
I don't mean to be a jerk, but why is fresh install not an option?

Take a backup of all your configuration files and anything document-wise that isn't a program that can be reinstalled.

Fresh install of 10.04.

Reinstall apps, restore configs, docs, etc... might take a bit but the system will not only be clean, you also will run into a lot less headache.  Trust me, upgrading from 9.04 to 9.10 to 10.04 is going to take WAY more time than a fresh install.

Use this as a learning experience - always keep your servers on LTS releases, and always make sure to update them before the product goes EOL!  This is much easier on LTS releases as it takes much longer to go EOL than regular releases.

Good luck.

To answer your latest question, you can mount it where ever you want.

```
sudo mount -o loop /path/to/alternate-cd.iso /mnt/alternate
``` Would work fine if /mnt/alternate exists, and you actually populate the /path/to/alternate-cd.iso.

---

### Post by kustomjs on 2012-01-31
Bc its going take couple hours to back up 20G of disk if u want to know that is why fresh install is out of option.

---

### Post by arrrghhh on 2012-01-31
> **kustomjs said:**
> Bc its going take couple hours to back up 20G of disk if u want to know that is why fresh install is out of option.

You'd rather spend 6-8 hours trying to get an upgrade to work (keep in mind that's only one upgrade, you still have another), that is quite likely to fail?

Seriously, you will save A LOT of time just backing stuff up and starting fresh.  If you have a separate /home, you don't even have to format it when starting fresh - so no need to backup that partition.

Again, not trying to be a jerk - just trying to be reasonable.  Cost/benefit analysis...

---

### Post by kustomjs on 2012-01-31
There is no cost here its a home server fyi. All my stuff is located in /var/www and plus I host some websites off of this server.

and I tried to mount it and still getting command not found.

---

### Post by kustomjs on 2012-01-31
Alright I tried it with sudo sh ./cdromupgrade --frontend=DistUpgradeViewText

but still getting An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

---

### Post by arrrghhh on 2012-01-31
> **kustomjs said:**
> Alright I tried it with sudo sh ./cdromupgrade --frontend=DistUpgradeViewText

but still getting An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

> **Cheesemill said:**
> You need to mount the CD first.

**Also make sure you are using the ubuntu-9.10-alternate-i386.iso CD.**

I'm signing off for the night now, but just follow the instructions in the links I posted, I can't really explain it any better than they do.

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)
[https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD](https://help.ubuntu.com/community/Upgrades#Upgrades_via_alternate_CD)

Could not explain it any better than this.

I would say the part I bolded is especially important.  You won't be able to go from 9.04->10.04.  You have to go to 9.04->9.10, then to 10.04... Oy, that is going to be a PITA!

I really, truly hope you have backups of everything.  Upgrades usually are not pretty, especially if you have a lot of custom stuff.  Or going thru two of them...  I'm going to do it again - backup that data (because you should anyways) and start from 10.04 fresh.

April 2015 is the EOL date for 10.04 server.  Heck, it's ironic but if you were on 8.04 that doesn't EOL until April 2013...

---

### Post by lisati on 2012-01-31
Thinking back to my recent experience of upgrading my server, making a backup of the important stuff and then a fresh install turned out to be way easier. Having said that, links have already been provided to tutorials and other relevant information that will let you proceed with an upgrade.

---

### Post by kustomjs on 2012-01-31
Alright I finally got upto 10.04 without cd's but I just followed this guide: [http://echenh.blogspot.com/2010/04/how-to-upgrade-ubuntu-server-904-to-910.html](http://echenh.blogspot.com/2010/04/how-to-upgrade-ubuntu-server-904-to-910.html)

---

### Post by kustomjs on 2012-01-31
its official I was able to load 10.04.3 LTS with that guide I posted up.

Thanks for all help.

---

