---
title: "Funny Commands in Linux"
date: 2008-02-08
forum: The Cafe
---

### Post by victorbrca on 2008-02-08
Some of them don't work on Ubuntu's bash:


> % cat "food in cans"
cat: can't open food in cans

% nice man woman
No manual entry for woman.

% "How would you rate Quayle's incompetence?
Unmatched ".

% Unmatched ".
Unmatched ".

% [Where is Jimmy Hoffa?
Missing ].

% ^How did the sex change operation go?^
Modifier failed.

% If I had a ( for every $ the Congress spent, what would I have?
Too many ('s.

% make love
Make: Don't know how to make love. Stop.

% sleep with me
bad character

% got a light?
No match.

% man: why did you get a divorce?
man:: Too many arguments.

% !:say, what is saccharine?
Bad substitute.

% %blow
%blow: No such job.

% \(-
(-: Command not found.

$ PATH=pretending! /usr/ucb/which sense
no sense in pretending!

$ drink matter
matter: cannot create




Vic.

---

### Post by Mary.Riley on 2008-02-08
I really shouldn't find this funny. But, I do.

---

### Post by icechen1 on 2008-02-08
Ubuntu uses Bash by default,i think there is a way to switch back to Bash do a search on the net.

---

### Post by sumguy231 on 2008-02-08
Ubuntu uses bash as the login shell, dash for running scripts. But all of those examples are from the 80s and generally for bourne shell or csh on classic Unix systems.

Edit: Heh, look at the Dan Quayle joke. That should date it.

---

### Post by victorbrca on 2008-02-08
> **icechen1 said:**
> Ubuntu uses Bash by default,i think there is a way to switch back to Bash do a search on the net.

I kinda got dizzy reading your comment!! :D

If I'm not mistaken the command is:

```
sudo dpkg-reconfigure dash
```


Vic.

---

### Post by FiskFisk33 on 2009-10-10
This is the beginning of sentient linux computers! :O

---

### Post by Propeng on 2009-12-07
I usually don't like reviving old threads, but I've found out that they actually work on csh:
```
$ sudo apt-get install csh
$ csh
% ...
```

---

