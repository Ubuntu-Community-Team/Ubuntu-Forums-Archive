---
title: "problem regarding dhcp configuration"
date: 2008-04-15
forum: Server Platforms
---

### Post by tusharhiwse on 2008-04-15
hi all,
i have a dhcp configured server. There are near about 65 clients configured with that server. IP's of that clients are binded with their mac addresses  in the dhcp server.  I have given the range for that configuration is 10.0.0.2 to 10.0.0.210.                                                    Now my problem is, if i connect another external  machine in that network , it automatically gets IP from that dhcp server. I have to make configuration such that no one external machine should get IP other than configured one.
  
note:- ip binded with their mac address in the server are not in serial. these are randomly binded with their mac addresses.

---

### Post by cdenley on 2008-04-15
I you want to assign IP's only to a predefined list of mac addresses, you can filter dhcp requests with iptables. You can also define static assignments in your dhcp configuration for all your computers, then omit the ip range. This would prevent dhcp assignments for anyone without a predefined static assignment.

If I understand correctly, you don't want someone hooking up their laptop to your network and getting a dhcp assignment. This isn't very effective for securing your network, since they can set a static ip address on their computer.

---

### Post by tusharhiwse on 2008-04-17
hi ,
thanks for suggestion.

but you tell me , how i have to filter the dhcp request with the help of iptables.
can you tell me the procedure for it ?

---

### Post by cdenley on 2008-04-17
I think this command would allow dhcp requests from a given mac address.
```

sudo iptables -A INPUT -p udp --dport 67:68 --sport 67:68 -m mac --mac-source XX:XX:XX:XX:XX:XX -j ACCEPT

```

This command would drop all remaining dhcp requests
```

sudo iptables -A INPUT -p udp --dport 67:68 --sport 67:68 -j DROP

```

There are tools that make it easier to work with iptables, but I'm not familair with how to use them, or if they can filter dhcp requests by host.
-firestarter
-guarddog
-webmin
-ufw
-firehol

---

### Post by peterquistgard on 2008-04-30
Hi guys. I'm looking for way to isolate my ip address from eth0 (my NIC) and assign an alias to it. I'm planning to use it in a proxy autoconfiguration script. I wrote this short script:

IP=`ip route show | grep src | awk '{print $NF}'`
sudo sed -i "/eth0Address/c\\$IP eth0Address" hosts

This script works fine . It updates the ip address for the alias "eth0Address".

Does anyone know how I can get this script to run every time i get a fresh ip address using DHCP??

Thanks in advance.

---

### Post by cdenley on 2008-04-30
I think you can create a script in /etc/dhcp3/dhclient-exit-hooks.d/ for this purpose. I never tried it.

---

