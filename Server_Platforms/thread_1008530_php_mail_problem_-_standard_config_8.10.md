---
title: "php mail problem - standard config 8.10"
date: 2008-12-11
forum: Server Platforms
---

### Post by AzaraT on 2008-12-11
Hi there

I've just installed the latest Ubuntu Server with a LAMP and Mail server.

I am having a problem using a simple mail script with php, it simply does not deliver the email.

I have only changed one thing in the configuration and that is apaches directory index.

I have no idea why this fails. Here is the script im using:

[PHP]<?
/* this part can either be in the same file as the form or it can be in a different file. If you want this in a different file, make the "action" of the form go to that file */

if(sizeof($_POST)) {
$body = "";
while(list($key, $val) = each($HTTP_POST_VARS)) {
$body .= "$key: $val \n";
}

mail("email@example.com", // to
"Subject Line",
$body);

echo "Thanks for your submission. The results were mailed.";
}

// end form processing
?>

<form
method="post"
action="<? echo $PHP_SELF; ?>">
<input type="text" name="whatever">
<input type="radio" name="this" value="radioval">
<select name="another">
<option value="sel1">Select 1
<option value="sel2">Select 2
</select>
<input type="submit" name="submit">
</form>[/PHP]

I have no clue why the hell this aint working. For a php info go here: [http://62.242.47.104/info.php](http://62.242.47.104/info.php)

I do not want to send the mail with smtp(postfix) but just with plain simple php.

Hope someone can help me on this
Thanks
AzaraT

---

### Post by cdenley on 2008-12-11
PHP's mail function uses the sendmail command. If you have postfix installed, then you're using postfix. Are you sure it's failing to send, and your message isn't simply being rejected?
```

dpkg -S /usr/sbin/sendmail
tail /var/log/mail.log

```

---

### Post by AzaraT on 2008-12-12
using the first command it shows im using postfix and the second tells me that im getting connection timeout to send the email.

```
Dec 12 15:27:59 server postfix/cleanup[2700]: 2C47D87B3D: message-id=<20081212142759.2C47D87B3D@server>
Dec 12 15:27:59 server postfix/qmgr[2691]: 2C47D87B3D: from=<www-data@zorps.dk>, size=350, nrcpt=1 (queue active)
Dec 12 15:28:05 server postfix/smtp[2693]: connect to mail.azaratmusic.com[208.68.171.91]:25: Connection timed out
Dec 12 15:28:05 server postfix/smtp[2694]: connect to mail.zorps.dk[208.68.171.91]:25: Connection timed out
Dec 12 15:28:05 server postfix/smtp[2696]: connect to mail.zorps.dk[208.68.171.91]:25: Connection timed out
Dec 12 15:28:05 server postfix/smtp[2695]: connect to mail.azaratmusic.com[208.68.171.91]:25: Connection timed out
Dec 12 15:28:05 server postfix/smtp[2693]: 7A68087B5D: to=<azarat@azaratmusic.com>, relay=none, delay=72075, delays=72045/0.04/30/0, dsn=4.4.1, status=deferred (connect to mail.azaratmusic.com[208.68.171.91]:25: Connection timed out)
Dec 12 15:28:05 server postfix/smtp[2694]: D5B7487B5B: to=<listreports@mail.zorps.dk>, relay=none, delay=73074, delays=73044/0.06/30/0, dsn=4.4.1, status=deferred (connect to mail.zorps.dk[208.68.171.91]:25: Connection timed out)
Dec 12 15:28:05 server postfix/smtp[2695]: 69C8087B5C: to=<azarat@azaratmusic.com>, relay=none, delay=72075, delays=72045/0.07/30/0, dsn=4.4.1, status=deferred (connect to mail.azaratmusic.com[208.68.171.91]:25: Connection timed out)
Dec 12 15:28:05 server postfix/smtp[2696]: 681A787B4E: to=<listreports@mail.zorps.dk>, relay=none, delay=73610, delays=73580/0.07/30/0, dsn=4.4.1, status=deferred (connect to mail.zorps.dk[208.68.171.91]:25: Connection timed out)

```

I dont know but it seems like it cannot connect with port 25. I have port forwarded port 25 (tcp&udp) to the server so thought that should be ok? firewall in ubuntu is disabled.

---

### Post by cdenley on 2008-12-12
That definitely looks like a networking problem.
```

nc -z -v mail.azaratmusic.com 25
nc -z -v ubuntuforums.org 80

```

---

### Post by AzaraT on 2008-12-12
> **cdenley said:**
> That definitely looks like a networking problem.
```

nc -z -v mail.azaratmusic.com 25
nc -z -v ubuntuforums.org 80

```

Well im getting

```
DNS fwd/rev mismatch: mail.azaratmusic.com != mail.reliabledomainspace.com

DNS fwd/rev mismatch: ubuntuforums.org != feijoa.canonical.com
ubuntuforums.org [91.189.94.12] 80 (www) open


```

And I do get the same error with all port 25 servers.

---

### Post by cdenley on 2008-12-12
I would expect the first command to give you some sort of result, but I'm guessing you killed it before it timed out. It appears that either outgoing traffic on port 25 is dropped on your network, or the related incoming reply is dropped. Are you sure you haven't configured iptables?
```

sudo iptables -L -n

```

---

### Post by AzaraT on 2008-12-12
yeah I killed it.

This is what i get from iptables command:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I've never touched these settings.

---

### Post by cdenley on 2008-12-12
Then it's definitely a networking problem. Nothing you can do within ubuntu.

---

### Post by AzaraT on 2008-12-12
Ok thanks for helping :D

I just figurede that port 25 is completely closed by my ISP :( Is there anyway to use another port than 25?

---

### Post by cdenley on 2008-12-12
> **AzaraT said:**
> Ok thanks for helping :D

I just figurede that port 25 is completely closed by my ISP :( Is there anyway to use another port than 25?

Well, you need to connect on port 25 because that is the port the mail servers listen on. How do you send e-mail if your ISP filter port 25. Do they filter everything but their own smtp server? You could probably use a proxy. Perhaps your ISP is trying to stop their customers who are unwilling botnet members from sending spam. You could probably configure postfix to relay e-mail thorugh your ISP's smtp server.

---

### Post by AzaraT on 2008-12-12
> **cdenley said:**
> Well, you need to connect on port 25 because that is the port the mail servers listen on. How do you send e-mail if your ISP filter port 25. Do they filter everything but their own smtp server? You could probably use a proxy. Perhaps your ISP is trying to stop their customers who are unwilling botnet members from sending spam. You could probably configure postfix to relay e-mail thorugh your ISP's smtp server.

Yeah they have a mail server, and that is exactly what I am doing atm :)

However they do require a username and password, how do I set this? When I do a dkpg-reconfiguration of postfix it doesn't say anything about a username or password.

---

### Post by cdenley on 2008-12-12
[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html)

---

### Post by AzaraT on 2008-12-12
ah thanks a lot, much appreciated :)

---

