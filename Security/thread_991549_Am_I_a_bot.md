---
title: "Am I a bot?"
date: 2008-11-23
forum: Security
---

### Post by pollywog on 2008-11-23
I take care of my Grandfather's computer, which was running gutsy, and he got a message from his ISP informing him that his email account had been flagged as being the point of origin for spam e-mailings, and that he likely had a virus hijacking his computer. He is using Thunderbird, so I peeked in the "sent" folder, and found nothing odd. I just performed a clean install of Intrepid, so I don't think that there could be anything malicious on there now, but the question is, could someone have been using his box to spam, and if so, how could I keep this from happening in the future? I tend to think that someone likely cracked their password, and was monkeying around directly at the server, I just wondered if a virus was possible/likely?

---

### Post by Afkpuz on 2008-11-23
Virus?  Very unlikely.  Password?  More likely than a virus

---

### Post by Skripka on 2008-11-23
His email account or his IP# was the source of spam?


Odds are his account was compromised--change his password methinks.

---

### Post by Dr Small on 2008-11-23
The password theory is plausible, if their password was semi-weak, but unless you have Postfix setup on the system as an open relay (which I doubt) then no one has been using his system to spam others.

Another theory which could be plausible is that spammers are using his email address to send their spam around, which someone has reported to the ISP, wherein they flagged the account as the origin of spam. I have seen this happen with my parents email address, and spammers were using it for the From address.

Dr Small

---

### Post by solitaire on 2008-11-23
If it's from his IP address it sounds like open relay spamming, are you on a fixed IP address?

If it's from his account (anyone can log into it anywhere and send spam!) then change all passwords.

If not someone else may have used that IP address and one of those 'Spam cop' type agency flagged the IP address as spaming, by the time the ISP passed on the warning you've picked up that IP address. Some ISP's get auto flagged as spammers (AOL UK flagged and banned all BT's email traffic from it's network for a while a few years ago over a small industry tiff!!)

check the pc on a ferw of these checkers (I've not tried these!)

[http://spamlinks.net/prevent-secure-relay-test.htm](http://spamlinks.net/prevent-secure-relay-test.htm)

Just to make sure everything is fine at the PC's end..

---

### Post by Dr Small on 2008-11-23
> **solitaire said:**
> If it's from his account (anyone can log into it anywhere and send spam!)

You don't have to be logged into the account to send mail from it.

---

### Post by cariboo on 2008-11-24
I had a similar problem, I was using my origional email, that I got in 1994, it had been around so long that it was available in dozens of hits in Google. I never had my ISP send me an email about generating spam, but I got countless emails from other organizations about spam. My email address was used even thought the emails  did not go through my account. It finally got to the point where I was getting so much spam that I finally gave up the account.

The best thing might be to just create a new email account.

Jim

---

### Post by brian_p on 2008-11-24
> **pollywog said:**
> 

. . . . .  but the question is, could someone have been using his box to spam, and if  I tend to think that someone likely cracked their password, and was monkeying around directly at the server, I just wondered if a virus was possible/likely?

My money would be on Dr Small's theory in the second paragraph of post #4. If you feel like pursuing the matter ask your ISP for copies of some of the mails **with the complete headers**.

---

### Post by nubdora on 2008-11-25
Dr. Small is correct. Lately, I've been receiving emails from myself addressed to myself about various online prescription offers. Unless I'm sleep-computing and my subconscious is trying to drop a hint about organ lengths, this must be the new spam bandwagon.

---

### Post by amac777 on 2008-11-25
I think it is quite possible your grandparent's computer was a bot if the following two conditions are both true:

1. You setup an ssh server (or vnc or whatever) on their computer so you could login remotely and help them maintain their computer.
2. Either your username/password or their username/password were easy to guess. (ie, common account names with dictionary word or easy passwords)

With that combination, in my opinion, it's only a matter of time before some script kiddie hacks in and installs a whole bunch of stuff on your computer. In my opinion, they don't even need root/sudo privledges to turn your computer into a bot because regular user privledges are enough to run bot programs and send emails etc.

If that is what happened, you can probably solve it by:
1. reinstalling
2. use good (strong) passwords

And for extra safety:
3. configure ssh to only allow your account to login
4. install denyhosts to automatically block people that try to hack in

---

### Post by kevdog on 2008-11-25
I'd reiterate to take a look at the entire email header.  I guess no one on this thread has ever used mixmaster.  Using mixmaster its totally possible to send anonymous email with anything specified in the "from" field.  Usually however somewhere in the header there will be some clue that its gone through a mixmaster gateway.  Although I'm sure it can be used for nefarious purposes, sending anonymous email to friends -- particularly the first few times -- with the from field labeled from their boss at work creates quite a reaction -- very comical -- and short-lived excitement.  Use with care!!

Kind of a preview of how to do it (although there are other ways also :)): [http://www.linuxjournal.com/video/anonymize-your-emails-mixmaster](http://www.linuxjournal.com/video/anonymize-your-emails-mixmaster)

---

### Post by Dr Small on 2008-11-26
> **kevdog said:**
> I'd reiterate to take a look at the entire email header.  I guess no one on this thread has ever used mixmaster.  Using mixmaster its totally possible to send anonymous email with anything specified in the "from" field.  Usually however somewhere in the header there will be some clue that its gone through a mixmaster gateway.  Although I'm sure it can be used for nefarious purposes, sending anonymous email to friends -- particularly the first few times -- with the from field labeled from their boss at work creates quite a reaction -- very comical -- and short-lived excitement.  Use with care!!

Kind of a preview of how to do it (although there are other ways also :)): [http://www.linuxjournal.com/video/anonymize-your-emails-mixmaster](http://www.linuxjournal.com/video/anonymize-your-emails-mixmaster)
I have also done this same thing by writing a program in Php to accept input for the From field, To field and message contents. It is very trivial.

But to look at this from a spammers point of view, he is only getting to send his product out to one email address, when the From headers are fake addresses. The person clicks reply, and their message never gets delivered.

With spoofing the From headers with a legitimate address, he is increasing his odds of targeting 2 people with his product, instead of one. If a person clicks reply to the originating email, the innocent person who was in the From headers gets the email too, and if he is stupid, he may buy the scam too.

Their tactics involve strategy and greed.

Now, if someone wants to report an email address for spamming them, the email address is legitimate, instead of some fake made up address generated by the bot. Of course, the bots use Open Relay SMTP servers to send flood their spam through, so the IP Address of the sending server is that of the SMTP server that never secured itself.

Thus, the spam bots make off again, without a trace, continuously collecting revenue.

---

### Post by kevdog on 2008-11-26
That is why open relay smtp servers are "dangerous" in one sense of the word!

---

