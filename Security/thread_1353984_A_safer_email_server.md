---
title: "A safer email server???"
date: 2009-12-13
forum: Security
---

### Post by PepeLapiu on 2009-12-13
Hi, I have been using Gmail for a while and before that, MSN and Hotmail. But I have some concerns about Google and MSN's privacy policy.

Can anyone here suggest a different email server accessible to all? Something safer and more private then Google and MSN?

Maybe something designed directly for/by Linux or Ubuntu users? 

Thanx ahead for your help, the Linux community really is a bunch of great peep-hole.

Cheers,
PepeLapiu :D

---

### Post by BkkBonanza on 2009-12-13
If you're really concerned about privacy then you shouldn't be using any public email server. I doubt google is much different then the rest of them, and probably better for security practices - though more of a target perhaps for attacks.

For privacy you would want to run your own mail server. The software is all freely available in the Ubuntu repos but you really need to have a machine with 24/7 connection to the net. Hence, in general you probably should run it on a small VPS server account. Fact is, wherever you put your email it is potentially hackable by someone.

Google at least uses SSL for access which is better than many others still using unsecured POP3. If you have emails you really want private I'd say using Thunderbird with Enigmail (gpg encryption) is likely one of the best options. Other options also work. At least this way if Google (or whoever) is secretly stealing your email at least they can't see the content of the encrypted messages.

The downside to encrypted email is that no one out there except tech nerds is using it. I tried to get my family members to do it but they all just shrugged.

---

### Post by phillw on 2009-12-13
> **PepeLapiu said:**
> Hi, I have been using Gmail for a while and before that, MSN and Hotmail. But I have some concerns about Google and MSN's privacy policy.

Can anyone here suggest a different email server accessible to all? Something safer and more private then Google and MSN?

Maybe something designed directly for/by Linux or Ubuntu users? 

Thanx ahead for your help, the Linux community really is a bunch of great peep-hole.

Cheers,
PepeLapiu :D

IMHO, I've used g-mail since it's very, very early days. Apart from one successfull hack-attack on my account - It has run faultlessly since Dec 2004. I'm not overly concerned over their privacy policy, because the authorities can access any internet activity any time they apply to a court.

I like google-apps e-mail system, it is an easy way to put email onto a small web-area for free.

My vpolink account is a paid for version of google-apps, and the owner has added a virus scanner to it - to stop a 'nasty' being forwarded from me to an unsuspecting Win user.

I'm just about to put this one onto my server ... This *should* be fun !!!

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

So, you could always make your own.

Phill.

---

### Post by BkkBonanza on 2009-12-13
I've been using google apps for email on several of my domains as well and it's always worked very well for me. I use name.com for my domains and every domain I register gets free google apps, so I've offloaded all my email onto that and don't bother running my own server now. Heck, they have about 5-6 servers I CNAME into so that's way more redundant than me.

Is there an issue with privacy? No idea. Not for me so far anyway.

---

### Post by tubbygweilo on 2009-12-13
> The downside to encrypted email is that no one out there except tech nerds is using it. I tried to get my family members to do it but they all just shrugged.
So, so true.

It is often of more use to know what information is held in the to:, cc: and bcc: fields of an email as this can not be encrypted but must travel as normal text. Whom you contact can not be hidden and their is nothing you can do about it but what you say can be hidden so encrypt and hide amongst the millions of other email crossing the web each and every hour of the day and keep your fingers crossed.

---

### Post by PepeLapiu on 2009-12-14
> **BkkBonaza said:**
> Is there an issue with privacy? No idea. Not for me so far anyway.

Here is what I have to offer about Google: they track your IP and they also track your searches and this information is used to direct advertising to you. Next time you log into your Gmail account, look at the advertising scroll at the top, you will find that they seem to know pretty well the kind of person you are.

Think also about China and how Google was instrumental in structuring the Big Brother type of Internet they have there. That really is only a test, a model for future plans world-wide.

I also have it of good source that your google searches supposedly remain confidential, however the advertising that is sent to you isn't confidential and so the 'guberment' has been working together with Google to obtain this track record of advertising sent to you to profile you. I have personal knowledge of Homeland Security using this information.

Also, ever since Google has bought Youtube, they have attempted to censor some of my videos, allegedly because of some obscure false copyright laws, but the real reasons were only too transparent.

Simply put, we are moving slowly but steadily into a Big Brother system.

I might not be able to oppose it by myself, but I sure don't have to accept it. I can certainly fight it as best I can and maybe even slightly slow down the progression of Big Brother.

Is there an issue with privacy? ......Look to my sig for a part of the answer.

The first part is about religion, the second part is about 9/11 and the last part is about the culprits and the big picture: 2 hours of intense information you likely never heard before.

Cheers,
PepeLapiu :D

---

### Post by BkkBonanza on 2009-12-14
> **PepeLapiu said:**
> 
Simply put, we are moving slowly but steadily into a Big Brother system.


Wait. I thought we were already there many years ago.

I've always used Thunderbird to get my mail from gmail so never see any ads from them. Thankfully they aren't yet tagging ads onto my emails directly. Now that would piss me off.

If I was concerned that they profile me for showing ads then I'd use the "serpico maneuver" and search for lots of stuff I'm not even vaguely interested in. I could write a script to repeatedly search for religious material that would have them way out in left field on me. Not going to bother though. I live in Thailand.

Regarding the documentary - I've heard it all. Some I believe and some I doubt.

---

### Post by PepeLapiu on 2009-12-14
Which part do you not believe?
My guess is the part about religion, isn't it?

---

### Post by PepeLapiu on 2009-12-14
> **BkkBonaza said:**
> If I was concerned that they profile me for showing ads then I'd use the "serpico maneuver" and search for lots of stuff I'm not even vaguely interested in. I could write a script to repeatedly search for religious material that would have them way out in left field on me. Not going to bother though.

You don't even have to bother, you can just use TrackMeNot, a FireFox add-on that does exactly that.

> **BkkBonaza said:**
> I live in Thailand

I don't live in the States either, that is not relevant.
The agenda they are working on is not aimed at the USA specifically, it is aimed directly at you and me.

---

### Post by HermanAB on 2009-12-14
Hmm, rent a server from Godaddy or some such and install Citadel on it.  Every true geek should run his own server, otherwise you should have your geek licence revoked...
:)

---

### Post by BkkBonanza on 2009-12-14
I've never liked GoDaddy and if he's paranoid about Google then he may as well go offshore. I pay $9.50/mo for my VPS in the UK. Not that the UK is any better though. 

Every geek does need a server to feel whole.

---

### Post by Sarmacid on 2009-12-14
Seeing the paranoia level in your posts, it seems the only solution you'd really be happy with is running your own server. Most of the good free mail servers out there will read your mail and claim it as their property, so you'd be better off with your own server, or try encrypting everything.

---

### Post by Dr Small on 2009-12-14
> **PepeLapiu said:**
> Here is what I have to offer about Google: they track your IP and they also track your searches and this information is used to direct advertising to you. Next time you log into your Gmail account, look at the advertising scroll at the top, you will find that they seem to know pretty well the kind of person you are.

Think also about China and how Google was instrumental in structuring the Big Brother type of Internet they have there. That really is only a test, a model for future plans world-wide.

I also have it of good source that your google searches supposedly remain confidential, however the advertising that is sent to you isn't confidential and so the 'guberment' has been working together with Google to obtain this track record of advertising sent to you to profile you. I have personal knowledge of Homeland Security using this information.

Also, ever since Google has bought Youtube, they have attempted to censor some of my videos, allegedly because of some obscure false copyright laws, but the real reasons were only too transparent.

Simply put, we are moving slowly but steadily into a Big Brother system.

I might not be able to oppose it by myself, but I sure don't have to accept it. I can certainly fight it as best I can and maybe even slightly slow down the progression of Big Brother.

Is there an issue with privacy? ......Look to my sig for a part of the answer.

The first part is about religion, the second part is about 9/11 and the last part is about the culprits and the big picture: 2 hours of intense information you likely never heard before.

Cheers,
PepeLapiu :D
Hear, hear! Bravo.

> **HermanAB said:**
> Every true geek should run his own server, otherwise you should have your geek licence revoked...
:)
+1 Herman

---

