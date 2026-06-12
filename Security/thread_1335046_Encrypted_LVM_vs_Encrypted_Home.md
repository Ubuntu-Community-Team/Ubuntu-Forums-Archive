---
title: "Encrypted LVM vs Encrypted Home"
date: 2009-11-23
forum: Security
---

### Post by Logan1985 on 2009-11-23
I'm about to re-install Ubuntu on my work machine (laptop, and I'm very mobile so loss/theft is a real possibility) and I am trying to weigh up the pros and cons of installing via the alternate CD and using the Encrypted LVM option, vs taking the Encrypted /home option from the regular install cd. 

I'm thinking in terms of performance, security, etc. Currently I'm leaning towards encrypted /home only but I would like to understand the trade off in security terms before I make a firm descision.

Many thanks

---

### Post by XCan on 2009-11-23
The tradeoff in terms of security when encrypting only /home is that you risk temporary files to be stored elsewhere, for example, in /tmp. Also, stuff that are swapped out may remain in the unencrypted swap-partition. But to be honest, if you're concerned with thieves stealing your notebook to sell them and make money, you should be fine with /home encryption, as the thieves hardly will have the knowledge to figure it out anyway. If you're concerned about espionage, then perhaps you should do a full-disk encryption, the tradeoff, according to Phoronix, seems to be about 5% performance hit using AES256.

---

### Post by Logan1985 on 2009-11-23
> **XCan said:**
> The tradeoff in terms of security when encrypting only /home is that you risk temporary files to be stored elsewhere, for example, in /tmp. Also, stuff that are swapped out may remain in the unencrypted swap-partition. But to be honest, if you're concerned with thieves stealing your notebook to sell them and make money, you should be fine with /home encryption, as the thieves hardly will have the knowledge to figure it out anyway. If you're concerned about espionage, then perhaps you should do a full-disk encryption, the tradeoff, according to Phoronix, seems to be about 5% performance hit using AES256.

Thanks for the input, most appreciated.

I also saw that post on Phoronix - the performance hit is less than I thought it would be. 

My main concern actually is the fact I use the laptop for some personal stuff as well as work related - and most of the personal stuff isn't going to go near /tmp but swap is a real possibility. 

You are quite correct about the thieves not having a clue, but complacency isn't really a quality of mine! I'm going to test out the encryped LVM option first. I like the idea of pre-boot auth (like with TrueCrypt for Windows).

Food for thought, I think. There is a strong argument in the corner of full encryption if the performance hit is only around 5%!

---

### Post by Grenage on 2009-11-23
LVM with encryption is a geed way to go, you don't have to think about it afterwards; you know that whatever you're working on is covered...

...unless you think someone is going to jack your RAM if you leave the system unattended, but let's not go there.

---

### Post by scaine on 2009-11-23
> **Grenage said:**
> ...unless you think someone is going to jack your RAM if you leave the system unattended, but let's not go there.

Anyone know if the Princeton attack (freezing the ram from a standby machine), works on a LUKS encrypted system?  I think it only works if you know where to look for the decryption key, which BitLocker always stores in the same bytes of memory...?  If LUKS does the same thing, then I suppose it would, but I have no idea how that system works.

---

### Post by fargle on 2009-11-23
I think that, no matter what LUKS does, finding the passphrase and/or key is a solveable problem.  If all else fails, it's in there somewhere and using a rolling sample of the captured RAM to test against the encrypted volume will find it a lot faster than brute-forcing it.

So physical security is still very important - don't leave your machine suspended to RAM unless you're in physical control of it at all times, and when in doubt, it's best to shut it down and make sure you retain control until the RAM degrades.

I do wish there was more TPM support for Linux to allow for key storage there, which would help fix some of these issues, but sadly there isn't.  IBM is moving on to systems that use a hypervisor for trusted boot, which supports TPM but is massive overkill for this scenario, IMHO.

---

### Post by FuturePilot on 2009-11-23
If you pick the encrypted home option at install, it will also encrypt your swap partition as well. However, that will break hibernate so beware if you use hibernate.

---

### Post by Logan1985 on 2009-11-23
Some nice tips there, thanks.

@fargle - I don't tend to use hibernate/standby. Especially if using pre-boot auth. 

@FuturePilot - Thanks - Didn't know that about swap. Not too fussed about losing hibernate functionality. Ubuntu starts and shuts down nice and fast anyway. It's MUCH faster than XP on that front (and in general, for that matter)

My Windows partition is playing up, so taking the opportunity to fully rebuild the machine from scratch. I'll use IBM recovery CD's to get the laptop back to standard, install necessary apps in XP, then shrink it down with GParted, leaving a few GB for as and when I need to use it. I will then use full disk encryption with TrueCrypt for that partition. Then I'm going to install Ubuntu, leaning towards alternate install (so encrypted LVM) at the minute. 

Should be pretty nice and secure then! Your average thief MAY be able to get into Linux if it's not encrypted, but I must admit, I am not concerned about potential RAM related attacks! 

Thanks for all the tips. It's all good learning.

---

