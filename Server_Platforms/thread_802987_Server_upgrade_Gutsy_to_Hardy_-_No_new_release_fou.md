---
title: "Server upgrade Gutsy to Hardy - No new release found"
date: 2008-05-21
forum: Server Platforms
---

### Post by moaxey on 2008-05-21
am attempting to upgrade a server install from 7.1 to 8.04

followed these simple instructions
[https://help.ubuntu.com/community/HardyUpgrades#head-e059d5452a24b50d09c64df48058ef2d834eb197](https://help.ubuntu.com/community/HardyUpgrades#head-e059d5452a24b50d09c64df48058ef2d834eb197)

but the do-release-upgrade command returned
'No new release found'

Here is a thread with a similar problem but upgrading from dapper:
[http://ubuntuforums.org/showthread.php?t=800707&highlight=hardy+server+upgrade](http://ubuntuforums.org/showthread.php?t=800707&highlight=hardy+server+upgrade)

Despite feeling awkward about installing an entire xserver unnecessarily, I did it, only to receive the same message as before.

Since then I've been trying different repositories, and put my desktop machine successfully into the upgrade process.

I just don't know what else to do!

---

### Post by cdtech on 2008-05-21
I did the dapper to Hardy and had the same problem.

I don't know why, but I had to replace my exsiting sources.list with a new one to get the update to work correctly.

So I copied this list to my sources.list:
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-proposed main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
```

Once I replaced the list I verified that my current install was completely up to date:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```

Then I did the:
```
sudo aptitude install update-manager-core
start the upgrade using:
sudo do-release-upgrade
```

Hope this helps........

---

### Post by moaxey on 2008-05-22
I think it was just some weird network thing here...

I tried running through one of our proxy servers, and got an error from untarring hardy download tool

```
sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmp4MeEru/hardy.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

```

then apt-get upgrade would not connect to any servers

so I logged out and in again to clear environment

ran do-release-upgrade again 

and it appears to be working

---

