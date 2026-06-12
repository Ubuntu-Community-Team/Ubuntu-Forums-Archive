---
title: "Sending a Fax using PHP on Ubuntu Server?"
date: 2011-02-24
forum: Server Platforms
---

### Post by CrusaderAD on 2011-02-24
Does anyone have any info on setting up faxing capabilities on Ubuntu Server with a PHP page? I'm not interested in an online service, so please don't post those. Any help would be appreciated.

---

### Post by HugoSerrano on 2011-02-24
Hi, check Hylafax and Avantfax

Regards.

---

### Post by CrusaderAD on 2011-02-24
Thanks, I found those but they seemed geared towards Fedora and implementing them looks time consuming. Any other ideas?

---

### Post by CrusaderAD on 2011-02-24
Does anyone know if Hylafax and Avantfax absolutely requires a modem or can it be done completely through Ethernet?

---

### Post by SeijiSensei on 2011-02-24
You're sending a fax.  Of course you need a modem.

Hylafax can be configured to convert emailed documents to faxes and send them out.  I think that would be the best solution to use with a PHP application.

---

### Post by CrusaderAD on 2011-02-24
Thanks for the info. Then what does FOIP mean? You need a modem and analog line to send and receive faxes with a linux server?

---

### Post by headvampyre@hotmail.co.uk on 2011-02-24
FoIP is Fax over Internet Protocol, basically, if you use that it should be capable over ethernet, but only for a LAN/WAN (i think).

---

### Post by SeijiSensei on 2011-02-24
If you're intending to send faxes to normal fax machines that are connected to telephone lines, you need a modem.  Faxing over IP would require that the receiving device support that protocol.  Perhaps that's true for your specific situation, but FOIP certainly would exclude the vast majority of fax machines in the world.

---

### Post by CrusaderAD on 2011-02-24
> **SeijiSensei said:**
> If you're intending to send faxes to normal fax machines that are connected to telephone lines, you need a modem.  Faxing over IP would require that the receiving device support that protocol.  Perhaps that's true for your specific situation, but FOIP certainly would exclude the vast majority of fax machines in the world.

I see, so do you think I wouldn't be able to fax to an analog fax machine unless I use analog? FOIP is only to FOIP?

---

### Post by SeijiSensei on 2011-02-24
Does the analog fax machine have a network connection?  Can you ping it by IP address over the network/Internet?  If the answers to these questions are no, then you need to use a modem.

By the way, if you need to buy a modem, [this]("http://cgi.ebay.com/USROBOTICS-56K-COURIER-V-EVERYTHING-MODEM-/300526375331?pt=PCC_Modems&hash=item45f8c491a3") is the one you want.  (I originally paid $300 or so for these back in the day.)

---

### Post by elico on 2011-02-24
well you can always use a FAX-to-MAIL and MAIL-to-FAX or INTERNET base fax such as VOIP(SIP or other) server.

---

### Post by CrusaderAD on 2011-02-24
> **elico said:**
> well you can always use a FAX-to-MAIL and MAIL-to-FAX or INTERNET base fax such as VOIP(SIP or other) server.

How do you use FAX-to-MAIL? Searching around doesn't provide much.

---

### Post by Vegan on 2011-02-24
I have a brother MFC-544CN that can handle all the fax services.

The problem is that Brother still does not support Linux even though the printer is on the LAN.

Conexant is the maker of semiconductors for the sector now and they are now supporting all operating systems so that their chips are as widely used as can be.

I have not seen fax as a printer for Linux like the service in Windows.

So find a cheap Conexant modem and expect to use lots of C++ in addition to PHP to achieve that.

---

