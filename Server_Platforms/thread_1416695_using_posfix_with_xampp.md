---
title: "using posfix with xampp"
date: 2010-02-26
forum: Server Platforms
---

### Post by nivosh on 2010-02-26
Hello friends.

I Realy need some help here.
I installed Xampp in order to test some sites locally.
i installed all kinds of forums locally and noticed i havn't received mail to my gmail account when the local installation of the forums finished.

I assumed that i need sendmail so i installed sendmail and noticed that postfix was uninstalled during sendmail installation.

I then loged in my gmail account and checked my junk mail folder and I saw all the mails that the forums sent, so naturally i reinstalled postfix again and noticed that sendmail was uninstalled.

but now I don't recieve ANY mails from my locally installed forums.

how do I configure postfix exactly the way it is configured in a fresh installation of ubuntu?

the local server is just for testing not production.

hope I made my self clear...

thanks

**i am on linux mint 8 which is ubuntu 9.10 with kde 4.3**

---

### Post by noway2 on 2010-02-26
XAMPP is a set of Apache, MySQL, PHP and Perl.  I don't understand how you got postfix installed as part of the process. I am especially surprised that it just worked out of the box.  Normally getting postfix set up as part of an email system is a, shall we say, very involved, task. 

Did you follow a how to or was it a selection during your initial install, or what?  At some point you must have answered some questions to generate configuration files.  What was that step?

---

### Post by cdenley on 2010-02-26
Postfix (and other MTA's) provides the "sendmail" command, so you can only have one MTA installed at a time. Postfix should be fairly simple to configure.
```

sudo dpkg-reconfigure postfix

```

---

### Post by nivosh on 2010-02-26
> **noway2 said:**
> XAMPP is a set of Apache, MySQL, PHP and Perl.  I don't understand how you got postfix installed as part of the process. I am especially surprised that it just worked out of the box.  Normally getting postfix set up as part of an email system is a, shall we say, very involved, task. 

Did you follow a how to or was it a selection during your initial install, or what?  At some point you must have answered some questions to generate configuration files.  What was that step?

ubuntu comes preinstalled with postfix, so i've heard.

I just installed Xampp and later found out that my gmail account recieved the forum emails sent to my address but went to the junk mail.

I havn't configured anything after Xampp install :???::???:

---

### Post by nivosh on 2010-02-26
> **cdenley said:**
> Postfix (and other MTA's) provides the "sendmail" command, so you can only have one MTA installed at a time. Postfix should be fairly simple to configure.
```

sudo dpkg-reconfigure postfix

```

I know the reconfigure command for postfix and gone through it with all the default settings but for no evail.

So there isn't any simple way to use a local server which will send out mails?

---

### Post by cdenley on 2010-02-26
> **nivosh said:**
> ubuntu comes preinstalled with postfix, so i've heard.

I just installed Xampp and later found out that my gmail account recieved the forum emails sent to my address but went to the junk mail.

I havn't configured anything after Xampp install :???::???:

I'm pretty sure ubuntu does not come preinstalled with postfix. It certainly shouldn't. It is an optional component for the server edition installer, I believe, if you select a mail server configuration.

---

### Post by cdenley on 2010-02-26
> **nivosh said:**
> I know the reconfigure command for postfix and gone through it with all the default settings but for no evail.

So there isn't any simple way to use a local server which will send out mails?

If you want to configure postfix to send mail with smtp, then you want to select the "Internet Site" option in the configuration menu. It really is quite simple when you read the configuration menu. The "default setting" is to leave the configuration alone.

---

### Post by nivosh on 2010-02-26
> **cdenley said:**
> If you want to configure postfix to send mail with smtp, then you want to select the "Internet Site" option in the configuration menu. It really is quite simple when you read the configuration menu. The "default setting" is to leave the configuration alone.

I have configurd Postfix with "internet site" as well as all the other configuration options which I choose default.

Still the mail is not getting sent out for some reason.

---

### Post by cdenley on 2010-02-26
> **nivosh said:**
> I have configurd Postfix with "internet site" as well as all the other configuration options which I choose default.

Still the mail is not getting sent out for some reason.

Are you sure google isn't just rejecting it. I think they reject anything that doesn't have a matching PTR record.

```
tail /var/log/mail.log
```

---

### Post by nivosh on 2010-02-27
> **cdenley said:**
> Are you sure google isn't just rejecting it. I think they reject anything that doesn't have a matching PTR record.

```
tail /var/log/mail.log
```

You are probably right.
Here is the mail.log:

```
Feb 27 16:54:43 nivosh-desktop postfix/smtp[4429]: 9558B22295: host gmail-smtp-in.l.google.com[209.85.135.114] said: 421-4.7.0 [84.109.30.177] Our system has detected an unusual amount of 421-4.7.0 unsolicited mail originating from your IP address. To protect our 421-4.7.0 users from spam, mail sent from your IP address has been temporarily 421-4.7.0 blocked. Please visit http://www.google.com/mail/help/bulk_mail.html 421 4.7.0 to review our Bulk Email Senders Guidelines. u9si7180564muf.9 (in reply to end of DATA command)     
```

How can I resolve that?

---

### Post by cdenley on 2010-02-27
> **nivosh said:**
> How can I resolve that?

You read that URL google gave you, then wait for your temporary ban to expire. What kind of e-mails have you been sending? Are there other systems which share your WAN IP? What is this output:
```

host `wget -O - -q http://whatismyip.org/`

```

---

### Post by nivosh on 2010-02-27
> **cdenley said:**
> You read that URL google gave you, then wait for your temporary ban to expire. What kind of e-mails have you been sending? Are there other systems which share your WAN IP? What is this output:
```

host `wget -O - -q http://whatismyip.org/`

```

this is the output:
```
177.30.109.84.in-addr.arpa domain name pointer bzq-84-109-30-177.red.bezeqint.net.

```

I am not sending personal emails, I just need to retrieve my forum install password...

Is there a way to get the emails to a local dir?

---

