---
title: "Online banking security; how about this..."
date: 2009-02-05
forum: Security
---

### Post by runesvend on 2009-02-05
Hey all

I've been thinking a little about online banking, and about increasing the security of this on my computer and I would like to get some advice from people here on what they think about my approach. What I've been thinking about is the following:

[LIST=1]
[*]Create a user in Ubuntu used solely for online banking.
[*]The key-file that (in combination with a password) is used to log in to the online banking system should be owned by this user and only readable and modifiable by this user
[*]Logged in as this "online banking"-user, use Firefox with the NoScript add-on for online banking
[/LIST]

Wouldn't this be pretty safe? The only was a hacker could steal my key-file would be to gain root access to my computer or access to the "online banking"-account, both of which should have a strong password protecting them.

Please let me know if there are any flaws in this, or if there is some superior way, or additional security measures, for securing online banking.


Regards,

Rune

---

### Post by tubbygweilo on 2009-02-05
Some [thoughts]("http://ubuntuforums.org/showthread.php?t=833816") from a few months ago may offer some additional ideas.

---

### Post by hyper_ch on 2009-02-05
what's on that keyfile?

---

### Post by slowth5 on 2009-02-05
Hi runesvend,  

I've pondered secure online banking extensively, and your solution should work well.  You've mitigated the risk, but we must all be aware of the inherent insecurity of online banking.  I would be more concerned with your bank's security measures, since you and I are just small change to crooks.  I still think you're as safe as possible on your end, just watch out for phishers.

---

### Post by runesvend on 2009-02-05
> **tubbygweilo said:**
> Some [thoughts]("http://ubuntuforums.org/showthread.php?t=833816") from a few months ago may offer some additional ideas.
Thanks, I found that while searching the forums and it offers some pretty good advice, probably the most important advice actually. Though not much on the technical side.

> **hyper_ch said:**
> what's on that keyfile?
My bank says that it's an encrypted file containing, amongst other things, my password and some information from the bank. It's 500 bytes in size.

> **slowth5 said:**
> Hi runesvend,  

I've pondered secure online banking extensively, and your solution should work well.  You've mitigated the risk, but we must all be aware of the inherent insecurity of online banking.  I would be more concerned with your bank's security measures, since you and I are just small change to crooks.  I still think you're as safe as possible on your end, just watch out for phishers.
Cool, I'm glad to hear it. I realize phishing and trying to get the password from people via emails is the greatest security risk, but I'm sure I won't be doing that, so I'm more concerned with people hacking into my computer and stealing information. Using this method at least makes it harder for them.

---

### Post by brian_p on 2009-02-05
> **runesvend said:**
> 

. . . . . so I'm more concerned with people hacking into my computer and stealing information. Using this method at least makes it harder for them.

That's not one of my worries; I'm more concerned about being electrocuted when switching the machine on.

---

### Post by Koori23 on 2009-02-05
To my knowledge, the risk of online banking isn't the users machine necessarily. It's not even what goes on over the wire. It's what happens to the machine at the bank where that information is stored.

If that bank was as forward thinking as you are with your idea, that's a great step. However, I doubt they are that ambitious.

---

### Post by runesvend on 2009-02-06
> **brian_p said:**
> That's not one of my worries; I'm more concerned about being electrocuted when switching the machine on.
Huh? I'm not quite following you...

> **Koori23 said:**
> To my knowledge, the risk of online banking isn't the users machine necessarily. It's not even what goes on over the wire. It's what happens to the machine at the bank where that information is stored.

If that bank was as forward thinking as you are with your idea, that's a great step. However, I doubt they are that ambitious.
Yeah, I saw some analysis from a university saying that 75% of all online banking systems they tested had security flaws. 

But I'm thinking that if I do this on my part, at least I've done what I can to make the whole process more secure.

---

### Post by brian_p on 2009-02-06
> **runesvend said:**
> 

Huh? I'm not quite following you...

Neither event is likely to happen. Why be concerned about one rather than the other?

---

### Post by runesvend on 2009-02-06
> **brian_p said:**
> Neither event is likely to happen. Why be concerned about one rather than the other?
You're absolutely right, there's no reason to be concerned (worried) about it.

Instead, I'll just do the things described in the thread and leave it at that.

---

### Post by hyper_ch on 2009-02-06
safest thing would be to (a) store the keyfile encrypted on a usb stick, possibly in a truecrypt cotnainter and (b) use a ubuntud live cd for booting up.

That way nothing should be able to be hijacked.

---

### Post by xzero1 on 2009-02-06
> **hyper_ch said:**
> safest thing would be to (a) store the keyfile encrypted on a usb stick, possibly in a truecrypt cotnainter and (b) use a ubuntud live cd for booting up.

That way nothing should be able to be hijacked.

But Ubuntu live cds don't have the latest security updates. Please correct me if I am misinformed on this.

> Logged in as this "online banking"-user, use Firefox with the NoScript add-on for online bankingHow secure is NoScript?

---

### Post by hyper_ch on 2009-02-06
they don't but you won't be doing your online banking for hours at one time, right? you know you have an untainted system and chances any hacker will find a weakness just when you do online banking is slim.

---

### Post by xzero1 on 2009-02-06
> **hyper_ch said:**
> they don't but you won't be doing your online banking for hours at one time, right? you know you have an untainted system and chances any hacker will find a weakness just when you do online banking is slim.

I agree with you but I just wanted to point out possible issues.

---

### Post by tturrisi on 2009-02-07
Online bank sites use SSL, if not, change your bank.
All data over the SSL wire is encrypted and is difficult to decrypt.
The only real vulnerabilities that customers face are:
1. phishing scams.
2. storing login passwords locally.

It's foolish to have the browser "remember passwords typed in forms" and other form input.

All you need for secure online banking is a properly configured browser that supports SSL. Leave the rest of the security to the bank site.

Implementing additional security locally won't serve any purpose if the bank site is exploitable.

---

### Post by zerofool2005 on 2009-02-09
This is kinda like what barclays do. You log into online banking by putting your physical bank card into a non-connected chip reader. Enter your pin. And it generates a number. You enter the number in the website along with the bank account and password info. Has its flaws though. As its a predefined list with the algo used.

---

