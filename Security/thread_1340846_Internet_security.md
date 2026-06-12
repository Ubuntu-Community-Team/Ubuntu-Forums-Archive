---
title: "Internet security"
date: 2009-11-29
forum: Security
---

### Post by judge jankum on 2009-11-29
A few days ago...On a machine running XP with KasperSky Internet Security we click into a web page, the page goes blank, KasperSky goes crazy...Next we get a charge on a credit card from "Frndfnder" So some way our info was stolen even with KasperSky... Is this just a Windows thing? Is this possible with Ubuntu/Linux?

---

### Post by BenAshton24 on 2009-11-29
It will be windows only. I presume you were using IE? do you have a link to the website? I wanna check it out, ya know, just for kicks :P

---

### Post by lisati on 2009-11-29
Interesting. Google gave me only one result for Frndfnder

[http://800notes.com/Phone.aspx/1-702-434-0599](http://800notes.com/Phone.aspx/1-702-434-0599)

---

### Post by judge jankum on 2009-11-29
Windows Xp with Firefox 1.0.15 and KasperSky internet security... We think it was maybe an e-mail from Myspace in our Yahoo e-mail.

---

### Post by judge jankum on 2009-11-29
Firefox 3.0.15 oops

---

### Post by judge jankum on 2009-11-29
frndfndr228 8885758383 888-5758383 CA  This is the charge we got...

---

### Post by BenAshton24 on 2009-11-29
> **judge jankum said:**
> Firefox 3.0.15 oops

Realy? In Firefox? Did you download and run an exe or did it just happen all of a sudden? I presume the latter based on how you phrased it, and if so that is the first case of malware getting pased firefox without user error that i've ever seen :P Could it have been an awful coincidence and at the same time someone was hacking your box?

---

### Post by judge jankum on 2009-11-29
Afterward KasperSky told us Firefox had been compromised and was a vulnerability...We un-installed it and got another version...

---

### Post by OpSecShellshock on 2009-11-29
Well, the charge on your statement was from a real company. Between the time of the odd Kaspersky/firefox activity and the time you received the credit card statement, had you purchased anything online using your credit card? Had you logged into a PayPal account or anything similar?

Sounds like the activity of a password/account/data-stealing trojan. I suspect that what happened is that this trojan started running every time you browsed the web with firefox, just waiting for you to put in some credit card or banking information, then sending that information off to a machine run by a criminal. Usually they sell that information in bulk to other criminals, who then make fake cards or just make purchases. Someone then set up a profile on FriendFinder using your credit card. You'll need to dispute that charge right away, cancel that card and get a new one. From what I've seen regarding FriendFinder, it's an automatic monthly billing setup, meaning you'll see recurring charges until you deal with it.

Just to be safe, I'd reload the OS on the Windows machine. Do not use a system restore point. Do not back up any files that you don't absolutely need.

---

### Post by Beverly Roberts on 2009-11-29
I would use a Ubuntu LiveCD to surf the web, just be to safe. Everytime you reboot, all viruses are wiped out.  

Beverly Roberts

---

### Post by django1fete on 2009-11-29
...not sure if Im in the right room, am new to all of this Ubuntu, the forum and this blg..but Ive been having issues getting my Nvidia driver going...Im using the Nvidia 180 on Ubuntu 9.04v, none of the suggestions worked for me..now Ive found that my firefox Firewall is disabled and Im getting things running all the time resulting in a much slower machine, here lately ive noticed this "phantom" window labeled 'FCTB XMLlayer' going and it doesnt open to anything...Im guessing i got nailed with a virus or someones pimping my machine...does anybody know anything about this? 
Can you help a brother out?:)

---

### Post by judge jankum on 2009-11-29
Thanks for all the input on this!!!! I havn't heard of Ubuntu being hit with anything, but i wonder if Firefox could be hit in Ubuntu same as in Windows? Anyone know?

---

### Post by cariboo on 2009-11-29
> **django1fete said:**
> ...not sure if Im in the right room, am new to all of this Ubuntu, the forum and this blg..but Ive been having issues getting my Nvidia driver going...Im using the Nvidia 180 on Ubuntu 9.04v, none of the suggestions worked for me..now Ive found that my firefox Firewall is disabled and Im getting things running all the time resulting in a much slower machine, here lately ive noticed this "phantom" window labeled 'FCTB XMLlayer' going and it doesnt open to anything...Im guessing i got nailed with a virus or someones pimping my machine...does anybody know anything about this? 
Can you help a brother out?:)

So what is the problem? Is it a graphics issue, or something else you've done? Please explain. 

The majority of viruses out there are Windows only, so that isn't a problem.

I would suggest you start a new thread explaining exactly what the problem is, without bringing in a lot of other issues.

---

### Post by Velnias on 2009-11-30
> **judge jankum said:**
> Thanks for all the input on this!!!! I havn't heard of Ubuntu being hit with anything, but i wonder if Firefox could be hit in Ubuntu same as in Windows? Anyone know?

Firefox on all OS'es shares the same vulnerabilities. However, malware (Firefox vulnerabilities are only gate for malware) is OS dependent, so Windows malware will not run under Linux. So far, security by obscurity still works great on Linux.

---

### Post by EJeanmaire on 2009-11-30
> **judge jankum said:**
> A few days ago...On a machine running XP with KasperSky Internet Security we click into a web page, the page goes blank, KasperSky goes crazy...Next we get a charge on a credit card from "Frndfnder" So some way our info was stolen even with KasperSky... Is this just a Windows thing? Is this possible with Ubuntu/Linux?

Is that the only charge on the credit card?  Perhaps someone in your household was getting a bit lonely and looking for a friend?

The event you described does not explain how they obtained your credit card number.  If your card really was stolen then the scenario would be something more like this.  You received an email with a bogus link to a website you might frequent at, where you then typed in your credit card information.  Fake paypal, ebay, bank sites are very common.

---

### Post by lisati on 2009-11-30
> **EJeanmaire said:**
> Is that the only charge on the credit card?  Perhaps someone in your household was getting a bit lonely and looking for a friend?

The event you described does not explain how they obtained your credit card number.  If your card really was stolen then the scenario would be something more like this.  You received an email with a bogus link to a website you might frequent at, where you then typed in your credit card information.  Fake paypal, ebay, bank sites are very common.

+1.

I had one from "Paypal" the other day hinting that the security of my account was compromised. Very nice copy of the real Paypal login screen, but the the effect was spoiled by the unprofessional appearance of the email.

Things to look for in the emails you receive include the bogus links. The text in the email might appear to be a genuine link, but when your browser opens, the address is different to what you'd normally use to access the real site. Another thing to watch for is the real organization's policy on asking for personal details by email or phone. And legitimate companies don't normally require the security number on your credit card to make refunds.

I got lucky with the first phishing email I received and was alerted to the potential for problems by three things: (a) I'd closed the account I'd had with the bank in question some time earlier (b) the email was from the wrong country (.com.au instead of .co.nz) and (c) I'd never used internet banking with that bank.

---

