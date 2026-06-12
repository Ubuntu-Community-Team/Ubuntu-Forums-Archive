---
title: "Patching Problem WoW-3.2.0.10192-to-3.3.0.10958-enGB"
date: 2010-08-20
forum: Wine
---

### Post by alchemisty on 2010-08-20
Hello ubuntuforums.org,  I have the following problem, i installed WoW recently using the online installer. But then Launcher stuck, and nothing happend, it downloads the patch, but it doesn't install it.

Wine-Log (Launcher.exe):  

```
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURL_GetQuery default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURL_GetRef default action not implemented
fixme:mshtml:nsChannel_IsNoStoreResponse (0x177880)->(0x32d454)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x177880)->(0x32d454)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:mshtml:nsChannel_IsNoStoreResponse (0x1b7a70)->(0x32d454)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x1b7a70)->(0x32d454)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:mshtml:nsChannel_IsNoStoreResponse (0x181be8)->(0x32d990)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x181be8)->(0x32d98c)
fixme:ras:RasEnumConnectionsA (0x630607a8,0xb4e820,0x6305f610),stub!
fixme:ras:RasEnumConnectionsA RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:service:EnumServicesStatusA 0x131f70 type=30 state=1 0xb4e5a8 240 0xb4e7ec 0xb4e7f4 0xb4e7e8

http error code = 404
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x3398c4, uiNumDevices=2, cbSize=12) stub!
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x13ca30, 0x965e130
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x13ca48, 0x965e130
fixme:ras:RasEnumEntriesA ((nil),(null),0x965d104,0x965d8c0,0x965d8bc),stub!
fixme:service:EnumServicesStatusA 0x13ca58 type=30 state=1 0x965e4d0 240 0x965e714 0x965e71c 0x965e710
fixme:ras:RasEnumEntriesA ((nil),(null),0x965d104,0x965d8c0,0x965d8bc),stub!
err:ole:CoGetClassObject class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:CoGetClassObject class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:create_server class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:CoGetClassObject no class object {e2085f28-feb7-404a-b8e7-e659bdeaaa02} could be created for context 0x7
fixme:ras:RasEnumEntriesA ((nil),(null),0x965d104,0x965d8c0,0x965d8bc),stub!
fixme:ras:RasEnumEntriesA ((nil),(null),0x965d104,0x965d8c0,0x965d8bc),stub!
fixme:ras:RasEnumEntriesA ((nil),(null),0x965d104,0x965d8c0,0x965d8bc),stub!
fixme:service:EnumServicesStatusA 0x1477b0 type=30 state=1 0x965e4d0 240 0x965e714 0x965e71c 0x965e710
fixme:ras:RasEnumEntriesA ((nil),(null),0x965d104,0x965d8c0,0x965d8bc),stub!
err:ntdll:RtlpWaitForCriticalSection section 0x5e2b48 "?" wait timed out in thread 0056, blocked by 001e, retrying (60 sec)

```

When i run "wine WoW-3.2.0.10192-to-3.3.0.10958-enGB-patch.exe" nothing comes back.


Installed Wine, Winetricks, and nearly every expansion of Winetricks.



You got any ideas? I appreciate help very much ):P

Yours truly 

alchemisty

---

### Post by liquidfunk on 2010-08-20
What version of Wine are you using?

```
wine --version
```

---

### Post by alchemisty on 2010-08-20
alchemist@hellhound:~$ wine --version
wine-1.3.0
alchemist@hellhound:~$ 

i hope it helps

//EDIT: Dang wrong forum, please move

yours truly

alchemisty

---

