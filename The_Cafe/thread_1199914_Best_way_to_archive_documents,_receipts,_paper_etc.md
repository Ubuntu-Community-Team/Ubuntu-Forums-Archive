---
title: "Best way to archive documents, receipts, paper etc."
date: 2009-06-29
forum: The Cafe
---

### Post by dhughes on 2009-06-29
I have tons of paper sitting around that bug me, things I should keep like tax related paperwork and vehicle repair receipts I have to keep for warranty reasons (I probably have to keep the originals and not scan them).

 In the past I have scanned and converted them to pdf for lack of an alternative, I guess it's a good choice but I'd rather use a non-proprietary format that isn't at risk of disappearing in ten years. It was tedious to scan anything I may have overlooked such as pay stubs, after 100 it gets boring and no I don't have a document feeder on my scanner.

 Saving as a png or jpg is an option too but is it wise due to the possible degradation due to compression? I may be able to lower the file size but having the document legible is more important that its file size.

 Searching is also a big problem, with images I can't search the document only the file name. I assume the contents of a pdf can be searched but I've never tried it.

 Are any of you saving documents in an efficient way?

---

### Post by .Maleficus. on 2009-06-29
PNG is lossless image compression.  JPEG is quite lossy so that probably wouldn't be a good choice.  I would say that for images, the best way to store them would just be a descriptive directory structure.  Windows 7 has a way of tagging images so you can search your system for the keyword and find all of the images tagged with it.  Maybe a program for Linux will pop up with that feature.  Otherwise, don't know.

---

### Post by NightwishFan on 2009-06-29
PDF or PNG would be excellent. If you want to save physical drive space, you can compress similar files in a .tar.lzma file. PDF gets compressed excellently using gz/bz2/lzma (I use lzma).

For example:

You have a folder for all of your warranty.

Compress that folder to .tar.lzma

To add more, just uncompress, add, then recompress.


EDIT: I think if you used individual .gz, you can still search your pdfs. Someone may be able to confirm this. As Nautilus can preview .pdf.gz but not lzma. (Lzma just compresses more)

---

### Post by koenn on 2009-06-29
> **dhughes said:**
> I have tons of paper sitting around that bug me, things I should keep like tax related paperwork and vehicle repair receipts I have to keep for warranty reasons (I probably have to keep the originals and not scan them).

 In the past I have scanned and converted them to pdf for lack of an alternative, I guess it's a good choice but I'd rather use a non-proprietary format that isn't at risk of disappearing in ten years. It was tedious to scan anything I may have overlooked such as pay stubs, after 100 it gets boring and no I don't have a document feeder on my scanner.

 Saving as a png or jpg is an option too but is it wise due to the possible degradation due to compression? I may be able to lower the file size but having the document legible is more important that its file size.

 Searching is also a big problem, with images I can't search the document only the file name. I assume the contents of a pdf can be searched but I've never tried it.

 Are any of you saving documents in an efficient way?

PDF/A is an open standaard pdf format specifically suited for archiving - [http://en.wikipedia.org/wiki/PDF/A](http://en.wikipedia.org/wiki/PDF/A)

you *will* need to scan anything that's delivered on paper, so you do want a scanner with feeder, or some model that allows you to easily feed  the originals in to it (eg a handheld scanner etc)

If you want to go all the way, you'll store your pdf/a files in a content management system so you can tag and index them. 

pdf is searcheable, at least the ones generetd by a computer program. Scans may just be images so uou might be unable to get the text out of it, unless you have an OCR program.

Here's a poor man's text search in a pdf :
```

k@nix:~$ pdftohtml the_c_book.pdf -stdout |grep "Functions"

&quot; 1.2. Functions [<i>http://publications.gbdirect.co.uk/c_book/chapter1/functions.html</i>]<br>
! Chapter 4. Functions [<i>http://publications.gbdirect.co.uk/c_book/chapter4/</i>] <br>
! 1.2. Functions [<i>http://publications.gbdirect.co.uk/c_book/chapter1/functions.html</i>] <br>
<A name=21></a>The C Book — Functions<br>
<b>1.2. Functions </b><br>
Functions are C's equivalents of the functions and subroutines in FORTRAN, <br>functions and procedures in Pascal and ALGOL. Neither BASIC in most of its <br>simple mutations, nor COBOL has much like C's functions. <br>
<A name=22></a>The C Book — Functions<br>
This chapter has introduced many of the basics of the language although informally. <br>Functions, in particular, form the basic building block for C. Chapter 4 <br>[<i>http://publications.gbdirect.co.uk/c_book/chapter4/</i>] provides a full description of <br>these fundamental objects, but you should by now understand enough about them <br>to follow their informal use in the intervening material. <br>



```

---

### Post by t0p on 2009-06-29
Do you use p2p software like gnutella?  If so, be careful - the pauldotcom crew have [showed how dangerous it can be to store sensitive documents on your computer]("http://pauldotcom.com/2009/06/information-disclosure-via-p2p.html").

> In this first round of research, using readily available software, they focused on the acquisition of personal information one could use to perpetrate fraud. They were able to acquire high resolution images of social security cards, passports, visitation visas, tax returns, retirement planning forms, and drivers licenses. In one instance, they were able to uncover personal data on an former Iraqi national who fled to the US fearing retribution for themselves and their family for assisting the US lead coalition forces.
Their findings are illustrated by [this lovely .pdf document]("http://pauldotcom.com/P2PInformationDisclosure.pdf").  And you can get the audio of their presentation [here]("http://pauldotcom.com/2009/06/pauldotcom-security-weekly---e-12.html").

Of course, if you don't do p2p - or if you know how to do permissions 'n' stuff - you are safe.  But if not... Moo-ha-ha-ha!! :evil:

---

### Post by dhughes on 2009-06-29
Thanks for the tips.

 One thing I just noticed when I did a test scan with xsane, I used the save as a pdf option but really it's just an image not what I would call a pdf, you can't search text in the pdf file using Find. If you can't search the document to me that's not really a true pdf it's just an image which is no use to me.

 I guess I'll stick with pdf and as always be careful of my security and probably compress the life out of directories to get as much space as possible even though it's going on two 1TB external drives powered off when not in use. Maybe not too much as mentioned to retain search-ability since search is extremely important when dealing with archived documents, otherwise it's pointless. Although maybe not being able to search is a good security feature if I choose to send a compressed archive to a storage service such as DropBox or UbuntuOne.

 I'm sure more people need to do this, I'll keep looking maybe something is already made or some steps, a procedure is out there somewhere that makes this easier.

 I wish I could get a document feeder and I'll have to look into scripting so it can auto-name scanned documents fast instead of by hand.

 The quest continues!

---

### Post by Firestem4 on 2009-06-29
one intended point of a PDF file rather than other formats is intended to be non-editable. 

And, if you are paranoid you can encrypt your files/folders. I use bcrypt which is a very easy command-line based program using the Blowfish algorithm. (The encryption standard is very strong if you use a strong key.)

TrueCrypt can encrypt entire volumes using various encryptions methods. AES256 (Rijndael and other variations) Blowfish, etc.

---

### Post by mikewhatever on 2009-06-29
> **dhughes said:**
> ...

 One thing I just noticed when I did a test scan with xsane, I used the save as a pdf option but really it's just an image not what I would call a pdf, you can't search text in the pdf file using Find. If you can't search the document to me that's not really a true pdf it's just an image which is no use to me.
...

I was just gonna mention that. There is also no point in archiving for the very same reason, you'll just be wasting time and CPU cycles. If you are concerned about security, use an encrypted folder or partition.

I used to work for a company that launched a project of converting all its important documents into a searchable database. They scanned the documentes into pdf and then used OCR software to create searchable html files. Some of the documents were rather old and badly printed, and therefore turned out a mess in ORC, but that didn't really matter, because they only needed the keywords to be searchable. Anyway, it's a lot of tedious work and probably isn't an option for you.

---

### Post by Sublime Porte on 2009-06-29
> In the past I have scanned and converted them to pdf for lack of an alternative, I guess it's a good choice but I'd rather use a non-proprietary format that isn't at risk of disappearing in ten years.

PDF is no longer proprietary.

[quote=Wikipedia:PDF]Formerly a [proprietary format]("http://en.wikipedia.org/wiki/Proprietary_format"), PDF was officially released as an [open standard]("http://en.wikipedia.org/wiki/Open_standard") on July 1, 2008, and published by the [International Organization for Standardization]("http://en.wikipedia.org/wiki/International_Organization_for_Standardization") as ISO 32000-1:2008[/quote]

> One thing I just noticed when I did a test scan with xsane, I used the save as a pdf option but really it's just an image not what I would call a pdf, you can't search text in the pdf file using Find. If you can't search the document to me that's not really a true pdf it's just an image which is no use to me.

It's a real PDF, you just mean you want to run it through OCR before you save it, so it's converted into proper text. Search in Synaptic for "ocr", sure you'll find quite a few packages in there. However, I'd advise still keeping a copy of the document as an image, because the text alone would not be considered a genuine copy of the original document, as anyone could type up whatever text they liked.

---

### Post by m83 on 2009-06-30
For document organization and to help you search between them you may find useful a document management solution like [Knowledge Tree]("http://www.knowledgetree.com").

---

### Post by Gizenshya on 2009-06-30
I've done this before.

A tradition scanner will take AGES to do it!

it is worth your time to contact local libraries to find a device that is specifically made to scan images into files.

Our university library has a "KIC" station (just like the one attached).  You can scan in hundreds of documents per hour-- I know, because I've done it! lol  You can save them in individual images or pdf files, or all in one big pdf file.  And then save them to a USB drive or email them.  Amazing machines.  and VERY fast :)  just a couple seconds per document.  This will save TONS of time and effort, and I very, VERY strongly recommend finding one! (or something similar at a library near you).

And if you want searchable documents (database) you need some sort of OCR software that does batch commands.

If you want some examples of KIC station files, pm me an email and I'll type up a test page, print it, scan it and email it to you fromthe KIC station in some different formats.

---

### Post by papangul on 2009-06-30
'DJVU' is better option than pdf, atleast for this purpose.
[http://djvu.org/resources/djvu_digital_vs_super_hero_pdf.php](http://djvu.org/resources/djvu_digital_vs_super_hero_pdf.php)
[http://www.print-driver.com/news/pdf-vs-djvu-i1909.html](http://www.print-driver.com/news/pdf-vs-djvu-i1909.html)

---

### Post by koenn on 2009-07-01
[QUOTE=papangul;7543083]'DJVU' is better option than pdf, atleast for this purpose.

never heard of this before, so that's interesting, but in light of the OP's questions 


- "I'd rather use a non-proprietary format" ; i don't see any info on this in the links you gave, I'm assuming djvu is a proprietary format
- DJVU looks like it's intended to be used on digitally created documents, not scans. The OP is about scanning. 

so why exactly do you think djvu is the better option for the OP's purpose ?

---

### Post by papangul on 2009-07-01
The following answers both your questions:
[http://djvu.org/resources/whatisdjvu.php](http://djvu.org/resources/whatisdjvu.php)
I have a manual of a samsung monitor in djvu format and it opens in evince.

Procedure for creating djvu files:
[http://commons.wikimedia.org/wiki/Help:Creating_a_DjVu_file](http://commons.wikimedia.org/wiki/Help:Creating_a_DjVu_file)

The following links are even better:
[http://en.wikipedia.org/wiki/DjVu](http://en.wikipedia.org/wiki/DjVu)
[http://www.howtoforge.com/creating_djvu_documents_on_linux](http://www.howtoforge.com/creating_djvu_documents_on_linux)

---

### Post by rpineger on 2009-11-07
OK. What I was looking for was a way of automatically Scan -> PDF-with-OCR in one step. All the advice here is great but exactly _how_ do we do that? This is standard functionality for Adobe Acrobat software. Is there a FLOSS equivalent? 

I know that KnowlegdeTree used to have an interface that used TOCR(?) in the background to covert scans and insert the text in the PDF but I'm strictly small-time. I just want to keep my letters somewhere but not in a full-blown DMS (they get too big too quickly and controlling size is not easy).

Any ideas?

---

