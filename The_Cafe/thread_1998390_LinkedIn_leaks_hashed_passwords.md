---
title: "LinkedIn leaks hashed passwords"
date: 2012-06-06
forum: The Cafe
---

### Post by Erik1984 on 2012-06-06
[http://it.slashdot.org/story/12/06/06/1335228/linkedin-password-hashes-leaked-online](http://it.slashdot.org/story/12/06/06/1335228/linkedin-password-hashes-leaked-online)

I suggest changing your password in case you have a LinkedIn account. At least that's what I did after I read this news. Of course if you have a strong passwords there is probably no reason to panic, but just to be safe I suggest a password change.

---

### Post by HansKisaragi on 2012-06-06
Ouch... that is a lot of passwords.

---

### Post by scouser73 on 2012-06-06
Things like this will always happen because of sloppy attitudes towards security.

---

### Post by Frogs Hair on 2012-06-06
Thanks for posting ! Password Changed . ;)

---

### Post by CharlesA on 2012-06-06
Yikes!

---

### Post by dniMretsaM on 2012-06-06
Does anyone happen to know if they were salted or not? I don't have an account, I'm just curious.

---

### Post by Erik1984 on 2012-06-06
> **dniMretsaM said:**
> Does anyone happen to know if they were salted or not? I don't have an account, I'm just curious.

Probably not. If I look at the various replies, some could find their hashed password in the list by creating a sha1 hash of their current password without anything else.

---

### Post by Frogs Hair on 2012-06-06
This incident was posted in my account when I logged in with change password instructions .

---

### Post by CharlesA on 2012-06-06
> **Euroman said:**
> Probably not. If I look at the various replies, some could find their hashed password in the list by creating a sha1 hash of their current password without anything else.
That's what I thought.

I don't understand why password information would not be salted. That is a very bad security practice.

Also: 
[http://blog.linkedin.com/2012/06/06/linkedin-member-passwords-compromised/](http://blog.linkedin.com/2012/06/06/linkedin-member-passwords-compromised/)

---

### Post by Frogs Hair on 2012-06-06
> **CharlesA said:**
> That's what I thought.

I don't understand why password information would not be salted. That is a very bad security practice.

Also: 
[http://blog.linkedin.com/2012/06/06/linkedin-member-passwords-compromised/](http://blog.linkedin.com/2012/06/06/linkedin-member-passwords-compromised/)

I was able to login with the old password and received no emails , but I changed it anyway.

---

### Post by stmiller on 2012-06-06
Passwords were not salted and all have been cracked.

SHA1 with no salt... might as well have stored the passwords in plain text! :) JtR can rip through these easily.

Pretty bad for a major company!!

---

### Post by dniMretsaM on 2012-06-06
> **CharlesA said:**
> That's what I thought.

I don't understand why password information would not be salted. That is a very bad security practice.

Also: 
[http://blog.linkedin.com/2012/06/06/linkedin-member-passwords-compromised/](http://blog.linkedin.com/2012/06/06/linkedin-member-passwords-compromised/)

This. Also, why not SHA256 (or SHA512, but not a lot of places use that yet I don't think)? Better than MD5 I suppose.

Good to see that their implementing salts according to the blog post you linked.

---

### Post by Dr. C on 2012-06-06
According to the blog not all the passwords were compromised and the accounts of those whose password was compromised were disabled and those users notifed by email. I was not notified nor was my account disabled; however I changed my password anyway to be safe.

Thanks for letting us know.

---

### Post by CharlesA on 2012-06-06
> **dniMretsaM said:**
> This. Also, why not SHA256 (or SHA512, but not a lot of places use that yet I don't think)? Better than MD5 I suppose.

Good to see that their implementing salts according to the blog post you linked.

It's just sad to see they were storing passwords as hashes without being salted. My account wasn't locked out but I've changed my password anyway. Better safe than sorry.


> **Dr. C said:**
> According to the blog not all the passwords were compromised and the accounts of those whose password was compromised were disabled and those users notifed by email. I was not notified nor was my account disabled; however I changed my password anyway to be safe.

Aye. I feel better changing my password just to be safe. :)

---

### Post by skellat on 2012-06-06
> **Euroman said:**
> [http://it.slashdot.org/story/12/06/06/1335228/linkedin-password-hashes-leaked-online](http://it.slashdot.org/story/12/06/06/1335228/linkedin-password-hashes-leaked-online)

I suggest changing your password in case you have a LinkedIn account. At least that's what I did after I read this news. Of course if you have a strong passwords there is probably no reason to panic, but just to be safe I suggest a password change.

Hmm...yet another social network I may consider leaving.  I already terminated any sort of presence on Twitter after they had a breach like this recently.

I do hope the FreedomBox folks come out with *something* so that we don't have to worry about these data silos.

---

### Post by Metallion on 2012-06-07
Technically I should be safe. Very strong password that I don't use anywhere else. Never used anything else than the main site to log in either. Still I don't feel very comfortable knowing those passwords aren't salted.

---

### Post by vazduxosbra4kania on 2012-06-07
> **Metallion said:**
> Technically I should be safe. Very strong password that I don't use anywhere else. Never used anything else than the main site to log in either. Still I don't feel very comfortable knowing those passwords aren't salted.

Agree with you i have very good pass but of course after this case u have this nagging feeling that something is not OK anymore. You just do not trust them anymore!

---

### Post by Erik1984 on 2012-06-07
btw here is a list (continuously updated) [https://www.insomnia247.nl/linkedin.txt](https://www.insomnia247.nl/linkedin.txt) of all hashes from the LinkedIn for which the plain text password has been determined*. 

I checked some random records from this list and they do appear in the 'combo_not.txt'. A link to that file can be found in many of the threads on this subject. So those really ARE the stolen hashes from LinkedIn. To no surprise there are lots of weak passwords on the list but also some typical XKCD passwords ;) [http://xkcd.com/936/](http://xkcd.com/936/)

*AFAIK LinkedIn has reset passwords on all compromised accounts so the link I posted could do no harm to accounts involved. Also this list only shows password and no further login credentials.

---

### Post by Metallion on 2012-06-07
Didn't get an email that my password is reset either. Gonna download those hashes and see if it's in there when I get home. Does anybody know anybody working at linkedin btw? Tell them to figure out who decided passwords don't need salt and throw a pie in their face or something.

Edit: This made me lol. :) [https://twitter.com/i0n1c/status/210649411901075457](https://twitter.com/i0n1c/status/210649411901075457)

---

