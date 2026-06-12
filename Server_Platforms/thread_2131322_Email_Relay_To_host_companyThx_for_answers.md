---
title: "Email Relay To host company?Thx for answers"
date: 2013-04-01
forum: Server Platforms
---

### Post by Tavring on 2013-04-01
Hi
I have a free hosting, but needed more access to the server.
So I did set up a Ubuntu server 12.04.
I have a simple environment with LAMP,SSH,Webmin and a CMS.

I have used this:sudo apt-get install ssmtp
Then edit the ssmtp configuration file:
sudo -e /etc/ssmtp/ssmtp.conf
I do not know details of an SMTP server available to you, so I will give a GMail example:
Root=your_email@gmail.com
Mailhub=smtp.gmail.com:465
RewriteDomain=gmail.com
AuthUser=your_gmail_username # [EMAIL="me@gmail.com"]me@gmail.com[/EMAIL]
AuthPass=your_gmail_password
FromLineOverride=Yes
UseTLS=Yes

And it work well with Gmail;), I point the DNS on the hosting company to my own server.
I want to use the [EMAIL="user@domain.com"]user@domain.com[/EMAIL] the same FQDN that is on the server, but use the hosting company's mail server.

Is this possible?

Thank you for your time and answers

Best Regards

Tavringen

---

### Post by annoyingrob on 2013-04-02
Yes you can do that. You can set up your server as a relay and forward the smtp requests like you just did. But, why don't you just change your DNS records to point the mail server to your hosting company rather than have all of the mail going through your server? Also, is there a particular reason why you don't want to just handle all of the email on your own server?

---

### Post by Tavring on 2013-04-07
Hi thank you for your repley.
Sorry it took so long time to answer.

No, their is no particular reason to why i want the mail to run trough my server.

The MX records are pointed to hosting on the hosting control panel.
(I made a mail account on the control panel with the same domain name [EMAIL="autoreplay@mysite.com"]autoreplay@mysite.com[/EMAIL])
The DNS records are pointed to my home server(mysite.com).

I tried to setup the configuration for the CMS to handle that email account and use it default.

Now to the server side.
I added nameserver on the resolv.conf file,
Changed the default email on CMS to [EMAIL="autoreplay@mysite.com"]autoreplay@mysite.com[/EMAIL].
I edit the /etc/ssmtp/ssmtp.conf:

Root=autoreply@mysite.com
AuthUser=username # [EMAIL="me@gmail.com"]autoreply@mysite.com[/EMAIL]
AuthPass=yourpassword
FromLineOverride=Yes
UseTLS=Yes

hosting is servage

I can not get the configuration to work.
I´m in need of some guideline to they config.
Manged to get the CMS to work with a gmail account.

Thank you for your time and replys

Tavringen

---

