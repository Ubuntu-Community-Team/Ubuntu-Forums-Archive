---
title: "WINE: Burraco On Line"
date: 2010-05-23
forum: Wine
---

### Post by manolomanolo on 2010-05-23
Hi to all.

Wine oes not permit me to play BurrconOnLine executabes. I downloaded the client from [http://www.burraconline.com/downloads.asp](http://www.burraconline.com/downloads.asp)
and run the installation with Wine 1.1.42

The applicaton is not in the *Application -> Wine* menu. Browsing the installation folder, when double clicking on BurracoClient.exe I get the following error

```
Archive:  /home/mariella/.wine/dosdevices/c:/Programmi/Burraconline/BurracoClient.exe
[/home/mariella/.wine/dosdevices/c:/Programmi/Burraconline/BurracoClient.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/mariella/.wine/dosdevices/c:/Programmi/Burraconline/BurracoClient.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/mariella/.wine/dosdevices/c:/Programmi/Burraconline/BurracoClient.exe or
          /home/mariella/.wine/dosdevices/c:/Programmi/Burraconline/BurracoClient.exe.zip, and cannot find /home/mariella/.wine/dosdevices/c:/Programmi/Burraconline/BurracoClient.exe.ZIP, period.
```

Any suggestion please?
Thanks.

---

### Post by philinux on 2010-05-23
Moved to WINE forum.

---

### Post by ronnielsen1 on 2010-05-23
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19927](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19927)

> 1) wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
2) sh winetricks allfonts dotnet11
3) sh winetricks dotnet20
4) sh winetricks gdiplus 
5) wine setup_bc_4_53_76.exe
6) play!

(I installed the gdiplus.dll manually, but shoulds work with winetricks too)


---

### Post by manolomanolo on 2010-05-23
ronnielsen1, it works!

Thanks very much!

---

### Post by ronnielsen1 on 2010-05-24
Winehq is a great place. You can check the compatibility of windows software.

---

### Post by manolomanolo on 2010-05-28
I do managed to install the program but I am unable to run it correctly.

I get the following error and as a result sometimes the application crashes and that's not funny :)

How could I solve the problem?
Thank you.

```
See the end of this message for details on invoking 
just-in-time (JIT) debugging instead of this dialog box.

************** Exception Text **************
System.NotImplementedException: The method or operation is not implemented.
   at System.Windows.Forms.UnsafeNativeMethods.IHTMLElement2.InsertAdjacentElement(String where, IHTMLElement insertedElement)
   at System.Windows.Forms.HtmlElement.InsertAdjacentElement(HtmlElementInsertionOrientation orient, HtmlElement newElement)
   at System.Windows.Forms.HtmlElement.AppendChild(HtmlElement newElement)
   at by.b()
   at ap.k(Object A_0, EventArgs A_1)
   at System.Windows.Forms.Form.OnLoad(EventArgs e)
   at ap.a(EventArgs A_0)
   at System.Windows.Forms.Form.OnCreateControl()
   at System.Windows.Forms.Control.CreateControl(Boolean fIgnoreVisible)
   at System.Windows.Forms.Control.CreateControl()
   at System.Windows.Forms.Control.WmShowWindow(Message& m)
   at System.Windows.Forms.Control.WndProc(Message& m)
   at System.Windows.Forms.ScrollableControl.WndProc(Message& m)
   at System.Windows.Forms.ContainerControl.WndProc(Message& m)
   at System.Windows.Forms.Form.WmShowWindow(Message& m)
   at System.Windows.Forms.Form.WndProc(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.OnMessage(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.WndProc(Message& m)
   at System.Windows.Forms.NativeWindow.Callback(IntPtr hWnd, Int32 msg, IntPtr wparam, IntPtr lparam)


************** Loaded Assemblies **************
mscorlib
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll
----------------------------------------
BurracoClient
    Assembly Version: 4.53.0.82
    Win32 Version: 4.53.0.82
    CodeBase: file:///C:/Programmi/Burraconline/BurracoClient.exe
----------------------------------------
System.Windows.Forms
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll
----------------------------------------
System
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System/2.0.0.0__b77a5c561934e089/System.dll
----------------------------------------
System.Drawing
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
----------------------------------------
System.Management
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Management/2.0.0.0__b03f5f7f11d50a3a/System.Management.dll
----------------------------------------
System.Configuration
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
----------------------------------------
System.Xml
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll
----------------------------------------
System.Web
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_32/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll
----------------------------------------

************** JIT Debugging **************
To enable just-in-time (JIT) debugging, the .config file for this
application or computer (machine.config) must have the
jitDebugging value set in the system.windows.forms section.
The application must also be compiled with debugging
enabled.

For example:

<configuration>
    <system.windows.forms jitDebugging="true" />
</configuration>

When JIT debugging is enabled, any unhandled exception
will be sent to the JIT debugger registered on the computer
rather than be handled by this dialog box.



```

---

### Post by cogadh on 2010-05-28
Run the game from the terminal and get Wine's error output instead of the game's error output, it will be much more informative.

---

### Post by manolomanolo on 2010-05-28
I copied the command line invoked by the launcher that I find on my desktop after installing the program.

This is what I get from the moment when loading the program by terminal until the username and password is asked:

```
mano@mano-laptop:~$ **env WINEPREFIX="/home/mano/.wine" wine "C:\Programmi\Burraconline\BurracoClient.exe"** 
fixme:sync:CreateMemoryResourceNotification (0) stub
err:ole:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:win:EnumDisplayDevicesW ((null),0,0x32d988,0x00000000), stub!
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:shell:URL_ParseUrl failed to parse L"BurracoClient.resources"
fixme:shell:URL_ParseUrl failed to parse L"BurracoClient.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Management"
fixme:wbemprox:wbemprox_cf_QueryInterface interface {b196b28f-bab4-101a-b69c-00aa00341d07} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000144-0000-0000-c000-000000000046} not implemented
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:wbemprox:wbem_locator_ConnectServer 0x183a28, L"\\\\.\\root\\cimv2", (null), (null), L"", 0x00000080, L"", (nil), 0x41ddbfc)
fixme:wbemprox:wbemprox_cf_QueryInterface interface {b196b28f-bab4-101a-b69c-00aa00341d07} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000144-0000-0000-c000-000000000046} not implemented
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:wbemprox:wbem_locator_ConnectServer 0x184138, L"\\\\.\\root\\cimv2", (null), (null), L"", 0x00000080, L"", (nil), 0x42ddb7c)
fixme:wbemprox:wbemprox_cf_QueryInterface interface {b196b28f-bab4-101a-b69c-00aa00341d07} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000144-0000-0000-c000-000000000046} not implemented
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:wbemprox:wbem_locator_ConnectServer 0x1853e0, L"\\\\.\\root\\cimv2", (null), (null), L"", 0x00000080, L"", (nil), 0x41ddafc)
fixme:wbemprox:wbemprox_cf_QueryInterface interface {b196b28f-bab4-101a-b69c-00aa00341d07} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wbemprox:wbem_locator_QueryInterface interface {00000144-0000-0000-c000-000000000046} not implemented
fixme:ole:Context_QueryInterface interface not implemented {51372ae0-cae7-11cf-be81-00aa00a2fa25}
fixme:wbemprox:wbem_locator_ConnectServer 0x186690, L"\\\\.\\root\\cimv2", (null), (null), L"", 0x00000080, L"", (nil), 0x42dda7c)
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:ole:Context_CC_ContextCallback (0x186748/0x18674c)->(0x79f277a5, 0x2b2e4c8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x186748/0x18674c)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x186748/0x18674c)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x185498/0x18549c)->(0x79f277a5, 0x2b2e4c8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x185498/0x18549c)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x185498/0x18549c)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x1839a0/0x1839a4)->(0x79f277a5, 0x2b2e4c8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x1839a0/0x1839a4)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x1839a0/0x1839a4)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x183ed8/0x183edc)->(0x79f277a5, 0x2b2e4c8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x183ed8/0x183edc)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x183ed8/0x183edc)->(0x79f277a5, 0x2b2e45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:ras:RasEnumConnectionsW (0x17b668,0x32ef5c,0x32ef58),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:ras:RasConnectionNotificationW (0xffffffff,0x250,0x00000003),stub!
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:shdocvw:WebBrowser_QueryInterface (0x194d58)->({c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} 0x32d2ec) interface not supported
fixme:shdocvw:ProvideClassInfo_GetClassInfo (0x194d58)->(0x32d1c4)
fixme:shdocvw:WebBrowser_QueryInterface (0x194d58)->({00000003-0000-0000-c000-000000000046} 0x32d160) interface not supported
fixme:shdocvw:WebBrowser_QueryInterface (0x194d58)->({00000144-0000-0000-c000-000000000046} 0x32d1d8) interface not supported
fixme:shdocvw:WebBrowser_get_RegisterAsDropTarget (0x194d58)->(0x32dabc)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32da08:3; TargetFrameName 0x32d9e0:0)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32bcf4
fixme:iphlpapi:NotifyAddrChange (Handle 0x61be8d8, overlapped 0x61be8e0): stub
0[1baaf0]: IMM32: InitKeyboardLayout, aKeyboardLayout=04100410, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x194df8)->((null) 1 0x32c434 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x194df8)->(0x32c3fc)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4}
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {b196b283-bab4-101a-b69c-00aa00341d07}
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {00000003-0000-0000-c000-000000000046}
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {00000144-0000-0000-c000-000000000046}
fixme:shell:URL_ParseUrl failed to parse L"BurracoClient.resources"
fixme:shell:URL_ParseUrl failed to parse L"BurracoClient.resources"
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -701
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x194df8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:shdocvw:ClientSite_GetContainer (0x194df8)->(0x32ece0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x194df8)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:WebBrowser_get_RegisterAsDropTarget (0x194d58)->(0x32d38c)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x194d58)->(0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21

```

**This is what I get after inserting user and password until the error message comes out:**

```
fixme:ole:Context_CC_ContextCallback (0x1824f8/0x1824fc)->(0x79f277a5, 0x2b2e4c8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:shell:URL_ParseUrl failed to parse L"BurracoClient.resources"
fixme:shell:URL_ParseUrl failed to parse L"BurracoClient.resources"
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32dbc8:3; TargetFrameName 0x32dba0:0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32db78:3; TargetFrameName 0x32db50:0)
fixme:shell:URL_ParseUrl failed to parse L"System.Web"
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x194de8)->(0x32d668)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x194de8)->(0x32d668)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:InPlaceFrame_SetStatusText (0x194de8)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x194de8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:InPlaceFrame_SetStatusText (0x194de8)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x194de8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x194de8)->(L"Done")
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4}
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {b196b283-bab4-101a-b69c-00aa00341d07}
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {00000144-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x194de8)->(0x32bcac)
fixme:mshtml:HTMLDocument_put_charset (0x1926d8)->(L"unicode")
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:InPlaceFrame_SetStatusText (0x194de8)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x194de8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x194de8)->(L"Done")
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x194de8)->(0x32bcac)
fixme:mshtml:HTMLDocument_put_charset (0x1926d8)->(L"unicode")
fixme:mshtml:SupportErrorInfo_InterfaceSupportsErrorInfo (0x19272c)->({332c4425-26cb-11d0-b483-00c04fd90119})
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:InPlaceFrame_SetStatusText (0x194de8)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x194de8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:mshtml:HTMLElement2_insertAdjecentElement (0x63faff8)->(L"BeforeEnd" 0x5dee334 0x32db28)
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms.resources"


```

**And again this is what I get when pressing the DETAILS button (please, see the attached screenshot)**


```
See the end of this message for details on invoking 
just-in-time (JIT) debugging instead of this dialog box.

************** Exception Text **************
System.NotImplementedException: The method or operation is not implemented.
   at System.Windows.Forms.UnsafeNativeMethods.IHTMLElement2.InsertAdjacentElement(String where, IHTMLElement insertedElement)
   at System.Windows.Forms.HtmlElement.InsertAdjacentElement(HtmlElementInsertionOrientation orient, HtmlElement newElement)
   at System.Windows.Forms.HtmlElement.AppendChild(HtmlElement newElement)
   at by.b()
   at ap.k(Object A_0, EventArgs A_1)
   at System.Windows.Forms.Form.OnLoad(EventArgs e)
   at ap.a(EventArgs A_0)
   at System.Windows.Forms.Form.OnCreateControl()
   at System.Windows.Forms.Control.CreateControl(Boolean fIgnoreVisible)
   at System.Windows.Forms.Control.CreateControl()
   at System.Windows.Forms.Control.WmShowWindow(Message& m)
   at System.Windows.Forms.Control.WndProc(Message& m)
   at System.Windows.Forms.ScrollableControl.WndProc(Message& m)
   at System.Windows.Forms.ContainerControl.WndProc(Message& m)
   at System.Windows.Forms.Form.WmShowWindow(Message& m)
   at System.Windows.Forms.Form.WndProc(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.OnMessage(Message& m)
   at System.Windows.Forms.Control.ControlNativeWindow.WndProc(Message& m)
   at System.Windows.Forms.NativeWindow.Callback(IntPtr hWnd, Int32 msg, IntPtr wparam, IntPtr lparam)


************** Loaded Assemblies **************
mscorlib
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/Microsoft.NET/Framework/v2.0.50727/mscorlib.dll
----------------------------------------
BurracoClient
    Assembly Version: 4.53.0.82
    Win32 Version: 4.53.0.82
    CodeBase: file:///C:/Programmi/Burraconline/BurracoClient.exe
----------------------------------------
System.Windows.Forms
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll
----------------------------------------
System
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System/2.0.0.0__b77a5c561934e089/System.dll
----------------------------------------
System.Drawing
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Drawing/2.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
----------------------------------------
System.Management
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Management/2.0.0.0__b03f5f7f11d50a3a/System.Management.dll
----------------------------------------
System.Configuration
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Configuration/2.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
----------------------------------------
System.Xml
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_MSIL/System.Xml/2.0.0.0__b77a5c561934e089/System.Xml.dll
----------------------------------------
System.Web
    Assembly Version: 2.0.0.0
    Win32 Version: 2.0.50727.42 (RTM.050727-4200)
    CodeBase: file:///C:/windows/assembly/GAC_32/System.Web/2.0.0.0__b03f5f7f11d50a3a/System.Web.dll
----------------------------------------

************** JIT Debugging **************
To enable just-in-time (JIT) debugging, the .config file for this
application or computer (machine.config) must have the
jitDebugging value set in the system.windows.forms section.
The application must also be compiled with debugging
enabled.

For example:

<configuration>
    <system.windows.forms jitDebugging="true" />
</configuration>

When JIT debugging is enabled, any unhandled exception
will be sent to the JIT debugger registered on the computer
rather than be handled by this dialog box.



```

---

### Post by manolomanolo on 2010-05-31
up

---

### Post by manolomanolo on 2010-06-03
up... ](*,)

---

### Post by manolomanolo on 2010-06-09
up :confused:

---

### Post by manolomanolo on 2010-06-10
[http://bugs.winehq.org/show_bug.cgi?id=23100]("http://bugs.winehq.org/show_bug.cgi?id=23100")

---

