---
title: "Idea or Direction  voice secure"
date: 2008-11-21
forum: Security
---

### Post by xmx on 2008-11-21
noob here, 
I was wondering if there was a voice recognition program that will allow users to log in just saying their name over a microphone. (ubuntu 8.10)  I have a voice editor program that is interesting, (edit, reverse, manipulate) and I was wondering if there is a application that can be integrated with security.
Or to use for sudo commands ect.  


Or if there isn't any, where would be a good place to request such and idea?

Voice your log ins or even voice to type.

---

### Post by Dr Small on 2008-11-21
There is none that I know of, as this would be a big security flaw in the authentication system.

---

### Post by xmx on 2008-11-22
> **Dr Small said:**
> There is none that I know of, as this would be a big security flaw in the authentication system.

-------------------------------------------------------------------
How so?  I don't know much about ubuntu but would like to learn as much as I can.  Would the integration make the authentication be unstable? Or would it be a breech point?

---

### Post by Dr Small on 2008-11-22
> **xmx said:**
> -------------------------------------------------------------------
How so?  I don't know much about ubuntu but would like to learn as much as I can.  Would the integration make the authentication be unstable? Or would it be a breech point?
It would be considered an area that an attacker could easily gain authentication. Here is an example for you.

Joe sets his system up for Voice Authentication. He must say his username, and the system checks his voice against his pre-recorded voice. If it sounds within 90% the same, the system logs him in. Joe is out of the room for awhile, locks the screen (or logs out) and an attacker plants a tape recorder in the room. When Joe comes back, he authenticates by using his voice, which is now recorded by the attacker.

When Joe leaves, the attacker removes his tape recorder, can take it home, make a duplicate of it, removes the whitespace, and now has the key to Joe's computer. The attacker can now come at a time when Joe is not around, play Joe's recorded voice to the computer, the system will recognize it as Joe's voice, compare it, and the attacker will be given access.

They do the same things with webcams for authentication. So far, a strong password is your best form of auth. It may not be convenient, but you can not sacrifice convenience for security.


The above example may not be true in every situation, but it can be accomplished different ways with the same intentions. If a webcam is used, we'll steal your picture; If a voice recording, we'll steal your voice; If a fingerprint reader, we'll steal your fingerprint; If a password, we'll either try to crack it, or just steal your computer (more likely to be noticed).

Dr Small

---

### Post by teddks on 2008-11-23
> **Dr Small said:**
> 
The above example may not be true in every situation, but it can be accomplished different ways with the same intentions. If a webcam is used, we'll steal your picture; If a voice recording, we'll steal your voice; If a fingerprint reader, we'll steal your fingerprint; If a password, we'll either try to crack it, or just steal your computer (more likely to be noticed).

Dr Small

I'd be interested in hearing how you "steal a fingerprint" outside of a James Bond film.

---

### Post by Dr Small on 2008-11-23
> **teddks said:**
> I'd be interested in hearing how you "steal a fingerprint" outside of a James Bond film.
The same way the FBI and investigators do it. A little dust and some scotch tape.

---

### Post by teddks on 2008-11-23
> **Dr Small said:**
> The same way the FBI and investigators do it. A little dust and some scotch tape.

And then you run the tape over the fingerprint scanner, hoping the dust sticking to the fingerprint lines will register on the scanner? 

I've just seen this "fingerprints are insecure" attitude in this forum, and I'm wondering why.

---

### Post by Dr Small on 2008-11-23
> **teddks said:**
> I've just seen this "fingerprints are insecure" attitude in this forum, and I'm wondering why.

The attitude should be, "Anything is unsecure unless proven otherwise." Never take anything for granted when dealing with security.

---

### Post by randy78 on 2008-11-23
Check here: [http://www.securityfocus.com/news/6717]("http://www.securityfocus.com/news/6717")

It seems relatively easy to lift and clone fingerprints, with many tutorials available online.

---

### Post by teddks on 2008-11-23
> **randy78 said:**
> Check here: [http://www.securityfocus.com/news/6717]("http://www.securityfocus.com/news/6717")

It seems relatively easy to lift and clone fingerprints, with many tutorials available online.

Wow, that sounds like complete science fiction to me. I guess pam_fprint is coming out of my configuration.

---

### Post by stmurray on 2008-11-24
Security is always a trade-off.  How inconvenient you make the security should be offset by what you are protecting.  Yes, a voice-type authorization system would be  less secure than a strong password, but if it is fairly secure physically, and the most sensitive data on it is your high-score in Gnometris, then that is probably a good convenience trade-off.  

Yes, cloning fingerprints is possible, but who is going to go through the trouble of doing it to steal your credit card number (when a valid credit card number is only worth a few bucks on black market)?

---

### Post by NIT006.5 on 2010-09-26
Using any form of biometric authentication to replace a password might be less secure, but personally I think it's best to combine different methods of authentication. For instance, I use facial recognition and password, and both are required to log in. This at least offers some minimal additional security should someone discover my password. In case facial recognition becomes impossible for some reason, a usb key stored in a secure place is a fallback option to gain access.

Combining these options is also useful for fairly "high security" clients where I provide remote support. For instance, they might not want me to log in remotely without their knowledge, so as well as my password, it might require a usb key to be physically connected before I can gain remote access. I haven't implemented this yet, but it's something I'm looking at. This is also a prime example of how important "physical" security is too. For a system housed in a secure server room for instance, there is much less risk with a usb key than there is on a mobile device, laptop, etc. There are a lot of factors to be considered, and different scenarios require different security measures.

---

