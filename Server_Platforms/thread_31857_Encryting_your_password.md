---
title: "Encryting your password"
date: 2005-05-05
forum: Server Platforms
---

### Post by ron126 on 2005-05-05
I have heard about encrption to secure your password. How do u set it up on ubuntu?
i wouldn't want someone to see my password even when i type my password on websites, provided i'm being sniff.  :mad:

---

### Post by Xerampelinae on 2005-05-05
Yeah, if that little lock appears in the bottom right corner of your web browser (firefox, maybe others), then you have an encrypted connection to the web server and your password will be encrypted.

It's more something set up by the web server rather than you.

---

### Post by ron126 on 2005-05-07
So when i log into [www.friendster.com](www.friendster.com) and didnt see any lock icon, it simply means im prone to sniffer attack. I have also try sniffing my connection with friendster's after entering my username and password and they're both seen in clear text.

Do you have a solution for this?

---

### Post by Xerampelinae on 2005-05-07
Well, if friendster.com doesn't support encryption... then encrypting stuff on your end would do no good... in fact it would be harmful, since then you couldn't use friendster.com

But... are you using a wireless internet connection?  There are ways to encrypt the data that is sent from your machine to a wireless receiver... which prevents sniffing.  Unfortunately, I don't know about it.

---

### Post by ron126 on 2005-05-07
tada~, im not using wireless...so no solution???  ](*,)

---

### Post by Xerampelinae on 2005-05-07
Well... I suppose not...

---

### Post by ron126 on 2005-05-07
Xerampelinae has been really supportive O:) , im soo touched.

Ok, maybe i should change my question.

How can you do to find out if your computer is being sniff attack?

---

### Post by LordHunter317 on 2005-05-07
If you're on the web, unless your connection says [https://,](https://,) your traffic can be sniffed.

This is how the internet works.  There is nothing you can do about, so don't worry about it.

Obviously, any data you value (like credit card number, pin, SSN, etc) you don't send over an unencrypted connection.

But the rule of thumb is unless you know it's encrypted from **end-to-end**, it's not.  In this case, there's nothing you can do about it.

---

### Post by ron126 on 2005-05-07
That's both a good and bad news to me...thanks    ;-)

---

### Post by ssam on 2005-05-07
making sure that you use different passwords for different things is a good idea.

also for some one to sniff a packet need to be going through a computer they have access to. roughly speaking, if you are on a LAN then you can see all the packets on that LAN. for example in an internet cafe anyone could see your packets. if you had an unencrypted wireless network, then someone could sit in there car outside your house and sniff your packets.

if you are on a wired internet connection, and you dont share it with other people, then it would be difficult to sniff your packets. people might try to do it if they though they could get credit card details, or some valuable.

useing https, encrypted web pages means that all the data in a packet is encypted, so that even if someone catches the packet they cant read it.

i think the way crackers and bad people get personal information is through 'phising scams' these often look like emails from you bank or paypal/ebay/amazon, which ask you to click a link and verify your details. the link actually takes you to a fake site that looks like your bank's, and the address may even look like your bank's. these are what you should really worry about.

be care full. dont always trust the from address on an email

sam

---

### Post by Xerampelinae on 2005-05-07
This is a good explanation.  I just thought I would point out one technical detail that probably only has academic interest...

In a switched lan, your packets are only sent to the switch and not the other machines, so it's a bit more private.  I believe most networks these days use switches... so most likely you only have to worry about people in control of the routers/switches.

---

### Post by LordHunter317 on 2005-05-07
[QUOTE=ssam]if you are on a wired internet connection, and you dont share it with other people, then it would be difficult to sniff your packets.[/quote]No, it's not.  You're only considering the local LAN.

Traffic between you and the website has to go through several (usually 10-30) or so routers and other machines between you and your destination.  The packet could be potentially sniffed anywhere along this path.

Most people forget to consider the above, and it must be considered.  Once the packet hits your ISP, it's security is out-of-your hands.  If you didn't take proper steps to secure it before it left your machine/network (i.e., encrypt it's contents), then you can't do anything to prevent its contents from being examined.

> be care full. dont always trust the from address on an emailYou should always look at the URL for **any** link in the status bar before you click on it.

[quote=Xerampelinae]In a switched lan, your packets are only sent to the switch and not the other machines, so it's a bit more private.[/quote]That's assuming the switch is configured to not allow promiscuous mode.  If it does, it's still easy to see everything.

>  I believe most networks these days use switches... so most likely you only have to worry about people in control of the routers/switches.Most home networks do not.  Or if they do, they can be bypassed like above.

---

### Post by ron126 on 2005-05-08
[QUOTE=LordHunter317]

  If you didn't take proper steps to secure it before it left your machine/network (i.e., encrypt it's contents), then you can't do anything to prevent its contents from being examined.above.
[/QUOTE]

Can you suggest the proper steps please?

I live in dormitory and my computer is on a lan network. I once tried lan sniffer software and able to see clear username and password.

What can i do to not fall victim into this kind of threat?

---

### Post by LordHunter317 on 2005-05-08
On the web?  As I said before, only use HTTP over SSL (HTTPS) whenever possible.

For other things, it depends.  Do remote administration over SSH.  Don't use FTP, use SFTP wherever possible.

You really need to say: I want to be able to do this before anyone can tell you how to go about doing it securely.

---

### Post by ron126 on 2005-05-08
Ok, so a website without SSL connection simply means your username/password is prone to being sniff attack.

Since i cant prevent my password from being sniff, can i find out if my connection is being sniffed?

---

### Post by LordHunter317 on 2005-05-08
[QUOTE=ron126]Ok, so a website without SSL connection simply means your username/password is prone to being sniff attack.

Since i cant prevent my password from being sniff, can i find out if my connection is being sniffed?[/QUOTE]
 As I said before, unless the connection is encrypted, you must operate under the assumption that your connection is being sniffed, even if it's not.

You can only make the value judgement as to whether some data is unimportant enough to be sent unencrypted by assuming somone is sniffing your traffic.

There aren't any super-easy ways to see if you're being sniffed, and it's near impossible to do past your local LAN anyway.

---

### Post by ron126 on 2005-05-08
[QUOTE=LordHunter317]As I said before, unless the connection is encrypted, you must operate under the assumption that your connection is being sniffed, even if it's not.

You can only make the value judgement as to whether some data is unimportant enough to be sent unencrypted by assuming somone is sniffing your traffic.

There aren't any super-easy ways to see if you're being sniffed, and it's near impossible to do past your local LAN anyway.[/QUOTE]


Ok, so there is no way i can log into [www.frienster.com(which](www.frienster.com(which) has no SSL) and prevent my username/password from being sniffed and view as clear text. 

I already got it, arnt i?  :roll: 

Maybe saying good luck before pressing enter will help.

---

### Post by LordHunter317 on 2005-05-08
[QUOTE=ron126]Ok, so there is no way i can log into [www.frienster.com(which]("http://www.frienster.com%28which") has no SSL) and prevent my username/password from being sniffed and view as clear text.[/quote]Nope.  Obviously, you have to make the choice to not use that service or that the data you send to it isn't important enough to you that you care if someone else is listening.

---

### Post by ron126 on 2005-05-09
Thanks to LordHunter317 and many others, you all are really informative and helpful.  O:)

---

### Post by Jet2k5 on 2005-05-18
Lately I have been getting into the whole " cracking " scene.  The most things that " crackers " protect is their passwords.  Their passwords are just not 1 or 10 letters, they are usually over 30 characters long.  Why do they type such long passwords?  So that if they get attacked by a script kiddie, it won't work!  It's nearly imposible, not even the FBI ( from reading a book about it ) was able to crack it.  

How do they make it so long?  Easy, just take some of your favorite slogans, or famous speeches like the one by Dr. Martin Luther King.  And string them together with others ones.  I can garantee that your password will be literally un-hackable.

So for your question some info is not sent over an encrypted network, but usually firefox does a good job of telling you if it is, such as turning the address bar yellow/orangish color with a big LOCK on it :).

Anyhow just thought that you might need a quick tip on how to create a password, so that you don't have to change it every 1 to 2 months, and instead let it leave for a longer time :)

---

