---
title: "Default Keyring with blank password"
date: 2008-12-16
forum: Security
---

### Post by S_e_P_p on 2008-12-16
Hello all,

I'm referring to the discussion how has started in this thread:
[http://ubuntuforums.org/showthread.php?t=1003471](http://ubuntuforums.org/showthread.php?t=1003471) 

People how are using WLAN are asked every time on start up to enter the default keyring. As this is annoying it looks like most of the users enter a blank keyring in order not to be asked for the password on each start up.

I just wondering about security disadvantages of this procedure? What might happen to your system?
Isn't there another way to save the WLAN password as nobody want's to enter a keyring password on each start up?
Is only the WLAN password saved in the default keyring, or can I see it as a pool of all passwords?

Thank you very much.

SePp

---

### Post by S_e_P_p on 2008-12-19
bump

---

### Post by SamNSane on 2008-12-19
Hi, I was the guy who recommended you post over here. Doesn't look like you're getting much action. I had hoped that someone with some solid knowledge of the specifics in this matter would respond to your questions. I'm interested, too, in anything I can learn about security features like this. Since it's an issue that comes up often (putting blank passwords in the keyring manager) I hope someone with real knowledge -- not my slightly educated guesswork from the other thread -- would chime in!

---

### Post by antiOST on 2009-02-13
Hi

The disadvantage can be hard to see, when your keyring's only holding your password to the wireless. 

The first one that comes into to mind is that your keyring (in this matter your password store) is unprotected, thats is, if somebody gets a hold of your keyring file, they'll have access to your passwords.
This might be okey if its only your wireless pass, but in theory (and pratice) the keyring could hold password (or encryption keys) for several other applications such as email acounts, encrypted data etc.

So yeah its insecure to have a blank password as well as automatic login, but most of us do it anyway, cause even though we haven't thought about it, we actually made an risk assesment that concluded that it isn't worth the time compared to what we loose.

On the other hand, lets say you have a company laptop, if you loose that one (and that happens alot) the theives might be able to get the keyring off the computer without logging in and that way could get the password for the companys wireless network, mail, encrypted customer data or other sensible data. 
(I know that not a lot of applications are using the keyring, at least the ones I'm using yet but that might change in the future).

So it's all about what you are willing to risk. I you don't have anything to lose you don't need security and "bad" security wouldn't be that bad after all.

But from a security point of view you should always have things locked down (e.g. with password) and then you loosen up (e.g. no password).

Hope this help.

Kim

---

