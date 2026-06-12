---
title: "Is there any program like Adobe Pro ?"
date: 2010-01-25
forum: Ubuntu Studio
---

### Post by mrhellboy86 on 2010-01-25
Hi all
I wanted to ask you that If any program like Adobe Professional exist for Ubuntu?
I want a software that be handy for reading and also have some good tools to write some comments, HighLight , ... for editing and marking
sorry if i did send this thread here, I am just fresh in this forum , don't know if I send thread in its own place or the place is wrong 
thanks in advance

---

### Post by lykeion on 2010-01-25
Your questions are a bit unclear... Ddo you mean Adobe Acrobat Pro? And what kind of documents do you want to read, comment, etc?

If you're talking about PDF files, here's some info:

[LIST]
[*]Saving/export as PDF can easily done in **OpenOffice**

[*]**Evince** is a good reader for PDFs (and other formats)

[*]Edit PDFs it's a bit harder. Mainly because PDF is a distribution file format not meant to be edited even though there are software capable of this. 
Maybe **inkscape** can do this? (Search around in the forums)

[*]To annotate PDFs (i.e make comments, notes, highlights, etc) - I think you can use **pdfedit** or **xournal**
but I have little experience with this, so I suggest you try for yourself.
[/LIST]

All of these mentioned applications are available with Ubuntu.

Hope this helps somewhat.

---

### Post by mrhellboy86 on 2010-01-26
> **lykeion said:**
> Your questions are a bit unclear... Ddo you mean Adobe Acrobat Pro? And what kind of documents do you want to read, comment, etc?

If you're talking about PDF files, here's some info:

[LIST]
[*]Saving/export as PDF can easily done in **OpenOffice**
[*]**Evince** is a good reader for PDFs (and other formats)
[*]Edit PDFs it's a bit harder. Mainly because PDF is a distribution file format not meant to be edited even though there are software capable of this. 
Maybe **inkscape** can do this? (Search around in the forums)
[*]To annotate PDFs (i.e make comments, notes, highlights, etc) - I think you can use **pdfedit** or **xournal**
but I have little experience with this, so I suggest you try for yourself.
[/LIST]

All of these mentioned applications are available with Ubuntu.

Hope this helps somewhat.
Ya I meant Adobe Acrobat Pro
thank you for your suggestions I will try them out

---

### Post by prokoudine on 2010-01-26
> **lykeion said:**
> 
[*]Edit PDFs it's a bit harder. Mainly because PDF is a distribution file format not meant to be edited even though there are software capable of this. 
Maybe **inkscape** can do this? (Search around in the forums)

[*]To annotate PDFs (i.e make comments, notes, highlights, etc) - I think you can use **pdfedit** or **xournal**
but I have little experience with this, so I suggest you try for yourself.
Well, **actually** :) PDFedit is the PDF editor and annotations can be done in Okular (KDE4 applications).

I don't think you can substitute Acrobat Professional fully, but as usual it pretty much depends on what you do.

Inkscape does open PDF files, but it sometimes it crops a page and doesn't show everything. Moreover it treats all colors from PDF as sRGB (the PDF library it uses actually has it fixed, but using the related functionality is not something Inkscape developers have done already).

---

### Post by mrhellboy86 on 2010-01-30
I have Gnome
so I couldn't use the KDE apps?
is it possible to install KDE beside Gnome?
there is not any Gnome version ?

---

### Post by prokoudine on 2010-01-30
> **mrhellboy86 said:**
> I have Gnome
so I couldn't use the KDE apps?
is it possible to install KDE beside Gnome?
there is not any Gnome version ?
You can use both KDE and GNOME applications at the same time. A GNOME version of what exactly do you refer to? :)

---

### Post by doublewitt on 2010-01-30
Okular is very, very good! It's my favorite pdf viewer. Okular lets you annotate your pdf's easily. Annotations include: drawing circles around text, highlighting, underline, insert in-line notes, popup notes, stamp, different colors. In the options, you can untick "Obey DRM limitations" and passwords and restrictions will not stop you. I really enjoy using this application. It's solid, stable and I've never had any problems with it.

---

### Post by cherep on 2010-12-13
> **doublewitt said:**
> Okular is very, very good! It's my favorite pdf viewer. Okular lets you annotate your pdf's easily. Annotations include: drawing circles around text, highlighting, underline, insert in-line notes, popup notes, stamp, different colors. In the options, you can untick "Obey DRM limitations" and passwords and restrictions will not stop you. I really enjoy using this application. It's solid, stable and I've never had any problems with it.

can all drawing and highlighting be saved in a pdf-file?

---

### Post by apollothethird on 2010-12-13
> **cherep said:**
> can all drawing and highlighting be saved in a pdf-file?

Yes.

The editing tool would be rather useless if all changed went out the window when you closed the pdf file.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cherep on 2010-12-13
> **apollothethird said:**
> Yes.

The editing tool would be rather useless if all changed went out the window when you closed the pdf file.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Cool, it really works! Thanks!

---

### Post by berlinblue on 2010-12-16
Hi all, 

Thanks for pointing me to these programs, I didn't know of yet. 
I just tried out [[COLOR="Red"]PDFEdit[/COLOR]]("http://pdfedit.petricek.net/en/index.html"), but it looks quite complicated in use for me as a newbie... 
For example, I couldn't find the way to changing the page order (if that's possible at all??). 

Then I found two useful, more **Newbie-proof** software packages:
1. [[COLOR="Red"]Pdftk[/COLOR]]("http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/") (**PDF Chain** in Software Center @ Ubuntu 10.10)
2. [[COLOR="Red"]PdfMod[/COLOR]]("http://live.gnome.org/PdfMod")

Looks like they're a good help for me, in keeping around
my most used functionality of Acrobat Professional!

And more software reviews can also be found [[COLOR="Red"]here[/COLOR]]("http://www.ubuntugeek.com/list-of-pdf-editing-tools-for-ubuntu.html").

Hope this helps!

---

### Post by DZ* on 2011-01-04
> **cherep said:**
> can all drawing and highlighting be saved in a pdf-file?

Drawing and annotations are saved outside of the PDF (in ~/.kde/share/apps/okular/docdata). If you rename the file or move it to a different computer, they will be lost. To keep it all together, use File -> Export As -> Document archive. This will make a file with .okular extention. You can later open that file in okular.

---

### Post by tshirtdr1 on 2011-01-04
Yes. I use Konqueror on my gnome system. I just type sudo apt-get install konqueror at the prompt. I get the bare bones KDE with konqueror installed. Konqueror is available in gnome. I also install other software this way. Just try "sudo apt-get install whateversoftware" at the prompt.

---

### Post by dsfitzpat on 2011-08-19
This is a bit late, so I'm not sure it'll be helpful (I came across this wondering if Acrobat Pro would run on Linux, since a license is available through my employer.)
As was already pointed out, Okular works, but only if you're not planning to share with others (esp. others who run Windows).  There are two options; one I've tried, one is on my 'to play with' list:
1. PDF-XChange viewer.  You can download it for free from Tracker Software.  This is a Windows program, but it's worked 100% for me under Wine.  It allows annotations, sticky notes, editing, etc.
2. Acrobat reader + pdftk.  It is possible to annotate a pdf in Linux with the free version of Acrobat, provided someone else has enabled the necessary permissions (typically with Acrobat Pro).  There are a lot of things you can do with pdftk - encryption, collating, merging, etc - and I've read that enabling the annotation permissions is one of them.  I haven't tried it out.  If it works, I'd be interested in hearing about it.

---

### Post by dsfitzpat on 2011-08-19
Update: I installed acrobat and tried using pdftk to allow annotations, but it didn't seem to work.  I might tinker some more in the future, but it's quite likely that option 1 is the way to go.

---

### Post by Indecline on 2011-09-18
I'm also looking for a PDF reader that can highlight and made basic modifications to PDF files without tooo much labour. I'll give [COLOR=Black]Pdftk a shot to see if it is what I'm looking for. 

Thanks for posting links, and thanks to everyone who has responded so far!
[/COLOR]

---

### Post by PC_load_letter on 2011-09-19
> **lykeion said:**
> 
... or **xournal**.

That's what I use to edit and annotate pdf files, works like a charm. Install from the repos.

---

### Post by dsfitzpat on 2011-09-19
I thought xournal had the same problem in that the annotations live in a separate .xml file, so if you need it to save annotations that someone using Windows and Acrobat can read, it doesn't work.  Is xournal now able to edit the pdf?

---

### Post by maul9999 on 2011-09-20
> **mrhellboy86 said:**
> Hi all
I wanted to ask you that If any program like Adobe Professional exist for Ubuntu?
I want a software that be handy for reading and also have some good tools to write some comments, HighLight , ... for editing and marking
sorry if i did send this thread here, I am just fresh in this forum , don't know if I send thread in its own place or the place is wrong 
thanks in advance

Hmm.  It should be come with DVD installing Linux.  I don't know. It had been long ago.

---

### Post by dedede12 on 2011-09-22
do you have a link on PDF&
well, i see that it works))





-----------
download my [shoutbox script]("http://www.wilsontechnology.com/")

---

### Post by dsfitzpat on 2011-09-22
I tried the latest xournal and it doesn't seem to save the annotations to the original pdf.  It also seems to lack thinks like sticky notes and a callout tool.  So far I haven't been able to use pdftk to enable editing permissions so the free acrobat can be used but I'll keep fiddling with that.  I know running a Windows program under Wine always seems like a small failure but it might still be the best option.

---

### Post by maul9999 on 2011-09-22
Ah! I remember!  You should try Ubuntu Studio, it is good way for graphics, CAD, and office work like PDF exporter.  There is a lot of developer and design program.  Here is link.  [http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by dsfitzpat on 2011-09-22
Bad news with pdftk.  OK, you can convert your document to allow permissions for things like annotations and editing, but only if you do so while also applying a password used to unlock said permissions.  And of course, the only way you can use this password to unlock those permissions is if you're using - wait for it - Adobe professional.

I am going to stick with PDF-Xchange viewer under Wine as the best solution at the moment.  It has all the editing tools you need, like sticky notes, callout, highlighting, etc, and saves these things natively to the pdf.
Okular will do the same but doesn't modify the actual pdf, so it's not as useful for sharing.

My understanding of Ubuntu Studio is that it's basically regular Ubuntu with programs like GIMP and Inkscape and Blender installed by default.  You can use GIMP to edit a PDF, but you have to import one page at a time, and it's really kludgey.

---

### Post by maul9999 on 2011-09-22
> **dsfitzpat said:**
> Bad news with pdftk.  OK, you can convert your document to allow permissions for things like annotations and editing, but only if you do so while also applying a password used to unlock said permissions.  And of course, the only way you can use this password to unlock those permissions is if you're using - wait for it - Adobe professional.

I am going to stick with PDF-Xchange viewer under Wine as the best solution at the moment.  It has all the editing tools you need, like sticky notes, callout, highlighting, etc, and saves these things natively to the pdf.
Okular will do the same but doesn't modify the actual pdf, so it's not as useful for sharing.

My understanding of Ubuntu Studio is that it's basically regular Ubuntu with programs like GIMP and Inkscape and Blender installed by default.  You can use GIMP to edit a PDF, but you have to import one page at a time, and it's really kludgey.

Be glad that you can download other program for free.  Finding good program, installing it.

---

### Post by dsfitzpat on 2011-09-22
PDF-Xchange is the best free option I've found, even though it requires Wine.  There is also this: [http://www.qoppa.com/pdfstudio/](http://www.qoppa.com/pdfstudio/) but it costs money.  There's a free trial available and they have a Linux version, but I've never tried it and don't know if it's trustworthy.

---

### Post by maul9999 on 2011-09-22
> **dsfitzpat said:**
> PDF-Xchange is the best free option I've found, even though it requires Wine.  There is also this: [http://www.qoppa.com/pdfstudio/](http://www.qoppa.com/pdfstudio/) but it costs money.  There's a free trial available and they have a Linux version, but I've never tried it and don't know if it's trustworthy.

Be warning, WINE is not stable-true neither PlayonLinux.  I can't promise that it is more safe for your Windows-Base program within ubuntu-base WINE.  DirectX for linux is not stable yet.  Any made mistaken with setting WINE, you will have to remove everything or reformat and reinstalling OS.

---

### Post by dsfitzpat on 2011-09-22
So WINE can break Ubuntu to the point of requiring an OS reinstall?  I hadn't heard that before.  The only thing I use it for is this PDF program so I'm not too worried.

---

### Post by maul9999 on 2011-09-22
> **dsfitzpat said:**
> So WINE can break Ubuntu to the point of requiring an OS reinstall?  I hadn't heard that before.  The only thing I use it for is this PDF program so I'm not too worried.

Yeah.  as my experience with WINE.  I used it for gaming.  One thing i make mistaken with WINE, game stop work and unable to boot up or start up game.   ONLY reinstall OS if you can't fix WINE.  First i uninstall corrupt WINE program then i delete it by use package manage.  Then reinstalling WINE from internet to fix it.  WINE does not break Ubuntu's file but it can get bug inside WINE as well.  WINE is not a stable-true, it have 3d problem and sound problem.  Sound card used by linux is work like AC 97', not HD audio.

---

