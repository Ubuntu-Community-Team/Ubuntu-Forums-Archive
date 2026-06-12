---
title: "cli to list ip addresses"
date: 2008-09-15
forum: Server Platforms
---

### Post by bbarrons on 2008-09-15
Here is my situation. I monitor my zimbra server at the school from here at home. The school systems uses a windows 2003 server for dhcp and dns. I ssh into my zimbra server to test connections and do updates and so on.
 When a user is having problems with their computers I check to make sure accounts are logged and if they arent I would like to ping their box. Is there a way to retrieve all the ip  addresses in use from a cli? I could do a remote connection to the windows server but I do have a terminal window open most of the time and sometimes just need to verify connectivity... any thoughts?
thanks
Bill B

---

### Post by caljohnsmith on 2008-09-15
You could do an ARP/ping scan on the LAN:
```
sudo apt-get install nmap
sudo nmap -PR -sP 192.168.1.0/24
```
And replace the 192.168.1.0 with whatever your LAN subnet is. The /24 notation makes it so nmap scans from 192.168.1.0 - 192.168.1.254, or all the subnet addresses. Let me know if that is what you are looking for, or if you are thinking of something different.

---

### Post by bbarrons on 2008-09-15
thank you. it was just that simple. exactly what I was looking for.

---

### Post by bbarrons on 2008-09-15
that gave me mac address as well as ip and computer name. perfect for what I was wanting to do.

---

