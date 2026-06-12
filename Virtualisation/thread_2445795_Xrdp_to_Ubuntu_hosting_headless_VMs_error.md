---
title: "Xrdp to Ubuntu hosting headless VMs error"
date: 2020-06-19
forum: Virtualisation
---

### Post by aquascrotum on 2020-06-19
I have a machine running Ubuntu 20.04, with Virtualbox running 2 headless Windows VMs in parallel. 

The 2 VMs have bridged network connections and static IPS. I use windows remote desktop from other machines on the local network to access the VMs which works well. 

I installed xrdp with the intention of using remote desktop to manage the ubuntu installation, however when I connect via RDC to the ip address or computer name of the Ubuntu host, it connects to the display of one of the VMs. 

Is this a consequence of the bridged network connection or how can I connect to the ubuntu desktop?

---

### Post by TheFu on 2020-06-22
Here's my guess.

Probably an issue with Windows proprietary authentication of connections.  Determine the method used on Windows, then seek the highest, most secure method, supported by xrdp.  Finally, you want to lower the Windows authentication method to the level that xrdp supports.

Microsoft has been improving defaults for security across Win10, as their users migrate. This has been disrupting all sorts of connectivity between CIFS, Samba, and RDP.  Google for "*Win10 rdp authentication from Linux*", hopefully that will find the issue and settings on a Win10 site.
[https://kamarada.github.io/en/2020/04/20/remote-desktop-connection-to-windows-from-linux-using-rdp-clients/](https://kamarada.github.io/en/2020/04/20/remote-desktop-connection-to-windows-from-linux-using-rdp-clients/)
> At some point, Microsoft released an Windows update that has since made the use of Network Level Authentication (NLA) required by default. FreeRDP does support NLA, while rdesktop does not.

Static IPs are good.
Bridges, assuming they are working properly are good (well, within the known limitations around security that all host-based bridging includes).

---

