---
title: "Do you host your own mail server at home?"
date: 2013-06-07
forum: The Cafe
---

### Post by PartisanEntity on 2013-06-07
As the title says, I am contemplating setting up my own mail server at home. For fun and to learn how it works.

But, how safe is it? How credible is it that this could get hacked or compromised?

For those who host their own mail server, what have your experiences been with security?

Thanks

---

### Post by CharlesA on 2013-06-07
I have a mail server running on my VPS, but it's mostly to provide mail about updates and from my contact form on my website.

As long as you are keeping your software up-to-date and don't have it set up as an open relay, you should be "OK"

---

### Post by markbl on 2013-06-07
I always install a local mail server on my ubuntu installation just so local backup/etc scripts can email me etc. Just "sudo apt-get install exim4-daemon-light" and answer the few configuration questions, mainly just to set your ISP mail server as the smart host. I do the same on all the raspberry pi's, sheevaplug, etc around my house. Although all these can send email to the internet, of course they can not be accessed externally.

---

### Post by Irihapeti on 2013-06-07
I've had a mailserver at home for nearly a year. I use it for testing website features before they go live on the hosting site, and for getting system notifications.

It's set up to work only on the LAN, which is behind a NAT router. In addition, I've set up iptables on the relevant box, though I'm not sure it's actually doing anything that the router isn't. I've never seen any indication of unauthorised access.

---

### Post by SeijiSensei on 2013-06-08
I have CentOS boxes running as mail servers at home, on my virtual server at Linode, and at clients' sites. They all run [MailScanner]("http://www.mailscanner.info/") with sendmail as the SMTP daemon.  I've been running Internet mail servers since the mid-1990s.  On a couple of occasions I accidentally configured things wrongly so my box became an open relay, but that was quite a few years ago now.

From a security perspective, your number one task is to make sure the server only accepts mail for your domain(s) and rejects messages addressed elsewhere.  The site [http://mxtoolbox.com/](http://mxtoolbox.com/) provides some useful tools to check whether your server has been blacklisted as a spam source, test for an open relay, and the like.

---

### Post by prodigy_ on 2013-06-08
Voted "no" though I did have postfix installed in the past. I used it for testing and sending notifications from unattended scripts but ultimately migrated to Gmail.

---

### Post by PartisanEntity on 2013-06-08
> **SeijiSensei said:**
> I have CentOS boxes running as mail servers at home, on my virtual server at Linode, and at clients' sites. They all run [MailScanner]("http://www.mailscanner.info/") with sendmail as the SMTP daemon.  I've been running Internet mail servers since the mid-1990s.  On a couple of occasions I accidentally configured things wrongly so my box became an open relay, but that was quite a few years ago now.

From a security perspective, your number one task is to make sure the server only accepts mail for your domain(s) and rejects messages addressed elsewhere.  The site [http://mxtoolbox.com/](http://mxtoolbox.com/) provides some useful tools to check whether your server has been blacklisted as a spam source, test for an open relay, and the like.

Thanks for the tip, completely forgot about Linode. Are you happy with them?

---

### Post by kevdog on 2013-06-08
I dont think the problem is receiving mail, however sending the mail.  Usually you will have to forward the mail through a known provider since all the mail I've ever sent originating from my machine is blocked by Comcast

---

### Post by CharlesA on 2013-06-08
> **kevdog said:**
> I dont think the problem is receiving mail, however sending the mail.  Usually you will have to forward the mail through a known provider since all the mail I've ever sent originating from my machine is blocked by Comcast

Yep. I had to configure postfix at home to send via Gmail because port 25 is blocked and port 587 didn't work for whatever reason. I might have to try it again sometime.

---

### Post by SeijiSensei on 2013-06-08
> **PartisanEntity said:**
> Thanks for the tip, completely forgot about Linode. Are you happy with them?

Very much so!  I've got two virtuals in Linode data centers, one on each coast, in Newark, NJ, and Fremont, CA.  That gives me two geographically and topologically separate DNS servers.  One of them has very limited visibility on the Internet, while the other one hosts web services and accepts inbound mail. 

I also pay for their snapshot backup service.  I've only used it once and found the easiest solution was to create a new virtual, then restore the backup to that machine.  I retrieved what I needed and deleted the VM.  Linode didn't charge me a penny since I had the VM only a couple of hours!

They also have good tools for managing the server in cases where it won't boot cleanly, or you cannot connect to it with SSH.  Along with a web-based terminal, you can even open a session at the host level, so you can muck around in the machine's image if you need to.  I did that once when I accidentally deleted an OpenSSL library or two and all the client software stopped working because the dependency was gone.  I could actually replace the missing files directly into the image from another location and fix the problem that way.

Linode is pricier than some VM providers, with a 1 GB machine starting at $20/month.  But they are very professional and well-informed, and their offerings are rock solid.  I recommend them whole-heartedly.

---

### Post by buzzingrobot on 2013-06-08
Linux desktops very often run sendmail or postfix or exim or dovecot or some such mail server to handle internal system mail.

But, I suspect you're asking about the pro's and con's of standing up a distinct piece of hardware as a server handling mail for a domain you own.  I don't see the value in that.  Too much work and hassle and staying on top of security issues.  In the end, it's the same mail you'd send or get via Gmail or whoever.

---

### Post by Roasted on 2013-06-08
I have a server that does literally everything else besides mail. File, print, backup, web, video surveillance, ownCloud, but no mail here...

---

### Post by Paqman on 2013-06-09
> **CharlesA said:**
> I have a mail server running on my VPS, but it's mostly to provide mail about updates and from my contact form on my website.


Same here, it's only there so the server can get in touch with me. I've got the mail server on my NAS at home set up for the same reason. All my personal mail goes through gmail.

---

### Post by t0p on 2013-06-09
I used to have a mail server on my box as an experiment, basically a convoluted way to use my Gmail accounts via the command line - using programs like mail, mailx, mutt.  Of course, I'm not doing that anymore - Gmail is used via browser easily.  But it was an interesting thing to do, learned a lot by it.

---

### Post by lisati on 2013-06-09
I've been running my own email server from home for three years now. As others have said, make sure you don't set yourself up with an open relay. 

My setup started as a fairly "standard" postfix/amavis/clamav/spamassassin combination. Over the years I've also added monitoring with fail2ban and some custom policy and content filters.

---

### Post by Paqman on 2013-06-10
> **lisati said:**
> Over the years I've also added monitoring with fail2ban and some custom policy and content filters.

IMO running *any* kind of internet-facing server without fail2ban or denyhosts is mental. If nothing else it stops the script kiddies from spamming up your logs.

---

