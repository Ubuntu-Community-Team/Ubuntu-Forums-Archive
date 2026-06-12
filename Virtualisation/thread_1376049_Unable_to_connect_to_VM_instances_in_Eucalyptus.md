---
title: "Unable to connect to VM instances in Eucalyptus"
date: 2010-01-08
forum: Virtualisation
---

### Post by Everett Toews on 2010-01-08
Hi All,

I've been working on getting a test Eucalyptus cloud up and running using Ubuntu 9.10 (Karmic Koala).  I was following the instructions ([https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)) and things we're going well until I got to Step 7 point #5 where you ssh into the instance you just ran.  It's as if this instance simply doesn't exist.  I can get the IP address of it from euca-describe-instances but I can't ssh into it and I can't even ping it.

I suspect it's some networking/firewall problem.  I've tried running Eucalyptus in MANAGED-NOVLAN and SYSTEM modes with the same result.  I've tried monkeying around with the firewall on the front-end but I'm no Linux networking guru so this felt like shooting in the dark.  I've also tried images from Canonical and Eucalyptus.  Same thing everything.

Does anyone know why I might not be able to connect to my instances?  Anyone having the same problem?

Here are the details.

Eucalyptus version - 1.6~bzr931-0ubuntu7.4
Installed from Ubuntu Server 9.10 64 bit (as per [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall))
Hypervisor type - KVM
Topology - 1 physical machine for the front-end (cc) and 1 physical machine for a node (nc)
Networking mode - MANAGED-NOVLAN

In the attached file eucalyptus-1.6-info.tar.gz I've included all of the commands, config and logs I think are relevant.

cc logs - /eucalyptus-1.6-info/cc/var/log/eucalyptus
cc conf - /eucalyptus-1.6-info/cc/etc/eucalyptus
cc diagnostic commands/results - /eucalyptus-1.6-info/cc/commands.txt

nc logs - /eucalyptus-1.6-info/nc/var/log/eucalyptus
nc conf - /eucalyptus-1.6-info/nc/etc/eucalyptus
nc diagnostic commands/results - /eucalyptus-1.6-info/nc/commands.txt

client commands to run image and attempt to connect - /eucalyptus-1.6-info/client/commands.txt

When I try to ping it I get 100% packet loss. When I try to ssh to it I get a "ssh: connect to host 129.128.184.50 port 22: Connection refused".

Any help is greatly appreciated!

Everett

---

### Post by bluntknife on 2010-01-21
Hi,

I am having exactly the same problem.  I suspect it's the network config but I haven't managed to locate anything that looks incorrect.  The Public IP range allocated to the new instances is on the same subnet as the CC NIC but I cannot communicate with the instances in any way.  They appear to be running fine, but in limbo!

Any help would be very much appreciated.

---

### Post by Everett Toews on 2010-01-22
We were never able to pin point the exact cause of the problem.  After viewing the console of the starting VM by ssh'ing into the node controller and running the command,[INDENT]virsh console <instance_id>
[/INDENT]We noticed that the VM appeared to be hanging after the message,[INDENT]Waiting for ec2 meta-data service
[/INDENT]This issue has something in common with the bug [ec2-init hangs boot on non-EC2/Eucalpytus systems]("https://bugs.launchpad.net/ubuntu/+source/ec2-init/+bug/424065") but we don't think that was the root cause of the problem.

The solution?

We contacted Eucalyptus support and pretty much the first thing they recommended was upgrading to Eucalyptus 1.6.1, which is not what Ubuntu 9.10 uses.  It uses Eucalyptus version 1.6~bzr931-0ubuntu7.4 (I've updated my original post to reflect this).  Unfortunately 1.6.1 is not available for Ubuntu Karmic yet (see [Eucalyptus downloads]("http://open.eucalyptus.com/downloads")).

So ultimately we switched to CentOS 5.4 and installed Eucalyptus 1.6.1 (this time we went with SYSTEM mode to keep it simple and Xen).  After our front-end and node controller were up and running we bundled, uploaded and registered both CentOS and Ubuntu images we got from the [Eucalyptus Image Creator's Guide]("http://open.eucalyptus.com/wiki/EucalyptusUserImageCreatorGuide_v1.6").  Then we ran the images and could immediately ping and ssh into the instances.

---

### Post by mithil on 2010-02-01
Have the same problem here..
I have  1 frontend(CLC,CC,SC,Walrus-SC) and 1 NC machine.
I have installed the UEC.
The problem is, the instance gets in  running state and its public DNS is same as that of network but its not responding to 'ping' nor it is possible to 'ssh' into it!

                    Is there any way that i could get out of this and do you have any idea where the problem lies?
                    Also there appear to be many problems,..such as sometimes the 'euca-describe-availability-zones' command gives error and after some time it works fine....Also, euca2ools on client machine have problems connecting to the frontend whereas Elasticfox works!
                       Any help is greatly appreciated!
mithil.

---

### Post by Everett Toews on 2010-02-03
We never did find out exactly what the problem was.  Our only recourse was to go to CentOS 5.4, Eucalyptus 1.6.1, Xen and SYSTEM mode networking.

---

### Post by ecowden on 2010-02-04
I've also been having the same problem.  The CentOS image is downloading now...

As an aside - Everett: How did you manage to SSH into the node controller?  Specifically: what username and password does one use?  The install process never let us set one, the CC un/pw doesn't work (unsurprisingly) and we haven't been able to find any default.

---

### Post by mithil on 2010-02-05
Thanks Everett..

---

### Post by Everett Toews on 2010-02-05
@ecowden

SSHing into the node controller was never a problem for us.  We just set the username/password when we installed the OS (whether it was Ubuntu or CentOS) and later used that combo to SSH into it.

---

### Post by mithil on 2010-02-07
I have added the karmic server image on the front end(CC machine)
and it seems to be running.Its a 32-bit image
Now i am able to start an instance and SSH into it.The ping works from inside the running instance to the network LAN but cannot ping from other computers to the running instance(looks like firewall settings problem....)
Another problem is that instances of other images such as fedora 11,ubuntu 9.04(64-bit) are still giving the same problem of pending--->shutting down---->terminated!The reason stated is as "User Requested Shutdown"!! I searched many posts related to it,and it seems like the 'Hardware Virtualization support' kind of thing.....Do you have any idea what the reason may be?
And what about your installation?Are you running it successfully or still any problems?

---

### Post by Everett Toews on 2010-02-09
First try running a Xen or KVM image (whichever you are using) without Eucalyptus.  Your problems may not even be Eucalyptus related.

You might want to try giving the thread [**Instance pending, then terminates, never runs**]("http://ubuntuforums.org/showthread.php?t=1317012&highlight=eucalyptus") a read.  In fact, you might want to check out all of the posts by [**ewgates**]("http://ubuntuforums.org/search.php?searchid=69902535").

If that doesn't help, try giving a the people at [Eucalyptus support]("http://www.eucalyptus.com/services/support") a call.  They were very helpful for us.

Good luck.

---

### Post by mithil on 2010-02-15
Thanks for the help...
The problem was solved by reinstalling the complete UEC cloud!
Now we have a running cloud wherein instances can be started and also "ssh" is possible :)
The IaaS is ready.We uploaded the appscale image( code.google.com/p/appscale/) as the goal was to setup PaaS over Eucalyptus IaaS,..but problems logging in..!


cloud@cloud-desktop:~/Desktop$ appscale-run-instances --machine emi-42110D9B 
Run instances message sent successfully. 
Waiting for the image to start up.
[Sun Feb 14 19:16:40 +0530 2010] 3599.999986 seconds left until timeout...
[Sun Feb 14 19:18:42 +0530 2010] 3477.953337 seconds left until timeout...
[Sun Feb 14 19:20:44 +0530 2010] 3355.686997 seconds left until timeout...
[Sun Feb 14 19:22:46 +0530 2010] 3233.304671 seconds left until timeout...
[Sun Feb 14 19:24:49 +0530 2010] 3111.029966 seconds left until timeout...
[Sun Feb 14 19:26:51 +0530 2010] 2988.33919 seconds left until timeout...
[Sun Feb 14 19:28:53 +0530 2010] 2866.219506 seconds left until timeout...
[Sun Feb 14 19:30:55 +0530 2010] 2744.111804 seconds left until timeout...
[Sun Feb 14 19:32:57 +0530 2010] 2621.989847 seconds left until timeout...
Please wait for your instance to complete the bootup process.
[scp -i ~/.appscale/appscale.key -i ~/.appscale/appscale.key -i 
~/.appscale/appscale.private -o StrictHostkeyChecking=no 2>&1 /home/
cloud/.appscale/appscale.key [email]root@192.168.4.222:/root/.ssh[/email]/id_dsa; echo
$? >> ~/.appscale/retval] returned 1 instead of 0 as expected. 
Is your environment set up properly?



The instance is running,  but not possible to login.

---

### Post by nirmalraj on 2010-02-17
hi guys my suggestion is to download the eucalyptus and add the key to the ubuntu source finally install the cc,clc and the nc if everything went fine...means u did it.

in my case i did it in the same way it works too good...eccalyptus version 1.5.2 and the vm get booted... :) i feel the problems with the certificate it expired very soon, so there was a need for the same thing in the NC again and again....

---

### Post by bmullan on 2010-05-15
> **Everett Toews said:**
> Hi All,

I've been working on getting a test Eucalyptus cloud up and running using Ubuntu 9.10 (Karmic Koala).  I was following the instructions ([https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)) and things we're going well until I got to Step 7 point #5 where you ssh into the instance you just ran.  It's as if this instance simply doesn't exist.  I can get the IP address of it from euca-describe-instances but I can't ssh into it and I can't even ping it.

I suspect it's some networking/firewall problem.  I've tried running Eucalyptus in MANAGED-NOVLAN and SYSTEM modes with the same result.  I've tried monkeying around with the firewall on the front-end but I'm no Linux networking guru so this felt like shooting in the dark.  I've also tried images from Canonical and Eucalyptus.  Same thing everything.

Does anyone know why I might not be able to connect to my instances?  Anyone having the same problem?

Here are the details.

Eucalyptus version - 1.6~bzr931-0ubuntu7.4
Installed from Ubuntu Server 9.10 64 bit (as per [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall))
Hypervisor type - KVM
Topology - 1 physical machine for the front-end (cc) and 1 physical machine for a node (nc)
Networking mode - MANAGED-NOVLAN

In the attached file eucalyptus-1.6-info.tar.gz I've included all of the commands, config and logs I think are relevant.

cc logs - /eucalyptus-1.6-info/cc/var/log/eucalyptus
cc conf - /eucalyptus-1.6-info/cc/etc/eucalyptus
cc diagnostic commands/results - /eucalyptus-1.6-info/cc/commands.txt

nc logs - /eucalyptus-1.6-info/nc/var/log/eucalyptus
nc conf - /eucalyptus-1.6-info/nc/etc/eucalyptus
nc diagnostic commands/results - /eucalyptus-1.6-info/nc/commands.txt

client commands to run image and attempt to connect - /eucalyptus-1.6-info/client/commands.txt

When I try to ping it I get 100% packet loss. When I try to ssh to it I get a "ssh: connect to host 129.128.184.50 port 22: Connection refused".

Any help is greatly appreciated!

Everett

One thing I found was the netmask of my VMs was different from my local network.

My local net is a 192.168.1.x 255.255.255.0
The VMs were created with a 192.168.1.x 255.255.255.**255**

So the VMs can't talk outside of their subnet which is behind the Bridge br0.

My suspicion is this is related to a feature read about in the UEC [**Enterprise Cloud Architecture document**]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.ubuntu.com%2Fsystem%2Ffiles%2FUbuntuEnterpriseCloudWP-Architecture-20090820.pdf&ei=qB_vS5yjIoO88gbm6uX9Cg&usg=AFQjCNF_86QBrU-ZavDxaqghkxQcNY34Sw&sig2=hIvYZPcLOXI_hDFA2IpNIQ") in the section titled NETWORKING.

UEC has 3 possible networking modes you can configure for the VMs.

SYSTEM mode
STATIC mode
MANAGED mode

In the description of Managed Mode they mention that the UEC admin defines the network usually private **and unroutable**

That's what I think might be getting setup but I've not had time to check my own UEC setup yet.

---

### Post by erlguta on 2010-07-28
I have the same problem. It seems that a lot of people have the same problem.
I have tested the SYSTEM and STATIC modes, and i can not ping or ssh my instances.
So which is the solution?. Reinstalling from the start is never a solution...

If i do one:
euca-describe-instances

I see my instance runing ok with his IP:
```

RESERVATION	r-485908D8	admin	default
INSTANCE	i-3C7D07C5	emi-CC1B109D	192.168.1.101	172.19.1.2	running	mykey	0		c1.medium	2010-07-28T08:37:12.127Z	cluster1	eki-DE6914F4	eri-1E7515D0

```

I googled a while and I see no solutions. If it is a problem so common with so many people suffering it the first time, it should be better documented or in the FAQS.

---

