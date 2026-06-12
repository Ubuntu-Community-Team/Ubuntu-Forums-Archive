---
title: "vmware workstation start virtual machine on boot?"
date: 2009-09-12
forum: Virtualisation
---

### Post by misha680 on 2009-09-12
Is there a way to do this?

I swear this was possible with VMWare Server but can't find with Workstation...

Thank you
Misha

(p.s. I like shared folders so don't want to switch to server)

Found a solution here:
[http://74.125.47.132/search?q=cache:qDiiiklApXoJ:www.experts-exchange.com/OS/Linux/Distributions/Ubuntu/Q_23297901.html+vmware+workstation+start+virtual+machine+on+boot&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.47.132/search?q=cache:qDiiiklApXoJ:www.experts-exchange.com/OS/Linux/Distributions/Ubuntu/Q_23297901.html+vmware+workstation+start+virtual+machine+on+boot&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a)

---

### Post by misha680 on 2009-09-13
Same idea, different command.

```

crontab -e

```

Copy and paste:
```

@reboot sleep 20; /usr/bin/vmrun start pathtomyvmx.vmx nogui

```

Misha

Ok only problem with this is that I don't think the vms get safely shut down on shutdown of machine...

I made a file /etc/init.d/vmware-workstation:
```

#!/bin/bash
/usr/bin/vmrun stop "/home/misha/vmware/Virtual Machines/Windows XP Professional x64 Edition/Windows XP Professional x64 Edition.
vmx" nogui

```

```

sudo chmod +x /etc/init.d/vmware-workstation
sudo ln -s /etc/init.d/vmware-workstation /etc/rc0.d/K00vmware-workstation
sudo ln -s /etc/init.d/vmware-workstation /etc/rc0.d/K06vmware-workstation

```

---

