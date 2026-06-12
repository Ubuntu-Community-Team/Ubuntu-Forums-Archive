---
title: "Iran May Have Acquired Google SSL Certificate, Prompts Browser Security Alerts"
date: 2011-08-30
forum: The Cafe
---

### Post by lovinglinux on 2011-08-30
[http://www.conceivablytech.com/9157/products/iran-may-have-acquired-google-ssl-certificates-prompts-browser-security-alerts](http://www.conceivablytech.com/9157/products/iran-may-have-acquired-google-ssl-certificates-prompts-browser-security-alerts)

> Chrome was reportedly able to detect the fraudulent certificate whey a recent security update in its browser and confirm the vulnerability. Google the informed Mozilla and Microsoft which both issued security updates for their products. Mozilla revoked the certificate, but said that the extent of the problem is not clear and has therefore published &#8220;new versions of Firefox for desktop (3.6.21, 6.0.1, 7, 8, and 9) and mobile (6.0.1, 7, 8, and 9), Thunderbird (3.1.13, and 6.0.1) and SeaMonkey (2.3.2) shortly that will revoke trust in the DigiNotar root and protect users from this attack.&#8221;

Users are urged to update their browsers.

[Deleting the DigiNotar CA certificate]("http://support.mozilla.com/en-US/kb/deleting-diginotar-ca-cert")

[http://blog.mozilla.com/security/2011/08/29/fraudulent-google-com-certificate/](http://blog.mozilla.com/security/2011/08/29/fraudulent-google-com-certificate/)

> 
**Issue**

Mozilla was informed today about the issuance of at least one fraudulent SSL certificate for public websites belonging to Google, Inc. This is not a Firefox-specific issue, and the certificate has now been revoked by its issuer, DigiNotar. This should protect most users.

**Impact to users**

Users on a compromised network could be directed to sites using a fraudulent certificate and mistake them for the legitimate sites. This could deceive them into revealing personal information such as usernames and passwords. It may also deceive users into downloading malware if they believe it&#8217;s coming from a trusted site. We have received reports of these certificates being used in the wild.

**Status**

Because the extent of the mis-issuance is not clear, we are releasing new versions of Firefox for desktop (3.6.21, 6.0.1, 7, 8, and 9) and mobile (6.0.1, 7, 8, and 9), Thunderbird (3.1.13, and 6.0.1) and SeaMonkey (2.3.2) shortly that will revoke trust in the DigiNotar root and protect users from this attack. We encourage all users to keep their software up-to-date by regularly applying security updates. Users can also manually disable the DigiNotar root through the Firefox preferences.
Credit

This issue was reported to us by Google, Inc.


[http://weblogs.mozillazine.org/gerv/archives/2011/08/diginotar_compromise_webmaster_notificat.html](http://weblogs.mozillazine.org/gerv/archives/2011/08/diginotar_compromise_webmaster_notificat.html)

> A Dutch CA called [DigiNotar]("http://diginotar.nl/") has suffered a security breach. Mozilla is [removing trust from their root certificate]("http://blog.mozilla.com/security/2011/08/29/fraudulent-google-com-certificate/") - we hope to release updates today. We have used the [EFF SSL Observatory]("https://www.eff.org/observatory") data to make a list of affected websites (those whose certificates chain up to the DigiNotar root[0]). We want to warn the webmasters of these sites that they need to get new certificates ASAP. And that's where we use the power of the community :-)

If you can read Dutch, we would appreciate your help. There is a [Google Docs spreadsheet]("https://docs.google.com/spreadsheet/ccc?pli=1&key=0AtLNtYDDyKsudG1lc2xmRDZRNTBkdXR1M0gzelZ3MkE&hl=en_GB#gid=0") with the list of affected sites and instructions on how to find the webmaster email or contact form and warn them, using a letter we have written. The more warning they get, the less disrupted the Dutch SSL internet will be. Please head over there and help out :-) Thanks!



---

### Post by elliotn on 2011-08-30
huh

---

### Post by Nyromith on 2011-08-30
Nice job defending the world against the cloud. :)

---

### Post by Dragonbite on 2011-08-30
A co-worker who went to Black Hat told us about this issue and when he saw this article he forwarded it to us.  Scary.

---

### Post by Thewhistlingwind on 2011-08-30
This update apparently hasn't been pushed out to fedora users yet.

I guess I should go file a bug report?

EDIT: Reread the OP, so this update isn't out yet?

---

### Post by Aquix on 2011-08-30
Someone mentioned this last night on irc. But I haven't heard about anyone tracing where the traffic goes through, ot who is behind it

And, yes. scary. we need ssl to be watertight. :(

---

### Post by Dragonbite on 2011-08-30
> **Aquix said:**
> And, yes. scary. we need ssl to be watertight. :(

It isn't.

There are some interesting methods of countering that which sounds interesting.

---

### Post by Bachstelze on 2011-08-30
> **Aquix said:**
> 
And, yes. scary. we need ssl to be watertight. :(

SSL is. It is the CA model that is deeply flawed and needs to be scraped altogether. The problem is coming up with a better one..

---

### Post by lovinglinux on 2011-08-31
[Deleting the DigiNotar CA certificate](http://support.mozilla.com/en-US/kb/deleting-diginotar-ca-cert)

---

### Post by tmette on 2011-08-31
I just got my update to Firefox 6.0.1 this morning, I assume it was because of this.

---

### Post by handy on 2011-08-31
I just did my morning system upgrade on Arch & went from Firefox 6.0-1 to 6.0.1-1 .

---

### Post by doorknob60 on 2011-09-01
That explains these then:
```

core/ca-certificates        20110502-1     -> 20110502+nmu1-1
extra/chromium              13.0.782.215-1 -> 13.0.782.218-1
extra/firefox               6.0-1          -> 6.0.1-1
extra/xulrunner             6.0-2          -> 6.0.1-1
```

Good old Arch, handling things nice and quickly:)

---

### Post by NightwishFan on 2011-09-01
I do not appear to have this certificate in Opera so I think I am safe. :)

Edit: Just actually got an update for it now from the deb repo. So I guess that would be why.


[http://www.debian.org/security/2011/dsa-2300](http://www.debian.org/security/2011/dsa-2300)
[http://www.debian.org/security/2011/dsa-2299](http://www.debian.org/security/2011/dsa-2299)

```
0 added, 1 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
  does not exist: /etc/ssl/certs/DigiNotar_Root_CA.pem
done.
```

---

### Post by lovinglinux on 2011-09-02
Updates on the issue:

[http://blog.mozilla.com/security/2011/09/02/diginotar-removal-follow-up/](http://blog.mozilla.com/security/2011/09/02/diginotar-removal-follow-up/)

---

### Post by sffvba[e0rt on 2011-09-03
Huge continues blunder by DigiNotar... wow...


404

---

### Post by Oxwivi on 2011-09-03
> **not found said:**
> Hugh

Who?

> **not found said:**
> Hugh continues blunder by DigiNotar... wow...
I think the edit tag on the last post with this quote is self-explanatory.

---

### Post by sffvba[e0rt on 2011-09-03
> **Oxwivi said:**
> Who?

What?

---

### Post by Oxwivi on 2011-09-03
If you can edit, so can I...

---

### Post by sffvba[e0rt on 2011-09-03
> **Oxwivi said:**
> If you can _***ninja***_, so can I...

[IMG]http://www.overclock.net/images/smilies/wheee.gif[/IMG]

On topic: ...I actually have nothing to add right now... Carry on...

---

### Post by NightwishFan on 2011-09-03
> **not found said:**
> What?

Nice! :lolflag:

---

### Post by lovinglinux on 2011-09-05
**Update:**

[URL="http://www.conceivablytech.com/9239/business/mozilla-sharply-attacks-diginotar-over-now-531-hacked-certificates"]
Mozilla Developer Attacks DigiNotar Over Now 531 Hacked Certificates, including Mozilla, LogMeIn, WordPress, Facebook, Twitter, Skype, CIA, Google, The UK Secret Intelligence Service, Verisign, Israel’s Mossad, and Live.com.[/URL]

---

### Post by Bachstelze on 2011-09-05
Attacking DigiNotar amounts to attacking the cashier at the store when your product is too expensive. It is the system that needs to be scraped, there's nothing DigiNotar can do about it.

---

### Post by lovinglinux on 2011-09-05
> **Bachstelze said:**
> Attacking DigiNotar amounts to attacking the cashier at the store when your product is too expensive. It is the system that needs to be scraped, there's nothing DigiNotar can do about it.

Except that they did not disclosure the breach when discovered.

---

### Post by Bachstelze on 2011-09-05
That's an epiphenomenon. What if they had disclosed it? That wouldn't have changed the fact that it occurred and affected websites that were in no way associated with DigiNotar. That's the real problem, and it is much depeer. The rest is just buzztalk.

---

### Post by Paddy Landau on 2011-09-06
> **Bachstelze said:**
> Attacking DigiNotar amounts to attacking the cashier at the store when your product is too expensive. It is the system that needs to be scraped, there's nothing DigiNotar can do about it.> **Bachstelze said:**
> That's an epiphenomenon. What if they had disclosed it? That wouldn't have changed the fact that it occurred and affected websites that were in no way associated with DigiNotar. That's the real problem, and it is much depeer. The rest is just buzztalk.

I agree that DigiNotar was not to blame for the illegal actions of others.  However, as a CA in a position of responsibility, its behaviour in  failing to immediately notify relevant parties was disgraceful.

I think your metaphor of a cashier in this case is not quite appropriate. Here's a better metaphor:

Imagine a food manufacturer whose food has been poisoned by the illegal  actions of someone else (this has happened in the past). Would you find  it acceptable if the food manufacturer failed to notify anyone until after the police had investigated the deaths of several people, just because it wasn't the food manufacturer's  fault?

---

### Post by Syndicalist on 2011-09-06
Good thing I dont like Chromium.

Firefox used to suck, but now its fast 'enough' and with better features. Since 4.0 its been close enough that I dont even notice the difference on my machine

---

### Post by Dragonbite on 2011-09-06
I don't know... being "hacked" is too easy of an excuse in case they knowingly and willingly sold it to the highest "bidder".

---

### Post by Paddy Landau on 2011-09-06
> **Syndicalist said:**
> Good thing I dont like Chromium.
What does Chromium have to do with it? The certificate was faked, which means every browser was affected.

---

### Post by lovinglinux on 2011-09-07
New developments!!!!!

[http://www.conceivablytech.com/9256/products/comodohacker-claims-responsibility-for-diginotar-hack](http://www.conceivablytech.com/9256/products/comodohacker-claims-responsibility-for-diginotar-hack)

It is more serious than expected. Other 4 Certificate Authorities have been compromised as well, not only DigiNotar.

Here are some parts of the article:

> 
Security researchers from F-Secure were first to notice ComodoHacker’s updated Pastebin page, which delivers some clues about the DigiNotar hack. ComodoHacker, who created fake certificates back in March, also with an origin that pointed to Iran, said that not an “Army” in Iran, but he as a 21-year old individual penetrated DigNotar 5-6 layers deep and “owned” their entire computer network. He published DigiNotar’s administrator password as evidence that he breached the company’s network. DigiNotar has not replied to our request to either confirm or deny ComodoHacker’s claims.

ComodoHacker says that he has also access to four more Certficate Authorities (CAs) and he is able to issue certificates as he desires. He also claims that he can send out Windows Update messages in Microsoft’s name. To proof his point, he is offering Microsoft’s Windows Calculator for download that is signed with a Google Certificate.

There appears to be still a political motivation behind the hack, as the hacker says that the attack is directed at the Dutch government in retaliation for the July 1995 events in Srebrenica, Bosnia. Back then, 110 Dutch peacekeeping troops were stationed to protect the Muslim population of the town, but were overrun by Serbs who committed what is now know as the Srebrenica massacre or genocide, in which between more than 8000 people have been slaughtered. The Dutch Peacekeepers reportedly were lightly armored and accepted rapes and killings that took place close by. Following a report on the events in Srebrenica, the Dutch government accepted partial responsibility for the massacre and the cabinet resigned 2002.

---

