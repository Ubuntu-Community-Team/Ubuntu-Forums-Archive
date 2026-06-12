---
title: "How to send email using another postfix server on the network"
date: 2021-03-27
forum: Server Platforms
---

### Post by ameinild on 2021-03-27
Let me start by saying I'm a complete noob with Unix/Linux email, so there are a lot of things I don't know about this.

Here's the scenario:

[LIST]
[*]I have a couple of servers, including some VM's, where I want to be able to send a "standard" email from cron, part of scripts, from command line etc. 
[*]On my main server, I want to install Postfix so emails can be sent from here to the internet. 
[*]I would like my other servers (including VM's) to be able to use the main Postfix server on the network to send out emails. 
[/LIST]

I have found plenty of guides on installing a Postfix server - I'm pretty sure I got this covered.
So my question is, how do I set up the other servers to use a central Postfix server on the network? I want to do this in the most simple way possible, preferably if there is a "default" way to do this.

Also, I know nothing about the /etc/mail.rc and ~/.mailrc files, so any information about those would be appreciated as well.

Thanks in advance! :)

---

### Post by TheFu on 2021-03-27
During the install of postfix, choose satelite for the config type and point it at our mail postfix server.  I always find using IP, not DNS, for the man server make it work easier.  May want to setup local /etc/aliases to forward mail to e main account, not leave it local. Good to have local root, thefu, postmaster, webmaster all forwarded to centralized accounts, for example.

---

### Post by ameinild on 2021-03-28
So just to understand your point, you have to install postfix (or something similar) on all servers, even if my "satellite" servers should use the central postfix server to actually send the mail off to my internet email address?

---

### Post by LHammonds on 2021-03-28
If its a mail server, other servers should be able to use just about whatever mail client you want as long as the protocols used on the mail server are supported in the client.

For example, I currently use NethServer as a back-end mail server just so my other servers, copiers, etc. have a way to utilize mail notification but I make sure nothing on the outside can utilize it and no unexpected devices can utilize it (do not want my IP flagged as a spam source) so I only allow specific IP addresses to connect.  Previously, this has also been Microsoft Exchange, Zimbra or external GMail.

As for the ability to use the mail server, there are several ways of doing it but I wanted a very lightweight client that did not need to install 200 libraries. hehehe.  So I ended up going with ssmtp.  [Here is how I did it](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=257).

LHammonds

---

### Post by TheFu on 2021-03-28
> **ameinild said:**
> So just to understand your point, you have to install postfix (or something similar) on all servers, even if my "satellite" servers should use the central postfix server to actually send the mail off to my internet email address?

There are many ways, but UNIX is designed around each system running an MTA.  sendmail, postfix, exim are each MTAs.  The configuration controls whether any inbound SMTP is allowed or not. Postfix in "satellite" configuration doesn't accept inbound email over the network, so only local email ... like what a cron job would create or what Mail creates would be accepted. The listener doesn't even run on port 25/tcp, so there's ZERO risk for network attacks to these satellite setups.

Where that mail goes is dependent on the satellite setup - really the *relayhost* setting which would be to your main mailserver.  It is about 30 seconds to configure this stuff and all programs on the system can use it.  If the /etc/aliases doesn't point email to be forwarded to your main server, then that email will sit on the local machine.
There's a trivial manpage for the aliases file.

```
MAILER-DAEMON:  postmaster
postmaster:     root
root:           my-real-account@domain.com
www-data:       my-real-account@domain.com
...
```
The just remember to run **sudo newaliases** and that's it.

Use the same MTA on all the systems and you don't need to worry about funky other programs and those configs.

---

### Post by ameinild on 2021-03-28
Thanks to both of you.

I read about ssmtp before, and it looks like a good and lightweight option that I'll look into some more

---

### Post by TheFu on 2021-03-28
Happy you found something useful. LHammonds' method fits many situations.

Please post a follow up with the final choice AND please mark this thread as SOLVED using the "Thread Tools" button in the upper right of this page/thread to help others out.

---

### Post by ameinild on 2021-03-29
Ok I got this to work exactly as I wanted - here is what I did.

I installed postfix and opendkim on my main server, using the following guides:

[https://ubuntu.com/server/docs/mail-postfix](https://ubuntu.com/server/docs/mail-postfix)

[https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu](https://www.linuxbabe.com/mail-server/setup-basic-postfix-mail-sever-ubuntu)

[https://www.web-workers.ch/index.php/2019/10/21/how-to-configure-dkim-spf-dmarc-on-sendmail-for-multiple-domains-on-centos-7/](https://www.web-workers.ch/index.php/2019/10/21/how-to-configure-dkim-spf-dmarc-on-sendmail-for-multiple-domains-on-centos-7/)


Then I installed ssmtp 2.64-9 on my "satellite" servers (perfectly valid on 20.04 too, get it here: [https://ubuntu.pkgs.org/20.10/ubuntu-universe-amd64/ssmtp_2.64-9_amd64.deb.html](https://ubuntu.pkgs.org/20.10/ubuntu-universe-amd64/ssmtp_2.64-9_amd64.deb.html))

Here I used the following config file:

```
## Config file for sSMTP sendmail
mailhub=10.10.2.2:25 #IP of my server
UseTLS=YES
UseSTARTTLS=YES
hostname=mydomain.ext
```

Now it works perfectly that all machines can send system email via the postfix server on 10.10.2.2 (or mail.mydomain.ext). =d>

---

