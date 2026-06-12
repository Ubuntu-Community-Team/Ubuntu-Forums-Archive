---
title: "Wireless Printer/Scanner for Ubuntu 14.04?"
date: 2014-10-16
forum: The Cafe
---

### Post by Quarkrad on 2014-10-16
I need a new multifunctional printer for home and had not too good experiences with HP models - although the driver support is excellent.  I wanted a change and decided that Epson and Canon were worth looking at - in the end I have purchased a Canon Pixma MX535 – encouraged by the fact that on Canon's support web site there were linux (both rpm and deb) drivers for many of their machines.   The Printer app under System Settings found the printer (wifi connected) straight away and I was connected up and can print.  However, the scanner remains undetected.  I have installed the Canon linux drivers and synaptic tells me the scangear driver is alive and OK.  However, still no ability to communicate with the scanner over wifi (I can via usb).   I think this is going to be difficult to fix – the hp worked out of the box re the linux driver.  I am thinking of selling and getting another non hp device – what is the best why to ensure what I buy will have both printing and scanning over wifi?

---

### Post by pqwoerituytrueiwoq on 2014-10-16
direct wireless scanning as far as i know is not possible, indirect however is
the only way i know of (given canon provides scanner drivers that are usable via the scanimage command) would be to use my scanner server (link in sig) with a low profile (ok it does not have to be low-profile, but...) server then access it via wifi
or you share the scanner via sane and access it via simple scan, i have had issues with this feature after 10.04, no where near as stable

---

### Post by Quarkrad on 2014-10-16
Thank you.  I've had bad experiences with HP but I must say their linux driver worked a treat - wireless printing AND scanning with full functionality.  Mother-in-law needs a new printer so I'm thinking of giving her this one - at least she (12.04) is usb connected.  Problem I have is - am I forced to go with HP or can I go to another manufacturer who support ubuntu/linux and get my wireless printing and scanning?  I thought I was safe with Canon so now I'm nervous.

---

### Post by pqwoerituytrueiwoq on 2014-10-19
perhaps i should add something to the 1st line of my last post
direct wireless scanning as far as i know is not possible **(regardless of brand or operating system)**, indirect however is...

---

### Post by kurt18947 on 2014-10-20
Brother has quite good linux support though scanner installation not 'plug 'n' play' like HP seems to be. I've had success including scanning over a wifi network using Brother's installer found here:

[http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625)

There may be two post-install fixes necessary.  One is talked about here:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

The second - necessary for normal (non-admin account) USB connected scanning is here:

[http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04)

To use a Brother scanner over a network, I need to run this command:

```
Step 5. Setting for your network scanner
[HR][/HR]*****Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.**[HR][/HR]5-1. Add network scanner entry Command  :  brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
 

```

[http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

Another possibility would be to download a trial of VueScan and see if your networked Canon is detected. You'd need to purchase a license to remove the watermark from scanned images but you can determine whether or not your Canon scanner functions as expected without purchasing anything.

[http://www.hamrick.com/](http://www.hamrick.com/)

VueScan when extracted is a binary and two other files. It does not need to be installed, double-clicking the binary should launch the app.

Sorry for being a bit long winded.

---

### Post by tray2 on 2014-10-26
Hi,

I hope this is not hijacking the thread, but am I correct in understanding that wireless scanning is not possible with Lubuntu 14.04? I have an HP Photosmart 7515, and would like to 'Scan to File' using wireless, but have not yet found a suitable driver. Do you have any guidance on this?

Thanks,
Tray

---

### Post by pqwoerituytrueiwoq on 2014-10-26
> **tray2 said:**
> Hi,

I hope this is not hijacking the thread, but am I correct in understanding that wireless scanning is not possible with Lubuntu 14.04? I have an HP Photosmart 7515, and would like to 'Scan to File' using wireless, but have not yet found a suitable driver. Do you have any guidance on this?

Thanks,
Tray
if you have a computer (or low profile mini pc like a rPi) hooked to it via you can via the software in my signature

---

### Post by kurt18947 on 2014-10-27
> **tray2 said:**
> Hi,

I hope this is not hijacking the thread, but am I correct in understanding that wireless scanning is not possible with Lubuntu 14.04? I have an HP Photosmart 7515, and would like to 'Scan to File' using wireless, but have not yet found a suitable driver. Do you have any guidance on this?

Thanks,
Tray

I can scan wirelessly on a Brother MFD.  I have the Brother connected via ethernet to a wireless router. I don't know about scanning via an adhoc connection, I've never tried that. It appears a Samsung MFD supports wireless scanning via a wireless router as well.

---

