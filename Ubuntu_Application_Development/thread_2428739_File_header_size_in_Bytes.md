---
title: "File header size in Bytes"
date: 2019-10-08
forum: Ubuntu Application Development
---

### Post by zak100 on 2019-10-08
Hi,
I need to know the file header size of various document type files like pdf, MS-word, Libre Office and any document type file format. I got a list of file format at wikipedia [URL="https://en.wikipedia.org/wiki/File_format"]https://en.wikipedia.org/wiki/File_format
[/URL]but I 
can't see information about the header size. For instance, I know the header size of bmp file=54 byts.Can some body please guide me any link which tells me this information.

Zulfi.

---

### Post by Skaperen on 2019-10-08
not all file types even have headers. many others vary in size.  g/l

---

### Post by TheFu on 2019-10-08
> **Skaperen said:**
> not all file types even have headers. many others vary in size.  g/l

+1. Exactly this.  You can look at the "file" utility source code for how other projects do it.
```
$ file /etc/hosts
/etc/hosts: ASCII text

$ file /bin/bash 
/bin/bash: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, 
interpreter /lib64/l, for GNU/Linux 2.6.32, BuildID[sha1]=6f072e70e3e49380ff4d43cdde8178c24cf73daa, 
stripped
```

And sometimes the header isn't only at the beginning of the file. There are multiple headers throughout some files.

---

### Post by zak100 on 2019-10-08
Hi,

Thanks.

I tried the following :

$ info utility/function/LibreOfficeWriter
info: ./utility/function/LibreOfficeWriter: No such file or directory

Sorry I can't understand how to use the file utility to extract the header of a LibreOfficeWriter file or a pdf file.Please guide me.

Zulfi.

---

### Post by zak100 on 2019-10-08
Hi,
I found a link related to file but none of the examples show the retrieval of header bytes:

[https://en.wikipedia.org/wiki/File_%28command%29](https://en.wikipedia.org/wiki/File_%28command%29)

Somebody please provide me some example for retrieving header for libreOffice and pdf files.

Zulfi.

---

### Post by TheFu on 2019-10-08
I hate to say this, but if you are having trouble with what I've shown already, then you are much too new to accomplish what you want, especially for binary, compressed, files like LibreOffice and PDF use.

Start here to get your Linux-Fu strengthened: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  

Get the source code for the GNU 'file' utility. Read that.  It is C code and full of the sort of example code you'd need to understand and write.

BTW, why would you use 'info'?  That tool is for something completely different.  I showed **exactly** how to use 'file'.

---

### Post by zak100 on 2019-10-08
Hi,

I used on .odt but got following information:

$ file 'prob in timing.odt'
prob in timing.odt: OpenDocument Text

No information in terms of bytes.

Zulfi.

---

### Post by Skaperen on 2019-10-08
the program/command named [COLOR=#0000cd][FONT=courier new]**file**[/FONT][/COLOR] is not designed to provide details about a file that cannot be seriously used.  if the file type has a fixed size header, how does that help anything?  the concept of having a header can be very complex.  many file types can have a series of sections that vary in size an include something you might call a "section header".  what follows is often little subsections.  and all of this, including all the headers, might be compressed by a specific algorithm.

a file format like BMP or WAV is simplistic compared to very "rich" formats like ODT, PDF, XLC or even Microsoft Word.  the concept of a header just doesn't apply.

maybe we could explain this better for you if we knew what you are trying to accomplish.

---

### Post by Skaperen on 2019-10-08
a text file has no header.  a file that has just printable ASCII characters in the first several bytes that [COLOR=#0000cd][FONT=courier new]**file**[/FONT][/COLOR] tries to read, is guessed to be a text file.  i could fool it by making a file with the first million bytes being text followed by a compressed binary dump of a database of documents.  but what would that accomplish?  it wouldn't help anything.

---

### Post by TheFu on 2019-10-08
> **zak100 said:**
> Hi,

I used on .odt but got following information:

$ file 'prob in timing.odt'
prob in timing.odt: OpenDocument Text

No information in terms of bytes.

Zulfi.
 
 Nothing exists to do what you have requested that I've heard about.  I assumed you intended to code something, because that is the only solution.  The 'file' utility will have very similar code to what you need to write. That is the entire reason I pointed it out.   

This sounds like a homework assignment for a programming class.

---

### Post by spjackson on 2019-10-09
As has been said, unlike .bmp files, many file formats do not specify any "header" data.

All of the major current LibreOffice native formats are zip archives (.odt, .ods etc.). All of the major current Microsoft Office native formats are also zip archives (.docx, .xlsx, .pptx etc.) but not the old ones (.doc, .xls, .ppt etc.).

A zip archive begins with the header of the first file contained within the archive. This is not a header for the archive itself and it is varying length (30 + X + Y bytes where X and Y are 2 lengths specified in the first 30 bytes). The interesting part, if you like, is the Central Directory which is located at the end of the archive and is also of varying size.

For a .pdf file, all you are guaranteed up front is %PDF followed by a (varying length) version number. Similar to a zip archive, the Trailer Dictionary will be found at the end of the file, before the %%EOF. The Trailer Dictionary tells you, among other things, where to find the xref (cross reference) table, which will often be just before the trailer but need not be.

---

### Post by Skaperen on 2019-10-10
if you want to get information from a file, you will need more information than just the size of the header.  you will need to know where it puts the information want.  maybe you want to collect the frequency count for each letter and word in the document.  to do something like that, you will need to know a lot more than what byte offset you need to get past the header.  you'll need to know how to uncompress it.  you will also need to know how it interleaves the formatting and positioning of the letters and words.

i cannot imagine any end goal that only needs to know the size of the header than can work for more than a small handful of file types.

---

