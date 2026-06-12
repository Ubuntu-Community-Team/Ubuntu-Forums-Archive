---
title: "No calDAV-compatible calendar for the tablet?"
date: 2016-04-26
forum: Ubuntu Phone and Tablet
---

### Post by Johan_Helsingius on 2016-04-26
Subject says it all, I guess...

---

### Post by KFoder on 2016-04-28
I have succeed in setting syncevolution up to sync with my owncloud on my M10, using a script found [here]("https://askubuntu.com/questions/616081/ubuntu-touch-add-contact-list-and-calendars/664834#664834").

It wasn't exactly easy (it seems to me as if the cloud calendar name and the calendar name in the script has been swapped), but after a lot of experimentation (and 3 full resets of the tables, probably because of missing knowledge of syncevolution) I finally had my tablet syncing, and integrating smoothly with the build in calendar and contacts.

I'm only missing the birthdays from the owncloud contacts to be synced with the corresponding calendar in the tablet.[URL="http://answers.microsoft.com/en-us/insider/forum/insider_wintp-insider_desktop/start-menu-doesnt-open-in-windows-10-tech-preview/3edf2294-7b5c-4b48-88ea-9bed66f0538b?auth=1"]
[/URL]
A more technical solution can be found [here]("http://askubuntu.com/questions/606020/how-to-sync-contacts-and-the-calendar-on-ubuntu-touch-with-owncloud").

I'm no syncevolution expert, but by now I have learned a lot, so feel free to ask if you believe I can help.

/Kim

---

### Post by Johan_Helsingius on 2016-04-28
Thanks, but we have the usual problem of /etc/apt being on a read-only file system. Will have to wait until I have enough time to deal with things going wonky as a result of remounting it rw....

---

### Post by KFoder on 2016-04-28
No, if you just use the script, no apt-get is necessary!

I did it directly on the device.

Just download the script: [Download ubuntu-touch_owncloud-sync_contact-calendar.sh]("https://gist.githubusercontent.com/boTux/069b53d8e06bdb9b9c97/raw/a03be09136c5275b2956c512accdad69b30e8074/ubuntu-touch_owncloud-sync_contact-calendar.sh"), edit it (I used nano from the Terminal app), allow execution with chmod +x ..., and execute script as user.

/Kim

---

### Post by Johan_Helsingius on 2016-04-28
Ah, so you don't actually need phablet-shell.

---

### Post by KFoder on 2016-04-28
No, it's a bit more cumbersome on the tablet (using the on screen keyboard as I did), but it is doable.

---

### Post by Johan_Helsingius on 2016-04-28
Thanks!

---

