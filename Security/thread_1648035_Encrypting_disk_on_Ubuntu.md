---
title: "Encrypting disk on Ubuntu?"
date: 2010-12-18
forum: Security
---

### Post by PDA1 on 2010-12-18
I'm new to the encryption stuff and I've read you can encrypt portions of a hard drive and/or separate files.  

I've used Truecrypt and never have had any trouble with it- except the "awful-awful" of forgetting the password.

What would you recommend in terms of encrypting stuff on my computer and what areas or folders should be encrypted.  Yes, I know "only I can decide" what should be encrypted so I guess I'm looking for your opinion, or what is the current doctrine, concerning encrypting a file system or hard drive?

I've read some folks recommending encrypting the home folder but I don't know what that means.

---

### Post by surfer on 2010-12-18
when you install the ubuntu desktop edition you are asked during the install process if you want your password to just log you in or also to be used to encrypt your home directory. if you choose this second option, your home is encrypted.

if you are working in a really sensitive environment there is more to consider: swap and /tmp may be filled with sensitive data that remains there even if your computer is shut down. if you have databases, /var is the place where most of the data goes. your filenames are usually also stored in /var (for the locate db). if you need all that to be encrypted as well, i'd recommend the ubuntu alternate cd, where you can use dm-crypt (during the installation; i.e. the partitioning).

i tend to create a /boot partition (256MB, not encrypted), a swap partition, encrypted with a random key, a /tmp partition, also with a random key, and a big passphrase encrypted partition where i put my /home and / in a linux volume group.

---

### Post by Megaptera on 2010-12-18
What version of Ubuntu are you running? Lucid & Maverick give you the option of encrypting home while you're installing.

Also:
7 Steps To An Encrypted Partition (local or removable disk)
[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

and how to enable full disk encryption in Lucid
[http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html)

---

### Post by PDA1 on 2010-12-18
I'm running 10.04

---

### Post by PDA1 on 2010-12-18
> **Megaptera said:**
> What version of Ubuntu are you running? Lucid & Maverick give you the option of encrypting home while you're installing.

Also:
7 Steps To An Encrypted Partition (local or removable disk)
[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

and how to enable full disk encryption in Lucid
[http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html)


Those are good ideas.  The problem is I don't know what to do.  The var and tmp problems (not that I have any idea what that's about) are something I have no idea what to do about.

To put it bluntly- I want to encrypt my system so that no one can access it without a password and I don't want the system to slow down because of an encryption system....though I know there will be some.

---

### Post by PDA1 on 2010-12-18
> **surfer said:**
> when you install the ubuntu desktop edition you are asked during the install process if you want your password to just log you in or also to be used to encrypt your home directory. if you choose this second option, your home is encrypted.


if you are working in a really sensitive environment there is more to consider: swap and /tmp may be filled with sensitive data that remains there even if your computer is shut down. if you have databases, /var is the place where most of the data goes. your filenames are usually also stored in /var (for the locate db). if you need all that to be encrypted as well, i'd recommend the ubuntu alternate cd, where you can use dm-crypt (during the installation; i.e. the partitioning).


i tend to create a /boot partition (256MB, not encrypted), a swap partition, encrypted with a random key, a /tmp partition, also with a random key, and a big passphrase encrypted partition where i put my /home and / in a linux volume group.


What do you do IF you've already installed Ubuntu and want to encrypt the home folder?

Can the swap /tmp and /var stuff be deleted manually before I shut my computer down....?

That stuff is beyond me.

---

### Post by Megaptera on 2010-12-18
> **PDA1 said:**
>  I want to encrypt my system so that no one can access it without a password and I don't want the system to slow down because of an encryption system....though I know there will be some.

How to enable full disk encryption in Lucid
[http://rationallyparanoid.com/articl...-security.html](http://rationallyparanoid.com/articl...-security.html)

If that's not your preferred option, how about doing a fresh install (having backed up all docs etc to external media) and select encrypted home partition at install?

Or carry on with TrueCrypt?

Or look at have a look at Ubuntu Privacy Remix. Boot from CD, do your docs etc from USB, shut down disc & remove ...

From their website: "The goal of Ubuntu Privacy Remix is to provide an isolated working environment where sensitive data can be dealt with safely. The system installed on the computer running UPR remains untouched, UPR is not intended for permanent installation on hard disk. Instead of that Ubuntu Privacy Remix runs from a modified Live-CD based on Ubuntu Linux. All user data reside exclusively on encrypted removable media.
Ubuntu Privacy Remix is a tool to protect your data against unsolicited access. The risk of theft of such private data arises not only from "conventional" criminals, trojans. rootkits, keyloggers etc."

[https://www.privacy-cd.org/](https://www.privacy-cd.org/)

---

### Post by PDA1 on 2010-12-18
Well now....that makes some sense.

Thank you, all, for the suggestions and ideas.

Perhaps, I should stay with TC and hope there's no corruption of TC or the files.

---

### Post by Megaptera on 2010-12-18
You're welcome, making some TC backups of your TC stuff to seperate external media might be a good idea.

Cheers

---

