---
title: "automatic updates hourly"
date: 2010-03-05
forum: Security
---

### Post by stardustdk on 2010-03-05
Hey all.

I am wanting to update hourly and therefore i found this:

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)


On that page i found a cron job file that looked right:
> 
#!/bin/bash
apt-get update
apt-get upgrade -y
apt-get autoclean

I put in cron.hourly and made it executable.

It did not work as supposed.. :?:

Do you have any ideas what to do?


Best regards

---

### Post by byStanderone on 2010-03-05
...am not sure about the hourly update if the system allows it or not, but by default ubuntu listens for updates whenever it is connected on the web, ...besides there's no need for an hourly update, a daily check is more like it.

---

### Post by stardustdk on 2010-03-05
And how do i make that daily update, so i am sure it's running? Ie the cron job.

Best regards

Stardustdk

---

### Post by ajgreeny on 2010-03-05
Go to the *Updates* tab of *System ->Administration ->Software sources* and set your update frequency there.  By default it is set to Daily, I think, so there should be nothing to do at all.

---

