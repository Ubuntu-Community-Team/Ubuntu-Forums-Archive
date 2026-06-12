---
title: "How to prevent zip file corruption?"
date: 2011-06-21
forum: The Cafe
---

### Post by sudoer541 on 2011-06-21
I am trying to encrypt a folder using 7-Zip (Windows version) and I always password protect my files with AES 256 algorithm . Can people actually break this code, or its secure (I'm kinda worried)? 
I always add a second layer of security to my files, by changing the extension of the encrypted zipped folder (such as:  .mp3) and I add the fake .mp3 to another zipped encrypted folder. Will this corrupt the folders or the content? :o

EDIT: I do the exact reverse when I want to open my files.

---

### Post by Artemis3 on 2011-06-22
So long as you stick with AES, they should be safe provided you use a long enough password, 12+

You can increase security a little by reducing compression (make the file bigger).

Don't see any point in renaming stuff, 7z has the option of encrypting file names.

And the password should be unique of course.

To prevent corruption you can use external redundancy tools such as par2.

---

### Post by varunendra on 2011-06-22
> **sudoer541 said:**
> I am trying to encrypt a folder using 7-Zip (Windows version) and I always password protect my files with AES 256 algorithm . Can people actually break this code, or its secure (I'm kinda worried)?
For a rough idea of the reliability of AES256 security, read [this]("https://help.ubuntu.com/community/EncryptedFilesystemHowto#How%20many%20bits%20should%20the%20key%20used%20by%20the%20algorithm%20have?").
Excerpt from the above link:
> A 256bit key gives about 1077 (a 1 followed by 77 zeros) different keys while a 128bit key has "only" about 1038 (a 1 followed by 38 zeros). At the moment a typical PC can generate and test about 3*105 (3 followed by 5 zeros) keys per second. So breaking a 128bit key would take a single average PC about 1025 years (1 followed by 25 zeros), which is longer than the universe exists. That should be secure enough for most users. 
To understand how secure 128 bit keys are, you may read [this analogy]("http://www.interesting-people.org/archives/interesting-people/200607/msg00058.html") by Jon Callas:


“Imagine  a computer that is the size of a grain of sand that can test keys  against some encrypted data. Also imagine that it can test a key in the  amount of time it takes light to cross it. Then consider a cluster of  these computers, so many that if you covered the earth with them, they  would cover the whole planet to the height of 1 meter. The cluster of  computers would crack a 128-bit key on average in 1,000 years.”


Even  if you don't believe that the NSA has another planet devoted to key  cracking, you still may want to use a longer key. If a weakness in your  chosen crypto-module is found, it may limit the keyspace that needs to  be tested, and you will then have an effectivly shorter key. Using a 256  bit key will keep your data secure much longer if that should happen. 

Although the above analogy by Jon Callas was made in 2006, and computer speeds have increased significantly since then, I don't think it is gonna make much difference when it comes to break a AES256 encryption :). Hope it helps reducing your worries.

> **sudoer541 said:**
> I always add a second layer of security to my files, by changing the  extension of the encrypted zipped folder (such as:  .mp3) and I add the  fake .mp3 to another zipped encrypted folder. Will this corrupt the  folders or the content? :eek:
Given the strength of above security with a lengthy passkey (I'd say, 9+ would be sufficient!) I think you don't need that additional security layer unless the passkey is too obvious or you are sure the CIA is after your files ;).. Although it definitely increases the security (but only if you use different passkey in second archive, else it's useless since the first thing a cracker (if any) would do is to try the same cracked passkey on the second layer too).

If you still want to use double encryption, just make sure to use "store" mode in next archive since the first one is already compressed. This will save your time. But frankly, you really don't need this if your passkey is long enough and difficult to guess.

And yeah, it won't corrupt your files, no matter how many layers you use. But be informed that some filesystems may report file copy/extraction errors in case of very long filenames (including their path), or if the names contain characters not supported by that filesystem (as sometimes happens with archives created in linux ext filesystem and extracted on a fat or ntfs partition). This indicates filesystem incompatibility, not necessarily a corrupt file!

Hope I didn't confuse you.

---

### Post by DZ* on 2011-06-22
AES strength itself seems to be of very little relevance when all that's needed for decryption is a password.

If I encrypt a text file
```
echo "[COLOR="Red"]Bah[/COLOR]" > text.txt
``` 
with AES-256 using a a number between 0 and 1000 for a passphrase:
```
gpg --cipher-algo AES256 -c text.txt
```
then, provided that knowledge about the chosen passphrase, it takes under 4 sec to bruteforce it on a meager laptop
```
time bash ./decr.sh 2> /dev/null > out; cat out
real    0m4.804s
[COLOR="Red"]Bah[/COLOR]
```

```
cat decr.sh

declare -i i=0 n=1000; while [ $i -lt $n ]; do
 echo $i | gpg --passphrase-fd=0 --no-tty -d text.txt.gpg
 let i+=1
done
```

---

### Post by sudoer541 on 2011-06-22
> **varunendra said:**
> For a rough idea of the reliability of AES256 security, read [this]("https://help.ubuntu.com/community/EncryptedFilesystemHowto#How%20many%20bits%20should%20the%20key%20used%20by%20the%20algorithm%20have?").
Excerpt from the above link:


Although the above analogy by Jon Callas was made in 2006, and computer speeds have increased significantly since then, I don't think it is gonna make much difference when it comes to break a AES256 encryption :). Hope it helps reducing your worries.


Given the strength of above security with a lengthy passkey (I'd say, 9+ would be sufficient!) I think you don't need that additional security layer unless the passkey is too obvious or you are sure the CIA is after your files ;).. Although it definitely increases the security (but only if you use different passkey in second archive, else it's useless since the first thing a cracker (if any) would do is to try the same cracked passkey on the second layer too).

If you still want to use double encryption, just make sure to use "store" mode in next archive since the first one is already compressed. This will save your time. But frankly, you really don't need this if your passkey is long enough and difficult to guess.

And yeah, it won't corrupt your files, no matter how many layers you use. But be informed that some filesystems may report file copy/extraction errors in case of very long filenames (including their path), or if the names contain characters not supported by that filesystem (as sometimes happens with archives created in linux ext filesystem and extracted on a fat or ntfs partition). This indicates filesystem incompatibility, not necessarily a corrupt file!

Hope I didn't confuse you.

This makes sense.  And LOL the contents of  my encrypted folders are "Bank statements" for those who are wondering LOL. 
Thanks!

---

### Post by doas777 on 2011-06-22
> **DZ* said:**
> AES strength itself seems to be of very little relevance when all that's needed for decryption is a password.

If I encrypt a text file
```
echo "[COLOR=Red]Bah[/COLOR]" > text.txt
```with AES-256 using a a number between 0 and 1000 for a passphrase:
```
gpg --cipher-algo AES256 -c text.txt
```then, provided that knowledge about the chosen passphrase, it takes under 4 sec to bruteforce it on a meager laptop
```
time bash ./decr.sh 2> /dev/null > out; cat out
real    0m4.804s
[COLOR=Red]Bah[/COLOR]
``````
cat decr.sh

declare -i i=0 n=1000; while [ $i -lt $n ]; do
 echo $i | gpg --passphrase-fd=0 --no-tty -d text.txt.gpg
 let i+=1
done
```

yes, if you limit yourself to (3^9) + 1 options, bruteforcing is easy. that is not an argument about AES however, but one regarding strong password use.
a 8-digit 4-factor password has a complexity of 64^8, a much larger number. 281474976710656 possible combinations vs 19683 in your example, and assuming a linear time scale, would take 14333179383 times longer than your sample did, or in this case 15925755 hours (1818 years) using your 4second finding.

---

### Post by doas777 on 2011-06-22
> **sudoer541 said:**
> This makes sense.  And LOL the contents of  my encrypted folders are "Bank statements" for those who are wondering LOL. 
Thanks!

[Truecrypt]("http://www.truecrypt.org/") FTW.

---

### Post by jerenept on 2011-06-22
> **doas777 said:**
> [Truecrypt]("http://www.truecrypt.org/") FTW.

I use AES-Twofish-Serpent with truecrypt. Never, ever gonna be cracked.

---

### Post by DZ* on 2011-06-22
> **doas777 said:**
> yes, if you limit yourself to (3^9) + 1 options, bruteforcing is easy. that is not an argument about AES however, but one regarding strong password use.

I'm not arguing against AES. I'm saying that its strength is largely irrelevant when the key is generated from a password. You simply don't retain the 256 bit strength when you use it that way. Actually, in my example there are only 1000 passwords to guess and one reason it took whole 4 sec to break is the usage of gpg which deliberately slows down the key generation process by salting the password and iterating. Is that even implemented in 7zip?

---

### Post by varunendra on 2011-06-23
> **DZ* said:**
> I'm not arguing against AES. I'm saying that its strength is largely irrelevant when the key is generated from a password. You simply don't retain the 256 bit strength when you use it that way. Actually, in my example there are only 1000 passwords to guess and one reason it took whole 4 sec to break is the usage of gpg which deliberately slows down the key generation process by salting the password and iterating. Is that even implemented in 7zip?

You're right from your point of view, an easy password = easy to crack.

That's why it is always recommended to use a strong (long + complex) password which is difficult to guess. And that's when we come to the point of view of doas777, or Jon Callas for that matter..

Here 'long' does not mean you necessarily have to write a full poem as your password. It'll be too easy to guess/crack if the cracker knows or can guess that your favourite one is "Twinkle-twinkle little star....". Again, if the password is complex enough (not an obvious word or phrase, uses a combination of alphabets in small & caps + numbers + special chars) then even 9 digits produce a huge no. of passwords to guess.

And for a person who uses such technique for security (who at least 'knows' s/he's using AES-256 encryption), don't we presume that s/he understands the importance of the strength of a password?

By the way, doas777, I'm not familiar with the term 'four-factor'8-[, seems to be an important one to know, can you explain it for me please? :)

---

### Post by Artemis3 on 2011-06-23
Look at this: [http://whitepixel.zorinaq.com/](http://whitepixel.zorinaq.com/)

This is why you are advised to use a longer password, because an 8 char one is starting to be possible to brute force in months, not years like it used to.

GPUs, specially ATI (AMD) are scary computational monsters for this type of task. Things like bitcoin mining has made people set up crazy farms for hashing, which could be instantly switched for brute forcing passwords (just more hashing).

[http://www.pcpro.co.uk/blogs/2011/06/01/how-a-cheap-graphics-card-could-crack-your-password-in-under-a-second/](http://www.pcpro.co.uk/blogs/2011/06/01/how-a-cheap-graphics-card-could-crack-your-password-in-under-a-second/)

---

### Post by BkkBonanza on 2011-06-23
In encryption situations using any of the "strong" algorithms it is the implementation that is always most suspect. A programming error can result in vulnerabilities that are the weak link much more than the encryption algorithm. It's really hard to know if a specific product has an implementation that is fully proofed. If there are back doors into certain products or even algorithms they largely seem to NOT get publicly reported which always leaves you wondering.

---

### Post by doas777 on 2011-06-23
@varunendra: just a name for somthing you already know. a "4-factor" password consists of lowercase and uppercase alpha characters, numbers, and special characters (exactly as you recommended). the goal as I'm sure you can discern, is the expand the size of the character set. as that dramatically increases the resistance to bruteforce (more than adding additional characters to teh password length.) the characterset size varies from langague to langague (the number of special characters changes) but for most english keyboards, it's 72 or so characters. I used 64 in my example cause its true for almost all localities.

---

### Post by doas777 on 2011-06-23
> **Artemis3 said:**
> Look at this: [http://whitepixel.zorinaq.com/](http://whitepixel.zorinaq.com/)

This is why you are advised to use a longer password, because an 8 char one is starting to be possible to brute force in months, not years like it used to.

GPUs, specially ATI (AMD) are scary computational monsters for this type of task. Things like bitcoin mining has made people set up crazy farms for hashing, which could be instantly switched for brute forcing passwords (just more hashing).

[http://www.pcpro.co.uk/blogs/2011/06/01/how-a-cheap-graphics-card-could-crack-your-password-in-under-a-second/](http://www.pcpro.co.uk/blogs/2011/06/01/how-a-cheap-graphics-card-could-crack-your-password-in-under-a-second/)


well, keep in mind, this is a different kind of thing. cracking hashes and bruteforcing an authentication mechanism are very different processes. with hash cracking, you have already captured the hash, and you are just trying different mathematical operations to return it to its un-hashed form. this means that all the algorithm needs to do to test a proposed solution is self-contained and can be done in nanoseconds. 

a bruteforce does not usually involve a captured hash, so without more information, tools like rainbow tables and gpu acceleration are useless. they can onlyl process each attempt as fast as teh authentication method they are trying to BF will allow them too, as DZ* pointed out. for instance, gnome introduces a 3 second pause ( with a random >5 second salt) between failed login attempts. that means that each combination you try takes between 4 and 8 seconds to complete. GPU accellerated hash cracking should be able to test millions or billions of passwords per second, but for any case were you don;t have the hash up front, there is little that can be done except a really really really slow grind.

---

### Post by Bandit on 2011-06-23
This thread has me curious and willing to do some real world test.
Test document will be a Open Document Spreadsheet, single page with 1 page of data (its a fishing tackle inventory) the emulate a banking spreadsheet.

Will be using AES256 Encryption.

Password will be 8 characters long, featuring at least 2 numbers, 1 special character like the $ dollar sign and a combination of lower and capital letters in a combination that do not form a dictionary word.

Test machine will be my main system, 2.5GHz AMD Quad Core with 4GB DDR2-800. Which is a average speed desktop by todays standards.

+-----------------------------------------------------------------------+
WILL EDIT THIS POST WHEN I HAVE FINAL DATA..  - Joe

---

### Post by doas777 on 2011-06-24
kewl!

your major bottle neck *should be* the time it takes gpg to respond to each request. depending on how concurrent gpg is, you may be able to get good results by running a few threads each trying a different password. With a quad core, you should be able to keep 3-4 running at a time.

---

### Post by DZ* on 2011-06-24
> **doas777 said:**
> kewl!

your major bottle neck *should be* the time it takes gpg to respond to each request. depending on how concurrent gpg is, you may be able to get good results by running a few threads each trying a different password. With a quad core, you should be able to keep 3-4 running at a time.

but.. don't we already know the answer? The expected number of guesses is 0.5*(size of the character set)^password_length, assuming the password is truly random.

gpg can be forced to build the key much slower compared to the default. The slowest right now can be achieved with the option "--s2k-count 65011712" which gives about 1.8 sec per guess on my  laptop.

---

### Post by doas777 on 2011-06-24
> **DZ* said:**
> but.. don't we already know the answer? The expected number of guesses is 0.5*(size of the character set)^password_length, assuming the password is truly random.

gpg can be forced to build the key much slower compared to the default. The slowest right now can be achieved with the option "--s2k-count 65011712" which gives about 1.8 sec per guess on my  laptop.


quite right! practical experimentation is fun though.

---

