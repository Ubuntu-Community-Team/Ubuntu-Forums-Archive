---
title: "HylaFax; blank pages"
date: 2010-04-26
forum: Server Platforms
---

### Post by awacs on 2010-04-26
I just set up HylaFax on Lucid, using the Sourceforge WinPrintHylafax client. Works great; talks to the modem, send faxes, responds to status commands.

Only problem: the faxes are blank, except for the fax header that HylaFax adds. 

I used the recommended Apple PS driver, and also a HP PS driver, which gave an error message: "PCL documents are not (currently) supported."

Browsing the system logs reveals noting amiss. Tried several different types of documents: html, pdfs, word, etc.

What might be the problem?

Thanks!

---

### Post by awacs on 2010-04-26
Follow-up to my own question: I found the directory /var/spool/hylafax/docq, where my converted documents live, is postscript format, and evince is able to read them. this means (I think) that the conversion is correct, and the converted files are blanked somehow ...?

---

### Post by awacs on 2010-04-26
Nevermind: I found my answer in the Hylafax fora. I had to put 'Use2D: no'
in /etc/hylafax/config.

---

### Post by juk_de on 2011-01-28
Thank you very much for posting the solution! :)
I had exactly the same problem after upgrading from hardy to lucid.

---

### Post by kc5goi on 2011-05-09
I also want to say thanks.  Your fix took care of my problem too.

Guy

---

### Post by Ghibli68 on 2011-12-22
> **awacs said:**
> Nevermind: I found my answer in the Hylafax fora. I had to put 'Use2D: no'
in /etc/hylafax/config.
 Thank you for the solutions.
I had the same problem and i resolve with this. :)

---

### Post by wmccarty on 2012-01-03
> **awacs said:**
> Nevermind: I found my answer in the Hylafax fora. I had to put 'Use2D: no'
in /etc/hylafax/config.

 I had to use Lucid for a new install of hylafax and this Use2D: no fixed my blank pages sending problem. Perhaps this should be mentioned in the Hylafax documentation?

---

