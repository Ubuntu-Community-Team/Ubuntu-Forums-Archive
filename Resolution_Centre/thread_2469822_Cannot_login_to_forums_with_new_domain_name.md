---
title: "Cannot login to forums with new domain name"
date: 2021-12-10
forum: Resolution Centre
---

### Post by Nattereri on 2021-12-10
I cannot log into Ubuntu forums using my email address for the atomic.computer domain. I can log on to the SSO site but when i get redirected back to the forums site I get the message Invalid email address. I am assuming this is a software issue with the site and not support the new TLDs?

---

### Post by coffeecat on 2021-12-10
What exactly are you trying to do? Your Nattereri forum account is linked to an active Ubuntu One SSO, and it is clear from your post that you can log in OK. Changing your preferred email in your Ubuntu One SSO account, if that is what you are trying to do, should make no difference to logging into the forum.

Are you trying to log into the forum from a second Ubuntu One SSO account with the "atomic.computer" email address. If so, why? 

Please don't make assumptions about the from software and tld's. Let's determine what is happening first

---

### Post by Nattereri on 2021-12-10
I m trying to log on from a second account because that is my new business email. The account I am on now will be deleted soon after I get this sorted.

---

### Post by coffeecat on 2021-12-10
:sigh:

I don't see any need to do that. Simply changing the email in both the SSO account and forum account should suffice. The two accounts will remain linked whatever emails you set in them. If you make a new SSO account and try to log into the forum, that will create a new forum account linked to the new SSO account. If you subsequently want your Nattereri forum account linked to the new SSO account, you make unnecessary work for the forum admins. 

Out of interest, and to be clear, is the atomic.computer domain email of the form: ***local-part**@atomic.computer*?

---

### Post by coffeecat on 2021-12-10
Did some digging, and found this: [https://forum.vbulletin.com/forum/vbulletin-4/vbulletin-4-questions-problems-and-troubleshooting/4385220-user-can-t-register-with-computer-email-domain](https://forum.vbulletin.com/forum/vbulletin-4/vbulletin-4-questions-problems-and-troubleshooting/4385220-user-can-t-register-with-computer-email-domain)

Yes, the version of vbulletin we're on throws a hissy fit at the .computer tld. Which is silly, but I've had enough experience of vbulletin not to be surprised. If it's not too late, and you want to keep the old SSO account and this forum account, it looks as though I can change the email in the forum account for you without you having to divulge that in this thread.. Let me know what stage you're at and we can go from there.

---

### Post by Nattereri on 2021-12-10
If you can change the email for this account that will be good for me. Let me know how to get the email address to you.

---

### Post by coffeecat on 2021-12-10
Send me a pm with it and I can change the forum email address - or at least try to. Hopefully, you'll be able to change it in your Ubuntu One account without any problem. Just to be clear - this forum account, Nattereri, and your SSO account are linked in a way that can only be disabled by a forum admin. Changing the email in either or both accounts won't break the link.

---

