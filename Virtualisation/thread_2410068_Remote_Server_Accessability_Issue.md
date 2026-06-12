---
title: "Remote Server Accessability Issue"
date: 2019-01-10
forum: Virtualisation
---

### Post by josephmmorgan on 2019-01-10
I'm working on a remote administration tool and need to test against a remote server.  So I installed a server on another Ubuntu machine, but I can't seem to access it.  This is my setup:

Development machine:  inet 192.168.1.82  netmask 255.255.255.0  broadcast 192.168.1.255
Development server (inside VMWare on my development machine):  192.168.94.2

So, I can access the development server from the development machine just fine.

Remote machine:  inet 192.168.1.86 netmask 255.255.255.0 broadcast 192.168.1.255
Remote server (inside VMWare on the remote machine):  192.168.221.2

I can access the remote server from the remote machine just fine.

I need to be able to access the remote server from the development machine.  These two machines right next to each other connected through the same switch.  I thought ufw would have solved my problem, but didn't (or I was doing it wrong). I now suspect it has something to do with how I have VMWare networking properties set, but don't know enough to solve the problem.

Can someone help this networking dummy solve the problem??

---

### Post by 1clue on 2019-01-10
In your VMware settings, is your network type bridged? If not, make it be bridged. Otherwise you will need to configure VMware to route the packets, which is less easy.

---

### Post by josephmmorgan on 2019-01-10
There are 4 network adapters:
Network Adapter     Custom (/dev/vmnet1) <-- I think VMWare sets this up this way
Network Adapter 2   Bridged (Automatic) 
         Radio "Bridged:  Connected directly to the physical network" is selected
         Chexk box "Replicate physical network connection state is *not* selected
Network Adapter 3   Host-only
Network Adapter 4   Host-only

---

### Post by wildmanne39 on 2019-01-10
Moved to Virtualisation .

---

### Post by 1clue on 2019-01-10
You need to use an IP address which is assigned to the bridged network. Your client machine doesn't know anything about your host-only networks. Not sure what vmnet1 is set up as. So go with network adapter 2

You should be using an ip address on the same subnet as your client if you're using a traditional bridged network.

---

### Post by josephmmorgan on 2019-01-10
OK.. So when I'm inside the server inside the VM, I'm seeing 4 network interfaces named eth0, eth1, eth2 and eth3.  I suspect network adapter 2 is eth1.  
At this point, I'm not exactly sure what to do.  Do I set the IP of the server to 192.168.1.87?

---

### Post by 1clue on 2019-01-10
You seem to be a novice at VMware and virtualization as well as a novice at networking. Sorry if that's not true, but in the interest of clarity I'm going to talk like you have no idea what I'm saying.

VMware supplies these types of networks:
[LIST=1]
[*]Bridged. The VM appears to be a computer on your real network. It is assigned an IP address from your regular DHCP server. 
[*]Host-only. The host and the guest are the only systems on this network. Your VM can reach your host, and your host can reach the VM. 
[*]NAT. This works the same way your home router does, meaning your vm gets an address on a private network which is NOT the same as your real network. 192.168.94 instead of 192.168.1 in your case. The VM can use this to get to the Internet or to a server or printer on your local network, but nothing can get into your VM unless there is a port forwarding inside of VMware (a virtual router) or if it's from one VM to another VM. 
[/LIST]

Under normal circumstances there should be a DHCP server to automatically assign addresses for all three of these scenarios. So you shouldn't need to assign an address. Given that one of your VMs is a server you may want to give it a static address, but first let's get things talking the way we expect.

Personally I would shut down your VM, and then delete all its network interfaces and start over.

For the sake of this experiment you really only need one network adapter for your VM, and that should be bridged. You should for the moment leave it to its default, which would be to get an address automatically from DHCP.

On your VM, what type of operating system does it say?  64-bit Linux Ubuntu? This should be set as closely to accurate as you can make it. The reason is that VMware changes how its software talks to the VM based on what you choose here.

So, assuming you have an accurate item selected in the VMware control panel for operating system, here's what you do:
[LIST=1]
[*]Shut down the vm. 
[*]Edit the settings 
[*]Delete all 4 network adapters. 
[*]Create a new network adapter.
[LIST=1]
[*]Choose the defaults for what brand/type of device. 
[*]Make sure it's bridged. 
[/LIST]
  
[*]Save settings. 
[*]Start the VM. 
[*]Login to the VM through the vmware console 
[*]Get your ip address. 
[*]Ping your workstation from the VM 
[*]From your workstation, ping your VM. 
[*]From your VM, ping 8.8.8.8 or [www.google.com]("http://www.google.com"), or any other public IP which responds to ping. 
[/LIST]

If all that works, you're done.

---

### Post by josephmmorgan on 2019-01-10
> You seem to be a novice at VMware and virtualization as well as a novice at networking.
100% correct!  

> I'm going to talk like you have no idea what I'm saying.
Thank you!

The host of the VM is 64 Bit Linux
The OS of the server is an IBM DataPower appliance

The DataPower appliance does need ethernet interfaces (unless it is a Linux, Azure, or Docker variant of the appliance).
These things only seem to work if at least one ethernet interface is  correctly configured, because that's how the appliance receives traffic.  

It might also be important to know it is running inside VMWare Workstation 14.

If I use the custom interface to the /dev/vmnet1 that was created on  both my dev machine and this other server machine, at least I can access  the appliance locally (on the VM's host only).

I did as you suggested.  But it is not working.  In fact, inside the  server, it is saying the ethernet interface now no longer exists (even  though I can see in the VMWare window at least it thinks one does)!   That is, if I can't configure the eth0 (or any other), it simply won't  work other than accessing directly on the command line.

So I shut it down, deleted them all again.  When recreating the  adapters, the "Custom" option isn't even there (which is what it seemed  to default to when I imported the image into VMWare) so I can't even  restore it back to the way it was, which may mean this server appliance  is now pushing up daisies (as far as my needs go).  What's worse is when  I even try to ping, it logs me out like slamming a door in my face.

I could always delete the entire VM and re-import it, but I'd be back to no access outside of the host.

---

### Post by 1clue on 2019-01-10
Full disclosure here, I have never messed with an "IBM DataPower Gateway." I have a pdf opened and am trying to figure this out as I go. I do NOT miss IBM's RedBook documentation scheme. Nothing has changed evidently in the 20 years since I worked there.

According to the documentation, there is no support shown for VMware workstation. That may or may not be a problem.

It looks like you downloaded an appliance specifically for VMware, so some questions go away.

Network interfaces: 
[LIST]
[*]At no time will your system be running without a network interface. It would be the virtual equivalent of powering down your box, taking out all the network cards and putting a single, new, known-to-be-good card in, and then powering back up.
[*]Just because you don't have a host-only network defined does not mean your host can't communicate with the VM. Any network that both the host and the VM have access to can be used to communicate in a normal fashion between host and VM.
[*]Your host has a regular network connection on your real network.
[*]If your VM has a regular network connection on your real network (by using a bridged network in VMware) then your host and VM can communicate, and any other computer on your network can get to the VM too.
[*]If you have a host-only NIC on the vm, then that network can be used for private communication between the host and the VM.
[*]If you have a NAT NIC on the vm, then you can communicate with the host OR any other VM which shares that virtual network, but real systems on your real network can't reach them through that network, nor can VMs which are on another host.
[/LIST]

The NAT and host-only network card types can be a brain bender for a VM newbie. If you make everything be a bridge until you figure things out -- especially since you have two hosts -- then you will just see the VMs as computers on your network. You don't have to worry about routing or the security inherent in the other networking types which may be causing your lack of communication.

That said, if you don't want to delete the network cards from your VM, then you can figure out how to determine the IP address of interface 2 and use that.

Personally with managing VMs, it's not uncommon to have the guest network connection be borked up, and the easiest solution is to delete the NIC and add it again. Then it starts with defaults.

If someone else would chime in with VMware experience it might provide reassurance.

---

### Post by 1clue on 2019-01-10
The beauty of VMs is that you can always start with a fresh copy of the image and do it again. If your image insists on that custom interface being there then it may be true that deleting it trashed your image. If that's the case then I'm sorry.

If you do go that route (restoring from the original VM image), then make sure that the custom vmnet1 interface is left untouched, and then add a bridged network for interface 2. Just leave it at the default settings, and it should get an address so it appears to be a peer of the host.

There may be some sort of firewall on your appliance too, which would prevent network traffic outside the host. I don't see anything about that in the PDF.

My wife is calling, so I gotta go. Good luck. If you still have questions tomorrow I'll try to answer them.

---

### Post by josephmmorgan on 2019-01-10
If that's the case then I'm sorry.> If that's the case then I'm sorry.
No worries.  This is easy to fix as I can just recopy my Dev vm files back over to the other machine and try, try again.  Which I will do and try the bridge interface on eth1 ( which I suspect is the same as second network adapter ).

---

### Post by josephmmorgan on 2019-01-11
So I have the appliance back up to the way it was.  Eth0 is on the dev/vmnet1.  Now that I have my network adapter 2, which I presume is the DataPower appliance's eth1, what is the IP of that interface?

---

### Post by 1clue on 2019-01-11
If your VM has a VMware Tools then you can see the IP address from the vmware console.

Otherwise, you'll have to figure it out from inside the VM. Since I don't have any idea what operating system your VM is based on I can't help with that.

If it's Linux, and if you can get a command line, then you could use one of:
[LIST]
[*]**ip address list**
[*]**ifconfig**
[/LIST]

---

### Post by josephmmorgan on 2019-01-11
With DataPower, I don't (or have never seen) it automatic, and those commands are not available in the DataPower CLI.    I don't have a clue where to go in VMWare to see the IP.  If I click on the network adapter icon for Network Adapter 2, I can go to settings and look around there, but even under Advanced there is no IP being displayed.  So I tried the same on the Network Adapter on the dev/vmnet1, where I know an IP exists because I'm able to connect to the appliance's web management on that IP, but VMWare doesn't show me the IP anywhere.

There is a link under the Virtual Machine menu in VMWare "Reinstall VMware Tools..", but it is grayed out.

---

### Post by 1clue on 2019-01-11
In the panel where all the VMs on a certain host are displayed, and whether they're running or not, you will see an IP address for fully running systems which communicate that back to the host.

I don't even know what operating system this VM is based on. If it's Windows-based then your command would be **ipconfig /all**

---

### Post by josephmmorgan on 2019-01-11
DataPower OS (DPOS) is very very loosely based on Linux, but the only command similar to traditional Linux systems is traceroute.  Just about everything else is proprietary to the shell and there is no way to change that.  The one thing I can get doesn't show an IP on any other interface than the one (eth0) on the dev/vmnet1 device.  But, strangely, there seems to be a large number of bytes on the receiving end of eth1.

As far as eth0 on the dev/vmnet1 device goes, even though the host (ifconfig) shows the host IP as 192.168.221.1, I still had to configure the eth0 interface primary IP as 192.168.221.2 with a default gateway of 192.168.221.1 for anything to actually work.

So, does that also go for the bridged adapter on eth1 (network adapter 2)?  That is, if ifconfig shows my host as 192.168.1.86/24 (broadcast on 192.168.1.255), can I use an IP ending with any other number from 2 to 254?


I suspect the VMWare Workstation 14 Player does not have what you're talking about.  I went through every menu option, every screen, every setting and popup I can find while running and not running, and I don't see IP reported by VMWare anywhere.

---

### Post by josephmmorgan on 2019-01-11
Oh yay!  You solved it!  I should have just tried my guess before responding.  So I found I was able to ping to the host's main IP of 192.168.1.86, and then put the eth1 on 192.168.1.87 with .86 as my default gateway.. and BOOM!  It works!

Thanks a million.  I still don't completely understand what I've done here, but it lets me do what I need to do!

---

### Post by 1clue on 2019-01-11
To avoid confusion, your 192.168.1 address is almost certainly your real network used by your house or office or whatever.

That network (192.168.1) is managed by a dhcp server, which will either be a separate system (if you're in a bigger office) or by your wireless router, if you're working from home or a small office.

You should go look at the settings for that and figure out your DHCP address pool. If you randomly choose an IP in the subnet, or worse, pick your known IP + 1 as you did, then there is a really good chance that the dhcp server will assign your .87 address to the next system that wants an address. At that point you'll have an address conflict and one or both systems will not work correctly.

FWIW your VMware settings for the guest should let you choose which network to connect the virtual NIC to. That network will be either a real network or a virtual one. That's a generic virtualization thing, not a VMware thing.

---

### Post by josephmmorgan on 2019-01-11
> To avoid confusion
Like I'm not confused already!  LOL.  
> our 192.168.1 address is almost certainly your real network used by your house or office or whatever.
Everything I have (home) is 192.168.1.xxx (except these VM's... which clearly do something different).
> You should go look at the settings for that and figure out your DHCP address pool
That I *can* do and in spite of my general ignorance, I can reserve IPs for certain systems.  Hopefully it will allow me to reserve that one. 
> the dhcp server will assign your .87 address to the next system that wants an address
Will it do that while the VM is running?  That is, if something is already listening on .87 on the network, will the DHCP just arbitrarily assign that IP?
> your VMware settings for the guest should let you choose which network to connect the virtual NIC to
I have no doubt, but I certainly cannot figure out how to do it.

Either way... this is enough to get me going.  If I run into address conflicts, at least I'll have a good idea on what is causing it.  This is a pretty short term proof of concept test, so once I work out any kinks in it, it will go away as quickly as it came.

Can't thank you enough.

---

### Post by 1clue on 2019-01-11
OK. Best practice would state that you put your static addresses outside of the DHCP pool. Most SOHO routers (small office/home office) will let you reserve whatever IP was allocated for that system, which drives me and probably every other IT professional crazy.

Your DHCP server will renew the .87 address as long as you're using DHCP to get that address and the system leasing it is running. From what you said though, you configured a static IP address which you decided on by adding 1 to your workstation's address So .87 was not allocated by DHCP and your DHCP server does not know that someone is using it. So likely the very next device which tries for a DHCP address will get .87, and you'll have a conflict.

In other words, it could very likely allocate .87 to another computer while the VM is running. There SHOULD be code in the dhcp project to check for somebody using that address, but in my experience it's not always reliable.

Most SOHO routers have a default DHCP pool either right close to the low end of the block (.2, .3 or .10, .11 etc)  or at the high end. You need to choose something for your static server addresses which is not part of the pool range. I already said this so I guess I need to shut up now.

:)

Good luck and have fun.

---

