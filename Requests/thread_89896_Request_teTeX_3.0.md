---
title: "Request: teTeX 3.0"
date: 2005-11-13
forum: Requests
---

### Post by bugmenot on 2005-11-13
Would be *very* welcome.
I managed to cram in teTeX 3 from Debian experimental half a year ago, but the cleaning up afterwards was a waste of time.
So, it was a joyful sight to see that it made it into Dapper.

There is a nice summarizing request from September here: [http://ubuntuforums.org/showthread.php?t=68439&highlight=tetex](http://ubuntuforums.org/showthread.php?t=68439&highlight=tetex)

---

### Post by jdong on 2005-11-13
What effect would such a backport have on compatibility, etc?

I'm not too familiar with tetex.

---

### Post by Manny C on 2005-11-13
Hehe...tetex is humungous...See this [INSTALL]("http://tug.org/teTeX/tetex-src/INSTALL") file for prerequisites.

Not sure how pressing this update is. Bugmenot, is there anything in TeTeX 3.0 that's new or worth updating? That is, what is in TeTeX 3.0 that you need that isn't in v. 2?

---

### Post by andrewpmk on 2005-11-13
[QUOTE=Manny C]Not sure how pressing this update is. Bugmenot, is there anything in TeTeX 3.0 that's new or worth updating? That is, what is in TeTeX 3.0 that you need that isn't in v. 2?[/QUOTE]

The [manual]("http://www.tug.org/teTeX/texmf/doc/tetex/TETEXDOC.pdf") includes a changelog. The biggest change seems to be that pdfetex is now the default TeX engine for all TeX invocations except "plain TeX", though pdfetex is capable of producing either pdf or dvi files. This allows greater typographic options and the use of the more common pdf format. Other changes include better support for right-to-left text (Aleph), PNG export functionality (dvipng), and the addition of various macro packages and fonts.

---

### Post by ember on 2005-11-13
I second this request - since I'm hopefully going to start writing on my diploma thesis soon this would be helpful. When I looked at the debian unstable package, it seemed, all dependencies are met.

---

### Post by jdong on 2005-11-13
Heh, builds fail because libxaw8-dev has a new name under Dapper....

And according to current Backports team policies, the backport can no longer be done.

---

### Post by bugmenot on 2005-11-14
[QUOTE=jdong]Heh, builds fail because libxaw8-dev has a new name under Dapper....

And according to current Backports team policies, the backport can no longer be done.[/QUOTE]

Too bad. But then, wasn't the point of backporting to make adaptations to +1's sources? What's the policy about?

EDIT: As for the reason to upgrade from 2.0.2 to 3.0. It's simply a mission to rid the world of horribly unreadable Type3 font rendering in PDFs still seen everywhere on campus and on the web. TeTex 3.0 makes a very big step by defaulting to pdfetex. Also, PDFs are now smaller, of higher quality and more compatible. Plus the big packages (memoir, beamer) are more recent. That's basically it.

For me personally, I already have a working install on my secondary box since I sorely needed it for ConTeXt.

---

### Post by jdong on 2005-11-14
> 

Too bad. But then, wasn't the point of backporting to make adaptations to +1's sources? What's the policy about?

No, actually it was to make +1's packages binary-compatible with the current release, which 99% of the time is a mere recompile against stable's libraries and environment.


In the current official Backports policies, no source modifications are permitted, though I'm toying with the idea of proposing to the tech board a new set of policies permitting the Ubuntu maintainers for packages to make backports-specific modifications.

---

### Post by bugmenot on 2005-11-14
So the name should rather be something like Ubuntu Recompiles? ;)

---

### Post by jdong on 2005-11-14
The name is "borrowed" from Debian Backports ([http://backports.org)](http://backports.org)), which does the same thing for Debian (where it's MUCH NEEDED a year or two into the release)

---

### Post by bugmenot on 2005-11-15
So, just getting apt-get source --build 'the package' on the Dapper sources would amount to the same thing?

---

### Post by chandra on 2005-11-15
If the revised policy allows it, I second the request for backported versions of the teTeX 3.0 family of packages, covering at least the following 2.02 versions:
tetex-base
tetex-bin
tetex-doc
tetex-extra

---

### Post by jdong on 2005-11-15
[QUOTE=bugmenot]So, just getting apt-get source --build 'the package' on the Dapper sources would amount to the same thing?[/QUOTE]

yes, though it probably won't work that way. You're gonna have to apt-source, edit dependencies, then do apt-get build-dep and dpkg-buildpackage. Not fun.

---

### Post by bugmenot on 2005-11-16
[QUOTE=jdong]apt-source, _edit dependencies_, then do apt-get build-dep and dpkg-buildpackage.[/QUOTE]
I don't want to overstress this, but doesn't that (emphasis) include accomodating for the following problem?
[quote=jdong]Heh, builds fail because libxaw8-dev has a new name under Dapper[/quote]

---

### Post by jdong on 2005-11-16
Yes -- though that is something the official backports branch is _NOT_ permitted to do (modify source packages)

---

### Post by Chris100 on 2005-11-16
My 2 cents for this request. I am also the guy living on tetex (paricular pdftex) and hope that tetex 3 will be the available sooner than later in ubuntu.

---

### Post by Salamander on 2005-11-16
Where do I have to put my sign on?... please move to tetex 3  !!!

Maik

---

### Post by Manny C on 2005-11-19
Moved myself to Dapper. TeTeX 3.0 definitely resides here and Dapper definitely working ***at the moment***.

---

### Post by kaspersv on 2005-11-20
[QUOTE=jdong]Yes -- though that is something the official backports branch is _NOT_ permitted to do (modify source packages)[/QUOTE]

If enough people reply to this post, is it likely you will consider bending the rules in this particular case? :p

---

### Post by dada1958 on 2005-11-21
Yeah, put tetex 3 on the repositories **NOW**!

Please?:)

---

### Post by bojaren on 2005-12-15
Is tetex 3 in backport-staging? or backport? 
I want to use tetex 3 in breezy not in the dapper(far from now...)
Please make tetex 3 available in breezy..

---

### Post by bojaren on 2005-12-29
Bump.. :)
Many people want it....tetex 3.0
tetex 2.0 is tooo old for today.

---

### Post by jdong on 2006-01-02
I cannot bend the rules, unless I submit my proposals for source-change backports to the Tech Board. It'll be met with strong opposition and questioning from some Ubuntu developers, and currently I am not ready with the strong rebuttals necessary to "win the argument" so to speak.

---

### Post by dada1958 on 2006-02-03
Maybe a little bit off topic but [TeXLive 2005]("http://www.tug.org/texlive/") could be an option. I downloaded the CD and I managed to install the stuff.
There are more people working on texlive than on tetex; they are experimenting with Debian repositories so in the not too distant future we can take profit of them.

niels@p3:~$ pdflatex --version
pdfeTeX 3.141592-1.30.4-2.2 (Web2C 7.5.5)
kpathsea version 3.5.5
Copyright 2005 Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).

---

### Post by sergio.callegari on 2006-04-11
But can and should a mere change in dependency naming be considered an actual source modification?

Apart from this philosophycal question, would it be possible, to provide a tetex 2 fixed to _embed_ all fonts when pdftex is used? This is a mere fix to a config file, and - to me - the fact that pdftex in tetex 2 does not embed fonts should be considered a bug  to fix with new packages (even remaining at tetex 2).

Using tetex 2 as distributed with current ubuntu, by pdflatex people make pdf files that are not correctly displayed on all hosts, thus breaking the platform independence of pdf. Furthermore the pdf being produced are not accepted by many publishers as valid camera-ready files.

---

### Post by incubus on 2006-04-15
I'm usually conservative with respect to rules and I see the trouble in convincing other developers in conceding to this.

However, I do think many people would benefit from teTeX 3.0 features and "bug-fixes". 

Also, many of us TeX users are undergraduate or graduate students, not to forget professors and professional writers, who were attracted by Ubuntu for its versatility and being fairly up-to-date. 

If it doesn't happen now, it is something that deserves consideration for the (near) future.

incubus

---

### Post by hugmenot on 2006-04-17
[QUOTE=incubus]If it doesn't happen now, it is something that deserves consideration for the (near) future.[/QUOTE]

In a sense the future /is now/. Therefore I suggest considering to upgrade to the next Ubuntu version. I use it since January and in my opinion it is already more stable than Breezy Badger because most of the stability depends on the bug-fixing that takes place upstream of Ubuntu between releases.

The upgrade process is usually pain-free and you will find TeTex updated in all its glory.

---

### Post by pte on 2006-04-28
Hi!

I have a question about the new version of latex in dapper. /usr/bin/latex links directly to /usr/bin/pdfetex. This means that running latex file.tex creates a pdf document instead of the expected dvi file. This creates problems with Kile and maybe other programs. Is it possible to make /usr/bin/latex into a wrapper that calls

/usr/bin/pdfetex -output-format=DVI?

kind regards,
Pieter

---

### Post by Gerektoolhy on 2006-05-07
We need teTeX 3.0!

---

