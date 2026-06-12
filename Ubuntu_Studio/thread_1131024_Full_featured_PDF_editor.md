---
title: "Full featured PDF editor?"
date: 2009-04-20
forum: Ubuntu Studio
---

### Post by javyn999 on 2009-04-20
Hey all.  Been using Ubuntu for a little over a week now, and have to say, I love it, and am wanting very badly to finally ditch Windows....at home at least.

My biggest issue though for completely moving away from Windows XP is as follows:

I work as a paralegal in very document intensive litigation.  I NEED a full featured PDF editor, nothing short of Adobe Acrobat or Nitro PDF's functionality.  I use NitroPDF for work mainly.  

I have done a bit of searching, but it doesn't seem like a native Linux app will fill my requirements here.  I also checked the compatibility list in Wine, Adobe Acrobat full seems to be problematic...and Nitro just flat out doesn't work at all in Wine.  

I tried running NitroPDF in a Windows XP Virtual Machine via VirtualBox.  Editing PDFs in a XP VM is incredibly SLOW....but... I only have 512 system ram, and 198 of which dedicated to my XP VM.  If I upgrade this box (Athlon XP2800+, 2.07ghz) to 2 gigs of DDR RAM and allocate 512 of that to my XP VM, think that will solve my problem?

Or would I be best off finding a native Linux pdf editor...or...are neither of these a good solution, and I can expect my PDF editing to be excruciatingly slow regardless how much system ram I have, and regardless how much ram I allocate to my XP virtual machine?  

Kinda lost here and can really use some guidance to be completely Microsoft free!

Thanks guys!

---

### Post by Stochastic on 2009-04-20
Give pdfedit a try (it's in the repos) it has some bugs but gets the job done for my needs.

---

### Post by lukeiamyourfather on 2009-04-20
PDF is a horrifically misguided file format and has only recently become a partially "open" file format. If at all possible I'd suggest migrating to a current open file format like ODF that has better editor support and is intended for mainstream end users rather than manufacturers, product manuals, tax forms, 3D content, etc.

---

### Post by kayosiii on 2009-04-21
Scribus is the animal you are looking for.... It produces really descent quality pdf files... This page should explain it best...
[http://docs.scribus.net/index.php?lang=en&page=pdfexport1](http://docs.scribus.net/index.php?lang=en&page=pdfexport1)
It may or not be able to replace your existing software.
Good luck

---

### Post by wylfing on 2009-04-21
> PDF is a horrifically misguided file format and has only recently become a partially "open" file format.

I have a sneaking suspicion that the OP wants to get work done and collect a paycheck rather than engage his employers in a holy war about open formats. Just guessing. :P

> Scribus is the animal you are looking for

Unlikely. Scribus and Acrobat do entirely different things.

> Give pdfedit a try

Pdfedit can do some fairly sophisticated things, but it is *extremely* user-unfriendly. Also, its capabilities are technical-focused instead of workflow-focused, i.e., it doesn't mesh well with what I actually have to do for work.

> I NEED a full featured PDF editor, nothing short of Adobe Acrobat or Nitro PDF's functionality.

You are out of luck. You need Acrobat, and for Acrobat you need Windows.  There is no way around it. 

NitroPDF is the closest substitute in existence for Acrobat, and it's a relatively poor runner-up. There is nothing even remotely close to Acrobat that runs natively on Linux. (Pdfedit is probably the best there is, and it's...well, not even close.)

---

### Post by kayosiii on 2009-04-21
Have a look at your system usage memory Check under windows in the VM... If you are paging then you definately will get a boost from more memory.

Scribus does have excellent PDF output including, forms, slideshows and scripting. The major limitation being that it only exports PDF documents, it can not import them.

Sorry I can't help more...

---

### Post by Stochastic on 2009-04-21
Can you clarify a little bit as to whether you need to simply create a pdf document or modify existing pdf documents?

Lots of tools can do the former, only pdfedit (that I know of) can do the latter (on a linux system).

---

### Post by lukeiamyourfather on 2009-04-21
> **wylfing said:**
> I have a sneaking suspicion that the OP wants to get work done and collect a paycheck rather than engage his employers in a holy war about open formats. Just guessing. :P

I see that side of the story and completely understand the situation but there's also a matter of using the right tool for the job. Unless there's a specific reason for using PDF, as in the PDF provides functionality that other formats don't (embedded 3D content, "Connect" meetings, etc.) , then there's no reason to use PDF anymore.

As other users have said there really isn't a good way to work with PDF files in Linux to the same extent as Acrobat offers. So if Linux is going to be used perhaps its a good idea to move away from PDF files (to ODF for example). If PDF files are a necessity then maybe Linux isn't the way to go right now. Cheers!

---

### Post by Stochastic on 2009-04-21
If any format switch was to be undertaken, I wouldn't suggest ODF, as from what I know, that's only readable by OpenOffice.  I'd suggest using a postscript file ( .ps extension) as they're very comparable to pdf files.

---

### Post by jobix on 2009-04-22
If you know how to use latex, you can create PDF documents by compiling your tex source document, but it is a lot of work formatting to get it to exactly what you want it to be. But, if you want to work with other people's PDF documents, then this method won't work.

---

### Post by javyn999 on 2009-04-23
Thanks for the responses guys.  Well, I can't go to a different format, PDF is how I live or die.  A large part of my job entails converting documents of various formats over to PDF, editing them to make them conform with the Federal District Court's filing criteria, then filing electronically with the Court.  

I don't think many federal clerks or judges are going to be too interested in downloading whatever viewers are necessary to read what I file on behalf of our clients heheh.

Still, I thank you all for the responses.  I am definitely going to stick with Ubuntu....but it looks like instead of upgrading to Jaunty this weekend, I'll be doing a clean format so I can dual boot XP and Jaunty.

---

### Post by ju2wheels on 2009-04-23
If your computers fast enough you might want to consider VirtualBox instead of dualbooting... saves you from having to restart to switch between the two all the time.

---

### Post by javyn999 on 2009-04-23
I tried that, and running Nitro is incredibly slow.  I only have 512 RAM though, and 192 of it dedicated to my XP VM.  I have 2 gigs of ram on order and when I get that it may alleviate some of that lag.  Probably allocate 512 RAM to the VM and see how that goes.

---

### Post by Stochastic on 2009-04-23
> **javyn999 said:**
> A large part of my job entails converting documents of various formats over to PDF, editing them...

Can OpenOffice help you with this at all?  Open the given file in OO modify, then export to PDF.

---

### Post by sky pilot on 2009-04-23
From The Synaptic Package Manager
> Editor for manipulating PDF documents

Complete editing of pdf documents is made possible with PDFedit. You
can change either raw pdf objects (for advanced users) or use
predefined gui functions. Functions can be easily added as everything
is based on a scripts.

Scripting is used to a great extent in editor and almost anything can
be scripted, it is possible to create own scripts or plugins.

Canonical does not provide updates for pdfedit. Some updates may be provided by the Ubuntu community.



pdfedit can be made to do whatever you need it to do judging from this.  Usually I use pdf as a final formatter, do work in more specialized tools and then converting to pdf upon send or print.  Acrobat is not the best tool to create docs in but it is a very usable final format.

---

### Post by Bateluer on 2009-04-24
> **ju2wheels said:**
> If your computers fast enough you might want to consider VirtualBox instead of dualbooting... saves you from having to restart to switch between the two all the time.

The OP stated the PC was an AXP 2700 with 512MB of RAM. Upgrading the RAM to 2GB or so would make a substantial difference in VM, but it'll still be slower than XP native, unfortunately. 

RAM is cheap right now though, so I'd still do it regardless.

---

### Post by javyn999 on 2009-04-24
ebay and 16 bucks total upgraded me to 2 gigs pc2100.  Not the fastest in the world, but for the price, hell.

---

### Post by javyn999 on 2009-04-24
ebay and 16 bucks total upgraded me to 2 gigs pc2100.  Not the fastest in the world, but for the price, hell.  

Oh, and I use Nitropdf for editing, and CutePDF to print any document that's printable to convert to a PDF.  Acrobat is terribly expensive, and I find Nitro to work quite well.

---

### Post by chrisby on 2009-04-24
I have had pretty good luck with the portable version of PDF-XChange Viewer under wine.

I add annotations and fill in forms with it.  I know the full version has some other functionality.

---

### Post by ClarkePeters on 2009-07-01
Wish I had gotten in on this sooner, but pdfEdit, while it may not be user-friendly overall, it is exceptionally easy if all you need to do is edit the text (e.g. you don't need to move images around or anything.  

When you install it from synaptic (hardy), it goes into your "Graphics" menu and not the accessories, office, or "other" menus as you might expect.

Then, the only thing you need to do is start the pdf Editor from the Graphics menu. Then open your file.   You'll see a whole host of icons (editing buttons or whatever their called) on the top toolbar. The only one you need is the one on the second row down and near the middle -- it looks a little like a capital "I" with angled top and bottom cross bars.  Click this button and now you can edit any text, line -by - line, by clicking on the desired text. 
The selected text can be edited in a long text box in the upper left. Mark your changes and hit enter. (there's a tutorial online that walks you through a lot of unnecessary steps for this, I think it's outdated, so don't get confused if you come across this tutorial)

To navigate from page to page, use the green arrow buttons on the upper right side on the toolbar.

Doing anything beyond that gets complicated. I tried adding a text box (upper right button near the strikeout key), but everytime I did, it put the text in vertically rather than a normal horizontal line. Never could figure out how to adjust it. It was also very tiny text and I couldn't find a text of font size adjustment.

---

### Post by stribor2001 on 2009-07-05
hello, everyone, i'm also new to ubuntu and in a need of a practical pdf editor. i just downloaded pdf edit, but the main problem is that after every change on a document it fades out and stops responding for a while. since a use pdf mostly for reading and highlighting and commenting this is very annoying and slows progress through texts. 
do you have any suggestions for a more practical pdf editor?

---

### Post by westea49 on 2009-07-12
I am also looking for a PDFeditor like Adobe for reviewing and comments only, I do not want to modify the original document. I use it to send in suggestions to co-authors for papers and highlight problem areas.  

Yesterday I loaded the PDF plugin to openOffice and while it read in the PDF file, I ended up with sentences moving everywhere. Openoffice does a good job of reading in DOC files and converting to PDFs.  The PDF input does not recreate the original page formatting very well. Therefore, I was thinking about trying pdfedit.

I do have a VMware virtual XP and could load Adobe but was trying to "kick" the windows habit.  But Windows being a resource hog I did have to increase my memory for the virtual machine from 512MB to 1G to keep one of my applications stable (CorelDraw) so I understand the problem with using a virtual machine.

I may try pdfedit but it sounds like I may need to load Adobe on my VM

---

### Post by kayosiii on 2009-07-15
I know of two pdf viewers on Linux that allow for annotations.
One of them is Acrobat Reader from Adobe and the other is Okular... Okular is available through the package manager.

---

### Post by timjohn7 on 2009-07-15
Have you tried OpenOffice Writer with the pdf import extension? It's available here [http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport) and I must state that I HAVE NOT USED IT PERSONALLY so this is a question rather than a recommendation.  I also don't know whether the extra steps of importing and exporting would limit your workflow unacceptably, but perhaps its worth trying?

I have just tried to get this extension working and I cant... I also re-read the description etc and feel that it is probably far too impractical for your use, so I therefore withdraw my posted question.  Apologies!

---

### Post by Vorl the Magnificent on 2009-07-22
Let me second -- or third -- comments concerning pdfedit being useful for light modification of PDFs.

One thing I will say is that if you're going into it expecting an Acrobat-style interface, you'll be disappointed.

My main use for PDF editors is typewriter functionality -- that is, literally typing wherever you like on the page.  Pdfedit provides this, so it works for my purposes.  If you find that the hardest thing you're having to do regularly with PDFs is type some info on some blanks and then print the thing out or print it to a new PDF for mailing off, the combination of pdfedit and evince-viewer should do the trick.

As indicated above, this clearly won't do for the thread parent, who relies on extensive PDF editing for his livelihood.  Like others above, I run Acrobat in an XP vm via virtualbox for this purpose -- and I bet once you get that RAM in, you'll be able to do the same using NitroPDF or Acrobat, as you've said.

Man, I'll tell you what, though -- the Evince viewer is hella good about ignoring lots of the "you can't print me!  I've got a stupid watermark!" functions built into some otherwise useful PDFs.  I'm working as a paralegal right now, too, and I helped our firm's clerk by taking a PDF of a Power of Attorney he needed -- one with a giant "SAMPLE! printed across each unprintable, uncopyable page -- and opening and printing it in Evince, which is in the Debian VM I've conveniently installed my XP work box.  Yeah, I know I defeated a lockdown someone put in the file for a reason -- but it was for a good cause!  I freed some good boilerplate from the Man that day!  (Ironically, of course, it served to benefit the Man.  But hey... the Man's the man who pays me).:D
--VoTMagn

---

### Post by Malcy on 2009-08-02
> **timjohn7 said:**
> Have you tried OpenOffice Writer with the pdf import extension? It's available here [http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport) and I must state that I HAVE NOT USED IT PERSONALLY so this is a question rather than a recommendation.  I also don't know whether the extra steps of importing and exporting would limit your workflow unacceptably, but perhaps its worth trying?

I have just tried to get this extension working and I cant... I also re-read the description etc and feel that it is probably far too impractical for your use, so I therefore withdraw my posted question.  Apologies!

This works really well. You can easily do any editing that you want to a PDF document and then export it as a PDF doc again.

To install, download the correct version from the link above. Right click and choose 'Open with open Office'. Accept the licence terms and complete the install.

To use, 

Start any open Office app, though it will work in Draw, so you may as well use that.

Click on file Open then when the file selection window appears, go to the bottom where it says 'File type'. Click on this and select PDF. Navigate to the location of your acrobat file and select it. 

It will open as a fully editable document. You can save it in any available format or export back to PDF. :P

---

### Post by edcompsci on 2012-08-25
I've had enough with the slowness of pdfedit. Does anyone know if it's any faster on other brands of Linux?


Anyway here's my workaround.

1. Split the pdf into individual pages (burst option of pdfsam works well)
2. Open each individual file separately using gimp, then save them each from gimp as .png files
3. open each individual file using gpaint
4. type in all of your fill-in information (really fast, works great)
5. correct any mistakes by saving where you are, then opening the saved file with rgbpaint, and paint over it in white, then save, close and proceed back to gpaint
6. one it's filled completely out in gpaint, save it, exit gpaint, open the file in image viewer and print it as a pdf.
7. Wala!


Now someday when I'm not feeling lazy I might make this process into a bash script.

---

### Post by aeqel on 2012-12-04
> **edcompsci said:**
> I've had enough with the slowness of pdfedit. Does anyone know if it's any faster on other brands of Linux?


Anyway here's my workaround.

1. Split the pdf into individual pages (burst option of pdfsam works well)
2. Open each individual file separately using gimp, then save them each from gimp as .png files
3. open each individual file using gpaint
4. type in all of your fill-in information (really fast, works great)
5. correct any mistakes by saving where you are, then opening the saved file with rgbpaint, and paint over it in white, then save, close and proceed back to gpaint
6. one it's filled completely out in gpaint, save it, exit gpaint, open the file in image viewer and print it as a pdf.
7. Wala!


Now someday when I'm not feeling lazy I might make this process into a bash script.

Why go past Step 2? You can do all your editing in GIMP with ease! =)
However - I find GIMP for PDF Editing my second choice. I personally find Inkscape is much better at handling PDF's. I personally am unaware of any special features Adobe may have that makes it very special when it comes to PDF editing.

---

### Post by cedric_tux on 2012-12-10
Have you already tried PdfStudio form Qoppa.
For me it's the best alternative for Adobe Acrobat on Linux

---

