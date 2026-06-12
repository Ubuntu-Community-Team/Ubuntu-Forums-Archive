---
title: "VirtualBox WinXP GUEST accessing HOST local webserver?"
date: 2008-03-18
forum: Virtualisation
---

### Post by mrmoney on 2008-03-18
Hi,

I was wondering if it was possible to have a setup like so.
On my Ubuntu HOST, I have my own local webserver running on which I can do my web developement locally. 

I installed VirtualBox and Windows XP as a GUEST for the sole purpose of being able to test various browsers on a windows OS.

So ideally Id like the WinXP guest to just be able to hit my webserver running on my Ubuntu OS. 

Normally I would have a webserver running on Windows and just modify the hosts file to point certain domains at the local server, but that would require copying the files over from Ubuntu to Windows and running two separate servers when all I want in Windows is to be able to test sites in the browsers.

Anoter solution, though less ideal, would be that I could install the webserver on windows, then share my harddrive between the two and just point the Windows server virtual hosts to the existing files, negating the need to copy over any files. Though Id like not to have to do this if there is an easier way.

Can this be done?

Thanks in advance

---

### Post by vikrant82 on 2008-03-18
You could setup advanced networking so that your windows host gets a DHCP address directly from the router. 

However for your simple requirement (Assuming you have given a NAT connection to windows host), the default gateway on windows machine is the address of your ubuntu host.

http://<default_gateway>:<port> should do it.

You could look for default gateway using "ipconfig" on windows host.

Hope this helps.

---

### Post by Hero of Time on 2008-03-18
I replied here: [http://forums.virtualbox.org/viewtopic.php?t=5238](http://forums.virtualbox.org/viewtopic.php?t=5238)
Use nat, connect through 10.0.2.2 to access your Host webserver.

Next time, check your other topics first before asking somewhere else ;).

---

### Post by mrmoney on 2008-03-18
hi,

thanks for the replies. Modifying the windows hosts file to point my virtualhost names to 10.0.2.2 has done the trick. Thanks again

---

### Post by viento on 2012-08-23
hello! :) sorry, if this was asked before - i'm really new to Ubuntu.

what is i want to access one of my Apache "Virtual Hosts" on my host system from my guest system?

my setup is: Ubuntu 12 + VirtualBox - Windows XP as a guest system.

thanks in advance! :)

---

