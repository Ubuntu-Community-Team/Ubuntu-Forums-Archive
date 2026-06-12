---
title: "Automated Reminders System/Script?"
date: 2009-05-17
forum: The Cafe
---

### Post by jowilkin on 2009-05-17
I have a weekly meeting with several participants.  Each week, one of the participants is designated the "moderator" and needs to do some extra work.

I need a system that sends the moderator an email roughly 4-5 days before the meeting to remind them they have extra work that week.  Then it should email all the participants 1 day before the meeting to remind them they should attend the meeting.

Does anyone know of a good system for doing this?  I have searched around and can't find anything that quite fits my needs.

I found this project on sourceforge: [http://sourceforge.net/projects/e-reminders/](http://sourceforge.net/projects/e-reminders/), but it is more designed for one person to email reminders to themself and lacks some of the features I need.  It has daily, monthly, and yearly repeat settings but not weekly for some reason, and does not have good support for mailing to multiple people.

I'm tempted to just write my own bash script to take care of it, but I feel like someone must have done this already.

---

### Post by spupy on 2009-05-18
> **jowilkin said:**
> I have a weekly meeting with several participants.  Each week, one of the participants is designated the "moderator" and needs to do some extra work.

I need a system that sends the moderator an email roughly 4-5 days before the meeting to remind them they have extra work that week.  Then it should email all the participants 1 day before the meeting to remind them they should attend the meeting.

Does anyone know of a good system for doing this?  I have searched around and can't find anything that quite fits my needs.

I found this project on sourceforge: [http://sourceforge.net/projects/e-reminders/](http://sourceforge.net/projects/e-reminders/), but it is more designed for one person to email reminders to themself and lacks some of the features I need.  It has daily, monthly, and yearly repeat settings but not weekly for some reason, and does not have good support for mailing to multiple people.

I'm tempted to just write my own bash script to take care of it, but I feel like someone must have done this already.

I think Google Calendar can do what you described. You can add several reminders to each event. A reminder can send emails.

---

### Post by toupeiro on 2009-05-18
cron?

---

### Post by jowilkin on 2009-05-25
Thanks for the replies.  I thought of using google calendar, but I don't trust google with my data and neither does my boss (and he's the one who counts).  I think it would also require me to get everyone to sign up for a google account and subscribe to the calendar which is undesirable (could be wrong about that, haven't checked too closely).

As for cron, yes if I make my own system it will obviously use cron, but I am hoping there is something out there already that's easy to use (maybe a web interface) and will be easy for someone else to take over when I leave who may not have good Linux skills.

---

