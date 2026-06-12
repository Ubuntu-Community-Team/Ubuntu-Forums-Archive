---
title: "WSL2 Ubuntu WSLg Lithuanian language input not working"
date: 2023-06-11
forum: Virtualisation
---

### Post by ugnius40 on 2023-06-11
Hi,

I would like to use WSLg applications on Win11, but I'm having trouble with those apps recognizing Lithuanian input.
I get this in weston.log:

```
[19:52:39.463] Client: ClientGetAppidReq: pid:468 appId:Gedit WindowId:0x6
[19:52:39.464] Client: LanguageImeInfo: ProfileType: 2 (TF_PROFILETYPE_KEYBOARDLAYOUT)
[19:52:39.464] Client: LanguageImeInfo: LanguageID: 0x427
[19:52:39.464] Client: LanguageImeInfo: LanguageProfileCLSID: GUID_NULL
[19:52:39.464] Client: LanguageImeInfo: ProfileGUID: GUID_NULL
[19:52:39.464] Client: LanguageImeInfo: KeyboardLayout: 0x10427
[19:52:39.464] convert_rdp_keyboard_to_xkb_rule_names: matching model=pc105 layout=us variant=(null) options=(null)
[19:52:39.466] rail_client_LanguageImeInfo_callback: new keyboard layout: 0x10427

```

But still input works as if US layout is enabled.

I do not know how all the bits and pieces work together to get the right layout. 
May be there's some config file (like xkb config), where I could make changes myself - to make this work.

About my system:
Windows: Microsoft Windows 11 Pro, 10.0.22621 Build 22621
Linux: Ubuntu 22.04.2 LTS
WSL version: 1.2.5.0
Kernel version: 5.15.90.1
WSLg version: 1.0.51
MSRDC version: 1.2.3770
Direct3D version: 1.608.2-61064218
DXCore version: 10.0.25131.1002-220531-1700.rs-onecore-base2-hyp
Windows version: 10.0.22621.1702


Thanks,
I can provide any additional info...

---

### Post by TheFu on 2023-06-12
Does Ubuntu 22.04 running in a real virtual machine (virtualbox, VMware Workstation) have the same issue?

WSL is a MSFT tool.  WSLg is pretty new from MSFT.

---

