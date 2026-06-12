---
title: "Samba Printing"
date: 2008-05-10
forum: Server Platforms
---

### Post by Spready on 2008-05-10
Hi all,
I have tried and tried with this and searched everywhere but cannot find the answer to this.
I have recently rewired my home network and it now consists of:
1 Xubuntu 7.10 acting as a File & Print Server.
2 Windows XP Machines, 1 work and 1 kids.
1 Ubuntu 8.04 Machine for everyday stuff.  

On the Xubuntu Print Server I have a Canon MP500 connected via USB and shared.
I can print perfectly from that machine AND also from any of the Windows boxes. 
Problem: When I try to connect to this Printer from the Ubuntu PC, upon the verify connection test I get the error:
" Print Share Is Not Accessible"
Upon searching the forums there are suggestions that changing the machine name to the IP address should help. 
I have tried smb://192.168.X.X/MP500 but nothing.
Any help appreciated.

David

---

### Post by Sef on 2008-05-10
Moved to Server Platforms.

---

### Post by Spready on 2008-05-11
There must be a simple solution to this problem. 
I can see the printer - I can point CUPS to it on the Ubuntu box by selecting a Samba printer but still nothing.
Any Ideas?

---

### Post by Spready on 2008-05-11
Ok! I am officially stupid!
After hours of fiddling - IT WAS SO SIMPLE!
On the server - open the CUPS admin page by entering [http://localhost:631](http://localhost:631)
Then select the Manage Printer button.
You will then see a tick box for Share Printer on network.
As they are both Linux  - it doesn't have to go through SAMBA (That was the bit that got me stuck!!)
Then on the conected desktop, when I select prining - I see a new printer under 'Remote Printers'. It has automatically found the MP500 and also set it to default printer!

I am now happy!
Hope this helps others!!!!

---

