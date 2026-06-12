---
title: "XP listening on port x in virtualbox, but host not."
date: 2008-09-09
forum: Virtualisation
---

### Post by jezjones on 2008-09-09
I am running XP in a virtual box, using NAT for the networking.
This means XP has an IP of 10.*, whereas the host has a 192.* IP.

This should not really matter due to the use of NAT. I can connect ouwards from XP to the internet, so networking is functioning.

What i would like to do is connect from my lan to XP.
I am running a network rendering tool on XP that listens on port 28257 and 28258.

A netstat on XP shows it is listening on those ports, but on the host box, i only have http, mysql and ssh open.

I tried running 

 sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 28257 -j ACCEPT

in the host but it does not seem to make a difference.

I started up Firestarter and have set the policy to allow connections on those ports, but still i cannot connect to the XP in the virtualbox.
I have also stopped firestarter so that no firewall is running, but still only get the original 3 ports showing as open.


Any suggestions?

---

### Post by triphazard on 2008-09-09
I hope I'm understanding this correctly...it seems to me that rather than using NAT you'd want to use bridged networking.  This is available by default in apps like VMware but needs some fiddling to get working in VirtualBox.

[This tutorial]("http://samiux.wordpress.com/2007/07/11/bridge-network-interface-on-virtualbox/") shows you how to create the bridge in Ubuntu and also tell VirtualBox how to use that connection instead of NAT.

That way the XP virtual machine can have its own separate IP address on your lan.

I hope that was what you're after.  If not, just let me know.

---

### Post by jezjones on 2008-09-10
Thanks for the reply, i wanted to try it out before getting back to you.

I think you understand the problem. Although i did not have much luck with the tutorial, so i am not so sure that bridging is the way to go.

When i did the bridging thing, my virtual box got the same IP as the host, in the 192.168 range, rather than the 10.0... range as before.

This didn't get around the other machines on the network finding it.

I think all i need to do is work with the NAT to provide port forwarding from my host to the guest, the internal network is fine on another IP range i think.

~~~~

writing things down often helps and having posted, i have now searched on port forwarding from host to guest and found this which seems to be what i am looking for...

[http://sk.c-wd.net/wp/2008/01/05/virtualbox-port-forwarding-with-linux-host/](http://sk.c-wd.net/wp/2008/01/05/virtualbox-port-forwarding-with-linux-host/)

---

