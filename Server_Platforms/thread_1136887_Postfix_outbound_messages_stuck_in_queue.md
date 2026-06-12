---
title: "Postfix: outbound messages stuck in queue"
date: 2009-04-25
forum: Server Platforms
---

### Post by seamusandboo on 2009-04-25
I wonder if anybody can help me out with this. So I installed postfix on Ubuntu 9.04 Server following all the directions on this guide:

[http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p5](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p5)

I had to change the default postfix port from 25 to 587 as my ISP blocks 25 for some reason, so I commented and uncommented the respective lines in the master.cf file:

#smtp inet n - - - - smtpd
submission inet n - - - - smtpd

I then restarted the server. But when I send e-mails to outside e-mail addresses, the messages are not sent, they get stuck in the queue indefinitely. How do I go about troubleshooting this?

I really don't care about receiving e-mails, I just want to be able to send e-mails with the php mail() function.

Any help will be appreciated!

---

