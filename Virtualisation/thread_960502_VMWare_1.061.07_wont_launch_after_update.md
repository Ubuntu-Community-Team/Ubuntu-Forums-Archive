---
title: "VMWare 1.06/1.07 wont launch after update"
date: 2008-10-27
forum: Virtualisation
---

### Post by toy71camaro on 2008-10-27
Been using Ubuntu 8.04 and VMWare 1.06 for a while now. Was prompted to install some updates for Ubuntu. So I did them. AFter that, When I restarted and went to launch VMWare Server, it starts to load (mouse spins, get the program launch on the task bar, then nothing happens).

I tried  reinstalling (which upgraded to VMWare 1.07).

Then I tried re-compiling (sudo vmware-config.pl) after finding that suggestion in the Virtualization Sticky.

I get the following message when I do it, and i have tried both yes/no and no change:

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same compiler as one used for building your kernel. Do you want to go with compiler "/usr/bin/gcc" version "4.2.4" anyway?

Please help a newb out :)

---

### Post by toy71camaro on 2008-10-28
Bump... any help please??:confused:

---

### Post by fjgaude on 2008-10-28
I've compiled with different gcc and it worked. So:

Do you want to go with compiler "/usr/bin/gcc" version "4.2.4" anyway?

Answer, yes.

See what happens.

---

### Post by toy71camaro on 2008-10-28
Thanks for the response. 

I did try the YES option togo with the 4.2.4 compiler, but no luck. I tried uninstalling it, then re-installing it. It mentions the same message about being compiled differently (if you answer no, it aborts the install). I chose YES, but same result - the task bar shows "VMWare Server", the mouse spins, then after about 10 seconds the task bar item goes away, and nothing ever opens.

---

### Post by fjgaude on 2008-10-28
Have you tried using vmware-any-any-update117? I can't say where to get it but it has worked for some folks. Google it and likely you'll find.

---

### Post by toy71camaro on 2008-10-28
Thank again for the suggestion.

I went and tried the any-any patch, but same result, other than the shortcut moved from the "system tools" section to the "other" section.

Still not able to launch the VMWare app, and access my VM's.

---

### Post by fjgaude on 2008-10-28
Try from the commandline, first without sudo then with.

---

### Post by Zarckon on 2008-10-29
I'm having the same problem. Looks like gcc got updated before it should have been. Is there some way to go back to the earlier version of gcc?

---

### Post by toy71camaro on 2008-10-29
well after lots more searching - i was able to find someone who had a fix:

> **dmizer said:**
> This script is not needed to install vmware server.

Install as normal, then perform these commands:
```
sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

That's it. No script. This process has worked for me for the past 3 or 4 vmware server versions in Hardy.

Fix found here: [http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

---

### Post by Zarckon on 2008-10-30
Toy,

Thanks for those two (2) lines. Worked perfectly.

---

