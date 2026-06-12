---
title: "Flaw in OpenOffice.org2: OpenOffice is vulnerable to MS Word 0 day vulns"
date: 2006-12-18
forum: Server Platforms
---

### Post by reiatzu on 2006-12-18
It's openoffice-2.0.4, and it did crashed with the below
error...

reiatsu@rotten:/rotten$ openoffice --version
This is OpenOffice.org built with ooo-build-2.0.4

reiatsu@rotten:/rotten$ uname -a
Linux rotten 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

reiatsu@rotten:/rotten$ oowriter 12122006-djtest.doc
libGL warning: 3D driver claims to not support visual 0x5b
Application ErrorApplication Error

Fatal exception: Signal 6
Stack:
/usr/lib/openoffice/program/libuno_sal.so.3[0xb71b31eb]
/usr/lib/openoffice/program/libuno_sal.so.3[0xb71b3321]
/usr/lib/openoffice/program/libuno_sal.so.3[0xb71b33b8]
[0xffffe420]
/lib/tls/i686/cmov/libc.so.6(abort+0x103)[0xb6b65ef3]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e7abe2]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application5AbortERK6String+0x1d)[0xb7c20a4d]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop9ExceptionEt+0x4b)[0x80646eb]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c26fdf]
/usr/lib/openoffice/program/libvos3gcc3.so(_ZN3vos26signalHandlerFunction_implEPvP13oslSignalInfo+0x18)[0xb7404ae8]
/usr/lib/openoffice/program/libuno_sal.so.3[0xb71b2e67]
/usr/lib/openoffice/program/libuno_sal.so.3[0xb71b3392]
[0xffffe420]
/lib/tls/i686/cmov/libc.so.6(abort+0x103)[0xb6b65ef3]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e7abe2]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application5AbortERK6String+0x1d)[0xb7c20a4d]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop9ExceptionEt+0x2ea)[0x806498a]
/usr/lib/openoffice/program/libsfx680li.so[0xaef363f1]
/usr/lib/openoffice/program/soffice.bin[0x808f222]
/usr/lib/openoffice/program/soffice.bin(_Znaj+0x26)[0x808f296]
/usr/lib/openoffice/program/libsw680li.so[0xac4a7cdd]
/usr/lib/openoffice/program/libsw680li.so[0xac4a7e8d]
/usr/lib/openoffice/program/libsw680li.so[0xac4aff90]
/usr/lib/openoffice/program/libsw680li.so[0xac4b0083]
/usr/lib/openoffice/program/libsw680li.so[0xac4b33e1]
/usr/lib/openoffice/program/libsw680li.so[0xac46283f]
/usr/lib/openoffice/program/libsw680li.so[0xac463d5a]
/usr/lib/openoffice/program/libsw680li.so[0xac464796]
/usr/lib/openoffice/program/libsw680li.so[0xac4648b1]
/usr/lib/openoffice/program/libsw680li.so[0xac31f66f]
/usr/lib/openoffice/program/libsw680li.so[0xac51cf9d]
/usr/lib/openoffice/program/libsfx680li.so(_ZN14SfxObjectShell6DoLoadEP9SfxMedium+0x79c)[0xaed8d74c]
/usr/lib/openoffice/program/libsfx680li.so(_ZN12SfxBaseModel4loadERKN3com3sun4star3uno8SequenceINS2_5beans13PropertyValueEEE+0x323)[0xaedf23c3]
/usr/lib/openoffice/program/libsfx680li.so[0xaee28d9f]
/usr/lib/openoffice/program/libfwk680li.so[0xae86ab76]
/usr/lib/openoffice/program/libfwk680li.so[0xae86cdaa]
/usr/lib/openoffice/program/libfwk680li.so[0xae86cff5]
/usr/lib/openoffice/program/libfwk680li.so[0xae712433]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop15DispatchWatcher23executeDispatchRequestsERKN4_STL6vectorINS0_15DispatchRequestENS1_9allocatorIS3_EEEE+0x2676)[0x8083976]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop15OfficeIPCThread22ExecuteCmdLineRequestsERNS_23ProcessDocumentsRequestE+0x133)[0x8076693]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop11OpenClientsEv+0x119f)[0x807173f]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop16OpenClients_ImplEPv+0x3d)[0x8072a7d]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e0b846]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN10SalDisplay21DispatchInternalEventEv+0xb1)[0xb5696e01]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a822d6]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a82311]
/usr/lib/libglib-2.0.so.0[0xb5cb2aa1]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb5cb4802]
/usr/lib/libglib-2.0.so.0[0xb5cb77df]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb5cb7d45]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5a84201]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN14X11SalInstance5YieldEbb+0x37)[0xb5698027]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application5YieldEb+0x68)[0xb7c21f08]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application7ExecuteEv+0x3c)[0xb7c21fdc]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x1637)[0x806d8b7]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c27c2c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c27d35]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x43)[0x805fdb3]
/usr/lib/openoffice/program/soffice.bin(main+0x36)[0x805fe36]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6b508cc]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x39)[0x805fce1]

** (process:24084): WARNING **: Unknown error forking main binary / abnormal early exit ...


[http://www.milw0rm.com/sploits/12122006-djtest.doc](http://www.milw0rm.com/sploits/12122006-djtest.doc) was used in this test.

---

### Post by endersshadow on 2006-12-18
Got the same error w/ OO.o.  Got the following with abiword (both from the repos):

```
eric@homesteadgrays:~/Desktop$ abiword 12122006-djtest.doc 

(abiword:29712): libgsf:msole-CRITICAL **: ole_get_block: assertion `block < ole->info->max_block' failed

** (abiword:29712): WARNING **: Invalid seek

** (abiword:29712): WARNING **: Invalid seek

** (abiword:29712): WARNING **: Invalid seek

** (abiword:29712): WARNING **: Invalid seek
```

---

### Post by Lord Illidan on 2006-12-18
Mine just crashed..

---

### Post by reiatzu on 2006-12-18
I'd have to do more research on this later. A little strange, it should be patched up soon, however.

---

### Post by emacsuser on 2007-10-04
Nothing happened here, is there supposed to be a macro in that document?

---

