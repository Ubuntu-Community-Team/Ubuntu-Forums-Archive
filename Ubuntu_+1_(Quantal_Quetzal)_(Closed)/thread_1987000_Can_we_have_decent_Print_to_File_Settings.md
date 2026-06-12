---
title: "Can we have decent Print to File Settings?"
date: 2012-05-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pt123 on 2012-05-25
The settings in **print to file** option in Ubuntu is limiting and dangerous. All the applications apart from Firefox print to a file ~/output.pdf, *[COLOR="Red"]this is dangerous as you can overwrite a previous print[/COLOR]* [COLOR="Blue"]Edit: this doesnt seem to be the case with print to file[/COLOR]. Why can't applications use the title of the document, the filename or the page title of the web page?

What package and where are the settings of this **print to file** held. I would prefer it printing to the desktop if it cannot intuitively chose a filename, as when it arrives on the desktop it would be a visual reminder for the use to change the filename.

The screenshot application uses date in the filename to avoid you over writing the previous screenshot why can't **print to pdf** do the same?

Previously I did not use the print to file feature, as the **cups-pdf **didn't have these short comings (in 10.10). But the latest releases including 12.04 of cups-pdf has been botched and all text are converted to images before embedding them in the pdf. Making the PDFs pretty much useless as it prevents the selecting of text and the sharpness of the text is lost too. 
The bug has been reported for sometime now, 
[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820)
and as usual been labelled as a wish list feature.

Why can't we have the ability to have some decent settings for the **print to file** feature. Also what package controls this utility.

---

### Post by cariboo on 2012-05-25
The bug should be sent upstream, as Canonical/Ubuntu have nothing to do with maintaining CUPS.

---

### Post by pt123 on 2012-05-25
> **cariboo907 said:**
> The bug should be sent upstream, as Canonical/Ubuntu have nothing to do with maintaining CUPS.

No, **[SIZE="2"]Print to File[/SIZE]** is not part of **CUPS**

---

### Post by VMC on 2012-05-25
> **pt123 said:**
> No, **[SIZE="2"]Print to File[/SIZE]** is not part of **CUPS**

I get a warning if output.pdf exists.

---

### Post by pt123 on 2012-05-25
> **VMC said:**
> I get a warning if output.pdf exists.
I didn't realise that, CUPS-pdf although it would give better names, it didn't provide this feature. Good to know this solves a third of the problem.

---

### Post by cariboo on 2012-05-25
After some research the problem seems to be in gnome print, as you can see from the bug report you linked to, it is still an upstream problem. I'm not on my desktop system at moment,  but it should be fairly easy to find the maintainer/authors name, and send him a email.

---

### Post by jbicha on 2012-05-25
Having a default of output.pdf is not dangerous. You can change the title easily.

---

### Post by pt123 on 2012-05-25
> **jbicha said:**
> Having a default of output.pdf is not dangerous. You can change the title easily.

It's not dangerous as unlike cups-pdf, **print to file** doesn't overwrite the file. That said it would be nice if better filenames were preset.

Looking at how Mozilla changed the default name to Mozilla.pdf,
[https://bugzilla.mozilla.org/show_bug.cgi?id=539426](https://bugzilla.mozilla.org/show_bug.cgi?id=539426) each application might need to handle presetting a better name. 
It would be also nice to set dpi for the images in the PDF like with cups-pdf.

That said the default ~/output.pdf must be mentioned somewhere, hopefully it can be changed by the user. I have checked gconf-setting couldn't find it there.

---

### Post by pt123 on 2012-05-25
Good news is that Gedit and Eye of Gnome are remembering the last filename and location you printed, so when you print next time it is presetting them. 
Although using the context of the document would be better, the fact that Gnome applications are remembering the last location used is refreshing.

---

