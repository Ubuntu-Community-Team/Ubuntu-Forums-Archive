---
title: "End all spam with PGP.....forever?"
date: 2007-09-11
forum: The Cafe
---

### Post by curuxz on 2007-09-11
Something I suggested in another thread I wanted to expand on....

Do you think that if we all signed ALL our emails, even the automated ones we use on our websites with pgp and then set all mail servers to drop all unsigned emails that we could eliminate spam forever?

I mean think about it, pgp has key servers, if someone starts spamming, their key gets disabled and they cant send messages. 

Yes it would mean massive reconfigurations to mail servers, and everyone would have to adopt it pretty quick but at the very least it would do away with all spoof bank emails, they just could not do it if all email was signed. 

What are you thoughts, would it work? Is there a better way..?

---

### Post by init1 on 2007-09-11
Where else can I get my Viagra? :lolflag: Just kidding, I don't even get spam. But I did on older accounts.

---

### Post by mostwanted on 2007-09-11
Pretty much all of my spam is caught by the GMail spam filter :)

What annoys me the most is all those meails I get from people who think I'm someone else because of my somewhat generic email address.

---

### Post by curuxz on 2007-09-11
> **init1 said:**
> Where else can I get my Viagra? :lolflag: Just kidding, I don't even get spam. But I did on older accounts.

](*,) so you voted against an idea, just because you dont get spam lol.

Thanks, now my poll is ruined :(

:lolflag:

---

### Post by curuxz on 2007-09-11
> **mostwanted said:**
> Pretty much all of my spam is caught by the GMail spam filter :)

What annoys me the most is all those meails I get from people who think I'm someone else because of my somewhat generic email address.

fair enough, i agree a lot is caught by spam filters....but could signed emails stop the rest of the spam, plus speed the internet up by not allowing junk that has a massive effect on speed.

---

### Post by mostwanted on 2007-09-11
I'm against it because it's an uneccesary centralisation process which won't eliminate the problem. It's a just a more effective spam filter and since spam filters are good enough already, I don't see anything to gain from it.

---

### Post by PartisanEntity on 2007-09-11
> **curuxz said:**
> Something I suggested in another thread I wanted to expand on....

Do you think that if we all signed ALL our emails, even the automated ones we use on our websites with pgp and then set all mail servers to drop all unsigned emails that we could eliminate spam forever?

I mean think about it, pgp has key servers, if someone starts spamming, their key gets disabled and they cant send messages. 

Yes it would mean massive reconfigurations to mail servers, and everyone would have to adopt it pretty quick but at the very least it would do away with all spoof bank emails, they just could not do it if all email was signed. 

What are you thoughts, would it work? Is there a better way..?

I think it would work, why this hasn't been done already is worthy of finding out.

---

### Post by curuxz on 2007-09-11
> **PartisanEntity said:**
> I think it would work, why this hasn't been done already is worthy of finding out.

Thankyou :D

Now I need to find out how hard it is to implement, there seem to be 3 problems:

- We need to get all clients to pgp sign and php verify email. Of course we all need to register with at least 1 key server for this to work...

- We need to convert all websites to send their automated emails via a trusted site key, not that hard just time consuming.

- We need to get a way for the email servers to drop email that is not signed, now putting it somewhere else like a filter is simply not good enough but good be a short term solution, we need it to drop the email like it would a malicious packet. Spam wastes so much of the net's bandwidth we want to be actively destroying spam data by dropping it not simply moving it around.


Nice to see a forum admin likes the idea, maybe you guys could start signing emails from the ubuntu forum system, 

This guide seems an easy enough way of putting pgp inside of your php sendmail script. :)

[http://oregonstate.edu/cws/docs/gpgwrap](http://oregonstate.edu/cws/docs/gpgwrap)

---

### Post by Tautoa on 2007-09-11
I think, in theory, the idea would work, although it might instigate a lot of attention on breaking the PGP system (I think someone already tried this?)

I set up Kmail to sign all my outgoing mail a couple of days ago, and I've got to say, I didnt find the whole process very easy, I was following instructions, but it just didnt work (and then it just did.... peculiar)

But, to implement such a system, you would have to get everyone to follow it, including all the people who use computers casually for email and Minesweeper. If you start talking about digital signing and key servers, and your idea becomes a mandatory part of the email system, those people will simply find an easier way to communicate, and the spam problem will follow them.

In spite of all this, I voted for your idea, because the theory is pretty sound, even if the implementation is difficult :)

---

### Post by curuxz on 2007-09-11
> **Tautoa said:**
> I think, in theory, the idea would work, although it might instigate a lot of attention on breaking the PGP system (I think someone already tried this?)

I set up Kmail to sign all my outgoing mail a couple of days ago, and I've got to say, I didnt find the whole process very easy, I was following instructions, but it just didnt work (and then it just did.... peculiar)

But, to implement such a system, you would have to get everyone to follow it, including all the people who use computers casually for email and Minesweeper. If you start talking about digital signing and key servers, and your idea becomes a mandatory part of the email system, those people will simply find an easier way to communicate, and the spam problem will follow them.

In spite of all this, I voted for your idea, because the theory is pretty sound, even if the implementation is difficult :)

thanks! :D

I agree it would be really hard to do, but if you could just get gmail, yahoo, aol and hotmail to sign up to the idea then it would probs catch on.

I think they may consider it if someone showed them how, since it would save them tons on bandwidth and resources.

---

### Post by jdong on 2007-09-11
My problem is, how do you stop spammers from just generating new keys? The way I see it, there's two mechanisms of action:

(1) GPG allows you to cryptographically identify the person who sent the message, so you can disable that person if he misbehaves/spams.
(2) GPG uses a circle-of-trust system so you can assign different "trust levels" to e-mails coming in. Highly trusted e-mails are more likely to end up in the inbox than a freshly made key with no signatures.
(3) Just adding another unique requirement to e-mails results in a fraction of automated scripts and less technically savvy people unable to satisfy them.

Now for #1 and #3, I don't think it would work to any degree of satisfaction. A person can generate an infinite number of GPG keys to sign his e-mails with, so disabling the host doesn't work... And as far as #3, it won't be too long until spammers adjust their scripts to call gpg --sign on their e-mails :)

#2 has a meritable chance of working -- It could really help you separate out the truly important e-mails. However, what about new contacts or people new to e-mail? Well they'll end up in some sort of "untrusted" folder, and we're back to sifting through the "spamfolder" but with a different name :)

Ending spam is good, but I personally don't believe this solution would work.... In fact I'm a pretty pessimistic person on this one -- I've heard very very few ideas of how to stop spam that I actually believe stand any chance of working.

---

### Post by curuxz on 2007-09-11
> **jdong said:**
> My problem is, how do you stop spammers from just generating new keys? The way I see it, there's two mechanisms of action:

(1) GPG allows you to cryptographically identify the person who sent the message, so you can disable that person if he misbehaves/spams.
(2) GPG uses a circle-of-trust system so you can assign different "trust levels" to e-mails coming in. Highly trusted e-mails are more likely to end up in the inbox than a freshly made key with no signatures.
(3) Just adding another unique requirement to e-mails results in a fraction of automated scripts and less technically savvy people unable to satisfy them.

Now for #1 and #3, I don't think it would work to any degree of satisfaction. A person can generate an infinite number of GPG keys to sign his e-mails with, so disabling the host doesn't work... And as far as #3, it won't be too long until spammers adjust their scripts to call gpg --sign on their e-mails :)

#2 has a meritable chance of working -- It could really help you separate out the truly important e-mails. However, what about new contacts or people new to e-mail? Well they'll end up in some sort of "untrusted" folder, and we're back to sifting through the "spamfolder" but with a different name :)

Ending spam is good, but I personally don't believe this solution would work.... In fact I'm a pretty pessimistic person on this one -- I've heard very very few ideas of how to stop spam that I actually believe stand any chance of working.

Ok ok I agree there are problems, BUT spam is sent because it does make money. Most of the money comes from either 'passing off' or just plain old scams. Now having your bank sending all its emails to you signed is a big plus, you can instantly tell when the ebay, paypal, hsbc etc scams come into your box because it would have a big cross against the email.

I think option 2 is the best idea, but there has to be a way to pre-verify keys for new users. I think this would be a big weapon in identity theft if people all had at least 1 key, maybe it needs to come from governments and thats tricky.

---

### Post by kuja on 2007-09-11
Edit: screw what I wrote, just read what Jdong wrote ... same thing, better explanation

In other words, no, I don't think it stands a chance of working.

---

### Post by curuxz on 2007-09-11
> **kuja said:**
> I voted no, because there are issues with it that would probably stop it from working. From where are you supposed to obtain their public key?
Assuming you're using a public key server,what's to stop the spammers from using GPG too?

nothing stops them using the current key servers. But if you put capatcha's on keys and made diffrent types of keys so if a personal key is being used thousands of times a day then it becomes invalid, but if your a company and want a mailing list you have to provide a confirmed address for a mass mailing key then it works.

Its not perfect but spam costs millions a year so any solution no matter how hard is a step in the right direction :)

---

### Post by Tom Mann on 2007-09-11
Just thinking... Would there be a way to send signed spam? in which case we'd be back to square one anyway. Excuse my lack of knowledge on this subject! :)

---

### Post by curuxz on 2007-09-11
> **Tom Mann said:**
> Just thinking... Would there be a way to send signed spam? in which case we'd be back to square one anyway. Excuse my lack of knowledge on this subject! :)

well yes but then thats kinda the point.

The second someone sends a spam message using a key we have a trail, if they are using a botnet then its impossible to trace the person but if they are using a key then that key can be identified and destroyed and the spam dies with it.

Its main function is to keep spoof emails out of the system and to make emails actual messages.

In the UK emails are considered a written form of communication, which is insanity to say that they can legally binding without being signed.

---

### Post by jdong on 2007-09-11
There is a really really good point that I think should be advanced -- **financial institutions using signed e-mails** -- I'm pretty bothered that those types of e-mails are still unverifiable. I think, if this is not a good spam solution, it should at least be the beginning of more verifiable email. What really needs to happen is GPG technology gets adopted more readly by the general mass. Unfortuantely there's the blocker of unfamiliarity and ignorance to the insecurity of e-mail...

---

### Post by curuxz on 2007-09-11
> **jdong said:**
> There is a really really good point that I think should be advanced -- **financial institutions using signed e-mails** -- I'm pretty bothered that those types of e-mails are still unverifiable. I think, if this is not a good spam solution, it should at least be the beginning of more verifiable email. What really needs to happen is GPG technology gets adopted more readly by the general mass. Unfortuantely there's the blocker of unfamiliarity and ignorance to the insecurity of e-mail...

I know its amazing that banks have not bothered to do this, I mean to the uninformed its a small block of text at the end of an email its not like its going to cause panic to those that don't want to use it!

People need to start signing emails all the time because people assume that an email is from the person who sent it. Only last night my girlfriends sister and boyfriend are staying over and I showed them how I could send an email from my email server saying it was from her address in under 15 seconds i could spoof her.

I was trying to explain that with a little bit of inside knowledge email can be devastating, the example i used was that i could send a message as her to him say i was drunk and admitting to cheating on him, or something equally offensive and of course totally made up. Now yes they would use other communication methods but it would certainly stir up a lot of trouble. Now imagine if I emailed your boss again under the ruse that i was 'drunkenly speaking my mind' and called him a $%£ ^$%^$ %^$%^%$ you could get in serious trouble for it when there is NOTHING you can do to stop it.

Email sucks as a communication method since its totally insecure, php signing should be a must and serious consideration should be taken on php encrypting all messages!

---

### Post by kuja on 2007-09-11
> **curuxz said:**
> nothing stops them using the current key servers. But if you put capatcha's on keys and made diffrent types of keys so if a personal key is being used thousands of times a day then it becomes invalid, but if your a company and want a mailing list you have to provide a confirmed address for a mass mailing key then it works.

Its not perfect but spam costs millions a year so any solution no matter how hard is a step in the right direction :)

???

But as things stand now, keys are stored on individual computers, completely independent of internet tracking of any sort (download once, use at will) So just how would you know that a key is being used thousands of times a day? Though, it would be possible to see how many times a day a key is downloaded from a single key server I'm sure. 

Again though,the problem with spam is that you close one door, six more open ... 

Perhaps what we need is a similar technology adapted to meet new requirements, with a key server managed by an organization (or organizations) that researches and verifies on a basis similar to what you described. I don't think this will happen anytime too soon though. I think it would definitely be a step in a positive direction though. 

Oh, so many possibilities (unified key server network? a perhaps modified IMAP over TLS protocol, etc) on how this could be made very secure by default, but so unlikely that anything will ever happen :(

---

### Post by curuxz on 2007-09-11
> **kuja said:**
> ???

But as things stand now, keys are stored on individual computers, completely independent of internet tracking of any sort (download once, use at will) So just how would you know that a key is being used thousands of times a day? Though, it would be possible to see how many times a day a key is downloaded from a single key server I'm sure. 

Again though,the problem with spam is that you close one door, six more open ... 

Perhaps what we need is a similar technology adapted to meet new requirements, with a key server managed by an organization (or organizations) that researches and verifies on a basis similar to what you described. I don't think this will happen anytime too soon though. I think it would definitely be a step in a positive direction though. 

Oh, so many possibilities (unified key server network? a perhaps modified IMAP over TLS protocol, etc) on how this could be made very secure by default, but so unlikely that anything will ever happen :(

but thats my exact point, you would need to unify the key servers somehow to compare data, or make trusted orginisations that hold big key servers, much like ICAN does with domain name certificates, in fact that same framework could be used to issue official PGP keys that are 100% genuine identities! How great would it be to have domains that are owned by a key, that stops people stealing domains or spoofing who owns them.

Im not saying its exactly possible off the shelf it would require a lot of thought but i do think it would solve a lot of problems with email. Every time you open an email it can call back to the key server network to verify the key, thats where you clock the people using their key outside normal usage and can target anti-spam efforts at them.

---

