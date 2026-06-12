---
title: "Utorrent 1.8.5 stopped working on wine"
date: 2010-05-07
forum: Wine
---

### Post by avada on 2010-05-07
It was working for a few days after I installed Ubuntu 10.04. But now it doesn't. It hangs after I start it. I get a blank white notification area icon instead of the utorrent icon. The system monitor shows pipe_wait for utorrent. And I get these error messages If I leave it for a while:

```
fixme:heap:HeapSetInformation 0x110000 0 0x47ae3c 4
fixme:heap:HeapSetInformation 0x4b6000 0 0x47ae3c 4
fixme:hnetcfg:fw_app_get_Enabled 0x134c80, 0x32fac8
fixme:hnetcfg:fw_app_put_ProcessImageFileName 0x134c80, L"D:\\alkalmaz\00e1sok\\Bittorrent\\utorrent\\1.8\\utorrent_1.8.5.exe"
fixme:hnetcfg:fw_app_put_Name 0x134c80, L"\00b5Torrent"
fixme:hnetcfg:fw_apps_Add 0x141230, 0x134c80
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
err:winediag:WSASocketW Failed to create a socket of type SOCK_RAW, this requires special permissions.
err:winediag:WSASocketW Failed to create a socket of type SOCK_RAW, this requires special permissions.
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
fixme:keyboard:RegisterHotKey (0x10062,1,0x00000005,4E): stub
fixme:iphlpapi:adapterAddressesFromIndex address family 23 unsupported
fixme:iphlpapi:GetBestInterfaceEx address family 23 not supported
fixme:iphlpapi:adapterAddressesFromIndex address family 23 unsupported
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:heap:RtlCompactHeap (0x4b6000, 0x0) stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:iphlpapi:GetBestInterfaceEx address family 23 not supported
fixme:iphlpapi:adapterAddressesFromIndex address family 23 unsupported
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:iphlpapi:GetBestInterfaceEx address family 23 not supported
fixme:iphlpapi:adapterAddressesFromIndex address family 23 unsupported
wineserver: sock_get_ntstatus() can't map error: No route to host
fixme:winsock:NtStatusToWSAError Status code c0000001 converted to DOS error code 1f
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:iphlpapi:GetBestInterfaceEx address family 23 not supported
fixme:iphlpapi:adapterAddressesFromIndex address family 23 unsupported
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:iphlpapi:GetBestInterfaceEx address family 23 not supported
fixme:iphlpapi:adapterAddressesFromIndex address family 23 unsupported
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
wineserver: sock_get_ntstatus() can't map error: No route to host
fixme:winsock:NtStatusToWSAError Status code c0000001 converted to DOS error code 1f
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000017
```
What went wrong? How can I fix this?

---

### Post by Rasa1111 on 2010-05-07
can I ask..

why are you using utorrent in wine?

Do you know there are other bittorrent clients that work great in Ubuntu?

Like Deluge, Ktorrent, Transmission,
(Im partial to deluge myself)

 I guess I just wonder why you wouldnt use one of those?
 that work perfect on Ubuntu alone, 
rather than with some other app needed. ....
 unless you were not aware of them?

I dont use wine so i cant help there, 
but you should really try a client thats made for Ubuntu.
[Deluge is almost exactly like utorrent] only a lil better imo. lol

---

### Post by avada on 2010-05-07
> **Rasa1111 said:**
> can I ask..

why are you using utorrent in wine?

Do you know there are other bittorrent clients that work great in Ubuntu?

Like Deluge, Ktorrent, Transmission,
(Im partial to deluge myself)

 I guess I just wonder why you wouldnt use one of those?
 that work perfect on Ubuntu alone, 
rather than with some other app needed. ....
 unless you were not aware of them?

I dont use wine so i cant help there, 
but you should really try a client thats made for Ubuntu.
[Deluge is almost exactly like utorrent] only a lil better imo. lol

I tried them (except KTorrent maybe) a while ago. I think U missed some functionality and convenience otherwise I would be using them. Also with utorrent I can just continue using where I left it under windows.

---

### Post by Rasa1111 on 2010-05-07
> **avada said:**
> I tried them (except KTorrent maybe) a while ago. I think U missed some functionality and convenience otherwise I would be using them. **Also with utorrent I can just continue using where I left it under windows.**


ahh, I understand.
makes sense now.  

Ktorrent is also really close to utorrent and deluge. 

well, then I guess we wait for someone who knows what theyre talking about. lol :)

good luck

---

