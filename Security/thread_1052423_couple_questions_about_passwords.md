---
title: "couple questions about passwords"
date: 2009-01-27
forum: Security
---

### Post by jimmy the saint on 2009-01-27
We all know, or should, that using strong passwords is an very important habit.  They should be "long" not be "based on dictionary words" and be all around PIAs.  A couple clarifying questions, since the articles I have found either dumb down the conversation to the point of worthlessness, or are written for an audience far more guru-like than I.

1) "based on dictionary words"   Does that mean "word," "word123," "WorD123" "W0r8"??  How far does that go?  Are passwords that are loosely based on a word but with most characters are replaced strong or weak?

2) I know of people who say they use passwords that are "25 characters long... randomly generated.... etc.).  How can that even be practical?  Granted, this particular guy only used a crazy PW for root, but I do root-level tasks daily (updates, installation/remove etc.) and that password would not last long around here.  How do people implement such a long, complex pw?

Thanks

---

### Post by rileinc on 2009-01-28
1) Yes, "word123" and its variants should be considered a dictionary phrase, and I'd go as far as calling "l33t" a dictionary word because it is so common. The list can also include words spell backwards. e.g., "nimda" (admin).

2) It's a personal strategy, you have to devise one yourself (or copy someone else's). 

I manage mine by scrambling a short line. 
e.g.
Ubuntu_Linux_for_Human_Beings [29 characters]
.Ubun7u*L|nux+f0r=Hum@n~B3|ng$!9 [32 characters]
[and so on...]

Take it from there, twist and replace characters as much as you can remember. The only hard part is recalling which characters have been changed. It can be random or every other character. It's up to you.

Hope this helps.

---

### Post by fluffybacon on 2009-01-28
I was taught to pick  a sentence from  a book and use the first letter from each word.  

Example:  
> NT users have years of experience (if not with NT, then with Windows 3,95,98)  

Becomes 
> 
NTuhyoe(inwNTtww39598)


Although it does sometimes take me 2 or three mins just to type my password.

---

### Post by tubbygweilo on 2009-01-28
> **fluffybacon said:**
> I was taught to pick  a sentence from  a book and use the first letter from each word.  

Example:  
 

Becomes 


Although it does sometimes take me 2 or three mins just to type my password.

And someone can see your lips move as you type;)

I have several strings of between 8 and 12 characters long and use various permutations of them to construct longer and I hope stronger pass phrases and yes you can also see my lips move as I type.

---

### Post by cdenley on 2009-01-28
First of all, you should not set a root password at all. If you need root privilege, that's what sudo is for. I think 95% of brute force attempts assume you have a root password, and try to guess it.

When people use a random 25-character password, I assume they use some sort of password manager for that password. I wouldn't be able to remember a password like that. Keeping a hard copy of your password is not safe.

Probably the dictionary they are referring to is a password dictionary. A password dictionary is a long list of commonly used passwords attackers use to guess your password. They consist of real words like "apple" or "baseball", as well as commonly used computer terms like "l33t", common variations of words, and even patterns like "qwerty" or "!@#$%^".

I feel a good compromise is to use a word you can easily remember, and add a few random numbers AND special characters (!@#$...) before or after it.

---

### Post by HermanAB on 2009-01-28
Hmm, bear in mind that most dictionaries have word lists with up to 8 characters.  That is why having a password with 9 or more characters is suggested.  I use 16 character semi-pronounceable passwords and my systems have never been hacked.

Cheers,

Herman

---

### Post by Denestria on 2009-01-28
I have long random garbage passwords that I use for important things like banking.  They are saved in KeePassX.  KeePassX itself is protected with a passphrase, make sure it's a good one!

You can set a key combo to copy/paste your login/password for websites.  Once the passphrase is entered, the database remains unlocked until you decide otherwise (or until it is closed) so you don't have to keep typing the passphrase, just type it in once for a session and then if you leave your computer you can lock it.

It also has an option in its settings to control how long the password remains in the clipboard so even if the database is locked someone can't just hit ctrl-v.  It can generate random passwords for you and allows you to select/unselect options for it like length, special characters, case, etc so you can pick whatever the website/program allows for passwords.

---

### Post by e1mer on 2009-01-28
I like the book phrase idea for a different reason.
As long as the people listening are not in 
the illuminati group, you can tell trusted people
the password in clear text.

EG: "Remember, the root password is our best 
    kept secret. Never write it down."
tells your coworker they want to type: RtrpiobksNwid

Something like that makes your passwords pretty safe.
Some places require numbers and letters, so you could
mix in numbers at punctuation: R1trpiobks2nwid

Abbreviate and add a number? No problem:
There once was a pie from Nantucket could give you the password
   Towamfn3wpwslhcsi1Hswag4ahwohc1imewacicf5

I would be impressed with any dictionary attack that knew
dirty limericks AND math. (PI:3.1415)

---

### Post by jimmy the saint on 2009-01-28
That KeePassX is the type of thing I was curious about.  Coming up with crazy long/complex passwords is the easy part, using them and still getting anything done between 10 minute password entering sessions seems to be the hard part.  I will look into that little app out of curiosity.  

I am curious if the more security conscious just remember their long passwords and type them in constantly or use password managers like that one?

---

### Post by Dr Small on 2009-01-28
> **jimmy the saint said:**
> I am curious if the more security conscious just remember their long passwords and type them in constantly or use password managers like that one?

I'm using a 10 character password that is semi-pronounceable. I use it on various websites and for system login. But, I've had it for several months and it is starting to 'feel' old. I'm probably going to change it sometime soon to something randomly generated that I can memorize. 

I have a password manager (an encrypted file!) where I store all of my logins, but I know all of my passwords by heart. So I don't use the password file for referencing my passwords.

---

