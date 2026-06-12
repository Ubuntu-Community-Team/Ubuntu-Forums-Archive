---
title: "Ubuntu server 8.04 - fancier fonts with lp and cups"
date: 2009-05-17
forum: Server Platforms
---

### Post by 3L33T on 2009-05-17
I have a legacy ERP app running on ubuntu 8.04 server (no gui) that pipes printing to 'lp' which is currently working perfectly.  However, this is the year 2009 and I would like to use a fancier font like Arial 10 pts when printing.  By default, if you pipe output to 'lp' (cli), it uses courier font.

Is it possible to use better looking font?

---

### Post by mbeach on 2009-05-17
It will likely depend on your printer. If you have a configuration tool for the particular printer, its default font is likely courier. I suspect you are lp a raw text file straight to the printer. If not, you may be sending a pcl file in which case your application's templates likely set the font. If that is the situation, you'll probably need to amend those to pick another font.

you do have some ability to change the look with the cpi and lpi options (see man lp) but I don't think you can change the font in the cups options (I have not seen that done - but perhaps you can - I suspect not)

Another thing to consider is that if you use a non-monospaced font, reports with columns etc will likely not line up giving you some unhappy users.

The other option is to intercept the print stream and create a 'prettier' document.

---

### Post by 3L33T on 2009-05-17
> **mbeach said:**
> It will likely depend on your printer. If you have a configuration tool for the particular printer, its default font is likely courier. 


I standardized on HPLJ 4000, 8000, and 9000 printers.  I do not wish to configure a default font on the printer because it is a shared printer and others use it too.

> 
I suspect you are lp a raw text file straight to the printer. If not, you may be sending a pcl file in which case your application's templates likely set the font. If that is the situation, you'll probably need to amend those to pick another font.


Correct.  I send raw text straight to the printer.  

> 
you do have some ability to change the look with the cpi and lpi options (see man lp) but I don't think you can change the font in the cups options (I have not seen that done - but perhaps you can - I suspect not)



Correct again.  I managed to set the correct cpi and lpi options (/etc/cups/lpoptions) to print the reports with right margins and correct pagination.  ** CHANGING THE FONT IN THE CUPS ** is really my issue.  I do not know if there is a way.  Hence, I'm asking here if anyone had thought about this before and found a solution.


> 
The other option is to intercept the print stream and create a 'prettier' document.

Hmmmm, thats an idea. How do you capture/intercept the print stream in cups into a file that I can 'pipe' to a script that will massage the font and make it 'prettier'?

---

### Post by mbeach on 2009-05-19
look into the backend scripts.
man backend

A sample python script as a cups backend
[http://www.g-loaded.eu/2006/12/03/pdf2email-cups-backend/](http://www.g-loaded.eu/2006/12/03/pdf2email-cups-backend/)

Basically create the printer, which uses your backend script (set in the device-uri).

---

### Post by 3L33T on 2009-06-22
I would like to keep this thread alive as currently there isn't much positive results after searching the web for 'default cups fonts'.  Thanks to mbeach post above, this is one solution.  There is another I found from another forum and would like to crosspost here though i'm not sure if it is allowed but I will let the moderators decide:

> 

I have (or had) a similiar problem on a new RHEL4 system that I installed for one of the reserachers here. He typically prints Fortran programs using 'lp', and he didn't like the font, and found that bthe text was too light and hard for him to read. It looked different than the results he got printing the same files from his old RH9 system.

RHEL4 uses CUPS. I could find no documentation that told me how to change the default print font for the 'lp' command, but I did find the directory /usr/share/cups/fonts, which had several files named for fonts. I also found that, within the PPD file for my printer in /etc/cupd/ppd, the "Defaultfont" value would get changed back to "Courier" after I edited it to be something else and ran the print GUI.

So, back in /usr/share/cups/fonts I renamed the 'Courier' font text file as 'NotCourierAnymore', and copied 'Courier-Bold' onto 'Courier'. It worked! the 'lp' command output is darker and more readable to the researcher's elderly eyes. 

CLearly, this is not the correct way to do this, but it works. If anyone knows the correct way to change the default 'lp' font on this system (RHEL4 and CUPS), please advise.

source:  [http://forums.fedoraforum.org/showthread.php?t=81801](http://forums.fedoraforum.org/showthread.php?t=81801)



OK, this is more of a hack than a solution but it is worth trying.

---

