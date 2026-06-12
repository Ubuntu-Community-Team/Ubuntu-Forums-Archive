---
title: "PGP Key mobility??"
date: 2009-06-04
forum: Security
---

### Post by ManiDhillon on 2009-06-04
Hi there! I want some questions anawered about making PGP keys in Ubuntu 9.04.
Ah in-fact I know how to make them. :)

I dont' know whether it is possible or not but here is the situation!
Assume I make a PGP key for myself say to encrypt and sign e-mails now if I somehow want to use the same key as OWNER on another OS(slackware)?

Or say I install another copy of Ubuntu's upcoming release on my other PC and I want to use the same key as owner in that installation too.

How to do I do that? I know I can export keys but what then?

[To MODS: I don't know where to post this query, so if I am in wrong place move it to the right one!]

---

### Post by kevdog on 2009-06-04
You can definitely import and export the public and private keyrings.  Are you using PGP or GPG?  GPG is opensource, PGP is not.

---

### Post by Agent ME on 2009-06-04
You can extract your keys from your keychain on one computer and import them on the other.

But even easier is to just copy the keychain files from one to the other computer. Just copy the ~/.gnupg directory to your other computer.

---

### Post by ManiDhillon on 2009-06-05
> **Agent ME said:**
> You can extract your keys from your keychain on one computer and import them on the other.

But even easier is to just copy the keychain files from one to the other computer. Just copy the ~/.gnupg directory to your other computer.
Will I be able to use them as owner then? 
I mean can I edit them like add new emails and encryption methods?

---

### Post by rookcifer on 2009-06-05
> **ManiDhillon said:**
> Will I be able to use them as owner then? 
I mean can I edit them like add new emails and encryption methods?

Yes.  I recently did a reinstall and I copied my .gnupg folder to a USB stick.  Once I got the OS installed, I copied that folder over to /home/.gnupg.  It works just exactly as it did before.

---

### Post by ManiDhillon on 2009-06-05
Thanks Agent ME and Rookcifer!
It is a great help you know! I really need this thing!
Thanks to all of you man!

---

