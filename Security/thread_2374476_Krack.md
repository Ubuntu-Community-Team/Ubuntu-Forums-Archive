---
title: "Krack"
date: 2017-10-16
forum: Security
---

### Post by rpaco on 2017-10-16
I am not tech savvy in this but it sounds very bad indeed.  Can someone who is intimte with WPA2 and the versions used in current/recent Ubuntu variants please have a look and advise what we need to do. This is not about router passwords its far more fundamental and foole the 4 way exchange. Here is the write up by the guy who discovered it. I saw it on the BBC news pages today so it is not a tech secret any more. Now it is kown about no doubt some low-lifes will be using it.   Aricle here: [https://www.krackattacks.com/](https://www.krackattacks.com/)  Note posted as basic text not as a link.

---

### Post by devine.steve on 2017-10-16
My understanding is that we should: 
a) Avoid public WiFi and if we live in areas where physically attaching to our home networks is easy (apartment houses, condos. etc) then we should also be careful. If possible use a hard wired Ethernet cable to your router.
b) Be certain that you are using encrypted connections (HTTPS) for all traffic.  
c) Review passwords - I don't mean change them but confirm that you are not using the same password for your bank, credit card etc as you are using for your kids fundraising site. Remember that not all entities on the internet view security the same way. 

I myself would like to know this:
1) AN ETA on security patches.
2) Will these patches be announced on the announce list?
3) Is there a particular CVE that will be associated with the patches? 

And finally God's speed to all!

---

### Post by deadflowr on 2017-10-16
Patch it now:
[https://usn.ubuntu.com/usn/usn-3455-1/]("https://usn.ubuntu.com/usn/usn-3455-1/")

---

### Post by QIII on 2017-10-16
While the fix is in for Ubuntu (and presumably others), mobile Android devices and your home router may not yet be patched.  It might be advisable not to use WiFi with those until we learn more.

---

### Post by Geoff_Lane on 2017-10-17
> **QIII said:**
> While the fix is in for Ubuntu (and presumably others), mobile Android devices and your home router may not yet be patched.  It might be advisable not to use WiFi with those until we learn more.

Whilst security is an issue might this not be a bit paranoid? The attacker has to be within wifi range (blimey, I lose signal sometimes in my own home), and be waiting for you to connect and then be lucky enough to get something that is useful.

Whilst using an Android device on an Open WiFi might be an issue this may be being hyped - bit like the Russian threat.

Geffers

---

### Post by QIII on 2017-10-17
While your mobile device may not be able to detect a signal reduced by some function of the square of the distance between your device and the router/gateway and the ambiant RF background, a weak signal can be detected and amplified by appropriate equipment.  How do you suppose it has been done by WEP crackers in the past?

Do they have to happen to be listening at just the right moment?  Of course.  But that's already what they do.

It would be paranoic if you thought someone were going to specifically target you.  It is wise to protect yourself from random victimization -- just as taking precautions to thwart pickpockets while on vacation.

---

### Post by lah-ca on 2017-10-18
Hi,

Mr. Krebs is worth a read:  [https://krebsonsecurity.com/2017/10/what-you-should-know-about-the-krack-wifi-security-weakness/#more-41189](https://krebsonsecurity.com/2017/10/what-you-should-know-about-the-krack-wifi-security-weakness/#more-41189)

He tones down some of the hysteria which seems to be going around with WPA2 security problem without dismissing the seriousness of the issue.  Reading some of the comments at the bottom of the page is also worthwhile.

Cheers.

---

### Post by Geoff_Lane on 2017-10-18
> **QIII said:**
> While your mobile device may not be able to detect a signal reduced by some function of the square of the distance between your device and the router/gateway and the ambiant RF background, a weak signal can be detected and amplified by appropriate equipment.  How do you suppose it has been done by WEP crackers in the past?

Do they have to happen to be listening at just the right moment?  Of course.  But that's already what they do.

It would be paranoid if you thought someone were going to specifically target you.  It is wise to protect yourself from random victimization -- just as taking precautions to thwart pickpockets while on vacation.

Sensible precautions yes but as many people - and I'd include myself here - do not understand the incredible workings of computers and the internet many believe in threats that are less likely than being struck by lightening or being hit by meteorite debris. Yes I know we avoid standing under trees in thunder storms but who knows even an umbrella can be a conductor.

What does amaze me is, there are so many brilliant people in the World yet, this security flaw has gone unnoticed for 10 years and now many apparently understand it.

Geffers

---

### Post by yoshii on 2017-10-23
Thanks for posting up this info.  
This was a rather important issue.  
I'm glad if it got fixed already.  
I too read the BBC article about the vulnerability.  
It was frustrating because most of the article explained over and over again how to hack people instead of just explaining how to fix and prevent the hacking.

---

