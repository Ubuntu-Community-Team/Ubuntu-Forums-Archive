---
title: "How do I change outgoing email port number?"
date: 2022-12-02
forum: Server Platforms
---

### Post by mikecolley on 2022-12-02
Hi All:

I hope this is not a duplicate post, I made a mistake earlier a couple days ago.

I have been using Ubuntu 20.04 Server a couple years now, very happy with it.  Web server still works fine.  Incoming email works fine. Outgoing email worked until 2-3 weeks ago when I started getting ```
Subject: Undelivered Mail Returned to Sender
``` in my alpine email inbox.  I send one or two e-mails every week (total).

I have kept this 20.04 as close as possible to the original.  When I got it working I told myself don't touch the baby and the only thing I have changed is to add postfix.  It works, don't touch it.

Outgoing email broke.  I don't know why.  I had an old disk backup (actually a mirror image bootable flash drive) from a couple months ago and booted this exact same mirror image system backup (two months old), that I am using today, from a couple months ago, but outgoing email was still broken, so I know the ubuntu server 20.04 isn't the cause.  I only use this old old HP8730 core2-duo laptop as a personal web and mail server and nothing else, nothing virtual.

Error Message from bounced returned email(I changed the users and domain names):

```

Subject: Undelivered Mail Returned to Sender
Parts/Attachments:
   1   Shown     17 lines  Text, "Notification"
   2   Shown    530 bytes  Message, "Delivery report"
   3   Shown    894 bytes  Message, "Undelivered Message"
   3.1 Shown     12 lines  Text
----------------------------------------

This is the mail system at host mydomain.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<user-destination@twc.com>: host mail.twc.com[47.43.26.4] said: 550 5.1.0
    <user-me@mydomain.com> sender rejected. The email address you are sending as
    must match the email address you used to auth. Please check your SMTP
    settings. AUP#Out-1500 (in reply to MAIL FROM command)


    [ Part 2: "Delivery report" ]

Reporting-MTA: dns; mydomain.com
X-Postfix-Queue-ID: CCB5B15F708
X-Postfix-Sender: rfc822; user-me@mydomain.com
Arrival-Date: Wed, 30 Nov 2022 14:14:32 -0500 (EST)

Final-Recipient: rfc822; user-destination@twc.com
Original-Recipient: rfc822;user-destination@twc.com
Action: failed
Status: 5.1.0
Remote-MTA: dns; mail.twc.com
Diagnostic-Code: smtp; 550 5.1.0 <user-me@mydomain.com> sender rejected. The email
    address you are sending as must match the email address you used to auth.
    Please check your SMTP settings. AUP#Out-1500



    [ Part 3: "Undelivered Message" ]

Date: Wed, 30 Nov 2022 14:14:32

```

I called my internet provider (very nice helpful person) told me my regular subscriber account didn't support a server, but I will say that person was very nice.  BTW, it has been working fine for two years and that person still talked to me after that.

Someone (I can't say who) suggested I change the port number to 587.

I logged into my DNS and it doesn't need renewal for a couple years, no problem there.  I've tried to check everything so now I am asking for help.  Three problems;


[LIST]
[*]PROBLEM 1: I googled and googled but I gave up trying to find WHICH FILE to edit to change the port number so I decided to ask here. 
[*]PROBLEM 2: I also don't know if I have to run a program to make the port change take affect.  (which one?) 
[*]PROBLEM 3: I also don't know how to restart the server after changing the port to 587.  It won't hurt me if I have to power the laptop (server), that should work. 
[/LIST]

Thanks for taking the time to read this post and thanks for your help.

- Mike

---

### Post by mikecolley on 2022-12-02
I said I added postfix, wrong, that was already part of 20.04 - Mike

---

