---
title: "LastPass - Who uses it?"
date: 2010-06-04
forum: Security
---

### Post by lookitseman on 2010-06-04
*[COLOR="Silver"]I saw another thread on LastPass, but it looks like it was written when the service was just getting started, and the thread kinda died off, and there was no reason to resurrect it.[/COLOR]*

Do any of you guys use LastPass?  Do you trust it?  Is there another browser-based password manager "in the cloud" that you use instead?

I'm on the fence.  I use it, but I don't mention it to others.  I couldn't recommend it to others to trust, because I don't know if I trust it myself.  I can't come to a determination if I should keep using it, or if I should head for the hills and start changing my passwords.

I think the best way to phrase what I'm asking is...

**Would you recommend LastPass to the average computer user, knowing that the average computer user wouldn't think twice before giving it their banking information?**

---

### Post by lookitseman on 2010-06-05
Well that's not a good sign...

Do any of you use web-based password managers at all?

---

### Post by rookcifer on 2010-06-06
I use it, although rather reluctantly as it's not open-source.  However, it is much easier to use than the alternatives I have come across with the added benefit of having a FF and a Chrome plugin.

I have no reason to distrust it, as (according to the site) all passwords are encrypted locally before ever being uploaded to their servers.  I do wish there were an open-source alternative, however.

---

### Post by CharlesA on 2010-06-06
I use keepassx, but then I wouldn't trust anything in the "cloud" as it is out of my control.

---

### Post by an0dos on 2010-06-06
I prefer to use "password" as my password on all web sites. (j/k)

I actually use a low-tech and free solution. I write them on a piece of paper and lock them up. If someone breaks into my house I have a lot more to worry about than them getting my passwords. I don't really trust any sort of service that aggregates my passwords. My gut feeling is that the increased likelihood of such a service being attacked combined with the detriment caused by someone with nefarious purposes gaining access to said passwords offsets any potential benefit of using said service.

---

### Post by BigCityCat on 2010-06-06
Been using it for a couple weeks.

---

### Post by uRock on 2010-06-06
> **an0dos said:**
> I prefer to use "password" as my password on all web sites. (j/k)
I use failword. It has never been cracked.

---

### Post by swimfish on 2010-06-07
i've had good results with keypassx.  its interoperable with keypass 1.17 i think it is for windows.  if you save your .kbd file to your dropbox account, its accessible to all of your own personal computers.  

i know nothing about lastpass.  

in order to open the .kbd database you have to unlock it locally on the keypass program trying to access it.  nice thing about keypass for windows is they have a version that will work without a local install (usb drive).  i'm thinking it has mac support too.  

i'd like to hear about other alternatives.  

please no flames i only use win7 for itunes :)  if only banshee with convert to mp3 on the fly :)

---

### Post by Jay Car on 2010-06-07
I've been using Lastpass for a couple of weeks now. Someone had asked me what I thought of it. I had never heard of it before, so I told them I'd try it out and see how it worked.

So far it's worked fine. I only chose a few passwords for LastPass to keep track of, and I don't let it fill-in forms for me, but it will do that if you want it to.

---

### Post by SteamInc on 2010-06-08
I use lastpass, it works, but i dont trust it. I just use it for basic things like gaming websites or forums. Nothing that will kill me.

---

### Post by anomie on 2010-06-08
[QUOTE=lookitseman]Would you recommend LastPass to the average computer user, knowing that the average computer user wouldn't think twice before giving it their banking information?[/QUOTE]

Assumptions about the "average" computer user: 
[list]
[*] He uses his computer for banking, entertainment, research, and work. 
[*] He does not use strong passwords. 
[*] He runs Windows. 
[*] He may or may not run all programs as Administrator. 
[*] He allows scripts to run (the default) in his buggy web browser. 
[/list]

The guy is already a sitting duck. Using a cloud-based password keeper isn't going to make his situation substantially worse. In fact, it may be an improvement, as he'll have the capability to store multiple, *different* passwords somewhere other than a Notepad file on his desktop. 

Would I recommend a cloud-based password keeper to someone who is careful enough to use a well known, vetted, open source, local password keeper? No.

---

### Post by dot2kode on 2010-06-08
I have been using last pass for a long time now and I have never had any problems with it of course some of the more 'sensitive' sites i use i.e banking I do not store in lastpass.  One thing it does though I really like is is sends you notifications anytime any password to one of your sites has been modifed or whatever along with the IP  You can also make profiles so if your away say on a public computer you can setup a profile that only has a few of your passwords you might need.  You can also add extra passwords to individual sites, so if for instance to login to ubuntuforums you would also setup another password for it and you must enter it in to access the forums.  There is also an offline/portable version available too but im not for sure if they have a linux version.

p.s. sorry for the typo's long day ](*,)...if you have any other questions feel free to send me a message.

---

### Post by lookitseman on 2010-06-09
> **anomie said:**
> 
The guy is already a sitting duck. Using a cloud-based password keeper isn't going to make his situation substantially worse.

You have a very good point, and thank you all for the other responses.  I'm going to have to try this other program you guys speak of.

I'm working on an article which describes some ways to keep your accounts safe without the hassle associated with remembering a bunch of complex passwords.  I had planned to mention LastPass, but I don't think I will anymore, instead sticking to more common methods (using a mnemonic, [password], P455w0Rd, not using common passwords like "password", etc).  I'll probably stop using LastPass myself if any of the open source options work out.

Thanks again.

---

### Post by JoeSiegrist on 2010-06-10
Full Disclosure: I'm from [LastPass]("http://lastpass.com")

You can use the open source versions of LastPass: We have a binary free version for Firefox, and Chrome, both are 100% Javascript and DHTML with accessible source.  We obfuscate it to make smaller and more difficult for our competitors to directly copy us, but in the sense of:
[LIST]
[*]"prove this is safe", 
[*]"if there's some emergency I can fix it", and
[*]"show me the source code",
[/LIST]
the source is available.  The binary versions have extra functionality (like a faster implementation of encryption/decryption) but they're not required.  So LastPass can be run using open source just not "free open source".  If you're against LastPass making money from software, so be it, we can't change your religion.

Most people simply don't understand how a cloud based password manager could be safe so they err on the side of caution and ignorance without looking into how it actually works. 

Pick a strong master password, and your sensitive data is secure because the data is AES encrypted and decrypted locally (**on your computer only**). A fact you can verify using the source.

Not including LastPass and helping to ensure the status quo where almost all users are going to ignore your advice about making stronger passwords seems pretty pointless.

---

### Post by anomie on 2010-06-10
[QUOTE=JoeSiegrist]Pick a strong master password, and your sensitive data is secure because the data is AES encrypted and decrypted locally (**on your computer only**). A fact you can verify using the source.[/quote]

An Ubuntu forum thread on LastPass gets CEO-level attention? ;) 

Let's talk about attack vectors for a moment. 

So, encryption/decryption is handled locally on the user's workstation. (Good idea.) But you're still remotely storing an encrypted file that contains all his credentials. If said encrypted file is captured by a bad guy, it can be subjected to an offline attack, which means one hurdle to stealing credentials has been eliminated. 

What this comes down to in my book is: Who do I trust more to keep my own encrypted files safe? Me? Or a third-party remote host? With respect, I trust myself substantially more. (Many users likely feel differently.) 

Tangentially: I suspect (but don't know for sure) that the folks who replied to this thread are not opposed to your organization making $$, nor do they seek to maintain a status quo for its own sake.

---

### Post by swimfish on 2010-06-10
i think i'll stick to keypassx

---

### Post by uRock on 2010-06-10
> **JoeSiegrist said:**
> Full Disclosure: I'm from [LastPass]("http://lastpass.com")

You can use the open source versions of LastPass: We have a binary free version for Firefox, and Chrome, both are 100% Javascript and DHTML with accessible source.  We obfuscate it to make smaller and more difficult for our competitors to directly copy us, but in the sense of:
[LIST]
[*]"prove this is safe", 
[*]"if there's some emergency I can fix it", and
[*]"show me the source code",
[/LIST]
the source is available.  The binary versions have extra functionality (like a faster implementation of encryption/decryption) but they're not required.  So LastPass can be run using open source just not "free open source".  If you're against LastPass making money from software, so be it, we can't change your religion.

Most people simply don't understand how a cloud based password manager could be safe so they err on the side of caution and ignorance without looking into how it actually works. 

Pick a strong master password, and your sensitive data is secure because the data is AES encrypted and decrypted locally (**on your computer only**). A fact you can verify using the source.

Not including LastPass and helping to ensure the status quo where almost all users are going to ignore your advice about making stronger passwords seems pretty pointless.

I can clearly understand charging money for such a service, because to make the promise of security comes with having employees protecting your servers.

I would only use a system like your on a server stationed within a local intranet where they server can't be accessed from outside the intranet without hacking one of the local system on the network and using it to connect to the server. At that point it just doesn't sound cost efficient.

At home I use my own password storage with encryption, though I don't need it because I have the ability to memorize my passwords and don't trust storing highlevel passwords even on the local machine.

---

### Post by randyklein99 on 2010-06-10
I use it and love it.

---

### Post by rookcifer on 2010-06-10
> **anomie said:**
> An Ubuntu forum thread on LastPass gets CEO-level attention? ;) 

Let's talk about attack vectors for a moment. 

So, encryption/decryption is handled locally on the user's workstation. (Good idea.) But you're still remotely storing an encrypted file that contains all his credentials. If said encrypted file is captured by a bad guy, it can be subjected to an offline attack, which means one hurdle to stealing credentials has been eliminated. 

Doesn't concern me.  Good luck to the bad guy in trying to brute-force AES-128 or 256.  He will be waiting longer than the age of the universe.

> What this comes down to in my book is: Who do I trust more to keep my own encrypted files safe? Me? Or a third-party remote host? With respect, I trust myself substantially more. (Many users likely feel differently.) 

Do these local password managers automatically fill in the login credentials to all your websites?  LastPass does, which is why I use it.

> Tangentially: I suspect (but don't know for sure) that the folks who replied to this thread are not opposed to your organization making $$, nor do they seek to maintain a status quo for its own sake.

I agree.  I, for one, don't have an issue with people making money from software.  I just wish a lot of the closed-source software makers weren't so, well, secretive with the source, especially when it comes to security software.

---

### Post by anomie on 2010-06-10
[QUOTE=rookcifer]Doesn't concern me.  Good luck to the bad guy in trying to brute-force AES-128 or 256.  He will be waiting longer than the age of the universe.[/QUOTE]

Notice I made no comments about the strength of AES (or any other cipher). 

My point was the security of the file itself is another layer in the security onion. If it legitimately was not we'd all keep our encrypted files out on publicly accessible ftp servers for convenience.

---

### Post by FuturePilot on 2010-06-10
> **rookcifer said:**
> 
Do these local password managers automatically fill in the login credentials to all your websites?  LastPass does, which is why I use it.


Firefox can remember passwords and when you couple that with the Secure Login extension, logging in to a site is literally 1 click away.

> I agree. I, for one, don't have an issue with people making money from software. I just wish a lot of the closed-source software makers weren't so, well, secretive with the source, especially when it comes to security software. 

Exactly, which is why I love KeePass. They have this quote on their front page:

> As a cryptography and computer security expert, I have never understood the current fuss about the open source software movement. In the cryptography world, we consider open source necessary for good security; we have for decades. Public security is always more secure than proprietary security. It's true for cryptographic algorithms, security protocols, and security source code. For us, open source isn't just a business model; it's smart engineering practice.
[Bruce Schneier, Crypto-Gram 1999/09/15]("http://www.schneier.com/crypto-gram-9909.html")

---

### Post by rookcifer on 2010-06-10
> **anomie said:**
> Notice I made no comments about the strength of AES (or any other cipher). 

My point was the security of the file itself is another layer in the security onion. If it legitimately was not we'd all keep our encrypted files out on publicly accessible ftp servers for convenience.

I keep my private encryption keys on a cloud server (both public and private keys).  Of course, the private key itself is encrypted with a very strong password.  I have no reservations about it since it would be much easier for the [MIB's]("http://en.wikipedia.org/wiki/Men_in_Black") to use [rubber-hose cryptanalysis]("http://en.wikipedia.org/wiki/Rubber-hose_cryptanalysis") than to brute force my password.  The way I look at it, my private key has equal security either on my PC or on a cloud server.

---

### Post by lookitseman on 2010-06-11
> **JoeSiegrist said:**
> If you're against LastPass making money from software, so be it, we can't change your religion.

You must have misunderstood me, because I'm a software developer, and I love money, probably as much as you do. :p

> **JoeSiegrist said:**
> Most people simply don't understand how a cloud based password manager could be safe so they err on the side of caution and ignorance without looking into how it actually works.

I have looked into how it works, but your website is the only authority on that matter.  As a security company, I'm sure you see the need for a trusted third party to verify that LastPass is as trustworthy as LastPass says it is.  Without that, I can't recommend LastPass to others, as they would see me as *their* trusted third party (I know many of my readers personally), and I would be breaking the chain of trust.

It's not about whether or not LastPass is good software.  I think it's great software, I've been using it for about a month.  It's about whether or not I am willing to recommend it to my readers, which I'm not comfortable with just yet.

It's nothing personal, I wish you and your team the best, and I applaud you on making such a great product.  Hopefully I'll be recommending LastPass to others in the near future.

---

