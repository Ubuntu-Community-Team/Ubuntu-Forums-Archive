---
title: "Virtualbox 2.1 won't launch in 8.10"
date: 2009-01-09
forum: Virtualisation
---

### Post by ngpsaki4 on 2009-01-09
The solution was really simple. Delete the referenced .xml file. It is re-written when xVM VB launches, and the program loads and runs as it is supposed to.

I am having an install problem with xVM VB 2.1 in Intrepid, also. The error message I get back is:

Could not load the settings file '/home/nick/.VirtualBox/VirtualBox.xml'.
Element '{http://www.innotek.de/VirtualBox-settings}SystemProperties',
attribute 'defaultHardDiskFolder': [facet 'pattern'] The value '' is not accepted by the pattern '.+'.
Element '{http://www.innotek.de/VirtualBox-settings}SystemProperties',
attribute 'defaultHardDiskFolder': '' is not a valid value of the atomic type '{http://www.innotek.de/VirtualBox-settings}TLocalFile'.


Result Code:
VBOX_E_XML_ERROR (0x80BB000A)
Component:
VirtualBox
Interface:
IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}

I am not versed enough in Linux yet to parse this problem. I downloaded and reinstalled 2.1 from Sun's website, but got the same error. I tried to look at the referenced .xml file, but it was not well-formed, according to Firefox, so I gave up.

Any advice or suggestions from the seasoned veterans in this forum?

Thanks,

Nick

---

### Post by Dedoimedo on 2009-01-09
Try the following:

Uninstall VB. Rename or delete the .VirtualBox folder in your home directory. Then reinstall and see if this clears the error. Of course, if you have data saved in that directory, then back it up by all means.

Dedoimedo

---

