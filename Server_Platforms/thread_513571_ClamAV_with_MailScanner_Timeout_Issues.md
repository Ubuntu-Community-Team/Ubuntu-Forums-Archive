---
title: "ClamAV with MailScanner Timeout Issues"
date: 2007-07-30
forum: Server Platforms
---

### Post by JohnnyPiratefish on 2007-07-30
I'm seeing log entries in my mail log that say "Virus Scanning: Denial Of Service attack is in message" and "Virus Scanning: Denial Of Service attack detected!"

Apparently when these messages are being generated, clamav dies, and doesn't finish it's job, and MailScanner isn't delivering the messages.  Now for obvious reasons, it's likely that MailScanner might need  a tune-up so that it talks better to ClamAV, but when I go looking at ClamAV, it's harping on (as usual) about my needing to upgrade.

Currently, on Ubuntu server, the latest I can get is verison .90.2, while the current one is .91.something.

I have tried upgrading a server to the latest by compiling the source, a total pain in the butt, but I was wondering, who's the Ubuntu ClamAv package maintainer, and how does one go about finding out how far down the pike an upgrade to ClamAV is?

My need for concern is that I've got a number of users using my anti-spam directions (see [www.piratefish.org](www.piratefish.org) for more info) and they're all using ClamAV to scan their email - and they may all be experiencing these problems.

Thanks.

-----------------

2 Days later, 24 views, no posts.

I've now confirmed this issue appears on other users systems - and there's some other news as well - the mail.log file is showing this:

Jul 27 15:26:07 (server) MailScanner[16763]: Commercial scanner clamav timed out!
Jul 27 15:26:07 (server) MailScanner[16763]: clamav: Failed to complete, timed out
Jul 27 15:26:07 (server) MailScanner[16763]: Virus Scanning: Denial Of Service attack detected! 

Turning off ClamAV does help - in fact, the anti-spam performance without it is fantastic - however, having working anti-virus would be nice.

---

