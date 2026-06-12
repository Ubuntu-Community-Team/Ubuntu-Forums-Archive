---
title: "Guitar hero 3 needs virtual memory"
date: 2009-06-20
forum: Wine
---

### Post by koekjestrommel on 2009-06-20
[http://appdb.winehq.org/commentview.php?iAppId=6160&iVersionId=9860&iThreadId=28118](http://appdb.winehq.org/commentview.php?iAppId=6160&iVersionId=9860&iThreadId=28118)

The wine HQ said something about saving this in a .reg and opening it with the registry. My question is, how?

```
[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\Memory Management]

"ClearPageFileAtShutdown"=dword:00000000

"DisablePagingExecutive"=dword:00000000

"LargeSystemCache"=dword:00000000

"NonPagedPoolQuota"=dword:00000000

"NonPagedPoolSize"=dword:00000000

"PagedPoolQuota"=dword:00000000

"PagedPoolSize"=dword:00000000

"SecondLevelDataCache"=dword:00000000

"SystemPages"=dword:00000000

"PagingFiles"=hex(7):43,00,3a,00,5c,00,70,00,61,00,67,00,65,00,66,00,69,00,6c,\

00,65,00,2e,00,73,00,79,00,73,00,20,00,31,00,30,00,30,00,20,00,31,00,35,00,\

30,00,30,00,00,00,00,00

"PhysicalAddressExtension"=dword:00000000

"SessionViewSize"=dword:00000030

"SessionPoolSize"=dword:00000004

"WriteWatch"=dword:00000001



[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management]

"ClearPageFileAtShutdown"=dword:00000000

"DisablePagingExecutive"=dword:00000000

"LargeSystemCache"=dword:00000000

"NonPagedPoolQuota"=dword:00000000

"NonPagedPoolSize"=dword:00000000

"PagedPoolQuota"=dword:00000000

"PagedPoolSize"=dword:00000000

"SecondLevelDataCache"=dword:00000000

"SystemPages"=dword:00000000

"PagingFiles"=hex(7):43,00,3a,00,5c,00,70,00,61,00,67,00,65,00,66,00,69,00,6c,\

00,65,00,2e,00,73,00,79,00,73,00,20,00,31,00,30,00,30,00,20,00,31,00,35,00,\

30,00,30,00,00,00,00,00

"PhysicalAddressExtension"=dword:00000000

"SessionViewSize"=dword:00000030

"SessionPoolSize"=dword:00000004

"WriteWatch"=dword:00000001



[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\RNG]

"Seed"=hex:ac,28,70,71,d1,c7,76,6e,33,06,81,61,85,59,1f,67,58,c1,88,11,b0,d7,\

43,04,40,43,af,73,d8,1f,c0,6b,73,cd,0c,72,2a,c4,e6,3c,1a,51,98,f3,e1,ad,0e,\

d8,9a,6a,86,7b,1e,e6,97,23,b1,61,3e,4e,97,73,9b,03,d8,78,dc,f6,f2,fb,1e,2b,\

a0,70,a0,97,2e,98,d7,17
```
I hope you guys can help me :)

---

### Post by NightMKoder on 2009-06-20
Create a new text file, say wine.reg and put that text in it. Now do this in terminal:

```

wine regedit wine.reg

```

---

### Post by koekjestrommel on 2009-06-21
```
joost@joost-laptop:~$ wine regedit /home/joost/Desktop/wine.reg
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:service:EnumServicesStatusW 0x125db8 type=30 state=3 (nil) 0 0x87e798 0x87e7a4 0x87e7a0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x87e5a8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x125818,(nil)): stub
```

This is what I did.

Rightclick on desktop. Click create document > empty file.

Past everything in it.

Save it as wine.reg

open terminal

do this
```
wine regedit /home/joost/Desktop/wine.reg
```

That's what came out. It still doesn't work.
Still the virtual memory error.

PIC[IMG]http://i273.photobucket.com/albums/jj202/k0ffiekopje/Screenshot.png[/IMG]
What did I do wrong :(

---

### Post by NightMKoder on 2009-06-21
I think you have extra blank line in there. Make sure that there are none and do it again.

---

### Post by koekjestrommel on 2009-06-21
I copied the exact same piece of text as in my 1st post. what is the blank line that I am missing?

---

### Post by NightMKoder on 2009-06-21
> ```

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\Memory Management]
"ClearPageFileAtShutdown"=dword:00000000
"DisablePagingExecutive"=dword:00000000
"LargeSystemCache"=dword:00000000
"NonPagedPoolQuota"=dword:00000000
"NonPagedPoolSize"=dword:00000000
"PagedPoolQuota"=dword:00000000
"PagedPoolSize"=dword:00000000
"SecondLevelDataCache"=dword:00000000
"SystemPages"=dword:00000000
"PagingFiles"=hex(7):43,00,3a,00,5c,00,70,00,61,00,67,00,65,00,66,00,69,00,6c,\
00,65,00,2e,00,73,00,79,00,73,00,20,00,31,00,30,00,30,00,20,00,31,00,35,00,\
30,00,30,00,00,00,00,00
"PhysicalAddressExtension"=dword:00000000
"SessionViewSize"=dword:00000030
"SessionPoolSize"=dword:00000004
"WriteWatch"=dword:00000001

[HKEY_LOCAL_MAHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management]
"ClearPageFileAtShutdown"=dword:00000000
"DisablePagingExecutive"=dword:00000000
"LargeSystemCache"=dword:00000000
"NonPagedPoolQuota"=dword:00000000
"NonPagedPoolSize"=dword:00000000
"PagedPoolQuota"=dword:00000000
"PagedPoolSize"=dword:00000000
"SecondLevelDataCache"=dword:00000000
"SystemPages"=dword:00000000
"PagingFiles"=hex(7):43,00,3a,00,5c,00,70,00,61,00,67,00,65,00,66,00,69,00,6c,\
00,65,00,2e,00,73,00,79,00,73,00,20,00,31,00,30,00,30,00,20,00,31,00,35,00,\
30,00,30,00,00,00,00,00
"PhysicalAddressExtension"=dword:00000000
"SessionViewSize"=dword:00000030
"SessionPoolSize"=dword:00000004
"WriteWatch"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\RNG]
"Seed"=hex:ac,28,70,71,d1,c7,76,6e,33,06,81,61,85,59,1f,67,58,c1,88,11,b0,d7,\
43,04,40,43,af,73,d8,1f,c0,6b,73,cd,0c,72,2a,c4,e6,3c,1a,51,98,f3,e1,ad,0e,\
d8,9a,6a,86,7b,1e,e6,97,23,b1,61,3e,4e,97,73,9b,03,d8,78,dc,f6,f2,fb,1e,2b,\
a0,70,a0,97,2e,98,d7,17

```

Something like that instead? You have an extra empty line after every line which needs to be removed.

---

