---
title: "Ubuntu Mail Server to Replace Exchange"
date: 2009-10-21
forum: Server Platforms
---

### Post by SynnerG on 2009-10-21
Im looking to replace an exchange server with an opensource solution. What OpenSource & Free setup would be best to replace an exchange server, using Ubuntu Server at the core ?

---

### Post by shazbut on 2009-10-21
If you need exchange-like features, maybe Zimbra?  I've not used it myself, but the name gets bandied about a lot as an exchange alternative.

---

### Post by drumbug1 on 2009-10-22
> **SynnerG said:**
> Im looking to replace an exchange server with an opensource solution. What OpenSource & Free setup would be best to replace an exchange server, using Ubuntu Server at the core ?

Can you be more specific to exactly what features of Exchange Server you need?  This would help us point you in the right direction.

---

### Post by vlc-designer on 2009-10-22
like the above post can you explain what you are trying to accomplish 

if you just want a mail server maybe [THIS]("http://flurdy.com/docs/postfix/") is what you want

---

### Post by druhboruch on 2009-10-22
Recently sogo is getting very popular:
[http://www.scalableogo.org/english.html](http://www.scalableogo.org/english.html)

Some users on this forum recommend citadel.

If you want nice looking web interface than have a look at openxchange.  The debs for Ubuntu make the installation very easy and the support forum is great.

---

### Post by SynnerG on 2009-10-22
Ive looked at Zimbra, it seems like most of the solutions cost money, especially if you want features, you seem to only get the basics with the opensource versions, like Zimbra and AtMail.

I just need the following
Mail with IMAP support
Global Contacts an Address Book
Support for mobile devices or PUSH
and shared Calendars

Thanks for the input

---

### Post by drumbug1 on 2009-10-22
> **SynnerG said:**
> Ive looked at Zimbra, it seems like most of the solutions cost money, especially if you want features, you seem to only get the basics with the opensource versions, like Zimbra and AtMail.

I just need the following
Mail with IMAP support
Global Contacts an Address Book
Support for mobile devices or PUSH
and shared Calendars

Thanks for the input

Are you wanting to use Blackberry or Windows Mobile?

Note about Open-Xchange:  "Open-Xchange Community Edition is free for non-commercial use." from:

[http://www.open-xchange.com/en/try](http://www.open-xchange.com/en/try)

...so you can't use open-xchange other than for personal use without paying some $$.




I just looked at SOGo's solution:  I've got to say that the website makes it look impressive.  I don't know if the e-mail is necessarily "push", but it appears it's a full e-mail/calendar/address solution that has blackberry/palm support for free.  Check out the screenshot tour here:

[http://www.scalableogo.org/tour/screenshots.html](http://www.scalableogo.org/tour/screenshots.html)

---

### Post by Dave.Wynne on 2009-10-23
I've just done an install of insight server 4.2 from [www.bynari.net]("http://www.bynari.net"), so far very happy. With insight connector I have full exchange / outlook functionality. One slight hiccup I couldn't use my ldap server from my Samba Domain controller. Second downside is it basically requires its own server. Although I'm going to have another go on my test setup in a few weeks (I'm presently on holiday). Have a look at the website and have a go.

---

