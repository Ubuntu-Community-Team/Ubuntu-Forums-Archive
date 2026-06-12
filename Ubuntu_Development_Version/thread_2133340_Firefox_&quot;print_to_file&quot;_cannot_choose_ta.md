---
title: "Firefox &quot;print to file&quot; cannot choose target folder."
date: 2013-04-07
forum: Ubuntu Development Version
---

### Post by monkeybrain2012 on 2013-04-07
Try print something from Firefox with "print to file", no matter which destination is chosen to print to (say Desktop) the output always end up in Home/username.

---

### Post by tgalati4 on 2013-04-07
I'm running Firefox20 and I also get an error message:  "Can't select target directory."  But, it did leave a PDF in the correct directory.  So I don't know if this is a CUPS bug a Firefox bug.

---

### Post by monkeybrain2012 on 2013-04-08
This happens only in Firefox20's  Raring  buid (in Precise no problem). Just tested with Chrome and there is no problem choosing target directoty.

---

### Post by monkeybrain2012 on 2013-04-13
I have just tested this again and still cannot choose directory to print to.

---

### Post by ubu-for on 2013-04-13
Try [PrintPDF]('https://addons.mozilla.org/de/firefox/addon/printpdf/') instead. Works fine :)

---

### Post by mc4man on 2013-04-13
As per comment 2 while it says it can't choose target folder *while printing* it actually does so  to whatever folder was chosen

---

### Post by monkeybrain2012 on 2013-04-13
> **mc4man said:**
> As per comment 2 while it says it can't choose target folder *while printing* it actually does so  to whatever folder was chosen

Which printer? If you use 'PDF' (with cups-pdf) then it always cannot choose output folder. But with 'print to file" you should be able to. I didn't see any "can't select directory" message but the box for the output destiny is blank (rather than with default say usrname) and whatever I choose from the box I end up always printing to Home/username

---

### Post by rrnbtter on 2013-04-13
Greetings,
Open a webpage and choose Print/Print to file. In the "Save in Folder" box choose "Other". Select your folder and give your file a name. It should print in the correct folder. You may see a message that says "Firefox can't use selected folder" but it will print to the selected folder anyway. At least that how mine Firefox 20 works.

---

### Post by mc4man on 2013-04-13
> **monkeybrain2012 said:**
> Which printer? If you use 'PDF' (with cups-pdf) then it always cannot choose output folder. But with 'print to file" you should be able to. I didn't see any "can't select directory" message but the box for the output destiny is blank (rather than with default say usrname) and whatever I choose from the box I end up always printing to Home/username
Well "print to file" which works as described (cups-pdf wasn't mentioned in thread title or OP

As far as cups-pdf (PDF option in print to file
That seems quite whacked here, there is no output option in the print window. Defaults to ~/PDF here & doesn't respond well to any output changes in 
/etc/cups/cups-pdf.conf (checking /var/log/cups/page_log & cups-pdf_log if enabled

Is there something that cups-pdf provides that print to file doesn't? (other than some poor behavior

Edit: or is there a way to use a local conf for cups-pdf?

---

### Post by ping-wu on 2013-04-14
> **mc4man said:**
> 
Is there something that cups-pdf provides that print to file doesn't? (other than some poor behavior

With cups-pdf you don't have to type the filename (unless you want to enter a different one).  Sometimes it is a humbug to always have to type in a filename.

Also with cups-pdf, you always know that your output file will go to the $HOME/PDF folder which can be subsequently moved to another folder.

---

### Post by pqwoerituytrueiwoq on 2013-04-14
i can also confirm this, it puts that message in the file name
*_ubuntu__Firefox__print_to_file__cannot_choose_target_folder.pdf*
printed using cups-pdf
same thing in chromium, must be a issue in cups-pdf
*_ubuntu__Firefox__print____t_choose_target_folder.pdf*

---

### Post by mc4man on 2013-04-14
> **pqwoerituytrueiwoq said:**
> i can also confirm this, it puts that message in the file name
*_ubuntu__Firefox__print_to_file__cannot_choose_target_folder.pdf*
printed using cups-pdf
same thing in chromium, must be a issue in cups-pdf
*_ubuntu__Firefox__print____t_choose_target_folder.pdf*
Did you 'print' this thread? (took me a moment or 2 to realize that cups-pdf was properly using this thread title..

Overall here the PDF option works fine now, the only thing I can't get is it to save to somewhere different than ~/PDF via the conf file.

---

### Post by pqwoerituytrueiwoq on 2013-04-14
> **mc4man said:**
> Did you 'print' this thread? (took me a moment or 2 to realize that cups-pdf was properly using this thread title..

Overall here the PDF option works fine now, the only thing I can't get is it to save to somewhere different than ~/PDF via the conf file.

*looks at title*
opps seems it worked properly, lol

---

### Post by monkeybrain2012 on 2013-04-14
> **ubu-for said:**
> Try [PrintPDF]("https://addons.mozilla.org/de/firefox/addon/printpdf/") instead. Works fine :)

I know it works fine, but I don't want that because you can't choose the output directory (always in ~/PDF) "print to file" can, or should be able to, that is the whole point of this thread. This is a bug, saying that there is an alternative, --which really isn't for the purpose of being able to choose the output directory, --is not very much of a solution. :)

OK, if I was confusing I will clarify it with a screenshot from Precise (I am not on Raring now), there are 3 options here. I am talking about the first one,  not the second. Now see the box that says "Desktop"? In Raring that box is left blank and no matter what I choose there the output is always in Home/user.

---

### Post by pqwoerituytrueiwoq on 2013-04-14
if you want a static location for it you can make ~/PDF a symlink to where you want them to end up
you can hide the symlink using a .hidden file with "PDF" in it in your home folder

---

### Post by monkeybrain2012 on 2013-04-14
> **pqwoerituytrueiwoq said:**
> if you want a static location for it you can make ~/PDF a symlink to where you want them to end up
you can hide the symlink using a .hidden file with "PDF" in it in your home folder

Thanks, I know that, but I am talking about a lost functionality here which I think is somewhat a bug of the FF raring build. :) (Same version of FF don't have this problem in Quantal or Precise)

---

### Post by mc4man on 2013-04-14
> **monkeybrain2012 said:**
> Thanks, I know that, but I am talking about a lost functionality here which I think is somewhat a bug of the FF raring build. :) (Same version of FF don't have this problem in Quantal or Precise)

Now back  to (or never should of left?) "print to file"
If there is a bug not seen here, ubuntu session
Can pick any folder, either the default displayed or thru 'other'
In case of screens picked Documents/saved_web & pdf's are printed to there (every time, irregardless of any message - screen 3

---

### Post by mc4man on 2013-04-16
Taking a bit of  a closer look at "print to file", there does seem to be a bug.
If any of the 'default' displayed folders are chosen directly then the whatever.pdf always goes to home folder.
If that same folder is chosen via the 'other' menu then the .pdf is saved to that location.

Ex. - pick Documents from initial 'save in folder' dropdown. Saved to home.
Pick Documents from the 'other' menu, it's saved to Documents

Seems to only be with browsers, tried FF & chromium

---

### Post by monkeybrain2012 on 2013-04-24
> **ping-wu said:**
> you always know that your output file will go to the $HOME/PDF folder which can be subsequently moved to another folder.

Yes, but I would like to choose where to print my file instead of it always going somewhere. For the same reason I configure Firefox and Chrome to "alawys asks" for download destination instead of having it always going to ~/Download

---

### Post by monkeybrain2012 on 2013-04-24
I can choose the destination with "Print to file" only if I choose "other" from the "save in folder" box and then choose my folder, however if I just say, click Desktop (or any option) in the box it will always save to ~/Download. This only happens in FF's Raring build, so I think it is a bug.

---

### Post by mc4man on 2013-04-24
filed on that a week ago, apparently a gtk 2 bug
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1169405](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1169405)

---

### Post by Elfy on 2013-04-24
commented and confirmed it

---

