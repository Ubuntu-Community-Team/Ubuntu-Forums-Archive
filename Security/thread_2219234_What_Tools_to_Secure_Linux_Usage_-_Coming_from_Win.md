---
title: "What Tools to Secure Linux Usage - Coming from Windows XP/7"
date: 2014-04-23
forum: Security
---

### Post by mysubs on 2014-04-23
I'm coming from a *purely Windows* environment and I haven't used Linux as a primary OS at all.  I'm familiar enough with it to get around, and I feel comfortable enough to begin the transition.  I have a 100% offline machine at home which is the target for loading Linux; currently it runs Windows XP SP3.  I have a lot of sensitive data on the computer and I'm curious what I need to know about switching from my *quote-unquote* "secure" Windows XP system to a secure Ubuntu system.  I'm very much in the dark here about how to do the following:

Removing traces of accessed files (documents, offline browser activity, etc - [Windows] I use CCleaner
Wiping sensitive files - [Windows] I use [Eraser]("http://eraser.heidi.ie/download.php") set to 35 passes. All disks are HDDs
Wiping Freespace - [Windows] I use Eraser
Encrypted storage - [Windows] a combination of Truecrypt hidden volumes and PGP Desktop (9.x) encrypted volumes.  I know TC runs on Linux, but I semi-dread the idea of having to convert several massive PGP Desktop volumes to something else.  Is there anything for Linux which opens PGP Desktop volumes?

I know the information is out there, but I'm trying to find updated, relevant, and credible assistance because I want to do this 'right' from the get go.
Thanks in advance! :)

---

### Post by sudodus on 2014-04-23
Welcome to the Ubuntu Forums :-)

Get some general information from this link [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

And then consider what level of security you want. An encrypted disk or encrypted home directory increases security, but not while you are running the system. And if you forget the password you will lose all information. Your own browsing habits and treatment of unknown attached files (in email) is at least as important as advanced tools for security.

---

### Post by HermanAB on 2014-04-23
Well, if you install Linux with 'full disk encryption', then beyond that, you don't have to do anything.  Just relax and enjoy your new, surprisingly secure system.

---

### Post by ant2ne on 2014-04-23
An encrypted drive only protects the data at rest. If you have poor OS security your mounted encrypted drive is still vulnerable.

---

### Post by mysubs on 2014-04-23
> **HermanAB said:**
> Well, if you install Linux with 'full disk encryption', then beyond that, you don't have to do anything.  Just relax and enjoy your new, surprisingly secure system.
That's what I keep hearing.  And coming from Windows, obviously I'm somewhat skeptical.

[QUOTE=ant2ne]An encrypted drive only protects the data at rest. If you have poor  OS security your mounted encrypted drive is still vulnerable.[/QUOTE]
That's fine too, my primary concern is securing data while at rest and to eliminate traces of file activity.  At least on my **offline-only** computer, which will be the first system to make the transition to Linux.  It's also the computer which requires the most security, and thus the reason it's offline.

Thanks for the link @sudodus, I've read through it.  That's a good starter and I continue to look deeper.

---

### Post by HermanAB on 2014-04-23
Most of the internet servers run Linux.  It is pretty good.

I run my web/mail servers with a single rate limiting rule and nothing else and they keep running 24/7 for 5 to 7 years, when the PSU eventually blows up.  

So you don't need any additional 'protection'.  Linux isn't Windows.

---

