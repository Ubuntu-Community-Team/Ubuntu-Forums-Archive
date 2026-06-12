---
title: "Delete ALL Mail Server Settings and Start From Scratch? :("
date: 2010-12-21
forum: Server Platforms
---

### Post by Nunnsby on 2010-12-21
Hi All

I've kinda gone hopelessly lost on my mail server install and now want to start from scratch, after having wasted 4 days on this.

Basically I have a 95% working postfix installation, a probably 100% working dovecot installation, but am not happy with it as a few things aren't working properly, and I don't know what I did! :-(

[LIST]
[*]mail to /var/mail/richard **NOT** /Maildir - being the main one
[/LIST]

But, also the fact that I don't know where I went wrong, and want to understand why everything is now haywire. I am not certain if my security is working on the mail or the logins either.

What I would like to achieve is the following:

[LIST]
[*]Postfix
[*]Dovecot
[*]Virtual Users - using IMAP with Security, allowed to send mail from their client
[*]Virtual Domains
[*]Postfix Admin
[*]Webmail (Roundmail)
[*]Anti-Virus and Spam-filtering
[/LIST]

I started with this guide ([http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) - How to set up a mail server on a GNU / Linux system), which seems very, very good I might add, but it is for Courier, and when I bumbled along with the Dovecot equivalent ... that is where things broke. :(

So, now, I want to start from scratch.

Any easy ways to clear the settings I have applied so far? Do I remove or reinstall packages? Delete main.cf/master.cf/dovecot.conf?

Any advice would be appreciated!

Regards

Nunnsby

---

### Post by windependence on 2010-12-21
[http://www.zimbra.com/downloads/os-downloads.html](http://www.zimbra.com/downloads/os-downloads.html)
 
[http://www.citadel.org/doku.php/start](http://www.citadel.org/doku.php/start)
 
Much easier, much more secure, much faster to set up.
 
-Tim

---

### Post by stmiller on 2010-12-21
```
sudo apt-get remove --purge postfix
```

Doing the --purge removes all traces of a package, including config files and everything.

---

### Post by elico on 2010-12-24
well i recommend that you will understand the concepts of the programs POSTFIX and DOVECOT and then move on to other stuff.
i used this nice and amazing thing
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)
it has a lot of stuff that really good but only one line of the settings is missing and that is the reason it wont work but just for an overview its good. (dont copy and paste the code... write it manualy)


this [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)
ubuntu manual is like one of the best!!

it's goint step by step.

about the purging thing... my suggestion is that you will save any current settings you have.

---

### Post by pricetech on 2010-12-24
Easiest way to erase your changes and start fresh is to restore the backup you made of the original file before you started editing.

---

### Post by HermanAB on 2010-12-24
Howdy,

Once you are totally fed-up, you can install Citadel.  

The Easy Install script takes about 20 minutes and then it Just Works (TM).  Easy Install will also remove Postfix for you so don't worry about a conflict:
[http://citadel.org](http://citadel.org)

Look for Download and Easy Install.

---

