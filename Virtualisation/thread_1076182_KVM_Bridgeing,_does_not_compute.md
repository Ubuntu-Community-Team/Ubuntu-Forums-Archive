---
title: "KVM Bridgeing, does not compute"
date: 2009-02-21
forum: Virtualisation
---

### Post by lewtwo on 2009-02-21
I am trying to setup Ubuntu Server as a vitual machine host.
As a server natting is not very usefull to me thus I am trying to get bridging working. Because the guest will be servrs i want to use static IPs on the real Lan.

I read several posts, help files, etc. One point remains very confusing. The sticky post at the top of this forum:

[http://ubuntuforums.org/showthread.php?t=973756&highlight=KVM+Bridging](http://ubuntuforums.org/showthread.php?t=973756&highlight=KVM+Bridging)

Shows an example of the changes to the "/etc/network/interfaces" file. In the static example is shows eht0 as "manual" ip interface but does not show the parameters in particular the IP address.

Under the Tap examples it shows two taps both using the SAME "uml_proxy_arpa 192.168.0.10" line. 

Further down in the br0 it shows the same address for the IP address "address 192.168.0.10". I am thinking that this should be the static address assigned to the guest machien using br0. Further down it shows the line "bridge_ports eth0 tap0 tap1".

===============
So the questions are:
1) Is the IP address above the IP address to be assigned to the guest ?

2) Why would one need two taps for br0.

3) What do the following lines mean/do:
   bridge_fd 9
   bridge_hello 2
   bridge_maxage 12
   bridge_stp off

4) Is there a good document on bridging that documents all the parameters and I have just failed to find it ?? (where is it) ??

5) I have to delve into controling Ubuntu Server's firewall or figure out how to turn it off. As I have a firewall in front of the machine I would rather just turn it off. Is there a simple way to remove it or turn it off ??

Thanks in advance for any help.

Lewis

---

### Post by bodhi.zazen on 2009-02-21
I do not know of a single good "all in one" source of information on bridging your network cards, and I admit I no longer recall what all the options are.

Basically, you make a bridge, then you add you physical ethernet card to it, then you add a tap. You add 1 tap per virtual machine. If yo uonly have 1 guest, you need only 1 tap.

Personally, at the moment, I use KVM. I start KVM with a wrapper script which makes a tap for each guest on demand, so I do not do more then configure a bridge on my host.

Of course some guests, such as when I test an ISO, so not need more then the default NAT anyways ... 

By default the firewall (iptables) in Ubuntu is permissive and should allow all traffic.

So, this can be as complex as you wish to make it, and you are asking good, but somewhat complex questions.

If you wish to assign a static IP to your bridge, you need to assign an IP on the host. You then add a tap, boot the guest, then configure the guest to use a static IP address.

Sorry I can no toffer you a ton of more specific advice, I tend to delve into such things whenever I set up a host for my virtual OS, then ignore it untill the next time. Personally I go between Ubutnu / Debian/ and Fedora as a host, and the options aer all somewhat different in each host / guest.

You migh ttry this : 

[http://www.citi.umich.edu/projects/asci/uml/2.6.6uml.html](http://www.citi.umich.edu/projects/asci/uml/2.6.6uml.html)

referances at the bottom of the page ;)

And from the first link, this is awesome : [http://edeca.net/articles/bridging/index.html](http://edeca.net/articles/bridging/index.html)

---

### Post by lewtwo on 2009-02-22
Thanks for the input.
I did manage to get br0 set up and working, but everytime I tried to add another I lost all ip functionality. 

I have not been able to find good documentation on bridging. I am going to try something else (VBox). There is simply too much effort rerquired to get it working properly. In a production enviroment that effort would translate to dollars (yen, eros, pounds or whatever). At the moment we are running HyperV and VM server on Windows Server OS hosts. About every six months I come back to linux to see what progress has been made.

My conclusion this time with regards to KVM: not ready for prime time.

---

### Post by bodhi.zazen on 2009-02-22
I am sorry it did not work out for you, but ...

To be honest it takes me at the most 10-15 minutest to set up a bridge. Virtualization is, IMO, complex, especially in the "production" environmnet and you are making a sweeping generalization / assumption.

Even "VMWare" , a gold standard in this area, has training and certification and you should not expect to understand how this all works out of the box.

[http://mylearn1.vmware.com/portals/certification//](http://mylearn1.vmware.com/portals/certification//)

To be honest, what you are facing is a lack of personal knowledge. This is not the same thing as Linux or KVM being deficient or not ready for prime time.

people recieve extensive training to do what you are asking and these things do not work "out of the box" the way you envision.

Have you looked at KVM solutions ?

[http://www.proxmox.com/](http://www.proxmox.com/)

Open source, KVM + OpenVZ, web based interface, virtual applicances available ...

---

### Post by alexkent on 2009-03-05
I loved xen until it became unsupported on ubuntu and other platforms, making me look at KVM before my needs grow any larger.

The one thing I couldn't figure out was how to set an IP address of the virtual server - something I'm surprised isn't vitally important to people that someone has made it easy!

xen has a really good way for assigning IP address. In the config for a server, the following line does it:

vif = [ 'ip=146.3.120.34,mac=00:16:AA:AA:AA:AA' ]

Does anyone know why xen can do, yet KVM needs these complicated bridging steps to have been performed before the domU is started?

Or is at simple as xen, yet I've failed to find the documentation anywhere?

Any help = much appreciated,

Alex

---

### Post by freakalad on 2009-03-16
I'm not quite sure if my issue relates to this one, but it has some similarities.

I'm running KVM at work (64-bit Hardy) & at home (64-bit Intrepid).

On both environs it seems pretty stable (well, more or less). 
On both, I have 2 physical NIC's; my host's eth0 is bound to my br0 for LAN network 10.0.0.0/25 & my eth1 bound to br1 for WAN on 192.168.0.0/25.
From the host, I'm able to ping nodes on the separate networks, though from clients it's pretty tough & go at times.

At home I've managed to install pfSense, connecting to both interfaces.
At work, I've not had that much luck, yet.

Something screwy takes place if I stop/suspend a VM, remove or alter an interface (for purposes like tapping it to another bridge or isolated private network or point-2-point), even if observed from a 32-bit hardy client/vm. 
Interfaces iterate (eth0, eth1, eth2, ethX), and this is causing all sorts of trouble on the clients (I have to do a "factory reset" of my pfSense VM router/firewall to get it going again, which, as you may guess, is less than ideal), so that arrangement is somewhat less than ideal.

Does anyone have any info or recommended reading for me on this?
I'll work through this systematically, but just hoping someone else has been through this before and may be able to give me some pointers, please

Cheer

- J

P.S. as a quick fix, where can I rename ethX to eth0?

---

### Post by lewtwo on 2009-03-20
> **bodhi.zazen said:**
> I am sorry it did not work out for you, but ...

To be honest it takes me at the most 10-15 minutest to set up a bridge. Virtualization is, IMO, complex, especially in the "production" environmnet and you are making a sweeping generalization / assumption.

Even "VMWare" , a gold standard in this area, has training and certification and you should not expect to understand how this all works out of the box.

[http://mylearn1.vmware.com/portals/certification//](http://mylearn1.vmware.com/portals/certification//)

To be honest, what you are facing is a lack of personal knowledge. This is not the same thing as Linux or KVM being deficient or not ready for prime time.

people recieve extensive training to do what you are asking and these things do not work "out of the box" the way you envision.

Have you looked at KVM solutions ?

[http://www.proxmox.com/](http://www.proxmox.com/)

Open source, KVM + OpenVZ, web based interface, virtual applicances available ...

The reason that WINDOWS is king in the SMB enviroment is that it works out of the box (in 99.9% of the cases). 

VMWare traning/certification/support is hugely exspensive beyond the budgets of most SMB IT Deparments. VMware server 1.X was huge success because anyone could run it (out of the box) on nearly any platform and maintian it with tools they were familar with. Version 2.X discards all that. Along comes HyperV that runs on nearly any hardware (that supports processor vertualization) and has a simple GUI interface.

Yes I have looked at proxmox and I am very impressed thus for. It does seem to work out of the box. They have a good start but are missing a few things (Exampe): Built is backup is great but only if there is a restore to go with it (can be done from ssh command line but missing in the GUI). Still it is good start and they are making rapid progress ... it may prove to be  giant killer.

Ubuntu and KVM is a good combination but NATing the VMs on the host is useless except for running an Alternate OS workstation. Bridging/Tap is complex, poorly documented and unreliable. It is a problem to be resolved if the combination is gather critical mass to move to the top of the heap (where I believe it belongs).

---

### Post by freakalad on 2009-03-23
lewtwo : I'm likely to agree with you on the docco-side, but this will catch up & fill in as the use becomes more pervasive.

I hear what you're saying about "out-of-the-box" windoze, but it's also out-of-the-box viruses & exploits. Poor planning & implementation is no excuse for poor security. If you want something close to "out-of-the-box" LAN networking in desktop linux, NFS is really the way to go, but Samba's also pretty widely-used & implemented nowadays (thanks in part to m$).

I expect much of these needs, requirements & shortcomings will get addressed very soon, as one of the strong selling points of the upcoming Ubuntu releases would be it's focus on cloud-centric services & therefore, by extension, VM's (VM/utility-computing on posix/unix/linux had been well established for a VERY long time - back to mainframe days in fact - but it's becoming more user-friendly now)

IMO, windoze is a bad habit that's hard to shake...

---

### Post by lewtwo on 2009-03-24
>> but this will catch up & fill in as the use becomes more pervasive. <<
That is why I keep coming back to take a look. I think the whole Linux arena is getting very close. Of course there are other limitations such as some applications that will only run under Windows.

>> Poor planning & implementation is no excuse for poor security. << 
Unless it works there is nothing to protect. I have seen Net Admins who secured there resources so well the users could not make efficent use of then. Resources that are unuseable (by the unwashed masses) are worthless.

>> If you want something close to "out-of-the-box" LAN networking in desktop linux, NFS is really the way to go <<
Would like to agree with you but anything Linux based still runs with limited file attributes and management compared to NTFS and Active Directory.

I live/work in realm of international corporate computing enviroment where theoretical solutions get crushed against the wall of real world limitations on a regular basis. I sit in stands for the home team but I want the other side to pull ahead ... sometimes that gets me in trouble.

---

### Post by freakalad on 2009-03-24
1) I've found very little in the way of limitations: most win-based apps have a very good, or better, FOSS equivalents, though some do require a bit of polish. The rest are covered very well with wine

2) I agree. I've come to the conclusion that security is about risk-management; the tighter your security, the more of an inconvenience it is for the end-user (which may inadvertently weaken security, since user are likely to pick weak password to simplify their lives). 
IMO, there's no such thing as "absolute security", other than turning the machine off & pulling all plugs

3) My usage of directory services are very limited, so I'm not in a position to comment. Corp may be forced to consider the "theoretical" & FOSS if they plan to get ahead; it's about the bottom line, and licence fees are going to suffer (I'm seeing this in some of my dealings)

The biggest obstacle I've found in "the big switch", is that of a paradigm shift. Hats off to m$ (and kudos to Bill's vision) for fostering a widespread adoption of computing in our everyday lives, but this is a double-edged sword.
My opinion of win is that of "crack-ware"; laymen users are so hooked on the platform they know (i.e. "that little blue 'e' at he bottom of my screen"), and the politics & philosophy that goes with it, that very few have ever even wondered if there are alternatives. Some *nixers abrasive attitudes don't help either, and that HAS to change (I'm trying to foster better harmony between these 2 groups)

Buuuuuuuut, discussion is getting OT, although it IS very interesting.

---

### Post by lewtwo on 2009-03-26
> **freakalad said:**
> 1) I've found very little in the way of limitations: most win-based apps have a very good, or better, FOSS equivalents, though some do require a bit of polish. The rest are covered very well with wine

2) I agree. I've come to the conclusion that security is about risk-management; the tighter your security, the more of an inconvenience it is for the end-user (which may inadvertently weaken security, since user are likely to pick weak password to simplify their lives). 
IMO, there's no such thing as "absolute security", other than turning the machine off & pulling all plugs

3) My usage of directory services are very limited, so I'm not in a position to comment. Corp may be forced to consider the "theoretical" & FOSS if they plan to get ahead; it's about the bottom line, and licence fees are going to suffer (I'm seeing this in some of my dealings)

The biggest obstacle I've found in "the big switch", is that of a paradigm shift. Hats off to m$ (and kudos to Bill's vision) for fostering a widespread adoption of computing in our everyday lives, but this is a double-edged sword.
My opinion of win is that of "crack-ware"; laymen users are so hooked on the platform they know (i.e. "that little blue 'e' at he bottom of my screen"), and the politics & philosophy that goes with it, that very few have ever even wondered if there are alternatives. Some *nixers abrasive attitudes don't help either, and that HAS to change (I'm trying to foster better harmony between these 2 groups)

Buuuuuuuut, discussion is getting OT, although it IS very interesting.

Good points ...

1) Our solid modeling program, its attached document control system) and our vehicle simulation systems are windows based apps that will not run under wine (indeed they are sometimes challeneged on XP64 with 8 GBytes of RAM and high end Nvida graphics). They also have no equivalent in the Linux world (the vendor of the first two is said to be considering a Linux port ... but we are not holding our breath).

2) My first LAN had fairly good security. It was ArcNet with no connection to the ourside world. Only a few machines had the floppy disks connected (in the ones that did you could never count on two machines having the floppys aligned the same). Those days are gone.

3) We make extensive use of hiarchical group trees (ie group A & B belongs to group G, group A and C belong to group F, Group E and F belogn to group Z .... and its get worse). 

The only constant is change, however smaller changes are easier to digest. MS's radical change with the OS GUI for Vista and the GUI for office was thier biggest mistake. Many SMB's have refused to switch (we are one of them) because all the users would/will have to be retrained. That hits the bottom line hard. As I told our MS Rep ... "If you force us to retrain our users then why should we not not train them to use Linux and Open Office so we do not have retrain them again every 3 yarns".

cheers,

Lewis

---

