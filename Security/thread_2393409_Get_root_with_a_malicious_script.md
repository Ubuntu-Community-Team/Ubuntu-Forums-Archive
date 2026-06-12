---
title: "Get root with a malicious script?"
date: 2018-06-03
forum: Security
---

### Post by richard.meyer on 2018-06-03
Came accross a link to [French Ubuntu forums](https://forum.ubuntu-fr.org/viewtopic.php?id=2026792) where I found an encrypted file supposed to be a script to gain root privileges. It is written both in English and French. However, as there is no password, I was wondering if it was a joke or something?

---

### Post by richard.meyer on 2018-06-03
Sorry, it seems the link is no longer working? Can be found <snip>

---

### Post by mohicann on 2018-06-03
Anyway, I think everyone agrees that once an arbitrary code has been executed from "the inside", the game is over, no matter under which privileges it was. And if you had even just a clue that your computer could be compromised this way, not only should you consider totally reinstalling it but also you should be reviewing your security policy: IMHO, letting a script be executed this way is equal to providing root access to an attacker. The difference is mainly something that one automatically ignores: the skills and the motivation of the attacker, which means the time and the smartness they will use to achieve their goal. And it can't reasonably be presumed. 

Concerning the file itself, 7Z uses AES-256 encryption, which means that it's safe from quantum computers bruteforcing if the key is complex and long enough. Otherwise said, if this announcement is legit, this file without its password is like a knife without its blade: harmless. It looks like this announcement was... just an announcement.

PS: I've just passed by this webpage again and it seems they added a SHA-256 file integrity checksum for their files (for the record): 
a7a62ae150f8805af83813bda39e23a5696e1a6084ee31f7b9b3e541b812a081
It rather means the story is something you shouldn't hear about again anytime soon.

---

### Post by oldos2er on 2018-06-16
> **richard.meyer said:**
> Came accross a link to <snip> where I found an encrypted file supposed to be a script to gain root privileges. It is written both in English and French. However, as there is no password, I was wondering if it was a joke or something?

No script is needed to gain root privileges on Ubuntu. Seems fishy to me.

---

### Post by QIII on 2018-06-16
> **oldos2er said:**
> No script is needed to gain root privileges on Ubuntu. Seems fishy to me.

This.  

References to dangerous, possibly malicious, script snipped.

---

### Post by TheFu on 2018-06-28
> **oldos2er said:**
> No script is needed to gain root privileges on Ubuntu. Seems fishy to me.

There are thousands of ways to trick an unsuspecting member of the sudoers group into providing remote root access. This is fact.

The rest below are educated guesses based on years of systems and programming experience in all sorts of coding.
There are probably over 100 elevated permissions methods unknown in any given OS, with probably 5 known to a tiny subset of the world.  These would have to be run by an account userid already running on the machine.

There are probably 5 remote access flaws in any OS at any given time. These are beyond any flaws in specific listeners like apache, nginx, ftp-server, ssh-server, dns, ntpd, etc.  Hopefully, less than 1 is known in the world.

In my linux training classes, I've tricked the students into copy/pasting malicious code that contained more than what was viewable in their web browsers.  Nothing teaches NOT to copy/paste from any website showing linux commands like having your box pwnd by doing so early in your learning process.  In short, never trust what you are shown on a webpage.  Always copy then paste into an editor first, never directly into an interactive shell.   And those **curl "URL" | sudo bash -** things are bad too. Doesn't matter which website they are from.   Always download scripts separately and review them for malicious commands.

---

### Post by mohicann on 2018-07-05
I think so. This is the perpetual attack/defense game. This is how things always work and not only in the computer security field: based on the environment, what features could I exploit to reach my goal (gaining access, stealing data, etc). And its opposite: based on the attack, how can I protect my/this information system?

When you are looking for something, you are best placed to find it, the opposite is true as well. As far as you feel secure, you are sure to never be looking for a flaw and thus to never find it. It is also a psychological characteristic: we always feel more secure than the average person, even if or even though it's wrong. It answers 3 human traits: being lazy, feeling secure and thinking knowing.

---

