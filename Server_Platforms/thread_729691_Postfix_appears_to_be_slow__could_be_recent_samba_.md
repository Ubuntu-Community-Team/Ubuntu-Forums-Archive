---
title: "Postfix appears to be slow // could be recent samba install."
date: 2008-03-20
forum: Server Platforms
---

### Post by davyboy1979 on 2008-03-20
Hello

I have a Ubuntu 6.0.6.1 LAMP server which was simply running Postfix and I think Dovecot for IMAP email.  It is being used solely as an email server to send email from the lan and receive email from the outside world - there are about 14 users on it.  It had been working fine for about 6 months, since install but then I had to install Samba on it, so that another server could reach in and take a backup of the email files.

About 2 or 3 days after installing samba users starting complaining that it was taking a minute or so to send even a text email - they have a 100mb network.  before it was so quick you didn't know if thunderbird had sent the message without looking in sent items.

So i started investigating:  telnetting on port 25 from a machine to the ubuntu server sees a delay of about 20 seconds before the server acknowledges and gives the welcome message.  telnetting to localhost port 25 see's an instant response.  Very very strangely, computers from the outside world telnetting in on port 25 also get an instant response, so it is only machines on the local network that are seeing this problem.

I have checked syslog and the messages log but there is nothing untoward in there.  I spoke to a friend and he thought it might be a reverse DNS lookup issue - but I had one added to the external IP and it made no difference.

so I am stuck for ideas... is there anyone out there that may know why this is happening???

Thanks for your help.

Davyboy.:guitar::confused:

---

### Post by MJN on 2008-03-21
> **davyboy1979 said:**
> I spoke to a friend and he thought it might be a reverse DNS lookup issue - but I had one added to the external IP and it made no difference.

It probably is a reverse DNS issue, for the clients (perhaps for logging, or access control depending on how your server is configured).

Try adding an entry on the server in /etc/hosts for one of your clients e.g. 192.168.0.5 client1.yourdomain and see if connections from that client speed up.

Mathew

---

