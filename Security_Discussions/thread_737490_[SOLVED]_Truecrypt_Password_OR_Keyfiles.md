---
title: "[SOLVED] Truecrypt Password OR Keyfiles?"
date: 2008-03-27
forum: Security Discussions
---

### Post by saj0577 on 2008-03-27
Hey,

Im wondering whether if i have no password and just purely use keyfiles if this is still a secure way? Or is it recommended to always use a password as well?

Opinions please.

Saj

---

### Post by gilgongo on 2008-03-27
If you're OK with losing your keyfile in the knowledge that the finder can just hit return and get in to your machine, then fine. 

Security is all about what you have to lose anyway. Use tight security when you want to protect something, don't use any when you don't.

---

### Post by saj0577 on 2008-03-27
So they still need keyfile to get in yeah? I just thought that they might be able to bypass it somehow.

Saj

---

### Post by wieman01 on 2008-03-28
_You have 3 options:_

1. Password only
2. Keyfile only (no password)
3. Password & keyfile

Talking about option 3, the password is there to protect the key file in case it gets stolen. Your password encrypts the key file and hence sort of protects it.

I recommend that you go for a option 1. Choose a long & secure password which is a good trade-off between security & convenience. Also you don't have to worry about the key file. If you lose it, you might as well lose all your precious data.

---

### Post by saj0577 on 2008-03-28
Okay Cheers il have to change my scripts then.

Saj

---

### Post by cprofitt on 2008-03-29
I use a 21 character password... and no key file... though I have thought of using a key file.

---

### Post by saj0577 on 2008-03-30
How you pick a password u rememeber. Yous just think of a phrase of something and add random numbers and dashes in it?


Saj

---

### Post by euler_fan on 2008-03-30
> **saj0577 said:**
> How you pick a password u rememeber. Yous just think of a phrase of something and add random numbers and dashes in it?


Saj

One of my favorites for people who don't want to go completely pseudo-random is to take it in pieces:

Part One: A word, phrase, whatever, which you can easily remember.
Part Two: ten pseudo-random characters.

put part two after part one (with or without a space is your choice if your password system supports spaces) and bingo: long password which should be both relatively easy to remember and also hard to crack (even by dictionary attacks!)

---

### Post by saj0577 on 2008-03-30
Then how your remeber the characters you just memerise them after a while?

Saj

---

### Post by hyper_ch on 2008-03-31
> **PrivateVoid said:**
> I use a 21 character password... and no key file... though I have thought of using a key file.

Bad thin to tell the exact lenght ^^


> **saj0577 said:**
> Then how your remeber the characters you just memerise them after a while?

Saj

You don't have to rembmer the password just how you get it... e.g. take your favourite poem or song or whatever (as example I'm going to use Cesar's first phrase in De Bello Gallico:

> 
Gallia est omnis divisa in partes tres, quarum unam incolunt Belgae, aliam Aquitani, tertiam qui ipsorum lingua Celtae nostra Galli appellantur.


The simplest one is to take the first letter of each word:

[G]allia [e]st [o]mnis [d]ivisa [i]n [p]artes [t]res, [q]uarum [u]nam [i]ncolunt [B]elgae, [a]liam [A]quitani, [t]ertiam [q]ui [i]psorum [l]ingua [C]eltae [n]ostra [G]alli [a]ppellantur.

Ending up with:
GeodiptquiBaAtqilCnGa (21 chars)

Now you can alter it a bit:
tres means "3", unam means "1", tertiam means "third". You can use "3" for third or replace with "3rd" or with 3.

Geodip3q1iBaA 3 qilCnGa

Geodip3q1iBaA 3rd qilCnGa

Geodip3q1iBaA 3. qilCnGa

To add more complexity we can even add birth and death dates (years) to it. July 13, 100 BC – March 15, 44 BC:

J13100BC  Geodip3q1iBaA 3. qilCnGa  M1544BC

Now, that password is difficult to remember but you can deduce it anytime. Howevder for cracking it it's not quite simple.

---

### Post by saj0577 on 2008-03-31
Thanks so much very good post!!

Cheers
Saj

---

### Post by picopir8 on 2008-03-31
> **euler_fan said:**
> One of my favorites for people who don't want to go completely pseudo-random is to take it in pieces:

Part One: A word, phrase, whatever, which you can easily remember.
Part Two: ten pseudo-random characters.

put part two after part one (with or without a space is your choice if your password system supports spaces) and bingo: long password which should be both relatively easy to remember and also hard to crack (even by dictionary attacks!)

I use a similar approach.  Find a phrase that is easy to remember and just use the first or last letter from each word, lyrics from songs are usually easy to remember. Then, prefix or append the newly created acronym with the date you created the password.  That will make it easy to remember what the number is until it is set to memory.  It will also remind you how long you have been using the password so you know when to change it.  The end result is a password that  can be set to memory easily but looks meaningless.

---

### Post by euler_fan on 2008-03-31
> **saj0577 said:**
> Then how your remeber the characters you just memerise them after a while?

Saj

Yes and no.

I find simply opening a text editor and typing the password a couple dozen times will imprint it into muscle memory--in fact I really can't tell anyone my most secure passwords because it's become second nature to see a certain prompt and enter the correct password.

On a side note . . . 

I have my doubts about schemes like "take a long phrase and use the first letter of each word" because of entropy concerns. Simply put, the first letters of words in any language are not random. Naively, look at the relative lengths of the various chapters of an Oxford English Dictionary. Consequently, it will be possible to generate dictionaries to attack such constructions which are far shorter than would otherwise be necessary because one can start with the most likely constructions (and the usual obfuscations) before moving on to less likely ones.

---

### Post by saj0577 on 2008-03-31
So you just put together random characters and memerise them?

Saj

---

### Post by euler_fan on 2008-03-31
> **saj0577 said:**
> So you just put together random characters and memerise them?

Saj

More to the point, I use KeePassX to manage my passwords and have it generate pseudo random passwords for things I really need to be secure, then memorize them.

Mostly, though, I have memorized the one HUGE password protecting the password database then copy-paste the passwords where I need them. Other ones I use regularly I end up memorizing too.

---

### Post by picopir8 on 2008-03-31
> **euler_fan said:**
> 

On a side note . . . 

I have my doubts about schemes like "take a long phrase and use the first letter of each word" because of entropy concerns. Simply put, the first letters of words in any language are not random. Naively, look at the relative lengths of the various chapters of an Oxford English Dictionary. Consequently, it will be possible to generate dictionaries to attack such constructions which are far shorter than would otherwise be necessary because one can start with the most likely constructions (and the usual obfuscations) before moving on to less likely ones.

such acronyms are not truly random, but they are more than sufficient.  The average person is only able to memorize a 7 character sequence of numbers/letters, and 10 characters is about the maximum.  Using a long acronym allows a person to generate much longer passwords that would be more secure than a shorter purely random sequence.

---

### Post by euler_fan on 2008-03-31
> **picopir8 said:**
> such acronyms are not truly random, but they are more than sufficient.  The average person is only able to memorize a 7 character sequence of numbers/letters, and 10 characters is about the maximum.  Using a long acronym allows a person to generate much longer passwords that would be more secure than a shorter purely random sequence.

I would find it reasonable to use a 7-10 character random salt in addition to your suggested pass phrase scheme. In fact, with a well chose salt one could use a well chosen dictionary word (e.g. a random one which is still easy to associate with a site, etc) and do any number of interesting things with it to form hard-to-guess passwords. I don't recommend it, but it would be possible nonetheless.

The point--mostly--is to expand the search space for an attacker to the point where brute force is more effort than whatever you password is protecting is worth. Nothing does that better than (pseudo) random passwords.

---

### Post by saj0577 on 2008-04-01
KeePassX wont it leave history in your clipboard of your passwords?


Saj

---

### Post by euler_fan on 2008-04-01
> **saj0577 said:**
> KeePassX wont it leave history in your clipboard of your passwords?


Saj

To my understanding, no. As it is, Linux clears the clipboard of associated materials whenever a program is closed.

---

### Post by saj0577 on 2008-04-02
Thanks :D

Just it would be bit pointless having passwords if they stored in a clipboard hehe



Saj

---

### Post by cprofitt on 2008-05-11
> **saj0577 said:**
> KeePassX wont it leave history in your clipboard of your passwords?


Saj


It should not do that, but it will likely still be in memory. Though I would not think it likely that a person could get a ram dump from your computer.

---

### Post by saj0577 on 2008-05-11
Okay thanks

Saj

---

