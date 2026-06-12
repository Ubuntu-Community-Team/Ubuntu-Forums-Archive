---
title: "Encryption-is it necessary?"
date: 2008-08-22
forum: Security
---

### Post by EdThaSlayer on 2008-08-22
I was thinking of making my whole hard drive one huge encrypted partition. 
But my question to you is if it's actually worthwhile?
Linux(Kubuntu 8.04) is secure out of the box right? So is it really necessary for you to encrypt your hard drive even if you're the only one using the pc? I know encryption protects you and all but is it actually worth the effort of setting it up?


Thank you in advance.

---

### Post by hyper_ch on 2008-08-22
encryption -- protection from physical access

---

### Post by Oldsoldier2003 on 2008-08-22
> **EdThaSlayer said:**
>  I know encryption protects you and all but is it actually worth the effort of setting it up?


For a laptop I'd say yes. I personally have no need to whole disk encrypt my desktop so I don't.

As Hyper_ch pointed out in the post above, whole disk encryption is meant to protect you against physical access. If you aren't worried about that then its not worth the trouble.

---

### Post by niteshifter on 2008-08-22
Hi,

I think no, it's not worth it for most people, be the machine laptop or desktop. Much better to learn a bit of "storage discipline" and use tools like gpg or truecrypt.

Whole Disk Encryption - like any other aspect of security - is a set of trade-offs you have to make. Key management is one issue: one user, one key ... the problem is obvious:) In the corporate environment a key escrow scheme is used - if Ms Comptroller falls over dead this evening, the CIO, CTO, CFO (plus more if desired) can submit their keys to unlock and reset the key for the Comptroller's laptop in the am. This is difficult to do on a personal level: issues about trust and accountability exist.

Another oft overlooked thing is backup. Most backup tools have the smarts to read the file system and only backup what actually exists, that is to say a 120GB disk with 40GB of files: 40GB gets read and compressed onto backup media. Were that WDE that's a single 120GB chunk to read and write.

It should go without saying, but I'll say it anyway: If you are backing up an encrypted drive over an unsecured path (net backup) or to unencrypted media: Then what the hell is the point of the encrypted disk?

Also overlooked is repair: One stands a sporting chance at recovery if the EIDE/SATA controller or cable flakes out with an ordinary disk. Encryption can make this difficult, if not flat out impossible.

Myself, I use truecrypt to provide a few container volumes to keep sensitive stuff in. I use a two-tier approach: Tier 2 is stuff I prefer to keep private - but will divulge if I can be convinced of the need. Tier 1 is stuff that only a valid subpoena will unlock. The container file sizes are small (less than 2GB) for "quick" backup to external HD, DVD or flash drives. Tier 2 is protected by pass-phrase only, Tier 1 is pass-phrase and keyfile protected, with the keyfile(s) kept off-system.

---

### Post by hyper_ch on 2008-08-22
> **niteshifter said:**
> Much better to learn a bit of "storage discipline" and use tools like gpg or truecrypt.
Hmmmm, what about /tmp and swap, log files that could contain clues.... with storage discipline you can make it more or less equally save... problem is people are not disciplined....

> **niteshifter said:**
> one user, one key ... the problem is obvious:) 
luks: 1 storage device, 10 keys


> **niteshifter said:**
> Another oft overlooked thing is backup. Most backup tools have the smarts to read the file system and only backup what actually exists, that is to say a 120GB disk with 40GB of files: 40GB gets read and compressed onto backup media. Were that WDE that's a single 120GB chunk to read and write.
Or you sync the unlocked data to another unlocked data container ;)

> **niteshifter said:**
> It should go without saying, but I'll say it anyway: If you are backing up an encrypted drive over an unsecured path (net backup) or to unencrypted media: Then what the hell is the point of the encrypted disk?
that's why you also encrypt the media accordingly... setup a backup external disk or onto another full encrypted system...

> **niteshifter said:**
> Also overlooked is repair: One stands a sporting chance at recovery if the EIDE/SATA controller or cable flakes out with an ordinary disk. Encryption can make this difficult, if not flat out impossible.
That's what backups are for :)

---

