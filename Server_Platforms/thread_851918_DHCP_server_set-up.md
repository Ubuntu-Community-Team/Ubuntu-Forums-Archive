---
title: "DHCP server set-up"
date: 2008-07-07
forum: Server Platforms
---

### Post by Malfet on 2008-07-07
I'm trying to setup DHCP server in a way to split one local network to the several subnets, i.e. 192.168.1.0-255, 192.168.2.0-255, 192.168.3.0-255 etc. So far, I do not have a good experience with Linux systems I'm using "webmin" and right now have a follows configuration

dhcpd.conf
```

shared-network 192.168.0.0 {
	# 192.168.3.0
	subnet 192.168.3.0 netmask 255.255.255.0 {
		range 192.168.3.1 192.168.3.15;
		# 115
		group {
			# Class-01
			host Class-01 {
				hardware ethernet 00:17:31:C7:4B:17;
				}
			# Class-02
			host Class-02 {
				hardware ethernet 00:17:31:51:9A:59;
				}
			}
		}
	# 192.168.6.0
	subnet 192.168.6.0 netmask 255.255.255.0 {
		range 192.168.6.1 192.168.6.25;
		# administration
		group {
			# ninam
			host ninam {
				hardware ethernet 00:17:31:51:98:AB;
				}
			}
		}
	}

```

Later I would like to add more hardware ethernet adresses and few other subnets, but DHCP server in this configuration is not starting.  I'll really appreciate any help. dhcp3-server states ```
INTERFACES=eth1
```.

M.

---

### Post by pdwerryhouse on 2008-07-07
It might be best if you post some of the logs you get when you try to start it...  output from /var/log/daemon.log would probably be handy.

---

### Post by Malfet on 2008-07-08
> **pdwerryhouse said:**
> It might be best if you post some of the logs you get when you try to start it...  output from /var/log/daemon.log would probably be handy.

Thanks for the reply, I solved it, but did not succeed with main task. 
I would like to split one network to several subnets in a way, that a computer with specific ethernet address will always get an IP from a specific range, For example computer with 00:17:31:C7:4B:17 will always get IP in range from 192.168.3.1 to 192.168.3.15, while 00:17:31:51:98:AB will always get an IP in range from 192.168.6.1 to 192.168.6.25.
Code I've posted above did not gave any result (computers did not obtain IP address). I've changed it like this 

```

shared-network 192.168.0.0 {
	# }
	subnet 192.168.0.0 netmask 255.255.240.0 {
		range 192.168.3.1 192.168.3.15;
		# 115
		group {
			# Class-01
			host Class-01 {
				hardware ethernet 00:17:31:C7:4B:17;
				}
			# Class-02
			host Class-02 {
				hardware ethernet 00:17:31:51:9A:59;
				}
			}
		range 192.168.6.1 192.168.6.50;
		}
	}

```

This way it works, but DHCP distribute IPs randomly. Please, how to set-up the server in a way that 00:17:31:C7:4B:17 will always get IPs from third subnet and never from forth, sixth or whatever else (with dynamic IPc, without static IP addresses)?

Thanks in advance,
M.

---

### Post by Malfet on 2008-07-13
No one?

---

### Post by enrique.lopez on 2008-07-14
I've 2 NICs 1 for external (internet-eth0 192.168.1.2 gateway 192.168.1.1) and 2 (internal LAN eth1 192.168.80.1) i want run DHCP in eth1 but no possible y choose DHCP server in MCC mythbuntu but the client no boot in PXE mode. Any solutions?
Thanks

---

### Post by koenn on 2008-07-14
> **Malfet said:**
> No one?

Look at the examples here : [http://www.openfree.org/forums/showthread.php?t=524](http://www.openfree.org/forums/showthread.php?t=524)

you probably should use an IP address as name for the shared-network
In your 2nd attempt, your netmask is probably too wide so it works as 1 subnet, not 3 (or 5 or 6) subnets.
I'd say your first attempt is pretty close. 
You do know that you need multiple NIC's or aliases so that the server has an IP address in each subnet it serves addresses for, don't you ?

---

