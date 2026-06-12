---
title: "WMware and Win98SE"
date: 2008-07-24
forum: Virtualisation
---

### Post by Living2007 on 2008-07-24
OK, Hands up all the people who have used a Virtual Machine, OK, now all the people who are having problems with 98 regarding Sound and Ethernet. oh, So far only me!
 
As you just read, i am having problems with Windows 98 regarding Sound and Ethernet connection. Windows is detecting and Unknown device, when it is literally part of the Motherboard. It is detecting it as a PCI Ethernet Controller and PCI Multimedia Audio *something*.
 
I also tried looking for a driver on my Motherboard CD. I may have not looked hard enough.
 
Any thread bumps, or tips and tricks will be greatly appreciated. Cheers
 
PS. For those who wonder how long I have been off for, it has been 6 weeks since my last post.

---

### Post by Living2007 on 2008-07-31
Not one reply yet! Don't worry I can wait*

This is just a bump!

*Not Forever!

---

### Post by Zalbor on 2008-08-14
I never had a problem with the ethernet on mine...
As for the sound, there's a driver that worked fine. However I don't remember where I found it... The program's name is "SBPCI_WebDrvsV5_12_01.exe".

---

### Post by Living2007 on 2008-08-14
> **Zalbor said:**
> I never had a problem with the ethernet on mine...
As for the sound, there's a driver that worked fine. However I don't remember where I found it... The program's name is "SBPCI_WebDrvsV5_12_01.exe".
Where about's is it found?

P.S. What drivers are you using for the Ethernet and Audio?

---

### Post by chungy on 2008-08-15
Install Intel PRO/1000 drivers for the ethernet: [http://www.intel.com/support/network/sb/cs-006120.htm](http://www.intel.com/support/network/sb/cs-006120.htm)

---

### Post by Zalbor on 2008-08-16
I said I don't remember where I found it, sorry. But I think there was a thread here, try a search.

---

### Post by Shazaam on 2008-08-16
A link...
[http://communities.vmware.com/message/458456;jsessionid=048ED3E8DEA4559DB1D8D63AEDB806DD](http://communities.vmware.com/message/458456;jsessionid=048ED3E8DEA4559DB1D8D63AEDB806DD)

Try here for the sound drivers on your Win98 guest...
[http://support.creative.com/Products/ProductDetails.aspx?catID=1&subCatID=207&prodID=1864&prodName=Sound%20Blaster%20PCI%20128&subCatName=Others&CatName=Sound+Blaster](http://support.creative.com/Products/ProductDetails.aspx?catID=1&subCatID=207&prodID=1864&prodName=Sound%20Blaster%20PCI%20128&subCatName=Others&CatName=Sound+Blaster)

---

### Post by Living2007 on 2008-08-17
Well, thank you to those people who posted back. I now have sound with the Creative Labs driver, Thank you.

But the Intel Pro/1000 doesn't work ([http://www.intel.com/support/network/sb/cs-006120.htm](http://www.intel.com/support/network/sb/cs-006120.htm)) because the driver (discovered by Everest Home Ed.) is in fact a Intel 82545 Gigabit Ethernet (Copper).

Where would you find the driver for this.

PS: Also can you connect 2 VM on the same computer w/o a router?

---

