---
title: "CUPS-PDF with 6.06 not working"
date: 2008-10-06
forum: Server Platforms
---

### Post by jaie on 2008-10-06
I have installed CUPS-PDF on two different amd64 6.06 server versions of Ubuntu and had no success with having a Virtual Printer show up in cups. I have tried the same steps with 6.06 32bit edition and everything works fine.

I perform the following steps:

sudo apt-get install CUPS-PDF
open up cups at server:631
Select the "Administration" tab in CUPS
Select "Add Printer"
On the first prompt give the printer a name such as "PDF"
On the second tab titled "Device" I would expect there to be a "Virtual Printer (PDF Printer)" but it does not exist (in the 32bit version its there).

I read that if the permissions of the file in the /usr/lib/cups/backend directory are wrong it wont work. I checked the backend/cups-pdf file and its default permissions are -rwxr-xr-x and it is owned by root. I read an article suggesting to change the permissions to 700 which I have done but it has not helped.

I have noticed on the 32bit version (that works) the backend/cups-pdf has the permissions -rwsr-sr-x, I have no idea what the 's' means but perhaps this is the key to it working.

Any help would be appreciated, please refrain from posts telling me to upgrade to 8.04 or change to 32bit, if it were easy for me to do that I would of.

Jaie

---

### Post by Sef on 2008-10-06
1) Moved to Server Platforms.

2) What's your printer's make and model?

---

### Post by jaie on 2008-10-06
Its the CUPS-PDF printer, not a physical printer.

It seems that my initial post lead me to my answer. I changed the permissions of the /usr/lib/cups/backend/cups-pdf file from -rwxr-xr-x to -rwsr-sr-x by using the following command:

sudo chmod ug+s /usr/lib/cups/backend/cups-pdf

Then restarted cups with:

sudo /etc/init.d/cupsys restart

When I logged into cups through the web browser at localhost:631 there was an option to add the PDF Printer, and printing a test page resulted in a .pdf document. Success !!

I would suggest that the default package in 6.06 amd64 set these permissions by default to avoid other people from having the same problem.

---

