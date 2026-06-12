---
title: "How Evince and Adobe Reader for Linux both suck"
date: 2009-10-30
forum: The Cafe
---

### Post by azangru on 2009-10-30
Yes, they do. Each in its way, though, which amazed me so much that I came to gripe here.

I have this huge .pdf document and it contains about 1500 pages and weighs over 300 MB. Evince is painfully slow with navigating it - it takes about a minute to show a new page. Adobe Reader 9 is several times faster, but, for some reason, the way it shows the pages is awful. I believe it oversharpens them somehow. The result (it's a Russian text, so don't be surprized if it looks strange) is shown below: on the left is how Evince shows a page, and on the right is how the same page is shown by Adobe Reader.

[IMG]http://lh4.ggpht.com/_9XY75hL8Ero/Suq2Trnbc_I/AAAAAAAAATo/fTP4Gl4odSE/s800/Page.jpg[/IMG]

As a result, both programs are unusable for me: Evince gives readable pages, but at a cost of speed; Adobe Reader is reasonably fast (though nowhere as fast as Acrobat Reader on Windows), but makes the text unreadable.

And to think that on Windows everything works fine, and Acrobat shows pages of the same quality as Evince does, but a hundred times faster. Damn!!!

---

### Post by koleoptero on 2009-10-30
Have you tried epdfview in linux and foxit in windows?

---

### Post by azangru on 2009-10-30
> **koleoptero said:**
> Have you tried epdfview in linux

No, not yet. Is it fast?

---

### Post by koleoptero on 2009-10-30
It's faster. How much you'll have to discover by yourself I'm afraid.

---

### Post by papangul on 2009-10-30
There is a version of foxit for linux also:
[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)

---

### Post by LookTJ on 2009-10-30
I find Adobe to be slower than any of the PDF viewers I've tried. Evince loads fast and simple for me. Foxit is stable, but not near as fast as Evince was at loading PDFs. epdfview is okay, also it is very quick, faster than the ones mentioned.

Good luck on your journey of PDF viewer.

---

### Post by azangru on 2009-10-30
There must be something wrong about this pdf, because, if anything, epdfviewer performed even worse than Evince on it. Foxit, on the other hand, managed to combine Adobe Reader's speed and Evince's quality, and although it's stil about ten times slower than Acrobat on Windows, it's workable. Thanks for suggesting it!

---

### Post by LookTJ on 2009-10-30
Oh and don't forget about xpdf.

But if Foxit is working fine as is, just leave it at that :).

---

### Post by 3rdalbum on 2009-10-30
I don't really know why someone would scan in 1500 pages of text as an image and just chuck it into a PDF file. That's a complete perversion of PDF. They should use OCR (assuming it exists for Russian) or just provide it as a set of images without the PDF wrapping.

---

### Post by Dragonbite on 2009-10-30
For KDE (4) there is Okular which is not too bad, but I haven't fooled around with it very much.

I too wish PDF readers were faster with good quality. I hate the idea of installing Adobe's official reader, but like you mentioned Evince is a pain to go through large documents.

---

### Post by pwnst*r on 2009-10-30
adobe is slowest, for sure, but it works.

---

### Post by orlox on 2009-10-30
I have many scanned books, but in djvu format. Scanned pdf books waste too much space, and render very slow. Perhaps you could try pdf2djvu to transform the file to djvu format. I've never tried it before (and considering the size of your file it should take a while), but I think it could help you.

---

### Post by infestor on 2009-10-30
> **Dragonbite said:**
> For KDE (4) there is Okular which is not too bad, but I haven't fooled around with it very much.

I too wish PDF readers were faster with good quality. I hate the idea of installing Adobe's official reader, but like you mentioned Evince is a pain to go through large documents.

evince is pain in the *** when it comes to large pdfs...takes ages to display a page...xpdf is way faster than evince

---

### Post by sayyidhassan on 2009-10-30
Okular is the best.you can even highlight the text,bookmark sections and change the background colour.all in all it has an option for setting the kind of response you want from it (depending on the RAM and CPU).give it a try

---

### Post by NightwishFan on 2009-10-30
Evince uses Poppler, which I think uses Cairo. It is very fast on my accelerated Nvidia hardware. I have found the new Okular to be very close in performance, but the fonts and images are slightly grainy on my machine.

---

### Post by Xbehave on 2009-10-30
> **NightwishFan said:**
> Evince uses Poppler, which I think uses Cairo. It is very fast on my accelerated Nvidia hardware. I have found the new Okular to be very close in performance, but the fonts and images are slightly grainy on my machine.
okular also uses poppler. In my experience poppler & xpdf based readers are good for text but slow on image based pdfs. Switching around between pdf readers will not help much (excluding foxit/adobe), however playing with your settings might (increase/decrease cache settings, changing backend* etc)

*This may be easiest to do by switching app, poppler has 3 backends:
cairo - standard
splash -missing features but does some bitmap stuff
qt4 - unofficial but stable

I believe that pdf is the wrong format for the file and if you converted it to a djvu you would get much better performance using a djvu reader.

---

### Post by azangru on 2009-10-30
> **3rdalbum said:**
> I don't really know why someone would scan in 1500 pages of text as an image and just chuck it into a PDF file. That's a complete perversion of PDF. They should use OCR (assuming it exists for Russian) or just provide it as a set of images without the PDF wrapping.

The answer to that is simple: PDFs and DJVUs that consist of scanned images offer the greatest fidelity to the original source. In my case, it's an 18th-century Russian book, which can't be OCRed because in those times the Russians had a somewhat different alphabet, and because the scanned copy is of a rather poor quality.

Besides, every OCRed book needs to be proofread; otherwise it'll be full of errors. I've seen so many such books with imperfectly recognized text that I wished people would just stop using OCR at all. Either that or proofread every single page of every single book.

As for the set of images, you are right, of course; but a single wrapping, be it PDF, DJVU or something else, makes the book so less cumbersome and so easier to handle. In the ideal world, I mean, when PDF readers are not easily overwhelmed by the size of the resultant file.

Actually, set of images is what I finally chose to make: I'm converting this PDF to 1500 JPEGs :p Regretfully, this again proved to be done easier in Windows: I first tried imagemagick in Linux, but that was too tiring and slow, so I used Acrobat Professional on a Windows machine. It's so frustrating to realize how much I still depend on Windows :(

> **orlox said:**
> I have many scanned books, but in djvu format. Scanned pdf books waste too much space, and render very slow. Perhaps you could try pdf2djvu to transform the file to djvu format. I've never tried it before (and considering the size of your file it should take a while), but I think it could help you.

Thanks for the suggestion; I'll try to play with pdf2djvu too.

---

