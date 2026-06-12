---
title: "Courier Problems"
date: 2006-04-19
forum: Server Platforms
---

### Post by davierik on 2006-04-19
Hi there!

I had some devastating problems with my server the other day, and had to do a complete reinstall. So I thought, why not try Ubuntu this time? :) 

So far it has been relatively painless, but now I'm facing a problem. I've setup my own IMAP server using courier, to which I fetch email from 2 POP3 accounts using fetchmail and procmail. The emails seems to be fetched at placed into ~/.maildir/new as they should be (right?). And using a client, I can connect to my server. The problem lies in my client not fetching any messages!

Checking the logs, I have ```
chdir Maildir: No such file or directory
```. I've interpreted this as that Courier has no idea where to look for my email, and so I have hunted down various config files, but to no avail! I have seen some earlier threads with this/similar problems, but all solutions seems to have been using mysql, while I run with pam.

/etc/courier/imapd contained the promising variable MAILDIRPATH, which was set to Maildir, so I figured that was the problem. But oh no, ```
MAILDIRPATH=~/.maildir
``` makes no difference, and the error message is still the same, so it doesn't seem to be the right place. :(

I have been without email for a week now due to my server's problems, and I am desperate! Please help me! :wink: ](*,)

---

### Post by nagilum on 2006-04-19
The default config defines "MAILDIRPATH=Maildir", maybe you just have to set  it to ".maildir" and not "~/.maildir".

---

### Post by davierik on 2006-04-19
I think it more likely that I am editing the wrong file, since otherwise, at least my new path should show up in the error message.

That said, I did try it out, and I also found a similar setting in imapd-ssl, which I also edited. That latter one is probably more likely to be the right one, since I'm using ssl, but unfortunately neither action seems to have fixed the problem. And yes, I did remember to restart the server. :) 

I don't really have any requirement to the name, thought ~/.maildir is what courier wanted on my old server. I can easily move it around, and change procmailrc accordingly, I just need to know to where? Because just renaming it Maildir didn't help any either. :???:

Oh, and on an additional note, when I chose in my client to select folders to subscribe to, the list is empty. But this fits with courier not being able to find the maildir folder.

---

### Post by nagilum on 2006-04-19
I just reactivated my old Courier imap server (changed about 2 months ago to Dovecot) and (I think) found what's wrong. Pretty simple actually, the MAILDIRPATH variable from /etc/courier/imapd is overwritten in the initscript with the value given in /etc/default/courier. So it doesn't matter what you specify in the config file (stupid design IMHO). If you change it in /etc/default/courier and restart your server it really points to the config-path (you might want to check this with a 'ps ax', the last argument is the MAILDIRPATH variable).
Somehow the 'restart' option to the server didn't work properly, had to issue a stop/start to get it accept the new dir, but that might have been bad luck. ;)

HTH

---

### Post by LordHunter317 on 2006-04-19
Why are you storing your mail in .maildir instead of ~/Maildir anyway?  That's teh default nearly every program expects.

---

### Post by davierik on 2006-04-19
.maildir was the default name on my old system, gentoo. Why, I have no idea.

I thought I had tried renaming to Maildir, but I must have made some mistake, because I tried it again now, and it worked!

That said, thanks a lot to nagilum as well for the help. But it's probably better to go with Maildir than to change the initscript, in case of updates etc. :)

---

### Post by nagilum on 2006-04-20
Glad it works.
Sticking to defaults often saves a lot of trouble, that's for sure. :)

---

