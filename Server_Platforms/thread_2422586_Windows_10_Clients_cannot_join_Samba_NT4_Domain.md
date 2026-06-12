---
title: "Windows 10 Clients cannot join Samba NT4 Domain"
date: 2019-07-10
forum: Server Platforms
---

### Post by joshi82 on 2019-07-10
Greetings,


I have inherited an Ubuntu 16.04.6 Server 64bit, running Samba 4.3.11. We have a NT4-Style, single label, Samba domain, which servers for authentication and file services for about 100 clients. On top of that a homebrew admin software, which is designed to work with the NT4 domain. Works very well so far. Since Windows 7 is coming to an end, I need to evaluate 2 different Win10 clients for performance and compabitility. Unfortunatelly, I do not get Win10 to join the domain. I´ve tried several tricks, fixes, workarounds - all that I could find so far on the internet.


I tried older builds (1507), because I heard, these have been known to work. They didn´t. I t ried newer builds, with and without patches. Didn´t work. I have tried enabling SMBv1, misc. reg hacks, all with reboots in between, nothing worked.


I tried the following Registry changes:
HKLM\CurrentControlSet\Services\Netlogon\Parameters\NT4Emulator DWORD 1
HKLM\CurrentControlSet\Services\Netlogon\Parameters\NeutralizeNT4Emulator DWORD 1
HKLM\CurrentControlSet\Services\LanmanWorkstation\Parameters\DNSNameResolutionRequired DWORD 0
(and two others, but I dont remember them)


The error message is the same as other people have posted:
07/09/2019 14:24:47:471 NetpDoDomainJoin
07/09/2019 14:24:47:471 NetpDoDomainJoin: using current computer names
07/09/2019 14:24:47:471 NetpDoDomainJoin: NetpGetComputerNameEx(NetBios) returned 0x0
07/09/2019 14:24:47:471 NetpDoDomainJoin: NetpGetComputerNameEx(DnsHostName) returned 0x0
07/09/2019 14:24:47:471 NetpMachineValidToJoin: 'WIN10-VBOX'
07/09/2019 14:24:47:471 NetpMachineValidToJoin: status: 0x0
07/09/2019 14:24:47:471 NetpJoinDomain
07/09/2019 14:24:47:471 	HostName: win10-vbox
07/09/2019 14:24:47:471 	NetbiosName: WIN10-VBOX
07/09/2019 14:24:47:471 	Domain: mydomain
07/09/2019 14:24:47:471 	MachineAccountOU: (NULL)
07/09/2019 14:24:47:471 	Account: mydomain\root
07/09/2019 14:24:47:471 	Options: 0x27
07/09/2019 14:24:47:471 NetpValidateName: checking to see if 'mydomain' is valid as type 3 name
07/09/2019 14:24:47:485 NetpCheckDomainNameIsValid [ Exists ] for 'mydomain' returned 0x0
07/09/2019 14:24:47:485 NetpValidateName: name 'mydomain' is valid for type 3
07/09/2019 14:24:47:485 NetpDsGetDcName: trying to find DC in domain 'mydomain', flags: 0x40001020
07/09/2019 14:24:47:485 NetpDsGetDcName: failed to find a DC in the specified domain: 0x54b, last error is 0x0
07/09/2019 14:24:47:485 NetpJoinDomainOnDs: NetpDsGetDcName returned: 0x54b
07/09/2019 14:24:47:485 NetpJoinDomainOnDs: Function exits with status of: 0x54b
07/09/2019 14:24:47:485 NetpJoinDomainOnDs: NetpResetIDNEncoding on '(null)': 0x0
07/09/2019 14:24:47:485 NetpDoDomainJoin: status: 0x54b


I tried different username/password/domain combinations, also false ones. The client does not come that far, he obviously does not find his way to the DC. Browsing shares At this point I am neither able to upgrade to AD, nor to migrate to Windows. So I need (and also would like to) keep the NT4 domain up and running, until I could free up some time to migrate.


Has anybody here some experience with this kind of problem? I found some evidence that I need to adjust "smb ports" in smb.conf or to disable that at all (do not remember exactly). I didn´t alter the samba-config yet, because I am not very confident here...
Any advice/help/tip is highly appreciated.


Thanks
Johannes

---

