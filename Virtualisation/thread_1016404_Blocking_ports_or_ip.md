---
title: "Blocking ports or ip"
date: 2008-12-19
forum: Virtualisation
---

### Post by quikone8 on 2008-12-19
I have had a mail server running on ubuntu for some time.  I wanted to install a web server as well, but couldn't figure out how to make the two co-exist.  I now have installed VMware and plugged in the additional NIC but am having trouble starting the VM.  Also,it seems that when VMware is running it locks me out of the rest of the machine from the outside world.

Anyone have suggestions?

---

### Post by bodhi.zazen on 2008-12-19
we need more details.

Version of VMWare ?

How did you configure your network ?

What problem / error are you getting when vmware starts ?

---

### Post by quikone8 on 2008-12-19
> **bodhi.zazen said:**
> we need more details.

Version of VMWare ?

1.07

How did you configure your network ?

Email server is running on Intrepid (the email server is Citadel/Webcit), this is running on metal.

What problem / error are you getting when vmware starts ?

total 1212
-rw-r--r-- 1 root root 514 2008-12-19 11:51 config
drwxr-xr-x 3 root root 4096 2008-12-08 21:13 hostd
-r-xr-xr-x 1 root root 16606 2008-12-08 21:13 installer.sh
-rw-r--r-- 1 root root 375 2008-12-19 11:49 license.vs.1.0-00
-rw-r--r-- 1 root root 1162303 2008-12-19 11:48 locations
-rw-r--r-- 1 root root 86 2008-12-13 17:11 netmap.conf
drwxr-xr-x 2 root root 4096 2008-12-08 21:13 pam.d
drwxr-xr-x 2 root root 4096 2008-12-08 21:13 service
-r--r--r-- 1 root root 182 2008-12-08 21:13 signing-key.pub
drwxr-xr-x 2 root root 4096 2008-12-10 20:52 ssl
drwxr-xr-x 2 root root 4096 2008-12-08 21:13 state
-rw-r--r-- 1 root root 122 2008-12-18 13:57 vm-list
-rw-r--r-- 1 root root 87 2008-12-19 11:23 vm-list-private
drwxr-xr-x 3 root root 4096 2008-12-19 11:46 vmnet1
drwxr-xr-x 4 root root 4096 2008-12-19 11:45 vmnet8
ron@tolmarket:/etc/vmware$

I turned looging on and get this;

Unable to change virtual machine power state: The process exited with an error:
vmxvmdb: Index name being generated from config file
POST(no connection): Directory "/home/ron/.vmware" is not accessible: Permission denied.
Cannot proceed without directory "~/.vmware". It is needed to store user preferences and other information.

Failed to initialize VM.
End of error message. 

I am sorry I don't have access to the config file right now.  One question I have regarding that is when configuring the new server should I let the wizard choose the ip's or should I assign them.  In other words, I noticed the wizard does not pick the ip's of the NIC's.

---

### Post by bodhi.zazen on 2008-12-20
The first error : 

> POST(no connection): Directory "/home/ron/.vmware" is not accessible: Permission denied.

Is a permissions problem.

.vmware is a directory in your home directory, it is hidden (because of the . in front).

so .... 

what are the ownership and permissions of that directory ?

```
ls -l ~ | grep .vmware
```The second question is a bit different. And your posting style continues to be quite sparse on details. Version of vmware ? Hose OS ? Guest OS ? All these variables come into play.

In general on the vmware interface you select an interface (bridge, NAT, host only) and in general the IP address is assigned by configuring the guest as you would any physical computer.

If you use bridged, your IP will be assigned by your router. If you use NAT your IP will be assinged by VMWare as a sub net.

To be more specific we need more details on what you are running and what problem you are having.

---

### Post by quikone8 on 2008-12-20
> **bodhi.zazen said:**
> The first error : 



Is a permissions problem.

.vmware is a directory in your home directory, it is hidden (because of the . in front).

so .... 

what are the ownership and permissions of that directory ?

```
ls -l ~ | grep .vmware
```The second question is a bit different. And your posting style continues to be quite sparse on details. Version of vmware ? Hose OS ? Guest OS ? All these variables come into play.

In general on the vmware interface you select an interface (bridge, NAT, host only) and in general the IP address is assigned by configuring the guest as you would any physical computer.

If you use bridged, your IP will be assigned by your router. If you use NAT your IP will be assinged by VMWare as a sub net.

To be more specific we need more details on what you are running and what problem you are having.

I will get back to you on the permissions, I will be in front of the server this afternoon.

The VMware version is 1.07.  The Host OS is Ubuntu 8.10, I am hoping that the guest OS will be 8.04.  This is running on an older Dell 2900 server.  I don't know if it makes a difference, but I will be accessing with a laptop running 8.10.

You talked about the ip's in reference to my question.  That is another part I was not understanding.  If I am going to use a static ip, how do I answer the questions posed in setting up the config.pl?

In general, I am experiencing two problems, the first and most important is that with VM running I cannot access the server from the outside world, and the router is routing the traffic.  When I vmware stop, access from the outside world is no problem.  So, I am sure I have the config.pl set up incorrectly.  

Second of course is the fact that I cannot start the virtual server.  Which I think your question will eventually solve.  (thank you)

This was all complicated by the fact that network manager has a bug that has yet to be solved.  I have switched to wicd.

Thanks again,

Ron

---

### Post by bodhi.zazen on 2008-12-20
Usually when installing vmware, go with the defaults.

You set an IP in the guest.

So fire up the Ubuntu guest, use Network Manager (or manually edit) to set a static IP address, same as you would on the host. You do not set an IP for your guest in the configuration of VMWare.

You mentioned Wicd, are you using a wireless card ? If so, did you use the any-any update to install vmware ?

---

### Post by quikone8 on 2008-12-20
> **bodhi.zazen said:**
> Usually when installing vmware, go with the defaults.

You set an IP in the guest.

So fire up the Ubuntu guest, use Network Manager (or manually edit) to set a static IP address, same as you would on the host. You do not set an IP for your guest in the configuration of VMWare.

You mentioned Wicd, are you using a wireless card ? If so, did you use the any-any update to install vmware ?

Following are the results of what you asked;

 ls -l ~ | grep .vmware
drwxrwxrwx  2 ron  ron       4096 2008-12-18 13:51 vmware
drwxr-xr-x  7 ron  ron       4096 2008-12-12 16:31 vmware-mui-distrib
drwxr-xr-x  7 ron  ron       4096 2008-12-14 20:17 vmware-server-console-distrib
drwxr-xr-x 11 ron  ron       4096 2008-12-09 17:14 vmware-server-distrib
-rw-r--r--  1 ron  ron      44736 2008-12-10 20:22 vmware-specific-specific-55x-and-kernel-2627
drwxr-xr-x  2 ron  ron       4096 2008-12-10 20:37 vmware-update-2.6.27-5.5.7-2
-rw-r--r--  1 ron  ron    1754854 2008-10-27 08:30 vmware-update-2.6.27-5.5.7-2.tar.gz
 
I am using wicd in place of  NM 0.7, because I cannot get NM to retain a static ip on both cards.  No wireless, I am just using wicd for the connection manager until NM is fixed.

You said fir up the Ubuntu guest.  I cannot, due to the fact that it will not fire up.  See first post for details.  So, I do not even have the OS loaded yet due to that problem.  Hopefully the above info will help.

Again, thanks for your help,

Ron

---

### Post by bodhi.zazen on 2008-12-20
sorry, my mistake

ls -l**a** | grep .vmware

---

