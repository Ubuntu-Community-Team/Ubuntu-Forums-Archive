---
title: "2FA app for Ubuntu"
date: 2021-03-08
forum: Security
---

### Post by lordgallen on 2021-03-08
I am looking for a 2FA app for Ubuntu that works with a GUI or terminal, and does not bind to my phone number, so not authy. Is there such app?

thank-you.

---

### Post by TheFu on 2021-03-08
There are PAM modules which can be configured to work with many u2f key-fobs to provide 2fa for logins to most linux dstros.
I use a yubikey challenge-response setup to unlock the LUKS encryption on drives, but not for logins. Yubikey is the most popular, but others following standards should work.
Yubikey make usb, usbc, nfc versions.  These devices can be used for u2f logins to hundreds of webapps too.

Or did I miss the question entirely?

---

### Post by lordgallen on 2021-03-09
> **TheFu said:**
> There are PAM modules which can be configured to work with many u2f key-fobs to provide 2fa for logins to most linux dstros.
I use a yubikey challenge-response setup to unlock the LUKS encryption on drives, but not for logins. Yubikey is the most popular, but others following standards should work.
Yubikey make usb, usbc, nfc versions.  These devices can be used for u2f logins to hundreds of webapps too.

Or did I miss the question entirely?

I have the 16 digit codes, I think they are, to enter into an app that works like Google Authenticator. I don't need 2FA to unlock LUKS, and I don't have a yubikey. So basically I am looking for an app that can store my 2fa codes, for sites like gmail, etc...

---

### Post by TheFu on 2021-03-09
> **lordgallen said:**
> I have the 16 digit codes, I think they are, to enter into an app that works like Google Authenticator. I don't need 2FA to unlock LUKS, and I don't have a yubikey. So basically I am looking for an app that can store my 2fa codes, for sites like gmail, etc...

If the codes are pre-provided, I'd print them out and put them in my wallet next to a credit card.
If you seek some sort of program that creates valid codes, know those aren't very secure, since the system you are using could be compromised.  External devices .... 2FA .... something you have - separately.  A piece of paper, a key-fob.

If you insist on storing pre-provided codes.  Use a password manager. Something like **keepassxc**. It is in the repos.
Have you checked what alternativeto.net says? [https://alternativeto.net/software/google-authenticator/](https://alternativeto.net/software/google-authenticator/) has a list.

In the early 2000s, I was forced to deploy software-based SecurID as 2FA at work for tens of thousands of users.  Software is not as secure as hardware, in this situation.
Of course, there are different opinions about this.

---

### Post by lordgallen on 2021-03-09
> **TheFu said:**
> If the codes are pre-provided, I'd print them out and put them in my wallet next to a credit card.
If you seek some sort of program that creates valid codes, know those aren't very secure, since the system you are using could be compromised.  External devices .... 2FA .... something you have - separately.  A piece of paper, a key-fob.

If you insist on storing pre-provided codes.  Use a password manager. Something like **keepassxc**. It is in the repos.
Have you checked what alternativeto.net says? [https://alternativeto.net/software/google-authenticator/](https://alternativeto.net/software/google-authenticator/) has a list.

In the early 2000s, I was forced to deploy software-based SecurID as 2FA at work for tens of thousands of users.  Software is not as secure as hardware, in this situation.
Of course, there are different opinions about this.

I am not sure that I am making myself clear as to what I am looking for. I apologize if that's the case. I am looking for a program that works exactly like authy, but does not require me to bind a telephone number to it for back up purposes. The app should generate new codes every 30 seconds. I will configure each login manually from a code I have written down on a piece of paper as a back up. thank- you.

---

### Post by TheFu on 2021-03-09
Did you click the link? There are a number of options.

---

### Post by lordgallen on 2021-03-09
> **TheFu said:**
> Did you click the link? There are a number of options.


I will take a look, thank-you!

---

### Post by ahbart on 2021-03-17
I see this question is from a week ago, so maybe not relevant anymore. Sorry then.
I'm using Bitwarden as password manager. Bitwarden has clients for iphone, android, linux, macos and windows, and with each password you can store an totp code, which generates a code every 30 seconds. 
With a bitwarden browser plagin I just have to paste this code. Very easy. 
Bitwarden has free accounts, but these are a bit limited. But I run Bitwarden on a server, as [Bitwarden-rs]("https://github.com/dani-garcia/bitwarden_rs") version, which does not have these limitations.

---

### Post by TheFu on 2021-03-17
From the KeePassXC FAQ:
> We believe that storing both (TOTP and the TOTP secrets) together can still be more secure than not using 2FA at all, but to maximize the security gain from using 2FA, you should always store TOTP secrets in a separate database, secured with a different password, possibly even on a different computer. 

Convenience is often the enemy of security.  I prefer having physical FOBs over software methods for TOTP.

---

