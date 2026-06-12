---
title: "Does My Doctor Comply HIPAA when she Sends me Personal Health Information over Gmail?"
date: 2012-10-08
forum: The Cafe
---

### Post by Paper Pusher on 2012-10-08
By default Gmail encrypts all of its communication with SHTTP. That was done to keep the Chinese government from spying on Chinese dissidents who used Gmail. Is that same process sufficient to allow my doctor to send me personal health information? 

I have a Gmail account and I use the web interface through Gmail. I can also use Thunderbird as a Gmail client. Do I have to use Thunderbird to comply with HIPAA?

---

### Post by audiomick on 2012-10-08
Although I am not familiar with these matters, I would expect that anything that is supposed to be good enough to keep out the Chinese government would probably be pretty secure. Anyway, you could start by looking at these two Wikipedia pages and perhaps following the links to the cited references.

[http://en.wikipedia.org/wiki/Hipaa]("http://en.wikipedia.org/wiki/Hipaa")

[http://en.wikipedia.org/wiki/Shttp]("http://en.wikipedia.org/wiki/Shttp")

On top of that, if your doctor suggested the method, you could simply ask the doctor if he or she has adequately researched the subject. If you are concerned about HIPPA then I assume you are in the USA. I can't imagine a doctor in the USA leaving himself open to being sued.

---

### Post by DuckHook on 2012-10-08
This is an urban myth. SHTTP was not implemented because of concerns over the Chinese govt. Google is far more concerned with compromised financial transactions, nosy neighbours, etc than they are with foreign governments. Nonetheless, some standard rules of use must be repeated here.

*ALL* e-mail must be treated as publicly viewable. Without exception. They reside on public servers, are backed up every night by your ISP and are routed through god knows how many routers and servers before they ever land on your computer. From the sound of it, neither your doctor nor you are using anything like gpg encryption on the stuff you intend to send each other, so your e-mail is viewable by any geek who can scan last night's ISP backup.

The fact is that e-mail today is largely "secure" only because the sheer volume of it imposes a sort of security through anonymity. Any dedicated hacker can intercept your e-mail with little effort using ready-made tools that are so common, they can be downloaded by torrent. If you wish to practice even minimally robust security, your doctor and you must install the gpg module on your e-mail client, then actually commit to encrypting it. Otherwise, sensitive private documents are best left to traditional mail of the pony express kind.

---

### Post by audiomick on 2012-10-08
Fair comment.

---

### Post by TheFu on 2012-10-08
Never heard of SHTTP, perhaps you mean HTTPS?  That only applies to web users. IMAP and SMTP users need to be certain they force IMAPS(993) and SMTPS (often 465) ports and protocols. I don't know the gmail specific ports since using gmail and wanting anything to be "personal" is an oxymoron.

I don't know what the strict rules are for HIPPA, but email unless they use x.509 or GPG certs are not encrypted, so they do not meet with any real security at all. Google (and any intermediary system/network) can look inside the message and read everything.  email is like a postcard.  Anyone that the postcard passes through can look at the contents.

gmail uses SMTP, SMPTS, IMAP, IMAPS, HTTPS and POP3, POP3S.  None of these have anything to do with how the files are stored on gmail's servers ... unencrypted.  Half of those are for server-to-server communications and half are for client-to-server communications.  Most servers do not demand that the other server only use SSL/TLS encrypted sessions, so there is no way to ensure that the Doctor's email system forced gmail to use encryption for the transport of the email.

Of course, you probably signed something that agreed to them using email to notify you of test results.

If you want strong encryption, look at 
* **gpg** (you need an OpenPG cert)
* **thunderbird**
* **enigmail** (plugin/extension for thunderbird)

Other email programs will do openpg like **Claws**.
The best how-to guide is at the **enigmail **site.

When you create a gpg-key for signing and encrypting email, you probably want to make it for 5 or 10 years and 2K in size.

Of course, if you do all this, then the doctor also needs to do it. There is no 1-way encryption method possible for OpenPG email encryption. Both parties need keys and OpenPG software to properly make this work. I've never seen any Doctors, CPAs, or other "professionals" able to deal with GPG encrypted emails. They do not have the time.

Encrypted email has some downsides.
* it is encrypted, so there is no way to search inside the messages.
* it is encrypted, so if you lost your private key, there is no known way to decrypt messages encrypted with your public key.
* The receiver must also have a private and public key setup. You must know their public key to encrypt messages that only they can receive.

---

### Post by oldos2er on 2012-10-08
Moved to Community Cafe.

---

### Post by critin on 2012-10-08
> **Paper Pusher said:**
> By default Gmail encrypts all of its communication with SHTTP. That was done to keep the Chinese government from spying on Chinese dissidents who used Gmail. Is that same process sufficient to allow my doctor to send me personal health information? 

I have a Gmail account and I use the web interface through Gmail. I can also use Thunderbird as a Gmail client. Do I have to use Thunderbird to comply with HIPAA?

If the Chinese government wanted to spy on its citizens, and they do in certain situations, you can bet that Google will not lock them out.  I believe they have to contract with the government to even be there, and google wants to be there.

There may be programs that claim to keep the government out, but it isn't gmail.   No one can keep them out if they want to come in.   
> 
 Do I have to use Thunderbird to comply with HIPAA?I  don't think it's you that has to comply, it's the health care providers.

You might find your answer here.

[http://www.hhs.gov/ocr/privacy/hipaa/administrative/privacyrule/index.html](http://www.hhs.gov/ocr/privacy/hipaa/administrative/privacyrule/index.html)

---

### Post by Information Technology on 2012-10-08
> **Paper Pusher said:**
> Thunderbird as a Gmail client. Do I have to use Thunderbird to comply with HIPAA?

No one tool solves this problem.  And, using Gmail is probably no worse than using any other email technology.  It must be secured.  However, you have other issues with Gmail public accounts, which is the user agreement put in place by Google.  I recommend reading and understanding it.

I hope this helps.

---

### Post by Paper Pusher on 2012-10-08
Thank you very much for all the new comments.

Yes, Google uses HTTPS.  My mistake.  That's why I posted this initially to complete the forum.  Here is a useful link on HIPPA and G-mail.

[http://luxsci.com/blog/gmail-not-hipaa-compliant-email.html](http://luxsci.com/blog/gmail-not-hipaa-compliant-email.html)

This link indicates that G-mail is okay for patients to use to receive personal medical information but it's not okay for providers to use.  There are some business processes required that G-mail does not support.

---

### Post by oregonbob on 2012-10-09
I have been following the issue of HIPAA and Gmail for around a year because I am a consultant and I would like to introduce GMail to some of my clients in the health care industry.

Is GMail HIPAA compliant? The real answer is only "maybe". We won't know for sure until there is a lawsuit and precedent is set. Personally I think GMail is as secure as any other cloud email service, but there are many experts who disagree.

As for "HTTPS" encryption: that only applies to information in transit. It does not encrypt email once it reaches the destination. HIPPA may require encryption at all times.

Businesses that sell email service specialized for health care have declared it is not HIPAA compliant. Other experts who do not have an dog in the fight claim that it does meet HIPPA requirements.

We simnply won't know until there is a precedent-setting court case.

**Shame on the massive Google** for not using its clout to settle this matter, but it appears they have cowardly backed away from it, as they do many things. Of course I am NOT a legal expert.

---

### Post by TheFu on 2012-10-09
> **oregonbob said:**
> Personally I think GMail is as secure as any other cloud email service, but there are many experts who disagree.

For most business uses in normal businesses, I'd never use a cloud provider.

OTOH, if you are only putting information that you want the entire world to know and see in the cloud - I say go for it.  

Medical records of any sort should never be stored in the cloud, IMHO.  Virtual CPU, virtual networks, virtual storage, virtual servers ... that's a lot of virtual things for a human to accidentally screw up.  Even with encrypted storage, that doesn't mean nobody can see the files/data, since even accessing that data requires decryption on some level.  Best to not use public cloud computing for sensitive data.

Some call me paranoid.

I absolutely LOVE private clouds either on systems located inside a company or inside a cage at a shared data center where nothing but the network and power is shared with others.

---

### Post by oregonbob on 2012-10-22
Google would not make a commitment to make gmail compliant to HIPAA health care privacy rules. So now they have new competition as Microsoft seizes an opportunity:

Microsoft Office 365 Boasts HIPAA-Compliant 
[http://www.informationweek.com/healthcare/security-privacy/office-365-boasts-hipaa-compliant-messag/240009519]("http://www.informationweek.com/healthcare/security-privacy/office-365-boasts-hipaa-compliant-messag/240009519")

---

### Post by Penguin360 on 2012-10-22
You should never use email to send or receive sensitive information, no matter what email provider you use.

---

### Post by mike acker on 2012-10-22
> **CodingBeaver said:**
> You should never use email to send or receive sensitive information, no matter what email provider you use.

it should be remembered hackers generaly steal the data they want from one of the endpoints -- using malware

at the same time we note public e/mail services tend to archive and index customer e/mails so that targeted adverts can be sent

to get around this: get one of the 4:1 office printers that can scan, copy, print, and fax.  this way you can communicate with folks who only use printers and fax machines.

when someone sends you a document you can scan it, store the scan as .pdf and throw the original away.

of course people *could* use Libreoffice-- which will offer the alternative: instead of printing you can send via .pdf   when you do this Libreoffice converts your document (write or spreadsheet) to .pdf and creates an e/mail via Thunderbird with the .pdf attached.  all you need to do yet is click on PGP for encryption, --

-- it's all there -- but you won't see folks using it until are 3d graders become grandparents

---

