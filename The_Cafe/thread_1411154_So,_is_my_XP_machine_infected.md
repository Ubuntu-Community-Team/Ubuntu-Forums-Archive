---
title: "So, is my XP machine infected?"
date: 2010-02-19
forum: The Cafe
---

### Post by Pogeymanz on 2010-02-19
Actually not mine, but my fiancee's.

Anyway, she uses Yahoo! for email. She does not use any email clients, just Firefox->Yahoo.com

This morning her email account sent out an email to the first 10 people in her address book with some link to a male enhancement web page. This was not address-spoofing because the message was in her sent folder. 

Was this just a random attack on yahoo accounts, or could a virus have somehow key-logged her and somehow configured its own IMAP client to send this stupid email?

I checked the registry: seems fine. No weird processes (that I could spot, at least), and I did a scan with AVG that turned up negative.

She changed her Yahoo! password, but obviously, if this is a virus, it probably doesn't matter.

If I have to reinstall XP, she is going to be totally stressed out over having to back up all her documents and "What if they don't copy correctly?"

P.S. Don't tell me that she shouldn't use XP or Yahoo, or whatever.

---

### Post by Simon17 on 2010-02-19
I've never heard of a virus that spammed through webmail. Could it have been an XSS attack?
Does she stay logged in to Yahoo all the time?

---

### Post by Twitch6000 on 2010-02-19
With a bit of googling this seems to be a flaw in yahoo mail.

Where people can use the flaw to get into your email account and send spam.

So my only idea would be change your password or switch to gmail,msn,wtfever.

---

### Post by Simon17 on 2010-02-19
I did a quick Bing search on it too, and it looks like it is an XSS exploit.

Change her password and log out of yahoo whenever she isn't using it.

---

### Post by Pogeymanz on 2010-02-19
Okay. Then at least it isn't a virus. She did change her password, and I'll let her know to always log out when she's done.

I googled it this morning and didn't get very far. Can you post a link explaining this XSS problem?

---

### Post by T-n-T Handywork on 2010-02-19
As this is an Ubuntu forum, I'll start by suggesting you search for methods of using Ubuntu as a tool to check your XP hard drive. I apologize, but I can't remember exactly where I read it, but you can use the Ubuntu Live CD on your XP machine to do a scan using Clam Antivirus. Also, I would suggest downloading Malwarebytes Anti-malware onto the suspect XP machine and run a scan. I run a part-time computer repair business and have found that if your computer is doing things you didn't ask it to or you think it is, then it's better to error on the side of caution and thoroughly check it out. A lot of the new "garbage" (ie. virus, malware, scareware, etc.) infections are very quick about taking over a system and preventing the owner from using them. It's sad, but true that people make these kind of programs that hurt others. I always tell my clients that the internet is as good as it is bad. It depends on how you use it and being proactive about self-protection. I do not personally use Yahoo, but for certain, you'll want to make sure your machine is safe.
I run dual boot (Ubuntu & XP) and triple boot (Ubuntu, XP, & Win 7) for a reason. Although I'm not that savvy with Ubuntu. In fact I'm a noob, but one thing I've come to appreciate about it is that it's secure and I have an operating system to boot to if windows fails. That's why I back everything up in an Ubuntu file system. That way if a virus hits the MS Operating System, it's not long and I'm back up again. Hope this helps.

---

### Post by TheNessus on 2010-02-19
> **Pogeymanz said:**
> Actually not mine, but my fiancee's.

Anyway, she uses Yahoo! for email. She does not use any email clients, just Firefox->Yahoo.com

This morning her email account sent out an email to the first 10 people in her address book with some link to a male enhancement web page. This was not address-spoofing because the message was in her sent folder. 

Was this just a random attack on yahoo accounts, or could a virus have somehow key-logged her and somehow configured its own IMAP client to send this stupid email?

I checked the registry: seems fine. No weird processes (that I could spot, at least), and I did a scan with AVG that turned up negative.

She changed her Yahoo! password, but obviously, if this is a virus, it probably doesn't matter.

If I have to reinstall XP, she is going to be totally stressed out over having to back up all her documents and "What if they don't copy correctly?"

P.S. Don't tell me that she shouldn't use XP or Yahoo, or whatever.
you should check where your fiancee surfs... 

kidding, kidding!
ok, seriously now: AVG is NOT enough. Get a more serious anti-virus such as NOD32 or the new Norton, AS WELL as at least two good anti malware such as Ad-Aware and Spybot.

---

### Post by Simon17 on 2010-02-19
Pogeymanz: Here is a very in-depth description of the problem
[http://netcooties.blogspot.com/2007/06/yahoo-endangers-users-do-web-sites-care.html](http://netcooties.blogspot.com/2007/06/yahoo-endangers-users-do-web-sites-care.html)

I'm not sure what your level of knowledge on the subject is, but basically, another site pretending to be yahoo uses the credentials stored on your computer to gain access to your webmail.

---

### Post by Simon17 on 2010-02-19
I also want to point out that XSS (cross-site scripting) flaws are on top of the top 25 list discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=1409680") and I'm sure they have been for the past several years.

---

### Post by steveneddy on 2010-02-19
Mt thoughts on this:

1. Yes - if you have a Windows machine connected to the internet, it is vulnerable and probably has already malicious software on there somewhere.

2. Yahoo mail is notorious for spamming other from the inbox of subscribers. for this reason I don't use Yahoo mail anymore. Too much spam.

3. With Yahoo, as has been said before, sign out when not using it, change the PW at least once a month and tell aal of your friends that send you smiley's and junk over e-mail that they are most likely sending little packets of software that can help others spy on you.

I know, sounds ridiculous, but windows users will find that if they simply block images from web mail the occurrences of little attacks like this and others will become minimal.

The web is a horrible place to try and stay secure anymore, especially with e-mail.

---

### Post by katie-xx on 2010-02-19
[SIZE=2][COLOR=Blue]Just for your interest you might want to look at the e-mail headers to see where about the message originated. I will put my money on China:)

This link shows you how to examine the Yahoo message Headers.
[http://help.yahoo.com/l/us/yahoo/mail/original/basics/basics-31.html](http://help.yahoo.com/l/us/yahoo/mail/original/basics/basics-31.html)

Once you have the originating IP address from the mail header move over to here

[http://www.dnsstuff.com/tools](http://www.dnsstuff.com/tools)

and do a WHOIS query.

Also for info: Hotmail have been suffering the same problems recently. I would guss your best bet is to get a GMail account.

Kate[/COLOR][/SIZE]

---

### Post by MichealH on 2010-02-19
I fi remember On the other computers in my network that all Windows I have noticed that they send messages over MSN saying stuff like:

"OMG Caught you out! hahahaha I really loled when I seen this!" But on ubuntu I bet I can visit that site because mine wont be vunerable to that virus but imagine the average user? Theyll get a virus but what else seems bad Is It seems to come from annother person from the contact list and my mam got one off my dad and he said he never went near MSN so I think there are hackers that are getting clever out there!

---

### Post by BETATEST on 2010-02-19
> **MichealH said:**
>  I bet I can visit that site because mine wont be vunerable to that virus but imagine the average user? 

Never say "never" ... :^)  Our world is just as full of malevolent intelligent people as any other platform. ;)

---

