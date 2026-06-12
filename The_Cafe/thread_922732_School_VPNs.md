---
title: "School VPNs?"
date: 2008-09-17
forum: The Cafe
---

### Post by Warpnow on 2008-09-17
These things confuse the hell out of me.

I downloaded the Client. Patched it. Compiled it, and have run it and connected it...

Now what does it DO?

I understand I am supposed to go through their connection...but how? My IP doesn't change when I run the VPN.

```

chase@chase-desktop:~$ vpnclient connect
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

The command you are trying to execute requires additional parameters.
Usage:
 vpnclient connect <profile> [user <username>] [eraseuserpwd | pwd <password>]
                             [nocertpwd]
 vpnclient disconnect
 vpnclient stat [reset] [traffic] [tunnel] [route] [repeat]
 vpnclient notify
 vpnclient verify [autoinitconfig]
 vpnclient autoinit
chase@chase-desktop:~$ vpnclient connect UTD-ISP
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at 129.110.16.13
User Authentication for UTD-ISP...

Enter Username and Password.

Username [cnb083000]: 
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.

 
            VPN tunnel to UTD established

  If your computer is running a Microsoft operating 
  system, you should visit the following website and 
  install any critical software updates required for 
  your computer.  http://windowsupdate.microsoft.com/

Do you wish to continue? (y/n): y

Your VPN connection is secure.

VPN tunnel information.
Client address: 10.40.1.33
Server address: 129.110.16.13
Encryption: 128-bit AES
Authentication: HMAC-SHA
IP Compression: None
NAT passthrough is active on port UDP 10991
Local LAN Access is enabled

```

I need to access some journal things through the library...

Do I have to CHOOSE to go through the VPN somewhere?

---

