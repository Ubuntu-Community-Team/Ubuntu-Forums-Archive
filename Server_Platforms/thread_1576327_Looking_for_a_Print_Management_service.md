---
title: "Looking for a Print Management service"
date: 2010-09-17
forum: Server Platforms
---

### Post by lebleed on 2010-09-17
Hi Guys!!

Is there any Print Management service for centralized Print Manager and Print Monitor?

My requirement is a Print Management Server which monitor all the printers in my office and keep tracks of all the the printing operations (IP of the user, Digital copy of the printed documents, date, time...)

I installed CUPS but it's not the solution which I'm looking for.

Please help me.
Best regards.

---

### Post by LightningCrash on 2010-09-19
What's wrong with cups?

You'll have to use a backend script to capture the actual print output, but it has everything else you asked about.

check
[http://localhost:631/jobs?which_jobs=completed](http://localhost:631/jobs?which_jobs=completed)

check
/var/log/cups/access_log

---

### Post by Simbamangu on 2010-11-24
I have the same issue of wanting to do print tracking and management (shared printer from Ubuntu machine, being printed to from Mac / Windows / Ubuntu).

The /var/log/cups/access_log only seems to have the current session's worth of data.

However, the //localhost:631/jobs?which_jobs=all list seems to show _all_ the jobs since the printer was installed - from which log is that CUPS page deriving the all_jobs list?

I would prefer to find the actual, full log for the printer so that I can automate tracking, import to a spreadsheet, etc.

Any ideas?

---

### Post by SeijiSensei on 2010-11-24
I've had to set up printing for a mixed environment of printers running Windows and Linux.  Some of the printers had HP JetDirect boxes as well.  Of all the tasks I've had some involvement with, managing and maintaining printers has been the most difficult.  

CUPS still seems like the best centralized solution to me.  It can see anything that supports IPP, as well as Samba, JetDirect, and traditional lpd *nix printers.  It has extensive logs that use the Apache log format which makes them easy to parse.  

You can control the duration of logging for CUPS is by changing the parameters in /etc/logrotate.d/cups, or simply remove this file to keep the logs from being rotated at all.

---

### Post by Simbamangu on 2010-12-04
Thanks, SeijiSensei - I'll try to change the log rotations so that it doesn't always archive the old ones! 

The print logs are readable - but does anyone know of a way of parsing them automatically into, say, a spreadsheet?

CUPS is fantastic, I agree - great for managing with a mixed Ubuntu / Win / OSX set of computers.

---

### Post by SeijiSensei on 2010-12-04
> **Simbamangu said:**
> The print logs are readable - but does anyone know of a way of parsing them automatically into, say, a spreadsheet?

I don't know about "automatically" doing that, but to import a log into a spreadsheet just use the program's text import function and tell it to treat spaces as field delimiters.

Usually I parse logs with a PHP script and write the results into a PostgreSQL database.  Then I can analyze the data however I want.  You could take this approach to automate the parsing and storage issues, then use the PostgreSQL ODBC driver to import the data into something like Excel or Access.  (MySQL works here, too.)

---

