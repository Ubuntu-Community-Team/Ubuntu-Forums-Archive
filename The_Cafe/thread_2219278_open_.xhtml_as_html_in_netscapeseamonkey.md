---
title: "open .xhtml as html in netscape/seamonkey"
date: 2014-04-23
forum: The Cafe
---

### Post by kurja on 2014-04-23
Hey,

would anyone happen to know of a trick that I could use to force netscape composer / seamonkey editor to open files with a .xhtml suffix as normal html files - using windows machines - or do you know of an editor that could do this?

Might sound like a weird thing to do so here's a little background - on an industrial production system, there are html files that are for some obscure reason named as .xhtml and the proprietary software won't read them if it's renamed to .html. Older workstations came with a netscape composer for editing the files, new one came without any editor so I plucked in seamonkey just because it's almost the same so others can use it without having to learn any new tricks. But neither netscape nor seamonkey won't open the .xhtml files properly, they just spit out an xml parser error so to make an edit I have to make a copy of the file, rename it, then edit, rename back, replace the original... and it's, well, not optimal.

I asked this at mozilla forum some time ago but didn't get any suggestions, so, if you got one I want it =)

---

### Post by SeijiSensei on 2014-04-23
According to [this review](http://webdesign.about.com/od/windowshtmleditors/tp/free-windows-editors.htm), [BlueGriffon]("http://www.bluegriffon.org/") supports XHTML editing in Windows.  There's also a Linux version.

By the way, I found this review in seconds by searching for "edit xhtml on windows" in Google. ;)

---

### Post by kurja on 2014-04-23
um yea but I don't want to edit xhtml.

Problem is that I have html files that are *named as xhtml* which they in fact are not and the editors go boink upon encountering these.

---

### Post by SeijiSensei on 2014-04-23
Did you at least try installing that program and seeing what it does?

XHTML files are merely plain text.  You can edit them in a normal editor like gedit or kate or, from the command prompt, nano.  They won't care what the extension is.

Is there something more that you mean by "editing?"

---

### Post by kurja on 2014-04-24
Apart from plain text editing, there's some formatting, simple tables and links and such to handle, nothing too special really.

Gedit / Notepad et al won't care if a file is html or xhtml, but an editor trying to create a wysiwyg preview would, which I believe is the root of the problem.

I admit I didn't try Bluegriffon yet, now that I'm at work I can give it a spin to see if it behaves differently.

---

### Post by kurja on 2014-04-24
Okay, I tried it, as expected being a wysiwyg editor it behaves like netscape/seamonkey - it sees a dot xhtml file and tries to open it as such, and spits out a parser error.

---

### Post by SeijiSensei on 2014-04-24
Maybe there really is a parser error?  Have you run the file through the [Validator application]("http://validator.w3.org/") at the World Wide Web Consortium?

---

### Post by kurja on 2014-04-24
There's going to be parser errors if you try to parse a language as another, html as xml in this case, right? Remember that the files work fine in proprietary browser, and in editors, when renamed as .html instead of xhtml. Parser error comes up when opening them as-they-are, with the .xhtml suffix.

---

