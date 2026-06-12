---
title: "Securing Ubuntu (SSH)"
date: 2005-09-15
forum: Server Platforms
---

### Post by kook44 on 2005-09-15
Hi-
I have an ubuntu box that is connected to my home router.  I'm forwarding port 22 requests to that box for ssh, and everything is working great.  I'm exposing any vulnerabilities this way?  I've ssen some stuff about encypted public keys, but isn't that just for the client connecting to the server to verify who it's connecting to?

---

### Post by LordHunter317 on 2005-09-15
No, keypairs are for doing two-factor identifaction: instead of a password, you need a password and a file to connect to.  They're totally different from host keys, which are used to verify a host is who it says it is.

You're not exposing any vulnerabilites unless your passwords aren't strong, or if a bug in SSH is found.

---

### Post by Glut on 2005-09-15
The more paranoid would disallow root logins from ssh and setup allowusers to a set of known users.

---

### Post by kook44 on 2005-09-15
[QUOTE=Glut]The more paranoid would disallow root logins from ssh and setup allowusers to a set of known users.[/QUOTE]


Isn't the root acct disabled by default in ubuntu?

---

### Post by Glut on 2005-09-16
Many users enable a root account for various reasons. If you have, reading the man page on the sshd_config should give you a few options for securing this.

---

### Post by djmadkins on 2005-09-28
Careful, many script kiddies troll the internet looking for systems like yours to try to connect to. They will try to use a dictionary attack to gain access.


Google "denyhosts" for a method that will prevent this.

---

### Post by LordHunter317 on 2005-09-28
Except the dictionary attack is pretty worthless, if you have strong passwords.

---

### Post by Kyral on 2005-09-28
Or if you happen to know the IP addresses of the computers you will be connecting from (Like a school campus). Then you can setup IPTables to block all SSH attempts that do not come from that IPBlock

---

### Post by AllFather on 2005-09-29
Not claming to be some sort of ssh guru, but there is no point in allowing root connect now is there?
 
Log on as default user insted and do a su root ?
I also never use passwords, but pass-fraces, normaly a sentence with 10-15 letters, and I find that secure anough, only takes a second to type anyho if you know how to move your fingers ;)

---

### Post by TheDanMan on 2005-09-29
A few things.

Move SSH to work over a different port.  This will stop 99% of attacks on SSH. 

Use RSA keys.

Dissable direct root login from SSH.  You can get root after loging in with a regular user account.

---

### Post by LordHunter317 on 2005-09-29
[QUOTE=TheDanMan]A few things.
Move SSH to work over a different port.  This will stop 99% of attacks on SSH. [/quote]Yes, **but it doesn't solve the actual security issue**.

As such, it's a poor countermeasure at best.  Moreover, I'm just slowly tickign away the days until SSH brute-force attackers simply port scan before attacking.

---

### Post by Glut on 2005-09-29
Moving the port also annoys users, if you're dealing with more than a handful.

---

### Post by Beernut on 2005-10-01
[QUOTE=LordHunter317]Except the dictionary attack is pretty worthless, if you have strong passwords.[/QUOTE]

I am with LordHunter on this one your fine is you just use strong passwords like a combination of numbers letters and different case.  If you want a bit more security, use key pairs that will allow you to use a **passphrase** like the following "I like beer" :D  instead of just a password.

---

### Post by kentborg on 2005-10-04
My favorite way to generate passwords is to use a program called
mnencode (there is also mndecode).  It takes arbitrary binary data and
turns it into pronouncable english words.  (mndecode does the
reverse, it turns those words into the original binary data.)
To generate a password I do:

head -c 4 /dev/random | mnencode

This will produce a password that has 32-bits worth of entropy in it,
yet one that is startling easy to remember.  Here are some examples:

george-montana-answer

druid-crater-waiter

madam-welcome-protein

Being three simple dictionary words they don't look like good
passwords, but they are as good as 32 coin tosses.  It is pretty easy
to make up a little story to make sense of the three words.
Note, this is not a good enough passphrase for encrypting data where a
motivated foe has an opportunity make a brute force attack, but this
*is* good enough for a password where your foe is throttled in his/er
attempts.

For a more secure passphrase suitable for very secure encryption,
change the number of bytes you feed in:

head -c 16 /dev/random | mnencode

It will produce results like:

compare-nobel-carrot--avenue-beast-front
alien-iceberg-bless--sonata-karl-pilot

or:

neutral-cantina-ultra--orient-average-pizza
cafe-pasta-future--ritual-portal-audio

They are easily good enough to stand up to a brute force
attack (having a full 128-bits of entropy), but they are much harder
to remember.  (They are also much harder to blind type without making
errors.)

If you have another technique for generating passphrases that produces
easier to remember passphrases, be skeptical.  You might not have as
much entropy in the passphrase as you think.  "I like beer." has very
low entropy.  Many used to think that things like "gandolf" or a girl
friend's name were terribly obscure and so good passwords, but they
were wrong, they are at the top of any good cracker's list.  I expect
"I like beer" will be on future lists.

The thing that makes
neutral-cantina-ultra-orient-average-pizza-cafe-pasta-future-ritual-portal-audio
so hard to remember is that there is no relationship between the
words.  If you use a real sentence that makes sense there is a lot of
connection between the words, which also means there is a lot less
entropy in the result.  Drop one word from the above passphrase and no
one can easily guess it.  Drop one word from some real sentence and
[...] is pretty easy to make a good guess what is missing.  Much lower
entropy.

Back to a 32-bit password: It isn't completely weak.  If a foe knew
exactly how you generated your password and were only missing the
32-random bits you fed in, s/he would still have to try over three
thousand passwords a second for an entire week to have even-odds of
cracking in.  That might be good enough for may purposes.  Or, maybe
split the difference and use 64-bits of entropy for something like:

tokyo-gold-clark--shake-permit-amazon

Not terribly hard to remember.  It would require testing over 30
trillion passwords a second to have even odds of breaking it in a
week.  If one could try a billion possibilities each second, it would
still take 292 years of trying to have even odds of cracking in. The
NSA could crack it if they wanted to, but they would have to want to;
they would have to spend some time and money to do so.

-kb

---

### Post by LordHunter317 on 2005-10-04
[QUOTE=kentborg]This will produce a password that has 32-bits worth of entropy in it,[/quote]No, that's not true.  Just because the input into mmencode has 32-bits of entropy doesn't mean the output does.

And the amount of entropy is irrelevant when talking about cracking an invidiual password.

Password strength is generally a function a of two things: length, and "complexity".  Generally, complexity is the probablity of having characters that are not in the attacker's dictionary.  For something like a rainbow table, complexity essentially doesn't matter.  For something like brute-force SSH attacks, where the table is small, a "complex" password can easily keep you safe.

> but they are as good as 32 coin tosses. Which (and I'm reiterating this because it's so critical) doesn't matter at all in this context.  

It'd only matter if someone was attempting to attack the generator to figure out the next password that would be generated.  Which we're not doing, and isn't a terribly practical form of attack unless the generator is trivial to break (i.e., the entropy is irrelevant).

> For a more secure passphrase suitable for very secure encryption,It's not.  Passwords that are the input to something that needs to be very secure, like a private key of a keypair, are hashed, and that hash is used as the key to a symmetric cipher that protects the keypair.  This is the only way to make brute-force attacks impractical, as you kill any ability to do precomputation beyond the dictionary itself.

As such, the strength of the hash is far more important than the password used to generate the hash, as it's easier to attack the hashing function.

More over, it's once again irrelevant unless you're trying to make an attack on the generator *itself*.  In which case, what the password is intended for is  irrelevant.

> If you have another technique for generating passphrases that produces
easier to remember passphrases, be skeptical.  You might not have as
much entropy in the passphrase as you think.But the entropy doesn't matter for password attacks.  We could care less about how the password was generator, and recovering from the generator, because it's much easier to attack the hashed version and recover the password that way, or do simple brute force on the output.  In either case, the generator (and the entropy bestowed on the key) are irrelevant.

---

### Post by Beernut on 2005-10-04
[QUOTE=kentborg]I expect "I like beer" will be on future lists.[/QUOTE]

That's why I don't use it but a much better passpherase would be "I lIkE b33R"

[QUOTE=kentborg]
neutral-cantina-ultra-orient-average-pizza-cafe-pasta-future-ritual-portal-audio
[/QUOTE]

I don't really see how that is a better passphrase other than the length of it and some punctuation your still using dictionary words.  Lodhunter had a good point the strength is really in the key pair.

---

### Post by Glut on 2005-10-04
[QUOTE=Beernut]That's why I don't use it but a much better passpherase would be "I lIkE b33R"[/QUOTE]
A good article on the topic: [http://www.microsoft.com/technet/security/secnews/articles/itproviewpoint100504.mspx](http://www.microsoft.com/technet/security/secnews/articles/itproviewpoint100504.mspx)
Ahh! run and hide! a Microsoft link!

---

### Post by drogoh on 2005-10-04
[QUOTE=Glut]The more paranoid would disallow root logins from ssh and setup allowusers to a set of known users.[/QUOTE]
I do this on all of my servers, allow only certain known IPs to 22 and only have pubkeyauthentication yes...  The SSH drones can kiss my ass.

My account is the only "vulnerable" account because I have NOPASSWD: (ALL) set in sudoers, everyone else gets the ultra BOFH treatment.  But it's not like anyone's getting my account unless they managed to unlock the magnetic locks to the door (swipe card, key code and hand scanner), are sitting in front of my machine and have one of my hands.  (biometrics, baby!)  If they DO have one of my hands, by all means they can have the damned machines. :)

---

### Post by Beernut on 2005-10-04
> **Glut]Ahh! run and hide! a Microsoft link![/QUOTE]

Interesting article except they forgot the part that MS recommends that you right your password on a sticky note and press it firmly against your forehead.   said:**
> But it's not like anyone's getting my account unless they managed to unlock the magnetic locks to the door (swipe card, key code and hand scanner), are sitting in front of my machine and have one of my hands. (biometrics, baby!) If they DO have one of my hands, by all means they can have the damned machines.

Ahhh they don't need your hands just some Jello.  [http://www.engadget.com/entry/2511741206338374/](http://www.engadget.com/entry/2511741206338374/)

---

### Post by AgenT on 2005-10-05
[quote=drogoh]allow only certain known IPs to 22[/quote] 
How do you do this? What keyword do you use in the sshd_config file to accomplish this? I could not figure this out (what probably is very simple) from reading the man page for sshd_config.

---

### Post by drogoh on 2005-10-05
[QUOTE=AgenT]How do you do this? What keyword do you use in the sshd_config file to accomplish this? I could not figure this out (what probably is very simple) from reading the man page for sshd_config.[/QUOTE]

I don't do that in sshd, I do it in the external firewall.

---

### Post by terrrorr on 2005-10-07
I have two links for you all

[http://denyhosts.sourceforge.net/]("http://denyhosts.sourceforge.net/")

[http://sourceforge.net/projects/daemonshield/]("http://sourceforge.net/projects/daemonshield/")

pretty handy tools

---

### Post by kentborg on 2005-12-07
[QUOTE=LordHunter317]No, that's not true.  Just because the input into mmencode has 32-bits of entropy doesn't mean the output does.[/QUOTE]

The key here is that mnencode is completely reversible, mndecode will get back the original data.  Consider the original 32 bits.  It doesn't matter if I write them as a string of "H" and "T", "0" and "1", or "on" and "off".  The key is that the coding of those 32-bits must be reversible.  You could e-mail those 32-bits and if the e-mail is uuencoded or base64 encoded doesn't matter, because those are reversible operations.  mnencode and mndecode are also reversible, one could encode e-mail attachments with mnencode/mndecode if one wanted to be inefficient--mnencode/mndecode are reversible.

[QUOTE=LordHunter317]And the amount of entropy is irrelevant when talking about cracking an invidiual password.

Password strength is generally a function a of two things: length, and "complexity".  [/QUOTE]

No, password strength is **exactly** about how many combinations there are to guess.  And the word "entropy" has a precise meaning which is exactly what you are trying to describe here.

Realize that the possible number of passwords a given system allows is only one factor.  The other factor is how you choose your password.  Say a system requires exactly 8 lowercase letters.  26 letters, that works out to 26^8, or 200 billion possible passwords.  Cool.  But what if you choose your password by selecting one 8-letter english language word?  You would have reduced the number of possibilities drastically.

I described a method for generating a password which will be one choice out of 4-billion possibilities.  That's right.  Those three words might be simple to remember, but they really are 4-billion combinations there.  (That is the whole point.)

Password strength is all about how hard it is to guess.  More combinations require more guesses.  The passwords I describe have exactly 4,294,967,296 combinations, so that is exactly how strong they are.

-kb

---

### Post by cactus on 2005-12-07
[QUOTE=AgenT]How do you do this? What keyword do you use in the sshd_config file to accomplish this? I could not figure this out (what probably is very simple) from reading the man page for sshd_config.[/QUOTE]

3 possible ways..

1) iptable rules
2) with tcp wrappers. put "ALL: ALL" in /etc/hosts.deny, and "sshd: ip_address1 ip_address2 etc.." in /etc/hosts.allow
3) in /etc/ssh/sshd_config, put "AllowUsers username1@hostname username2@ip username2@ip username..."

with 3, you get the added bonus of only those specific users being allowed to connect..and from only those hosts...

:)

---

### Post by jrib on 2005-12-07
And you can use groups as well.  I don't want anyone with sudo priveleges to login so I put: ```
DenyGroups admin
``` in my config file.

This link helped me when i was setting ssh up: [http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Restricting_User_Logins.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Restricting_User_Logins.html)

---

