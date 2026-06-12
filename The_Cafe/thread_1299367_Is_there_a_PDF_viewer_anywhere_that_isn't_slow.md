---
title: "Is there a PDF viewer anywhere that isn't slow?"
date: 2009-10-23
forum: The Cafe
---

### Post by rob86 on 2009-10-23
The PDF Viewer that comes with Ubuntu is very slow to use. I tried ePDFview which was decent, but lacking some features that don't look to be added anytime soon. It was a bit buggy as well, when I scroll down a page, then scroll back up, the previous page is a blank white page. Odd. 

I tried xPDF which wasn't bad either, and I almost stuck with it, but it had one huge problem, the font rendering was impossible to read at smaller zoom levels. Full screen was okay, but sometimes I have to unmaximize it and still be able to read it.  I tried different command line things like turning AA on and off, and it just made things worse. 

Is there any PDF viewer out there that works good and is light on resources? I hate it when PDF viewers take a noticeable amount of time to render a page.  ePDF and XPDF did a pretty good job in the speed department, too bad about the other issues. I hope they aren't my only light-weight options.

I'd even settle with XPDF if someone could tell me how to make the font readable at smaller zoom levels. You think there'd be some way to make it look like every other pdf veiwer I tried, but I coudn't figure it out.

---

### Post by fdrake on 2009-10-23
PDF Viewer SLOW?! I mean compared to adobe reader on my machine it takeas 1/2 or 1/3 of the time that the adobe requires. Don't forget also that it depends on your machine(RAM you have). What about thinking to try Google-documents to store and read the pdf files on the browser. Let google's servers handling the process.

---

### Post by jrusso2 on 2009-10-23
The best one I found is foxit pdf reader for Linux.

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

### Post by oldsoundguy on 2009-10-23
I use PDF Download in FireFox.  Loads in an instant.  And it does MORE than just read the things!!  Read up on it in the add-ons for FireFox.

---

### Post by RichardLinx on 2009-10-23
Okular.

---

### Post by rob86 on 2009-10-23
I find "PDF Viewer" if that's what it called slow. It's not as slow as Adobe, but there are faster alternatives. It might not be noticeable on a computer with lots of RAM but on mine it sure is. On xPDF I can scroll continuously and not notice a bit of lag between page changes. On PDF Viewer it takes maybe 0.5 to 1 second to load which doesn't seem like a lot but it's distracting.

I wasn't aware Foxit was available on linux. I used it on windows. I'll give it a try. I see xPDF is still under active development, maybe I'll see if the author can help with the poor font rendering issue. It was pretty good.

---

### Post by Firestem4 on 2009-10-23
> **RichardLinx said:**
> Okular.

Seconded,

One thing I like about Okular is it allows you to control its memory management by telling it to aggressively use it or not. It has a fast backend and can also load multiple file formats (eg: .doc)

---

### Post by Sealbhach on 2009-10-23
> **Firestem4 said:**
> Seconded,

One thing I like about Okular is it allows you to control its memory management by telling it to aggressively use it or not. It has a fast backend and can also load multiple file formats (eg: .doc)

It only works in KDE though?

.

---

### Post by SomeGuyDude on 2009-10-23
I've been using evince for a while with no issues.

---

### Post by RichardLinx on 2009-10-23
> **Sealbhach said:**
> It only works in KDE though?

.
No, it works fine under GNOME too. I'm using it in Ubuntu right now.
Pretty sure it's in the repo's too:
```
sudo apt-get install okular
```

---

### Post by SunnyRabbiera on 2009-10-23
> **Sealbhach said:**
> It only works in KDE though?

.

No it will work fine, it will just look a little out of place.

---

### Post by NFblaze on 2009-10-23
If I'm not mistaken the default PDF Viewer in gnome (Evince) has been trimmed and greatly improved in 9.10. Try the packages from that distro repository and see if you gain anything.

---

### Post by Sealbhach on 2009-10-23
> **RichardLinx said:**
> No, it works fine under GNOME too. I'm using it in Ubuntu right now.
Pretty sure it's in the repo's too:
```
sudo apt-get install okular
```

True, but it's got a truckload of KDE dependencies:


```
sudo apt-get -s install okular
[sudo] password for sealbhach: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:

  exiv2 kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data khelpcenter4 libclucene0ldbl libepub0 libexiv2-5
  libknotificationitem1 liblzma0 libokularcore1 libplasma3 libpoppler-qt4-3
  libqca2 libqimageblitz4 libqt4-qt3support libsoprano4 libstreamanalyzer0
  libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-misc-plugins libxine1-x libzip1
  phonon-backend-xine soprano-daemon

Suggested packages:
  kdebase djvulibre-bin libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-ossl libqca2-plugin-pkcs11 gxine xine-ui libxine1-doc
  libxine-doc libxine1-ffmpeg okular-extra-backends texlive-base-bin


```I don't like having loads of these libraries hanging around, it's just more stuff to update.

.

---

### Post by HappyFeet on 2009-10-23
The default pdf viewer works fast for me. Then again, with a quad core cpu and 6gb ram, *everything* is fast. Get a better computer.

---

### Post by Firestem4 on 2009-10-23
> **Sealbhach said:**
> True, but it's got a truckload of KDE dependencies:
[/code]I don't like having loads of these libraries hanging around, it's just more stuff to update.

.

Lol, I hear you...Thats the reason i never downloaded Firefoxfrom the Repo's because of all of the Gnome dep's. I don't have a problem with gnome, it's just I hardly use any Gnome-specific programs. 

(not to mention Firefox in the repo is outdated)

---

### Post by wilee-nilee on 2009-10-23
> **RichardLinx said:**
> No, it works fine under GNOME too. I'm using it in Ubuntu right now.
Pretty sure it's in the repo's too:
```
sudo apt-get install okular
```

 Did you notice the huge amount of kde stuff that came with the install.

---

### Post by RichardLinx on 2009-10-24
> **wilee-nilee said:**
> Did you notice the huge amount of kde stuff that came with the install.

I have a large amount of KDE applications installed on my GNOME installation so I already have most the dependencies. I don't think it's such a big deal anyway. In the end you're getting a better program.

---

### Post by koleoptero on 2009-10-24
Okular and k3b are two major reasons that I'm going to switch to kubuntu next week. But evince has had no speed issues on my laptop (which isn't powerful at all).

---

### Post by wilee-nilee on 2009-10-24
> **RichardLinx said:**
> I have a large amount of KDE applications installed on my GNOME installation so I already have most the dependencies. I don't think it's such a big deal anyway. In the end you're getting a better program.

 I would agree, personally I don't like KDE so as soon as I saw the added stuff I would never use I hit the n on a terminal install. There is a OS for everybody I like mine fairly straight forward I don't need the visual bling.

---

### Post by speedwell68 on 2009-10-24
eVince works just fine.  It does everything it says on the tin.:D

---

### Post by Jesus_Valdez on 2009-10-24
evince slow? 

Really?

Do you have a steam-powered pc?

---

### Post by amitabhishek on 2009-10-24
> **jrusso2 said:**
> the best one i found is foxit pdf reader for linux.

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

+1

---

### Post by Xbehave on 2009-10-24
> **wilee-nilee said:**
> I would agree, personally I don't like KDE so as soon as I saw the added stuff I would never use I hit the n on a terminal install. There is a OS for everybody I like mine fairly straight forward I don't need the visual bling.
Lets have a look at your irational fear by seeeing which are KDE dependancies:
[LIST]
[*]kde-icons-oxygen (a program needs icons :O)
[*]kdebase-runtime / kdebase-runtime-bin-kde4 / kdebase-runtime-data / kdebase-runtime-data-common / kdelibs-bin / kdelibs5 / kdelibs5-data / libknotificationitem1 / libplasma3.
[INDENT]packages that add kde calls so okular can work, no overhead when they are not running and only a slight amount of memory usage when they are. Sure it seams like a lot but the total filesize will be minimal, the large number is due to the modularity of kde (gnome is just as good, install a gnome app on a kde desktop and you pull a lot of gnome deps that add up to a couple of MB). Do you remove all libs of apps you don't use on a clean install or just those that have a k in them? The bottom line is none of these are even programs[/INDENT]
[*]khelpcenter4 (ZOMG a prgram needs a help viewer)
[*]libqt4-qt3support (packaging mistake)
[*]phonon-backend-xine (ability to pipe music though xine, no overhead)
[/LIST]

---

### Post by nikhilbhardwaj on 2010-03-04
> **Firestem4 said:**
> Seconded,

One thing I like about Okular is it allows you to control its memory management by telling it to aggressively use it or not. It has a fast backend and can also load multiple file formats (eg: .doc)
i'm going to have to disagree
okular is very very slow
atleast for me.
when you move from one page to the next theres a considerable lag
and that too , when there's only text when it comes to images it becomes woeful

---

### Post by nikhilbhardwaj on 2010-03-04
> **Jesus_Valdez said:**
> evince slow? 

Really?

Do you have a steam-powered pc?

probably
i've pentium 4 1.5ghz
1 gb ram
ans 256 mb graphics

its not much
but it should be able to render pdfs 
didnt know that was so resource intensive

come to think of it
are postscript files easier on the system resources in comparison to pdf ??

---

### Post by V for Vincent on 2010-03-04
The free-as-in-beer personal version of PDF Xchange viewer (through wine but it works great) is awesome. It's lightning fast for viewing and for search, plus it offers some really useful markup features for any document, even those that can't normally be edited. Overall, I'd say it's the best reader I've found so far.

---

### Post by audiomick on 2010-03-04
> **nikhilbhardwaj said:**
> probably
i've pentium 4 1.5ghz
1 gb ram
ans 256 mb graphics

its not much
[COLOR=Red]but it should be able to render pdfs 
didnt know that was so resource intensive[/COLOR]

come to think of it
are postscript files easier on the system resources in comparison to pdf ??
It surprised me too, but in fact PDF files are quite RAM intensive, apparently. I regularly have to look at large plans that were exported as PDFs from Autocad. They often have layers and whatnot in them. On this desktop, dual core @3.3GHz with 4GB RAM, evince and acroread both run ok, but you can tell that the computer is busy shovelling. The Vista laptop, dual core @2.4GHz, I think and 4GB RAM, is similar. My last laptop, a 1.6 Centrino with 2GB RAM had a lot more trouble dealing with those sort of files. I had upgraded that computer from 512GB RAM, and one of the most noticable changes was how it dealt with those monster PDF files.

---

### Post by urukrama on 2010-03-04
I just tried Foxit on Linux, and I'm impressed with its speed.

---

### Post by Ibidem on 2010-03-21
Xpdf (though it is odd, a bit dated in the UI, and maybe limited) is the fastest and lightest I've seen.
PdfEdit is second for lowest ram (really), but it was designed as a form-filler (+a little more) and very odd and clunky
ePdfView is third of the ones I tried, 1.5 mb more ram (resident size) than xpdf
Evince is a little bloated, with another mb used
Approx ram (resident memory size, 1.3 MB whitepaper from ESRI used to test):
xpdf                          2900kb
pdfedit                      4000kb
epdfview                   4500kb
evince                      5500kb
All started quite quickly; pdfedit wanted password (edit-protected pdf).
Not checked:
Wine+pdf Xchange (good, fast, Windows but works very well w/ Wine)
Foxit  (Windows version is better than Acrobat, but not comparable to PDF Xchange)
Acrobat
Okular, GIMP (yes it does open pdfs, but it's a kludge), others

Aspire One, AOA150--Atom N270 (1.6 GHz, dual core); 1 GB ram; i945 integrated graphics
(1 core better than the OP)
Ibidem

---

### Post by ronshani on 2010-03-26
"Anywhere PDF Viewer" - [http://secnote.com/pdf](http://secnote.com/pdf)  - is the new way to view PDFs online - just because you need to install NOTHING!!!

It allows you to view, zoom, print - any online PDF - just by changing link path - for the publisher - and NOTHING is required from user viewer side!!!

Try the demonstration  - with any online PDF you like - and see it for yourself.

"Anywhere PDF Viewer" - [http://secnote.com/pdf](http://secnote.com/pdf)

This is THE solution for any operating system - any browser - any site - any development language - just upgrade current PDF link to "Anywhere PDF Viewer" links - in no-time***

Engoy (and start using...).

---

