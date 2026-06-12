---
title: "Need help installing a good SMTP server on Ubuntu"
date: 2012-12-06
forum: Server Platforms
---

### Post by gcis2012 on 2012-12-06
Hi there

We just installed a fresh new version of Ubuntu 12.04.1 LTS server edition and we need to install and configure a SMTP server with a graphical user interface that will authenticate SMTP service on port 587.

We've tried installing iRedMail several times but keep getting all kinds of error messages.

Do you guys know of anything that is easy to use and that works?

We need to have this thing going ASAP. Any help will be greatly appreciated.

Thank you

---

### Post by SlugSlug on 2012-12-06
I use postfix. It's not very graphical you get a few options during install. But google is full of the config settings & you will find a lot of info on here :)

---

### Post by SeijiSensei on 2012-12-06
I've only used [Webmin]("http://www.webmin.com") on RedHat-flavored platforms, but it offers a web-based front-end for most standard SMTP servers.  

[Installation](http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html)

---

### Post by darkod on 2012-12-06
It depends what you expect from the GUI.
The most common option seems to be postfix as smtp server and dovecot for pop3/imap access. Recently I did a quick test in VBox and without any mailserver experience it worked right away, just with installing them. The only change I did was to use Maildir and not mbox.

If you plan not to limit mailbox size, and other settings, it's probably much easier to setup postfix + dovecot without any GUI. You will only need to create each user/mailbox when you need a new user, but that's easily done from the CLI in ubuntu server.

If on the other hand you need/expect much more configuration options and are not comfortable with the CLI, I guess a non-GUI solution might not work for you.

---

### Post by SeijiSensei on 2012-12-06
The default configuration only supports connections via localhost for security reasons, so right away if you're running a server on a LAN, you need to change that.  You'll also need to change some other security settings, tell Postfix the name of the domain(s) for which mail is to be accepted, and so forth.  That would be true if you use sendmail as well.

The only reason I can see for having a GUI on a Linux mail server is to handle adding users.  But then you can simply install a desktop environment on the server and use its native user management application for that task. Once the server software is configured you pretty much never need to touch it again.

Here is the Ubuntu Postfix documentation: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
The Ubuntu Server Guide might also prove useful: [https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

However there is one large issue that the OP needs to address:  scanning for viruses and spam.  In an office setting you simply must have these protections in place because most users are untrustworthy when it comes to things like clicking on random attachments or believing the authenticity of mail.  

For this task I strongly recommend [MailScanner]("http://www.mailscanner.info/"), which is a single application that integrates an SMTP server like sendmail or Postfix with virus scanning and spam scanning using [SpamAssassin]("http://spamassassin.apache.org/"). For virus scanning I use the open-source [ClamAV]("http://www.clamav.net/"), but MailScanner supports commercial antivirus scanners as well. Webmin has some MailScanner tools, though I would suggest doing the initial configuration in a text editor.  MailScanner has a *lot* of options that make it incredibly flexible but a bit daunting at first.

---

### Post by SlugSlug on 2012-12-06
> **SeijiSensei said:**
> For this task I strongly recommend [MailScanner]("http://www.mailscanner.info/"), which is a single application that integrates an SMTP server like sendmail or Postfix with virus scanning and spam scanning using [SpamAssassin]("http://spamassassin.apache.org/"). For virus scanning I use the open-source [ClamAV]("http://www.clamav.net/"), but MailScanner supports commercial antivirus scanners as well. Webmin has some MailScanner tools, though I would suggest doing the initial configuration in a text editor.  MailScanner has a *lot* of options that make it incredibly flexible but a bit daunting at first.


Sorry to sound dumb - but what does this do? I use clam to scan emails, I've not yet had an issue with spam but plan to use SpamAssassin when I do.

So just wondering why you pick this over just installing the two? Does it have some form or console you can use or something?

---

### Post by SeijiSensei on 2012-12-06
MailScanner is a completely integrated solution that manages the entire task of scanning mail. It provides enormous flexibility in terms of notifications, whitelists, blacklists, archiving, and many other tasks.  You can have different levels of spam rejection and allow dubious messages to be delivered with a tag in the Subject line while disposing of obvious spams.  MailScanner also includes an add-on that lets you write rules to handle outbound messages.  I used that recently at a medical provider to insure that outbound mail doesn't contain "personal health information" whose transmission in unencrypted email constitutes a violation of the Federal law known as HIPAA.

The other useful tool for any mail administrator is [procmail]("http://www.procmail.org/"), which replaces the standard "mail delivery agent."  Procmail enables you to write "recipes" that can massage messages depending on their content and even pipe them to scripts and commands for further processing.  You can have recipes that apply to individual users and ones that apply system-wide.

---

### Post by SlugSlug on 2012-12-07
Thanks [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"), I'll come back to this when the time comes :)

---

### Post by lisati on 2012-12-07
*Thread moved to **Server Platforms**.*
I use Postfix/amavisnew/spamassasin/clamav, with a handful of custom written policy filters.

---

### Post by sixfootseven on 2012-12-07
I'm new to Linux servers and new to these forums... this is my first post.

I have installed Ubuntu 12.04 and happily using Postfix and Dovecot.

Webmin is an amazingly good and easy option for graphical admin, and is a web app so doesn't need a GUI on the server.

I documented my progress so far... check out [http://www.geekzone.co.nz/TonyHughes/8273](http://www.geekzone.co.nz/TonyHughes/8273)

---

### Post by sandyd on 2012-12-07
I am using Axigen right now. Its for corperate providers, so it might be a bit too fiddly (it requires adjustment just to allow sending emails to addresses that aren't hosted by it), but is extremely secure.

---

