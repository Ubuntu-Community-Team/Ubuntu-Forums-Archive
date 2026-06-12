---
title: "LibreOffice &lt;-&gt; MSFT Office 2010"
date: 2013-01-16
forum: The Cafe
---

### Post by mike acker on 2013-01-16
[LIST]
[*]has anyone any experience in transferring LibreOffice documents to Windows Office 2010 users ?
[*]msft complains the LibreOffice document is 'corrupt' . it offers to 'recover' the document but does a crappy job
[*]all of the formulas in our .ods document were replaced with 'values only'
[/LIST]

---

### Post by drawkcab on 2013-01-16
> **mike acker said:**
> [LIST]
[*]has anyone any experience in transferring LibreOffice documents to Windows Office 2010 users ?
[*]msft complains the LibreOffice document is 'corrupt' . it offers to 'recover' the document but does a crappy job
[*]all of the formulas in our .ods document were replaced with 'values only'
[/LIST]

Can't you save the document in a microsoft format with Open Office?  My guess is that MS does this on purpose so don't look to them for compatibility solutions.

---

### Post by bootedguy on 2013-01-16
Upload the odt file to Google Drive, and then download as DOCX. Google seems to have done a pretty good job of reverse engineering the DOCX format.

---

### Post by sidzen on 2013-01-17
Thanx for the workaround info, bootedguy!  
I was importing Libre Office into abiword and exporting as a PDF in order to get that damned M$ Word to read my docs.

---

### Post by mike acker on 2013-01-17
> **sidzen said:**
> Thanx for the workaround info, bootedguy! 
I was importing Libre Office into abiword and exporting as a PDF in order to get that damned M$ Word to read my docs.

yep

experiments this morning indicate that when i
 
[LIST]
[*]save document as odt or docx in     Linux and then
[*]attempt to read document in     windows:
[/LIST]
 
[LIST=1]
[*]using LibreOffice: OK
[*]using MSFT/Office results in an error: MSFT/Office fails
[/LIST]
 however
 
[LIST]
[*]after reading the .odt in Windows/LibreOffice and then
[*]re-saving as either .docx or .doc --
[*]MSFT/Office recovers good approximation of original without     printing an error message
[/LIST]
 Conclusion: my experience with Linux/Windows transfers indicates the trouble is often in Windows use of CR LF rather than simple LF as 'end of line ' mark . I'd bet the problem in moving .odt ( or .ods ) from Linux to MSFT/Office 2010 has its roots in this AGE OLD issue
~~~
Amendment 1
Note to LibreOffice: when you are directed to "save as .docx or as .doc your output file should be acceptable to MSFT. If you have to write in DOS format to do it,--- get 'er done .

---

### Post by forrestcupp on 2013-01-17
Just an addition. When saving from LibreOffice to a Microsoft format, *always* use doc and not docx. LibreOffice does a great job saving docs, but their docx support is worse than dismal. It does a good job of *opening* docx files that were saved from MSO, but it does a horrible job of *saving* them.

---

