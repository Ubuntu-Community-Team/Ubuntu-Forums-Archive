---
title: "Personal Email Server"
date: 2008-04-30
forum: Server Platforms
---

### Post by SuperCzar on 2008-04-30
I want to setup a personal email server.

I recently got a small VPS and want to set it up with a custom apache install and get rid of my shared hosting that currently hosts my email. 

However, I am having a hell of a time with the email portion.

I've tried every howto in the book, "the perfect server", everything I can search out here in the forums, and whatever else, but I cannot seem to find the solution.

The perfect server seems to much for me.

I basically only need the server to host about 2 accounts and on a single domain. I will be hosting multiple domains on the server, but only one needs email access. 

I have the server DNSed as domain1.
I have another domain pointed to it for testing, domain2.
eventually I will move over domain3 and domain4 but for now I need to keep them live and running.

In the end the server will be domain1, thats largely all domain1 will be used for.

Domains 2, 3, and 4 will be web served, and domain3 will have email access.

I'm sorry for the confusion, but can anyone point me in the right direction for simple IMAP and SMTP access? So far I know I'll need Postfix and Courier or Cyrus or Dovecot and SASL authentication, but configs are eluding me.

---

### Post by bluefrog on 2008-04-30
What can do more can do less.

howtoforge.com has all the howtos wanted to set up anything.

Their perfect server howto are just quite easy to follow (copy/paste basically) and will give you what you want in no time.

James Dupin

---

### Post by windependence on 2008-04-30
Try Zimbra. They have an open source implementation that does almost everything the pay version does. Runs on Ubuntu also. [http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

Best way to do it would be to run it in a virtual machine on Vmware. Use Vmware server (free) and you can run 3 or 4 machines on one. There is even a  Vmware appliance that is preconfigured and ready to go, all free as in beer.

-Tim

---

### Post by SuperCzar on 2008-04-30
> **bluefrog said:**
> What can do more can do less.

howtoforge.com has all the howtos wanted to set up anything.

Their perfect server howto are just quite easy to follow (copy/paste basically) and will give you what you want in no time.

James Dupin

Your idiom does ring true, however, I have gone through the tutorials, and get to the end, at which point. I have an unconfigured server that does not seem to accept any settings, or respond to connections from the outside world.

It just appears to me that the added complexity of a server configured to host reseller accounts is probably adding more effort than is required.

If that is not the case, than I will continue to work at that solution.

---

### Post by SuperCzar on 2008-04-30
> **windependence said:**
> Try Zimbra. They have an open source implementation that does almost everything the pay version does. Runs on Ubuntu also. [http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

Best way to do it would be to run it in a virtual machine on Vmware. Use Vmware server (free) and you can run 3 or 4 machines on one. There is even a  Vmware appliance that is preconfigured and ready to go, all free as in beer.

-Tim

I am hoping to run this under a smallish VPS.

I don't think virtualizing with VMWare on a Xen virtualized machine is going to work well.

---

### Post by SuperCzar on 2008-05-01
OK I followed the tutorial here:
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

on a virgin 7.10 system.  It seemed much more aligned to what I wanted... and will allow me to manage it manually.

I am having two issues. I can telnet into my SMTP server locally, but cannot reach it with thunderbird or telnet externally.

Also my IMAP server is having an issue, Thunderbird is telling me that I cannot login, but I am getting this error:
```
May  2 00:26:19 thirdrate imapd: Connection, ip=[::ffff:17.221.46.138]
May  2 00:26:24 thirdrate imapd: chdir domain.tld/admin/: No such file or directory

```

But the folder /var/spool/mail/domain.tld/admin exists.

---

### Post by SuperCzar on 2008-05-01
OK, well I reduced the issue to courier, and checked the /home/vmail folder that the howto had setup for mail.

However, there was no domain.tld/admin folder to be found. I created the folder and now do not see an error in /var/log/mail.log

but thunderbird is telling me that the server responded "Unable to open this mailbox..."

---

### Post by ginjabunny on 2008-05-01
if you are using Dovecot, I think by default it doesn't allow plain text passwords, there is an option to allow it in the conf file

---

