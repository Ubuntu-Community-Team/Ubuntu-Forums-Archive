---
title: "RemoteApps with Ubuntu 16.04.1 LTS?"
date: 2016-08-09
forum: Virtualisation
---

### Post by darren-j on 2016-08-09
I have Ubuntu 16.04.1 64-bit installed as the host with Windows 10 Enterprise 64-bit setup as a guest in Virtual Box.  RemoteApps have been configured in Windows 10 Enterprise VM & I am able to RDP to the VM with Remmina using the host's Computer Name &/or the host's IP Address.  I have been unable to successfully launch any RemoteApps using Winconn.  Does anyone know if RemoteApps will work on Ubuntu 16.04?  I have seen a number of posts using 14.04 but have been unable to find any mention, one way or the other, as to whether RemoteApps will work on 16.04.1.

Best-

Darren

---

### Post by MAFoElffen on 2016-08-09
Let me get this straight. Where do you have your IIS and RD Session Host Role Service installed to? Are you trying to host an RD Web Access Web site on your Windows 10 Enterprize VM?

Because, once that is hosted, the client side is just a browser for the RemoteApp menu, then an RDP client: [XRDP on Ubuntu 16.04]("http://c-nergy.be/blog/?p=8952")

---

### Post by darren-j on 2016-08-09
Thank you for the prompt response.  IIS & RD Gateway have not been configured.  The Windows 10 Enterprise VM is hosted locally, on a Ubuntu laptop, through Virtual Box  (NAT with Port Forward TCP 3389).  The Windows 10 Enterprise registry was configured using the RemoteApp tool from [http://www.kimknight.net/remoteapptool](http://www.kimknight.net/remoteapptool).  It was my understanding IIS & RD Gateway were not needed for this setup.  On the Ubuntu host, I have been attempting to use WinConn to create an icon/launcher for the RemoteApps but have been unsuccessful in getting WinConn to connect to the VM.  Remote Desktop Services is running & I have confirmed I can RDP to the VM via Remmina.

---

### Post by MAFoElffen on 2016-08-10
On one side, you have me at a slight disadvantage. My experience with Win RemoteApps is with Win Server 2008 through 2016 (Preview 5). I've not done it from a Desktop Edition. But I think the same diagnostics techniques should work.

And thank you for sharing that link. That is something I'm going to learn more about and play with it.

My initial thoughts would be to verify the networking connectivity and the services:
Can you ping the Vm from your host? You are verifying that you have a valid route from your Host (the RDP client) to your Win VM Guest (your RDP server).

In your Win VM Guest, open the registry and verify your port number in:
```

HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp\PortNumber

```
The default is 3389, but is configurable, so verify what is is.

Then get to a cmd prompt in your Win VM Guest and see if your service has a listener open on that port.
```

netstat -abno | find /I ":3389" 

```

Next, go to your RDP client. Verify than your RDP client is configured for the IP and port of your VM Guest.

You said you are doing port forwarding through NAT... Please describe how you are doing that... Why are you not bridging your VM to your host network?

Next would be to check that the port is getting through the firewalls of both your Host and VM Guest. Easiest and fastest is to just toggle them off temporarily, to see if that changes your result.

---

