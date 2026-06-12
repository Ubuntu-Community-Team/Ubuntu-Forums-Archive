---
title: "How would you respond to a malicious device on your network?"
date: 2013-06-13
forum: Security
---

### Post by wlraider70 on 2013-06-13
Today I found a device I didn't recognize on my network. Turned out it was ok, but now I'd like to know what you would do. 
Specifically what would you do if it was malicious. 

I used nmap and did some intensive scanning. I tried connecting to it via open ports. 
I guess I would have ultimately banned the mac and changed some passwords, but I wasn't too panicked.

Can I use wireshark to monitor the traffic to the box?

---

### Post by bab1 on 2013-06-13
> **wlraider70 said:**
> Today I found a device I didn't recognize on my network. Turned out it was ok, but now I'd like to know what you would do. 
Specifically what would you do if it was malicious.

It depends on what you mean by "my network".  Is this your home network, or *your* businesses network, or the network where you work.  If this network is a a business network, do you have a posted policy regarding rogue devices?  In short, there is no pat answer.

On my home network there are no available IP addresses for a rouge device to use so that is the end of that story.  At work we have a posted policy forbidding  unregistered devices.  If the user persists in introducing these to the network they will be fired.  We monitor the network flow all the time (not me) and regularly remove devices and warn users.  Most of the time on a LAN these devices (personal NAS devices or user owned laptops) are inadvertent and only sometimes cause real problems.
> 
I used nmap and did some intensive scanning. I tried connecting to it via open ports. 
I guess I would have ultimately banned the mac and changed some passwords, but I wasn't too panicked.

Can I use wireshark to monitor the traffic to the box?
How did you find this rogue device?  You should monitor the entire network.  You can set up a host the runs wireshark and attach it to a managed switch that would aggregate all the other ports on that switch that are going to the router.  Or you can install wireshark on a host that has 2 NIC's and forwards all network traffic through this host.  Wireshark would then monitor one of its NIC's.

---

### Post by Hungry Man on 2013-06-13
Really depends. If it's behind my router I'd make note of any information on the device, like MAC, and shut the router off from the internet and reconfigure the password, ensure all of the settings are the same, and potentially wipe it and start fresh.

From there maybe I'd confirm my system settings, making sure the Firewall hasn't been changed, that my ports aren't changed, etc. But I wouldn't worry too much about it, I'd just assume some kid got onto my wifi somehow. I'd just make sure to check the router and its logs for a few weeks to make sure it didn't happen again.

---

