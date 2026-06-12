---
title: "texlive 2007"
date: 2007-02-21
forum: The Cafe
---

### Post by bns on 2007-02-21
According to the TeX Users Group, Texlive 2007 has been released.  Any word on when the packages might be available for ubuntu?

---

### Post by lhtown on 2007-02-22
I believe it is too late for Fiesty. I see that it still has 2005 in the repository. Maybe it will show up in Fiesty +1. If it makes the Debian unstable repository in the next few months, I would expect it then.

BTW, in case anyone is interested, here is a summary of the changes from Texlive 2005:
[http://www.tug.org/texlive/doc/texlive-en/live.html#x1-7000010.2](http://www.tug.org/texlive/doc/texlive-en/live.html#x1-7000010.2)

---

### Post by Mateo on 2007-02-22
is texlive even in the repo?  i think I have tetex installed on my system *blush*.

---

### Post by bns on 2007-02-22
Thanks for the info lhtown.

Yes, texlive is in the repository.  It installs without any trouble and it is more up to date and more complete than tetex.  Tetex still seems to be the default for most distributions.  I'm not sure why, but then I'm not a developer, so maybe there's a good reason.

---

### Post by Mateo on 2007-02-23
i see it now. I think before I had thought it was called tetexlive so when I searched in synaptic it didn't come up.  but now I uninstalled tetex and have texlive.  not sure if I'll ever know the difference since i'm a pretty basic user.

---

### Post by bns on 2007-02-23
I'm a pretty basic user myself...  But tex changes pretty quickly and the new packages are making life easier on us non-expert tex-ers.  I had tetex at first (because when I installed kile it automatically pulled in tetex) and I couldn't build some of the programs I had written in Windows with MikTex.  If you've been using tetex, then you probably won't notice much of a difference, but there are some nice features that tetex doesn't have.  At least, that's my experience.

---

### Post by sonmez on 2007-03-12
Hi there,

There are deb files here.

[http://www.tug.org/texlive/Debian/](http://www.tug.org/texlive/Debian/)

---

### Post by bns on 2007-03-12
Thanks!

---

### Post by nik1982 on 2007-03-31
Hi,

when i add the source [http://www.tug.org/texlive/Debian/]("http://www.tug.org/texlive/Debian/") to my sources.list version 2007 of texlive is appearing in the packet management. But if i try to install it every package i want to is showing me that some other package of texlive should not be installed... Anyone an idea how to unlock texlive 2007 with this package repository for ubuntu?

Thanks
Nik

---

### Post by bns on 2007-05-30
UPDATE: Just FYI, Texlive 2007 will be the standard for gutsy.

---

### Post by Rebelde on 2007-06-04
Hey guys, 

I was reading the posts on LiveTex and, judging by your comments, it looks far better than TeTeX. Just one question, do you know how to get it? I was looking around and apparently there is not 2007version in the Ubuntu-repositories. I also looked at [LiveText]("://www.tug.org/texlive/acquire.html") site, but, before downloading or doing something nasty to my poor computer, I'd rather ask you for your advice. Can you help me by giving me some hints on the downloading, installing and configuring LiveTex? Por favor :biggrin:

---

### Post by bns on 2007-06-04
The 2007 version will not be ready until gutsy gibbon.  Right now texlive 2005 is in the feisty repos.  The easiest thing to do would be to install texlive 2005 from the repos and wait for gutsy to upgrade to 2007.  You could try downloading and installing 2007, but it messes up the paths.  If you know what you're doing that's not hard to fix, but if you don't then it's probably best to go with 2005 for now.  Also, they're working on an unofficial repo for feisty,edgy, and maybe dapper but I don't think it's ready yet (see [this link]("http://ubuntuforums.org/showthread.php?t=411470&page=2")).

hth

---

### Post by Rebelde on 2007-06-04
Man!! 

That was fast reply! Thanks a lot! I think I have no many choices for now: either stick to TeTex or download LiveTex and wait until Gutsy is released. Have to think about it... Wait until october? ... :-k I will try something 'coz I'm a little bit desperate, so... I think I will be coming back for more advices very soon.
Gracias a lot [COLOR="Red"]bns[/COLOR]!!

---

### Post by krcabrer on 2008-06-04
Hi ubuntu gurus:

I am trying to install comicsans font on the my texlive that
I installed from the ubuntu repositories. (I install texlive full).

But I don't know where is the texmf directories (I see there
are several texmf-*.
I install .tds file in all the texmf directories and I do rehash,
but nothing happends.

The kile editor always shows me:
"cannot found comicsans.sty file".

Can you please help me where to unzip the .tds.zip file?
Am I doing something wrong when I rehash?

Thank you for your help.
Kenneth

PS: uname command shows me:
Linux ubuntu-desktop 2.6.24-18-rt #1 SMP PREEMPT RT Wed May 28 21:53:07 UTC 2008 x86_64 GNU/Linux
and latex --version shows me:
pdfTeX 3.141592-1.40.3-2.2 (Web2C 7.5.6)
kpathsea version 3.5.6
Copyright 2007 Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
Kpathsea is copyright 2007 Karl Berry and Olaf Weber.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the pdfTeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the pdfTeX source.
Primary author of pdfTeX: Peter Breitenlohner (eTeX)/Han The Thanh (pdfTeX).
Kpathsea written by Karl Berry, Olaf Weber, and others.

Compiled with libpng 1.2.15; using libpng 1.2.15
Compiled with zlib 1.2.3; using zlib 1.2.3
Compiled with xpdf version 3.01

---

### Post by hugmenot on 2008-06-04
Can you paste the output of these commands:

kpsewhich comicsans.sty
locate comicsans.sty

comicsans.tds.zip contains as top level folder "texmf", so it should be extracted in the folder above that.

cd /usr/local/share
sudo unzip -o comicsans.tds.zip
sudo texhash

BTW, bad bad choice of font.

---

### Post by bns on 2008-06-04
hugmenot is right, but I would recommend you extract it in $HOME.  That keeps stuff you install separate from the stuff that comes with the ubuntu package and that way it won't get deleted when/if you upgrade.

use texhash to update $HOME/texmf
use sudo texhash to update everything else

---

### Post by krcabrer on 2008-06-04
Thank you for your rapid answer.

Before I try to install with the command you suggest I type:
```
kpsewhich comicsans.sty
```

But nothing shows up.
The same with:

```
locate comicsans.sty
```

Then I type:
```
sudo unzip -o /home/kenneth/downloads/LaTeXPackage/comicsans.tds.zip 
sudo rehash
```

Again I type:
```
kpsewhich comicsans.sty
```

And I obtain nothing.
but when I type:

```
sudo kpsewhich comicsans.sty
```

At this time I obtain:

/usr/local/share/texmf/tex/latex/comicsans/comicsans.sty

But if I type:

```
locate comicsans.sty
``` or ```
sudo locate comicsans.sty
```

I obtain nothing

What am I doing worng? BTW, why do you say is a very,
very bad, font?
Do you mean for an aesthetic reason?

I try to make an example with the kile editor, but
the font shows a gibberish characters on the .dvi file.
I try to make the .ps file and the .pdf file.
It shows the words but not in the comic sans font.

Again, thank you very much for your help.

---

### Post by bns on 2008-06-04
OK.  Now it looks like you have the .sty installed correctly, but you don't have the font installed.  Try installing msttcorefonts (sudo aptitude install msttcorefonts).  See if that helps.

---

### Post by krcabrer on 2008-06-04
> **bns said:**
> OK.  Now it looks like you have the .sty installed correctly, but you don't have the font installed.  Try installing msttcorefonts (sudo aptitude install msttcorefonts).  See if that helps.

bns, I already installed msttcorefonts. I check it with
synaptic too.

Any way I reinstalled it again, but the problem persists.
There is no errors in the kile log file, but
I cannot get the comic font as I expect, and on the .dvi
file it shows just some black boxes in place of the characters.

Thank you very much for your help.

Kenneth.

---

### Post by hugmenot on 2008-06-04
"kpsewhich" should definitely return the same result as "sudo kpsewhich". kpsewhich is used to find the files needed during compilation.
The font itself has to be installed in /usr/local/share/texmf/fonts/ttf/
microsoft/comicsans/. This information is from the PDF manual. Did you have a look?

[http://www.ctan.org/tex-archive/macros/latex/contrib/comicsans/](http://www.ctan.org/tex-archive/macros/latex/contrib/comicsans/)

---

### Post by krcabrer on 2008-06-04
> **hugmenot said:**
> "kpsewhich" should definitely return the same result as "sudo kpsewhich". kpsewhich is used to find the files needed during compilation.
The font itself has to be installed in /usr/local/share/texmf/fonts/ttf/
microsoft/comicsans/. This information is from the PDF manual. Did you have a look?

[http://www.ctan.org/tex-archive/macros/latex/contrib/comicsans/](http://www.ctan.org/tex-archive/macros/latex/contrib/comicsans/)

No, "kpsewhich" and "sudo kpsewhich" do not give me the same result.

I found comicsans font on the following path:

```
/usr/local/share/texmf/fonts/tfm/microsoft/comicsans
```

not on

```
/usr/local/share/texmf/fonts/ttf/microsoft/comicsans/

```

there is a difference in "tfm" in my case and "ttf" in your path:

But I unzip the tds.zip file and it comes with that path.

I read the .pdf manual, I think the ttf and tfm is the problem, because
in the manual speaks about ttf not tfm... What do you think?

The other problem is why both "kpsewhich" and "sudo kpsewhich" do not
shows the same result?

Thank you for your help.

Kenneth

---

### Post by hugmenot on 2008-06-05
I think you may have not read thoroughly enough.
The package you downloaded can of course not include the font files themselves, because they are copyrighted by microsoft. All that is included are the support files that are needed to make stuff work in Latex. These include the important »font metrics«, which are called »tex font metrics« or .tfm files. The font files themselves are called .ttf, or »True Type Font«.
So, what you need to do is to copy the support files from the zip into your tex tree, or TEXMF. After that you place the .ttf font files from your Windows partition, or from msttcorefonts, into the texmf tree as well.
There are three actual texmf trees on your file system. The tree from the Ubuntu packages lives in /usr/share/texmf and will be overwritten. The tree in /usr/local/share/texmf is for customized but system-wide stuff. Then every user can create a texmf in his home directory for himself only.

Make sure that all files are in their right places, otherwise Latex will not find them. If it still doesn't work, post the .log file after you compiled your document.

---

### Post by hugmenot on 2008-06-05
BTW, all this hassle with font installation is well known for Latex users. There is a variant called XeTeX that allows you to use all fonts installed on your system, without any installation. I use it all the time.

If you want to give it a try, start from the attached example.
You compile it with the command

xelatex cs.tex.txt

---

### Post by krcabrer on 2008-06-08
> **hugmenot said:**
> BTW, all this hassle with font installation is well known for Latex users. There is a variant called XeTeX that allows you to use all fonts installed on your system, without any installation. I use it all the time.

If you want to give it a try, start from the attached example.
You compile it with the command

xelatex cs.tex.txt

Thank you, hugmenot.

It works!!!
I do the work with xelatex and it works!  :)

I'm still trying to install in the old fashion way, without
success, because I want to use the .tex -> .dvi -> .ps -> .pdf
process that I must do if I use powerdot for presentations with
pstricks package.

Thank you for your help.

---

### Post by hugmenot on 2008-06-08
You can use pstricks with xelatex normally. No dvips, pstopdf etc is needed because internally Xetex works with dvi.

---

### Post by krcabrer on 2008-06-08
> **hugmenot said:**
> You can use pstricks with xelatex normally. No dvips, pstopdf etc is needed because internally Xetex works with dvi.

Can I work also with powerdot, beamer, prosper and so on?

 Does any one had any experience with XeLaTeX an those packages?

Can I include .eps, .pdf, .png and .jpg graphics?

If the answer is yes... I am going to reconfigure kile to work with
XeLaTeX as the default compiler.

Again, thank you very much for your help.

Kenneth

---

### Post by hugmenot on 2008-06-09
You can use this [mailing list search engine]("http://search.gmane.org/?query=beamer&author=&group=gmane.comp.tex.xetex&sort=relevance&DEFAULTOP=and&xP=Zbeamer&xFILTERS=Gcomp.tex.xetex---A") to find out.

But seriously, don't use Comic Sans for presentations. I was always awfully distracted by this. You want to appear reputable, right. Comic Sans makes it look like, 'hey this is not serious, I'm a totally laid back and casual presentation, don't take me for granted...' etc.

Look here for a second opinion: [http://mjg59.livejournal.com/79244.html](http://mjg59.livejournal.com/79244.html)

---

