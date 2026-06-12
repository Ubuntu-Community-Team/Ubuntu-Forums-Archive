---
title: "Any WYSIWYG web page editors that actually work?"
date: 2007-11-01
forum: The Cafe
---

### Post by svivian on 2007-11-01
I'm pretty well-versed in HTML, CSS, etc. But sometimes you just can't beat a good WYSIWYG HTML editor. Much nicer if you're typing formatted text/paragraphs.

However, there doesn't seem to be any good editor for Linux that I can find. I've tried *KompoZer* and *IceApe* (Mozilla SeaMonkey).

*KompoZer* is decent but has a lot of problems. For a bug-fix release of Nvu, it still has A LOT of bugs!

*IceApe* is very limited and comes with all that other crap (browser/mail) which I don't want or need.

I've spotted only one other program in Synaptic, which is *Amaya*. But according to Wikipedia it doesn't have very good CSS support, ironic for a program designed to be a w3c testbed! Has anyone used this? Is it any good?

Are there any other programs worth checking out?

---

### Post by LaRoza on 2007-11-01
> 
Any WYSIWYG web page editors that actually work?


No.

---

### Post by happysmileman on 2007-11-02
None that I know of, I think by definition they're aimed more at the personal site just for showing a couple of family photo albums on a flowery background than any real work.

Best I could reccomend is a nice tabbed, syntax-highlighting text editor.

---

### Post by macogw on 2007-11-02
> **happysmileman said:**
> None that I know of, I think by definition they're aimed more at the personal site just for showing a couple of family photo albums on a flowery background than any real work.

yep yep

---

### Post by MrFSL on 2007-11-02
```
apt-cache search html | grep -i editor | grep -i WYSIWYG

```

Yeilds: tinymce - platform independent web based Javascript/HTML WYSIWYG editor

Never used it but there you go.

---

### Post by igknighted on 2007-11-02
Quanta+ is pretty nice (part of the kdewebdev package IIRC).  I don't use the WYSIWYG portions often though, so I can't really tell you much about them.  Your best bet is something that is of very questionable legality (license wise), but if you look up wine-doors you can install dreamweaver8 from a repo online.  Like I said, questionable legality... but if you only need it for a brief project it could be worth a shot.  Or you could shell out $400 for a license yourself...

---

### Post by Scruffynerf on 2007-11-02
Nope.

KompoZer is about the best that there is.

Amaya in the repo's seems to be broken - it always starts up, then immidately crashes. Starting it via the terminal is fun - no error messages appear whatsoever.

Quanta.... is odd. It's probably me, but it doesn't behave logically.

---

### Post by TeaSwigger on 2007-11-02
Hello,

Yes. I don't love any of 'em, but feel no need to summarily dismiss the efforts of their respective authors. So happens that they work for what they're designed to do. Whether that corresponds to what you happen to want it to do is the issue you have to determine. I agree they do appear to be aimed at less demanding projects.

There's no monolithic replacement for Dreamweaver though, if that's what you want. For that you'll have to pony up a mountain of bucks payable to Adobe Corporation and then see how well you can get it to run in WINE.

My humble for best featured open source Linux-oriented WYSIWYG is Quanta Plus. Then KompoZer for simplicity. Bluefish if you're working in code side. There are also tools of note which offer functions not found in the editors above, such as KLinkStatus or Kompare or Kdiff3 or KImageMapEdit. 

Amaya looks like it's amazing. What it's amazing at though, I have no idea.

On a side note, there is one area in which I've had more luck with in linux: doing diff operations, both file and file content. Lots of good tools there which in my humble best windows side offerings in their tasks.

Speaking of KompoZer (a second side note... oh well why not). It looks like the repos actually caught up with the latest KompoZer. Is that the version you have? Just whipped up some pages on it earlier and nothing went terribly wrong. I have had problems with it in the past, but then I've had problems in the past doing as much from the best bigtime payware (Dreamweaver) in Windows. And KompoZer didn't ask a thing from me.

---

### Post by MrFSL on 2007-11-02
> Yes. I don't love any of 'em, but feel no need to summarily dismiss the efforts of their respective authors. 

...it doesn't sound like anyone is dismissing anyone else's efforts (at least not as I read it.)  It sounds more like frustrated users of HTML software not yet finding what they are looking for in terms of a replacement for Linux and giving their honest opinions as to the inadequacies in that software genre.

---

### Post by sloggerkhan on 2007-11-02
Quanta looks interesting. Kinda odd, but it looks like at a minimum it could make laying out tables/frames easy.

---

### Post by Scruffynerf on 2007-11-02
> **MrFSL said:**
> ...it doesn't sound like anyone is dismissing anyone else's efforts (at least not as I read it.)  It sounds more like frustrated users of HTML software not yet finding what they are looking for in terms of a replacement for Linux and giving their honest opinions as to the inadequacies in that software genre.

This is my take on it as well.

Having used Dreamweaver, and seeing how relatively good a graphical editor can be (I know DW has it's problems, but then, what software honestly hasn't?) I'm disappointed with the offerings that there is on linux.

Going back over my post:

My requirements: Small website, mainly to act as a bit of a blog and also a quick and nasty way to make available photos over the web of family and other 'artsy' photos that I take with family and friends across the world. I get a 50mb free website as part of my ISP deal.

Not a huge ask. 

KompoZer: This is what I use. Generally alright, however there are problems dealing with tables and respective alignments. Occasionally, right-click is disabled randomly, or it'll default to a colour selector all by itself. It's "publish" / FTP functionality is plain borked. I have to resort to FireFTP to get stuff uploaded. For a supposed 'bugfix' release after NVU, it has a lot of problems.

Amaya: The repo version seems broken. So is the versions available on the website. I suspect that the problem is specific to my computer, as there is no hue and cry from the community. I've re-installed it, re-compiled it and eventually purged it. I suspect that I've disabled or removed a dependency, however nothing I've done can get it to work.

Quanta / Quanta + : The problem here is definitely with me. I just don't understand the program. Can't understand it's logic or the way it is supposed to work. Have no idea how to attach a thumbnail to a page.

Bluefish: Isn't really a WYSIWYG editor - I suppose that it may be good for coders, however so's Vi or Notepad. Could not see a way of enabling a graphical view.

What I did find that worked wonderfully **for me** on Edgy was Mozilla Composer, however I've not been able to locate a Feisty-happy version. I know KompoZer (wtf with that stupid name) is supposed to mimic it along with NVU, but I have found it to be a lot buggier.

---

### Post by RAV TUX on 2007-11-02
> **svivian said:**
> I'm pretty well-versed in HTML, CSS, etc. But sometimes you just can't beat a good WYSIWYG HTML editor. Much nicer if you're typing formatted text/paragraphs.

However, there doesn't seem to be any good editor for Linux that I can find. I've tried *KompoZer* and *IceApe* (Mozilla SeaMonkey).

*KompoZer* is decent but has a lot of problems. For a bug-fix release of Nvu, it still has A LOT of bugs!

*IceApe* is very limited and comes with all that other crap (browser/mail) which I don't want or need.

I've spotted only one other program in Synaptic, which is *Amaya*. But according to Wikipedia it doesn't have very good CSS support, ironic for a program designed to be a w3c testbed! Has anyone used this? Is it any good?

Are there any other programs worth checking out?

[Xinha Here!]("http://www.hypercubed.com/projects/firefox/")

---

### Post by TeaSwigger on 2007-11-02
Interesting extension, RAV TUX, ty :)

> **MrFSL said:**
> ...it doesn't sound like anyone is dismissing anyone else's efforts (at least not as I read it.)  It sounds more like frustrated users of HTML software not yet finding what they are looking for in terms of a replacement for Linux and giving their honest opinions as to the inadequacies in that software genre.

My apologies if anyone was offended. Perhaps then the expectations are too steep? Doing everything Dreamweaver does from the obvious WYSIWYG to file management to link checking to scripting to Flash to server integration without a cadre of full time coders, access to proprietary code and no funding is... well I guess it didn't occur to me to look for that, so maybe that's why it sounded the way it did to me. It perfectly understandable from the perspective of the frustration, again sorry for not taking that into full account.

If you should want and be able to use Dreamweaver in WINE, I'll be happy to help if I can. I have it running ok here.

---

### Post by MrFSL on 2007-11-02
> ...and no funding is... well I guess it didn't occur to me to look for that

Actually - I for one turn to Linux to provide all the features that I need **and more**! Remarkably, even without funding (or with much funding) this is possible and has been achieved many times over in the Linux/Open Source arena.  Just not concerning WYSIWYG HTML development software ;)

---

### Post by jroon on 2007-11-03
The idea that WYSIWYG design programs are just for the inexperienced is mistaken.   In Dreamweaver's split view, you can highlight an element and it highlights the corresponding code the source view.  I find this incredibly useful.  It also helps me to instantly see the results of changes I make.  I'm having a rough time letting go of Dreamweaver for these reasons.  I've run the gammut of Linux design programs over the last month:

-  My version of Dreamweaver, MX 2004, won't work for me yet under Wine.  There may be a few workarounds out there I haven't tried yet, but so far, no luck.  Perhaps I could install an older version, but then I lose things like SFTP.
  
- Aptana has been problematic for me, so I haven't spent much time exploring it.  I finally got it working again after my Gutsy upgrade only to discover they removed SFTP support in their free version when they launched their paid package.  I might pay $100 for the right program, but I can't tell yet if Aptana is the one.  I had a lot of trouble getting their version of Firebug to install, and I don't understand yet why I would pay for a troublesome version of Firebug to do my editing.  Still, Aptana has a nice feel, so I'll might check in with them again.

- Amaya won't start for me under Gutsy, so I haven't tried it either.

- Kompozer seems to be a solid program, but it doesn't have a split source/WYSIWYG screen.  And I can't seem to use undo in the source view.  It also mucks around with my CSS, and I don't want a WYSIWYG where I can't control the code.  Kompozer might be the best bet for somebody who doesn't want to directly edit their code. 

- Quanta was a colossal pain to get used to, but that's where I've landed for now.  The WYSIWYG won't refresh when I change CSS, which is not good, but maybe I'll find a solution to that.  As a former Dreamweaver user, the hardest thing in Quanta was figuring out how to set up my projects.  It can be done.  Perseverance does pay off.

---

### Post by ellis rowell on 2007-11-03
I used to use Star Office in Windows, then went to Open Office (another variation of Star Office). However, as the members of the organisation wanted a redesign of the website, I then went to Nvu. It does what I want and I have no problems with it. I suppose it depends on what you want. If you want to show how b***** clever you are with fancy graphics etc. then maybe it's not for you. 

I started in communications about 50 years ago (in the Cold War). I was taught that the essence of communication is to keep it simple. I have always applied this whether it was Radio Telephony, Telephone or the Internet. I still have my Home Office Radio Telephony instructors certificate somewhere and I did work in BT network planning for 12 years.

---

### Post by p_quarles on 2007-11-03
> **Scruffynerf said:**
> What I did find that worked wonderfully **for me** on Edgy was Mozilla Composer, however I've not been able to locate a Feisty-happy version. I know KompoZer (wtf with that stupid name) is supposed to mimic it along with NVU, but I have found it to be a lot buggier.

Feisty-friendly Mozilla Composer [here]("http://packages.debian.org/etch/iceape"). :)

I tested this in i386 Feisty a bit ago, and it works fine. Some elements of the suite suffer from the Debian/Ubuntu binary problems (notably the chat app), but Composer worked.

Also, the Iceape suite is in the normal repos as of Gutsy. 

+1 for Quanta, though. Yes, it's perplexing at first, but it is really powerful. I don't use it for the WYSIWYG, myself, just the project managament, so it may very well fail in that area.

---

### Post by bash on 2007-11-03
Anybody tried screem?

---

### Post by p_quarles on 2007-11-03
> **ubun-two said:**
> Anybody tried screem?
Yep. I think it's pretty good, but definitely not what you want if you need a WYSIWYG editor.

---

### Post by zugu on 2007-11-03
I stopped searching a long time ago. There's nothing like Dreamweaver 8.

---

### Post by klange on 2007-11-03
There's no such thing as "WYSIWYG"
Not even Dreamweaver is "WYSIWYG".
The only editor I've ever tried was an extension for Firefox that was discontinued over 3 years ago called MozEdit. It was really quite nice and was truly WYSIWYG, but it's buggy and incomplete and lacks the features of even the low end editors of today...

---

### Post by Tuxdequébec on 2008-02-21
I don't know if it's just me but when I installed Quanta, I didn't get to see the WYSIWYG part. I could work in code but nothing else. Was there a plugin of some sort I missed? Amaya told me that it had to install the older version because of my repositories. Fine. I installed the older version. Its menus are not very user-friendly... For example, when you want to edit a link. So I use it and work in codes. At that rate, I'll use the GEDIT. :lolflag: Even OpenOffice.org, that used to be fine, is losing it sometimes. It either needs a psychologist or the programmers do.

---

### Post by macogw on 2008-02-21
> **MrFSL said:**
> ...it doesn't sound like anyone is dismissing anyone else's efforts (at least not as I read it.)  It sounds more like frustrated users of HTML software not yet finding what they are looking for in terms of a replacement for Linux and giving their honest opinions as to the inadequacies in that software genre.

I've found a great Linux replacement for what I loved to use on Windows.  On Windows I used Notepad.  On Linux I use Vim.  Vim's even better than Notepad since it has syntax highlighting!

In all seriousness, I've yet to find "HTML software" on any OS that doesn't suck.  There simply is no replacement for properly written code.

> **Scruffynerf said:**
> 
Bluefish: Isn't really a WYSIWYG editor - I suppose that it may be good for coders, however so's Vi or Notepad. Could not see a way of enabling a graphical view.
My understanding of Bluefish is that it's an IDE for web-app development.  It's not for HTML & CSS based design, but for writing crazy dynamic PHP or Python or Perl or CGI script based websites.  Kinda like it's the Eclipse of web development.

---

### Post by sloggerkhan on 2008-02-21
I'm trying out iceape composer right now.
It's easy to use and the pages look exactly like you'd expect.
If you just want to throw together a table based layout, I'm sure it's fine, but I doubt it's good for anything fancy. The stuff it generates gets athenticated as 4.01 compliant transitional html, I think.

---

### Post by lespaul_rentals on 2008-02-22
I sometimes use Kompozer for Linux and I love it.  The best I've ever found for WYSIWYG is Adobe Dreamweaver CS3.

But, I usually code HTML using Kate.

---

### Post by RAV TUX on 2008-02-22
> **RAV TUX said:**
> [Xinha Here!]("http://www.hypercubed.com/projects/firefox/")

> **TeaSwigger said:**
> Interesting extension, RAV TUX, ty :)

Good Welcome. ;)

---

