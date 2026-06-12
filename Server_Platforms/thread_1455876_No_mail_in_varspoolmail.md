---
title: "No mail in /var/spool/mail"
date: 2010-04-16
forum: Server Platforms
---

### Post by dado prso on 2010-04-16
Hello,


I'm running sendmail and I believe that proc mail is no longer writing mail to my spool directory.

Any Idea why this would be happening?

Thank you,
dado

---

### Post by JonRohan on 2010-04-16
Was it ever working? If not then permissions would be my first port of call.

---

### Post by dado prso on 2010-04-19
It was working, then I tried to replace var spool mail with a named pipe.

I have set the permission to write to the mail folder.

I think it has something to do with path directions:
my mail is now sent straight to var/mail/eric (eric is my username)
and get held there if I don't read them.

if i do read them they get saved in /home/eric/mbox.

I think I need to set up procmail? Is this a good idea?

Thanks for the suggestion!

---

### Post by dado prso on 2010-04-19
Ok, so what I'm trying to do is have all mail that goes through my sendmail be sent to a named pipe so I can gather statistics.

I tried to get a .forward file working; I'm having trouble, but I believe this is the best way to go.

Any advice?

---

