---
title: "XLogic stuff"
date: 2004-11-13
forum: The Cafe
---

### Post by TravisNewman on 2004-11-13
What is this? Sometimes, seemingly at random times sometimes, because it sometimes only lasts for a few seconds, I can't get into ubuntuforums.com because it asks me to login to "XLogic stuff." I thought it was forum maintenance until it started doing it so sporadically.

---

### Post by ubuntu-geek on 2004-11-13
[QUOTE=panickedthumb]What is this? Sometimes, seemingly at random times sometimes, because it sometimes only lasts for a few seconds, I can't get into ubuntuforums.com because it asks me to login to "XLogic stuff." I thought it was forum maintenance until it started doing it so sporadically.[/QUOTE]
 Hrm.. Must be a bug with the new setup. I'll make some changes.. Sorry :(

---

### Post by TravisNewman on 2004-11-13
S'ok :) What's causing it, out of curiosity?

If you don't want to say for security reasons, I understand :)

Edit: sorry for posting in general support, I meant to post here to begin with

---

### Post by ubuntu-geek on 2004-11-13
It could be the named virtual hosting in apache and all the dns has propagated to the new NS servers yet.. I moved the site to a new server last night :)

No worries about the wrong section ..

---

### Post by TravisNewman on 2004-11-14
[QUOTE=ubuntu-geek]It could be the named virtual hosting in apache and all the dns has propagated to the new NS servers yet.. I moved the site to a new server last night :)

No worries about the wrong section ..[/QUOTE]
 Yeah it started last night, that's probably it. I'd think I'd be using the same NS servers though, but I guess not.

---

### Post by TravisNewman on 2004-11-14
A bit of an update here...

Whenever I try to type "www.ubuntuforums.com" into the address bar, it gives me the XLogic stuff prompt every time. Literally every time. But when I get an email about an updated thread and click on it, it works fine... doesn't make much sense...

---

### Post by HiddenWolf on 2004-11-14
Hm, my bookmark still works fine. :-)

[www.ubuntuforums.org](www.ubuntuforums.org)

---

### Post by ubuntu-geek on 2004-11-14
[QUOTE=HiddenWolf]Hm, my bookmark still works fine. :-)

[www.ubuntuforums.org](www.ubuntuforums.org)[/QUOTE]
 Yeah I cant reproduce the only thing I can think of is the dns wasnt propagated yet or was but the isp you use was cached..... But should be now if you still see the issue let me know.

---

### Post by TravisNewman on 2004-11-14
[QUOTE=ubuntu-geek]Yeah I cant reproduce the only thing I can think of is the dns wasnt propagated yet or was but the isp you use was cached..... But should be now if you still see the issue let me know.[/QUOTE]
 Yeah if I make a bookmark or click your link up there, hiddenwolf, it works fine. But it's when I type it in the address bar that it freaks out. And yes, it still does it. I can't figure this one out.

---

### Post by adbak on 2004-11-14
Panickedthumb: make sure that you type .org instead of .com.

I've noticed this too when trying to get to [http://art.ubuntuforums.org](http://art.ubuntuforums.org) .  Which is a bummer.

---

### Post by TravisNewman on 2004-11-14
[QUOTE=adbak]Panickedthumb: make sure that you type .org instead of .com.

I've noticed this too when trying to get to [http://art.ubuntuforums.org](http://art.ubuntuforums.org) .  Which is a bummer.[/QUOTE]
 Yeah, it happens for all these:
ubuntuforums.com - I didn't even know this existed
ubuntuforums.org
art.ubuntuforums.org

---

### Post by ubuntu-geek on 2004-11-15
[QUOTE=panickedthumb]Yeah, it happens for all these:
ubuntuforums.com - I didn't even know this existed
ubuntuforums.org
art.ubuntuforums.org[/QUOTE]
 Ok,

Whew! I seen the issue with the art.ubuntuforums.org and the ubuntuforums.com they both redirect correctly now.. But I still cant reproduce with ubuntuforums.org by itself.

---

### Post by TravisNewman on 2004-11-15
[QUOTE=ubuntu-geek]Ok,

Whew! I seen the issue with the art.ubuntuforums.org and the ubuntuforums.com they both redirect correctly now.. But I still cant reproduce with ubuntuforums.org by itself.[/QUOTE]
 I think I was typing in [www.ub](www.ub) and then hitting down to go through my recently typed url's, and its a definite possibility that I typed it wrong once and just didn't notice it for a couple days.

If so, sorry for the confusion, but I'm glad this thread got your attention for the other domains.

---

### Post by ubuntu-geek on 2004-11-15
[QUOTE=panickedthumb]I think I was typing in [www.ub](www.ub) and then hitting down to go through my recently typed url's, and its a definite possibility that I typed it wrong once and just didn't notice it for a couple days.

If so, sorry for the confusion, but I'm glad this thread got your attention for the other domains.[/QUOTE]
 No worries.. Glad the other ones got mentioned so they could get fixed.. :)

---

### Post by HiddenWolf on 2004-11-15
Seems to work fine now.

---

