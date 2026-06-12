---
title: "Using external smtp server with apache and drupal"
date: 2009-02-17
forum: Server Platforms
---

### Post by bfr-dwn on 2009-02-17
Hi!

I'm pretty sure this has been answered, but could not find anything.. 
I have apache installed on 8.10, and i'm trying to get the mail function to work with drupal(so it can send mail to registered user). 

However, i don't know how to set this up. We have another mail server already up that requires no authentication, so i dont want to install mail server to this machine. 
In the php.ini i can find lines for smtp server and port, but it says "win32 only".

For unix there is "sendmail path" but i dont know how to use this. 
If this is the correct line, could i have example what to put there if the mailserver is at mail.example.com and port is 25.

Thanks in advance.

---

### Post by songshu on 2009-02-17
you need another mailserver.

i personaly use postfix, it can be used by the sendmail path so don't need to change that.

you can have postfix to simply send everything to your normal mail server for further distribution.

---

### Post by bfr-dwn on 2009-02-17
Are you sure? Sounds a bit overkill to me.. i mean, i can send mail from any mail client without having my own mail server, but apache can't?

---

### Post by songshu on 2009-02-17
understand what you mean but its not that bad.

if apache would have a build in mail client that would be overkill ;)

i guess drupal could have it done via php but not sure if it has that functionality,
mailx would work and its a lot smaller, but again not sure if drupal can handle that.

postfix is not that heavy so its not that much of an overkill i guess.

maybe somebody else has a better idea and more experience with drupal, but thats how i would do it

---

### Post by bfr-dwn on 2009-02-17
I think it actually does it via php, that is why i'm configuring php.ini, right? Does this change the situation?

---

### Post by AndyMcCall on 2009-02-17
You need to install a Mail Transport Agent (MTA), like Sendmail, then tell sendmail to route all mail to your existing SMTP host.

This [post]("http://ubuntuforums.org/showthread.php?t=196112") shows what I would do to install Sendmail and set PHP to work with it.

I don't know where the sendmail.cf file is on Ubuntu off of the top of my head, on Solaris its /etc/mail/sendmail.cf, but you need to look for the sendmail.cf file and then change the "Smart" relay host setting like this:

# "Smart" relay host (may be null)
DSsmtp.yourmailservername.co.uk.

This will then allow PHP to send mail via sendmail and all mail from this server will be routed via your corporate mail server. (I mean all mail too!).

I haven't actually done this, but it looks fairly easy and its what I would do in your situation.

Hope that helps.

---

### Post by bfr-dwn on 2009-02-18
Got the sendmail working, thanks for both of you!

---

