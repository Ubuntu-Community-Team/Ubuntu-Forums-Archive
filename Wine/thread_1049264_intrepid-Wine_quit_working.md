---
title: "intrepid-Wine quit working"
date: 2009-01-24
forum: Wine
---

### Post by caver1 on 2009-01-24
Using 64bit intrepid and my WINE quit working.
I can browse the c:/ drive but no programs will open I can't Uninstall them and I cannot configure wine.
I have gone as far as reinstalling WINE with no change.
Any ideas?
caver1

---

### Post by WatchingThePain on 2009-01-24
It's not always possible to run an application on builtin DLL's. Sometimes native DLL's simply work better. Altough these DLL overrides can be set using winecfg you might want to use the WINEDLLOVERRIDES environment variable to set them. 

For example, if you wanted wine to use native ole32.dll, oleaut32.dll and rpcrt4 you could run wine like this: 
$ WINEDLLOVERRIDES="ole32,oleaut32,rpcrt4=n" wine program_name
        
There are four DLL's you should never try to use the native versions of: kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll. These libraries require low-level Windows kernel access that simply doesn't exist within Wine. 

With that in mind, once you've copied the DLL you just need to tell Wine to try to use it. You can configure Wine to choose between native and builtin DLL's at two different levels. If you have Default Settings selected in the Applications tab, the changes you make will affect all applications. Or, you can override the global settings on a per-application level by adding and selecting an application in the Applications tab. 

To add an override for FOO.DLL, enter "FOO" into the box labeled New override for library: and click on the Add button. To change how the DLL behaves, select it within the Existing overrides: box and choose Edit. By default the new load order will be native Windows libraries before Wine's own builtin ones (Native then Builtin). You can also choose native only, builtin only, or disable it altogether.

---

### Post by caver1 on 2009-01-24
The problem I have is that everything has worked for at least a year and has just stopped working.
caver1

---

