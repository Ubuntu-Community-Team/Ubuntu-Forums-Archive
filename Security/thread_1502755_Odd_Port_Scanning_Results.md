---
title: "Odd Port Scanning Results"
date: 2010-06-06
forum: Security
---

### Post by Aiello on 2010-06-06
I was testing the security of my Ubuntu 10.04 64bit install by running a port scan from [https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2) and I came upon some odd results. It appears that basically all my ports are closed, but only Port 646 is dropping packets silently. Furthermore, Port 80 is open.

Should I be concerned about this? Is there anyway to silence these other ports? 

Thanks!

---

### Post by an0dos on 2010-06-06
I am not an IT professional and I am not a Linux guru. The following information is based on things I have read on this forum and in the Security sticky.
[I]
Should I be concerned about this?

[/I]It depends on what you are doing with your computer and how your network is setup. If your computer is behind a router, then probably not because the scan is only detecting how the firewall on your router is configured (unless you placed your computer in a DMZ). That being said port 80 on your router shouldn't be accessible from the internet and you may want to reconfigure it.

Is your computer behind a router? If so, then the port scan from grc is only scanning your router. You can check what processes are listening on ports by running the following command from the terminal:

```
sudo netstat -tulnp
```If you post the output here, people can review it and see if there's anything you should be concerned about.

If you want to run a port scan on your computer may want to install a program called nmap on a second computer behind your router and run the following command:
```
sudo nmap -PN -sT -p- -v <ip address>
```You will insert the IP address of the computer you want to scan where I wrote "<ip address>".
This will run a scan of all TCP  ports on the computer. It may take a while. You can do just about any scan you can imagine with nmap. Very useful tool. Read the man pages.

You can find the IP address of your computer by running
```
ifconfig
```In a typical home network your IP address will be 192.168.1.x where "x" will be a number between 2 and 254.

You may want to consider enabling the Ubuntu firewall by running the following command
```
sudo ufw enable
```If you are really concerned about these issues, read the stickies at the top of the Security Forum. There is a lot of good detailed information.

---

### Post by FuturePilot on 2010-06-06
If you're not hosting a web server and port 80 is open, this usually has to do with the web interface of your router being open to the internet. This is bad. Check your router and make sure you don't have it accessible to the whole world.

---

### Post by bodhi.zazen on 2010-06-06
> **Aiello said:**
> I was testing the security of my Ubuntu 10.04 64bit install by running a port scan from [https://www.grc.com/x/ne.dll?rh1dkyd2](https://www.grc.com/x/ne.dll?rh1dkyd2) and I came upon some odd results. It appears that basically all my ports are closed, but only Port 646 is dropping packets silently. Furthermore, Port 80 is open.

Should I be concerned about this? Is there anyway to silence these other ports? 

Thanks!

If you have a router you are scanning your router and not your Ubuntu computer.

To scan or check for open ports on your computer use nmap (zenmap = graphical front end), losf, or netstat (all from your LAN.

nmap -v -A ip_address

netstat -ntulp

lsof -i -n -P 

These tools all have several options, so if you are interested read up on them.

---

### Post by Aiello on 2010-06-06
Thanks for all the responses! I took your advice and started playing around in my router's firmware. It turns out that DMZ was enabled. After disabling that, port scans are now reporting that all packets to all ports were dropped silently! Thanks again!

---

### Post by an0dos on 2010-06-06
In a typical home network scenario you shouldn't ever need to put a computer in a DMZ.

---

