---
title: "Upgrade commands on UF"
date: 2009-10-30
forum: Resolution Centre
---

### Post by slakkie on 2009-10-30
Hello,

with the current release of Karmic I see a lot of people telling others how to upgrade:

```

update-manager -d

```

I don't know where this comes from, but this advise is plain wrong. It learns people to upgrade to **development** releases. When someone does this on Karmic in a few weeks time they could be in serious trouble as they will upgrade to a development release (lucid).

Maybe an idea to make a thread to tell people how to properly upgrade?

====
HOWTO upgrade Ubuntu:

```

# Via a GUI
update-manager

# Via cli:
sudo aptitude install update-manager-core
sudo do-release-upgrade

# Via alternate CD as image, GUI
mount -o loop /path/to/alternate-cd-of-karmic.iso /path/to/mountpoint
cd /path/to/mountpoint
sudo ./cdromupgrade

# Via alternate CD as image, cli
mount -o loop /path/to/alternate-cd.iso /path/to/mountpoint
cd /path/to/mountpoint
sudo ./cdromupgrade --frontend=DistUpgradeViewText

# The Debian way (not advised by Ubuntu developers):
sudo aptitude update
sudo aptitude safe-upgrade
sudo perl -p -i.ORIG -e 's/jaunty/karmic/g' /etc/apt/sources.list
sudo aptitude update
sudo aptitude install dpkg apt aptitude
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

```

---

### Post by bodhi.zazen on 2009-10-30
I agree this is a common "mistake", I [s]have made it myself[/s] see it all the time.

The mistake comes because people are familiar with upgrading during the testing phase, before the release, in which case they need the -d .

The advice is posted on the Ubuntu wiki :

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I suggest:

1. Education within the threads when you see this advice.

2. Link to the wiki page as it is most comprehensive.

Personally I fine people do not read stickies for things like this, so education within the thread is best.

Once people see the mistake, others will help and I will pass this advice to the BT as well.

---

### Post by slakkie on 2009-10-30
> **bodhi.zazen said:**
> 
I suggest:

1. Education within the threads when you see this advice.
2. Link to the wiki page as it is most comprehensive.

Personally I fine people do not read stickies for things like this, so education within the thread is best.

Once people see the mistake, others will help and I will pass this advice to the BT as well.

Maybe add this recommendation in the following post/announcement:
[http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331) ??

The problem with explaining this in all kinds of threads is that there are too many threads where this advise is given. I see this in any upgrade thread, 8.04 to 8.10, 8.10 to 9.04 and now with 9.04 to 9.10. Maybe put this as a sticky in the install/upgrade forum. While we know not everyone will read this, it will spread knowledge for those who read it and hopefully they will inform others.. 

BTW, what is BT?

---

### Post by slakkie on 2009-10-30
BTW, I've created the following wiki page, perhaps we can put this somewhere: [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Hopefully Google will index it and people will read it :)

---

### Post by bodhi.zazen on 2009-10-30
I have more faith in education then in stickies.

Thank you for the advice, we will take it under advisement. Thank you as well for the wiki page.

---

