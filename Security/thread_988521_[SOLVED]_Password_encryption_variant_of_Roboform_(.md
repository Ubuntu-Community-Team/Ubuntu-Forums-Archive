---
title: "[SOLVED] Password encryption variant of Roboform (Win) in ubuntu"
date: 2008-11-20
forum: Security
---

### Post by Jammanuser on 2008-11-20
Hi, i just recently installed Ubuntu 8.10 on my laptop computer, on top of my pre-installed Vista OS, using Wubi installer, and i was wondering if there is a program for ubuntu that is similar to Roboform, a Windows OS password encrypting program that stores passwords in ur browser, using an encrypted format, and allows auto-filling in of user name and password fields on websites, requiring only ONE master password to access ur passcards, making it a hell of a lot easier to access websites requiring usernames and passwords, securely, without having to memorize every single username and password. i've heard of the two ubuntu password storing programs called Revelation and LastPass. well...i've heard once before (don't know if its true or not; u judge) that LastPass is some kind of scam! and as for the program Revelation, i recently installed that program, and learned that it is NOTHING like Roboform, and does not even look like it allows u to access passcards from within ur browser, and certainly probably does not encrypt them if it does!

so my question is this: does anyone who has used Roboform before, and uses Ubuntu, know of any program that is similar to it, for Ubuntu? i would also like for it support the format that Roboform uses (rfp), so that i can simply import my passcards from Roboform into the program in Ubuntu, so that i don't have to spend days manually filling in the information from the passcards in Roboform!

Thanks in advance! :)

---

### Post by Linteg on 2008-11-20
I'm not really sure if this is what you really want, but Firefox has a master password setting (Tools(?)->Options->Security). If you activate it, you'll have to type in the master password when you want to use any of the stored passwords.

---

### Post by Dr Small on 2008-11-20
I store all my passwords in a GPG encrypted text document, for ease.

---

### Post by Jammanuser on 2008-11-20
Thanks, Linteg, but no! that's not what i want! of course i know about the Firefox feature, but i'm not convinced that it stores passwords in an encrypted format, like Roboform does, so i really want..well, pretty much what i said i wanted!!! i want a program similar to Roboform, with similar features, that will work on Ubuntu 8.10!

---

### Post by Jammanuser on 2008-11-20
uhh...Dr. Small!!! i don't want to store my passwords in a DOCUMENT, i want to store them in a PROGRAM similar to Roboform!!! did u not even read my above message?

Thanks for the effort, but that's not what i want to do!!!

---

### Post by dunkar70 on 2008-11-20
There is a windows program called KeePass that stores various information in an encrypted database. There is a portable version available [here]("http://portableapps.com/apps/utilities/keepass_portable"). Although a windows program, it runs very well under wine.

---

### Post by Dr Small on 2008-11-20
> **Jammanuser said:**
> uhh...Dr. Small!!! i don't want to store my passwords in a DOCUMENT, i want to store them in a PROGRAM similar to Roboform!!! did u not even read my above message?

Thanks for the effort, but that's what i want to do!!!

Yes, I read your post. I was just giving you a hint as to how I do it ;)

> **dunkar70 said:**
> There is a windows program called KeePass that stores various information in an encrypted database. There is a portable version available [here]("http://portableapps.com/apps/utilities/keepass_portable"). Although a windows program, it runs very well under wine.

There is a linux native one called "KeepassX". It should be in the repositories.

---

### Post by dunkar70 on 2008-11-20
Thanks for the heads-up Dr. Small.

---

### Post by Jammanuser on 2008-11-20
> **Dr Small said:**
> Yes, I read your post. I was just giving you a hint as to how I do it ;)



There is a linux native one called "KeepassX". It should be in the repositories.

oh..ok! thanks! do u know where i can find 'KeepassX'? i mean, i know u said its in the repositories, but i'm not sure what that means! i assume it means that its probably already installed on my computer, but i don't know what u mean when u say 'repositories'! please explain!

sorry! :popcorn: i'm a noob! :confused:

---

### Post by Dr Small on 2008-11-20
> **Jammanuser said:**
> oh..ok! thanks! do u know where i can find 'KeepassX'? i mean, i know u said its in the repositories, but i'm not sure what that means! i assume it means that its probably already installed on my computer, but i don't know what u mean when u say 'repositories'! please explain!

sorry! :popcorn: i'm a noob! :confused:
Not a problem. We all start somewhere ;)
Check out this wiki page that has already been created to expound on the subject. It's a great read:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Jammanuser on 2008-11-21
well, thanks, Dr. Small, but...i downloaded and installed keypassx (using synaptic, of course), and it turns out to be pretty much like the other password program, 'Revelation', that i already have installed on Ubuntu, but was looking for something like Roboform! again, i need something that will allow me to store passcards in an **encrypted** format in my browser, so that when i'm at a particular site that requires a username and password, all i have to do click the appropriate passcard (from **within** my browser, and the program will automatically fill in the empty fields, after typing a master password...like Roboform!!!

is there nothing for Ubuntu that can do this then????

Thanks to all honest replies!!!

---

### Post by cariboo on 2008-11-21
If you open System-->Administration-->Synaptic Package Manager and click the search button (don't use quick search) and enter:

```
encrypt passwords
```

I come up with quite a few password management programs. You'll have to check them out yourself to see what suits you best.

Jim

---

### Post by Dr Small on 2008-11-21
> **Jammanuser said:**
> well, thanks, Dr. Small, but...i downloaded and installed keypassx (using synaptic, of course), and it turns out to be pretty much like the other password program, 'Revelation', that i already have installed on Ubuntu, but was looking for something like Roboform! again, i need something that will allow me to store passcards in an **encrypted** format in my browser, so that when i'm at a particular site that requires a username and password, all i have to do click the appropriate passcard (from **within** my browser, and the program will automatically fill in the empty fields, after typing a master password...like Roboform!!!

is there nothing for Ubuntu that can do this then????

Thanks to all honest replies!!!
Since you are not happy with that, you can try this addon that I use for Firefox:
[https://blueimp.net/mozilla/](https://blueimp.net/mozilla/)

Not really sure on encryption, nor how Roboform works, but you just press the key (or ALT + n) and it auto-logs you in. I'm pretty sure it just uses the passwords from the Firefox Password Manager. This is your best bet.

---

### Post by cdenley on 2008-11-21
> **Jammanuser said:**
> Thanks, Linteg, but no! that's not what i want! of course i know about the Firefox feature, but i'm not convinced that it stores passwords in an encrypted format, like Roboform does, so i really want..well, pretty much what i said i wanted!!! i want a program similar to Roboform, with similar features, that will work on Ubuntu 8.10!

You're not convinced it stores passwords in an encrypted format? Then take a look for yourself!
```

gedit ~/.mozilla/firefox/*.default/signons3.txt

```

[http://kb.mozillazine.org/Signons3.txt](http://kb.mozillazine.org/Signons3.txt)
> 
This file is encrypted to help prevent others with access to your computer from seeing your passwords.


---

### Post by Jammanuser on 2008-11-23
> **cariboo907 said:**
> If you open System-->Administration-->Synaptic Package Manager and click the search button (don't use quick search) and enter:

```
encrypt passwords
```

I come up with quite a few password management programs. You'll have to check them out yourself to see what suits you best.

Jim

Thanks, Jim! but i decided to go with the Firefox solution, after all, since i learned that Firefox does indeed encrypt its stored passwords...and u can even set it to ask u for a master password to access the encrypted passwords! 

anyway, thanks for the effort!


Cheers!

:guitar:

---

### Post by Jammanuser on 2008-11-23
> **Dr Small said:**
> Since you are not happy with that, you can try this addon that I use for Firefox:
[https://blueimp.net/mozilla/](https://blueimp.net/mozilla/)

Not really sure on encryption, nor how Roboform works, but you just press the key (or ALT + n) and it auto-logs you in. I'm pretty sure it just uses the passwords from the Firefox Password Manager. This is your best bet.

Thanks, Dr. Small! i tried ur solution...using the Firefox addon 'Login Secure', and thought it was really cool...until i learned that it doesn't prompt u for ur Firefox master password, so anyone on my computer would be able to access them, which would be dangerous! so i decided to go with just the Firefox Password Manager itself, after all, after learning that it DOES store the passwords in an encrypted format!

Anyway, thanks for the effort!

:lolflag:

---

### Post by Jammanuser on 2008-11-23
> **cdenley said:**
> You're not convinced it stores passwords in an encrypted format? Then take a look for yourself!
```

gedit ~/.mozilla/firefox/*.default/signons3.txt

```

[http://kb.mozillazine.org/Signons3.txt](http://kb.mozillazine.org/Signons3.txt)


thanks, cdenley! that's what i needed to know! i wasn't sure before about Firefox storing passwords encrypted, and that's why i was looking for something like Roboform for Windows, only for Ubuntu, instead! thanks for clearing it up, and i've decided to go with that after all...since i'm not sure about all those password managing programs for Linux, that i could install using synaptic, and would rather not spend the time digging through them all!

anyway, thanks! much appreciation!

Cheers!

:lolflag:

---

### Post by Dr Small on 2008-11-24
> **Jammanuser said:**
> Thanks, Dr. Small! i tried ur solution...using the Firefox addon 'Login Secure', and thought it was really cool...until i learned that it doesn't prompt u for ur Firefox master password, so anyone on my computer would be able to access them, which would be dangerous! so i decided to go with just the Firefox Password Manager itself, after all, after learning that it DOES store the passwords in an encrypted format!

Anyway, thanks for the effort!

:lolflag:
It would probably prompt you for the master password if you enabled it in the Firefox Preferences. I've never tried it, but that's just a guess.

---

### Post by kevdog on 2008-11-24
Just a word of caution

I didn't know prior to this discussion that firefox stored passwords using encryption.  That is good to know.

However beyond just saying "They are encrypted in a file" and forget about it --- how about discovering what type of encryption they use?  What algorithm do they use?  Saying they are encrypted and that's good enough, is a little bit misleading.  Lets all try to find some details on their encryption scheme so we can all learn.

---

### Post by Jammanuser on 2008-11-24
> **kevdog said:**
> Just a word of caution

I didn't know prior to this discussion that firefox stored passwords using encryption.  That is good to know.

However beyond just saying "They are encrypted in a file" and forget about it --- how about discovering what type of encryption they use?  What algorithm do they use?  Saying they are encrypted and that's good enough, is a little bit misleading.  Lets all try to find some details on their encryption scheme so we can all learn.

good idea!!! i was wondering that myself, but not sure how to find out what kind of encryption firefox uses!

Maybe u could help with that... (hint)

:guitar:

---

### Post by cdenley on 2008-11-24
As far as I can tell, it uses PKCS#11.
[http://www.mozilla.org/projects/security/pki/nss/db_formats.html](http://www.mozilla.org/projects/security/pki/nss/db_formats.html)
[http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html](http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html)
[http://en.wikipedia.org/wiki/PKCS11](http://en.wikipedia.org/wiki/PKCS11)

---

### Post by Jammanuser on 2008-11-24
> **Dr Small said:**
> It would probably prompt you for the master password if you enabled it in the Firefox Preferences. I've never tried it, but that's just a guess.

it doesn't!!! believe me! i tried it! :(

---

### Post by Jammanuser on 2008-11-24
> **cdenley said:**
> As far as I can tell, it uses PKCS#11.
[http://www.mozilla.org/projects/security/pki/nss/db_formats.html](http://www.mozilla.org/projects/security/pki/nss/db_formats.html)
[http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html](http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html)
[http://en.wikipedia.org/wiki/PKCS11](http://en.wikipedia.org/wiki/PKCS11)

so is that a good encryption format? or can it be hacked easily?

Looking forward to ur reply...

---

### Post by Dr Small on 2008-11-24
> **Jammanuser said:**
> it doesn't!!! believe me! i tried it! :(
Works as expected for me; I just tried it :-k

---

### Post by Jammanuser on 2008-11-25
> **Dr Small said:**
> Works as expected for me; I just tried it :-k

r u sure??? why would it work for u and not for me, then? i tried multiple times logging in a site using Login Secure, with Master Password enabled in Firefox, and every single time it didn't prompt me for the master password, and automatically filled in my username and password without prompting!!!

not sure why it didn't work for me then...

---

### Post by kevdog on 2008-11-25
> **Jammanuser said:**
> so is that a good encryption format? or can it be hacked easily?

Looking forward to ur reply...

I looked into PCKS#11 -- and that isn't really a cipher.  The only cipher suite available with Mozilla specifically implementing the PCKS#11 standard is a cipher suite known as Fortezza.  Looking around the Mozilla site I'm unable to actually pin down the exact ciphers and hashes used in the Fortezza cipher collection, however I've seen the following ciphers mentioned: RC4 with 128-bit encryption (US only) or RC4 with SKIPJACK 80-bit encryption.  Because of US government standards, not all encryption capabilities can be exported.

SHA-1 is definitely the hash used for all.  

So its a variant of RC4 along with the SHA1 hash.  I'm no cryptographer, however RC4 (AKA ArcFour) is the cipher used with in WEP.  Judging its security level -- as someone famous most recently stated -- "That's beyond my paygrade!"

---

### Post by Jammanuser on 2008-11-26
> **kevdog said:**
> I looked into PCKS#11 -- and that isn't really a cipher.

so r u saying then that Mozilla Firefox **doesn't** encrypt its passwords then, after all, despite that that other guy said it did??? now i'm **really** confused!!! does or does not Firefox  encrypt its stored passwords?

i need to know, because i REALLY want my passwords to be safe!!!

Thanks in advance! :)

EDIT: and where can i find Fortezza, or whatever it is?

---

### Post by kevdog on 2008-11-26
no PCKS#11 is a standard for cryptographic tokens. 

Firefox's implementation of the PCKS#11 standard uses the Fortezza encryption suite.

Depending on the locale of Firefox (US vs non-US b/c some export of some cryptographic functions are illegal), Mozilla's fortezza implementation uses a RC4(128-bit encryption)/SHA-1 hash (for US) or RC4(80 bit Skipjack encryption)/SHA-1 hash.

I found this information on Firefox's website this morning.  Sorry I didn't list the reference.  But if I remember correctly I googled Fortezza Mozilla and it provided a reference.

Edit:  Here is the page I found: [http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html](http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html)

---

### Post by michaelzap on 2008-11-26
> **Jammanuser said:**
> ...i've heard once before (don't know if its true or not; u judge) that LastPass is some kind of scam!

You "heard" that LastPass is a scam and a) believed it without any evidence and b) spread this rumor here on the forums? Shame on you. I can certainly understand if people would rather not trust an online service with their password info, but it's irresponsable to spread FUD without at least doing a little bit of research into whether the rumor you heard is well-founded or not.

LastPass [encrypts all your password data locally]("http://ubuntuforums.org/showpost.php?p=5899644&postcount=8") before sending it to their servers. This is similar to many other online services like JungleDisk and hardly seems consistent with them being a scam. All of this is [abundantly documented on the LastPass website]("https://lastpass.com/faq.php#stolen").

Personally I decided that I prefer to use KeePassX (and I have no affiliation with the LastPass folks), but I didn't feel that it was right to allow this little bit of misinformation to go uncorrected.

---

### Post by erawk on 2008-11-27
I would defenitly give my vote to lastpass

I never thought id say it... but i found a replacement for Roboform that works equally as good... if not better, while being equally as secure.... I tried 3-4 of em before i finally found one that actually performs like it needs too.... I have tried all the ones suggested and they all were piss poor.... 

If you are used to Roboform... Dont waste your time w/ any of these: Sxipper, Keypass, autofill/secure login.

> **Do you use a salted hash for login purposes?**
*Yes, we first do a 'salt' of your LastPass password with your username on the client side (on your computer, LastPass never gets your password), then server side we pull a second 256 bit random hex-hash salt from the database, use that to make a salted hash which is compared to what's stored in the database. This is beyond overkill but we want to store nothing that can even theoretically be used to do a dictionary attack against password hashes if LastPass' servers were somehow compromised. We hope having nothing of value makes us less of a target, and that by taking every conceivable caution we can think of makes you more safe.*

**What encryption is being used?**
*AES utilizing 256-bit keys. AES-256 is accepted by the US Government for protecting TOP SECRET data. AES is implemented in JavaScript for the LastPass.com website, and in C++ for speed in the Internet Explorer and Firefox plug-ins. This is important because your sensitive data is always encrypted and decrypted locally on _your computer_ before being synchronized. Your master password never leaves your computer and your key never leaves your computer. No one at LastPass (or anywhere else) can decrypt your data without you giving up your password (we will never ask you for it). Your key is created by taking a SHA-256 hash of your password. When you login, we make a hash of your username concatenated with your password, and that hash is what's sent to verify if you can download your encrypted data.*

---

### Post by Jammanuser on 2008-11-27
> **kevdog said:**
> no PCKS#11 is a standard for cryptographic tokens. 

Firefox's implementation of the PCKS#11 standard uses the Fortezza encryption suite.

Depending on the locale of Firefox (US vs non-US b/c some export of some cryptographic functions are illegal), Mozilla's fortezza implementation uses a RC4(128-bit encryption)/SHA-1 hash (for US) or RC4(80 bit Skipjack encryption)/SHA-1 hash.

I found this information on Firefox's website this morning.  Sorry I didn't list the reference.  But if I remember correctly I googled Fortezza Mozilla and it provided a reference.

Edit:  Here is the page I found: [http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html](http://www.mozilla.org/projects/security/pki/nss/tools/modutil.html)

ok..thanks!!! :)  so what ur basically saying then, is that PCKS#11 isn't the **actual** password encryption format...but Firefox **does** encrypt its stored passwords, using RC4/SHA-1 (128 bit) hash for US or RC4/SHA-1 hash (80 bit)? ok..**now** i get it! :) now my new question is...is RC4/SHA-1 hash encryption a **good** encryption, or does it have a lot of security holes? can my passwords be trusted to this encryption or no? 

Thanks! :guitar:

---

### Post by Jammanuser on 2008-11-27
> **michaelzap said:**
> You "heard" that LastPass is a scam and a) believed it without any evidence and b) spread this rumor here on the forums? Shame on you. I can certainly understand if people would rather not trust an online service with their password info, but it's irresponsable to spread FUD without at least doing a little bit of research into whether the rumor you heard is well-founded or not.

LastPass [encrypts all your password data locally]("http://ubuntuforums.org/showpost.php?p=5899644&postcount=8") before sending it to their servers. This is similar to many other online services like JungleDisk and hardly seems consistent with them being a scam. All of this is [abundantly documented on the LastPass website]("https://lastpass.com/faq.php#stolen").

Personally I decided that I prefer to use KeePassX (and I have no affiliation with the LastPass folks), but I didn't feel that it was right to allow this little bit of misinformation to go uncorrected.

ok...i apologize! like i said before... i HEARD that LastPass was a scam, and that i WASN'T sure if it was true or not...i **clearly** stated that, and also for others to judge whether it is or is not! i was just throwing that out there, to see if someone clarified that it was, or would say that it didn't...like u did! i wasn't trying to spread a rumor...i only wanted to know if it was true or not, since i haven't had the time to research it yet!

Sorry if i've got on ur bad side, but i was just posting it so others could judge whether it was true or not! yo! :popcorn:

---

### Post by Jammanuser on 2008-11-27
> **erawk said:**
> I would defenitly give my vote to lastpass

I never thought id say it... but i found a replacement for Roboform that works equally as good... if not better, while being equally as secure.... I tried 3-4 of em before i finally found one that actually performs like it needs too.... I have tried all the ones suggested and they all were piss poor.... 

If you are used to Roboform... Dont waste your time w/ any of these: Sxipper, Keypass, autofill/secure login.

ok..thanks for the info about LastPass! again, i wasn't trying to offend anyone on here that uses LastPass and likes it...even though **personally** i would prefer not to have my passwords stored online, period...but that's just me!!! 

Cheers! :guitar:

---

### Post by kevdog on 2008-11-27
Im not a mathmatician or cryptoanalyst to comment on the relative security of the rc4 algorithm.  A lot of programs use it.  Its probably good enough unless your computer is stolen by the NSA.

---

### Post by Jammanuser on 2008-11-28
> **kevdog said:**
> Im not a mathmatician or cryptoanalyst to comment on the relative security of the rc4 algorithm.  A lot of programs use it.  Its probably good enough unless your computer is stolen by the NSA.

ok...that's what i figured!!!

Thanks for all the replies! :guitar:

---

### Post by markharding557 on 2008-11-30
I have found that revalation password manager is pretty good.
native to gnome too

---

