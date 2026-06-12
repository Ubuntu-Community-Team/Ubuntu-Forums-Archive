---
title: "Printer privacy"
date: 2011-02-02
forum: Security
---

### Post by asdfghjkl67 on 2011-02-02
Does a multifunction printer (epson) retain logs and copies of the data that went through the scanner or what it printed out?

---

### Post by sydbat on 2011-02-02
> **asdfghjkl67 said:**
> Does a multifunction printer (epson) retain logs and copies of the data that went through the scanner or what it printed out?No.

---

### Post by cariboo on 2011-02-02
CUPS can do page logging, just go to [http://localhost:631](http://localhost:631), on the system the printer is connected to, and setup logging under administration.

---

### Post by asdfghjkl67 on 2011-02-04
Ok i just found this [http://www.theregister.co.uk/2010/08/06/ebay_photocopier_disposal_risk/](http://www.theregister.co.uk/2010/08/06/ebay_photocopier_disposal_risk/)

I have a epson stylus SX115-how do i get at the hard drive to erase it?

---

### Post by cariboo on 2011-02-04
Your printer doesn't have a hard drive, that article is talking about computer hard drives, if you don't want printer logs  disable logging in the cups interface.

---

### Post by asdfghjkl67 on 2011-02-05
From that link 'Multi-purpose photocopiers, which double as scanners and printers, use hard drives to store data.' 

The model i have the epson stylus sx 115 can print, scan and copy all on ubuntu-surely there must be a way to format the printers hard drive via ubuntu right?

---

### Post by uRock on 2011-02-05
The specs on their site say nothing about a hard drive. [http://www.epson.co.uk/Printers-and-All-In-Ones/Inkjet/Epson-Stylus-SX115/Tech-Specs;jsessionid=D3FB161677F772CFA245120C9BA2A085.acc2-new](http://www.epson.co.uk/Printers-and-All-In-Ones/Inkjet/Epson-Stylus-SX115/Tech-Specs;jsessionid=D3FB161677F772CFA245120C9BA2A085.acc2-new)

Reading their TM might be helpful. [ftp://download.epson-europe.com/pub/download/3233/epson323393eu.pdf](ftp://download.epson-europe.com/pub/download/3233/epson323393eu.pdf)

Most printers that are multipurpose have RAM to temporarily store data. Higher quality Printers will have expansion ports for adding more RAM. I have never heard of a printer having a hard drive,except in the case where there is a PC/Server being used as print server which may be set to log print jobs, such as Active Directory has the ability to do, but that is a separate system connected to the printer.

If your want to clear the RAM, then turn the printer power off, then back on again.

PS, I am open to corrections on this as I am not a printer pro, but I did just ace the Cisco PC trouble shooting and repair class that has in depth coverage of printers.

---

### Post by cariboo on 2011-02-05
There are some high end photocopiers that do have hard drives, back in the day when I serviced copiers for a living we had one highspeed copier that used a hard drive to cache pages, as the mechanical section couldn't keep up. At the time, the copier retailed for well over $100,00.00

---

### Post by asdfghjkl67 on 2011-02-10
Ok so i emailed  epson tech support and this is the answer i got back-

'[SIZE=2]In reply to your email, the only printers in the Epson  range that have any kind of internal memory are the units that have a  built in fax. Apart from that Epson printers spool all the information  on the PC itself and no information is retained in the units.' 

My multifunction device doesent have a faxing ability so guess there must be no internal memory right apart from ram? 
[/SIZE]

---

### Post by cariboo on 2011-02-10
Internal memory is ram, you won't see any internal storage drives on inexpensive consumer printers

---

