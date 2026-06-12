---
title: "Postfix smtp won't allow extern computers to connect."
date: 2009-09-13
forum: Server Platforms
---

### Post by artheus on 2009-09-13
Hi!

I've got a little problem using my postfix smtp. When I try to connect to my server using an external computer, at one of my friends house or something It refuses to communicate.
When I'm at home it works great. I've forwarded the necessary ports in my Router, and other things like dovecot and such works great. I am using port 2525 for my smtp settings.
And in "mynetworks" I've put in "127.0.0.0/24 127.0.1.0/24 192.168.1.0/24". So I guess it's the mynetworks that is supposed to be different? Or am I totally wrong?

Hope there's someone here who's got the answer.

Cheers,
Artheus

---

### Post by fakrulalam on 2009-09-14
Can you provide the mail log (/var/log/mail.log) output when you try to connect from your friends network.

---

### Post by KiLaHuRtZ on 2009-09-14
Are you attempting to use your server for SMTP relay or outgoing server from your friend's network?  Mind you that you'll need a courier (i.e. IMAP or POP3) to retrieve your mail.  Please elaborate on the issue.

---

