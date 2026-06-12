---
title: "VMWare Sever: Hardy Host and Win 2003 client won't talk to each other!"
date: 2008-07-19
forum: Virtualisation
---

### Post by SteveTheRed on 2008-07-19
Hello, 

Forgive me if this has been asked and answered before. My usually strong Google-fu has failed me for this problem.

I am running VMWare Server 1 on an Ubuntu 8.04 host and a Windows Server 2003 Standard Edition client. I installed VMWare via VMware's tarball and installed the any-any patch. I set up NAT (since I have a wireless adapter) and host-only networking. I also installed samba and a samba share.

In the windows client, internet access works fine. When I try to map my samba share to a windows drive, it will not connect, claiming that there is no network. I'm trying to map to the ip address of the host side of the host only network, although I've also tried to map every other ip I could come up with in desperation. I am also using "connect as user" with the name and password of the dedicated samba user on my host.

To add insult to injury, I can't uninstall VMWare Server, either.

Any ideas, please? Thank you.

---

### Post by tact on 2008-07-19
I also run winserver2k3 in a VM as needed from time to time.   Actually I run winserver2k3 in one VM, winXP in another, and another shade of linux in a 3rd VM - all running on my ubuntu hardy host.

Applications inside of the 3 VM's all talk together via tcp/ip and the server2k3 and XP VM's need to share folders to work together.

All three VM's can also see and be seen by the host.

I use VMware server compiled from source with the anyany patch pretty much as you have described.

Not trying to boast at all - just showing that what you want to do can be done.    Now all we need to sort out is what is different with your installation with a view to seeing what you need to fix.

1.  make sure you have no firewalls (host or VM's) that might be blocking things.
2.  configure the guest to use the NAT connection.  Check its accessing the internet properly.  Find out its IP address.  
3.  try to ping the host from the guest using IP addresses.
4.  try to ping the guest from the host using IP addresses
5.  repeat above pinging using hostnames instead of IP addresses
6.  open up nautilus and in the location bar type in smb://ip.address.of.machine/sharename
See how you go...  work from there.

---

