---
title: "can't run winetricks"
date: 2010-10-22
forum: Wine
---

### Post by bandito40 on 2010-10-22
Hi,

I have been trying to install winetricks on 10.04.1 LTS but I am having no success.  Does anyone know what the problem is?  I get the following errors:


wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
winetricks: 4382: cannot create /home/bandito/.wine/dosdevices/c:/winetrickstmp/zenity.sh: Permission denied
winetricks: 4382: cannot create /home/bandito/.wine/dosdevices/c:/winetrickstmp/zenity.sh: Permission denied
sh: Can't open /home/bandito/.wine/dosdevices/c:/winetrickstmp/zenity.sh


Thanks in advance!

---

### Post by tadaskr on 2010-10-23
same problem for me. I can't install d3dx9 from winetricks:
> Extracting cabinet: /home/tadas/.winetrickscache/directx_feb2010_redist.exe
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/apr2005_d3dx9_25_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/apr2005_d3dx9_25_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/apr2006_d3dx9_30_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/apr2006_d3dx9_30_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/apr2007_d3dx9_33_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/apr2007_d3dx9_33_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2005_d3dx9_27_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2005_d3dx9_27_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2007_d3dx9_35_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2007_d3dx9_35_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2008_d3dx9_39_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2008_d3dx9_39_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2009_d3dx9_42_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/aug2009_d3dx9_42_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/dec2005_d3dx9_28_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/dec2005_d3dx9_28_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/dec2006_d3dx9_32_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/dec2006_d3dx9_32_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/feb2005_d3dx9_24_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/feb2005_d3dx9_24_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/feb2006_d3dx9_29_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/feb2006_d3dx9_29_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/jun2005_d3dx9_26_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/jun2005_d3dx9_26_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/jun2007_d3dx9_34_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/jun2007_d3dx9_34_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/jun2008_d3dx9_38_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/jun2008_d3dx9_38_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/mar2008_d3dx9_37_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/mar2008_d3dx9_37_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/mar2009_d3dx9_41_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/mar2009_d3dx9_41_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/nov2007_d3dx9_36_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/nov2007_d3dx9_36_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/nov2008_d3dx9_40_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/nov2008_d3dx9_40_x86.cab: Permission denied
  extracting /home/tadas/.wine/dosdevices/c:/winetrickstmp/oct2006_d3dx9_31_x86.cab
/home/tadas/.wine/dosdevices/c:/winetrickstmp/oct2006_d3dx9_31_x86.cab: Permission denied

All done, errors in processing 19 file(s)
------------------------------------------------------
Note: command '/usr/bin/cabextract -d /home/tadas/.wine/dosdevices/c:/winetrickstmp -L -F *d3dx9*x86* /home/tadas/.winetrickscache/directx_feb2010_redist.exe' returned status 1.  Aborting.
------------------------------------------------------


---

### Post by bandito40 on 2010-10-25
I did this command from my home directory.

> bandito@bandito1:~$ sudo chmod -R  777 .wine

now I get the library selection window when I run with this command 

> sh winetricks

but when I try to install a library i get the following error.
> 
Note: command 'wget -O cc32inst.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/platformsdk/redist/5.80.2614.3600/w9xnt4/en-us/cc32inst.exe](http://download.microsoft.com/download/platformsdk/redist/5.80.2614.3600/w9xnt4/en-us/cc32inst.exe)' returned status 1.  Aborting.


Seems like I can't connect to the Microsoft website. Anyone knows why?

Thanks,

Carl

---

### Post by bandito40 on 2010-10-27
Actually if I just copy the link ([http://download.microsoft.com/download/platformsdk/redist/5.80.2614.3600/w9xnt4/en-us/cc32inst.exe]("http://download.microsoft.com/download/platformsdk/redist/5.80.2614.3600/w9xnt4/en-us/cc32inst.exe")) then it will download. Just not sure what to do with the file afterwards.

---

