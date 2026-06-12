---
title: "Use commands as passwords"
date: 2016-09-12
forum: Ubuntu, Linux and OS Chat
---

### Post by SnuKies on 2016-09-12
Hi guys,

Because I was working a lot on a Linux machine (openSuse), I was thinking of changing my accounts password ( gmail, Ubuntu, other sites) with a combination of personal words and ubuntu commands. Something like `sudo rm ~/my_password`

What are the changes that such commands (or other commands) will mess up the whole system?

---

### Post by pfeiffep on 2016-09-12
Maybe try it in a virtual instance ???

---

### Post by Impavidus on 2016-09-12
A command used as a password shouldn't mess up your system, unless you accidentally type your password at some place other than a password prompt. Sooner or later, you probably will. You may touch your touchpad just before typing the password, shifting the focus to a different window.

Furthermore, using commands as passwords will give you passwords vulnerable to dictionary attacks. That's not a very good idea. Unless you make the commands really long, like passphrases.

---

### Post by Habitual on 2016-09-12
> **Impavidus said:**
> A command used as a password shouldn't mess up your system, unless you accidentally type your password at some place other than a password prompt. Sooner or later, you probably will. You may touch your touchpad just before typing the password, shifting the focus to a different window.

Furthermore, using commands as passwords will give you passwords vulnerable to dictionary attacks. That's not a very good idea. Unless you make the commands really long, like passphrases.
"It sounded like a good idea"...?
And it is provocative. It just squeaks of impending doom.
</opinion>

---

### Post by SnuKies on 2016-09-13
> **Impavidus said:**
> A command used as a password shouldn't mess up your system, unless you accidentally type your password at some place other than a password prompt. Sooner or later, you probably will. You may touch your touchpad just before typing the password, shifting the focus to a different window.

Furthermore, using commands as passwords will give you passwords vulnerable to dictionary attacks. That's not a very good idea. Unless you make the commands really long, like passphrases.


But what about other accounts, like GMail, Facebook, Twitter etc?

---

### Post by Impavidus on 2016-09-13
It doesn't matter what the password is for. Using commands as passwords shouldn't give nasty effects other than making the password easy to guess, which is nasty. Unless you type it at the wrong place.

Passwords should be hard to guess. The number of possible commands in Linux is just too small to make them good passwords. If you include a long filename or path in your command, that itself may make a decent passphrase, but in that case you could drop the command part of it.

Better use things like completely random strings or sequences of random words (best with spelling errors). You can even use a proper sentence, provided it's really long – long enough to no longer fit in a Twitter message – and not a quote from any text you know of. Longer passphrases with less randomness per character are easier to memorise for the same security.

There are [password managers]("https://en.wikipedia.org/wiki/Password_manager") than can memorise your passwords for you, protected by a master password.

---

### Post by vasa1 on 2016-09-13
Moved to Chat because OP is on "openSuse" and the question isn't about Ubuntu (or "openSuse"), per se.

---

### Post by The Cog on 2016-09-13
> **Impavidus said:**
> A command used as a password shouldn't mess up your system, unless you accidentally type your password at some place other than a password prompt. Sooner or later, you probably will. 
^^^This.
You may think "Nah, not me.". But as Impavidus says, sooner or later, you probably will.
I have had to wipe my command history to remove a plain-text copy of my password quite a few times over the years.

---

### Post by Remson_Felipa on 2016-09-14
Do you want to use same password for all account

---

### Post by uNoubu8a on 2016-09-14
> **Remson_Felipa said:**
> Do you want to use same password for all account

As long as you have ***/dev/random*** in your password you would be good to go :P

---

### Post by SnuKies on 2016-09-16
> **Remson_Felipa said:**
> Do you want to use same password for all account


Kind of yes.

(Regarding the other replies) My password is a mix of inhouse terms and linux commands. 
Commands that will be used are very powerful (meaning they can delete/modify/add files), but since I've been working a lot with them, I memorized them :D

Thank you all!

---

### Post by SagaciousKJB on 2016-09-16
Try out diceware passphrases...

[https://en.wikipedia.org/wiki/Diceware](https://en.wikipedia.org/wiki/Diceware)
[https://www.rempe.us/diceware/#eff](https://www.rempe.us/diceware/#eff)

---

### Post by TheFu on 2016-09-21
> **SnuKies said:**
> Hi guys,

Because I was working a lot on a Linux machine (openSuse), I was thinking of changing my accounts password ( gmail, Ubuntu, other sites) with a combination of personal words and ubuntu commands. Something like `sudo rm ~/my_password`

What are the changes that such commands (or other commands) will mess up the whole system?

There are a few best practices for passwords worth mentioning.
a) Don't use passwords, unless absolutely necessary. 
b) Use key-based authentication, whenever possible.
c) For passwords, there is no substitute for length. Use the longest, random, passphrase possible. 55 characters is a good start.
d) Never use any words or "l33t Sp34k" in your passwords.  Random everything.
e) Never reuse passwords. Every login should have a different password - all very long, random.
f) Use a F/LOSS password manager to store passwords.  Most have "autotype", so you'll never need to manually enter credentials. They also have a random password generation tool.  Use those to create long, unique, complex, passwords.  If you never need to type them in, why not have 40+ character, completely random, passwords?
g) There are 3 passwords you should know. No more.  
[LIST]
[*]Login for the system you sit behind.
[*]Huge, long, passphrase to access the password manager
[*]huge, long, passphrase to unlock ssh-keys
[/LIST]

20 characters should be the minimum length of all passwords.  16-character passwords can be cracked in less than 24 hrs with brute force methods. [http://www.dailymail.co.uk/sciencetech/article-2331984/Think-strong-password-Hackers-crack-16-character-passwords-hour.html](http://www.dailymail.co.uk/sciencetech/article-2331984/Think-strong-password-Hackers-crack-16-character-passwords-hour.html)

**In short, if you know the password, then you've already failed from a security perspective.**

If you need temporary access to certain systems where you cannot have the password manager with you, then set a long, temporary password with 2 parts - write down the longer part, but remember a sorter part (still long).  Put the paper with the longer part with your passport/credit cards. This is a reminder that these things are very important. At login time, you have 1) something you have (the piece of paper) and something you know (memorized part).  For systems you control, it is possible to setup a one-time password-pad solution for use during travel.

If you can, use 2FA methods for targeted logins (gmail is one).  That would be a cell phone running google-authenticator or a yubikey.  Unfortunately, google doesn't allow a yukikey to be used without setting up a cellphone for authentication first. Bad, bad, bad google. SMS shouldn't be used anymore. There are multiple attacks for that.

If you care about privacy, never use credentials from 1 service on another.  Never login using your gmail/facebook/twitter logins on a 3rd party site. Why not?  [http://www.inc.com/larry-kim/you-wont-believe-all-the-personal-data-facebook-has-collected-on-you.html](http://www.inc.com/larry-kim/you-wont-believe-all-the-personal-data-facebook-has-collected-on-you.html) ... did you intend for them to know this much?  They appreciate it.

---

### Post by Roger_Williams on 2016-09-21
I just recently changed all my passwords and it was not fun. I used to use 16 character passwords I thought were secure but after reading about the power some of the password crackers have I decided it was time for an update. I use 1Password so I just use the password generator to generate 40 character passwords with symbols, numbers and random letters for all my accounts. I did the same for the secret questions as well saving them as passwords under the appropriate resource. I always say your passwords should be as secure as the importance of whatever they are protectiing.

---

