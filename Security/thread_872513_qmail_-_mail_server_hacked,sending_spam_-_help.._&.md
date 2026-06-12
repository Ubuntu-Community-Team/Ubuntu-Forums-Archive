---
title: "qmail - mail server hacked,sending spam - help.. &gt;"
date: 2008-07-28
forum: Security
---

### Post by stoynev on 2008-07-28
Hello, I have problem with one of my mail servers...,
I am using qmail , from 2 days I notice that there is huge load average on the server - 9 and up ..., I stopped its wlan access , when I look at the top table the mail services make big load average, and when I stop qmail the average stops. (qmailctl stop) ..
So I checked the queues of qmail, and saw that My server actually is sending hundreds of mails :/ (last time where 1000+), I deleted them and it starts to send again more and more...,
My problem is that I can't locate the source of the hack, where should I look to stop the process which makes my server sending SPAM..
Thanks. :confused:

---

### Post by Mumbly on 2008-07-28
If I'm understanding this right, your server has not been hacked necessarily, but is acting as an open relay for spammers. Take a look at this site below to see how to stop QMail from being an Open Relay. Apparently QMail is an Open Relay by default (not sure if the Ubuntu package is setup this way or not). In any case, this site shows you what to do.

[http://qmail.jms1.net/relay.shtml](http://qmail.jms1.net/relay.shtml)

Hope it helps! :)

EDIT: Forgot to add this site. This will test whether you are running an open relay or not. Just put in your IP address and click Test for relay (don't worry about the other things such as e-mail address, etc.), and it will scan your system.

[http://www.abuse.net/relay.html](http://www.abuse.net/relay.html)

---

### Post by stoynev on 2008-07-28
> **Mumbly said:**
> If I'm understanding this right, your server has not been hacked necessarily, but is acting as an open relay for spammers. Take a look at this site below to see how to stop QMail from being an Open Relay. Apparently QMail is an Open Relay by default (not sure if the Ubuntu package is setup this way or not). In any case, this site shows you what to do.

[http://qmail.jms1.net/relay.shtml](http://qmail.jms1.net/relay.shtml)

Hope it helps! :)

I believe that this is not the problem , because the server is from more than 1 year working well and the problem started few days ago..., but I will check it, Thanks!

Any other suggestions ? :/

---

### Post by hyper_ch on 2008-07-28
> **stoynev said:**
> I believe that this is not the problem , because the server is from more than 1 year working well and the problem started few days ago...

so? I'd also say open relay.

---

### Post by stoynev on 2008-07-28
Nope , I do have added host to rpchosts allow and deny...,
And if I stop and start or restart the server it starts sending spams and filling the queue with mails even if the LAN cable is unplugged ..... and load average getting high.


EDIT1: I have changed the Qmail hostname and there is not problem now.., load average is normal and the machine is not sending spam messages (I dont see any in qmail queue)
So what was the problem? Somebody or something is attacking/flooding the old hostname?

---

### Post by Mumbly on 2008-07-28
Not sure why switching the hostname would fix this. Perhaps someone on the qmail mailing lists would have a better idea. Here is the site with the official lists.

[http://cr.yp.to/lists.html#qmail](http://cr.yp.to/lists.html#qmail)

Here are the anti-spam techniques used in qmail.

[http://qmail.eclipsi.net/top.html#spam](http://qmail.eclipsi.net/top.html#spam)

From this page, I thought this entry yielded some promise:
> Russ Nelson wrote the selfhelo patch, which causes qmail-smtpd to reject email sent using a HELO hostname equal to your IP address, your hostname, or any hostname without dots. 

It doesn't really explain it though, so I'm not sure.

In any case, if you find out more information, please post it here so it can be of use to others. :)

---

### Post by mcolvin on 2008-07-30
What you're more than likely seeing is "Backscatter" e-mail spamming.  If you haven't patched qmail with the validrcpto patch (Also at the jms1.net site) or with some other valid e-mail address verification scheme, the default behavior of Qmail is to "Bounce" e-mail sent to bad addresses.

What the spammer does is spoof the "From" address of the e-mail, send it to a bogus e-mail address at a valid domain on your server, causing your server to bounce it to teh "From" address, the actual target of the spam.  This is why you see your queue filling up with messages to various e-mail addresses.

This is a PITA.  It's hard to block because it is usually done using a bot net or something that uses multiple servers/hosts to send simulatneously, which floods your server with mail, usually crippling it.

Another use I've recently seen for this technique appears to be to overload "Spamassassin", causing it to timeout, thus allowing other mail, sent to valid accounts, to bypass the spam filtering.  Again, another PITA.

Too bad they've outlawed hanging.  I think it should be allowed for spammers.

---

