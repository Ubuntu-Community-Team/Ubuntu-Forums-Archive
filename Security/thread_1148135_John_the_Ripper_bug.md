---
title: "John the Ripper bug?"
date: 2009-05-04
forum: Security
---

### Post by usopenplayer on 2009-05-04
Hey guys, I'm running Ubuntu 9.04 and downloaded john the ripper via synaptic to see if my password was secure...

I ran the following commands
$ sudo unshadow /etc/passwd /etc/shadow > test.txt
$ sudo john test.txt
it then tells me
"No password hashes loaded"
I checked the documentation and it says

> **Q**: Why doesn't John load my password file? It says "No password hashes loaded". 
**A**: Your password file might be shadowed. You need to get both /etc/passwd and the shadow file (typically /etc/shadow), and combine them into one file for use with John. Please refer to [EXAMPLES]("http://www.openwall.com/john/doc/EXAMPLES.shtml"). 
**A**: All of the password hashes found in the file (that John recognizes as such) might be already cracked by previous invocations of John. 
**A**: The file you're trying to run John on might in fact not be a password file at all. 
**A**: Your command line syntax might be wrong, resulting in John trying to load a wrong file. 
**A**: Your password file format or hash type(s) might not be supported by John, or at least by the version and build of John that you're using. If you're positive that this is the case, you may want to check the contributed resources list on John the Ripper homepage for a suitable patch and, if unsuccessful with that, post a note to the mailing list (see [CONTACT]("http://www.openwall.com/john/doc/CONTACT.shtml")) including a sample password file line that John does not load (please make sure that the password is already changed by the time you post). 


I know the syntax is correct, I know the file is not shadowed, the file IS a password file, I actually tried multiple different hash functions and JTR would not recognize the file... I checked the website and the readme and cannot seem to find any useful information... does anyone know what could be going on here?

---

### Post by ooobooontooo on 2009-05-04
From what I remember of using john, just the unshadowed file of passwd and shadow isn't the correct format that john requires. I think it needed to be in format "<user>:<hash>". Can you try doing that instead of including all that extra stuff like the shell info and all that?

EDIT: If john says no hash loaded, that means you're file has bad syntax...I remember struggling for a while before getting it right.
EDIT: Also, it could be a weird thing with permissions. Try to change the permissions to your password file to all-readable (make sure no one else can access your computer while doing this though I'm sure you already knew that), and try running john on that, though I'm not exactly sure why this would be considering you ran john with sudo...but try it anyway.

---

### Post by usopenplayer on 2009-05-04
> **ooobooontooo said:**
> From what I remember of using john, just the unshadowed file of passwd and shadow isn't the correct format that john requires. I think it needed to be in format "<user>:<hash>". Can you try doing that instead of including all that extra stuff like the shell info and all that?

EDIT: If john says no hash loaded, that means you're file has bad syntax...I remember struggling for a while before getting it right.
EDIT: Also, it could be a weird thing with permissions. Try to change the permissions to your password file to all-readable (make sure no one else can access your computer while doing this though I'm sure you already knew that), and try running john on that, though I'm not exactly sure why this would be considering you ran john with sudo...but try it anyway.


I tried this and John still did not recognize the hashes, I however manually entered an MD5 hash using the syntax you provided  and I finally got John to read it however I do not think it is actually working... I made 3 test accounts with very simple passwords (like: password) and John comes up and says that it has detected 6 password hashes and has been running for 10 minutes now with no results, I'm not sure if I am just being impatient but I would have expected John to guess these passwords in under 5 seconds =P

---

### Post by bodhi.zazen on 2009-05-04
John the ripper doe snot support sha-512 hashes.

The numbers you are referring to, 
[FONT=monospace]
[/FONT]$1$ == md5[FONT=monospace]
[/FONT]$5$ == sha256[FONT=monospace]
[/FONT]$6$ == sha512

> Out of the box, John supports (and autodetects) the following Unix crypt(3) hash types: traditional and double-length DES-based, BSDI extended DES-based, FreeBSD MD5-based (now also used on Linux and in Cisco IOS), and OpenBSD Blowfish-based (now also used on some Linux distributions). Also supported out of the box are Kerberos/AFS and Windows LM (DES-based) hashes.

There may  be patches for john, but I could not find one.

You would need to convert your hashes, find a patch, or try a different password checker.

---

### Post by ooobooontooo on 2009-05-04
@ usopenplayer

About john being slow. That's most likely because you put john to an incremental search, which basically tries every single possibility until it gets to your password. If you provide it a wordlist, it will be much faster (if it contains your password).

---

### Post by usopenplayer on 2009-05-04
> **ooobooontooo said:**
> @ usopenplayer

About john being slow. That's most likely because you put john to an incremental search, which basically tries every single possibility until it gets to your password. If you provide it a wordlist, it will be much faster (if it contains your password).


I tried both incremental and wordlist...I'm not totally hopeless with this stuff :D I was confused because I was following some tutorials that where made specifically for Ubuntu...and it didn't work for me, I wasn't sure if it was a bug in 9.04 or if they changed the hash function for the password.... it would appear that the latter is true.

does anyone have any reccomendations for a cracker more comprehensive than JTR?

---

### Post by ooobooontooo on 2009-05-04
JTR is definitely one of the most comprehensive crackers out there. The other alternative that comes to mind is Cain and Abel, but that's only for Windows machines...other than that you might have to go to hash-specific crackers.

---

### Post by raymondh on 2009-05-04
> **ooobooontooo said:**
> JTR is definitely one of the most comprehensive crackers out there.

+1 on that

---

### Post by peridot on 2009-05-22
> **bodhi.zazen said:**
> John the ripper doe snot support sha-512 hashes.

The numbers you are referring to, 
[FONT=monospace]
[/FONT]$1$ == md5[FONT=monospace]
[/FONT]$5$ == sha256[FONT=monospace]
[/FONT]$6$ == sha512



There may  be patches for john, but I could not find one.

You would need to convert your hashes, find a patch, or try a different password checker.

Does anyone know an alternative to use?

---

### Post by ooobooontooo on 2009-05-22
You could try [Hash Cracker]("http://www.ohloh.net/p/hash-cracker"). I found it while browsing (Note: I never used it myself so I don't know how well/reliable it is). It claims it can brute force sha-512, but from what I know of encryption...cracking sha-512 will take a LONG time unless you have a wordlist...

---

### Post by Dr Small on 2009-05-22
> **ooobooontooo said:**
> You could try [Hash Cracker]("http://www.ohloh.net/p/hash-cracker"). I found it while browsing (Note: I never used it myself so I don't know how well/reliable it is). It claims it can brute force sha-512, but from what I know of encryption...cracking sha-512 will take a LONG time unless you have a wordlist...
Every cracker I know of, uses a wordlist (including John the Ripper). Incremental mode is what generates random stuff to try to crack the password. That puts your possibility of cracking the hash up to years, or never.

---

### Post by ooobooontooo on 2009-05-22
> **Dr Small said:**
> Every cracker I know of, uses a wordlist (including John the Ripper). Incremental mode is what generates random stuff to try to crack the password. That puts your possibility of cracking the hash up to years, or never.

Not true. JTR is able to crack passwords of average length (6-7) characters in incremental mode within the day from my experience. (Especially if you know which characters the password used is limited to)

---

### Post by Dr Small on 2009-05-22
> **ooobooontooo said:**
> Not true. JTR is able to crack passwords of average length (6-7) characters in incremental mode within the day from my experience. (Especially if you know which characters the password used is limited to)
I was speaking in the sense of a very strong password (10+ character). It could take John a very long time to crack it, and if it used special symbols, or random capitalization, it greatly reduces your odds of ever cracking it.

I know that it can crack passwords in Incremental mode, I am not denying this, but if the hash is from a very strong password, the chance of it ever being cracked is slim.

Dr Small

---

### Post by ooobooontooo on 2009-05-23
> **Dr Small said:**
> I was speaking in the sense of a very strong password (10+ character). It could take John a very long time to crack it, and if it used special symbols, or random capitalization, it greatly reduces your odds of ever cracking it.

I know that it can crack passwords in Incremental mode, I am not denying this, but if the hash is from a very strong password, the chance of it ever being cracked is slim.

Dr Small

Agreed. I'm sorry if my comment seemed aggressive in any way.

---

### Post by Dr Small on 2009-05-23
> **ooobooontooo said:**
> Agreed. I'm sorry if my comment seemed aggressive in any way.
Well, it did, but I didn't hold it against you... It's fine :)

---

### Post by ooobooontooo on 2009-05-23
> **Dr Small said:**
> Well, it did, but I didn't hold it against you... It's fine :)

Fantastic. :D

---

### Post by JohnTwenty on 2009-06-18
Hi,
I noticed that if I set my password using ubuntu's user dialog, I get MD5 encryption. If I use passwd in my terminal, I get SHA-512 encryption.
Is the same password safer, just because the encryption is better?

JohnTwenty

---

### Post by ooobooontooo on 2009-06-22
lol you should've probably created a new thread for this...

Anyway, sha-512 and md5 are both "uncrackable" in theory I believe, meaning given a hash you can't revert it to the original password with an algorithm. Because they are both one-way hashing algorithms, both are pretty safe, especially if you include caps, numbers, and signs in your password.

However, if given the choice I would probably pick sha-512 over md5. I believe finding collisions (guessing at passwords) for sha-512 is much harder than it is for md5. So I guess go for the password command in  the terminal if you have the choice...but really...you shouldn't need to worry as long as your shadow file's (/etc/shadow) permissions are set correctly and you use a reasonably difficult password. What you should really be worried about is -> [this]("http://xkcd.com/538/")

That's rather strange though...I didn't know ubuntu employed 2 different hashing algorithms solely based on where you enter the password. Are you sure you didn't set any specific options?

---

### Post by JohnTwenty on 2009-06-22
Well thanks for your reply,

as for your question: No, I didn't use any specific options. I have read an article on John The Ripper and tried to crack my user password in Ubuntu 8.10. It did the job in 1 second. That was kinda scary. Then I changed my password using the termional (passwd) and tried again to crack it to see if the new one was any better. I then got the message that JTR couldn't find any hashes. After a little research I found that JTR does not support sha-512. 
So I was wandering if sha-512 was generally more secure (if there were no other crackers that do support sha-512, that is)

JohnTwenty

---

### Post by x3roconf on 2009-06-23
> **ooobooontooo said:**
> JTR is definitely one of the most comprehensive crackers out there. The other alternative that comes to mind is Cain and Abel, but that's only for Windows machines...other than that you might have to go to hash-specific crackers.

Really? John doesn't even support mysql hashes or raw md5 hashes without patching sources!

---

### Post by JohnTwenty on 2009-06-25
I just noticed that it is only easy peasy (Ubuntu 8.10) on my Asus eeePC 901 that behaves this way. I just tested it on another machine running Ubuntu 8.04 an there passwd does not create an sha-512 hash, but still an ordinary md5 one.

JohnTwenty

---

### Post by ooobooontooo on 2009-06-26
Hi. Sorry for the delay of my reply. That's interesting...different encryptions based on where you put your password...

Anyway, if john can crack your password in a second...that's not good...Try adding numbers and special signs (/, $, %, etc.) to your password so that it doesn't fall under any wordlist; then the only way for john to crack your password would be through incremental mode, and that takes a while especially if you password is longer than 6 characters. However, you shouldn't worry too much about someone 'cracking' your password as long as your shadow file remains hidden. What you should be more worried about is social engineering. Because you said john cracked your password in a second, I'm going to assume it was a very easy password to guess, so you might want to look into changing that...

As for crackers for the sha-2 family (including sha-512), I believe there was a research group that managed to crack hashes with 44% accuracy...but it took like 22 steps or something. I would reference the article, but I kind of forgot where the site was. Anyway, I don't know of any common crackers that will handle the sha-2 family, so you should be safe with it. But remember to invest in a more secure password so as not to get socially reverse engineered.

Have Fun.

---

### Post by JohnTwenty on 2009-06-27
Thanks for your reply.

Yes, I know that my password was extremely weak (it was just my first name and my username was very similar).

You say I needn't worry as long as nobody could read my shadow file. But that is not too difficult to do. Simply type 'c' in GRUB and it will drop into a command shell, where you can do a simple cat /etc/shadow and thats it. (You would of course have to copy the hashes by hand, but other than that there are no problems)

I know that I could protect GRUB by using a password and use hiddenmenu, but for reasons of convenience only very few people do that.

JohnTwenty

---

### Post by ooobooontooo on 2009-06-27
> **JohnTwenty said:**
> Thanks for your reply.

Yes, I know that my password was extremely weak (it was just my first name and my username was very similar).

You say I needn't worry as long as nobody could read my shadow file. But that is not too difficult to do. Simply type 'c' in GRUB and it will drop into a command shell, where you can do a simple cat /etc/shadow and thats it. (You would of course have to copy the hashes by hand, but other than that there are no problems)

I know that I could protect GRUB by using a password and use hiddenmenu, but for reasons of convenience only very few people do that.

JohnTwenty

Agreed! However, I was speaking of the case in which people would only have remote access to your computer. If a person has physical access to your computer, you can only truly do so much to protect your computer. I could just pop a livecd in and try to look at your shadow file from there...I suppose encrypting your hard drive might be one solution...blah still, a person would probably just take your hard drive (or your computer) while he's at it...Anyway, don't worry too much over shadow file. That is my advice to you.

@x3roconf
Sorry. Didn't see your post before. Well my initial response to your statement would be that similar to how firefox gets a lot of its power from add-ons, john gets a lot of its powers from patches that other users have provided. Also, I really don't know of more versatile crackers than john. If you could please reference a cracker that has more modes than john, I would be grateful.

---

### Post by zeealpal on 2010-05-19
Lol i know this is kinda late, and off topic in relation to JTH, but there is an insanely fast M5D and other: 
MD5
md5(md5($pass))
md5(md5($pass).$salt)
MySQL
MD4
NTLM

And it uses OpenCL on your graphics card. On Ubuntu 10.04 it was taking me on average 5-8 mins to crack an 8 character random alphanumeric with caps hash. Or in mny case 1023100 hash/s second.or about 1 million. Thats on a ATI 5850 on ubuntu with catalyst and opencl drivers

---

