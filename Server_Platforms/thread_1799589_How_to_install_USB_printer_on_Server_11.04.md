---
title: "How to install USB printer on Server 11.04?"
date: 2011-07-07
forum: Server Platforms
---

### Post by youthgonewild23 on 2011-07-07
Recently, I installed Server 11.04 and selected the options for the print server and file server. I would like to add a HP Officejet J3680 printer (USB connection) but cannot figure out how. On a remote computer running Ubuntu 11.04 desktop, I tried using the CUPS web interfce but I keep getting the "Unable to connect" message. I installed webmin on the same remote computer and tried installing it that way. That way, I selected "USB Printer 1" and used "generic postscript driver" This did not work. I do not know how to install a printer. I'll use command line on the server if necessary. How is this done?

---

### Post by Hulkiedulkie on 2011-07-07
Have you taken a look at Samba?
 
[https://help.ubuntu.com/community/Samba/PrinterSharing](https://help.ubuntu.com/community/Samba/PrinterSharing)
 
If you haven't used Samba before I'd suggest you first try to share a folder, and then try a printer.
 
Unfortunately I don't have any experience with CUPS or webmin.

---

### Post by youthgonewild23 on 2011-07-08
I appreciate it but that's how to share a printer. It needs to be installed to the print server before it can be shared. I can't figure out how to install a printer on Ubuntu 11.04 server. Thank you.

---

