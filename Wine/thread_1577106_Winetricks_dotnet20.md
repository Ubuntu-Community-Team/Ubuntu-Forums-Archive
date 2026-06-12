---
title: "Winetricks dotnet20"
date: 2010-09-18
forum: Wine
---

### Post by roemhildtg on 2010-09-18
Hello, 

I'm fairly new to Linux and I've been trying to install Synctoy from Microsoft and according to the wine website, the command winetricks dotnet20 should be used. The setup runs, and says it is successful however I have my doubts. Here is the console results.

gregg@gregg-laptop:~$ winetricks dotnet20
------------------------------------------------------
Instaling .net 2.0 runtime. Can take several minutes. See [http://wiki.winehq.org/MicrosoftDotNet](http://wiki.winehq.org/MicrosoftDotNet) for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/gregg/.winetrickscache/dotnet20/l_intl.nls /home/gregg/.wine/dosdevices/c:/windows/system32/
Executing wine reg delete HKLM\Software\Microsoft\.NETFramework\policy
2.0 /f
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
The operation completed successfully
Executing wine reg delete HKLM\Software\Microsoft\.NETFramework /v InstallRoot /f
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
The operation completed successfully
Executing wine /home/gregg/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapiecryptFileA "C:\\users\\gregg\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f33c,0x00000001,0x33f364) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"gregg" (nil) 0x7cde3c (nil) 0x7cde40 0x7cde34 - stub
fixme:advapi:LookupAccountNameW (null) L"gregg" 0x14f9d0 0x7cde3c 0x171f58 0x7cde40 0x7cde34 - stub
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub BindImage -> 8 ignored L"BindImage" table values
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:rpc:I_RpcGetBuffer no binding
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
errle:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
errle:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
errle:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixmele:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
errle:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
errle:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
errle:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
errle:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixmele:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
errle:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
fixme:advapi:RegisterEventSourceW ((null),L"ASP.NET 2.0.50727.0"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0001,0x400003f9,(nil),0x0002,0x00000000,0x33ed0c,(nil)): stub
fixme:advapieregisterEventSource (0xcafe4242) stub
fixme:loadperf:UnloadPerfCounterTextStringsW (L"u \"ASP.NET_2.0.50727\"", 1): stub
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
fixme:msi:install_assembly Manifest unhandled
fixme:msi:install_assembly Win32 assemblies not handled
fixme:msi:install_assembly Manifest unhandled
fixme:msi:install_assembly Win32 assemblies not handled
fixme:loadperf:LoadPerfCounterTextStringsW (L"C:\\windows\\system32\\lodctr.exe C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\_Networkingperfcounters.ini", 0): stub
fixme:loadperf:LoadPerfCounterTextStringsW (L"C:\\windows\\system32\\lodctr.exe C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\_DataOracleClientPerfCounters_shared12_neutral.ini", 0): stub
fixme:loadperf:LoadPerfCounterTextStringsW (L"C:\\windows\\system32\\lodctr.exe C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\_dataperfcounters_shared12_neutral.ini", 0): stub
fixme:loadperf:LoadPerfCounterTextStringsW (L"C:\\windows\\system32\\lodctr.exe C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\_DataPerfCounters.ini", 0): stub
fixme:loadperf:LoadPerfCounterTextStringsW (L"C:\\windows\\system32\\lodctr.exe C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\corperfmonsymbols.ini", 0): stub
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices"
fixme:shell:URL_ParseUrl failed to parse L"System"
errle:CoGetClassObject class {ecabb0c8-7f19-11d2-978e-0000f8757e2a} not registered
errle:CoGetClassObject no class object {ecabb0c8-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1
errle:CoGetClassObject class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered
errle:create_server class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered
fixmele:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
errle:CoGetClassObject no class object {6eb22881-8a19-11d0-81b6-00a0c9231c29} could be created for context 0x15
err:msi:HANDLE_CustomType34 Unable to execute command L"\"C:\\windows\\Microsoft.NET\\Framework\\netfxsbs20.exe\" /install" with working directory L"C:\\windows\\Microsoft.NET\\Framework\\"
errle:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
errle:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
fixmele:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
errle:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x15
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.Design"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System.Security"
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.Serialization.Formatters.Soap"
fixme:shell:URL_ParseUrl failed to parse L"System.Deployment"
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Data.SqlXml"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System.Data"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualC"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"System.Transactions"
fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System.Design"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Data"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.Design"
fixme:shell:URL_ParseUrl failed to parse L"System.Web"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Data.OracleClient"
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.Serialization.Formatters.Soap"
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:shell:URL_ParseUrl failed to parse L"System.Web.RegularExpressions"
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
Clearing Windows version back to default
Executing early_wine regedit c:\winetrickstmp\unset-winver.reg
Install of dotnet20 done
winetricks done.


Once this completed, I tried installing SyncToy 2.1 and this also claimed success, however when I try running the program, I get an error saying something like There is no Windows software configured to run this program.

Any ideas?

Thanks guys for your help, I definitely appreciate it.

---

### Post by dino99 on 2010-09-19
see comments here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19768](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19768)

[http://bugs.winehq.org/show_bug.cgi?id=24172](http://bugs.winehq.org/show_bug.cgi?id=24172)

but you might search for "synchronization" into synaptic (syrep, conduit, unison, rsync, ...): lot of synctoy alternatives :)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[http://www.webupd8.org/2010/03/grsync-rsync-gui-110-ubuntu-910-and.html](http://www.webupd8.org/2010/03/grsync-rsync-gui-110-ubuntu-910-and.html)

---

