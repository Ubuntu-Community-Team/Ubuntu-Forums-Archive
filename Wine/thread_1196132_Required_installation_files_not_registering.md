---
title: "Required installation files not registering?"
date: 2009-06-24
forum: Wine
---

### Post by ZeldaFan on 2009-06-24
I am trying to install Crossfire Commander (a chemistry database program), and the installation proceeds fine but I receive an error at the end that:

The following files did not self-register or unregister:
C:\Program Files\MDL CrossFire Commander 7.0\SPOR32X30.ocx

C:\Program Files\MDL CrossFire Commander 7.0\dcrossfiretoword.dll

C:\Program Files\MDL CrossFire Commander 7.0\crossfiretoword.dll

As a result, the program will not run. Therefore, is there anyway to "register" these files or solve the issue?

---

### Post by qwertymn on 2009-06-25
try 'winetricks mfc42'

If that doesn't help, paste the complete console output

---

### Post by NightMKoder on 2009-06-25
You could always try to register them manually

wine regsvr32 SPOR32X30.ocx

and the other 2.

---

### Post by BoudewijnD on 2010-04-13
I found this thread because I also want to run crossfire commander. The winetrick did the job for running the program but I was unable to use the search button. than the programs hangs. here is the terminal code:
```
boudewijn@boudewijn-laptop:~/.wine/dosdevices/c:/Program Files/CrossFire Commander 7.1$ wine XfCm.exe 
fixme:mscoree:_CorDllMain (0x3b0000, 1, (nil)): stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\CrossFire Commander 7.1\\crossfiretoword.dll") not found
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\CrossFire Commander 7.1\\dcrossfiretoword.dll") not found
fixme:shdocvw:PersistMemory_Load (0x1d5230)->(0x7227a4 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x1d5230)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1d5230)->(0)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0x717eb984, overlapped 0x717eb968): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x3e5ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1d52cc)->((null) 1 0x273c0ac (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 25 2 0x273c0c0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 26 2 0x273c0c0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1d52cc)->(0x273c104)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x273c1c0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x273c250)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 29 2 0x273dae4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1d52cc)
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClientSite_GetContainer (0x1d52cc)->(0x273d1f4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1d52cc)->(0xb778ab71)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 25 2 0x273d100 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 26 2 0x273d100 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x273da24)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x273da24)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 26 2 0x273dac4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 29 2 0x273dad4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1d52cc)->(0x7bca5530)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 28 2 0x273da24 (nil))
fixme:mshtml:HTMLElement_get_innerText (0x1eb640)->(0x273de74)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1d52cc)->((null) 21 2 (nil) (nil))
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()

```

I was also unable to register the ddl's. So maybe some help on that as well. :D

\Boudewijn

---

### Post by asdfoo on 2010-04-13
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\CrossFire Commander 7.1\\crossfiretoword.dll") not found
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\CrossFire Commander 7.1\\dcrossfiretoword.dll") not found


use winetricks to install vbrun6

---

### Post by BoudewijnD on 2010-04-14
I installed vburn6 but when I search the programs stops. 

Do I need to register the ddl manualy?? And how can I do that.

Cheers,

\BoudewijnD

---

