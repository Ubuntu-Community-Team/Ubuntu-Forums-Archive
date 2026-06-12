---
title: "Feelin Like A N00b, no web server access"
date: 2010-12-21
forum: Server Platforms
---

### Post by dankap99 on 2010-12-21
I have an Ubuntu server up and running, got all my html, css etc files in my /var/www, got external ip, opened up ports 21, 22, and 80 on my router, removed the firewall from the machine on the router, no firewall on the box itself. Got my lamp action on, openSSH, the whole shabang. When i go to the local ip (192.168.1.x) i can get to everything no problem. But when i try the external ip all i get is timeout error.

Is is a problem that i'm running the server in a virtual machine (vmware fusion, network bridged), or am i missing something? any help is greatly apprecitaed.

(I'll make the external IP available if requested)

---

### Post by spynappels on 2010-12-21
Is port 80 blocked by your ISP?

---

### Post by dankap99 on 2010-12-21
i'm not sure. but would they also be blocking 22? i cant event ssh into it. i have att btw

---

### Post by J_5 on 2010-12-21
Did you port forwarded the ports that you opened up to point to your internal IP?

---

### Post by msandoy on 2010-12-21
Make sure you have the VM use bridged adapter, not NAT. Set it up with fixed IP, not DHCP. Direct port forwaring in your router to the fixed IP of your VM. This should work, unless your ISP is blocking you.

It might clear things up, if you do an nmap on both your internal IP and on your external IP, and post the output.

---

### Post by windependence on 2010-12-21
You will not be able to reach your site from the inside with the external IP unless your router supports NAT reflection (and most don't). You need to edit your hosts file (on the client machine, NOT your server) and add an entry for your external DNS name, for example:
 
```
 
xxx.xxx.xxx yourdomain.com

``` 
-Tim

---

### Post by dankap99 on 2010-12-21
J_5, i have this "machine" totally open on my router, all applications allowed, all ports open, no firewall.

Msandoy, my internal nmap shows 22 and 80 open, but the external nmap shows all 1000 scanned as filtered.

and windependence, i've had a couple friends try to get to it, and i've tried from my phone over 3g as well.

the external ip is 99.188.51.212 if that'll be at all helpful

---

### Post by msandoy on 2010-12-21
This might be a stupid question, but have you tried rebooting your router after doing changes?

You could try to set DMZ in your router to your internal VM IP, just for testing. It is not recommended to run like that.

Btw, nmap is telling you that all ports are leading nowhere at the moment. I'm guessing the configurations have not been activated.

---

### Post by dankap99 on 2010-12-21
just set it to dmz, rebooted the server, and i can get to it over 3g.

could someone else please verify that they can get to it too?

---

### Post by msandoy on 2010-12-21
If you do another nmap on your external IP, it should tell you port 22 and 80 are open, if it worked.
Btw, I'm on my work computer at the moment, will be on my own computer later, and I can test it then.

---

### Post by dankap99 on 2010-12-21
did that right before i saw ur reply, got 22 and 80 open

---

### Post by dankap99 on 2010-12-21
so it works for about a minute, then i cant connect to it any way i try. i re-set it to dmz, then reboot the server, then i'm good for another 2 mins or so. wha...?

---

### Post by msandoy on 2010-12-21
Try rebooting the router after setting the DMZ. Your router might need a reboot to accept new settings.

---

### Post by dankap99 on 2010-12-22
so i spent a few hours last night working on this, and i dont think it's my router.
after many reboots and settings re-sets and server reboots etc. i realized that all my VMs are dropping internet connection pretty quickly inside vmware. i'm thinking of building a real machine as a testbed anyways, so maybe i'll just try this all over again on a real box. you guys have been super helpful thanks so much! :D

---

### Post by CharlesA on 2010-12-22
Good luck. I haven't had any problems with using a VM as a test server, but everyone's environment is different.

---

### Post by dankap99 on 2010-12-22
do you use vmware or virtual box? alot of my friends use virtual box, i've just never had a reason to make the change.

---

### Post by CharlesA on 2010-12-22
I've been running VirtualBox, as that's what I am most familiar with. I have most of my VMs on one machine, and connect to them over the network.

There really shouldn't be much difference between VMware and Virtualbox, as long as you have your VMs set to use bridged networking.

---

### Post by msandoy on 2010-12-22
I have a few VM's running in Virtualbox, and I have never had this problem with dropping of network. 
Please post back if you find the problem with VMware.

---

### Post by windependence on 2010-12-22
> **dankap99 said:**
> do you use vmware or virtual box? alot of my friends use virtual box, i've just never had a reason to make the change.
I have several production servers running on VMware and I have never had this problem in 4 years . Do check your NIC settings though in VMware and make sure they are live. Right now I'm also at work but later I may be able to get into my VMs and tell you what to check. Also check port acces using canyouseeme.org.
 
-Tim

---

