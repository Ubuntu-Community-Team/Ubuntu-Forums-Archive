---
title: "Sendmail not being sent to my mailserver"
date: 2008-08-20
forum: Server Platforms
---

### Post by theonlygonzo on 2008-08-20
Ok i have been looking into this for quite some time now, and still can not come to a solution. I have a configured a webserver using Ubuntu 8.04 Hardy using sendmail (8.14.2.2)for a form on the webiste.
The only purpose for sendmail is to email information that is entered into a form on the website to an internal email. My mail server is configured on another server.
Right now I can submit info on the website and have it sent to the email account I have specified, and the webserver sends a reply mail to the sender informing them that their email has been sent.
Now the problem is no matter where this email is sent from (internal or external to the LAN), it will get stuck in the queue to be sent to the mailbox for the specified email account. The system log shows that the sending of the info from the website form, has timed out during the sending. It also shows me the IP address it tries to send to, which is the public address for my mailserver.
To my knowledge, I have never been able to get to my mailservers public address. This is because my ASA5520 does not allow traffic from internal (private address) to get to a destination on the DMZ (public) address. I can only get to my mailserver thru the private address.
So my question is this: Is there a way in sendmail to configure it to send to a private address instead of the public address it is trying currently? If there is, then I should be able to get the info being sent from my website to the desired mailbox. If not, then does anyone have any suggestions as to another email service to use in Ubuntu other than sendmail?

---

### Post by Ximbiot on 2008-08-20
> **theonlygonzo said:**
> Is there a way in sendmail to configure it to send to a private address instead of the public address it is trying currently? If there is, then I should be able to get the info being sent from my website to the desired mailbox. If not, then does anyone have any suggestions as to another email service to use in Ubuntu other than sendmail?

You could edit /etc/hosts on the web server to contain the private IP of the mail server.  If the web server doesn't need to handle incoming mail, you could also install the nullmailer package on it and configure it to forward all the mail it receives via your internal mail server IP.  Nullmailer is much easier to configure than sendmail.

---

### Post by theonlygonzo on 2008-08-20
> **Ximbiot said:**
> You could edit /etc/hosts on the web server to contain the private IP of the mail server.  If the web server doesn't need to handle incoming mail, you could also install the nullmailer package on it and configure it to forward all the mail it receives via your internal mail server IP.  Nullmailer is much easier to configure than sendmail.

When I edit /etc/hosts do I use @domain.com or just domain.com

Thanks, for the help.

---

### Post by Ximbiot on 2008-08-20
> **theonlygonzo said:**
> When I edit /etc/hosts do I use @domain.com or just domain.com

For information on the format of the /etc/hosts file:

```
man 5 hosts
```

Basically, though, assuming an internal IP like 10.10.10.10 and a hostname of mail.domain.com, you need something like:

```
10.10.10.10 mail.domain.com
```

I wouldn't put domain.com in the /etc/hosts file.  That might work, but if there is also a web server at domain.com and it has a different IP from your mail server, then you might cause yourself problems.  Just alias the mail server IP(s).

---

### Post by theonlygonzo on 2008-08-21
> **Ximbiot said:**
> For information on the format of the /etc/hosts file:

```
man 5 hosts
```

Basically, though, assuming an internal IP like 10.10.10.10 and a hostname of mail.domain.com, you need something like:

```
10.10.10.10 mail.domain.com
```

I wouldn't put domain.com in the /etc/hosts file.  That might work, but if there is also a web server at domain.com and it has a different IP from your mail server, then you might cause yourself problems.  Just alias the mail server IP(s).

Still did not work, I think I am going to give up on sendmail and try something a little more friendly to a Linux newb.

Thanks for your help.

---

