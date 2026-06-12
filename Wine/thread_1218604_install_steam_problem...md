---
title: "install steam problem.."
date: 2009-07-20
forum: Wine
---

### Post by Dr.iCe on 2009-07-20
so i do 
```
wine start steaminstall.msi
```

but it just opens and closes and i get this in my terminal

```
fixme:exec:SHELL_execute flags ignored: 0x00000500
drice@drice-laptop:~$ fixme:sfc:SfcIsKeyProtected ((nil), (null)) stub
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x33f558,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x130688,(nil)): stub
err:eventlog:ReportEventW L"=====================================================\r\nException code: C0000005 ACCESS_VIOLATION\r\nFunction: 0x0\r\n=====================================================\r\n\r\nRegisters:\r\nEAX:00000000  EBX:004BEF2D  ECX:0033F594  EDX:00000031  ESI:0033F71C  EDI:00000000\r\nCS:EIP:0073:00000000 "...
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
drice@drice-laptop:~$ 


```

someone please help me

---

