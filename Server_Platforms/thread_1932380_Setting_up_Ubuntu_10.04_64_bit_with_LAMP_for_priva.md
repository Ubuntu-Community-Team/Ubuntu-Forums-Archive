---
title: "Setting up Ubuntu 10.04 64 bit with LAMP for private network (no internet connection)"
date: 2012-02-27
forum: Server Platforms
---

### Post by thesufi on 2012-02-27
Hello, I am totally new in Ubuntu. I need to install Ubuntu 10.04 64bit with LAMP to run a custom PHP script in my local server. I already have a local network with 70 computers there. I have bought a intel core i5 computer for this.
I will not have any domain, only IP. IP will be 192.168.x.x
I will be grateful if someone guide me how to do that. Lots of step-by-step instructions are available in internet. I am confused which one to follow.
Some help will be appreciable.

Please keep in mind that I will not have any internet connection in the server, but I can use internet during server setup (Ubuntu and LAMP setup), if necessary.

Thanks.

---

### Post by mörgæs on 2012-02-27
Hi, welcome to the fora.

Setting up LAMP is done with the commands

```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

while connected to the internet.

---

### Post by thesufi on 2012-02-27
> **mörgæs said:**
> Hi, welcome to the fora.

Setting up LAMP is done with the commands

```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```while connected to the internet.

Thanks. So after this, I just need to install Apache, MySQL, PHP etc? A little detailed will be more helpful for me.
I need around 800GB space to host my files. My goal is to browse this files (php scripts as well) from the network using the server IP (local). I have  one 1TB SATA drive. How should I distribute the partition? 50GB for the Ubuntu and other softwares, and rest of the space for files?
I never installed Linux before. When I install windows, I need to setup motherboard chipset. Should I do this also for linux and how can I do this? I have intel DH 67 mainboard.

---

### Post by sidzen on 2012-02-27
I do not think you will need 50Gb for Ubuntu -- about half that should do it unless *beau coup* software.

---

### Post by spynappels on 2012-02-27
Your safest bet is to burn a CD from an ISO downloaded from the Ubuntu website.

This will ask you about partitioning the hard disk, you can just select "Guided, use entire disk" and at the Software install phase, just select LAMP server and SSH server.

You should set the IP during the install phase as well and where it asks for your gateway, just use any IP address in your chosen subnet.

Upload your HTML/PHP pages to /var/www, restart Apache2 and away you go.

---

### Post by thesufi on 2012-02-27
I have tried with the CD. But it can not detect the network device during the installation. How can I proceed?

---

### Post by spynappels on 2012-02-27
Is the server at least connected to your internal network? If it is, you can just manually put the IP address, netmask and gateway in, although the gateway will be more of a dummy entry as this will not be on a Net connected network. You may need to put some DNS IPs in too, just use 8.8.8.8 and 8.8.4.4.

---

### Post by thesufi on 2012-02-27
What I have found so far is, I am unable to install Ubuntu 10.04 LTS 64 bit on an intel PC. I need to use the x86 for intel. Am I right?

---

### Post by thesufi on 2012-02-27
No network interfaces detected! this is the error I am facing during the installation, and I am unable to fix it. Any solution please?

---

### Post by HugoSerrano on 2012-02-27
You can install Ubuntu 64bits on a Intel CPU, as long it supports 64bits systems.

The problem with your NIC (Network Interface Controller)... can you tell us the model? Can you run a Ubuntu Desktop Live CD and see if it can "see" the NIC?

Did you installed the system? And "only" lacks the interface? 
Can you type ```
ifconfig -a 
```

Best Regards!

---

### Post by mörgæs on 2012-02-27
> **thesufi said:**
> Thanks. So after this, I just need to install Apache, MySQL, PHP etc? A little detailed will be more helpful for me.

The commands given install the whole LAMP stack. You don't need any more commands.

---

### Post by thesufi on 2012-02-29
Instead of installing of server, I have installed desktop version of Ubuntu 10.04
But I can not connect it to internet. I am using intel DH67BL mainboard. It is not getting the network device. How can I install the LAN card? Or connect to internet?

---

### Post by mörgæs on 2012-02-29
How does it work in Buntu 11.10 or 12.04 beta?

---

