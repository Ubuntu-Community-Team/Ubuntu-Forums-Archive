---
title: "I tried to play Star Wars Jedi Academy the other day but i cant fiqure out this"
date: 2010-02-03
forum: Wine
---

### Post by Espryon on 2010-02-03
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315)


With newer nvidia drivers, the app will crash early because of a buffer overflow.  You must run as

__GL_ExtensionStringVersion=17700 wine jasp.exe

where do i put this? ^^^^^^^^^^^^^^^

i have a nvidia 280 gtx vid card

plz plz help me out guys i want to play swja

---

### Post by Espryon on 2010-02-04
JA: v1.0.0.0 win-x86 Aug  5 2003
Initialising zone memory .....
----- FS_Startup -----
Current search path:
Z:\home\sev/base

----------------------
0 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:

running in terminal output 

sev@s3v-desktop:~$ '/home/sev/.wine/dosdevices/c:/Program Files/LucasArts/Star Wars Jedi Knight Jedi Academy/GameData/jasp.exe' 
fixme:advapi:SetEntriesInAclA 1 0x33f73c (nil) 0x33f774
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f728 (nil) 0x33f770
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f748 (nil) 0x33f790
fixme:advapi:SetSecurityInfo stub
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33f098
fixme:iphlpapi:NotifyAddrChange (Handle 0xe5e8d8, overlapped 0xe5e8e0): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

Z:\home\sev/demo

----------------------
0 files in pk3 files
Couldn't load default.cfg

---

### Post by Espryon on 2010-02-04
can anyone please tell me whats wrong with this application and why it wont run i just want to play swja in wine on linux

---

