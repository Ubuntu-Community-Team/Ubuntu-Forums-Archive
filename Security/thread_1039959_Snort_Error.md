---
title: "Snort Error"
date: 2009-01-15
forum: Security
---

### Post by 3dmatrix on 2009-01-15
I have installed Snort but when I run the command
[COLOR="DimGray"]snort -A full -c /etc/snort/snort.conf[/COLOR]
I get the following error,
[COLOR="DimGray"]Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
ERROR: Unable to open rules file: /etc/snort/snort.conf or /etc/snort/snort.conf
Fatal Error, Quitting..[/COLOR]
What is going wrong ?

---

### Post by utnubuuser on 2009-01-15
Are you sure it installed properly? Tried re-installing?

---

### Post by 3dmatrix on 2009-01-15
Reinstalled the four packages from Synaptic but the error persists.

---

### Post by The Tronyx on 2009-01-15
> 
/etc/snort/snort.conf or /etc/snort/snort.conf


And do both of these files exist?  What user level are you trying to start snort as?  What are the permissions on the 2 files listed above?  Have you tried sudo?

---

### Post by 3dmatrix on 2009-01-15
Both the paths refer to the same file. And that file exists.
I tried sudo and it seems to be working that way. After a long length of reporting it displayed :
[COLOR="DimGray"]
 --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.7.0 (Build 35)  
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           (C) Copyright 1998-2007 Sourcefire Inc., et al.

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.6  <Build 11>
           Preprocessor Object: SF_FTPTELNET  Version 1.0  <Build 10>
           Preprocessor Object: SF_SSH  Version 1.0  <Build 1>
           Preprocessor Object: SF_DCERPC  Version 1.0  <Build 4>
           Preprocessor Object: SF_DNS  Version 1.0  <Build 2>
           Preprocessor Object: SF_SMTP  Version 1.0  <Build 7>
Not Using PCAP_FRAMES
[/COLOR]
Do you think its working fine ? If so how can I make it start automatically after every boot ?

---

### Post by cjacobsen on 2009-01-23
Have you updated the snort rules? I got a few errors like this because I didn't update the rules properly using Oinkmaster.

First try uninstall agin with these commands:
sudo apt-get --purge remove snort (or snort-mysql)
sudo apt-get --purge autoremove 

the delete all the remaining files with:
sudo rm -fr /etc/snort

Then try to install agian.

I have covered SNORT in my howto series on Ubuntu security on my blog (see signature). Snort is covered in part IV I believe.

---

### Post by wirelessmonkey on 2009-01-23
I recently had this issue, it turns out that you just need to set the rules variable correctly.  To do this, edit /etc/snort/snort.conf
on or around line 193 you'll see
```
var RULE_PATH ../rules
```
change it to read
```
var RULE_PATH /etc/snort/rules
```

then restart snort
```
sudo /etc/init.d/snort restart 
```

That should do it...

---

