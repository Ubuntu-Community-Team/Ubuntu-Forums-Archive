---
title: "Reverse engineering Adobe Acorbat Pro"
date: 2008-10-27
forum: Ubuntu Brainstorm
---

### Post by pallukucchu on 2008-10-27
Hi all!
       I want to know whether there is any open source software which has similar features as Adobe Acrobat Pro. I want to know which open source software is good for editing .pdf files. If there is none, is it possible to reverse engineer the existing Adobe Acrobat Pro software.

Sincerely,
M.

---

### Post by ad_267 on 2008-10-28
Does Acrobat Pro actually let you edit pdf files? I don't think it does. Pdfs aren't like a word document, they can't be edited that easily. PDF is an open standard by the way, so there doesn't need to be any reverse engineering of the file format.

Inkscape can import pdfs and so can OpenOffice 3.0 with the pdf import plugin, although I couldn't get it to install.

---

### Post by qamelian on 2008-10-28
> **ad_267 said:**
> Does Acrobat Pro actually let you edit pdf files? I don't think it does. Pdfs aren't like a word document, they can't be edited that easily. PDF is an open standard by the way, so there doesn't need to be any reverse engineering of the file format.

Yes, it does. Acrobat is the original application for editing and creating PDF files. It also includes a utility that allows other applications to "print" to PDF format. Acrobat reader, on the other hand, only allows reading of PDF files. Although other apps, such as OpenOffice, allow documents to be exported as PDF, Adobe Acrobat is the original PDF editor.

---

### Post by SunnyRabbiera on 2008-10-28
well I know applications like scribus can at least create new PDF's, and possibly edit a few.

---

### Post by panda726 on 2008-10-28
There also exists in the repos a program called PDF Editor.  I've used it a little, but I don't know that it is necessarily all that Acrobat is.  I am under the impression that PDF is largely considered an end of line read only format in the free software world.

Tor

---

### Post by stephantom on 2008-10-28
> **qamelian said:**
> It also includes a utility that allows other applications to "print" to PDF format.
cups-pdf does the same just fine. Granted, I can't do printer optimization with that, but it's good enough for 90% of my requirements.

---

### Post by smartboyathome on 2008-10-28
> **stephantom said:**
> cups-pdf does the same just fine. Granted, I can't do printer optimization with that, but it's good enough for 90% of my requirements.

There is even a "print to file" feature which I found recently in Intrepid (but I think it exists in hardy as well) which does the exact same thing as cups-pdf with the added bonus of allowing to print to ps as well.

---

### Post by ad_267 on 2008-10-28
Oh ok I found this: [http://www.adobe.com/products/acrobat/solutions/detail/edit_pdf.html](http://www.adobe.com/products/acrobat/solutions/detail/edit_pdf.html).

So you can actually make minor changes to a pdf. I still think some people are missing the point though. Pdf isn't designed to be edited. Once you make a pdf file that's supposed to be it. You can create pdfs with OpenOffice or Scribus or Acrobat but the actual pdf file format isn't intended to be an editable format like a word document. Obviously some small edits are possible though.

And yes I realise that you can't create a pdf with Adobe Reader but you can with Adobe Acrobat. What I was talking about was the actual _editing_ of a pdf, which is quite a different thing to just creating a pdf.

OpenOffice is supposed to have a PDF import plugin that should offer the same capabilities, although I can't get it to install. Inkscape also has PDF import capabilities although I don't know how this would work with multiple page documents.

> PDF is largely considered an end of line read only format in the free software world.
- That's not just in the free software world, that's in the whole world.

---

