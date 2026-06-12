---
title: "Shouldn't Email-Encryption be default in new installation."
date: 2009-11-06
forum: Security
---

### Post by t.rei on 2009-11-06
Hi,

As I'm currently working on my thesis on Usability of IT-Security and am currently at the topic of secure communication via email, I noticed something:

It is very very easy. Now, wouldn't it be great if on every default installation the keys are created during setup? Without troubling the user at all. The fact that signed and encrypted email as a default would make it alot easier to filter spam and distinquish between fakes and phishings. But I'm preaching to the priests.

So, question I want to place in this forums and the *ubuntu community:

"Sould gpg-encryption and signature be default after install?"

---

### Post by __p1n__ on 2009-11-06
1. I think that mean to say PGP (it stands for pretty good privacy) and not GPG

2. Key-managed security extends far beyond a client set up.  There are key distribution and key management concerns that need to be addressed as well.

3. There are other encryption schemes besides PGP and even restricting the focus to PGP there is the question of key size and other options so an automatic scheme is not really feasible.


Still, not bad for an academic effort (as opposed to a technical effort.)

---

### Post by Sarmacid on 2009-11-06
I don't think it should be default in an installation, but I guess it wouldn't be bad at all to offer the option when you fire up evolution for the first time.

The first reason is because I may have already have a key pair, so I don't need another. And the second one would be that not that many people use PGP and for the ones that do you'd have to send your key or stablish some sort of way your key is easily accessed and you access someone else.

---

### Post by t.rei on 2009-11-06
I am well aware of the concerns of key-management. But on todays net I'd say those issues should be addressed. And there is quite some demand for secure communications. 

If any software is able to create the ideas and solutions for a topic like this it is OSS. I am rather confident in this. But I would not doubt that commercial software companies are already working on providing integrated communication security. The awareness for it is on a rising level, especially with social networks getting cracked as often as they are currently. This awareness does transpire into the heads of management and workers. 

There is or will be a growing interest. But it has to be... you all know it... simple.

---

### Post by MechaMechanism on 2009-11-06
[I]No, there are legal implications that prohibit the use of encryption.

In many countries encryption is de facto assumption of guilt.  Better to make it available via download instead of default install.  Of course Ubuntu offers to encrypt your home dir and I do wonder about Ubuntu's acceptance in various countries.  But frankly most of my email is not worth the hassle of encryption, although if I lived in North Korea I might feel differently.  Also would not spam start using encryption and would that not make it harder to detect because you would not know it was spam until you decrypted the message?
[/I]

---

### Post by t.rei on 2009-11-06
The thing that works against spam is not the encryption, but the signing of emails. Since mostly spammers "claim" to be someone from your or any poor fellows addressbook, faked mail would easily be recognized. Also, if spammers create valid email signatures for themselves they get traceable. And signatures are ahrd enough to fake to be valid in court to some extend.

I know that most of my email is not worth any hassle, but there are those private little notes that I write to my love or discussions about contracts and job offers that should NOT be seen. So I encrypt. Not to anyone, but to anyone who has my key and who's key I have. Just to make it a habbit. And all I need to do is sometimes type my key-password. 

But yes, there are rather large and well known countries that are... very cynical at claiming privacy as valuable but encryption as bad. Good call.

---

### Post by qamelian on 2009-11-06
> **__p1n__ said:**
> 1. I think that mean to say PGP (it stands for pretty good privacy) and not GPG


No, he probably does mean GPG...Gnu Privacy Guard, which is essentially the F/OSS equivalent of PGP.

---

### Post by kevdog on 2009-11-06
Most people know nothing of GnuPG.  Why would it be the default?  Try getting your friends to use it regularly.  I bet they turn lazy although there are good implementations of it such as Gmail and Firegpg.

---

### Post by subynut on 2009-11-06
I agree with some sort of encryption, however, since we are talking a global communication system with countries that frown very heavily on encryption, that makes it practaly imposible due to good ol' politics.
However, one possibility would be to spit up the countries and use different email standards. Although, that would require some very complex infrastructure that would take years to install and very expensive.  It also would be very expensive to maintain due to human error during the planing stages.
From a practical point of view, it will not happen on a global scale.

---

### Post by t.rei on 2009-11-07
So it comes down to:
Encryption should be obtainable but it would be dependant on the capabilities of both parties - recipient and sender - if encrypted communication is possible.

I'd say, considering that most communication worthy of encryption would be in between parties that know of each other and are very well aware of their reasons. So an easy opt-in system during or right after the basic system setup would be cool.

BUT. Remember another part: Signing email. THAT is a feature that could be interesting not only for the users, but also for the 'net itself. Since a step towards "only accept signed email" would probably be a good way towards getting less spam.

---

### Post by tubbygweilo on 2009-11-07
Encryption should not be installed by default but should be easily installable if wished by a new or relativity unsophisticated user.

For email I use Thunderbird + Enigmail + Gmail as all are easy to use and install but it is so hard to get many others to use them as a modern email package. Not too many public bodies or organisations seem to have or publish their public keys. I sign and encrypt my emails to those who use keys, I sign to all others but only when sending from my laptop thus an unsigned email indicates it may well have been sent from someone else's machine, a public machine or some other not too secure location. I keep Truecrypt encrypted copies of .gnupg folder holding all keys and keeping them safe from prying eyes. Key management needs a little thought with backups of all keys taken from time to time and kept safe from harm.

---

### Post by Stolea on 2009-11-08
Encryption is a great concept, but if it involves more than two people agreeing on a single point, I cannot see it ever getting off the ground. Its fine (and very sensible)between say a remote office and head office where rules can be enforced.
However for normal everyday communications, what's the point. If someone wants to read my email to my cousin, I hope thay have a great time of it.

---

### Post by tubbygweilo on 2009-11-08
> However for normal everyday communications, what's the point. If someone wants to read my email to my cousin, I hope thay have a great time of it.
Sometimes it is the contact based information such as the to,cc,bcc that is of interest rather than the content as by using contact information connections between groups and peoples may be derived or inferred and iirc such information can not be encrypted.

---

### Post by t.rei on 2009-11-08
> **Stolea said:**
>  If someone wants to read my email to my cousin, I hope thay have a great time of it.

Ah you see, thats just the thing. In Europe there is this new trend in politics to log all telecomunication connections, and content whenever "it might be relevant for security."

You see, you aren't doing anything bad, you cousin isn't. But someone who thought it was funny or something talked to your cousin's sister about "how to build remote controlled bomb-airplains". Just because he's a geek and thinks girls think this is cool. Two days later someone threatens to assault any obviously corrupt banker, politician and their families using remote controlled bomb airplanes wich they cannot defend themselves against, so security is highly threatened. 
Now all they do is check who talked to who about "remote controlled bomb-airplanes" and their relatives and close contacts. Since the communication was not encrypted and the mail account was on an imap server anyone can check it's contents without the owner noticing. Even if nothing found you WILL be registered as "has been checked before in matters of possible terrorist attacks on valued members of our society." And you can not know what that might result in in 25 years when "dna samples to determine how much the state is supporting your child" will be normal. 

This is the one aspect of data in the internet.

The other aspect is basically "what google does". Just more defined. If you get the average opinion stated in all communications going in and out of your country, you can find out which triggers exactly to push to manipulate your population to vote as you want them to. It's happening as I type, really. It's called "public opinion poll". Problem today is: it's the PUBLIC opinion and not the true one that is only mentioned when talking to relatives, i.e. a cousin.

Now: "But who would do that?"

Answer: "Anyone who can get power or money out of it and is not a 'nice' person."

Those are some arguments FOR encryption. It's in days where states and buisnisses make Billions out of Data. Collection of Data is just now really getting public. And it's spreading. And slowly we are getting used to less privacy and twitter our lives online.

To counter the "collect to control" effect it might be a good idea to work to make privacy and freedom - those things are REALLY valuable - not as "well who needs them, and for what?" as is induced to us on a daily basis.

Name ONE example in history where control of the people has ever meant security for the people.

---

