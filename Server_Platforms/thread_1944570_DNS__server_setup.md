---
title: "DNS  server setup"
date: 2012-03-21
forum: Server Platforms
---

### Post by crashdogy on 2012-03-21
OK got my DHCP server up and running would like to add a DNS server to it can some point me to a good tutorial for mixing the to ?:guitar:

---

### Post by CharlesA on 2012-03-22
DNSMasq would work fine but there is also Bind9.

[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

---

### Post by d4m1r on 2012-03-23
Bind9 comes preinstalled with Ubuntu server so I'd recommend that as a starting point. Google "bind9 setup" and I am sure you'll get lots of guides.

---

### Post by crashdogy on 2012-03-23
Thanks for all the responses is there a way to back up the system fully before I do this ?

---

### Post by CharlesA on 2012-03-23
> **crashdogy said:**
> Thanks for all the responses is there a way to back up the system fully before I do this ?
You shouldn't have to because you can always remove those services.

If you do want to back it up, you might want to consider clonezilla to clone the drive, or just using tar to backup the entire file system.

---

### Post by TommyKlien on 2012-03-25
I just got done doing the same thing. I followed the steps from [http://mixeduperic.com/ubuntu/seven-easy-steps-to-setting-up-an-interal-dns-server-on-ubuntu.html](http://mixeduperic.com/ubuntu/seven-easy-steps-to-setting-up-an-interal-dns-server-on-ubuntu.html) and things went pretty smooth.

I think the hardest thing to work through for me was setting up  pxe boot settings in dhcp. I was trying to setup thin station on my network.

Anyways hope you got through the issues.

---

### Post by collisionystm on 2012-03-25
Just install bind9. 
sudo apt-get install bind9

The config files are in /etc/bind

First thing to do is edit named.conf.options

setup the forward to go to google dns 8.8.8.8 or your isp dns.

after editing the file

sudo service bind9 restart

edit /etc/resolv.conf

change nameserver to

nameserver 127.0.0.1

get rid of other nameserver entries.

try to ping google.com

adding hosts is pretty easy, however the quickest way is to just use webmin to add your hosts.

---

### Post by collisionystm on 2012-03-25
Another cool thing about bind9 is you can use a tool such as this

[http://pgl.yoyo.org/as/hosts2bind.php](http://pgl.yoyo.org/as/hosts2bind.php)

You can grab a hosts file of known ad-servers and put them in bind to have them blocked.

Host file here. [http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

---

### Post by crashdogy on 2012-03-25
I'm geting confused when it asks for hostname domain name.  I don't know what it wants the IP or the name of the server.  I have 2 nic card in my setup its dhcp gatway firewall I did set the cachaing  part of the DNS but no zone stuff ?:confused:  

I need a index of what they are asking for  ? 


I followed this 

 [https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3](https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3)

---

### Post by darkod on 2012-03-25
I recently had a problem that dnsmasq didn't work and realised it was up to the firewall. Make sure you open port 53 in your firewall for both protocols. It actually uses udp more than tcp. My error was that I allowed tcp only. Once udp was allowed dnsmasq worked right away, the instructions for it are pretty easy.

If you want to use your ubuntu router/firewall as DNS for local machines, make sure the firewall is letting port 53 through. If we are talking only about DNS forwarding you don't need to worry about any zones or touch anything about it. You only need to work with zones if you want your server to be main DNS for your own domain for example.

Pay more attention to the firewall settings.

---

### Post by crashdogy on 2012-03-25
I used bind9 and firewall is not the issue its knowing what the thes guilds are talking about I just got to setup the zones now I'm just plugin along any one know how to Change port 53 or how to lockit down abit ?

---

