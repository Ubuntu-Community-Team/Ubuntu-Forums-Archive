---
title: "Secure and cheap USB device for fprint (fingerprint for unlocking Ubuntu) ?"
date: 2021-12-29
forum: Security
---

### Post by gigi1335 on 2021-12-29
Hello,

I am looking for a secure and cheap USB device for fprint (fingerprint for unlocking Ubuntu) ? Which one would you suggest me, please ?

Thanks in advance for your help.

Gilles

---

### Post by TheFu on 2021-12-29
I don't believe any fingerprints can be part of a "secure" access control solution.
[https://hackaday.com/2015/11/10/your-unhashable-fingerprints-secure-nothing/](https://hackaday.com/2015/11/10/your-unhashable-fingerprints-secure-nothing/)
[https://www.pcmag.com/news/hacking-fingerprints-is-actually-pretty-easy-and-cheap](https://www.pcmag.com/news/hacking-fingerprints-is-actually-pretty-easy-and-cheap)
[https://arstechnica.com/information-technology/2020/04/attackers-can-bypass-fingerprint-authentication-with-an-80-success-rate/](https://arstechnica.com/information-technology/2020/04/attackers-can-bypass-fingerprint-authentication-with-an-80-success-rate/)
[https://cipher.com/blog/biometric-hacking/](https://cipher.com/blog/biometric-hacking/)
[https://www.biometricupdate.com/201911/chinese-researchers-reveal-method-to-bypass-biometric-fingerprint-scanners-in-smartphones](https://www.biometricupdate.com/201911/chinese-researchers-reveal-method-to-bypass-biometric-fingerprint-scanners-in-smartphones)
[https://www.csoonline.com/article/2223077/laptop-fingerprint-reader-destroys-entire-security-model-of-windows-accounts.html](https://www.csoonline.com/article/2223077/laptop-fingerprint-reader-destroys-entire-security-model-of-windows-accounts.html)

We leave fingerprints all over the place, so they are available almost anywhere we've touched for someone else to copy.  I suppose if the goal is to keep a 10 yr old little brother off your computer, then fingerprints are fine ... until he gets some silly putty and hacks into the computer. Never use fingerprints to secure smart phones or tablets.

I've worked places that used fingerprint readers to provide access to more secure parts of the facility.  They had a long story about how THEIR specific reader couldn't be hacked by the most common methods and I think it was correct, but we'd often get stuck inside the room and have to press the emergency door-open to get out because all our hands were too cold to meet the required "finger temperature" level as proof our fingers were really connected to a human and not just silly putty.  About the 90th day straight of using the emergency exit button and they finally disabled the reader for exit needs.  That data center was kept very chilled.  

At another work location, we'd enter a pin code, our card-key/ID and only after both of those were accepted, our fingerprint would be scanned ... as the 3rd factor for access.

Rather than using a finger print, why not use a BT or RFID device?  If the BT device is in range, then allow unlocking the computer ... or even just automatically unlock it. I think that would be just as secure as a bad biometric device for authentication.  If you want a little more security, check out a Yubikey device.  These can be configured in a challenge/response mode and work completely offline.  I use one to unlock my LUKS encrypted storage. Without the yubikey, I'd need to type in a 60+ random character "backup" passphrase. I have doubts that I could accomplish that if impaired at any level. The yubikey is much more secure - something I have + the challenge is something I know.  The challenge can be any length. It gets run through the built-in, seeded, crypt function, then spits out a long result which is validated as the decryption passphrase. [https://developers.yubico.com/yubico-pam/Authentication_Using_Challenge-Response.html](https://developers.yubico.com/yubico-pam/Authentication_Using_Challenge-Response.html)

---

### Post by gigi1335 on 2022-01-12
Thanks a lot for your detailed and interesting answer !

---

