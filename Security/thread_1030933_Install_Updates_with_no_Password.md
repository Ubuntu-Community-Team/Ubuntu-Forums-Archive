---
title: "Install Updates with no Password"
date: 2009-01-04
forum: Security
---

### Post by joseph1975 on 2009-01-04
I am using Ubuntu 8.10.  Is there a way for Ubuntu to automatically install security and recommended updates without having to type in the root password.  What I'm looking for is a way the computer will check for updates once a day (I've already figured that part out), but will install the updates, rather then just tell me they exist.

Thanks for your help,
Mark

---

### Post by pytheas22 on 2009-01-04
You could write a cronjob for root to run the command:
```

sudo apt-get upgrade
```

I'm pretty sure this would work; I know it works on Ubuntu 6.06 because I used to use it to keep a server updated without manual intervention.

You could probably pass more options to apt-get to tell it to install only important upgrades, if you don't want it to install everything.

If you don't know how to write a cronjob I can give instructions, but it should also be easy enough to figure out with some quick googling.  Make sure you add the cronjob to root's crontab or it won't work.

---

### Post by Dave_Connor on 2009-01-04
You can edit /etc/crontab and enter the command and what user (root in this case) you want the command and when to run the command.

---

### Post by bodhi.zazen on 2009-01-05
> **pytheas22 said:**
> You could write a cronjob for root to run the command:
```

sudo apt-get upgrade
```I'm pretty sure this would work; I know it works on Ubuntu 6.06 because I used to use it to keep a server updated without manual intervention.

You could probably pass more options to apt-get to tell it to install only important upgrades, if you don't want it to install everything.

If you don't know how to write a cronjob I can give instructions, but it should also be easy enough to figure out with some quick googling.  Make sure you add the cronjob to root's crontab or it won't work.

If you are running a cron task as root, sudo is not needed.

IMO you should :

apt-get update && apt-get dist-upgrade

use the full path in cron jobs ...

You can also configure Synaptic ..

Go into the Repositories tab -> Updates 

Under automatic updates check off "Install security updates without confirmation"

IMO you should review non-security updates before you update.

---

### Post by joseph1975 on 2009-01-05
Thank you everyone for your replies.  They were very helpful.

---

