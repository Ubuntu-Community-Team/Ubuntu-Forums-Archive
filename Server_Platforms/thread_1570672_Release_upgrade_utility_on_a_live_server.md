---
title: "Release upgrade utility on a live server?"
date: 2010-09-08
forum: Server Platforms
---

### Post by Vunutus on 2010-09-08
Does anyone have any experiences to share regarding this? Our server is still running Hardy and, of course, the time is rapidly approaching where I need to upgrade to the latest LTS.

Now, I'm sure a complete re-installation would obviously be preferred, but I noticed that there's a release upgrade feature for Ubuntu server. Is this reliable enough to use on our production server without wrecking everything? I really don't want to have to go through the process of configuring software RAID and all our other services again.

Obviously I'll take normal precautions such as making tons of backups and starting the process on a weekend so if the proverbial poo hits the fan I can work over the weekend and have everything up and rolling by monday. This server is not exposed to the outside world as a webserver or anything like that so it can afford to be down over the weekend (although not preferable since we have financial cron jobs and such running in the wee hours of the morning).

---

### Post by arrrghhh on 2010-09-08
You may have already read this but...

[LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) - read the section on "Network Upgrade for Ubuntu Servers (Recommended)".

I'd say it's fairly safe.  I've had a few issues with upgrades in the past, it really depends on what you have installed.

---

### Post by Vunutus on 2010-09-08
> **arrrghhh said:**
> You may have already read this but...

[LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) - read the section on "Network Upgrade for Ubuntu Servers (Recommended)".

I'd say it's fairly safe.  I've had a few issues with upgrades in the past, it really depends on what you have installed.

Yeah that's the article I read that spurred me to make this topic since I had previously been planning a complete reinstall and had been putting that off due to the massive potential for things to go wrong.

The server isn't set up in a very complex way or anything, it's mostly a LAMP server with some other stuff like Samba and backup services. It has 4 hard drives, 3 running most of their space in a software RAID5 config with a small RAID1 partition for boot files (since GRUB won't boot from RAID5, or at least didn't when I set it up initially) and 1 drive as a hotspare. I assume the distro upgrade utility will leave my RAID settings alone?

---

### Post by arrrghhh on 2010-09-08
I don't run RAID... and it shouldn't.  It's never hosed up any of my conf files - just be sure if it asks you to replace a configuration file, choose to keep the original or at least have a good backup of the original...

---

### Post by y@w on 2010-09-09
I've had issues with the upgrader from past versions, but so far I'm 2 for 2 upgrading from 8.04 to 10.04.

---

### Post by slakkie on 2010-09-09
[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

---

