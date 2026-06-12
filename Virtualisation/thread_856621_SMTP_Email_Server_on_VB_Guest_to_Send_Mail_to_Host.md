---
title: "SMTP Email Server on VB Guest to Send Mail to Host"
date: 2008-07-11
forum: Virtualisation
---

### Post by bluelamp999 on 2008-07-11
Hello Friends,

Here's what I like to do...

I'm developing an application on a VirtualBox XP guest (Visual Studio.Net) with 8.04 Ubuntu as the host.

An essential component of the app is to send emails (with attached PDFs) via an SMTP email server (e.g. MicroSoft Exchange Server).

I don't want/can't afford Exchange Server so I'm thinking of using a free/open source SMTP server, specifically hMailServer.

I would like the app on the guest to send the emails using hMailServer and to receive them on the host system.

I'd rather not go out over the internet, I'd just like the guest to receive the emails over a bridged network between guest and host.

Do I need 2 SMTP servers, one on the guest (to send) and one on the host (to receive)?

Essentially what I'd like to do is prove the concept that the guest app is properly sending emails without bothering my ISP and keeping it all on the bridged network.

Is this possible?

Is there a better alternative?

Any advice/suggestions gratefully received.

Many thanks

Mike

---

### Post by nicko7i on 2008-07-11
If all the app needs to do is send mail, then you don't need hMailServer.  Configure the app to send outgoing mail through an SMTP server that's not on the local machine.  For instance, that's how someone sets up Outlook to send mail.

If your Ubuntu host is connected to the Internet, then the easiest thing to do would be to set up your XP app to hand outgoing mail to *your* email service provider: smtp.gmail.com or whomever.  Send your test emails from the app to your personal email account.

For testing, this has the advantage of looking the most like what your actual users will encounter.

If your Ubuntu host is *not* connected to the Internet, or if for some other reason you would prefer to keep all testing on the internal network, then you could set up an SMTP server on Ubuntu.  This is more complicated and wouldn't be my first choice, but the good news is I successfully did this, today, for the first time (after nearly 30 years of using Unix) by installing Ubuntu Postfix.  The installer will ask you some questions.  You'll want local delivery but you don't need relaying.

As I mentioned, I don't recommend this approach.  If your XP app users will be connecting to outside SMTP server, then the Ubuntu server isn't a very good model of what they will encounter.  Real-world servers have various security protocols that you wouldn't be testing against on Ubuntu.

A final technical note: what you and I have been calling "SMTP server" is technically a "Mail Transfer Agent (MTA)".  Doesn't make any difference for our purposes.

Good luck!

n

---

### Post by bluelamp999 on 2008-07-12
Hey nicko7i!

Firstly, thank you so much for taking the time to reply...

I really love the Ubuntu ethos that encourages complete strangers to just help each other...

Anyway, enough gushing...

You're dead right in saying that all the app needs to do is connect to a(ny) MTA <-see? I'm learning!

However, this app is an attempt to commercialize a solution I've developed for my corporate overlords and, as such, has always been tethered to an Exchange server.

When I (hopefully) demonstrate to prospectives I'd like to be able to show the whole thing running in a walled garden type of thing (on my trusty laptop), so your endorsement of Postfix is extremely helpful...

Again, many thanks...

---

