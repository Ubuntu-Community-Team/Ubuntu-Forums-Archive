---
title: "Problem with LTSP and client"
date: 2015-09-02
forum: Virtualisation
---

### Post by vladan3 on 2015-09-02
Hi all,i have some kind of problem with my ltsp.I need to install ltsp(Ubuntu) and configure him to allow some random client to access server and boot his op system.When i try that the client vm on my workstation sent me this error PXE-M0F: Exiting Intel PXE ROM.Operating System not found.
[IMG]http://s17.postimg.org/jsbfk32gv/error.jpg[/IMG]
My configuration for the ltsp interfaces is
[IMG]http://s17.postimg.org/fte819dtr/interfaces.jpg[/IMG]
And for dhcp is:
[IMG]http://s17.postimg.org/ocxlz0m67/dhcp.jpg[/IMG]
I am not expert but i think that dhcp is that connection the allows that client to access ltsp.
p.s my ltsp server have two network cards,first is set on Host-only,and secound is on Briged,and my client vm is on Host-only.
Tnx everyone.

---

### Post by jgordon2 on 2015-09-09
If I am right, you are doing this all on VMs?  I don't know if this is as much an Ubuntu issue as it is, are your BIOS configs set to properly boot from the network (on your VM).  Is VMWare capable of this?  Have you checked VMWare's docs on PXE?

Good luck!

---

### Post by vladan3 on 2015-09-10
Hi man,tnx for the re,i found what the problem is but dont know how to fix it.The problem is with dhcp server,he won't start after configuration,on the start he work fine,but after i set static ip and configure him he stoped.I tried too many things for ex to turnoff network manager service,to turn off my local dhcp service,but result is the same,fail to start dhcp server.My thin client doesn't recive ip and he can't connect to ltsp.I almost give up,but i really want to find solution for this problem.Tnx again.

---

