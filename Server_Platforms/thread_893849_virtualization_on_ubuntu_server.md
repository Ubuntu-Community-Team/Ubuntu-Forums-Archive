---
title: "virtualization on ubuntu server"
date: 2008-08-18
forum: Server Platforms
---

### Post by mansonthomas on 2008-08-18
Hi,

 Before this terrible day, I had 2 servers, one under linux (sme server) and one under Windows 2003 server.

 Today the linux one died (multiple capacitor leak).

 The other will quickly follow as I see that some capacitor leak too.

 So I plan to buy some new Hardware, and since I've played with ubuntu on several other server, I'll switch from sme server to ubuntu server.


 I'd like to run what i used to run on the sme server on the ubuntu, and virtualize the windows 2003 server.

So here is some questions : 
[LIST]Is it possible?[/LIST]
[LIST]Do I need a X running?[/LIST]
[LIST]What's the best solution : VMWare Server, XEN, QEMU or something else ?  I know well VMWare server so it has my preference.[/LIST]


Manson Thomas.

---

### Post by wilbbe01 on 2008-08-18
I would go with VMWare server, and I want to say you don't need X in order to use it.  I think you can download the client from their download section for vmware server, which you could then use to connect to and administer the server with the vmware service running.

---

### Post by dmizer on 2008-08-18
Vmware server requires X11, it will not compile without it.  I don't know about the rest, but I suspect that all virtual hosts will require X.

---

### Post by wilbbe01 on 2008-08-18
> Vmware server requires X11, it will not compile without it. I don't know about the rest, but I suspect that all virtual hosts will require X.

Do you need the full X though?  Couldn't it be installed with the libs only?

---

### Post by jayson.rowe on 2008-08-18
> **dmizer said:**
> Vmware server requires X11, it will not compile without it.  I don't know about the rest, but I suspect that all virtual hosts will require X.
VMWare Server does not require X at all. Here's an old thread here I did: [http://ubuntuforums.org/showthread.php?t=646644](http://ubuntuforums.org/showthread.php?t=646644)

That was from 7.04 when VMware Server was in the partner repo, but it's similar w/ the tar-ball - you just make sure you have build-essential and xinetd installed - extract the tar and run "sudo ./vmware-install.pl".

Also, you don't "compile" VMware Server - the tar-ball you download is compiled - you just execute an install script - the only thing that gets compiled are kernel modules - none of which require X at all.

---

### Post by dmizer on 2008-08-18
Very interesting.  Last time I tried it without X, I remember that there was some sort of compile issue, but it's been since Dapper.

I stand corrected.  Thanks for the information.

---

### Post by jayson.rowe on 2008-08-19
> **dmizer said:**
> Very interesting.  Last time I tried it without X, I remember that there was some sort of compile issue, but it's been since Dapper.

I stand corrected.  Thanks for the information.
hmmm - that's odd - it had to have been something else wrong and not the lack of X - my VMware server here at home is still running Dapper (reminds me I need to get around to upgrading it)...

---

### Post by mansonthomas on 2008-08-23
Sorry for replying so late.

Thanks for the information. I'll use VMWare Server then, without X.

---

### Post by mellowd on 2008-08-23
True, X is not required. I've got a few test virtual machines on my ubuntu server not running any form of X. I've got the client installed on my XP pc and use it from there. I also can connect to and use the VM's from my laptop running fluxbuntu

---

### Post by windependence on 2008-08-23
Not only that but if you are buying new hardware, you don't even have to use VMware server anymore. VMware ESXi is now FREE! This WAS a $500 product, but VMware released it free when Micro$oft came out with their hypervisor. It is absilutely fantastic. The only gotcha is the hardware must be on the compatibility list to make sure it will install. If you are buying anyway, that would be perfect. ESXi does not need a host OS, it runs it's own OS directly on the hardware (a stripped down Linux). 

You need no X at all to use VMware Server or ESXi. You manage them from another machine or from the command line whichever you please. You can connect remotely using a GUI interface from Linux or Windows.

VMware as opposed to the others:

VMware supports the largest variety of guest operating systems. Also, on many of the other hypervisors you cannot use your CDROM/DVDROM, you have to load from the network or an ISO file. Even if you can use the device like on Xen, changing CDs is really nasty. VMware uses the CD just like you would use it to install any OS from a single server. Here's a cool feature - in ESXi, you can install a guest OS from your laptop or desktop using the CD *on the remote machine*. That's right I said you can boot from the remote machine! That means you do not have to be at the server at all. Great for co-lo hosted servers.

To the OP: You will have no problems at all running server 2003 in a VM, in fact, my colleagues tell me it runs *better* than on the hardware itself. You will be able to create virtual switches and NICs too. All of this on just a 32MB footprint. You won't be sorry you did it.

Some useful links:

[VMware ESXi Hypervisor]("https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1")

[Hardware compatibility list]("http://www.vmware.com/resources/techresources/1032")

-Tim

---

### Post by dmizer on 2008-08-23
> **windependence said:**
> Not only that but if you are buying new hardware, you don't even have to use VMware server anymore. VMware ESXi is now FREE! This WAS a $500 product, but VMware released it free when Micro$oft came out with their hypervisor. It is absilutely fantastic. The only gotcha is the hardware must be on the compatibility list to make sure it will install. If you are buying anyway, that would be perfect. ESXi does not need a host OS, it runs it's own OS directly on the hardware (a stripped down Linux). 

You need no X at all to use VMware Server or ESXi. You manage them from another machine or from the command line whichever you please. You can connect remotely using a GUI interface from Linux or Windows.

VMware as opposed to the others:

VMware supports the largest variety of guest operating systems. Also, on many of the other hypervisors you cannot use your CDROM/DVDROM, you have to load from the network or an ISO file. Even if you can use the device like on Xen, changing CDs is really nasty. VMware uses the CD just like you would use it to install any OS from a single server. Here's a cool feature - in ESXi, you can install a guest OS from your laptop or desktop using the CD *on the remote machine*. That's right I said you can boot from the remote machine! That means you do not have to be at the server at all. Great for co-lo hosted servers.

To the OP: You will have no problems at all running server 2003 in a VM, in fact, my colleagues tell me it runs *better* than on the hardware itself. You will be able to create virtual switches and NICs too. All of this on just a 32MB footprint. You won't be sorry you did it.

Some useful links:

[VMware ESXi Hypervisor]("https://www.vmware.com/tryvmware/login.php?eval=esxi&t=1")

[Hardware compatibility list]("http://www.vmware.com/resources/techresources/1032")

-Tim

Fantastic info.  Tone it down next time, that really read like spam.

---

### Post by windependence on 2008-08-23
Sorry, if it offended you. I have thoroughly tested most of the others and VMware was just so far out in front in the end. I am not saying some of the others weren't useful, just that IMHO this was better, and then when they made ESXi free, that did it for me. ;)

-Tim

---

### Post by Kolipoki on 2008-08-25
> **windependence said:**
> ...ESXi does not need a host OS, it runs it's own OS directly on the hardware (a stripped down Linux). 

-Tim
I was about to start a thread with exactly that topic, asking on OSs, thinking on both perspectives, that is, if VMware should go before or after a given OS installation. So found this thread while searching if the subject had been discussed. All that after we recently got 2 Xeon PowerEdge 2950 (we bought them on purpose without any OS from factory) and some version of VMware came in with the software installation CD! 

Tim, thanks a ton for all that info. I appreciate every piece of it very much. I personally didn't find it particularly biased. Not trying to start a debate here with that statement, but well, if the product is good, specially for (us) the people who will have their hands on the daily basis, then it's hugely appreciated to have as much info as possible before making any commitment with any solution. After all, the core intention of any technology is to make things faster, better and more efficient (including costs) and probably everyone is interested to know such outcomes. 

I actually would like to know more. VMware seems to have various alternatives. So, I'm somewhat lost, specifically, on how is ESXi opposed to what they call the VMware "server". K.

---

### Post by windependence on 2008-08-25
VMware server runs on a host OS, Linux, Windows, etc., and the guests run on top of that. It will run a much more types of harware since you have a choice of what the host OS will be. It's a bit slower than ESXi but not enouh that you would notice it on most installations.

ESXi runs directly on the hardware, there is no host OS. You load it from an ISO image or burn the ISO to CDROM and run it from the CD to install. It's a bit picky about hardware, but it runs on most server hardware and some desktop hardware with no problems. ESXi has a more detailed interface and the interface cannot be run on the host machine, you must access it from another computer.

Both are great products, they are just a bit different.

Hope this clears things up a bit.

-Tim

---

### Post by Kolipoki on 2008-08-25
> **windependence said:**
> VMware server runs on a host OS, Linux, Windows, etc., and the guests run on top of that. It will run a much more types of harware since you have a choice of what the host OS will be. It's a bit slower than ESXi but not enouh that you would notice it on most installations.

ESXi runs directly on the hardware, there is no host OS. You load it from an ISO image or burn the ISO to CDROM and run it from the CD to install. It's a bit picky about hardware, but it runs on most server hardware and some desktop hardware with no problems. ESXi has a more detailed interface and the interface cannot be run on the host machine, you must access it from another computer.

Both are great products, they are just a bit different.

Hope this clears things up a bit.

-Tim

Very nice... Thanks again. Getting the ISO as I write. :)
 
K.

---

