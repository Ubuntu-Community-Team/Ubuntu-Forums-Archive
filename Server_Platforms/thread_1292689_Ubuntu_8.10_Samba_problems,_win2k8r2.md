---
title: "Ubuntu 8.10 Samba problems, win2k8r2"
date: 2009-10-16
forum: Server Platforms
---

### Post by LarsEriksson on 2009-10-16
Im using samba (3.4.0, from karmic repo) as a (master)domain server.
Last night a windows server(connected to the samba domain) used for remoteapp(terminal services) was automatically updated and rebooted, and now when clients try to connect to the remote app-server with their domain account the following error message is displayed:

The trust relationship between this workstation and the primary domain failed.

PLEASE, can anyone help me out here?

---

### Post by LarsEriksson on 2009-10-26
Still having this problem. Ive tried uninstalling all updates on the windows-machine, without success.

Windows can join the domain, but when im trying to log in the trust relationship error pops up.

Is there noone who can help me out here ?

Ive read that some people is able to join domain and log in with Samba 3.3.6, can anyone confirm this?
And if so, how do i downgrade Samba?

---

### Post by LarsEriksson on 2009-10-28
Solved, with theese registry hacks in Win7 and Win2k8r2

        HKLM\System\CCS\Services\LanmanWorkstation\Parameters
            DWORD  DomainCompatibilityMode = 1
            DWORD  DNSNameResolutionRequired = 0

        HKLM\System\CCS\Services\Netlogon\Parameters
            DWORD  RequireSignOnSeal = 1
            DWORD  RequireStrongKey = 1

---

