---
title: "Is it safer to download a PDF instead of using a plugin to view online?"
date: 2011-03-14
forum: Security
---

### Post by nrundy on 2011-03-14
I read a lot about how plugins can be a security vulnerability for exploits.

Is there any security advantage to NOT using a PDF-plugin but instead just downloading PDFs that you want to view? Or is using a plugin to view a PDF just as risky has downloading a potentially hostile file? From a security perspective, is one preferable to the other?

---

### Post by iiiears on 2011-03-14
There isn't likely to be a difference as much of the mischief embedded in pdfs calls java. Java is powerful there isn't much that can't be done with it except maybe write a driver.
 
Linux gives you small percent advantage. Only the most intrepid and savvy users have it installed.


     Open the pdf in a live CD or second choice virtual machine.

 
There are a few tools out there to sanitze pdfs of script but that that still leaves maybe a dozen other vectors in each pdf.
 
Read what Bruce Schnier has to say about word docs being dethroned as the king of malware transport. He claims 47 percent of sampled attacks come from pdf files.

Really, nuke them from orbit it is the only way to be sure...

---

### Post by wdtd on 2011-03-14
Is there a particular PDF reader you would recommend that will just show the basic PDF and not the potentially problematic "extras"?

---

### Post by SeijiSensei on 2011-03-14
[okular]("http://okular.kde.org/") works fine for me, but it is a KDE application. Installing it on GNOME Ubuntu will require other libraries to be installed as well.  

I always smile when I see the checkbox in okular's preferences marked "Obey DRM limitations!"  Disobedient boy that I am, I leave that unchecked.

---

### Post by nrundy on 2011-03-14
> **iiiears said:**
> 
 
Read what Bruce Schnier has to say about word docs being dethroned as the king of malware transport. He claims 47 percent of sampled attacks come from pdf files.


I found this comment by Bruce Schnier at [http://www.schneier.com/blog/archives/2010/04/booby-trapping.html](http://www.schneier.com/blog/archives/2010/04/booby-trapping.html). The link leads to a page listing EVINCE as one of the recommended PDF readers. Based on this I'll assume it's safer to download the PDF and open it in EVINCE.

          _____@Ron Helwig 
           _____PDF actually stands for Perilously Dangerous Format.
            
          _____@Bruce 
          _____Isn't this stuff really old news? 
_____FYI: Alternative readers that don't support a lot of the dangerous features 
          _____allowed for by the PDF specs are listed here: [http://pdfreaders.org/](http://pdfreaders.org/)
 
           _____Posted by: AlanS at [April 22, 2010  2:58 PM]("http://www.schneier.com/blog/archives/2010/04/booby-trapping.html#c430228")


> **iiiears said:**
> 
Really, nuke them from orbit it is the only way to be sure...

What do you mean by this? Is there some way to "sanitize" them before download?

---

### Post by doas777 on 2011-03-14
> **nrundy said:**
> I read a lot about how plugins can be a security vulnerability for exploits.

Is there any security advantage to NOT using a PDF-plugin but instead just downloading PDFs that you want to view? Or is using a plugin to view a PDF just as risky has downloading a potentially hostile file? From a security perspective, is one preferable to the other?
yes but only in a very very narrow and specific case. in the long run the practical difference is small.

---

