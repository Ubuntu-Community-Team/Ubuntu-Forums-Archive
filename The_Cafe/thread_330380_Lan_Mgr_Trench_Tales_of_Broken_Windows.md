---
title: "Lan Mgr Trench Tales of Broken Windows"
date: 2007-01-03
forum: The Cafe
---

### Post by SuperMike on 2007-01-03
**WINDOWS:**
Today in the trenches I had a W2K3 file server that allowed fast downloads but super-slow uploads, over mapped drives. Same thing happens whether mapped by IP or name. Happens on all clients connecting only to this particular server. Happens on any shares this server has. Happens even when backup net card is disabled. Happens even though the net card is proven to be 100Mb full duplex. Happens even when the net card and protocol settings match the same as another, functional server. Happens even though we reboot the server. Happens even though the processor, memory, and net utilization show no errors, and when the event log has no correlating events, on both client and server, and tested on several servers. Happens even when the Ethernet switch is forced to 100Mb full duplex. Happens even on the same subnet. Baffles Microsoft Premier Support when I called them and spent 5 hours with them straight on the phone, running tests, finding out at least what it is *NOT*, but not any closer to what it is. I had to leave for the day and we plan to pick it up tomorrow.

The only clue we had was that the net sniffer said that all clients were being told mysteriously by the server to delay sending packets for 3 microseconds between packets, slowing things down. This pushes the problem up from the TCP/IP network layer and into the SMB protocol layer.

If the Windows OS is corrupt for these daemons, then there's more to it than having to uninstall the Server and Redirector services -- MS gives you no way to do that. Instead, you have to either do a repair install from the install cd, or use the install cd to install the OS into a separate directory. And you're going to need a reboot or two. Otherwise, you're looking at DLL and Registry surgery.


**COMPARISON ON LINUX:**
If NFS or SSHFS exhibited signs of trouble, I would simply backup the config files for these tools if I had them, and then use '/etc/init.d' option to shut down these services, and then use 'apt-get --purge remove' option to remove these things, and then remove the old config files if they were left behind, and then use 'apt-get install' option to install them back. Then, copy back out config files, update the system to the max, and restart services from /etc/init.d. No reboot necessary.

---

