---
title: "Apache on ubuntu server in virtualbox on win 10 can't access server"
date: 2016-07-24
forum: Virtualisation
---

### Post by jimeast on 2016-07-24
I have Ubuntu Server 16.04 in a virtual box on a win 10 pro machine.  I run ifconfig to get the ip address "10.0.2.15".  From the windows machine I bring up a browser and enter [http://10.0.2.15/](http://10.0.2.15/)  shouldn't that get me in?

---

### Post by steeldriver on 2016-07-24
Since the virtualbox virtual network adapter is configured for NAT, you would also need to forward a free port from the host machine to the webserver port on the virtual machine I believe

Look under the VM's Settings --> Network menu and then press the Port Forwarding button

---

### Post by jimeast on 2016-07-24
I chose NAT and network  and I'm able access with ssh just not http.  I installed Lamp by selecting the option for lamp during the server install.  I don't know if more is required to get the Apache server running.  I was browsing through the folders looking for the www folder.  Do you know what the exact path to the www folder should be for a properly installed Apache server?

---

### Post by SeijiSensei on 2016-07-24
I suggest you change the network configuration in VirtualBox from NAT to bridged and reboot the VM.  Now it will get an address in the same network subnet as  the host computer.  You'll be able to see the VM just like any other machine on your network.

NAT works well if you only want the VM to be a client.  If you want it to act as a server, you should use bridged networking.

---

### Post by jimeast on 2016-07-24
I'm sorry I was away from the machine in question and I forgot that I had actually set it to bridged then I deleted that vm and started a new Ubuntu Server 16 install because I wanted to select lamp for installation and I thought it would be the easy way.  On the new install I had forgotten the bridged network thing and I thought for sure I would have ssh access because that's what happened when I set network to bridged on the last install.  So now I'm setup with bridged networking and when I try to ssh into it the connection is refused.  I noticed when I use the wrong IP the connection times out now it's refused like it's mad at me or something.  So now I'm back to trying to figure why ssh isn't working .... arrrgh! :(

---

### Post by SeijiSensei on 2016-07-25
Are you sure you have the right IP address for the VM?

---

### Post by howefield on 2016-07-25
Moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2016-07-26
Did the OP ever say what OS his host was running???

If the host is Ubuntu. Open a terminal on both the host, and post the results of
```

ifconfig -a

```
If the host is Windows, open a cmd window and post the results of
```

ipconfig /all

```
On the guest, open a terminal and post the results of
```

ifconfig -a

```
..that input from you will let us know if your guest is on the same NID as your host... and where to go from there.

---

