---
title: "updates, do-release-upgrade"
date: 2015-01-23
forum: Server Platforms
---

### Post by spyros6 on 2015-01-23
Yesterday i received credentials for an ubuntu server system that had a website running, the goal was to add a second one (virtualhost). After setting up everything correctly, i had time to check out the system in general. To my surprise the VPS runs ubuntu server 12.04 , never updated. So it's exploitable to shellshock , and who knows whatever else. So my simple question is this : Can i simple "do-release-upgrade" or will i lose everything i configured ? Can i safely restart the machine ? I don't know how i check which services startup with it, im afraid ssh,apache,mysql wont launch with the restart. Any way to copy everything to an image and boot it up on my local machine with virtualhost or qemu? Also if i can configure it to automatically update every x days that will be great :) edit : do-release-upgrade notifies me it will update to 12.04.1, however i see the latest one is 12.04.5. Can i upgrade to this directly or do i have to go up one version at a time ?

---

### Post by TheFu on 2015-01-23
**do-release-upgrade** till take 12.04 to 14.04.xx.  This isn't a good idea without testing, backups, planning first. Be careful. Besides, you need to be fully patched before running that.
[B]
sudo apt-get update
sudo apt-get dist-upgrade [/B]
will take you to the latest 12.04.xx ... which has support until 2017 (assuming server install).  I run this weekly and haven't had any terrible surprises, however, after waiting so long, I'd be cautious, have good backups and be prepared if things don't restart.  Have a plan so if things don't work out, you can recover in the allowed time.

To virtualize or not is not an easy question, though I run everything in a virtual machine.

Seem you may not be running the version you think you are.  do-release-upgrade goes from lts to lts to lts ... so
10.04 to 12.04 to 14.04.  It doesn't do intermediate releases or 3rd level point releases - at least not on an Ubuntu server.  Perhaps debian works differently?

---

### Post by spyros6 on 2015-01-23
The message says do-release-upgrade goes to 14.04.1 LTS. I didn't read it correctly i thought it was saying 12.04.1. So i will probably break the whole server ? Good. I will start backing up stuff

---

### Post by TheFu on 2015-01-23
> **spyros6 said:**
> The message says do-release-upgrade goes to 14.04.1 LTS. I didn't read it correctly i thought it was saying 12.04.1. So i will probably break the whole server ? Good. I will start backing up stuff

Whoa!!!!!!


Who said nothing would break?  Not me.

There is a major apache release change.
There is a major samba release change.

Do your planning. Practice.  See what works and what doesn't.

Nobody can say whether your 1-off system will work tomorrow, much less after an OS upgrade.

Sorry - but you have to do the homework, testing yourself.  Might be smart to look for apache migration documents, huh?

---

### Post by Bucky Ball on 2015-01-23
Just wondering why you think this machine to be so vulnerable. 12.04 LTS is supported for five years, until April 2017.

Doing:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... should get you to 12.04.5

---

### Post by MAFoElffen on 2015-01-24
If it was never updated (the OP mentioned), then yes, it would have missed the security update for bash, which fixed the shellshock vulnerability... But (as Fu suggested) if he just does an in-version update/upgrade (via dist-upgrade, which is safer) then he keeps the same version LTS (which is supported) and gets up-to-date on his security updates.

+1 w/ Fu and Bucky. Get up-to-date w/ the normal updates. Then.. Always have a fallback plan for a release upgrade. Things rushed into, don't always turn out as planned.

---

