---
title: "Mail Server &amp; Command Guide"
date: 2008-09-16
forum: Server Platforms
---

### Post by syedsiddiqui on 2008-09-16
Hi Guys,

I have couple questions.

1 I installed Ubuntu(Server Edition)as a mail server. when i try to send the mail i get the following error.

The following recipient(s) cannot be reached:

      'syedsiddiqui@gmail.com' on 9/16/2008 1:55 PM
            554 5.7.1 <syedsiddiqui@gmail.com>: Relay access denied

2 where do i get the post installation guide? i am very new to this, i don't even know a simple basic commands, I really appreciated for your help. Thank you.

---

### Post by alastair on 2008-09-16
> **syedsiddiqui said:**
> Hi Guys,

Hey - might be some gals around as well!

> **syedsiddiqui said:**
> I have couple questions.

1 I installed Ubuntu(Server Edition)as a mail server. when i try to send the mail i get the following error.

The following recipient(s) cannot be reached:

      'syedsiddiqui@gmail.com' on 9/16/2008 1:55 PM
            554 5.7.1 <syedsiddiqui@gmail.com>: Relay access denied


What mail client are you using?
What SMTP (outbound mail) server is it configured to use?

If you are setup to send email via your /own/ SMTP server above :

What mail server s/w?
What configuration has it got?

If you are using Postfix, post your /etc/postfix/main.cf.


> **syedsiddiqui said:**
> 2 where do i get the post installation guide? i am very new to this, i don't even know a simple basic commands, I really appreciated for your help. Thank you.

There's lots of guides around on the net, not quite sure what you are after. Be careful running a server, especially if it is public access. If you don't know how to set it up and secure it, keeep it off the net until you do. Or get someone to do it for you. Good luck.

Alastair

---

