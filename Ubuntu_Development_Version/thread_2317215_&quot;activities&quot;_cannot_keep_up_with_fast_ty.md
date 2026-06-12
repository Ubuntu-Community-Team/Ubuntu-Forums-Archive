---
title: "&quot;activities&quot; cannot keep up with fast typers"
date: 2016-03-14
forum: Ubuntu Development Version
---

### Post by shinyblue on 2016-03-14
One of the reasons I love gnome shell is the quick way to start apps. Hit Windows key, type a few characters and hit enter. Windows term Enter. etc.

However since upgrading to 16.04 Beta1 I notice that if I type quickly the letters come out in the wrong order! At first I thought this was me being clumsy, but it's definitely not.

Examples:
[LIST]
[*]clem becomes celm or even clme
[*]term become temr
[*]fox become fxo
[/LIST]

This makes the feature unusuable unless you type slowly. Which I don't. It used to be so convenient and I love that I could start an app with my eyes shut. Would love a fix.

---

### Post by shinyblue on 2016-03-14
actually you really don't have to type very fast at all. If you want a proof that it's not my typing, try running your finger from Q to T. You should get QWERT, of course, and of course because of the way you're doing it it would be physically impossible to type the letters out of sequence. I got **qwter**

---

### Post by kansasnoob on 2016-03-14
I wonder if the keyboard was properly detected? I'm not sure how to find out, just thinking out loud :redface:

Definitely worth filing a bug report over, but I'm also not sure what package to file against :confused:

I'm full of *I dunno*'s this AM :(

---

### Post by PaulW2U on 2016-03-14
> **shinyblue said:**
> However since upgrading to 16.04 Beta1 I notice that if I type quickly the letters come out in the wrong order! At first I thought this was me being clumsy, but it's definitely not.
Hi shinyblue, I found that too in my brief use of Ubuntu GNOME earlier this year. I thought it was due to my very poor specification laptop but then doubted by findings when I installed Ubuntu and found that Unity worked fine. Since I now use Xubuntu on that laptop I never got to the point of looking for or reporting a bug which I think you should do especially as 16.04 is an LTS release.

---

### Post by shinyblue on 2016-03-14
There seems to be a general keyboard issue.

e.g. in Photos (the mystery app that shows a couple of pictures with apparently no way to determine what it shows), click search and in that box every key I press comes up twice!

Trying apport-bug gnome-shell... [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1557089](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1557089)

---

### Post by PaulW2U on 2016-03-14
> **shinyblue said:**
> There seems to be a general keyboard issue.

e.g. in Photos (the mystery app that shows a couple of pictures with apparently no way to determine what it shows), click search and in that box every key I press comes up twice!

I'm seeing the same booting straight into a live session using today's daily build (20160314) so I've confirmed the bug report and added the bug to the ISO testing tracker. This is using a Toshiba C-50B laptop.

Hopefully this problem will get a little more exposure now.

Edit: Already reported on the GNOME bug tracker - [https://bugzilla.gnome.org/show_bug.cgi?id=750792](https://bugzilla.gnome.org/show_bug.cgi?id=750792)

---

### Post by mc4man on 2016-03-14
Maybe it's related to gnome activities starting a search per character & it gets 'confused' or falls behind when new characters are in putted too fast.
If inclined to file a bug should be soon & also do a report upstream as Ubuntu isn't likely  going to address this

---

### Post by ventrical on 2016-03-14
Some Dell PCs , Dell  proprietary mice and keyboards on non-Dell machines will produce this same result. I have had this happen several times with infra -red vs track-ball ans there are issues. 

switching mouse/keyboard solves problem.

regards..

---

### Post by sgage on 2016-03-15
I made a fresh install of today's daily, and I am seeing this bug as well. It is quite a strange one. If I go to type 'term' quickly I can see 'te' come up but as soon as i hit the 'r' it turns into 'tre'.

---

### Post by PaulW2U on 2016-03-22
Computers, I hate 'em although I must say, Ubuntu GNOME has never looked better than it does in 16.04. :)

I'm now running a live Beta 2 Ubuntu GNOME session and I'm very surprised to find that no matter how hard I try I cannot make this bug appear in my Activities searches. There appears to have been no activity on either the Ubuntu or GNOME bug reports. Has the bug been fixed and the bug reports not been updated?

Strange. :confused:

---

### Post by sgage on 2016-03-22
> **PaulW2U said:**
> Computers, I hate 'em although I must say, Ubuntu GNOME has never looked better than it does in 16.04. :)

I'm now running a live Beta 2 Ubuntu GNOME session and I'm very surprised to find that no matter how hard I try I cannot make this bug appear in my Activities searches. There appears to have been no activity on either the Ubuntu or GNOME bug reports. Has the bug been fixed and the bug reports not been updated?

Strange. :confused:

My guess is that they've fixed it ;-)  I am going to make a new install of XX tomorrow and check it out.

---

### Post by sgage on 2016-03-23
Just installed today's build (23 March), and the problem seems to have been fixed.

---

### Post by PaulW2U on 2016-03-23
> **sgage said:**
> Just installed today's build (23 March), and the problem seems to have been fixed.
Thanks for the confirmation sgage. I've just zsync'd my local image to the latest build (20160323.1) and I'm thinking the same. :D

---

