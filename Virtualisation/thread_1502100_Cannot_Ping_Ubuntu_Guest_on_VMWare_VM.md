---
title: "Cannot Ping Ubuntu Guest on VMWare VM"
date: 2010-06-05
forum: Virtualisation
---

### Post by 808mlee on 2010-06-05
**Cannot Ping Ubuntu Running on VMWare VM** 
Hi:

I just completed clean install of Ubuntu Linux 10.04 to run Nagios. I have Nagios up and running properly and monitoring my windows servers. I have a couple of questions that I can't seem to find the answer to:

1. I cannot ping the Ubuntu VM from other machines on the same subnet. I can ping the Host system from other machines on the same subnet. I can also log on to the Ubuntu VM and ping all other machines on the local subnet. I can also ping the Ubuntu VM from the VMWare host system.

2. I have installed apache and the Nagios software is running correctly but I can't use a web browser to attach to the Nagios web page from other machines on my local subnet. I wonder is this is related to my inability to ping the Ubuntu Linux machine.

Some things I have tried:

1. Disable IPV6
2. Check to make sure firewall is turned off. I ran iptables -L and see no rules
3. This is running in bridged mode.

I don't know what else to do at this point. Any help you can provide will be greatly appreciated.

Thanks.

Mark Lee

---

### Post by Jeroensum on 2010-06-05
Can you please post the ip settings of:

-Your host
-The Nagios VM
-One of the hosts on the subnet

---

### Post by 808mlee on 2010-06-07
Here is my setup:
 
Host System:  Windows XP Pro.  IP address 192.168.17.100/21.
 
Guest System running on VMWare Server:  Ubuntu Linux 10.04.  IP address 192.168.17.101/21.
 
The thing is I can ping the guest system from a command prompt on the host system.  so ping from 100 to 101 is okay.  Also ping from 101 to 100 is okay.
 
I have another client 192.168.16.220/21.  I can ping from 101 to this 16.220 address but when i ping from 16.220 to 101 it fails.
 
Mark

---

### Post by Jeroensum on 2010-06-07
Ok, just summarizing here.

We know the connectivity is good, since you can ping from the ubuntu machine to other clients.
We also know the ubuntu machine is responsive so there's nothing on the ubuntu machine blocking icmp or other connections. Since you have installed Nagios I also assume the ubuntu machine is capable of real network connections (pulling files over the net) instead of only being able to ping.

The culprit here seems to be your windows box, or the vmware server application, blocking icmp or possibly all connections.

Now the thing I know about Windows XP pro editions, especially with an SP2 or 3 setup, is that they have a firewall running. You can disable this thing by stopping it in the services module or trough the command line:
Start -> Run -> services.msc (find firewall service and stop)
or
Start -> Run -> cmd.exe -> net start (copy the firewall service name)
net stop "(paste full firewall name)"  (really use the double quotes!)

Now when the windows firewall is out of the way, you might want to check if you have any VPN software installed on the windows box, if so uninstall it. Sometimes the VPN software messes up the network-adapters so vmware can't make heads or tails of it.

Hope this helps :)

---

### Post by 808mlee on 2010-06-08
Thanks for your input.  I found out what my problem is.  I have Symantec running on the host system and I thought I had disabled network threat protection but it was turned on.  Turned it off and all is well.
 
Thank you.
 
Mark

---

### Post by Jeroensum on 2010-06-12
Great! Case closed so to speak :)
Kindly prefix your topic tile with the [Solved]  tag so people know :)

---

