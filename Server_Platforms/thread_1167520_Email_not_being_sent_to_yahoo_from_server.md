---
title: "Email not being sent to yahoo from server"
date: 2009-05-23
forum: Server Platforms
---

### Post by redbrad0 on 2009-05-23
I have tried to send a email to my yahoo from our server and it never gets delivered (not into the spam or anywhere). So a couple questions

1. How can I tell what emails are in Queue on the server that are waiting to be sent?

2. How can I tell if the email server is even running?

3. How do I restart/start the email server?

Thanks for your time,
Brad

---

### Post by cariboo on 2009-05-23
It is pretty hard to help with so few details, which mail server are you using? Do you have a staic ip address? If your are using dyndns or a similar service your email may be getting bounced.

---

### Post by kustomjs on 2009-05-23
can you telnet into it? do you have the ports open if on router? are you using domain keys? do you know if your ISP is blocking ports? the easiest way to find out if your ISP is blocking ports go to canyouseeme.org and type in port 25 and port 110. like cariboo907 we need more details of your server before we can help you out.

---

### Post by mellowd on 2009-05-23
And your MTA is what?

---

### Post by redbrad0 on 2009-05-23
Sorry I guess I should of supplied more info, I thought everything used was for servers and used the same email server.

We have a server that has been working fine for a year. I am not a unix guy, the one that manages our server I can not get ahold of right now so I am not sure what the email server is but for some reason Exim is sticking in my head. Anyway to tell?

The IP's, port's or nothing has changed as it is a dedicated server with dedicated IP Address. I can telnet (using putty) into the mail server but just have not been able to find anything.

---

### Post by mellowd on 2009-05-23
> **redbrad0 said:**
> Sorry I guess I should of supplied more info, I thought everything used was for servers and used the same email server.

We have a server that has been working fine for a year. I am not a unix guy, the one that manages our server I can not get ahold of right now so I am not sure what the email server is but for some reason Exim is sticking in my head. Anyway to tell?

The IP's, port's or nothing has changed as it is a dedicated server with dedicated IP Address. I can telnet (using putty) into the mail server but just have not been able to find anything.


Run ps -e to see if you can see any exim, qmail, postfix and so on processes

---

### Post by redbrad0 on 2009-05-23
I didn't see anything buy I just went to my command prompt and did a telnet to my server and it responded back with "ESMTP Postfix <Ubuntu>"

---

### Post by HermanAB on 2009-05-23
First verify that your DNS is working.  Maybe your domain expired or something equally stupid.

$ nslookup mail.example.com
$ dig mail.example.com MX


Since you are running postfix, go to the postfix web site and start reading.

---

### Post by kustomjs on 2009-05-23
if you got a domain name is your cname and aaa pointing at your IP address? because if not is not going to send out.

---

### Post by gombadi on 2009-05-23
Can I be the first to suggest that you have a look at the email server logs to see what it is saying.

If you are running exim they are normally in /var/log/exim/main.log or other files in that directory.

At least that will give you an indication of the type of problem when you are sending to yahoo - connection refused, connection timed out, rejected because ... etc.

---

### Post by redbrad0 on 2009-05-24
Thanks thats what I was wanting is to see the logs. But I know when I used to have a windows server I could see a list of all the emails in queue that are needing to be sent out and different things like that. Are there any other things I can look at other then the logs?

Side Note:
I found it odd that nobody has reported problem with email to me but I wasnt able to send a email to my other email which is yahoo. I tested and sent it to another email address outside our server and it went through. Finally late last night yahoo sent me a bounce message which shows the problem. I submitted a message to yahoo postmaster. We don't spam or anything else, send one email a month but send out emails when people buy things. We have 35,000 members which 8,000 are yahoo and no longer getting their emails :-(
              The mail system <xxxxxxxxx@yahoo.com>: delivery temporarily suspended: host f.mx.mail.yahoo.com[68.142.202.247] refused to talk to me: 421 4.7.1 [TS03] All messages from xx.xx.xx.xx will be permanently deferred; Retrying will NOT succeed. See [http://postmaster.yahoo.com/421-ts03.html](http://postmaster.yahoo.com/421-ts03.html)

---

### Post by albinootje on 2009-05-24
> **redbrad0 said:**
> I didn't see anything buy I just went to my command prompt and did a telnet to my server and it responded back with "ESMTP Postfix <Ubuntu>"

With postfix you can use the command "mailq" to see whether email is still in the queue for some reason.
For that you have to be logged in to the server itself.

---

### Post by albinootje on 2009-05-24
> **redbrad0 said:**
>  All messages from 66.135.56.12 will be permanently deferred; Retrying will NOT succeed. 

I just checked your ip address in the following blacklists :
[http://www.spamcop.net/](http://www.spamcop.net/)
[http://www.au.sorbs.net/](http://www.au.sorbs.net/)
[http://www.spamhaus.org/](http://www.spamhaus.org/)
and that's all fine, but this one :
[http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx)
complains.. 

> 
Blacklist Name	 	Status	Reason	TTL	Response Time (ms)
BARRACUDA	Listed	LISTED	Detail
Return codes were: 127.0.0.2	898	16

Could be harmless, but see for yourself.

---

### Post by redbrad0 on 2009-05-24
> **albinootje said:**
> 
[http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx)
complains.. 


Could be harmless, but see for yourself.

I went ahead and requested removal from this. Thanks for the info

---

### Post by albinootje on 2009-05-24
> **redbrad0 said:**
> I went ahead and requested removal from this. Thanks for the info

Okay, but.. you should have your system-administrator find out what the real problem was.. or is.

Getting yourself removed from a blacklist without making any changes, or doing any research, doesn't give you a clue about what happened, does it ?

What if there was someone in the LAN with an infected MS-Windows computer that started sending out spam through your ip address ?
If the infected MS-Windows machine is still there, then it is possible that you'll end up in blacklists again, and then it will only become harder to get out of those blacklists because you haven't done anything concerning your setup.

---

### Post by windependence on 2009-05-24
Do you have a PTR record (reverse DNS) set up for your domain? Mail servers are getting picky today. I usually cannot send to some of the big ones without having PTR set up for the domain.

-Tim

---

### Post by albinootje on 2009-05-24
> **windependence said:**
> Do you have a PTR record (reverse DNS) set up for your domain? Mail servers are getting picky today. I usually cannot send to some of the big ones without having PTR set up for the domain.

Possible, yes.

The yahoo link that the OP gave actually leads to this :
[http://help.yahoo.com/l/us/yahoo/mail/postmaster/basics/mltapbprctcymal.html](http://help.yahoo.com/l/us/yahoo/mail/postmaster/basics/mltapbprctcymal.html)

which mentions :
> 
Pay attention to your reverse DNS of your IPs that send mail. If the reverse DNS entry looks like a dynamically assigned IP address instead of a static mail server, Yahoo! is more likely to downgrade your sending reputation.


---

### Post by kustomjs on 2009-05-24
well it could be sent but emails will be sent to spam if you do not have domain keys setup on your server.

---

### Post by windependence on 2009-05-24
Can you elaborate? Maybe I'm used to another term. Domain keys?

-Tim

---

### Post by kustomjs on 2009-05-24
yahoo mail server does require domain keys before your message is sent if you do not have domain keys on your server your mail from your server will not be sent or if it does been sent yahoo will throw the email into spam.

here is wiki about domain keys.
[http://en.wikipedia.org/wiki/DomainKeys]("http://en.wikipedia.org/wiki/DomainKeys")

---

### Post by albinootje on 2009-05-24
> **kustomjs said:**
> yahoo mail server does require domain keys before your message is sent if you do not have domain keys on your server your mail from your server will not be sent or if it does been sent yahoo will throw the email into spam.


Interesting, but the emails from the OP are permanently being rejected by Yahoo, not just temporarily for the reason of missing 
DKIM.

And, by the way, when did yahoo start using it actively ?
I cannot clearly find that anywhere yet.

[http://answers.yahoo.com/question/index?qid=20080402111559AAR0qW7](http://answers.yahoo.com/question/index?qid=20080402111559AAR0qW7) (1 year ago)
[http://www.mail-archive.com/dkim-milter-discuss@lists.sourceforge.net/msg01330.html](http://www.mail-archive.com/dkim-milter-discuss@lists.sourceforge.net/msg01330.html)
(nov.2008)
[http://www.rentvine.com/blog/index.php/yahoo-email-451-and-421-frustration/](http://www.rentvine.com/blog/index.php/yahoo-email-451-and-421-frustration/)
(see comments)

---

### Post by kustomjs on 2009-05-24
yes yahoo does look at the domain keys if you ever logged into a yahoo mail account it will show you this:

[IMG]http://www.eserv.ru/img/domainkeys-yahoo.png[/IMG]

[IMG]http://help.campaignmonitor.com/img/help/88-domainkeys-yahoo.png[/IMG]

it could be that yahoo is rejecting the email because of this if not then I dont know what else it could be.

have you tried to send to different domains like hotmail.com, aol.com?

---

### Post by redbrad0 on 2009-05-26
Thanks everyone for their help. It appears I am now getting yahoo messages again, come to find out they were blocking me because a php file contained a way where people could email other users so our server was being blocked due to the high volume of spam. I added in where I was CCed on the emails, and I got about 10 emails in a minute. Who knows how long this was going on but I was able to get it all going. 

Now time to get some of these ISP's to allow for our email to go through again :(

---

### Post by windependence on 2009-05-26
After some research it appears that if you have correct PTR then yahoo will not send you to the junk bin. They are trying to push domain keys as the standard, but as far as I can tell there aren't many providers using it yet.

-Tim

---

