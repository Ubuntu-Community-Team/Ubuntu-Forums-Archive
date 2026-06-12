---
title: "Mail Server questions"
date: 2009-07-20
forum: Server Platforms
---

### Post by M4verick on 2009-07-20
So I had some questions. I'm working on a personal mail server for virtual domains and used the walkthrough listed here - 
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

But I noticed that I couldn't e-mail outside of the domain from the addresses on the inside, which errors out and gives me "relay access denied". I was wondering what it would take to change it so that I could send mail outside of the domain, yet keep it authenticated so that it's not just open for anyone. Thanks for any replies.

---

### Post by HermanAB on 2009-07-20
If you want to run a real mail server, then you have to have a domain name and a proper DNS with a static IP address, A, PTR and MX records.

Otherwise, you have use your ISP mail server as a 'smart host' or 'relay host' and slave your mail server to theirs.

---

### Post by M4verick on 2009-07-20
I actually do have an FQDN & a DNS server hosted by everydns.net. My ISP has the PTR record already bound to my static IP address. A, CNAME, & MX records are already in place and confirmed working. I can receive mail from other domains, I just can't send out side of my domain. I just don't have any experience trying to host a mail server on linux. I'm much more fluent with Windows...But then again, I don't really feel that Windows is such a challenge considering there's a GUI for everything...

---

### Post by HermanAB on 2009-07-21
So what mail server are you using? Sendmail, Postfix, Qmail, Zimbra, Citadel...

Whatever it is, the thing to do is to go to the project web site and start reading.  Look for information on the log files.  Check the logs to see what the server is complaining about. Then plug the error message into [http://www.google/linux](http://www.google/linux). It is usually pretty basic stuff.

If you want a Linux server with a GUI for everything, then you should either install Webmin, Usermin and Virtualmin, or switch to Suse or Mandriva.  Mandriva is easier to configure than Windows servers.  However, if you want to learn how things really work, then Ubuntu is fine - it will force you to learn!

---

### Post by M4verick on 2009-07-21
It's using Postfix with Dovecot for Pop/IMAP. I wasn't aware of google.com/linux, so thank you for that. And no, I'd like to move away from GUI's as I don't think they're really all that practical for a server if you can do everything from command line. I have no problem with learning. Just needed a point in the right direction. So thank you.

---

