---
title: "New version of Lyx. Breezy debs available."
date: 2006-03-10
forum: The Cafe
---

### Post by kleeman on 2006-03-10
Good morning scientific/latex bling lovers (my sabdfl imitation). A major new version of lyx the spiffy latex frontend has arrived:

[http://wiki.lyx.org/LyX/NewInLyX14](http://wiki.lyx.org/LyX/NewInLyX14)

I have prepared some breezy debs which you can download from here:

[ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/ubuntu/](ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/ubuntu/)

Note the new gnome frontend. Be careful with it because it is still buggy.

There is a README which explains installation but if you have any missing dependencies then

sudo apt-get -f install

is your friend.

This version can be a little sluggish compared to the 1.3.6 version in breezy and there are issues with exchanging
output files between version so be careful how you use it.

---

### Post by neoflight on 2006-03-10
Hey Kleeman

Interesting... thanks for the link. btw....
Howz lyx's  performance in bibliography? 
I never used a wysiwyg program for latex..... 

later.

---

### Post by kleeman on 2006-03-10
[QUOTE=neoflight]Hey Kleeman

Interesting... thanks for the link. btw....
Howz lyx's  performance in bibliography? 
I never used a wysiwyg program for latex..... 

later.[/QUOTE]
Pretty good actually. I use jabref and Pybliographic with it and you can export citations to lyx via a pipe from these apps.
One big advance in 1.4.0 is versioning control which should make collaboration (joint papers) easier.

---

### Post by Brunellus on 2006-03-10
questions:  

1) will this be in dapper?

2)  why only scientists?  

I like LyX, and I'm really really impressed by it, but I need to find some resources on making proper templates for humanities-style papers and legal documents (and their associated bibliographies).

---

### Post by Paulus on 2006-03-10
Hi, I am keen to try out lyx as I will be writing my dissertation entirely in latex.  I'm attempting to install the debs you kindly provided on dapper, but encountered problems installing lyx-qt_1.4.0-1.lyx.org.1_i386.deb ,  it's complaining about libaiksaurus0 dependency, which is obsolete in dapper and is replaced by libaiksaurus-1.2-0c2a (which I have installed).  Any ideas on how I could sort this?

Thanks in advance :)

---

### Post by kleeman on 2006-03-10
I doubt it very much that this will be in dapper as we have passed the upstream freeze deadline. I know that 1.3.7 is there now.

Sorry I didn't mean to imply this was only for scientists (my words were scientist/latex bling lovers). If you check the lyx-list you will see that many humanities folks use it and discuss their issues there. There is also an excellent wiki you might want to trawl through:

[http://wiki.lyx.org/LyX/LyX](http://wiki.lyx.org/LyX/LyX)

---

### Post by kleeman on 2006-03-10
[QUOTE=Paulus]Hi, I am keen to try out lyx as I will be writing my dissertation entirely in latex.  I'm attempting to install the debs you kindly provided on dapper, but encountered problems installing lyx-qt_1.4.0-1.lyx.org.1_i386.deb ,  it's complaining about libaiksaurus0 dependency, which is obsolete in dapper and is replaced by libaiksaurus-1.2-0c2a (which I have installed).  Any ideas on how I could sort this?

Thanks in advance :)[/QUOTE]

These debs are for breezy not dapper unfortunately. I will investigate a dapper version a bit down the track when the beta comes out....

---

### Post by Brunellus on 2006-03-10
[QUOTE=kleeman]I doubt it very much that this will be in dapper as we have passed the upstream freeze deadline. I know that 1.3.7 is there now.

Sorry I didn't mean to imply this was only for scientists (my words were scientist/latex bling lovers). If you check the lyx-list you will see that many humanities folks use it and discuss their issues there. There is also an excellent wiki you might want to trawl through:

[http://wiki.lyx.org/LyX/LyX](http://wiki.lyx.org/LyX/LyX)[/QUOTE]
I've been trawling through the wiki.  

As I said, I've been SUPER impressed with LyX...it's just sad that the program is not more widely used by non-scientists.  It's a killer with mathematics, of course, but the beautiful typesetting is what gets me.  

There aren't a lot of lawyers using LyX, f'rinstance, and from what I know (I work in a law firm) they really should.

---

### Post by akvik on 2006-03-15
Hi,

I use Dapper, and managed to install lyx 1.4 through the debian packages available through 
[ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/debian-unstable](ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/debian-unstable)
I guess it's unstable, but at least you get to install 1.4 in dapper!

:-)

akvik

---

### Post by JeP! on 2006-03-17
Hello,

I managed to install Lyx 1.4.0 from these files: [ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/ubuntu](ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/ubuntu) . After that I upgraded to Dapper, and Lyx is still working correctly. 

I am missing style templates, thought, such as APA-style etc... And they were already missing in Breezy. Any ideas how to get them? Or is this rather a Lyx-bug?

---

### Post by magnusbb on 2006-03-17
Thank you very much kleeman, I really appreciate your work.

But one problem I have with both this version and the standard Breezy version is encountering error messages when I try some of the templates in "/usr/share/lyx/templates". For example, I get, "The document was missing a TeX class (latex8). Lyx will not be able to produce output". 

Has somebody got a clue?

---

### Post by kleeman on 2006-03-17
[QUOTE=magnusbb]Thank you very much kleeman, I really appreciate your work.

But one problem I have with both this version and the standard Breezy version is encountering error messages when I try some of the templates in "/usr/share/lyx/templates". For example, I get, "The document was missing a TeX class (latex8). Lyx will not be able to produce output". 

Has somebody got a clue?[/QUOTE]
No probem.

The issue you have sounds like a latex rather than lyx issue. A certain latex class is missing. Make sure you have all the tetex packages installed (use synaptic to search for them). If that doesn't help you could try manually installing them using ctan but you need to read up on this. Another possibility
 is to install Texlive which is more complete than tetex as a latex distro:

[http://www.ubuntuforums.org/showthread.php?t=131507](http://www.ubuntuforums.org/showthread.php?t=131507)

---

### Post by kleeman on 2006-04-13
There are now 1.4.1 debs for breezy available from

[ftp://ftp.lyx.org/pub/lyx/bin/1.4.1/ubuntu](ftp://ftp.lyx.org/pub/lyx/bin/1.4.1/ubuntu)

Note: the initial README had an error the lyx-common deb should read:

lyx-common_1.4.1-1.lyx.org.1_i386.deb

1.4.1 has a series of bugfixes.

---

### Post by Stormy Eyes on 2006-04-13
[QUOTE=Brunellus]As I said, I've been SUPER impressed with LyX...it's just sad that the program is not more widely used by non-scientists.  It's a killer with mathematics, of course, but the beautiful typesetting is what gets me.[/QUOTE]

I used to use LyX for letter-writing, but I dumped it when OpenOffice.org became usable, because I never could figure out how to make LyX (or LaTeX for that matter) give me the monospaced typewriter-style output I need when submitting printed fiction for publication. Also, publishers tend to insist on either RTF or Word format when accepting electronic submissions.

Then again, I get rejected all the time anyway, so I suppose I could go back to using LyX. Does it still use Qt, or have they provided a GTK interface?

---

### Post by Gustav on 2006-04-13
Just installed it, looks beautiful :)

(I needed to install libglademm-2.4-1c2 to get lyx-gtk to install though)

The README said that I needed to install all files (gtk, qt and xforms) why is that?

---

### Post by Brunellus on 2006-04-13
[QUOTE=Stormy Eyes]I used to use LyX for letter-writing, but I dumped it when OpenOffice.org became usable, because I never could figure out how to make LyX (or LaTeX for that matter) give me the monospaced typewriter-style output I need when submitting printed fiction for publication. Also, publishers tend to insist on either RTF or Word format when accepting electronic submissions.

Then again, I get rejected all the time anyway, so I suppose I could go back to using LyX. Does it still use Qt, or have they provided a GTK interface?[/QUOTE]
the new versions have gtk support, and don't look half bad.  

I'd be keen on using LyX for longer things, like legal briefs.  LyX/BibTeX would rock for tables of contents/tables of authorities, if I could only learn to use them better.

---

### Post by Stormy Eyes on 2006-04-13
[QUOTE=Brunellus]the new versions have gtk support, and don't look half bad. [/qUOTE]

I'll have to compile it, then; the breezy packages won't install on Dapper because of the dependencies.

---

### Post by kleeman on 2006-04-13
If you want to compile it yourself on Dapper look here:

[http://wiki.lyx.org/LyX/LyXOnDebian](http://wiki.lyx.org/LyX/LyXOnDebian)

I agree the gtk frontend is nice and actually a bit snappier than the old qt interface . Be warned that it may be more unstable as it is under very heavy development at present.

Stormy: The mailing list (find it through the wiki) is very helpful and authors types as opposed to science types (like me) hang out there and give advice. A nice community from my experience.

---

### Post by akvik on 2006-04-17
Does anyone have lyx 1.4.1 debs for Dapper available for download? Would be great, the instruction for compiling is probably ok, but I think I developed an allergy towards compiling big apps when using Gentoo ;-) (no offense though, Gentoo is great as well)

---

### Post by kleeman on 2006-04-18
I'll compile them when the beta comes out later this week.

---

### Post by magnusbb on 2006-04-18
Thanks again for your great packaging work, kleeman! Works magnificantly this time also.

---

### Post by akvik on 2006-04-18
thanks for making packages for Dapper, I really appreciate it!

:-)

---

### Post by nickle on 2006-04-18
How does lyx compare to kile?

---

### Post by akvik on 2006-04-18
they almost doesn't lyx is like a layer on top of tex, while kile is working from the "inside" of tex. If you are not familiar with tex, then Lyx is your thing, and the other way around. 

To my opinion, Lyx is the best word processor for papers, CVs, thesises, letters and such, while OpenOffice is great for semi-layouted documents, where you want certain objects to be at a certain place. Lyx figures all this out for you, and all you have to worry about is getting the text in there! :-)

---

### Post by dakhan on 2006-04-22
Hi All!

As new version of LyX appeared I have finally decided that it's time to start moving my work environment from W2K to Kubuntu. Even greater incentive was the fact that under Windows both LyX 1.4.0 and LyX 1.4.1 neglected my Polish localization and show me menus and dialogs in English.

However also Linux version isn't free from localization problems... ](*,) 
In Breezy (on my laptop) at least qt works fine. But my desktop was upgraded to Dapper and now all platforms of LyX 1.4.1 (gtk, qt and xforms) started from console state that "Locale pl_PL could not be set". Nevertheless most of menus are in Polish, but instead of Polish diacritical marks there are some very strange symbols: first uppercase A with double dots above it and (in qt and xforms) empty box or (in gtk) square with matrix of some numbers.
Additionally in gtk it isn't possible to change coding of screen fonts, so Polish marks are ruined also in my text. In xforms it is possible to change the coding system in settings, and in qt it isn't necessary.

I suspect that most of the problems are in fact that Kubuntu is now altogether Unicode coded and LyX stays with ISO coding pages (latin2 in my case).
It also can be seen that in Breezy gtk and xforms are using ISO-8859-1 coding system for menus while in Dapper the replacements for Polish marks are different.

Is it possible to modify coding systems so that at least one platform would be working correctly?

Best regards,
Andrzej Tomaszewski

***EDIT***
Well I managed to get qt displaying Polish menus correctly by inputing line:
pl_PL ISO-8859-2

in file:
/var/lib/locales/supported.d/pl

Xforms shows no change in it's behaviour (apart from that it not shows warning about locale pl_PL when start from console) and gtk has stopped working altogather, but I have what I need - one version of LyX works as I want it!!! :)

---

### Post by jakes on 2006-04-23
Hi guys,
I've just installed LyX 1.4.1 from the debs (thanks, kleeman!), and i really like it. Now I'm trying to get it to work with Pybliographer, but I'm having a few problems. Since this area of the forum isn't really for support, I won't detail it here, but I've added my issue to an older thread I found, where someone else was having similar problems:
[http://www.ubuntuforums.org/showthread.php?p=948738#post948738]("http://www.ubuntuforums.org/showthread.php?p=948738#post948738")
So, if anybody who has the LyX/Pybliographer combo working could perhaps have a look at my issue, that would be great. I'm really looking forward to getting this working properly.
cheers,
jakes.

---

### Post by akvik on 2006-04-24
For help on Lyx, I advise you to check out the mailing list at MARC archives:

[http://marc.theaimsgroup.com/?l=lyx-users&w=2](http://marc.theaimsgroup.com/?l=lyx-users&w=2)

It is a really good forums, where you can get help on any topic related to Lyx.

:-)

---

### Post by akvik on 2006-04-24
BTW, I'm using Jabref to handle my references in Lyx, and I think it works really nice. 

[http://jabref.sourceforge.net/](http://jabref.sourceforge.net/)

I managed (as the only program I could find) to import my old Endnote references in Jabref.

---

### Post by kleeman on 2006-04-24
For those interested there are now 1.4.1 packages apparently for Dapper and installable from an apt repository. See here:

[http://wiki.lyx.org/LyX/LyXOnDebian](http://wiki.lyx.org/LyX/LyXOnDebian)

---

### Post by akvik on 2006-04-24
Hi,

I've tried the packages with an updated dapper:

1. the ones from the sid repository:
```

akvik@stua:~$ apt-get install lyx-qt
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
akvik@stua:~$ sudo apt-get install lyx-qt
Reading package lists... Done
Building dependency tree... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  lyx-qt: Depends: lyx-common (= 1.4.1-1.lyx.org.1) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
          Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be installed
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).

```

and from the other packages mentioned on the site:

```

akvik@stua:~$ sudo dpkg -i Desktop/lyx-qt_1.4.1-0.mc.1_i386.deb
Selecting previously deselected package lyx-qt.
(Reading database ... 130313 files and directories currently installed.)
Unpacking lyx-qt (from .../lyx-qt_1.4.1-0.mc.1_i386.deb) ...
dpkg: dependency problems prevent configuration of lyx-qt:
 lyx-qt depends on lyx-common (= 1.4.1-0.mc.1); however:
  Package lyx-common is not installed.
 lyx-qt depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu17.
 lyx-qt depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 lyx-qt depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing lyx-qt (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lyx-qt

```

I really hoped this would work... but it didn't. Anyone else had any luck?

:-)

---

### Post by Ziggurat on 2006-04-25
Hi, i am compiling lyx 1.4.1 on updated dapper system but have no place to upload the deb's. Is there any wiki or any place where i can put this??

Thanks.

---

### Post by kleeman on 2006-04-25
I use this:

[http://www.yourfilelink.com/](http://www.yourfilelink.com/)

---

### Post by akvik on 2006-04-27
any Dapper packages out there yet?

---

### Post by kleeman on 2006-04-27
I compiled them on dapper beta. Pick them up here:

[http://www.math.nyu.edu/faculty/kleeman/dapper/](http://www.math.nyu.edu/faculty/kleeman/dapper/)

---

### Post by akvik on 2006-04-28
Thanks kleeman!

It works - had to remove some ispell packages and such, but it works! Beautiful!

---

### Post by Ziggurat on 2006-04-28
Hi, just in case i compiled lyx 1.4.1. All frontends, updated Dapper, files are here:

[http://www.fileden.com/files/7402/lyx_1.4.1-1.lyx.org.1_all.deb](http://www.fileden.com/files/7402/lyx_1.4.1-1.lyx.org.1_all.deb)
[http://www.fileden.com/files/7402/lyx-common_1.4.1-1.lyx.org.1_i386.deb](http://www.fileden.com/files/7402/lyx-common_1.4.1-1.lyx.org.1_i386.deb)
[http://www.fileden.com/files/7402/lyx-gtk_1.4.1-1.lyx.org.1_i386.deb](http://www.fileden.com/files/7402/lyx-gtk_1.4.1-1.lyx.org.1_i386.deb)
[http://www.fileden.com/files/7402/lyx-qt_1.4.1-1.lyx.org.1_i386.deb](http://www.fileden.com/files/7402/lyx-qt_1.4.1-1.lyx.org.1_i386.deb)
[http://www.fileden.com/files/7402/lyx-xforms_1.4.1-1.lyx.org.1_i386.deb](http://www.fileden.com/files/7402/lyx-xforms_1.4.1-1.lyx.org.1_i386.deb)


I just have a problem with special characters on the GUI (like á, etc...). When i figure out how to solve it i compile again.

---

