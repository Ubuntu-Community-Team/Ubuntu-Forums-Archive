---
title: "I have a document that needs to be encrypted."
date: 2009-01-18
forum: Security
---

### Post by shiningkenmonster on 2009-01-18
I have this openoffice document that needs to be for my eyes only. Is there a way to lock this doc with a password protect? or make a 10 MB enyrupted safe?

I am running ubuntu 8.04 with the Dell's custom version of Ubuntu with the LPIA.

i heard Ubuntu 8.10 already has a build in encryption. but i need it for Ubuntu 8.04

---

### Post by kbuel on 2009-01-18
You could check out gpg.

it is a pretty standard tool used to encrypt and decrypt files.  It also integrates well with email clients, so that you can send encrypted mail to people.

---

### Post by jrusso2 on 2009-01-18
I would check out true crypt there is a Linux version, if not gpg should do it.

---

### Post by shiningkenmonster on 2009-01-18
> **jrusso2 said:**
> I would check out true crypt there is a Linux version, if not gpg should do it.

i just installed it. How do I use true crypt?

---

### Post by Tubes6al4v on 2009-01-18
For truecrypt, just type ```
sudo truecrypt
```

If you want it just for your ubuntu side, then you could just right click it and select encrypt, using (I think) dm-crypt.

---

### Post by binbash on 2009-01-18
+1 for truecrypt.Encrypt the file via truecrypt

---

### Post by hyper_ch on 2009-01-18
protect against whom?

---

### Post by The Cog on 2009-01-18
In the OpenOffice File->Save As dialog, there is a checkbox for Save With Password. Use a strong password to prevent dictionary attacks.

---

### Post by kevdog on 2009-01-18
I'd still use gpg -- its well known, proven, and has many several ciphers you can use for either asymmetric or symmetric encryption methods.  Yes I suppose a case could also be made for truecrypt which isn't a bad option, however I think for encrypting individual files, gpg is an ideal option.

---

### Post by shiningkenmonster on 2009-01-18
> **hyper_ch said:**
> protect against whom?

oh you know, from police, law enforcers, the FBI. People in general too.

Do you think the true crypt or gpg is good enough? Whats your recommendation?

---

### Post by shiningkenmonster on 2009-01-18
> **The Cog said:**
> In the OpenOffice File->Save As dialog, there is a checkbox for Save With Password. Use a strong password to prevent dictionary attacks.

thanks, i didnt know openoffice had a feature like that. I wish it has that 3 attempt try, if fails lock the file down for a couple of minutes. Which would make the dictionary attack try harder and longer.

---

### Post by shiningkenmonster on 2009-01-18
> **kevdog said:**
> I'd still use gpg -- its well known, proven, and has many several ciphers you can use for either asymmetric or symmetric encryption methods.  Yes I suppose a case could also be made for truecrypt which isn't a bad option, however I think for encrypting individual files, gpg is an ideal option.

i ll try gpg

---

### Post by hyper_ch on 2009-01-19
> **shiningkenmonster said:**
> oh you know, from police, law enforcers, the FBI. People in general too.

In that case just encrypting that one file won't calm your mind as there will be fragments left of the uncrypted file.

---

### Post by shiningkenmonster on 2009-01-19
> **hyper_ch said:**
> In that case just encrypting that one file won't calm your mind as there will be fragments left of the uncrypted file.

what does that mean?

---

### Post by hyper_ch on 2009-01-19
what part don't you understand?

---

### Post by tubbygweilo on 2009-01-19
> **shiningkenmonster said:**
> oh you know, from police, law enforcers, the FBI. People in general too.

Do you think the true crypt or gpg is good enough? Whats your recommendation?

shiningkenmonster, 
you can I expect slow the law enforcement officers and others in their task of examining your data by adopting measures such as full disk encryption, truecrypt, gpg either alone or in combinations but then you may well be the weak link rather than your encryption methods. When asked a question about how to keep things safe from others I would at first suggest keeping all such data in a truecrypt container that way I know that all data is encrypted by default when not in use and as a bonus held in one place. I have yet to see widespread debate in the Ubuntu or the open source world suggesting that this is a bad idea. 

One thing against it is that the container may be removed from you disk and subjected to extended examination but I expect you may well  divulge your encryption keys way before that becomes necessary.

---

### Post by shiningkenmonster on 2009-01-19
> **hyper_ch said:**
> what part don't you understand?

the whole thing

---

### Post by shiningkenmonster on 2009-01-19
> **tubbygweilo said:**
> shiningkenmonster, 
you can I expect slow the law enforcement officers and others in their task of examining your data by adopting measures such as full disk encryption, truecrypt, gpg either alone or in combinations but then you may well be the weak link rather than your encryption methods. When asked a question about how to keep things safe from others I would at first suggest keeping all such data in a truecrypt container that way I know that all data is encrypted by default when not in use and as a bonus held in one place. I have yet to see widespread debate in the Ubuntu or the open source world suggesting that this is a bad idea. 

One thing against it is that the container may be removed from you disk and subjected to extended examination but I expect you may well  divulge your encryption keys way before that becomes necessary.

Yes, i was thinking about that. That is one reason when i had an option to buy a new mini notebook. I had two choices to a 8 GB SSD, or the 16 GB SSD. I decided to get the 8 GB SSD. So I can store "other" data on memory cards.

I have two SDHC cards right about now, but i was thinking about buying one to place sensitive data in it, and encrypting the whole memory card. 

If i knew prior someone such as a law enforcement officers to examine my stuff. I would just destroy the memory card with a hammer.

---

### Post by Tubes6al4v on 2009-01-19
Disclaimer: I am not an expert, this is just how I explain it to myself.

Things become much more complicated when considering a well funded organization may want your information. 

Most well funded organizations can have phorensic testing done to your memory storage device. If you smash it with a hammer, they may be able to recover some of the data. With modern journaling file systems, some of the data is written like a map to prevent seaking latency. Also, SWAP space, or non-RAM memory is written to the disk, and even if it is written to all 0's, there is a ghost image of what was there before. You could overwrite it with random data, which may not be a bad idea, but it is time consuming. Then there are logs all through the programs you run and the OS, so there are traces. I think this is what hyper_ch was saying. The only way to protect this is to encrypt everything (with the exception of /boot , so that you can boot).

The US as well as others can compell you to reveal your passphrase (is this only for terrorist allogations? They could always say that and then find something else). Unfriendly organizations can also rely on torture or threats to get the passphrase from you. This is why stenography is so interesting. I have only played around with it on Truecrypt, but it allows you to create a hidden volume within another encrypted volume. You can make a hidden Windows OS (no linux or mac yet). With a hidden OS, the advantage is that, if you set things up correctly, it will be virtually impossible to prove the existence of data or even the OS. Have a look through their documentation.

---

### Post by tubbygweilo on 2009-01-19
> **shiningkenmonster said:**
> If i knew prior someone such as a law enforcement officers to examine my stuff. I would just destroy the memory card with a hammer.

shiningkenmonster,  If they come after you with a No knock warrant then your attempts to destroy your data will be the least of your problems.

---

### Post by HermanAB on 2009-01-19
You are not paranoid, if they really are out to get you...
;)

If an organization with unlimited funding (FBI) is out to get you, then you don't have much of a fighting chance.  However, just using Linux already provides a lot of protection, even without encryption, against ordinary scoundrels.

If you want to use encryption, then you should encrypt at least /swap and /home.  (/tmp is in RAM nowadays with tmpfs).  Encrypting less than those two partitions is a waste of time, since there will be bits and pieces of plain text data on the drive.

In general, encryption only works properly when used in a physically secure environment such as a defence force comcen where you are in the middle of a military base where everyone is trained and armed.

Cheers,

Herman

---

### Post by Tubes6al4v on 2009-01-20
Wouldn't a desktop be preferable if someone broke into your house while you were on the computer? You could just pull the plug, then the drive is just encrypted and the data on RAM quickly fades. Is this right?

---

### Post by Primefalcon on 2009-01-20
Use GPG that's an open source version og PGP which well has even had the government mistified ;-)

---

### Post by shiningkenmonster on 2009-01-20
> **Tubes6al4v said:**
> Wouldn't a desktop be preferable if someone broke into your house while you were on the computer? You could just pull the plug, then the drive is just encrypted and the data on RAM quickly fades. Is this right?

data can be stored up to 2 hours in the physical RAM after a shutdown.

---

### Post by Tubes6al4v on 2009-01-20
Damn, but that is less the hotter it is right? Not that I would want my box to be particularly hot. I guess an emergency shutdown could be configured that stops everything and overwrites the ram. Though 4gb of data even to ram, may take too long.

---

