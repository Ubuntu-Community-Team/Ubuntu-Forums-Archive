---
title: "hp-setup fails on setting up print queue"
date: 2015-03-27
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-03-27
Trying to add my Envy_4500 printer/scanner to Vivid using hp-setup -i [ipadd].  Fails trying to create the print queue.  

---------------------
| PRINT QUEUE SETUP |
---------------------


Please enter a name for this print queue (m=use model name:'ENVY_4500'*, q=quit) ?ENVY_4500
Using queue name: ENVY_4500
Locating PPD file... Please wait.

Found PPD file: drv:///hpcups.drv/hp-envy_4500_series.ppd
Description: 

Note: The model number may vary slightly from the actual model number on the device.

Does this PPD file appear to be the correct one (y=yes*, n=no, q=quit) ? y
Enter a location description for this printer (q=quit) ?Downstairs
Enter additonal information or notes for this printer (q=quit) ?

Adding print queue to CUPS:
Device URI: hp:/net/ENVY_4500_series?ip=192.168.1.205
Queue name: ENVY_4500
PPD file: drv:///hpcups.drv/hp-envy_4500_series.ppd
Location: Downstairs
Information: 
error: Printer queue setup failed. Error : server-error-internal-error 

Can add the printer via Settings -> Printers but the scanner will not work.  Experenced same problem on 14.04.2 but using hp-setup there worked OK.

---

### Post by mbott on 2015-03-27
I have the HP Envy 5530 and I set it up in Vivid like I set it up in 14.04: via CUPS add a printer.  Then I added the HP toolbox via the software center and it set up perfectly.  I realize this is may be backwards for some people.  For me, it just works.

-- 
Mike

---

### Post by crcarson on 2015-03-27
> **mbott said:**
> I have the HP Envy 5530 and I set it up in Vivid like I set it up in 14.04: via CUPS add a printer.  Then I added the HP toolbox via the software center and it set up perfectly.  I realize this is may be backwards for some people.  For me, it just works.

-- 
Mike

Thanks, installing HP Toolbox corrected the errors I was seeing with hp-setup.  Installed the printer again and can both print and scan.

---

### Post by mbott on 2015-03-27
Glad it helped.

-- 
Mike

---

