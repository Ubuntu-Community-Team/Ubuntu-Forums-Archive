---
title: "How to upgrade to Ringtail daily build?"
date: 2012-11-10
forum: Ubuntu Development Version
---

### Post by heavyonion on 2012-11-10
I thought my last post might have been in the wrong place,Sorry.
Any way any ideas on how to upgrade to 13.04 daily build with out a fresh install from an ISO? Is there a daily build repository? Haven't found one yet. any way thanks for what ever help. I guess my other post about the sudo do-release-upgrade -d problem is common right now?

---

### Post by cariboo on 2012-11-10
> **heavyonion said:**
> I thought my last post might have been in the wrong place,Sorry.
Any way any ideas on how to upgrade to 13.04 daily build with out a fresh install from an ISO? Is there a daily build repository? Haven't found one yet. any way thanks for what ever help. I guess my other post about the sudo do-release-upgrade -d problem is common right now?

Raring is a moving target until it's released in April. The daily builds are just that, a build at one point during the day. The best way to get involved is to use this command, to change the repositories from Quantal to Raring:

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```

then run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

As to:

```
sudo do-release-upgrade -d 
```

there is no problem with the command, as it only works for upgrading to a released version.

To keep current, most of us upgrade several times during the day.

---

### Post by heavyonion on 2012-11-10
Thanks,

---

### Post by jokerdino on 2012-11-11
> **cariboo907 said:**
> 

As to:

```
sudo do-release-upgrade -d 
```

there is no problem with the command, as it only works for upgrading to a released version.

To keep current, most of us upgrade several times during the day.

No no no. That's not correct. 

If you check the man page of do-release-upgrade, you would see this:

```
-d, --devel-release
              Check if upgrading to the latest devel release is possible
```

Basically, if you append a -d parameter, it would naturally let you upgrade to the current devel release, which happens to be raring at the moment. It is currently only failing because of a [bug]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1076186") and not because the command is meant for upgrading to a released version.

For upgrading to a released version, you would just use the command without any added parameter.

---

### Post by jerrylamos on 2012-11-11
Development releases have and do and are expected to crash.

People all over the world are upgrading and writing packages and some could be incompatible.
Development releases have and do and are expected to crash.

Upgrades often screw up there are many tales over the ubuntu forums of woe where someone tried an upgrade which failed and now they are stuck with no way to downgrade to a running ubuntu.

So what we do in testing unstable might crash development half baked ubuntu is have back up partitions example quantal and/or precise LTS.

For raring ringtail I'm using two partitions.  Install or upgrade to one, if it works, then next upgrade/install to the second partition and alternate from there.

You learn a lot of linux from doing installs - and installs show up bugs which is why we testers are even running raring ringtail.

Now some people have experience that by forever doing upgrades they keep up with the latest ubuntu.  That's like "rolling upgrades" which some linux distributions do.  

I've found an install plus upgrades daily frankly works for a while, then the disk space usage gets fatter and fatter despite apt-get clean, autoclean, autoremove.  And running two ubuntu side by side the new install will be different than the forever upgraded one.

Now running development unstable ubuntu's and doing installs teaches a lot about how to get your customized setup running what's needed and what's not.

So when there wasn't working daily builds I did a new fresh quantal release, changed quantal to raring in /etc/apt/sources.list, and upgraded.  Now that there are daily builds I've installed those.

So far only problem has been for a few days daily build install would wipe out peoples whole hard drive and install a 3GB image onto a 120 GB hard drive losing everything else.  Not too many screams since us testers look out for such boo-boos.

When install went by the select partition stage I quick cancelled out, read the forums, and found out how to get install working right.

If you're on raring ringtail, watch this forum closely for reported screw-ups before doing anything....

---

### Post by grahammechanical on 2012-11-12
I used the first two commands given by cariboo907 to convert a fresh install of 12.10 into the beginnings of a Raring ringtail installation. I did the same when I wanted to turn a Precise Pangolin install into a Quantal Quetzal one. It works.

At the end of the Precise development cycle I tested the upgrade path from 10.04 and 11.10 to 12.04. I followed the testcase which said this:

> 1. Install all update available for the release you want to upgrade.
2. Run update-manager -d -c from a terminal.
3. Click the upgrade version button
4. Watch it upgrade, noting any errors.

[http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade]("http://testcases.qa.ubuntu.com/Testing/Cases/DesktopUpgrade")

Come the last week of November I shall be doing at least one fresh install of a Raring daily image as part of the first Cadence testing week.

[https://wiki.ubuntu.com/QATeam/Cadence/Raring]("https://wiki.ubuntu.com/QATeam/Cadence/Raring")

Regards.

---

### Post by ventrical on 2012-11-12
> **jerrylamos said:**
> Development releases have and do and are expected to crash.

You learn a lot of linux from doing installs - and installs show up bugs which is why we testers are even running raring ringtail.

.

 This is a good bottom line. Also, if possible, have a few extra PCs/Laptops for testing if at all possible. (I know you do.)

regards...

---

### Post by gixxxerjoe on 2013-03-23
> **ventrical said:**
> This is a good bottom line. Also, if possible, have a few extra PCs/Laptops for testing if at all possible. (I know you do.)

regards...

Would there be any disadvantage to testing these virtually?

---

### Post by cariboo on 2013-03-23
> **gixxxerjoe said:**
> Would there be any disadvantage to testing these virtually?

You'll be running on virtual hardware, so testing drivers is out, but running programs like you normally would may cause some problems, so you can still create bug reports.

---

### Post by PJs Ronin on 2013-03-23
> **gixxxerjoe said:**
> Would there be any disadvantage to testing these virtually?

That's where I start, with a VM, mainly because I'm a Linux noob.   I can replicate my 'production' configuration within a VM and then upgrade/test within the VM looking for problems for my system/configuration rather than pushing the limits of the new Ubuntu version.   If necessary I can blow the VM away, or reload to a previous snapshot, and continue punching.   I let others create life from a command prompt and stand in awe of them.

---

### Post by cariboo on 2013-03-23
> **PJs Ronin said:**
> That's where I start, with a VM, mainly because I'm a Linux noob.   I can replicate my 'production' configuration within a VM and then upgrade/test within the VM looking for problems for my system/configuration rather than pushing the limits of the new Ubuntu version.   If necessary I can blow the VM away, or reload to a previous snapshot, and continue punching.   I let others create life from a command prompt and stand in awe of them.

There is nothing awesome or extraordinary about the command prompt, it's just another tool, that in most cases has been replaced by gui apps. For some of us it's just easier to use. :)

---

