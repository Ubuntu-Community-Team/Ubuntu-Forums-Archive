---
title: "Can I make Cups-pdf print to a specific directory based on Printer"
date: 2012-06-08
forum: Server Platforms
---

### Post by wpflum on 2012-06-08
I have the latest and greatest version of Ubuntu server installed and have cups-pdf print working.  Right now it defaults to saving the file in the user's directory under a folder called PDF.  I see that I can change that to save in a generic directory for anonymous prints but what I'd like to do is save to a particular folder based on the printer name itself.  What I eventually want to do is have a cron job monitor several directories and when a pdf is printed to a specific folder the cron will email it to a specific email group or individual.  This way I can have folders for Management , Sales and Staff and corresponding printers such as EmailSalesPDF and such that when I print to those printers the resulting pdf is then emailed to whoever I have setup in the cron program monitoring that folder.  

Any ideas how I can trap the printer name in the cups-pdf.config and make it do what I want?  What I'm trying to do is tie together several legacy systems together into a consolidated report system capable of emailing reports automatically instead of manually running the reports, copying them and distributing them through normal mail channels.

Any suggestions?

---

