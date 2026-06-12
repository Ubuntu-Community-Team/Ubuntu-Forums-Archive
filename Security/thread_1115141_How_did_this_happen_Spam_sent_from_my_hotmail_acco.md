---
title: "How did this happen? Spam sent from my hotmail account."
date: 2009-04-03
forum: Security
---

### Post by SerpicoUK on 2009-04-03
Hi all,

A few months ago I made the switch to ubuntu. Last night, my hotmail account sent a spam email to all my contacts list.

To my knowledge I've not been doing anything I've not done before using Windows/internet. 

I'm using firefox with the no-script plug which I've used for years. I didn't download anything or even open any emails. 

Looking back through yesterdays internet history I didn't visit any websites I've not visited before. And no dodgy websites at all.

Anyone know what caused the spam sending? And what actions should I take now? My confidence in Ubuntu has taken a slight dent - hopefully you guys can reassure me!

Serp.

---

### Post by cariboo on 2009-04-03
It sounds like someone has cracked you hotmail account, probably due to a weak password. It has nothing to do with Ubuntu. Hotmail is a webmail service, that is operating system agnostic. My suggestion would be to close the account and create a new one with a strong password.

Jim

---

### Post by ajgreeny on 2009-04-03
Can't you just change your password to something more difficult to hack?

---

### Post by Mason Whitaker on 2009-04-03
Switch to Gmail, which is a hundred times better with no ads...?
You can also set it up where you can send email from your hotmail account, which is really nifty.

---

### Post by albinootje on 2009-04-03
> **SerpicoUK said:**
> Last night, my hotmail account sent a spam email to all my contacts list.

How did you find out exactly ? There was spam in your outbox ?
Or did one of your contacts complain ?
If there was no spam in your outbox, did you then check the email-headers to see which ip address was used ?
Are you using only webmail, or also a mail-client which connect to hotmail.com ?

You should also realise that email-viruses on infected MS-Windows machines make up pretty random From: and To: addresses (in the emails they send out) bases on addressbooks that the virus comes across.

Apart from that, IIRC, hotmail.com has had security problems in the past where mailboxes could be read and used by others.

---

### Post by Cope57 on 2009-04-03
Microsoft owns Hotmail... go figure.

Hotmail accounts get hacked all the time...

---

### Post by SerpicoUK on 2009-04-03
Everyone has been emailing me telling I've sent them an odd email. Some in my sent box as well.

I find it hard to believe my account has been cracked. If so then whoever did must surely be able to get into 90% of accounts as my account is secured by a long random string of alpha-numeric.

---

### Post by albinootje on 2009-04-03
> **SerpicoUK said:**
> Everyone has been emailing me telling I've sent them an odd email. Some in my sent box as well.

Okay, did you check the email-headers ?
To find out about the possible ip address source, the possible email-client used, and the time it was send around.
> 
I find it hard to believe my account has been cracked. If so then whoever did must surely be able to get into 90% of accounts as my account is secured by a long random string of alpha-numeric.

Do you use https for all your webmail accounts, and pop3-ssl and imap-ssl ? If not, your password could have been sniffed by a 3rd party in between your machine and then destination.

And this could be interesting to read :
[http://74.125.77.132/search?q=cache:z6B1_Bq5MT0J:paper.ijcsns.org/07_book/200805/20080504.pdf&cd=4&hl=en&ct=clnk](http://74.125.77.132/search?q=cache:z6B1_Bq5MT0J:paper.ijcsns.org/07_book/200805/20080504.pdf&cd=4&hl=en&ct=clnk)

---

### Post by SerpicoUK on 2009-04-03
Just http - the emails originated from my own account. Hotmail doesn't display any information on the email regarding what computer sent it. Does look like something cracked my account.

I reckon my password it 100x stronger than the common net user. But I've just been googling brute force attacks...looks like you can buy cracking machines for relatively cheap sums (i.e low level criminal spamming outfits) that would make mince meat out of my (and most peoples) password.

A consequence of computer speed increasing and prices dropping at break neck pace. Can't be too long before a password (that you can remember) just won't protect anything.

Bit of an eye opener. Thanks for all your replies.

---

### Post by SerpicoUK on 2009-04-03
I'm not entirely sure how these things work - but surely microsoft wouldn't allow one ip address to make millions of attempts on a password. Or is there a technical reason as to why they can't stop that?

Makes me wonder if something more sinister isn't going on - some key-logging or something else...

Amazing how much paranoia one spamming email can cause.

---

### Post by albinootje on 2009-04-03
> **SerpicoUK said:**
> 
Makes me wonder if something more sinister isn't going on - some key-logging or something else...

I got the impression that you're using the same password for more than just the MS-Hotmail account, right ?
If you're using the same password to fetch email via pop3 from your ISP then your plain text communication there could have been sniffed. 
I think it's a bad thing that some ISP companies still use the old fashioned plain text pop3, but it's still there :(

And.. are you using wireless at home ? Wifi or Bluetooth ?

Have you been using computers elsewhere and checked your email from your hotmail-account ?

---

### Post by SerpicoUK on 2009-04-04
I only use hotmail for email. No pop3 set up on my computer at all.

I've never accessed my hotmail account from an unknown computer.

From a quick search this sort of thing seems to go on all the time. Not just with hotmail but also gmail and yahoo to name but a few.

Seems that no one is too sure about the cause but some may be viruses, some may be brute force attacks and some may be user names and passwords bought/stolen from other websites/services - seeing that people often use the same or simple variations of user names/passwords.

---

### Post by hyper_ch on 2009-04-05
I'd just host my own email services.

---

### Post by khelben1979 on 2009-04-05
> **Mason Whitaker said:**
> Switch to Gmail, which is a hundred times better with no ads...?
You can also set it up where you can send email from your hotmail account, which is really nifty.

I agree. Does hotmail offer SSL (according to Wiki, SSL has been replaced by [TLS]("http://en.wikipedia.org/wiki/Transport_Layer_Security") now. Did not know this myself) as Gmail?

---

### Post by hyper_ch on 2009-04-05
why bother about tls/ssl if both services will index your mail anyway.

---

### Post by khelben1979 on 2009-04-05
> **hyper_ch said:**
> why bother about tls/ssl if both services will index your mail anyway.

What do you mean by the that? Throw away security thinking? :confused:

---

### Post by hyper_ch on 2009-04-05
what security? when your email runs through hotmail or gmail then Microsoft or Google will auto-analyze it to display nice adds to you. The email is already known... so I wonder why even bother with ssl/tls

---

### Post by glotz on 2009-04-05
> **SerpicoUK said:**
> I'm not entirely sure how these things work - but surely microsoft wouldn't allow one ip address to make millions of attempts on a password. Or is there a technical reason as to why they can't stop that?Yes there is, the attacks these days are distributed, thanks to (Micro$oft) botnets. 
[http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html](http://bsdly.blogspot.com/2008/12/low-intensity-distributed-bruteforce.html)

Ubuntu has pretty secure default settings. The problem is, you can change them. Got some rogue repos, for example? Do **cat /etc/apt/sources.list** Perhaps get and run **rkhunter** and **chkrootkit**.

---

### Post by tturrisi on 2009-04-07
How do you connect to the Internet?  Email usernames and passwords are sent in clear text, so if use wifi then anyone can sniff the username and password.  If wired, they can also be sniffed but someone would need to be connected to your LAN or physically tap the line.

For example, use a laptop in a coffee shop, check your email and I'll show you your email username & password before you finish reading your first new message!

---

### Post by albinootje on 2009-04-07
There's an interesting article here about new ways to attack SSL-based traffic :
[http://www.linux-magazine.com/online/news/attack_on_ssl_users_discovered_tool_sources_released](http://www.linux-magazine.com/online/news/attack_on_ssl_users_discovered_tool_sources_released)

---

### Post by kevdog on 2009-04-07
I posted about this awhile ago.  You must have received the [www.niyacn.com](www.niyacn.com) letter.  Clicking on this link sent to you from a friend propogates this letter to all your contacts -- erases your contact list -- and then sets your vacation responder announcement to keep mailing this letter if anyone attempts to contact you!  See if your vacation response announcement has been altered.  There are a few reports on the 'net about this, but the response from M$ has been tepid.

---

### Post by albinootje on 2009-04-08
> **kevdog said:**
> I posted about this awhile ago.  You must have received the [www.niyacn.com](www.niyacn.com) letter.  Clicking on this link sent to you from a friend propogates this letter to all your contacts -- erases your contact list -- and then sets your vacation responder announcement to keep mailing this letter if anyone attempts to contact you!  See if your vacation response announcement has been altered.  There are a few reports on the 'net about this, but the response from M$ has been tepid.

In the thread about your original posting about this "scam" mentions an .exe file.

The OP in this thread was using Linux. Perhaps with Wine installed, perhaps not, I don't know, but let's not confuse those two things.

---

### Post by kevdog on 2009-04-08
There was no .exe file associated with the email.  If you want I can email you the letter.  I would suggest a google search since others confirm the same behavior as originally described by this poster.  Albeit I haven't seen anything yes or no about Linux, however the reports from the hotmail.com support site are very scant.  It seems like M$ is burying the issue.  BTW, this also affects yahoo accounts as well, but I have seen no reports in association with gmail or any other mass email hosting service.

---

### Post by albinootje on 2009-04-08
> **kevdog said:**
> There was no .exe file associated with the email.  If you want I can email you the letter.  

Can you attach it to a personal message ? Thanks.
> 
I would suggest a google search since others confirm the same behavior as originally described by this poster.  Albeit I haven't seen anything yes or no about Linux, however the reports from the hotmail.com support site are very scant.  It seems like M$ is burying the issue.  BTW, this also affects yahoo accounts as well, but I have seen no reports in association with gmail or any other mass email hosting service.
So you're saying that, no matter what OS is/was used, clicking on that specific website made some sort of connection with another tab in Firefox where the hotmail user was using hotmail emails, and then launched spam emails to all the contacts in that hotmail account.

---

### Post by kevdog on 2009-04-09
I cant confirm the OS other than Windows however it doesn't seem to be windows specific.  

Here is the copy of the email:


Subject: Secure shopping !

Hello!How are you recently?

I would like to introduce a good company who trades mainly in electornic  products.Now the company is under sales promotion,all the products are  sold nearly at its cost.They provide the best service to customers,they  provide you with original products of good quality,and what is more,the  price is a surprising happiness to you!It is realy a good chance for  shopping.just grasp the opportunity,Now or never!The web address: [www.niyacn.com](www.niyacn.com)

---

### Post by albinootje on 2009-04-09
> **kevdog said:**
> The web address: [www.niyacn.com](www.niyacn.com)

Now that you mention it, this is what users for WOT have to say about it : [http://www.mywot.com/en/scorecard/niyacn.com](http://www.mywot.com/en/scorecard/niyacn.com)

Here's one comment :
> 
Like other posters, I had my Yahoo address book stolen (hacked) from my PC, despite having anti-virus, antii-malware, anti-spyware software. A letter was sent to everyone who had appeared in my address book, and that SPAM email appeared in the SENT folder of my yahoo email account.


---

### Post by lisati on 2009-04-09
Another possibility is that some ratbag has forged your email address as the "From:" address - it's easy enough to do if you know how. I've had "bounces" come back for emails I never sent on more than one occasion - recently it was for emails supposedly sent from an email account I haven't used for some time. I usually report the bounces via [spamcop]("http://spamcop.net") with a note attached to the effect that it's backscatter from spam.

---

### Post by wsonar on 2009-04-09
Sorry if this was posted all ready but someone could pfish your myspace or facebook accounts also to get your e-mail and password

---

