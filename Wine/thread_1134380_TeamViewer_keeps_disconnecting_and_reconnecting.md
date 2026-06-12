---
title: "TeamViewer keeps disconnecting and reconnecting"
date: 2009-04-23
forum: Wine
---

### Post by eilios on 2009-04-23
^
I am using Jaunty, with wine 1.1.19. I get this error.
```

fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:msg:ChangeWindowMessageFilter 4a 00000001
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_MAX_CONNS_PER_SERVER (20): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_MAX_CONNS_PER_1_0_SERVER (20): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (9000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 9000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 120000
fixme:shell:IsUserAdmin stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x32f0e8,0x00000001,0x32f104) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:dwmapi:DwmIsCompositionEnabled 0xbde1a8
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32e8c4,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x5004e 0x00000000
fixme:msg:ChangeWindowMessageFilter c042 00000001
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x12fddd4,0x00000001,0x12fddf0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x32dd80,0x00000001,0x32dd9c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 3
fixme:wininet:INET_QueryOption Unhandled dwOption 2
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x32f0cc,0x00000001,0x32f0e8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 3
fixme:wininet:INET_QueryOption Unhandled dwOption 2
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x32f0cc,0x00000001,0x32f0e8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 3
fixme:wininet:INET_QueryOption Unhandled dwOption 2

```

---

### Post by eilios on 2009-04-24
Bump

---

### Post by quattrodrifter on 2009-04-28
I got the same problem with Hardy after an TeamViewer update.


```

fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_MAX_CONNS_PER_SERVER (20): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_MAX_CONNS_PER_1_0_SERVER (20): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (9000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x32f0e8,0x00000001,0x32f104) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32e8c4,0x00000000), stub!
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x7ddb0df4,0x00000001,0x7ddb0e10) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x80052 0x00000000
fixme:secur32:GetUserNameExW 2 0x32ed08 0x32ecf4
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x7ddb0df4,0x00000001,0x7ddb0e10) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:netapi32:NetWkstaUserGetInfo Level 1 processing is partially implemented
fixme:advapi:LsaOpenPolicy ((null),0x7ddb0df4,0x00000001,0x7ddb0e10) stub
fixme:advapi:LsaClose (0xcafe) stub


```


With Wireshark i see that my PC is sending RST packages to the TeamViewer server. So i think it is a Problem since the update from TeamViewer. :(

regards

 quattrodrifter

---

### Post by quattrodrifter on 2009-04-28
^^ Its a version problem.

Take 4.1.6016 and everythng is ok!!


I got the problem only with 4.1.5988 .


regards 

 quattrodrifter

---

