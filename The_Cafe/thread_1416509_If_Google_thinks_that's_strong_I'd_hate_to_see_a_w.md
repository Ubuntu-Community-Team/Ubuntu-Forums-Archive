---
title: "If Google thinks that's strong I'd hate to see a weak one!"
date: 2010-02-26
forum: The Cafe
---

### Post by t0p on 2010-02-26
Yesterday I was helping out one of my more technologically-challenged friends.  He'd forgotten his Gmail password and didn't know what to do, so I went about changing it for him.

In common with many other computer users, my friend is totally incapable of remembering strong passwords.  Against my advice, he wanted to use an 8-digit number.  Unwise, but it's his life.  So I set the new password.

When you set a Google password, there's a "password strength indicator" that tells you if it's "weak", "fair" or "strong".  I'm not sure if there are other grades of strength used.  I typed in the 8-digit number, hit <Tab>, and the indicator said: *Strong*!

Now I know for a fact that an 8-digit number is *not* a strong password.  So I did a little experiment.  I tried an 8-letter dictionary word: that was "Fair". I tried an 8-letter dictionary word spelt backwards: that was "Strong"!

Why would Google want to mislead its users about the strength of their passwords?

---

### Post by hobo14 on 2010-02-26
"Strong", "fair", "weak" are all subjective.

---

### Post by Bachstelze on 2010-02-26
> **hobo14 said:**
> "Strong", "fair", "weak" are all subjective.

No, they're not. The strength of a password is proportional to the computing power needed to crack it, which is very well defined and not subjective at all.

---

### Post by hobo14 on 2010-02-26
> **Bachstelze said:**
> No, they're not. The strength of a password is proportional to the computing power needed to crack it, which is very well defined and not subjective at all.

I beg your pardon?
They most certainly are subjective.
If not, please tell me the precise definition of a "strong" password (a figure representing the processing power needed at the the point between "fair" and "strong" and the time limit within which it must complete will be sufficient.)

---

### Post by t0p on 2010-02-26
> **hobo14 said:**
> "Strong", "fair", "weak" are all subjective.

Of course you're right.  That's what I said in the thread title.  I'm interested to know if the security wonks at Google truly believe an 8-digit number or 8-letter dictionary word spelt backwards are strong passwords.  And if they don't believe that, why are they encouraging their users to believe it?

---

### Post by SomeGuyDude on 2010-02-26
Google attempts to be more "user friendly", so they're not going to badger people to pick wonked out passwords like 3r#$gYy6gTW.

For what it's worth, I've always used words as passwords unless the site literally won't let me log in without numbers and I've never had an issue.

---

### Post by t0p on 2010-02-26
> **SomeGuyDude said:**
> 
For what it's worth, I've always used words as passwords unless the site literally won't let me log in without numbers and I've never had an issue.

I daresay most people who use dictionary words as passwords never have any problem.  But if someone decides to pick on your account, a password like that will *not* keep them out.

Maybe you think that's paranoid talk.  But remember: many Gmail/Yahoo/Hotmail accounts are "hacked" *every day* - by crooks, by jealous boyfriends, by enemies... by anyone.  There's also the fact that if you find someone's email account password, there's a very good chance that someone uses the same password for other sites.  Maybe very sensitive sites (like banks, or pr0n).

Using strong passwords is an important online habit, and I think companies like Google ought to do try and encourage it.

---

### Post by hobo14 on 2010-02-26
> **t0p said:**
> Of course you're right.  That's what I said in the thread title.  I'm interested to know if the security wonks at Google truly believe an 8-digit number or 8-letter dictionary word spelt backwards are strong passwords.  And if they don't believe that, why are they encouraging their users to believe it?

Well, I think we can assume that's 64 bits, and Gmail no doubt has a lockout after a certain number of tries, and a minimum time between tries, so it's not too bad really.

The reversed word might be more of a concern, but I have no idea how common reversed dictionary attacks are...?

---

### Post by t0p on 2010-02-26
> **hobo14 said:**
> Well, I think we can assume that's 64 bits, and Gmail no doubt has a lockout after a certain number of tries, and a minimum time between tries, so it's not too bad really.

The reversed word might be more of a concern, but I have no idea how common reversed dictionary attacks are...?

The reversed dictionary attack is a very well-known attack vector, as a look at [this page]("http://www.google.co.uk/#hl=en&newwindow=1&safe=off&ei=zMGHS_6PI4Sy0gTB_OHJCw&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAUQBSgA&q=reverse+dictionary+attack&spell=1&fp=c6c9946001627c7b") will demonstrate.  There are a lot of reversed dictionaries and dictionary-reversing tools out there for the crook to download and use.  It's certainly something every internet user should be aware of.  Unfortunately, most users don't even think about *regular* dictionary attacks.

You're right about password retry limits on Google sites; though I believe there are ways to circumvent this.  My main gripe is that Google *encourages* the use of weak passwords with its password so-called strength indicator; and if a user uses a weak password for Gmail, he'll probably use weak passwords elsewhere.  Google really should be more security-conscious: they've been "hacked" often enough.

---

### Post by hobo14 on 2010-02-26
> **t0p said:**
> The reversed dictionary attack is a very well-known attack vector, as a look at [this page]("http://www.google.co.uk/#hl=en&newwindow=1&safe=off&ei=zMGHS_6PI4Sy0gTB_OHJCw&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAUQBSgA&q=reverse+dictionary+attack&spell=1&fp=c6c9946001627c7b") will demonstrate.  There are a lot of reversed dictionaries and dictionary-reversing tools out there for the crook to download and use.  It's certainly something every internet user should be aware of.  Unfortunately, most users don't even think about *regular* dictionary attacks.
Ah, I see.  Does make the "strong" reversed word seem dubious...

> You're right about password retry limits on Google sites; though I believe there are ways to circumvent this.  My main gripe is that Google *encourages* the use of weak passwords with its password so-called strength indicator; and if a user uses a weak password for Gmail, he'll probably use weak passwords elsewhere.  Google really should be more security-conscious: they've been "hacked" often enough.
I think the usability excuse ids probably right.  I know that I personally hate being forced to add symbols or digits to a password when I wasn't planning to.

---

### Post by t0p on 2010-02-26
> **hobo14 said:**
> 
I think the usability excuse ids probably right.  I know that I personally hate being forced to add symbols or digits to a password when I wasn't planning to.

Oh for sure!  Password requirements like that are a real pain.  If I decide to use a combination of letters and special characters (like #@!&) and a message pops up telling me I have to use numbers, I want to growl.  I'm not suggesting that Google makes requirements like that.  just a more truthful strength meter (and suggestions on how to strengthen a password) would do.

Google often errs on the side of usability rather than security.  I understand why they do this - but I still think it's wrong.

---

### Post by sameden on 2010-02-26
i think google works on a system of compering passwords with other passwords so commen passwords are "weak" and uncommen passwords are "strong".
 
what i think is happaning is peaple dont use what they think weak passwords are and using more strong passwords so as more people use strong passwords they become more weak as more user will be suing them and so called weak password will become strong.
 
this is only a thought btw
 
sam

---

### Post by hobo14 on 2010-02-26
> **t0p said:**
> Oh for sure!  Password requirements like that are a real pain.  If I decide to use a combination of letters and special characters (like #@!&) and a message pops up telling me I have to use numbers, I want to growl.  I'm not suggesting that Google makes requirements like that.  just a more truthful strength meter (and suggestions on how to strengthen a password) would do.

Google often errs on the side of usability rather than security.  I understand why they do this - but I still think it's wrong.

"Truthful" is not applicable to something subjective, "cautious" would be much better.

I'm comfortable using 8 byte passwords for things like my personal email, but I see your point.

---

### Post by nothingspecial on 2010-02-26
I always use the same 2 easy to remember words, then choose different combinations of ways to mix them up periodically.

For example


```
rolling stones
```

mix them one letter at a time
```

rsotlolniensg
```

move each letter 3 spaces up the alphabet
```

uvrworoqlhqvj
```

Roman numerals become numbers and o becomes 0

```
u5rw0r0q50hq5j
```

So I always know the starting point. I find it easier to remember the current "trick" than a random collection of letters and numbers.

---

### Post by sameden on 2010-02-26
wow thats clever i may try that the next time i need a password
 
if google dident lock your account after so meny atemps to sing in, some dir atk programs run the atk with dir words then it runs patterns like that to hack the acount
but that would make the password strong tho
 
sam

---

### Post by t0p on 2010-02-26
> **sameden said:**
> wow thats clever i may try that the next time i need a password
 
if google dident lock your account after so meny atemps to sing in, some dir atk programs run the atk with dir words then it runs patterns like that to hack the acount

The only way an attacker could hit on a password like u5rw0r0q50hq5j would be if he was making a brute force attack.  And the time a brute force attack would take to hit on a password like that, with numbers and letters... well, it would take a long time.  A *very* long time. According to [this site]("http://lastbit.com/rm_bruteforce.asp"), such an attack could take considerably longer than 6 years, assuming the attacker knows the password contains only lower case letters and numbers.  If the attacker wanted to check for all printable ASCII characters, it could take considerably longer than 44530 years!

Fortunately for the attacker, he doesn't need to bother with brute force.  Most users use dictionary words.  And a dictionary attack would generally be a lot faster.

> **sameden said:**
> 
but that would make the password strong tho
 

Sorry sameden, but I don't understand what you mean about weak passwords becoming strong or vice versa.

---

### Post by nothingspecial on 2010-02-26
> **t0p said:**
>  such an attack could take considerably longer than 6 years, assuming the attacker knows the password contains only lower case letters and numbers.  


You can make another rule - change numbers to alternate lower, upper case letters and change letters to their alphabet number

```
u5rw0r0q50hq5j
```

becomes

```
21FiVe1823ZeRo23ZeRo22FiveZeRoEiGhT22fIvE10
```

All from "rolling stones" The possibilities are endless ;)

---

### Post by Keyper7 on 2010-02-26
> **t0p said:**
> You're right about password retry limits on Google sites; though I believe there are ways to circumvent this.

I think you need to elaborate on that, because I'd guess that's exactly what Google relies on. Circumventing a password retry limit is not exactly drinking a cup of tea, specially for the average jealous boyfriend.

With the possibility of full-fledged dictionary attacks being low, then a non-stupid (examples of stupid: your name, your surname, "password", etc.) dictionary word is not a bad password.

If I were to guess, I'd say that most of the so-called "hackings" on webmails were actually just clever or not-so-clever guesswork, based on how much the attacker knew about the person.

---

### Post by Keyper7 on 2010-02-26
> **nothingspecial said:**
> ```
21FiVe1823ZeRo23ZeRo22FiveZeRoEiGhT22fIvE10
```

Ok, if you're going with this level of rubbishness then it's just easier to take the md5sum.

rolling stones => fbf9efeb49e11c657c791d6b02807a45

voilà :)

---

### Post by undecim on 2010-02-26
an 8 digit password really is just as strong as a few words from the dictionary.

Seriously, unless its something like 12345678, it's not a password that crackers are likely to try.

As far as passwords go, my passwords are usually a random sentence. It can be really simple, but it will be hard to break, and easier to associate with that particular web site. (weird how the brain remembers more information better than less information.)

---

### Post by nothingspecial on 2010-02-26
> **Keyper7 said:**
> Ok, if you're going with this level of rubbishness then it's just easier to take the md5sum.

rolling stones => fbf9efeb49e11c657c791d6b02807a45

voilà :)

It`s an example of how to remember a gibberish password, or rather to figure it out if you forget it...... of course you shouldn`t have to work it out each time, but if you do forget it you can.


Some people would say Helloween were on a whole new planet of > **Keyper7 said:**
> rubbishness

I happen to quite like them though ;)

> **Keyper7 said:**
> rubbishness is subjective :P

---

### Post by Old_Grey_Wolf on 2010-02-26
At work I have been required to use strong passwords for years. Strong being defined as, at least 8 characters comprised of at least one of each of the following, upper case alpha character, lower case alpha character, special character, and numeric character. They do not prevent the alpha characters from being a dictionary word, which, is something I use as part of the definition of a strong password. The password has to be changed every month, and can not be one that has recently been used.

That doesn't mean I can't hack someones account at work rather easily. If the employee is named "John Doe", the account ID is jdoe or doej. Because they have to change it often, many people use some simple way of remembering their password. I can tell you that a lot of employees use something like what "John Doe" might use. Password = John#001 (first month), John#002 (second month),...John#012 (twelfth month). Notice that the password satisfies the company's definition of a strong password; however, not by my definition. 

:lolflag:

---

### Post by hessiess on 2010-02-26
> **Keyper7 said:**
> Ok, if you're going with this level of rubbishness then it's just easier to take the md5sum.

rolling stones => fbf9efeb49e11c657c791d6b02807a45

voilà :)

Or use a cryptographically strong, maximum entropy random number generator.

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

Just tacking the MD5 of a word is not secure because the attacker can just preform a normal dictionary attack, with the addition of an MD5 function;)

---

### Post by Post Monkeh on 2010-02-26
> **hessiess said:**
> Or use a cryptographically strong, maximum entropy random number generator.

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

Just tacking the MD5 of a word is not secure because the attacker can just preform a normal dictionary attack, with the addition of an MD5 function;)

i think the whole point is that his method gives him a random password that actually isn't random to him so it's easy to guess if he forgets it. easy to guess for him that is, not someone else, it's a pretty good system.

---

### Post by nothingspecial on 2010-02-26
> **Post Monkeh said:**
> i think the whole point is that his method gives him a random password that actually isn't random to him so it's easy to guess if he forgets it. easy to guess for him that is, not someone else, it's a pretty good system.

I think we have a winner here :D

---

### Post by Keyper7 on 2010-02-26
> **nothingspecial said:**
> It`s an example of how to remember a gibberish password, or rather to figure it out if you forget it...... of course you shouldn`t have to work it out each time, but if you do forget it you can.

I know, I was joking. :)

Not *completely* joking, though. Taking the md5sum *would* be easier for me, as I certainly cannot tell all letters by their alphabet order, not very fast at least.

---

### Post by Keyper7 on 2010-02-26
> **hessiess said:**
> Just tacking the MD5 of a word is not secure because the attacker can just preform a normal dictionary attack, with the addition of an MD5 function;)

But of course, the attacker needs to figure out he must do that in the first place. And if he does, one pinch of salt can make his life much more difficult.

---

### Post by nothingspecial on 2010-02-26
> **Keyper7 said:**
> I know, I was joking. :)

Not *completely* joking, though. Taking the md5sum *would* be easier for me, as I certainly cannot tell all letters by their alphabet order, not very fast at least.

The point is you try to remember it......but if you forget ......

---

### Post by t0p on 2010-02-26
> **undecim said:**
> an 8 digit password really is just as strong as a few words from the dictionary.

I disagree.  If you use an 8-digit number, there are only 100,000,000 variations.  According to t[his site]("http://lastbit.com/rm_bruteforce.asp"), it's possible to try 500,000 different passwords per second.  That's probably a bit conservative - [this site]("http://mandylionlabs.com/PRCCalc/misconcept_more.htm") says 17 billion per hour - but let's err on the side of caution and stick with 500,000 per second.  At that rate, you could try every variation of the 8-digit number in 200 seconds - a little over 3 minutes.  (If I've made a mistake in my arithmetic,  I'm sure someone will point it out.)

> **undecim said:**
> 
Seriously, unless its something like 12345678, it's not a password that crackers are likely to try.


Surely you can see what's wrong with that statement?

---

### Post by aysiu on 2010-02-26
I think Google is just trying to be practical.

For the vast majority of computer users, having a mostly weak password is already a great accomplishment (because they would much prefer a totally weak password).

If you at least encourage the folks who have a mostly weak password then the chances are that much slimmer their accounts will be cracked. For that segment of the population (and it's a huge segment), it's futile to try to get them to use an actually fair or strong password. If Google insisted on that, people would just ditch GMail for Yahoo! or Hotmail.

---

### Post by doas777 on 2010-02-26
> **sameden said:**
> i think google works on a system of compering passwords with other passwords so commen passwords are "weak" and uncommen passwords are "strong".
 
what i think is happaning is peaple dont use what they think weak passwords are and using more strong passwords so as more people use strong passwords they become more weak as more user will be suing them and so called weak password will become strong.
 
this is only a thought btw
 
sam

password strenght is a factor of the size of the charater set required to bruteforce teh password. 
an 8 digit numeric password has 8^10 possible combinitations.
an 8digit alphabetic has 8^52
an 8digit alphanumeric has 8^62
and 8digit alphanumeric with special has 8^72 possible. 

just a factor of time and cpu power.

---

### Post by tacantara on 2010-02-26
Perhaps the future of secure password computing lies in smart card technology.  I use a smart card to access my web-based Army e-mail from home and when logging onto government computers when I'm on active military duty.  It is probably too costly now for all web-based e-mail and business sites to adopt, and there's always the "what if my smart card isn't working" or "what if I lose my smart card."  With my web-based Army e-mail, I have an option to sign in using a strong password, then answer three "security questions" that I set up on the account.

IMO, smart card technology is pretty decent as a security tool.  Perhaps it will also be extended to credit cards.  Imagine not having to worry about your credit card number being compromised, because it's not embossed on the card.

---

### Post by Post Monkeh on 2010-02-26
> **t0p said:**
> I disagree.  If you use an 8-digit number, there are only 100,000,000 variations.  According to t[his site]("http://lastbit.com/rm_bruteforce.asp"), it's possible to try 500,000 different passwords per second.  That's probably a bit conservative - [this site]("http://mandylionlabs.com/PRCCalc/misconcept_more.htm") says 17 billion per hour - but let's err on the side of caution and stick with 500,000 per second.  At that rate, you could try every variation of the 8-digit number in 200 seconds - a little over 3 minutes.  (If I've made a mistake in my arithmetic,  I'm sure someone will point it out.)



Surely you can see what's wrong with that statement?

500000 is 36 billion per hour, so it's not really more conservative. ;)

---

### Post by Lightstar on 2010-02-26
my facebook password is 48 characters long :)

---

### Post by SomeGuyDude on 2010-02-26
> **t0p said:**
> I daresay most people who use dictionary words as passwords never have any problem.  But if someone decides to pick on your account, a password like that will *not* keep them out.

Maybe you think that's paranoid talk.  But remember: many Gmail/Yahoo/Hotmail accounts are "hacked" *every day* - by crooks, by jealous boyfriends, by enemies... by anyone.  There's also the fact that if you find someone's email account password, there's a very good chance that someone uses the same password for other sites.  Maybe very sensitive sites (like banks, or pr0n).

Using strong passwords is an important online habit, and I think companies like Google ought to do try and encourage it.

Here's what I think, though:

1) Actual hackers will not be deterred by your fancy-pants password. It might take a little while longer, but they'll get it.

2) As long as your password isn't something stupid or obvious like "password" or "qwerty", most tech-dumb crooks aren't going to get it at all. If your password is "albedo" or "PuddingPop" no one's gonna freakin' guess that.

3) I'm talking about casual use, obviously. Banks and such would want to take every possible precaution.

More complex passwords are like extra locks on your front door. Someone who's just jiggling the handle and trying a credit card will get stopped by just a simple deadbolt, and serious thieves will smash the door down even if you have six locks and an extra chain.

---

### Post by jflaker on 2010-02-26
The only strong password is not using a Pass WORD, but a PASS PHRASE.

Once you pick your phrase, which should be a full sentence you will easily remember.....THEN change up some letters for look-alike numbers and some numbers for look alike letters.

I want to go to the STORE at 6

becomes

1 wan7 70 60 70 7h3 57or3 at G

Now we have a pass PHRASE that is essentially immune to a dictionary attack...and makes no sense to anyone except the user.

Phrases are the only way to be immune (almost) from hackers unless they are willing to spend an exceptional amount of resource to get your account.  Normally, after a short amount of time, they will move on to lower hanging fruit, like those who have stupidly simple pass WORDS.

---

### Post by SomeGuyDude on 2010-02-26
By that same logic, just typing "p@ssw0rd" is immune to a dictionary attack. Or take your favorite movie and 1337 it up. No need for these gigantic 50 character monstrosities.

---

### Post by jflaker on 2010-02-26
> **SomeGuyDude said:**
> By that same logic, just typing "p@ssw0rd" is immune to a dictionary attack. Or take your favorite movie and 1337 it up. No need for these gigantic 50 character monstrosities.

"P@55word" is much more immune to being broken EASILY than "Password"  As you start adding spaces and more words, the hacker is likely to move on to easier prey.  Nothing is unhackable, it depends on how much time and resources the hacker wants to invest on a single account before they move on to easier prey.

Which is why I say you should you a pass-PHRASE, which will consist of more "randomly" placed spaces and does not consist of real words as you replace some letters or numbers with numbers or letters.

MOST internet users have rediculously small words as their passwords and can be hacked in a few minutes....

---

### Post by nmccrina on 2010-02-26
> **Post Monkeh said:**
> 500000 is 36 billion per hour, so it's not really more conservative. ;)

One of us is confused...500000/sec * 3600 sec/hr = 1,800,000,000/hr?

---

### Post by SomeGuyDude on 2010-02-26
I just see this whole "more complex the better" culture as similar to the Windows users who take pride in the fifty various security suites they run at the same time or people who install outlandish security systems in their houses.

The only people any of us have any real reason to worry about are people in our lives, and believe me no one I know personally is smart enough to guess anything I use. As for the actual hackers? Well if they REALLY want to get into my gmail or facebook accounts, they'll get 'em.

Footnote: I use "shapes" for important stuff like banking/loans/etc. I pick a shape on my keyboard and hit the keys that draw it out. That strikes me as an instance where semi-stupid hackers WOULD just grab names at random and try to guess stuff for a while.

---

### Post by Post Monkeh on 2010-02-26
> **nmccrina said:**
> One of us is confused...500000/sec * 3600 sec/hr = 1,800,000,000/hr?

yeah, i must have typed an extra zero. and a 2 :D
in my defence i'm a bit tipsy

---

### Post by t0p on 2010-02-26
> **SomeGuyDude said:**
> By that same logic, just typing "p@ssw0rd" is immune to a dictionary attack. Or take your favorite movie and 1337 it up. No need for these gigantic 50 character monstrosities.

I take it you've never used John the Ripper.  John can transform the contents of a dictionary file according to a huge number of rules, including changing words into L337 speak. 

You're right that there's no need for a "gigantic 50 character monstrosity".  But using a weak dictionary word of 8 characters or under won't do you too much good if there are attackers out there who want to get into your stuff.

---

### Post by SomeGuyDude on 2010-02-26
> **t0p said:**
> I take it you've never used John the Ripper.  John can transform the contents of a dictionary file according to a huge number of rules, including changing words into L337 speak. 

You're right that there's no need for a "gigantic 50 character monstrosity".  But using a weak dictionary word of 8 characters or under won't do you too much good if there are attackers out there who want to get into your stuff.

And any serious attackers, who really want to get into your stuff, aren't going to be stopped by anything outside of a monstrous encryption. So for email and pizzahut.com I just pick my usual categories, then for my student loans and banking and whatever else it's my shapes.

---

### Post by hobo14 on 2010-02-26
> **SomeGuyDude said:**
> Here's what I think, though:

1) Actual hackers will not be deterred by your fancy-pants password. It might take a little while longer, but they'll get it.

I'd like to see ANYONE or anything crack a 50 character password that didn't use dictionary words.

> **doas777 said:**
> password strenght is a factor of the size of the charater set required to bruteforce teh password. 
an 8 digit numeric password has 8^10 possible combinitations.
an 8digit alphabetic has 8^52
an 8digit alphanumeric has 8^62
and 8digit alphanumeric with special has 8^72 possible. 

just a factor of time and cpu power.
You mean 10^8, of course...

> **t0p said:**
> I disagree.  If you use an 8-digit number, there are only 100,000,000 variations.  According to t[his site]("http://lastbit.com/rm_bruteforce.asp"), it's possible to try 500,000 different passwords per second.  That's probably a bit conservative - [this site]("http://mandylionlabs.com/PRCCalc/misconcept_more.htm") says 17 billion per hour - but let's err on the side of caution and stick with 500,000 per second.  At that rate, you could try every variation of the 8-digit number in 200 seconds - a little over 3 minutes.  (If I've made a mistake in my arithmetic,  I'm sure someone will point it out.)

You can't try 500,000 per second on Gmail though.  You'd be lucky if they let you try 1 per second.

The attacker would have to know that you used only digits before being able to narrow it down to 100,000,000.  
Otherwise using the whole keyboard 8 characters would be 
94^8 (6*10^15 ==> 380 years at 500,000/sec), 
or if using all 64 bits 
2^64 (18*10^18 ==> more than 1 million years at 500,000 per second)

---

### Post by TheNessus on 2010-02-26
> **t0p said:**
> Yesterday I was helping out one of my more technologically-challenged friends.  He'd forgotten his Gmail password and didn't know what to do, so I went about changing it for him.

In common with many other computer users, my friend is totally incapable of remembering strong passwords.  Against my advice, he wanted to use an 8-digit number.  Unwise, but it's his life.  So I set the new password.

When you set a Google password, there's a "password strength indicator" that tells you if it's "weak", "fair" or "strong".  I'm not sure if there are other grades of strength used.  I typed in the 8-digit number, hit <Tab>, and the indicator said: *Strong*!

Now I know for a fact that an 8-digit number is *not* a strong password.  So I did a little experiment.  I tried an 8-letter dictionary word: that was "Fair". I tried an 8-letter dictionary word spelt backwards: that was "Strong"!

Why would Google want to mislead its users about the strength of their passwords?

upon installing ubuntu it prompts for a pass and it has an indicator too. try the same pass and tell us it is also says "strong". and then complain about google.

---

### Post by Keyper7 on 2010-02-26
> **nothingspecial said:**
> The point is you try to remember it......but if you forget ......

...I will still remember the very simple original word and therefore can calculate the md5 again with a single command line.

Easier than having to remember a whole bunch of replacement rules and the order they should be applied.

(for me at least)

---

### Post by nothingspecial on 2010-02-26
> **keyper7 said:**
> ...i will still remember the very simple original word and therefore can calculate the md5 again with a single command line.

Easier than having to remember a whole bunch of replacement rules and the order they should be applied.

(for me at least)

ok

---

### Post by HalfWord on 2010-02-26
Concerning password strength, I think it would be more appropriate to consider rainbow tables than brute force attack nowadays. Rainbow tables can significantly accelerate password cracking, so I guess "strong" passwords would be ones that cannot be cracked in a shorter time than several months or years on a fastest modern PC.

Of course, the same password could be cracked much faster using massively parallel machines, crypto-accelerator chips and good parallelization and cryptanalysis algorithms. However, any  protected information that is worth less than the cost of obtaining it is considered safe ;)

For a method to obtain "random" letters which are easy to remember, I've often used initials of some song lyrics or names I know quite good :D
For example, Ray Charles' "I can't stop loving you" provided icsly, Tina Turner's "We don't need another hero" gave wdnah, and using complete verses could give sequences like AyltDymmtAyswda (from an Elvis song) which are actually "replayed" every time if you know where does it come from... And if you add an interpunction sign and a numbe it foils password cracking attempts (no real need to be more than just one of each, although more of them does add strength, the first one does it tremendously, while others simply act to lengthen the password, which would a plain letter do equally well.)

Oh btw, please don't say "password 'hacking'", use "password 'cracking'" instead ;)

---

### Post by sameden on 2010-02-28
> **Lightstar said:**
> my facebook password is 48 characters long :)

OTT :p i didnt know that facebook would allow that long password and how do you remember that

---

### Post by t0p on 2010-02-28
> **TheNessus said:**
> upon installing ubuntu it prompts for a pass and it has an indicator too. try the same pass and tell us it is also says "strong". and then complain about google.

So I can complain about Google's password strength indicator only if Ubuntu's indicator is better?  How did this state of affairs come about?  Who died and made Ubuntu the universal yardstick of computer security?

---

### Post by undecim on 2010-02-28
> **t0p said:**
> I disagree.  If you use an 8-digit number, there are only 100,000,000 variations.  According to t[his site]("http://lastbit.com/rm_bruteforce.asp"), it's possible to try 500,000 different passwords per second.

That is for passwords for applications on a personal computer where you already have the encrypted form of the password, not web apps like gmail where the server has to hash it, intentionally delays you, and locks you out after three tries.

most attackers will just try stuff like "12345", "monkey", and other common passwords before moving on to the next potential victim.

Most crackers won't spend much time on any particular person, unless they are targeting that person specifically. And then, cracking a password is much less practical then, for example, going to the victims facebook page to find the answer to a security question.

---

### Post by t0p on 2010-02-28
> **undecim said:**
> That is for passwords for applications on a personal computer where you already have the encrypted form of the password, not web apps like gmail where the server has to hash it, intentionally delays you, and locks you out after three tries.

most attackers will just try stuff like "12345", "monkey", and other common passwords before moving on to the next potential victim.

Most crackers won't spend much time on any particular person, unless they are targeting that person specifically. And then, cracking a password is much less practical then, for example, going to the victims facebook page to find the answer to a security question.

All true.  But is any of that a reason to use a weak password?  I don't think so.  Nor do I think "I can't remember long passwords" is an excuse.

There's an awful lot of identification theft and other such stuff going on.  And it's only going to get worse.  If you can't be bothered to protect yourself, why should anyone else bother?  To protect you, I mean.

---

### Post by sameden on 2010-03-09
> **t0p said:**
> All true. But is any of that a reason to use a weak password? I don't think so. Nor do I think "I can't remember long passwords" is an excuse.

 
something that migh help people to remeber passwords is to use a program that keeps your passwords in a bank or something and will enter it in to a site if the user need it to.
this would allow the user to use long complex passwords.
 
sorry i dont know any programs that do this of by hart.

---

### Post by Tristam Green on 2010-03-09
Here's a thought.  Keep your personal data on paper and in a fireproof safe.  Take email completely out of the equation.

That's some tight security right there.

---

### Post by Tristam Green on 2010-03-09
> **t0p said:**
> All true.  But is any of that a reason to use a weak password?  I don't think so.  Nor do I think "I can't remember long passwords" is an excuse.

There's an awful lot of identification theft and other such stuff going on.  And it's only going to get worse.  If you can't be bothered to protect yourself, why should anyone else bother?  To protect you, I mean.

Because people live far too short a life to be fearful of "someone stealing my identity".

Identity theft is the biggest crock of hooey I've *ever* seen.  **NOBODY, AND CERTAINLY NOT A FREAKING NUMBER**, is going to tell ANYONE who I am.  That's up to me.  If they don't feel like believing me, then that's their damned problem.

---

### Post by DawieS on 2010-03-09
> **Tristam Green said:**
> Identity theft is the biggest crock of hooey I've *ever* seen.  **NOBODY, AND CERTAINLY NOT A FREAKING NUMBER**, is going to tell ANYONE who I am.  That's up to me.  If they don't feel like believing me, then that's their damned problem.
You would probably feel different about this if you wake up one morning, only to find out that your bank account has been wiped clean...

Or even worse, you start receiving notices of bond repayments on your house, that you know nothing about.

Last year a guy in England came home from holiday, only to find out that he has sold his house to someone else, and that this someone has taken out a bond on the house, and has now disappeared with the money.

The subsequent court case was controversial, in that they handed him back his house, but he was held liable to re-pay the bond. The arguments in court were that he failed to take reasonable steps to protect his identity. His mailbox was left open, bulging with unopened mail, making it easy for everyone to steal his identity, while he was on holiday.

---

### Post by Tristam Green on 2010-03-09
> **DawieS said:**
> You would probably feel different about this if you wake up one morning, only to find out that your bank account has been wiped clean...

Or even worse, you start receiving notices of bond repayments on your house, that you know nothing about.

Last year a guy in England came home from holiday, only to find out that he has sold his house to someone else, and that this someone has taken out a bond on the house, and has now disappeared with the money.

The subsequent court case was controversial, in that they handed him back his house, but he was held liable to re-pay the bond. The arguments in court were that he failed to take reasonable steps to protect his identity. His mailbox was left open, bulging with unopened mail, making it easy for everyone to steal his identity, while he was on holiday.

That's a classic case of utter stupidity though.  Protecting your *assets* like your mail, your bank information, etc. is fine and well.

---

### Post by TheNessus on 2010-03-09
> **t0p said:**
> So I can complain about Google's password strength indicator only if Ubuntu's indicator is better?  How did this state of affairs come about?  Who died and made Ubuntu the universal yardstick of computer security?
You attack Google in particular for something nearly all companies and services that offer a password do. Why do you choose to criticize Google in particular then? Best to check if others do the same, and then make a general complain. Otherwise it's just pointless Google-bashing; a very popular (and pointless) thing to do.

---

### Post by doas777 on 2010-03-09
> **TheNessus said:**
> You attack Google in particular for something nearly all companies and services that offer a password do. Why do you choose to criticize Google in particular then? Best to check if others do the same, and then make a general complain. Otherwise it's just pointless Google-bashing; a very popular (and pointless) thing to do.


because the op started a thread after seeing somthing on google. this is not some megamaniacal attempt at "google-bashing" as you put it.  stimulus -> response.
bashing a user because they said somthing you don't like about <insert proper noun here> company, as part of a conversation, is far more disruptive than someone complaining about a 3rd party that is not participating in the conversation.

---

### Post by Toddus on 2010-03-09
Is it really that inconvenient to have to had a couple numbers at the end and capitalize the first letter of your password?
It might not be the "strongest" password for some of you, but you don't need a 32-bit encryption for your e-mail and so forth. 

Only thing that is the real weakness here is most people, use the same password for 90% of their internet/computer use. Get one, you most likely have them all.

Also, finger print reader for the win, that way you don't have to remember 30 passwords.

---

### Post by phrostbyte on 2010-03-09
[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

---

### Post by doas777 on 2010-03-09
> **Toddus said:**
> Is it really that inconvenient to have to had a couple numbers at the end and capitalize the first letter of your password?
It might not be the "strongest" password for some of you, but you don't need a 32-bit encryption for your e-mail and so forth. 

Only thing that is the real weakness here is most people, use the same password for 90% of their internet/computer use. Get one, you most likely have them all.

Also, finger print reader for the win, that way you don't have to remember 30 passwords.

actually email is one of the most valuable assets to your computing identity that you have, since it is the nexus of all your online activities. people can learn a lot from your email (including what accounts you have where, and often login info). additionally, an email account is useful to scammers and spammers who want to relay through it.

---

### Post by doas777 on 2010-03-09
> **phrostbyte said:**
> [IMG]http://imgs.xkcd.com/comics/security.png[/IMG]
I love that one! good explaination of why stenographic volumes are often the best approach for highly sensitive data.

---

### Post by |{urse on 2010-03-09
Really the whole concept of a strong password is a bit misunderstood. Once some not-nice person cracks your password running a rainbow table across multiple (usually windows) clients rooted to a botnet that joins these clients to an irc command and control server where the cracker(s) can set all these machines about to the task of cracking your password, the discovered password is generally added to the rainbow table upon success. So really just beacause the password is alphanumeric and 8+ characters and/or integers long does not mean it hasn't been used and cracked and added to a huge rainbow table that is freely available on the net for whomever to use.

So really an 8+ alphanumeric password that is _also_ _obscure_ is the way to go.

This is most likely why your backwards dictionary password was considered strong by google.

---

### Post by |{urse on 2010-03-09
someone mentioned a 13 some char/int password taking 6 years to crack. That estimate is wrong (perhaps based on single client attacks). I have personally cracked much more sophisticated passwords and it didn't take 6 years, more like a few weeks. Its all about the size of your botnet and what table(s) you are using! (my botnet was set up on willing participants machines with a modified version of rbot purely for academic purposes.)

---

