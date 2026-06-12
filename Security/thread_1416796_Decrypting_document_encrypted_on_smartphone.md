---
title: "Decrypting document encrypted on smartphone"
date: 2010-02-26
forum: Security
---

### Post by Irihapeti on 2010-02-26
I'm an absolute beginner at encryption. gpg and keys still have me somewhat mystified, so please forgive me if the following seems like a stupid question.

I'm looking at encryption software for my smartphone. I've found a Java program called TinyEncryptor that uses the TwoFish algorithm and claims to be a shell for the "Legion of the Bouncy Castle" libraries. It just uses a passphrase; there are no keys involved as far as I am aware.

Naturally, I would like to be able to decrypt files on my desktop that I've encrypted with this program. So far, I've not had any success with finding one. How would I would I know which program to use and the appropriate settings?

---

### Post by Agent ME on 2010-02-27
If it's a java program, couldn't you run it on your computer too? (Though I guess it's some phone's version of java, so it might not be completely straightforward.)

---

### Post by Irihapeti on 2010-02-27
> **Agent ME said:**
> If it's a java program, couldn't you run it on your computer too? (Though I guess it's some phone's version of java, so it might not be completely straightforward.)

I thought about that, actually, but you are right: programs written for J2ME (the phone version of Java) don't run on desktop Java. There are emulators, but you have to install the full Java Development Kit (over 100MB) to run them, which seems a bit over the top for a non-developer. Even then, I can't be sure that I'd be able to access files outside of the emulation environment.

I do have a non-free option, but naturally I'd prefer something else.

---

### Post by Irihapeti on 2010-03-01
Update:

I asked the same question of the TinyEncryptor developer. A decryption program written for desktop Java has appeared on his website. I've tested it and it does what I want. Nice one!

---

