---
title: "Debian Mail Server -&gt; Ubuntu"
date: 2008-01-23
forum: Server Platforms
---

### Post by quietas on 2008-01-23
Ok, here's the deal. I've got a mail server that was Debian 3.0 and over the years has been upgraded to 4.0 by previous admins. Frankly it's a mess and it runs damned slow. For a P4 2.0, 2gb RAM, it hardly handles  3000 messages a day with out choking at least once a day.

Rather than dealing with it and troubleshooting a POS, I'm going to attempt to just rebuild it on a slightly faster system using Ubuntu server. Which version 6.06, 7.10, or hang out and wait for 8.04?

Also it's using Exim 3 still, so I'll be movin to Exim 4, or should I swap to Postfix for the MTA? Along with Exim, we've got MailScanner and PHPGroupware running. I'll be making these current as well.

Also I'll need to move users and home directories, any insight there?

If there's anything I missed, please feel free to chime in.

~ Culley

---

### Post by smileypaul on 2008-01-24
Definately stick with an LTS release .. so either 6.06.2 or 8.04 when it comes out in a few months..  the last thing you want to be doing is full upgrades every 8 months or so

---

### Post by DDuong on 2008-01-26
I say wait till 8.04 is out and go with postfix.  

I've read that Postfix is more efficient than Exim.  But that is just my opinion :)

---

### Post by HermanAB on 2008-01-26
Hey, no mail thread is complete without me recommending Citadel.

I've used Postfix for many years, but I have come to the conclusion that like Sendmail before it, it is now time to throw off the shackles and join the new age...

Cheers,

Herman

---

### Post by quietas on 2008-01-31
The catch with Citadel is:
[LIST]
[*]How user friendly is the interface?
[*]How hard is it to move existing users and home dirs (complete with Maildir folders)?
[*]Outlook connector?
[/LIST]

---

### Post by HermanAB on 2008-01-31
The catch with Citadel is:

    * How user friendly is the interface?

Unbeatable. Web based. Nothing easier.

    * How hard is it to move existing users and home dirs (complete with Maildir folders)?

You have to forward the mail to the new server.   Mail is stored in a database, so Citadel has to process it.

    * Outlook connector?

Outlook works very well using IMAP with Citadel.  There is also a connector available, but I find IMAP to be good enough.
Citadel works with any mail client, though you don't need one, since the web interface is very good and has many more features than a mail client.

Cheers,

H.

---

### Post by quietas on 2008-01-31
Sounds good and I've browsed the website a bit. Looks good as well, with company colors and logos added in.

One thing of course is moving all my current users and mail away from the old box and mail system to Citadel.

---

### Post by HermanAB on 2008-01-31
I have found that the best way to move old mail is *not* to move it.

Outlook saves old mail in a PST file.  So just keep that, change the incoming mail server setting or port number to some dud value so that it can't connect to anything, then make a new account for the new mail server.

So then people can still access their old mail and a reply to an old mail will be sent via the new mail server, but the new mail server will only collect new mail.

---

### Post by vpsville on 2008-01-31
I agree with not moving it if you don't have to.

If you dont mind spending some money to get a better mail server, take a look at Surgemail.  We set it up for a client with major spam issues and its working very well now.  That and SPF made a huge difference.

---

### Post by quietas on 2008-01-31
Our current old system is an old Debian box running Imap, thus to keep it all I suppose I need to drag over all the Maildir's, but I'll have to see how Citadel stores everything.

---

