---
title: "server noob help"
date: 2009-05-08
forum: Server Platforms
---

### Post by sidcypher on 2009-05-08
I know how to setup this stuff up in the desktop edition...

but still TRY to shy away from console, which isn't good now that i am running a server install on a machine..

a couple of hopefully easy to answer questions..

[This is basically what I am running]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3") which is the perfect server setup using ISPConfig..

i know i need to install samba, to be able to connect to windows network locations..so my questions are..

once samba is on, how do i mount network locations? like i said, could do in a gui..but don't know in console

share locations on my server with windows?

sure this would be some sort of script..so i will just explain what i want to happen, since unsure how to phrase..

> ftp user uploads files to "their ftp root folder" multiple ftp users..
once upload is complete, or in a timely manner..say 5pm everyday

server auto copies all files from all users to folders based on ftp username inside the "windows share"


what i am doing...is a book review site, and i want the publishers to ftp the books to me, instead of massively large, and numerous emails..is that possible? since if it copied to a folder w/publishers name..it would keep it organized..

and something i am completely clueless about..is since i have a dynamic IP..and would double my DSL bill to get a static..
i setup the email...and trying to send via the squirrelmail from the above How-to, checking the mail log, the outside servers are refusing the mail, since the dynamic is blacklisted....
So I found and followed this [tutorial]("http://www.howtoforge.com/postfix_relaying_through_another_mailserver")..on how to forge for getting it to forward through my ISP's mailserver..but it seems they are refusing to send since the "from address" doesn't match my ISP email login..replied from mailserver to MY server email address:

```
<ichangedthis@gmail.com>: host smtp.att.yahoo.com[68.142.198.11] said: 553 From:
    address not verified; see
    http://help.yahoo.com/sbc/dsl/mail/pop/pop-11.html (in reply to MAIL FROM
    command)

```

from mail log
 ```
May 8 12:51:00 beast postfix/smtp[11818]: 58A151C8463E: to=, relay=smtp.att.yahoo.com[68.142.198.11]:25, delay=2.3, delays=0.02/0.02/1.9/0.3, dsn=5.0.0, status=bounced (host smtp.att.yahoo.com[68.142.198.11] said: 553 From: address not verified; see http://help.yahoo.com/sbc/dsl/mail/pop/pop-11.html (in reply to MAIL FROM command))
May 8 12:51:00 beast postfix/cleanup[11800]: B62941C8463F: message-id=<20090508175100.B62941C8463F@beast.gateway.2wire.net>
May 8 12:51:00 beast postfix/bounce[11820]: 58A151C8463E: sender non-delivery notification: B62941C8463F
May 8 12:51:00 beast postfix/qmgr[6770]: B62941C8463F: from=<>, size=3445, nrcpt=1 (queue active)
May 8 12:51:00 beast postfix/qmgr[6770]: 58A151C8463E: removed
May 8 12:51:00 beast postfix/pipe[11821]: B62941C8463F: to=, relay=maildrop, delay=0.03, delays=0.01/0/0/0.02, dsn=2.0.0, status=sent (delivered via maildrop service)
May 8 12:51:00 beast postfix/qmgr[6770]: B62941C8463F: removed
```

is there another way around this? if you didn't see I am using ATT (sbcglobal) DSL..i am sure they are blocking it, i called their tech line, and the guy gave me some other address's to try all kicked back same error, so he basically just wished me luck on finding another loophole...

---

### Post by kanikilu on 2009-05-08
That's kind of a lot of questions for one thread, but I'll try to help with at least one of them...

> once samba is on, how do i mount network locations? like i said, could do in a gui..but don't know in console 

To mount windows shares from the command line, check out the man page for **mount.cifs**. An example might look like:

```
sudo mount.cifs //server/share /mount/point -o user=windowsUsername,password=windowsPassword,domain=windowsDomain
```

---

### Post by bacardiandwatermelon on 2009-05-08
Sorry can't help but there is a good Mailserver write up here...

[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

---

### Post by sidcypher on 2009-05-08
kanikilu -

thanks that works for mounting remote shares great..kina long command, oh well.

---

### Post by Iowan on 2009-05-08
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting CIFS shares.

---

