---
title: "catch all email collector/server"
date: 2008-07-15
forum: Server Platforms
---

### Post by brocky102 on 2008-07-15
i am wanting to setup an email system that receives email then cleans it of spam then forwards it on to another email server. Is this possible at all i have postfix + dovecot + spamassassin installed and configured to work as an email server but don't know where to go from there

---

### Post by promodus on 2008-07-15
Yes it's possible. What you want to set up is known as a "mail relay."

I have set something up similar here:
[http://www.promodus.net/postfixmailrelaysmarthostforexchange](http://www.promodus.net/postfixmailrelaysmarthostforexchange)

A relay for exchange. It was my intention to add spam filtering to that, but to be honest I've been pretty busy. The jist of setting up a mail relay, then a smart host for exchange I believe I covered those steps.

---

### Post by brocky102 on 2008-07-16
thanks man. i am yet to try it but by the looks of it that should work beautifully as i am to using it in front of exchange

---

### Post by brocky102 on 2008-07-17
Thats very close to what I was after but what it needs to do is pull mail down off the internet first then spam clean it then forward it to exchange. I have installed fetchmail which was looking promising but when fetchmail downloads emails i don't know where to send it as we are running a M$ exchange server with catchall filtering. Anyone has any idea?

---

### Post by PraysToPan on 2008-07-17
> **brocky102 said:**
> Thats very close to what I was after but what it needs to do is pull mail down off the internet first then spam clean it then forward it to exchange. I have installed fetchmail which was looking promising but when fetchmail downloads emails i don't know where to send it as we are running a M$ exchange server with catchall filtering. Anyone has any idea?

Check out the fetchmail package.  It can download from various types of email accounts (including ssl) and then pass it on to the SMTP server.  In your case, it can be configured to send to your Exchange server.

EDIT:
You will still have to do up maps in the fetchmailrc (man fetchmailrc) file for each pop or imap account you poll.

You can also get fetchmail to poll for the mail for an entire domain using ETRN smtp function but I haven't had experience doing this.  It's all in the fetchmail docs.

EDIT:
Google is my friend.  This might be of interest to you:
[http://www.wizzy.com/wizzy/mail.html#fetchmail](http://www.wizzy.com/wizzy/mail.html#fetchmail)

Jon

---

