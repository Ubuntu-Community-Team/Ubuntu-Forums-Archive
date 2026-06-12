---
title: "Security and gaming"
date: 2013-06-14
forum: Security
---

### Post by LearnAlways on 2013-06-14
Greetings,

What security precautions should I take if I choose to game online with Linux?

For example, how would I secure my computer in preparation for playing Battle for Wesnoth online?

Thanks

---

### Post by CharlesA on 2013-06-14
You shouldn't really have to do anything special.

---

### Post by LearnAlways on 2013-06-14
Thank you CharlesA. You're probably right, in that the default settings should be sufficiently secure.

Are there any particular settings which I ought to confirm are still in the default configurations?

For instance, a list of ports that should be closed?

I know very little of Linux, so I don't mess with things too much. But maybe I've managed to do something wrong.

---

### Post by slickymaster on 2013-06-14
CharlesA is right, you don't have to do anything special if you follow same basic common sense rules. Such as taking in consideration that in Massive Multiplayer Online Role Playing Games, the presence of a large online community of anonymous strangers and the unfiltered, unmoderated discussions, can pose a variety of potential risks like inadvertently or recklessly giving away personal information, including password, email or home address; downloading ‘cheats’ which claim to help you but which, in fact, may contain viruses/spyware; downloading 'free' web and app-based games in which you have to pay to access the full content, etc.

---

### Post by CharlesA on 2013-06-14
> **slickymaster said:**
> CharlesA is right, you don't have to do anything special if you follow same basic common sense rules. Such as taking in consideration that in Massive Multiplayer Online Role Playing Games, the presence of a large online community of anonymous strangers and the unfiltered, unmoderated discussions, can pose a variety of potential risks like inadvertently or recklessly giving away personal information, including password, email or home address; downloading ‘cheats’ which claim to help you but which, in fact, may contain viruses/spyware; downloading 'free' web and app-based games in which you have to pay to access the full content, etc.

Pretty much this entire thing. Don't forget gold buying either... :p

---

### Post by Hungry Man on 2013-06-14
Being exploited through your game is unlikely, since there's generally a small userbase, and most content has to pass through some server that will likely validate it and filter it. I would set up UFW, which there's a guide for in a sticky.

---

### Post by CharlesA on 2013-06-14
> **Hungry Man said:**
> Being exploited through your game is unlikely, since there's generally a small userbase, and most content has to pass through some server that will likely validate it and filter it. I would set up UFW, which there's a guide for in a sticky.

+1. Also 'lo. :)

---

### Post by slickymaster on 2013-06-14
> **CharlesA said:**
> ... Don't forget gold buying either... :p

Unfortunately, with European's present economical situation, you wouldn't believe how much that scam as grown.

---

### Post by CharlesA on 2013-06-14
> **slickymaster said:**
> Unfortunately, with European's present economical situation, you wouldn't believe how much that scam as grown.

I don't want to think about it. :p

I remember spambots in Diablo 2, Diablo 3, World of Warcraft, Guild Wars, Guild Wars 2... 

*shudders*

---

### Post by RadicaX on 2013-06-15
I would do last common sense thing, do not use the same password that gives you root access to your computer, or allows you to log on. This is just a bad idea, having atleast two or three passwords tends to be a good idea. You should be good to go. [http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

Just incase you need to know what ports to open for your game, it should be listed somewhere that ordeal.

---

### Post by CharlesA on 2013-06-15
It's a good idea to use a different password for everything, anyhow. :)

---

### Post by RadicaX on 2013-06-15
That is very true! I am shocked at how many people use one password for everything, and it is almost always something like: password. Then are shocked they were hacked.

---

### Post by LearnAlways on 2013-06-15
Thanks to everyone who responded. I'm less worried now, after reading your replies, and you've provided me with some good information about securing my computer.

---

### Post by tubbygweilo on 2013-06-16
Bruce Schneier has a longish posting with a good few other references on choosing passwords and pass phrases [https://www.schneier.com/blog/archives/2013/06/a_really_good_a.html#comments](https://www.schneier.com/blog/archives/2013/06/a_really_good_a.html#comments), have a read, a think and then decide if you need to change your existing password policy.

---

### Post by LearnAlways on 2013-06-18
> **tubbygweilo said:**
> Bruce Schneier has a longish posting with a good few other references on choosing passwords and pass phrases [https://www.schneier.com/blog/archives/2013/06/a_really_good_a.html#comments](https://www.schneier.com/blog/archives/2013/06/a_really_good_a.html#comments), have a read, a think and then decide if you need to change your existing password policy.

Fascinating read. Thank you.

One thing that I am curious about is how the crackers were able to piece together whole passwords from the hashes of *portions* of those passwords. 

From the post:
> 
The article goes on to explain how dictionary attacks work, how well they do, and the sorts of passwords they find.[INDENT]Steube was able to crack "momof3g8kids" because he had "momof3g" in his 111 million dict and "8kids" in a smaller dict.[/INDENT]
[INDENT]


[/INDENT]
[INDENT]I thought that even the slightest modification to the input of a cryptographic hash function would substantially change the hash. So how were the crackers able to piece-together whole passwords, simply due to their having constituents of those passwords' hashes in their dictionaries? The author of the blog post mentioned that the passfile was hashed with MD5, so maybe that has something to do with it. I was aware that, as the author stated, MD5 was inappropriate for hashing passcodes - although I don't have a good understanding of why that is. I'm new to this stuff. But isn't MD5 still somewhat good for validating the integrity of files (i.e., to verify they weren't tampered with)? So wouldn't a small change to the input of the MD5 hash, still produce a substantially different hash?[/INDENT]

---

### Post by CharlesA on 2013-06-18
md5sum is cryptographically insecure.

There are a bunch of stuff out there about it, and one of the better sites I found probably shouldn't be linked to as it was disucssing cracking methods...

Have a read here: [http://security.stackexchange.com/questions/15790/why-do-people-still-use-recommend-md5-if-it-is-cracked-since-1996](http://security.stackexchange.com/questions/15790/why-do-people-still-use-recommend-md5-if-it-is-cracked-since-1996)

---

### Post by LearnAlways on 2013-06-19
Amazing info man. Thanks!

---

