---
title: "Sendmail Configuration"
date: 2013-05-14
forum: Server Platforms
---

### Post by VorlonShadow on 2013-05-14
Our primary email server is MailEnable on a Windows server.  We have a customer who periodically sends out a mass email of 15,000 or so to it's members.  This drags our current email server down to a crawl and no one can get anything through until that mass email is finished. Therefore I installed a new VM with Ubuntu Server and installed SendMail.  I created an asp.net function on the primary Windows server to test this.  This works when I'm going to an outside domain (gmail.com, aol.com, yahoo.com, etc).  However, if I'm going to the domain for which I am sending (for instance, if my domain is mydomain.com and I'm sending to [email]jesse@mydomain.com[/email]) the emails through I get the error "MX list for mydomain.com points back to mail.mydomain.com"  From what I've read it says to put the domain in the /etc/mail/local-host-names file, which I tried.  The problem if I do this is that this is not really the primary email server so if I do this I then get an error, "user unknown".  Does anyone know how I should configure SendMail so that any emails sent through to "mydomain.com" go to the right email server?

Hope I've explained that well.

Thanks,
Jesse

---

### Post by SeijiSensei on 2013-05-15
Do you want the mail for your domain to be delivered to this server or to the Windows one?  I'm guessing the latter.

If you have an internal DNS server, make sure the MX record for your domain points to the Windows server.  That is the primary method that sendmail (and all other SMTP exchangers) uses to determine where to route messages.  If you have DNS server, but did not configure an MX record for your domain, do that now.  Make sure the Linux box is configured to use that DNS server in /etc/resolv.conf.  Remove the entry from /etc/mail/local-host-names, restart sendmail, and try again.  Now mail for your domain should flow directly to the Windows server.

If you do not have an internal DNS server, then you need to set up a mailertable.

Now the last time I looked at Ubuntu server it does not include the appropriate configurations for a mailertable by default.  (RedHat and its derivatives include all these configurations.)  You will probably have to regenerate sendmail.cf by adding directives to sendmail.mc as I described in [this post]("http://ubuntuforums.org/showthread.php?t=2094739&p=12404961&viewfull=1#post12404961").  Personally if it were me, I'd just install [CentOS 6]("http://www.centos.org/") and have it all be there for me out-of-the-box.

Once you have the ability to use a mailertable, you can use it to solve your problem like this.  First, create a file (as root) called /etc/mail/mailertable and put this line in it:
```
example.com       relay:[mail.example.com]
```
replacing "example.com" with your domain and "mail.example.com" with the hostname (or IP address) of the Windows server.

Next run this command:
```

cd /etc/mail
sudo makemap hash mailertable < maileratable

```
That reads the file you created and converts it to a db4 database.  Remove any references to your domain from /etc/mail/local-host-names.  Now restart sendmail.  You should see the server send mail for example.com to the Windows box, and mail for anywhere else out to the Internet.

---

