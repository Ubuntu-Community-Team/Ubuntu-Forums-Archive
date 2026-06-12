---
title: "Failed 12.04 -&gt; 14.04 upgrade. What now?"
date: 2014-08-22
forum: Server Platforms
---

### Post by Klamann on 2014-08-22
Hi there,
  
this morning I had a perfectly fine 12.04 server, but then, out of some kind of mental derangement, I decided to enter 'do-release-upgrade' as proposed by the greeting message in my terminal window (maybe I thought i was running 14.04 and the upgrade to 14.04.1 wouldn't hurt, maybe my brain was still booting, I don't know...). Now, a few hours later, after resolving all the dependency issues that occured, what remains is a totally broken apache server, a broken mail server and lots of other stuff that doesn't work any more...

Of course, the last backup is already a few months old, so right now I'm kinda desparate. I don't want to spend the entire weekend a) fixing all the stuff that's broken or b) replaying a backup and merging the current changes into it. I'm really not sure how to go on from here, but maybe there's a third option I didn't think of, so if you know a way for me to resolve this mess, please let me know!

best regards

---

### Post by Hugo_Serrano on 2014-08-22
Hello!

Well... there some ways to go. But first I would say to do a backup from what you have... eventually you will need to re-install and restore.

Than, let's find out why things are not running. 
What errors do you have when you try to start your services?

Cheers,
Hugo.

---

### Post by Klamann on 2014-08-22
I don't even know where to start... Apache 2.4 is starting now, though I still have to rewrite my entire config from 2.2, but the php.ini seems to be broken, as I can't access any PHP-extensions (mcrypt, mysql, etc.). The mail server was a custom setup (postfix, dovecot), and here also the configuration seems to be broken. Honestly, I don't feel like I'm up to the task of fixing all that's broken.

Right now, I'm backing up the system and preparing to revert to the last backup (9 months old, but there were no major changes in the setup since then).
I was just wondering if there is this magic "damn the upgrade failed, would you like to revert everything?"-button or something like that ;)

---

### Post by Hugo_Serrano on 2014-08-23
Hi.

Don't think there's any magic button :-(
You may backup everything, and do a fresh install of 12.04 and restore configs and data. It may work.

Cheers,
Hugo.

---

