---
title: "winetricks HAS TONS OF ERRORS!!!"
date: 2009-06-09
forum: Wine
---

### Post by nandnor on 2009-06-09
when i try to do a basic install with winetricks, like
> sh winetricks dotnet20
Setting Windows version to win2k
Executing wine regedit /home/arts/.wine/drive_c/winetrickstmp/set-winver.reg
Executing cp -f /home/arts/.winetrickscache/dotnet20/l_intl.nls /home/arts/.wine/drive_c/windows/system32/
Executing wine /home/arts/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f3c0,0x00000001,0x33f3e8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"arts" (nil) 0x7e1a5438 (nil) 0x7e1a543c 0x7e1a5430 - stub
fixme:advapi:LookupAccountNameW (null) L"arts" 0x147ed0 0x7e1a5438 0x144660 0x7e1a543c 0x7e1a5430 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 4 ignored L"ServiceControl" table values
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 4 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveDuplicateFiles -> 7 ignored L"DuplicateFile" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 16 ignored L"CreateFolder" table values
fixme:msi:msi_unimplemented_action_stub BindImage -> 8 ignored L"BindImage" table values
fixme:reg:GetNativeSystemInfo (0x33f428) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x630118 0x33f400) stub!
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17
fixme:advapi:CheckTokenMembership ((nil) 0x630140 0x33f3b0) stub!
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
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
wine: Unhandled exception 0xc06d007e at address 0x7b845450 (thread 0076), starting debugger...
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices"
fixme:shell:URL_ParseUrl failed to parse L"System"
err:ole:CoGetClassObject class {ecabb0c8-7f19-11d2-978e-0000f8757e2a} not registered
err:ole:CoGetClassObject no class object {ecabb0c8-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1
err:ole:CoGetClassObject class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered
err:ole:create_server class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {6eb22881-8a19-11d0-81b6-00a0c9231c29} could be created for context 0x15
fixme:advapi:RegisterEventSourceW (L".",L"System.EnterpriseServices"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000000,0x8764e4,0x876360): stub
err:eventlog:ReportEventW L"System.EnterpriseServices failed to install. Please fix the problem (see exception below) and run 'regasm System.EnterpriseServices.dll' again to install System.EnterpriseServices.\n\rException:\n'System.InvalidCastException: Retrieving the COM class factory for component with CLSID {6EB22881-8A19-11"...
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:ole:CoGetContextToken stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:CoGetContextToken stub
err:msi:HANDLE_CustomType34 Unable to execute command L"\"C:\\windows\\Microsoft.NET\\Framework\\netfxsbs20.exe\" /install"

it shows a buttload of errors, and nothing works. the same story with every winetricks package i tried. its damn depressiong and i dont know what to do. is there a special ubuntu version of winetricks perhaps? cos i just downloaded the regular one from its page
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

thanks for any help

---

### Post by nandnor on 2009-06-10
up

---

### Post by Tibuda on 2009-06-10
From your link:
> Reporting bugs *in* Winetricks

Winetricks has a bug tracking system at [http://code.google.com/p/winezeug/issues/list](http://code.google.com/p/winezeug/issues/list) though sending email to wine-devel at winehq.org is usually good enough. 

---

### Post by paradigm2 on 2009-06-10
I have somewhat of the same problem.  A certain install hosed my drive_c so  have to start over.  I find it convenient, but the documentation seems VERY lacking.  The Wiki is very general and the wine.org forum doesn't really allow in depth discussion of winetricks (Maybe it cuts from codeweaver$?).  I wish there were a forum or even a good searchable mailing list with the archives open...

In answer to your question, you'll probably have to start a new drive_c from scratch.  I learned that it is best to make a backup copy of your entire .wine before installing anything.  If it fails, put the backup back into .wine.  I'm not aware of any uninstall feature in winetricks (of course the cdocumentation s so poor, how would I know).

---

### Post by hikaricore on 2009-06-10
Please refrain from posting your title in CAPS for no reason..

---

### Post by NightMKoder on 2009-06-10
What documentation do you want for winetricks? It simply an automator, using known methods to make some libraries install.

As for your problem - .net 2.0 is an incredibly large installer that I believe doesn't work too well under wine right now. It's not winetricks' fault, rather, it's a wine error. 

FYI winetricks isn't made by anyone at codeweavers (Dan Kegel works at google, Austin...not at codeweavers at least).

winetricks are also made to be installed on a clean prefix (meaning fresh wine installation), so if your wine prefix is already dead that practically disqualifies you from support. It's too hard to debug all the different problems you might have.

Lastly - even if you manage to get it installed, .net apps will most likely not work. Still too many bugs in wine. Check the .net appdb entry.

---

### Post by ajackson on 2009-06-11
> **NightMKoder said:**
> As for your problem - .net 2.0 is an incredibly large installer that I believe doesn't work too well under wine right now. It's not winetricks' fault, rather, it's a wine error. 
+1 .NET and Wine don't get on very well at the moment, sure with some versions of Wine you can get .NET installed but running .NET apps is another matter. It is work in progress and progress is slow because dear old Microsoft made a mess of developing .NET

Also, you are complaining about a helper script and wanting help but I don't see you post any of the useful information you are supposed to post when making support requests in this particular sub-forum but then it is easier to criticise than it is to read the stickies I guess.

---

### Post by Elfy on 2009-06-11
> **ajackson said:**
>  but I don't see you post any of the useful information you are supposed to post when making support requests in this particular sub-forum but then it is easier to criticise than it is to read the stickies I guess.

The thread was moved here from elsewhere - so no the OP didn't read the stickies - probably not even aware they exist until they read these 2 posts.

---

### Post by ajackson on 2009-06-11
> **forestpixie said:**
> The thread was moved here from elsewhere - so no the OP didn't read the stickies - probably not even aware they exist until they read these 2 posts.
OK so they didn't think that a problem with winetricks should be in the Wine sub-forum, makes it worse rather than better IMHO.

---

### Post by nandnor on 2009-07-13
bump, still cant get winetricks scripts to work, even with newest wine version(1.1.25), any ideas?

---

### Post by ajackson on 2009-07-13
> **nandnor said:**
> bump, still cant get winetricks scripts to work, even with newest wine version(1.1.25), any ideas?
Still not learnt how to read the stickies or even post 3 in this thread hey?

You are attempting to install, from what I can tell, .NET. NET doesn't work very well in wine, sure with some versions of Wine you can get it to install but running almost anything fails. It is heavily work in progress and from what I can tell (from reading what a few of the Wine/Crossover devs have said) progress is slow.

---

### Post by nandnor on 2009-07-14
> **ajackson said:**
> Still not learnt how to read the stickies or even post 3 in this thread hey?

You are attempting to install, from what I can tell, .NET. NET doesn't work very well in wine, sure with some versions of Wine you can get it to install but running almost anything fails. It is heavily work in progress and from what I can tell (from reading what a few of the Wine/Crossover devs have said) progress is slow.
youre right in a sense - but i guess thats what humanity is about, laziness. And I certainly am too lazy to seriously mess around with bug reporting etc, instead hoping for a quick fix to solve my problems.

---

### Post by ajackson on 2009-07-14
> **nandnor said:**
> youre right in a sense - but i guess thats what humanity is about, laziness. And I certainly am too lazy to seriously mess around with bug reporting etc, instead hoping for a quick fix to solve my problems.
:popcorn:

---

