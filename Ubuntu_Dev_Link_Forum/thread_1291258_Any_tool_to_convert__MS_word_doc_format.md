---
title: "Any tool to convert  MS word doc format?"
date: 2009-10-14
forum: Ubuntu Dev Link Forum
---

### Post by vksingh on 2009-10-14
Hi,

I have got a assignment to code a tool to convert one format of MS word to another.

Does some similar tool exists in Ubuntu to do the same?:(

Thanks,

Vivek

---

### Post by giuspen on 2009-10-14
you open the document with openoffice, then you just save into the format you want

---

### Post by moe_syzlak on 2009-11-21
You can use macro record in OOo writer to automatically do it. You can even use the OOo APi, UNO.

---

### Post by gradinaruvasile on 2009-11-21
But beware: the M$ formats may(probably will) have formatting differences once loaded/saved from OpenOffice. Its just that OpenOffice's interpretation of them isnt exactly 100% cause the format is essentially reverse engineered. Especially tables suffer from formatting issues.

---

### Post by pmorton on 2010-01-30
This may be a bit late for your assignment, but I was recently looking for something to batch convert docs to odt's and came across this:

[http://leapon.net/en/mso2ooo-batch-convert-microsoft-office-documents-openoffice-documents](http://leapon.net/en/mso2ooo-batch-convert-microsoft-office-documents-openoffice-documents)


It converts docs, xls and ppd files to their respective open document formats for files in nested directories, so you can do an entire drive in one go. It is done in two stages, the second involving a OO Writer macro,so you could easily adapt it to convert to whatever you please.

---

### Post by Hagar Delest on 2010-01-30
> **vksingh said:**
> I have got a assignment to code a tool to convert one format of MS word to another.
Who could have given you this assignment??? Until recently, the .doc format for example was held secret. OOo import/export filters have been made by reverse engineering (imagine the workload!). As for the dirty OOXML (.docx), there are more than 6,000 pages of specification not truly documented and containing some bugs.

---

