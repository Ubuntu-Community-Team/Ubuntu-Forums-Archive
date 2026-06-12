---
title: "Server and virtualization question"
date: 2008-05-13
forum: Server Platforms
---

### Post by johan.alfa on 2008-05-13
Hello,

I would like to set up a server for a small office.
Very few users and all they need is file sharing.

But I also need to setup a web server on the same machine.
I would prefer to use a separate machine for the webserver but we can not afford that. would it make sense to run the webserver as a virtual machine so that a potential hacker can not attack the actual server?

thank you,

greetings

---

### Post by songshu on 2008-05-13
yes it would make sense, very much sense actually.
i would say run both of them as a virtual server.

small office? all you need is a file server is what you said last year right? 
this year you want a web server
next year? will you still be happy with the relatively cheap but sometimes flaky e-mail provider?
companies grow and there needs seem to evolve with them, PC hardware is cheap and powerful and Linux runs on anything so you have room to grow without shelling out a lot of $$ for something you don't need yet.

running virtual servers can provide the means to a secure setup, but are not secure by definition, just like servers on separate hardware you still need to have an idea about what you are doing.

---

### Post by johan.alfa on 2008-05-13
I have been reading a bit but still have some doubts.
Can the vmware virtualization done completely free or should I buy something from vmware?

greetings,

Johan

---

### Post by johnwillis on 2008-05-13
I use visualization at work on our core servers

I would recommend getting VMWare Workstation if your budget can afford it, it is very easy to use, creating a network and "teams" (a group of virtual appliances/machines you can control and network together) is simple.

I did start off with QEMU/Virtualbox but VMWare worked out the box.

It entirely depends on your needs. If you want a simple virtual server running through NAT then your needs will suit VirtualBox / VMWare Server. But if you plan on moving more and more services in house and virtualized then I'd seriously consider VMWare Workstation.

You can also take a look into XEN to virtualise servers. But I have never used this.

Let us all know what you decide :)

-J

---

### Post by songshu on 2008-05-14
so many people so many choices,

vmware can be done without an extra license.

personaly i find vmware slow (unless you want to go with the expensive ESX version), but that also depends on your hardware and the number of virtual servers you want to deploy.

xen i found a bit faster, and liked using it.

above two or "full" virtualisation.

personaly i use Vserver on debian, its very light but you have to consider that all virtual servers use one single kernel, namely the one of the host.

KVM i never tried but its somewhere comparable to Vserver AND its the one preferred by Ubuntu on Hardy.

---

### Post by windependence on 2008-05-14
> **johan.alfa said:**
> I have been reading a bit but still have some doubts.
Can the vmware virtualization done completely free or should I buy something from vmware?

greetings,

Johan

Vmware Server is free and a very good product. Although VMware says they don't recommend it for production use, I have to question their motives as I have been running mail, web, and database servers in production on that product for a year now with no problems. 

The only thing about VMware is it need lots of RAM. so buy whatever you can afford. CPU power seems not to be too much of an issue.

Xen is nice but funky lloading the OS from CD as you have to do some pretty convoluted stuff to chage CDs.

VMware also has the largest choice of guest OS. I am running Linux as the host (Ubuntu server) and FreeBSD as the guests without any problems.

-Tim

---

### Post by johan.alfa on 2008-05-14
I heard somewhere vmware server is free beacause it has debug code in it. Is this right?

greetings,

---

### Post by windependence on 2008-05-14
> **johan.alfa said:**
> I heard somewhere vmware server is free beacause it has debug code in it. Is this right?

greetings,

No, this not true. It is their Open Source product and quite good I might add. Give it a try and see for yourself.

-Tim

---

### Post by josir on 2008-06-03
I've already tried vmware and kvm/qemu. 

I think vmware is easier to install/configure but I found kvm/qemu much more faster (but it depends if your hardware accepts its technology). 

Good Luck,
Josir

---

### Post by mpzarde on 2008-06-03
I can speak to the VMWare ESX product; I installed the thirty day eval to try it out and was up and running in a few hours.

You install one CD which installs the host OS on your PC at which point you're done with the host install and are ready to setup guest OSs. 

You go to a web site on your VMWare machine which allows you do download the ESX client (Windows Only) which you then use to manage your machine, install OSs, etc...

Was absolutely painless, I was so happy with it I saved my Coke bottles and shelled out the $499 for the software which has been working 100% for three months now.

The downside in your scenario is that you could probably buy a new hardware device for $499. 

In my case however I still have enough capacity on my server to add a few more OSs if I want to.

Currently running Ubuntu Gutsy and Windows 2003 server on a Dell PowerEdge 840 with a Pentim D 3.0GHZ and 4GB RAM.

Performance is great on both sides (OSs).

Someone else mentioned XEN which I believe is still free for now but has been bought by a commercial interest lately.

I believe XEN is essentially the same approach where you have a Linux based host on which you install guest OSs.

---

### Post by windependence on 2008-06-04
Vmware server 1.5 is OSS and free. Unlike ESX it needs to run on a Linux or Windows box. ESX installs as it's own OS and is quite nice, but Server is just as good IMHO and you just have to install it on a host OS. I have servers running on 1.4 for almost a year now with no problems.

-Tim

---

### Post by gtdaqua on 2008-06-04
> **windependence said:**
> Vmware server 1.5 is OSS and free. Unlike ESX it needs to run on a Linux or Windows box. ESX installs as it's own OS and is quite nice, but Server is just as good IMHO and you just have to install it on a host OS. I have servers running on 1.4 for almost a year now with no problems.

-Tim

You mean 1.0.5 and not 1.5. They are actually good for production environment. Version 2 is however in beta and not a good one for production.

---

### Post by mpzarde on 2008-06-04
My experience with VMWare server was less stellar (I'm sure it works fine, we just has problems with it). 

Whenever the host OS restarted VMWare server wouldn't always come up, then some of the admins would try to start it in separate RDP sessions (host OS was Windows) and it wouldn't start and every so often it would just hang for no good reason.

This was running the TWiki appliance under Windows. 

For our office it was fine since it was an internal solution, just not sure I'd trust it for a production of external facing environment.

---

### Post by fisionchips on 2008-06-04
We have just started out on the first small steps to virtualization with a Dell PowerEdge SC1430 Intel Xeon quad Core processor 4GB Ram 2x 250GB HDD in a mirrored raid 1 configuration.  On this we have put 64bit Ubuntu Hardy Heron, Vmware Server 1.0.5 which is running SBS 2003 as the single virtual machine (at the moment).  

There are a couple of problems, one is (we think) fairly innocuous as there isn't a lot we can do about it and we think it doesn't have a great impact, the other is pretty serious which I hope someone can help with here.  

First we have a WD USB connected drive which we have had to connect using USB 1.0 because USB 2.0 isn't yet supported in VMWare - This drive hosts a Pervasive/Exchequer database in use by multiple clients. Any ideas on how this can be better connected (we don't want to use the beta versions of VMWare software in this environment) would be welcome. 

Secondly - the VMware machine seems to be stopping at around 10 at night for reasons unknown.  This is a few hours after all bods in the office have gone home and the only thing that is running is the nightly backups (runs on one of the connected clients not on the server). The backup software backs the data on the connected USB drive to the C drive of the client machine running the backup.  


Could the backups be causing a failure? 
Are there config settings we need to change to ensure VMware is kept alive?  Is there an automatic sleep setting in Ubuntu on idle or inactive processes such as VMWare or is this a VMWare issue.  What system logs would be most useful in Ubuntu/Vmware (and where can they be found?) to indicate the failure (if any) type?  We use webmin to view the Ubuntu logs and there doesn't seem to be anything there which indicates a shutdown.  The SBS 2003 logs just show normal up to a certain time and then end - no shutdown sequence.

Any ideas would be most welcome... :)

---

### Post by gtdaqua on 2008-06-05
> 
First we have a WD USB connected drive which we have had to connect using USB 1.0 because USB 2.0 isn't yet supported in VMWare - This drive hosts a Pervasive/Exchequer database in use by multiple clients. Any ideas on how this can be better connected (we don't want to use the beta versions of VMWare software in this environment) would be welcome. 

Try VMware's ESX - its not free. USB 2.0 is not supported until VMware 2.0 officially comes out - this is free version. Its still in beta and therefore not recommended for production use.

> 

Secondly - the VMware machine seems to be stopping at around 10 at night for reasons unknown. This is a few hours after all bods in the office have gone home and the only thing that is running is the nightly backups (runs on one of the connected clients not on the server). The backup software backs the data on the connected USB drive to the C drive of the client machine running the backup.


Or the VMs shutting down or the VMware services in Hardy are going out? If your swap setting is incorrect for a 4GB server, your VMware process will die eventually - although this should happen moments after your server is powered on. 

Can you do a 'free -m' and post the output? 

Also, if you are not going to expand your SC1430 beyond 4GB RAM, I would suggest you install Ubuntu Juice (JeOS). JeOS Edition is 32-bit and just has bare metal parts to run an OS and an improved kernel for virtualization. A 64-bit OS is not going to be great on machines under 4GB RAM. Your call here.

See Ubuntu JeOS [here]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos").

---

### Post by fisionchips on 2008-06-05
Thank you very much gtdaqua...  :KS

We will look at the ESX VMWare as a possibility but it might be worth our while hanging around for the new version of VMWare server if the USB issue causes no major problems and we can live with the 32bit for now. 

We are also looking at JeOS as a more efficient OS for our environment. 

We still don't have much idea what is causing the overnight system failure.  The system remains stable during the day when it is being used... The VMWare service was still on, and the SBS logs reveal nothing, the machine just seems to freeze...  which probably brings us back to the memory contraints you suggest could be causing problems. :confused:


free -m results were as follows:

Total 3962, Used 3836, Free 125, Shared 0, Buffers 13, cached 3649, -/+Buffers/cache used 173, free 3788, Swap total 11609, used 0, free 11609. 

We have tweaked the reserve memory to 3183 in VMWare to yield: Used 3710 and Free 252, Buffers 12, cached 3550

During use the free memory seems to drop to around thirty and stay around there.  That seems very low (I presume this is in MB - if it's bytes or KB I'd think we are in deep doo doos) but I have no idea what acceptable tolerances are.  

testing JeOS... this might well solve a lot of problems..

---

### Post by mealan on 2008-06-05
that sometimes wont report all the memory that ubuntu is using. I have several companies up and running on esx and ubuntu+vmwareserver if they didn't want to shell out the coin, just curious, whatever. these are production sql and web servers, not hit to hard, but still in production neither the less. I have had 1 or two problems but nothing major, most of it was getting the web ui to come back to life after a restart, I can share the information I collected if you would like it, but would like to point out I certainly didn't make it!

I prefer Vmware the best of zen or virtuozzo, but I am might be baised because I am a vcp. 

check the hard disk space on the sbs vm, sbs is by all means a hog and you might be hitting the limit at night, so make sure the page file has a set limit,

also, about the b2d problem, to get around it I made the host os (ubuntu 7.10 server) a samba server and then just mapped a drive in the sbs box. works awesome and very fast. If you need to use it on other windows box's, just use 3g ntfs

Alan

---

### Post by gtdaqua on 2008-06-05
> 
Total 3962, Used 3836, Free 125, Shared 0, Buffers 13, cached 3649, -/+Buffers/cache used 173, free 3788, Swap total 11609, used 0, free 11609.


Your ideal swap should always be 1.5x the Physical Memory and not more the 2x. For 4GB RAM, ideal swap is between 6GB and 8GB. But you have 11609 MB???? Thats way too high! 

Linux grabs all system memory even if you have 32GB - Its for good, don't worry. Linux will release the memory to processes as required. Thats how the architechture is. 

When the VM system is  freezing, run 'top' on the ubuntu server and notice which process is consuming the CPU and memory.

---

### Post by gtdaqua on 2008-06-05
> **mealan said:**
> ........

 I have had 1 or two problems but nothing major, most of it was getting the web ui to come back to life after a restart, I can share the information I collected if you would like it, but would like to point out I certainly didn't make it!

Alan


Bringing the web console is easy. You have to do "sudo /etc/init.d/vmware-config-mui.pl" and accept the default options. Only then Web UI will start. You can automate this by adding it to your startup. Edit "/etc/rc.local" and just before the line "exit 0" type: 

```

vmware-config-mui.pl -d

```

That will fire the web console with the default option (without user intervention) and listen on SSL port 8333.

Note: all commands specified inside /etc/rc.local with run with root privileges - so you don't have to 'sudo' them.

---

### Post by fisionchips on 2008-06-05
Thanks Alan, 

I think the beauty of ESX is that it is standalone which is arguably one less OS to administrate.  The disadvantage is that with free options out there, for a small company like ours, it is hard to justify the outlay when a free offering will achieve what we want. 

We have set aside a volume for the page file for SBS and that is 16GB - I can't see that it would be doing a lot of paging in an effective idle time though, then again...  
> 
also, about the b2d problem, to get around it I made the host os (ubuntu 7.10 server) a samba server and then just mapped a drive in the sbs box. works awesome and very fast. If you need to use it on other windows box's, just use 3g ntfs 

Followed you all the way there right up to the 3g ntfs bit?  

Good idea though - Thanks. 
> 
Your ideal swap should always be 1.5x the Physical Memory and not more the 2x. For 4GB RAM, ideal swap is between 6GB and 8GB. But you have 11609 MB???? Thats way too high!

Linux grabs all system memory even if you have 32GB - Its for good, don't worry. Linux will release the memory to processes as required. Thats how the architechture is.

When the VM system is freezing, run 'top' on the ubuntu server and notice which process is consuming the CPU and memory.

Thanks Gtdaqua - makes sense.

---

### Post by gtdaqua on 2008-06-05
ntfs-3g is package for Ubuntu to read and write on NTFS partitions. So your linux clients can directly access a NTFS partition. Its not required if you are using hosting your files through standards based protocols -like FTP, HTTP etc. 


16GB of swap for the SBS?? Swapping principle applies to Windows too. Too much Swap on windows is a definite killer of your OS. Windows is not equal to performance; as such, you have to do a lot of tweaking on a WinOS for a decent performance. Follow swapping rules to the letter on Windows machines. Might save you.

Go for ESX if your accountant allows the spending. It leaves an utra-minimal footprint - about 32 MB I guess. The ESX kernel still is kickstarted by linux modules even though VMware's own code runs the OS.

---

### Post by fisionchips on 2008-06-05
aha! 

We had established a large partition for the page file (supposed to be double the possible page file size apparently) but had set the page file size incorrectly to 8GB.  As we have defined the memory allocation for SBS as being 3GB if we set the pagefile maximum size as being 4.5GB does that sound reasonable?  Is it better to start out with an an initial smaller size of say 2GB and allow it to allocate to the maximum as required? 

If ESX is worth beating the accountant up then I might well go for it - double advantage :lolflag:

Thanks!

---

### Post by gtdaqua on 2008-06-05
For 3GB RAM in Windows Server: Swap Size - Initial: 4600MB; Max: 6000MB;

That should be ok. Even better is when the swap is physically located on a different controller or over a Gigabit/10G iSCSI box. 

Am going offline now and will be back in 12 hours! 

Yeah, ESX is ok if you got the money. Personally, ESX license is pricey because of no 'real' competitors. And you must to buy that license with 'support' which is half the license price! Worth for fatter customers! ;)

---

### Post by gtdaqua on 2008-06-05
For 3GB RAM in Windows Server: Swap Size - Initial: 4600MB; Max: 6000MB;

That should be ok. Even better is when the swap is physically located on a different controller or over a Gigabit/10G iSCSI box. 

Am going offline now and will be back in 12 hours! 

Yeah, ESX is ok if you got the money. Personally, ESX license is pricey because of no 'real' competitors. And you must to buy that license with 'support' which is half the license price! Worth for fatter customers! ;)

---

### Post by fisionchips on 2008-06-05
Excellent.  Thanks again.  We will make a few changes and monitor the situation and post back.  

> Yeah, ESX is ok if you got the money. Personally, ESX license is pricey because of no 'real' competitors. And you must to buy that license with 'support' which is half the license price! Worth for fatter customers!


Shame I was rather looking forward to clubbing the accountant...

---

### Post by mpzarde on 2008-06-05
> **fisionchips said:**
> Excellent.  Thanks again.  We will make a few changes and monitor the situation and post back.  



Shame I was rather looking forward to clubbing the accountant...

You can get ESX for a single server for $499, not so bad, and for the size of box you described you should be able to run several more VMs without too much trouble.

Although that $499 price might be for up to two cores or a single physical cpu, not sure, their licensing is so bizarre.

---

### Post by windependence on 2008-06-05
I wouldn't recommed running any virtualization on top of Windoze, but that's just me.

You may wish to consider 32 bit Ubuntu for the underlying host because VMware server is a 32 bit application anyway and 64 bit has been problematic for me. You can still run 64 bit guests on top of the 32 bit host. All my guests are FreeBSD so I don't hve any experience running Ubuntu as a guest. The suggestion to use JEos is a good one.

Never any problem with swap files, only if they were too small. Bigger has not been a problem. I use 2x RAM as a guide with no problems. 

ESX is certainly good but probably not necessary.

-Tim

---

### Post by gtdaqua on 2008-06-06
> You can still run 64 bit guests on top of the 32 bit host.

You wud typically use 64-bit on machine that has highger than 4GB RAM. If you want to achieve this, you would install a 64-bit base OS. Running a 32-bit base OS in PAE and then running a 64-bit atop doesnt make much sense; Of course, you CAN achieve by using HDD space as additional memory for the VM. But that actually achieves nothing - performance wise.

> 
I wouldn't recommed running any virtualization on top of Windoze, but that's just me.

Me too! A very unreliable OS in terms of consumption of memory & CPU with no regards to other applications (VMs) running.

---

### Post by fisionchips on 2008-06-06
> A very unreliable OS in terms of consumption of memory & CPU with no regards to other applications (VMs) running.

Linux is inherently more secure as well? 

We changed the swap file in SBS to a more sensible size but we couldn't find a way to change the ubuntu swap file size?  It is still over 11,000

---

### Post by gtdaqua on 2008-06-06
You have to reconfigure your swap drive.

In a nuthell: Boot using a live CD and delete the swap partition. Reboot. 
Then create a fresh swap partition after booting into Ubuntu. Reboot again.

Need a walkthrough?

> Linux is inherently more secure as well? 

Actually, you should see it as windows is more insecure. See like this: There is the first house with large holes; and there is second simple house with no  holes. Commonsense wise, wat wud you say? Second is more secure or first one is insecure? 

Linux was built as to how systems are supposed to behave. M$ put us in mind frame that:

after a few weeks any OS would eventually slow down
more programs you install, computer will become slow

Linux is totally against that and people are surprised to see that. Think why would your computer slow down after installing a dozen games or apps? Should your computer be calling all the apps all the time? only then it wud be slow. 

Unless M$ turns around and gets it act right, they are going to keep losing on 'reliability' which is imperative for us sysadmins.

Btw, how is the juice coming?

---

### Post by fisionchips on 2008-06-06
> In a nuthell: Boot using a live CD and delete the swap partition. Reboot.
Then create a fresh swap partition after booting into Ubuntu. Reboot again.

Walkthrough would be very useful or a link to where the info can be found - thanks for the offer.   

The USB drive we are connecting is FAT (we inherited this one).  This is something I'd really like to change.  We have some HDDs hanging around including a WD raptor so I am thinking along the lines of networking them and moving the data from the FAT32 drive - reformatting the whole thing and making it NTFS.  

> Actually, you should see it as windows is more insecure. See like this: There is the first house with large holes; and there is second simple house with no holes. Commonsense wise, wat wud you say? Second is more secure or first one is insecure?Linux was built as to how systems are supposed to behave. M$ put us in mind frame that:

after a few weeks any OS would eventually slow down
more programs you install, computer will become slow

Linux is totally against that and people are surprised to see that. Think why would your computer slow down after installing a dozen games or apps? Should your computer be calling all the apps all the time? only then it wud be slow.

Unless M$ turns around and gets it act right, they are going to keep losing on 'reliability' which is imperative for us sysadmins.

Btw, how is the juice coming?

Absolutely agree:  
  
Unfortunately the MS Windows systems were built to satisfy the *unpicky* needs of the mass market rather than the rather more selective needs of the IT technicians of the time (who, if I remember, were furiously installing OS/2 on their PCs in opposition - shame IBM won't open source it: [http://www.theregister.co.uk/2008/01/22/os2_history/]("http://www.theregister.co.uk/2008/01/22/os2_history/")).  

I think things will slowly change, MS software is expensive and suffers from 'holey house' syndrome. There are now so many excellent, free, secure and 'easy to use', Open Source software offerings about.  The average user isn't going to worry about whether or not their PC will slow down after a few weeks or perhaps even that it is insecure...  but tell them what the OS is going to cost when there is a good, easy to use, free alternative gets their attention... 

My colleague has installed Juice on a VM on one of our PC's:  I was trying out the VMWare Player and downloaded the Juice Hardy appliance.... then became rather distracted by the Open Source ERP appliance TinyERP - which I will be looking at in detail later lol. 

One thing that is bothering us is that we can't find any references/documentation on Juice being used as a host.. plenty about setting it up as an appliance but we are little lost in the fog here...

---

### Post by gtdaqua on 2008-06-06
> One thing that is bothering us is that we can't find any references/documentation on Juice being used as a host.. plenty about setting it up as an appliance but we are little lost in the fog here...

Juice should be on the host and its been there since 2007. Don't install this inside a VM. Don't worry about its reliability - its from Canonical's shelves. Should be good to go with this. Or simply go for Debian Etch! 


Boot from Live CD. Open terminal and type "sudo fdisk -l". You should see something like this:

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1891    15189426   83  Linux
/dev/sda2            2029        9726    61834185    5  Extended
/dev/sda5            2243        6200    31792603+  83  Linux
/dev/sda6            6201        9726    28322563+  83  Linux
/dev/sda7            2030        2242     1710891   82  Linux swap / Solaris

```

In the above case: "/dev/sda7" is hosting the swap drive. Then type "sudo fdisk /dev/sda". You should get this output:

```

The number of cylinders for this disk is set to 9726.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):

```
Press "p" to print the partitions:
```

Command (m for help): p

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1891    15189426   83  Linux
/dev/sda2            2029        9726    61834185    5  Extended
/dev/sda5            2243        6200    31792603+  83  Linux
/dev/sda6            6201        9726    28322563+  83  Linux
/dev/sda7            2030        2242     1710891   82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help):

```

Now press "d" to delete a partition and it will ask the number. Just type the correct "dev/sd"x" number of the swap drive and it will be gone. 

Press 'm' for help there and you can easily create a swap drive. Get past this stage and reboot and tell me how it went. I will tell you wat next to do.

Fancy a reading, then go here: [The Structural Failures of Windows]("http://www.theinquirer.net/en/inquirer/news/2004/04/13/the-structural-failures-of-windows"). Give yourself a 'sabash' if you make it to the end of the article! The last 2 paragraphs are fantastic.

---

### Post by fisionchips on 2008-06-06
Thanks again gtdaqua - that's really helpful. 

My colleague RBZ43 will use this info and try it out later and get back to you.  

Thanks for the history link.  I didn't make it to the end ... yet.   

I can remember a few of my colleagues beaming at the idea they had OS/2 on their PCs instead of Windows...

---

### Post by gtdaqua on 2008-06-06
> I can remember a few of my colleagues beaming at the idea they had OS/2 on their PCs instead of Windows...

House is good but no 'furniture' would be made for it. Thats why it had to go!

---

### Post by fisionchips on 2008-06-06
> House is good but no 'furniture' would be made for it.

lol - I used it a few times but always had trouble finding the door...

---

### Post by rbz43 on 2008-06-11
Thanks for the guide gtdaqua, i have now changed our swap partition to 5gb, everything seems to be running ok, but will have to wait till tonight to see if that solves the crashing issue. Is there anything else you would recommend us to change from what we have told you so far?

---

### Post by thedevnull on 2008-06-11
> **windependence said:**
> Vmware server 1.5 is OSS and free. Unlike ESX it needs to run on a Linux or Windows box. ESX installs as it's own OS and is quite nice, but Server is just as good IMHO and you just have to install it on a host OS. I have servers running on 1.4 for almost a year now with no problems.

-Tim

Tim,

VMWare is NOT OPEN SOURCE, its Freeware.  There is a HUGE difference between the two.  Don't hold your breath for EMC to open source it..

Go with Xen, QEMU,  or Virtual Box if you want real FOSS.

---

### Post by WallyWest on 2008-06-11
I am a wage for the network department in the Smeal college of business at PSU and we are seriously looking at VMware's ESXi product. My brother who is a top consultant for Accenture heavily pushes this product every day. It is very versatile and worth a serious look because of its VMotion capability and the ability to be run without a "host" OS. Of course a SAN would be needed for the VMotion to work but this investment now would mean the ability to keep all your virtual machines running while migrating them to other physical hosts. That could end up being extremely useful in a long term situation.

---

### Post by ixus_123 on 2008-06-12
Just found this browsing as I want to set up a few personal servers on a single machine using vmware.

I thought I'd throw my opinion on swap size into the mix - I don't see much benefit in having a swap file larger than 2GB on a single partition.

The old rule of 2x physical RAM harks back to days when cost really limited RAM.  These days when you can have 32GB GB on a cheap tyan mobo or dell server, double or equal the ram is not practical as for one it would waste disk space but more importantly do you really want you server thrashing on the swap partition?

I guess is largely depends on what your server does and if anyone is around to support it. I'd much rather have my server fall over and die from an out of memory kernel panic caused by running out of swap than having everything grind to a crawl due to swap space thrashing.

At the end of the day, if your server keeps falling over due to out of memory crashes, then you simply need to add more RAM :)

---

### Post by shannondoko on 2008-06-12
This has been an interesting thread, I'm just curious, what exactly do you think a good swap size for 24GB of ram should be? 


I have 2 server 2k3 boxes running under 8.04 server vmware server

both are DC's and one is a file server

I've noticed that running AV (es-et if that makes a differnce) or doing any major amount of file copying the guest pretty much completely locks up. 

In keeping with the suggestions:
What I decided to do in our environment, we have 5 Host servers

On each Physical server we have 1 nic per guest, so we don't tank each nic. 

Then we have one extra nic for the management nic, this nic is part of it's own seperate network. On it's own switch. With on box where we can manage our vm's without having to worry about other people accessing them, or wasting bandwidth on the network. 

I'm aware that second idea doesn't work in bigger environments, but if you're on the small side like us, it should work pretty well.

---

### Post by gtdaqua on 2008-06-13
> **thedevnull said:**
> Tim,

VMWare is NOT OPEN SOURCE, its Freeware.  There is a HUGE difference between the two.  Don't hold your breath for EMC to open source it..

Go with Xen, QEMU,  or Virtual Box if you want real FOSS.

There is indeed an open source VMWare Server version. 
See [here]("http://www.vmware.com/download/server/open_source.html").

Other Open-source VMware products are [here]("http://www.vmware.com/download/open_source.html").

---

### Post by gtdaqua on 2008-06-13
> **shannondoko said:**
> This has been an interesting thread, I'm just curious, what exactly do you think a good swap size for 24GB of ram should be? 


I have 2 server 2k3 boxes running under 8.04 server vmware server

both are DC's and one is a file server

I've noticed that running AV (es-et if that makes a differnce) or doing any major amount of file copying the guest pretty much completely locks up. 

In keeping with the suggestions:
What I decided to do in our environment, we have 5 Host servers

On each Physical server we have 1 nic per guest, so we don't tank each nic. 

Then we have one extra nic for the management nic, this nic is part of it's own seperate network. On it's own switch. With on box where we can manage our vm's without having to worry about other people accessing them, or wasting bandwidth on the network. 

I'm aware that second idea doesn't work in bigger environments, but if you're on the small side like us, it should work pretty well.

See post #39. If you a lot of physical RAM, then you don't want to swap much. You could tweak your 'swappiness' too.

Type:
```

cat /proc/sys/vm/swappiness

```

The value will tell your default swapping priority. Higher the number, your machine will depend more on swap memory. The default value is 60.

For 24GB, you could positively set the value to 10 so that actual memory is used in priority. This will be a great performance boost. You could set the value to 0 also, and achieve max performance but in case you run of RAM, you could be in trouble. 

Modify by:
```

sudo nano /etc/sysctl.conf

```

Add the following line at the end of the file:
```

vm.swappiness = 10

```
Save the file. Exit nano and restart the machine and type the command "cat /proc/sys/vm/swappiness". You should see 10 now.

---

### Post by rbz43 on 2008-06-13
The server seems to be running much better now and has not crashed overnight for the last two nights, but we are still having problems when the server is idle. I set up servers alive to monitor the server and woke up to 30 emails from the server going up and down overnight. Cant find anything in the logs that point to anything, anyone got any ideas?

---

### Post by gtdaqua on 2008-06-13
> 
but we are still having problems when the server is idle. I set up servers alive to monitor the server and woke up to 30 emails from the server going up and down overnight.

What exact problems when idling? 
Wat sort of emails and going to whom?

> Cant find anything in the logs that point to anything, anyone got any ideas?
where exactly are you looking for the logs?

---

### Post by rbz43 on 2008-06-13
i set up servers alive on another machine to monitor the small business server, which pings it every 5 minutes then emails me if it doesn't respond. before changing the swap file it would do this and then eventually not come back up and be frozen when we return in the morning, which happened every night last week.

I have briefly looked in the logs for small business server, vmware and ubuntu but can't find anything, i will look at them more thoroughly later when i get time.

---

### Post by thedevnull on 2008-06-13
> **gtdaqua said:**
> There is indeed an open source VMWare Server version. 
See [here]("http://www.vmware.com/download/server/open_source.html").

Other Open-source VMware products are [here]("http://www.vmware.com/download/open_source.html").

Hey there,

VMWare server is NOT open source, its freeware.  Totally different.  As you know most people are downloading the freeware version and NOT the supposed "open" one you reference.The link you reference states that its a "modified version" and states no OSI approved license.  What is it under?   

VMware Server Modified Source
Released 10/20/04
Download .tar file

Do you know of any official statement from VMWare on the license its under?  Strange I can't seem to find it on their site...

---

### Post by windependence on 2008-06-14
> **thedevnull said:**
> Tim,

VMWare is NOT OPEN SOURCE, its Freeware.  There is a HUGE difference between the two.  Don't hold your breath for EMC to open source it..

Go with Xen, QEMU,  or Virtual Box if you want real FOSS.

In fact, as gtdaqua pointed out it IS open source, and in fact it was born from OSS. EMC merely "acquired" it as happens to most good OSS unfortunately. The good thing is that usually, the OSS is forked into another product since the code can't be restricted. this results in a paid version and an OSS version which gives you a choice, and that's what it's all about. I stick with OSS whever possible, BUT, sometimes paid software is the only viable choice, especially in the server space.

[http://www.vmware.com/resources/opensource/](http://www.vmware.com/resources/opensource/)

If you look at this page you will see they actually call these versions "open source":

[http://www.vmware.com/download/open_source.html](http://www.vmware.com/download/open_source.html)

-Tim

---

### Post by shannondoko on 2008-06-30
Does anyone know if there is a way to dump all the RAM? I'm concerned that by turning off the swap some of the VM's are staying in RAM and not clearing out. I'd like to just ensure it gets cleared every night.

---

### Post by windependence on 2008-06-30
I don't turn off the swap on my individual VMs, in fact I still use swap on my host OS. That being said, yes there is a way to clear RAM, but I'm curious as to why. If for security you are way more paranoid than myself and I didn't think that was possible. :)

VMware will take all your RAM and seem like it's using more than it really is. This is so that it can give RAM where it's needed to the VMs. Not really a problem, at least it hasn't been for me as of yet.

-Tim

---

### Post by shannondoko on 2008-06-30
No I'm not paranoid at all. My real concern is that it's having a hard time flushing the RAM. The concern is that RAM is full of useless things and it can't flush it to make room for needed things. I've been told Linux doesn't do a good job with memory management.

---

### Post by windependence on 2008-06-30
On the contrary, Linux is MUCH better than Windoze on memory management. One thing you have to remember about virtualization is that it needs a good amount of memory. You have your VMs, and you also have your host OS or if you are using paid software your VM software still needs memory. Processor seems not to be too important at least in my experience, but memory is critical. As an example, I am just now finishing up a server that will host about 5 VMs and I have 12 gigs of memory in it.

-Tim

---

### Post by shannondoko on 2008-06-30
Haha I want to make it abundantly clear that I knew linux was better than windows with most everything server related. 

The box in question has 3 VM's with the full 3.6GB of RAM. The host OS (ubuntu server 7.10) has 24GB of RAM

---

### Post by gtdaqua on 2008-07-01
> **shannondoko said:**
> No I'm not paranoid at all. My real concern is that it's having a hard time flushing the RAM. The concern is that RAM is full of useless things and it can't flush it to make room for needed things. I've been told Linux doesn't do a good job with memory management.

Linux does a good job with memory - way better than windows does.
If you want your windows guests to work faster, apply these at end of the vmx file of your VM:

```

MemTrimRate = "0"
sched.mem.pshare.enable = "FALSE"
MemAllowAutoScaleDown = "FALSE"

```

On the base-server, consider these as well if you have got a good amount of memory (>= 4GB)

Edit the /etc/sysctl.conf file to include these:
```

vm.swappiness=0
vm.overcommit_memory=1
vm.dirty_background_ratio=5
vm.dirty_ratio=10
vm.dirty_expire_centisecs=1000
dev.rtc.max-user-freq=1024

```

Its a given fact that anything runs on physical RAM is faster. Try not to swap. The above tweak tells linux not to use swap unless it has run out of memory.

There are some tweaks that you can add based on file systems which will 'significantly' increase your host and VM performance. You can see clearly see the performance improvement between stock settings and tweaked settings. Let me know if you want these too.

---

### Post by windependence on 2008-07-01
Try what gtdaqua suggested above, and also, if you are running two virtual processors, set it back to one. There have been some issues with the experimental SMP.

-Tim

---

### Post by shannondoko on 2008-07-01
> **gtdaqua said:**
> Linux does a good job with memory - way better than 
There are some tweaks that you can add based on file systems which will 'significantly' increase your host and VM performance. You can see clearly see the performance improvement between stock settings and tweaked settings. Let me know if you want these too.



I am very interested please elaborate. I want these servers to scream.

---

### Post by promodus on 2008-07-01
> **mpzarde said:**
> My experience with VMWare server was less stellar (I'm sure it works fine, we just has problems with it). 

Whenever the host OS restarted VMWare server wouldn't always come up, then some of the admins would try to start it in separate RDP sessions (host OS was Windows) and it wouldn't start and every so often it would just hang for no good reason.

This was running the TWiki appliance under Windows. 

For our office it was fine since it was an internal solution, just not sure I'd trust it for a production of external facing environment.

VMWare server, in your example, is not installed properly.
All my VM's shut down when my host is told to shut down.
I have VM's that start automatically when the host starts.

I would:
*Verify your host hardware is working correctly and is stable.
*run vmware-config.pl script
*Check VM settings > Options > Startup/Shutdown.

I would definitely trust it for production environments. However, for production based environments I'd consider ESX Server instead, it's always good to have support if it's needed. Depends on the costs of downtime.

edit: My Bad, the host OS was windows?  That's the first mistake :)

---

### Post by promodus on 2008-07-01
> **shannondoko said:**
> This has been an interesting thread, I'm just curious, what exactly do you think a good swap size for 24GB of ram should be? 


I have 2 server 2k3 boxes running under 8.04 server vmware server

both are DC's and one is a file server

I've noticed that running AV (es-et if that makes a differnce) or doing any major amount of file copying the guest pretty much completely locks up. 

In keeping with the suggestions:
What I decided to do in our environment, we have 5 Host servers

On each Physical server we have 1 nic per guest, so we don't tank each nic. 

Then we have one extra nic for the management nic, this nic is part of it's own seperate network. On it's own switch. With on box where we can manage our vm's without having to worry about other people accessing them, or wasting bandwidth on the network. 

I'm aware that second idea doesn't work in bigger environments, but if you're on the small side like us, it should work pretty well.

What's your disk storage for those machines? 
I wouldn't recommend using fake raid or software RAID in a situation like that. The problem of nearly locking up may be the result that disk IO can't keep up between the two machines and possibly the host.

---

### Post by shannondoko on 2008-07-01
> **promodus said:**
> What's your disk storage for those machines? 
I wouldn't recommend using fake raid or software RAID in a situation like that. The problem of nearly locking up may be the result that disk IO can't keep up between the two machines and possibly the host.


I have 4TB in setup as RAID 10 2TB of actual space to work with. It's a dell 2900 perc 5i controller. I highly doubt it's a software RAID but I don't truly know for sure.

---

### Post by promodus on 2008-07-01
> **shannondoko said:**
> I have 4TB in setup as RAID 10 2TB of actual space to work with. It's a dell 2900 perc 5i controller. I highly doubt it's a software RAID but I don't truly know for sure.

If I understand correctly that's a  mirrored set then striped sets.
You gain performance in reading and writing, however that performance can now be split between the two VM's & host. You have to now multitask disk IO between virtual systems. 

I don't know if you're able to move one of the vmdk to another target to test, but that may be something to look into if the nearly-locking up is a problem.

I have suggested that storage for virtual machines should be treated the same as if they're physical. Depending on how much space you need, as I believe your controller can keep up, is possibly split the array into two sets mirrored. You halve your space but you dedicate disk IO between VM's.

---

### Post by gtdaqua on 2008-07-02
> **shannondoko said:**
> I am very interested please elaborate. I want these servers to scream.

**First: Tweak the host**

***File System***

Your vmdk files are huge and ext3 is not very good handling them. See, ext3 is an all rounder. But we need a specific scorer here. 

Store your vmdk files on a separate partition - (for e.g say /dev/sda5 is "/vmguests")

Choose XFS or JFS. Its debatable between the two. I use XFS. Many debian admins use XFS. Their own website vouches for XFS.

```

sudo apt-get install xfsprogs xfsdump
sudo mkfs.xfs /dev/sda5 -f

```

Use the "noatime" option to mount your xfs drive in /etc/fstab. Usually a write is made on the file system even when its being read. To disable this function, use "noatime". 

```

/dev/sda5       /vmguests    jfs   noatime    0       2

```


***Kernel Boot Parameters***

Edit the /boot/grub/menu.lst to include these

```

# kopt=root=UUID=... ro elevator=deadline
...
kernel	/boot/vmlinuz-2.6.24 ... elevator=deadline

```

This improves is I/O scheduler significantly. You will see the utilization dropping allowing more processes to added.

***Swap Memory***

Try not to swap. Run as much as you can on the physical RAM.
Your default swap priority is 60. Lowering the priority is a very good option. Edit the "/etc/sysctl.conf" and add these at the end:

```

vm.swappiness=0
vm.overcommit_memory=1
vm.dirty_background_ratio=5
vm.dirty_ratio=10
vm.dirty_expire_centisecs=1000
dev.rtc.max-user-freq=1024

```

This tells linux not to use swap until it has run out of physical RAM.  

Reboot the server the effect the new settings.

**Second: Tweak the Guest OS**

***Virtualization Setting - VMware only***

For Both Windows and Linux, edit the "vmx" file and these at the end of the file:

Modify the .vmx file to include these settings.

```

MemTrimRate = "0"
sched.mem.pshare.enable = "FALSE"
MemAllowAutoScaleDown = "FALSE"

```

This improves performance significantly, especially on Windows Guests. Additionally, on Windows server, whether a VM or physical machine, turn off services that you dont need. 

On a linux guest, consider "elevator=noop" on the kernel boot parameters. And you can do the "/etc/sysctl.conf" tweak on the Linux guests too. 

You should see an overall performance improvement on both the host and the guest operating systems. If you have records of utilization, you shud see that they have dropped after these tweaks. So, if your utilization drops, you can stuff more load!

---

### Post by windependence on 2008-07-02
> **shannondoko said:**
> I have 4TB in setup as RAID 10 2TB of actual space to work with. It's a dell 2900 perc 5i controller. I highly doubt it's a software RAID but I don't truly know for sure.

The perc card is real RAID so yo shouldn't have any problems there. I would have done it in RAID 5  myself, and split it into several logical disks. This is a lot of space to manage.

Also, like someone here said, IMHO Windoze is a lousy host OS for VMware server. Try CentOS or even Ubuntu.

Also, like I said before, only run with a single CPU on the guest OS, and follow gtdaqua's tips.

-Tim

---

### Post by shannondoko on 2008-07-02
> **windependence said:**
> 
Also, like someone here said, IMHO Windoze is a lousy host OS for VMware server. Try CentOS or even Ubuntu.


Have No fear I'm running ubuntu on my hosts. Windows are the guests and they're for the Active Directory.

---

### Post by shannondoko on 2008-07-02
All of my servers currently have around 6 NICs. Currently I have each NIC bridged per server. So every server has a NIC. Is there a way I could do load balancing? 

So basically all the NICs on the host act as one so I don't have to create as many bridged networks? 

I'm hoping if that's possible I might get better network speeds to my servers.

---

### Post by windependence on 2008-07-02
[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

This is for 6.10, but should work well with other versions as well.

-Tim

---

### Post by gtdaqua on 2008-07-03
> **shannondoko said:**
> All of my servers currently have around 6 NICs. Currently I have each NIC bridged per server. So every server has a NIC. Is there a way I could do load balancing? 

So basically all the NICs on the host act as one so I don't have to create as many bridged networks? 

I'm hoping if that's possible I might get better network speeds to my servers.

You may not actually require load balancing if you are maxing traffic often. 1Gbps is effectively 125MB/sec wire speed. Most HDDs dont write at this speed unless they are in an array of RAID-0. 

Also, load balancing is good if you are exceeding 70% of traffic on one single apapter. If you are, however, using iSCSI-targets, then load balancing make sense. 

By all means, do load-blalance. But are you going to exceed the wirespeed throughput and you are going to exceed them often?

---

### Post by mstjohn1974 on 2011-09-18
Like they already mentioned VMware is the market leader in virutalization and it is free and with vsphere 5 you get a lot...
also very good and closing up to vmware is Citrix XenServer which is also free and offers a lot.
You also can install it from scratch on any ubuntu/debian system but Citrix already did that for you and it offers a neat management console.
KVM is a very nice solution also free and easy to install on a ubuntu/debian system.
then there is virtual box more like a workstation solution but if you run it headless than if is kind of nice too for a server solution.

There is a lot of information regarding those solutions on the internet and as usual google is your best friend.
I always prefer [www.howtoforge.net](www.howtoforge.net) and [www.ubuntuvideocast.com](www.ubuntuvideocast.com)

---

