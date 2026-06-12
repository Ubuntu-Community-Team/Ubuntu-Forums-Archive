---
title: "Ubuntu Enterprise Cloud running on a single machine"
date: 2010-02-09
forum: Server Platforms
---

### Post by teo2403 on 2010-02-09
Hi all. I ve been using Ubuntu Desktop since v 6.06 and Ubuntu server since 8.04 .

Back at home, I am running a XenServer v5.5 with 6 VMs on it (4 Ubuntu Server 8.04, 1 Ubuntu Desktop 9.10 and 1 MS XP). This is not a production environment ofcourse, I use it just for my personal needs.

Since Ubuntu moved to "Enterprise Cloud" i started making migration plans. Like moving from XenServer to UAC. I do not care about the existing VM's, i will rebuild them from scratch either way, but i d like to know if it's possible to run a UAC (management + node) in a single machine. Is there a tutorial or some other guide for such a thing??

If not, is there a tool/framework where i could manage my Ubuntu VM server from web ?

Thanks,
Teo

---

### Post by teo2403 on 2010-02-09
I forgot to mention before, that i have already tried VMWare server but i prefer XenServer (ESXi is not compatible with my hardware).

In general, i am satisfied with XenServer but it lacks GUI support for linux, this is why i m searching for alternative.

Another nice solution could be ProxMox but i m not sure if i could install Windows on that.

---

### Post by samosamo on 2010-02-10
Can you post more details on this setup? Why would you move from Xen/VMWare to UEC?  My hardware is not ESXi compatible either so I choose to use VMWare Server, but I'm always open to new ideas.

---

### Post by teo2403 on 2010-02-10
XenServer is very good alternative to ESXi and since its based on Debian (i think) it has much larger hardware support than ESX/ESXi.

However XenServer lacks linux GUI. I have not found a management console for linux. I have to RDP to a Windows machine from which i can access XenCenter (official .NET management console by Citrix for XenServer).

This is what makes me want to look to other solutions.

I used to have VMWare Server as well but i have found XenServer far more stable (had lots of crashes/failures with VMWare Server) and much easier to setup (XenServer is barebone installation)

Regards,
Teo

---

### Post by teo2403 on 2010-02-10
Sorry about the mistakes in my previous post, i replied while it was time to leave work and i was in a hurry :)

(XenServer is barebone installation) --> i mean baremetal.


Regarding "Why would you move from Xen/VMWare to UEC?", besides management console, since Ubuntu moved to UEC why not give it a try ? :) After all i dont think there is some other "official" management tool for Ubuntu KVM Server.

---

### Post by dragos2 on 2010-02-10
My 2 cents.

I've worked with Amazon Ec2 and it's pretty decent. But I am not that convinced.

In a cloud everything is relative, you have the flexibility but you won't get the native
performance of a baremetal hypervisor like XenServer - which is great by the way :)

So migrating from XenServer to cloud is not a gain at least for now. And migrating
from XenServer to Amazon Ec2 is completely foolish - there are few problems which
I can detail if anyone interested.

---

### Post by teo2403 on 2010-02-10
It should be mentioned that XenServer might be free for now, but it works under a license provided by Citrix which expires after 1 year (mine on March i think). Therefore we cannot be sure we ll have XenServer for free forever.

dragos2 - have you worked with ubuntu as a VM server ??? You have any opinion on that kind of setup ?

---

### Post by dragos2 on 2010-02-10
> **teo2403 said:**
> It should be mentioned that XenServer might be free for now, but it works under a license provided by Citrix which expires after 1 year (mine on March i think). Therefore we cannot be sure we ll have XenServer for free forever.

dragos2 - have you worked with ubuntu as a VM server ??? You have any opinion on that kind of setup ?

Yes, now I am using Ubuntu with OpenVZ kernel on one of the servers and I like it, but that is another story - I had a few networking problems with it but its running stable after setup.

And I also run VirtualBox on Ubuntu Server last year but not in production - it was allright,
it has a command line tool to work with on headless servers.

Yes, unfortunately XenServer needs a license and it only lacks remote ISO boot, but even so it
is a great product.

---

### Post by userkiller on 2010-02-10
I just learned couple of stuff just by reading this topic.;)

---

### Post by teo2403 on 2010-02-11
OpenVZ seems nice but i want to be able to use Windows/Solaris VMs as well so it won't fit for me.

Dragos :
"unfortunately XenServer needs a license and it only lacks remote ISO boot"

What do you mean by that ?? What i do usually, is keep my ISOs in a shared samba location and attach this as a remote samba repository to XenServer. There are other ways besides Samba as well (like NFS) but i havent used any.

---

### Post by teo2403 on 2010-02-19
UPDATE: I found something interesting here : [Oracle VM Server]("http://www.oracle.com/us/technologies/virtualization/oraclevm/index.html")

Haven't tested yet. Oracle VM server and Oracle VM Manager are seperate downloads so maybe it requires 2 separate machines to work. I ll update once i ve tested this although i m not sure when i ll have time to do so.

---

### Post by px43 on 2010-03-31
So, back to the original question.

Does anyone know if it's possible to run the frontend server and a node server on the same machine?  I have been trying, and it almost seems to work, but it seems like whatever it is that is managing the networking configs is fighting with itself when trying to setup the bridge.

Has anyone gotten this to work?
Does anyone know if this is possible/normal/insane?

I might end up going back to vmware server if I can't get this worked out soon :-/

---

### Post by kenada on 2010-03-31
> **teo2403 said:**
> Hi all. I ve been using Ubuntu Desktop since v 6.06 and Ubuntu server since 8.04 .

Back at home, I am running a XenServer v5.5 with 6 VMs on it (4 Ubuntu Server 8.04, 1 Ubuntu Desktop 9.10 and 1 MS XP). This is not a production environment ofcourse, I use it just for my personal needs.

Since Ubuntu moved to "Enterprise Cloud" i started making migration plans. Like moving from XenServer to UAC. I do not care about the existing VM's, i will rebuild them from scratch either way, but i d like to know if it's possible to run a UAC (management + node) in a single machine. Is there a tutorial or some other guide for such a thing??

If not, is there a tool/framework where i could manage my Ubuntu VM server from web ?

Thanks,
Teo


Do you mind asking what you'll use the cloud for?
I've entertained taking it on purely as a project, though I cant really think of a use for a cloud at home lol

---

### Post by kiranmurari on 2010-03-31
Hi px43,

I have got UEC running on a single machine, using KVM as the hypervisor. Please see the below link for more information.

[http://kiranmurari.wordpress.com/2010/03/19/22/](http://kiranmurari.wordpress.com/2010/03/19/22/)

Hope that helps.

---

### Post by px43 on 2010-03-31
kiranmurari:

Awesome, thanks for the blog post.  When I did the network changes you suggested, I had the same result where I could start up an instance, but it just says "pending" forever.  The only errors I can see in logs are network timeouts.

Then I wiped everything and started over, and now the command
euca_conf --no-rsync --discover-nodes
Isn't finding any nodes, even though I can see eucalyptus-nc running

Frustrating.  Were there any specific things that explicitly needed to be changed from the default install?  Many of the steps in your instructions are similar to the UEC documentation.  One main difference I noticed was using br0 instead of eth0 in the vmnet pub/priv interface settings, and a static bridge IP rather than one set by dhcp.

---

### Post by kiranmurari on 2010-03-31
Hi,

 Please do a clean stop and clean start of eucalyptus services after changing the network configuration and the network options in eucalyptus.conf.
```
$ sudo service eucalyptus stop CLEAN=1
$ sudo service eucalyptus-nc stop CLEAN=1
$ sudo service eucalyptus start CLEAN=1
$ sudo service eucalyptus-nc start CLEAN=1
```     Let me know if that worked. Also can you post the error message displayed on the console (if any) and any significant log messages that you see in cc.log and nc.log.

---

### Post by px43 on 2010-03-31
Still no love.  When I try to find nodes, I **instantly** get back

pierce@majin:~$ sudo euca_conf --no-rsync --discover-nodes
haystack=  10.1.10.185 1 192.168.122.1 
haystack=  10.1.10.185 1 192.168.122.1 

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.
pierce@majin:~$ 

10.1.10.185 is the IP of the macheine (ip given to me by dhcp).  I have no idea what the 192 address is, since I registered 10.66.77.0/24 as the private IPs that the instances are supposed to get.

****** new information ******

I still have no idea what "haystack" means, and annoyingly when I googled around for "haystack eucalyptus" this post was the first and only related hit on google.  That list is apparently the list of nodes, and in retrospect, the "1" there might have been preventing any of the nodes from properly joining the cluster, which is why **euca-describe-availability-zones verbose** was coming up with all zeros.  This list can be manipulated directly with euca_conf and the --list-nodes --deregister-nodes and --register-nodes flags.  I also don't understand how the 192 address got in the list (was resolving to locahost), but it has happened to me a few times after a clean install, and looks like it doubles the number of max resources in the availability zones.  I would suggest removing it if you see it.

---

### Post by px43 on 2010-04-07
disclaimer: I am running 10.04 server beta with cloud install and all cloud components selected at install time.  All results are on an updated lucid server.

Okay, I was able to get MANAGED_NOVLAN working on a single server, but I have not managed to figure out how to get the instances to allow incoming connections from the internet.

I was also able to get SYSTEM working, which I was able to route to from the internet, but I was having some instance issues.  First of all, none of the ubuntu EMIs I have looked at emi-DDE8105C, emi-76CE170F, etc seem to support STATIC or SYSTEM configuration.  First off, ec2-init hangs for about an hour on every boot (before running sshd), and the instances have a bad habit of not coming back when the host is rebooted (no idea why, sometimes they boot and are immediately terminated, other times they just disappear with no trace).

Has anyone found any good workarounds for either of these setups?  I suppose I could use some iptables and ip forwarding trickery to route internet traffic to my instances in MANAGED_NOVLAN mode, or I could use SYSTEM mode, and turn on manual cleanup so instances don't delete themselves when terminated, and then I could set up a bunch of scripts to directly run kvm to prop my instances back up when they kill themselves.

Any insights would be greatly appreciated.  Thanks

---

### Post by mnagc on 2010-05-01
> **teo2403 said:**
> XenServer is very good alternative to ESXi and since its based on Debian (i think) it has much larger hardware support than ESX/ESXi.

However XenServer lacks linux GUI. I have not found a management console for linux. I have to RDP to a Windows machine from which i can access XenCenter (official .NET management console by Citrix for XenServer).

This is what makes me want to look to other solutions.

I used to have VMWare Server as well but i have found XenServer far more stable (had lots of crashes/failures with VMWare Server) and much easier to setup (XenServer is barebone installation)

Regards,
Teo
openxencenter [http://www.openxencenter.com/](http://www.openxencenter.com/) to manage XenServer from Linux

---

### Post by mnagc on 2010-05-01
import openfiler vm ([http://www.openfiler.com/community/download/](http://www.openfiler.com/community/download/)), follow the community to create a NFS share and dump all your ISO there.
By the way XenServer license can be renewed every year without cost.

---

### Post by px43 on 2010-05-02
I actually ended up running convirt.  Free, runs on ubuntu, super simple to deploy.  It has a really nice web ui, and I didn't run into nearly the number of bugs compared to the UEC/vmware/citrix solutions I was looking into.

---

