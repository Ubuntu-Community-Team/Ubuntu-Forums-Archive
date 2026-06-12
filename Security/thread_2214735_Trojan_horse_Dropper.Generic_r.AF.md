---
title: "Trojan horse Dropper.Generic_r.AF"
date: 2014-04-02
forum: Security
---

### Post by SuperFreak on 2014-04-02
I have scanned my .WINE directory and found this:
```
You are currently up-to-date
Update was successfully completed.
david@MainSqueeze:~$ sudo avgscan /home/david/.wine
AVG command line Anti-Virus scanner
Copyright (c) 2013 AVG Technologies CZ

Virus database version: 3722/7286
Virus database release date: Wed, 02 Apr 2014 08:20:00 -0400

/home/david/.wine/drive_c/windows/syswow64/ddhelp.exe  Corrupted executable file
/home/david/.wine/drive_c/windows/syswow64/dsound.vxd  Corrupted executable file
/home/david/.wine/drive_c/windows/syswow64/dosx.exe  Corrupted executable file
/home/david/.wine/drive_c/users/david/Local Settings/Temporary Internet Files/Content.IE5/GF18X0XI/tpq[0]  Trojan horse Dropper.Generic_r.AF
/home/david/.wine/drive_c/users/david/Local Settings/Temporary Internet Files/Content.IE5/GF18X0XI/completeappp[2]  Adware Generic5.APDD
/home/david/.wine/drive_c/users/david/Local Settings/Temporary Internet Files/Content.IE5/GF18X0XI/completeappp[0]  Adware Generic5.APDD
/home/david/.wine/drive_c/users/david/Local Settings/Temporary Internet Files/Content.IE5/GF18X0XI/completeappp[1]  Adware Generic5.APDD
/home/david/.wine/drive_c/users/david/Local Settings/Temporary Internet Files/Content.IE5/C7NVUH1X/completeappp[0]  Adware Generic5.APDD
/home/david/.wine/dosdevices/g::  Object scan failed; Specified file was not found.
/home/david/.wine/dosdevices/f::  Object scan failed; Specified file was not found.
/home/david/.wine/dosdevices/i::  Object scan failed; Specified file was not found.
/home/david/.wine/dosdevices/e::  Object scan failed; No medium found

Files scanned     :  19173(9313)
Infections found  :  1(1)
PUPs found        :  4
Files healed      :  0
Warnings reported :  3
Errors reported   :  4

```

Deleted the /home/david/.wine/drive_c/users/david/Local Settings/Temporary Internet Files/Content.IE5 folder contents completely and reran AVG which found no more viruses.

Am I done at this point? 

I am soon going for a clean install of 14.04 when it is released but unfortunately my wife inadvertently downloaded a bunch of .exe files and I think it led to this infection in my WINE  folders. I believe I have routed evrything out and I know it being a Ubuntu machine there is hopefully little chance of it infecting system directories. Or should I be worried?

---

### Post by CharlesA on 2014-04-02
Clean your temp internet files and be done with it. :)

---

### Post by SuperFreak on 2014-04-02
Thanks I did that. To be sure I uninstalled Wine and all programs under it as I don't think I will need it in the next few weeks

---

