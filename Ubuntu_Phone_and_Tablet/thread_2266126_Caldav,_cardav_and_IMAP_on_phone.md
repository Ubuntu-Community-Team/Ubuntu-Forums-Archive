---
title: "Caldav, cardav and IMAP on phone"
date: 2015-02-20
forum: Ubuntu Phone and Tablet
---

### Post by danceswithcats on 2015-02-20
This sounds like a silly question, but I can't find an answer anywhere. Can I use these settings on Ubuntu phone, without being a hacker? 

Also, anyone got any idea about Owncloud integration? 

I've got a bq phone on the way, due to arrive *sometime in March*, but I' m getting uneasy about it. All the comments are about how great it is or how it'll never succeed. I don't want anything turbo charged: I just want a phone I can run without a Google account.

---

### Post by danceswithcats on 2015-02-20
Thanks to Ricardo at [http://rpadovani.com/about/](http://rpadovani.com/about/), I can answer my own question: Caldav is a low priority bug on the calendar app, but not currently available. The calendar team are working really hard and have a long list of bug reports to deal with, (and the calendar looks really cool on the screenshots) so I don't want to moan, but this seems to me to be a fairly important function. The bug report is [here]("https://bugs.launchpad.net/ubuntu-calendar-app/+bug/1199774"), by the way.

IMAP is available on an app called [Dekko]("https://appstore.bhdouglass.com/app/dekko.dekkoproject") that looks really beautiful and uses IMAP. WooHoo!

Ricardo doesn't think Owncloud is happening at the moment. I will bother them on the Owncloud forums about that and link to it, in case anyone shares my interest and would like to join in.

I am really looking forward to receiving my phone.

---

### Post by grahammechanical on 2015-02-20
The other day someone asked a similar question on Discourse Ubuntu and they followed by suggestion

[http://discourse.ubuntu.com/t/what-is-the-status-of-carddav-caldav-on-ubuntu-touch/2068](http://discourse.ubuntu.com/t/what-is-the-status-of-carddav-caldav-on-ubuntu-touch/2068)

At some point during this Ubuntu On Air session their question is answered. These Ubuntu On Air Q & A sessions are a good place to ask questions of people directly involved in the development of Ubuntu

[https://www.youtube.com/watch?v=u-Jai3K9MVA](https://www.youtube.com/watch?v=u-Jai3K9MVA)

My reading of Ubuntu phone and tablet software development is that everything is under continued development and Canonical is not monopolizing the development of applications. The hardware on a Ubuntu phone that we purchase today may become outdated over time but the software will be up to date. We will not need to buy a new Ubuntu phone to get the latest Ubuntu phone OS.

BY the way, I have heard that a lot of the negative comments are being made by people who do not have a BQ Ubuntu phone to review.

[http://rpadovani.com/ubuntu-phone-hardware/](http://rpadovani.com/ubuntu-phone-hardware/)

Regards.

---

### Post by danceswithcats on 2015-02-27
Thanks for this Graham.  I'll look out for another Q&A. I'd seen the post from Riccardo. I take it for granted that a lot of rubbish will be posted about anything new.  I said as much on this discourse post.

[http://discourse.ubuntu.com/t/why-are-you-excited-about-ubuntu-touch/1912/2?u=peter_mason77](http://discourse.ubuntu.com/t/why-are-you-excited-about-ubuntu-touch/1912/2?u=peter_mason77)

I'm just anxious about the phone, because my wife will not be impressed if I've spent the better part of 200 quid on a phone I can't use as my main phone. She is a good person who uses Ubuntu and understands my enthusiasm, but £200 is £200 and I'm a part time community tutor who doesn't work in an office and relies upon a calendar synched to his phone. A wait is as good as a lack, in that regard. I'll be lugging round the Android phone and have the Ubuntu phone just to write blog posts about.

I did look at making a scope for my Owncloud calendar, but I'm afraid it's beyond me. I don't suppose you know anyone who'd be interested in guiding/educating/doing it for me? :rolleyes:

Now, if Twitter wasn't ready for it yet, that would not be a problem. I'd be a picture of patience.

Never mind, it's spent now.

---

### Post by Martin_Schwetz on 2015-05-01
CALENDAR BACKUP UBUNTU PHONE

Maybe this is relevant for some of you: 

With Ubuntu Phone (I use Aquaris E4.5 Ubuntu Edition) there seems to be an easy way to backup the CALENDAR without using bluetooth sync or google etc. by simply copying the iCalendar file which is stored on the phone.

With my Ubuntu Phone it worked like this:

1. In the filemanager („Dateiverwaltung“) select hidden files („versteckte Dateien anzeigen“)  and full access (? auf Deutsch: "für vollen Zugriff freischalten"). The "filemanager" is available at the Ubuntu Store.

2. Go to  /home/phablet/.local/share/evolution/evolution/calendar/system/calendar.ics
("home" wird in Deutsch auch angezeigt als "Persönlicher Ordner").

3. Copy the file „calendar.ics“ to the  SD-card of the phone or somewhere else from where you can copy the file to your PC.

4. Copy „calendar.ics“ from the phone to the PC 

5. Be sure that you have already installed „Evolution“ on your PC.

6. In „Evolution“, import the file „calendar.ics“ as a new calendar. That means:
Choose „New – calendar“. Then select „use iCalendar-File (*.ics)“ (Deutsch: „eine vorhandene iCalendar-Datei (*.ics)“ verwenden) in the following window. Select your just copied file „calendar.ics“ and press „ok“. Now your calendar should appear in „Evolution“.

But of course you can also just save the file „calendar.ics“ on your PC as a backup, without importing it into „Evolution“.

Finally, the other way round of course it should be possible to copy an ics-calendar file from the PC to the phone by just copying the calendar file to the directory /home/phablet/.local/share/evolution/evolution/calendar/system/ 
of the phone.

---

