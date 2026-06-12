---
title: "Cloud platform"
date: 2009-09-23
forum: Server Platforms
---

### Post by epsolon77 on 2009-09-23
Please correct my terminology which I am sure I am not getting correct.

I run an IT department that currently has about 10 separate servers hosting their own operating system on a 1 to 1 ratio.  One OS to one box.  I would like to bind all these disparate hardware platforms together into an operating cloud, that I could build or destroy virtual instances on as needed.  The main advantage would be that I could add or remove a hardware device for repair, service or upgrade without taking any virtual machine offline.  Anyone have any idea's? I would be even happier if they were GNU.  Thank you.

---

### Post by dragos2 on 2009-09-24
> **epsolon77 said:**
> Please correct my terminology which I am sure I am not getting correct.

I run an IT department that currently has about 10 separate servers hosting their own operating system on a 1 to 1 ratio.  One OS to one box.  I would like to bind all these disparate hardware platforms together into an operating cloud, that I could build or destroy virtual instances on as needed.  The main advantage would be that I could add or remove a hardware device for repair, service or upgrade without taking any virtual machine offline.  Anyone have any idea's? I would be even happier if they were GNU.  Thank you.

Eucalyptus.

---

### Post by scorp123 on 2009-09-24
> **dragos2 said:**
> Eucalyptus. +1 !
[http://en.wikipedia.org/wiki/Eucalyptus_(computing)](http://en.wikipedia.org/wiki/Eucalyptus_(computing))

[http://open.eucalyptus.com/](http://open.eucalyptus.com/)

---

### Post by openfly on 2009-09-24
Redhat offers a virtualization solution...

but most of the business world relies on Virtual Infrastructure.  XEN hasn't quite caught up to VMWare yet on that front.

I'd look into shelling out the cash for a VI4 environment.  You'd probably be glad you did.

BUT!

I will be starting another thread soon on this topic.  I do a lot of cloud work myself ... on the automation of config management and provisioning.  As a result I purchased a dl585 recently... and got 2 more along with it as a bonus.

SO!  I am probably going to very shortly host a Virtualization hackathon at NYC Resistor.  I'll need a list of different virtualization solutions to try out.  I'll post results here when done.

---

### Post by epsolon77 on 2009-09-24
> **openfly said:**
> Redhat offers a virtualization solution...

but most of the business world relies on Virtual Infrastructure.  XEN hasn't quite caught up to VMWare yet on that front.

I'd look into shelling out the cash for a VI4 environment.  You'd probably be glad you did.

BUT!

I will be starting another thread soon on this topic.  I do a lot of cloud work myself ... on the automation of config management and provisioning.  As a result I purchased a dl585 recently... and got 2 more along with it as a bonus.

SO!  I am probably going to very shortly host a Virtualization hackathon at NYC Resistor.  I'll need a list of different virtualization solutions to try out.  I'll post results here when done.
Excellent info.  Please keep me posted!

---

### Post by scorp123 on 2009-09-24
> **openfly said:**
>  Redhat offers a virtualization solution... Which vendor doesn't?

> **openfly said:**
>  XEN hasn't quite caught up to VMWare yet on that front.  Oh really?
[http://www.citrix.com/English/ps2/products/feature.asp?contentID=1686939](http://www.citrix.com/English/ps2/products/feature.asp?contentID=1686939)

Especially the side-by-side comparison is interesting. :)

> **openfly said:**
>  I'd look into shelling out the cash for a VI4 environment.  You'd probably be glad you did.  VMware sucks. I'd rather go with XENserver (free!) or with SUN (more choice) ...

Sun VDI3 - current "stable" release:
[http://wikis.sun.com/display/VDI3/Home](http://wikis.sun.com/display/VDI3/Home)

Sun VDI 3.1 - "Early Access"; to be released in November:
[http://wikis.sun.com/display/VDI3dot1/Home](http://wikis.sun.com/display/VDI3dot1/Home)

VDI 3.1 is interesting as it supports VMware, Hyper-V and VirtualBox (yes, VirtualBox can be used on servers too if you do it right) as hypervisor backends.

> **openfly said:**
> I'll need a list of different virtualization solutions to try out.  I'll post results here when done.

Have fun :D

---

### Post by openfly on 2009-09-24
It's interesting when you look at needs of medium and small businesses compared to enterprise businesses.

VMWare dominates in enterprise for several reasons. 

1.  It was there first

2.  Vendor Partnerships.... VMWare is hooked into partnerships with so many solution providers that sometimes the solution providers are handling the support contracts for the clients in place of VMWare.  That's to say nothing of the "supported environment" problem.  VMWare is considered a supported environment for a number of industry wide utilities that are now somewhat impossible to phase out or replace either due to a lack of a competitor in the market or just complexity and cost of integrating a new solution into the enterprise policy framework.

3.  VMWare still has some tricks up its sleeves that others don't.  The new API access on VI4 is allowing people like Cisco to develop and sell "soft switches" such as the Nexus 1000V.  This stuff is fairly cool.  Also the complexity of cluster and datacenter management options are continuing to increase.

4.  Superstructures... VMWare is just the base for integrating a number of major industry applications... such as HP SA ( formerly Opsware ). 

So while XEN is progressing, and Citrix is certainly capable of carving out a niche in the small to medium business market... there are still some forces at play that will continue to provide VMWare with an upper hand with bigger fish for years to come.

That being said, free is nice... and for small businesses and under budgeted IT depts XEN is definitely growing into very real option.  I know that plenty of people even in VMWare shops run XEN on their workstations for prototyping builds and dev environments.

Diversity is good.  Open Source is good.  Free, is always good.

But finding the right tool for the job is priceless.  Regardless of what that tool is.

PS thanks for the list... Highly Appreciated.

---

### Post by scorp123 on 2009-09-24
> **openfly said:**
>  VMWare dominates in enterprise for several reasons ...  That is changing though. I have seen several shops --some in the "Enterprise" category-- abandon ship especially after last year's disaster with those horrible and badly tested VMware patches that prevented VM's from coming back up again. The other problem is their prices. Yes I know: the really super-large shops won't care if they have to dish out 30k for VMware licenses, they spend at least 10 x as much on the rest of the infrastructure. But still ... there are more and more voices saying that VMware is getting too expensive and that VMware should reconsider their price policies "or else ... "

I'm all for "or else" :D  and I hope that VMware's prices stay where they are because this is creating opportunities for other things. 


> **openfly said:**
>  3.  VMWare still has some tricks up its sleeves that others don't. Such as? VMware's money-maker trick "VMotion" (let's face it: it is THE killer feature that VMware has!) is by no means alone anymore. XENserver has "XENmotion".

And there are even free + opensource "VMware Clones" such as ProxMox that implement this if you configure its hosts into a cluster:
[http://www.proxmox.com/cms_proxmox/en/products/proxmox-ve/proxmox-ve-startseite.html](http://www.proxmox.com/cms_proxmox/en/products/proxmox-ve/proxmox-ve-startseite.html)

@OP ... maybe you want to read this?

"KVM & OpenVZ Virtualization And Cloud Computing With Proxmox VE"
[http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve](http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve)

ProxMox is now at version 1.3 (the article above was about an older version) and it's completely free + opensource (licensed under the GPL v2)

> **openfly said:**
>  Citrix is certainly capable of carving out a niche in the small to medium business market Huh? Last time I checked Citrix XenServer was clearly an "Enterprise" product. And it was exactly there where I see it making progress. Small to medium market would more be the domain of opensource XEN, KVM, ProxMox, and probably Hyper-V in the large number of Microsoft shops where the admins don't know or don't want to know about anything else.

And Microsoft Hyper-V clearly should not be considered "Enterprise ready" as this article demonstrates:

"Ramming Microsoft down IT's throat"
[http://infoworld.com/d/hardware/ramming-microsoft-down-its-throat-868](http://infoworld.com/d/hardware/ramming-microsoft-down-its-throat-868)

The funny thing here is that Microsoft is celebrating "a brand new feature: live migration ... "  Yeah right. LOL. The only thing that's missing is the claim that they invented it (like they "invented" TCP/IP and the Internet ...) ...  :D
.
.
.
.

---

### Post by openfly on 2009-09-24
Heh, I dunno what planet you are living on but I haven't seen a single enterprise deployment of citrix xen server.  And until recently I was a professional services consultant jumping through a lot of the enterprise world.  VMWare is openly acknowledged as having something like a 99% market share.

Anyways... I like Xen.  It's good stuff.  I hope it gets better and better.

Also I like how you ignored the mention of the cisco nexus 1000v... this is a BIG attractor to vi4.  Xen doesn't have a virtualized switching solution out yet that will allow network management to be returned to the network ops teams.  That would be a very large barrier for them to hurtle when competing with VMWare.

But not the largest by far.  The biggest is XENserver not being a "supported environment" by a host of applications.  That will kill them dead in the water in most places.  And real enterprise... as in rolling out 10000 baremetal systems enterprise doesn't exactly change directions at the drop of a dime.  I decision to adopt citrix would take years to roll out.  And they have literally not even been around long enough to be adopted by an enterprise organization.

I'd also be interested in whether or not there's any Federal adoption.  Most of the open standards that exist and are adhered to in technology are the direct result of Military standardization.  If they aren't being adopted federally many enterprise organizations would be loathe to adopt them themselves.

No one wants to be first in the commercial world, but federal is always willing to burn some tax payers money on developing some standards to meet their use case.

---

### Post by scorp123 on 2009-09-24
> **openfly said:**
>  Heh, I dunno what planet you are living on but I haven't seen a single enterprise deployment of citrix xen server.  Europe :D

> **openfly said:**
>  VMWare is openly acknowledged as having something like a 99% market share.  So is Microsoft .. but us Linux users we don't really care, right? :D

> **openfly said:**
>  Anyways... I like Xen.  It's good stuff.  I hope it gets better and better.  Yes, let's hope Citrix doesn't screw it up. Such corporations certainly have a talent for that ... 

> **openfly said:**
>   Xen doesn't have a virtualized switching solution out yet that will allow network management to be returned to the network ops teams.  Solaris 10 or OpenSolaris 2009.06 + Sun CrossBow + Sun xVM (Sun's version of XEN running on their Solaris kernel). Taddaaaa. Done. :D

I did not ignore what you said. I just thought "Oh well - let's not start an argument about that ..." :D ... But virtualised network switches isn't that new for me. Solaris + OpenSolaris can do that since at least early 2007 (when I had "Early Access" to it) and the technology is even opensource.

So if I really really want virtualised network switches and what not on a XEN-like environment I can easily stick to my SUN stuff. No problem. :D

[http://en.wikipedia.org/wiki/OpenSolaris_Network_Virtualization_and_Resource_Control](http://en.wikipedia.org/wiki/OpenSolaris_Network_Virtualization_and_Resource_Control)
[http://opensolaris.org/os/project/crossbow/](http://opensolaris.org/os/project/crossbow/)
[http://blogs.sun.com/droux/entry/crossbow_for_cloud_computing_architectures](http://blogs.sun.com/droux/entry/crossbow_for_cloud_computing_architectures)
[http://blogs.sun.com/shri/entry/crossbow_integrated_in_solaris](http://blogs.sun.com/shri/entry/crossbow_integrated_in_solaris)
[http://www.c0t0d0s0.org/archives/5355-Upcoming-Solaris-Features-Crossbow-Part-1-Virtualisation.html](http://www.c0t0d0s0.org/archives/5355-Upcoming-Solaris-Features-Crossbow-Part-1-Virtualisation.html)


> **openfly said:**
>  That would be a very large barrier for them to hurtle when competing with VMWare. 
[http://blogs.sun.com/droux/entry/private_virtual_networks_for_solaris](http://blogs.sun.com/droux/entry/private_virtual_networks_for_solaris)
[http://opensolaris.org/os/community/xen/](http://opensolaris.org/os/community/xen/)

> **openfly said:**
>  The biggest is XENserver not being a "supported environment" by a host of applications.  That will kill them dead in the water in most places. Maybe so. Maybe not. We will see. And even if: There is still the opensource XEN variation and its offsprings such as Sun xVM.

> **openfly said:**
>   And real enterprise... as in rolling out 10000 baremetal systems enterprise doesn't exactly change directions at the drop of a dime. Don't underestimate the power of stupid managers :D  ... If the bribe ^H ^H ^H ^H  ... "incentive" is high enough they will even sell their mothers to the highest bidder, let alone their IT ...

But yes you are right: In a "normal" environment this should hardly happen and any change --if ever-- would take place veeeery slowly. If at all.

> **openfly said:**
>   I decision to adopt citrix would take years to roll out.   Depends. Migrate existing servers (where all the money is!!): No chance ever they will allow you to touch that, yes. 

But if the shop or the upper brass is fairly new (new managers always have the tendency that they want to "change" and "improve" things even though their IT guys didn't ask them to ....) or if they did not yet formalise any final decisions on their virtualisation platform and if their IT landscape is heterogenous anyway then you might easily convince them to give new solutions a try ... Been there, done that.


> **openfly said:**
>  No one wants to be first in the commercial world  Very true. But sometimes you get lucky, you can land one hit and then use that one as reference for all the others that are willing to follow.

---

### Post by openfly on 2009-09-24
Heh, sun has some great stuff... the biggest grip I've hear parroted across the board about sun solutions is that sun may stop supporting their solutions at random if they decide they internally want to put forward some other solution for the same task that suddenly won out on the inner political struggle... apparently this happens all the time... <cough> package management </cough>.

I've not had an opportunity to play with sun's xVM stuff too much, but I am looking forward to it.  It's odd how poorly sun does in the market when their solutions are so freaking robust.

I mean not since DEC was still in business have I seen a company push out systems with 10 year shelf lives at their deployment locations.

Sometimes I'm a fan of sun.  But other times I'm left realizing they are their own worst enemy.

---

### Post by epsolon77 on 2009-09-24
Do any of these solutions that are being thrown out here allow for auto creation on kill of an instance dynamically?  

In addition to virtualizing my servers, I would love to virtualize my desktops as well.  Now I could create 25 separate, constant running instances, but it would be way cooler and more economical if each session were created on the fly from a standard iso, or some kind of snapshot.  For this kind of setup I would much rather have something more akin to LTSP, with PXE boot systems and "dumb" terminals in front of the users.  We extensively use multi monitors, and that is difficult in a Microsoft terminal server environment so that case would be out.  For the record, I have little hope of switching to a full linux shop until our management database will work cross platform, and after dealing with their support I think the answer to that is close to never...

---

### Post by scorp123 on 2009-09-24
> **openfly said:**
> ... the biggest grip I've hear parroted across the board about sun solutions is that sun may stop supporting their solutions at random if they decide they internally want to put forward some other solution for the same task that suddenly won out on the inner political struggle...  Very true, unfortunately ](*,)

I'm still somewhat mad at them for killing off "Sun xVM Server" after the first two "Early Access" releases. That product was soooo promising. It was basically OpenSolaris + XEN + nice looking web interface. And so easy to use. Buggy as hell though but OK ... it was an "Early Access" release. I was so looking forward to get the final product ...

And then they all of a sudden announced that they cancelled the product and instead chose to go forward with their "OpsCenter" management thing. Ohhh maaan. #-o


> **openfly said:**
>   It's odd how poorly sun does in the market when their solutions are so freaking robust.  Let's face it: their marketing is total BS. Sad but true.

> **openfly said:**
>  Sometimes I'm a fan of sun.  But other times I'm left realizing they are their own worst enemy. Oh yes, very true.

---

### Post by openfly on 2009-09-24
> **epsolon77 said:**
> Do any of these solutions that are being thrown out here allow for auto creation on kill of an instance dynamically?

Read into what VMotion and XENMotion do.  Maybe that's what you mean here but are having trouble expressing it... otherwise...

There's a perl api to VMWare that allows you to do things like start and stop VMs... probably can deploy a vm from template without too much trouble... mind you customization of systems can be a bit limited in VMWare.  Things like new SID generation may not be possible.  The alternative is to just spin off a new template that hit a kickstart or autoyast instance that could autobuild you whatever you are trying to build... that could be a bit intensive to layout for more granular system customization.

The sort of utility you are looking for would be available in much more expensive enterprise automation solutions but I don't think there's something on the level you are looking at.  

> **epsolon77 said:**
> 
In addition to virtualizing my servers, I would love to virtualize my desktops as well.  Now I could create 25 separate, constant running instances, but it would be way cooler and more economical if each session were created on the fly from a standard iso, or some kind of snapshot.  For this kind of setup I would much rather have something more akin to LTSP, with PXE boot systems and "dumb" terminals in front of the users.  We extensively use multi monitors, and that is difficult in a Microsoft terminal server environment so that case would be out.  For the record, I have little hope of switching to a full linux shop until our management database will work cross platform, and after dealing with their support I think the answer to that is close to never...

VMWare's answer to this was called Ace I believe... and it's not integrated into VI4... but it seems like in future realses it will end up an integrated product.

The idea is you get a thing like a usb key to boot a virtual instance off of.  Great for giving people like consultants access to the resources they need for the time that they need it without having to provide them with a laptop.  ( not that that would ever really work in the real world ) but it makes things easier in some cases regardless.

There are a number of "dumb terminal" style solutions for various virtualization products.  Citrix was banking on those 3 or 4 years ago as a revenue stream.

---

### Post by scorp123 on 2009-09-24
> **epsolon77 said:**
>  Do any of these solutions that are being thrown out here allow for auto creation on kill of an instance dynamically?   Sun VDI can do that. BUT --and that's a big "but"-- to really make full use of this you'd have to deploy "Sun Ray" ThinClients. And those things only really make sense if you're willing to go the "Server based computing" route as envisioned by Sun.

> **epsolon77 said:**
>   but it would be way cooler and more economical if each session were created on the fly from a standard iso, or some kind of snapshot.  Yes, Sun VDI works like that. You have a template and you define how many instances may ever run at the same time, and what the initial state of each freshly cloned instance should be. It can be "running" or "powered off". So you'd have a template, you set the max-size to 25, and voila: 25 instances that are powered off. And you can set idle timeouts and what not so that idle instances are powered down and "recycled" (either "reset to snapshot" or "destroy" or "reuse").

> **epsolon77 said:**
>  For this kind of setup I would much rather have something more akin to LTSP, with PXE boot systems and "dumb" terminals in front of the users.  Hmmm ... Did you ever try Sun Rays? Sun calls it "ultra-thin" and that's no joke -- those things really are dumb as a brick. There is no data, no logic, nothing whatsoever ever stored on them. And they only consume around 4W of power. And you can "hot-desk" between the terminals, e.g. the session goes wherever you login. You left your session running in Chicago but now you're in your Paris office? No problem. Just log in and your session will come to you.

> **epsolon77 said:**
>  We extensively use multi monitors, and that is difficult in a Microsoft terminal server environment  Sun Rays in "multi-head" mode:

[IMG]http://blogs.sun.com/thinkthin/resource/6head-angle.jpg[/IMG]

Those are very old "Sun Ray 1" terminals in that picture. The present-day top-of-the-line model "Sun Ray 2FS" has 2 x DVI connectors and can do 1920 x 1200 max.

Sun Ray "multi-head" is limited to 16 Sun Ray terminals within the same setup. So with the Sun Ray 2FS you'd get 16 x 2 screens = 32 screens. All controlled by one keyboard and one mouse.

[http://wiki.sun-rays.org/index.php/Multihead](http://wiki.sun-rays.org/index.php/Multihead)
[http://blogs.sun.com/ThinkThin/entry/multihead_sun_rays](http://blogs.sun.com/ThinkThin/entry/multihead_sun_rays)

Sorry for advertising Sun here (I admit I work for one of their partners ...)  ... to each his own :D

---

### Post by openfly on 2009-09-24
Sun rays were cool... I just wish they hadn't killed the java ibuttons... those things were the hotness.

---

### Post by dragos2 on 2009-09-25
Scorp has provided you with great info but dudes (op and others) don't
mix things up(op): you asked about cloud but I think you really want
virtualization ?

A cloud is an evolved virtualization, but they are not the same.

The only viable cloud solution that I know which is more than a framework 
is Eucalyptus.

When speaking about hypervisors Citrix Free Xen Server is to be taken
into consideration, I am running it in production, the only thing it lacks
(now) is remote iso boot.

---

### Post by openfly on 2009-09-25
Uhm opsware ( now HP server automation ) would provide the functionality necessary to deploy a cloud.  In fact many cloud providers use it.  But it's incredibly expensive.

---

### Post by epsolon77 on 2009-09-30
Expensive is a problem given that my funding is almost non existant.  I think I will end up testing Eucalyptus here before long, I still have to craft a chat system first.  Of course given the current state of the economy, my IT budget is pretty much non existant.

dragos2, you make a good point about the flexibility in the topic.  I know I don't have a compleate understanding of clouds, virtualized systems and all the rest of this large topic, my initial question was about clouds as I understand them.  Just to make sure I am on the right page I will describe what my end product would look like.

I currently have 6 actual servers each on their own machine.  I am not using all of the processing provided by any one machine.  I would like to take all 6 physical machines and place a software piece on it so that their resources would be shared.  Thus the 6 functional machines would not load on a specific physical machine, which means if a physical machine fails, we would not lose the function on that physical machine, only the extra resources it would provide.  To the best of my knoladge this is a cloud system.

Now I would also like to add resources on the fly by adding another physical hardware to the system, and I would like to be able to add virtual machines to the cloud on the fly.  Say my boss calls me at 2 am and asks if I can set up an internal website for the next 6 months, I don't have to get a new physical machine to fill his need, just create a new instance and off it goes.

Another limit is that we are currently using Microsoft OS's on all our servers.  I can't get away from this at the current point in time, in part because I can not set up 2 systems running concurrently because of lack of resources.  With a cloud setup, I could change our enviorment much easier and cheaper.

The part about virtualizing our desktops was a pipe dream, but ya never know what's out there so it doesn't hurt to ask.  Part of my long term goal for our IT is to turn our desktops into all server based computing on a PXE boot system.  I can't use Microsoft Terminal Server for this because we use 2 monitors on every computer.  There are ways to get some functionality out of 2 monitors on terminal server, but I know that field well enough to know it really doesn't work.

I was able to set up LTSP to fuction almost exactly as I'd need it, except for one software program that can not function on a linux base because it required (Yes past tense) dotnet 1.1 and IE.  Now about 2 months ago they upgraded to using dotnet 2.0 which has better wine support, but I have not had the time to retest this.  I figured if we had a cloud setup already for my servers, what's the difference in having desktops hosted and viewed on a person's workstation, that could also be part of the cloud?  While I know the awnser is that there is a big difference, it is still close enough to warrent the question being asked.  I know it would be easy enough to have each windows install run on the cloud with a person logging in remotely through their workstation, but I think I still have a problem with how 2 monitors would work.  You would either span them, use 1 monitor or buy expensive software (upwards of 500 per user x 50 or more users = WAY over budget) to allow you to use both monitors speratly.  

Please everyone, shoot holes in my concept here, I am looking for criticism and advice.  Be brutal, I can take it.

---

### Post by windependence on 2009-10-01
Scorp needs to stop spreading FUD about VMware. Simple solution - FREE

ESXi - FREE, and before you say it, yes, VSphere client is free also, download from the server once it's up via http.

Veeam - FREE FastSCP tool moves files between data stores with a GUI. Yes, not running but it's just a matter of time before someone comes up with a free VMotion clone, and so far we have been able to live without it in an environment like the OP has. He could do what he wants to do on 2 servers and cluster them.

VMware won't recognize your storage controller? Set up a FREE NAS server and connect using iSCSI or NFS. I use FreeNAS, but you can even use these little NAS boxes they sell for under $200. You have to start thinking outside the box.

Xen? Give me a break. KVM is messy for quick set up, no remote GUI, just not ready for production yet. VBox? Not bare metal, sorry, not for me. VMware blows them all away. I am doing nothing but setting up TOTALLY FREE Vmware servers for small business right now, and I have more work than I can handle. Like Openfly, I have never seen ANY of the other vendors deployed in any fortune 500 I have worked for. That includes IBM.

To the OP: Think outside the box, and learn all you can about virtualization befiore you can move on to "cloud" computing which is really nothing "new".

-Tim

---

### Post by epsolon77 on 2009-10-01
windependence thank you for your advice.  I am looking into as much of these technologies as I can while I have other projects on my desk.  I'm glad you mentioned iSCSI and NAS systems.  The before I even think about deploying any virtualized or cloud system I will have to have my iSCSI system up and running and for reasons unrelated to the virtual system I am hoping to set up.  

You mentioned that VMware is free.  As I understand it, the free VMware package does not include the ability to have multiple hardware platforms working together to run a pool of virtual servers, which is primarily what I am hoping to achive.  Please correct me if I am wrong.

---

### Post by scorp123 on 2009-10-01
> **windependence said:**
> Scorp needs to stop spreading FUD about VMware.  Yeah, right. LOL

> **windependence said:**
>  ESXi - FREE But highly limited hardware compatibility. And from that point of view it sucks.

> **windependence said:**
>  it's just a matter of time before someone comes up with a free VMotion clone [www.proxmox.com](www.proxmox.com) ... Free + OpenSource. KVM and OpenVZ, so you get two hypervisors in one product. And ProxMox can be clustered and it can move virtual hosts between machines. For Free, as in "really free and open source". No obscure closed-source app with limited hardware compatibility needed here.

Then there is Xen. It can do that as well.

Free VMotion clone in ESXi?? Forget it. Not going to happen. VMware will sue the hell out of anyone trying to create such a thing.

> **windependence said:**
>  Xen? Give me a break. And that would be ... why? :)


> **windependence said:**
>   KVM is messy for quick set up, no remote GUI, just not ready for production yet. ProxMox. See above. KVM wrapped up in a nice web GUI.

> **windependence said:**
>  VMware blows them all away. If you use Sun VDI (as described in my earlier postings) to deliver desktop VM's to Sun's "Sun Ray" ultra-thin clients then VMware ESX or ESXi only make sense if you use Windows only. VMware can't deliver OpenSolaris or Linux VM's (it can start them, yes ... but the screens will remain black) to those devices. Cheapo VirtualBox can. Now, the nice thing with Sun's VDI is that you can mix and match the hypervisors. So you can use both if you wanted to, e.g. VMware to host the Windows VM pools and VirtualBox for the Linux VM pools.

> **windependence said:**
>  Like Openfly, I have never seen ANY of the other vendors deployed in any fortune 500 I have worked for. That includes IBM.  You're working on the wrong continent.

It's the same with those discussions in US media one can read about "Linux adoption -- never going to happen?" and what not. Here in Europe those discussions are long over and it's already happening and Linux is widely being adopted in lots of places while the USA are still just talking, blogging, writing and whining about this.

When I tell US guys that Linux is in wide use over here I am usually met with the same disbelief like in this thread where I dared to claim that not everyone is using VMware ...

Guys. Seriously. Travel more, yes? :D

---

### Post by scorp123 on 2009-10-01
> **epsolon77 said:**
>  You mentioned that VMware is free. VMware ESXi is ... but it's a bit limited in its abilities.

VMware ESX (please note the missing "i" here at the end!) definitely is NOT and costs a fortune.

> **epsolon77 said:**
>  As I understand it, the free VMware package does not include the ability to have multiple hardware platforms working together to run a pool of virtual servers, which is primarily what I am hoping to achive. "windependence" can surely correct me on this, but what you describe sounds like VMware's "vSphere" where you can put servers into pools and move VM's between them. That feature isn't free as far as I know.

---

### Post by openfly on 2009-10-01
ESX has a dominating control of the enterprise market and you won't see permeation in that market for at least the next several years.  Regardless of how good the competitors are.  And virtual smart switches are now in VMWare only, further crushing the competition.  That's on a global scale.  Most enterprise organizations deploy the same stuff across the globe.  So yeah, VMWare still dominates in europe.  I know that for a fact.

That being said, the quad and six core beasts people are buying today can actually run VMs fairly well.  It would not surprise me if the rate of development in the Xen community accelerated as adoption rates among home  small business and research users begins to climb.

Xen is a fine bit of software, but so far it's been unable to outpace VMware in feature or market growth.  

It may yet in the future prove to be the dominant hypervizor but for now it is not, and shows no signs of taking that crown soon.

All that being said, ESX has some crazy hardware requirements.  It pretty much expects an enterprise environment.  Not many people are willing to go out of their way to get real server gear and real disk storage solutions for their virt environment.  Especially with cheap sata storage in the terabytes and home pc's being fast enough to spin up 20 machines easy.  

Xen is by far the most economical solution for a functional yet limited virtualization environment.  

I could see a lot of little mom and pop IT shops looking to leverage it's capabilities.

---

### Post by scorp123 on 2009-10-01
> **openfly said:**
> And virtual smart switches are now in VMWare only "CrossBow" in Solaris. We already discussed that.

> **openfly said:**
>  So yeah, VMWare still dominates in europe.
Maybe so. But it's by no means "alone" anymore. VMware's competitors are making lots of progress .... and for us the users that's good. It means we get more choices.

We already have an ugly monopoly in the desktop OS market ... we don't need another one in the virtualisation market.

> **openfly said:**
>  All that being said, ESX has some crazy hardware requirements.  It pretty much expects an enterprise environment. True. And your hardware better be certified if you plan to run this in your server room or else you will be throwing a lot of money out of the window. My favourite server in that regard is Sun's X4600M2 .... 8 x Quad-Core CPU's and now up to 512 GB RAM. It's certified to run VMware and it runs it extremely well .... if you can afford it that is.

Last time I checked other vendors had similar offerings ... but not in a 4RU form factor.

---

### Post by openfly on 2009-10-01
scorp it seems to me these days that if you aren't a sun shop you are an HP or IBM shop.  There really isn't much else.

---

### Post by scorp123 on 2009-10-01
> **openfly said:**
>  There really isn't much else. Did you omit Dell on purpose? :D

I find their servers are very very "plasticky" if you know what I mean. But they too offer VMware-certified hardware. But I have not had my hands on Dell hardware in a long time, so no idea how good or bad those boxes are.

---

### Post by chrisjsmith on 2009-10-01
I don't get why people don't like VMware.  Are you afraid of paying for something?  My experience:

a) We're using VMWare ESX/vSphere/vCenter on Dells with a FC SAN up the back.

b) We probably have a bigger deployment than most (2 sites, 100 VMs per site).  We do this in one 42U per site.

c) We have virtual everything (servers, network infrastructure, monitoring, the lot).

d) we run CentOS, Ubuntu, Windows 2003, Windows 2008 (predominantly the latter)

It is expensive compared to raw kit but considering...

1. it saves on provisioning costs.  we just clone VMs, do the mac change and newsid them and they're online.
2. it saves on rack space.
3. if something fails, we can shift the load onto other boxes without changing the software configuration.
4. we can change the hardware without taking ANYTHING offline.
5. we rarely go to the data center (once a quarter at average).

All that makes it cheaper than real servers.

We could probably do better in respect to rack space with blades but we don't need to.

Xen/Sun goes nowhere near this space.  It's VMware circa 2002.

That is all I have to say.

---

### Post by epsolon77 on 2009-10-01
> **scorp123 said:**
> Yeah, right. LOL

 
It's the same with those discussions in US media one can read about "Linux adoption -- never going to happen?" and what not. Here in Europe those discussions are long over and it's already happening and Linux is widely being adopted in lots of places while the USA are still just talking, blogging, writing and whining about this.

When I tell US guys that Linux is in wide use over here I am usually met with the same disbelief like in this thread where I dared to claim that not everyone is using VMware ...

Guys. Seriously. Travel more, yes? :D

I don't want to detract from the wonderful discussion we have on virtualization here, but I did want to broaden your view on US companies and going linux full out.  You are dead on that it is possible, but it is much more possible outside the US.  Software development in the US is done almost soley on Microsoft OS's.  This is very very unfortunate.  Also many US vendors do not strive to go cross platform on their apps.  A great example is my office's desktops.  I've made 90% of our functionality work through WINE and MONO, but our customer data reporting system REQUIRES dotnet framework 1.1 and MsSQL.  Most of the non american software I see does not force users into a software choice, wherease here it seems to be the norm to force users into restrictive systems.  Personally I am FED UP with it and have been throwing all the weight I have in this company behind something that won't charge us hundereds per liscence, threaten us with law suits so we can use a crappy system.

I have not been out of the country recently, but I have spoken with IT personnel outside the US and it does seem like many of the challenges I face to going open source are not issues.  ESPECIALLY how set in their ways our users are.  I had a PC with a dead hard drive used only to access the internet, and put a liveCD in as a temp fix, and no one would use it.  Even with Firefox sitting up there.  The menu bar was different so they wouldn't handle it.  Such a shame.  I'll keep wearing them down though!  At least the owners of the company see how much money we can save, and how much more productive our users can be on an open system because of projects like the one I started this thread to discuss.

---

### Post by scorp123 on 2009-10-01
> **chrisjsmith said:**
> I don't get why people don't like VMware.  Are you afraid of paying for something?   Well, let's face it: VMware isn't exactly "cheap". Sure, if you can afford all the licenses and really really need all the features ... go for it.

All I'm saying is: There are alternatives. Some are open source. Some are free. Some lack a few features VMware ESX obviously has (e.g. "VMotion"). It depends ultimately what the needs are. Not everybody needs every feature. Why throw money out of the window and pay for really expensive software if --maybe-- a less expensive or even free alternative could do the same?

I personally just find the notion "there is nothing out there but VMware" a bit silly. No insult intended here. Please: nobody get me wrong here, OK? It's just the same problem us Linux users face with e.g. Windows, e.g. some people out there act as if they were _forced_ to use Windows. Well ... they're not. There are alternatives. Same with VMware. If you _really_ need all the features plus the kitchen sink and if the price tags _really_ are no problem for you ... fine, go ahead.

But if any those things I just mentioned _is_ a problem for you --the most likely being money-- then it can't harm to know a few alternatives that might offer similar features? :)

> **chrisjsmith said:**
>  1. it saves on provisioning costs.  we just clone VMs, do the mac change and newsid them and they're online.
2. it saves on rack space.
3. if something fails, we can shift the load onto other boxes without changing the software configuration.
4. we can change the hardware without taking ANYTHING offline.
5. we rarely go to the data center (once a quarter at average). I am not 100% sure (and I'll admit that) but wouldn't any of the other virtualisation solutions offer these very same features too? Or at least most of them?

---

### Post by ForrestDean on 2009-10-01
Does Xen support 4 Quad Core processors?

---

### Post by dragos2 on 2009-10-02
I am still happy with Citrix FreeXenServer
[http://www.citrix.com/English/ps2/products/feature.asp?contentID=1686939](http://www.citrix.com/English/ps2/products/feature.asp?contentID=1686939)

It is a good stable bare-metal hypervisor with big compatibility list, it has good remote
administration - all free. Of course you need to pay for some extras but Citrix is
a pretty big company

[http://www.wolframalpha.com/input/?i=citrix%2C+vmware](http://www.wolframalpha.com/input/?i=citrix%2C+vmware)

so I would bet on Citrix's Xen in the next years.

---

### Post by openfly on 2009-10-02
> **scorp123]
Did you omit Dell on purpose?

I find their servers are very very "plasticky" if you know what I mean. But they too offer VMware-certified hardware. But I have not had my hands on Dell hardware in a long time, so no idea how good or bad those boxes are.
[/quote]

Heh yes I did.  They are the old navy of server sales.  They don't even have their own storage systems anymore.  And to be blunt they are just kind of wasting away to nothing.  The only people that buy dell are in academia, and failures of a feather tend to flock together if you get my drift.

[QUOTE=dragos2 said:**
> I am still happy with Citrix FreeXenServer
[http://www.citrix.com/English/ps2/products/feature.asp?contentID=1686939](http://www.citrix.com/English/ps2/products/feature.asp?contentID=1686939)

It is a good stable bare-metal hypervisor with big compatibility list, it has good remote
administration - all free. Of course you need to pay for some extras but Citrix is
a pretty big company

[http://www.wolframalpha.com/input/?i=citrix%2C+vmware](http://www.wolframalpha.com/input/?i=citrix%2C+vmware)

so I would bet on Citrix's Xen in the next years.

Citrix is lacking key functionality in datacenter virtualization and automation and is not yet on a level where it can compete with Sun and VMWare.  That may someday change, but it has not yet.  

That being said, Citrix provides some of the best end user virtualization and resource sharing solutions on the market today, and their work with Xen is progressing very well.  It will be interesting to see if they can compete with VMware and Sun in the future.

---

### Post by openfly on 2009-10-02
> **epsolon77 said:**
> I don't want to detract from the wonderful discussion we have on virtualization here, but I did want to broaden your view on US companies and going linux full out.  You are dead on that it is possible, but it is much more possible outside the US.  Software development in the US is done almost soley on Microsoft OS's.  This is very very unfortunate.  Also many US vendors do not strive to go cross platform on their apps.  A great example is my office's desktops.  I've made 90% of our functionality work through WINE and MONO, but our customer data reporting system REQUIRES dotnet framework 1.1 and MsSQL.  Most of the non american software I see does not force users into a software choice, wherease here it seems to be the norm to force users into restrictive systems.  Personally I am FED UP with it and have been throwing all the weight I have in this company behind something that won't charge us hundereds per liscence, threaten us with law suits so we can use a crappy system.

I have not been out of the country recently, but I have spoken with IT personnel outside the US and it does seem like many of the challenges I face to going open source are not issues.  ESPECIALLY how set in their ways our users are.  I had a PC with a dead hard drive used only to access the internet, and put a liveCD in as a temp fix, and no one would use it.  Even with Firefox sitting up there.  The menu bar was different so they wouldn't handle it.  Such a shame.  I'll keep wearing them down though!  At least the owners of the company see how much money we can save, and how much more productive our users can be on an open system because of projects like the one I started this thread to discuss.

That's a load of crap by the way.  The US has a hell of a lot more UNIX and UNIX-like server deployments than anything else.  The assumption that Microsoft is leading the server pack is based on a complete lack of understanding in the market.  

Lets think for a second.  

Solaris - Sun / Oracle, Pretty much every tech shop in america has at least one Solaris deployment.  Most people deploying oracle have sun equipment, and there are a number of Unix engineering teams that are completely sun shops.  Between Enterprise America and Federal Agencies Solaris has seen very large scale deployment for the past 20 years or so.

RedHat - RedHat, On the whole I have yet to see a major organization with more Windows servers than RedHat servers. 

SuSE - Novell, Thanks to Novell's domination of the LAN environment back in the early and late 90s, there are plenty of large organizations that still turn to novell to support their legacy environments and adapt some of those services for a new era.  E-Directory remains one of the most deployed and successful directory services in the world.  And for those that have worked with it, it's a fairly badass bit of code.

BSD, Not much talked about.  But you will find a hell of a lot of FreeBSD, or BSDi systems hiding in the dark recesses of any major organization.  Sometimes not even all of IT knows they are there, doing their jobs dutifully.  But the simple fact is they are.  And I run into them all the time.  Dust covered old servers long bought out from lease... just chugging away doing their thing until they die and get replaced.  Until a few years ago, many enterprise unix guys were FreeBSD or Solaris only.  Linux is still considered fairly juvenile on the enterprise playing field... largely because it is.  

Then let's look at windows...

   It's good for 2 things.  Active Directory and Exchange.  That's pretty much it.  Sure you'll see it all over an MIS wing, or in userland interfaces.  But the fact is, Windows server is purpose built for supporting windows apps.  It's impressive that Windows has made the headway it has in recent decades in getting a foothold in the server land, but i've seen the counts from major organizations and the number of Windows servers deployed pales in comparison to unixes. That's in the US.

   Gotta remember, UNIX has been around a long long time.  And there's been people using it since long before windows had a server at all.  Those deployments and the people maintaining them haven't really changed much over the years.  And, Windows is a fairly new entrant to the world of servers.

---

### Post by chrisjsmith on 2009-10-02
> **scorp123 said:**
> Well, let's face it: VMware isn't exactly "cheap". Sure, if you can afford all the licenses and really really need all the features ... go for it.

If you need it, you can afford the licenses.  There is little or no reason to use it unless you have a big chunk of kit.

> **scorp123 said:**
> All I'm saying is: There are alternatives. Some are open source. Some are free. Some lack a few features VMware ESX obviously has (e.g. "VMotion"). It depends ultimately what the needs are. Not everybody needs every feature. Why throw money out of the window and pay for really expensive software if --maybe-- a less expensive or even free alternative could do the same?

Agree, but for the pricing points involved, the open source solutions make little sense.  My point is that the open source stuff requires more work to get off the ground, meaning a greater expenditure in time.  Time == money therefore you might as well use VMware for which you can get commodity staffing for rather than handing down some hacked up software rig to "the new guy" when you leave.

> **scorp123 said:**
> I personally just find the notion "there is nothing out there but VMware" a bit silly. No insult intended here. Please: nobody get me wrong here, OK? It's just the same problem us Linux users face with e.g. Windows, e.g. some people out there act as if they were _forced_ to use Windows. Well ... they're not. There are alternatives. Same with VMware. If you _really_ need all the features plus the kitchen sink and if the price tags _really_ are no problem for you ... fine, go ahead.

My statement is that there is nothing but VMware so far.  In time I'm sure there will be.

> **scorp123 said:**
> But if any those things I just mentioned _is_ a problem for you --the most likely being money-- then it can't harm to know a few alternatives that might offer similar features? :)

The cost can always be offset against time, or you're not getting paid enough :)

> **scorp123 said:**
> I am not 100% sure (and I'll admit that) but wouldn't any of the other virtualisation solutions offer these very same features too? Or at least most of them?

They do to varying degrees.  With VMware you get the tools integrated and configured rather than having to build on top of what is there already to suit your needs.

---

### Post by chrisjsmith on 2009-10-02
I'm a fan of Ubuntu and open source software but you speak crap.

> **openfly said:**
> That's a load of crap by the way.  The US has a hell of a lot more UNIX and UNIX-like server deployments than anything else.  The assumption that Microsoft is leading the server pack is based on a complete lack of understanding in the market.

That might have been the case in 2000 but MS's marketing has been very aggressive and their products are a lot better than they used to be.  I've not seen an org for 5 years that ISN'T MS end to end.  We only use Linux to support stuff (ESX hosts, monitoring with zenoss etc etc).

> **openfly said:**
> RedHat - RedHat, On the whole I have yet to see a major organization with more Windows servers than RedHat servers.

From experience (with op revenue): Raytheon ($23bn), BAE (£18bn), UK MoD (£35bn), Microsoft ($60bn), QInetiQ (£1.3bn).

> **openfly said:**
> SuSE - Novell, Thanks to Novell's domination of the LAN environment back in the early and late 90s, there are plenty of large organizations that still turn to novell to support their legacy environments and adapt some of those services for a new era.  E-Directory remains one of the most deployed and successful directory services in the world.  And for those that have worked with it, it's a fairly badass bit of code.

I call ********.  I spent the last 10 years killing Netware installations because it's a pile of crap with no viable upgrade path.  Consolidation is what the last 10 years have been about.

> **openfly said:**
> BSD, Not much talked about.  But you will find a hell of a lot of FreeBSD, or BSDi systems hiding in the dark recesses of any major organization.  Sometimes not even all of IT knows they are there, doing their jobs dutifully.  But the simple fact is they are.  And I run into them all the time.  Dust covered old servers long bought out from lease... just chugging away doing their thing until they die and get replaced.  Until a few years ago, many enterprise unix guys were FreeBSD or Solaris only.  Linux is still considered fairly juvenile on the enterprise playing field... largely because it is.p

Apart from those who use it to host J2EE...  

> **openfly said:**
> Then let's look at windows...

   It's good for 2 things.  Active Directory and Exchange.  That's pretty much it.  Sure you'll see it all over an MIS wing, or in userland interfaces.  But the fact is, Windows server is purpose built for supporting windows apps.  It's impressive that Windows has made the headway it has in recent decades in getting a foothold in the server land, but i've seen the counts from major organizations and the number of Windows servers deployed pales in comparison to unixes. That's in the US.

Possibly in the US, but it's all Windows here in the UK.

On and you forgot SQL Server and Sharepoint....

> **openfly said:**
> Gotta remember, UNIX has been around a long long time.  And there's been people using it since long before windows had a server at all.  Those deployments and the people maintaining them haven't really changed much over the years.  And, Windows is a fairly new entrant to the world of servers.

Well 20 years ago it was...

Sigh.

---

### Post by openfly on 2009-10-02
> **chrisjsmith said:**
> I'm a fan of Ubuntu and open source software but you speak crap.



That might have been the case in 2000 but MS's marketing has been very aggressive and their products are a lot better than they used to be.  I've not seen an org for 5 years that ISN'T MS end to end.  We only use Linux to support stuff (ESX hosts, monitoring with zenoss etc etc).



They don't have products to enter most markets in IT / Industrial tech.  They literally CAN'T compete.


> **chrisjsmith said:**
> 
From experience (with op revenue): Raytheon ($23bn), BAE (£18bn), UK MoD (£35bn), Microsoft ($60bn), QInetiQ (£1.3bn).


Random stats without any context are random.

> **chrisjsmith said:**
> 

I call ********.  I spent the last 10 years killing Netware installations because it's a pile of crap with no viable upgrade path.  Consolidation is what the last 10 years have been about.



Netware died years ago.  True.  E-directory didn't.  It's still kicking *** and taking names.  In fact I've seen pleny of Active Directory deployments backended by E-dir.  It scales better than any other directory service.  On an unrelated note, I also still occasionally see I-chains systems in the market.  It's not like everyone uses siteminder... and while I-chains is still netware based last I checked... it's also fairly competent.

> **chrisjsmith said:**
> 
Apart from those who use it to host J2EE...  


zoof?

> **chrisjsmith said:**
> 
Possibly in the US, but it's all Windows here in the UK.

On and you forgot SQL Server and Sharepoint....


People use oracle.  MSSQL is only allowed to be used when it's the only option.  That's pretty much edict everywhere I've seen it deployed.

As for sharepoint... god such a revolting piece of crap.  Everytime I log into it, I get the feeling I'm in some alternate universe where up is down, left is right, and the worlds crappiest webapp is somehow deployed everywhere.  It's ******* wrong is what it is.  Some sort of bizarro world hell just for me.

> **chrisjsmith said:**
> 

Well 20 years ago it was...

Sigh.

Still is.  Find me a dev in corporate america that isn't a java dev.  Then find me one that isn't deploying their serverside apps to a unix box.  I say it's damned near impossible to.  

Just the way the cookie crumbles.

---

### Post by epsolon77 on 2009-10-02
> **openfly said:**
> That's a load of crap by the way.  The US has a hell of a lot more UNIX and UNIX-like server deployments than anything else. 

I am sorry that I did not make myself clear.  I assumed when we were talking about the US not implementing Linux we were referring to desktops, not servers.  The only reason why we have Microsoft servers is because they were in place before I came on, and I'm not about to cause downtime to switch OS's.  That's where the cluster comes in.  My issue with switching our desktops to Linux is the fact that most vendors here in America seem to be reluctant to support Linux or any type of cross-platform solution, like Java instead of ActiveX ect.

---

### Post by openfly on 2009-10-02
There's a lot of reasons not to roll linux as a desktop actually.  

Linux did not properly adopt GSSAPI, so there's no equivalent for SPNEGO based SSO auth passing.

Enterprise monitoring utilities for windows such as radii do not exist in linux.

Your front line helpdesk people are ill equipped to begin servicing users linux use needs.  And that last statement is an understatement.

Linux does not have the sort of integration that Outlook + Exchange + sharepoint + communicator provides.

Also pretty sure there is no collaborative tool like webex or adobe connect that will support screen sharing with linux.

No enterprise virus scanners for linux.  Cause if you switch your users to linux, lord knows the virus writers will have a bloody field day.

... I mean these are just the ones that come to mind immediately.

---

### Post by epsolon77 on 2009-10-02
> **chrisjsmith said:**
> 
That might have been the case in 2000 but MS's marketing has been very aggressive and their products are a lot better than they used to be.  I've not seen an org for 5 years that ISN'T MS end to end.  We only use Linux to support stuff (ESX hosts, monitoring with zenoss etc etc).

While Microsoft's product has improved, it still is expensive for the options you get.  Especially their desktop offerings have been piss poor.  While I have not used Windows 7, I am too sick of Microsoft's Good OS followed by Crap OS followed by Good OS and fanfare on how awesome their new product is.  I don't think Windows 7 will be that much better than any other current OS out there, where Vista was a toilet bowl compared with most comparable systems.  And I'm paying them to put me through huge hassles for installing, reinstalling, licensing, putting fear and pressure in my company because of audit uncertainties, despite the fact we have paid for our seats plus some.  Why am I throwing 500+ dollars at an OS that is a big target for viruses, and constricts our ability to use and expand our computers.  


> **chrisjsmith said:**
> 
Possibly in the US, but it's all Windows here in the UK.

On and you forgot SQL Server and Sharepoint....


Sigh.

Microsoft SQL server as decent?  Now THAT is a joke.  I haven't seen anything MsSQL does that MySQL can't do better, faster, and cheaper, exept run the database that was specifically programed to only allow MsSQL to run it.  My first tech job was programing Databases, and I CAN NOT STAND MsSQL.  The old Oracle 9i sessions were more robust than MsSQL 2005.  

Now I haven't used sharepoint, so I can not comment.

All in all, while I do see many people using Microsoft products it seems to be more because of fear than for true reasons.  No examination of uptime, or productivity, or cost analysis.  It's all "Well we had Windows 98 back in the day, so I guess we can't use anything else".  Or the famous "If I use Linux, I can't open a word document sent by the client".  

Look I'm not bashing Microsoft, because I use it and support it.  But paid software does not mean it is better software.  Microsoft is a comfort zone for many people and companies.  If they have the cash and the time to dump on it, so be it.  I don't.  I have done more with 4 P4's, ubuntu and GNU software for this company than the 30,000 we spent on a windows specialized consultant to upgrade and expand our systems.

---

### Post by epsolon77 on 2009-10-02
> **openfly said:**
> 
Your front line helpdesk people are ill equipped to begin servicing users linux use needs.  And that last statement is an understatement.

In my case this is not an issue.  I am the IT deparment, front line, back end, upside down and on Sundays too.:guitar:

> **openfly said:**
> 
Linux does not have the sort of integration that Outlook + Exchange + sharepoint + communicator provides.


While I have not deployed any there are actually more out there than you would initially think.  Yes Active Directory is a great central repository for SSO, but many of the Exchange features I find very cumbersome.  I have found lots of both paid and GNU offerings for IMAP or POP3 email services, integrated with calendar sharing, IM, webchat and much much more.  I think if Microsoft has anything going for them it would be their AD and Exchange.  I hate outlook and it's constant registry issues though.

---

### Post by openfly on 2009-10-02
Ultimately you have to think of it like this... large organizations don't buy software.  They buy solutions.

They go out to the microsofts, suns, and hp/ibms of the world and they say... hey... we want something that helps us meet our initiatives as outlined by x corporate leadership doc.

Then those companies dump a bunch of their software on the table and try to cobble something together that you as the organization would be willing to drop coin on.

Usually cobble is exactly the right word... consultants become the glue that forges 12 little apps into some monster app with 15 arms 12 heads and no legs.  Their sales guys present it as the ultimate in head and arm solutions neglecting to mention the lack of legs... 

You adopt it thinking wow i'll never need another 2 armed 2 legged 1 headed solution ever again since I've got this awesome beast. 

And 2 years down the road they are back in the office telling you how expensive it's going to be to attach this thing to a wheel barrow so one of your noc monkeys can wheel it about ever so slowly.

This is kinda how enterprise software gets bought and put into use.

This is kinda how sharepoint and exchange and every other major piece of software in business was born.

---

### Post by scorp123 on 2009-10-02
> **openfly said:**
>  BSD, Not much talked about.  But you will find a hell of a lot of FreeBSD, or BSDi systems hiding in the dark recesses of any major organization.  Sometimes not even all of IT knows they are there, doing their jobs dutifully.  But the simple fact is they are.  And I run into them all the time.  Talking of which .... :lolflag:

Yesterday I had a meeting with a company who want to replace their energy-hungry PC's with Sun Ray ThinClients .... And they want to go the VDI route (the Sun stuff I posted about above). Yes, no kidding. So we discussed what they should keep, what they should throw away, and so on. 

And before anyone panics: Yes, they will keep their precious ESX server farm :D  We will do server virtualisation on those monsters. They're tip top for that and their admins won't need to be retrained too much. So you see, I am not "anti-" anything (hmmm ... definitely anti-Microsoft ... but that doesn't count, LOL :D ) and I am definitely not on a "anti-VMware" FUD-jihad as someone up there claimed. :D

And so the discussion turned to the things they don't have but should have because their users demand that ... e.g. Bigger screens. Check. Those Sun Rays can do "multihead" so we could do really huge screens if we wanted to. Their users want to have a choice between Linux and Windows. Check. VirtualBox can do that. So we will have to use Sun xVM VirtualBox somewhere somehow ... But no problem. We can mix ESX and VirtualBox. No big deal. And I say "... and your users will have a choice between Windows, OpenSolaris or Linux when they login ... "

And all of a sudden one of the geeks in one of the rear seats asks "Uhhmm ... what about BSD? Could I have a BSD on those Sun Ray screens too?"

I want to turn around and answer the question when one of the "suits" gets up from the chair and goes Steve Ballmer on that guy: **"BSD???? WE DON'T HAVE BSD!!!  WE DON'T USE THAT .... "**

Without even moving his face that nerdy admin shyly says: **"But we do. We have BSD systems. Lots of them."**

The suit looks at the lady who is responsible for corporate IT and with a shy smile she says "**Yes ... they had to ... and ... so I let them."**

The suit turns red in the face, looks at the lady's boss and even before anything is said the guy just says **"Yes. I knew about it."**

The guy sits down again and just mumbles **"OK ... so we have BSD systems. *Lots of them *... "**

I had to control myself ... I was so close to falling off the chair :lolflag:

And the answer is .... No idea if that works. I'll have to go to my lab and find out :D

---

### Post by openfly on 2009-10-02
I swear to god I've seen that happen before.  On numerous occasions.

---

### Post by scorp123 on 2009-10-02
> **openfly said:**
> There's a lot of reasons not to roll linux as a desktop actually.   But it's happening. A lot of cities all across Europe are moving or already have moved to Linux. Munich and Hamburg in Germany, Paris in France, Bergen in Norway, and many others.

The canton (Swiss sub-state) I live in has moved to Linux too:
[http://www.osor.eu/news/ch-solothurn-canton-migrates-desktops-to-open](http://www.osor.eu/news/ch-solothurn-canton-migrates-desktops-to-open)
[http://linuxbsdos.com/2008/02/29/solothurn-swiss-canton-to-migrating-2000-desktops-to-debian-gnulinux/](http://linuxbsdos.com/2008/02/29/solothurn-swiss-canton-to-migrating-2000-desktops-to-debian-gnulinux/)
[http://times.debian.net/1224-Solothurn,-CH,-is-migrating-2000-desktops-to-Debian-migrating-2000-desktops-to-Debian](http://times.debian.net/1224-Solothurn,-CH,-is-migrating-2000-desktops-to-Debian-migrating-2000-desktops-to-Debian)

And our highest court, the Swiss Federal Court, has moved to OpenSolaris:
[http://www.osor.eu/case_studies/open-source-on-the-desktops-of-the-swiss-federal-court-and-federal-administrative-court-organisational-challenges](http://www.osor.eu/case_studies/open-source-on-the-desktops-of-the-swiss-federal-court-and-federal-administrative-court-organisational-challenges)

Not exactly Linux ... but it's still a Unix-like OS and open source too.

> **openfly said:**
>  Enterprise monitoring utilities for windows such as radii do not exist in linux.  HP OpenView exists for Linux as far as I know? And I should know. I worked at HP for 7 years (2000 - 2007). Google came up with this:

https://h10078.www1.hp.com/cda/hpms/display/main/hpms_content.jsp?zn=bto&cp=1-11-15-28^1745_4000_100__

And what do we see down there in the list?
**"HP Operations Manager 9 on Linux Evaluation"**

You need to have a "HP Passport Login" to download the software. But as far as I can tell you're proven wrong. Such tools do exist for Linux. Even the really expensive "Enterprise" level ones.

> **openfly said:**
>  Your front line helpdesk people are ill equipped to begin servicing users linux use needs. Why should they be "ill equipped" for "linux use needs"? Like simple helpdesk people (the guys who are just supposed to pick up the phone, say their name, and then write down what the problem is .... Been there, done that. Ages ago! :D ) are "better equipped" when it comes to Windows problems? That's BS. Sorry to say so. For the helpdesk folks it makes no difference. They pick up the phone, they write down what the problem was, they assign the trouble ticket to one of the support engineers ... and that's it from their POV. Linux, Windows, Solaris, HP-UX, BSD, HP OpenView, IBM Tivoli, BEA WebLogic, Oracle .... for the frontline helpdesk guys that stuff is all the same.

The real question is if the "2nd line of defence", e.g. the IT support guys and the engineers can handle Linux ... or whatever you're throwing at them.

In case of a Linux migration I'd have to say "Yes, they can" ... or why else would you be migrating to Linux? This is assuming that thorough evaluation and assessment was done before the migration was decided. Usually large-enough organisations and corporations have no problem finding enough Unix- and Linux know-how amongst their own staff so that such questions become a non-issue.

I am sure even Microsoft would find enough employees with tons of Linux know-how so that they too could migrate if Steve Ballmer were not so darned good at throwing chairs around ... :lolflag:

> **openfly said:**
>  Linux does not have the sort of integration that Outlook + Exchange + sharepoint + communicator provides.  
[http://www.egroupware.org/](http://www.egroupware.org/)
[http://www.zimbra.com/](http://www.zimbra.com/)
[http://www.open-xchange.com/](http://www.open-xchange.com/)

and so on and so on .... And the last two offer commercial packages too.

Solothurn --the Swiss Canton I live in-- moved their 2000 desktops from Microsoft Exchange/Outlook to this solution:

[http://www.scalix.com/](http://www.scalix.com/)


> **openfly said:**
>  Also pretty sure there is no collaborative tool like webex or adobe connect that will support screen sharing with linux. Wrong again.

Solothurn here uses this:
[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)

The software also replaces all their VPN stuff. I also earn my money selling that product and it's very very powerful. Far away from "cheap" or "free" as it can get, but it runs on Linux too and you can use it with & from Linux desktops too.

Then there is this plugin:
[http://www.tbsol.de/](http://www.tbsol.de/)

Again not "free" and far away from "cheap". But worth every penny. With that TBS plugin you can also share any application session with any connected client OS.

Voila. Done. They do their meetings like that. One guy with appropriate permissions shares his desktop, everybody else --no matter if they have Mac OS X, BSD, Linux or Windows-- connects to the shared session and voila, everybody sees the same thing.


> **openfly said:**
>  No enterprise virus scanners for linux. [http://www.avira.com/en/products/avira_antivir_server_3.html](http://www.avira.com/en/products/avira_antivir_server_3.html)
[http://www.avast.com/eng/download-avast-for-linux-server.html](http://www.avast.com/eng/download-avast-for-linux-server.html)


> **openfly said:**
>  Cause if you switch your users to linux, lord knows the virus writers will have a bloody field day.

... I mean these are just the ones that come to mind immediately. Hmmm ... seems I didn't get your sarcasm immediately :D

---

### Post by openfly on 2009-10-02
> **scorp123 said:**
> But it's happening. A lot of cities all across Europe are moving or already have moved to Linux. Munich and Hamburg in Germany, Paris in France, Bergen in Norway, and many others.

The canton (Swiss sub-state) I live in has moved to Linux too:
[http://www.osor.eu/news/ch-solothurn-canton-migrates-desktops-to-open](http://www.osor.eu/news/ch-solothurn-canton-migrates-desktops-to-open)
[http://linuxbsdos.com/2008/02/29/solothurn-swiss-canton-to-migrating-2000-desktops-to-debian-gnulinux/](http://linuxbsdos.com/2008/02/29/solothurn-swiss-canton-to-migrating-2000-desktops-to-debian-gnulinux/)
[http://times.debian.net/1224-Solothurn,-CH,-is-migrating-2000-desktops-to-Debian-migrating-2000-desktops-to-Debian](http://times.debian.net/1224-Solothurn,-CH,-is-migrating-2000-desktops-to-Debian-migrating-2000-desktops-to-Debian)

And our highest court, the Swiss Federal Court, has moved to OpenSolaris:
[http://www.osor.eu/case_studies/open-source-on-the-desktops-of-the-swiss-federal-court-and-federal-administrative-court-organisational-challenges](http://www.osor.eu/case_studies/open-source-on-the-desktops-of-the-swiss-federal-court-and-federal-administrative-court-organisational-challenges)

Not exactly Linux ... but it's still a Unix-like OS and open source too.


Just because one lemming is jumping off the cliff doesn't mean we should all follow.

> **scorp123 said:**
> 
 HP OpenView exists for Linux as far as I know? And I should know. I worked at HP for 7 years (2000 - 2007). Google came up with this:


https://h10078.www1.hp.com/cda/hpms/display/main/hpms_content.jsp?zn=bto&cp=1-11-15-28^1745_4000_100__

And what do we see down there in the list?
**"HP Operations Manager 9 on Linux Evaluation"**

You need to have a "HP Passport Login" to download the software. But as far as I can tell you're proven wrong. Such tools do exist for Linux. Even the really expensive "Enterprise" level ones.


Yeah looks like there is a radia client for linux.  It wasn't supported for most OO ( operations orchestration ) stuff when I worked for HP.  And I doubt anyone is orchestrating linux Radia clients in a way relevant to desktop use.

But yeah obviously I haven't researched that one enough... just going off some stuff I picked up from HP OO teams I worked with.

> **scorp123 said:**
> 

 Why should they be "ill equipped" for "linux use needs"? Like simple helpdesk people (the guys who are just supposed to pick up the phone, say their name, and then write down what the problem is .... Been there, done that. Ages ago! :D ) are "better equipped" when it comes to Windows problems? That's BS. Sorry to say so. For the helpdesk folks it makes no difference. They pick up the phone, they write down what the problem was, they assign the trouble ticket to one of the support engineers ... and that's it from their POV. Linux, Windows, Solaris, HP-UX, BSD, HP OpenView, IBM Tivoli, BEA WebLogic, Oracle .... for the frontline helpdesk guys that stuff is all the same.

The real question is if the "2nd line of defence", e.g. the IT support guys and the engineers can handle Linux ... or whatever you're throwing at them.

In case of a Linux migration I'd have to say "Yes, they can" ... or why else would you be migrating to Linux? This is assuming that thorough evaluation and assessment was done before the migration was decided. Usually large-enough organisations and corporations have no problem finding enough Unix- and Linux know-how amongst their own staff so that such questions become a non-issue.

I am sure even Microsoft would find enough employees with tons of Linux know-how so that they too could migrate if Steve Ballmer were not so darned good at throwing chairs around ... :lolflag:


I respectfully, completely, and utterly disagree.

> **scorp123 said:**
> 
 
[http://www.egroupware.org/](http://www.egroupware.org/)
[http://www.zimbra.com/](http://www.zimbra.com/)
[http://www.open-xchange.com/](http://www.open-xchange.com/)

and so on and so on .... And the last two offer commercial packages too.



Yeah, they all suck too.  I mean sure they are "get the job done."  but they are in no way capable of providing an all purpose calendar / sharing / communication integration across the board.  Any claim to the contrary is either wishful thinking or just uninformed.

> **scorp123 said:**
> 

Solothurn --the Swiss Canton I live in-- moved their 2000 desktops from Microsoft Exchange/Outlook to this solution:

[http://www.scalix.com/](http://www.scalix.com/)


 Wrong again.

Solothurn here uses this:
[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)

The software also replaces all their VPN stuff. I also earn my money selling that product and it's very very powerful. Far away from "cheap" or "free" as it can get, but it runs on Linux too and you can use it with & from Linux desktops too.

Then there is this plugin:
[http://www.tbsol.de/](http://www.tbsol.de/)

Again not "free" and far away from "cheap". But worth every penny. With that TBS plugin you can also share any application session with any connected client OS.

Voila. Done. They do their meetings like that. One guy with appropriate permissions shares his desktop, everybody else --no matter if they have Mac OS X, BSD, Linux or Windows-- connects to the shared session and voila, everybody sees the same thing.


They aren't webex and they aren't connect.  None of the consultants / business partners they work with will have this technology...  when they are invited to webex sessions ( which they will certainly be... ) do they just say... Sorry I can't?  That seems unacceptable to me.

> **scorp123 said:**
> 

 [http://www.avira.com/en/products/avira_antivir_server_3.html](http://www.avira.com/en/products/avira_antivir_server_3.html)
[http://www.avast.com/eng/download-avast-for-linux-server.html](http://www.avast.com/eng/download-avast-for-linux-server.html)



They don't address risks to linux well at all.  That **** is sold to people who think "ZOMG I NEED ANTIVIRUS".  Pretty much the only semi-effective approach to antivirus i've seen on linux today is either tripwire style checksumming or ROSH / OGFS style forcing everything through some ridiculously highly audited command engine.

But that being said, avira is still a joke.


> **scorp123 said:**
> 
 Hmmm ... seems I didn't get your sarcasm immediately :D

You are either an excellent salesperson or severely deluded.  That's just my opinion >=D.

---

### Post by scorp123 on 2009-10-02
> **openfly said:**
> Just because one lemming is jumping off the cliff doesn't mean we should all follow.  Ballmer, is that you?? :lolflag:  (... searching for cover ... chairs are flying low tonight ... )

> **openfly said:**
>  Yeah, they all suck too.  BS. Sorry to say so. Sure, if someone is completely stubborn and unwilling to see the light than you get "Linux sucks. Windows is better" messages and what not. Oh sure. But no matter how often you call Linux users "lemmings" will change the facts. And the facts are that people, corporations and governments are switching over to Linux.

> **openfly said:**
>   I mean sure they are "get the job done."  Last time I checked *this* is precisely what counts. Technical merits and all that, you know? 

> **openfly said:**
>  but they are in no way capable of providing an all purpose calendar / sharing / communication integration across the board.  Download e.g. Open-Xchange and see for yourself, LOL

> **openfly said:**
>   Any claim to the contrary is either wishful thinking or just uninformed. And that claim was ... what? "Informed"? Definitely not.

> **openfly said:**
>  They aren't webex and they aren't connect.  None of the consultants / business partners they work with will have this technology...   LOL

To connect to a Sun Secure Global Desktop session all it takes is a web browser and a working Java browser plugin. It doesn't matter if you use Windows, Linux, Mac OS, BSD ..... For as long as you have a browser.

So rest assured when I say that their partners and consultants have no problems whatsoever joining any of their online conferences via SSGD.

We do that all the time too. No problem whatsoever. You can use Windows, you can use Mac OS, you can use Opera, you can use Google Chrome, Firefox, Internet Explorer ... whatever you wish.

Nice job shooting yourself in the foot :D

> **openfly said:**
>  when they are invited to webex sessions ( which they will certainly be... ) do they just say... Sorry I can't?  Why would they??? :lolflag:

Fresh from WebEx Germany's web site:
[http://www.webex.de/de/customercare/system-requirements.html](http://www.webex.de/de/customercare/system-requirements.html)

"... **_System requirements:_**

... Ubuntu 8.04, Fedora 8, Red Hat 5, OpenSuSE 10.3
[LIST][*]Firefox 2/3
[*]JavaScript enabled
[*]Requires Sun Java 5 or higher
[/LIST]
... "

As a matter of fact I just recently was in a WebEx session which was held by another Sun partner. And I sure don't use anything from Redmond on my desktop :D

So I know for fact that WebEx works with Linux desktops without troubles. Oh .... and I just sunk your argument. ):P  ... Sorry about that. NOT. :)

> **openfly said:**
>  They don't address risks to linux well at all. "risks to Linux" ... such as? Steve ... is that you? :) You really sound like Ballmer. 

> **openfly said:**
>  Pretty much the only semi-effective approach to antivirus i've seen on linux today is either tripwire style checksumming  Sorry for ruining your parade again, but tripwire?? Against "viruses"? On Linux? LOL. Yes, Linux has security problems. Just like any other software written by us imperfect humans. But viruses are not on that list. The one security problem you really have to be worried about on Linux is human hackers ... or rather "crackers" as they should be called. That's what tripwire is good for. Finding manipulated binaries. But those aren't "viruses". And last but not least: There are mechanisms such as AppArmor and SELinux and what not that would prevent a manipulated binary from doing what it wants to do.

Anti-virus solutions on Linux --such as the ones I mentioned-- may make sense if you run Linux mail or file servers which are distributing mails and files to Windows end-users too. That's what those programs are good at and what you should use. Using "tripwire" trying to find non-existing Linux viruses is idiotic, sorry to say so.

> **openfly said:**
>  You are either an excellent salesperson or severely deluded. A little bit of both I guess but as for the "deluded" part it seems I am not alone with that symptom? :D

---

### Post by epsolon77 on 2009-10-03
Ok I'm a tad confused.  What is the difference between a Cloud and a virtualized cluster?  

As far as I can tell a cloud is anything distributed over a network (talk about vauge.  According to that deffinition my exhcnage system could be considered a cloud....  Just a joke)

It seems that eucolyptus supports running virtual machines on the cloud, but I can't tell if the virutal machine is chained to a physical machine.  I suppose that would be ok so for my purposes so long as if that machine failed, the virtual machine would automatically be transfered over to another machine.  Any comments?

---

### Post by scorp123 on 2009-10-04
Yes, it is vague.

But to get back on-topic and your original posting: You said you wanted --if possible-- desktop virtualisation. Now, server virtualisation is one thing, and if you can afford it and don't mind the price tag then ESX is what you need. It's "VMotion" feature would move virtual servers between the ESX instances so you could do e.g. maintenance on one physical server without having to plan downtime or anything like that. Other products offer the same or similar features, e.g. Citrix "XenServer" calls that feature "XenMotion", and many open source solutions can do that too, e.g. KVM or open source "Xen" (on which Citrix's commercial package "XenServer" is based on).

OK ... so much for server virtualisation. But have you already looked at desktop virtualisation?

---

### Post by epsolon77 on 2009-10-04
> **scorp123 said:**
> Yes, it is vague.

But to get back on-topic and your original posting: You said you wanted --if possible-- desktop virtualisation. Now, server virtualisation is one thing, and if you can afford it and don't mind the price tag then ESX is what you need. It's "VMotion" feature would move virtual servers between the ESX instances so you could do e.g. maintenance on one physical server without having to plan downtime or anything like that. Other products offer the same or similar features, e.g. Citrix "XenServer" calls that feature "XenMotion", and many open source solutions can do that too, e.g. KVM or open source "Xen" (on which Citrix's commercial package "XenServer" is based on).

OK ... so much for server virtualisation. But have you already looked at desktop virtualisation?

My "10 year goal" was to move the computers to an LTSP type solution, with each workstation functioning on a PXE boot, loading all data from the server.  I went to work in my lab, got LTSP to work using dual monitors on boot, stable and running all our software.  I even managed to extend the LTSP server as a true remote terminal server, allowing any computer to VNC in using dual monitors.  Then the owners of my company bought a customer records database product which required dotnet 1.1 to function.  Now in the last two months the reporting system upgraded to using dotnet 2.0, which I may be able to get running.  I figured though, if you look at a solution for the servers, there isn't too much of a difference to extending this to desktops.  I could be wrong, and this could be very different, but it doesn't hurt to ask.

On servers I guess what I need is a virtualized system with something akin to VMotion.  Do you know of any GNU packages that accomplish this?

My issue with all this is that I am sick and tired of having to go on site to fix someone's desktop, or replace a broken piece of hardware.  I feel like in this day and age I shouldn't need to care what is sitting at my end users desk.  Let it be the stupidest piece of junk out there that can support the graphics needed, and move all the roles to someone central, portable and stable.  All the PC's at my office are dying.  They have been in service every day for the last 5-8 years.  They really don't have much time left on em.  I would hate to shell out 900 per pc to get a system just as unreliable as before, but the company does not have an abundance of cash because of the current financial situation, so asking the boss's for 10 grand for a new server setup with full VD licensing would either make everyone laugh or get me fired, depending on how the owner's coffee tasted that morning.  I know I could justify a new server or two to the tune of 2 to 5 grand if I showed a substantial cost savings on both long term hardware and showed that I am leveraging software that is stable and very inexpensive. The owners loved the idea of LTSP, until the fancy new reporting database though bought wouldn't work on it.

---

### Post by scorp123 on 2009-10-04
> **epsolon77 said:**
> My "10 year goal" was to move the computers to an LTSP type solution, with each workstation functioning on a PXE boot, loading all data from the server. Yeap, sounds like *the* classical thin-client scenario.

> **epsolon77 said:**
>  I figured though, if you look at a solution for the servers, there isn't too much of a difference to extending this to desktops. In the end it highly depends on the clients you can use or want to use. The thinner your client is the more of this you can put on your servers ... and thus achieve "desktop virtualisation".

> **epsolon77 said:**
>  Then the owners of my company bought a customer records database product which required dotnet 1.1 to function.  That's where I'd use "Sun Secure Global Desktop". Yes, I admit: I am biased. Heavily biased. There's no point in arguing that. I work for a Sun partner ... 

Maybe you want to read the Wikipedia entry on SSGD?
[http://en.wikipedia.org/wiki/Sun_Secure_Global_Desktop](http://en.wikipedia.org/wiki/Sun_Secure_Global_Desktop)

And to be perfectly honest with you: That Wikipedia entry was partially written by me too. It's easily visible in the page history (same nick). The argument here being that I have done several projects with that product and that I know the product well enough so that I felt entitled to help that Wikipedia article get better.

So ... with all that honesty flying around here: does that product have downsides? Well, it sure has one: It's expensive like hell. Really expensive. And it's not always easy to get rebates out of this. You simply have to try.

So ... what's so special about SSGD? The nice thing here is that you can install any weird and exotic application on your server side ... and all the end-users have to know is how to click that icon in their "web top". Because that's exactly all they will need to access that application: A web browser. And it doesn't matter if your exotic application is on Windows, Unix, IBM AS/400, IBM 3270 .... Your end-users don't have to know. They don't want to know. All they want is to click that icon ... and voila ... they get that application in a window ... or fullscreen. Whatever you decide. 

And as I said previously: It doesn't even matter what client OS the end-users have. Could be Windows. Could be Windows CE. Could be Solaris. Could be Mac OS. Could be Linux or BSD ... It doesn't matter for as long as you have a web browser on that OS and a working Java browser-plugin.

SSGD also works as "VPN replacement". So when you're in the office you have a thin-client on your desk (e.g. Fujitsu-Siemens "Futro"? Or VXL Itona? Or a Atom-based Net-top PC with a "Damn Small Linux" installation?) and you access all your applications remotely, be that Solaris desktops, IBM host sessions, telnet sessions, SSH sessions or Windows desktops ... Doesn't matter. Thanks to SSGD's magic it will all feel as if those apps were installed locally.

And then you go home and *"Ohhhh ... sh**** ... I forgot to copy that super-duper important presentation to my manager .... "  *
No problem: all you need is a web browser. You login via your company's external HTTPS: address and voila, you're back in your desktop session .... as if you were in the office again.

I work like that all the time when I'm on the road, at customers and basically anywhere but in the office. All it takes is a few clicks and I get my Windows, Solaris and Linux desktops delivered to me, no matter where I am.

My point being? With SSGD management can introduce whatever applications and frameworks they want. For as long as I have a server where I can put that application and its framework onto and for as long as my end-users have a web browser on whatever desktop OS they happen to use I can deliver that application to them. They can work and get their jobs done. Linux or not. Windows or not. BSD or not. Mac OS or not. I don't have to care about their client OS'es not being able to run whatever crazy application my managers came up with ... that issue simply doesn't exist here.

> **epsolon77 said:**
>  On servers I guess what I need is a virtualized system with something akin to VMotion.  Do you know of any GNU packages that accomplish this?  ProxMox Virtual Environment ... It's basically a highly specialised Debian variation which does one thing and one thing only: act as "bare metal" hypervisor. And being based on Debian it's 100% GNU GPL. No other licenses, no hidden IP traps, nothing. Pure GNU GPL.

Link to the product:
[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

Link to a tutorial which shows and explains the product:
[http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve](http://www.howtoforge.com/kvm-and-openvz-virtualization-and-cloud-computing-with-proxmox-ve)


> **epsolon77 said:**
>  My issue with all this is that I am sick and tired of having to go on site to fix someone's desktop, or replace a broken piece of hardware.  Sorry for boring the heck out of everyone here ... But *you* _**definitely**_ sound like you should call SUN and have them demonstrate their "Sun Ray" ultra-thin-clients to you.

On a "Sun Ray" there is nothing to manage. Nothing. Rien. Nada. Niente. Nichts. Nihil. In the rare occasion that one should get broken (which rarely if ever happens!) you simply replace it. Unplug power, unplug VGA, unplug LAN, unplug mouse & keyboard. Throw old Sun Ray into the trash bin, hook up new Sun Ray to the aforementioned devices (LAN, keyboard, power, VGA) ... and your end-user can continue their work as if nothing had happened. Or the user simply walks over to another Sun Ray and "hotdesks" back into his session while his old Sun Ray gets replaced.

> **epsolon77 said:**
>  I feel like in this day and age I shouldn't need to care what is sitting at my end users desk. Let it be the stupidest piece of junk out there that can support the graphics needed, and move all the roles to someone central, portable and stable.  Bingo! :D

> **epsolon77 said:**
>  I would hate to shell out 900 per pc to get a system just as unreliable as before The cheapest Sun Ray, the "Sun Ray 2" is like $ 349.-- per piece, as per list price. 
[http://www.sun.com/sunray/sunray2/](http://www.sun.com/sunray/sunray2/)

But I have never ever seen anyone pay that list price, usually you get rebates and what not out of any deal with Sun, especially if you buy servers from them. Because that's what really counts with them: buying their servers. Buy a few good servers from Sun and they'll throw in Sun Rays and the necessary software for free.

> **epsolon77 said:**
>  so asking the boss's for 10 grand for a new server setup with full VD licensing would either make everyone laugh or get me fired Ever heard of "Try & Buy"? No kidding: You can get Sun equipment for up to 60 days (90 and even 120 days if you know the right people and ask in a super-duper sugar-sweet way ...) for free. Don't like it? Return it. And it didn't cost you anything, just a bit of time. 

> **epsolon77 said:**
>  The owners loved the idea of LTSP, until the fancy new reporting database though bought wouldn't work on it. I see ...  And placing that application on a special server or a special virtual image and then deliver the application via SSH or VNC wouldn't work?


Again sorry for turning this into a Sun ad fest .... Unless OP has more questions I will STFU and not mention Sun any further. I just felt that their thin-client products can do what OP wanted to achieve .... OK?

---

### Post by epsolon77 on 2009-10-04
> **scorp123 said:**
> 
Again sorry for turning this into a Sun ad fest .... Unless OP has more questions I will STFU and not mention Sun any further. I just felt that their thin-client products can do what OP wanted to achieve .... OK?

Being that I am OP, trust me I don't mind sticking it to a single vendor since you are obviously in tune with the product.  And I also don't mind both the conflicting opinion or the debate that has fostered.  IMHO vicious debate, so long as it is civil, is the greatest benefit even achieved from society.

I will have to look much closer at ProxMox.  I must have done something wrong in my quick testing of ProxMox because the Live Migration wasn't working for me.  

I am coming up with a whole list of questions about the sun product, but I will sleep on them and research them some tomorrow before just blindly asking questions.  I like the idea of the product, I am just almost certain the owners will not want to pony out the cash for it.  We are getting to the point where we are selling our used toners and refurbishing early P4's to keep our agents online.  I don't think any major investment is going to be made.  If any investment were made, a system like ProxMox would make it easier to slowly move our users instead of requiring a quick move.  

I would like to note to everyone who has been posting, Thank you for all your candid opinions and discussions.  I know I'm up to this job that I am in, but there are times when I feel like I have barely scratched the surface on the resources I could be leveraging, and discussions like this make me feel much more up to speed.  I also know that no one could ever know all the info that is out there. Thank you all again, even when you thought you were being a bit of a jerk in pushing your opinion (or maybe though the other guy was a jerk for pushing their opinion) it is very appropriated.  I promise if I do set up a successful test bed for a GNU option I will create a How TO.

---

### Post by scorp123 on 2009-10-05
> **epsolon77 said:**
>  I will have to look much closer at ProxMox ...  Talking of which:

[http://itknowledgeexchange.techtarget.com/server-virtualization/proxmox-pve-offers-vm-mash-up-for-the-virtualization-market/](http://itknowledgeexchange.techtarget.com/server-virtualization/proxmox-pve-offers-vm-mash-up-for-the-virtualization-market/)

---

### Post by openfly on 2009-10-05
lol scorp123... you still making **** up ?

---

### Post by scorp123 on 2009-10-05
> **openfly said:**
> lol scorp123... you still making **** up ?
"making up" ??

Looking at your previous posting I'd say that description rather fits to you, but never mind. I am here because I want to help OP, believe it or not. That's the reason I hang out on this forum.

So if that thread has started to bore the heck out of you and if you find yourself unable to keep the tone friendly and civil ... why don't you move on then? Just asking. Or do we really need an admin come in here and lock the thread?

---

### Post by openfly on 2009-10-05
Scorp 5 of the last 7 posts were you and in none of them did you address the points I raised, instead crafting answers to points I did not raise as if they were somehow relevant.  Which they were not.

You are a pretty smart guy scorp, and I think a lot of your advice is helpful.  But it's also severely one sided and borders on ignorance concerning limitations.  And I don't think it's helpful to ignore well founded concerns simply because you don't like the competing products.

---

### Post by scorp123 on 2009-10-05
> **openfly said:**
> Scorp 5 of the last 7 posts were you and in none of them did you address the points I raised I think I did, "Mr. Ballmer" ( <== not to be taken serious). For example: Your arguments against Linux on the desktop were sunk. Same goes e.g. with your argument about "frontline support people not being ready" and what not. Your *"I respectfully, completely, and utterly disagree"* was noted ... but having worked as "Callcenter Agent" myself ages ago I know the facts from first-hand experience, e.g. that for frontline callcenter agents it really doesn't matter what they support. **Been there myself, done that myself. Ages ago.** As callcenter agent you're just supposed to pick up the phone, say your employer's name, say your name, open a trouble ticket, and that's it. You're not supposed to know anything. Be that Windows, Linux, Oracle, BEA WebLogic, HP-UX, Solaris ... You just take the phone and open the ticket. That's it. So your point *"Your front line helpdesk people are ill equipped to begin servicing users linux use needs."* is simply wrong, wrong and wrong. Paris is proving you wrong. Munich is proving you wrong. Bergen is proving you wrong. The Swiss canton I live in is proving you wrong.

So that was for example just another point I skipped because I felt discussing that with you would lead nowhere. You have your opinons, fine. I let you have them and I am not going to "evangelize" you ... it's just that I skipped over this because I know better. I don't need to prove it, neither to you, neither to OP, neither to the admins here or anyone else. Google is your friend and the facts about more and more conversions to Linux speak for themselves. But never mind.

> **openfly said:**
>  But it's also severely one sided I already admitted several times that I am heavily biased ... just like everyone else here it seems? So what? I never claimed to know the ultimate truths about cloud computing and virtualisation. I can just speak for myself and tell you and everyone who cares what *I* do day by day or how *I* would go about solving OP's problem *if I* were facing them. Others have added their own input and more or less shown their biases too .... And OP thought he benefitted from that discussion as he stated himself. So voila: mission accomplished. Me being one-sided or not. It's not my job not to be one-sided. :D

And while we're dealing out criticism for single postings here then let me tell you that I thought that your postings were of tip top quality ... up and until this one:
[http://ubuntuforums.org/showpost.php?p=8041676&postcount=39](http://ubuntuforums.org/showpost.php?p=8041676&postcount=39)

I somehow had hoped that this was sarcasm and that you really didn't mean that in full earnest?? But apparently not so. Oh well. ](*,)

> **openfly said:**
>  and borders on ignorance concerning limitations. Honestly ... after posting #39 you're not really in a position to accuse me of ignorance. And I already posted several times that some of the stuff I came up with *does* have limitations or not all features that you'd get with a Enterprise-level VMware ESX license. But then again it now seems that OP is on a tight budget and probably won't need all those expensive ESX features? So ... limitations or no limitations, but in that light suggesting alternatives was more helpful than harmful.

> **openfly said:**
>  And I don't think it's helpful to ignore well founded concerns  Last time I checked this thread wasn't locked yet .... so by all means: bring up all technically well-founded concerns that you may have, let OP benefit from your knowledge and from your opinions .... But if you could just drop the Steve Ballmer talk that you keep coming up with since posting #39 please? Thank you. ):P

---

### Post by openfly on 2009-10-05
Still no responses to anything I said.  Well done.

---

### Post by epsolon77 on 2009-10-06
> **openfly said:**
> Still no responses to anything I said.  Well done.

Openfly, you've stopped adding rational thought to the discussion.  If you have a technological point to make, back it up with facts.  You may not agree with scorp123's point of view and hardware preferences, but put out some facts, not this childish argument scheme.  I appreciate all the points that have been raised in this thread, but lets keep this an open debate and not a pecker fight.

---

### Post by scorp123 on 2009-10-06
> **epsolon77 said:**
> Openfly, you've stopped adding rational thought to the discussion.  My thoughts exactly.

> **epsolon77 said:**
>  If you have a technological point to make, back it up with facts. +1 

> **epsolon77 said:**
>  but put out some facts, not this childish argument scheme.  Exactly. Do we really need an admin come in here and lock the thread?
[B][U]
@epsolon77:[/U][/B] I am who I am and I know what I know and I don't care if other people think that they are right and that I am wrong. I shall be so slightly arrogant and simply say: "I know better." Even if that should mean that my opinion is biased and one-sided. But ultimately we all are biased about something, pro-this and anti-that. That's what having the freedom of having an opinion is all about.

So if you have questions about that Sun stuff that I mentioned or anything ... please feel free to PM me. Other than that I think this thread has served its purpose and any further comments are unnecessary. The truth is out there and it speaks for itself. For example this bit of news I saw today:

"Open Source Makes Big Gains at the London Stock Exchange"
[http://www.computerworlduk.com/toolbox/open-source/blogs/index.cfm?entryid=2568&blogid=14](http://www.computerworlduk.com/toolbox/open-source/blogs/index.cfm?entryid=2568&blogid=14)

The LSE is throwing away their $65 million Windows solution and replacing it with Linux (and a bit of Solaris). That speaks volumes I guess.

And to get back on-topic, maybe you're interested in this aricle too?

"Run your own Ubuntu Enterprise Cloud, part 1"
[http://fnords.wordpress.com/2009/10/04/run-your-own-uec-part-1/](http://fnords.wordpress.com/2009/10/04/run-your-own-uec-part-1/)

.
.
.

---

### Post by epsolon77 on 2009-10-06
> Other than that I think this thread has served its purpose and any further comments are unnecessary.

If an admin see's this, please do not lock this thread yet.  I hope to post a link to my findings regarding proxmox and maybe even a how to.

---

### Post by scorp123 on 2009-10-08
Some fun. And yes, this happened for real.

[IMG]http://i121.photobucket.com/albums/o217/scorp123_2006/Humor/th_Sun_VBox_phone-conf.jpg[/IMG]

Full size [here]("http://i121.photobucket.com/albums/o217/scorp123_2006/Humor/Sun_VBox_phone-conf.jpg")

---

### Post by epsolon77 on 2009-10-09
> **scorp123 said:**
> Some fun. And yes, this happened for real.

[IMG]http://i121.photobucket.com/albums/o217/scorp123_2006/Humor/th_Sun_VBox_phone-conf.jpg[/IMG]

Full size [here]("http://i121.photobucket.com/albums/o217/scorp123_2006/Humor/Sun_VBox_phone-conf.jpg")

LOL!  That is great.

A quick note to anyone researching ProxMox,  it REQUIRES a 64 bit processor.  Straight up, no way around it.  Otherwise it seems very full featured.  I have yet to successfully get a virtual machine installed, but there could be many reasons for that.

Scorp do you know if VBox's will RDP server will integrate with Active directory and always transfer a user to a specific VM?  I have to admit that I am being a little lazy in asking, because I have not spent hours researching this one.

---

### Post by scorp123 on 2009-10-09
> **epsolon77 said:**
>  Scorp do you know if VBox's will RDP server will integrate with Active directory and always transfer a user to a specific VM?   With VirtualBox alone ... Nope, I don't think you could do that.

If you wanted to something like this you'd have to employ Sun's "VDI" software. This is one of its core functions, e.g. users authenticate against LDAP or Microsoft Active Directory and then exactly get those virtual machines (from VirtualBox, VMware ESX or Hyper-V) they are supposed to get access to, but nothing else. And you as admin can decide whether they get to keep those virtual machines ("personal desktop") or if their virtual instances are destroyed after they logout ("flexible desktop").

Take a look at these pictures (borrowed from a presentation I got from folks at Sun ... ):

[IMG]http://dl.getdropbox.com/u/1614648/Screenshots/Sun_VDI_basic-scheme_75perc.jpg[/IMG]

Similar schematics are available from their publicly accessible Wiki:
[http://wikis.sun.com/display/VDI3dot1/Home](http://wikis.sun.com/display/VDI3dot1/Home)

BTW ... Sun recently released a "soft-client", i.e. a software that emulates their Sun Ray thin-clients. Brilliant stuff. So you can try out their VDI technology without having to buy or borrow those clients from somewhere. Your existing Windows clients will do (Linux clients can run the software via WINE). There is a forum message describing the installation on WINE:

[http://forums.sun.com/thread.jspa?threadID=5410731&tstart=0](http://forums.sun.com/thread.jspa?threadID=5410731&tstart=0)

---

### Post by plankton127 on 2009-10-09
This is a great thread!:popcorn:

---

### Post by scorp123 on 2009-10-10
> **epsolon77 said:**
>  do you know if VBox's will RDP server will integrate with Active directory and always transfer a user to a specific VM?  I just had a chat with a buddy of mine. We were talking about virtualisation and even this thread when this question popped up:
**"Hmmm ... what if we leave RDP away?"**

Duh. Of course #-o ... I am getting old. Let me explain:

You said you wanted to use LTSP ... I honestly have no clue about LTSP but I just read the Wikipedia article and there I found this bit:

From: [http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)
> " ... The client connects to the XDMCP login manager on the LTSP server. In case of the newer MueKow (LTSP 5) setup, the client first builds an SSH tunnel to the LTSP server's X environment, through which it will start the LDM login manager (on the LTSP server). From this point forward, all programs are started on the LTSP server, but displayed and operated from the client. ... " 

So you have a normal working X11 environment on those LTSP clients? e.g. you have GDM and all that?

Well ... if ***that*** is the case then **yes**, I know a way how to make sure that a user who logs in only gets the VM he's supposed to get. I implemented something like this myself ... because I had to. Long story. I should have remembered sooner. ](*,)

Please read here:
[http://ubuntuforums.org/showpost.php?p=6475112&postcount=8](http://ubuntuforums.org/showpost.php?p=6475112&postcount=8)

So there is no RDP (you'll have to find a solution with VNC somehow), there is no resource management and as for recycling unused or dead VM's you'll have to write a few cron jobs that get their info out of **"VBoxManage"** and other such shell commands ... Last but not least there is no built-in web administration interface ... you'll have to add that yourself:
[http://code.google.com/p/vboxweb/](http://code.google.com/p/vboxweb/)

Maybe you could cook up something with these things? The advantage I see here is that it would most likely work with whatever hardware you have at your disposal and it would not require you to buy or pay _ANYTHING_ as most of this stuff can be had for free.

And Microsoft AD integration is easy. Just fetch these packages from the repositories: ```
sudo apt-get install likewise-open likewise-open-gui
```

Google will tell you the rest. But it's easy. If you do it right your Linux server will then authenticate users against Microsoft AD. Taddaaaa!

So:

- build your LTSP server and clients
- Install LikeWise Open and make sure your LTSP server authenticates against Microsoft AD
- install VirtualBox on your server
- use my "Poor Man's VDI" method as explained here:
[http://ubuntuforums.org/showpost.php?p=6475112&postcount=8](http://ubuntuforums.org/showpost.php?p=6475112&postcount=8)

==> User logs in via LTSP, selects "AutoVM" as his session and tadaaaa ... the user gets the VM he is supposed to have access to.


The downside:

Switching between VM's would either require multiple user accounts or changing the login script which selects the VM .... Or you cook up some interactive program (e.g. with **"zenity"** ??) that let's the user pick the VM he wants to start ... 

So if your budget is really super duper tight and buying expensive server hardware and/or expensive software licenses and/or proprietary thin-clients are total no-starters .... well, maybe this stuff could do what you want?

Yes, it's quite hackish ... But at least it would be free.


My apologies for using up so much space in this thread .... I will STFU now. :-#

---

### Post by epsolon77 on 2009-10-10
(Taking a shot of Nerds for a sugar rush before beginning post)


Ok.  Scorp, GREAT Idea.  I had not even considered combining LTSP with virtual box.

Since LTSP isn't really a virtualized system I am going to take a few moments to explain LTSP and my test LTSP sever that I set up about a year ago.  Please forgive any terms I am getting wrong here. 

LTSP (Linux Terminal Server Project) sets itself up as a dns server and boot master for PXE booting.  Your terminal does not need any sort of hard drive, only a PXE capable nic.  The PXE boot takes you to the login on the LTSP server.  It is exactly as if you were sitting in front of the LTSP server, without actually being there.  This means that installing a program on one remote terminal installs the same program on ALL terminals.  It also means that multiple monitors are extreamly easy, and user logins are portable.  Any machine that is compatible with the LTSP host operating system and has a PXE boot option can be the terminal.  I tested on three different motherboards, including one AMD and one INTEL processor.

Now I did not integrate with AD because it was a test server, and I do not have a test AD set up.  

I extended the LTSP server with FreeNX from George Wright's webpage ([http://blog.gwright.org.uk/articles/2008/07/12/freenx-package](http://blog.gwright.org.uk/articles/2008/07/12/freenx-package))  I am not a security expert, but I know that FreeNX as the remote protocol was WAY faster than VNC.  This extension allows you to not only access your user profile from any local PXE boot machine, but also remotely.

If anyone has further questions on this process let me know, it's been a long time but I think we can figure something out.

Ok back to the virtualization.  

I was reading the Sun VirtualBox User Manual (v 3.0.8 if anyone cares).  on pages 93-99 they are talking about vbox remote virtual machines.  They go into being able to connect to each virtual instance via RDP through the built in RDP server on virtalbox.  On the virtual box website ([http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)) it says "Remote Desktop Protocol. Unlike any other virtualization software, VirtualBox fully supports the standard Remote Desktop Protocol (RDP). A virtual machine can act as an RDP server, allowing you to "run" the virtual machine remotely on some thin client that merely displays the RDP data."  I know this is a payed feature, but I was wondering if you knew where the RDP server makes it's decision on which virtual machine the thin client loads.  Does it load after the user name and login, or when the thin client boots.

Sorry for misspelling.  Too lazy to spell check at the moment.  My two darling children ran my butt into the ground.

---

### Post by epsolon77 on 2009-10-10
> **scorp123 said:**
> 
My apologies for using up so much space in this thread .... I will STFU now. :-#

The information you are providing is proving invaluable to me, and I am hopeing the rest of the people that have been reading as well.  Please don't stop.

Your Ideal of the LTSP boot to a VM would work well in my case.  Each user has their machine which is the only machine they really want to use.  When one of the users sits in front of someone else's computer for the day, they would really rather see their own desktop anyway.  It would be a pill to set up, but I'm thinking we would end up taking each person's current computer, and porting it to a virtual instance, then I could use your LTSP with Virtualbox idea to allow each person's boot to send then to the LTSP login, which would load and authenticate their VM.  It's a couple extra steps to set up a new users, but will make long term maintinance SOOO much easier on me, considering all but 4 of our desktops are a minimum 5 years old.  I forsee needing to replace at least 15 desktops in the next 2 years.  Software an all that's gonna be at least 10 grand.  

For the record I am not against a paid system, but I would need to prove that a paid system will work, will work well, BEFORE any money would be spent.  So If I can get virtual box to do 90% minus a plug in that we have to pay them for to automatically connect a person's login with their VM, it's money in suns pocket.  I do really like your LTSP idea on so many levels.  LTSP is a very thin build too.  On my test I had a Pentium 4 with 256mb of ram running 4 simultaneous desktops out my cable line and into my office T1 and ran a flash game on each desktop at the same time without any noticeable lag.  This is a vast difference to our lightly used terminal server that laggs like crazy when there are three people in it, and that's on a xeon 3ghz with 3gb of ram.  So that might have great potential.  Thank you so much for the thought.

---

### Post by kevindontenville on 2009-10-15
We have been using Proxmox for a while now and mixing KVM and OVZ has been great. The new 1.4 currently beta version supports improved storage options which will open up the high availability options.

At the risk of hijacking, what gets unclear for me with the clouds, grids, clusters, hypervisors, virtual machines etc is how they all hang together with the various implementations and vague definitions. Most seem to allow the movement of live VMs from a host to another host, some with intervention and some automatically. Usually one box of processors can run many VMs and share common storage with other hosts etc

For me though, it feels like true cloud computing ought to be an autonomous self healing environment. A bunch of mixed hardware playing nicely with each other and sharing resource as needed. If hardware fails then it should quietly die off without losing a VM and the cloud should let you know. 

A bit like a cluster of hardware acting as a single instance host that is running many VMs. 

Is that too simplistic a view? Does it exist in FOSS world?

---

### Post by Denbert on 2009-11-24
> **epsolon77 said:**
> 
I extended the LTSP server with FreeNX from George Wright's webpage ([http://blog.gwright.org.uk/articles/2008/07/12/freenx-package](http://blog.gwright.org.uk/articles/2008/07/12/freenx-package))  I am not a security expert, but I know that FreeNX as the remote protocol was WAY faster than VNC.  This extension allows you to not only access your user profile from any local PXE boot machine, but also remotely.

If anyone has further questions on this process let me know, it's been a long time but I think we can figure something out.



Hi, the link is down, showing default apache webpage - I'm testing LTSP5 server in order to make an alternative Terminal Server sugestion for my daughters school, as they are planning a Terminal Server setup with +150 clients. They have received 3 offers from 3 local system integrators, all based on Windows 2008 Terminal Server!

I've made a ***[test install in vmware 2.0.1 server]("http://ubuntuforums.org/showpost.php?p=8374107&postcount=13")*** and the LTPS runs great

But the school plans to invest in 25 thin clients (for one classroom) and then they will offer access to students terminals via their own laptops, using RDP, and they also wants to give access via internet.

Please, do you have an idear give this solution based on full Ubuntu Setup?

---

### Post by epsolon77 on 2009-11-24
I'll have to check again, but I don't think freenx uses the standard RDP protocol.  It uses the NX remote client software, which is blazingly fast and free.  It's a shame the link went down, I hope it will be up soon.  In the meantime if you want to PM me your email address I'll see if I can pull my file up and send it to you.  Installing installing an NX server on top of LTSP would provide the functionality you are looking for. Local thin clients would boot off the server via PXE boot, then remote users can access the same server session via freeNX which is free, open source and available on all platforms.  The small issue with this might be that the base desktop would be ubuntu and not windows.  In my opinion not a huge deal, but that may be one of the schools requirements.  If it is you can try to run a Virtualbox instance at each local startup running whatever flavor of windows you would like.  Licensing could get expensive though on the windows side of this.

---

### Post by Denbert on 2009-11-24
> **epsolon77 said:**
> I'll have to check again, but I don't think freenx uses the standard RDP protocol.  It uses the NX remote client software, which is blazingly fast and free..

I followed this [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

and did the changes to port 8888.

For some strange reason it works whitout a glitch on local lan, but I cant connect from internet. My Firewall is set to forward TCP/UDP port 8888 to the LTSP server.

Must be something with me, changing from 2 nics to one nic.

My /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.9.12
    netmask 255.255.255.0
    network 192.168.9.0
    broadcast 192.168.9.255
    gateway 192.168.9.254
```

And dhcp3 server i working and has this in /etc/ltsp/dhcpd.conf:

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.9.0 netmask 255.255.255.0 {
    range 192.168.9.100 192.168.9.250;
    option domain-name "hegnstoften.net";
    option domain-name-servers 208.67.222.222, 208.67.220.220;
    option broadcast-address 192.168.9.255;
    option routers 192.168.9.254;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

What have I missed?

---

### Post by epsolon77 on 2009-11-24
When you say it works from the local lan, are you referring to the LTSP PXE boot or using FreeNX from a self booting OS.  I understand you can make the LTSP server work with one nic, but I highly recommend moving it to two nics, one for all the thin clients, and one for internet facing services.  This may be my inexperience as an IT person, but I found it much easier and more stable.

---

### Post by Denbert on 2009-11-24
> **epsolon77 said:**
> When you say it works from the local lan, are you referring to the LTSP PXE boot or using FreeNX from a self booting OS. 

It works in both PXE and in the FreeNX client from a Windows Client

> **epsolon77 said:**
>  I understand you can make the LTSP server work with one nic, but I highly recommend moving it to two nics, one for all the thin clients, and one for internet facing services.  This may be my inexperience as an IT person, but I found it much easier and more stable.

Yeps, The real setup ( If I can convince the School headmaster to go Linux instead of Windows) will also be with two nics

---

### Post by epsolon77 on 2009-11-24
I wonder if it is in your port forwarding.  I think free NX requires it's own port for each connection.  It starts at whatever the set is an increments up 1 for each new session.  I would check to make sure you have your incoming ports 8888 to at least 9000 open and forwarded, and make sure the recursive is ported through the same IP.  

Not to throw a stick in the mud, but one advantage to a windows terminal server environment is it's extendability onto multiple machines to cope with the load.  I'm sure there is a way to do this with freeNX, but I'm not sure what that would be.  You might want to look into ways to extend freeNX into a front end and backend solution to see if it's possible.

---

### Post by epsolon77 on 2009-11-24
> **kevindontenville said:**
> We have been using Proxmox for a while now and mixing KVM and OVZ has been great. The new 1.4 currently beta version supports improved storage options which will open up the high availability options.

At the risk of hijacking, what gets unclear for me with the clouds, grids, clusters, hypervisors, virtual machines etc is how they all hang together with the various implementations and vague definitions. Most seem to allow the movement of live VMs from a host to another host, some with intervention and some automatically. Usually one box of processors can run many VMs and share common storage with other hosts etc

For me though, it feels like true cloud computing ought to be an autonomous self healing environment. A bunch of mixed hardware playing nicely with each other and sharing resource as needed. If hardware fails then it should quietly die off without losing a VM and the cloud should let you know. 

A bit like a cluster of hardware acting as a single instance host that is running many VMs. 

Is that too simplistic a view? Does it exist in FOSS world?

Sorry it took me so long to reply kevin...  

I have not been able to test systems yet because I don't have any virtual capable processors, and only 1 64 bit processor to test on.  

Currently it seems like eucalyptus and proxmox may be self healing to an extent.  The question I have comes down to where and how virtual machines are run.  Granted this is in part because I do not have resources to test.  I can not determine if a virtual instance is run on one machine, or many.  If it is running only on one hardware platform, and that hardware platform failed, I am unsure if the system would recover the VM elsewhere and keep going or not.  I know VMware has their live migration and high availability utilities that allow this, but I can't test any free software yet to see if they will do this.  However the owners of the company I work for have been asking to get these features implemented.  This means I need a test environment to at least test the VMware stuff, so I can test proxmox and others to see how they do too.  I will keep you updated.

---

### Post by Denbert on 2009-11-24
I'll make a new tread with the FreeNX issue, as this is a Cloud thread :-)

---

### Post by dion9 on 2010-05-30
Check out this company from Switzerland, they provide a really good service.
Just finished with the trail version.

Xcloud - Mac OS X Server Hosting on Parallels Mac Bare Metal Edition

[www.innofield.com]("http://www.innofield.com/")

---

### Post by rsgooch on 2010-05-30
I use Sun's Virtualbox for virtual server deployments and it works well.  Stable, Fast and easy to setup with the GUI.  I use most of the vm headless so I configure them from the command line. 

I have been very happy with the product. I have 2 Windows 2k3 servers one of then running MS SQL 2008 the other is a DC.  I have a small 10 users windows xp based terminal server also running in a Virtualbox VM and it works great (using xp unlimited for terminal services). 

I hope this helps.

---

