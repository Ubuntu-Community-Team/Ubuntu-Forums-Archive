---
title: "Install Office Addons (Export to PDF)"
date: 2009-11-23
forum: Wine
---

### Post by roystreet on 2009-11-23
Hello,
    I've looked around & I can't find a thread here on how to install some of the addons for MS Office 2007.  I have office running on my machine right using WINE.  I would like to use the export to PDF addon that office has.  I don't know if it's possible because I have read that service packs for office will not install using WINE, but I'm not sure.

Thanks,
   ~roystreet

---

### Post by Leighman on 2009-11-23
I've successfully installed the XPS/PDF exporter add-on thing a few builds back and it seems to work fine.
Service packs on the other hand :(

---

### Post by roystreet on 2009-11-24
Hi,
...Well I tested it.  It looked like it installed perfectly & quickly.  It  even appears in word in the save as options.  When I try to save it as a pdf, it goes through the regular moves, asking me what to name it, where to put, etc.  Then when I tell it to save it - it acts like it's trying, but then wine kinda crashes.  Wine gives me a sad message saying sorry, but something went wrong (Those aren't the exact words, but is the gist)  
...Then word is still open, but the document is dark & uneditable.  I then have to force word to close.

Any thoughts on why this is happening?

~roystreet

---

### Post by Leighman on 2009-11-26
Seems to be something to do with t2embed.dll.
You could try going to winecfg -> libraries and setting that as native.
Sorry, I don't have time to test at the mo

---

### Post by teejay17 on 2010-03-25
> **roystreet said:**
> Hi,
...Well I tested it.  It looked like it installed perfectly & quickly.  It  even appears in word in the save as options.  When I try to save it as a pdf, it goes through the regular moves, asking me what to name it, where to put, etc.  Then when I tell it to save it - it acts like it's trying, but then wine kinda crashes.  Wine gives me a sad message saying sorry, but something went wrong (Those aren't the exact words, but is the gist)  
...Then word is still open, but the document is dark & uneditable.  I then have to force word to close.

Any thoughts on why this is happening?

~roystreet
Did you ever figure out how to get it working? I currently have Office 2007 installed, and it works really well, but I'd like to install the service packs because I'd like to be able to save as PDF. I'd also like to install the Office Live Add in 1.4 so that I can access the files I have saved online.

---

### Post by donkyhotay on 2010-03-26
Why use an office addon to export when you can just print to PDF natively? Ubuntu has an option where you can choose to print to PDF, this allows you to create PDF's of any program capable of printing. I don't use MSoffice myself but I do use this feature with other programs. Assuming you can print to a normal printer with MSoffice in wine then you can just as easily print to PDF and create your files that way.

---

### Post by roystreet on 2010-03-26
Hi donkyhotay,
....I'd have to look into what you are talking about.  I can say that I believe I remember...with the PDF apps I've used on Linux I don't recall it ever converted it totally correctly.  For instance maybe formatting changed some, maybe bumping words over, etc.  This would apply outside of MS office apps.
...I will have to double-check that again.  Even with that though, the question that teejay17 has is also mine, is there a way to install service packs to MS office.
.
Once again, donkyhotay thank you for your sugesstion & I will try that out.  (I don't remember if I had or not)
Thanks,
~roystreet

---

### Post by Leighman on 2010-03-26
From what I remember, you can print to file if you install the cups-pdf package from Synaptic, but it didn't really work very well with wine.

You can follow the wine bug reports for SPs and PDF exporter at:
[http://bugs.winehq.org/show_bug.cgi?id=18376](http://bugs.winehq.org/show_bug.cgi?id=18376)
[http://bugs.winehq.org/show_bug.cgi?id=21427](http://bugs.winehq.org/show_bug.cgi?id=21427)
and provide any info if you have any.

---

### Post by teejay17 on 2010-03-30
> **Leighman said:**
> From what I remember, you can print to file if you install the cups-pdf package from Synaptic, but it didn't really work very well with wine.

You can follow the wine bug reports for SPs and PDF exporter at:
[http://bugs.winehq.org/show_bug.cgi?id=18376](http://bugs.winehq.org/show_bug.cgi?id=18376)
[http://bugs.winehq.org/show_bug.cgi?id=21427](http://bugs.winehq.org/show_bug.cgi?id=21427)
and provide any info if you have any.
Do you know if the Wine service pack bugs also affect installation CDs with the service packs already included. I'm trying to install an Office 2007 SP2 disk and it is encountering an error about half-way through the installation.

---

### Post by Leighman on 2010-03-31
No idea I'm afraid. Could well be.
You could try running it from the terminal and see whether the output is the same as that given in the bug report?
If it is, maybe mention it in the report.
If not, file a new one =D

---

### Post by Leighman on 2010-03-31
Fix for saving as PDFs just landed in git so should be released on Friday in .42!

---

### Post by teejay17 on 2010-03-31
> **Leighman said:**
> Fix for saving as PDFs just landed in git so should be released on Friday in .42!
Oh awesome! Can't wait for this feature.

---

### Post by teejay17 on 2010-04-04
So now that Friday has come and gone, what do we need to do to  incorporate the patch/fix?

---

### Post by Leighman on 2010-04-04
The release announcement has been made at [http://www.winehq.org/](http://www.winehq.org/)
You could get the source from there and compile (not really recommended but [http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)) or you could just wait for it to land in Ubuntu.  I'm afraid I don't know when, I don't have any control over that.

---

### Post by teejay17 on 2010-04-05
> **Leighman said:**
> The release announcement has been made at [http://www.winehq.org/](http://www.winehq.org/)
You could get the source from there and compile (not really recommended but [http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)) or you could just wait for it to land in Ubuntu.  I'm afraid I don't know when, I don't have any control over that.
I'll just wait for it to land in Ubuntu. Let's hope it is sooner rather than later (like in time for the official 10.04 release).

---

### Post by supergj on 2010-04-14
installing cups-pdf worked for me.

---

