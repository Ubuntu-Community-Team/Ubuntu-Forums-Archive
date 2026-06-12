---
title: "wine is not opening at all"
date: 2009-08-12
forum: Wine
---

### Post by rhythmiccycle on 2009-08-12
i just installed wine, i did it before on my other computer and it worked fine,

when i got to "browse c:/ drive" the screen flickers and nothing happens

i also tried to open a program from the termainal this is what happend:

```
mjm@ubuntu:/host/Program Files/Adobe/Adobe Dreamweaver CS4$ wine Dreamweaver.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\xerces-c_2_7.dll") not found
err:module:import_dll Library xerces-c_2_7.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobePSL.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobePSL.dll") not found
err:module:import_dll Library AdobePSL.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Fireworks Library.dll") not found
err:module:import_dll Library Fireworks Library.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\NetIO.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\LIBCURL.dll") not found
err:module:import_dll Library LIBCURL.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\NetIO.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\NetIO.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\NetIO.dll") not found
err:module:import_dll Library NetIO.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\LIBCURL.dll") not found
err:module:import_dll Library LIBCURL.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libapr.dll") not found
err:module:import_dll Library libapr.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libapr.dll") not found
err:module:import_dll Library libapr.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libaprutil.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libapr.dll") not found
err:module:import_dll Library libapr.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libapriconv.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libapriconv.dll") not found
err:module:import_dll Library libapriconv.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libaprutil.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\libaprutil.dll") not found
err:module:import_dll Library libaprutil.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\neon.dll") not found
err:module:import_dll Library neon.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AlcidDLL.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AlcidDLL.dll") not found
err:module:import_dll Library AlcidDLL.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Workspace.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Workspace.dll") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\xerces-c_2_7.dll") not found
err:module:import_dll Library xerces-c_2_7.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Workspace.dll") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Workspace.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\host\\Program Files\\Adobe\\Adobe Dreamweaver CS4\\Dreamweaver.exe" failed, status c0000135
mjm@ubuntu:/host/Program Files/Adobe/Adobe Dreamweaver CS4$ 

```

what the problem?

---

### Post by myownserver on 2009-09-09
EXACT same problem here and I haven't found a solution yet.

I did find this one article, even though it's on Dreamweaver CS3, it could be a starting point to solving the issue with Dreamweaver CS4 and Wine.

[http://ubuntuforums.org/archive/index.php/t-879801.html](http://ubuntuforums.org/archive/index.php/t-879801.html)
(Go to the very bottom of that page and read the last couple of posts)

I tried installing the package he mentions fixed Dreamweaver CS3, but I have no clue how to do that in Ubuntu.

Hopefully someone with the right knowledge will come along, solve it, and write a kick-awesome tutorial to help all of us needing this fix.

---

