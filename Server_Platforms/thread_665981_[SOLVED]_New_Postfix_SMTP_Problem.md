---
title: "[SOLVED] New Postfix SMTP Problem"
date: 2008-01-12
forum: Server Platforms
---

### Post by notaloafer on 2008-01-12
To start off with I've confirmed with dnsstuff.com and a few other websites that my ISP is no longer allowing port 25 SMTP inbound connections (I called Comcast and they told me they discontinued this feature to reduce spam). 

What I think I need to do now is setup postfix to listen on port 587 instead of 25... will this work and how would I go about changing the SMTP port that postfix listens on?

Right now if I try to "telnet mail.notaloafer.com 25" I get a refused connection error (I've tried it on remote machines). I know this is 100% Comcast's doing because up until yesterday my mail server was working fine for about 5+ months with no hitches..

If I change my server to listen on port 587 instead of 25 will I still be able to receive email? How do I go about changing postfix to do this?

Thanks
-Eric

---

### Post by notaloafer on 2008-01-12
Okay now I know for sure that Comcast is blocking port 25 inbound.

I setup Postfix to accept mail on port 587 and I tested it with a telnet connection (successful) but still my mail servers are failing; no one can send me email! I can send email out through my server and people can receive it (gmail, hotmail, etc.) but I cannot get email. When I download email from dovecot (which I am able to do because dovecot is setup correctly) I never get any new messages nor do I get any failure messages from Gmail, etc. (the emails I try to send the test emails from).

Since port 25 is blocked inbound by Comcast is there a way to setup my DNS to automatically tell the connecting clients (Google, Hotmail, etc.) to use port 587 instead of port 25? I think what is happening is this:

1) Test email is sent from [email]xxx@gmail.com[/email] to [email]xxx@notaloafer.com[/email]
2) notaloafer.com says its mail record is mail.notaloafer.com
3) Gmail attempts to deliver the message via mail.notaloafer.com on port 25 (which Comcast is blocking) instead of port 587
4) The connection fails from Gmail because port 25 is being blocked before it even gets to my server. Gmail needs to use port 587 but doesn't know that.

The question is how do I set mail.notaloafer.com to tell services such as Gmail to use port 587 instead for mail delivery?

If I'm thinking about this wrong please let me know.

Thanks
-Eric

---

### Post by HermanAB on 2008-01-12
You have to upgrade your account to a 'server' account.  It will cost a little more, but that is what it is all about.  The ISP wants to make more money.

---

### Post by notaloafer on 2008-01-12
Am I to understand that there is no way around this? I looked around more and haven't found a solution...

I'm guessing dynamic DNS services would also be a option..?

---

### Post by MJN on 2008-01-13
> **notaloafer said:**
> Since port 25 is blocked inbound by Comcast is there a way to setup my DNS to automatically tell the connecting clients (Google, Hotmail, etc.) to use port 587 instead of port 25? I think what is happening is this:

1) Test email is sent from [EMAIL="xxx@gmail.com"]xxx@gmail.com[/EMAIL] to [EMAIL="xxx@notaloafer.com"]xxx@notaloafer.com[/EMAIL]
2) notaloafer.com says its mail record is mail.notaloafer.com
3) Gmail attempts to deliver the message via mail.notaloafer.com on port 25 (which Comcast is blocking) instead of port 587
4) The connection fails from Gmail because port 25 is being blocked before it even gets to my server. Gmail needs to use port 587 but doesn't know that.

Hi Eric,

Your understanding is correct, however it is not possible to advise the sending MTA of the alternative port - at least not using DNS anyway.

You need a higher-level solution and one which will ultimately involve a 3rd part accepting your mail on your behalf (your MX record would point to them) and they would then connect to your server on an pre-determined alternative port.

No-ip.com provides such a service - the [Mail Reflector]("http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html") service but it does cost and I have no personal experience of it so cannot 'recommend' per se. An obvious disadvantage of this strategy is a limited anti-spam ability (unless you rely on no-ip.com doing it for you) given that you would be unable to perform filtering at the SMTP stage (given that all connections, given they are from no-ip.com, would have to be considered trusted). However, beggars can't be choosers...

Mathew

---

### Post by notaloafer on 2008-01-13
Yeah I understand about the alternate 3rd-party MX host. I looked into it and the cheapest I can get is $15.00 / year... the only problem with this is most of the websites I host are free and I don't really make any revenue to justify buying this redirection for all of my 20 domains.

Am I to understand that there is no possible way to send the MTA a alternate port to use? I looked this up for about 2 hours and came up empty-handed... do any of you guys know if there is a way to do this?

Thanks
-Eric

**Also:** Do MTA's such as gmail, etc. recognize SSL ports? Maybe I could configure my server to use SSL instead for SMTP and make it secure SMTP?

---

### Post by HermanAB on 2008-01-13
Yes of course you can set your MTA to use any one of 65000 ports, but there is no point in doing that since how are you going to tell the rest of the world that they are supposed to send mail to you on that port?

---

### Post by notaloafer on 2008-01-13
Well I was thinking that maybe the SSL standard port for SMTP is another one that MTA's automatically recognize? Am I wrong? =P

Thanks

---

### Post by MJN on 2008-01-13
Your only options are those that have been proposed...

Mathew

---

