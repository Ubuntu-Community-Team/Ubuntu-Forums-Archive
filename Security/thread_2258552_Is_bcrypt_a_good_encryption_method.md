---
title: "Is bcrypt a good encryption method?"
date: 2014-12-28
forum: Security
---

### Post by mikodo on 2014-12-28
Hi.

I have an aversion to encrypting my ~.  Don't ask why, because I can't give a reasonable explanation why not. C'est la vie!

I have only this one computer, a desktop, with only Xubuntu installed, well, I do still have a working Ubuntu 10.04 partition for posterity, but I use it for nothing and it will be gone in a month.

I keep a file with all my passwords, banking and work logins, (well everything, including non-password data about personal stuff) and encrypt it with bcrypt. [Ubuntu manpage for bcrypt.]("http://manpages.ubuntu.com/manpages/precise/en/man1/bcrypt.1.html")

I have a 16 mixed character password that uses an even mixture of numbers, characters, lower and upper case letters, with no repeats. One I will never forget.

Besides regular backups to other drives, that I do now, I am thinking of using a Cloud Backup Service, just for this file ...

So security experts, is using bcrypt satisfactory for this, if my computer is stolen (break in). Can I feel assured that the file is safe with it?
...
Edit: I guess this is still a pretty good encryption method [Wikipedia article on it states:]("https://en.wikipedia.org/wiki/Blowfish_%28cipher%29")

*"Blowfish provides a good encryption rate in software and no effective [cryptanalysis]("https://en.wikipedia.org/wiki/Cryptanalysis") of it has been found to date"*.

Now, if I could find a easy way to use twofish, I would use it.

Thank you.

[URL="https://en.wikipedia.org/wiki/Blowfish_%28cipher%29"]
[/URL]

---

### Post by bashiergui on 2014-12-29
[QUOTE=mikodo]I have an aversion to encrypting my ~. Don't ask why, because I can't give a reasonable explanation why not.[/QUOTE]It's perfectly reasonable to have that aversion. There are always costs with security. If you encrypt home and lose the password then you're hosed. Each user must decide if the risk is worth the benefit.

As for bcrypt, yes it's still decent. It can be a computationally expensive algorithm (assuming you've chosen an expensive iteration count). It is designed to take a long time to calculate, thus limiting the number of attempts an attacker can make. See this quote from [this]("http://arstechnica.com/security/2012/12/25-gpu-cluster-cracks-every-standard-windows-password-in-6-hours/") link:> As a result, the new cluster, even with its four-fold increase in speed, can make only 71,000 guesses against Bcrypt and 364,000 guesses against SHA512crypt.The result is that it will take an attacker much longer to crack a bcrypt password. Looking at [this]("http://www.lockdown.co.uk/?pg=combi&s=articles#Classes") link for speed of cracking, you can see an 8-character password would take roughly 2000 years to crack at that rate. A 16 character password would take much longer.

---

### Post by mikodo on 2014-12-29
Thank you, bashergui. I had seen the first link before, (I read it slower this time). I had not seen the second link.

I have not used a high iteration count. I have used the default number of overwrites (3) of the input files. What would you deem an "expensive" number of overwrites?

---

### Post by untrustytahr on 2014-12-29
> **mikodo said:**
> 

Now, if I could find a easy way to use twofish, I would use it.
[URL="https://en.wikipedia.org/wiki/Blowfish_%28cipher%29"]
[/URL]

```
gpg -c --cipher-algo TWOFISH file.txt
```
Will symmetrically encrypt using twofish.

---

### Post by mikodo on 2014-12-29
> **untrustytahr said:**
> ```
gpg -c --cipher-algo TWOFISH file.txt
```
Will symmetrically encrypt using twofish.
Why, thank you.

It's past 04:00 here, and I just looked and saw your post. I will look into your command later.  

g'nite.

---

### Post by mikodo on 2014-12-29
> **untrustytahr said:**
> ```
gpg -c --cipher-algo TWOFISH file.txt
```
Will symmetrically encrypt using twofish.
Well, thanks again, for taking the time, to share this. But, I did some preliminary reading about twofish and it is way, way over my head. I need something easy like bcrypt, to ease my way into retirement, and what comes with that! I think I will stay with bcrypt. It is simple enough for me, and seemingly offers enough security, against any B&E dudes, who are only going to sell the puter for 20 bucks to their friends any ways.

I am going to look into backing up the small encrypted file to a Cloud Storage medium, just for the added peace of mind it will bring me.

Thanks.

---

### Post by bashiergui on 2014-12-29
> I am going to look into backing up the small encrypted file to a Cloud Storage medium, just for the added peace of mind it will bring me.That is a good idea. Backing up data that is already encrypted is the best approach. Then if the cloud service has a breach your data can't be stolen. Just be sure to keep the key/password and the recovery key (if there is one) out of the same cloud instance.

---

### Post by mikodo on 2014-12-29
> **bashiergui said:**
> That is a good idea. Backing up data that is already encrypted is the best approach. Then if the cloud service has a breach your data can't be stolen. Just be sure to keep the key/password and the recovery key (if there is one) out of the same cloud instance.
Okay.

Thanks, for all the advice!

---

### Post by open2reason on 2014-12-30
mikodo, 
a short link to work done by Stanford University network engineers discussing the length vs complexity debate about pass phrase strength [http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/](http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/) via [http://itservices.stanford.edu/service/accounts/passwords](http://itservices.stanford.edu/service/accounts/passwords)  would suggest that wherever possible pass phrase length contributes more to security that complexity when selecting a pass phrases to deploy.

---

### Post by HermanAB on 2014-12-30
Actually, a better solution is to use Keepass, KeepassX and KeepassDroid.  You can save the database on Dropbox or Copy and then access the data from all your devices, be they Windows, Linux, Mac or Android.

---

### Post by mikodo on 2014-12-30
> **open2reason said:**
> mikodo, 
a short link to work done by Stanford University network engineers discussing the length vs complexity debate about pass phrase strength [http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/](http://arstechnica.com/security/2014/04/stanfords-password-policy-shuns-one-size-fits-all-security/) via [http://itservices.stanford.edu/service/accounts/passwords](http://itservices.stanford.edu/service/accounts/passwords)  would suggest that wherever possible pass phrase length contributes more to security that complexity when selecting a pass phrases to deploy.Thanks, open2reason!

More information, for me to incorporate into my secure password. I appreciate the advice.

> **HermanAB said:**
> Actually, a better solution is to use Keepass, KeepassX and KeepassDroid.  You can save the database on Dropbox or Copy and then access the data from all your devices, be they Windows, Linux, Mac or Android.Hi Herman. It is nice to hear from you again.

I have only the desktop that I use. I quickly looked at Keepass, KeepassX and KeepassDroid, and I think KeepassX, looks promising. I need to save more than just passwords, in this little 15.4 Kb file, (I just checked it's present size). [KeepassX, on their page indicates,]("https://www.keepassx.org/") that I can save "comments". That might work well. That it uses AES or Twofish encryption, is better than  me trying figure that out myself. Also, your mentioned comment about saving the database on Dropbox or Copy, might be a viable Cloud Storage solution.

And who knows, I might join the 21st Century wireless age, and get a smart phone. Especially, if I pursue a business idea, after retirement.

Thank you.

Edit: I have decided I am going to try [KeePass2.]("http://keepass.info/help/base/security.html") It's in the repos. It supposedly has an area for "notes", additional functions and plugins, and increased security measures. I might as well learn, what all it provides now.

---

