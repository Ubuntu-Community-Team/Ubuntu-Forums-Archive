---
title: "Simple Roboform (password manager) Replacement"
date: 2006-06-24
forum: Tutorials
---

### Post by Smile! :) on 2006-06-24
Roboform is a great password manager because it allows you to go to a site, fill in your login and password, and automatically click the login button, all in one click. But it's not available for Linux.

Solution: Use Firefox's simple password manager together with two GreaseMonkey scripts to replicate the above functionality.

1. Install GreaseMonkey firefox extension: [http://greasemonkey.mozdev.org/]("http://greasemonkey.mozdev.org/")

2. Install Allow Password Remember script, available from [here]("http://blog.monstuff.com/archives/images/AllowPasswordRemembering.user.js"). This script makes sure that sites which direct the browser not to remember passwords are ignored.

3. Install AutoLoginJ script, available from [here]("http://www.squarefree.com/userscripts/autologinj.user.js"). This script automatically clicks the login button.

The two GreaseMonkey scripts above, along with many useful scripts, can be found at [http://dunck.us/collab/GreaseMonkeyUserScriptsGeneric]("http://dunck.us/collab/GreaseMonkeyUserScriptsGeneric").

Now when you click on a bookmark, it will go to the site, fill in the login and password, and hit OK all in one operation.

---

### Post by golem3 on 2007-02-12
Great - works well for existing passwords, but doesn't allow Firefox to remember new ones!!!

---

### Post by hebetude on 2007-10-05
IMHO, none of them do it right, but roboform is my favorite.  My problem is that all somebody needs to do is compromise your "master" password then they can find every password in the database.  Why do they all do this?  thats a huge security risk.  So, I can't use it for any of my banking sites, even at the risk of there being a keylogger program on my system.

I'm also unsure of their claim to be keylogger-immune, other sites have said you can fill in forms in IE but that firefox lacked the functionality to do so.  Is this true?

Frankly, what I want is the public key encryption model applied to firefox saved passwords.  Where I can type in a passphrase to allow a program to input my passwords into the field, but never allow me to actually see them in plaintext.  This is really not that paranoid, SSH has been doing it for quite some time.  With pageant it even makes the process far simpler.  

One day ... maybe

p.s. read the notice on the greasemonkey site, the security holes in greasemonkey make windows seem like a utopia

---

### Post by erawk on 2008-11-16
LASTPASS - I never thought id say it... but i found a replacement for Roboform that works equally as good... if not better, while being equally as secure.... I tried 3-4 of em before i finally found one that actually performs like it needs too.... I have tried all the ones suggested and they all were piss poor.... 

If you are used to Roboform... Dont waste your time w/ any of these: Sxipper, Keypass, autofill/secure login

---

### Post by MountainX on 2008-11-16
I have to admit that I have been trying Sxipper, Keypass, and others and it does feel like I've been wasting my time.

I will try Lastpass. However, I have to point out that it is not open source. I'm think OK with that atm, but I'll have to learn more about the people behind it. Furthermore, I'm not so sure I like them storing all my sensitive info in an offsite backup (even if it is encrypted). Again, I need to read more.

I'm also thinking about trying the password feature built into Foxmarks, but I don't know enough about it yet to be comfortable with it either.

Anyway, Lastpass does look like the most promising option. Thanks for the suggestion!

---

### Post by erawk on 2008-11-18
Yeah you should take a read at their FAQ's... they answer a lot of those questions and explain it all in detail. True, its not open souce, but its freeware, the next best thing... and it helps me stay working on my linux os rather than windoze, which is what i want.

> **Do you use a salted hash for login purposes?**
*Yes, we first do a 'salt' of your LastPass password with your username on the client side (on your computer, LastPass never gets your password), then server side we pull a second 256 bit random hex-hash salt from the database, use that to make a salted hash which is compared to what's stored in the database. This is beyond overkill but we want to store nothing that can even theoretically be used to do a dictionary attack against password hashes if LastPass' servers were somehow compromised. We hope having nothing of value makes us less of a target, and that by taking every conceivable caution we can think of makes you more safe.*

**What encryption is being used?**
*AES utilizing 256-bit keys. AES-256 is accepted by the US Government for protecting TOP SECRET data. AES is implemented in JavaScript for the LastPass.com website, and in C++ for speed in the Internet Explorer and Firefox plug-ins. This is important because your sensitive data is always encrypted and decrypted locally on _your computer_ before being synchronized. Your master password never leaves your computer and your key never leaves your computer. No one at LastPass (or anywhere else) can decrypt your data without you giving up your password (we will never ask you for it). Your key is created by taking a SHA-256 hash of your password. When you login, we make a hash of your username concatenated with your password, and that hash is what's sent to verify if you can download your encrypted data.*

---

### Post by robinpaschal on 2010-09-27
Nice software....Reducing my seconds to fill up forms..

---

### Post by stimpyaw on 2012-10-14
I too want the same thing with Roboform to work on Ubuntu, my only work around is to purchase the Windows app and use my BlackBerry Torch 9810. I also install the Roboform app to my BlackBerry and then copy the "user" folder (the Roboform storage folder in 'My Documents' on my PC) from my PC to my BlackBerry Roboforms "user" folder. This is a work around and it comes in handy when I'm using my Ubuntu laptop. Until Roboforms makes a Linux, Ubuntu version this works a lot better then using an encrypted spreadsheet or a txt file too. I just wish more software companies would take a better look at Linux and Ubuntu for that matter.  I hope my work around can help, they have a iPhone and Android app too, so post back if my work around helps you.

---

### Post by nothingspecial on 2012-10-14
Old thread.

Closed.

---

