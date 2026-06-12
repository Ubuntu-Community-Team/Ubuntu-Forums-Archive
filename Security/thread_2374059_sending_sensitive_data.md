---
title: "sending sensitive data"
date: 2017-10-12
forum: Security
---

### Post by Buntu Bunny on 2017-10-12
I did some work with a group that wants a W-9 in order to pay me. They want me to send it as a fill-in pdf file via email or as a shared file on Google Drive. Everything in me questions the security of either option (especially by email) and I've just spent the last hour searching the internet for up-to-date information on shared sensitive document security in Drive. Every article I find is either several years old (and likely outdated), comes from Google (of course they're secure), comes from someone wanting to sell an encryption service, or beats around the bush and never gets to the point. So, would you do it? If so, how? 

Come to think of it, if they receive this information via the internet, should I be concerned about how they store it on their devices?

---

### Post by sudodus on 2017-10-12
Try to teach one of them to use **gpg** and create a private/public key pair, and publish the public key or send it to you. If successful, you can encrypt the pdf file with this person's public key

```
gpg -er <user-id-name> <filename> 
```

for example

```
gpg -er sudodus file.pdf
```

and send the gpg-encrypted file **file.pdf.gpg**. Then it will be safe to send it via for example email.

The receiving person can decrypt the file with the following command

```
gpg <filename>
```

for example

```
gpg file.pdf.gpg
```

and use their public key (and a passphrase to activate this public key).

[hr][/hr]
There is a version of gpg for Windows too.

If this is impossible, I don't know any general safe way via the internet. Maybe paper mail is good enough.

---

### Post by CharlesA on 2017-10-12
The company should have policies and practices in place for the handling of any sensitive data.

If you don't want to send the information in the clear and they still want it via email, you could always stick the document in an encrypted zip file and send the passphrase via a different method.

EDIT: Looks like sudodus beat me, but if either method won't work. Paper mail or maybe even fax would be best.

---

### Post by Buntu Bunny on 2017-10-12
> **sudodus said:**
> Try to teach one of them to use **gpg** and create a private/public key pair, and publish the public key or send it to you. If successful, you can encrypt the pdf file with this person's public key

<snip>

There is a version of gpg for Window too.

> **CharlesA said:**
> The company should have policies and practices in place for the handling of any sensitive data.

sudosus and CharlesA, thank you. I will approach them with both of these. They started with a home-business idea of bundling eBooks for a niche audience. This turned out to be very successful so they are moving full steam ahead to expand on the idea. My guess is that they really haven't thought it through to this extent yet. Likeable folks, but from my interactions with them I'm guessing they are more experienced in marketing than computers and computer/internet security.

---

### Post by ian-weisser on 2017-10-12
> **Buntu Bunny said:**
> They want me to send it as a fill-in pdf file via email or as a shared file on Google Drive.

It's not their form. It's the IRS's form. Nobody else can require you to use their private version.
The fillable version on the IRS website is intended to be printed for hand-signature. After that, it should be mailed or scanned.
A W9 can be dangerous in the wrong hands - it's your SSN and your current name/address, all in one convenient package. A highly-desired target for theft.

We exchange W9's via email...as scanned or faxed images from business to business (EINs instead of SSNs).
For personal SSNs, we always use paper and the US Postal Service.

---

### Post by Buntu Bunny on 2017-10-12
> **ian-weisser said:**
> It's not their form. It's the IRS's form. Nobody else can require you to use their private version.
The fillable version on the IRS website is intended to be printed for hand-signature. After that, it should be mailed or scanned.

Yes, it is the IRS's form, they just sent a link to fetch a copy. 

> A W9 can be dangerous in the wrong hands - it's your SSN and your current name/address, all in one convenient package. A highly-desired target for theft.

Agreed, which is why I'm so concerned. It amazes me how many people are willing to blindly hand over personal data without a thought. I won't even give out my phone number when a cashier asks for it!

> We exchange W9's via email...as scanned or faxed images from business to business (EINs instead of SSNs).
For personal SSNs, we always use paper and the US Postal Service.

Excellent advice, which makes me think I should ask if they will input this data into a computer database. That goes back to the question of how they protect such data on their home business computers. For me it has to be an SSN because I'm not in business, just making a little hobby income (which, of course must still be reported).

---

### Post by ian-weisser on 2017-10-12
> **Buntu Bunny said:**
> how they protect such data on their home business computers. For me it has to be an SSN because I'm not in business, just making a little hobby income (which, of course must still be reported).

Small (home) US-based business means they probably use QuickBooks, which protects the SSN field using their encrypted database and internal API controls.
It can be a real pain to get data out of QB. If anyone ever cracks the QB encryption, they can sell it for millions *legitimately* to third-party vendors and won't need to steal PII.

Of course, their Google-based data, other server-stored data, or local data have no such protections.

If they accept credit cards, PII protection policies and practices are part of their annual PCI compliance requirement.

---

### Post by SeijiSensei on 2017-10-12
If you're this concerned, put the form in an envelope and take it to the Post Office.  You can choose Certified or Registered Mail if you want surety of handling.  If you pay for a return reciept, you'll be notified when the item arrives, and the return card will indicate the name of the person who signed for the delivery.

Really, there is a reason why we still have paper forms and traditional mail services.  Not everything has to be electronic.

---

### Post by Buntu Bunny on 2017-10-12
> **ian-weisser said:**
> Small (home) US-based business means they probably use QuickBooks which protects the SSN field using their encrypted database and internal API controls. 

Good info. I will be sure to ask.

> **ian-weisser said:**
> If they accept credit cards, PII protection policies and practices are part of their annual PCI compliance requirement.

They accept credit cards and Paypal. They pay via Paypal. Having had Paypal recently help itself to my account I'm not too happy with them at the moment, but that's another story.

> **SeijiSensei said:**
> If you're this concerned, put the form in an envelope and take it to the Post Office... Not everything has to be electronic.

That's why I'm here asking, to make sure I haven't missed out on any brand new super-duper security information. I've asked these folks for a mailing address so that I can send the form by snail mail, but I have yet to hear back from them. We'll see.

---

### Post by HermanAB on 2017-10-13
In my experience, the strongest data security method that non-geeks can handle are encrypted zip files.

---

### Post by sudodus on 2017-10-13
> **HermanAB said:**
> In my experience, the strongest data security method that non-geeks can handle are encrypted zip files.

You may be right about that. Do you consider the zip encryption secure enough to send this type of data via the internet?

---

### Post by HermanAB on 2017-10-14
Yes, it is good enough.  Even the military uses it to protect files against casual inspection (as opposed to a laboratory attack with a super computer).

Send the file by email and the password by SMS.

---

### Post by Buntu Bunny on 2017-10-15
> **sudodus said:**
> Do you consider the zip encryption secure enough to send this type of data via the internet?

> **HermanAB said:**
> Yes, it is good enough.  Even the military uses it to protect files against casual inspection (as opposed to a laboratory attack with a super computer).
Send the file by email and the password by SMS.

Thank you for that. I tried to search the internet for an answer to sudodus's question, but the web articles were all several years old. From those I gathered that zipped files still needed some special encryption. Not finding a more current answer made me hesitant to go that route.

Oddly, I've not received an answer from these folks about a mailing address for snail mailing the form. Mostly we upload files for the project to Google Drive, so I asked them about alternatives while I researched email and Drive security for sending sensitive documents. This thread has been part of that research. If I ever hear from them I now have a few more questions to ask about how they store it. 

I always get good help here.

---

### Post by CharlesA on 2017-10-15
7zip can create password protected zip files. I believe Winzip and Winrar can do the same.

---

### Post by Buntu Bunny on 2017-10-16
Thanks CharlesA. That helps.

Now here's a related question for you all. Suppose I do send these folks my W-9 in a zipped file with a password. They input the data into something like QuickBooks but save the W-9s everybody sent in a separate folder. How secure is that? 

I'm not trying to get way out here, but the longer they take to address my concerns, the more my mind runs through scenarios like this.

---

### Post by sudodus on 2017-10-16
If you don't want them to save your W-9 as a data file, ask again for a paper mail address and send it that way.

---

### Post by Buntu Bunny on 2017-10-16
> **sudodus said:**
> If you don't want them to save your W-9 as a data file, ask again for a paper mail address and send it that way.

Agreed! That's what I've done - twice. No response so far.

---

### Post by Buntu Bunny on 2017-10-16
Well, it may be a moot point now. I just checked my email and discovered that they'd sent my payment via Paypal even without the W-9.

---

### Post by ian-weisser on 2017-10-16
> **Buntu Bunny said:**
> sent my payment via Paypal even without the W-9.

That's good faith on their part, but they likely still want the form. If they get audited...

---

### Post by sudodus on 2017-10-17
> **ian-weisser said:**
> That's good faith on their part, but they likely still want the form. If they get audited...
+1

But *they* have to send their address to you ...

---

### Post by HermanAB on 2017-10-17
Well, the most insecure part of the data exchange is the email, since nobody has full control over that - it is a free for all and passes through a hodge-podge of servers.  After that, the second most insecure place would be the destination computer, but you have to hope that they have a corporate IT service that nominally knows what they are doing.

---

### Post by Buntu Bunny on 2017-10-17
> **ian-weisser said:**
> That's good faith on their part, but they likely still want the form. If they get audited...

> **sudodus said:**
> +1

But *they* have to send their address to you ...

Exactly! But they haven't responded with that information, which I've asked for twice. 

> **HermanAB said:**
> Well, the most insecure part of the data exchange is the email, since nobody has full control over that - it is a free for all and passes through a hodge-podge of servers.  After that, the second most insecure place would be the destination computer, but you have to hope that they have a corporate IT service that nominally knows what they are doing.

Something I doubt and so why snail mailing the original form would be more secure in the long run than emailing it.

---

### Post by kurt18947 on 2017-10-18
> You may be right about that. Do you consider the zip encryption secure enough to send this type of data via the internet? 				

From what I've read, encryption via 7-zip using AES256 is fairly secure, better than encrypted zip files. The benefit to the zip formats is that they're widely known and cross platform. No doubt PGP encryption is better but challenging for non-techies to use. 7-zip full is available in the repositories.

---

