---
title: "Can't use Brother Scanner"
date: 2016-03-28
forum: Ubuntu/Debian BASED
---

### Post by dallase1 on 2016-03-28
I can't use my Brother MFC-L8850CDW's Scanner, I can use the printer feature of it just fine but not the Scanner.
It was working at one time but now has stopped working in Linux works fine in Windows 7 but the program from Brother Stinks.

When I try to open a scanning program like Xsane I got some kind of error message about an invalid augment.
I did a complete removable of all the SANE Drivers and then reinstalled them reinstalled the Brother Linux Drivers from Brothers Webpage and got the 
invalid augment error message again so I tried uninstalling the Brothe Drivers again but could not uninstal one driver brscan in s   	 	 	 	   (Reading database ... 1007199 files and directories currently installed.)  
 Removing brscan ...  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory  
 dpkg: error processing brscan (--remove):  
  subprocess installed post-removal script returned error exit status 1  
 No apport report written because MaxReports is reached already  
                                                               Errors were encountered while processing:  
  brscan  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
 A package failed to install.  Trying to recover:  

 when I try to remove the brscan driver in Synaptic Package Manager

   by selecting mark for complete removable and when I click apply I get 
   
   
(Reading database ... 1007199 files and directories currently installed.)  
 Removing brscan ...  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory 
 rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory  
 rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory  
 dpkg: error processing brscan (--remove):  
  subprocess installed post-removal script returned error exit status 1  
 No apport report written because MaxReports is reached already  
                                                               Errors were encountered while processing:  
  brscan  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
 A package failed to install.  Trying to recover:  
 
I can't unmark it and when I exit Synaptic Package Manager I get the message "Quit and discard marked changes ?"
"There are still marked changes that have not been applied they will get lost if you choose quit Synaptic" 



Now when try to install the scanner drivers I get could not install all depedenicies and
the same errormessage 

```
(Reading database ... 1007199 files and directories currently installed.)
Removing brscan ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bucky Ball on 2016-03-28
Could you provide a link to the Brother webpage you are getting the drivers from and tell us which version and flavour of Ubuntu you are using, please?

Also, use code tags for terminal output (see example in your last terminal output, last post). See the link in my signature at the bottom of this post for how. Thanks.

---

### Post by billrbilly on 2016-03-28
I use this link to setup my laser
 printer scanner brother model
[URL="http://askubuntu.com/questions/486699/brother-dcp-7065dn-ubuntu-14-04-64bit-can-print-to-network-printer-but-cannot"]http://askubuntu.com/questions/486699/brother-dcp-7065dn-ubuntu-14-04-64bit-can-print-to-network-printer-but-cannot

[COLOR=#000000]download your correct drivers for your model[/COLOR]
[/URL]

---

### Post by SeijiSensei on 2016-03-29
Usually the easiest solution for Brother products is to download and run the "Driver Install Tool" from Brother's site.  For your device it appears to be on this page: [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl8850cdw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl8850cdw_us_eu_as&os=128)

---

### Post by dallase1 on 2016-03-30
I got the drivers from 
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl8850cdw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcl8850cdw_us_eu_as&os=128)

I'm using 
Cylon 12.04 32-bit Release 12.04 (precise) 32-bit
Kernel Linux 3.2.0-101-generic-pae
GNOME 3.4.2

I can't install the drivers because I get an error from the brscan driver in Synaptic Package Manager and anytime I install any updates I get a partial install message because of the brscan driver problem and I can't un mark it in Synaptic Package Manager and get the brscan  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
 A package failed to install.  Trying to recover: error message.

I don't know what coded tags are

---

### Post by joverstreet1 on 2016-03-30
Go back to the Brother support page, find the installer for your particular flavor of Linux, make sure you do all of the things that are applicable in the prerequisites before installing the driver install tool, and after you finish installing the driver install tool, get your scanner function working by following the instructions at:

[http://ubuntuforums.org/archive/index.php/t-2274746.html](http://ubuntuforums.org/archive/index.php/t-2274746.html)

Good luck.

---

### Post by Bucky Ball on 2016-03-30
*Thread moved to **(unknown)**.*

> **dallase1 said:**
> 
I'm using 
Cylon 12.04 32-bit Release 12.04 (precise) 32-bit


You should have mentioned this earlier. Not supported in the main support areas here. ***Official Flavours Support*** and ***Specialised Support*** areas are for "... questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu and Ubuntu Mate."

---

### Post by dallase1 on 2016-03-31
none of this works because I Can't uninstall the old brscan driver in [COLOR=#000000]Synaptic Package Manager and it effects Linus updates because of the brscan driver. I can't unmark it



[/COLOR][ATTACH=CONFIG]268094[/ATTACH]

---

