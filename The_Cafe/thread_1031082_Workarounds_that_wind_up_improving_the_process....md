---
title: "Workarounds that wind up improving the process...?"
date: 2009-01-05
forum: The Cafe
---

### Post by dwasifar on 2009-01-05
Have you ever been forced, grumbling, into a workaround, only to discover that the workaround is actually an improvement?

Case in point: I run Quickbooks under Crossover Office.  I have to print invoices to PDF.  Up until recently I had kdeprint installed for just this purpose.  I'd print from Quickbooks, select KDEPrint for the printer, and with PDF output selected it would give me a dialog for where to save and what to name the pdf file.  My naming standard was to name the file for the client and date and save it in a specific network directory.

With Intrepid, Kubuntu went to KDE4, and kdeprint is not in the repos any more.  So I had to switch to cups-pdf.  Inside Crossover Office, the cups-pdf output dialog is not available, so anything I print from Quickbooks goes to ~/pdf/_stdin_.pdf and I can't change the name or path on the fly.  So at first I was copying and renaming the files manually.  Then I had the idea to write a shell script to do it.  The script copies the _stdin_.pdf file to the network directory and renames it properly by parsing the system date.

For a while after I did this, I kept looking for ways to get back the old functionality.  Then one day I realized, hey, cups-pdf and the shell script are actually SAVING me steps.  All I have to do now is hit Print on the invoice, double click the script, and I'm done.  I don't have to manually specify a path or name any more.  Plus, because the script uses system date for the rename, it forces me to keep up with my invoices and not put them off.  

Has anyone else had an experience like this, where suddenly you realize your workaround is better than the way you used to do it before?

---

### Post by cardinals_fan on 2009-01-05
Well, I moved to Xvesa when the proprietary NVIDIA drivers stopped working.  I haven't looked back.

---

