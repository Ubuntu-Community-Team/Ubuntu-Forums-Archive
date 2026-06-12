---
title: "Install server 8.04 RC today and ..."
date: 2008-04-22
forum: Server Platforms
---

### Post by lord_farfig on 2008-04-22
Hi guys,

I've just built a new server for my home/office and I'm curious to test 8.04 since it's going to be an LTS distro.  Anyway, I wish to know if I install the RC (DLing now), can I (in 3, err 2 days) upgrade via APT to the FINAL?  

Not that I can't wait 3 days, but I would rather have this machine online and serving files ASAP.  I get antsy with new equipment!  Hehe. :)

-Eric

(p.s. I posted in Install/Upgrade too)

---

### Post by conjur3r on 2008-04-22
Yes.  This is how we keep on top of beta releases :)  There's nothing special about it.

---

### Post by lord_farfig on 2008-04-22
> **conjur3r said:**
> Yes.  This is how we keep on top of beta releases :)  There's nothing special about it.

Excellent, that is what I thought.  Granted I'll probably DL 8.04 when it *is* available too, but this should get me started and be a bit easier!  Thanks!

-Eric

---

### Post by adamos on 2008-04-22
sudo do-release-upgrade --devel-release   <- to upgrade to 8.04 rc now

sudo do-release-upgrade  <- when its finalized in 2 days

---

### Post by pot_roast on 2008-04-22
This might be another thread in itself, but are LTS -> LTS upgrades officially supported? I have a 6.06 LTS server, and I can't risk having it blow up on me.

It's a very light duty server, and everything has been installed from the dapper repos (courier/mysql/postfix/antispam stuff/apache & php)

If i can do-release-upgrade from 6.06 LTS to 8.04 LTS, I'd be a happy human. :)

It *seemed* to work OK on a vanilla install, but I did not test on a production machine with configured stuff installed.

---

### Post by Brazen on 2008-04-23
> **pot_roast said:**
> This might be another thread in itself, but are LTS -> LTS upgrades officially supported? I have a 6.06 LTS server, and I can't risk having it blow up on me.

It's a very light duty server, and everything has been installed from the dapper repos (courier/mysql/postfix/antispam stuff/apache & php)

If i can do-release-upgrade from 6.06 LTS to 8.04 LTS, I'd be a happy human. :)

It *seemed* to work OK on a vanilla install, but I did not test on a production machine with configured stuff installed.

Yes, LTS-to-LTS upgrades are officially supported.  And given that their paying enterprise customers will be doing mostly LTS-to-LTS upgrades, it will probably be at least as reliable as a Gutsy-to-Hardy upgrade.

---

### Post by Wim Sturkenboom on 2008-04-23
> **pot_roast said:**
> ... and I can't risk having it blow up on me.
...
...
It *seemed* to work OK on a vanilla install, but I did not test on a production machine with configured stuff installed.
If you can't risk that it blows up on you, you certainly have a fully configured redundant system available. So try it on that one first (instead of on a vanilla install) and next on your main system.

---

### Post by lord_farfig on 2008-04-24
> **pot_roast said:**
> This might be another thread in itself, but are LTS -> LTS upgrades officially supported? I have a 6.06 LTS server, and I can't risk having it blow up on me.

It's a very light duty server, and everything has been installed from the dapper repos (courier/mysql/postfix/antispam stuff/apache & php)

If i can do-release-upgrade from 6.06 LTS to 8.04 LTS, I'd be a happy human. :)

It *seemed* to work OK on a vanilla install, but I did not test on a production machine with configured stuff installed.

That is an awesome tid-bit of information!  I have 6.06 on my home server too and to upgrade that to 8.04 would be much easier than having to reconfigure all of it...  albeit it wouldn't take more than 30 minutes! :lolflag:

---

### Post by /etc/init.d/ on 2008-04-24
> **pot_roast said:**
> This might be another thread in itself, but are LTS -> LTS upgrades officially supported?
Yes, this is supported, see:

[https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197](https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197)

If you are not running an exotic configuration and run completely from the APT repositories, your chances are good.

---

