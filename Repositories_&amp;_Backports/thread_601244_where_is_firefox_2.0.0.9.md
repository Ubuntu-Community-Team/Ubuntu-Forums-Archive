---
title: "where is firefox 2.0.0.9 ?"
date: 2007-11-03
forum: Repositories &amp; Backports
---

### Post by DO55 on 2007-11-03
hi

why i cant find  Firefox 2.0.0.9 when i  update Ubuntu ? 

[http://www.mozilla.com/en-US/firefox/2.0.0.9/releasenotes/](http://www.mozilla.com/en-US/firefox/2.0.0.9/releasenotes/)

---

### Post by markusf21 on 2007-11-03
if you want the latest you have to install it yourself the new versions of firefox take a while to get down to us

---

### Post by DO55 on 2007-11-03
im new with Linux


its very hard to me to install it 

in windows its very easy 
just download EXE file and   click over it

---

### Post by reacocard on 2007-11-03
Just be patient. It will soon come in along with all your normal ubuntu updates.

---

### Post by Mothinator on 2007-11-03
It takes awhile for the ubuntu team to put together some updates like those to firefox. It's usually just a couple of days.

When it is released, you'll get notified that there is a security update available and you can just click to install it (much like windows updates).

---

### Post by DO55 on 2007-11-07
now 4 days and no update


please any one can tell me how can install it ?
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

---

### Post by mivo on 2007-11-07
> **DO55 said:**
> now 4 days and no update

Do you experience trouble with 2.0.0.8? I looked at the release notes for 2.0.0.9 and didn't see anything crucial that would require an immediate (and manual) update. It's mostly Windows/Vista fixes.

---

### Post by tombott on 2007-11-07
if you really can't wait for it to hit the repo's then follow this [guide]("http://ubuntuforums.org/showthread.php?t=330386")

However I'd just wait for it to be verified and packaged for Ubuntu mate.

---

### Post by Seisen on 2007-11-09
If its all Vista/XP problems then we probably won't see an update, if you take notice we went from 2.0.0.6 to 2.0.0.8 and skipped 2.0.0.7 because the fixes were Windows related.

---

### Post by Ricardus on 2007-11-16
Actually, I believe there are some CSS rendering issues that cane about in 2.0.0.8, and I was told that 2.0.0.9 would fix them.  Certain web sites don't render properly, and I was hoping the new release would fix them, so I hope they package it.

---

### Post by mellowd on 2007-11-16
Which websites? I haven't seen any problems with 2.0.0.8

---

### Post by peterx14 on 2007-11-16
Not seeing any problems with specific sites myself, but there were some regressions in 2.0.0.8 that .9 fixed, including this one:

[https://bugzilla.mozilla.org/attachment.cgi?id=285582](https://bugzilla.mozilla.org/attachment.cgi?id=285582)

---

### Post by Ricardus on 2007-11-17
The site that isn't rendering quite right is an e-commerce site that a web-designer friend is re-designing.  The new site isn't quite ready to go live yet, so he doesn't want me making the URL public.

Every other browser on the planet renders the page correctly, but Firefox 2.0.0.8 doesn't display the banner logo at the top like it's supposed to (maybe it's just the linux version, I don't know).  My friend googled around and found some references to 2.0.0.8 breaking some CSS stuff, and 2.0.0.9 re-fixes them,   :)

He's a great web designer and has run his code through a variety of tests, and is certain it's not in the code.  He also said that 2.0.0.9 addresses some security concerns as well, so it's a little surprising that Ubuntu hasn't packaged it up yet.

---

### Post by peterx14 on 2007-11-19
This is starting to impact my work (web development) as some things are rendering incorrectly... I have to test on a Windows box to check things; that can't be right!

Who/what needs chasing to get this sorted out?

If there is a valid reason for the delay, then I'm fine with it, but I'd really like some decent information about what's going on.

---

### Post by jonathan3003 on 2007-11-25
There's also an open bug for this:
[https://bugs.launchpad.net/ubuntu/gutsy/+source/firefox/+bug/160895](https://bugs.launchpad.net/ubuntu/gutsy/+source/firefox/+bug/160895)

and this too:

[https://answers.launchpad.net/ubuntu/+question/18282](https://answers.launchpad.net/ubuntu/+question/18282)

---

### Post by peterx14 on 2007-11-27
Firefox 2.0.0.10 is out now which contains security fixes, so I guess this will force the issue.

---

### Post by qamelian on 2007-11-27
> **peterx14 said:**
> Firefox 2.0.0.10 is out now which contains security fixes, so I guess this will force the issue.

Firefox 2.0.0.10 landed in the Gutsy repos yesterday. Mine updated last night when I got home from work.

---

### Post by peterx14 on 2007-11-27
Excellent!

---

### Post by Ricardus on 2007-11-30
Yeah, accept the new version didn't fix my problem.  The web site that I need to view still isn't rendering properly.

---

### Post by tombott on 2007-12-01
> **Ricardus said:**
> Yeah, accept the new version didn't fix my problem.  The web site that I need to view still isn't rendering properly.

What website causes you the issue?

Oh and I think you may mean 'except', please accept my apologies if this is not the case :-\"

---

### Post by peterx14 on 2007-12-01
> **tombott said:**
> Oh and I think you may mean 'except', please accept my apologies if this is not the case :-\"

[Are you the grammar sheriff?](http://bp1.blogger.com/_4Rzur2dF2wU/RuO7zOMM58I/AAAAAAAACI0/-hyNaQGbe3s/s1600-h/grammar+sherrif.jpg) :wink:

Back on topic... maybe when we get Firefox 2.0.0.11 that'll fix it?

---

### Post by tombott on 2007-12-01
> **peterx14 said:**
> [Are you the grammar sheriff?](http://bp1.blogger.com/_4Rzur2dF2wU/RuO7zOMM58I/AAAAAAAACI0/-hyNaQGbe3s/s1600-h/grammar+sherrif.jpg) :wink:

Back on topic... maybe when we get Firefox 2.0.0.11 that'll fix it?

lol, nice. No I aint no grammar sheriff, just a see you next tuesday.

---

### Post by mivo on 2007-12-01
Well, I'm glad that was finally sorted -- and Pidgin 2.2.2 as well. :)

---

