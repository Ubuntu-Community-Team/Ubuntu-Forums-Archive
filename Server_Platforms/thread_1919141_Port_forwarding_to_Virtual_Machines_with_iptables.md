---
title: "Port forwarding to Virtual Machines with iptables"
date: 2012-02-02
forum: Server Platforms
---

### Post by Moose67 on 2012-02-02
I currently have an Ubuntu server running vmware server software with 6 virtual machines running online demos for our company software. I Have a Netgear DSL Modem/Router with the ports forwarded to the individual VM's depending on the inbound port address request. My router is set to forward the HTML & VNC port request to the corresponding VM. This has worked great for over a year now. I frequently now have to reset my router to get the port forwarding to work again for some unknown reason.

My problem is I want to add more VM's for demos but I've run out of port forwarding entries on my Netgear Router/Modem. I have to forward 2 ports per VM. One html and one VNC. I want to use iptables on the server so I can forward all the ports in the range to the server then have the server forward the ports to the correct VM. I've setup iptables and see that the settings are correct and I believe I am from everything I've read over the internet. My problem is it's not forwarding. 

I don['t want to have to buy another DSL modem and router to do this if I already have the hardware available. 

Can anyone give me any suggestions to try? Thanx!

---

### Post by SeijiSensei on 2012-02-02
Is TCP forwarding enabled in /etc/sysctl.conf?  Read the comments in that file to see what needs to be set.

A quick check is to run the command "cat /proc/sys/net/ipv4/ip_forward".  If the result is zero, forwarding is denied.  You can turn it on temporarily by running 
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```
but to make the change permanent you need to edit sysctl.conf.

---

### Post by Moose67 on 2012-02-02
Here is the file.
root@live-demo:/proc/sys/net/ipv4# cat ip_forward
1

Am I missing something else? Do I need to restart the network again? I believe I did before.

---

### Post by Moose67 on 2012-02-02
Its is now working. Apparently I didn't restart the networking service. I don't reboot the machine because it takes too long to get all of the VM's back up and running properly. That's a problem for another day.

Thanks

---

