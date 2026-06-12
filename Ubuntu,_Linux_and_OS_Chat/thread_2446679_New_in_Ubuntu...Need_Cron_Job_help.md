---
title: "New in Ubuntu...Need Cron Job help"
date: 2020-07-04
forum: Ubuntu, Linux and OS Chat
---

### Post by ymurawski on 2020-07-04
Hi, 

i totally new to Linux and i need help for a Cron Job.
Under windows i had a script that printed a testpage every second Monday at 10AM.

I now want to switch to Linux/Ubuntu but i have no idea how to set up something like that. I searched a lot but i dont understand what some people wrote.
The Script what i found is:

#!/bin/bash
# Drucke Testseite auf dem Standarddrucker - Anzahl der Ausdrucke: -# 1
lpr -# 1 '/home/administrator/Downloads/testbild.pdf'

Can anybody help :(

I'm using Ubuntu 20

---

### Post by mastablasta on 2020-07-04
here is the official guide: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

digital ocean tutorial (they are easy to understand, so i use them often): [https://www.digitalocean.com/community/tutorials/how-to-use-cron-to-automate-tasks-ubuntu-1804](https://www.digitalocean.com/community/tutorials/how-to-use-cron-to-automate-tasks-ubuntu-1804)

if you need a GUI there is Corntab (the online crontab generator: [http://corntab.com/](http://corntab.com/) )
or you can install GUI: [https://www.ghacks.net/2011/03/09/schedule-cron-jobs-with-this-easy-to-use-gui/](https://www.ghacks.net/2011/03/09/schedule-cron-jobs-with-this-easy-to-use-gui/)

you already have the script you want to run, now you just need to edit crontab to make it run anyway you would like it to run.

crontab works the same for a while now so it doesn't really matter if you have 20.04 of 18.04. process of setting it up should be more or less the same.

---

### Post by QIII on 2020-07-04
I'm going to +1 the Digital Ocean stuff.  Very easy to understand and most of them give you some information as to why you are doing what you are doing.

Bear in mind that their tutorials are usually good to get you up and running with *basic settings*.  From there, you should go to the other resources.  The beauty of using Digital Ocean's tutorials first is that when you get to the more advanced tutorials, you sort of have an idea what is going on.

---

