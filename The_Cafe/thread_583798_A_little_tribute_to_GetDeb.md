---
title: "A little tribute to GetDeb"
date: 2007-10-20
forum: The Cafe
---

### Post by risotto77 on 2007-10-20
I filed today a bug over at GetDeb.net, missing the latest Blender release 2.45 for Gutsy. Not more than three hours later they release Blender 2.45 for Gutsy. I think that was fast enough. I am very pleased. Thank you very much.

---

### Post by aimran on 2007-10-20
Correlation does not prove causality.

---

### Post by popch on 2007-10-20
> **aimran said:**
> Correlation does not prove causality.

Correlation does not disprove causality, either.

:lolflag:

---

### Post by aimran on 2007-10-20
> **popch said:**
> Correlation does not disprove causality, either.

:lolflag:

Touche!

---

### Post by 23meg on 2007-10-20
There's an ongoing discussion about GetDeb in [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss"), for those interested.

---

### Post by ruibernardo on 2007-10-21
Yes, people have that "bad habit" of installing everything from everywhere in their computer. Using getdeb or any other "third parties repository" have it's risks (not knowing who compiled what and what was compiled). 

It is sad that each Ubuntu release have "version frozen" on each version of each packages. This creates a gap of 6 month of "old" or "unfixed" packages like firehol, which has a bug since Feisty and will continue in Gutsy, though it could be easily updated, it will not be because it is Ubuntu policy not to do it between releases. This has it's pros (stability) and cons (no new version of software until someone makes a backport in the next Ubuntu release).

Getdeb (and others) try to fill that gap with fixes and new software versions, but it is too much of volunteers work (honestly, who knows what those "volunteers" did compiled on these packages? This isn't about getdeb, but all "third parties" ready to install packages, it's just a question of logic - installing things from who knows where is a bad thing to do - Windows is an example of that with the malware/virus/etc).

I'd like to be more positive about those "third parties" repos/websites, but they aren't (at least at the moment) "compatible" with the actual Ubuntu way and organization, but Ubuntu needs to find a way to "fill" the gap that getdeb and others are occupying and maybe create a new repository with "pre-backport" or "post-release" or "corrected" packages for cases like firehol and others? Could Getdeb help in this somehow? Could Ubuntu and Getdeb find a solution?

---

### Post by mikedep333 on 2007-10-21
epimeteo, I think you are overstating the danger of getdeb.

While I certainly would not grab from them something like the linux kernel, nautilus, or library like GTK, for the most part they are hosting programs that nothing else depends upon. The worst that installing and running alien arena (a FPS game) can do to my computer is cause X to crash.
I have yet to see a malicious package on 3rd party linux repo yet too.

More official backports is definitely a great idea. But until Ubuntu offers them, the only way I can play people in Alien Arena is to install the latest version. And that means using some source like getdeb. It is not always practical to continually use a past version of a piece of software, such as with FPS games.

---

### Post by ruibernardo on 2007-10-21
This is a tribute thread for getdeb, and I don't want to sound paranoid about it. It is a community of ubuntu users trying to help other people, which is a good thing, but the question of who compiles what is a serious question. You are installing those packages with sudo, so it's not a question of what privileges you are going to give when you run the program, but what was compiled and what it installs in your system.

If getdeb got recognized by Ubuntu (and this is the real question of getdeb for me), and it assured that no dist-upgrade problem would appear later, then it would be fine. But this involves much more work from getdeb and involves a  support from Ubuntu. 

That's what I'm talking about.

---

### Post by risotto77 on 2007-10-23
epimeteo. It is suggested to uninstall packages from GetDeb before dist-upgrading.( find them with version search 'getdeb' in Synaptic )


Personally I do not know the persons at GetDeb, but same thing goes for the people at Ubuntu and Debian. What they really puts into my computer I do not know. But this is open source software so I guess it is possible to get the sources, get the config files, and reproduce the exact deb files. Am I right? If so I really see no danger. And if so, does GetDeb differ from Debian and/or Ubuntu?

I have no reason to doubt the intentions of GetDeb.

I hope GetDeb and Ubuntu find a sollution to support eachother, maybe make GetDeb Ubuntu official. But only if GetDeb can continue serving up to date software.

---

### Post by loell on 2007-10-23
GetDeb.net, thank you :)

definitely one of the best if not the best source of newer deb package for ubuntu.

---

### Post by tehet on 2007-10-23
> **risotto77 said:**
> I have no reason to doubt the intentions of GetDeb.
Its' not just about intentions. These packages have not been properly tested against Gutsy as opposed to the official repo's. You may end up breaking your system (apt for instance) by installing 3rd party packages, regardless of whatever intentions. I know I have and I didn't have to wait until the next dist-upgrade. It was instantly borked.

---

### Post by loell on 2007-10-23
of course if they install from getdeb,net it is the user's resposibility to look out for his system. no doubt about that.

proper testing has somewhat a vague definition, 

from time to time , i've experienced  some rare packages from the official repo that can also broke your apt or the whole system. and after breaking your system, no one can tell you or assure you that its been properly tested. your best move is to file a bug report and hope for the next ubuntu release that it will get fix.

getdeb.net is there, to provide cutting edge software versions, that has not landed to ubuntu yet. 

it is never a replacement for the official ubuntu packages.

---

