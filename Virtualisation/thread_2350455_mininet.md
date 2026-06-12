---
title: "mininet"
date: 2017-01-24
forum: Virtualisation
---

### Post by dzonii on 2017-01-24
Hello to all.im using Oracle VM VirtualBox to start Mininet(Ubuntu-64).when i try you create custom topology in MiniEdit im getting a porblem when i try to ping one of pc to another from root terminal it display message"ping command not found",what could be problem ?? Im gonna appreciate any kind of  help.

---

### Post by ODTech on 2017-01-24
> **dzonii said:**
> Hello to all.im using Oracle VM VirtualBox to start Mininet(Ubuntu-64).when i try you create custom topology in MiniEdit im getting a porblem when i try to ping one of pc to another from root terminal it display message"ping command not found",what could be problem ?? Im gonna appreciate any kind of  help.

The ping command must be the first command. The way you typed it linux will assume your are looking for a h1 command which it obviously won't find.

---

### Post by dzonii on 2017-01-25
Thank you so much for reply,i write as you say,but still no result.There was a guy on one website,and according to him it should be "h1 ping h2".I have no idea how to resolve this

---

### Post by ads3 on 2017-01-29
From what I'm seeing, it appears that you're trying to use the ping command to ping the hostnames of these machines. If you don't have a properly-configured DNS server, that won't work because your host has no way to look up what the address of "h1" or "h2" is. 

I don't know how much you know about networking, so I'll start from the beginning - please excuse me if I mention things you already know. 

In a network, each device's interface needs an address. The most common of these addresses is an Internet Protocol, or IP address. IPv4 addresses (the most common kind currently) are expressed as four octets of 8-bit numbers written in decimal (between 0 and 255). For instance, the address of Google's public DNS servers are 8.8.8.8 and 8.8.4.4. Computers uses these addresses to identify each other on a network, and routers use them to decide who data should be sent to and how that data should get to its destination. More information on how this works is available on [https://en.wikipedia.org/wiki/IPv4](https://en.wikipedia.org/wiki/IPv4)

Domain names are meaningless to computers. Your machine has absolutely no idea what "ubuntuforums.org" means, but it DOES understand the address of 91.189.94.16 (which is the ubuntuforums.org ip. I checked using the nslookup command). There must be a service that translates this domain name into the IP address that the computer understands. that's what a DNS, or Domain Name Service, server does. More info on this is available on [https://en.wikipedia.org/wiki/Domain_Name_System](https://en.wikipedia.org/wiki/Domain_Name_System)

When I look at these screenshots and I see you typing, "ping h1," I see that as you're on one of these hosts, and you're giving the ping command a hostname. As such, the computer will take that hostname, and try to ask a DNS server what the corresponding IP address is. If there isn't a DNS server, ping (or any other network service) will fail with, "I don't know who that host is - **unknown host." **So the takewaway is, **you need to use the IP address of the host you want to ping.** A real world example of this would be, try typing "ping 8.8.8.8" into a terminal. Your computer will start to ping the host whose address is 8.8.8.8, which, as previously mentioned, is Google's public DNS server. Alternatively, try running, "ping google.com." You'll see ping resolve that domain name into an address, and start pinging it. 

Now, I'm not very familiar with the program you're using, so I can't tell you how to assign IP addresses to your hosts - which you will need to do manually if you don't have a DHCP server.

---

### Post by dzonii on 2017-02-01
Thank you so much for your reply,it was problem with IP,cause i put same IP address on both host...Btw im using mininet,and Python script MiniEdit,when you can configuring SDN

---

### Post by hidayah98 on 2018-01-18
How to install mininet in ubuntu 32 bit im using virtualbox?

---

