---
title: "Setting up a print server and accessing it from Windows Network"
date: 2011-10-10
forum: Server Platforms
---

### Post by DRouleau on 2011-10-10
Ok I have installed CUPS and have it working to the point that I can print a test page from the server. However I'm not able to see the printer from the network (every machine but the "print server" is a windows box). I'm using 11.04 Server edition. Also when I go to the servers share all the files are showing up but again not the printer (if you select printers). Pretty new to Ubuntu so any help will be appreciated. Thanks in advance!!

---

### Post by 2F4U on 2011-10-10
You can use Samba to make the printer visible to Windows machines. See, for example, here

[http://ubuntuforums.org/showthread.php?t=1339956](http://ubuntuforums.org/showthread.php?t=1339956)

---

### Post by DRouleau on 2011-10-10
You are the man (or woman)... Exactally what I was looking for.  Thank you!!!

---

### Post by DRouleau on 2011-10-10
Ok jumped the gun a little... so I can now see the printer, but when I try to add to to my windows box it tells me the driver isn't correct.

---

### Post by DRouleau on 2011-10-10
Got it working...  minor tweak on the setup but now it works...

---

