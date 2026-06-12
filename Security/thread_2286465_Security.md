---
title: "Security"
date: 2015-07-12
forum: Security
---

### Post by gordie692 on 2015-07-12
Hey I'm using ubuntu 14.04 and I here so much about linux isn't safe for banking online and should wanted to here from you guys if so. I heard that if I use linux for my banking needs and don't use the banks software I won't get reinbursed for if anything happens so is linux safe 
or should I use W7 with trustee rapport and say avast antivirus for W7

---

### Post by CharlesA on 2015-07-12
It should be ok as long as you keep it updated. However, if the bank is not going to cover any issues of fraud unless you are using Windows and have their software installed, you should use Windows and install their software.

---

### Post by QIII on 2015-07-12
I would contact your bank.

I've "heard" a lot of things about Linux.  Some of them are actually true.

---

### Post by CharlesA on 2015-07-12
> **QIII said:**
> I would contact your bank.

I've "heard" a lot of things about Linux.  Some of them are actually true.

+1. You might get a response similar to "We only support Windows" though.

---

### Post by buzzingrobot on 2015-07-28
To follow up on this and the closed thread the OP open y'day, the OP needs to query that bank to obtain, in writing, the specific scenarios in which the OP would be left liable for fraud on the account. That kind of info should already be posted at the bank's site; in the fine print. (If the bank actually includes that kind of requirement in its terms of service, I doubt it is enforceable.)

I would ask questions like this: if someone breaks into the bank's system and transfers money out of my account, will you really not make good unless I prove I had installed that prescribed software on my own PC? (Note that the software you install on your PC, or even whether that PC is turned on or turned off, has nothing to do with the bank's own security system and its responsibility to protect your data and your funds in its system.)

Liability for credit card fraud is typically set by the credit card issuers, and if that is not the bank, then the question should also be asked of them.

I don't see how a bank would know what, if any, AV software a user was using on a machine to access an account.  Mandating use of specific Windows desktop software also rules out using the bank via phone or tablet. 

The best thing the bank could do to improve the user's security is to offer Second Factor Authentication. I wouldn't use online banking without it.

---

### Post by TheFu on 2015-07-28
AV is a joke.  50% effective for stuff from last year, if that.  Running 10 AV might get you to 80% effective.

There was an article this week about the differences in behavior between how security experts behave online and what normal people do. Very enlightening. [http://arstechnica.com/security/2015/07/what-amateurs-can-learn-from-security-pros-about-staying-safe-online/](http://arstechnica.com/security/2015/07/what-amateurs-can-learn-from-security-pros-about-staying-safe-online/) is one of the better summaries.

When it comes to online banking - I follow Brian Krebs' advice philosophy, if not exactly. [http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/) 
a) I use a liveCD (tinycore Linux) for all online banking. It is actually the .iso file.
b) I use a different browser than I use for any other purpose (avoid cross contamination due to network shared bookmarks, etc).
c) I run this liveCD inside a VM that does NOT have another other use, purpose, running on a fully patched, not directly connected to the internet Linux system.

Some financial institutions DO offer 2FA, but sadly do not mandate it and allow customers to access their accounts without using it.

Whatever you do, do NOT use android or iphone/itablet for online banking. I'm always surprised when people do that. Those devices have so many security issues I don't even allow them on my secure home network - limited to the "guest network" like the kids and visitors get.

I had to be a little more paranoid, because of business bank accounts. Those do not have the same liability protections (in the USA) as private personal accounts. If that cash is gone - the bank isn't liable usually and it never comes back. Just try to explain to employees that they won't get paid because the money has been stolen. ;(

---

### Post by buzzingrobot on 2015-07-28
> **TheFu said:**
> AV is a joke.  50% effective for stuff from last year, if that.  Running 10 AV might get you to 80% effective. 

I am thoroughly skeptical of AV reviews and tests.  Among other reasons, I've never come across any that report how often an AV vendor pushes out signature updates.   


> There was an article this week about the differences in behavior between how security experts behave online and what normal people do. Very enlightening. [http://arstechnica.com/security/2015/07/what-amateurs-can-learn-from-security-pros-about-staying-safe-online/](http://arstechnica.com/security/2015/07/what-amateurs-can-learn-from-security-pros-about-staying-safe-online/) is one of the better summaries.

That got a fair amount of coverage, which is good. It highlights misunderstandings about where security threats come from.

> When it comes to online banking - I follow Brian Krebs' advice philosophy, if not exactly. [http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/) 
a) I use a liveCD (tinycore Linux) for all online banking. It is actually the .iso file.
b) I use a different browser than I use for any other purpose (avoid cross contamination due to network shared bookmarks, etc).
c) I run this liveCD inside a VM that does NOT have another other use, purpose, running on a fully patched, not directly connected to the internet Linux system.

I'm a bit more relaxed.  I just use one app on one device for one personal account.  The bank offers 2FA and I use it. I try to avoid bank access away traveling, but if I do need to I'll use the same app on a phone's cell network rather than risk wifi at an airport/hotel/coffee shop. (The bank does not mandate 2FA, but funds cannot be moved out of the account in any way without it, nor can any changes be made to the account. It's also required if the bank's cookies are gone, i.e., on a new browser, new device, etc.)


Back to the OP's issue... if that bank actually does insist that customers run certain flavors of AV software, then the bank ought to provide it gratis.  Not that I think they can verify its presence.

---

