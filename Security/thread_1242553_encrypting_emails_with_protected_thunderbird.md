---
title: "encrypting emails with protected thunderbird"
date: 2009-08-17
forum: Security
---

### Post by markymark1 on 2009-08-17
Hi,

My problem is as follows.

I have recently converted my laptop from Windows to Ubuntu (and this has saved my laptop from becoming landfill).  On my laptop, I use Thunderbird for email and Enigmail for email encryption.  This works fine (though Enigmail does not seem to cope with html - which is frustrating with regard to things like signature blocks).

In order to improve security on my laptop, I have recently moved my Thunderbird profile into a TrueCrypt container in order to keep my inbox secure in the event of laptop theft.  Having copied my main profile folder (called 'm743qiwa.default) into the TrueCrypt container, I now wish to delete the original folder in order to prevent access to this unencrypted material.

This is where my difficulty lies.  If I delete the original m743 folder, Thunderbird continues to operate as normal in conjunction with my copied profile in the encrypted container.  However, at the same time, I lose the ability to encrypt or decrypt emails.  By moving the m743 folder back to its original location, I regain the encryption/decryption function.

Does anyone have any suggestions as to how I can remove my original Thunderbird profile from the open part of my system without losing the functionality of being able to encrypt/decrypt emails?

Many thanks if you are able to help.

---

### Post by markymark1 on 2009-09-18
A little embarrassing to be answering my own question, but here we go.

I'm not sure why moving my Thunderbird profile would have triggered the problem, but all I needed to do was to reinstall the Enigmail add-on in Thunderbird.  This then made the PGP options available to me again in account settings.

Mark

---

### Post by falconindy on 2009-09-19
Extensions reside in your profile directory. Moving the profile and recreating a new one is equivalent to removing the extension.

---

### Post by markymark1 on 2009-09-19
That would explain it.  Thanks.

---

