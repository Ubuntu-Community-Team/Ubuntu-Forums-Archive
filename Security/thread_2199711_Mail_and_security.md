---
title: "Mail and security"
date: 2014-01-15
forum: Security
---

### Post by becerroloko on 2014-01-15
Hi! This is my first post, I hope the first of many more to come.



First off, sorry if this is an old question or a too basic one. I'm a new ubuntu user. I used the Advanced Search tool and didn't find the answers to the question I have.


The thing is I got a mail with some **pics attached** in my hotmail account from a non reliable source and **I don't know if it is safe to show the images**. I know in Windows that could cause some trouble, infecting your computer with malware. Is it possible to get malware from the mail in Ubuntu?

If so, I would like to know too if there's possible to get infected the same way while running an Ubuntu Live CD.



Thanks in advance and sorry again if this question is too basic.

---

### Post by newbie-user on 2014-01-15
Yes, it is possible to get malware from mail in Ubuntu. Nothing is impossible, but with Ubuntu, it's less likely. Checking your email using a live cd would be safe, since a live cd session doesn't actually require a hard drive. If you want to be completely safe, unplug your hard drive and then run the live cd.

---

### Post by Impavidus on 2014-01-15
In theory, yes, you can get malware via email. It's mostly trojans that you have to worry about, programs that, when executed, do something malicious. I don't think you have to worry about something as simple as a picture. Even if it's a Linux executable in disguise (with a .jpeg extension, for example), you can't run the file, only view it, unless you explicitly state you want to get execute permission for the file. So, even in the unlikely case of Linux-compatible malware, it's unlikely to cause damage when you only open the picture for display.

---

### Post by Bucky Ball on 2014-01-15
*Thread moved to** Security Discussions.***

---

### Post by becerroloko on 2014-01-15
Thank you very much both of you **newbie-user** and **Impavidus**.

> **newbie-user said:**
> Yes, it is possible to get malware from mail in Ubuntu. Nothing is impossible, but with Ubuntu, it's less likely. Checking your email using a live cd would be safe, since a live cd session doesn't actually require a hard drive. If you want to be completely safe, unplug your hard drive and then run the live cd.
What about the BIOS? Could it get infected even without the hard drive? (sorry if my question is silly)

> **Impavidus said:**
> In theory, yes, you can get malware via email. It's mostly trojans that you have to worry about, programs that, when executed, do something malicious. I don't think you have to worry about something as simple as a picture. Even if it's a Linux executable in disguise (with a .jpeg extension, for example), you can't run the file, only view it, unless you explicitly state you want to get execute permission for the file. So, even in the unlikely case of Linux-compatible malware, it's unlikely to cause damage when you only open the picture for display.
How do you state you want to get execute permission for the file?
Is there a way to know if the attached files are excutables in disguise **before** allowing the pics to be viewed? If not, how would you do it after?

I also would appreciate recommendations on Ubuntu antivirus and any advise you consider helpful for an inexperienced user like me.

Thank you very much again!

---

### Post by Irihapeti on 2014-01-16
As a rule, it's not considered necessary to run antivirus on Ubuntu unless you are exchanging a lot of files with Windows users and want to check that they're safe before transferring them.

For Ubuntu security info, a good place to start is [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by CharlesA on 2014-01-16
When in doubt delete the email without opening it.

---

### Post by Dave_L on 2014-01-17
> **becerroloko said:**
> Is there a way to know if the attached files are excutables in disguise **before** allowing the pics to be viewed? If not, how would you do it after?

CharlesA's advice is good.

But if you don't want to do that, a compromise is:

1) Instead of trying to open the files from your email client, save them to a temporary directory.

2) Open the relevant application, e.g. an image viewer or word processor.

3) Open the files from within the application.

4) If it's an email from Nigeria offering you a great way to make a lot of money, don't trust it. :)

---

### Post by SeijiSensei on 2014-01-17
> **becerroloko said:**
> Is there a way to know if the attached files are excutables in disguise **before** allowing the pics to be viewed?

Usually malware posing as image attachments have filenames like jenna.jpg.exe.  Older mail clients had bugs that enabled the use of various techniques to hide the .exe part of the filename from view.  Most contemporary mail clients are protected against those sorts of attacks.

The easiest way to see what is in an email message is to view its "source."  In Thunderbird, use F8 to hide the message preview window, then highlight a message in the list and use Ctrl-U to view its source. You'll see something like this ahead of the MIME-encoded attachment itself:

```

--===============1680891543==
Content-Type: application/octet-stream
MIME-Version: 1.0
Content-Transfer-Encoding: base64
Content-Disposition: attachment; filename="PARCEL FOR YOU.rtf"

```

(This is from an obvious scam I received this morning.)

---

### Post by kc1di on 2014-01-17
While others have hopefully answered your question , I just want to welcome you to Ubuntu , enjoy ;)

---

### Post by Irihapeti on 2014-01-17
> **SeijiSensei said:**
> The easiest way to see what is in an email message is to view its "source."  In Thunderbird, use F8 to hide the message preview window, then highlight a message in the list and use Ctrl-U to view its source....

You can also see, if you read through the entire header, where the thing has come from.

An origin of something like "yahoo.com.br" or "mail.ru" when it says it's from USPS, for example, is a dead giveaway that it's not legitimate.

Ctrl-U also works in Firefox, by the way, if you're using a web interface.

---

