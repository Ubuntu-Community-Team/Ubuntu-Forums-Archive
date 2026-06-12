---
title: "Problem with mail"
date: 2018-01-04
forum: Server Platforms
---

### Post by raleigh3 on 2018-01-04
Can not get mail to work. ?
  ```
mail -s "Hello World" andrew7@yahoo.com
test
andy@7:~/Downloads$ sendmail: warning: valid_hostname: numeric hostname: 7
sendmail: fatal: unable to use my own hostname
```

---

### Post by TheFu on 2018-01-04
Do you own a domain name purchased from a registrar?
Did you setup postfix?  Sendmail is for ISPs and high-end experts.  I've been running email servers since the mid 1990s and switched to postfix when it was released. Never looked back.
Did you setup the MX DNS record for your domain?
Does your server have a static, public, IP?

Please post output from:

$ postconf -n

---

### Post by raleigh3 on 2018-01-04
Ever since I install mail-utils, I have all kinds of problems.

I uninstalled it with no luck. I need this problem fixed.
```

E: postfix: subprocess installed post-installation script returned error exit status 1

bc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 postfix
 mailutils
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by howefield on 2018-01-04
Thread moved to the "*Server Platforms*" forum.

---

### Post by raleigh3 on 2018-01-04
> **TheFu said:**
> Do you own a domain name purchased from a registrar?
Did you setup postfix?  Sendmail is for ISPs and high-end experts.  I've been running email servers since the mid 1990s and switched to postfix when it was released. Never looked back.
Did you setup the MX DNS record for your domain?
Does your server have a static, public, IP?

Please post output from:

$ postconf -n

I was just trying to send email from a terminal.

andy@7:~/Downloads$ postconf -n 
postconf: warning: valid_hostname: numeric hostname: 7
postconf: fatal: unable to use my own hostname

---

### Post by TheFu on 2018-01-04
It appears that postfix, the default MTA for Ubuntu, isn't configured.

I'm assuming that this never worked. Can't tell from what has been written.

If the pre-requisites aren't in place, then configuring the MTA without a plan to get around the anti-spam protections that all email server use to doesn't make sense.  And if the sending system is on a DHCP subnet from an ISP, those emails will be blocked by default.

To send an email from any non-full-client machine on **any** Unix system, there must be a local MTA configured.  postfix is an MTA. There are others, like sendmail, qmail, exim. For any SMTP server to accept email from your desktop using the SMTP protocol without authentication, then it needs to have a full email server configured.

Which is why I asked the questions about owning a domain, having a registrar, and whether MX DNS records were setup.

In the old days, sending email from a desktop was really easy. But since spam became a huge, global, problem, all sorts of addons to limit spam have been added.  But the underlying method that email is send from a Unix system hasn't really changed.  CLI mail programs talk to the local system MTA, then the system MTA contacts the email server for the "TO" address and transfers the email.

If you want to send email bypassing the local MTA, then the program used needs to speak enough SMTP to contact the correct SMTP server(s) for the TO/CC/BCC fields (look those up in DNS by the MX record), then transfer the "data" to each.  I wrote a tiny perl script to do this, so they definitely exist.  But my script will fail to send email to any SMTP servers on the internet. They will block it.  OTOH, it can send email to MY internal email server which can then send email to the world through a gateway.

So ... there are ways around having a fully configured SMTP server on the internet.  I've seen posts where people have configured their SMTP server to either forward all email through their ISP gateway email servers or to a gmail account.  I've never done either, but others have posted instructions for the gmail solution in these forums before.

Sorry I'm not more helpful.

---

### Post by raleigh3 on 2018-01-04
I would like to get my system back to before mail-utils was installed.

It is messing with my update,clean,and remove script.

postconf: warning: valid_hostname: numeric hostname: 7 

postconf: fatal: unable to use my own hostname
Use of uninitialized value $destinations in scalar chomp at /var/lib/dpkg/info/postfix.config line 221.     Use of uninitialized value $_[1] in join or string at /usr/share/perl5/Debconf/Client/ConfModule.pm line 121.
    postconf: warning: valid_hostname: numeric hostname: 7
   postconf: fatal: unable to use my own hostname
   dpkg: error processing package postfix (--configure):
     subprocess installed post-installation script returned error exit status 1
    Processing triggers for libc-bin (2.23-0ubuntu9) ...
    Errors were encountered while processing:
     postfix
    E: Sub-process /usr/bin/dpkg returned an error code (1)
  This is in mail.log
  Jan  3 17:08:02 7 postfix/sendmail[6178]: warning: valid_hostname: numeric hostname: 7
Jan  3 17:08:02 7 postfix/sendmail[6178]: fatal: unable to use my own hostname

I have a clone image, but it's 10 days old. :-(

I guess I am the first to have this problem.

---

### Post by TheFu on 2018-01-04
If you don't help us understand by answering our questions, it is next to impossible to be helpful.

I don't have the mail-utils package installed. 
I don't have the mailutils package installed either. [https://packages.ubuntu.com/xenial/mailutils](https://packages.ubuntu.com/xenial/mailutils)

Perhaps a dumb question, but is the hostname set for the system and for the MTA config file?

---

### Post by raleigh3 on 2018-01-04
I have answered what I know as far as I know.

I do not know if the hostname is set for my system and for the MTA config file.

If you want to recreate my problem, install mailutils and pick whatever it defaults to during installation.

sudo apt install mailutils

---

### Post by raleigh3 on 2018-01-04
I have answered what I know.

---

### Post by raleigh3 on 2018-01-04
Sorry, Please delete this.

---

