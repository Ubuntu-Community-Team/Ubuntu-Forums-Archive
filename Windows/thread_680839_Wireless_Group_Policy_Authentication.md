---
title: "Wireless Group Policy Authentication"
date: 2008-01-28
forum: Windows
---

### Post by Pablohoney32 on 2008-01-28
I am running a small Win2003 network and want to control Wireless access authentication via Group Policy to prevent the user from removing there Wireless connections. 
I have created a GPO within the Client OU and via the Wireless Network Policy have set encryption to WPA-PSK. The Policy applies but the Client  can not acquire a Network Address. 
When I add the Wireless settings\credentials before Policy is applied the Client will connect ok. Even when I then apply the Policy via a gpupdate the connection remains constant.
The problem starts when I reboot the Client. Once rebooted the Client again can not acquire a Network address.
I have had a look at Local Computer Group Policy but no Wireless Policy appears to exist there. 
Can anyone advise me how to keep the authentication on the client after reboot? 

Cheers,
Pablo

---

