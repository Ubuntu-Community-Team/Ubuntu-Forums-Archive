---
title: "Fortiguard blocking expressvpn"
date: 2020-08-24
forum: Security
---

### Post by thomas46 on 2020-08-24
Hi, all.
I am running Ubuntu 20.04 and the network I am connected to now is using Fortiguard from Fortinet which blocks my Expressvpn. I have been in contact with Expressvpn which have not been able to solve the block.
Expressvpn is installed and I also have the extension in Firefox. I have never had any problem with this system. 

Any suggestions for a workaround?

---

### Post by TheFu on 2020-08-24
May want to research a little deeper about who actually owns Expressvpn.  
[https://vpnscam.com/expressvpn-really-based-in-hong-kong/](https://vpnscam.com/expressvpn-really-based-in-hong-kong/)

I would expect Fortiguard to block all outbound UDP.
It isn't like Fortiguard is use by home users, so you should probably talk to your IT and network security guys about this. Wouldn't want you to be fired.

---

### Post by thomas46 on 2020-08-24
No risk of getting fired. It is a hotel!
Do you have a recommendation for another client that does not get blocked? TCP are also blocked

---

### Post by TheFu on 2020-08-24
Hotels have to allow 443/tcp, so try that.  I run my VPN on multiple ports, including 443/tcp for this sort of issue.

However, enterprise firewalls should be able to tell the difference between HTTPS and VPN SSL traffic, so it may not work. I don't know how smart Fortiguard is. I can say that Bluecoat is NOT impressed when I try to do that, but very few organizations will spend on bluecoat protection. I've been in hotels around the world and never had issues connecting back home with 443/tcp.  Be certain the all DNS queries go through the VPN too, without leaks.  That means the initial connect to the VPN has to use an IP, not DNS.

I wouldn't trust any VPN trying to use the web browser as a platform.  Browsers leak so much data already. Don't want to give them another chance.

What country are you in currently?

I've had some of my websites blocked by the country I was in, but the IP always worked. Odd thing was, other websites hosted on the exact same machine using the same IP were allowed.  Sure, you expect that in China and Thailand, but I didn't expect that in Turkey or India or some other "free" countries.

---

### Post by thomas46 on 2020-08-25
Thanks for the tips!
How do I set up 443/tcp on EVPN? There is no option for that either in the terminal or in my account at EVPN.
The vpn is installed through the terminal. The browser extension is only for controlling it since the program does not have a GUI.
I am 100% sure that the VPN is blocked by the hotel. Everything works perfect on all other networks.

---

### Post by TheFu on 2020-08-25
> **thomas46 said:**
> Thanks for the tips!
How do I set up 443/tcp on EVPN? There is no option for that either in the terminal or in my account at EVPN.
The vpn is installed through the terminal. The browser extension is only for controlling it since the program does not have a GUI.
I am 100% sure that the VPN is blocked by the hotel. Everything works perfect on all other networks.

You don't have any control over the ports. That's on the VPN server side.

---

### Post by thomas46 on 2020-08-25
Thanks!
I will try to contact the supplier of the VPN.
If all fails, any recommendation for another supplier of VPN?

---

### Post by TheFu on 2020-08-26
> **thomas46 said:**
> Thanks!
I will try to contact the supplier of the VPN.
If all fails, any recommendation for another supplier of VPN?

[LIST]
[*]One that isn't owned by an hidden corporation. Can you trace the owners without a forensics accounting degree?
[*]One that has been proven, in court, to be telling the truth about their log policy.
[*]One that posts clear ovpn configs for each of their exit nodes.
[*]One that supports udp and tcp connections on multiple ports, especially 443.
[*]One that provides a way to have all DNS traffic inside the tunnel too. This is hard for many VPNs.
[*]One that has plenty of exit nodes around the world, but none inside anti-privacy regimes.
[*]One that charges enough to remain in business, but not so much as to be a rip off.
[*]One that provides sufficient bandwidth for your needs.
[*]One that doesn't have $20 "lifetime" accounts, unsustainable.
[*]One that doesn't claim PPTP to be a viable VPN.
[*]One that supports 4K keys and AES256. Claims that they use some new encryption method are companies to be avoided.
[/LIST]
Those should be enough to filter out the bad providers.

Or just run your own.

---

### Post by thomas46 on 2020-08-28
Thanks!
Based on what you said and some research I downloaded and installed Mullvad. And it works beautifully!
One caveat: after uninstalling Mullvad some of the network settings have been adjusted so internet will not work. I managed to find out that it could be related to DNS settings. By running in terminal:
  	 	 	 	   x@x:~$ sudo rm /etc/resolv.conf

  x@x:~$ sudo ln -s /var/run/systemd/resolve/resolv.conf /etc/resolv.conf

  x@x:~$ sudo systemctl restart systemd-resolved.service
everything got corrected and the internet connection works again. NB! Replace x@x with your computer name in terminal

---

