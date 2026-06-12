---
title: "gnupg key confusion?"
date: 2012-04-23
forum: Security
---

### Post by Matt 6:27 on 2012-04-23
Still trying to get my head around what's happening here, so please bear with me.  

I have two key pairs (call them K1 and K2) on my newly installed 64bit 12.04.  The key pairs were created using seahorse a few versions ago in Lucid... I've simply moved them along as I upgraded to 11.10 and now to 12.04.  Each upgrade has been a clean install.  I'm using seahorse-nautilus and not the command line.

Here's the issue:  If I encrypt a file using K1, then attempt to decrypt the file, the system asks for the passphrase for K2.  In fact, K1's passphrase will not decrypt the encrypted file, but K2's will.

If I encrypt with K2, only K2's passphrase will decrypt it (as one would expect).

This obviously leaves cause for concern.  Has anyone else seen this behavior?  Any thoughts on why this might be happening and how to fix it?

---

### Post by rookcifer on 2012-04-24
Are both these key-pairs associated with one another (i.e. is k2 a subkey of k1?)  If they are two completely distinct key-pairs, then k2 would not be able to decrypt data encrypted with k1.

---

### Post by Matt 6:27 on 2012-04-24
> **rookcifer said:**
> Are both these key-pairs associated with one another (i.e. is k2 a subkey of k1?)  If they are two completely distinct key-pairs, then k2 would not be able to decrypt data encrypted with k1.

Right, sounds impossible, but that is what I'm seeing... which is why I'm a little (a lot?) uneasy about this happening. They were created at two distinct times and do not share subkeys. The only "association" I can recall is I likely signed one with the other (& vice versa) back in the day.

Could there have been some cross-up when I imported them?  I did so by accessing the disk containing my private keys and right-clicking on the *.asc files and selecting "Open with Import Key".  This seemed to do the job of dropping them into My Personal Keys section of Seahorse.

Thanks for the follow-up.

---

### Post by donsy on 2012-04-24
> **Matt 6:27 said:**
> ...  I'm using seahorse-nautilus and not the command line. ...
What happens when you use the command line? If OK then the problem is with seahorse-nautilus and and I would stop using it.

---

### Post by Matt 6:27 on 2012-04-24
> **donsy said:**
> What happens when you use the command line? If OK then the problem is with seahorse-nautilus and and I would stop using it.

Ok, I tried the command line and it seems like it did the same thing.  I then went back to seahorse-nautilus and the only change I made was to reduce the time it retains a passphrase from the default 5 mins to 1 min (the minimum permitted).  After making that change, it appears to be working correctly using either the command line or seahorse-nautilus.  I'm still testing, but right now it seems like it's doing what it's supposed to do.  Crazy Train!

---

### Post by Matt 6:27 on 2012-04-25
This problem persists and can be duplicated easily.  I ran a series of tests to try to ID the source of the problem and it does appear to reside with seahorse-nautilus. My findings in a nutshell:  If you use multiple personal key pairs, you should encrypt with the comand line (CLI), but may decrypt using either CLI or seahorse-nautilus.

I've attached a copy of my notes and hope they are helpful to someone smarter than I am.

I am on my way to Launchpad to report same.

---

### Post by donsy on 2012-04-25
How much time are you allowing to elapse between tests? You  mentioned previously that you changed the time limit for passphrase caching  from 5 minutes to 1. Are you allowing a full minute to elapse between tests? If not try it and see if that makes a difference.

---

### Post by Matt 6:27 on 2012-04-25
> **donsy said:**
> How much time are you allowing to elapse between tests? You  mentioned previously that you changed the time limit for passphrase caching  from 5 minutes to 1. Are you allowing a full minute to elapse between tests? If not try it and see if that makes a difference.

Good question, but yes, I allowed the time to elapse before each new step.

---

### Post by slugg007 on 2012-04-25
> **Matt 6:27 said:**
> Ok, I tried the command line and it seems like it did the same thing.

Maybe it would be useful to show the exact commands you are using to encrypt and decrypt a file. Once you get the command line to work you could then look at using seahorse-nautilus.

Are you using K2's public key to encrypt K1's file?

---

### Post by Matt 6:27 on 2012-04-25
> **slugg007 said:**
> Maybe it would be useful to show the exact commands you are using to encrypt and decrypt a file. Once you get the command line to work you could then look at using seahorse-nautilus.

Are you using K2's public key to encrypt K1's file?

Check out the attachment in my earlier post, it includes the exact commands I used (including some screen shots).

Personally, I could easily use the command line going forward, but the people I support are terminal-phobic and want the convenience of a right-click to encrypt/decrypt.  I'm hoping for a fix short of telling them they shouldn't have more than one personal key pair.

---

### Post by slugg007 on 2012-04-25
> **Matt 6:27 said:**
> Check out the attachment in my earlier post, it includes the exact commands I used (including some screen shots).

Personally, I could easily use the command line going forward, but the people I support are terminal-phobic and want the convenience of a right-click to encrypt/decrypt.  I'm hoping for a fix short of telling them they shouldn't have more than one personal key pair.

Sorry. I personally do not like to open attachments off the web. You should be able to show your commands in a few lines.

I don't have trouble with your user community not wishing to use the command line. It just seems to me that until you get the CLI sorted out you will never get the GUI fixed.

Maybe I am getting involved in something over my head and won't really be able to help.

---

### Post by Matt 6:27 on 2012-04-25
> **slugg007 said:**
> Sorry. I personally do not like to open attachments off the web. You should be able to show your commands in a few lines.

I don't have trouble with your user community not wishing to use the command line. It just seems to me that until you get the CLI sorted out you will never get the GUI fixed.

Maybe I am getting involved in something over my head and won't really be able to help.

Don't apologize, I appreciate any input... and I understand the concern re attachments.  What's in there are two pages of notes I took testing different scenarios (e.g., encrypting with CLI, then decrypting with SN, vice versa and other combinations). I suppose I could paste all the notes into a post if that would be helpful to people interested in the issue.

I'm missing your point re "until you get the CLI sorted out".  I have no problems with the CLI at all; it works great.

---

### Post by ottosykora on 2012-04-26
@ Matt

do you mean that when there would be only one keypair in the ring, then even the seahorse would behave half way normally?


It looks that this new seahorse is even worse then it looks like.

---

### Post by slugg007 on 2012-04-26
> **Matt 6:27 said:**
> Don't apologize, I appreciate any input... and I understand the concern re attachments.  What's in there are two pages of notes I took testing different scenarios (e.g., encrypting with CLI, then decrypting with SN, vice versa and other combinations). I suppose I could paste all the notes into a post if that would be helpful to people interested in the issue.

I'm missing your point re "until you get the CLI sorted out".  I have no problems with the CLI at all; it works great.

OK - I understand better now. I was thinking that both the CLI & GUI encryption/ decryption were broken. And I was wondering whether the user's public or private keys got swapped around somehow. Since SN is the only broken application maybe SN is doing this for you. I have never used and can not help you with SN.

All I can do is ask questions which you have probably already pursued. Is there some type of SN config file that has gotten munged? If this is a very recent issue, can you retrieve important files from backups and see if things have changed? Does SN have some type of logging/verbose info that will help you? Can you just uninstall and reinstall the SN apps? As a last resort, can you set up a test environment and attempt to duplicate the problem?

I don't envy you at all. I am sure your users want an answer now, not next week sometime.

---

