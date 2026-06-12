---
title: "Samba OpenLDAP and Landscape"
date: 2018-12-03
forum: Security
---

### Post by gone.sovereign on 2018-12-03
Hi All,

I'm newish to the linux community and looking for some direction on building out my very small network.  I have 10-12 computers with various OS's from Windows 7, Mac OS and Ubuntu 18.04 both desktop and server.  I'm looking to centrally manage the network with a domain controller but I'm having a problem finding the right solution, many of them out there.  I'd like to manage security authorization as well as login scripts and system updates etc...I also have a file server and VM server. I've been scouring the web and youtube and most of the info I'm coming up with is either piecemeal or really old.  I have a VM sandbox spun up so I can play around with different options but I'm having a problem bringing it all together.  I think what I'm looking for is something like using OpenLDAP as a back end data base for Samba as the PDC and then running second instance of Samba on my file server to handle drive shares.  I was just digging into Ubuntu Landscape though and that looks like a really cool tool for managing packages and updates.  

So with all this rambling I guess my questions are as follows.
1. Will the above do what I'm looking to do?
2. What order do I want to spin this network up?  Should I first get the PDC in place and then add my DNS server and File Server Etc...
3. can I run landscape along side samba or would landscape take the position of a PDC.

Any help is appreciated.

---

