---
title: "Ubuntu terminal server; Windows fat or thin clients"
date: 2010-02-18
forum: Server Platforms
---

### Post by detyabozhye on 2010-02-18
I want to set up an Ubuntu terminal server that will store user accounts and user data. I want it to be accessible from Windows fat clients, so people booting a fat client will have to log in using credentials stored on the Ubuntu server. Also, I want this clients to be able to boot into a Windows environment that the Ubuntu server will serve somehow.

I've searched around, and I can't find a solution for either of those. I tried setting up diskless nodes before, but I'm not sure how to do that legally with Windows without throwing away a load of money, so I decided to try a network that can support both fat and thin clients instead. Any information that can help me set up either of those would be extremely helpful. Thanks.

---

### Post by bmathis on 2010-02-19
You can serve up thin clients with a Linux desktop, but as far as I know, you cannot use Linux as a terminal server for Windows.

I'm afraid the only solution you have for providing a Windows based terminal server is to use Windows Server with Terminal Services or Citrix installed.

---

### Post by grg3 on 2010-02-19
I have never heard of using a Linux server setup using windows as "fat" clients. LTSP can use Linux thin clients and Linux "lofat" clients" and DRBL can use computers as Linux fat clients. I believe (haven't tried it) that DRBL can use a computer with Windows installed as a fat client. In other words, it boots Linux from server but uses some local resources and can also boot windows. You would have to check that on the DRBL site. I have used DRBL servers, but only for the CLoenzilla function of the server.

You could have a Linux server authenticate and keep personal shares for windows clients, but not run windows from the server. 

Some windows thin clients have the ability to run remote desktop on boot. You might be able to have the on rom Windows thin client software start in remote desktop mode and connect to a Linux server that way. It would still be a Linux desktop session.

---

### Post by mcarrara on 2010-02-19
I think there my be an issue with terminology here.

You asked:
[I]I want to set up an Ubuntu terminal server that will store user accounts and user data. I want it to be accessible from Windows fat clients, so people booting a fat client will have to log in using credentials stored on the Ubuntu server.
[/I]
The term fat client is where the problem comes in.  In this situation they are not fat clients, just clients logging into a network.  That can be done with Samba running as a PDC.  Windows (any PRO version greater than Win95) is installed on the workstations WINDOWS HOME VERSIONS WILL NOT WORK.  Then after Samba is setup and running as a PDC you can have the clients join the domain and your Ubuntu box will authenticate, serve profiles, host home directories, everything a Windows DC would do.

Now for thin clients.  I was told that it is possible to have Linux serve Windows desktops to thin clients.  I have never seen it, only been told about it.  I am attending a conference the first week of March where the person who told me about it is presenting.  I will be there to check it out.

However remember if you have 5 thin clients you still need 5 Windows licenses, you can not get by with buying one copy and sharing it to other computers, so there is no savings there.  You will save in the terminal server licensing, and the TCO should be much lower.

Mark

---

### Post by lykwydchykyn on 2010-02-19
> **mcarrara said:**
> 

Now for thin clients.  I was told that it is possible to have Linux serve Windows desktops to thin clients.  I have never seen it, only been told about it.  I am attending a conference the first week of March where the person who told me about it is presenting.  I will be there to check it out.

However remember if you have 5 thin clients you still need 5 Windows licenses, you can not get by with buying one copy and sharing it to other computers, so there is no savings there.  You will save in the terminal server licensing, and the TCO should be much lower.

Mark

Sounds a lot like a VDI sort of thing such as VMware offers - basically your thin client remotes into a virtualized Windows session on the VMware server. (see this: [http://www.vmware.com/products/view/](http://www.vmware.com/products/view/))

I've tried to set this up "on the cheap" using Linux and VirtualBox before.  I suppose this would work in theory, but in my testing the performance was appalling.  The hardware required to run something like this effectively would be expensive enough.

How many thin client users are we talking here?  And what sort of workload are they putting on Windows?

---

### Post by detyabozhye on 2010-02-19
Thanks for the replies. After more research, I've come to the conclusion that Windows thin clients will be too expensive for the company I'm setting this up for.

I've used DRBL before for Linux-based diskless nodes, and I've heard you can use DRBL for Windows diskless nodes as well, but we run into the same issues with licensing and cost as with thin clients (except that thin clients will probably require a Windows server as well and thus be more expensive).

There will be a total of maybe 25 clients for now, and all will be fat clients, or if that's the incorrect term, they will store data on and authenticate users with the server.

---

### Post by tikal808 on 2010-02-21
You should really look into [NoMachine]("http://www.nomachine.com/") NX Server

I have used the free version for a while now with much success.  The free version is only limited by the amount of concurrent users and connections, not functionality.  So it's definitely worth experimenting with. It uses [OpenSSH server]("http://openssh.org/") for securing/encrypting connections.  NX Server will use the existing accounts that are already on the system by default. You can always tweak it slightly in the config file to change the behavior.

I live in Seattle and installed it remotely over SSH on a friends Ubuntu Desktop running GNOME, who lives in Portland. (a ~3 hour dive)  _It's like I'm sitting in front of his desktop._  **It's shockingly fast.**  

I'm also running a NXserver over a residential 802.11G wifi (a short distance) routed over the Internet from about 25 miles from where I am.  It's a lot slower but still manageable.

The best part is that they natively support x86-64 and x86-32.  And naturally you can mix and match your 32 and 64 bit clients to the 32 or 64 bit server!!
[http://www.nomachine.com/select-package.php?os=linux&id=1]("http://www.nomachine.com/select-package.php?os=linux&id=1")

---

### Post by ICEB3AR on 2010-02-21
Don't know if it is that what you expect, but if you only want to store user data a Primary Domain Controller would work for you. You can set up one with Samba. I do not know exactly what other Predefined Values you need or can Configure with samba, but it should be worth a look.

Best Regards

---

