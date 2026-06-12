---
title: "vmware : Host and Guest communication"
date: 2007-12-24
forum: Virtualisation
---

### Post by s_raghu20 on 2007-12-24
Hi,

I have a gutsy host and another gutsy as guest using vmware. 

Though the installation went fine, and the guest system can see internet etc (I have using NAT).. it cant see the host system. Same goes for the host, it just doesnt see the guest.

Please help.

regards
raghav..

---

### Post by popch on 2007-12-26
What do you mean by 'seeing' ? Can you ping one machine from the other one using the IP adress ?

What kind of LAN do you run, and does it have a DNS server?

---

### Post by veloce on 2007-12-27
If you have NAT working, then there will be a virtual network containing both your host and vm. 

Run "ipconfig" in a terminal of each machine.

On the vm you should get just one network (the NAT one)

On the host you will get at least two, one being real another being vmnet0, 1,2 or 8.  find the one with the same subnet as your vm network.  192.168.???.???  

You should be able to communicate between them by specifying the ip addresses.  As per the previous post, try pinging the other address from each machine.

As for communication between them, what do you want to do?  Share a file directory? Use ssh?

---

