---
title: "HMRC 2009 Software in Wine ubuntu?"
date: 2009-05-03
forum: Wine
---

### Post by higgylm on 2009-05-03
Hi there,

First of all thanks for looking,

I have been using wine under ubuntu to run the HM Revenue & Customs Employer Software 2008 to file my tax returns.

Unfortunately HMRC have decided to change a few things in the new 2009 update of the software and I can no longer get it run under wine,

(Its probably a simple fix but I haven't the experience to sort it) 

Anyway, here's the out from wine when calling the exe

```
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_net_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_net_vc.dll") not found
err:module:import_dll Library wxbase28uh_net_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library wxmsw28uh_core_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library wxmsw28uh_core_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_adv_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_adv_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_adv_vc.dll") not found
err:module:import_dll Library wxmsw28uh_adv_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_net_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_net_vc.dll") not found
err:module:import_dll Library wxbase28uh_net_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library wxmsw28uh_core_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_core_vc.dll") not found
err:module:import_dll Library wxmsw28uh_core_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_adv_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxbase28uh_vc.dll") not found
err:module:import_dll Library wxbase28uh_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_adv_vc.dll") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\wxmsw28uh_adv_vc.dll") not found
err:module:import_dll Library wxmsw28uh_adv_vc.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\HMRC\\Employer CD-ROM 2009\\python\\_core_.pyd") not found
```

Any Help is greatly appreciated,

Thanks

---

### Post by higgylm on 2009-05-03
SOLVED: After exploring the disk a bit more I discovered a native linux version of the software

---

### Post by akoskm on 2009-05-03
The error log says that the program cannot find this file: *MSVCP71.dll*. You can download dll files free from this site:
[www.dll-files.com]("www.dll-files.com").
Good luck.

---

