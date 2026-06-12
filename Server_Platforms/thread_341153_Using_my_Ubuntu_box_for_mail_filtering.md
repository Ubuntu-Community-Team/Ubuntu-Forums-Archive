---
title: "Using my Ubuntu box for mail filtering?"
date: 2007-01-18
forum: Server Platforms
---

### Post by Josh1 on 2007-01-18
Hi all,

I have read quite a few guides about setting up mailservers, but it isn't quite what I want/need. What I need to do is:

[COLOR="Blue"]Sender Sends Email[/COLOR] **(to ISP address**) -> [COLOR="Red"]ISP[/COLOR] (They have a really bad spam filtering software) -> [COLOR="Purple"]Ubuntu Box[/COLOR]**(Filtering for common spam keywords, but I also want to allow certain email addresses)** -> [COLOR="DarkRed"]Windows XP Outlook Express[/COLOR] **(Mail from Ubuntu box on LAN)** .

No idea where to start from, anyhelp would be appreciated.

Cheers,
Josh

---

### Post by jtc on 2007-01-18
I'll give a brief description of a possible solution. That way it ought to be easier to know which tuturials and Howtos you should look for. Feel free to ask more detailed questions as they arise.

**Ubuntu-server**
[LIST=1]
[*]Collects the mail from your ISP by POP och IMAP, where the later is prefered. For this task *fetchmail* is the tool you want.
[*]Fetchmail deliveres the mail to your MTA (mailserver). I'd recommend *Postfix*.
[*]Your MTA asks *amavisd-new* to checks if the mail contains spam or virsus.
[*]Amavisd-new can use a lot of diffrent scanners. I'd recommend *SpamAssassin* against spam and *ClamAV* against viruses.
[*]Your MTA delivers the clean mails to your mailbox, from where an IMAP-server can access them. Usually you still want to delivers the suspected spam, but tag it as such. When it comes to IMAP-servers I kind of like Courier-IMAP myself.
[/LIST]

**Windows Outlook**
[LIST]
[*]Instead of collection the mail from your ISP you collect them from your Ubuntu-server.
[*]You tell Outlook to filter the spam-tagged into a special folder, which you look in from time to time, in case of false positives. Another option here would be to have Procmail do there sorting directly at your mailserver.
[/LIST]

---

### Post by Josh1 on 2007-01-18
> **jtc said:**
> I'll give a brief description of a possible solution. That way it ought to be easier to know which tuturials and Howtos you should look for. Feel free to ask more detailed questions as they arise.

**Ubuntu-server**
[LIST=1]
[*]Collects the mail from your ISP by POP och IMAP, where the later is prefered. For this task *fetchmail* is the tool you want.
[*]Fetchmail deliveres the mail to your MTA (mailserver). I'd recommend *Postfix*.
[*]Your MTA asks *amavisd-new* to checks if the mail contains spam or virsus.
[*]Amavisd-new can use a lot of diffrent scanners. I'd recommend *SpamAssassin* against spam and *ClamAV* against viruses.
[*]Your MTA delivers the clean mails to your mailbox, from where an IMAP-server can access them. Usually you still want to delivers the suspected spam, but tag it as such. When it comes to IMAP-servers I kind of like Courier-IMAP myself.
[/LIST]

**Windows Outlook**
[LIST]
[*]Instead of collection the mail from your ISP you collect them from your Ubuntu-server.
[*]You tell Outlook to filter the spam-tagged into a special folder, which you look in from time to time, in case of false positives. Another option here would be to have Procmail do there sorting directly at your mailserver.
[/LIST]

Thank you very much for your detailed response, I can now start tinkering. Thanks also for the much needed advise.

- Josh

---

### Post by Josh1 on 2007-01-18
Turns out my ISP does not offer IMAP, just POP3 which is a shame. Oh well lol. Willstill get everything sorted and post back how I did it. :)

---

