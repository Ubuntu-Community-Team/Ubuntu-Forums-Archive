---
title: "cron: for what do you use it ?"
date: 2008-07-09
forum: The Cafe
---

### Post by cosine352 on 2008-07-09
Hi Ubuntu friends,
I just want to know for what reasons do you use cron job ? I sometime use it to remind me of something for the day in work. 

What about you???????:)

---

### Post by Gamma746 on 2008-07-09
I used to use it to remind me about people's birthdays, anniversaries, etc. so I could send them emails.

Now cron sends the emails.  Efficient!

---

### Post by kaivalagi on 2008-07-09
> **Gamma746 said:**
> I used to use it to remind me about people's birthdays, anniversaries, etc. so I could send them emails.

Now cron sends the emails.  Efficient!

Great idea! :) I always forget birthdays...

Cron is a scheduling daemon used to run tasks at set times

```
man cron
```

---

### Post by ice60 on 2008-07-09
i use it to empty ~/.thumbnails/normal/ once a week of anything that hasn't been viewed in the last 7 days! 

i think the directory will keep getting bigger and bigger otherwise, but i'm not 100% sure! i'm using an old version of gnome/nautilus though, things could have changed with newer versions.

---

### Post by spupy on 2008-07-09
First, I recommend the program **gnome-schedule**. It is a very handy gtk front-end for both the **at** and the **cron** daemons.

All the time I have two scripts scheduled with cron:
1. Every day at 00:01 AM the DateIcon.sh runs. I have an icon on the desktop for a calendar app, and that script puts the current date on the icon. Looks like the iCal icon on the OS X dock, but with a Tango icon. :)
2. Every 10 minutes gmail.sh runs. It checks my two gmail accounts. If there is new mail, it puts the count of unread mails on the icon for the mail client. Again like the Mail.app icon on the OS X dock, with a Tango icon for Thunderbird.
(I'm so ******* proud of this script XD)

---

### Post by weresheep on 2008-07-09
I have four scripts in my crontab. The first is my 'todo' script which simply parses ~/docs/personal/todo.txt and formats it according to category. Running this script via cron results in cron emailing me the output so every morning I have a reminder of my todo's.

Next isn't a script but simply a call to /usr/bin/remind. I have ~/.reminders set up to load various reminder files for birthdays, appointments, work stuff etc. and I use cron to get a daily email of whats due that day.

Both 'todo' and 'remind' can and are run directly from the shell but its nice having their output sitting in my inbox each monring (I sometimes forget to run the programs :) )

I have a 'gitbk' script which backs up my git repository. This is fairly simple at the moment and I have some plans for improving it but it does the basic job.

Finally I have 'clrma' (CLeaR Mail Archive) which runs once a week and clears my mail archive (procmail copies every incoming mail to an archive directory) of mail older than 3 months, but makes sure theres at least a thousand sitting around.

-weresheep

---

### Post by Mateo on 2008-07-09
I don't use cron that often but I do use **at** all the time.  I use it to record stuff with my tv tuner.

---

### Post by beercz on 2008-07-09
I use it to automate my backups :-)

Effortless!

---

### Post by init1 on 2008-07-09
I don't use cron, but this thread is inspiring me to do so :D

---

### Post by 50words on 2008-07-09
Backup. I set up a cron job for every weekday for my office workstation/file server to back up my business files every day with rsync. I am never more than 24 hours out from my latest backup, and I have four more, just in case.

---

### Post by dracule on 2008-07-09
damn, i am looking in to this :)

---

### Post by toupeiro on 2008-07-10
PostGres database maintenance, backups, collecting log files, syncing sudoers files across 100 or so systems from a master sourcefile.  What *can't* you use cron for?

---

### Post by regomodo on 2008-07-10
`

---

### Post by Hells_Dark on 2008-07-10
Up, could be interesting.

I use it in order to do sql backups.

---

### Post by mali2297 on 2008-07-10
Every minute, it runs a script to check the battery status. (I prefer to not use the acpi or apm daemons.) If it gets below a certain level, it sends a beep. If it gets even lower, the computer hibernates.

---

### Post by spupy on 2008-07-10
> **mali2297 said:**
> Every minute, it runs a script to check the battery status. (I prefer to not use the acpi or apm daemons.) If it gets below a certain level, it sends a beep. If it gets even lower, the computer hibernates.

Sounds handy, could you post the script somewhere?

---

### Post by mali2297 on 2008-07-10
> **spupy said:**
> Sounds handy, could you post the script somewhere?

Here you go:
```

#!/bin/sh

bat_tot=$(awk '/last full capacity/{print $4}' < /proc/acpi/battery/BAT0/info)
bat_free=$(awk '/remaining capacity/{print $3}' < /proc/acpi/battery/BAT0/state)
pbat=$(( 100 * $bat_free / $bat_tot ))

if [ $pbat -lt 9 ]; then
        echo -e '\a' > /dev/tty0
        if [ $pbat -lt 3 ]; then
                echo disk > /sys/power/state
        fi
fi

```

Note: 
Check first that you can hibernate the computer with
```

sudo -i
echo disk > /sys/power/state

```

---

### Post by jwkolberg on 2008-07-10
I use it to rsync all my pictures and documents onto my fileserver. Saved my *** many, many times. :)

---

### Post by cosine352 on 2008-07-10
> every Minute, It Runs A Script To Check The Battery Status. (i Prefer To Not Use The Acpi Or Apm Daemons.) If It Gets Below A Certain Level, It Sends A Beep. If It Gets Even Lower, The Computer Hibernates.

great \\:D/

---

### Post by toupeiro on 2008-07-10
> **mali2297 said:**
> Here you go:
```

#!/bin/sh

bat_tot=$(awk '/last full capacity/{print $4}' < /proc/acpi/battery/BAT0/info)
bat_free=$(awk '/remaining capacity/{print $3}' < /proc/acpi/battery/BAT0/state)
pbat=$(( 100 * $bat_free / $bat_tot ))

if [ $pbat -lt 9 ]; then
        echo -e '\a' > /dev/tty0
        if [ $pbat -lt 3 ]; then
                echo disk > /sys/power/state
        fi
fi

```

Note: 
Check first that you can hibernate the computer with
```

sudo -i
echo disk > /sys/power/state

```

Thats a brilliant little piece of code!  Thank you for sharing!

---

### Post by Traumadog on 2008-07-12
Nothing really creative......   I'm using cron jobs to rsync backup my server.  Not really exciting, but I sleep better at night knowing I have a daily backup if I need it! :)

---

### Post by ghindo on 2008-07-12
I had no idea these things were even *possible* :)

I should start looking into this "cron" thing.

---

### Post by akiratheoni on 2008-07-12
I use it on my webserver to backup my forum's database.

---

### Post by macogw on 2008-07-12
Cron installs updates on my mom's computer because I know she won't do it herself.

---

### Post by Lord DarkPat on 2008-07-12
> **spupy said:**
> First, I recommend the program **gnome-schedule**. It is a very handy gtk front-end for both the **at** and the **cron** daemons.

All the time I have two scripts scheduled with cron:
1. Every day at 00:01 AM the DateIcon.sh runs. I have an icon on the desktop for a calendar app, and that script puts the current date on the icon. Looks like the iCal icon on the OS X dock, but with a Tango icon. :)
2. Every 10 minutes gmail.sh runs. It checks my two gmail accounts. If there is new mail, it puts the count of unread mails on the icon for the mail client. Again like the Mail.app icon on the OS X dock, with a Tango icon for Thunderbird.
(I'm so ******* proud of this script XD)
Good joB! I dunno how you did it, but seems pretty easy to me!
```

#! /bin/sh
cp ~/Desktop/dates.ico ~/Desktop/`date +%d-%m-%y`.ico

cp ~/Desktop/time.ico ~/Desktop/`time %e %B %G`.ico
```
share the gmail script if you don't mind

---

### Post by K.Mandla on 2008-07-12
> **cosine352 said:**
> I just want to know for what reasons do you use cron job ?
I don't use it. I uninstall it.

---

### Post by Polygon on 2008-07-12
> **K.Mandla said:**
> I don't use it. I uninstall it.

is that wise? i always thought cron was something pretty important, and some programs might depend on it...similiar to removing something like wget...

---

### Post by Mateo on 2008-07-13
> **toupeiro said:**
> PostGres database maintenance, backups, collecting log files, syncing sudoers files across 100 or so systems from a master sourcefile.  What *can't* you use cron for?

It's hard to use cron on your home desktop PC unless you leave it on all the time.  That's the main reason why I don't use it.

---

