---
title: "Sun offers ODF translator for Microsoft Office"
date: 2007-02-08
forum: The Cafe
---

### Post by mips on 2007-02-08
[http://news.zdnet.co.uk/software/0,1000000121,39285845,00.htm](http://news.zdnet.co.uk/software/0,1000000121,39285845,00.htm)

So in future send files to people in ODF format and have links at the bottom of your mail to the plug-ins & open office.

---

### Post by Spr0k3t on 2007-02-08
Now the only thing I'm waiting for is a method to convert MSOOXML files (like *.docx, *.xlsx etc) over to ODF.  Someone sent me a DOCX file the other day containing their resume.  I promptly fired back a "use PDF please" with a link to OOo.

---

### Post by mips on 2007-02-08
> **Spr0k3t said:**
> Now the only thing I'm waiting for is a method to convert MSOOXML files (like *.docx, *.xlsx etc) over to ODF.  Someone sent me a DOCX file the other day containing their resume.  I promptly fired back a "use PDF please" with a link to OOo.

PDF is prop. but i understand that you can read it unlike ooxml.

---

### Post by weatherman on 2007-02-08
> **mips said:**
> PDF is prop. but i understand that you can read it unlike ooxml.
I don't think it is, they recently released full specifications for it. I might be wrong though. wikipedia states it's open [http://en.wikipedia.org/wiki/Pdf](http://en.wikipedia.org/wiki/Pdf)

---

### Post by maniacmusician on 2007-02-08
if it's open, why aren't there better linux apps for reading **and** editing them? It's kind of annoying having to use OO and print to pdf when I want to create a pdf file. You can't use any of the advanced features of pdf when you do that...

---

### Post by Arathorn on 2007-02-08
The export to pdf function in OOo works quite well. I'm not sure what advanced features you miss, but I can make an index with links to parts of the documnt and that's all I need.
I believe Adobe is making pdf more open because they're under pressure from their clients to do so.

---

### Post by maniacmusician on 2007-02-16
I'm talking about features like "chapters". That's not really even an advanced feature. (if you're confused, I'm referring to the ability to divide a document into chapters and having them display on the left pane when using a pdf viewer. That way, you can choose a chapter, and then navigate from there.

Indexes can work for that too, but they're less flexible. I don't want to use a page for an index when I can have it integrated into the UI.

---

### Post by Polygon on 2007-02-16
isnt the msooxml specification designed to be open? so programs should start supporting them eventually i would think

but of course, microsoft is being microsoft and is creating their own standard when they could of just easily used the already existing open document format.

---

### Post by JAPrufrock on 2007-02-16
> **Arathorn said:**
> The export to pdf function in OOo works quite well. I'm not sure what advanced features you miss, but I can make an index with links to parts of the documnt and that's all I need.
I believe Adobe is making pdf more open because they're under pressure from their clients to do so.

There are a lot of features that Acrobat offers that you can't do in Ubuntu, like advanced editing, changing specific text, changing and embedding fonts, control over the amount of resolution reduction in images, OCR capabilities, etc.   It would seem, then, that Adobe's Acrobat is not as open as one might think.  In fact, I miss those features so much that I run Acrobat 4 using wine.  However, I still can't get the OCR plugin to work.

---

### Post by maniacmusician on 2007-02-17
> **maniacmusician said:**
> I'm talking about features like "chapters". That's not really even an advanced feature. (if you're confused, I'm referring to the ability to divide a document into chapters and having them display on the left pane when using a pdf viewer. That way, you can choose a chapter, and then navigate from there.

Indexes can work for that too, but they're less flexible. I don't want to use a page for an index when I can have it integrated into the UI.
Hmm for clarification, it seems that Adobe calls them "Bookmarks". An example of a file using this is the [VirtualBox user manual]("http://virtualbox.org/wiki/Downloads") . When you open it in Adobe Reader or KPDF, there is a browsable menu of chapters, subsections, etc. 

If PDF really is an open format now, we should have applications that can do simple things like this, right?

---

### Post by handylinux on 2007-02-17
> **maniacmusician said:**
> If PDF really is an open format now, we should have applications that can do simple things like this, right?

Well, someone has to write them first, a non-trivial task I expect. At least I don't know how to do it, so I won't complain that they don't (yet) exist -- and will be thankful when they do.

I haven't followed this closely, but I believe it was only about a month ago I read about Adobe releasing the PDF format to open source. A welcome move, to be sure, but it will take a while for full-featured non-Adobe PDF creator apps to appear.

Speaking of PDF features, a recent [Macworld article]("http://www.macworld.com/weblogs/macosxhints/2006/09/embedpdflink/index.php") clued me that Apple's Pages offers an ability missing from MS Word: live links created in a Pages document are preserved and clickable when it's made into a PDF. Then I was pleased to discover the same ability in OO (actually in NeoOffice, the "Mac-native" version of OO, but I assume it's in OO as well).

Micro$oft's new "open" formats initiative, transparently intended to torpedo the real cooperative effort to create real, universal open formats, is so obvious I'm amazed anyone treats it as serious. Then again, I'm mystified that so many people put up with Micro$oft's abuse anyway.

---

### Post by darkhatter on 2007-02-17
> **Spr0k3t said:**
> Now the only thing I'm waiting for is a method to convert MSOOXML files (like *.docx, *.xlsx etc) over to ODF.  Someone sent me a DOCX file the other day containing their resume.  I promptly fired back a "use PDF please" with a link to OOo.

that is going to be supported in b Novell, I believe they can't submit the patches up stream but everything is gpl so you can compile it your self I hope it finds its way into  universe or multiverse

---

### Post by Bloodfen Razormaw on 2007-02-17
> Hmm for clarification, it seems that Adobe calls them "Bookmarks". An example of a file using this is the VirtualBox user manual . When you open it in Adobe Reader or KPDF, there is a browsable menu of chapters, subsections, etc. 
 
 If PDF really is an open format now, we should have applications that can do simple things like this, right?
Writer DOES do this.  So does Word.  Publishing to PDF will use your headers to automatically generate bookmarks.  As long as you use styles correctly (and if you don't, you aren't doing word processing correctly), you will get bookmarks.  The application will also tag the PDF with the correct document structure for accessibility.

>  Speaking of PDF features, a recent Macworld article clued me that Apple's Pages offers an ability missing from MS Word: live links created in a Pages document are preserved and clickable when it's made into a PDF. Then I was pleased to discover the same ability in OO (actually in NeoOffice, the "Mac-native" version of OO, but I assume it's in OO as well).
Links in Office documents are preserved when published to PDF.  That feature is not missing at all.

---

### Post by maniacmusician on 2007-02-17
> **Bloodfen Razormaw said:**
> Writer DOES do this.  So does Word.  Publishing to PDF will use your headers to automatically generate bookmarks.  As long as you use styles correctly (and if you don't, you aren't doing word processing correctly), you will get bookmarks.  The application will also tag the PDF with the correct document structure for accessibility.
Can you please expand more on how to "use styles correctly" to create bookmarks? For instance, what headers are you talking about? It would be an absolute godsend for me if you could help me with generating proper PDFs.

---

### Post by frup on 2007-02-17
Since I'm studying to be an architect and would prefer to do side projects in open formats (most work requires proprietary just to deal with consultants etc etc unfortunately) etc etc... any advances in .pdf's etc are always very very appreciated.

---

### Post by Bloodfen Razormaw on 2007-02-17
> Can you please expand more on how to "use styles correctly" to create bookmarks? For instance, what headers are you talking about? It would be an absolute godsend for me if you could help me with generating proper PDFs.
You should never be arbitrarily styling bits of text; instead create paragraph and character styles that are reusable and tag the text and paragraphs with that.  That way all you do is write text and the formatting handles itself separately.  In OO.o Writer the styles are in the default toolbar, or you can open a sidebar for them.  By default you will see some styles called Header 1, Header 2, etc.  These are special styles that OO.o knows indicate which text marks off sections.  For example, a book's chapters could be tagged with Header 1, and the subsections of each chapter with Header 2.  OO.o's Export to PDF feature, as well as many other features, depend on the use of Header styles to know the document structure.  When you export to PDF, Header 1 text becomes the top level of the bookmarks, Header 2 is nested under that, and so on.  Other stuff to do for making a good PDF: always fill out the metadata for your document, like title, author, keywords, etc., since those are included in the PDF.

(Also, since OO.o makes it optional, be sure to enable tagging in the export dialog.  I can't imagine a reason to NOT include tagging, since it makes the document usable by those with disabilities.)

---

### Post by Mateo on 2007-02-17
No thanks, I'll continue to use RTF until I'm given a good reason not to.  It works in nearly every processor I've ever used, and is 1/16th the size of DOC or ODF files.

---

### Post by Polygon on 2007-02-17
> **Mateo said:**
> No thanks, I'll continue to use RTF until I'm given a good reason not to.  It works in nearly every processor I've ever used, and is 1/16th the size of DOC or ODF files.

i just did a test to see if you were right

7 page paper:

Opendocument format: 18.3 KB
resaved as a RTF: 40.8 KB

---

### Post by H.E. Pennypacker on 2007-02-18
> **maniacmusician said:**
> If PDF really is an open format now, we should have applications that can do simple things like this, right?

PDF became open, what, a few weeks ago?  Time is still a factor in developing software.

---

### Post by maniacmusician on 2007-02-18
> **H.E. Pennypacker said:**
> PDF became open, what, a few weeks ago?  Time is still a factor in developing software.
yeah, my bad, I didn't know that

I'm sure we'll be seeing good stuff soon since it is open now.

Bloodfen, thanks for the tip, I'll try that out right now. Hope it works.

---

### Post by maniacmusician on 2007-02-18
> **Bloodfen Razormaw said:**
> You should never be arbitrarily styling bits of text; instead create paragraph and character styles that are reusable and tag the text and paragraphs with that.  That way all you do is write text and the formatting handles itself separately.  In OO.o Writer the styles are in the default toolbar, or you can open a sidebar for them.  By default you will see some styles called Header 1, Header 2, etc.  These are special styles that OO.o knows indicate which text marks off sections.  For example, a book's chapters could be tagged with Header 1, and the subsections of each chapter with Header 2.  OO.o's Export to PDF feature, as well as many other features, depend on the use of Header styles to know the document structure.  When you export to PDF, Header 1 text becomes the top level of the bookmarks, Header 2 is nested under that, and so on.  Other stuff to do for making a good PDF: always fill out the metadata for your document, like title, author, keywords, etc., since those are included in the PDF.

(Also, since OO.o makes it optional, be sure to enable tagging in the export dialog.  I can't imagine a reason to NOT include tagging, since it makes the document usable by those with disabilities.)
I tried out what you said...but the problem is, each of those "styles" has a default font. So, for example, I have a certain font for my body, but when I select it and label it "Text Body", it switches the font to Times New Roman, and changes the size. For Headings, it changes it to Arial. 

Is there any way I can modify the default fonts? I have certain fonts that I like to use, that are specific to this project that I'm working on. I can't go through a 50 page document and change all the fonts manually. 

edit:  okay, I figured all that out. Now, is there any way to set Bookmarks without using headers?

For instance, there's the cover page. When in PDF format, I want its bookmark to be the title of the book. Say the title of the book was "Learning to Ride a Bike." Then, I would want that to be the first bookmark, and have all the others branching off of it. But I can't write the bookmarks independently....any suggestions?

---

### Post by Bloodfen Razormaw on 2007-02-18
> edit: okay, I figured all that out. Now, is there any way to set Bookmarks without using headers?
 
 For instance, there's the cover page. When in PDF format, I want its bookmark to be the title of the book. Say the title of the book was "Learning to Ride a Bike." Then, I would want that to be the first bookmark, and have all the others branching off of it. But I can't write the bookmarks independently....any suggestions?
I don't believe there is.  The export functionality looks specifically for headers.  If you want the cover included the best method I can think of is to apply header text at the top of the cover, in a frame so as to not mess up text-flow, and make it hidden (if that functionality exists, or make the frame too small to see, or make the text transparent or the background color; I don't use OO.o, so I'm not sure what is available to implement that).  Keep in mind, if you use automatic table of contents, it will see that header too.

---

### Post by mostwanted on 2007-02-18
> **maniacmusician said:**
> 
If PDF really is an open format now, we should have applications that can do simple things like this, right?

PDF has always been an open format or at least has for as long as I can remember.... I think the news is that PDF is on it's way to become an ISO standard.

---

### Post by maniacmusician on 2007-02-18
> **Bloodfen Razormaw said:**
> I don't believe there is.  The export functionality looks specifically for headers.  If you want the cover included the best method I can think of is to apply header text at the top of the cover, in a frame so as to not mess up text-flow, and make it hidden (if that functionality exists, or make the frame too small to see, or make the text transparent or the background color; I don't use OO.o, so I'm not sure what is available to implement that).  Keep in mind, if you use automatic table of contents, it will see that header too.
Ah I see. Thanks for all your help, you've at least got me much much further than I was before. 

I'll try your suggestion. You're a saint, thank you **so much**.

---

### Post by maniacmusician on 2007-02-18
> **mostwanted said:**
> PDF has always been an open format or at least has for as long as I can remember.... I think the news is that PDF is on it's way to become an ISO standard.
if thats the case. then I'm a little pissed again that we don't have good applications for editing PDFs!

Of course, there's the fact that I can't code to save my life, so I shouldn't be complaining about it, but still. Someone should get going on this, PDF is a really widely used format, and we should have good support for it.

---

### Post by Bloodfen Razormaw on 2007-02-18
We will likely have excellent PDF editing tools soon.  PDF right now is very complex to implement, basically being preprocessed Postscript with extensions.  Upcoming versions of PDF will be replaced with what is now codenamed Mars, which is going to be a compressed archive with the document defined in XML.  That will make PDF implementation much easier.  It will basically be like XPS in concept, except with the full PDF featureset.  Mars is far enough along that Adobe already has experimental plugins for Adobe Acrobat/Adobe Reader which can open Mars PDFs and convert existing PDFs.

[http://labs.adobe.com/wiki/index.php/Mars](http://labs.adobe.com/wiki/index.php/Mars)

---

### Post by maniacmusician on 2007-02-18
That's pretty neat. I hope that Mars takes off soon...I don't want to have to reformat my book too many times, lol.

Those conversion tools never work properly for me. Some aspect of the formatting always seems to get screwed up.

---

### Post by Mateo on 2007-02-18
> **Polygon said:**
> i just did a test to see if you were right

7 page paper:

Opendocument format: 18.3 KB
resaved as a RTF: 40.8 KB

care to upload one of the files?

---

### Post by Bloodfen Razormaw on 2007-02-18
It's a fact that RTF will always be bigger than ODF or OOXML.  All are marked up plain text, but RTF is not compressed, unlike the later two.  I just tested DOCX vs. RTF with Office 2007 with 9 pages.

OOXML: 14kB
RTF: 73 kB.

Edit: Even more fun, this is what happens when I Insert a 138 kB image into each:

OOXML: 151 kB
RTF: 5,955 kB

That's right, the RTF hits about 6 MB!  At first I thought Word must have encoded the image into the RTF as a Windows Bitmap, but no, it is indeed the original JPEG.

Edit Again:
> Those conversion tools never work properly for me. Some aspect of the formatting always seems to get screwed up.
I doubt you need to worry.  Mars *is* PDF.  It has the same features and instructions.  Only now its XML.  Since there should be an exact correlation between Postscript-based PDF and XML-based PDF it should be possible to have an exact, flawless conversion.

---

### Post by Mateo on 2007-02-18
That's a curious result so I did some testing of my own.  I went to random news stories (found at news.google.com) and copy pasted the plain text. Here's one test:

[http://www.latimes.com/news/nationworld/world/wire/sns-ap-israel-palestinians-us,1,7186411.story?coll=sns-ap-world-headlines&ctrack=1&cset=true](http://www.latimes.com/news/nationworld/world/wire/sns-ap-israel-palestinians-us,1,7186411.story?coll=sns-ap-world-headlines&ctrack=1&cset=true)

DOC: 107KB
ODT: 16KB
RTF: 5KB

but further testing with longer documents (public domain short stories) the results came out different, with rtf being inexplicably bloated once you pass 5 or 6 pages.  this short story was:

[http://easyweb.easynet.co.uk/~fadey/magnus.html](http://easyweb.easynet.co.uk/~fadey/magnus.html)

DOC: 161KB
ODT: 31KB
RTF: 43KB

---

### Post by Bloodfen Razormaw on 2007-02-18
You are comparing the now-deprecated DOC format.  The old DOC was very large, whereas the current one is quite small.

The reason RTF explodes in size when the number of pages grow is that it has very poor handling of styles, which forces an excessive amount of repetition for things like font names, etc.  The lack of compression makes things much worse, since repetitive text is the best case for compression.  Since the same tags, and same style information is going to be repeated time after time in an ODF or DOCX file, the compression achieved is extremely high.  That 14 kB .docx file I mentioned is 48 kB without compression.  Much larger, but still smaller than the same document in RTF because of the better style handling and OOXML's extremely short tag names.

BTW, I tested that count magnus story and got 30 KB for OOXML, 60 KB for RTF.  When I trim it down to just one page, the difference actually grows, with OOXML using 13 kB, and RTF taking 34 kB.  If I zip that RTF it goes down to 19 kB, almost half what it was.

Edit: Another RTF filesize problem is internationalization.  RTF explodes in size if you use anything beyond ASCII.  I copied and pasted the text from Yahoo! Japan; 18 kB in OOXML, 152 for RTF.  Each character was encoded as 2 bytes in DOCX, and 15 bytes in RTF, since RTF doesn't support anything beyond ASCII natively.

---

### Post by Mateo on 2007-02-18
Office must handle RTF weird.  I'm using Open Office; 1 page of the magnus story was 19kb in ODT and 8kb in RTF.  ODT only takes over once you hit 4 pages.  At 3 1/2 pages they are even at 22kb.  Anything less than that and RTF is smaller.

---

### Post by Bloodfen Razormaw on 2007-02-18
Office is *the* RTF implementation.  RTF is Microsoft's proprietary specification, created and updated for the sake of handling Word documents.  Everything in RTF is there for the sake of supporting Word's features.

---

### Post by mostwanted on 2007-02-19
> **maniacmusician said:**
> if thats the case. then I'm a little pissed again that we don't have good applications for editing PDFs!

Of course, there's the fact that I can't code to save my life, so I shouldn't be complaining about it, but still. Someone should get going on this, PDF is a really widely used format, and we should have good support for it.

PDF was not originally supposed to be edited, it was solely intended to make documents into portable print-outs. Fomats like Microsoft word and HTML that are intended for subsequent editing are too "*fluid*" for publishers. They're great for drafts but too unreliable for general presentation.

---

### Post by Mateo on 2007-02-19
yeah, you make documents in word or html (depending on your needs) and then convert it to PDF as a sort of "final draft".  the fact that it can't be edited is supposed to be a good thing, if you are the publisher.

---

