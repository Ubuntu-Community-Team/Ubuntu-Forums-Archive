---
title: "help with repositories"
date: 2009-11-23
forum: System76 Support
---

### Post by jmwink on 2009-11-23
I use LaTeX very regularly throughout my workday and the pool of LaTeX packages in the Ubuntu repositories is a little delayed. I notice that debian unstable (sid) repositories have newer versions of a bunch of the LaTeX packages that I require. Of course, I don't want to supplant the ubuntu repositories with debian's, but I would like to use the most up-to-date version of LaTeX and a few affiliated packages. 

The solution I considered is to add a line to my sources.list for the tex subsection of the repository. Can anyone help me think through the possible negative consequences of this? Obviously, one danger is that one of the packages in this subsection will have dependencies that cannot be met, and that this would open up a seriously hellish mess. How seriously should I consider this worry? What are some other pitfalls?

Another option that I have seen floated either on this forum or elsewhere, is to add the unstable repositories, but make the package manager default to the ubuntu repositories. What do you think of this idea?

---

### Post by snowpine on 2009-11-23
Hi jmwink, never, ever use a Debian repository for Ubuntu. :)

In your case, I would recommend finding either
1) A Latex PPA for Ubuntu (a PPA is basically a one-application repository)
2) The source (or a .deb) for the latest Latex version.

You may find this page helpful: [http://www.latex-project.org/ftp.html](http://www.latex-project.org/ftp.html)

---

### Post by jmwink on 2009-11-23
thanks for the insight. duly noted. I should add that I have a full distribution of LaTeX -- the problem is not obtaining LaTeX, but updating the one I currently have. 

I'm not too up on how I would follow your option #1. Can you explain what how I could add a PPA, and what it's advantages would be? I understand #2, which is workable, but means lots of .deb files to download. For example, the package that I'm most interested in BibLaTeX (.8i-2) requires a version of texlive-latex-extra that is also not in the ubuntu repositories. I feel like it could get to the point where I'm downloading basically the entire TeX subsection of the debian repository... If that's the best solution, I'm game, it just seems, well, inelegant.

---

### Post by snowpine on 2009-11-23
A PPA is basically a one-application repository maintained by an untrusted 3rd party. Most of them are hosted at launchpad.net. For example, I used the OpenOffice PPA to get OO 3.0 in Hardy: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

No idea if anyone's put one together for Latex... Googling "latex ppa" gave some rather... interesting... results, and I'm at work right now. :)

Ubuntu is designed as a stable, time-based release distro. Its packages are always between 1 and 7 months out of date. I agree that workarounds to get the latest applications in Ubuntu are often inelegant. Is there a reason you are using Ubuntu instead of a more up-to-date distro like Sid?

---

### Post by jmwink on 2009-11-23
To answer your last question: I use Ubuntu because it's officially supported by System76, my laptop's manufacturer. :D

I'm running jaunty right now; would it be possible to update these packages via the karmic repositories? The ones in karmic might suffice. What are the possible drawbacks of downloading the .debs from the karmic repositories?

---

### Post by snowpine on 2009-11-23
Everything in Jaunty is at least six months old; I can see how that would be frustrating if you need the latest version of an application for work. 

Theoretically, you could try getting the Karmic .debs. The worst that is likely to happen is that some dependencies can't be satisfied, and the install fails.

---

### Post by gaussian on 2009-11-23
As a LaTeX user I would like to ask why you would want to do this? Little background: LaTeX/TeX is very old and very very stable system. Updating LaTeX is not like upgrading OpenOffice/MS-Office/Firefox or something like where you gain much of functionality with the cost of new bugs. LaTeX for most part just works and the TeX implementations progress really slowly.

If instead you are missing some LaTeX packages/styles/fonts etc, then I would recommend installing them to your own (user-specific) texmf-directory. But for that you don't need to install any ".deb" packages, you can just download the stuff from the web and install them yourself.

---

### Post by jmwink on 2009-11-24
Here's the full, detailed, personal problem. I don't want to upgrade LaTeX; I've been using it for a few years, and I understand its differences from traditional word processors both in its use and its ecology. All I'm trying to do is format an article's bibliography for publication, and the journal I'm sending it to requires me to follow the Chicago Manual of Style 15th ed. This style for those who don't use it is fairly idiosyncratic, but the journal in question does it one better by requiring end notes instead of footnotes. A developer is currently working on a style sheet that works with the BibLaTeX engine. 

That's where the hang-up happens, and why I started asking around here in the first place. The latest version of the BibLaTeX package can easily reprint footnotes as endnotes with a simple command in the preamble. The version of BibLaTeX installed via jaunty repositories does not define this command. Of course, I know that installing BibLaTeX version 0.8i-2 is as simple as following the install instructions and putting the important files in their place within the texmf directory tree. But BibLaTeX is a pretty complex little bugger, and depends upon eTeX and etoolbox packages. eTeX has been specified by the LaTeX team as the engine for the development of LaTeX, in the immediate future.

And this is the reason I wondered if I would need to do updates to the deeper root structure of LaTeX, since eTeX is part of the texlive-base package from the jaunty repositories. It's neither here nor there, as the problem has more or less been solved with only minor headaches.

---

### Post by snowpine on 2009-11-24
If it's just a one-time quick project, one possibility is to burn a sidux live cd, install the Debian Sid version of Latex you need, finish the project, then go back to using Ubuntu Jaunty.

Or, you could use Virtualbox to create a "latest version of Latex" virtual machine.

As I've never used Latex, I can't really comment specifically beyond that. Good luck!

---

### Post by gaussian on 2009-11-25
If you still need a solution, I think the best thing in this case probably would be to install minimal Deban/Sid system in chrooted environment until Ubuntu packages catch up. It is much more geekish solution than VirtualBox, requires little bit of googleing around to get it work, but having minimal Sid installation with just LaTeX/TeX installed there as a chrooted environment will use much less resources than VirtualBox, will not mess up your ubuntu installation and will be almost seamless.

---

### Post by jmwink on 2009-11-25
I managed to find exactly which packages the newish BibLaTeX depended upon, and installed those. It works reasonably well, though there's a bit of wackiness that doesn't impede final functionality. Once this deadline passes at the close of the semester, I should have more time to investigate without the tremendous pressure of publication deadline. Perhaps I'll experiment with the two different debian installation options suggested on this forum. Oh the puttering that awaits.

---

### Post by jdb on 2009-11-26
> **jmwink said:**
> I managed to find exactly which packages the newish BibLaTeX depended upon, and installed those. It works reasonably well, though there's a bit of wackiness that doesn't impede final functionality. Once this deadline passes at the close of the semester, I should have more time to investigate without the tremendous pressure of publication deadline. Perhaps I'll experiment with the two different debian installation options suggested on this forum. Oh the puttering that awaits.

Ah the putter list
Longer & longer it gets
I can not keep up

jdb

---

