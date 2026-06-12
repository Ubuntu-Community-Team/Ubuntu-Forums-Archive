---
title: "Simple mail server?"
date: 2006-06-08
forum: Server Platforms
---

### Post by Ixzat on 2006-06-08
Hi there.

I have been trying for a while now to get a small email server working. I used to run gentoo on my machine, and i thought that it would take some time of my hands swithcing distro to something more managable.However,  trying to get a mail service running on ubuntu dont seem to be easy enough for me... I had one running under gentoo fine.

What i want is the following:
[LIST]
[*]Imap Access
[*]Pop Access
[*]Smtp Access
[*]Webmail Access
[/LIST]

Nothing fancy about that, i just want to run a mail server on my home machine, no need for exta major security and such. 
I have been trying to follow nearly all guides i can find on the wiki and from links here on the forum but for some strange reason it just wont work.

Is there any other mail servers out there besides postfix and qmail that could suite me well?

---

### Post by Randomskk on 2006-06-08
Postfix is just an SMTP server; you can't use POP3 or IMAP on it but it works great for sending/recieving mail.
Dovecot is fairly good for a small IMAP/POP3 server, see the Ubuntu Server Guide (sticky in this part of the forums) in the mail section as it tells you how to set it up.
Web mail is simple, just apt-get install squirrelmail and symlink it to your web directory (it's in /usr/share/squirrelmail or something).

---

### Post by homegrown on 2006-06-14
Give Hula a try -- it might be overkill for what you're looking for, but i think it's great!

---

### Post by MJN on 2006-06-14
Like many others I went with the combo randomskk suggests.

If I've learnt anything in setting it up it's that you shouldn't try and do everything at once. Start with just getting Postfix working accepting mail for local users, then progress on to making it send mail remotely. There'll be plenty of example config files from others (heck, I've just commented mine so that might be of some use). Then move on to POP/IMAP access (the default config file will work out of the box on this one I seem to recall) and then finally Squirrelmail (nice Perl-based config tool to help you there).

It sounds a lot, and indeed you'll be scratching your head at a number of stages, however many many people have walked the path before you so if you break the whole thing down into stages as above and report problems as you find them there'll be someone out there that can help. It's when you're trying to do the whole lot at once that it can be a nightmare for you and/or anyone else to help pinpoint and solve whatever problem you're having.

Mathew

---

