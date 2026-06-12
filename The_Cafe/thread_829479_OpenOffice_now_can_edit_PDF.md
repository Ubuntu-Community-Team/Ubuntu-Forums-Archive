---
title: "OpenOffice now can edit PDF"
date: 2008-06-14
forum: The Cafe
---

### Post by racoq on 2008-06-14
Quite handy this new plugin from sun. it allows you to import PDF's and edit them directly in writer, a description follows next:

> 
The PDF Import Extension allows modifying existing PDF files for which the original source files do not exist anymore. PDF documents are imported in Draw and Impress to preserve the layout and to allow basic editing. It is the perfect solution for changing dates, numbers or small portions of text. Native PDF forms are not yet imported. 

(...)

This is just a beta version and it requires the OpenOffice.org 3.0 beta 2 to work. Please help us to optimize this Extension, any feedback is important for us. Find details about the preferred channel in this
GullFOSS article.



Please test the plugin and report possible bugs, for improving this great feature.

Link:

[http://extensions.services.openoffice.org/project/pdfimport]("http://extensions.services.openoffice.org/project/pdfimport")

---

### Post by Acglaphotis on 2008-06-14
Awesome, i had to use PDFedit for this until now.

---

### Post by zmjjmz on 2008-06-14
Needs OOo3, I hope it will be included by default for that.

---

### Post by phrostbyte on 2008-06-14
> **zmjjmz said:**
> Needs OOo3, I hope it will be included by default for that.

From what I hear PDF editing is one of the planned features of OOo 3.

---

### Post by racoq on 2008-06-14
> **phrostbyte said:**
> From what I hear PDF editing is one of the planned features of OOo 3.

The beta is availalabe, and for a beta is quite usable. So we have no excuse to start testing this since it will be a "plus" for any user, IMO the great feature of the next  Openoffice release, and eventually may promote user switch from MS Word, at least until next Office release (which i believe will enable edit and save PDF Files) .

The propose of my thread is for the large comunity of Ubuntu, to test this important feature. Then people can't say, "it's a memory Hog" , "its slow and can't render well" , as it is said about other software. I won't say the name of that software,   "coofffffirefox", "cough", "cough".

---

### Post by klange on 2008-06-14
It says it requires beta 2, which doesn't come out until July 1st.
Lies?

---

### Post by zmjjmz on 2008-06-14
3 seems to be a big number for the popular OSS :-k
Does anyone know if this is built-in to MS Office?

---

### Post by klange on 2008-06-14
> **zmjjmz said:**
> 3 seems to be a big number for the popular OSS :-k
Does anyone know if this is built-in to MS Office?

MS Office has no capabilities when it comes to PDF.

---

### Post by Mateo on 2008-06-14
I actually don't like this.  PDF's are not meant to be editted.  Oh well.

---

### Post by zmjjmz on 2008-06-14
Then this will be instrumental in getting my mom to switch to OOo.

---

### Post by racoq on 2008-06-14
> **WindowsSucks said:**
> It says it requires beta 2, which doesn't come out until July 1st.
Lies?

I haven't test it yet, althought you have a point there. You can however test it using one of the latest OpenOffice 3.0 snapshots, it will certanly work, see the following link:
[URL="http://download.openoffice.org/680/"]
http://download.openoffice.org/680/[/URL]

---

### Post by 71CH on 2008-06-14
So how do I install this after I download it?

---

### Post by kevin11951 on 2008-06-15
> **71CH said:**
> So how do I install this after I download it?

```
cd /the/folder/where/it/is
```

```
sudo dpkg -i *.deb
```

---

### Post by RiceMonster on 2008-06-15
you can also simply double click on it in Nautilus if it's a .deb

---

### Post by kevin11951 on 2008-06-15
> **RiceMonster said:**
> you can also simply double click on it in Nautilus if it's a .deb

well, the open office app, comes in core.deb, math.deb, writer.deb, impress.deb, calc.deb, base.deb, draw.deb, etc... 

so to install it, you need to do a *.deb

---

### Post by ad_267 on 2008-06-15
Yeah I was under the impression that you weren't supposed to be able to edit a pdf once it was created, but this would be a useful feature.

This explains why there is no PDF support in MS Office natively: [http://www.cio.com/article/22058/Adobe_Speaks_Out_on_Microsoft_PDF_Battle](http://www.cio.com/article/22058/Adobe_Speaks_Out_on_Microsoft_PDF_Battle)
Adobe was a afraid of Microsoft's Embrace, Extent, Extinguish method and fair enough. PDF export is available as a downloaded extra for MS Office.

---

### Post by hartl_vienna on 2008-06-15
Wow, it works great with OO 3 beta. This is a "killer feature" for OpenOffice!   :KS

---

### Post by kaboodle_fish on 2008-06-15
> **71CH said:**
> So how do I install this after I download it?

In OO Beta 3 select Tools - Extension Manager then navigate to where you saved the file and Add

---

### Post by bash on 2008-06-15
Here is an article about it:

[http://www.oooninja.com/2008/06/pdf-import-hybrid-odf-pdfs-extension-30.html](http://www.oooninja.com/2008/06/pdf-import-hybrid-odf-pdfs-extension-30.html)

The Hybrid PDF options sounds especially interesting. Really seems like an amazingly clever idea.

---

### Post by guraknugen on 2008-06-17
> **Mateo said:**
> I actually don't like this.  PDF's are not meant to be editted.  Oh well.

I have a couple of PDFs which I downloaded from some places. They are like forms, so you can enter things in fields. With the usual PDF readers, such as Adobe Reader, Evince and whatever, you can fill those fields with text and print it out, but when you save it, everything you filled in is gone. So what's the point with that form thing, if it's not possible to save it?

&#8221;Editing a pdf&#8221; means, of course, more than that, but at least being able to fill in a &#8221;PDF form&#8221; and then saving it should be possible. Why not?

---

### Post by rudihawk on 2008-06-17
> **Mateo said:**
> I actually don't like this.  PDF's are not meant to be editted.  Oh well.

Not actually. PDF is just a standard so that documents can be read and transported everywhere. Its just another format, e.g like .doc, .odt. Only difference is, up until now the software to edit it has been out of reach of most people.

and MS Office 07 does have 0 capabilities with regard to PDF. In my books = fail. I submit most of my work in .pdf format:guitar:

---

### Post by ssam on 2008-06-17
the PDF format is not designed with editing in mind.

think of the difference of saying: here is a few thousand words of text, at size X, on A4 pages, when you hit the end of a page, flow onto the next.

and: here is a word, it goes at coordinates x,y on page z. here is another word it goes at ...

now compare the work needed to change those instructions when someone adds a paragraph to the middle, or changes the font size.

to usefully edit PDF, the software has to do a lot of work to convert the information back into a usable format.

---

### Post by Mateo on 2008-06-17
> **guraknugen said:**
> I have a couple of PDFs which I downloaded from some places. They are like forms, so you can enter things in fields. With the usual PDF readers, such as Adobe Reader, Evince and whatever, you can fill those fields with text and print it out, but when you save it, everything you filled in is gone. So what's the point with that form thing, if it's not possible to save it?

”Editing a pdf” means, of course, more than that, but at least being able to fill in a ”PDF form” and then saving it should be possible. Why not?

But, for that problem, "editing a pdf" is just a way to hack around Adobe's design flaw.  It doesn't fix the problem.  The solution is for Adobe to design a way to save the form data to another file.

Another hack around the problem that I'd suggest for you is to print the form and then scan it back to PDF.  Not ideal but better than messing with a binary document.

---

### Post by guraknugen on 2008-06-18
> **Mateo said:**
> Another hack around the problem that I'd suggest for you is to print the form and then scan it back to PDF.

Since that copy will not be editalbe anyway, a better solution should be to Print as PDF (which doesn't require any additional software anyway, since it's installed with Ubuntu by default these days). No scanning necessary, which is good since there are no Linux drivers for my scanner anyway.

---

### Post by Methuselah on 2008-06-18
Why are people saying PDf documents aren't 'meant' to be edited?
How do you think they get created in the first place?

---

### Post by guraknugen on 2008-06-18
> **ssam said:**
> the PDF format is not designed with editing in mind.

think of the difference of saying: here is a few thousand words of text, at size X, on A4 pages, when you hit the end of a page, flow onto the next.

and: here is a word, it goes at coordinates x,y on page z. here is another word it goes at ...

now compare the work needed to change those instructions when someone adds a paragraph to the middle, or changes the font size.

to usefully edit PDF, the software has to do a lot of work to convert the information back into a usable format.

Yes, I know that. However, now and then I look for some kind of form that I need to fill in and send to some kind of authority. Their home page often tells me to download the form, print it out, fill it in (using a pen), and send it somewhere with &#8221;snail mail&#8221;. Of course I can do that, but I just think it would be nice to fill it in BEFORE printing it out, which indeed is possible in most cases, but I also want to save a copy on my HDD, so if I just could save my filled in form, that would be so nice.

Of course, no one would be happier than me if I first could convert the PDF to an ODF, THEN fill it in, print it out and save it.

But my point is something like &#8221;No, maybe a PDF is not supposed to be edited, but it wouldn't hurt anyone if I could, or at least convert it to a more editable format, preferably ODF&#8221;

---

### Post by shanek on 2009-01-02
By the way, if you install openoffice 3 using this repository:```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```The PDF import plugin is in this repository.```
sudo apt-get install openoffice.org-pdfimport
```

Cheers

---

### Post by pp. on 2009-01-02
> **guraknugen said:**
> ... download the form, print it out, fill it in (using a pen), and send it somewhere with ”snail mail”. Of course I can do that, but I just think it would be nice to fill it in BEFORE printing it out, which indeed is possible in most cases, but I also want to save a copy on my HDD, so if I just could save my filled in form, that would be so nice.

Of course, no one would be happier than me if I first could convert the PDF to an ODF, THEN fill it in, print it out and save it.

If the job is properly done, you can fill in fields in a PDF document, save that document to disk and mail or print later at your leisure.

---

### Post by zika on 2009-01-02
> **shanek said:**
> By the way, if you install openoffice 3 using this repository:```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```The PDF import plugin is in this repository.```
sudo apt-get install openoffice.org-pdfimport
```Cheers

I've installed openoffice.org-pdfimport through Synaptic and when I File->Open .pdf file in OoWriter I just get garbage ... what am I doing wrong?

Update: I should have used OpenDocument in Office.org ... ;) it takes for ages ...

---

### Post by OldBitByter on 2009-02-12
> **Mateo said:**
> I actually don't like this.  PDF's are not meant to be editted.  Oh well.

Maybe people shouldn't save things that need editing in PDF's then.:P

---

### Post by guraknugen on 2009-02-12
> **Mateo said:**
> PDF's are not meant to be editted.

And Compact Cassettes (remember those?) were not originally meant for music.

Heard of the word &#8221;development&#8221;?

---

### Post by llamabr on 2009-03-21
> **Mateo said:**
> I actually don't like this.  PDF's are not meant to be editted.  Oh well.

I guess don't like sunglasses either, as your nose wasn't "meant" to hold them up.

Ridiculous.

Regarding the design of pdf's, they're "meant" to be a format to make documents portable, across systems and architecture. 

That you were previously unable to easily edit them doesn't mean that the rest of us have not been doing so the entire time, nor that doing so is in some way inconsistent with their "nature".  I happen to not like putting movies on DVD, since that's not what they're "meant" for.  Oh well.

---

### Post by undoIT on 2009-07-03
I just installed this for Jaunty with the following repository:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
```

This plugin works fantastically well. I don't have any need for Adobe Acrobat anymore :)

---

### Post by PGScooter on 2009-07-29
that did it for me as well (I also added the key, just google the ppa for instructions on that). Everything installed fine, I had to restart, and then when I opened a pdf it automatically imported it (ie no "import" thing in the file menu, just open it!).

---

### Post by jmjohn on 2009-10-25
Everyone,

Editing PDFs is a normal activity and can be performed by the proprietary Adobe Acrobat software.

The idea the PDFs can't be edited is a misconception.  It is good that openoffice allows editing PDFs in Linux.

---

### Post by RichardLinx on 2009-10-25
> **jmjohn said:**
> Everyone,

Editing PDFs is a normal activity and can be performed by the proprietary Adobe Acrobat software.

The idea the PDFs can't be edited is a misconception.  It is good that openoffice allows editing PDFs in Linux.

This thread was started in 2008, and the last post was three months ago...
I don't think there's a misconception that PDF's can't be edited, it was talking about the fact that OpenOffice now supports the editing of PDF which was a feature a lot of people wanted/needed (myself included).

And of course it can be edited by the proprietary Adobe Acrobat Software, Adobe's the company that invented the format in the first place.

---

### Post by jmjohn on 2009-11-01
Good point.

:)

---

### Post by jmuggins on 2010-02-05
> **llamabr said:**
> I guess don't like sunglasses either, as your nose wasn't "meant" to hold them up.

Ridiculous.

Regarding the design of pdf's, they're "meant" to be a format to make documents portable, across systems and architecture. 

That you were previously unable to easily edit them doesn't mean that the rest of us have not been doing so the entire time, nor that doing so is in some way inconsistent with their "nature".  I happen to not like putting movies on DVD, since that's not what they're "meant" for.  Oh well.

That may be true, but in some PDFs I use as reference material, it would be nice to reformat a page or two that are landscape instead of portrait.

MHO...

---

### Post by jmuggins on 2010-02-05
> **undoIT said:**
> I just installed this for Jaunty with the following repository:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
```

This plugin works fantastically well. I don't have any need for Adobe Acrobat anymore :)

Thanks! ;)

---

### Post by mrvaio on 2010-02-08
I have tested it and it doesn't work for me. 
Every row in the pdf is inside a container and there is no way to edit them all in once.

I really interested in this feature but it is not so mature to be used in production.

Anyway, thanks.

---

### Post by AbdRahim on 2010-05-06
Did not work for me either. Tried opening pdf w/ OO writer and presentation. Then tried inserting it as OLE object from file. All cases produced an input/output error.:guitar::guitar:

---

### Post by gcbzzzz on 2010-07-18
opens as slides. and misses most of the images.

using version 1.0+OOo3.2

---

### Post by kevin11951 on 2010-07-18
> **gcbzzzz said:**
> opens as slides. and misses most of the images.

using version 1.0+OOo3.2

If its not sensitive, can you post the PDF here?

---

### Post by gauravm on 2010-07-27
If all you wish to do is add to a pdf file (as in filling a form) then the best software I have found for that purpose is xournal.  You can open a pdf via "File --> Annotate PDF" and then add to it whatever you choose and then "File --> Export To PDF" or "File --> Print" 

This is awesome with a tablet because essentially it has negated my need to ever print anything that I need to then scan back to email!  Good for trees!

---

### Post by SeraMea on 2010-09-21
I have used Xournal and like it, but when i'm workin with heavy documents i kind'a need the list (on the left side listing pages and topics) im used to from adobe. 
I'm using a tablet, so that list would be really helpfull. 

So my question is: how/what app do i use to work with hevy documnets and still manage to take notes with my tablet pen?? And of course a app that will provide me with such a list. It makes it easier to jump from one place to another in a document containing several hundred pages.... 

Thanks :)

---

### Post by SeraMea on 2010-09-21
By the way... 
Okular gives me what i need, but i can't use my tablet-pen to edit in it... Pains me big time this issue.... 

:P

---

