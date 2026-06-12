---
title: "Xubuntu 10.10 Server - No php or smtp mail!"
date: 2012-02-11
forum: Server Platforms
---

### Post by Raphial Hebert on 2012-02-11
Mkay, I've been struggling with this for DAYS. I cannot find anything to help me out.

I have a nice little Xubuntu 10.10 home web server installed with PHP5, Apache2, phpmyadmin, Webmin, postfix, MySQL, the whole nine yards.

But no matter what I try, do, or what, I cannot get my smtp or php mail settings to work. I have a phpbb forum running on my server, and I cannot get the email feature to work because my server is not configured correctly (Like registration activation emails and such). 

I've tried Postfix, Citadel, Sendmail, etc etc. I'm not sure if it's because I just am a newb or what. I didn't have much trouble with anything else, except this email issue.

Can somebody please steer me in the right direction.

---

### Post by Raphial Hebert on 2012-02-11
Come on? No one?

---

### Post by Raphial Hebert on 2012-02-11
:/ I really need some help with this asap.

---

### Post by savanna on 2012-02-12
Hmmm... Is the mail server even working?

I suggest you do a web search on "smtp telnet test" - try connecting to the mail server via telnet and manually sending an email to an external account (Hotmail, Yahoo, etc).

At the same time, in another terminal, do a "tail -f /var/log/mail.log" (or whatever the log is called for your mail server). That way you can see what the mail server is doing.

---

### Post by Raphial Hebert on 2012-02-12
> **savanna said:**
> Hmmm... Is the mail server even working?

I suggest you do a web search on "smtp telnet test" - try connecting to the mail server via telnet and manually sending an email to an external account (Hotmail, Yahoo, etc).

At the same time, in another terminal, do a "tail -f /var/log/mail.log" (or whatever the log is called for your mail server). That way you can see what the mail server is doing.

I uninstalled Postfix and installed sendmail to work with my php mail() function for my phpbb forum (Which is my ultimate goal anyway: to have email working on my phpbb forum). I installed Sendmail, configured my php.ini files to work with /usr/sbin/sendmail -i -t and still no luck. Only this time there is no errors in any error logs, so I have no idea what the server is doing, because my test emails have no been received.

My ultimate goal is to have the php mail() fuction working so I can have my phpbb forum working properly with email registration and whatnot.

---

### Post by Raphial Hebert on 2012-02-14
Bump. I really need some help here.

---

### Post by SlugSlug on 2012-02-14
I use postfix for my phpbb

first get that working before trying with phpbb


you can test with


sendmail [email]your@hotmail.accoun[/email]t

TEST

ctrl+d


then tail -50 /var/log/mail.log to see whats going on


You'll most likley need your ISP smtp adress in postfx's config for a relay

---

### Post by Raphial Hebert on 2012-02-14
> **SlugSlug said:**
> I use postfix for my phpbb

first get that working before trying with phpbb


you can test with


sendmail [email]your@hotmail.accoun[/email]t

TEST

ctrl+d


then tail -50 /var/log/mail.log to see whats going on


You'll most likley need your ISP smtp adress in postfx's config for a relay

What about just using the php mail() function? Is there a way to get that working instead?

---

### Post by Raphial Hebert on 2012-02-15
Bump.

Again.

---

### Post by savanna on 2012-02-17
> **savanna said:**
> Hmmm... Is the mail server even working?


I suggest you go back and read my earlier post :-)

Basic troubleshooting - subdivide the problem and find what works. Does your mail server work at all? Your problem mightn't be PHP or phpbb.

Hard way: install and configure an email client, send a test email.

Easy way: do a **telnet localhost 25** and see if you can manually send a test email. For example: [How to test an SMTP server by using telnet]("http://www.anta.net/misc/telnet-troubleshooting/smtp.shtml")

---

### Post by Raphial Hebert on 2012-02-18
It says the connection to 127.0.0.0 was refused.

---

### Post by SeijiSensei on 2012-02-20
Was 127.0.0.0 a typo? You should be connecting to 127.0.0.1, or just use "telnet localhost 25".

It sounds like you're still using sendmail.  If so, try "sudo service sendmail restart" and see what you get.  If you get an error, try "sudo /etc/init.d/sendmail restart".

---

### Post by Raphial Hebert on 2012-02-22
I restarted sendmail, then tested it using telnet.

I got the same error as before.

Connection refused. 127.0.0.1

(Paraphrased)

EDIT: I also forgot to mention I can edit and configure Sendmail in Webmin.

---

### Post by SeijiSensei on 2012-02-29
Either the sendmail service isn't running, or you have something blocking connections to port 25 like a firewall.  Do you have an iptables ruleset?  Do you allow TCP connections to port 25?

If you aren't running a firewall, or you have not blocked port 25, I suspect sendmail isn't running for some reason.  First try running "ps ax | grep sendmail | grep -v grep" and see whether there is a sendmail process listed in the process table.  If it's running, you'll see a line that reads "sendmail: accepting connections".

I also suggest you install the mailutils package so you can use the command-line "mail" program for testing like this:

```
echo 'test' | mail -s 'test' -v root@localhost
```

That will send a message to the local root account.  The -v will let you observe the entire transaction.

Your best source of help is /var/log/mail.log.

One other thing to examine is /etc/mail/sendmail.cf.  In particular, you should see a line like this:

```
O DaemonPortOptions=Port=smtp, Name=MTA
```

If you have anything else in that line like an IP address delete it and just use the identical directive to that above.  That tells sendmail to listen on all interfaces using port 25.  (Once you've got everything working, you can try re-enabling the restriction that sendmail listen only on 127.0.0.1.)

---

### Post by Raphial Hebert on 2012-03-17
This is the log:
> 
Mar 16 22:40:26 Motherserver sm-msp-queue[3065]: q2H5Dwlc002077: to=www-data, delay=00:18:06, xdelay=00:00:00, mailer=relay, pri=122298, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]


This is after I tried everything the best of my abilities according to your post. I'm completely lost.

---

### Post by Raphial Hebert on 2012-03-18
BUMP.

Please help guys.

---

### Post by Raphial Hebert on 2012-03-18
Bump. It's been quite some days...please help.

---

### Post by Raphial Hebert on 2012-03-22
Bump. Where is the support here? I seriously need help with this, and no one's replying. Come on now. Seriously.

---

### Post by ccrs8 on 2012-03-22
I'm afraid I can't help you in getting your own mail server to work, but I have experience with LAMP servers in general.  I was in charge of a few small servers like you describe at my own job and it was always easier to use the already existing SMTP servers on the network.  Does your ISP have its own SMTP server (the one it instructs you to use when using your ISP-provided email address)?  If so, you can put that server in your PHP configuration file, and then any php email function will use that server.

---

### Post by CharlesA on 2012-03-22
> **Raphial Hebert said:**
> Bump. Where is the support here? I seriously need help with this, and no one's replying. Come on now. Seriously.
No need to be rude. Everyone is a volunteer here.

It really sounds like your mail server isn't set up correctly.

---

### Post by dharmavir on 2012-03-24
I think you should try following:
$ sudo apt-get install tasksel
$ sudo tasksel lamp-server
$ sudo tasksel mail-server

That's it you're done, reply back if it does not work..!

---

### Post by Raphial Hebert on 2012-03-25
But installing the lamp-server will interfere with my configuration that I already have working.

I just need someone to tell me how to correctly install sendmail or postfix because I apparently forgot something or missed a step somewhere.

---

### Post by CharlesA on 2012-03-25
> **Raphial Hebert said:**
> But installing the lamp-server will interfere with my configuration that I already have working.

I just need someone to tell me how to correctly install sendmail or postfix because I apparently forgot something or missed a step somewhere.

Use postfix. It's not that hard to configure. See here:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by Raphial Hebert on 2012-03-25
> **CharlesA said:**
> [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

I spent an hour installing that step by step as carefully as I could following that documentation, and still nothing worked.

---

### Post by CharlesA on 2012-03-25
> **Raphial Hebert said:**
> I spent an hour installing that step by step as carefully as I could following that documentation, and still nothing worked.
How are you trying to set postfix up?

I have it set as a relay going thru gmail, but that might not be ideal for your environment. See here: [http://ubuntuforums.org/showthread.php?t=1939547](http://ubuntuforums.org/showthread.php?t=1939547)

---

### Post by Raphial Hebert on 2012-03-25
> **CharlesA said:**
> How are you trying to set postfix up?

I have it set as a relay going thru gmail, but that might not be ideal for your environment. See here: [http://ubuntuforums.org/showthread.php?t=1939547](http://ubuntuforums.org/showthread.php?t=1939547)

I was first trying to set it up as smtp, but now I just want my php mail to simply work for my forum, and anything else I have planned for the future.

---

### Post by CharlesA on 2012-03-25
> **Raphial Hebert said:**
> I was first trying to set it up as smtp, but now I just want my php mail to simply work for my forum, and anything else I have planned for the future.
You should be able to just install postfix, set it up a an internet site, which is what you do during the install, and then send mail that way.

Does using telnet after postfix is installed work?

```
telnet localhost 25
```

---

### Post by Raphial Hebert on 2012-03-25
> **CharlesA said:**
> You should be able to just install postfix, set it up a an internet site, which is what you do during the install, and then send mail that way.

Does using telnet after postfix is installed work?

```
telnet localhost 25
```

Give me a sec. I'll try it out.

---

### Post by Raphial Hebert on 2012-03-25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 localhost6.localdomain6 ESMTP Sendmail 8.14.3/8.14.3/Debian-9.2ubuntu1; Sun, 25 Mar 2012 09:18:20 -0700; (No UCE/UBE) logging access from: localhost.localdomain(OK)-localhost.localdomain [127.0.0.1]

Hm. Seems to connect fine now, but my php mail test page isn't sending any mail still. 

Here's the php mail code for verification:

<?php
$to = "raphial_hebert@hotmail.com";
$subject = "Test mail";
$message = "Hello! This is a simple email message.";
$from = "raphial_hebert@hotmail.com";
$headers = "From:" . $from;
mail($to,$subject,$message,$headers);
echo "Mail Sent.";
?>

Gonna try sending myself an email through my forum.

EDIT: Still nothing after testing my forum.

---

### Post by CharlesA on 2012-03-25
What does the mail.log say?

If you can connect via telnet, then the mail server is set up correctly.

Try this:

```
echo "Test mail" | mail email@domain
```

See if that works.

---

### Post by Raphial Hebert on 2012-03-25
I'm not seeing anything unusual.

I'm so lost.

---

### Post by CharlesA on 2012-03-25
Can you post this:

```
tail -10 /var/log/mail.log
```

---

### Post by Raphial Hebert on 2012-03-25
```
Mar 25 10:08:18 Motherserver postfix/smtp[5435]: warning: host mothership.iraph-studios.com[76.121.24.34]:25 greeted me with my own hostname mail.iraph-studios.com
Mar 25 10:08:18 Motherserver postfix/smtp[5435]: warning: host mothership.iraph-studios.com[76.121.24.34]:25 replied to HELO/EHLO with my own hostname mail.iraph-studios.com
Mar 25 10:08:18 Motherserver postfix/smtp[5435]: 7E4F64E09B9: to=<root@mothership.iraph-studios.com>, relay=mothership.iraph-studios.com[76.121.24.34]:25, delay=0.24, delays=0.05/0/0.19/0, dsn=5.4.6, status=bounced (mail for mothership.iraph-studios.com loops back to myself)
Mar 25 10:08:18 Motherserver postfix/smtpd[5442]: disconnect from c-76-121-24-34.hsd1.wa.comcast.net[76.121.24.34]
Mar 25 10:08:18 Motherserver postfix/qmgr[5037]: 7E4F64E09B9: removed
Mar 25 10:11:11 Motherserver postfix/postfix-script[7404]: refreshing the Postfix mail system
Mar 25 10:11:11 Motherserver postfix/master[3490]: reload -- version 2.7.1, configuration /etc/postfix
Mar 25 10:11:11 Motherserver postfix/anvil[5444]: statistics: max connection rate 1/60s for (smtp:76.121.24.34) at Mar 25 10:08:18
Mar 25 10:11:11 Motherserver postfix/anvil[5444]: statistics: max connection count 1 for (smtp:76.121.24.34) at Mar 25 10:08:18
Mar 25 10:11:11 Motherserver postfix/anvil[5444]: statistics: max cache size 1 at Mar 25 10:08:18
```

---

### Post by CharlesA on 2012-03-25
Try sending mail to an external email address. That one looks normal because you are sending mail to root.

---

### Post by Raphial Hebert on 2012-03-25
> **CharlesA said:**
> Try sending mail to an external email address. That one looks normal because you are sending mail to root.

I sent the mail to my email: ~snip~

---

### Post by CharlesA on 2012-03-25
Hrm. In that case, the mail server still isn't set up right. For some reason it's pointing to itself.

```
Mar 25 10:08:18 Motherserver postfix/smtp[5435]: warning: host mothership.iraph-studios.com[76.121.24.34]:25 greeted me with my own hostname mail.iraph-studios.com
Mar 25 10:08:18 Motherserver postfix/smtp[5435]: warning: host mothership.iraph-studios.com[76.121.24.34]:25 replied to HELO/EHLO with my own hostname mail.iraph-studios.com
Mar 25 10:08:18 Motherserver postfix/smtp[5435]: 7E4F64E09B9: to=<root@mothership.iraph-studios.com>, relay=mothership.iraph-studios.com[76.121.24.34]:25, delay=0.24, delays=0.05/0/0.19/0, dsn=5.4.6, status=bounced (mail for mothership.iraph-studios.com loops back to myself)
```

This would fix that:
[http://www.cyberciti.biz/faq/postfix-mail-for-domaincom-loops-back-to-myself-error-and-solution/](http://www.cyberciti.biz/faq/postfix-mail-for-domaincom-loops-back-to-myself-error-and-solution/)

---

### Post by Raphial Hebert on 2012-03-25
```
Mar 25 10:31:52 Motherserver postfix/cleanup[8801]: 2BD624E09B9: message-id=<20120325173152.2BD624E09B9@mail.iraph-studios.com>
Mar 25 10:31:52 Motherserver postfix/qmgr[8669]: 2BD624E09B9: from=<>, size=2909, nrcpt=1 (queue active)
Mar 25 10:31:52 Motherserver postfix/bounce[8805]: 26AB34E09B8: sender non-delivery notification: 2BD624E09B9
Mar 25 10:31:52 Motherserver postfix/qmgr[8669]: 26AB34E09B8: removed
Mar 25 10:31:52 Motherserver postfix/smtpd[8806]: connect from c-76-121-24-34.hsd1.wa.comcast.net[76.121.24.34]
Mar 25 10:31:52 Motherserver postfix/smtp[8803]: warning: host mothership.iraph-studios.com[76.121.24.34]:25 greeted me with my own hostname mail.iraph-studios.com
Mar 25 10:31:52 Motherserver postfix/smtp[8803]: warning: host mothership.iraph-studios.com[76.121.24.34]:25 replied to HELO/EHLO with my own hostname mail.iraph-studios.com
Mar 25 10:31:52 Motherserver postfix/smtp[8803]: 2BD624E09B9: to=<root@mothership.iraph-studios.com>, relay=mothership.iraph-studios.com[76.121.24.34]:25, delay=0.24, delays=0.05/0/0.19/0, dsn=5.4.6, status=bounced (mail for mothership.iraph-studios.com loops back to myself)
Mar 25 10:31:52 Motherserver postfix/smtpd[8806]: disconnect from c-76-121-24-34.hsd1.wa.comcast.net[76.121.24.34]
Mar 25 10:31:52 Motherserver postfix/qmgr[8669]: 2BD624E09B9: removed

```

---

### Post by Raphial Hebert on 2012-03-25
Tried a second time after restarting Postfix again, and still it says the same thing. Still loops itself.

---

### Post by CharlesA on 2012-03-25
I'm not sure why it's doing that. It kinda sounds like comcast is blocking port 25, but I don't know.

---

### Post by Raphial Hebert on 2012-03-25
How would I remove the "mail.iraph-studios.com" from it all? It should be localhost.

---

### Post by CharlesA on 2012-03-25
Try reconfiguring postfix:

```
sudo dpkg-reconfigure postfix
```

I think that's the right command.

---

### Post by Raphial Hebert on 2012-03-26
So emailing works now, to an extent.

Nothing is received on any Hotmail or Live accounts, and Yahoo only receives half the emails it feels like receiving. Gmail receives everything.

So, what could this be?

---

### Post by CharlesA on 2012-03-26
> **Raphial Hebert said:**
> So emailing works now, to an extent.

Nothing is received on any Hotmail or Live accounts, and Yahoo only receives half the emails it feels like receiving. Gmail receives everything.

So, what could this be?
That's strange. Have you checked the spam folders?

You might also want to check this site: [http://www.dnsbl.info/](http://www.dnsbl.info/)

---

### Post by Raphial Hebert on 2012-03-26
> **CharlesA said:**
> That's strange. Have you checked the spam folders?

You might also want to check this site: [http://www.dnsbl.info/](http://www.dnsbl.info/)

Yahoo, Hotmail, and Live don't even list it in the spam folders. It's completely blocked, but Gmail receives everything perfectly fine.

I checked the website you sent me, and according to that website, I am not blacklisted.

---

### Post by CharlesA on 2012-03-26
Interesting. Does the mail.log say anything different when you send to gmail and when you send to yahoo or hotmail?

---

### Post by Raphial Hebert on 2012-03-26
Nope. The last log was yesterday when we were last chatting on here.

God. One problem after another. Though Yahoo appears to receive everything, as I'm mistaken, but some emails take up to 15 minutes to receive while other emails are received instantly. Still no luck with Hotmail or Live.

---

### Post by CharlesA on 2012-03-26
That's so strange. I have my mail server set up differently (it relays via gmail, and then send to another gmail address) and I get emails within 1-2 minutes but most of the time it's almost instant.

I haven't really tried yahoo or hotmail tho.

---

### Post by Raphial Hebert on 2012-03-26
> **CharlesA said:**
> That's so strange. I have my mail server set up differently (it relays via gmail, and then send to another gmail address) and I get emails within 1-2 minutes but most of the time it's almost instant.

I haven't really tried yahoo or hotmail tho.

So it's not abnormal for email providers to block your mail server from sending emails to them?

---

### Post by CharlesA on 2012-03-26
> **Raphial Hebert said:**
> So it's not abnormal for email providers to block your mail server from sending emails to them?
It depends on the mail service as far as I know. I just use mine as a gmail reply, so I'm not sure if it's normal behavior or not.

---

### Post by Raphial Hebert on 2012-03-26
> **CharlesA said:**
> It depends on the mail service as far as I know. I just use mine as a gmail reply, so I'm not sure if it's normal behavior or not.

How did you set yours up?

---

### Post by CharlesA on 2012-03-26
> **Raphial Hebert said:**
> How did you set yours up?
Mine is set up like this post:
[http://ubuntuforums.org/showpost.php?p=11760272&postcount=4](http://ubuntuforums.org/showpost.php?p=11760272&postcount=4)

---

