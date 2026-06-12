---
title: "WEP Cracking / Security Testing"
date: 2011-08-12
forum: Security
---

### Post by rthwm on 2011-08-12
Hopefully i'm posting this in the right area. I've been doing some research over the last few weeks involving network and wireless security. Its pretty obvious to me now that "wireless security" is pretty much a joke as it seems almost everything out there can be broken in to one way or another. With this, I am still trying to find ways to secure my home wireless network and my companys wifi network.
 
From what I have been able to gather so far, there are different programs that can be used to break WEP or even WAP encryption. I started messing around with a couple of the guides on the web to see if I could infact break in to my own wireless router.
 
With this, there is a step involved that has to do with patching my wifi driver. Using aircrack-ng (and trying to follow the directions on their site), I am stuck on this whole patching process. I was able to determin that (pretty sure) I have a compatible wifi card (ath5k), but as for the process of actually doing the patch, the directions (following step by step) dont appear to be working.
 
Would anyone thats done wep cracking recently be able to provide me with a step by step process on the patching process of the wifi drivers?
 
Currently I running aircrack-ng and have the mdk3, crunch, and pyrit items installed and appear to be working. The WepCrackGui is reporting an error that it could not retrieve channel of monitor interface and that its because I have to patch my drivers.

---

### Post by haqking on 2011-08-12
I'm afraid that is not supported here.

There are plenty of resources available online however.

Good luck

---

### Post by Dangertux on 2011-08-12
> **rthwm said:**
> Hopefully i'm posting this in the right area. I've been doing some research over the last few weeks involving network and wireless security. Its pretty obvious to me now that "wireless security" is pretty much a joke as it seems almost everything out there can be broken in to one way or another. With this, I am still trying to find ways to secure my home wireless network and my companys wifi network.
 
From what I have been able to gather so far, there are different programs that can be used to break WEP or even WAP encryption. I started messing around with a couple of the guides on the web to see if I could infact break in to my own wireless router.
 
With this, there is a step involved that has to do with patching my wifi driver. Using aircrack-ng (and trying to follow the directions on their site), I am stuck on this whole patching process. I was able to determin that (pretty sure) I have a compatible wifi card (ath5k), but as for the process of actually doing the patch, the directions (following step by step) dont appear to be working.
 
Would anyone thats done wep cracking recently be able to provide me with a step by step process on the patching process of the wifi drivers?
 
Currently I running aircrack-ng and have the mdk3, crunch, and pyrit items installed and appear to be working. The WepCrackGui is reporting an error that it could not retrieve channel of monitor interface and that its because I have to patch my drivers.

The madwifi drivers are set up for injection. You could use those (in fact if you're using the ath5k or ath9k driver I recommend it anyway they are a bit more stable IMO)

As far as securing your wireless network WPA is reasonably secure so long as you pick a strong passphrase 64 characters, etc. Google creating strong WPA passphrases. It is considerably stronger than WEP which is an outright joke. The strength in WPA/2 lies in the fact that you can't perform a statistical attack against it. (Although some argue it can be done no proof of concept has been supplied). WEP can be cracked in under 2 minutes. With a strong passphrase it is unlikely that an attacker will be able to crack WPA/2 within a reasonable amount of time before the passphrase is changed.

---

### Post by stefangr1 on 2011-08-12
I wouldn't say that "wireless security" is pretty much a joke. Only WEP is. At this moment, WPA is still pretty much unbreachable, and it will most likely be for quite some time. The only thing you need to secure your network is a strong WPA key. Except for an issue with WPA Enterprise where people who already had access could listen to the traffic of others, but apart from that the basics of WPA and AES encryption have not been breached yet.

Using aircrack-ng for testing network security is therefore useless. Testing unsecured or WEP makes no sense (why would you ever want to use it), testing WPA is as difficult as the key you define. If it's a word on your wordlist, or a key wit less than five characters it's easy, if it's a 16 character key you would need to "test" your network for several trillions of years.

---

### Post by haqking on 2011-08-12
> **stefangr1 said:**
> I wouldn't say that "wireless security" is pretty much a joke. Only WEP is. At this moment, WPA is still pretty much unbreachable, and it will most likely be for quite some time. The only thing you need to secure your network is a strong WPA key. Except for an issue with WPA Enterprise where people who already had access could listen to the traffic of others, but apart from that the basics of WPA and AES encryption have not been breached yet.


Edit: re-read your post, changed my response ;-)

However the WPA is still pretty much unbreachable gives a false sense of security to people reading this.  if it is a weak passphrase then can br cracked very quickly if you catch the handshake

---

### Post by stefangr1 on 2011-08-12
> **haqking said:**
> ? mmmm

the basics not been breached yet ?

its easier to crack WPA with a weak password than it is WEP.

I would say that's due to having a weak password, not due to the basics of WPA.

The OP asks about wireless security, stating that he fears all wireless is insecure and wants to start testing. To my impression plain and simple WPA with a long enough key is pretty much impossible to breach from the outside.

---

### Post by haqking on 2011-08-12
I think we are both saying the same thing in different ways.

Semantics and context issues ;-)

peace

---

### Post by cariboo on 2011-08-12
As long as this stays a general discussion, and not wpa cracking howto, I'll leave this thread open.

---

### Post by FuturePilot on 2011-08-13
> **stefangr1 said:**
> I would say that's due to having a weak password, not due to the basics of WPA.

The OP asks about wireless security, stating that he fears all wireless is insecure and wants to start testing. To my impression plain and simple WPA with a long enough key is pretty much impossible to breach from the outside.

WPA is crackable if you use TKIP. Only use AES and you'll be fine.

---

### Post by rthwm on 2011-08-13
Ok I appreciate all the feedback. With this insight, i've gone ahead and changed my key to something deemed more secured. This pretty much answered my main questions which was the whole reason for wanting to test my security in the first place.
 
Thanks guys, I appreciate it.

---

### Post by steve11911 on 2011-08-13
A quick search at the excellent resource site slashdot produces EGAD !

[http://slashdot.org/index2.pl?fhfilter=wpa](http://slashdot.org/index2.pl?fhfilter=wpa)

Google searches about securing wireless produce lots of unsatisfying results.Probably can't hack my wireless network though...(don;t have one)...

---

