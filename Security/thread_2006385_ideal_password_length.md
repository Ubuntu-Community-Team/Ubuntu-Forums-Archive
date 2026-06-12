---
title: "ideal password length"
date: 2012-06-19
forum: Security
---

### Post by anon0 on 2012-06-19
Assuming your password is complex enough, how short is too risky, and how long is too cumbersome to use, in your view? I mean, if I have to sudo something quickly, I don't really want to type too many keystrokes, but I don't want weak passwords either.

By the way, if a Linux user has a weak password, what's the worst thing you can do to him?

---

### Post by jllipke on 2012-06-19
6 - 8 characters is usually good for me

although if it is a password like 123456 then length isn't your problem
but you usually don't want something random like H_7*tg then your problem is remembering it,
 
it is a matter of how well you will remember it and how much you will use it

---

### Post by HermanAB on 2012-06-19
The military advises using at least 9 character passwords with complexity (mixed case and funny characters) or 12 characters without.

The worst that can happen depends on which servers the perp installs after gaining entry to your system: Hosting a kiddy porn or Al Qaeda web site is probably the worst thing for an American.

---

### Post by HermanAB on 2012-06-19
> 6 - 8 characters is usually good for me

I have repaired many servers where some asshat thought that a 4 to 6 character password is cool...

---

### Post by OpSecShellshock on 2012-06-19
For your own systems that require physical access anyway, and assuming you don't have any sort of remote administration enabled, 8 or so is probably fine. For passwords on other services (online accounts of any kind) you're best off going with slight complexity and at least 16 characters. This is because eventually there will be a breach/dump, and at that point both miscreants and legit researchers will put effort into cracking whatever gets exposed. 16 characters exceeds reasonable effort for (and I can't stress this enough) *current *systems most commonly used for casual cracking, and then only if it hasn't been used, dumped, and cracked at some point already and isn't sitting in a list somewhere.

More important than strength, of course, is avoiding re-use.

---

### Post by haqking on 2012-06-19
> **HermanAB said:**
> The military advises using at least 9 character passwords with complexity (mixed case and funny characters) or 12 characters without.

The worst that can happen depends on which servers the perp installs after gaining entry to your system: Hosting a kiddy porn or Al Qaeda web site is probably the worst thing for an American.

I woudlnt take the militarys advice, they still use NT 3.51 with a dial up modem with RAS using a 4 character password near to where i live ;-)

To the OP, it depends on the value of your data or account you are protecting.

The more entropy (basically length) then the harder it will be to brute force it, add complexity into it aswell then you improve things, though entropy is more important than complexity overall.

I would say a minimum of 12 where allowed

Personally i use the maximum available, i use a personal construct per password with additional padding for entropy, and never re-use them

---

### Post by tubbygweilo on 2012-06-19
Take whatever Gmail recommends then double it!;)

---

### Post by Soul-Sing on 2012-06-19
I 'll take the max. available.
so wireless wpa2: 63 via a yubikey.):P

---

### Post by ashwinrao on 2012-06-19
Any thing above six should be safe and ideal!

---

### Post by Enigmapond on 2012-06-19
It's  not the length that you should worry about but the password itself. Using different case letters, numbers and other characters add's to the strength.`If you install pwgen and use this:

```
pwgen -s -y 8
```

it will give you a very strong password with only 8 characters.

---

### Post by Simian Man on 2012-06-19
One character passwords are sufficient, so long as that one character doesn't appear on any keyboard or in any character encoding.

---

### Post by haqking on 2012-06-19
> **Enigmapond said:**
> It's  not the length that you should worry about but the password itself. Using different case letters, numbers and other characters add's to the strength.`If you install pwgen and use this:

```
pwgen -s -y 8
```it will give you a very strong password with only 8 characters.

Length is more important then complexity overall due to keyspace and increased entropy.

asdfethujinmjtkpotht

is harder to crack than

@5Tsghu

The 20 chr password asdfethujinmjtkpotht is only lower case alpha  characters,  however that means there is a possible 26 values for each  letter of the password.

which is 26^20 combinations

Looking at the second which caters for special characters, upper  case lower case and numbers for approximately 72 values for each letter  which is

72^7 or much lower combinations than the first which uses length

Also  type of password is important, for example old LM passwords used in windows environments are null padded to 14 bytes and the split length is split between 2  x 7 byte pairs

To the OP use the maximum available (or functionally applicable or rememberable) for the application where applicable, length is more important than complexity but throw complexity in as well.

---

### Post by haqking on 2012-06-19
> **ashwinrao said:**
> Any thing above six should be safe and ideal!

You make my job so much easier ;-)

I would redirect you to an old post of mine and the attachments
[http://ubuntuforums.org/showpost.php?p=11793946&postcount=19](http://ubuntuforums.org/showpost.php?p=11793946&postcount=19)

---

### Post by |{urse on 2012-06-19
Yep, be sure its alphanumeric with mixture of cases and characters, I like them 12+ spaces long. Or else haqking's rainbow tables will sort it out in a few, depending on the speed of his available 'distributed computing' resources. :lolflag:

---

### Post by haqking on 2012-06-19
> **|{urse said:**
> Yep, be sure its alphanumeric with mixture of cases and characters, I like them 12+ spaces long. Or else haqking's rainbow tables will sort it out in a few, depending on the speed of his available 'distributed computing' resources. :lolflag:
rainbow tables ?

I am old skool, a crate of jolt cola and 75 WPM touch typist ;-)

---

### Post by Hungry Man on 2012-06-19
One of each character and 12+ if you can't verify the crypto behind it. If it's something like truecrypt with PBKF2 stretching for keys you'd be fine with 8+ characters, but again 12+ is fine if you're worried about the NSA.

If you can't verify what's being used (ie: it could be MD5 or some ****) go for 16 for 'critical' information.

Overall I'd say 8-12 characters with a full character set.

edit: And I don't think entropy matters at all. The idea of entropy is based on the assumption that you're fighting dictionary attacks. The fact is that your attacker has no idea what your password is or what it could possibly be therefor it's pretty easy to avoid a dictionary attack with 5 seconds of though. No need for true randomness.

Think of it this way... 

0v02!I17

That's a randomly generated 8 character password with one of each character type.

aaaaaaaaaaaaaaaaaaaaaaaa!23C

That's like 26 characters, 22 are 'a' and one of every character type. The entropy of the first password is far higher than the second password. It doesn't matter. The second is impossibly to bruteforce and no dictionary is going to have 22 a's and 4 random characters and dictionary attacks don't mix and match much at all.

Conclusion: the second password is far more useful and far easier to remember.

---

### Post by uylug on 2012-06-19
There is no ideal password length.

Usability vs Security. It's always been that.

A password with six characters including numbers, letters and special characters should be pretty hard to break.

My passwords are normally between 10-15 characters, combining numbers, letters and a couple special characters.

The key is making up a password you can remember ( maybe not on the first try )

---

### Post by |{urse on 2012-06-19
> **haqking said:**
> rainbow tables ?

I am old skool, a crate of jolt cola and 75 WPM touch typist ;-)

Sure, just load your tables into ram, log onto your c&c channel for ze botnet, divide the job among your nodes and crack that hash.

Or hook up like 30 keyboards, write a script to simulate an enter keystroke every few seconds and let 50 or 60 cats run around on them until you're in.

Or just sneak in the window and boot to a copy of ophcrack.

I see from your link earlier, you were using cain and abel. My.. you ARE oldskool. I still rock that program on occasion. :lolflag:

---

### Post by haqking on 2012-06-19
> **|{urse said:**
> Sure, just load your tables into ram, log onto your c&c channel for ze botnet, divide the job among your nodes and crack that hash.

Or hook up like 30 keyboards, write a script to simulate an enter keystroke every few seconds and let 50 or 60 cats run around on them until you're in.

Or just sneak in the window and boot to a copy of ophcrack.

I see from your link earlier, you were using cain and abel. My.. you ARE oldskool. I still rock that program on occasion. :lolflag:
LOL

yeah i only used it to show an example which showed years for the purposes of that discussion, it has its uses from time to time though.

Anyways im out of this thread now, these discussions get boring after a while ;-)

Peace

---

### Post by OpSecShellshock on 2012-06-19
Yeah I have to admit that even as a professional I glaze over at the details, because operationally the important thing is don't re-use and recover as quickly as possible. Assume third parties you trust passwords to are going to be breached and plan accordingly. Then you won't have to do what my friends and family had to after the LinkedIn thing (i.e. think "now what else did I use that one on? Did I get all of them?"). Seriously, it's going to happen if it hasn't already. If you're lucky, they'll tell you.

---

### Post by anon0 on 2012-06-19
The median length you guys recommended so far is about 12, so it looks like that's the minimum I should aim for.

> **Simian Man said:**
> One character passwords are sufficient, so long as that one character doesn't appear on any keyboard or in any character encoding.

If you can't type it, are you assuming you can transmit it directly, like copying and pasting?

Speaking of which, what do you guys think about using one highly secure file which contains all passwords you have, then copy passwords from that file? Obviously this is a security risk if you expose the master file, but otherwise, the individual passwords can then be purely random and maximum strength, but also usable. However, they become extremely difficult to use if you're not allowed to paste them directly. 

> **Hungry Man said:**
> One of each character and 12+ if you can't verify the crypto behind it. If it's something like truecrypt with PBKF2 stretching for keys you'd be fine with 8+ characters, but again 12+ is fine if you're worried about the NSA.  If you can't verify what's being used (ie: it could be MD5 or some ****) go for 16 for 'critical' information.

Is PBKDF2 basically using random salts and repeating the hashing a large number of times, which involves long calculations and thus slows down the generation of rainbow tables that convert all exposed hashed passwords in the database into plaintext? If an original 8-character password is weak then the attacker may still guess it successfully (eg poor user login password), whether PBKF2 is used or not, right? 

> **Hungry Man said:**
> ...The idea of entropy is based on the assumption that you're fighting dictionary attacks. The fact is that your attacker has no idea what your password is or what it could possibly be therefor it's pretty easy to avoid a dictionary attack with 5 seconds of though. .... aaaaaaaaaaaaaaaaaaaaaaaa!23C [is] impossibly to bruteforce and no dictionary is going to have 22 a's and 4 random characters and dictionary attacks don't mix and match much at all.

Interesting, so repeating something simple a large number of times will make it difficult to attack. If so, people should do that more then, since it's easy to do.

---

### Post by Hungry Man on 2012-06-19
> Speaking of which, what do you guys think about using one highly secure file which contains all passwords you have, then copy passwords from that file? Obviously this is a security risk if you expose the master file, but otherwise, the individual passwords can then be purely random and maximum strength, but also usable. However, they become extremely difficult to use if you're not allowed to paste them directly. 
That's the idea behind a master password. I suggest you look into LastPass.

> Is PBKDF2 basically using random salts and repeating the hashing a large number of times, which involves long calculations and thus slows down the generation of rainbow tables that convert all exposed hashed passwords in the database into plaintext? If an original 8-character password is weak then the attacker can still try to bruteforce it individually (eg user login password), whether PBKF2 is used or not, right? 
Sort of. But you're correct in that the idea is to hash over and over again, which drives the cost up computationally ie: if 1 round is 1 second 10 rounds is 10 seconds therefor more rounds = 10x the cost per computation.

Each guess has to be hashed 1000x or whatever before you can see if it's correct. So that's a large amount of computation added and it's going to slow thinsg down considerably.

> Interesting, so repeating something simple a large number of times will make it difficult to attack. If so, people should do that more then, since it's easy to do.
Yes, they should. There's no reason not to really. If your password is "HungryMan1!" it's very simple to make it much much stronger by simply adding "HungryMan1!????????????????????" All I have to remember is my original password and that there's 20 ?'s after it. No dictionary is going to guess that and bruteforcing it would take millions of years. It's called 'password padding'. There's really no reason not to do it, come up with a unique way to pad it ie:
<HungryMan1!>
!HungryMan1!?
((HungryMan1!))

Something simple like that adds a few characters and basically makes your password incredibly difficult to get past.

12 characters is a safe bet. For my master password (for LastPass) it's actually more than 20 characters with 20,000 rounds of PBKF2.

---

### Post by anon0 on 2012-06-20
> **Hungry Man said:**
> Each guess has to be hashed 1000x or whatever before you can see if it's correct. So that's a large amount of computation added and it's going to slow thinsg down considerably.

On the ten-year-old computer which I'm using to develop a website, 1,000 passes of SHA-2 takes about 0.02 seconds to run. So if I want to slow down the login to 1 second on this server, I'd have to use 50,000 passes. That may slow down the server too much though if more than one person tries to log in. I mainly just want to prevent people from trying random passwords remotely. I think I should combine the hashing with a delay for failed attempts.

---

### Post by Hungry Man on 2012-06-20
> **anon0 said:**
> On the ten-year-old computer which I'm using to develop a website, 1,000 passes of SHA-2 takes about 0.02 seconds to run. So if I want to slow down the login to 1 second on this server, I'd have to use 50,000 passes. That may slow down the server too much though if more than one person tries to log in. I mainly just want to prevent people from trying random passwords remotely. I think I should combine the hashing with a delay for failed attempts.

If it's for a server, yes. Every three-five tries just have it block another attempt for 15 seconds.

---

### Post by rnahlawi on 2012-06-21
I would consider 8 - 12 with mixed letters, symbols and numbers to be a good password.

---

### Post by Carborundum on 2012-06-22
How about using pass phrases? Something like "To be, or not to be?" (20 characters including uppercase, lowercase, whitespace and special characters) is extremely easy to remember and should be virtually impossible to brute force.

For true impregnability, use a foreign (and preferably obscure) language as well: "taH pagh, taHbe'?"

---

### Post by haqking on 2012-06-22
> **Carborundum said:**
> How about using pass phrases? Something like "To be, or not to be?" (20 characters including uppercase, lowercase, whitespace and special characters) is extremely easy to remember and should be virtually impossible to brute force.

For true impregnability, use a foreign (and preferably obscure) language as well: "taH pagh, taHbe'?"

[https://www.cl.cam.ac.uk/~jcb82/doc/BS12-USEC-passphrase_linguistics.pdf]("https://www.cl.cam.ac.uk/%7Ejcb82/doc/BS12-USEC-passphrase_linguistics.pdf")

Passphrases using shakespeare are not exactly the most secure, i have over 2 TB of dictionary files and passphrase dict files, including 13 different languages, the passphrase collections include all shakespeare quotes ;-)

Foreign is only foreign to you, not all crackers are english speaking.

Dont rely on what you think you know !

Peace

---

### Post by Carborundum on 2012-06-22
> **haqking said:**
> 
Foreign is only foreign to you, not all crackers are english speaking.

Dont rely on what you think you know !

I'm willing to bet that rather few of them speak Klingon. ;)

---

### Post by haqking on 2012-06-22
> **Carborundum said:**
> I'm willing to bet that rather few of them speak Klingon. ;)

Who needs to? I can make a dict file in 2 minutes using a word list compiler

[http://www.angelfire.com/md/startrekkie1701/klindic.html](http://www.angelfire.com/md/startrekkie1701/klindic.html)
[http://www.ebook3000.com/The-Klingon-Dictionary_4281.html](http://www.ebook3000.com/The-Klingon-Dictionary_4281.html)
[http://en.memory-alpha.org/wiki/Okrand%27s_Unabridged_Klingon_Dictionary]("http://en.memory-alpha.org/wiki/Okrand%27s_Unabridged_Klingon_Dictionary")



Peace

---

### Post by Carborundum on 2012-06-22
> **haqking said:**
> Who needs to? I can make a dict file in 2 minutes using a word list compiler

Only roots are listed in the dictionary, and you won't get very far with those. Klingon is agglutinative (meaning new words can be productively formed from existing roots) and declension is common (meaning the shape of a word changes depending on its grammatical function).

---

### Post by haqking on 2012-06-22
> **Carborundum said:**
> Only roots are listed in the dictionary, and you won't get very far with those. Klingon is agglutinative (meaning new words can be productively formed from existing roots) and declension is common (meaning the shape of a word changes depending on its grammatical function).

Of course, i am not saying that it is impossible to create a reasonably secure password or passphrase.

I was pointing specifically at your examples.

Shakespeare whether in English or Klingon be it "to be or not to be" or "taH pagh, taHbe" is not random and easily sourced for word compilation,  The Klingon hamlet is available online.

Peace

---

### Post by Carborundum on 2012-06-22
> **haqking said:**
> Of course, i am not saying that it is impossible to create a reasonably secure password or passphrase.

I was pointing specifically at your examples.

Shakespeare whether in English or Klingon be it "to be or not to be" or "taH pagh, taHbe" is not random and easily sourced for word compilation,  The Klingon hamlet is available online.

Peace
Absolutely, I can see why those examples aren't secure. But an original phrase in an obscure language should be reasonably secure, I think. I'm not very proficient in Klingon, so lets go with another conlang (Na'vi):

Kifkeyìri uvan ke sivengi Eywa
God doesn't play dice with the universe

In a dictionary, you would find "kifkey", "uvan si", "ke" and "Eywa", but to form the above sentence from those words, you would have to account for the topical case (-ìri), the subjunctive mood (<iv>), the pejorative affect (<eng>) and the fact that particle verbs are split up when negated. I feel reasonably safe in assuming that few dictionary attacks account for those things.

---

### Post by haqking on 2012-06-22
> **Carborundum said:**
> Absolutely, I can see why those examples aren't secure. But an original phrase in an obscure language should be reasonably secure, I think. I'm not very proficient in Klingon, so lets go with another conlang (Na'vi):

Kifkeyìri uvan ke sivengi Eywa
God doesn't play dice with the universe

In a dictionary, you would find "kifkey", "uvan si", "ke" and "Eywa", but to form the above sentence from those words, you would have to account for the topical case (-ìri), the subjunctive mood (<iv>), the pejorative affect (<eng>) and the fact that particle verbs are split up when negated. I feel reasonably safe in assuming that few dictionary attacks account for those things.


Well that example is fairly secure for sure, but not because it is avatar or any other language, but because it is long and contains upper case, spaces and special characters.

you could write nonsense using the same method.

Staying inline with the thread the point remains the same, use long and special character combinations preferably passphrases (where the password is created from a passphrase and not the passphrase itself), use the longest availabe which you can remember or the service allows and dont re-use.

I am now creating dictionary/common passphrase files from Na'vi and Klingon by the way ;-)

Peace

---

### Post by Carborundum on 2012-06-22
> **haqking said:**
> 
you could write nonsense using the same method.

Of course, but the strength of actual phrases are that they are easy for humans to remember while (ideally) still being hard for computer to guess.

> 
I am now creating dictionary/common passphrase files from Na'vi and Klingon by the way ;-)

Haha :D
I suppose I can no longer rely on security by obscurity then. ;)

---

### Post by haqking on 2012-06-22
> **Carborundum said:**
> **Of course, but the strength of actual phrases are that they are easy for humans to remember while (ideally) still being hard for computer to guess.**


Haha :D
I suppose I can no longer rely on security by obscurity then. ;)

Actually the strength is nothing to do with ease of remembering for humans, ease of use is nothing to do with security, infact the more secure something becomes the less easy it is to use and functionality decreases, it is called the security triad where as soon as you approach one the other 2 move further away.

And security through obscurity has never been a good idea.

Peace

---

### Post by Carborundum on 2012-06-22
> **haqking said:**
> Actually the strength is nothing to do with ease of remembering for humans, ease of use is nothing to do with security, infact the more secure something becomes the less easy it is to use and functionality decreases, it is called the security triad where as soon as you approach one the other 2 move further away.
Sorry, poor choice of words on my part. What I meant to say was that the *advantage*  of actual phrases as opposed to nonsense is that they are easier to remember.

> 
And security through obscurity has never been a good idea.

I'm aware. That was meant to be tongue-in-cheek.

---

### Post by haqking on 2012-06-22
[QUOTE=Carborundum;12046277]Sorry, poor choice of words on my part. What I meant to say was that the *advantage*  of actual phrases as opposed to nonsense is that they are easier to remember.


**I'm aware. That was meant to be tongue-in-cheek.[**/QUOTE]

I did assume that from the smiley, i thought i would respond just incase though ;-)

</sarcasm> works well as does the smiley

Peace

---

### Post by HarryTorry on 2012-06-22
> **haqking said:**
> rainbow tables ?

I am old skool, a crate of jolt cola and 75 WPM touch typist ;-)

Rainbow tables can't get me, I salt all of my passwords!

---

### Post by Hungry Man on 2012-06-22
> **haqking said:**
> Actually the strength is nothing to do with ease of remembering for humans, ease of use is nothing to do with security, infact the more secure something becomes the less easy it is to use and functionality decreases, it is called the security triad where as soon as you approach one the other 2 move further away.

And security through obscurity has never been a good idea.

Peace

d0g!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Easy to remember. I doubt your dictionary is going to break it unless you happen to have 70+ character words? lol 

The tradeoff between security and usability is not always there and not always so great. All I have to do is remember "X amount of !'s after d0g" and I've got an easy to remember password that isn't going to show up in any dictionary or be bruteforcable assuming the attacker has no information on my password.

Password padding is all anyone needs to get a strong password.

Take whatever your current password is and add 5 "anythings" at the end, aaaaa, !!!!!, <<<<<, etc. Your attacker doesn't know your padding or any information about your password.

---

### Post by haqking on 2012-06-22
> **Hungry Man said:**
> d0g!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Easy to remember. I doubt your dictionary is going to break it unless you happen to have 30+ character words? lol 

The tradeoff between security and usability is not always there and not always so great.

Password padding is all anyone needs to get a strong password.

Take whatever your current password is and add 5 "anythings" at the end, aaaaa, !!!!!, <<<<<, etc. Your attacker doesn't know your padding or any information about your password.


I am fully conversant with password padding, i dont get your point ?

I do have many dict files with 30+ chrs actually but thats irrelevant, at no time have i said i can crack any password, infact my point has been that length is better overall (so padding i agree with)

The d0g!!!! etc is a good password, what you quoted of mine was saying that ease of use does not make something secure, which it does not.

And a point to note, for alot of my dic files (alot of which you can download) alot of which i have made custom, include alot of padding at the end of common passwords including !.

oh i should add that the d0g would be cracked with my pad.rule file, you should change to alternate padding


But anyways.....

---

### Post by Ms. Daisy on 2012-06-22
> **Hungry Man said:**
> d0g!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Easy to remember. I doubt your dictionary is going to break it unless you happen to have 70+ character words? lol 

The tradeoff between security and usability is not always there and not always so great. All I have to do is remember "X amount of !'s after d0g" and I've got an easy to remember password that isn't going to show up in any dictionary or be bruteforcable assuming the attacker has no information on my password.

Password padding is all anyone needs to get a strong password.

Take whatever your current password is and add 5 "anythings" at the end, aaaaa, !!!!!, <<<<<, etc. Your attacker doesn't know your padding or any information about your password.Note to self: Hungry Man pads his passwords with multiples. That may or may not be handy to know ;)

---

### Post by haqking on 2012-06-22
> **Ms. Daisy said:**
> Note to self: Hungry Man pads his passwords with multiples. That may or may not be handy to know ;)

 LOL, well multiples are easily catered for with rule files

---

### Post by iphone predictor on 2012-06-22
i have 6-8 characters usually for my password, i think is ok to have 7 characters and  the password should be something unusual.

---

### Post by HermanAB on 2012-06-22
No, 7 characters are not enough for an important system.

---

### Post by cprofitt on 2012-06-23
Interesting discussion...

One thing of note -- do not share the 'rules' for your passwords...

Companies that 'publish' their rules for passwords -- like most banks and on-line retailers -- hurt security by publishing their 'rules'. This is because they 'limit' the possible passwords and make it easier for a custom dictionary to be created.

[link to pdf]("http://www.google.com/url?sa=t&rct=j&q=venn%20diagram%20password%20requirements&source=web&cd=1&ved=0CFMQFjAA&url=http%3A%2F%2Fwww.commoncriteriaportal.org%2Ficcc%2F9iccc%2Fpdf%2FB2402.pdf&ei=lonmT6bbCKjp6QHZ6oTmDg&usg=AFQjCNEib35GXcQ0F1zHVmhm5CVhKWHtaA&cad=rja")

Also, some systems like poorly configured Windows servers store passwords in an easy to crack format unless you go over 15 characters.

In general, length and frequency of change determine your security level... the longer the password the longer it takes to crack... the more rapidly you change your password the less time a cracker has to get your 'current' password. Mix those two variables together and you can make a resource very secure from password cracking...

Then again... there are exploits around passwords... like 'pass the hash'.

---

### Post by Bluenoser81 on 2012-06-24
> Length is more important then complexity overall due to keyspace and increased entropy.

asdfethujinmjtkpotht

is harder to crack than

@5Tsghu

This calls for some XKCD: [http://xkcd.com/936/](http://xkcd.com/936/)

There are other articles online I've read recently that are pushing the longer-the-better "passphrase" method, rather than the sort-of-standard 6-8 upper and lower case with extra characters at the end, which usually results in something like "Pass1!" and is an easily identifiable pattern.

---

### Post by tubbygweilo on 2012-06-24
This calls for some more XKCD:

Simple passphrases and bones can be cracked without too much effort - [http://xkcd.com/538/](http://xkcd.com/538/)

---

### Post by Cheesemill on 2012-06-24
> **tubbygweilo said:**
> This calls for some more XKCD:

Simple passphrases and bones can be cracked without too much effort - [http://xkcd.com/538/](http://xkcd.com/538/)
+1

That's always been one of my favourites :)

---

### Post by haqking on 2012-06-24
> **Cheesemill said:**
> +1

That's always been one of my favourites :)


If you are in the UK, you dont need a wrench, all they need is the RIPA act, if you dont hand over your passphrase you face upto 5 years jail anyways.

And there was William Wallace  thinking they would never take his freedom ;-)

---

