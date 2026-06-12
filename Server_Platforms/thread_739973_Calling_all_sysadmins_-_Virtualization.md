---
title: "Calling all sysadmins - Virtualization"
date: 2008-03-30
forum: Server Platforms
---

### Post by mespork on 2008-03-30
Hello all,

So here is the situation. About 7 months back I moved from being a sysadmin in the corporate world into higher education. Let me tell you I walked into a heck of a situation. 

Last year all the capital budget was spent before I came on board (I am not sure what they bought with the money). When they spent this money they failed to realize that MOST of our servers are out of warranty. Now that my old boss is gone (big M$ fan) I am going to be upgrading our datacenter. 

Here is my question to you. I plan on virtualizing most of our servers due to the fact that many of the servers are under utilized. I am caught between two solutions XEN and VMWare Infrastucture. 

Does anyone have any thoughts on either of these or experience deploying them in a production environment?

Thanks

David

---

### Post by csi_ on 2008-03-30
If you have windows servers, i would recommend using Vmware. Otherwise go for XEN. Both solution are solid, but requires you to write more documentation.

---

### Post by mespork on 2008-03-30
> **csi_ said:**
> If you have windows servers, i would recommend using Vmware. Otherwise go for XEN. Both solution are solid, but requires you to write more documentation.

I have heard that, but we have been told with HVM windows virtualization is not much a problem.

We are also considering the difference in price between the solutions, XEN is much more cost effective.

---

### Post by HermanAB on 2008-03-30
Hmm, depends on your hardware - Xen doesn't work on everything, while VMware does. Also, as pointed out already, Windoze guests require VMware.

---

### Post by koenn on 2008-03-30
and if you're new to all  this, you'll appreciate the comfort of the Vmware console GUI. XEN is still a lot of commandline / text file stuff (If I'm not mistaken) and you don't want to be learning the ropes  in a live production environment. Whereas Vmware, you can learn to run it in an hour or so - lots of point and click.

---

### Post by mespork on 2008-03-31
I work allot with virualization. I do all my testing on my personal computer via virtualbox (like I said our servers are old and don't have any spares.) I also use it to build all of our deployments of clients (I had to build ALL of the msi from scratch)

I don't mind using the command line. The only thing that I worry about is the other people at work being able to use it. XEN does have an enterprise console like vmware. There also seems to be some useful opensource tools like convirt. 

I am going to build a test enviroment soon so I can test both in action.

David

---

### Post by rickyjones on 2008-03-31
I'd recommend an enterprise VMWare installation if this is going to be the new environment. I've worked with it at a fortune 500 company and I believe it is worth the cost. The ease of use of ESX server is wonderful. Dedicated servers for everything. Auto migration of virtual machines between different servers if a hardware problem is detected...

Lots of benefits to using specialized commercial software here.

-Richard

---

### Post by BillGod on 2008-03-31
I am a big vmware fan. I run it at home on my server plus an entire development environment at work.  I would always go vmware if it was me.

---

### Post by HermanAB on 2008-03-31
VMware Workstation is totally worth the $80.

Note that Virtualbox only works with Windows XP clients.  It doesn't work reliably with Win2003.

---

### Post by netlogic on 2008-03-31
I agree. VirtualBox isn't there yet for a corporate adoption. However, they have progressed a lot. VMWARE still the leader in the virtual machine market.

---

### Post by mespork on 2008-03-31
> **netlogic said:**
> I agree. VirtualBox isn't there yet for a corporate adoption. However, they have progressed a lot. VMWARE still the leader in the virtual machine market.

I am not even considering using virtualbox. It is GREAT on the desktop for test machines. However, it has too much overhead for me. I am going to order the test environment tomorrows to get a feel for both products. 

Does anyone have any experience running xen in production? I always seem to run into people that run either VMware or M$ Virtual Server.

---

### Post by koenn on 2008-03-31
> **mespork said:**
> II always seem to run into people that run either VMware or M$ Virtual Server.
So there *are* people that run MS Virtual Sevrver ..?!

---

### Post by netlogic on 2008-03-31
Of course! There are fans out there for MS VM. Why should people just reboot once for the browser updates? Why not two? Why not 10!!! MS FOREVER with the robot Love!!! Let's reboot all together! Let's salute while they all go down!

---

### Post by mespork on 2008-03-31
Yeah, we had a vendor talk about us using that... needless to say that that proposal is filed under recycling.

---

### Post by ronald.higgins on 2008-04-01
VMware has some nifty tools like the VMotion and DRS,

I'm not aware if the competition has similar features.

I like the idea of Vmotion moving Virtual Machines that are taking resource punishment and moving them to another  host that can handle the load.

Well .... my vote goes to VMware.

Some other food for thought though, VMware has a Physical to Virtual converter, does the competition have similar products ?

---

### Post by koenn on 2008-04-01
> **ronald.higgins said:**
> VMware has some nifty tools like the VMotion and DRS,
Yeah, but VMotion is only included in the Enterprise suite, with a cost of , what, 1500$ extra compaired to the starter kit ? While, when using shared storage, you can just as well bring a VM guest down on one host, start it up on another host  You can ask yourself if your business requirements justify the extra cost to avoid 20 minutes downtime. 
But that's a management decision, not an IT decision :)

---

### Post by ronald.higgins on 2008-04-01
> **koenn said:**
>  
But that's a management decision, not an IT decision :)

Lol .... i like that ... let's just pretend money isn't an problem for us :D

---

### Post by mespork on 2008-04-01
> **ronald.higgins said:**
> VMware has some nifty tools like the VMotion and DRS,

I'm not aware if the competition has similar features.

I like the idea of Vmotion moving Virtual Machines that are taking resource punishment and moving them to another  host that can handle the load.

Well .... my vote goes to VMware.

Some other food for thought though, VMware has a Physical to Virtual converter, does the competition have similar products ?


Xen enterprise has Xen motion included but not drs, but it is also about 20% the cost.

---

### Post by csi_ on 2008-04-01
> **mespork said:**
> Does anyone have any experience running xen in production? I always seem to run into people that run either VMware or M$ Virtual Server.

Last year, we started using virtualised RedHat 4 and 5 in my company. Hosts are RedHat 5. It has been working really great for now.

About two years ago, I tryed xenified Windws guest at home, I ran into UI troubles. That's the reason I don't recommend XEN for such an OS, although it is possible, it is time consuming. I personnally use KVM or qemu for Redmont guests. It is know included in kernel. Have you considered it? 

Taken your needs into account, Vmware seems the best solution. Thanx for posting feedback regarding your testing environnement.

---

### Post by Deathrend on 2008-04-01
I've never used XEN, however, we highly use VMWare ESX..  I love it personally.  We currently have 8 ESX hosts on HP DL580's, (Six running 2.6-3 Ghz Dule Crore Xeons, two with Quad Core Xeons), all of which with 60, to 120 GB's of RAM.  Each ESX hosts betwene 10, and 20 Virtual Servers.  With ESX Clustering, you get VMotion, which lets you Drag and Drop servers WHILE RUNNING from one ESX to another, with ZERO notice from the end user.  The only down side, is you also have to be running SAN's for the VMotion/HA.  The High Avalibility moves servers automaticly baised on load balancing, as well as servers that have crashed, or are crashing.

The only down side, VMWare can be very Processor dependant, if we put our two quad-core servers into the cluster with the dule cores, it kills the VMotion, as they are, they can still be cold-boot migrated, however thus isn't very desireable for high end production

---

### Post by mespork on 2008-04-01
Xen does have tools available similar to VMWare. Check out the XEN enterprise edition:

[http://www.citrixxenserver.com/products/Pages/XenEnterprise.aspx](http://www.citrixxenserver.com/products/Pages/XenEnterprise.aspx)

We are going to be testing a vmware test environment this coming week to see how they compare.

---

### Post by jcostom on 2008-04-02
> **HermanAB said:**
> VMware Workstation is totally worth the $80.

Note that Virtualbox only works with Windows XP clients.  It doesn't work reliably with Win2003.

I sort of doubt he'd be running VMware Workstation for an environment of that size, particularly given the need to have a system logged in with the software running in the foreground..  The server products are what he's looking for..

I don't want to be the guy chucking rocks at VMware, but I've been having a fair bit of trouble lately with VMware Server.  I was using 1.0.4 until this week, when I upgraded to 1.0.5.  With 1.0.4, I would periodically get VMM faults in a CentOS 4.6 guest.  Host OS is Gutsy, running a custom 2.6.24.2 kernel.  Upgrading to 1.0.5 didn't fix the problem either.  Of course, given the newer nature of my kernel, I have to use the -any-any driver updates, which may be contributing to the instability.

Were I to deploy a large-scale virtualization project today, I'd likely run VMware's ESX Server product, using VMotion.  The ability to move VMs from one physical box to another without creating downtime is ridiculously cool && useful.

---

### Post by mespork on 2008-04-08
> **jcostom said:**
> I sort of doubt he'd be running VMware Workstation for an environment of that size, particularly given the need to have a system logged in with the software running in the foreground..  The server products are what he's looking for..

I don't want to be the guy chucking rocks at VMware, but I've been having a fair bit of trouble lately with VMware Server.  I was using 1.0.4 until this week, when I upgraded to 1.0.5.  With 1.0.4, I would periodically get VMM faults in a CentOS 4.6 guest.  Host OS is Gutsy, running a custom 2.6.24.2 kernel.  Upgrading to 1.0.5 didn't fix the problem either.  Of course, given the newer nature of my kernel, I have to use the -any-any driver updates, which may be contributing to the instability.

Were I to deploy a large-scale virtualization project today, I'd likely run VMware's ESX Server product, using VMotion.  The ability to move VMs from one physical box to another without creating downtime is ridiculously cool && useful.


I have done some testing and research. The enterprise version of xen is becoming very appealing.

---

### Post by D8TA on 2008-04-21
We have a ton of ESX machines that run nicely but because of cost we are also looking closely at Xen Enterprise. We also are running some test/development VMs under Novell's Suse Linux Enterprise Server using the Xen included with the OS, Open Source version of Xen. These run nicely but if you need management console Xen Enterprise is the way to go without breaking the bank. 

Another note, if you run VMware and have Linux hosts you will need to re-run the vmware tools install everytime the kernel gets upgraded. Not a big deal if you just run a few linux VMs but if you get into 100s you are talking about a lot of management.

Just in case one of these conferences are in your area, ```
http://www.registerandcompute.com/citrix/eventSelect/eventselect.asp?specialAccess=User
```
Unlock the Power of Virtualization. May be beneficial to your project. No, I am not affiliated with Citrix either.

---

### Post by awreneau on 2008-04-21
ESX is great, we use it on a SAN and we only have 4 Linux boxes on it the rest is M$.

It's easy to test upgrades too, u can get VMWare Converter and rip the image off convert it to VMWare Server stand alone and run  your tests against the box.   Even better, if you accept the tests you can run vmware converter again and convert it back to an ESX machine.  (downside is that the conversion from vmware to esx wont overwrite the original image.)

If you're thinking backups, Virtual Consolidated Backup is a good tool for IMG level backups too.  But thats another thread.

---

### Post by scorp123 on 2008-04-21
> **HermanAB said:**
> VMware Workstation is totally worth the $80.  He was clearly talking about VMware Infrastructure ... which is somewhere in the $1500 range. VMware Workstation? Oh please .... LOL

---

### Post by scorp123 on 2008-04-21
> **mespork said:**
>   Here is my question to you. I plan on virtualizing most of our servers due to the fact that many of the servers are under utilized. I am caught between two solutions XEN and VMWare Infrastucture. 

Does anyone have any thoughts on either of these or experience deploying them in a production environment? Well, you have to know what the differences are in the ways they achieve virtualisation and if they make sense for your servers and the applications that run on them.

XEN is a para-virtualiser. So it is extremely efficient in scenarios where you want to consolidate e.g. multiple Linux servers, let's say multiple web servers. Each web server could be a XEN instance. And while XEN is fantastic for running Linux on Linux it IMHO opinion sucks at anything that is too I/O intensive, e.g. databases. I definitely would not recommend to put a heavy-duty Oracle instance into a XEN guest ... Maybe we did it wrong but the performance sucked badly.

VMware on the other hand can be very handy if you want to consolidate e.g. multiple Windows machines ... if you have the right hardware that is. We have a few Windows 2003 application servers and we migrated them into VMware guests. Now we have all these servers running on our Sun Fire X4600 M2 server, under VMware ESX. Given the right amount of disks, RAM and CPU's servers such as a X4600 or similar servers in it's class (e.g. similar offerings from HP or IBM) will do their job tip top and your users won't be able to tell that the Windows app servers they are using are in fact VMware guest sessions.

What I am trying to tell you: Both XEN and VMware have their strong points, it ultimately really depends what your applications are doing and if they could really benefit from paravirtualisation or not, and if and how far your server hardware can play along with this (e.g. do your servers already have hardware virtualisation built-in into their CPU's?).

We have both solutions and given the right job both will perform tip top.

---

### Post by koenn on 2008-04-22
> **scorp123 said:**
>  I definitely would not recommend to put a heavy-duty Oracle instance into a XEN guest ... Maybe we did it wrong but the performance sucked badly.
Kinda strange, since Oracle themselves offer Xen virtalization solutions for their rdbms. 
+ I've been told that Oracle definately doesn't like their rdbms to be running in VMware - something to do with processor licenses and only Xen being able to "guarantee" the compartimentalisation Oracle (the company) desires.

---

### Post by scorp123 on 2008-04-22
> **koenn said:**
>  Kinda strange, since Oracle themselves offer Xen virtalization solutions for their rdbms.  As I wrote above ... maybe we did it wrong. The idea to try out one of our Oracle servers inside Xen was also based on precisely what you say. But despite all tweaking and tinkering the performance we got wasn't that great. So we decided to leave Oracle alone for now.

So based on your posting I would assume you've had good experience and satisfying results so far with Oracle inside Xen?

> **koenn said:**
>  I've been told that Oracle definately doesn't like their rdbms to be running in VMware Yes, because the number of real CPU's inside a system is something Oracle is looking at when they calculate the price you will have to pay for their product. Inside a VMware environment there is no way they can really tell how many CPU's are there or not - the guest OS will only see as many CPU's as you allow it to see. So Oracle Inc. may see that as some way of cheating I guess.

---

### Post by koenn on 2008-04-23
> **scorp123 said:**
> 
So based on your posting I would assume you've had good experience and satisfying results so far with Oracle inside Xen?

I have no real experience whatsoever, other than running vmware server at home, with a debian guest + oracle express - stuff to play with and get a feel for it.

I have a vague plan for a (much needed) storage and server consolidation project at the place where I work, and I've been collecting some information just to know what my options are ; that's how I found out about Oracle + Xen, and the VMware issue with processors/licenses.

---

### Post by netlogic on 2008-04-23
The popularity gain of Xen is pretty slow. Forecasters are expecting XenSource revenue to be between $3mill to $5mill for the period. They expect VMWARE to be around $438mill. Xensource is definitely cheaper than Vmware, but I prefer going along with the winner, because it is hard to predict the responsibilities of the migration. Also, I believe ESX is more robust than Xen. Since most IT directors don't take many responsibilities and delegate their ownerships, it is better to not risk the danger of our jobs. Also, I believe ESX is superior. I think it is worth the extra money.

---

