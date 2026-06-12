---
title: "Problem with Wine and dotnet 2.0"
date: 2009-01-21
forum: Wine
---

### Post by Triphys on 2009-01-21
I'm running Ubuntu 8.10 and I have a lil' problem..
I need dotnet2.0 to run an application I have, so I'm using winetricks for that.. Installing winetricks is no problems, and installing vcore6 works good aswell.. But when running "sh winetricks dotnet20" I get a load of problems.. This is the log:

```

fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
fixme:advapi:RegisterEventSourceW ((null),L"ASP.NET 2.0.50727.0"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0001,0x400003f9,(nil),0x0002,0x00000000,0x33ed84,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
wine: Unhandled exception 0xc06d007e at address 0x7b845450 (thread 0075), starting debugger...
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:ole:CoGetContextToken stub
fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices"
fixme:shell:URL_ParseUrl failed to parse L"System"
err:ole:CoGetClassObject class {ecabb0c8-7f19-11d2-978e-0000f8757e2a} not registered
err:ole:CoGetClassObject no class object {ecabb0c8-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1
err:ole:CoGetClassObject class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered
err:ole:create_server class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {6eb22881-8a19-11d0-81b6-00a0c9231c29} could be created for context 0x15
fixme:advapi:RegisterEventSourceW (L".",L"System.EnterpriseServices"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000000,0x87c7e8,0x87c664): stub
err:eventlog:ReportEventW L"System.EnterpriseServices failed to install. Please fix the problem (see exception below) and run 'regasm System.EnterpriseServices.dll' again to install System.EnterpriseServices.\n\rException:\n'System.InvalidCastException: Retrieving the COM class factory for component with CLSID {6EB22881-8A19-11"...
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:CoGetContextToken stub
err:msi:HANDLE_CustomType34 Unable to execute command L"\"C:\\windows\\Microsoft.NET\\Framework\\netfxsbs20.exe\" /install"
Clearing Windows version back to default
Executing wine regedit /home/triphys/.wine/drive_c/winetrickstmp/unset-winver.reg
Install of dotnet20 done
winetricks done.

```

It just won't work! Have tried 100 time now, but it doesnt seem to work. Would be highly appriciated if someone could help me :)

---

### Post by Infestdead on 2009-06-23
Same problem.
Anyone?

---

### Post by devroute on 2010-06-14
i'm also having this issue can anyone help?

---

