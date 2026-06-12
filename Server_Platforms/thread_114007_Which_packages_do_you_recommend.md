---
title: "Which packages do you recommend?"
date: 2006-01-07
forum: Server Platforms
---

### Post by RichSPK on 2006-01-07
I used to run web, FTP, and mail servers using Sambar Server software under Windows.  When my hard drive died I let those services revert to my ISP.  I want the services under my control again, and this time I want to try it with Linux, so I've just completed an install of Ubuntu 5.10, Breezy Badger.  I chose all the default settings, where applicable, during the installation process, so I've got the full Gnome GUI.

I want to run web (including SSL...or is that SSH?), FTP, and mail (IMAP plus web interface) servers.  I want to use the packages that are most often used with Ubuntu so that troubleshooting in the future will be as easy as possible.  Which packages do you recommend?

I've heard that Apache2 is needlessly complicated relative to Apache, but I don't see Apache listed in Synaptic.  Should I just use Apache2?  Does either flavor of Apache include an FTP server?  The biggest question for me is about the mail server because it's not clear to me which mail servers include IMAP or just provide POP3, or even which ones are just fetchers/forwarders and not really servers.

Thanks for your help!

---

### Post by RichSPK on 2006-01-07
I should note that this server isn't for some mission critical business.  I'll be the only user, for the most part, although I may create accounts for friends and family.

---

### Post by Soleil-Raid on 2006-01-08
[QUOTE=RichSPK]
I want to run web (including SSL...or is that SSH?), FTP, and mail (IMAP plus web interface) servers.  I want to use the packages that are most often used with Ubuntu so that troubleshooting in the future will be as easy as possible.  Which packages do you recommend?

I've heard that Apache2 is needlessly complicated relative to Apache, but I don't see Apache listed in Synaptic.  Should I just use Apache2?  Does either flavor of Apache include an FTP server?  The biggest question for me is about the mail server because it's not clear to me which mail servers include IMAP or just provide POP3, or even which ones are just fetchers/forwarders and not really servers.
[/QUOTE]

I'd go with Apache2, it's ever so slightly more complicated, but nothing you'd really notice.

Apache/2 doesn't include an ftp server. If you're running ssh, you get sftp/scp into the bargin, and it's probably easier to just use that.

For email you need an MTA (Mail Transfer Agent accepts incoming mail, stores it on disk and transfer outgoing mail to other SMTP servers), also often known as an SMTP server. I think by default Ubuntu ships with Postfix. I personally like Exim, but that's just because it's what I know.

There's also sendmail, but that's really best avoided unless you have to use it for legacy reasons. Chances are good that you don't.

For picking up your mail, I'm a big fan of Courier-imap/pop3. Apart from some well documented changes to the MTA config, it pretty much 'just works'. Courier also has it's own MTA, although I've never used it.

---

### Post by dustyculler on 2006-01-08
I've had good luck with vsftpd in the past for ftp.  User names and passwords are transmitted in the clear with ftp so that may be a concern.  I believe there are ftp servers that support tls for secure ftp, but I don't have any experience there.

I'm no expert on apache, but didn't find apache2 very difficult to get working for what I needed it to do.  You will need to either purchase an ssl certificate or create your own (browsers will complain that the certificate doesn't come from a trusted certificate authority if you create your own) to get https working using ssl.

I'm currently running postfix for smtp, courier for imap (I don't use pop3, but I believe courier also does pop3), sasl for smtp authentication, clamav for virus scanning, and spamassasin for spam filtering and I can say that that combination has worked well for me.  It did take quite a bit of time to learn about all of those packages and get them all configured correctly.  The last thing you want is to be an open relay and have your system used by spammers.

I've only read bits and peices, but I would recommend that you pick up a copy of [The Book of Postfix]("http://www.postfix-book.com/").  That would likely save you the hours of on-line research I went through.

Hope that helps.

---

### Post by dustyculler on 2006-01-08
I'd have to agree with Soleil-Raid in that ssh would be a better.  If you have users connecting from windows systems, winscp is a great application that works similar to an ftp client, but with better security.

---

### Post by RichSPK on 2006-01-08
Thanks for the help!  It sounds like you're saying that Courier is a fetcher.  If I'm running my own mailserver/MTA then I shouldn't need Courier, but I'll go take a look at it and see if I'm mistaken.

---

### Post by RichSPK on 2006-01-08
Okay, getting Apache2 up and running was thoroughly painless.  I'm having trouble configuring postfix.  I ended up installing Courier-IMAP, even though I'm not sure I need it.  I'll post about my postfix troubles in a separate thread.

Thanks again!

*edit*: Well, it wasn't painless.  The server I was using under Windows had a software RAID 1 array that crashed.  It was an Athlon XP 1800+ with two Seagate 120 or 160GB (I forget the capacity) SATA drives, and I thought one of the drives was still okay.  I intended to use an older, slower Athlon 850MHz system as my new server because it's quieter, but the DVD-ROM drive in it ended up being flaky, so I went back to the XP 1800+ system with one good drive.  That "good" drive started making some odd noises and then the computer stopped responding to input.  I'm beginning to suspect the motherboard SATA controller rather than the drives, but we'll see.  Anyway, I swapped out the DVD-ROM drive in the older computer for an old CD-ROM drive I had lying around, installed Ubuntu on that system, and it seems stable so far.

---

### Post by Soleil-Raid on 2006-01-09
[QUOTE=RichSPK]Thanks for the help!  It sounds like you're saying that Courier is a fetcher.  If I'm running my own mailserver/MTA then I shouldn't need Courier, but I'll go take a look at it and see if I'm mistaken.[/QUOTE]

Ah - I think you're thinking of fetchmail. 
Courier-IMAP in this case lets you access your mail folders from any PC. Courier-POP does the same thing, except using the pop3 protocol. Unless you plan on only using terminal access, you'll want one of them.

---

### Post by RichSPK on 2006-01-09
I think I get it now.  It started to make more sense when I telneted to the IMAP port (143?) and saw Courier-IMAP in the response.  I guess I do need it.  I may have to install Courier-POP, too, but I'm more interested in getting IMAP working right now.

---

