---
title: "strong password"
date: 2009-12-30
forum: Security
---

### Post by linuxonbute on 2009-12-30
Hi guys I thought I would run this past you.

I often see comments about strong passwords and many feel that strong passwords are too hard to remember. 

I am using the following system and wonder what your take is as to whether it gives strong but easily remembered passwords.

I pick a word in English then I look up the same word in 2 other languages.
I use each one as part of the password but use a capital letter for each word in the train. I also replace one of the letters i, o, e or b with a number and place  -, _ or ! between each word.

for example Cat_Chat_Gat0

I know this is using dictionary words but it could be from several languages so does not appear to be easily cracked by a dictionary attack.

Does this seem to be a reasonable way to tackle the problem?

---

### Post by scragar on 2009-12-30
Passwords are misleading, a better word is passphrase, choosing a password that's easy to remember and easy to write out can be pretty simple, the password:
```
My Ubuntu Forums Password
```
Is actually pretty secure, despite it's obviousness when it's written down to hack it will take a considerable amount of time and it's highly unlikely any form of dictonary attack will offer much success.
Obviously I suggest a more difficult phrase, but that's up to you.

Personally, for my passwords I use hashes, nothing quite like copying an SHA2 hash into a password field for security. :p (For my home computer this is stored in my encrypted home folder, so very secure, when out and about I can very quickly look up the hash using two mystery words and the site name(ensuring the password is always unique)).

---

### Post by BkkBonanza on 2009-12-31
The problem with regular words is the ability for people who monitor your activities (whether they are friends or enemies) have a high likelihood of narrowing down the domain of useful words. If I happen across your post about multi-language passwords in my reconnaissance on you then I know that I may need a multi-language dictionary to crack yours. 

While this isn't going to help totally random script kiddies - anyone determined to crack your account is helped immensely. Read "Counterhack Reloaded" by Skoudis & Liston. They delve into reconnaissance as a technique for any serious cracker. One of the first things done is to accumulate as much info as possible using Google on targets. In a couple days (or less) your post above will be "forever" linked with your user id and location in Google. 

The most secure way is totally random strings. I use Keepassx to store my passwords for hundreds of sites and it has a password generator that I use to make sure they are always something new. This reduces the problem to only one totally random password for me.

Using hashes is another valid approach as long as you can likewise store them or someone cannot guess your method for generating them. In the case above I now know that I only need two guessed words and the site name to generate one that works. Of course, you wouldn't publicize the real methodology. If the method is consistent then cracking it for one case means it's cracked for all others too, similar to someone finding out my master password.

@scragar - I hope all those names in your signature aren't related to your mystery words when hashing... he he.

---

### Post by Project PWNED on 2009-12-31
apt-get install apg

---

### Post by euler_fan on 2009-12-31
> **linuxonbute said:**
> Hi guys I thought I would run this past you.

I often see comments about strong passwords and many feel that strong passwords are too hard to remember. 

I am using the following system and wonder what your take is as to whether it gives strong but easily remembered passwords.

I pick a word in English then I look up the same word in 2 other languages.
I use each one as part of the password but use a capital letter for each word in the train. I also replace one of the letters i, o, e or b with a number and place  -, _ or ! between each word.

for example Cat_Chat_Gat0

I know this is using dictionary words but it could be from several languages so does not appear to be easily cracked by a dictionary attack.

Does this seem to be a reasonable way to tackle the problem?

No. First, because of the aforementioned valuable intel we all have which helps us craft a better dictionary.

Second, because there are equally easy approaches to salting any password you like to keep it memorable and secure. E.g. Add a string of ten pseudo-random characters to the end of whatever mnemonic you use to remember the password for whatever. So long as you use one salt for all the really important stuff and another for the throwaways you've already achieved more security than anyone short of those who use <hat tip> systems like keepassx to control their constellation of passwords.

Added plus: salting doesn't give anything away because it keeps you in the land of pure dictionary attack to brute force your password. If you can remember a ten digit phone number, you can remember a salt or two.

---

### Post by linuxonbute on 2009-12-31
Thanks for the intel so far.

One point I did not make clear is that I am using this, not for my self because I can easily remember 13 digit numbers never mind 10. I can remember my credit card, national insure, all my past car reg numbers etc, guess I am fortunate in that :rolleyes:. 
What I am doing is using the method for others to have what I hope is a strong password. Many of the younger ones I know do not seem to want to bother too much with this.
So is it reasonable then in this context?

---

### Post by BkkBonanza on 2009-12-31
Anything that makes more convoluted passwords is better than nothing. Friends I know use the most lame passwords and then the same one on all their sites! 

Making the password longer is a good thing but consider when you use dictionary words what you really do is reduce the password length while increasing the range of each term.

eg.

7 letters[A..Z] is 26^7 variations, about 8 billion.

3 common words is 5000^3 variaitions, about 125 billion.
(assuming 5000 common words... most dictionaries are much bigger)

So you see the actual possibilties are only somewhat bigger. The problem as mentioned is that most people will choose words that mean something to them which reduces the dictionary considerably.

3 meaningful words is 2000^3 = about 8 billion.
(thats 2000 words that have special meaning is about the same as 7 A..Z letters)

7 letters[A..Za..z0..9] is 62^7 variations, about 3521 billion.
12 letters[A..Za..z0..9] is 62^12 variations, about a billion billion billion (21 zeros!).

Lets say I do reconnaissance on you via Google and determine 100 meaningful words for you. How many words would you need to use in a password to match the numerical variety of using 7 random letters?

Between 6 and 7 words long... so if you promote your method be sure to make sure they choose words that have no special meaning to them. 

Also if you use language translations of the same word then once they guess your method and preferred languages your password is then reduced mathematically to just a single word. ie. 100^1 = 100, probably less than 1 second for a dictionary attack.

Secret knowledge of constructing a password is often not very secret. If someone finds out one of your passwords they can infer from it's structure how you make your passwords and then use that method to crack your others. Consider that a webmaster with access to his site database *[COLOR="Red"]may[/COLOR]* have access to one of your passwords and from that deduce how you made it. Or his database could be hacked.

Really, there is just no substitute for randomness. All in all, I'm saying your method may make it easy to remember but it doesn't make it hard to crack.

---

### Post by linuxonbute on 2009-12-31
> 

Really, there is just no substitute for randomness. All in all, I'm saying your method may make it easy to remember but it doesn't make it hard to crack.

Great explanation.

Thanks everyone.

---

### Post by scragar on 2009-12-31
> **BkkBonaza said:**
> Secret knowledge of constructing a password is often not very secret. If someone finds out one of your passwords they can infer from it's structure how you make your passwords and then use that method to crack your others. Consider that a webmaster with access to his site database *[COLOR="Red"]may[/COLOR]* have access to one of your passwords and from that deduce how you made it. Or his database could be hacked.

Really, there is just no substitute for randomness. All in all, I'm saying your method may make it easy to remember but it doesn't make it hard to crack.

I would like to remind everyone that hashes are one way, if someone knows my hash for one site it's impossible to, in a reasonable timescale, find the actual secret words and site name from the hash so as to attack another site, even telling you this it's debatable on what name I even used for the site in my hash, did I include a space? What about the suffix .org? Did I type it with capitals? I know I'm not telling :p
Honestly the most efficient method of attempting to guess my password would be to try and brute force the hash, not the greatest solution in the world.

As for guessing my password, I know it's 16^64 possible solutions, assuming you take only the most likely possibilities for English characters that's still 2^53 combinations, at 1,000,000 passwords a second it will still take in the order of 150 years on average. That sounds more than secure enough for my needs(And since most sites don't allow anywhere near that many attempts a second I'm even safer).

And no, the quote in my signature has nothing to do with my password, it's from Trigun, which I'd watched for the first time around the time I changed it.

---

### Post by BkkBonanza on 2009-12-31
I don't see a problem with using a hash like that. As long as you don't say how you generate the input it's impossible to tell from the output. It's essentially a very long random string that needs to be brute forced. The problem is with methods that are reversible by inspecting the password.

---

### Post by Tamalin on 2010-01-01
Usually, when I need a password, I use the app on my iPod called "password" (wow what a creative name :)) to automatically generate a random password.  Usually, I never remember these passwords myself, but keep them encrypted on my iPod so I can recall them wherever I am easily and only have to remember one password.  I can obtain that one password by the following proscess:

1) Create a sentence that you can remember: 'This is an interesting sentence about me.'
2a) Use this Sentence as your password, or...
2b) Take the first letter of each word in the sentence: 'tiaisam'
3) Add random capatalization: 'TiaIsaM'
4) And insert some digits: 'TiaIsaM89'

You will remember the capitalization after typing it a couple of times, and the actual characters can be remembered simply by repeating that sentence to yourself.

--Anyway thats how I've done it...

---

### Post by Repentinus on 2010-01-01
As previously stated, best passwords are random ones and should be constructed of as many character classes as possible, for example:

[LIST]
[*]Lowercase letters
[*]Uppercase letters
[*]Numbers
[*]ASCII special characters
[*]Unicode non-ASCII characters, if possible
[/LIST]
There are plenty of tools available to generate passwords which include characters from variety of these classes and it's not hard to code one for yourself either, though in that case you should read something on generating cryptographically secure pseudorandom numbers, in Linux it can easily be done with /dev/random . It tries very hard not to be pseudorandom number generator and is slow if you want to generate lots of pseudorandom strings in row, so you should take a look on /dev/urandom too.

I've heard some security experts recommending the use of cellular keypad and three or four random words, but all sorts of passwords which require the attacker to know the substitute cipher and implement dictionary attack to crack it are flawed by design.

Using random words could be reasonable if the number of words is around 10 and the password is changed often - you must change password more often than it would take for an attacker to crack it.

There is also the option of using some long sentences known only to you, in that case more punctuation marks - the better. And you also have to take care not to over- or underuse the sentence in normal conversations as both can raise suspicions in a determined attacker who might attempt social engineering.

In any case you must be sure not to use same password in multiple places and if you store some passwords, then they should be encrypted with strong algorithm (AES-256 for example) and you really should take care to protect the repository's password.

---

### Post by BkkBonanza on 2010-01-02
I've never seen a study of sentence/phrase passwords but I suspect that due to the structure of grammar it's likely that grammatically correct sentences have a much lower element of randomness.

Likely someone has looked into this. For example, if sentences follow a structure along the lines of <subject><verb><object> etc. The possible words that fit each of these terms is far reduced compared to random words. For each part of speech there is very few choices with the exception of adjectives, nouns maybe, where there would be many. I think mathematically it may prove to be weak.

---

### Post by crichard on 2010-01-06
Try this post to get some basic ideas about making of strong password. 
[http://surferzworld.com/?p=151](http://surferzworld.com/?p=151)
Nothing is written in stone, Itz all about the combinations of idea & creativity.

---

### Post by bodhi.zazen on 2010-01-06
A password is considered "strong" based on several characteristics

Length
Randomness 
Mix of UPPER lower numbers, and symbols 

There are several strategies to help you keep your "strong" password in mind, start with a word or phrase and "mix it up"

I think the key is to avoid short one word passwords with no symbols or numbers, such passwords are very easily cracked (dictionary attacks are very fast).

---

### Post by euler_fan on 2010-01-08
Let's not forget what the definition of a strong password is: One which for a given authentication system requires a `long' time is requires before an attacker has a given probability of having guessed it at random.

This requires two assumptions:
1) That the attacker has no better option than a random attack and 
2) That we know what `long' means and what our acceptable probability are.

Suppose we have a set of passwords, P with size Np, from which we chose one as our own. Then if we can test a fixed number of passwords per unit of time, say Rp, then the probability of having guessed the correct password after a certain number of time intervals (T) is T*Rp/Np. Ergo, for a given probability of guessing the password, the time interval between password changes is fixed.

Note: this forms an upper limit on the time required because it is for the perfect brute force attack case where the probability of choosing any member of P is equal. However, this simply isn't true for the overwhelming majority of passwords, therefore the threat posed by dictionary and other attacks. Yet it is almost true when using well-generated (pseudo)random passwords (a 36-sided die cast 10 times, for instance) or when including a (pseudo)random salt.

No matter how you generate a password the key is for T*Rp/Np to be less than your acceptable probability. But this requires us to know and respect our assumptions.

---

### Post by BenAshton24 on 2010-01-08
My old method: 

Note: if you think this is complex you should see my new one :P

1) Take your name (eg. BenAshton) and MD5 it (a3de03bd83b01639168681ca741dbf26)

2) Take all of the odd characters (ad0b8b13188c71b2) and remove the letters (0813188712)

3) Now think of a weak password (eg. "password")

4) Use each number from step 2 to move each character along the alphabet, for example, the second number is 8 so 'A' would become 'I'. (pitvxwzk)

5) Now intersperse the even numbers (33306966146) from the MD5 within the password (3p3i3t0v6x9w6z6k1)

6) Now, take the prime factors of the even numbers from the MD5 (2, 29, 4987, 115151) and combine them into a string (2294987115151). The first number (2) represents the position within your password, the second number represents the symbol that is above it on your keyboard (2=") and so on until you have 4 symbols inserted. 

7) You will end up with something like this: 3p"3i3t!0v*$6x9w6z6k1

7) Now you must learn your epic password... I suggest typing it many, many times :P

---

