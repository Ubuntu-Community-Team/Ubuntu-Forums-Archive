---
title: "PDF Form filler"
date: 2007-08-17
forum: The Cafe
---

### Post by bluefightingcat on 2007-08-17
Hi,

I need a pdf programme that is capable of allowing for forms to be filled in. I have been looking around and I haven't really found anything. Currenly I have KPDF (XPDF) installed. But this only allows me to view the pdf it doesn't allow me to fill in the fields. 

And whilst we're at it can you recommend the best pdf maker programme to convert document files to pdfs?

Any suggestions would be much appreciated. 

BFC

---

### Post by Biochem on 2007-08-17
I think Acrobat reader will do the trick if the pdf is already formated as a form
sudo apt-get install acroread

There is also pdfedit. It will let you format the pdf but is more complicated. And it is not in the repo

---

### Post by stmiller on 2007-08-17
Yep install acrobat *and* the acrobat plugins package to be able to fill in forms.

---

### Post by aysiu on 2007-08-17
Here are specific instructions:

**Step 1**
[Add the Medibuntu repositories](http://www.medibuntu.org/repository.php) if you haven't already.

**Step 2**
Update your repositories list by pasting this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
```

**Step 3**
Install Adobe Reader and plugins by pasting this command in the terminal: ```
sudo apt-get install acroread acroread-plugins
``` Adobe Reader should show up in your menu. If not, you can start it by pressing Alt-F2 and typing ```
acroread
```

---

### Post by raggari on 2007-08-17
Evince 0.9.2 should also include form support
[http://svn.gnome.org/viewcvs/evince/trunk/NEWS?revision=2601&view=markup](http://svn.gnome.org/viewcvs/evince/trunk/NEWS?revision=2601&view=markup)
It's only available for gutsy so that's not real option for "normal" user before october.

---

### Post by Mary2day on 2008-06-09
You can always try [www.PDFfiller.com](www.PDFfiller.com). It works.

---

### Post by drbcladd on 2008-08-11
Let us not forget that the website costs cash money (neither free beer, nor free speech). Just saying.

---

### Post by gigake on 2010-08-05
Simple Ubuntu Default Document Viewer can do that!

---

### Post by dewclaw82 on 2010-09-20
*"Let us not forget that the website costs cash money (neither free beer, nor free speech). Just saying."*
Amen, Doctor, Amen.  

And thanks to Aysiu, again!  I would never have managed to become an Ubuntu user without your great tutorials.

---

