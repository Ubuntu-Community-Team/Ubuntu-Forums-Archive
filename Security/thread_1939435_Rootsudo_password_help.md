---
title: "Root/sudo password help"
date: 2012-03-11
forum: Security
---

### Post by thatguy93 on 2012-03-11
Hey guys.
Alright having a huge issue with my laptop. I cannot do anything with my laptop because my root/sudo password does not work. Nothing is even allowing me to change the password. When in recovery mode, and in root, I type passwd *username*, which prompts me to change my password but then it says

> passwd: Authentication token manipulation error
passwd: password unchanged

Cant change anything to do with my account while logged in either, obviously. I never had any problems before, until about two days ago when it asked me to create a key-ring password(which I already had at the time). So I "created"(changed) one/it. The passwords I used at installation all do not work.

Any ideas?!

---

### Post by winh8r on 2012-03-11
This might help you:

[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")


Hope so.

---

### Post by thatguy93 on 2012-03-11
> **winh8r said:**
> This might help you:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)


Hope so.

Unfortunately no. Wont even let me create a new user, it just tells me the user does not exist.

---

### Post by dres on 2012-03-31
Same for me. I can't install updates available in Ubuntu 11.10 because it ask's for a root password. I type in the password I created when I first installed Ubuntu 11.10 and nothing (Your authentication request was unsuccesful). Please HELP!!!

---

### Post by Blackra1n on 2012-04-02
> **thatguy93 said:**
> Hey guys.
Alright having a huge issue with my laptop. I cannot do anything with my laptop because my root/sudo password does not work. Nothing is even allowing me to change the password. When in recovery mode, and in root, I type passwd *username*, which prompts me to change my password but then it says



Cant change anything to do with my account while logged in either, obviously. I never had any problems before, until about two days ago when it asked me to create a key-ring password(which I already had at the time). So I "created"(changed) one/it. The passwords I used at installation all do not work.

Any ideas?!

Maybe your root partition is mounted read only?
Type ```
mount
``` to find out.

---

