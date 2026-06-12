---
title: "Starcraft 2 can't login to Battlenet"
date: 2010-12-10
forum: Wine
---

### Post by Afisamuleal on 2010-12-10
Hello;

I've been playing around for a while trying to get Starcraft 2 to run on Ubuntu.

P7805u Gateway laptop
Nvidia GeForce 9800 GTS 1GB 
Wine 1.3 (I tried 1.2 earlier.)

I tried deleting all configuration files and reinstalling wine. This does not help. SC2 will open. It even updated, once (only once). However, when arriving at the Battle.net login screen, the standard "might be down or temporarily disabled" Internet/Battlenet message comes up. I can't find this problem anywhere on the internet.

Terminal output excerpt:

```
fixme:process:GetLogicalProcessorInformation ((nil),0x32c86c): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:process:GetLogicalProcessorInformation ((nil),0xf3c620): stub
fixme:process:GetLogicalProcessorInformation ((nil),0xf3c60c): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:process:GetLogicalProcessorInformation ((nil),0x103e9b8): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (2000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 2000
fixme:process:GetLogicalProcessorInformation ((nil),0x103e9b8): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x103e9b8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0xd3c304,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000003 not handled
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation ((nil),0x103e9b8): stub
sam@orange:~$ fixme:process:SetProcessDEPPolicy (1): stub
fixme:process:GetLogicalProcessorInformation (0x33fa5c,0x33fd5c): stub
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x148a58, 0x43cf0e8
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x43ced78,0x43ced7c): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:win:EnumDisplayDevicesW ((null),0,0x43cea08,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x43ce90c,0x00000000), stub!
```

---

### Post by Remmelas on 2011-01-01
Have you by chance found a solution?  I too am having the issue and haven't managed to find a solution regardless of hours of googling and reading forums, etc.

TIA
--Mike

---

### Post by Afisamuleal on 2011-01-07
No, indeed I have not yet found a solution. I am wrestling with some other problems right now, but I would suggest taking a look at this page:

[http://wiki.winehq.org/FAQ#head-0344b4325219c69636aeffeaa3596d6855283afd](http://wiki.winehq.org/FAQ#head-0344b4325219c69636aeffeaa3596d6855283afd)

Seeing if it helps at all (I don't quite recall if I tried that last time).

---

