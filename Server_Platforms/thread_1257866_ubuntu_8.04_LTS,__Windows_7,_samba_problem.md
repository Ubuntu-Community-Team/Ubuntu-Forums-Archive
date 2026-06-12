---
title: "ubuntu 8.04 LTS,  Windows 7, samba problem"
date: 2009-09-04
forum: Server Platforms
---

### Post by stbe on 2009-09-04
I have a machine running "Windows 7 64bit" that cannot connect to my samba server.

Server runs Ubuntu 8.04 LTS with samba 3.0.28a. I know that this is not a very new samba release but I failed to update samba using deb packages (dependencies).

I do not use samba as PDC (ads / domain controller), I just use it for sharing files to specific users (security=user).

I run "net use \\server\share" on the Windows 7 client but cannot logon to the server. I always get system error 86.

What's going wrong?

Maybe some newer Samba version is necessary, will 3.4.1 be available for hardy?


I already changed (lowered) some security options in Windows registry but this did not help:

LmCompatibilityLevel=1
[http://technet.microsoft.com/en-us/library/cc960646.aspx](http://technet.microsoft.com/en-us/library/cc960646.aspx)

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\LanmanWorkstation\Parameters]
"DomainCompatibilityMode"=dword:00000001
"DNSNameResolutionRequired"=dword:00000000

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Netlogon\Parameters]
"RequireSignOrSeal"=dword:00000000
"RequireStrongKey"=dword:00000000

---

### Post by stbe on 2009-09-09
All clear now.

I feel sheepish about this. But it really seems I just used the wrong password... 

samba 3.0.28a (current ubuntu 8.04 LTS) is working fine with Win7 and there seems to be no need of changing anything in registry (I just changed everything back to defaults and it still works after reboot). security=user.

---

