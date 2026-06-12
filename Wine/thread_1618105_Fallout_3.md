---
title: "Fallout 3"
date: 2010-11-10
forum: Wine
---

### Post by grrrbob on 2010-11-10
i have fallout 3 on my windows partition and therefore i copied the folder over to ubuntu. i then used the winehq guide to install the game [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

i have wine 1.3.5, ubuntu 10.04 (lucid) kernel 2.6.32-25-generic-pae and nvidia geforce gt220 graphics card, intel core 2 duo cpu

however i get this error when attempting to run the .exe file

```
desktop:~/Downloads/Fallout 3$ wine Fallout3.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library msidcrl40.dll (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
fixme:advapi:SetEntriesInAclA 1 0x33f724 (nil) 0x33f75c
fixme:advapi:SetSecurityInfo stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:module:import_dll Library xlive.dll (which is needed by L"Z:\\home\\faz\\Downloads\\Fallout 3\\Fallout3.exe") not found
fixme:advapi:SetEntriesInAclA 1 0x33f710 (nil) 0x33f758
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f730 (nil) 0x33f778
fixme:advapi:SetSecurityInfo stub
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\faz\\Downloads\\Fallout 3\\Fallout3.exe" failed, status c0000135
faz@faz-desktop:~/Downloads/Fallout 3$ fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:system:SetProcessDPIAware stub!
```

any ideas what is missing or what i need to do?

kind regards

---

### Post by grrrbob on 2010-11-10
just update kernal and wine and here is the error;

```
faz@faz-desktop:~/.wine/drive_c/Program Files/Fallout 3$ wine Fallout3.exe
fixme:advapi:SetEntriesInAclA 1 0x33f724 (nil) 0x33f75c
fixme:advapi:SetSecurityInfo stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\quartz.dll" (error=80)
fixme:advapi:SetEntriesInAclA 1 0x33f710 (nil) 0x33f758
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f730 (nil) 0x33f778
fixme:advapi:SetSecurityInfo stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\comctl32.dll" (error=80)
fixme:system:SetProcessDPIAware stub!
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
fixme:iphlpapi:NotifyAddrChange (Handle 0x74e914, overlapped 0x74e918): stub
fixme:advapi:SetEntriesInAclA 1 0x33d6a0 (nil) 0x33d6d8
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33d66c (nil) 0x33d6b4
fixme:advapi:SetSecurityInfo stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:system:SetProcessDPIAware stub!
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
fixme:iphlpapi:NotifyAddrChange (Handle 0x8dee914, overlapped 0x8dee918): stub
wine: configuration in '/home/faz/.wine' has been updated.
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library msidcrl40.dll (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
err:module:import_dll Library xlive.dll (which is needed by L"C:\\Program Files\\Fallout 3\\Fallout3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Fallout 3\\Fallout3.exe" failed, status c0000135

```

---

### Post by grrrbob on 2010-11-10
after removing and installin and fiddling with wine config i now have a variant of the error;

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library msidcrl40.dll (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
err:module:import_dll Library xlive.dll (which is needed by L"C:\\Program Files\\Fallout 3\\Fallout3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Fallout 3\\Fallout3.exe" failed, status c0000135

```

---

### Post by Gunman1982 on 2010-11-10
check the appdb on winehq for Fallout 3 and in particular the section with 'Game for Windows Live client'

---

### Post by Kn1v3s37 on 2010-11-11
Try throwing 'winetricks gfw' in the terminal, see if that helps.

---

### Post by annoyingrob on 2010-11-17
I found that the easiest way to install it was to just use PlayOnLinux, which has a pre-built script to apply all the needed patches for Fallout 3. After that, copy your fallout 3 directory from your "My documents" folder on windows to your home directory on linux, and everything should work fine.

---

