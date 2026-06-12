---
title: "E-book readers for Ubuntu?"
date: 2005-05-19
forum: The Cafe
---

### Post by Arto on 2005-05-19
Just wondering what y'all are using for reading ebooks?

Obviously Microsoft Reader files (.lit) are out of the question (right?), PDFs can be read with Evince (though it doesn't have the most friendly hotkeys for reading) or Adobe Acrobat, but is there any general-purpose ebook application included in the repositories that would handle text & HTML files such as can be obtained from, for example, [Project Gutenberg](http://www.gutenberg.org/)?

---

### Post by Burgundavia on 2005-05-19
If you email a lit file to the evince developers, they may be able to make evince work with it.

Corey

---

### Post by jonrkc on 2005-05-20
[QUOTE=Arto]Just wondering what y'all are using for reading ebooks?

Obviously Microsoft Reader files (.lit) are out of the question (right?), PDFs can be read with Evince (though it doesn't have the most friendly hotkeys for reading) or Adobe Acrobat, but is there any general-purpose ebook application included in the repositories that would handle text & HTML files such as can be obtained from, for example, [Project Gutenberg](http://www.gutenberg.org/)?[/QUOTE]
 I generally read e-books (mostly from Project Gutenberg) on my Palm Tungsten E, and before that on my IIIxe and IIIx.  When I do read something of that nature on my desktop computer, I just use OpenOffice.org and open the .txt file that way.  It's legible and you can pick the font that works best for you, etc.  I really don't see the need for specialized e-book software for desktop use, for myself, but of course if it resulted in nicer formatting that would be a good reason.

---

### Post by eeried on 2005-11-27
Well, an app may not be necessary but I really miss Tom's e-text Reader that worked under Windows : [http://pws.prserv.net/Fellner/Software/eTR.htm](http://pws.prserv.net/Fellner/Software/eTR.htm)
this reader gives you the look and feel of a book, you can add a TOC, and of course change the color of the background and the font and colour of the text, and edit the text. It reads all kinds of files, and even zip files -- so you don't have ti unzip your zipped e-book before reading it. Great app!

I can install Wine I suppose or beg "Tom" to make a Linux version...

---

### Post by erikpiper on 2005-11-27
That is cool! Cmon some developer, please?

---

### Post by mtalexan on 2006-07-17
I didn't take the time to really test it out thoroughly, but it looks like you can use "Tom's" program with wine.  To do so just run the command:
./wine eTextReader.exe "nameofbook.file"
where "nameofbook.file" is the full file name of the book.  It seems to automatically open the file.  If you have problems, make sure you're running the command in the same directory as the program, make sure it's a supported format, amd make sure the book is in the same directory as the program.  The program doesn't handle the file format I was looking for, so you'll have to do any further testing on your own.

---

### Post by eeried on 2006-07-18
Many thanks for your wine suggestion, mtalexan. I thought of that and tried it once under Libranet, and it worked (I still had windows98 as dual-boot).

Now I only have Linux and I didn't like the idea of installing wine -- too much of a hassle. But you're right I should try.

However I wrote to Tom the author who replied he was thinking of making a better version for Linux, not simply a port, so let's keep our fingers crossed. ;)

---

### Post by &#1050;&#1085;&#1077;&#1083;&#1077; on 2007-12-20
Greetings,

Possible solution for files with .lit extension can be OpenBerg Lector extension for Firefox web browser. Here is a short quide:[HOWTO: Open files with .lit extension in Firefox]("http://ubuntuforums.org/showthread.php?t=633429")
Best regards,
Knele

---

### Post by sanderella on 2007-12-20
This is a good thread.

I have had a Rocket ebook since they first came out in 1998. It still runs well, I use it every day. But I have to be careful how much I put on it, since it only has 8mb memory.

For a whole bookshelf full of books I bought an eBookwise with a 64 mb memory card.I have 16 books on it, and it's not half full.

My grumble is that I can't download files through Ubuntu and put them on my ebook readers, they're all locked into MS. The files I can download on Windows are rb, text, html, rtf and msword.

I would just LOVE someone to make libraries for these devices. Any helpful comments from anyone?:???:

---

### Post by mreierson on 2007-12-20
I just got an eBookWise device as well and it's great.  I made a program to download books in Linux.  It still requires a content server as it just provides the network connection.  You can convert books on the FictionWise website or run the GEBLibrarian under Wine.  It's on sourceforge at [http://www.sf.net/projects/eb1150](http://www.sf.net/projects/eb1150).

---

### Post by BobCFC on 2007-12-20
I started using [FBReader]("http://www.fbreader.org/desktop/debian.php").   

I like it because is it automatically remembers the position that you we reading when you leave.  So you can flick between books in your library and it jumps back to where you left it.


It was written for fedora but the homepage has deb files.   There are two libs that need to be installed as well, also in debs.  

They are in i386 but work fine in 64bit if you use the --force-architecture flag in *dpkg*.



Regarding .lit files there is a program to convert them to HTML. You can find [instructions here]("http://www.kyzer.me.uk/pack/convlit/") which I found more useful than the actual homepage.

Unfortunately the author called convert-lit by it's rude acronym that's why you never find it in the repos :(


basic usgage:

```
clit  book.lit   bookdir/
```


The trailing slash is important to create a new directory for the exploded contents of the ebook( cover.jpg etc)


As is the program will only extract one book at a time.  I downloaded a torrent the other day with 100 .lit files and I'll be damned if I'll do it that way so I wrote a small bash script  to automate the process:


```

#!/bin/bash
#============================================================================
# process every .lit file in the current directory 
# use clit to explode each file into directory of same name minus .lit extention
# (optional pass -z argument to create bzip2 files and remove new directories)
# 2007 RBH
#============================================================================


if [ $1 == '-z' ]
then
	for FILENAME in *.lit
	do
		clit "$FILENAME" "${FILENAME%%.lit}"/
		tar cjf "${FILENAME%%.lit}".tar.bz2 "${FILENAME%%.lit}"
                rm -rf "${FILENAME%%.lit}"
	done
else
	for FILENAME in *.lit
	do
		clit "$FILENAME" "${FILENAME%%.lit}"/
	done
fi

```


Save it as a text file and make it executable with chmod +x filename or rightclick and choose properties->permissions.

This script will extract all the .lit files in the current dir into folders of the same name.   Use the -z flag to create .bz2 files instead.

Use at own risk... this is my first proper bash script lol... I'm a C++ guy.

---

### Post by eeried on 2007-12-21
Many thanks for the news BobCFC. here's what the page you linked to has to say:

> FBReader is now included in the main debian testing/unstable repository, thanks to Joey Hess. Just run ‘apt-get install fbreader’ and enjoy.
For Debian 4.0 (Etch) and Ubuntu 7.04 users.
There are 2 ways to install FBReader on your computer: installation from our repository (recommended for almost all users) and manual installation.

    * Installation from the repository:
          o add the following lines to your /etc/apt/sources.list:
            deb [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) etch main 

I'm wondering if we can use the same DEB file for Gutsy?

This E-book reader looks good, and I wouldn't have to install wine just to run Tom's E-Text reader which is only for windows.

---

### Post by CbrPad on 2007-12-21
I've just installed the debs at the bottom of that page and it works great (I'm on Gutsy).

---

### Post by koleoptero on 2007-12-21
Can you post a screenshot of FBReader? There is no linux screenshot in their site.

---

### Post by CbrPad on 2007-12-21
Sorry, I've been trying to upload but I'm on hsdpa and it's impossible.  However it's pretty much as the screenshots on the web.  I've barely used it yet but I can see there's lots of ways in which it can be improved.

---

### Post by bruce89 on 2007-12-21
FBReader was too new to get into Gutsy, as it was [added to Debian in June]("http://packages.qa.debian.org/f/fbreader.html"). If you wanted, I could backport the package to Gutsy for my PPA.

**EDIT:** Just uploaded, will be built pretty soon.

---

### Post by BobCFC on 2007-12-22
Sorry I wasn't clear.. I stopped using Red Hat before Fedora was invented lol  

Yes I meant it works in 64bit gutsy with *--force-architecture* flag in dpkg

This is a way to install i386 deb files on 64bit.


It's not much to look at for screenshots.. Just a row of Icons at the top and one big page like a web page.

The cool thing is it remembers your position automatically as you go from book to book, no need for bookmarks or saving etc..  

It has a library manager and you can just add bz2 or gz files to it then organise by author etc.  Only used for a few days myself.


EDIT:  if anybody knows of a command line ebook reader that automatically remembers your position please say..   I thought about patching less to jump to a line with a flag lol.

---

### Post by john wagner on 2007-12-31
For .lit to html file conversions (MSReader to something my Dapper can open and read...) I downloaded and installed convert lit (clit18 ) from[ **here**]("http://www.convertlit.com/").  I simply installed it to my wine  directory, so when I have to read/convert one of my numerous MSReader books, I open wine (using the GUI), open the convert lit option.  Then navigate to where the book is, select it and convert it.  Takes, eh, maybe 5 seconds.  Creates a file wherever you want it, opens everything too.  Any cover images, internal artwork, everything.  Looks real professional too!  Then I close the GUI and open my book to read.

john

---

### Post by john wagner on 2007-12-31
I've tried to get FBReader to work for me (Dapper), but it won't cooperate.  I keep getting dependencies issues...even after I downloaded (and verified) the required libraries for the Dep/Ubuntu version.  Any help from youse guys would be great!
thanks
john

---

### Post by BobCFC on 2007-12-31
> **john wagner said:**
> For .lit to html file conversions (MSReader to something my Dapper can open and read...) I downloaded and installed convert lit (clit18 ) from[ **here**]("http://www.convertlit.com/").  I simply installed it to my wine  directory, so when I have to read/convert one of my numerous MSReader books, I open wine (using the GUI), open the convert lit option.  Then navigate to where the book is, select it and convert it.  Takes, eh, maybe 5 seconds.  Creates a file wherever you want it, opens everything too.  Any cover images, internal artwork, everything.  Looks real professional too!  Then I close the GUI and open my book to read.

john


It's the same program.

---

### Post by BobCFC on 2007-12-31
> **john wagner said:**
> I've tried to get FBReader to work for me (Dapper), but it won't cooperate.  I keep getting dependencies issues...even after I downloaded (and verified) the required libraries for the Dep/Ubuntu version.  Any help from youse guys would be great!
thanks
john


If I get these problems sometimes I chase the dependencies up the tree.  this needs this.. this needs this.. it does work if you google the libraries you can often download them from Debian unstable as .deb files.  But this could conflict in the future when Ubuntu updates

Another idea is to compile your own from source against your current libraries.  I have not tried it because I am not running dapper sorry... here is a link to the source code.. 

[http://www.fbreader.org/fbreader-sources-0.8.9.tgz](http://www.fbreader.org/fbreader-sources-0.8.9.tgz)

Good luck.

EDIT:  oops wrong source lol... You wanted FBreader not c-lit doh

---

### Post by john wagner on 2008-01-01
> **BobCFC said:**
> 
------------
It's the same program.

------------

If I get these problems sometimes I chase the dependencies up the tree.  this needs this.. this needs this.. it does work if you google the libraries you can often download them from Debian unstable as .deb files.  But this could conflict in the future when Ubuntu updates

Another idea is to compile your own from source against your current libraries.  I have not tried it because I am not running dapper sorry... here is a link to the source code.. 

[http://www.fbreader.org/fbreader-sources-0.8.9.tgz](http://www.fbreader.org/fbreader-sources-0.8.9.tgz)

Good luck.

EDIT:  oops wrong source lol... You wanted FBreader not c-lit doh

-------



Really?  Clit and FBReader are the same program?  Cool, did not know that.  I won't waste any more time trying to get FBR to work when I finally got clit doing so well!  
What I really need is something to read mobi-books on my Dapper with!  I've tried downloading the software from the mobi site and running it on Wine, but no go.  So any suggestions would be great!

john

---

### Post by BobCFC on 2008-01-02
> **john wagner said:**
> -------
Really?  Clit and FBReader are the same program?  



No.  I meant that the linux program in my earlier post is the same as the windows program from convertlit.com that you use in WINE.

FBR is just a reader/manger which remembers where you were on the page automatically.  If you viewed the HTML in a browser you will loose your place.  FBR reads many types but not .lit  The website says it supports non DRM'd mobipocket books natively

> Main features:

    * Supported formats are
          o fb2 e-book format (style attributes are not supported yet).
          o HTML format (tables are not supported).
          o CHM format (tables are not supported).
          o plucker format (tables are not supported).
          o Palmdoc (aportis doc).
          o zTxt (Weasel format).
          o TCR (psion text) format.
          o RTF format (stylesheets and tables are not supported).
          o OEB format (css and tables are not supported).
          o OpenReader format (css and tables are not supported).
          o Non-DRM'ed mobipocket format (tables are not supported).
          o Plain text format.
    * Direct reading from tar, zip, gzip and bzip2 archives. (Multiple books in one archive are supported.)
    * Automatic library building.
    * Automatic language and character encoding detection is supported.
    * Automatically generated contents table.
    * Embedded images support.
    * Footnotes/hyperlinks support.
    * Position indicator.
    * Keeps the last open book and the last read positions for all opened books between runs.
    * List of last opened books.
    * Automatic hyphenations. Liang's algorithm is used. The same algorithm is used in TeX, and TeX hyphenation patterns are used in FBReader. Patterns for Czech, English, Esperanto, Finnish, French, German, Italian, Norwegian, Portuguese, Russian, Spanish, Swedish and Ukrainian are included in the current version.
    * Text search.
    * Full-screen mode.
    * Screen rotation by 90, 180 and 270 degrees.


Did you try to compile?

---

### Post by john wagner on 2008-01-02
> **BobCFC said:**
> No.  I meant that the linux program in my earlier post is the same as the windows program from convertlit.com that you use in WINE.

FBR is just a reader/manger which remembers where you were on the page automatically.  If you viewed the HTML in a browser you will loose your place.  FBR reads many types but not .lit  The website says it supports non DRM'd mobipocket books natively



Did you try to compile?


Yeah, no luck...  Sigh.  And yeah, when I read html got no page minder features at all...  Would be nice to get FBR to work, but...  No luck so far.

john

---

### Post by cherry316316 on 2008-03-22
thanks

---

### Post by cop on 2008-05-13
hi, im a newbie with Ubuntu.
I try to read some ebooks (file .prc) and I installed FBReader already. However, when I add that book and open it, I cannot read because there are just codes instead of letters. I am confused. I checked on FBReader website and they said they do not support format .prc. Please advise me which program can read such those .prc file?
Thanks in advance

---

### Post by Ovi Dogar on 2008-06-06
Here is a free resource for creating amazing ebook covers: [http://www.absolutecovers.com/blog/2008/06/03/free-ebook-cover-action-script/](http://www.absolutecovers.com/blog/2008/06/03/free-ebook-cover-action-script/)

---

### Post by eeried on 2008-06-06
Ovi Doga, could you check your amzaing stuff is free like freedom, so has a free licence, and it's compatible with Linux and GIMP.

No use talking of M$ and Adobe stuff here, is it?

I'm looking for a Linux e-bookreader that can read books in PDF format. I know I can read PDF files with Evince or Xpdf but it would be nice to have something like Tom's e-text Reader that displays the text as an open book, and even allows you to edit it (very useful to correct misprints or improve the layout, and so generate a better TOC).

---

### Post by BobCFC on 2008-06-06
Just to update the situation, FBReader is in the Hardy Heron repositories now so much easier to install

type:
[B]
sudo apt-get install fbreader[/B]


or search for it in Add/Remove Applications or Synaptic




NOTE:  once installed it has capital letters FBReader

---

### Post by eeried on 2008-06-23
Yes FBReader is okay with Hardy but how dull it is compared to Tom's E-text Reader unless you can change the back-ground colour and the texte colour, and you can display two pages like in book... -- I don't relish wine or freeware but I think I'll have to go on with Tom's reader a little longer.

---

### Post by Mokoko on 2008-12-13
LIT TO PDF converter script beta

#!/bin/bash
#================================================= ===========================
# process every .lit file in the current directory
# uses clit to explode each file into directory of same name minus .lit extention
# and uses htmldoc to convert htm files to Acrobat Reader format (.pdf)
# then deletes the directories
# (optional pass -a argument to create bzip2 archive of pdf files and remove new directories)
# 2008 BobCFC
#================================================= ===========================


if [ "$1" == '-a' ]
then
for FILENAME in *.lit
do
clit "$FILENAME" "${FILENAME%%.lit}"/
htmldoc -t pdf13 --webpage -f "${FILENAME%%.lit}".pdf "${FILENAME%%.lit}"/*.htm
tar cjf "${FILENAME%%.lit}".tar.bz2 "${FILENAME%%.lit}".pdf
rm -rf "${FILENAME%%.lit}" "${FILENAME%%.lit}".pdf
done
else
for FILENAME in *.lit
do
clit "$FILENAME" "${FILENAME%%.lit}"/
htmldoc -t pdf13 --webpage -f "${FILENAME%%.lit}".pdf "${FILENAME%%.lit}"/*.htm
rm -rf "${FILENAME%%.lit}"
done
fi

---

### Post by BobCFC on 2008-12-13
> **Mokoko said:**
> LIT TO PDF converter script beta

#!/bin/bash
#================================================= ===========================
# process every .lit file in the current directory
# uses clit to explode each file into directory of same name minus .lit extention
# and uses htmldoc to convert htm files to Acrobat Reader format (.pdf)
# then deletes the directories
# (optional pass -a argument to create bzip2 archive of pdf files and remove new directories)
# 2008 BobCFC
#================================================= ===========================


if [ "$1" == '-a' ]
then
for FILENAME in *.lit
do
clit "$FILENAME" "${FILENAME%%.lit}"/
htmldoc -t pdf13 --webpage -f "${FILENAME%%.lit}".pdf "${FILENAME%%.lit}"/*.htm
tar cjf "${FILENAME%%.lit}".tar.bz2 "${FILENAME%%.lit}".pdf
rm -rf "${FILENAME%%.lit}" "${FILENAME%%.lit}".pdf
done
else
for FILENAME in *.lit
do
clit "$FILENAME" "${FILENAME%%.lit}"/
htmldoc -t pdf13 --webpage -f "${FILENAME%%.lit}".pdf "${FILENAME%%.lit}"/*.htm
rm -rf "${FILENAME%%.lit}"
done
fi



I am glad the new script worked for you Mokoko I have not used htmldoc before it was trial and error.

To be clear this script requires clit and htmldoc installed to run.  Clit is now in the ubuntu repos in the package named **convlit** so no need to compile anymore

You can install these programs with:

```
sudo apt-get install convlit htmldoc
```


EDIT:  also I don't know if bash has changed in the past couple of years but when I returned to the script it was complaining about the first IF statement, putting "speach marks" around the parameter solved this issue

e.g.   "$1"

---

### Post by Lundix on 2008-12-15
Hello, 

This forum seem to be split between software readers and some talk about e-book reading devices. Anyhow I choose to write in this thread. 

Does anyone have any advice/suggestions for cheap but still good value e-book reading devices if you live in [COLOR="Red"]Europe[/COLOR]. I checked out eBookWise device but that only ships in US and Canada. Else I would have bought it. I prefer if it can read PDf since I have a huge collection of those files.

Cheers

---

### Post by CbrPad on 2008-12-15
Check out [http://www.mobileread.com/forums/](http://www.mobileread.com/forums/) which is an excellent resource.  

There are plenty of devices available - Sony, Iliad, Hanlin/Bebook, Cybook and so on.  

The Iliads are probably the best bet for pdf's right now, especially if you want to annotate them or will be viewing large technical documents - however they do suffer in other areas such as short battery life and relatively high price.

I suggest post on the forums I linked to and specify your exact requirements and you should be able to get a better answer.

---

### Post by Cannaregio on 2008-12-17
Call me weird, but I quite like the lit format. I think is one of the less noisy and more eye-resting ones for reading on my laptops.

I wish to implement a lit reader for linux, without the need to convert the format at all; without the bogus activations and "shop" options and with links to the hundred of completely free repositories of *.lit format books that exist :-) 
I'm even working on that, slowly, maybe.

For the moment I have solved this whole problem simply installing microsoft reader in wine (ver. 1.0.1). 

No need for microsoft explorer, no need for activations, nothing.

When I need to consult my (huge) library I just navigate to the folder and launch a sh command there (of course you can just later copy the sh command to your Desktop and launch from there as well)

```
#!/usr/bin/env bash
# Script to run lit Reader
cd
export WINEPREFIX="/home/[COLOR="#696969"]YOUR_OWN_USERNAME[/COLOR]/.wine"
cd /media/BIGGEST750/books/literature/ebooks_lit
wine "/home/[COLOR="DimGray"]YOUR_OWN_USERNAME[/COLOR]/.wine/drive_c/Program Files/Microsoft Reader/msreader.exe"

```

Modify directories and paths for your own usage of course.

But note that the *.lit library will be [COLOR="Blue"]empty[/COLOR] at the beginning.

When I need to add a lit book I just navigate to the folder and add to the library opening first the target with [COLOR="Blue"]a specific[/COLOR] command in the terminal:

```
wine "C:\Program Files\Microsoft Reader\msreader.exe" wizod.lit
```

And hop! The Wizard of Oz is there in lit format. Added to the library.

and

```
wine "C:\Program Files\Microsoft Reader\msreader.exe" usher.lit 
```

and
```
wine "C:\Program Files\Microsoft Reader\msreader.exe" Treasure Island.lit
```

and so on.

Thattaway the library will be feeded.

DO NOT -repeat- [COLOR="Blue"]DO NOT launch[/COLOR] another copy of the reader from outside that already feeded sh script, or you'll risk loosing all your library additions.  When Microsoft Reader starts it creates a new LitPath.lpt file if one is not present or in path.

In fact the whole library collection is listed (and located) in 
```
.wine/drive_c/windows/profiles/[COLOR="#696969"]YOUR_OWN_USERNAME[/COLOR]/My Documents/My Library 
```
where you'll find  the [COLOR="Blue"]LitPath.lpt[/COLOR] listing file and also an "[COLOR="#0000ff"]Annotations[/COLOR]" folder with the [COLOR="#0000ff"].ebo[/COLOR] files (one for each [COLOR="Blue"].lit[/COLOR] ebook that has been opened and added to the library, they contain notes, drawings, and bookmarks from the various ebooks you've been reading).

It is maybe a good idea to copy the [COLOR="Blue"]LitPath.lpt[/COLOR] listing file  and the [COLOR="#0000ff"].ebo [/COLOR] files folder "*just in case*" in a secure location whenever your library grows enough.

Cheers!

---

