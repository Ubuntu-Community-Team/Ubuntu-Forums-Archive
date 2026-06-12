---
title: "[SOLVED] Problem receiving mail at Citadel with Apache"
date: 2008-08-11
forum: Server Platforms
---

### Post by R.Bucky on 2008-08-11
Here is the skinny - I currently host my web pages/blog with an Apache2 server using Ubuntu 7.10. I am using postfix for my Wordpress blog/etc.. The problem is that I cannot receive email using Citadel. I can send internally, but cannot receive. Hmmm. The Citadel forums were no help, nor were the FAQ/Knowledge Base on the Citadel site.

Here is what I have done so far:
(1) Update my firmware on the router to accept ports 504, 82(http req.), 587, 993, 465, 2020, and 5222 as per the standards. 
(2) Update my main.cf to reflect my FQDN
(3) Changed the FQDN in Citadel to buckyspalace.net and update 'Local Host' and 'Smart Host' to reflect the smtp.buckyspalace.net address.
(4) Edited my DNS at Network S. by adding mail servers to the affect of smtp.buckyspalace.net, mail.buckyspalace.net, and buckyspalace.net. That should cover it.
(5) What the hell!?!?

Does anyone have a clue why I cannot receive emails? 

I would appreciate any guidance or suggestions. 

~Mark
[http://buckyspalce.net](http://buckyspalce.net)
[email]buckman1@gmail.com[/email]

---

### Post by devonps on 2008-08-11
Lets start with the obvious: Is your ISP blocking port 25?

Then have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=884228") and see if anything there can help.

Finally have you tried nslookup?

Steve.

---

### Post by perfecttao on 2008-08-11
Ok....lets start with the basics and check that the mail server is accepting inbound connections on port 25 from internally.

Start with the server itself - telnet to localhost on port 25.  You should see the banner that suggests Citadel (not postfix) is accepting mail.

If this works, try from another host externally - using the ip address, not the FQDN.  This should also accept connections on port 25.

If this works, then it must be a DNS issue.  If not then you should have more information to go on....

---

### Post by jamesrfla on 2008-08-11
All I did was get citadel-suite and it came up with info to out in including integration into apache2. Then I setup everything in the administration tab and then in my router port forward port 25 for SMTP and port 80 for HTTP.

---

### Post by R.Bucky on 2008-08-11
Ok, I found out that port 25 was indeed blocked. I moved the services to other ports that check out on canyouseeme.org. I placed a screenshot of my new ports [here]("http://buckyspalace.net/files/53111218497626citadelports.png"). I decided to get rid of port 25 because comcast blocks.  They are all open. My hosts output is:
```
buckyspalace.net has address 24.18.97.15
buckyspalace.net mail is handled by 10 smtp.buckyspalace.net.
buckyspalace.net mail is handled by 30 buckyspalace.net.
buckyspalace.net mail is handled by 20 mail.buckyspalace.net.
buckyspalace.net mail is handled by 40 smtp.comcast.net.

```
It is strange that I received all 36 emails that I sent to myself today from my gmail account to [email]mark@buckyspalace.net[/email] with a mailer-daemon. A little overwhelming. 
Can anyone help on the next step?

---

### Post by jamesrfla on 2008-08-11
What is it that you need help on next?

---

### Post by R.Bucky on 2008-08-11
The problem: I cannot receive emails at my [email]mark@buckyspalace.net[/email] email address in Citadel. I just sent myself an email from Gmail to [email]mark@buckyspalace.net[/email]. It came back with this:

This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    [email]mark@buckyspalace.net[/email]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 5.1.0 Authentication required (state 13).

  ----- Original message -----

Received: by 10.181.5.4 with SMTP id h4mr4199439bki.37.1218498493202;
       Mon, 11 Aug 2008 16:48:13 -0700 (PDT)
Received: by 10.181.7.6 with HTTP; Mon, 11 Aug 2008 16:48:13 -0700 (PDT)
Message-ID: <f9ff80030808111648g5089463fv149c2ff2bebbc31@mail.gmail.com>
Date: Mon, 11 Aug 2008 16:48:13 -0700
From: "Mark I. Moore" <buckman1@gmail.com>
To: mark <mark@buckyspalace.net>
Subject: alskdj
MIME-Version: 1.0
Content-Type: multipart/alternative;
       boundary="----=_Part_16973_11404411.1218498493208"

------=_Part_16973_11404411.1218498493208
Content-Type: text/plain; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit
Content-Disposition: inline

alskdj

--
Mark I. Moore
[http://buckyspalace.net](http://buckyspalace.net)

  ----- Message truncated -----

---

### Post by jamesrfla on 2008-08-11
You need to go into your router and forward the SMTP port which will be 79 since you changed it. Then after you do that it should work. I am not sure SMTP will do its job with the port changed but it should work. Also reboot citadel or reboot your computer.

---

### Post by R.Bucky on 2008-08-11
Nope, that did not do the trick. I admit that I am puzzled. Here is the gmail return:
This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    [email]mark@buckyspalace.net[/email]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 5.1.0 Authentication required (state 13).

  ----- Original message -----

Received: by 10.180.231.20 with SMTP id d20mr4228879bkh.11.1218500131932;
       Mon, 11 Aug 2008 17:15:31 -0700 (PDT)
Received: by 10.181.7.6 with HTTP; Mon, 11 Aug 2008 17:15:31 -0700 (PDT)
Message-ID: <f9ff80030808111715t3bbd3caduced4de29d62cd214@mail.gmail.com>
Date: Mon, 11 Aug 2008 17:15:31 -0700
From: "Mark I. Moore" <buckman1@gmail.com>
To: mark <mark@buckyspalace.net>
Subject: from gmail
MIME-Version: 1.0
Content-Type: multipart/alternative;
       boundary="----=_Part_17055_23582756.1218500131921"

------=_Part_17055_23582756.1218500131921
Content-Type: text/plain; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit
Content-Disposition: inline

I chose port 79 at random because of the comcast issue.

---

### Post by jamesrfla on 2008-08-11
Maybe port 79 doesn't work too. My friend had comcast and he couldn't do anything other than get on the web. I think your in trouble unless you pay a bit more so you can have those ports open. Try calling or do a live chat with comcast and tell them that all my TCP ports are blocked and they might send you a link with instructions on how to configure your modem to allow the port like I had to do with my modem so I can host my mail server or tell you have to pay money to do that.

---

### Post by R.Bucky on 2008-08-11
I was dreading the phone call to comcast. I am baffled because the port is open, as verfied by canyouseeme.org. But, something is in the way. Thanks for the quick replies. 
~Mark

---

### Post by jamesrfla on 2008-08-11
Do you have a domain or something?

---

### Post by R.Bucky on 2008-08-11
Yes, I am using Ubuntu 7.10 with an apache2 server, Gnump media server, and Citadel. I host my own junk man! [http://buckyspalace.net](http://buckyspalace.net)

---

### Post by jamesrfla on 2008-08-11
If you are hosting you own web site then maybe comcast isn't the problem. It is just you can't use port 25. Interesting.

---

### Post by R.Bucky on 2008-08-11
I am online with one of their support staff now. I realized that the finger utility uses port 79, so I switched to 81. Still a no go. I will see what comcast has to say.

---

### Post by R.Bucky on 2008-08-11
Well, comcast says that they are not blocking port 25. While, their web site states clearly that they are blocking it for smtp. That was almost worthless. It was funny when the representative typed, 'we do not support Citadel or Linus.' I love that...

---

### Post by R.Bucky on 2008-08-11
I frickn' did it!!!! Cheese and rice.

Ok, so I placed the mailserver back on port 25. The stopping point for Citadel receiving email was the ServerIPAddress listing in Citadel's Site Configuration > Network Services. I was using my hard ip address as listed on whatsmyip.org. Instead, I substituted the router ip address. BAM!!!

There we have it! Silly, silly things. Thanks all.

~Mark

---

### Post by R.Bucky on 2008-08-16
Problem solved. I wrote a tutorial on what I have done.
[http://buckyspalace.net/linux/tutorials/citadel_configuration/](http://buckyspalace.net/linux/tutorials/citadel_configuration/)

---

