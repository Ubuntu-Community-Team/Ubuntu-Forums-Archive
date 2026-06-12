---
title: "Amavisd &amp; SpamAssassin doesn't work - Ubuntu Server 12.04LTS"
date: 2012-12-12
forum: Server Platforms
---

### Post by SteveCena on 2012-12-12
I'm looking to replace a RedHat EL 5.x Postfix server with an Ubuntu 12.04LTS one. In my test environment, I currently have an Ubuntu Server 12.04LTS (32bit)with Postfix running. I've followed this guide: [https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew) on getting ClamAV and SpamAssassin integrated.

ClamAV works perfectly. I can see in the logs (and email header) that the scanning is taking place. However, I cannot get SpamAssassin to function. If I use the console prompt and run, say, spamassassin -t < sample-spam.txt I can verify SpamAssassin works. However, if I send emails back and forth through Postfix, no SpamAssassin headers are added. I've even tried lowering the spam score (in the guide) to -999 and I still don't get anything.

If I run SpamAssassin itself as a content_filter for Postfix, it works correctly.

Is there a more recent guide for SpamAssassin/Amavis? What am I overlooking?

---

### Post by SteveCena on 2012-12-12
Oh one other thing I should note: Currectly, all the virtual machines are virtualized inside of VirtualBox from Oracle version 4.2.4 on Windows 7 64bit. I use that for testing. Production will be VMWare ESX Ver 5.x.

---

### Post by SeijiSensei on 2012-12-12
> **SteveCena said:**
> If I run SpamAssassin itself as a content_filter for Postfix, it works correctly.

Is that not an acceptable solution?

I believe that RedHat systems uses a procmail rule that passes each message to spamd for processing.  Ubuntu by default does not come with procmail installed (seems dumb to me, too), but you can install it from the repositories with "sudo apt-get install procmail".  Then create /etc/procmailrc and add this "recipe":
```

:0: fw
* < 256000
| /usr/bin/spamc

```

This passes every message less than 256000 bytes to spamc for checking against the spamd daemon.

I run [MailScanner]("http://www.mailscanner.info/") which does both virus and spam scanning at the SMTP level.  It works flawlessly on RedHat-flavored systems like CentOS.  I haven't tried the Ubuntu implementation, but it is in the repositories.

---

### Post by SteveCena on 2012-12-12
It is and it isn't. I am also trying to get MailScanner running as well (I bought the official book on MailScanner). It, as well as almost every other guide I've read, recommends using amavisd as the "service broker" for all of it (clamav, spamassassin, mailscanner). The other reason I'd prefer amavis is I have the option of running the scanning services as a physically separate machine.

It's odd to me that clamav runs great but not spamassassin. I'm also checking the mail log to see if perchance it's doing the scan and just not putting the headers in. I'm not seeing anything in the log that looks like its spam scanning. Virus, yes but not spam.

I can post logs if that will help.

Is it in the Ubuntu repositories? I'm running 12.04LTS and I don't see it listed. I do recall seeing it under earlier versions of Ubuntu but just assumed that it had been removed from the repos.

---

### Post by SeijiSensei on 2012-12-12
I've never used amavisd at all, and I've never read anything by Julian that suggests it should play a role.  I use sendmail rather than Postfix, though that should not really matter.  As I say, installing the RPM-based version that is available on the MailScanner site "just works" on any CentOS 5/6 machine I've built.  One reason I choose to use CentOS for servers is that MailScanner installs and works flawlessly on that platform.

You can have a separate scanning machine if you run clamd and spamd on it, and have the mail processor query them.  

Are you running SpamAssassin at the SMTP level, or at the delivery level with spamd?  As I said, the latter requires procmail.

---

### Post by SteveCena on 2012-12-12
You should definitely check out Postfix. I much prefer it to sendmail. I'm not against sendmail, but found Postfix to be easier to work with and more power. Ultimately, its what you feel comfortable with so take it with a grain of salt :)

I just checked the book, and I could be overthinking it. The book says to install SpamAssassin and a mail server but it doesn't specifically say it needs amavisd. I might be able to use amavisd for antiviral and mailscanner/spamassassin for the content filtration.

I've tried getting SpamAssassin/etc on CENT and was too much of a hassle. Needed to install RPMForge packages, etc. and still didn't get very far. Just an email server, that worked right out of the box as I expected.

Again, its what you feel comfortable with. I'm glad it worked out  for you but I want to see if I can pull with off with Ubuntu.

---

### Post by SteveCena on 2012-12-12
Actually, it looks like it is a moot point right now. Ubuntu has "renamed" the SHA1 library that the .DEB of MailScanner uses. So now, it's a stand off. Ubuntu has it as a bug they won't fix. They are pinning the change on the software developers to make the change.

I'm going to check out Debian and make another attempt at CENTOS again. I could use the server for Postfix & AV, but I really want the MailScanner antispam.

---

### Post by R_Lopez on 2013-03-04
> **SteveCena said:**
> Actually, it looks like it is a moot point right now. Ubuntu has "renamed" the SHA1 library that the .DEB of MailScanner uses. So now, it's a stand off. Ubuntu has it as a bug they won't fix. They are pinning the change on the software developers to make the change.

I'm going to check out Debian and make another attempt at CENTOS again. I could use the server for Postfix & AV, but I really want the MailScanner antispam.

I found your statement in an earlier post to this thread, "It, as well as almost every other guide I've read, recommends using amavisd as the "service broker" for all of it (clamav, spamassassin, mailscanner). " very interesting.

I am very happy running Postfix and MailScanner together. One of the side affects of having postfix put email in it's hold queue where MailScanner picks it up and when MS is finished placing it back into the Postfix incoming queue is the use of two postfix queueid. There ends up being only one "postfix/smtp" log record with delay times. It is only for the second processing of the email associated with the second queueid. [The other side affect is writing anything about MailScanner to a Postfix email list.]

I have sometimes thought if amaviz or something similar could be used to interface MailScanner to Postfix there could be only one postfix queueid and the logged times would be correct.  What has stopped me from giving it a try is the fact MailScanner "expects" the email to be re-inserted to Postfix and produces a handy log record which writes both queueid to a single record which makes log file continuity across both of them possible.

The above aside, if you have not yet gone off in another direction and still want to use MailScanner, please look at  http://apt.baruwa.org because it is a clean installation of MailScanner ("This repo provides Baruwa deb packages for Ubuntu and Debian, supporting packages such as mailscanner are also included in the repo").  I am currently using that on a test email gateway and so far I have found it solid.

Robert Lopez

---

### Post by SteveCena on 2013-03-05
I gave up on it. We've decided to go with Untangle to deal with spam. It's working out very well. The only think I don't like about it is there is no way to retrain the server with known good mail. Outside of that, it's worked very well for us.

---

### Post by R_Lopez on 2013-03-05
> **SteveCena said:**
> I gave up on it. We've decided to go with Untangle to deal with spam. It's working out very well. The only think I don't like about it is there is no way to retrain the server with known good mail. Outside of that, it's worked very well for us.

Thanks for the update. Best wishes with Untangle. This is the first I have read of it. I hope it serves you well.

---

### Post by SteveCena on 2013-03-05
R_Lopez: Thanks. The only thing I dislike about Untangle is its essentially a packet sniffing solution. It sits in between your mail server and the network as a bridge. Outside of that, it's performed very very well.

If I could get MailScanner actually WORKING I'd be happy to use that. At least then I can set up a mailbox for SpamAssassin to grab ham from to learn to recognize good email.

It's one of the biggest problems I have with a Linux based solution for anything. I'm all for open source, and I love Linux but if I can't get a product to install or function it doesn't matter how good that product is.

---

### Post by SeijiSensei on 2013-03-05
Have you, in fact, tried installing MailScanner on a CentOS 6.x machine?  As I said before, the [package]("http://www.mailscanner.info/files/4/rpm/MailScanner-4.84.5-3.rpm.tar.gz") that Julian provides on the MailScanner site installs everything you need with little or no work on your part.  You'd need to edit MailScanner.conf, of course, but most of the defaults are reasonable.  He also offers a [package]("http://www.mailscanner.info/files/4/install-Clam-SA-latest.tar.gz") that includes both ClamAV and SpamAssassin, but I just use the standard CentOS RPMs for those. For [ClamAV]("http://pkgs.repoforge.org/clamav/") you should add the [Repoforge]("http://repoforge.org/") (formerly RPMForge) repository.

---

### Post by SteveCena on 2013-03-06
[B][COLOR=#000000][SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"): Yes. I did. It didn't work. I got Postfix installed, and MailScanner. The virus scanning worked perfectly. Spam scanning didn't. It simply would not write the email headers into any of the mail for any spam checks, default or otherwise. CENT OS 5.9 with MailScanner. I even went to MailScanners IRC channel & everyone there was completely baffled. Posted all my configs, etc & nobody could figure out why the headers weren't getting written. So I gave up on it. 

If I *could* get it working on *something* I'd be willing to try it but I spent about two weeks tinkering with it but I chose to cut my losses & go with a pre-packaged/paid solution.[/COLOR][/B][COLOR=#000000][/COLOR]

---

