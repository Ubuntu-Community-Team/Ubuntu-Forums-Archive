---
title: "Can't run MS Office 2007 with Wine"
date: 2010-09-10
forum: Wine
---

### Post by jre6 on 2010-09-10
Ubuntu comes with OpenOffice.org, but I was just frustrated after seeing the inability of OpenOffice to open and display MS Office files correctly and installed Wine 1.0.1 to use MS Office. Since it would not run directly, I tried [this]("http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/") but after having done all these, MS Office still didn't work.

Here is some output from the terminal:
```

someuser@ubuntu:~$ wine /media/disk/Program\ Files/Microsoft\ Office/Office12/WINWORD.EXE
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\WINWORD.EXE" failed, status c0000135
someuser@ubuntu:~$ wine /media/disk/Program\ Files/Microsoft\ Office/Office12/POWERPNT.EXE
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\POWERPNT.EXE") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\ppcore.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\oart.dll") not found
err:module:import_dll Library oart.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\ppcore.dll") not found
err:module:import_dll Library ppcore.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\POWERPNT.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\POWERPNT.EXE" failed, status c0000135
someuser@ubuntu:~$ wine /media/disk/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\EXCEL.EXE") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\oart.dll") not found
err:module:import_dll Library oart.dll (which is needed by L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\EXCEL.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\disk\\Program Files\\Microsoft Office\\Office12\\EXCEL.EXE" failed, status c0000135

```Please help.

---

### Post by cake nom nom on 2010-09-10
That doesn't sound right, what type of files are you trying to open?

---

### Post by jre6 on 2010-09-10
> **cake nom nom said:**
> That doesn't sound right, what type of files are you trying to open?

The .docx , .pptx , .xlsx and the like aren't displayed properly. The text boxes lose their color, the alignment is destroyed and each and my document is a mess. And, OpenOffice doesn't allow me to do everything that I do on MS Office.

---

