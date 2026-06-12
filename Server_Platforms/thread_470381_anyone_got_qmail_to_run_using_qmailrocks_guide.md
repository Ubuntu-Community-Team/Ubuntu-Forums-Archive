---
title: "anyone got qmail to run using qmailrocks guide?"
date: 2007-06-10
forum: Server Platforms
---

### Post by ziggie216 on 2007-06-10
did you follow the guide exactly or was there any change that was needed? i'm having the hardest time here getting daemontools and ucspi-tcp to setup properly w/o seeing any warring mesage

---

### Post by hawzor on 2007-06-11
This is an uber-outstanding question. Qmail has only rocked in the past for me. Recent attempt to go Postfix has resulted in some success, but low confidence.

I can warn that** apt-get install postfix courier ** (etc., etc.) is no walk in the park either.

---

### Post by itwillbreak on 2007-06-19
I have been struggling through the Qmailrocks installation guide for Debian for over a week now.  I am now completely stuck on Part 12 - Installing Courier IMAP & IMAP SSL.  The qmail forums offer solutions to most of the problems but some still don't work.  I've kept a log of things I have tried that were recommended in the forum.  Believe it or not I have to setup a second qmail server and I'm going to have to struggle through the installation all over again.....arg....:(

I don't know if this would help but looking over my notes, I had this:

After you have untarred the daemontools file, go to the: admin/package/src directory and find the file: "conf-cc" - edit this and add the following to the parameter line for gcc: -include /usr/include/errno.h

Save it and run the commands as told to in the daemontools installation instructions. It should then work.

This was from the qmail forum somewhere.  Have you tried the qmailrocks forum?

---

### Post by MarilenCorciovei on 2007-12-27
This[ describes my experience]("http://www.len.ro/work/tools/gutsy-on-a-ubuntu-server/qmail/view") with qmail using the qmailrocks guide on gutsy

---

