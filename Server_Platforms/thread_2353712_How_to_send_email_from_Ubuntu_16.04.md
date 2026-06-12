---
title: "How to send email from Ubuntu 16.04"
date: 2017-02-24
forum: Server Platforms
---

### Post by fernandoch on 2017-02-24
Hello,

What is the best way to send emails from an Ubuntu server 16.04?

How to configure it?

Thank you

---

### Post by TheFu on 2017-02-24
Setup an MTA.  There are a few different options depending on your needs.  exim, postfix, sendmail.
MTAs are for server-to-server emails.  Not clients.  Your local clients would talk to your local server (MTA) and let it handle sending emails outside the network.

Of course, since email has become mostly spam, there are some barricades put in place to prevent home servers from sending email anywhere.  First you'll need a non-residential connection. Next you'll need a static IP and lastly, you'll need a valid, paid, domainname which is known to all DNS around the world (must have an MX record).

There are a few other things, but those are mostly anti-spam and if you don't have the above, forgetaboutit. Ok - your system CAN send email, but nobody will allow them to be received.  Most email systems see about 95% of all email as spam and block it.  I do.  If email comes from a DHCP IP, blocked. If the server sending doesn't use encryption, blocked. If the server sending it fails SFP, blocked.  If the sending server doesn't have a reverse-DNS, blocked.  There are a few other checks too.

It is possible to send email to a specific account that you own (like gmail), if you like.  That is outside my knowledge, but other people here do it.  I think they don't use a full MTA, just something like SSMTPd.

You didn't mention receiving email. Why not?

---

### Post by bearlake on 2017-02-24
As mention above, It is possible to send email to a specific account that you own (like gmail).

[https://easyengine.io/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://easyengine.io/tutorials/linux/ubuntu-postfix-gmail-smtp/)

Been using it on 16.04 with no issues.

---

### Post by SeijiSensei on 2017-02-24
If you are trying to send mail from a residential Internet connection, your ISP may block such traffic.  Before you get too invested, run a simple experiment.  Type this at a terminal prompt:
```
telnet gmail-smtp-in.l.google.com 25
```
If you see a result similar to this:
```
Trying 173.194.208.27...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP g38si1052478qtg.159 - gsmtp

```
you aren't being blocked.

---

### Post by fernandoch on 2017-02-24
Good thanks guys.

Not being blocked @SeijiSensei

Will try the tutorial @bearlake

To be able to send emails from my wordpress sites, I just need to configure postfix, right?

---

### Post by TheFu on 2017-02-24
> **fernandoch said:**
>  To be able to send emails from my wordpress sites, I just need to configure postfix, right?

No, not anymore.  20 yrs ago, that was enough.

Just because your ISP doesn't block outbound, doesn't mean nobody else will.

Only if you don't care whether anyone actually reads them. Then feel free to send whatever ... anti-spam efforts are necessary if you expect anyone to read those emails, as listed in my first reply.  There are many other reasons for emails to be blocked too - like you share a host or relay with another person/company who got the relay added to a spammers list.  You'll see.

For a few emails just to your email address, shouldn't be that big of an issue.
If you plan to send emails to readers and it is more than 15 accounts, that's when the anti-spam stuff becomes very important.

---

### Post by fernandoch on 2017-02-24
I just want to send emails to recover passwords or create new users.

I use an autoresponder for mass emails.

---

### Post by TheFu on 2017-02-24
Review post #2?  Those are the minimal needs for effective emails that will be seen - i.e. not blocked by the ISP anti-spam tools.  Start with the DNS MX record and work outwards from that. Mail servers don't trust other mail servers which don't have MX records and domainnames.

---

### Post by SeijiSensei on 2017-02-24
And include an [SPF record]("http://www.openspf.org/") in your DNS as well.

---

### Post by fernandoch on 2017-02-25
@bearlake

The guide worked great, thanks.

The only thing is that I get emails from root in the from.

Can that be changed to something else? Like the server name?

---

### Post by TheFu on 2017-02-25
The "FROM" can be anything you like - best if it represents your domain, at a min and if the address doesn't accept replies, would be nice to set to something like "no-reply@domain.com"

Control of the "FROM" is from the client program making the request (php-script?). If not provided, the default would be based on the passwd entry for the userid performing the sending .

---

### Post by SeijiSensei on 2017-02-25
To be clear, every email address has two "From" addresses.  One is the From that appears when you read the message in a mail client.  That From can be set to whatever you want when composing the message.  In PHP, for instance, I often use:
```

$to='someone@example.com';
$subj='Sample message';
$msg='Hi, Mom!';
$from='From: me@somewhere.net\n';
mail($to,$subj,message,$from);

```
(Notice that the From includes a return character at the end of the line.)  

However there is another From that actually matters more when mail is exchanged between servers.  It's called the "envelope-from" and is the content of the "MAIL FROM:" command during the SMTP dialogue between servers.  It may, or may not, match the From in the message itself, and it often cannot be manipulated by client software.  Only "trusted users," to use the sendmail term, can set the envelope-from.  It's this address that remote servers examine when applying anti-spam rules upon the message's arrival.

I have my server configured so that the "www-data" user, the one running the Apache web server process, is a trusted user.  Then I can set the envelope-from as well from PHP like this:
```

$env_from='bounce@somewhere.net';
mail($to,$subj,$msg,$from,"-f $env_from");

```
The last field adds "-f [email]bounce@somewhere.net[/email]" to the sendmail command and makes that address the envelope sender. Now if the message is undeliverable, the remote mail server will send the bounce notice to "bounce@somewhere.net" rather than "me@somewhere.net" which can be useful when managing mailing lists.

---

### Post by fernandoch on 2017-02-25
Thanks guys.

---

### Post by SeijiSensei on 2017-02-26
I made a couple of errors in the PHP code above.  I've fixed them now.

---

### Post by fernandoch on 2017-02-26
Thanks but I am not using php, mainly admin stuff.

---

### Post by TheFu on 2017-02-26
> **fernandoch said:**
> Thanks but I am not using php, mainly admin stuff.

**Mail** is the tool I use, but I try to send admin stuff to syslog and let logwatch tell me about it daily.  If you want immediate notification, setting up an monitoring/alarming system might be indicated. Something like nagios/munin or one of the 20 others.

Not that email is all bad, but when a server gets really busy, email is the first thing that gets automatically disabled by design.

---

### Post by fernandoch on 2017-02-27
When you need to recover a wordpress password or create a new forum user, you need email :) 

You can't send that to syslog :)

---

### Post by SeijiSensei on 2017-03-01
My examples were illustrative of the difference in senders, though if you're using WordPress, you're running PHP scripts.

From the command prompt, you can use the mail command from the mailutils package.

---

