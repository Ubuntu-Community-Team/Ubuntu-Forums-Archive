---
title: "Need help with a PDF note-taking software"
date: 2009-06-08
forum: Wine
---

### Post by ishtob on 2009-06-08
I'm a college student using a tablet to take notes in class (currently using Xournal for the job, but the highlighter covers over the text and makes it not very useful). I saw my classmate use a program called "PDF Annotator 2" to take notes, and saw that it is a pretty awesome note-taking software. It allows for writing with the pen, and also highlighting text. It also has a full screen mode which make it extremely useful for a tablet.

I tried to install it in Linux but it just freezes up.

this is the meessege i get from terminal:
```
$ env WINEPREFIX="/home/andy/.wine" wine "C:\Program Files\PDF Annotator\PDFAnnotator.exe"
fixme:reg:GetNativeSystemInfo (0x32fb94) using GetSystemInfo()
fixme:atl:AtlModuleInit SEMI-STUB (0x49b97000 0x49b97ae8 0x49a90000)
err:ole:CoWaitForMultipleHandles Unexpected wait termination: 192, 0
fixme:msvideo:DrawDibRealize (0x1, 0x64f0, 0), stub
fixme:gdiplus:GdipCreateHBITMAPFromBitmap stub
fixme:gdiplus:GdipCreateHBITMAPFromBitmap stub
err:seh:setup_exception_record stack overflow 1556 bytes in thread 0019 eip 7bc3c3de esp 03240d1c stack 0x3240000-0x3241000-0x3340000
```

I'm not sure what I am missing since im still new to linux and learning, can anyone help?

I am currently running:
Kubuntu 9.04
Wine version 1.1.22
on a HP TC1100

-----
cross-posted: [here]("http://ubuntuforums.org/showthread.php?t=1171698")

---

### Post by NFblaze on 2009-06-08
Well, if your saying that you work with PDF documents and that you need to make alot of annotations on it. Then I'd suggest Okular which KDE based but it runs on Gnome. It allows for you to highlight(appropirately). Actually place a virtual sticky note on the document, write a comments, underline with a black line, draw polygons, and write with a green marker. Its not fully customizable tho, but its pretty good I suggest you try it out.

---

### Post by ishtob on 2009-06-08
I have KDE and tried okular, it's not what I want from a note-taking software. I am running Kubuntu on a tablet, and I feel like okular is more geared towards a Keyboard-mouse computer. PDF annotator allows you to write on the PDF file as if it's a sheet of paper, which is much more friendly for a tablet.

---

### Post by NFblaze on 2009-06-08
Perhaps, you can take a look at this [http://code.google.com/p/whyteboard/wiki/Screenshots](http://code.google.com/p/whyteboard/wiki/Screenshots)

Sorry, unfortunately I dont use Wine. So I have no other suggestions.

---

### Post by PGScooter on 2009-07-09
Xournal allows you to write on it like a piece of paper. It is for Gnome.

---

### Post by ishtob on 2009-07-09
like i said b4 i am using xournal at the moment, but the highlighter is not very good, it makes the highlighted stuff hard to see, that is why I am trying to get annotator to work

---

### Post by PGScooter on 2009-07-17
mendeley is awesome! They are developing it very rapidly. I would use it just for pdf note taking-- it has a highlighter tool, note making, full screen mode. The highlighting and notes are exportable, but the highlighting covered up the text when I tried to read the pdf in Adobe Reader and Evince. Xournal and Xpdf correctly displayed the highlighting so imagine it will be fixed in evince soon (I posted a bug report). The note shows up perfectly when read in the only reader that I know supports notes, adobe reader.

I would definitely recommend mendeley. But keep in mind that it is not open source. They do seem to have great support for linux and good response to user input.

---

### Post by ishtob on 2009-07-18
hmm.. i'll look into that too, does it work with a tablet? like hand writing and marking notes?

---

### Post by PGScooter on 2009-07-18
As of yet no. But it's developing so fast that I'm guessing they will put that in. You should just ask them.

---

