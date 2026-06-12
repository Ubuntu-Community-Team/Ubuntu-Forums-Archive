---
title: "AMD64 packages"
date: 2005-07-09
forum: Ubuntu Backports
---

### Post by jocken on 2005-07-09
How's the support and backporting of AMD64 packages? Are all the debs backported for i386 available for AMD64 aswell?

---

### Post by wantilles on 2005-07-10
[QUOTE=jocken]How's the support and backporting of AMD64 packages? Are all the debs backported for i386 available for AMD64 aswell?[/QUOTE]

Unfortunately, **not a single package is available for AMD64.**

---

### Post by mo42 on 2005-07-12
Well, I am working on amd64 backports. I have offered jdong my help, but did not get a response yet.

---

### Post by jocken on 2005-07-12
[QUOTE=mo42]Well, I am working on amd64 backports. I have offered jdong my help, but did not get a response yet.[/QUOTE]

If you need any help with testing or anything, let me know.

---

### Post by Jet2k5 on 2005-07-12
Same Here

---

### Post by duffman25 on 2005-07-13
Hi

Somebody said that backports was going to move to ubuntus official building system, but no news about that. :( I'm beginning to think on reinstalling a 32 bit ubuntu. The chroot solution is kinda akward.

---

### Post by mo42 on 2005-07-13
I have many packages already backported, but still no reply from jdong. And I don't have the bandwidth to make my own public repository. But I hope that this situation will soon change.

---

### Post by duffman25 on 2005-07-13
[QUOTE=mo42]I have many packages already backported, but still no reply from jdong. And I don't have the bandwidth to make my own public repository. But I hope that this situation will soon change.[/QUOTE]

Have you mailed him? There's a web site with some backports for ubuntu amd64: [http://www.rossen.be/modules/news/](http://www.rossen.be/modules/news/)

Maybe the owner can host your backports until the current backports proyect deals with the amd64 situation. I've posted in that web a suggestion to get in contact with the official backports proyect.  I did a comment on their web but hasn't been answered.

I think amd64 users need backports, since there are some bugs with the main apps delivered in hoary, and it would also be great if we had the hoary-extras repository, with libdvdcss2, java & similar packages in there.

---

### Post by jdong on 2005-07-13
Backports packages for AMD64 will be available very soon, now that we're transitioning to archive.ubuntu.com :)

---

### Post by mo42 on 2005-07-14
What does your answer mean? "No, we do not want your packages.", "I have no time at the moment, try to find a backports developer to review and upload your packages!" or "Wait for the transitioning to archive.ubuntu.com and then we will see..."?

Well, my packages are ready _now_ and I would like make others able to use them. Until then, amd64-users who want to help to test my packages  (jocken, Jet2k5...) can mail or pm me, so I can give them access to my private repository.

---

### Post by DancingSun on 2005-07-15
For those that can't wait for the official AMD64 backports, Tamir has taken this matter into his own hands in another thread:

[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

Maybe Tamir will be willing to add your packages into his repository.  And guess what, he's already made Sun Java JRE and JDK 1.5, Blackdown Java JRE and JDK 1.4 available for AMD64!

---

### Post by mo42 on 2005-07-16
[QUOTE=DancingSun]For those that can't wait for the official AMD64 backports, Tamir has taken this matter into his own hands in another thread:

[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

Maybe Tamir will be willing to add your packages into his repository.  And guess what, he's already made Sun Java JRE and JDK 1.5, Blackdown Java JRE and JDK 1.4 available for AMD64![/QUOTE]
 Thanks for your hint!
My efforts are now coordinated with Tamir, we have completely different packages. Until now, he has focused on Java and Enlightenment, and I concentrated on Breezy backports and Mono packages.
So I hope that there will be a public repository of my packages soon. Until then, everyone who wants to use my packages now, can send me a pm and will get access to my repository which I have set up.

---

### Post by duffman25 on 2005-07-17
[QUOTE=mo42]Thanks for your hint!
My efforts are now coordinated with Tamir, we have completely different packages. Until now, he has focused on Java and Enlightenment, and I concentrated on Breezy backports and Mono packages.
So I hope that there will be a public repository of my packages soon. Until then, everyone who wants to use my packages now, can send me a pm and will get access to my repository which I have set up.[/QUOTE]

Can I please ask what have you backported?
Thanxs

---

### Post by mo42 on 2005-07-18
okay, here is a list of my backported packages:
abiword 2.2.7
drivel 2.0.1
easytag 1.99.6
firefox 1.0.4
gaim 1.4.0
gdesklets 0.35
gimp 2.2.8
gnome-art 0.2
gnome-blog 0.8
gtk-engines-clearlooks 0.6.2
liferea 0.9.2
llvm 1.4
xchat 2.4.4
mono 1.1.8pre

But there are many more packages which I am going to backport. If you want to have some other packages that you would like to be backported, just ask.

Note that tamir also did some packages of java and enlightenment. The link has already been posted in this thread.

---

### Post by jocken on 2005-07-18
How about "doing" GNOME Sensors Applet from [http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)

---

### Post by mo42 on 2005-07-18
Done, and uploaded to the repository.

---

### Post by redlabour on 2005-07-19
[QUOTE=mo42]Done, and uploaded to the repository.[/QUOTE]
 Only want to agree to the others ..... IA64 Packages are hardly missing. :(

---

### Post by duffman25 on 2005-07-19
[QUOTE=redlabour]Only want to agree to the others ..... IA64 Packages are hardly missing. :([/QUOTE]


Just for your information, IA64 is VERY different from the amd64 (or x86_64) arquitecture. The IA64 is a completely different arquitecture NOT compatible with x86, while the amd64 is compatible with x86 (intel calls this em64t).

Links:
[http://en.wikipedia.org/wiki/IA64](http://en.wikipedia.org/wiki/IA64)
[http://en.wikipedia.org/wiki/X86_64](http://en.wikipedia.org/wiki/X86_64)

Debian is working on a multiarch port for amd64 (x86_64) which will make pretty easy to use both x86 & x86_64 binaries without a chroot jail. I hope this gets in breezy+1 :D

---

### Post by inklingx on 2005-07-22
[QUOTE=duffman25]Have you mailed him? There's a web site with some backports for ubuntu amd64: [http://www.rossen.be/modules/news/]("http://www.rossen.be/modules/news/")

Maybe the owner can host your backports until the current backports proyect deals with the amd64 situation. I've posted in that web a suggestion to get in contact with the official backports proyect. I did a comment on their web but hasn't been answered.[/QUOTE]

I'm the owner of [www.rossen.be]("http://www.rossen.be") (and i've been travelling last month, that's why i didn't respond earlier ;))
It is indeed a good idea to join our amd64 efforts in one repo. However the problem for me is finding enough spare time to make quality packages (the packages on rossen.be are already outdated :().

I can work 2 or 3 hours a week on backporting amd64 packages, so if someone would like some help with his/hers repo, please don't hesitate to contact me!

---

