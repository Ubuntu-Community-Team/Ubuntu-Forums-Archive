---
title: "PGP/GPG, Security and Censorship"
date: 2012-01-18
forum: Security
---

### Post by GraeW on 2012-01-18
So I've been searching around some on the forums, and wondering what the use is for PGP/GnuPG security for the average user? I remember a decade ago (and more) how the push was trying to move people into more secure transactions online - thus the creation of secure connections for the web, email, etc.
 
But now, more than a decade later, I see just as little activity for average/daily encryption. Other than the digital signing of files for authenticity, how much encryption is really traded around out there in email and the like? Although I don't have it set up right now since reinstalling Ubuntu, I used to have a gpg plugin for email so I could digitally sign email. Is it worthwhile going back to being a conspiracy theorist? ;)
 
Just some things making me go "hmmmmm..." today. (and, ok, trying to boost my bean count.. ;)

---

### Post by Lars Noodén on 2012-01-18
I know that there are companies which do use PGP for billing and ordering.  There really was a big push about 10 years ago.  The background is the same as for SSL/TLS, you need secyre communications to safely do business.  

If you want to see some interesting loss of coverage, try to dig up the *final* resoltion A5-0264/2001 from the European Parliament to protect businesses.  
Points 28 - 32 are the most relevant, particularly 30 and 32:

[indent][i]
30. Calls on the Commission and Member States to promote software projects whose source text is made public (open-source software), as this is the only way of guaranteeing that no backdoors are built into programmes;
...
32. Calls on the European institutions and the public administrations of the Member States systematically to encrypt e-mails, so that ultimately encryption becomes the norm;[/i]
[/indent]

You can still get the package "enigmail" for Thunderbird.  The technology caught up with the mandate long ago.  Ubuntu could be leveraging these types of decisions in its marketing.

Edit:  Found it:

[http://www.europarl.europa.eu/sides/getDoc.do?pubRef=-//EP//TEXT+REPORT+A5-2001-0264+0+DOC+XML+V0//EN](http://www.europarl.europa.eu/sides/getDoc.do?pubRef=-//EP//TEXT+REPORT+A5-2001-0264+0+DOC+XML+V0//EN)

Item 29 is also highly relevant:

[indent]
*29.   Urges the Commission and Member States to devise appropriate measures to promote, develop and manufacture European encryption technology and software and above all to support projects aimed at developing user-friendly open-source encryption software;*
[/indent]

---

### Post by tubbygweilo on 2012-01-18
> You can still get the package "enigmail" for Thunderbird. The technology caught up with the mandate long ago. Ubuntu could be leveraging these types of decisions in its marketing.

I have been using this for a good few years, the hard bit is convincing those I wish to communicate with to install it and use it.

Sometimes it all seems an uphill battle.

Although google searching for the string > -----BEGIN PGP PUBLIC KEY BLOCK-----
does show a good few others using the technology.

---

### Post by GraeW on 2012-01-18
When I can get the laptop home and back on the network I will probably start getting all the crypto back up and running again. I have been lax about it - surprising, since it was my job for ten years when I was in the Navy.
 
I was passingly familiar with the European laws regarding open source software, and how they have pushed to keep government offices running FOSS as much as possible. Always good to see promotion of commercial alternatives wherever it happens.

---

### Post by kevdog on 2012-01-19
There are many startup companies associated with text messaging on phones that want to offer use of sms messaging that basically uses gpg encryption as the backend (or use of AES encryption and digital signatures).  The products however are transparent to the end user.

---

### Post by Lars Noodén on 2012-01-19
> **kevdog said:**
> There are many startup companies associated with text messaging on phones that want to offer use of sms messaging that basically uses gpg encryption as the backend (or use of AES encryption and digital signatures).  The products however are transparent to the end user.

Cool.  SMS is very insecure and PGP would help fix that.  

Although Gnupg is already part of the default installation for Ubuntu desktop, transparency to the end user is what it would take in Ubuntu, too, for it to be used widely.  For starters, Thunderbird would have to come with Enigmail as part of the default install.  And there would have to be a wizard to walk beginners through making keys.  

There is also some functionality that would have to be added to Thunderbird before encryption would be embraced by the public at large.  Right now, it is not possible to search old encrypted messages.  One way out could be to have a separate index for each key and require the key for each search.

---

