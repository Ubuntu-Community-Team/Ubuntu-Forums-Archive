---
title: "TightVNC on Windows Server 2000"
date: 2008-07-25
forum: Windows
---

### Post by gunksta on 2008-07-25
I have just been appointed the network administrator at work. This means I do more work without additional pay.

It also means I have to administer a Windows based network.  :-(

Oh well.

I have a server and I would like to give myself off-site access to it in case something goes awry. I have TightVNC installed and locally it works like a charm. But, when I'm off-site I can not get it to respond even though I am using the server's external IP, not the local IP address.

The box has a permanent IP address via our ISP.

I'm not familiar with VNC or Windows, so I'm pretty much SOL on this one. I suspect it may be the ISP's firewall. Any suggestions on how to test for this?

TIA!

---

### Post by seanc7 on 2008-07-26
First thing, check with the ISP about possibly blocking that traffic at their firewall.

---

### Post by rickyjones on 2008-07-28
1. If the server has Terminal Services installed then I would recommend that in addition to VNC as, in my experience, RDP is a bit more responsive over the WAN.
2. Verify that the ports necessary for this operation are open through your firewall. VNC is by default 5800 I think. RDP is 3389. Both TCP.

Sincerely,
Richard

---

### Post by gunksta on 2008-07-28
Hey thanks for the info. I was wondering if using RDP might be a better solution.

---

### Post by dca on 2008-07-28
Was RDP avail in Win2k, I thought it came out in XP/Server2k3?

---

### Post by rickyjones on 2008-07-28
> **dca said:**
> Was RDP avail in Win2k, I thought it came out in XP/Server2k3?

RDP, aka Remote Desktop Protocol, has been available since at least Windows 2000. However it was only available when you installed Terminal Services. Windows 2003 and XP have this functionality built in by default.

-Richard

---

