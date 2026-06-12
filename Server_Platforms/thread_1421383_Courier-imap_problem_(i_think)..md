---
title: "Courier-imap problem (i think?)."
date: 2010-03-04
forum: Server Platforms
---

### Post by Lorten on 2010-03-04
So ive been skimming around looking for the answer for awhile now tried all sort of things, 

getting close to finishing my little test mail server project, but ive run in to a couple of 

problems that i cant seem to find the answer for so im testing my luck over here.

So the first problem is:
Ive set up Courier-imap + squirrelmail + all the prerequisites, the first problem i ran into 

was not being able to connect to the mysql server, fixed that with changing when the mysql starts (before imap), 

then it worked until i rebooted the system now i cant login on squirrelmail,

 with the error: Unknown user or password incorrect.

I dont get any message in the Error logfiles but i get this message in the regular mail.log:

Mar  4 11:15:09 userver imapd: Connection, ip=[::ffff:127.0.0.1]
Mar  4 11:15:09 userver imapd: LOGIN FAILED, user=nisse, ip=[::ffff:127.0.0.1]
Mar  4 11:15:14 userver imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=47, sent=332

Cant seem to find the imap log if they even have their own log or if it used the mail.log.

Oh, yeah im using Ubuntu server 9.04 Jaunty.

Sorry for all the text hope its readable. 

Thanks in advance /Lorten :popcorn:

---

