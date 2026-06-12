---
title: "Real time email virus scanning in Lucid"
date: 2010-06-14
forum: Security
---

### Post by wyrdrat on 2010-06-14
I am building a PC that dual boots Kubuntu and Windows and want to share the email store.  Therefore, I would like to have real time or on access scanning of emails in an antivirus program like Windows does.  I am not running an email server, just a desktop using pop3 and eventually imap email.

In previous Debian versions ClamAV and Dazuko used to do this.  However, I understand that this setup doesn't work in Lucid.  I tried p3scan but that hasn't been updated since 2008, once I managed to install it, it failed to find clamd even though it was running.  I understand that clamdrib no longer works for Thunderbird 3.  Someone suggested Amavisd as a replacement for p3scan, but this seems to be for mail servers.

I would be really grateful if anyone could tell me how to get on access/real time virus scanning of pop3 and imap emails on a desktop running Lucid with either Thunderbird 3 or Kmail, without having to buy an antivirus program like Avast  Or point me to an existing tutorial that I might have missed.

As an aside (don't want much do I?) does anyone know if Kmail can be setup to only download the headers like Thunderbird does?

Thanks

---

### Post by linux-hack on 2010-06-14
I'm not sure but may be this can help you a little bit : [http://jameslick.com/clamassassin/](http://jameslick.com/clamassassin/)

---

### Post by wyrdrat on 2010-06-14
Thanks Boogy9 for getting back so quickly.  

I have had a cursory look at this and it seems to be for procmail, so I think it is geared for a mail server.  It also hasn't been updated since 2007 so I wouldn't mind betting there is some sort of library file that it needs which will be too recent in Lucid.  However, I could try to install it and piddle about with the settings, but my brain still hurts from trying to get p3scan to work!

So if anyone knows of anything that they know works on a desktop with TBird 3/Kmail in Lucid.

Cheers

---

### Post by wyrdrat on 2010-06-17
As no one knows of any other software, does anyone know if P3scan is still being worked on or if it has been abandoned?

Thanks

---

### Post by bodhi.zazen on 2010-06-18
clamav can do this for you.

---

### Post by wyrdrat on 2010-06-20
I am having trouble getting clamav to work with Lucid to scan incoming emails and notifying me immediately by a popup when it finds an individual email that is suspicious.  I have got bogged down with Dazuko and Dazukofs.  P3scan seemed to do what I want, but when I try to "make" it I get errors about struct cl_engine* and so on.

It seems that the person who created p3scan is unable to maintain it due to ill health and is asking for someone to take over the project.  My guess is that p3scan doesn't work with clamav 0.96.

---

### Post by wyrdrat on 2010-06-21
I am using P3scan v3 rc as it supports imap (v2.3.2 is provided with Ubuntu but it is only for pop3).  I managed to install it, you need to remove references to clamav when compiling p3scan v3, then add support for clamav in its conf later.  However now when it is rebooted p3scan does not create a PID file ...

---

