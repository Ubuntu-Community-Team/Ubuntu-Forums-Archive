---
title: "why can I see a font but not use it?"
date: 2016-02-19
forum: The Cafe
---

### Post by anotherChris on 2016-02-19
This is not exactly a support question... I just want to understand why something works...

If I open a .docx file in LibreOffice that was written in Times New Roman and an MS kanji font, LibreOffice can display these documents even when the fonts are not installed on my computer.  It's just that if I try to manipulate the document by typing in it, I can't insert anything new in these fonts.  I want to know why.

I'm guessing that a .docx file contains information similar to a PDF that tells a word processor how to display the fonts even though they aren't installed in the word processor.  So when LibreOffice shows me a .docx file in Times New Roman and has "*Times New Roman"* listed in the font drop-down menu in italics, it's been told by the .docx document how to display and what the name of the font is, but LibreOffice doesn't really "know" how to display Times New Roman even though it appears to be telling me that's what it's doing.

is this correct?

The other possibility is that Times New Roman is actually bundled with LibreOffice but somehow disabled for writing until ttf-mscore is installed, which "unlocks" the font via the license agreement.  But I suspect this is not correct.

Can anyone explain this quickly in non-technical language?  Thanks.

---

### Post by vasa1 on 2016-02-20
I don't know much about fonts and I don't have to deal with sending docs to others but I came across this which may be somewhat interesting to you: [https://larjona.wordpress.com/2014/05/21/some-experiences-and-todo-about-fonts/](https://larjona.wordpress.com/2014/05/21/some-experiences-and-todo-about-fonts/)

---

### Post by Bucky Ball on 2016-02-20
*Thread moved to **The Cafe**.*

> **anotherChris said:**
> This is not exactly a support question... 

You're also not exactly ***New to Ubuntu*** and that area is a support area. ;)

---

### Post by anotherChris on 2016-02-20
> **Bucky Ball said:**
> You're also not exactly ***New to Ubuntu***

Eh?  I am so new to Ubuntu.  Without the forums, I could barely turn on the power...

---

### Post by Bucky Ball on 2016-02-20
> **anotherChris said:**
> Eh?  I am so new to Ubuntu.  Without the forums, I could barely turn on the power...

Righto. Either way, this is the place for non-tech support stuff (along with ***Ubuntu, Linux and OS Chat***). :)

---

### Post by bapoumba on 2016-02-20
Two things :
- Fonts can be embedded in the document when it is saved ([https://support.microsoft.com/en-us/kb/290952](https://support.microsoft.com/en-us/kb/290952) & LO : File > Properties > Fonts), so someone else opening it can edit using the particular font is was created with. This leads to a heavier file, of course.
- On ubuntu, you can install ubuntu-restricted-extras (or the variation for your flavor : [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)) so that your LO can use the Microsoft fonts.

---

### Post by SeijiSensei on 2016-02-20
It's also possible that the document shows Times New Roman in the box, but it is actually being displayed with a similar font in your set like the default Liberation Serif.

---

### Post by anotherChris on 2016-02-20
> **bapoumba said:**
> Two things :
- Fonts can be embedded in the document when it is saved ([https://support.microsoft.com/en-us/kb/290952](https://support.microsoft.com/en-us/kb/290952) & LO : File > Properties > Fonts), so someone else opening it can edit using the particular font is was created with. This leads to a heavier file, of course.

That's cool.  Maybe I should go back to using Microsoft... *just kidding! *

> **SeijiSensei said:**
> It's also possible that the document shows Times New Roman in the box, but it is actually being displayed with a similar font in your set like the default Liberation Serif.

You know what?  I'm embarassed to say it, but that appears to be the case.  I've just a few moments ago gotten the MS fonts installed correctly and now that LibreOffice has Times New Roman in it, the documents are being displayed differently.  If I highlight everything and switch back and forth between Times New Roman and Liberation Serif, you can see quite clearly that they're different...

So, previously, Times New Roman was displayed in italics as the font name, but the font was actually being replaced by another in the document.  When I was trying to insert text in that situation, however, the text that was being inserted looked different.  So that's a different thing for me to understand, but I'm tired and need to go to bed.

---

