---
title: "I had a thought ... Thunderbird and Dropbox"
date: 2015-05-20
forum: The Cafe
---

### Post by mbott on 2015-05-20
... and this is where I usually get myself in trouble. But here it is.

I have two Ubuntu installations.  My desktop consists of 14.04.2 LTS and it is my primary system simply because it is more advanced than my laptop.  It is also where my e-mail resides.  I use Thunderbird to gather e-mail from 5 different accounts spread across three different commercial services. 

I also have a laptop running 15.04.  I use it primarily when we travel and when I don't feel like going down use the desktop.  But I don't have easy access to e-mail other than the web-based portals of the services I use.  The thought I had was moving the .thunderbird directory to my Dropbox account and pointing my installs to it there.  I'll probably give this a try but I thought I'd ask if anyone attempted anything similar and could provide any "heads-up" that I should be aware of.

Thanks!

-- 
Mike

---

### Post by Dragonbite on 2015-05-20
Don't know if it will work, but sounds like an interesting idea (and may try to implement something similar to that for my wife's computer).

Keep us updated, if you try it out.

---

### Post by Copper Bezel on 2015-05-21
I've tried similar things to mixed success. One thing to watch out for is that not everything is dumped into the dotfolder at the same time. Some settings are only saved on exit, etc. When I wanted to do something similar with Tomboy, I ended up using its built-in syncing feature to synchronize both machines to a Dropbox location instead, because sharing the database itself over Dropbox led to conflicts and meant things weren't getting reloaded into the running app when they were supposed to.

---

### Post by Dragonbite on 2015-05-21
For myself, I use IMAP (Gmail and Outlook.com) so that most things are synchronized.

---

### Post by kurt18947 on 2015-05-21
> **Dragonbite said:**
> For myself, I use IMAP (Gmail and Outlook.com) so that most things are synchronized.
I do the same but I think I'm doing similar with pop3 accounts by changing the account settings in T'bird to leave messages on the server until I delete them rather than the default delete on the mail server after downloading. I suppose I could overflow my pop3 mailbox but so far it hasn't been an issue.

---

### Post by oldfred on 2015-05-21
I just rsync the entire Thunderbird & Firefox profiles to my laptop when travelling and back when i return.

That has worked for me since about 2007 when laptop was even still XP. Files until recently were in a NTFS shared data partition for that reason.

But recently with new system I moved profiles back from the shared NTFS partition to /home defaults and either my script to vacuum all sqlite files, ownership or permissions since back to ext4, or something in copy is causing me to lose some emails.

---

