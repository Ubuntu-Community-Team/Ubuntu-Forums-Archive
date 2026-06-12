---
title: "Virtual XP guest - cannot share printer (or anything else!)"
date: 2010-02-14
forum: Virtualisation
---

### Post by Objekt on 2010-02-14
For a while I have had a Windows XP guest machine, using Virtualbox 3.1.2 PUEL, on my Ubuntu 9.10 64-bit host.  I had the printer shared from the XP machine, and it was visible to other Windows machines on my network.

A few days ago, for no apparent reason, the sharing stopped working.  That is, the printer is no longer visible to Windows clients on the network.  The virtual machine itself (named simple "VIRTUALXP") does show up, but none of its shared resources (printers or folders) are visible.

Around the same time, the Win XP guest stopped being able to browse the Web.  I fixed that by manually setting DNS server addresses, using the OpenDNS servers (208.67.222.222 etc.).  But I shouldn't have had to do that.  Before, the network connection was always set to "Obtain DNS server address automatically" and it worked that way.  

I can't help but think the two problems are related, but I have no idea how to fix them.

WTF is going on?  Why is all sharing broken suddenly, and why would I have to specify DNS servers manually?  I didn't make ANY changes to the virtual machine, or Virtualbox.

---

### Post by Objekt on 2010-02-15
OK things are back to normal.  I'm not quite sure how I fixed it, but in the process of trying, I did the following:

-Uninstalled NetworkManager (aka network-manager-gnome) on the Ubuntu host through Synaptic Package Manager.
-Deleted the entire folder /etc/NetworkManager (contains settings for NetworkManager connections).
-Reinstalled NetworkManager.
-Rebooted the host a couple of times.

I think there was something about the host's networking setup that was preventing the Win XP guest from communicating properly.  After I did the above, the printer I was trying to share from the Win XP guest - along with the guest's shared folders - immediately became visible to other Windows machines on the local network.

---

