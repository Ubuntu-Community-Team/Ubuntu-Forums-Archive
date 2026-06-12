---
title: "Guest Accounts in 11.10, security flaw?"
date: 2011-11-20
forum: Security
---

### Post by Ms. Daisy on 2011-11-20
This guy is not a fan of Ubuntu guest accounts.

[https://www.infosecisland.com/blogview/18268-Ubuntu-Decreases-Security-and-Calls-it-a-Feature.html](https://www.infosecisland.com/blogview/18268-Ubuntu-Decreases-Security-and-Calls-it-a-Feature.html)

Is this a security flaw?

---

### Post by Dangertux on 2011-11-20
> **Ms. Daisy said:**
> This guy is not a fan of Ubuntu guest accounts.

[https://www.infosecisland.com/blogview/18268-Ubuntu-Decreases-Security-and-Calls-it-a-Feature.html](https://www.infosecisland.com/blogview/18268-Ubuntu-Decreases-Security-and-Calls-it-a-Feature.html)

Is this a security flaw?

Ironically I've been spending some time messing around with the guest account in several versions of Ubuntu recently. Someone had brought it up on this forum a while back discussing the "security" of the guest account, not unlike this guy did. 

Now normally, I'm not a huge fan of guest accounts, and judging from the site you got that from neither is anyone else there. However that author is and has been prone in his career to like to scare people, presentations like "Using Reader? Watch your computer get penetrated!" come to mind. Okay okay... We all know Reader is second in line for file format exploits to only Flash this past year (hey Adobe what's up? lol), and if it keeps going that way file format exploits may end up back on the top 10 with the rest of the decade old exploitation methods that lulzsec made famous. 

Alright anyway back to the point. Let's break down how the guest account ACTUALLY works in Ubuntu. Note my research was SPECIFICALLY designed to simulate an attacker compromising the guest account in multiple ways --browser exploit, file format, shell thru persistant xss blah blah, the typical. Then I wanted to find out how easy it was to break out of it. I'll be perfectly honest with you. The guest account is just as easy to compromise as a regular account (this is the idea I suppose) However, getting out of it is VERY difficult I won't say impossible because there are very smart people out there, but I wouldn't bother targeting one, with any real hopes for success.

A lot of infosec dorks see guest account and it makes us excited in special ways. Come on everyone knows the stories of OMG I got subseven'ed because my guest account was enabled and I had file sharing on, from the Windows NT 4.0 days, the truth is this isn't that kind of account. 

The guest account in Ubuntu separates it's files from the standard home directory (it actually stores them in /var). The files are persistent however, they are pretty tightly locked away from other users accessing them.

DAC is configured in such a way that guest has virtually no ability to do anything anywhere. In addition to that GDM does a really good job of locking the little guy down.

If that wasn't enough, there is an apparmor profile in enforce mode by default called LightDM-guest-session, you might wish to check it out. MAC is in place , and it's not letting guest do much of anything. 

All setuid binaries are conveniently tucked away from guest, so no escalating through ping or udev in case anyone is worried about that. 

So long story short, what happens on guest pretty much stays on guest. Unless you are either very determined or VERY angry at someone.

So I disagree with the guy, in its current state it's not a liability and falls firmly into feature territory.

P.S : I know it's FUD Sunday, but yes I just said something positive about Ubuntu's built in security features feel free to quote me lol.

---

### Post by Ms. Daisy on 2011-11-20
> **Dangertux said:**
> So I disagree with the guy, in its current state it's not a liability and falls firmly into feature territory.

yes I just said something positive about Ubuntu's built in security features feel free to quote meOK, so you're saying Ubuntu is secure out of the box then, right?  

KIDDING. Couldn't resist!:twisted:

From a new user standpoint, I was confused by his article.  He said "there is no security on (guest) account." Sure it doesn't have a password, but that just gives the guest free reign over the preset limited permissions which would thereby qualify as security.  I suppose you removed one of the layers (password) in a layered security approach.  But then from what Dangertux describes, it sounds like the removed layer is replaced by several other layers (/var directory, GDM, DAC, apparmor, setuid).

---

### Post by lovbuntu on 2011-11-20
> **Ms. Daisy said:**
> OK, so you're saying Ubuntu is secure out of the box then, right?  

KIDDING. Couldn't resist!:twisted:

From a new user standpoint, I was confused by his article.  He said "there is no security on (guest) account." Sure it doesn't have a password, but that just gives the guest free reign over the preset limited permissions which would thereby qualify as security.  I suppose you removed one of the layers (password) in a layered security approach.  But then from what Dangertux describes, it sounds like the removed layer is replaced by several other layers (/var directory, GDM, DAC, apparmor, setuid).

Exactly. key word here is 'guest'. Why would the guest account have a password?

---

### Post by Dangertux on 2011-11-20
> **Ms. Daisy said:**
> OK, so you're saying Ubuntu is secure out of the box then, right?  

KIDDING. Couldn't resist!:twisted:

From a new user standpoint, I was confused by his article.  He said "there is no security on (guest) account." Sure it doesn't have a password, but that just gives the guest free reign over the preset limited permissions which would thereby qualify as security.  I suppose you removed one of the layers (password) in a layered security approach.  But then from what Dangertux describes, it sounds like the removed layer is replaced by several other layers (/var directory, GDM, DAC, apparmor, setuid).

I didn't say that -- I said the guest account is well secured for what it is lol... :-)

Well in this particular case the entire password thing is moot since ultimately nothing that happens on the account will actually end up being persistent (anywhere outside of that account). 

> **lovbuntu said:**
> Exactly. key word here is 'guest'. Why would the guest account have a password?

What... Don't you challenge your guests for authentication when you invite them over for dinner? lol :-P

---

### Post by lovbuntu on 2011-11-20
> **Dangertux said:**
> I didn't say that -- I said the guest account is well secured for what it is lol... :-)

Well in this particular case the entire password thing is moot since ultimately nothing that happens on the account will actually end up being persistent (anywhere outside of that account). 



What... Don't you challenge your guests for authentication when you invite them over for dinner? lol :-P

Haha, good point :)

---

### Post by Dangertux on 2011-11-20
So I re-read the article a little better this time

> 
But the second addition is the most  concerning. If you look at the user  list there is a new user present &#8211;  &#8220;Guest Session&#8221;. There is no  security on this account. Just select  &#8220;Guest Session&#8221;, leave the  password blank and log in!
Oh my gosh an account without a password on it run for the hills

Believe me, if you've ever read my blog you know I love to tear apart security issues, and lack of understanding of security principles in Ubuntu. . As I stated above, I gave several reasons why the account is rather secure, and not like a typical guest session.

If you want to talk about security talk about something with a reaching impact.  Let's worry about getting the actualy Ubuntu users who running an SSH or VNC server on their "unpriveleged" but still superuser equipped default user in line, before we worry about the "Guest boogeyman"

---

### Post by lovbuntu on 2011-11-21
Hey Adam, did you manage to break out of the guest session?:)

---

### Post by Dangertux on 2011-11-21
I haven't had a chance to really try any further. Although I am planning on writing about it on my website this week at some point when I have a chance.

For anyone who is interested I have been having a discussion with the author of the original article  [http://cyberarms.wordpress.com/2011/11/18/ubuntu-decreases-security-and-calls-it-a-feature/](http://cyberarms.wordpress.com/2011/11/18/ubuntu-decreases-security-and-calls-it-a-feature/)

scroll down to the comments section, if you want to comment it seems to be becoming rather interesting. Fair warning he moderates all of his comments, and it might not show up right away or at all if  you're a "ubuntu is safe" evangelist.

All in all, I don't think he was really trying to be an antagonist so much so as he was just expressing certain concerns over the existence of what would normally be an unneeded account.

EDIT: For anyone who cares this was my thought on the subject [http://dangertux.wordpress.com/2011/11/22/341/](http://dangertux.wordpress.com/2011/11/22/341/)

---

