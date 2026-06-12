---
title: "How do you manage your passwords?"
date: 2014-11-19
forum: Security
---

### Post by SagaciousKJB on 2014-11-19
Well I've been relying on a custom program for a while now.  I just stick the binary on a thumbstick, and then I can access my password file from an encrypted format.  Well recently in the spirit of not leaving good enough alone, I upgraded it from using my own custom encryption algorithm ( whose strength I really can't say for sure was strong or not, not a cryptanalyst ) and opted to use blowfish with the OpenSSL libraries.

Well, problem...  I can't go and install OpenSSL on every computer that I want to use the program on.  Kind of defeats the purpose, since I could just install one of many available password managers that are much better than mine in virtually all regards. :/

So what would you do?  Use your own questionable encryption routine, or a known standard?

The give and take is obvious: More chance my passwords can be cracked by someone who steals my thumbdrive, but much more convenience and accessibility; or pretty much the best security I can get for them, but with the hassle of having to install additional software on a computer I may not have permission to install software on--both literally and in terms of OS permission policies.

The reason not being able to install software on the computer being used is such a big deal is because I work on a lot of public computers or at friend's, school, etc--thus the need for portable and secure password management.  Just in a lot of places where I tend to need access to my online accounts but can't really just install anything I want on the computer in question.

I think I might just end up getting one of those hardware-encrypted thumbsticks, but I can't really remember the name of the one I really liked.  Plus I hate paying for anything.  Someone suggested something for an Android, but I don't even have a smartphone currently, and would rather be able to copy and paste my passes.

A part of me thinks I'm being way too cautious--that just having even my own custom encryption routine is probably going to keep 99.9x% of the population away from sensitive material. ...and the whole "Who would care enough about me to try that hard?" thing.  Some people suggest I'm already overly-cautious by using different passwords for everything at all.

---

### Post by ecophobia on 2014-11-19
Iron key used to be good, cross platform etc. Imation has acquired it, so I have no experienced with them after the acquisition happened.

---

### Post by untrustytahr on 2014-11-19
Just my opinion... but in your situation I don't think it would really matter.  Strength & implementation of algorithm only matters if someone is "attacking the math".  Your use case is on "public" computers.  A hacker would be wasting time trying to beat the math... it would be easier to attack the endpoint by installing a keylogger to get the passphrase for the whole file/database and then get the database from you.

---

### Post by untrustytahr on 2014-11-20
Speak of the devil.... an article just appeared in Ars... 
[http://arstechnica.com/security/2014/11/citadel-attackers-aim-to-steal-victims-master-passwords/](http://arstechnica.com/security/2014/11/citadel-attackers-aim-to-steal-victims-master-passwords/)

Take note of the last sentence.

I personally dont enter passwords on computers that I dont have a high trust degree in.  If I absolutly needed to use the machine I would boot up from a live image with with my password manger on it.

---

### Post by SagaciousKJB on 2014-11-21
> **untrustytahr said:**
> Speak of the devil.... an article just appeared in Ars... 
[http://arstechnica.com/security/2014/11/citadel-attackers-aim-to-steal-victims-master-passwords/](http://arstechnica.com/security/2014/11/citadel-attackers-aim-to-steal-victims-master-passwords/)

Take note of the last sentence.

I personally dont enter passwords on computers that I dont have a high trust degree in.  If I absolutly needed to use the machine I would boot up from a live image with with my password manger on it.

Interesting, tempts me to feel more secure in obscurity...  Using my own custom program, it's unlikely some malware is going to target it versus using a more popular one like KeePass.

Yeah that's an interesting thought too.  I use to boot up BackTrack off of school computers because I didn't know what kind of "snoop" software they had installed.  So I guess using the same strategy I could just make USB stick with a live system on it--or a CD since much of the time the computers I work on don't even boot off USB.  Plus then I could install whatever libraries I wanted.

I think I might just adopt your method.  Now if only more computers booted off USB I wouldn't have to carry a CD around with me all the time.  Maybe I could find a distro that's small enough to fit on one of those 3" CDs that I could keep in my wallet or something.

---

### Post by open2reason on 2014-11-21
Bruce Schneier (creator of Password Safe) shares his thoughts with others on his blog [https://www.schneier.com/blog/archives/2014/11/citadel_malware.html](https://www.schneier.com/blog/archives/2014/11/citadel_malware.html)

---

### Post by SagaciousKJB on 2014-11-21
> **open2reason said:**
> Bruce Schneier (creator of Password Safe) shares his thoughts with others on his blog [https://www.schneier.com/blog/archives/2014/11/citadel_malware.html](https://www.schneier.com/blog/archives/2014/11/citadel_malware.html)

Heh except Bruce himself doesn't weigh in.

This is the scenario that I imagine...

I have a hole in my pocket I don't know about, my thumbdrive falls on the street.  Someone picks it up and sees that there's a file named "passwords" and figure they have to take a list.  Then they realize it's encrypted, and give up--unless they don't feel like giving up and want to try to decrypt it.

I think it would be pretttttty unlikely for them to crack it.  I mean, let's assume I leave my program's source on the thumbstick and they can study my algorithm to its full extent, I still doubt they would even have enough data to crack it.

Would you really worry about a person trying to crack your random password file they found on the street?  Assuming they know nothing about who you are and their only interest is curiosity?

---

### Post by seabird22 on 2014-11-21
I  use lastpass with two-form factor authentication on laptop and smartphone. I would never log onto lastpass on an any hardware other than mine. It costs $12.00 per year for the smartphone app. There is not much talk here about lastpass and want to know what your thoughts are, from a security standpoint and otherwise.

---

### Post by bashiergui on 2014-11-21
> Would you really worry about a person trying to crack your random password file they found on the street? Assuming they know nothing about who you are and their only interest is curiosity?To prevent random curiosity, yes. The bar is extremely low with all the flat files of passwords out there, and easily obtainable rainbow tables for passwords up to 10 characters. If your method is anything other than hashing crappy passwords, even the moderately curious will pass it by. 

That said, friends don't let friends roll their own crypto. If you're not sure if it's good then it's guaranteed to be bad.

---

### Post by seabird22 on 2014-11-24
I  use lastpass with two-form factor authentication on laptop and smartphone. I would never log onto lastpass on an any hardware other than mine. It costs $12.00 per year for the smartphone app. There is not much talk here about lastpass and want to know what your thoughts are, from a security standpoint and otherwise.


No comment on lastpass huh? :lolflag:  I guess that is a comment in it of itself. I guess a lot of people don't like the idea that it is in the cloud and I can understand that.  I only use it for web logins, not hardware logins. my smartphone app is disabled since my subscription ran out. I think I am going to be looking for another solution. 


thanks.

---

### Post by coldraven on 2014-11-24
Buy two copies (yes, one is a backup) of a really boring book from a charity shop. Something like "Breeding hamsters for fun and profit" :)
Inside the front cover write "If found please return to <your address>".
Inside the back cover write a list of your web-sites.
Then for item X in your list add a number Y, goto page X+Y and use the first five words on line Z as your password. (and maybe add some characters)
You only have to remember the numbers Y and Z and they do not change. Anybody who finds the book would have to try a lot of combinations.
They will also think that you are a sad loser, feel pity, and mail your book back :)

P.S. I would never copy/paste a password on a machine that was not mine. I have seen a web-site that shows you the content of your clipboard, it is very insecure.

---

### Post by leclerc65 on 2014-11-24
Hackers now target Password Managers

[http://thehackernews.com/2014/11/new-citadel-trojan-targets-your.html](http://thehackernews.com/2014/11/new-citadel-trojan-targets-your.html)

---

### Post by mastablasta on 2014-11-25
> **coldraven said:**
> 
P.S. I would never copy/paste a password on a machine that was not mine. I have seen a web-site that shows you the content of your clipboard, it is very insecure.

keepass clears the clipboard I think

> **leclerc65 said:**
> Hackers now target Password Managers

[http://thehackernews.com/2014/11/new-citadel-trojan-targets-your.html](http://thehackernews.com/2014/11/new-citadel-trojan-targets-your.html)

worrying. maybe we need to setup basic Linux desktop in vbox to use kepass in there :-)

---

### Post by HermanAB on 2014-11-25
I use Keepass, KeepassX and KeepassDroid, with the database stored on Dropbox.  That way, I can access my passwords everywhere.

---

### Post by SagaciousKJB on 2014-11-26
> **bashiergui said:**
> To prevent random curiosity, yes. The bar is extremely low with all the flat files of passwords out there, and easily obtainable rainbow tables for passwords up to 10 characters. If your method is anything other than hashing crappy passwords, even the moderately curious will pass it by. 

That said, friends don't let friends roll their own crypto. If you're not sure if it's good then it's guaranteed to be bad.

"Friends don't let friends roll their own crypto."  Heh I like that, didn't see this post before.

Well all is well I took all the sound advice, and upgraded it to use OpenSSL.  It still uses my cipher too but to be honest that's mostly out of laziness, it operates as a stream cipher but it was also a convenient frame to do the input/output with too, the program just now "encapsulates" it in AES-128 afterward.  The OpenSSL library isn't as well documented as I would have hoped, but holy gnu was it more obvious than Libgrcrypt.

Herman that's an interesting approach.

---

### Post by haqking on 2014-11-26
Write them down, no one breaks into your house to look for passwords ;-)

It used to be the 'no-no' of security, do not write your passwords down. To be honest, at home there is no issue with it unless you don't want your partner or child accessing something but easy to secure a notepad than protect from malicious online or software attacks.

---

### Post by slickymaster on 2014-11-26
> **HermanAB said:**
> I use Keepass, KeepassX and KeepassDroid, with the database stored on Dropbox.  That way, I can access my passwords everywhere.

Same here. The only difference being that I keep my database stored in a encrypted USB stick.

---

### Post by HermanAB on 2014-11-27
" encrypted USB stick. "
The Keepass database is encrypted, but there is no such thing as too much encryption I suppose.

The reason I use dropbox, is that it is hard to plug a USB thingy into my phone.

---

### Post by slickymaster on 2014-11-27
> **HermanAB said:**
> " encrypted USB stick. "
The Keepass database is encrypted, but there is no such thing as too much encryption I suppose.

The reason I use dropbox, is that it is hard to plug a USB thingy into my phone.

:p

I have a very ancient phone. Only calls and text messages capabilities.

---

