---
title: "Zip Security"
date: 2009-02-21
forum: Security
---

### Post by RealG187 on 2009-02-21
Okay I want to email my bank card number to myself because I can't remember it and I want to be able to access it easily from any computer. However I don't think this is a smart idea because email is not secure and someone could get my information.

If I were to maybe put it in a ZIP file and put a password on it would that help? But I think there are ways that people can decrypt zip archives.

What is a secure way I can store my bank card number for easy access without risking my security?

---

### Post by dzark on 2009-02-21
Linux is huge on pgp.. [http://en.wikipedia.org/wiki/Pretty_Good_Privacy](http://en.wikipedia.org/wiki/Pretty_Good_Privacy)

but for something small like this a password protected archive seems pretty easy. Not 100% about zips, but i do know RAR files need to be bruteforced. While there are programs out there that can do this, it's a time factor. If your password is 'thisismyrediculouslylongpasswordthatwillneverbeinadictionaryandmaybeilladdsomenumberstoittoo12345'

you're looking pretty good ;)

---

### Post by chmbrs on 2009-02-21
write it down on a piece of paper and carry it in your wallet. thats the safest way.

---

### Post by slowth5 on 2009-02-21
I wouldn't use zip.

> ZIP supports a simple password-based symmetric encryption system which is known to be seriously flawed. In particular it is vulnerable to known-plaintext attacks which are in some cases made worse by poor implementations of random number generators.



I would use GnuPG:

[http://ubuntuforums.org/showthread.php?p=4903822](http://ubuntuforums.org/showthread.php?p=4903822)

---

### Post by RealG187 on 2009-02-21
I have a piece of paper but my card is in my wallet anyways. I want a way to find it on my computer without having to goto get the card or paper.

What's PGP (I don't use Wikipedia anymore)

---

### Post by bodhi.zazen on 2009-02-21
I would not use Zip, it can be cracked.

Use encryption.

What you want is cross platform portable encryption that does not require root or admin access ...

Take a look here : 

[http://portableapps.com/](http://portableapps.com/)

All the applications I have tried (and I have tried many) run in wine (they may look ugly or be missing buttons, but the functionality is there).

I use KeePass with a key + a password : [http://portableapps.com/news/2009-02-21-_keepass_portable_1.15](http://portableapps.com/news/2009-02-21-_keepass_portable_1.15)

Edit: What is the big deal with Wikipedia ? good source of basic information, really can not expect us to type basic info if you are unwilling to look at a link or use google ;) Would I trust wikipedia to be a definitive source of information, certainly not, but often a good first step.

---

### Post by insane_alien on 2009-02-22
> **chmbrs said:**
> write it down on a piece of paper and carry it in your wallet. thats the safest way.

Yes, so if your wallet gets stolen, not only do they have your bank card(with which a lot of damage can be done in itself) but they also have the PIN to that bank account meaning they can go to the nearest atm and clear you out.

perfectly safe. 

its a 4 digit number, pull the finger out and memorize the bugger.

---

### Post by RealG187 on 2009-02-23
I also use Windows Mobile so I would need something compatible with that. I can memorize the PIN number just not the card number.

Regrading Wikipedia, it just sucks, the "information" there just confuses a person more and then when you go on the talk pages to ask you get flamed. And despite their saying that "anyone can edit" this is not true, every article I made get's deleted or redirected to something barely related. Example I made an article on buffer underun protection "Superlink" and it was redirected to the article for Nero Burning ROM. If you are looking for information about Super Link you already know it has something to do with Nero because Nero uses it and you probably first found out about it in Nero. The article for Nero Burning ROM does not mention the word Super link once, I tried CTRL+F and foound nothing, so the the reditect was a pointless vandalism. Plus some *** kept vandalising my user page.

I found since I left Wikipedia things have been better, as someone said regarding quitting Wikipedia "It feels good to quit, doesn't it?"

---

