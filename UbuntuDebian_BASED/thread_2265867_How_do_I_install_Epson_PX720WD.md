---
title: "How do I install Epson PX720WD?"
date: 2015-02-18
forum: Ubuntu/Debian BASED
---

### Post by p.callan on 2015-02-18
Last time I tried to install something I broke it because I shouldn't have followed the guide that I did.
So this time I'm asking first, how do I install The Epson inkjet all-in-one PX720WD printer on Elementary OS Luna (Ubuntu 12.04) without availability to the drivers from Epson's site? 
The guide [on this site]("http://www.penguintutor.com/news/hardware/PX720WD") gives me [this]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/") and [this link]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") but none of them work to get to the software (.deb package). 
Now, I fin nothing on either "Epson" or "PX720WD" in the software center and I need this to work so now I'm asking for help (need to print passport application form). 
I'm not going anywhere near the terminal until I know what to do.

How do I install this?


THANK YOU.

---

### Post by pdc on 2015-02-18
Hi there p.callan

from the Epson site, [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) I typed in 720WD in the search space, and Epson seem to provide drivers for you; so that's great;

They provide [COLOR="#008000"]epson-inkjet-printer-artisan-725-835-series_1.0.0-1lsb3.2_i386.deb[/COLOR] or [COLOR="#008000"]epson-inkjet-printer-artisan-725-835-series_1.0.0-1lsb3.2_amd64.deb[/COLOR] as appropriate

______________________

Scanner components are:

iscan data first 

all from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35136&DSCCHK=de9429162c4ec47336d66db3c2c0433f55f79a46](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35136&DSCCHK=de9429162c4ec47336d66db3c2c0433f55f79a46)

1) [COLOR="#008000"]iscan-data_1.35.0-1_all.deb
[/COLOR]
2) scanner driver

3) network plugin if needed from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=34201&DSCCHK=36a645f307ab4aeeec8d6ac1331c27eb47814fa4](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=34201&DSCCHK=36a645f307ab4aeeec8d6ac1331c27eb47814fa4) and it comes down as [COLOR="#008000"]iscan-network-nt_1.1.1-1_amd64.deb[/COLOR] or 32bit 

______________

We hope all goes well

with a new printer; one needs to three things usually

1) a connection
2 install drivers
3) register printer with lpadmin

.........with the install scripts of Canon and Brother usually 2) and 3) are all done for you: with Epson you may need to open the PRINTER box and ADD a new printer ..................thus registering it with lpadmin

______________

if Elementary OS uses gdebi installer, it should do all the installing for you as you click to download these files ........if you don't have it installed, I recommend it!

---

### Post by p.callan on 2015-02-21
NOTE: The Epson website did not work when I wrote OP. "Service is temporarily unavailable".


I "add printer" in system settings and punch in the IP of the printer. It finds it and then "searching for drivers". "Choose driver" is displayed. I select "search for a printer driver to download" but [COLOR=#b22222]it finds nothing[/COLOR] on either "Epson" or "PX720WD". I select "provide PPD file" and select the downloaded drivers;

> [COLOR=#b22222]**PPD Error**
Failed to read PPD file.  Possible reason follows:[/COLOR][COLOR=#b22222]/home/patrick/Downloads/epson-inkjet-printer-artisan-725-835-series_1.0.0-1lsb3.2_i386.deb: FAIL[/COLOR]
[COLOR=#b22222]      **FAIL**  Unable to open PPD file - Missing asterisk in column 1 on line 1.[/COLOR]
[COLOR=#b22222]                REF: Page 15, section 3.2.[/COLOR]
[COLOR=#b22222]        WARN    File contains a mix of CR, LF, and CR LF line endi[ngs[/COLOR].

Third and final option is "choose printer from database" and a list of printer brands appear. I select epson and a list of printers appear. But, surprise! [COLOR=#b22222]PX720WD isn't in it[/COLOR]. Shocker. Because, why would it just work, right?

I open the driver .deb package with software center (the default) and install. It runs the install. I then check in system settings to see if there are printers installed. You guessed it, there are none.

I install [COLOR=#008000]iscan-data_1.35.0-1_all.deb [/COLOR]the same way, maybe that'll work better.
I try to install [COLOR=#008000]iscan-network-nt_1.1.1-1_i386.deb [/COLOR]"[COLOR=#b22222]dependency is not satisfiable iscan (>= 2.29.3)[/COLOR]". Note that I had just installed version 1.35.0-1!

So I try to install another version of iscan, namely [COLOR=#008000]iscan 2.30.1-1~usb0.1.ltdl[/COLOR] which is higher up in the Epson list. But this of course gives another error: "[COLOR=#b22222]dependency is not satisfiable libltdl3 (>= 1.5.2-2)[/COLOR]". 

And now I realize I am caught in the very time-consuming loop of non-working software installations that I was trying to avoid from the very beginning. Which usually happens. 

[COLOR=#b22222]Giving up[/COLOR]. You win again, Linux installs.

Rebooted and tried to print a document. No go. 
The printer is not in the list when clicking on 'print'. Only "print to file" is available.

---

### Post by speartip on 2015-02-21
Have you installed the correct thing?
I have just installed your printer driver from here:
[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35219&DSCCHK=01a2288d3ec549615b1491db99fd832d75b73aac](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=35219&DSCCHK=01a2288d3ec549615b1491db99fd832d75b73aac)
and it installs no problem with gdebi.

---

### Post by howefield on 2015-02-21
Thread moved.

Running various Ubuntu releases going back to 12.04 with the same printer, all I need to do is install the driver (epson-inkjet-printer-artisan-725-835-series_1.0.0-1lsb3.2_amd64.deb) - then add the printer via system settings. Seriously simple and I feel for you that it obviously isn't the case for you.

---

### Post by pdc on 2015-02-21
Hi there p.callan

howefield has commented above on the printer driver install;

______________________

for the**_ scanner driver install,_** I should perhaps have spelt out that one needs the [SIZE=4][COLOR="#0000FF"]ltdl7[/COLOR][/SIZE] version    ......... [COLOR="#008000"]iscan_2.30.1-1~usb0.1.ltdl7_amd64.deb[/COLOR]	or [COLOR="#008000"]iscan_2.30.1-1~usb0.1.ltdl7_i386.deb[/COLOR]        ........ltd3 is only for very old systems ............yes, they should list them somewhere else ............

I comment on that because you said > But this of course gives another error: "dependency is not satisfiable [SIZE=4][COLOR="#A52A2A"]libltdl3[/COLOR][/SIZE] (>= 1.5.2-2)". 

_________________________

can you please paste this command ```
dpkg -l | grep epson-inkjet-printer-artisan
``` into a terminal; please copy the result if you get any; and please tell us the result

---

### Post by howefield on 2015-02-22
> **pdc said:**
> Hi there p.callan

howefield has commented above on the printer driver install;...

Yep, as I said, that's all I need to do.

Scanner works without the need for "external" .deb packages

---

