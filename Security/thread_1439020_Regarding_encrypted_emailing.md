---
title: "Regarding encrypted emailing"
date: 2010-03-25
forum: Security
---

### Post by oingk on 2010-03-25
Hi

Don't know if it's the right place to ask this.

I am interested in encrypted emailing but don't know how to set this up yet. 

Two things I have gathered is that I can either use Evolution, or use Thunderbird+Enigmail. 
 
 I want to ask:
 
 [COLOR=Red]1[/COLOR]] Are these easy to set up? Which one is easier?
 
 [COLOR=Red]2[/COLOR]] In order to send/recieve encrypted emails, what email service provider should I use (e.g. can I use Gmail or Yahoo mail or Hotmail, etc). If I use an email service provider such as Gmail, could Google still be able to read my encrypted emails when they are passed through them?
 
 [COLOR=Red]3[/COLOR]] In order to send/recieve encrypted emails, should the person I'm talking to also have email encryption? If yes, should it be the same system as mine (for example should we both use Evolution)?

---

### Post by bodhi.zazen on 2010-03-25
Most people use gpg. It is moderately easy to set up.

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

[http://aplawrence.com/Basics/gpg.html](http://aplawrence.com/Basics/gpg.html)

[http://blog.objectmentor.com/articles/2007/08/23/secure-email-with-gnupg](http://blog.objectmentor.com/articles/2007/08/23/secure-email-with-gnupg)

[http://www.geeksaresexy.net/2008/04/16/keep-your-correspondence-private/](http://www.geeksaresexy.net/2008/04/16/keep-your-correspondence-private/)

On that last link, read the article, not the pictures, lol

---

### Post by oingk on 2010-03-25
Thanks quite a lot, I will read these.

---

### Post by rookcifer on 2010-03-25
> **oingk said:**
>  
 [COLOR=Red]2[/COLOR]] In order to send/recieve encrypted emails, what email service provider should I use (e.g. can I use Gmail or Yahoo mail or Hotmail, etc). If I use an email service provider such as Gmail, could Google still be able to read my encrypted emails when they are passed through them?

No, if you encrypt the e-mail, the only person that can read the e-mail is the recipient.  Google or Yahoo or any other provider will not be able to read it.
 
 > [COLOR=Red]3[/COLOR]] In order to send/recieve encrypted emails, should the person I'm talking to also have email encryption? If yes, should it be the same system as mine (for example should we both use Evolution)?

Yes the contact needs email encryption.  However, it doesn't matter what e-mail client they use.  All they need is to be using PGP/GPG.

---

### Post by undergrowth on 2011-09-20
If I have two public keys for one email address in my keyring, is there a way to choose which key gets used to encrypt any given message?  The only way I have found so far has been to go into Seahorse and delete the unwanted (for the moment) key, but that's a nuisance for a number of different reasons. Otherwise Evolution or Seahorse -I'm not sure which- will select a key to use, apparently at random.

---

### Post by spynappels on 2011-09-22
I don't have it set up at the moment, but from Thunderbird + Enigmail, I think you can choose which key to use. I know you can in Outlook if you use Kleopatra, I know that's Windows but useful to know none-the-less.

---

### Post by undergrowth on 2011-09-22
Thank you, spynapples! It's weird that there don't seem to be any posts about this topic. I hardly use PGP at all, and already have multiple keys for three different correspondents of mine. Not being able to choose which key I encrypt to them with is a real problem, but maybe I just haven't yet thought of the right words to search for to find related posts. If anyone has any ideas or links, please let me know.

---

