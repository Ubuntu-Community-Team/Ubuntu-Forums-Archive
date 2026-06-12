---
title: "Putty Connection Refused over the internet"
date: 2018-08-16
forum: Server Platforms
---

### Post by brasileiro3 on 2018-08-16
Putty Connection Refused but **I can access everything either through putty over LAN, but not over the internet.**


Let me [explain with more details]("https://ubuntuforums.org/showthread.php?t=1201321&highlight=putty+connection+refused"): my Windows 10 host or any laptop on my local network can easily login through ssh on my Ubuntu Server Virtualbox. 
Just using putty, the local ip (192.whatever) and login OK! 
However any computer from outside (like when I am at Starbucks wifi or my work location) the message from Putty is "connection is refused". I even saw something like "actively refusing connections on port 22".


Router's port forwarding is active for ports 80 and 22. I can see my website from anywhere (both lan and external networks).
My host machine (W10) has port forwarding enabled as well on Virtualbox setting (network/NAT/port forwarding) for my vm (Ubuntu server).

One last bit: I am using this machine as my personal webserver. So my website is displayed just fine(inside lan and outside) and the same process I used for port 80 I repeated for port 22.


Question: what role does Windows Firewall play here? Is there any need to enable port 22 on windows firewall directly? Does Virtualbox handle it directly? I never touched Windows firewall.


Question 2: Let's suppose W10 port is closed. Why can I access the server from computers over my internal network? Are these connections not passing through the machine firewall? Are they whitelisted somehow?

---

### Post by darkod on 2018-08-16
This is why I never use Vbox in NAT mode. It brings in another layer of uncertainty for any troubleshooting.

If it's not impossible for you, change the VM network type to Bridge on the host ethernet interface. That way the VM will be like plugged in directly to your LAN and you can use any free static IP from the LAN directly on the VM. The port forwarding you do on the router should work directly and only the VM firewall (iptables) could be blocking traffic (if used). In such setup you don't need to worry about your Win10 host firewall any more.

---

### Post by LHammonds on 2018-08-16
As darkod suggested, you really should setup your VBox adapter to be Bridged instead of NAT and assign it its own static IP on your LAN.

You need to enable port 22 on your Ubuntu firewall but since it is already working, it is likely you don't have the firewall enabled or is already configured to allow port 22.

However, your Windows firewall is a bit different.  By default, Windows firewall does NOT block any traffic from other machines on your same subnet!  So traffic coming from another subnet (like the Internet) would get stopped by the Windows firewall.  Make sure to add a rule for it.  Here is a command you can run that will do this if you are not familiar with the GUI:

```
netsh advfirewall firewall add rule name="SSH 22 TCP" dir=in action=allow localport=22 remoteport=any protocol=tcp remoteip=any profile=domain
```

The next thing you do is port-forwarding of an external port and map it to your Ubuntu's IP and internal port.  However, I strongly suggest you use a non-standard port number you pick out of thin air such as 12345.  On your router, have any traffic on port 12345 route to your Ubuntu server IP on port 22.

I would never open my SSH port to the Internet but if you have to, make sure you lock it down.  Configure sshd to only allow your specific ID to login.  I would also install Fail2Ban so that any brute-force attempts on that port will raise the firewall to block that incoming IP for a specific amount of time and log the results so you know if someone is trying to hack you.

Another measure of security would be to configure SSH keys so you are not typing any IDs or passwords to access the system which is far more secure.

Just some food for thought.
LHammonds

---

