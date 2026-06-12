---
title: "HOWTO: LaTeX [TeXLive] with Kile [gnome &amp; ...]"
date: 2006-03-09
forum: Tutorials
---

### Post by neoflight on 2006-03-09
--------------------------------------------------------------------------------
[COLOR="Blue"]EDIT: May 11, 2007.
Texlive and kile are avaialble in the repos. So you do not have to follow the howto to install texlive. Though Its good to have the texlive in a CD if you end up in a place where you dont have high speed internet connection. Another advantage of using repos is that you can selectively install stuff you need. for eg. language packs, and several meta packages. 

I would suggest installing texlive first and then kile to avoid tetex. I have also seen that when you install texlive from the repos, it will take out tetex if it is already installed. 
if you do not want to use kde stuff, and like gnome, try texmaker. [howto here]("http://ubuntuforums.org/showthread.php?t=131507")
--------------------------------------------------------------------------------
[/COLOR]
Hi,

For the latex lovers out there who are looking for a great editor, I highly recommend kile....Usually installing kile from the repos brings tetex with it....
This thread discusses installing LaTeX  (TEXLIVE2005)  the most comprehensive latex system.... 

If you want to install kile without tetex...follow this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=148954")

Various steps are:

**I. Download and install Texlive2005.**

1. Obtain TeXlive [here]("http://www.tug.org/texlive/"). and
[Burn it as iso image into a CD]("https://wiki.ubuntu.com/BurningIsoHowto"). 

2 Install Texlive2005 to disk[this is not for running it live]

Mount the texlive2005 CD and navigate to that directory using a terminal.
```
cd /media/cdrom0
```

3. now install process.

```
sudo sh install-tl.sh
```

4. You will be prompted with various options. I didnt change any of the suggested dir locations etc. just do this:
```
 i
``` and enter.

5. Now this is very important. set the PATH. [this information is provided in *[The TeX Live Guide]("http://www.tug.org/texlive/doc/texlive-en/live.pdf")* pp.11]. I did this before I could run texconfig. Its good if we could set the PATH first, I think.

```
PATH=/usr/local/texlive/2005/bin/i386-linux:$PATH; export PATH
```

you can do this at the terminal or put it at the end in /etc/bash.bashrc
This way, the path will be set when you login as this file is run at login. 

```
sudo gedit /etc/bash.bashrc
```

copy-paste the above PATH at the end of the file. save and close.

check the path and make sure that the path is there...
```
echo $PATH
```

discussions on setting env variables can be found [here]("http://www.ubuntuforums.org/showthread.php?t=2793&highlight=%2Fetc%2Fprofile+PATH").

6. Now run 

```
texconfig
```

if it returns 'command not found' the the Path is not set properly. i would suggest re-login after setting the path. Else, what you could do is to run the above path command at the terminal to activate it for the time being.

7. run 
```
sudo texhash
``` 
This updates various file name databases. [pp. 13 of tex live guide]

8. make sure it works...at the terminal type,

```
tex --version
```

you should see this:

```
TeX 3.141592 (Web2C 7.5.5)
kpathsea version 3.5.5
Copyright 2005 D.E. Knuth.
Kpathsea is copyright 2005 Karl Berry and Olaf Weber.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the TeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the TeX source.
Primary author of TeX: D.E. Knuth.
Kpathsea written by Karl Berry, Olaf Weber, and others.

```

Good. Its working ! Make sure all the tex commands are working by trying at the terminal (any directory) one by one...

latex, dvips, bibtex, gv, makeindex, xdvi, pdflatex, dvipdfm, ps2pdf, xpdf or acroread (install separately and make it executable), and mpost.

I have seen some permission issues preventing the commands running even from the terminal. so you can actually set the permissions using chmod command. Below is a sample (be careful when setting permission: do some research on issues when setting permissions or get help from some guru if in doubt). Couple of good references on this are  [here]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html") (detailed) and [here]("http://www.cae.wisc.edu/site/public/?title=linpermissions-change") (brief)

```
sudo chmod -R  755 /usr/local/texlive/2005/bin/i386-linux
```

**II. Install kile.**

1. [COLOR="Blue"]This section assumes that you haven't changed the TeXLive default dir locations [/COLOR]

```
sudo apt-get install kile
```

OR, you could use synaptic to install kile. In either case, Kile brings so many stuff with it (including some necessary libraries). Just say 'yes' and we will ignore its fellow packages 'including' tetex installation. IMO, texlive is much more comprehensive than tetex. 

2. Once both applications are installed in place, its time to start the configuration procedure. So open kile from 
```
Applications > Office > Kile
```
and  go to
```
Settings > Configure Kile
``` 
and select **Build** from the menu. This is where we need to put in all the info needed to link kile with texlive. All other options can be set as per your personal preferences. 

Observe that 
```
/usr/local/texlive/2005/bin/i386-linux/
```
is the locations where all the texlive executables we need are located. [this is the case when you have accepted the default directory locations the texlive installer specified]

3. You would see several listings under 'select a tool' menu. We will go step by step. A screen shot of what I have is given as plate1.

(i) select Latex and select 'modern' (in 'select a configuration')

Now, go to 'Advanced' tab and chose 'Run outside of Kile' in the 'Type' menu.
Come back to 'General' and copy the above directory in the command field to include /latex, which will then look like this.

```
/usr/local/texlive/2005/bin/i386-linux/latex
```
Note: Generally there are 3 major processes when using LaTeX:

a) compiling
Here we use applications such as latex, pdflatex, pdftex etc to compile a simple text file with .tex extension to dvi or pdf.

So, when configuring any compiler, the source extension filed can be left out since it will look in the directory to get the .tex file.

b) conversion
this is where we produce more useful file types such as .pdf, .ps etc.
For this we use covertion tools. such as dvips, ps2pdf, latex2html etc...

Here you need to specify the source and target extensions. its easy.
 
For e.g., when configuring DVItoPS tool, use 
```
/usr/local/texlive/2005/bin/i386-linux/dvips
```
options
```
-o '%S.ps' '%S.dvi'
```

Source: dvi
Target : ps

In general, after you do the set up as mentioned above for 'Advanced' tab. Make sure that you have the proper source and target file extensions given. Since we are not using tetex, might need to input these here after selecting "run ouside of kile".

Note: see 'Thoughts' below.

c) view files..

now, i think, this part is self explanatory. Same logic as before.
In some cases, as in my case, I use acroread to view pdf files. so just use the appropriate command. for e.g., you might use xpdf or acroread and these executables may not be in the locations we used for latex or pdflatex. 

Thoughts: if you have installed acroread separately then u need to just use 'acroread' in the command line for ViewsPDF (if acroread works from a normal terminal). select 'run outside of kile' here too. Sometimes it could happen that you will be using xpdf and if that is included in the tetex installation then do not bother to change anything.  Its just to view a pdf!!!

Samething with conversion tools.

** All we are interested in is to use texlive for *compiling***.

4. As you might have observed there are only a few steps involved in linking kile to texlive. they are: 
to,
-tell kile to run commands outside of kile

for that,
-give the paths to the executables appropriately.

And if you see no place to type in the command ['command' field under 'General'] then the "run outside of kile" is not set. again, to do this, go to 'Advanced' tab- do stuff, come back to 'General' and you will see the command field.

5. finally i would suggest restart kile and then do

```
Settings > system check...
```

Make sure that there are no serious errors. Things should come printed in green. You can safely ignore some of the warnings (orange) as we might not be using all of the options. See what things went wrong and take any action as necessary.

Do perform a check by running some sample tex files (simple to more complicated ones) using various compiling options such as latex, pdflatex etc...

an excellent source for latex source files can be found [here]("http://www.arxiv.org/")
and select any paper and then chose 'other' to get the zipped source.

6. To integrate aspell into kile. [by default kile uses ispell for spell check etc.]

```
Settings > Configure Kile..> Spelling > Client > Aspell.
```

If you dont have aspell installed then 

```
sudo apt-get install aspell
```

Or just use the convenient terminal window provided by kile.

```
aspell check filename.tex
```

and follow instructions...
-------                               --------                          ------------
Some Tips: (1) Everytime its good to clean the folder before checking new compiler. this will make sure that the commands are indeed working and generating appropriate files and not using those from the previous run.

(2)if you are getting an error on log file then it might be that the compiler is not working properly. go back to settings and see if you have given all the info correctly. 

(3)look at the command window output and check that all the commands you use are from the texlive installation and not tetex.

[HOWTO on using TeXmaker with TeXLive can be found here..]("http://ubuntuforums.org/showthread.php?t=131507")


I hope this helps... Please feel free to put your comments/suggestions/corrections.

---

### Post by neoflight on 2006-03-13
no complaints so far :mrgreen: .... i hope this is working for you.

---

### Post by cledezma on 2006-04-13
I am sorry, earlier I posted a question in this section. Now I realize this in not the place to do it. My apologies for that.

---

### Post by neoflight on 2006-04-15
[QUOTE=cledezma]I am sorry, earlier I posted a question in this section. Now I realize this in not the place to do it. My apologies for that.[/QUOTE]

you definitely  can post any number of messages here exactly or closely related to the topic...this is the place.....:)

---

### Post by pfdm on 2006-04-16
I have some problem , with texlive installation. I do all as it is said here but i can't launch kdvi with kile ,i 've an error  " can't find kpsewhich" , therefor i can launch and read a dvi when i launch it in a terminal. Other problem , it is with pdf , he said he can't find the font dictionnary, and replace by Helevetica, but can't find all font symbol .
So i search but can't find solution, if you know how to fix it?
Thks.

---

### Post by neoflight on 2006-04-22
[QUOTE=pfdm]I have some problem , with texlive installation. I do all as it is said here but i can't launch kdvi with kile ,i 've an error  " can't find kpsewhich" , therefor i can launch and read a dvi when i launch it in a terminal. Other problem , it is with pdf , he said he can't find the font dictionnary, and replace by Helevetica, but can't find all font symbol .
So i search but can't find solution, if you know how to fix it?
Thks.[/QUOTE]

sorry was busy with papers.....

i had the same problem with kile....i think the latest update with kile installed solves it... else ....try installing xdvi to view dvi.....it can also show u the eps figs.....i dont recommend using kdvi as it always gave me problems ......

install acroread for pdf viewer....its better than xpdf..... u can also install evince which is useful for ps and pdf viewing.....

another application u might need is 'ps2eps'.....openoffice draw is an excellent package for making schematics and print it as ps and use ps2eps to convert and use in latex......export as pdf to use with pdflatex....


all can be installed using synaptic or apt-get....try these and let me know....
hope it helps....

---

### Post by adamkane on 2006-04-22
Great HOWTOs. Many thanks.

Can you explain the benefits of kile/texlive vs kile/tetex vs kile/no tetex? My naive understanding is that texlive has more features than tetex.

I've used kile/tetex a bit, and it seemed to do what was needed.

Forgive all my ignorances. I'm hoping you can explain if one setup is preferable to another.

---

### Post by auroraborealis on 2006-04-23
What we really need is a decent Gnome *TeX IDE. The Kile interface makes me cringe every time I use it.

---

### Post by pfdm on 2006-04-26
Sorry , i have no time to test this. As soon as , i can do it , i'll post.

---

### Post by lamborghiniwang on 2006-10-29
> **neoflight said:**
> 
6. To integrate aspell into kile. [by default kile uses ispell for spell check etc.]

```
Settings > Configure Kile..> Spelling > Client > Aspell.
```

If you dont have aspell installed then 

```
sudo apt-get install aspell
```

Or just use the convenient terminal window provided by kile.

```
aspell check filename.tex
```



I'm having difficulty to make ispell/aspell work (Edgy+gnome+Kile 1.9.1). I get an error message says "I(a)spell could not be started" when I click "tools>spelling", and I couldn't find the "Spelling>Client" option in Kile 1.9.1. There are only 4 options under "Settings>Configure kile", which are "Kile","Latex","Tools" and "plugin".
The terminal method works though.
Any hints?

---

### Post by anders_jel on 2006-10-29
To get kile working with texlive from the ubuntu repositories (conflicts with tetex) without compiling kile from sources:

1. Get the kile deb file from [http://packages.ubuntulinux.org/edgy/tex/kile](http://packages.ubuntulinux.org/edgy/tex/kile)

2. Open a console and go to the location of the file

3. dpkg-deb -x kile_versionStuff.deb kile_versionStuff

4. dpkg-deb -e kile_versionStuff.deb kile_versionStuff/DEBIAN

5. Go to the kile_versionStuff/DEBIAN folder and open the control file using your favorite text editor

6. Change the package name from kile to kile-texlive

7. Change the dependency tetex-bin to texlive-base

8. Optional: Remove tetex stuff from recommends and add texlive and texlive-full instead

9. Add ", kile" to conflicts so you do not accidentially install kile on top of kile-texlive

10. Save the file and go back to the console and to the directory you started with (where you have the deb file).

11. mv kile_versionStuff kile-texlive_versionStuff

12. dpkg-deb -b kile-texlive_versionStuff kile-texlive_versionStuff.deb

13. dpkg -i kile-texlive_versionStuff.deb

14. If there are dependency problems open you favorite package manager and solve them, remove the broken kile-texlive package and go to step 13.

---

### Post by boban on 2006-11-09
> **lamborghiniwang said:**
> I'm having difficulty to make ispell/aspell work (Edgy+gnome+Kile 1.9.1). I get an error message says "I(a)spell could not be started" when I click "tools>spelling", and I couldn't find the "Spelling>Client" option in Kile 1.9.1. There are only 4 options under "Settings>Configure kile", which are "Kile","Latex","Tools" and "plugin".
The terminal method works though.
Any hints?

I had this problem too... Don't know how to make Kile use aspell in Gnome... But Kile can use ispell too...

---

### Post by adamkane on 2006-11-09
Gnome TeX editor:

Lyx + Maxima
[http://www.jstatsoft.org/v17/s01/v17s01.pdf](http://www.jstatsoft.org/v17/s01/v17s01.pdf)

---

### Post by neoflight on 2006-11-15
> **adamkane said:**
> Great HOWTOs. Many thanks.

Can you explain the benefits of kile/texlive vs kile/tetex vs kile/no tetex? My naive understanding is that texlive has more features than tetex.

I've used kile/tetex a bit, and it seemed to do what was needed.

Forgive all my ignorances. I'm hoping you can explain if one setup is preferable to another.

I have used tetex for sometime and i had trouble getting various custom (journal) packages installed and working correctly without errors...

texlive can have all those installed properly and its really easy. Its my personal preference though. May be  I made some mistakes in configuring tetex. 

the good news is now you can install texlive from the universe repos in edgy. in synaptics you can select the bundles you want with texlive. and can be used immediately without any tweaks. 

another good thing is that there is a latex plugin available for gedit. But i dont know how to add sequential commands to gedit plugin. i mean to make it run with latex first then apply dvipdfm and then acroread to view the result....any help would be appreciated...thanks

---

### Post by ichatz on 2006-11-26
> **boban said:**
> I had this problem too... Don't know how to make Kile use aspell in Gnome... But Kile can use ispell too...

In the new version of Kile 1.9 -- the configuration has moved to the "Kcontrol" -- so first install kcontrol (apt-get install kcontrol) and then from within kcontrol configure the spelling so that aspell is used.

I just figured it out... hope this solves your problem.

---

### Post by Aramis on 2006-12-12
Hi y'all,

I have strange problem using TeXLive and Kile, some bibliogrpahic styles do not work whereas a **locate** indicates that these are present, such as IEEEtranS for instance. Is there a command that I should re-use to refresh the database of supported bibliographic styles? or maybe something else?

I would like to stress that these styles work very well in MikTeX (win32), for instance.

For your information, in Kile I have a red message saying that BibTeX *finished with exit status 2*, which, I gather, indicates that BibTeX could not find the requested styles.

Help very much appreciated, and do no hesitate to ask for more details!

Happy TeXing and Thanks a lot,

Ar@mi$

---

### Post by neoflight on 2006-12-12
> **Aramis said:**
> Hi y'all,

I have strange problem using TeXLive and Kile, some bibliogrpahic styles do not work whereas a **locate** indicates that these are present, such as IEEEtranS for instance. Is there a command that I should re-use to refresh the database of supported bibliographic styles? or maybe something else?

I would like to stress that these styles work very well in MikTeX (win32), for instance.

For your information, in Kile I have a red message saying that BibTeX *finished with exit status 2*, which, I gather, indicates that BibTeX could not find the requested styles.

Help very much appreciated, and do no hesitate to ask for more details!

Happy TeXing and Thanks a lot,

Ar@mi$

can u run the commands outside of kile i mean from command line? 

if yes, then check the kile settings and use the appropriate commands...

if no:

did u install that package urself? did u run texhash command? 
run texconfig and texhash from the command line wit privilages and these will update the database...
see that the ieee folder is in the right place. the easy way to check is to see if you have other packages with it and how they are placed.... hope this helps....

---

### Post by Aramis on 2006-12-13
Hi Neoflight,

thanks for the reply. For your information:

1- I can run the various LaTeX commands from the command lines no problem. Before submitting this post I even copied and pasted Kile's command in to my terminal, and there is no apparent problem.
2- I installed tex-live as you indicated in the TeX-maker How-To (present on this forum), and as far as I can tell the package that causes problem (IEEEtranS) comes pre-installed:
```

locate IEEEtranS*.*
/usr/local/texlive/2005/texmf-dist/bibtex/bst/IEEEtran/IEEEtranS.bst

```
I actually posted in the TeX-Maker thread a problem similar with *dropping.sty* which is also present on the system but does not work. (Note: I just solved this problem, I shall post the solution in the TeX-Maker threads momentarely).
As you recommanded I re-run texconfig, and requested a texhash from the menu. However, it does not seem to solve my problems.
3- **Within Kile** the good news is that if I copy the above bst directly into the folder of my document the compilation is carried out no problem at all! which, in my opinion, indicates that the versions of IEEEtranS and tex-live are compatible. Note, that I have to add the package **url**. The documentation on IEEEtran provided with tex-live indicates that URLs are very tricky indeed, and adding the *url* package is recommanded.
4- **From the command line** using bibtex (with IEEEtranS) present poses problem in particular with web references :'(
5- **Without IEEEtranS.bst present** bibtex complains that it can't open the proper style file.

To conclude in my modest opinion, there are a couple of issues:
A) the LaTeX distribution is not fully searched when packages are requested used.
B) there might issues with the manner in which URLs are represented in the bibliographic database.

Any help is welcomed!

Ar@mi$

---

### Post by neoflight on 2006-12-13
Hello,

Is it that you are getting an error while using IEEEtranS?

I was going thru the distribution database and i find that the package name is **IEEEtrantools.sty** .

here: /texmf-texlive/tex/latex/IEEEtran/

how were you including the package in the source code? *.bst file?

Could you try 
```
\usepackage{IEEEtrantools}
```
and try to compile again? 

or better put IEEEtran.cls as in 

```
\documentclass{IEEEtran}
```

from IEEEtran.cls [lines 76-98]...this is a good file to get some useful info..
> % Available class options 
% (e.g., \documentclass[10pt,conference]{IEEEtran} 
% 
%             *** choose only one from each category ***
%
% 9pt, 10pt, 11pt, 12pt
%    Sets normal font size. The default is 10pt.
% 
% conference, journal, technote, peerreview, peerreviewca
%    determines format mode - conference papers, journal papers,
%    correspondence papers (technotes), or peer review papers. The user
%    should also select 9pt when using technote. peerreview is like
%    journal mode, but provides for a single-column "cover" title page for
%    anonymous peer review. The paper title (without the author names) is
%    repeated at the top of the page after the cover page. For peer review
%    papers, the \IEEEpeerreviewmaketitle command must be executed (will
%    automatically be ignored for non-peerreview modes) at the place the
%    cover page is to end, usually just after the abstract (keywords are
%    not normally used with peer review papers). peerreviewca is like
%    peerreview, but allows the author names to be entered and formatted
%    as with conference mode so that author affiliation and contact
%    information can be easily seen on the cover page.
%    The **default is journal**.

I am not familier with IEEE standards in referencing. I use AIAA package to get my papers done mostly. All I have to do is call the class. May be if you use package like above it will solve the problem? 

in the IEEEtran.cls file if you go to line # 3259 heading > %% CITATION AND BIBLIOGRAPHY COMMANDS you will find some useful comments... 

please let us know...hope this is a good suggestion...
thanks

---

### Post by Aramis on 2006-12-14
Hi Neoflight,

> **neoflight said:**
> Hello,

Is it that you are getting an error while using IEEEtranS?

Yes. Within Kile, I am told that the package cannot be found.
If, I copy the IEEEtranS.bst into the folder I am working in, then bibtex moans about the URLs. I do not want to have multiple copies of *.bst, or *.sty files on my system. This is a recipe for desaster.
> **neoflight said:**
> 
I was going thru the distribution database and i find that the package name is **IEEEtrantools.sty** .

here: /texmf-texlive/tex/latex/IEEEtran/

I just tested the following code:
```

\documentclass[a4paper,12pt]{article}
\usepackage{url}
\usepackage{IEEEtrantools}
\bibliographystyle{IEEEtranS}
\title{some title}

\begin{document}
\maketitle

-- snip --
\bibliography{myDatabase}
\end{document}

```
and I am told that IEEEtrantools cannot be found, which is once again untrue since:
```

locate IEEEtrantool*.*
/usr/local/texlive/2005/texmf-dist/tex/latex/IEEEtran/IEEEtrantools.sty

```
This is trully worrysome... :-k 
[quote=neoflight]
how were you including the package in the source code? *.bst file?
[/quote]
I trust I answered this question in the above. Let me know if I omitted something.
[quote=neoflight]
Could you try 
```
\usepackage{IEEEtrantools}
```
and try to compile again? 
[/quote]
that failed.
[quote=neoflight]

or better put IEEEtran.cls as in 

```
\documentclass{IEEEtran}
```
[/quote]
I desagree! I wish to use the IEEEtranS as my referencing style not my document style. With MikTeX (win32 distribution of LaTeX) I have used this referencing style with numerous document class including muthesis, and article with no problems at all. This is why I think something is not set properly.

[quote=neoflight]
from IEEEtran.cls [lines 76-98]...this is a good file to get some useful info..
[/quote]
I shall go have a look at it.
[quote=neoflight]
I am not familier with IEEE standards in referencing. I use AIAA package to get my papers done mostly. All I have to do is call the class. May be if you use package like above it will solve the problem? 
[/quote]
The IEEEtranS documentation indicates that it is a style very suitable for doctoral thesis in computing. I am getting started on my own thesis and this is why I am trying to ensure that I can work on the platform I want without too much problem. I don't know about the AIAA style,  I can try to use it, as a test, and see if it is a problem with the packages I use or a more general problem of PATH. What is the package's name for AIAA style? Anyways, I do know somethin' I don't like APA5 style of referencing at all - This stuff gives me headaches :evil: .
[quote=neoflight]
in the IEEEtran.cls file if you go to line # 3259 heading  you will find some useful comments... 
[/quote]
Bis! I shall go and read for myself.

[quote=neoflight]
please let us know...hope this is a good suggestion...
thanks[/QUOTE]
thanks to you, too :mrgreen:

Ar@mi$

---

### Post by neoflight on 2006-12-14
the code works for me  here!!!. interesting....
could you post the log file created while running latex?

---

### Post by Aramis on 2006-12-14
**Oh No!** I am such a bad user! I did not read the manual in full!
I assumed that since it was possible to use LaTeX, and bibtex, from the command line, it was okay to leave Kile default configuration!!!!!! 
Since my last post, I did add the full path in front of the commands I use the most (pdflatex, latex, bibitex) and since I no longer have this missing package problem for either IEEEtranS, or IEEEtrantools. My document compile without problems!

Geez, neoflight you were right all along I needed to double check the configuration of kile. Perhaps, it would be a nice addition to your how-to to stress that even though the path is correctly setup (all executables are accessible from the command prompt) you still need to configure kile with the full path!

that is my problem sorted!

thanks a lot again.

Ar@mi$ back to basics : learn how to read, and follow instructions to the letter.

---

### Post by neoflight on 2006-12-14
> **Aramis said:**
> **Oh No!** I am such a bad user! I did not read the manual in full!
I assumed that since it was possible to use LaTeX, and bibtex, from the command line, it was okay to leave Kile default configuration!!!!!! 
Since my last post, I did add the full path in front of the commands I use the most (pdflatex, latex, bibitex) and since I no longer have this missing package problem for either IEEEtranS, or IEEEtrantools. My document compile without problems!

Geez, neoflight you were right all along I needed to double check the configuration of kile. Perhaps, it would be a nice addition to your how-to to stress that even though the path is correctly setup (all executables are accessible from the command prompt) you still need to configure kile with the full path!

that is my problem sorted!

thanks a lot again.


NOTE:: there is an alternate way if you don't want to screw up.... if you are using Edgy, then texlive is in the universe repos... just install that one and then you don't need the entire path stuff as long as all the executables such as acroread, xdvi or evince installed and tell texmaker/kile to use it...._haven't_ tested this in kile....but for telive it works...!!!
Ar@mi$ back to basics : learn how to read, and follow instructions to the letter.

haha thats nice....its funny ain't it? ... it reminds me of my research...!
i almost convinced my prof that my results were right and then that was a brilliant  feet in engineering which could make some impact in the community...soon to be nuked by a variable with a wrong sign in my code...and we laughed our bowels out...!!!

anyway glad that you solved it... i was gonna varify the same thing from the log file...:mrgreen:

---

### Post by Aramis on 2006-12-15
Hi Neoflight,

your previous post is making me feel weird! where did that **Note** bit come from???
In any case, I could explain the reason why I did not care to fully configure Kile. I initially followed your How-To on TeXMaker, and this particular application did not require fiddling about with LaTeX PATH within the actual IDE. But it was important that the command lines worked and I did that. I was hoping/assuming that it would be the same in Kile.

I welcome the fact that tex-Live is now a debian package, it might make life easier for the users. It is too bad though, when you upgrade regularly, like I do (went from Brezzy to Dapper and finally Edgy using apt-get), you do not benefit of the cool stuff such as automatic Kile/LaTeX path combo configuration.

Ah well... Linux would not be Linux without these lessons.

Ar@mi$

PS: I am terrified of the fact that my PhD work might contain errors and these might be revealed at crucial moments, such as the final viva (gaps!!!!!!)

---

### Post by Cogito² on 2007-01-18
When I do a system check of kile, it says that neither Latex or tex are working properly. Here are my results:

```
#script:/bin/sh
#basedir:/tmp/kde-thomas/kilekgjwEe/

[TeX]
mustpass=where,basic,kile
executable=tex
where=
version=
basic=127

[PDFTeX]
mustpass=
executable=pdftex
where=
basic=127

[LaTeX]
mustpass=where,basic,kile
executable=latex
where=
basic=127

[PDFLaTeX]
mustpass=
executable=pdflatex
where=
basic=127

[DVItoPS]
mustpass=
executable=dvips
where=

[DVItoPDF]
mustpass=
executable=dvipdfm
where=

[PStoPDF]
mustpass=
executable=ps2pdf
where=/usr/bin/ps2pdf

[BibTeX]
mustpass=
executable=bibtex
where=

[MakeIndex]
mustpass=
executable=makeindex
where=

[KDVI]
mustpass=where
executable=kdvi
where=

[KGhostView]
mustpass=
executable=kghostview
where=

[KPDF]
mustpass=
executable=kpdf
where=

[Gv]
mustpass=
executable=gv
where=

[Acroread]
mustpass=
executable=acroread
where=

```

Does anyone know what may be the problem?

edit: It says it can't "find the binary for this essential tool" for latex, tex, and kdvi. Is there any common mistake that results in this?

edit2: This is the log when I try to run latex.

```
This is pdfeTeXk, Version 3.141592-1.30.4-2.2 (Web2C 7.5.5) (format=latex 2006.12.22)  18 JAN 2007 14:13
entering extended mode
 %&-line parsing enabled.
**course_notes.tex
(./course_notes.tex
LaTeX2e <2003/12/01>
Babel <v3.8g> and hyphenation patterns for english, usenglishmax, dumylang, noh
yphenation, basque, bulgarian, coptic, welsh, czech, slovak, german, ngerman, d
anish, spanish, catalan, estonian, finnish, french, greek, monogreek, ancientgr
eek, croatian, hungarian, interlingua, ibycus, indonesian, icelandic, italian, 
latin, mongolian, dutch, norsk, polish, portuguese, pinyin, romanian, russian, 
slovene, uppersorbian, serbian, swedish, turkish, ukenglish, ukrainian, loaded.

(/usr/local/texlive/2005/texmf-dist/tex/latex/base/article.cls
Document Class: article 2004/02/16 v1.4f Standard LaTeX document class
(/usr/local/texlive/2005/texmf-dist/tex/latex/base/size12.clo
File: size12.clo 2004/02/16 v1.4f Standard LaTeX file (size option)
)
\c@part=\count79
\c@section=\count80
\c@subsection=\count81
\c@subsubsection=\count82
\c@paragraph=\count83
\c@subparagraph=\count84
\c@figure=\count85
\c@table=\count86
\abovecaptionskip=\skip41
\belowcaptionskip=\skip42
\bibindent=\dimen102
)
(/usr/local/texlive/2005/texmf-dist/tex/latex/amslatex/amsmath.sty
Package: amsmath 2000/07/18 v2.13 AMS math features
\@mathmargin=\skip43

For additional information on amsmath, use the `?' option.
(/usr/local/texlive/2005/texmf-dist/tex/latex/amslatex/amstext.sty
Package: amstext 2000/06/29 v2.01

(/usr/local/texlive/2005/texmf-dist/tex/latex/amslatex/amsgen.sty
File: amsgen.sty 1999/11/30 v2.0
\@emptytoks=\toks14
\ex@=\dimen103
))
(/usr/local/texlive/2005/texmf-dist/tex/latex/amslatex/amsbsy.sty
Package: amsbsy 1999/11/29 v1.2d
\pmbraise@=\dimen104
)
(/usr/local/texlive/2005/texmf-dist/tex/latex/amslatex/amsopn.sty
Package: amsopn 1999/12/14 v2.01 operator names
)
\inf@bad=\count87
LaTeX Info: Redefining \frac on input line 211.
\uproot@=\count88
\leftroot@=\count89
LaTeX Info: Redefining \overline on input line 307.
\classnum@=\count90
\DOTSCASE@=\count91
LaTeX Info: Redefining \ldots on input line 379.
LaTeX Info: Redefining \dots on input line 382.
LaTeX Info: Redefining \cdots on input line 467.
\Mathstrutbox@=\box26
\strutbox@=\box27
\big@size=\dimen105
LaTeX Font Info:    Redeclaring font encoding OML on input line 567.
LaTeX Font Info:    Redeclaring font encoding OMS on input line 568.
\macc@depth=\count92
\c@MaxMatrixCols=\count93
\dotsspace@=\muskip10
\c@parentequation=\count94
\dspbrk@lvl=\count95
\tag@help=\toks15
\row@=\count96
\column@=\count97
\maxfields@=\count98
\andhelp@=\toks16
\eqnshift@=\dimen106
\alignsep@=\dimen107
\tagshift@=\dimen108
\tagwidth@=\dimen109
\totwidth@=\dimen110
\lineht@=\dimen111
\@envbody=\toks17
\multlinegap=\skip44
\multlinetaggap=\skip45
\mathdisplay@stack=\toks18
LaTeX Info: Redefining \[ on input line 2666.
LaTeX Info: Redefining \] on input line 2667.
)
(./course_notes.aux)
\openout1 = `course_notes.aux'.

LaTeX Font Info:    Checking defaults for OML/cmm/m/it on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for T1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OT1/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMS/cmsy/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for OMX/cmex/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.
LaTeX Font Info:    Checking defaults for U/cmr/m/n on input line 5.
LaTeX Font Info:    ... okay on input line 5.

! Undefined control sequence.
l.7 \chapter
            {Chapter Name}
? 
Missing character: There is no â in font cmr12!
Missing character: There is no &#8364; in font cmr12!
Missing character: There is no &#8482; in font cmr12!
Missing character: There is no â in font cmr12!
Missing character: There is no &#8364; in font cmr12!
Missing character: There is no &#8482; in font cmr12!
Missing character: There is no â in font cmr12!
Missing character: There is no &#8364; in font cmr12!
Missing character: There is no &#8482; in font cmr12!
Missing character: There is no â in font cmr12!
Missing character: There is no &#8364; in font cmr12!
Missing character: There is no &#8482; in font cmr12!
Missing character: There is no â in font cmr12!
Missing character: There is no &#8364; in font cmr12!
Missing character: There is no &#8482; in font cmr12!
[1

] (./course_notes.aux) ) 
Here is how much of TeX's memory you used:
 817 strings out of 94308
 9203 string characters out of 1170117
 58517 words of memory out of 1500000
 4109 multiletter control sequences out of 10000+50000
 6821 words of font info for 25 fonts, out of 1000000 for 2000
 647 hyphenation exceptions out of 8191
 27i,6n,20p,245b,189s stack positions out of 5000i,500n,6000p,200000b,5000s

Output written on course_notes.dvi (1 page, 1392 bytes).

```

edit: Okay well even though it says it doesn't work....it does. As long as I don't write "\chapter". That's a command in the latex help pdf i'm reading, but I guess I'll just ignore it for now...

---

### Post by neoflight on 2007-01-18
Are you using KDE or Gnome?

Anyway, 

could you compile the same file from the command line?
if it is not giving any error then the problem is with the kile set up...

if not, find the directory where the executables are and then give that path in the kile set up and select run outside of kile....

kdvi, kpdf, and gv are not installed automatically... if you insist on using those then you may get it from the repos....

```
sudo aptitude install kdvi kpdf gv
```

hope this helps...

---

### Post by venik212 on 2007-02-01
I wanted to use IEEEtran.cls in LyX, but did not know where to put it or how to makeit play nicely with LyX.  Any ideas?

---

### Post by Aramis on 2007-02-01
> **venik212 said:**
> I wanted to use IEEEtran.cls in LyX, but did not know where to put it or how to make it play nicely with LyX.  Any ideas?

Hi there,

this problem is not directly related to this particular subject. Anyways, you have to make sure that this package is within your LaTeX repository, in my case, and most certainly for those who use TeXLive 2005 IEEEtran.cls is located in /usr/local/texlive/2005/texmf-dist/tex/latex/IEEEtran/IEEEtran.cls . Once this is done, you have to refresh the LaTeX database so the compilers knows that new paquages are present. This is typically achieved by texhash (if I am wrong NeoFlight will surely highlight it :) ). Finally, and perhaps most importantly, the location that LyX searches when compiling documents must be setup properly. I did have issues with IEEE packages, myself and it all came down the way my editor was setup. If worse comes to worse you could place the package directly into your document folder, and it should work as long as there is no dependency involved.

HTH,

Ar@mi$

---

### Post by Mitlik on 2007-02-08
Everything seems to work except for the straight export to pdf for me.
I have it setup for:
configuration: modern
type: run outside kile
class: compile
command: /usr/local/texlive/2005/bin/i386-linux/pdfetex
options: -src -interaction=nonstopmode '%source'
I use pdfetex since pdflatex was just linking to this one. When I run it I get:
[PDFLaTeX] finished with exit status 1
No log is produced, I get nothing. Anyone have any ideas?


//Edit
Okay, I sat down and I was actually able to figure out was was going wrong with the pdflatex thing, class is supposed to be latex not compile, and options don't need -src. I might have a problem with a package used by Kig, but I'm going to look and see if I can't import it somehow.

---

### Post by toolisima on 2007-04-11
Hi there,
I just recently moved from Windows to Ubuntu and I really like it and all...and in this change I am trying to have all the programs I need to use, including a LaTex editor.
So with a friend's help I installed Texmaker (don't even remember why this and not Kile) and is nice and all...but I don't have all the libraries I need (e.g. amsmath, SIunits, etc.) so I've been searching for the way to install them...but it all seems rather confusing and have no specialized help here anymore...my friend is in the other side of the world now :( Then I read your post but still don't get it! It seems that everyone likes better Kile.
Do you think is better to install Kile? With Kile I can have all the libraries? Is it easier to install the ones I don't have?

---

### Post by toolisima on 2007-04-12
> **toolisima said:**
> Hi there,
I just recently moved from Windows to Ubuntu and I really like it and all...and in this change I am trying to have all the programs I need to use, including a LaTex editor.
So with a friend's help I installed Texmaker (don't even remember why this and not Kile) and is nice and all...but I don't have all the libraries I need (e.g. amsmath, SIunits, etc.) so I've been searching for the way to install them...but it all seems rather confusing and have no specialized help here anymore...my friend is in the other side of the world now :( Then I read your post but still don't get it! It seems that everyone likes better Kile.
Do you think is better to install Kile? With Kile I can have all the libraries? Is it easier to install the ones I don't have?

Hehehehe. I am replying myself!
So I got help some where else, and now Texmaker is good and runing the way I used to work with MikTex in Windows...all the libraries I need. Thanks Marco :lolflag: 
This is what I have done to make it work:

sudo apt-get install latex-ucs latex-ucs-contrib tetex-base tetex-extra tetex-bin

(The libraries that were missing and now I have: amsmath, natbib, booktabs, rotating, SIunits, times)

---

### Post by teHIngo on 2007-04-24
Guys I your help as LaTeX Professionals!! :(
Please take a look at this: [http://ubuntuforums.org/showthread.php?p=2525920#post2525920](http://ubuntuforums.org/showthread.php?p=2525920#post2525920)

---

### Post by tkjacobsen on 2007-04-24
Feisty users can just install texlive and kile from the repos. Working great for me.

---

### Post by jbor7755 on 2007-05-08
I have a problem with getting kile to recognise the paths to the comands:

The commands work fine at the command prompt.  I have also entered the correct path in front of all the common comands in the kile configuration box. Yet when I run system check all I get are errors.

Everything fails except PStoPDF.

Is there a magical tick box which needs to be ticked or something?  I am sure I followed the instructions and added the paths correctly.

Cheers

---

### Post by tkjacobsen on 2007-05-08
What ubuntu and desktop do you use.
How did you install tetex / texlive / kile ?

---

### Post by jbor7755 on 2007-05-09
I have Dapper with gnome. I installed kile from source without tetex as directed by attached how to on kile without tetex. I installed texlive from CD exactly as prescribed.

kile opens and I can run latex commands at the prompt just fine but kile for some reason doesn't like the paths it needs to run the commands. (System check fails)

---

### Post by htex on 2007-05-09
hi people;
CAN SOMEONE HELP.
I want to know if there is problem when i install kile in first and the texlive CD as a second.

---

### Post by neoflight on 2007-05-09
> **htex said:**
> hi people;
CAN SOMEONE HELP.
I want to know if there is problem when i install kile in first and the texlive CD as a second.

there is a lot of confusion in getting kile without tetex when people are looking for texlive.. i would suggest, in this case, install texlive from the repos first... and then install kile...

if you try the other way around, i.e, when you try to install kile first, it will try to bring many of the  latex executable with it so that kile can serve its purpose....when texlive is installed first, then the latex executables are already in place and kile will be happy and then aptitude/apt-get will only suggest bringing in tetex and not install.... I use texlive+kile...

NOTE: also i recently noticed that even when u install kile first (bringing in tetex). the existing tetex system will be removed if texlive is installed from the REPOS or using apt. there seems to be conflict among these two systems...which is good i guess...:)

anyway, IMHO, its a good idea to go with texlive as it is THE most comprehensive latex system you can get in a single install.

hope this helps...

---

### Post by neoflight on 2007-05-09
> **jbor7755 said:**
> I have Dapper with gnome. I installed kile from source without tetex as directed by attached how to on kile without tetex. I installed texlive from CD exactly as prescribed.

kile opens and I can run latex commands at the prompt just fine but kile for some reason doesn't like the paths it needs to run the commands. (System check fails)

this is usually the case when the paths are not set correctly in kile...
go to 
Tools>Configure Kile> tools tab>build > {executables} 

and provide the commands you specified in the path one by one there in the 
'command' field... system check might fail when one or more of the commands such as 
view ps or  pdf, or similar is not correctly specified.. for eg: you intent to use acroread to view the pdf but kile might be looking for kpdf which might not be there. check what the error is and adjust accordingly... its like learning how to ride a bicycle...just have to learn only once...:D

---

### Post by htex on 2007-05-10
In first thank you for the quick reply.

Now, if i install texlive in first, i didn't understand with this tutorial how i can configure kile (excuse me because i 'am not very well in english-thank you for you comprehence-:( ).
Because i have not connexion :( , can you help me to download kile packages without tetex and 	
and with which orders will be able I to install it.
finally, how will be able I to configure kile  to work with texlive cd.
I will like well that you use photos for better explaining us. Of course if there is not no time to you 

thank you in advance :) .

---

### Post by htex on 2007-05-10
hi neoflight

I think that it isn't necessary to reply for my request because I have just found, in this moment even, your tuto explaining the configuration and the installation of kile without tetex. Thank you very much for all help that you carry us.:lolflag: 

That god blesses you.:) :)

---

### Post by jbor7755 on 2007-05-10
> this is usually the case when the paths are not set correctly in kile...
go to 
Tools>Configure Kile> tools tab>build > {executables} 

and provide the commands you specified in the path one by one there in the 
'command' field... system check might fail when one or more of the commands such as 
view ps or pdf, or similar is not correctly specified.. for eg: you intent to use acroread to view the pdf but kile might be looking for kpdf which might not be there. check what the error is and adjust accordingly... its like learning how to ride a bicycle...just have to learn only once...

The thing is that the paths ARE correctly set. I have added the correct path to all the executables but Kile still doesn't like it. I have double and triple checked.
Do I need to do something else?
Are there extra commands which need to go into the "options" textbox?

Your help is greatly appreciated.

---

### Post by jbor7755 on 2007-05-10
Well it appears that the system check is wrong!
I just did a test document with my paths and it worked.

So ignore my last post.

However the fact that kile has to be manually forced to search for texlive and not its default tetex is a big pain. Especially as there is no way to access help files and tex documentation. The fact that it requires a lot of other KDE stuff to run is also wastefull of computer resources. Is there another editor which may fit the bill and be a bit easier to set up?

Prosit

---

### Post by neoflight on 2007-05-11
> **jbor7755 said:**
> Well it appears that the system check is wrong!
I just did a test document with my paths and it worked.

So ignore my last post.

However the fact that kile has to be manually forced to search for texlive and not its default tetex is a big pain. Especially as there is no way to access help files and tex documentation. The fact that it requires a lot of other KDE stuff to run is also wastefull of computer resources. Is there another editor which may fit the bill and be a bit easier to set up?

Prosit

I will imagine that you are using a linux distribution with gnome as your window envir...
If thats true then I would suggest you try out texmaker. This is made by the same guy who worked as a dev for kile. I have another [howto]("http://ubuntuforums.org/showthread.php?t=131507") on the same in this forum if you are interested. 

The things are same. Just do the installation from the repos.

---

### Post by venik212 on 2007-05-12
How do I tell Kile to search for TexLive?  I think I am having the same sort of problem-- KILE not finding the packages I have installed.

---

### Post by venik212 on 2007-05-12
Can someone who had installed Texlive and Kile and got them to work together under Kubuntu tell us EXACTLY how they did it?
Thanks

---

### Post by tkjacobsen on 2007-05-13
In fesity!. 

Uninstall tetex and kile if installed!!!
First I installed texlive-full and NOT kile. (If you don't want all of it then don't install texlive-full but only the packages you need/want)
Then kile.

This is because if you choose to install kile it will mark tetex if no latex is installed (tetex or texlive)

(I installed all from the repos)

---

### Post by htex on 2007-05-14
[COLOR="DarkGreen"]Hi latex users[/COLOR]

[SIZE="2"]Here, I could install both distribution (i.e. texlive and tetex), and I realized that I could compile with both. The marvellous one :KS  in all that it is that I could use both at the same time version. Now what appears equivocal to me, is-possible? I wonder whether it exist an example that I will be able to compile with texlive CD but does not go with tetex. With an aim of checking the two distributions goes really sets.
[/SIZE]

Good luck for all.

---

### Post by skywatcher on 2007-05-16
Hi

I received Tex Live yesterday, and successfully installed it on Linux (Dapper) from the CD. I also followed the How-To on setting up Kile, which works for the most part, except that PStoPDF does not work. When I checked, I noticed that ps2pdf is not to be found at 

```
/usr/local/texlive/2007/bin/i386-linux/ps2pdf
```.

Any idea where it may be found? Please help.

Thanks.

---

### Post by venik212 on 2007-05-18
I hope this is the right place for this question:
Under Windows, WinEdt has a button to compile a TeX file (pdflatex) as many times as it needs to, until it resolves all references, etc.  With Kile I have to click on the PDFLATEX button several times to get the same effect.  Is there a setting to avoid that, and tell Kile to repeat it as often as it needs to?
Thanks,

---

### Post by skywatcher on 2007-05-18
Hi

> **venik212 said:**
> I hope this is the right place for this question:
Under Windows, WinEdt has a button to compile a TeX file (pdflatex) as many times as it needs to, until it resolves all references, etc.  With Kile I have to click on the PDFLATEX button several times to get the same effect.  Is there a setting to avoid that, and tell Kile to repeat it as often as it needs to?
Thanks,

I don't know if this will help, but there is an option under "Settings > Configure Kile > Build > PDFLateX > General ... rerun LaTeX when necessary"

---

### Post by faraazs on 2007-05-26
> **auroraborealis said:**
> What we really need is a decent Gnome *TeX IDE. The Kile interface makes me cringe every time I use it.There is the LaTeX plugin for Gedit...you won't be able to compile directly from Gedit with just this though but its still pretty nice :). I find kile to be a little more powerful though.

[http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

---

### Post by skywatcher on 2007-05-28
Hi everyone

I'm just wondering, has anyone tried WineFish? The name is somewhat inappropriate, but who knows?

---

### Post by jbor7755 on 2007-06-20
I think that kile has a lot of potential as a tex editor and would like to continue using it.
I also like texlive as it is well maintained and up to date.
But this method of installation is now annoying me.
Because I installed kile from source, I don't have help files so I don't know how to install english or other language dictionaries.
A font for displaying accents and umlaute in Kile are also missing. I like to use the ae package so I don't have to encode accents. I use an international keyboard layout instead.  Because the fonts are missing such characters are displayed as little squares.
Texmaker is not a viable alternative as it is missing project features (needed for my disertation) and will not even attempt to display accented characters.

The most annoying thing now is that I don't know what command to use to uninstall kile as it was compiled from source (according to this how to) and is not from the repositories.

How can I uninstall it and start again?

---

### Post by neoflight on 2007-06-21
you could do 
```
dpkg -r packagename 
```
and remove all the instances of kile manually...

unfortunately, i am not familier with use of  languages other than english..sorry that i could not be of help there...

EDIT: i just realized that you cannot use dpkg here...
I think the best way is to remove it manually

---

### Post by lariosa42 on 2008-06-12
Hello, I am new to linux (just getting familiar with the terminal) but have used LaTeX with XP for a few years.  I just installed TeXLive 2007 and then Kile 2.0.0, but I have been unsuccessful in "linking" them together.  I tried to follow the description in the original post very closely (I got a little confused around section 3).  When I try to complie a simple TeX document in Kile, I get

[LaTeX] Test => Test.dvi (usr/local/texlive/2007/bin/i386-linux/latex)
[LaTeX] finished with exit status 127
[LaTeX] 0 errors, 0 warnings, 0 badboxes

and a similar thing when I try to view the .dvi file.  The document does not show up, and I am not sure what is going wrong.  My guess is something is incorrect with my directories.  I use LaTeX everyday, so it is important that I get it working soon.  Any help would be greatly appreciated!  Thanks in advance.

---

### Post by Van Fanel on 2008-06-23
It seems you haven't installed the kdvi package. The kdvi is the .dvi previewer set by default on Kile.

Just go to Synaptic Package Manager, search for 'kdvi' and install it.

---

### Post by D.Sync on 2008-07-24
I'm just started to use Kile and I had already setup the correct path for each command except:

P/S:
* I installed texlive2007 via repository

I had some path for commands as below (shown in [Configure Kile] -> [Tools] -> [Build]) which I had not yet set because I didn't know what is the corresponding file used by texlive. Hopefully you can setup the path or recommend other tools that does the commands. Regards.

1. Forward Dvi
2. Lilipond
3. Ps2Pdf
4. ViewBib
5. ViewPdf (currently using Kpdf, is there any other else that offers great functionality?)
6. Dvi2Png
7. DBLatex
8. Tar
9. Asy

---

### Post by macabro22 on 2009-04-07
Hi there, I am using texmaker and other KDE apps in gnome to write a latex text and these programs suddenly and very frequently alternate imput methods and I can no longer type accented characters. I then have to go into SCIM input method and activate my keyboard layout again. This is very annoying. Do you guys experience this behavior as well? How can I fix it?

---

### Post by jefflee on 2011-12-06
I ran into the same problem and figured out what's wrong. I suppose your problem had the same cause as mine.

Run command 'which latex' to see which latex is used by Kile. If it's /usr/bin/latex, congrats! You installed two TeX distributions, for example, one TexLive and one TeTex. In my case, I installed two TexLive. The one made trouble is an older version of texlive, installed as a depended package of Doxygen. It doesn't contain IEEEtran*. 

Therefore, though you installed the newest TexLive, Kile still uses the other TeX. In the old TeX's databse, there's no IEEEtran* style files. That led to the mysterious failure. Later you used a full path to specify latex commands, and then Kile locates the newer TexLive installation.

Solution: 
sudo apt-get remove [tex-distribution-name]

> **Aramis said:**
> **Oh No!** I am such a bad user! I did not read the manual in full!
I assumed that since it was possible to use LaTeX, and bibtex, from the command line, it was okay to leave Kile default configuration!!!!!! 
Since my last post, I did add the full path in front of the commands I use the most (pdflatex, latex, bibitex) and since I no longer have this missing package problem for either IEEEtranS, or IEEEtrantools. My document compile without problems!

Geez, neoflight you were right all along I needed to double check the configuration of kile. Perhaps, it would be a nice addition to your how-to to stress that even though the path is correctly setup (all executables are accessible from the command prompt) you still need to configure kile with the full path!

that is my problem sorted!

thanks a lot again.

Ar@mi$ back to basics : learn how to read, and follow instructions to the letter.

---

### Post by gweinstein on 2013-06-27
Trying to revive an old thread... I have just recently decided to finally start using BibTeX. Everything is pretty straightforward, except the placement of the database. I want the bib files to be in one location which hopefully gets backed up, e.g. a Dropbox folder. So I created ~/Dropbox/.texmf and edited 05TeXMF.cnf to have the definition:

> TEXMFHOME = $HOME/Dropbox/.texmf

I even "sudo texhash" -ed and "sudo mktexlsr" -ed although not everyone seemed to agree that it was necessary, but BibTeX still cannot find the database unless I give a full pathname in the .tex file. What am I missing?

Thanks in advance!

---

### Post by gweinstein on 2013-06-27
BTW, the OS is wrong. I am running 12.04, but for some reason I am not allowed to edit my profile.

EDIT: Was able to edit my profile and change my distro!

---

