---
title: "Gaim 1.3.1..."
date: 2005-06-10
forum: Ubuntu Backports
---

### Post by TheDocMan on 2005-06-10
Gaim 1.3.1 was just released...  Can we get a backport?

Thanks,

Brent

---

### Post by jdong on 2005-06-10
I was looking at it. Two relatively minor security bug fixes. Not in Breezy yet. If it doesn't enter Breezy/Sid by Sunday, I'll backport.

---

### Post by angrykeyboarder on 2005-06-10
[QUOTE=jdong]I was looking at it. Two relatively minor security bug fixes. Not in Breezy yet. If it doesn't enter Breezy/Sid by Sunday, I'll backport.[/QUOTE]

version 1.3.1 (6/9/2005):
	* The file transfer details section now also displays the full path to
	  the local file sent/received.
	* Yahoo! has the following new "/" commands:  /join, /buzz
	* Fix Yahoo! privacy bug
	* Fix Jabber Get Info crash on busted servers
	* Updated our gaim.desktop file, thanks to all our terrific translators
	  for sending in translations of the changes
	* Improvements to how Gaim handles new message notification

Security releases and bugfixes.  Purdy pleeze.....

---

### Post by abandoned_hussam on 2005-06-10
[QUOTE=jdong]I was looking at it. Two relatively minor security bug fixes. Not in Breezy yet. If it doesn't enter Breezy/Sid by Sunday, I'll backport.[/QUOTE]
 It is in debian unstable.
I'm rebuilding it now :)

---

### Post by sirukin on 2005-06-11
Grood!

---

### Post by Mez on 2005-06-11
Done

[http://www.sourceguru.net/ubuntu/hoary/backports/](http://www.sourceguru.net/ubuntu/hoary/backports/)

---

### Post by Farhad on 2005-06-11
[QUOTE=Mez]Done

[http://www.sourceguru.net/ubuntu/hoary/backports/](http://www.sourceguru.net/ubuntu/hoary/backports/)[/QUOTE]
 Reporting idle status by X usage isn't working with these packages here

---

### Post by jdong on 2005-06-11
Probably due to Debian-Ubuntu diversion.

I'm applying 1.3.0 Ubuntu patches to 1.3.1 sources from Debian.

---

### Post by skoal on 2005-06-11
argh! I thought 1.1.3 was the latest backport.  Can someone provide a mirror reference which has this 1.3?  thx.

/edit oops! must remember to read 3 posts above mine.

\\//_

---

### Post by Mez on 2005-06-11
[QUOTE=Farhad]Reporting idle status by X usage isn't working with these packages here[/QUOTE]

Is it owrking in 1.3.0 backport?

---

### Post by skoal on 2005-06-11
[QUOTE=Mez]Is it owrking in 1.3.0 backport?[/QUOTE]
hmm... he seems to be right! It's completely missing from the menu.  I never use it anyways, but it's gone nonetheless.

\\//_

---

### Post by Mez on 2005-06-11
Looking through idle.c - it seems to have bveen removed

unless you're on about setting idle via screensaver?

---

### Post by skoal on 2005-06-11
I really don't have a clue what that "idle" thingy does anyways.  Hell, half these gizmos and doo-dads showing up in "Preferences" are ancient Aramaic to me anyways.  I'm using your package and it passes teh "it Just works" quality check, so I'm good.  thx.

\\//_

---

### Post by Mez on 2005-06-11
Well - it does work... and it seems that xidle was dropped (according to the source code)

So well - It's up to you - I'm going to be using my version - backports people cna make their own for bp if they want

---

