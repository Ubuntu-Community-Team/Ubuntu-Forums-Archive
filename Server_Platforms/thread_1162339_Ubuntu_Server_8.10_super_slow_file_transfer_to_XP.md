---
title: "Ubuntu Server 8.10 super slow file transfer to XP"
date: 2009-05-17
forum: Server Platforms
---

### Post by reveller on 2009-05-17
Hello, 

I am trying to copy files from Ubuntu Server 8.10 to Windows XP.  I have tried what seems to be every combo of mount, mount.cifs, smbmount, smb.conf options, socket options, windows settings, and still cannot get more than 70kbps transfer rate to my XP machine.  

Both boxes have Gigabit ethernet going through an unmanaged gigabit switch with cat6 cables.  I ran iperf both ways and XP is getting 90Mbps to Ubuntu, but Ubuntu only gets 70kpbs to XP.  

iperf between 2 Ubuntu Server boxes on the same network, same switch, same ethernet cards and cables shows 951Mbps!

Not sure what I'm doing wrong.  Any direction or help would be greatly appreciated, as this is my first venture into the Linux domain :)

Thanks, rev

---

### Post by reveller on 2009-05-17
Fixed almost immediately after I posted this! (After searching for 3 days)

I changed the NIC's 'Speed and Duplex' mode on my Windows machine to Auto.

Now iperf gets 941Mbps from Ubuntu to XP!  

Soooo relieved!  Hope this helps someone!

---

