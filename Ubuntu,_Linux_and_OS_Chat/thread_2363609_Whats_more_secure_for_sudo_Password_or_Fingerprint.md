---
title: "Whats more secure for sudo? Password or Fingerprint?"
date: 2017-06-12
forum: Ubuntu, Linux and OS Chat
---

### Post by LastDino on 2017-06-12
Well, this thread isn't in support because this isn't exactly a support request, mostly curiously. 

So, I was wondering, since I've setup which can log in using my finger prints for sudo, is it worth configuring my ssh virtual network lab with fingerprint sudo access as well? (If it is possible, I would like to know how as well if anyone know. Right now I imagine configuring fprint on each network node should be enough, so when I ssh it will automatically ask for it, if wrong, please correct me)

Also, fingerprint unlock phones have gotten quite popular here, I can't imagine it to be more secure than passwords as you're walking around with access key and they have to have stored somewhere on the device locally. 

Also, is it possible to have dual security, where password as well as fingerprint is needed? (No I'm not going paranoid, just wondering, and if it is possible, I might try to configure it on my vm, so I get to have  some fun) :D

Any opinions/experiences?

---

### Post by TheFu on 2017-06-12
Fingerprint readers are known to be less secure and spoofable in pretty much every situation when compared to alternatives with passphrases.  A finger print will be more secure than a 4 digit pin, but that is an extremely low bar for access.

Google all the different fingerprint hacking methods. It really is amazing what works for less than $2 in supplies.

Anything less than 16 random characters isn't exactly secure these days. More is better.

Update:
2FA is really what you want.  There are multiple solutions for this - passphrase + OTP; passphrase + U2F; passphrase + Oauth2 ... SmartCards, yubikeys, oneKey, onlyKey ... most of these cost about $50.  Some have a pin to access the other modes and a pin to wipe the card to prevent any future use.

Where I live, the courts have ruled that forcing someone to unlock a computer with a fingerprint without a valid, signed, warrant, isn't a violation of their rights.  Just something more to consider.

You may only want enough security to keep a sibling out of the computer.  A finger-print alone isn't sufficient for that, if the other person can google.

---

### Post by ChuangTzu on 2017-06-13
I'll take passwords and secure keys any day over fingerprint, facial scanning, iris scanning etc....they are just too easy to fool.  Kinda makes you wonder why some tech is moving in that direction....just sayin.

---

### Post by monkeybrain20122 on 2017-06-14
> **ChuangTzu said:**
>  Kinda makes you wonder why some tech is moving in that direction....just sayin.
Because there is more money to be made. :)

---

### Post by LastDino on 2017-06-14
> **TheFu said:**
> Fingerprint readers are known to be less secure and spoofable in pretty much every situation when compared to alternatives with passphrases.  A finger print will be more secure than a 4 digit pin, but that is an extremely low bar for access.

Google all the different fingerprint hacking methods. It really is amazing what works for less than $2 in supplies.

Anything less than 16 random characters isn't exactly secure these days. More is better.

Update:
2FA is really what you want.  There are multiple solutions for this - passphrase + OTP; passphrase + U2F; passphrase + Oauth2 ... SmartCards, yubikeys, oneKey, onlyKey ... most of these cost about $50.  Some have a pin to access the other modes and a pin to wipe the card to prevent any future use.

Where I live, the courts have ruled that forcing someone to unlock a computer with a fingerprint without a valid, signed, warrant, isn't a violation of their rights.  Just something more to consider.

You may only want enough security to keep a sibling out of the computer.  A finger-print alone isn't sufficient for that, if the other person can google.

Very informative. Will experiment with 2FA

I found this with quick google search
[https://www.linux.com/learn/how-set-2-factor-authentication-login-and-sudo](https://www.linux.com/learn/how-set-2-factor-authentication-login-and-sudo)

Worth it? Better alternatives?

---

### Post by TheFu on 2017-06-14
> **monkeybrain20122 said:**
> Because there is more money to be made. :)

People have bought into the fallacy that fingerprints are unique.  They are not.  Cheap fingerprint reading devices simplify them so far as to make just 60 or so different "fingerprints" according to some reading I've done.  Use a Master Fingerprint for a 65% success rate.
[http://www.telegraph.co.uk/technology/2017/04/11/smartphone-fingerprint-scanners-could-easily-fooled-fake-prints/](http://www.telegraph.co.uk/technology/2017/04/11/smartphone-fingerprint-scanners-could-easily-fooled-fake-prints/)

Apple claims a 1:50,000 match rate, but that means there are ... let's do some simple math ... 140,000 people in the world whose fingerprints would match sufficiently to get into your iPhone with a fingerprint lock.  That is hardly unique and assumes that Apple's calculations are actually correct.  Didn't they have issues dealing with time for new years and daily savings multiple times?

There are documented, non-twin, identical finger prints in the world.  On TV, they act like a match is a match is a match. Everything is open to interpretation. Generally more points used in the matching, the better and more likely that the wrong prints won't be used to find someone guilty.  And don't get me wrong, finger prints read by an expert will certainly get in the 1:1,000,000 range, but that is much different from "completely unique" as we've been sold.

Should you trust google authenticator? I cannot say. I won't, but that is more about my total distrust of google and other overly popular centralized services than their security. Google is very good at security, if you can actually trust them.  That is your call to make.  Whatever you choose, be certain there is an alternate method to gain access, at least from the console.
In my mind, a properly secured ssh-key (with a strong passphrase) is more than sufficient. You can use OTP with a device plus a good passphrase too.   Yubikey makes example implementations for PAM that I'd rather use over anything from Google.

---

### Post by LastDino on 2017-06-15
Yes, I also agree with fingerprint fallacy as it is being sold, though I would prefer it on hand held device simply because number of times having to open it in public places, too many people peeking at your screen while typing pass-phrase or patterns. Laptops and server kind of machines are different things all together, actually many companies/organizations here  use Yubikey or similar system where each relevant employee is given USB like device which works as their access key in addition to usually some other measures. 

Though I came to know about this after you mentioned YubiKey, that it was possible to have it as google/facebook and even dropbox account access key. Rather amazing for $ 30-40 USD

---

### Post by ChuangTzu on 2017-06-15
in a not so distant future this silliness could lead to lots of armed men asking for your finger or your eye.  Long gone will be the days of taking your password to the grave ](*,)

---

### Post by 7dEfOk4AgU on 2017-06-18
I prefer Pin with two factor verification

---

