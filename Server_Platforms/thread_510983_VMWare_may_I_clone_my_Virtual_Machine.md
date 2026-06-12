---
title: "VMWare may I clone my Virtual Machine?"
date: 2007-07-27
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-07-27
With VMWare Server I installed and configured a fantastic virtual Ubuntu 6.06 server.:)
I was wondering how to clone/duplicate this virtual machine.
Is it correct to copy the VM files to a different directory and rename both the files on the host system and the VM on the virtual console or there is a smarter way?:confused:
I read that a VM has some sort of SID created for every VM but I didn't understand if I need to change it and how.
How do you clone your virtual machines?
Is it possible within the VMWare Server or I need VMWare Workstation?

---

### Post by k_grdn on 2007-07-28
Hi erasmo.da.rotterdam,

Just copying the contents of the vm folder to another directory works fine, when you open the image your prompted to create a new sid for the image.

Regards,

k_grdn

---

### Post by erasmo.da.rotterdam on 2007-07-30
Ok, I tried and the SID is generated
however the new virtual machine created doesn't function anymore

The procedure I followed was:
[LIST=1]
[*]stop the functioning virtual machine to clone
[*]cp -a /home/vm/first /home/vm/second
[*]on the virtual console change the name of the new generated vm to second
[*]start the second vm on the virtual console with consequent generation of the SID
[/LIST]

I supposed that with the first funcioning vm shutted down using the newly generated would have caused no problem. Instead it doesn't load correctly the network card and it isn't able to start Mysql. Do I have to specify in some configuration file something misterious?
Has anybody cloned a virtual machine without having to configure anything else?

---

### Post by HermanAB on 2007-07-30
It works for me.  Problems are probably due to setting a fixed IP address.

---

### Post by BatteryKing on 2007-08-29
When you first start up the cloned system and vmware asks for a new SSID (or something to the like), tell it to keep the the current SSID.  Having vmware create a new identifier seems to hose things like networking.

So far I have only tried this going between host machines, so I don't know how it would work on the same system.

---

### Post by HermanAB on 2007-08-30
Yes, you can copy the directory containing a virtual machine.

When you start it up the first time, let VMware asign a new ID to it.  Then go to the TCP/IP settings and change the IP Address and Hostname to something unique, so it doesn't clash with the previous machine.  That's all you need to do.

If you copy the machine to another host system then it should present few issues.  If you wish to have a second copy of the same machine on the same host machine, then it may be better to suspend the original while screwing with the IP settings of the new copy, then once it is running with a new set of network parameters, unsuspend the original and then you should have two identical machines running happily side by side.

Cheers,

Herman

---

### Post by ruibernardo on 2007-09-03
I came across this thread on Google because I had a problem with wmware-server and cloning a ubuntu 7.04 server.

I've copied it to another folder, created new SSID as usual, but the cloned server wouldn't get an IP and networking.

This happened because when the SSID was created, the /etc/iftab in the server still had the "old" MAC address of the network interface. The new MAC is inside the *.vmx file. Updated the /etc/iftab in the server, rebooted it and networking was up and running.

Hope this helps anyone that find the same problem.

---

### Post by Sgurd on 2008-02-01
> **epimeteo said:**
> I came across this thread on Google because I had a problem with wmware-server and cloning a ubuntu 7.04 server.

I've copied it to another folder, created new SSID as usual, but the cloned server wouldn't get an IP and networking.

This happened because when the SSID was created, the /etc/iftab in the server still had the "old" MAC address of the network interface. The new MAC is inside the *.vmx file. Updated the /etc/iftab in the server, rebooted it and networking was up and running.

Hope this helps anyone that find the same problem.

Created a 7.10 server, shutdown, copied folder.  Opened copied VM, wasn't prompted to create new SID (? - I've seen this before when using VMs downloaded from others).  Networking doesn't work, static or otherwise.

Found this post, but I don't have an /etc/iftab.

   ?

   - JD

---

### Post by gfowler on 2008-02-02
> **Sgurd said:**
> Created a 7.10 server, shutdown, copied folder.  Opened copied VM, wasn't prompted to create new SID (? - I've seen this before when using VMs downloaded from others).  Networking doesn't work, static or otherwise.

Found this post, but I don't have an /etc/iftab.

   ?

   - JD

Alas there is the rub JD, in Gutsy they changed the game.  You will need to go to /etc/udev/rules.d and find 70-persistent-net.rules.  Inside you will find a line with your NIC (eth0 or eth?) and in quotes you will find a MAC address.  My solution was to just comment out the line and reboot the server and it will re-populate the rule with the new MAC address and you will cooking on the front burner!

Jerry

---

