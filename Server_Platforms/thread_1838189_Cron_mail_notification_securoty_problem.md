---
title: "Cron mail notification securoty problem"
date: 2011-09-03
forum: Server Platforms
---

### Post by klaasvg on 2011-09-03
I encoutnered a strange problem. I have a backup script that runs each day on 20:00 to backup my major data directoryies to an external hard drive.

It appeared that some notification mail is sent to an email address that is not mine so the mail was recieved by someone who sent it back to me with the question to remove his address...
Some relevant data:
The mail address recieving the notifications/errorlogs corresponds with [email]myusername@myprovidername.nl[/email], and this appears to be an existing address which recieve my notifications! I did not even know these were sent.
From the mail he returned to me, it appears that a mail is first sent to myusername@ubuntu-desktop (this is the name of my Ubuntu machine)
This mail somehow was forwarded to [email]postmaster@myprovider.nl[/email], and finally arrived at the mail address  [email]myusername@myprovider.nl[/email] (again, this appeared to be the address of a stranger)

In the /var/log/syslog, the following entries are found which are probably the root of the problem:
Sep  2 20:00:01 ubuntu-desktop CRON[10382]: (myusername) CMD (/home/myusername/backup.sh # JOB_ID_1)
Sep  2 20:00:43 ubuntu-desktop sSMTP[10394]: Sent mail for [email]root@myprovider.nl[/email] (221 smtp15.gn.mail.iss.as9143.net closing connection) uid=1000 username=myusername outbytes=29225

I am startled because I would never have expeced this. How the heck is this possible?
Maybe there is a related event, to be able to send mail from my PHP websites using the mail function, I installed and configured SSMTP to send mail using the SMTP settings of my provider.
What happens here? Ideas are very welcome!

---

### Post by klaasvg on 2011-09-05
I still do not know shat happened exactly but sloved the problem by redirecting the standard output and error of my Cron jobs to log files.

---

### Post by gmargo on 2011-09-05
> **klaasvg said:**
> I still do not know shat happened exactly but sloved the problem by redirecting the standard output and error of my Cron jobs to log files.

Not an ideal solution.

It must be problem in the mail server configuration. What mail server are you using?   How is it configured? Can you still get mail locally or is it all forwarded?  Have you set up /etc/aliases to forward root & postmaster to you?  (And send that guy email apologizing in advance for the tests you are about to start!)

Edit: Rereading I see you are using SSMTP.  No doubt this is the problem. It does support redirecting root etc, but what is your config?

---

### Post by klaasvg on 2011-09-06
Gmargo thanks for your reply.
I indeed used SSMTP but I removed the installation and the config file is gone too. It appeared that the config file is poorly documented and not all options are included as commented lines.
My impression is that local mails were forwarded indeed. There is no /etc/aliases on my system, in fact I have little udnerstanding of mail forwarding of local mail, I just had installed and configured SSMPT to be able to send email using the PHP mail() function but had clearly no idea about the side effects... 
I must study this subject in more details! But I think find it pretty scary that the system just composes an email address from my Ubuntu user name and my internet provider.
Is Postfix an email server by itself and can I use this instead of SSMTP? It seems to be better documented.

---

