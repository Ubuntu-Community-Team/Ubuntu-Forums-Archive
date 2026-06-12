---
title: "crack encfs password?"
date: 2010-02-11
forum: Security
---

### Post by cd-r80 on 2010-02-11
Hi! I have lost my encfs-CD password, or I have to search more, but if I remember length of my password and more or less what characters it had, Is it possible crack the password and which program could do it?

---

### Post by cd-r80 on 2010-02-14
If it is AES I cannot use john? I would like to try with some Brute Force app. I remember part of the password but not all. Some prog. where I can put many already known letters, numbers? I Made this encfs disk in Feisty. Interested if I really could open it still in Karmic (Username is same, but don't know if Encfs version affects). I installed already encfs on Karmic & have old encfs5 file. Perhaps I could just make a bash script which tries list of old passwords, well more complex is not easy for me.

---

### Post by Simplicius on 2010-03-09
I have the exact same issue. I know it sounds like I'm trying to crack someone else's file system and I don't know how I can convince you otherwise. I remember some of the numbers and letters but I just can't remember the whole thing. The problem is, among the encrypted files I have a file with a bunch of passwords for banks, etc. This is already a big pain in the neck

---

### Post by bodhi.zazen on 2010-03-09
This is the downside of encryption. If you loose the password or key (depending on the protocol) you are out of luck.

---

### Post by rufus25 on 2010-09-15
I came across this thread while looking for some best practice tip to EncFS password length, etc. Kinda old thread, but maybe I can help out anyway:

I tend to forget small things about my paraphrases, so I wrote a little Perl script to build a list of possible passes I could try from the things I remember:

[http://home.arcor.de/brutus_/tools/genwordlist.pl](http://home.arcor.de/brutus_/tools/genwordlist.pl) 

It need Perl YAML support. You can install it with **aptitude install libyaml-libyaml-perl** or get **YAML::XS** on CPAN.

```
# example file called 'example.yaml'
---
- H
- h
---
- e
- 3
---
- ll
- 11
---
- o
- 0
---
- W
---
- o
- 0
---
- r
---
- l
- 1
---
- d
---
- '!'
- ' '
- .
```

After you build your wordlist layout run genwordlist.pl:

```
./genwordlist.pl *example*.yaml
```

And it gives you a list with all the possible pass-phrases:

```
HelloWorld!  HelloWorld HelloWorld.  HelloWor1d!  HelloWor1d HelloWor1d.  HelloW0rld!  HelloW0rld HelloW0rld.  HelloW0r1d!  HelloW0r1d HelloW0r1d.  Hell0World!  Hell0World Hell0World.  Hell0Wor1d!  Hell0Wor1d Hell0Wor1d.  Hell0W0rld!  Hell0W0rld Hell0W0rld.  Hell0W0r1d!  Hell0W0r1d Hell0W0r1d.  He11oWorld!  He11oWorld He11oWorld.  He11oWor1d!  He11oWor1d He11oWor1d.  He11oW0rld!  He11oW0rld He11oW0rld.  He11oW0r1d!  He11oW0r1d He11oW0r1d.  He110World!  He110World He110World.  He110Wor1d!  He110Wor1d He110Wor1d.  He110W0rld!  He110W0rld He110W0rld.  He110W0r1d!  He110W0r1d He110W0r1d.  H3lloWorld!  H3lloWorld H3lloWorld.  H3lloWor1d!  H3lloWor1d H3lloWor1d.  H3lloW0rld!  H3lloW0rld H3lloW0rld.  H3lloW0r1d!  H3lloW0r1d H3lloW0r1d.  H3ll0World!  H3ll0World H3ll0World.  H3ll0Wor1d!  H3ll0Wor1d H3ll0Wor1d.  H3ll0W0rld!  H3ll0W0rld H3ll0W0rld.  H3ll0W0r1d!  H3ll0W0r1d H3ll0W0r1d.  H311oWorld!  H311oWorld H311oWorld.  H311oWor1d!  H311oWor1d H311oWor1d.  H311oW0rld!  H311oW0rld H311oW0rld.  H311oW0r1d!  H311oW0r1d H311oW0r1d.  H3110World!  H3110World H3110World.  H3110Wor1d!  H3110Wor1d H3110Wor1d.  H3110W0rld!  H3110W0rld H3110W0rld.  H3110W0r1d!  H3110W0r1d H3110W0r1d.  helloWorld!  helloWorld helloWorld.  helloWor1d!  helloWor1d helloWor1d.  helloW0rld!  helloW0rld helloW0rld.  helloW0r1d!  helloW0r1d helloW0r1d.  hell0World!  hell0World hell0World.  hell0Wor1d!  hell0Wor1d hell0Wor1d.  hell0W0rld!  hell0W0rld hell0W0rld.  hell0W0r1d!  hell0W0r1d hell0W0r1d.  he11oWorld!  he11oWorld he11oWorld.  he11oWor1d!  he11oWor1d he11oWor1d.  he11oW0rld!  he11oW0rld he11oW0rld.  he11oW0r1d!  he11oW0r1d he11oW0r1d.  he110World!  he110World he110World.  he110Wor1d!  he110Wor1d he110Wor1d.  he110W0rld!  he110W0rld he110W0rld.  he110W0r1d!  he110W0r1d he110W0r1d.  h3lloWorld!  h3lloWorld h3lloWorld.  h3lloWor1d!  h3lloWor1d h3lloWor1d.  h3lloW0rld!  h3lloW0rld h3lloW0rld.  h3lloW0r1d!  h3lloW0r1d h3lloW0r1d.  h3ll0World!  h3ll0World h3ll0World.  h3ll0Wor1d!  h3ll0Wor1d h3ll0Wor1d.  h3ll0W0rld!  h3ll0W0rld h3ll0W0rld.  h3ll0W0r1d!  h3ll0W0r1d h3ll0W0r1d.  h311oWorld!  h311oWorld h311oWorld.  h311oWor1d!  h311oWor1d h311oWor1d.  h311oW0rld!  h311oW0rld h311oW0rld.  h311oW0r1d!  h311oW0r1d h311oW0r1d.  h3110World!  h3110World h3110World.  h3110Wor1d!  h3110Wor1d h3110Wor1d.  h3110W0rld!  h3110W0rld h3110W0rld.  h3110W0r1d!  h3110W0r1d h3110W0r1d.
```

Happy brute forcing ;)

---

### Post by wacky_sung on 2010-09-16
Ah dictionary attack is slow and painful.I will suggest to do it by rainbow tables.

---

### Post by Seo42 on 2010-09-16
Has anyone a link to a header documentation? Where is the hash value of the passphrase in the header?

---

### Post by serverfarm on 2010-09-17
Cracking a encrypted file-system is very difficult.  AES was designed to be virtually uncrackable.  Maybe if you knew someone at the NSA :wink: then you could get it cracked.  Sorry, but I think your stuck.  Unless you wrote down the hash it asks you to write down after encrypting it.   If you did then your in luck!  If anyones curious heres a 14 character alphanumeric password then it would take 768 years to crack.

[http://www.wilderssecurity.com/showthread.php?p=1261571](http://www.wilderssecurity.com/showthread.php?p=1261571)

---

### Post by wacky_sung on 2010-09-17
> **serverfarm said:**
> Cracking a encrypted file-system is very difficult.  AES was designed to be virtually uncrackable.  Maybe if you knew someone at the NSA :wink: then you could get it cracked.  Sorry, but I think your stuck.  Unless you wrote down the hash it asks you to write down after encrypting it.   If you did then your in luck!  If anyones curious heres a 14 character alphanumeric password then it would take 768 years to crack.

[http://www.wilderssecurity.com/showthread.php?p=1261571](http://www.wilderssecurity.com/showthread.php?p=1261571)

I do not think it require such a long time.If you know the hash and built a rainbow table with the require hash.Then you may only take weeks or days just to crack it using rainbow table.Just like md5sum password can be crack within minutes using rainbow table.

---

### Post by DZ* on 2010-09-20
> **wacky_sung said:**
> I do not think it require such a long time.If you know the hash and built a rainbow table with the require hash.Then you may only take weeks or days just to crack it using rainbow table.Just like md5sum password can be crack within minutes using rainbow table.

I think it would be useless to build a rainbow table to crack one particular password. It would take longer time to build a table than to brute force the password. They are only useful if a table is going to be re-used to avoid the same computations in the future.

---

### Post by wacky_sung on 2010-09-20
> **DZ* said:**
> I think it would be useless to build a rainbow table to crack one particular password. It would take longer time to build a table than to brute force the password. They are only useful if a table is going to be re-used to avoid the same computations in the future.

I disagreed with what you mentioned.If you create the database of the rainbow table which mean that you are able to crack all passwords using the same hash.As for novice,it is a waste of time and effort.Whereas a professional criminal seize the opportunity to exploit and compromise system.

---

### Post by Black_Tanto on 2010-09-21
> **bodhi.zazen said:**
> This is the downside of encryption. If you loose the password or key (depending on the protocol) you are out of luck.


Inst there tools to crack that encryption?

---

### Post by bodhi.zazen on 2010-09-21
> **Black_Tanto said:**
> Inst there tools to crack that encryption?

That might possibly work, but such tools are labor intensive, take time, and are not fool proof by any means, at least not yet.

---

### Post by n~kf)}BW% on 2010-09-21
So, this guys needs to:

1. Get his AES hash, header? And find a tool to start cracking...
2. Try to crack it using brute force (alnum up to 7 chars, alpha up to 8, num up to 12)
3. Then he should try dictionary attack with rules
4. Then, i would suggest combination attack and mask attack
5. Give up... :) FORGET RAINBOW TABLES :D it would take so much time to generate by yourself, you would have more chance by brute forcing it ;)

---

### Post by Black_Tanto on 2010-09-22
Somebody should come up with a method of trying to decode how the file was taken apart instead of guessing the password, reverse engineering the encryption app itself, predicting various ways it could take a file apart then generate possibilities for the original until it starts to look like text, or whatever you were looking for.

---

### Post by n~kf)}BW% on 2010-09-22
Reverse engineering of such an encryption is not an easy task. Forget it :)

---

### Post by Black_Tanto on 2010-09-23
I bet the government has programs that could do it. I have also seen it done with other things, though I dont think it was easy or quick. It could be reused though.


Anyway, there are tools in the Ubuntu repository, Backtrack Repository and Node Zero OS (based on Ubuntu) that will try to brute force the password for encrypted PDFs.

---

### Post by n~kf)}BW% on 2010-09-23
Craking PDF files is much different from cracking encrypted disks. It's way simpler. I don't think the government has programs that can reverse such an encryption. Yes, they have very good tools to crack it, but if you have a strong password, they fail.

So, you can crack it using different guessing methods, but you can't reverse it!

---

### Post by uRock on 2010-09-23
> **slovenia said:**
> I don't think the government has programs that can reverse such an encryption.
If they do, they won't tell.

---

