---
title: "Postfix - subdomain / A Record"
date: 2010-03-06
forum: Server Platforms
---

### Post by mrcool10 on 2010-03-06
Basic setup:

Domain (icynemo.us) points to shared hosting that I've had for years.
Subdomain (v.icynemo.us) is an A Record pointing to the IP of my VPS host. 

I've installed and configured Postfix to the point that I can send and receive mail using Webmin on my VPS. However, I can't get it to work in an external app - ie Thunderbird. I use v.icynemo.us for the POP/IMAP and SMTP. Thunderbird does it's thing, then POP/IMAP shows up as properly configured, but SMTP never has. However, even when Thunderbird says POP/IMAP is configured right, I haven't been able to receive email. That doesn't really matter, though, because basically all I need is to be able to *send* mail. 

My sister has a mailing list and shared hosting throttles email to the point that it is a pain. I don't care if I use Postfix or anything else. I'm thinking the A Record and/or MX entries (do I even have any?) is what's throwing me off but I don't know what to do about it. BIND DNS is a mystery to me. 

Thanks much.

---

### Post by Bachstelze on 2010-03-06
By default, Postfix does not allow other systems to send email through it (you don't want just anyone to be able to send email through your server). If you are going to allow other poeple to send email using your server, you must configure some kind of authentication:

[https://help.ubuntu.com/community/Postfix#Authentication](https://help.ubuntu.com/community/Postfix#Authentication)

As for POP/IMAP, this is not what Postfix is for. You need to also install a POP/IMAP server like Dovecot or Courier.

---

### Post by mrcool10 on 2010-03-06
Thanks for the reply. I do have Dovecot and auth set up. I am able to telnet localhost to pop3, imap2, and 25. Here is the ehlo output for 25:

[I]250-v
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH CRAM-MD5 NTLM LOGIN PLAIN DIGEST-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
[/I]
All I want to be able to do is to send mail via SMTP for a mailing list, and I'm using Thunderbird to test the SMTP settings. So far, no go. I'm using v.icynemo.us - do I need to use smtp.v.icynemo.us? If so, how do I set that up? I can add another A Record on the shared host, but it won't resolve correctly. I'm assuming I need to add some DNS settings but I'm not how if or how.

---

### Post by Bachstelze on 2010-03-06
What happens when you try to send an email?

---

### Post by dasunsrule32 on 2010-03-06
> **mrcool10 said:**
> Basic setup:

Domain (icynemo.us) points to shared hosting that I've had for years.
Subdomain (v.icynemo.us) is an A Record pointing to the IP of my VPS host. 

I've installed and configured Postfix to the point that I can send and receive mail using Webmin on my VPS. However, I can't get it to work in an external app - ie Thunderbird. I use v.icynemo.us for the POP/IMAP and SMTP. Thunderbird does it's thing, then POP/IMAP shows up as properly configured, but SMTP never has. However, even when Thunderbird says POP/IMAP is configured right, I haven't been able to receive email. That doesn't really matter, though, because basically all I need is to be able to *send* mail. 

My sister has a mailing list and shared hosting throttles email to the point that it is a pain. I don't care if I use Postfix or anything else. I'm thinking the A Record and/or MX entries (do I even have any?) is what's throwing me off but I don't know what to do about it. BIND DNS is a mystery to me. 

Thanks much.

Try my how-to, I had a lot of similar problems that you are having. Follow it and you should be golden.

[Link]("http://www.christiantechsaz.com/viewtopic.php?id=58")

Good Luck!

---

### Post by mrcool10 on 2010-03-07
Ok I've dropped v.icynemo.us (for now) and am accessing the SMTP server via the IP address.

When I would access v.icynemo.us I would get hostmonster stuff - that's the shared host, not the VPS.

This is what I'm getting now, sending from v.icynemo.us to icynemo.us:[INDENT]```
**SMTP Connection:**

            OK, connected to 204.12.227.91...
< 220 v.icynemo.us ESMTP Postfix (Ubuntu)
> HELO edit.dnsvr.com
< 250 v.icynemo.us
> MAIL FROM:<sasha@v.icynemo.us>
< 250 2.1.0 Ok
> RCPT TO:<sasha@icynemo.us>
< 554 5.7.1 <sasha@icynemo.us>: Relay access denied
```[/INDENT]Using this tool: [http://zoneedit.com/smtp.html](http://zoneedit.com/smtp.html)

And from v.icynemo.us to v.icynemo.us:```
[INDENT]      **SMTP Connection:**

            OK, connected to 204.12.227.91...
< 220 v.icynemo.us ESMTP Postfix (Ubuntu)
> HELO edit.dnsvr.com
< 250 v.icynemo.us
> MAIL FROM:<sasha@v.icynemo.us>
< 250 2.1.0 Ok
> RCPT TO:<root@v.icynemo.us>
< 250 2.1.5 Ok
> DATA
< 354 End data with <CR><LF>.<CR><LF>
> From: sasha@v.icynemo.us
> To: root@v.icynemo.us
> Subject: ZoneEdit Automated SMTP Test (204.12.227.91)
> 
> If you received this, then the mail server (204.12.227.91) is probably working.
> Sent at 2010-03-07 01:16:55 by 72.198.79.238 using Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2) Gecko/20100115 Firefox/3.6
> .[/INDENT]
```[INDENT]< 250 2.0.0 Ok: queued as 9FB61E90C1E
           [/INDENT]At least I know I'm accessing the right SMTP server now... (goes back to poking around)

Also, ehlo localhost output for telnet localhost 25:

```
ehlo localhost
250-v.icynemo.us
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
```

---

