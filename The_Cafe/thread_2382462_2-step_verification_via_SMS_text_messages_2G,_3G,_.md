---
title: "2-step verification via SMS text messages: 2G, 3G, ... SS7"
date: 2018-01-13
forum: The Cafe
---

### Post by haplorrhine on 2018-01-13
Existing are plenty of online articles on the subject of insecure telecommunications.  This includes insecure *2-step* verification, so called "two-factor authentication" that authenticates via SMS text messages, and other topics like low-budget IMSI catchers (stingrays) and the gaping hole in SS7.  Also existing are good summaries of the history of telecommunications protocols/standards from the 1G analog to 2G digital to 3G packet-switching to 4G jargon like "orthogonal frequency division..." and "higher-order 'quadrature amplitude modulation'."  These articles were my favorites.

HowStuffWorks: How Cell Phones Work
[https://electronics.howstuffworks.com/cell-phone.htm](https://electronics.howstuffworks.com/cell-phone.htm)

BREAKING GSM WITH A $15 PHONE... PLUS SMARTS (Jon Borland, 2010)
[https://www.wired.com/2010/12/breaking-gsm-with-a-15-phone-plus-smarts/](https://www.wired.com/2010/12/breaking-gsm-with-a-15-phone-plus-smarts/)

HACKERS SPOOF CELL PHONE TOWER TO INTERCEPT CALLS (Kim Zetter, 2010)
[https://www.wired.com/2010/07/intercepting-cell-phone-calls/](https://www.wired.com/2010/07/intercepting-cell-phone-calls/)

SO HEY YOU SHOULD STOP USING TEXTS FOR TWO-FACTOR AUTHENTICATION (Andy Greenberg, 2016)
[https://www.wired.com/2016/06/hey-stop-using-texts-two-factor-authentication/](https://www.wired.com/2016/06/hey-stop-using-texts-two-factor-authentication/)

THE CRITICAL HOLE AT THE HEART OF OUR CELL PHONE NETWORKS (Kim Zetter, 2016)
[https://www.wired.com/2016/04/the-critical-hole-at-the-heart-of-cell-phone-infrastructure/](https://www.wired.com/2016/04/the-critical-hole-at-the-heart-of-cell-phone-infrastructure/)

Alternatives are many, including Authy, U2F security keys, and various Yubikeys, and yet I hope to hold onto my SMS-only Yahoo email address.  The subject of SS7 is still over my head, but the articles from 2010 importantly reveal two things about GSM transmissions: they can be decrypted, eavesdropped, and imitated; the imitation transmissions are used to match the physical device to its network ID number; and, with a few thousands of dollars, a fake cell tower is possible.

However, these weaknesses were in GSM, a 2G standard.  With 3G underway, recent devices typically use UMTS, which uses W-CDMA and is based on GSM, or CDMA2000, which was designed for backward compatibility with CDMAOne (IS-95).  Indeed, my cheap LG Cosmos supports CDMA2000.  However, smoothing the transition into 3G (IMT-2000), CDMA2000 and CDMAOne can operate on the same frequency, and CDMA2000 is backward compatible.  Vulnerabilities must be known, but I only found a pair of pay-gated IEEE publications on the similar vulnerabilities of CDMA2000 and UMTS.

I worry that my investigation into cellular vulnerabilities is reaching a dead-end before any practical advice, and SS7 remains even more opaque.  I am ready to learn whatever I can from the ubuntuforums community.

---

### Post by mastablasta on 2018-01-15
there is nothing that is 100% safe. it's just how long would it take to break the lock.

i think more important sites should use key +password and maybe if necessary SMS as well. so the hacker would need to get all 3 compromised. 

also security always clashes with usability.

---

### Post by haplorrhine on 2018-01-24
> **mastablasta said:**
> there is nothing that is 100% safe. it's just how long would it take to break the lock.

Your statement is somewhat vague.  Knowing that someone could feasibly pick your lock (replay attack, MitM) differs from knowing the alternatives like following you inside (session hijacking) or obtaining a duplicate key from the landlord (corrupt access, apparently one problem with SS7).

---

### Post by mastablasta on 2018-01-25
it was just an example. point is there is nothing 100% safe. you have stories about high tech security being beaten by simple phone call where a worker provided the password.

you mentioned yahoo mail. it was hacked a couple of times already. last time they didn't even tell the people they got hacked. not sure it is a secure choice at all.

---

### Post by PaulW2U on 2018-01-27
> **haplorrhine said:**
> Existing are plenty of online articles on the subject of insecure telecommunications.
TLDR as they say but I get your point  :)
> **mastablasta said:**
> also security always clashes with usability.
Very true.
> **mastablasta said:**
> it was just an example. point is there is nothing 100% safe.
Every time I have to go through a security procedure whether on the web, on the phone or by email i wonder how effective security procedures really are. If someone has access to your data, email account or mobile phone then any security checks may prove successful from the view of whoever is requesting verification but you still may be not who you say you are.

If i should find an unsecured mobile phone then I could have access to any number of services that require a minimal input to a request for additional authorisation that will prove or disprove who I am or not? Isn't it all down to the probability of me being who I say I am taking all of the various factors into consideration? Or am I missing the point of the original post?

---

### Post by mastablasta on 2018-01-29
> **PaulW2U said:**
> 
Every time I have to go through a security procedure whether on the web, on the phone or by email i wonder how effective security procedures really are. If someone has access to your data, email account or mobile phone then any security checks may prove successful from the view of whoever is requesting verification but you still may be not who you say you are.


the idea is to make it more difficult for someone to pretend to be you.

password can be cracked. but 2 factor meas you need password and a way to receive a message sent to the mobile phone number the person entered. 

so if you crack the password or guess it (e.g. based on passwords stole on other websites) you still can't get it without having the mobile phone from the user. i am sure there is a way around that, it is just no that simple.

the question is if all sites require this kind of security. if not which ones then?

for example paying with my credit card involves password, passphrase, one time code (2 factor auth.) and then after the payment is done a notification. for larger sums i would even receive a phone call with short interrogation before payment is approved. all this could probably be bypassed, but it would not be easy.

but then i don't think that for example Ubuntuforums would need all this trouble for me to just write a post.

---

### Post by haplorrhine on 2018-01-31
> **PaulW2U said:**
> TLDR as they say but I get your point  :)

If i should find an unsecured mobile phone then I could have access to any number of services that require a minimal input to a request for additional authorisation that will prove or disprove who I am or not? Isn't it all down to the probability of me being who I say I am taking all of the various factors into consideration? Or am I missing the point of the original post?

The problem is that cell phones don't provide true 2FA anymore.  2FA implies that you must have the token in your possession, but, to repeat paragraph two, cellular transmissions, which are mobile transmission via cell towers, can be intercepted, decrypted, and even replicated relatively easily.  Paragraph three: this is part of why cell service providers are constantly developing new protocols, which are categorized as 2,3,4G but are actually more various.  These issues aren't being fixed quickly, and it seems that they're under-discussed.

---

