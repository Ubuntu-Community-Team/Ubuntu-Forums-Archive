---
title: "email can be sent but not receieved"
date: 2012-08-24
forum: Server Platforms
---

### Post by briceorbryce on 2012-08-24
Hi all,
I (think) I can send emails but I can't receive them.

I have two virtualbox ubuntu (12.04) servers that have DNS, Postfix, Dovecot, and Squirrelmail on them.
ubuntu has DNS and Squirrelmail
ubuntu2 has Postfix and Dovecot
^The hostnames

I can sign in with both user and fmaster into squirrelmail 
Just to be sure, the email address is "user@hostname.domain.name" right?

I was able to send email from root using:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)
Although the last few emails I sent stopped working (I think it's because I changed the way postfix works - the errors I got were about:
```

Diagnostic-Code: X-Postfix; cannot update mailbox /home/user/Maildir for user
    user. cannot open file: Is a directory

```I also read that resolv.conf might be a problem but since you can't edit it, you have to edit /etc/dhcp/dhclient.conf right?
```
prepend domain-name-servers 192.168.1.2;
```My router assigns them IPs so I don't worry about the /etc/network/interfaces. Could that be causing the problem?

Also when I hit alt+< on the ubuntu login screen I see:
```
apaceh2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
``` Is that telling me my settings aren't pointing to itself correctly?

Not calling it mail.domain.name is okay right? Just not the norm?

TBH I think the problem is either the DNS settings, or the postfix configuration. Any thoughts, ideas, questions, comments are welcomed. I ran nslookup and dig mx and it looked fine but I'm not entirely sure it is.

Thanks for any help ):P

---

### Post by angryfirelord on 2012-08-24
You may want to look at this post: [http://ubuntuforums.org/showpost.php?p=12190942&postcount=2]("http://ubuntuforums.org/showpost.php?p=12190942&postcount=2")

---

### Post by briceorbryce on 2012-08-25
The thing that really got me is that I am using an internal DNS server. And I don't know if increasing the serial number worked or if I used the correct "way" to email out but it works.
I think I was trying to send email out to a different machine which didn't have IMAP on it.
Since postfix and dovecot are on ubuntu2, the correct email address is:
[email]user@ubuntu2.domain.name[/email]

What's odd is when I receive an email it comes from ubuntu.domain.name and if I reply to the email using that hostname it doesn't get sent. I have to change the hostname from the ubuntu to ubuntu2.
*shrugs* it works at least. That's something.

---

