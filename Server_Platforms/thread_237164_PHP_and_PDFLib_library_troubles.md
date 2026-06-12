---
title: "PHP and PDFLib library troubles"
date: 2006-08-15
forum: Server Platforms
---

### Post by dbarbour on 2006-08-15
I'm trying to get PDFLib support for PHP up and running. So I uploaded to library (the .so), pointed the php.ini config file to the proper directory and file names and everything was just dandy. I could create PDF files to my hearts content. However, it killed support for most everything else.. most natoable PostgreSQL. So I reset everything back to the way it was, moved the pdflib library to the same location as all other extensions (/usr/lib/php5/20051025/) and hoped for the best. All I got was nothing.

Two things... Why wouldn't PHP load the new extension despite the fact that it is in the same spot as all other extensions? Two, why did changing the "extension_dir" directive in php.ini kill support for all of the other libraries?

---

