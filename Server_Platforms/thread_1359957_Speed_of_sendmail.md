---
title: "Speed of sendmail"
date: 2009-12-20
forum: Server Platforms
---

### Post by Starcraftmazter on 2009-12-20
Hello

I do quite a bit of PHP development on my machine. One thing that always gets me is that sendmail takes a few **minutes** to send an email (ie. mail() from PHP).

All the servers I've had (centos, etc) do this instantly, but ever since I've used Ubuntu for several years now, the sendmail package always sends emails very very slowly.

Can anyone shed any light on why this is, and how to improve it's speed?

:confused::confused::confused:

---

### Post by a9k3d on 2009-12-22
I'm using postfix on many ubuntu servers which send emails from php and ruby. It's under 3 seconds from send to deliver. The mail relay is on internal network.

Have you checked the mail.log files to see how long it really is taking? Sometimes the delays are not the sending but the receiving end.

---

### Post by Starcraftmazter on 2009-12-22
Sorry I think I wasn't being clear enough at all.

When I say it takes minutes to send, I mean **the php script hangs in execution** for minutes before the email is finally sent by the script.

---

