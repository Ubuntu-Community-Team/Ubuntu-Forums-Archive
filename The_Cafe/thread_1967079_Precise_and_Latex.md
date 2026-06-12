---
title: "Precise and Latex"
date: 2012-04-27
forum: The Cafe
---

### Post by azangru on 2012-04-27
A question to those who've switched to Ubuntu 12.04 and use Latex.

I've booted into liveUSB to look around (and like it so far), and, exploring the Ubuntu Software Center, was surprized to see that only texlive2009 is available. Now, I don't know whether it's a big deal for me or not (I need Xetex, which used to be buggy), but anyhow - why texlive2009 when texlive2011 is available? That's the one I use on my OpenSuse12.1 box, and it came by default.

So I'd like to ask you - if you use Latex, which texlive distribution do you use? Have you installed it from the Ubuntu Software Center or from the TeX Users Group site ([http://www.tug.org/texlive/acquire-netinstall.html](http://www.tug.org/texlive/acquire-netinstall.html)). Frankly, I'd much prefer the Software Center to do everything for me. But such an outdated package? Hmm...

---

### Post by phosphide on 2012-04-27
Thats interesting that there is no others in the SC. Are you sure you searched right?

I use Kile or GNU Texmacs Editor. I haven't tried either one on 12.04 yet by the way. I'm still on 10.04.

---

### Post by azangru on 2012-04-27
> **phosphide said:**
> Are you sure you searched right?

Yep, I started Software Center and keyed "Texlive" in the search field. Got one hit - "TeX Live: A decent selection of the TeX Live packages", with one review in the bottom complaining that it's a "Good but outdated package". The "Version" field in the Software Center says that it's "texlive 2009-15".

---

### Post by alphacrucis2 on 2012-04-27
> **azangru said:**
> A question to those who've switched to Ubuntu 12.04 and use Latex.

I've booted into liveUSB to look around (and like it so far), and, exploring the Ubuntu Software Center, was surprized to see that only texlive2009 is available. Now, I don't know whether it's a big deal for me or not (I need Xetex, which used to be buggy), but anyhow - why texlive2009 when texlive2011 is available? That's the one I use on my OpenSuse12.1 box, and it came by default.

So I'd like to ask you - if you use Latex, which texlive distribution do you use? Have you installed it from the Ubuntu Software Center or from the TeX Users Group site ([http://www.tug.org/texlive/acquire-netinstall.html](http://www.tug.org/texlive/acquire-netinstall.html)). Frankly, I'd much prefer the Software Center to do everything for me. But such an outdated package? Hmm...

Log it as a bug in launchpad. I would guess the version hasn't been updated because debian testing haven't upgraded. Unless the ubuntu devs give things special attention, lts versions by default get whatever is in debian testing IIRC

---

### Post by azangru on 2012-04-27
It has been filed a while ago (not by me though - I haven't used Launchpad yet). Here's the link: [https://bugs.launchpad.net/ubuntu/+source/texlive-base/+bug/712521](https://bugs.launchpad.net/ubuntu/+source/texlive-base/+bug/712521)

---

### Post by alphacrucis2 on 2012-04-27
> **azangru said:**
> It has been filed a while ago (not by me though - I haven't used Launchpad yet). Here's the link: [https://bugs.launchpad.net/ubuntu/+source/texlive-base/+bug/712521](https://bugs.launchpad.net/ubuntu/+source/texlive-base/+bug/712521)

You could try the ppa mentioned by jbicha in that bug. It appears that debian have now upgraded to 2011 version, which means that the packages will get merged into ubuntu 12.10. There is also possibility of backport to 12.04

---

### Post by keithpeter on 2012-04-28
> **alphacrucis2 said:**
> You could try the ppa mentioned by jbicha in that bug. It appears that debian have now upgraded to 2011 version, which means that the packages will get merged into ubuntu 12.10. There is also possibility of backport to 12.04

Hello alphacrucis2

Synaptic is showing 2009-15 as the latest version of Texlive available in my Debian Wheezy install.

Still a few months to go before package freeze I gather from a quick reading of the forums, so 2011 may make it in.

---

### Post by Tac2 on 2012-04-28
I ran into the same problem, but there is an easy solution, though it may not be perfect depending on your needs - specifically, you can end up with two versions of TeX Live installed if you use an editor which installs TeX Live as a dependency. This is only a problem if you have limited space though - the two installations won't conflict. I will describe what I did to get the newest version - maybe it will work for you. There may be other and better solutions though.

I installed Kile as my editor, which brought in TeX Live 2009 from the repositories. I then downloaded the net install script from [http://tug.org/texlive/acquire-netinstall.html](http://tug.org/texlive/acquire-netinstall.html) and ran the install. Check the documentation if you have any issues ([http://tug.org/texlive/doc/texlive-en/texlive-en.html#x1-150003](http://tug.org/texlive/doc/texlive-en/texlive-en.html#x1-150003)). A tip: unless you run the install script as sudo (which I would not advise you to do) you will either have to change one of the install paths or chmod 777 /usr/local/ temporarily - note that doing so could pose a security risk though, so be sure to chmod it back to normal permissions after install is done. Let me know if you could use some more details.

I proceeded to install the full version (about 3 GB I think). After the installation there is just one more step: adding the new path to your environment variables. In ~/.profile add these lines:

```
  
  PATH=/usr/local/texlive/2011/bin/i386-linux:$PATH; export PATH
  MANPATH=/usr/local/texlive/2011/texmf/doc/man:$MANPATH; export MANPATH
  INFOPATH=/usr/local/texlive/2011/texmf/doc/info:$INFOPATH; export INFOPATH
```

(Note: if you're on Ubuntu 64 bit put x86_64-linux instead of i386-linux. Also, if you changed the install directory mentioned above, you must change the paths above to the one you installed TeX Live in.)

Now when you execute pdflatex (or any other TeX Live command) it should use the newest version you just installed.

Hope it helps.

---

### Post by azangru on 2012-04-28
> **Tac2 said:**
> I installed Kile as my editor, which brought in TeX Live 2009 from the repositories.

Thank you for the tip! So, am I correct to understand that if I install a tex editor from the Software Center (I prefer TexWorks), it will inevitably bring along TexLive 2009? And then, after I install TexLive 2011 and enter the proper path in the .profile file ([here]("http://ubuntuforums.org/showthread.php?t=1359211"), by the way, the recommendation was to edit .bashrc file), TexWorks will automatically use TexLive 2011, without any additional fiddling?

---

### Post by Tac2 on 2012-04-28
yeah it might be bashrc, I'm not at my pc so can't confirm. After editing the file, you can try 'echo $PATH' to check if the change took effect (you need to log out and back in first for the change to take effect).

And yes, it works :-) at least for me

---

### Post by nomiz on 2012-05-04
Texlive 2011 is is now in the 12.10 repositories. Isn't there a way of apt-pinning to use that repository?

---

### Post by nomiz on 2012-05-04
Trying it right now :)

Added to /etc/apt/sources.list:
```
## next release, for apt-pinning kile and texlive
deb http://nl.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
```

Added to /etc/apt/apt.conf.d/01ubuntu
```
APT::Default-Release "precise";
```

Added to /etc/apt/preferences
```
Package: *
Pin: release a=precise
Pin-Priority: 900

Package: *
Pin: release a=precise-backports
Pin-Priority: 600

Package: *
Pin: release a=quantal
Pin-Priority: 300
```

Now I'm hoping that all dependencies will normalize while moving to quantal in the future.. ;)

---

### Post by nomiz on 2012-05-04
Nice! Work like a charm :)

I installed kile and texlive with:
```
sudo apt-get install -t quantal kile dvipng kile \
latex-beamer latex-xcolor luatex pgf prosper texlive \ 
texlive-base texlive-binaries texlive-common  \
texlive-doc-base texlive-extra-utils texlive-font-utils \
texlive-fonts-recommended  texlive-fonts-recommended-doc \
texlive-generic-recommended texlive-latex-base \
texlive-latex-base-doc  texlive-latex-recommended \
texlive-latex-recommended-doc texlive-luatex \
texlive-pstricks texlive-pstricks-doc tipa \
texlive-latex-extra
```

---

