---
title: "remove Postfix recipient restrictions"
date: 2009-03-15
forum: Server Platforms
---

### Post by artheus on 2009-03-15
Hey!

I'm currently configuring my Postfix Mail Server for the first time..
And I haven't gotten it to work yet.
Cause I will be using it with my Windows XP Thunderbird Mailclient.

And I can see that there are alot of recipient restrictions in postfix. And I wonder. How can I remove those?
Or how can I make it possible for me to send mail to **any** mail adress?

Cheers!

---

### Post by artheus on 2009-03-15
I am seriously starting to think that Postifx is not made to be able to send mails to non-local adresses like @hotmail.com or similar.. Cause I have been searching the net for like three days straight.. and find alot of those who have the same problem as me... and not a single solution (or at least no wolution that works)...

Is this right?

---

### Post by volkswagner on 2009-03-15
I am not sure what you mean postfix restrictions.  I have only encountered issues due to a dynamic ip address.  This is viewed as spam or masked or just banned due to the ip range.  If you have a static IP address from your ISP, I don't know what the issue is.

If you have a dynamic IP address, try using your ISP's smtp server for sending mail.  This is a work around and also saves resources on the server.

---

### Post by artheus on 2009-03-15
[http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions")

That is what I mean with restrictions.. It restricts everything that is not local.. It seems..

Might I ask what configuration you have in the **$mynetworks** field in main.cf?

Cheers

---

### Post by volkswagner on 2009-03-15
> **artheus said:**
> [http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions]("http://www.postfix.org/postconf.5.html#smtpd_recipient_restrictions")

That is what I mean with restrictions.. It restricts everything that is not local.. It seems..

Might I ask what configuration you have in the **$mynetworks** field in main.cf?

Cheers

```
mynetworks = 127.0.0.0/8
```


Again, I am using my ISP's smtp server in...

```
relayhost = smtp-server.myisp.com
```

---

### Post by artheus on 2009-03-15
Well.. The thing is that I do not want to use my ISP's smtp-server. I want my own. And my ISP says that they rather we didn't use their smtp-server, because of their traffic is limited.
So I would really love the day when my postfix smtp configuration works. Cause the only reason I installed Postfix was because of the smtp-server.

---

### Post by volkswagner on 2009-03-15
Do you have a static IP address?

I followed the [flurdy]("http://flurdy.com/docs/postfix/") docs how to.  Although I have not completed the advanced portion for filtering spam handling, etc., the setup works.  The how-to takes several hours for this  newbie to get a working setup.

  I particularly like the virtual mailbox setup.  This allows me to run mail servers for multiple domains.  The drawback is now usernames have to be the full email address.  This is necessary in case domain1 and domain2 both end up with a user "john smith".  So when john smith configures his email client or logs into webmail his username will be [email]johnsmith@domain1.com[/email].  Not a big deal considering the ability to host multiple domains' mail.

I have read the info from the link you provided.  It is very confusing to me.  The breakdown between local and remote particularly.  Let it be known.  Postfix DOES allow you to send mail anywhere.  I had it working using my own domain, except as I stated, often would get rejected by certain domains not allowing a dynamic ip sender.

From my main.cf```

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
```

With the flurdy how-to, use of virtual domains with mysql backend handles the virtual mailboxes, domains, etc.

I am fairly certain that the only change I made to main.cf was the relayhost.  I had to do this because gmail and many other hosts reject mail from a dynamic host.

Please, I am not expert.  If you have a static ip and want a simple setup, perhaps you can use one of the other directives.

Do realize, the more open you make it, the more likely outsiders try to use your server to send spam.

---

### Post by artheus on 2009-03-15
It seems as though I have got a dynamic IP... Which is not good... :/
Is there any way of making my IP static?

---

### Post by volkswagner on 2009-03-15
You have to ask your provider.  For me I would have to get RoadRunner business class for $150/mo vs. my current $45/mo.  Some people say an added $5 gets one from their provider, I don't know who though.

---

### Post by wkulecz on 2009-03-17
Assuming locally generated mail is handled correctly, I believe I had a similar issue in this thread:
[http://ubuntuforums.org/showthread.php?t=1097249](http://ubuntuforums.org/showthread.php?t=1097249)

Although receipent restrictions appeared to be the issue, it wasn't.

I made a mistake in the mynetworks= setting.

I believe the line:
mynetworks = 127.0.0.0/8
is what is limiting you to accepting only local mail.

I changed mine to:
mynetworks = 192.168.1.0/8 127.0.0.0/8 
initially and still had problems causing me to go down the receipent restrictions path.

The real solution was the correct mynetworks line:
mynetworks = 192.168.1.0/24 127.0.0.0/8

Replace the 192.168.1.0 with your subnet.  its /24 for class C, /16 for class B and /8 for class A subnets.  I had it backwards wich rejected everything but local mail generation. 

Wasted lots of time on a typo :(

Get it to work first, then add further restrictions as necessary for your needs.

If you have static IP you most certainly need further restrictions as otherwise you will be a spam relay for every host on your ISP's subnet!

Your problem with dynamic IP is accepting smtp mail from other peers, since they will not be able ro reliably find you.  You probably want incoming mail via your ISP's POP or IMAP service, and only outgoing mail relayed via your smtp server.

To be honest, if you are using only using Thunderbird, you are almost 100% for sure better off using your ISP's POP/IMAP and SMTP servers to send recieve Email directly with T-bird.

HTH,
--wally.

---

