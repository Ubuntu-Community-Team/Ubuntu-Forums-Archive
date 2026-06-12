---
title: "Libvirt nat portforwarding"
date: 2013-06-05
forum: Virtualisation
---

### Post by Yahya5678 on 2013-06-05
Hello guys,

I have server A with libvirt installed. On that server, there are several vms (managed by libvirt) that are on NATTEd network behind a bridge on server A.

I have another server (diff network) that I connect to server A that hosts libvirt but it does not allow me to ping to the vms hosted on server A.

Someone suggested to me that I have to do some port forwarding using ip tables on server A.

Is this the way forward or do I have to do something else?

Any help, greatly appreciated

Thanks

---

### Post by NigelRen on 2013-06-05
I had the same problem, the solution in my case was that iptables was rejecting any connection to the machine. When I did iptables -L -n I get something like

```
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            192.168.122.0/24     state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

```
I had to delete these last two rules using something like iptables -D FORWARD 5  also same for iptables -D FORWARD 4. This then seemed to pass through al traffic to the virtual machine.

General IP tables stuff - [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Yahya5678 on 2013-06-05
Hi nigelren, but what if I want to ping or connect to vms that are hosted on server A and I want to ping them directly from server  B without connecting to server A first. Does that make sense

---

### Post by NigelRen on 2013-06-05
I use a virtual machine as an apt-cache server so I needed to connect from machine B to a VM which was running on server A.  This is where when I attempted to connect I was getting a port unreachable error - which is where iptables reject was causing the problem.
The iptables configuration has to be done on server A, this then allowed other machines to connect to the VM.

---

