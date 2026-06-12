---
title: "VMware Player Issue"
date: 2013-04-30
forum: Virtualisation
---

### Post by db63 on 2013-04-30
Here's the issue...

I had installed VMware Player. This was a clean install and everything was working fine. I had just started setting up a VM and right during the middle of the VM setup, the computer powered off. Yep, I had a power outage and no UPS. So, I come back into Ubuntu and open up VMware Player only to receive the following message..."Before you can run VMware, several modules must be compiled and loaded into the running kernal". Well, the two options are "Cancel" and "Install". I select "Install" and absolutely nothing happens. The Player never opens...nothing. So, I tried to do another install...will not install...nothing happens. Any suggestions? I'm thinking that even though the Player may be corrupt, there is some type of service that is running and could be causing the issues? I'm just not sure. Suggestions are welcome! Thanks.

---

### Post by taidoka on 2013-05-12
Could you try uninstalling vmware-player?
```
 sudo vmware-installer -u vmware-player 
```

---

