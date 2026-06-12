---
title: "maildrop msgs not delivered correctly"
date: 2008-12-12
forum: Server Platforms
---

### Post by martien on 2008-12-12
Hello everyone. I have problem trying to run mail server using postfix, courier imap and maildrop:
I configured postfix and courier (with mysql virtual users) and in my transport table i have <mydomain> pointing to maildrop:
Well, i have maildrop and when i try to send mail using mail account (gmail,hotmail,etc.) it sents it and in my mail.log i have 
> ...relay=maildrop status=sent (delivered via maildrop service)
but when i open squirrelmail it has no msgs and when i try to browse the directories in /home/vmail/<mydomain>/<mailuser>/Maildir its no new files..
Then i found that all msgs that i sent were delivered into /home/vmail/Maildir (that is a file..)
How can i fix this? Any ideas? Thanks in advance

---

### Post by martien on 2008-12-20
Any idea? The problem is still here...

---

### Post by froek on 2008-12-23
I have this exact problem.

postfix + mysql + spamassassin + courier-maildrop is not working.

It appears that the maildroprc file isn't getting the $USER, $HOST, etc.. variables set.  They are blank and that's why my setup is delivering all mail to /home/vmail/./Maildir.

I don't know whether it's my master.cf entry for maildrop that's screwed up:

maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop /etc/maildroprc ${user} ${nexthop} ${sender}


???  This is quite puzzling!

---

### Post by froek on 2008-12-23
The other thing I just noticed, if I run the following command:

maildrop -V 4 -d [email]email_test@test.com[/email] < /etc/motd

it properly delivers my mail to the right location.  This is what makes me think that postfix is not passing the right arguments to maildrop.

---

### Post by crazief123 on 2008-12-23
[img]http://www.top1gaming.com/cosplay2/20081111/I-no-1.jpg[/img] See the answer [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-198.html).  Want to see [[color=#800080]more pics[/color]](http://www.top1gaming.com/cosplayer.php)? Show yourself  on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/index.php?gid=27)**Recommend:**[[color=orange]Christmas version Meer Campbell [/color]](http://www.top1gaming.com/coscontent-206.html)[[color=orange]Christmas Sailor Moon[/color]](http://www.top1gaming.com/coscontent-209.html)

---

