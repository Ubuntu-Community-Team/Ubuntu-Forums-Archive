---
title: "Complete Newbie w/ Virtual Box"
date: 2009-04-29
forum: Virtualisation
---

### Post by gdonwallace on 2009-04-29
I have just upgraded to 9.04, 64 bit Ubuntu.  At the same time I downloaded and installed VIrtual Box. (Also did the upgrade today to version 2.2.2) 

I am trying to get virtual box to find the virtual installs of Windows XP and some other distro's of Linux that we have on a dedicated server on our internal network.  But, I have yet to figure out how to get to the server so that it can find them.

We have everything setup on DHCP.  I don't need internet access from these virtual "Machines", I just need to ge to them to administer them if needed.

Any help would be appreciated.

---

### Post by Perryg on 2009-04-29
If you can connect to the network drive then you can go into the VBox preference and set the path to the VDI files there. Keep in mind that you will not be able to see these connections if the server ip address changes unless you have a means to reach it by name. I would think that the network server would be a constant address so this should not be an issue.

---

