---
title: "mail archiving/logging solution ?"
date: 2008-07-20
forum: Server Platforms
---

### Post by sanalkisi on 2008-07-20
Hi,

We have plenty of corporate mail addressess which we need to keep logs/archives of the arriving messages. We also need the ability to search and report of those messages.

Is there any open source solution ?

regards.

---

### Post by Aessa on 2008-07-21
This is not quite what you are looking for, but I have set up our mail server (about 8 users, so quite small) to forward all incoming and outgoing mail per user to a userbu (user's backup) account. This account is then gzip-backuped to another server and the last 100 days kept on the mail server. This setup works well with Maildir and Postfix (Postfix has an option to BCC From/To messages).

As for searching, I am waiting for that problem to arise before I solve it. I suppose you can get quite far with simple perl/ruby scripts or the like, but I think as soon as you get more than 20 users, this setup will start to break down.

So, in short, I'm also on the lookout for good mail backup/indexing solutions.

---

### Post by sanalkisi on 2008-07-21
Hi,

With 5000+ users and plenty of middle/high level administrators expecting a web based selfservice search/report system, I hope I can find a solution.

---

### Post by xbzus on 2009-02-23
Can you please tell me how to do this in webmin?

> **Aessa said:**
> This is not quite what you are looking for, but I have set up our mail server (about 8 users, so quite small) to forward all incoming and outgoing mail per user to a userbu (user's backup) account. This account is then gzip-backuped to another server and the last 100 days kept on the mail server. This setup works well with Maildir and Postfix (Postfix has an option to BCC From/To messages).

As for searching, I am waiting for that problem to arise before I solve it. I suppose you can get quite far with simple perl/ruby scripts or the like, but I think as soon as you get more than 20 users, this setup will start to break down.

So, in short, I'm also on the lookout for good mail backup/indexing solutions.

---

### Post by Aessa on 2009-02-23
In the latest webmin, when using Postfix, go to BCC Mapping.

Set the Sender and Recipient map fields something like this:
hash:/etc/postfix/sender_bcc
hash:/etc/postfix/recipient_bcc

And then edit the maps or use the webmin add boxes. Note that the Sender maps are the one open when you enter this page. You need to go to the Recipient maps tab to set up basically the same map. I suppose you can rather point both maps to the same file at the top of the page.

The map entries I used are full email addresses mapping to the full address of the backup user. Note that you can use any mail address then, so archiving to an off-site huge space is easy, only bandwidth hungry.


It's been a while since I last did this, but I think this is mostly all you need. Note that setting up the backup user is tedious and its password needs to be just as secure as the normal user - you could make them the same I suppose, but I like to use random 40 digit passwords everywhere - quite a mission with setups but worth it in many ways...



Oh as for the automated backups, this is messy. I used a Ruby script on the mail server to actually log in to the backup mail account - letting Dovecot worry about file/mailbox locks and the like. This works fine - runs long the first time, but thereafter only a minute or three for all the accounts which totals to about 10000 emails. With my recent enlightment of python, I'd suggest you rather use that for this task - I used Ruby because the Perl POP3 client broke too often and I didn't yet know much about python.

For what it's worth, I extract the first "Date: " line from each mail and use that for file naming, but spam and actually a few legitimate companies/users send out email with bad format or nonsensical timestamps. I just dump these in an Invalid folder with the filename based on the current date and time the backup took place. I also then delete it immediately from the backup acocunt so that you don't see it every day for the next 100 days. But, how and why this happens is up to you.

---

### Post by HermanAB on 2009-02-23
Hmm, alternatively, you can use a proper mail server that can handle truly mind bogglingly huge amounts of mail and then you don't have to worry about it - just keep everything forever.  Citadel can store 256 terabytes of mail in its BerkeleyDB back end.

Cheers,

Herman

---

