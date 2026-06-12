---
title: "Booklet printing"
date: 2015-02-10
forum: Ubuntu, Linux and OS Chat
---

### Post by Trenien on 2015-02-10
Hi,
like many now, I own a printer that is able to do duplex printing. At the same time, I've learned to love the use of booklets : you both save paper and get documents in a very convenient form. With duplex printers, it really is  extremely nice to do.
Which leads me to my question: I know that software such as acrobat or open/libreoffice can print document in a booklet format. I also know it is possible to use the command line to get the same result in a somewhat more generalized way. However, as far as I know, there is no easy, GUI way to do it for all documents (though I would love to be proved wrong).
I honestly don't understand why this feature hasn't been integrated by default in the standard printing interface.

I'm not sure exactly, but where should I go and make a request of that (read, politely rant) for it to maybe be implented ?

---

### Post by tgalati4 on 2015-02-10
Welcome to the forums.  What type of booklets?  I sometimes make pocket planners using letter size.  Others have turned them into books:  [http://www.instructables.com/id/How-to-make-a-PocketMod-Book/](http://www.instructables.com/id/How-to-make-a-PocketMod-Book/)

There are templates that you can find on the web for all sorts of booklet forms in SVG format for *inkscape* or *scribus*.

Perhaps describe the booklets that you are trying to make.

---

### Post by Trenien on 2015-02-10
Sorry, I thought it was known by everyone.
I call booklet the case when, if you have a multipage document, instead of printing it "as is", you print it in a reduced size (typically 2 A4 pages are reduced to A5 size and fit on a single page) with the order rearranged so that you simply have to grab the loaf of sheets of paper out of the printer (assuming it has duplex capability), fold it in two and you then can simply read it like a book.

to give a concrete exemple, if you assume an 8 pages document. If you simply do a reduced printing (2 pages on 1), with duplex printing, you'll get something like :
>1 2
<3 4
>5 6
<7 8
I use > for the recto and < for the verso
With booklet printing, it'll go like this :
>8 1
<2 7
>6 3
<4 5

Currently, under linux, you can do that in the following ways :
- acrobat with pdf documents
- a few apps can create ready to print pdf from a standard file
- libre/openoffice has the option to print your document as a booklet
- use the command line

And that's pretty much it. It doesn't seem such a tremendous thing to implement (but what do I know), so I just don't understand why it isn't part of the standard printing interface.
But if you have booklet printing,

---

### Post by tgalati4 on 2015-02-11
Yes, there is not much:

> tgalati4@Mint17 ~ $ apt-cache search booklet
psutils - PostScript document handling utilities
texlive-latex-extra - TeX Live: LaTeX additional packages
bookletimposer - PDF imposition toolkit
dvidvi - Manipulate .dvi files
fonts-levien-museum - metal Centaur fonts revival family
impose+ - Postscript utilities for two-up printing, bbox, etc


I'm not familiar with *impose+* but PDF imposition is really what you are trying to do.  Take single PDF pages and order them in such a way that they form a leaf (collection of single, folded pages) which can then be bound in a book.  Playing with *impose*, it is a commandline utility for creating 2-up booklets.

```
sudo apt-get install impose+
impose -help
```

To my knowledge, there is not a commercial package like [AxpertSoft PDF Creator]("http://download.cnet.com/AxpertSoft-PDF-Booklet-Creator/3000-18497_4-75911276.html") in Linux to create 2-up, PDF-imposed, booklets.

Here's an old [link]("http://www.makeuseof.com/tag/3-ways-to-create-physical-booklets-with-a-mac/") with some tips for Mac users and some online PDF imposers.  Don't know if they still work.

---

### Post by Mike_Walsh on 2015-02-11
Without a shadow of doubt, Scribus ought to do what you want. It has the capability for booklet printing, amongst many other possibilities; I use it myself.

It is available through the Software Centre. Just type scribus into the search box.


Regards,

Mike.

---

### Post by Trenien on 2015-02-11
I fear I haven't made myself clear.
I am perfectly aware of many of the possibilities there are to be able to print booklets.

BUT

Except for a couple of exceptions - within specific software - you always need to go through some conversion step, using a third party software.
What I hope for is to have the option of printing booklets integrated in the system general printing utility so that the same way you can choose to have any number of pages automatically reduced and printed on one, you could choose to have your document printed as a booklet.
Considering the aforementionned existing option, I may be wrong but it doesn't seem to me it is so difficult to implement : it only is a matter of reorganising the pages order before reduction. Had I any coding capacity, I probably would try to do it myself.

Considering this, I can only imagine that if the option doesn't exist it is because nobody really gave it a thought, which is why I've started this thread.

---

### Post by tgalati4 on 2015-02-11
LibreOffice developement would be the place for a feature request.

There is a way to do it with LibreOffice:  [https://help.libreoffice.org/Writer/Printing_a_Brochure](https://help.libreoffice.org/Writer/Printing_a_Brochure)

Another method:  [https://help.gnome.org/users/gnome-help/stable/printing-booklet-duplex.html.en](https://help.gnome.org/users/gnome-help/stable/printing-booklet-duplex.html.en)

And one more:  [http://ask.libreoffice.org/en/question/13789/pagination-for-a-2-up-folio-bound-book/](http://ask.libreoffice.org/en/question/13789/pagination-for-a-2-up-folio-bound-book/)

It's not a "one-button operation", but it is possible to do.

I use *scribus* because many times making a special, folded form with a specific duplex printer requires small adjustments to get the correct registration.  If you simply want to print a text book using LibreOffice, then you need to go through the manual page-numbering routine--which, for a large book, is quite tedious.

---

### Post by Trenien on 2015-02-11
Actually, it already exists within the printing options of libreoffice.

---

### Post by nicolas.bernaerts on 2015-11-05
I had this same need of printing a booklet from my Ubuntu workstation. 

But the source documents were not always produced from LibreOffice, I also had to print booklets from some A4 PDF files.  

As I didn't find a complete answer to my need, I've developed a small imposition script (booklet generation) compatible with PDF, LibreOffice and Ms-Office source documents. To simplify user experience, I've integrated the script launch directly from Nautilus file manager (as a Nautilus action, thru a right click menu on any compatible file).  

All explanations, scripts and configuration files are available from [http://bernaerts.dyndns.org/linux/74-ubuntu/248-ubuntu-imposition-print-book](http://bernaerts.dyndns.org/linux/74-ubuntu/248-ubuntu-imposition-print-book)  

Hope it helps.

---

### Post by tgalati4 on 2015-11-05
This is quite nice.  Thanks for sharing.  I sent a PM to the OP with your link.

---

