---
title: "Why Is CUPS Defaulting To A4?"
date: 2013-09-09
forum: Server Platforms
---

### Post by Kirk Schnable on 2013-09-09
I am running two CUPS servers here used by almost 1,000 end users.

This year, since upgrading everything to Ubuntu 12.04, printers around my building are plagued with an error message when users print.

[IMG]http://binaryimpulse.com/wp-content/uploads/2013/09/printer-error-A4-800x597.jpeg[/IMG]

Of course, I know that if you press the Go button on the printer twice, it'll print the page on Letter anyway.  I also know that you can select 8.5"x11" US Letter when printing and it'll work just fine.

I would like to determine why my CUPS clients\print servers are defaulting to this A4 paper size so often, and if there's any way I can change a default option somewhere to prevent it?

My CUPS servers are both running CUPS 1.5.3.

The default options for the printer itself seem to be correct.

[IMG]http://binaryimpulse.com/wp-content/uploads/2013/09/CUPS-default-options-letter-800x516.png[/IMG]

Any ideas?

Thanks,
Kirk

---

### Post by Kirk Schnable on 2013-09-13
We've determined that this is definitely happening in Evince regularly.  When users print PDFs from Evince, it's defaulting to A4.  It also seems to happen when printing PDFs out of Google Chrome.  The default options do appear to be correct in LibreOffice and GIMP though.  

I'm still not entirely sure what's going on.  Selecting US Letter in Chrome results in the printer asking for ISO-B5 paper now instead of asking for A4 or actually printing it on US Letter...

I'd love to get the ball rolling on this question, but I'm not sure what information might be helpful.  I'll keep making observations as I see the problem.

---

