---
title: "Replacing an old windows server with an Ubuntu server for a company network. Need som"
date: 2010-02-02
forum: Server Platforms
---

### Post by Demented ZA on 2010-02-02
Hi, 

_Here's Some Background:_

I have the following situation at work:

We have a windows 2k server that some guy set up for us. Its acting as an active directory controller as well as the internet gateway. The machine is old, slow and giving hardware problems.

At any given point in time we have about 20 PC's running on the network. 15 of them are used by agents to do remote work(remote desktop) , voip, e-mail and browsing simultaneously.

_For the above purpose, there are two major problems I have with this system:_

1)We can't afford downtime. If the current Windows server fails, if the modem fails, etc, we are in a jam, to put it lightly. Parts are difficult to get hold of, Microsoft licensing issues might force us to go to newer software etc.

2)All these pc's are going through a single internet connection of 1Mb. (No, I'm not kidding). It gets worse, its and ADSL connection. In other words, our upload speed is half of our download speed.


What I would like to do is construct a seperate network consisting of its own independent Ubuntu linux server, its own dedicated internet connection with only say 3 to 5 pc's connected to that network as the workstations. Running in parallel with the origional network, but independent from it.

The reason for my goal is to aleviate stress from the internet connection, to be able to switch over to linux entirely in the long run, and to provide higher uptime to our clients because if one system (network) fails, we have another to fall back on. (Ultimately I want three of these networks running.

I know the answer is Linux... ;-)

**_It all boils down to this:_**

My first major problem is that the pc's still need to be connected to the same domain name as the existing network, but running in parralel. 

The second problem is that these 3 - 5 workstation pc's will have to be controlled by the linux server probably throughLDAP or something so that we can track who's logged in when, etc)

How do I accomplish the above? Or rather, can it be done?

I'm just looking for pointers and some experienced insight please guys. I have searched the interwebs, but i havn't found anything really helpfull.

Thanks in advance.

---

### Post by fang0654 on 2010-02-02
I know this isn't what you are asking for, but - 
 
I recently ran into a similar situation in my company, as far as very old and fragile Active Directory servers running on the brink of death.  (Man, those old P3's were workhorses).  What I did is this:

Build out a new server, make an image of the Win2K server, and turn it into a VM image.  Using VirtualBox, you then take away the danger of imminent death.  Then retire the old machine.

Although I haven't done it personally, I am pretty sure you can bridge multiple internet pipes in through the linux box, maybe separating the rdp users to one interface, and the internal users to another.

---

### Post by munky99999 on 2010-02-02
> 
We have a windows 2k server that some guy set up for us. Its acting as an active directory controller
active directory really isnt compatible with linux really.

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

It's not really coming along sadly to say.

> At any given point in time we have about 20 PC's running on the network. 15 of them are used by agents to do remote work(remote desktop) , voip, e-mail and browsing simultaneously.
Depending on what exactly they are doing in remote desktop; like full virtual; just virtual apps?

Other then that. Ubuntu covers that well.

> 1)We can't afford downtime. If the current Windows server fails, if the modem fails, etc, we are in a jam, to put it lightly. Parts are difficult to get hold of, Microsoft licensing issues might force us to go to newer software etc.
Yep and you're looking at a minimum of about 750$ for that one. Also there will definitely be downtime. Regardless of how to choose to replace. 

> 2)All these pc's are going through a single internet connection of 1Mb. (No, I'm not kidding). It gets worse, its and ADSL connection. In other words, our upload speed is half of our download speed.
Sadly my net isnt much better.

> What I would like to do is construct a seperate network consisting of its own independent Ubuntu linux server, its own dedicated internet connection with only say 3 to 5 pc's connected to that network as the workstations. Running in parallel with the origional network, but independent from it.

The reason for my goal is to aleviate stress from the internet connection, to be able to switch over to linux entirely in the long run, and to provide higher uptime to our clients because if one system (network) fails, we have another to fall back on. (Ultimately I want three of these networks running.
Well to minimize downtime. You're going to have to do this in a lab sense first anyway. Better practice though would be to make sure the linux network is up and going; take a weekend or something and move everything over to the new network without much notice; if possible. Then scrap the old infrastructure; if not simply reusing the old stuff as single use platforms; like a backup dhcp server or whatever.

> My first major problem is that the pc's still need to be connected to the same domain name as the existing network, but running in parralel. 
It may be impossible to keep the same active directory domain.

[https://help.ubuntu.com/9.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/9.10/serverguide/C/samba-dc.html)

First thing it says is... it cant be a pdc for ad; but it can be one for NT4 domain; however you most likely have your domain functional level too high to have the samba pdc to grab control.

> 
The second problem is that these 3 - 5 workstation pc's will have to be controlled by the linux server probably throughLDAP or something so that we can track who's logged in when, etc)
Sure openldap is doable. You might want to use hardy to do it though. Karmic really doesnt like open ldap.


The first reply is really the best idea perhaps.

Physical to Virtual the active directory beast. Pop it onto a virtual running on the new whitebox; bridged and basically you are moving exactly everything the old server did. Then simply wait for Samba4 to become stable enough for production purposes.

---

### Post by quietas on 2010-02-02
munky has the right idea I think. Linux can be an alternative to Active Directory, but LDAP doesnt' have all the functionality let alone the ease of use. LDAP is a pain in the butt. Samba4 could be viable, but it has been in development for years with no product which is enterprise ready.

For the lowest cost I'd recommend like they are saying. Pick up a sub $1000 server, load Ubuntu Server, CentOS, or other server product and set it up as a virtual machine host. Load your ISO in to VirtualBox or Xen and keep using Win2k. It's a case of if it ain't broke, don't fix it.

I actually run 2 Win2k domain servers as well and they won't go away until the Active Directory tree and Group Policies get a serious revamp on our end.

---

### Post by tlsarles on 2010-02-02
Ok, here are my thoughts.

fang0654's idea of virtualization; Highly Recommended.

Don't use virtual box tho, it really isn't a mature enough product IMHO. VMWare's ESX server is free now, I know it's not open source, but honestly, It's the best, and it's free. Citrix's Xen Server is pretty close tho, and free as well.

Both of these products will let you run multiple VMs on bare metal without one OS being dependent on another.

munky99999's comment on SAMBA is correct, it really isn't a drop in replacement for AD.... However, your saying your coming from a Win2k server. If you don't use group policy, and really just use the server for simple file sharing and internet rationing, then SAMBA will be fine. I just setup an Ubuntu box to authenticate share access via a Windows domain controller. Almost like a Kerberos setup. So it can be done.

I would just keep the Win2k VM running in parallel with the Ubuntu install, simply to do the domain authentication. Putting it in the VM on a new machine will give it a kick in the butt if it was lagging.

You can use the Linux box to do your routing, although with what you want to do I really recommend a Cisco router. You can get a 1711 with a VPN Accelerator for less than $100 on ebay.

[http://cgi.ebay.com/Cisco-1711-VPN-K9-w-VPN-WIC-4ESW-WIC-1AM-96D-32F_W0QQitemZ260459363492QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item3ca4967ca4]("http://cgi.ebay.com/Cisco-1711-VPN-K9-w-VPN-WIC-4ESW-WIC-1AM-96D-32F_W0QQitemZ260459363492QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item3ca4967ca4")

Why? Because you can't have downtime. Because you only have a 1mb line. Cisco will give you much greater control of your limited bandwidth with advanced QoS options. And you can setup netflows and put NTOP on your linux box to get reporting of every packet that goes through your router. Know how much of what protocol is using your bandwidth.... Things like that.

If you want a separate LAN for whatever reason, you need VLAN aware switches and routers. If you need switch ports, get used Cisco off ebay again. Get like 12 100mb ports for around $20 for solid equipment.

Could do this whole project in a phased approach so that you downtime is only about the time required to reboot a box and switch the internet cable from one machine to the other. Won't cost a lot.

What sort of specs are you looking at for your new server?
BTW, What specifically are you using the w2k box for? Just domain authentication and file sharing?

---

### Post by Demented ZA on 2010-02-03
Once again, Thank you fang0654, munky99999, quietas, tlsarles, for your  input. much appreciated, you guys gave me some great ideas!

I think virtualizing would be a great idea. The only problem (And maybe I wasn't clear in my origional post) we are _not so much_ thinking of scrapping the origional win2k server just yet. Simply because it works. (Not my decision, but I respect it. That is not to say that its set in concrete ;-) ). Ultimately I want to do away with Windows server due to the costs, speed overheads, stability and because linux gives me greater flexibility and options.

A little more background: The 15 workstation pc's are used to (through windows RDP over internet) connect to workstations running windows xp in another company to track assets via satelite. The setellite uplinks are connected to these pc's. Due to licensing etc rdp is the best option. (Again, not my decision). If i had it my way, I would create a usb over tcp/ip link and have our workstations rather comunicate directly to the hardware over the internet. I need to experiment a bit as well though, as this company can't tell me how fault tolerant the software is. Encryption is also another point to look at, but nothing that scares me.

As for the internet connection, we can easily aquire two or three more lines (since upgrading the existing one will be sensless as our upload wouldn't increase).

As far as active directory goes, the only thing active directory needs to do is allow users to roam pc's (I.E. Joe can log in to workstation 1 now and work and have his e-mail, but tomorrow another user is usingworkstation 1 and joe has to use terminal 5. After login he has his files and e-mail accesable.  The other thing that is important is that we need to keep log of who logs in where and when.  For security and working out the guys' pay.

So far, going virtual on a new linux platform sounds like it could do the trick. I could route three internet lines into the linux box acting as the gateway/firewall/dhcp/dns and have windows 2000 just take control of active directory, no?

As far as downtime goes, I can considerably decrease response time by buying double of the same motherboards, spare routers and keep them configured same as the ones in use so that in an emergency, we have little to configure if something needs to get replaced. Nice thing bout linux is that its somewhat hardware independent compared to windows. (Lol, the thought of moving windows 2000 to newer hardware had crossed my mind. Ouch)

Once again, Thank you guys for your replies.

P.S. Isn't downtime something I could solve by running a cloud??

---

### Post by tlsarles on 2010-02-03
you could decrease downtime by clustering, but the costs involved are pretty substantial to do it right, as you would want some sort of an iSCSI SAN most likely.

Again, for your internet connection I'm going to recommend some used Cisco gear. They support HSRP (Hot Standby Router Protocol) so that if one fails, the other will step in and keep chugging transparently. Not to mention QoS with regards to your VoIP and whatnot. Also the ability to make access lists, if you only want some hosts to be able to get online, or use certain protocols.

As for the roaming profiles feature, I'm not aware of a good way to do this under linux. Not saying it can't be done.... but... I would keep the w2k box around as a VM on your new hardware. VMware's converter tool makes it very easy to transfer your physical machine to a VM on an ESX host

---

### Post by R.Bucky on 2010-02-03
If all that you need is remote access for your clients, why not configure a VPN on Ubuntu server and go virutal? I used likewise-open for AD authentication on my SBS 08 network without problem ([http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/](http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/)). Also, consider ClearOS as an MS domain controller replacement. It is based off CentOS and will be even better when Samba4 comes out.

---

### Post by tr333 on 2010-02-04
For joining AD domains, you might want to look at [Likewise Open](https://help.ubuntu.com/9.10/serverguide/C/likewise-open.html).  I've successfully used it in the past to handle domain logins on ubuntu clients and for AD-authentication for DekiWiki (running on Ubuntu Server).  Also check out the [Ubuntu Server Guide](https://help.ubuntu.com/9.10/serverguide/C/index.html) for other server how-to's.

As an alternative to Ubuntu, take a look at [ClearOS](http://www.clearfoundation.com/Software/overview.html) (formerly ClarkConnect) for a Linux server/gateway.  It appears to have (most of?) the features that you require, and I would think it's easier to manage than Ubuntu for a non-linux admin.

---

### Post by Demented ZA on 2010-02-04
> **R.Bucky said:**
>  If all that you need is remote access for your clients, why not configure a VPN on Ubuntu server and go virutal? 

If by going vpn, do you mean connect our pc's to the pc's on the remote network? Unfortunately, the company hosting the tracking hardware doesn't want that for security reasons.


> **R.Bucky said:**
>  I used likewise-open for AD authentication on my SBS 08 network without problem ([http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/](http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/)). 

Well I think thats something i'm definately going to read up on. We have very basic needs for AD and if it were up to me, I wouldn't even use active directory. I'm more of a linux person. 

> **R.Bucky said:**
>  Also, consider ClearOS as an MS domain controller replacement. It is based off CentOS and will be even better when Samba4 comes out.

Well that might work, however, Ubuntu is a South African product and our company is South African as well. Its a lot easier to sell my peers on linux if we keep close to home. It makes it a little more familliar and takes some of the scare factor out of it.
So in this case, we prefer to stick to ubuntu.

Thanks a lot for your input. I'm going to start drawing up a proposal with what I've learned here. 

(Sigh, paperwork :-( ... )

---

