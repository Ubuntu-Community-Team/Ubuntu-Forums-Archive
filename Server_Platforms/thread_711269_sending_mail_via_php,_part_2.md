---
title: "sending mail via php, part 2"
date: 2008-02-29
forum: Server Platforms
---

### Post by vsiege on 2008-02-29
OK, so i have verified that my php sendmail script is good. It works on my other server but not on my home 7.10 based server. When I installed 7.10 I never selected to have a mail server put in. Is this why my php mail function won't work?
Which one of these should i install....postfix? exim ? Sendmail ? masqmail?
I've never set one up.

At the moment I am using an IP addy to access my server publically - should I also be installing some sort of DNS server?

below is the php which is having trouble sending mail.
[PHP]<?php
$ip = $_SERVER['REMOTE_ADDR'];

$charset = 'UTF-8';
	
// the email where it gets delivered to
$to = "blablao@bla.com";

// the originator of the email
$senderMail = "info@myDomain.com";
$senderName = "from me";
$senderSubject = "Home Server IP";
$senderBody = "http://$ip";

//Add header information
$headers = "From: $senderName <$senderMail>\n";
$headers .= "Reply-To: $senderName <$senderMail>\n";

// To send HTML mail, the Content-type header must be set
$headers .= "MIME-Version: 1.0\r\n";
$headers .= 'Content-Type: text/plain; charset=$charset; format=flowed' . "\r\n";
$headers .= "Content-Transfer-Encoding: 8bit\r\n";
$headers .= "X-Mailer: PHP\n";


if(@mail($to, $senderSubject, $senderBody, $headers)){
	echo "it worked";
		}
		else
		{
	echo "nope it didn't work.";

}
?>[/PHP]

---

### Post by Mr. C. on 2008-02-29
PHP uses the "sendmail" compatibility program, originated in Sendmail, but also available in Postfix and others.

First, does your ISP allow you to run an MTA (mail server)?  An MTA will send email outbound with a destination port of 25.  If not, and they are likely blocking outbound port 25, you must use their servers.

If you're not sure, try:

telnet gmail-smtp-in.l.google.com 25

and see if you get output. If not, port 25 is blocked.  Report back results.

---

### Post by KCPokes on 2008-02-29
Even if you can send port 25 traffic, you should normally relay through your ISP's mail servers.  This will normally prevent all your mail from being bounced as SPAM.  Of course this is more of a MTA setup point, rather then PHP, but just something to consider.

---

### Post by vsiege on 2008-02-29
**Mr. C** I am at the temporary location of my server, so this might change when i finaly bring it to the final destination. for now it replies:```
Trying 66.249.83.114...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP i14si9747023wxd.11
```it appears to be good. Whats the next step?


If you dont mind telling me what happens if they blocked 25 that woudl be great too.

**KCPokes** So whether it is or not.... use my ISP's SMTP to send. Thanks. Im guessing Mr. C will probably tell me to install an MTA at this point.

---

### Post by Mr. C. on 2008-02-29
Good, so you can use your system to directly send mail.  As KCPokes indicated, there is increasing likelyhood your server's attempts to send mail will be blocked (due to being in various residential, dynamic, or other IP blacklists).

Anyway, you now need an MTA.  You have choices as you're aware, or can use the nullmailer package to relay via your ISP.  I'm a Postfix fan, don't care for Sendmail, and have never evaluated Exim.  Your choice.  Pick on that suits your needs (and this is tough, because there is a lot of hearsay, and without experience with the various systems, you can't really evaluate them).

Avoid using any of the mysql variants of the packages - they are too heavy for what you want.

Let us know what you pick, and we'll go from there.

btw. if the port was blocked, no output would have returned, since the remote server never receives your connection attempt.

---

### Post by vsiege on 2008-02-29
I will go with Postfix, it sounds like its very common and well-documented. I going to install it, now comes the harder part of the journey - im all ears.

> btw. if the port was blocked, no output would have returned, since the remote server never receives your connection attempt.I meant, if it didnt receive anything back - would you just end up telling your MTA to use the ISP's services?

---

### Post by Mr. C. on 2008-02-29
Install vanilla postfix, and use the Internet configuration when it asks.  You can select the postfix-pcre option too.

If the port is blocked, you change options in postfix to relay via your ISPs servers instead.

---

### Post by siouzi on 2008-02-29
Postfix is overkill if you don't need a mail server and just want to send out mail using a relay/smarthost. If the need is really simple, first install ssmtp and then mailx. sstmp is a mail-transport-agent which mailx, command line mail (user agent) uses. mailx *should* provide the sendmail program that PHP needs.

With ssmtp you can also have *system email* sent to you, even via gmail ([HOWTO Gmail and sSMTP](http://gentoo-wiki.com/HOWTO_Gmail_and_sSMTP)). It seems to be a pretty good lightweight solution, but it can't send system mail to multiple recipients (or I didn't try hard enough...) :/

---

### Post by vsiege on 2008-02-29
**Mr. C** Heres what I know to do, but its not exactly what you are saying:
normally I would do this first:
sudo apt-get install postfix
and use the package that came with 7.10, but when I looked up vanilla postfix I found a site that talked about slackware.

**siouzi** good site.... but im going to try to go big first, just in case down the line I want more

---

### Post by Mr. C. on 2008-02-29
> **vsiege said:**
> **Mr. C** ....
normally I would do this first:
sudo apt-get install postfix
and use the package that came with 7.10, but when I looked up vanilla postfix I found a site that talked about slackware.

That's fine.  If you want PCRE support, you can add it later.

---

### Post by vsiege on 2008-02-29
for my system mail name:
does this make a difference what this is called? right now its sticking the name i gave to the server in front of my ISP (like a sub-domain)
servername.myisp.com

like i said... im eventually moving this machine.... there is no domain registered to the machine itself

---

### Post by Mr. C. on 2008-02-29
> **vsiege said:**
> for my system mail name:
does this make a difference what this is called? right now its sticking the name i gave to the server in front of my ISP (like a sub-domain)
servername.myisp.com

like i said... im eventually moving this machine.... there is no domain registered to the machine itself

Yes.  This is the address that would be tacked onto unqualified addresses (eg: root) and is used in the HELO name to remote mail servers.  If it is bogus, remote MTAs will reject your email.  There are other hidden gotchas.

You'll just have to try your luck to see which MTAs accept your mail, and which ones don't.  Mine reject unqualified hostnames, and the default Ubuntu install does not tack on the domain name (append_dot_domain = no).  So, if you were to attempt relay to mail my server, you'd get:

... Sender address rejected: need fully-qualified address

using the typical:

```
mail mrc@example.com
```

---

### Post by vsiege on 2008-02-29
so I went ahead with everything.... visited my php page.... and now the message is that "it worked" but still no email is sent.... but obviously it is working a little more than when we began

the next thing i did was to write an email using mailX:
```
mail me@memrerm.com
Subject: test
body stuff here
~.
```I got no error or any other kind of response


How do I trouble shoot from here?

BTW I found **append_dot_domain = no** in the **/etc/postfix/main.cf** but didnt touch it yet

---

### Post by Mr. C. on 2008-02-29
First rule of postfix - go to the mail log.  In Ubuntu, its /var/log/mail.log.  Show the log entries.

---

### Post by vsiege on 2008-02-29
OK.... heres where I am.... it seems as though I get a ```
550 error: Mail Refused - bla bla bla
```now after that is a web site that my ISP hosts, on that site it tells me basically if you see this and are NOT a static or business class use our SMTP-server.bla.bla

where do i adjust postfix for this??

---

### Post by Mr. C. on 2008-03-01
That's a butchered version of the postfix log messages.  Show the entire line.  You can obfuscate IPs and email addresses if necessary, but you've removed important data.

So, now you've come to where we said you'd come - the receiving MTA isn't allowing you to send email directly.  So, you'll likely want to configure your postfix to relay via a smarthost, which will be that of your ISP.

However!  You need to know if you ISP requires SMTP authentication to relay mail via their servers.  This is required to configure postfix to be able to send to their their servers.

---

### Post by vsiege on 2008-03-01
theres a bunch more but it looks very similar to this```
Feb 29 22:29:46 myserver postfix/master[6438]: daemon started -- version 2.4.5, configuration /etc/postfix

Feb 29 22:33:55 myserver postfix/pickup[6442]: F3E1B36A58B: uid=33 from=<www-data>

Feb 29 22:33:56 myserver postfix/cleanup[6479]: F3E1B36A58B: message-id=<20080301033355.F3E1B36A58B@myserver.myisp.com>

Feb 29 22:33:56 myserver postfix/qmgr[6443]: F3E1B36A58B: from=<www-data@myserver.myisp.com>, size=502, nrcpt=1 (queue active)

Feb 29 22:33:56 myserver postfix/smtp[6481]: F3E1B36A58B: host hrndva-smtpin01.mail.hat.com[71.74.56.243] refused to talk to me: 550-hrndva-mxlb.mail.hat.com 550 ERROR: Mail Refused - res.hat.com - See http://theDynamicPage.com

Feb 29 22:33:56 myserver postfix/smtp[6481]: F3E1B36A58B: to=<myUSerName@myisp.com>, relay=hrndva-smtpin02.mail.hat.com[xx.xx.xx.545]:25, delay=0.2, delays=0.05/0.01/0.14/0, dsn=4.0.0, status=deferred (host hrndva-smtpin02.mail.hat.com[xx.xx.xx.545] refused to talk to me: 550-hrndva-mxlb.mail.hat.com 550 ERROR: Mail Refused - res.hat.com - See http://theDynamicPage.com)

Feb 29 22:39:46 myserver postfix/qmgr[6443]: F3E1B36A58B: from=<www-data@myserver.myisp.com>, size=502, nrcpt=1 (queue active)

Feb 29 22:39:46 myserver postfix/smtp[6507]: F3E1B36A58B: host hrndva-smtpin02.mail.hat.com[xx.xx.xx.545] refused to talk to me: 550-hrndva-mxlb.mail.hat.com 550 ERROR: Mail Refused - res.hat.com - See http://theDynamicPage.com
```

where do i find out if they require auth? can I try it without first?

I just found this on their site:
*.res.hat.com - This naming pattern indicates an IP address in hat's residential customer space. This is a dynamically assigned IP address, but the always-on nature of our cable modem service means that our customers can enjoy a persistence to their IP address assignment that can last for months or longer. Our AUP does not prohibit servers in this space, but we do make available to our customers in this space SMTP servers that they may use to relay all of their outbound mail, should they so choose.

---

### Post by Mr. C. on 2008-03-01
If you've used their mail servers to send mail via some mail client like Thunderbird or Outlook, then the settings you used their will suffice.

You can check what is accepted on their servers:
```

telnet theirMTAhostname 25
EHLO yourdomain.com
quit

```
and report back what results.  Do and report the same thing for port 587.  This will tell us what capabilities the server provides, and how you need to configure your client to relay.

If you needed to enable Authentication, then you'll need to do so w/postfix too.  If you didn't, you may be able to just reconfigure postfix:

[http://ubuntuforums.org/showthread.php?t=503078&highlight=postfix+smarthost](http://ubuntuforums.org/showthread.php?t=503078&highlight=postfix+smarthost)
See also:
[http://www.postfix.org/SOHO_README.html](http://www.postfix.org/SOHO_README.html)

---

### Post by vsiege on 2008-03-01
Heres what I get. I used the same smtp-server that I use in my mai applications.
```
me@mysr:~$ telnet theirMTAhostname 25
telnet: could not resolve theirMTAhostname/25: Name or service not known
me@mysr:~$ telnet smtp-server.yea.com 25
Trying xx.xx.xx.35...
Connected to smtp-server.yea.com.
Escape character is '^]'.
220 hrndva-omtalb.mail.yea.com ESMTP Welcome to yea.  WARNING: *** FOR AUTHORIZED USE ONLY! ***
EHLO mysr.yea.com
250-hrndva-omtalb.mail.yea.com
250-HELP
250-VRFY
250-XREMOTEQUEUE
250-ETRN
250-PIPELINING
250-DSN
250-8BITMIME
250 SIZE 30996480
telnet smtp-server.yea.com 587   
Connection closed by foreign host.

```

Side note: As iM sure my next trip after getting to setting up the MTA, is security. Below are the ports I have open to traffic trhough my router. My next endevour will be surely to make the server my secure.
I have always allow LAN Server IP address: xxx.xxx.x.xx
WAN Users: Any (which could be restricted to just a handful, problem is I travel)
[LIST]
[*]SMTP -25
[*]VNC -5900
[*]HTTP- 80
[*]HTTPS -443
[*]FTP -20..21
[*]SFTP -115
[*]SSH - 22
[/LIST]

---

### Post by Mr. C. on 2008-03-01
Ok, so it appears that you do not need to authenticate.  I cannot access that MTA, so it is allowing only clients on their network.  So you should just be able to send via their servers.

Just add:

```
relayhost = [smtp-server.yea.com]
```

to your main.cf file and reload postfix.

---

### Post by vsiege on 2008-03-01
It works.... this time forreal. Great stuff. Thankyou for your help. BTW that wasn't the real name of that server. replace *yea* with *nyc.rr*


Now if I go to my php page over the net, the page emails me.

I put this in rc.local as I want it to email me when the machine is first turned on, without logging in. I dont recieve an email though.

```
php /home/www/myfile.php
exit 0
```

---

### Post by Mr. C. on 2008-03-01
Sounds like you are well on your way.

Again, when mail fails, first go to the mail logs.  What do they show for the period right after you turned on the machine and expected your script to run?

---

### Post by vsiege on 2008-03-01
when i get rid of everything in the log, shut down then power up again. I then log in and check the log, here is what is there:
```
Mar  1 14:08:10 myserver postfix/master[5510]: daemon started -- version 2.4.5, configuration /etc/postfix
```
nothing else

---

