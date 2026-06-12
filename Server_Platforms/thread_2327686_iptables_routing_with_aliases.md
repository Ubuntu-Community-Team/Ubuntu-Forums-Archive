---
title: "iptables routing with aliases"
date: 2016-06-13
forum: Server Platforms
---

### Post by AlmoG on 2016-06-13
Hi, I have a problem I was hoping to solve with iptables, but any other solution will be appreciated.

I have a tool I use to overload my DB server with queries (for load balancing tests).
The problem I have with this tool is that it can only run from a single IP address, when I need to run it with multiple addresses.

I've created aliases on my NIC like so:
eht0 10.0.0.1/24
eht0:0 10.0.0.2/24
eht0:1 10.0.0.3/24
eht0:2 10.0.0.4/24

And now I want to run my tool simultaneously from these 4 addresses and have the source IP be different for each run.
e.g:
```

change_route eth0 && db_load_tool &
change_route eth0:0 && db_load_tool &
change_route eth0:1 && db_load_tool &
change_route eth0:2 && db_load_tool &

```

I don't have a lot of experience with iptables or routing so I'm hoping you guys could help me out.

Thanks.

---

### Post by SeijiSensei on 2016-06-13
I don't think iptables has any mechanism to do what you want. 

Your best bet would be to use VirtualBox or a similar virtualization solution and create multiple virtual machines on the client computer.  Make sure you choose "bridged" networking so each machine talks directly to the local network.  Give each VM a separate IP address either statically or via DHCP.  For your purposes I'd use Ubuntu server as the OS in the VMs since you don't need the overhead of running GUI desktops on each VM.  You can probably run each machine in [256 MB]("https://help.ubuntu.com/community/Installation/SystemRequirements") of physical memory.

---

### Post by AlmoG on 2016-06-13
Thanks for your input @SeijiSensei 
I was thinking something more in terms of routing tables and packet data manipulation.
This mechanism needs to be able to scale up or down - creating more IP aliases on demand and such, so setting up a virtual machine for each alias is pretty much out of the question.

Any other ideas?

---

### Post by SeijiSensei on 2016-06-13
I've only used aliasing to support multiple listeners on a single interface, for instance a separate HTTPS listener on a IP distinct from the primary address to which Apache listens on port 80.  Outbound traffic is going to use the primary eth0 address as far as I know, regardless of the number of aliases involved.

If you generate the tests with telnet, you might be able to use the -b switch to bind the outbound connection to a specific interface address.  Try something like
```
telnet -b 10.0.0.3 ip.addr.of.destination 3306
```
and see if that works.  I've never used this so it's just a shot in the dark.  Replace 3306, the MySQL port number, with the appropriate port like 5432 for Postgres.

---

### Post by cariboo on 2016-06-14
You may get better help here for your server question.

---

### Post by AlmoG on 2016-06-14
> **SeijiSensei said:**
> 
If you generate the tests with telnet, you might be able to use the -b switch to bind the outbound connection to a specific interface address.  

Unfortunately I have very limited wiggle room with the tests I want to run, so telnet is not an option. (the tool is written in Java using JDBC to connect to the DB server).

I gotta say, I really was hoping for a simple OS tweak to do this. It sounded like a trivial thing to do at first, but I can't find anything about this anywhere. :confused:

---

### Post by SeijiSensei on 2016-06-14
Perhaps you can rewrite the Java scripts to use a particular outbound address?

---

### Post by AlmoG on 2016-06-15
I found [this post]("http://unix.stackexchange.com/questions/201704/multiple-ip-source-on-single-interface-in-linux") and I'm gonna try it out tomorrow.

I will update with the results.

---

### Post by AlmoG on 2016-06-19
> **AlmoG said:**
> I found [this post]("http://unix.stackexchange.com/questions/201704/multiple-ip-source-on-single-interface-in-linux") and I'm gonna try it out tomorrow.

I will update with the results.

I found a solution that fits my needs using iptables and SNAT/DNAT rules:
for each alias I have I have designated a "false" IP address, and I run my client using that address:
./load-client --server=10.0.0.10
./load-client --server=10.0.0.11
./load-client --server=10.0.0.12
...etc

Next I am marking the packets sent to that address
iptables -t nat -A OUTPUT --dest 10.0.0.10 -j MARK --set-mark 10
iptables -t nat -A OUTPUT --dest 10.0.0.11 -j MARK --set-mark 11
iptables -t nat -A OUTPUT --dest 10.0.0.12 -j MARK --set-mark 12
...etc

Then I use that mark to edit the packets' source IP
iptables -t nat -A POSTROUTING -m mark --mark 10 -j SNAT --to-source <source ip of eth0:0>
iptables -t nat -A POSTROUTING -m mark --mark 11 -j SNAT --to-source <source ip of eth0:1>
iptables -t nat -A POSTROUTING -m mark --mark 12 -j SNAT --to-source <source ip of eth0:2>
...etc

Finally I change all the destination IPs of the "false" packets to the correct IP:
iptables -t nat -A OUTPUT --dest 10.0.0.10 -j DNAT --to-dest <real-server-ip>
iptables -t nat -A OUTPUT --dest 10.0.0.11 -j DNAT --to-dest <real-server-ip>
iptables -t nat -A OUTPUT --dest 10.0.0.12 -j DNAT --to-dest <real-server-ip>
...etc

So the end result is that I have several "fake" IPs that I can use and each one has it's own "spoofed" source IP and reaches the same destination.
I ran a sniffer on the destination server and saw that all my packets arrive from the spoofed IP.

Cheers.

---

