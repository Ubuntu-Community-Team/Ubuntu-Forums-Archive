---
title: "VMWare Server 2 in Ubuntu Jaunty 64bit"
date: 2009-06-02
forum: Virtualisation
---

### Post by rlogan on 2009-06-02
Hi all

I am wondering if anyone has been able to succesfully install and get operational VMWare Server 2 on the standard 64bit Jaunty Kernal. I have made a couple of attempts and had various issues with it.

Any tips or suggestions would be wonderful

Many thanks

Richard

---

### Post by xOrphenochx on 2009-06-03
Everything compiled perfectly on the Alphas, but VSOCK stopped working after a few upgrades, it isn't something that's really needed though. Everything else works fine on my box, been running it since early April.

---

### Post by rlogan on 2009-06-03
Wish I could say the same, are you using 64bit or 32 bit Jaunty ?

When compiling I get the vsock issue you advise of when compiling it. At the end of compilation I receive the following message

---------------------------------------------------------------------------

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.1 build-156745 for Linux for this 
running kernel completed successfully.
---------------------------------------------------------------------------

So from what I see all appears to have installed correctly but when I start a newly created vm it gets to 95% and fails with the error message "Failed to initialize monitor device. "


Any help greatly appreciated !!!

Cheers

Richard

---

### Post by wandernot on 2009-06-03
There is certainly something wrong at least in the 64bit realm. I had upgraded to jaunty release. at that point I was running vmware-server-2.0.0 and everything worked normally. at some point in the last two weeks, well after the upgrade, the virtual machines which were running closed their console windows and none of the vms would boot. all get to that 95% point and then die with the "failed to start dialog". Creating a new vm doesn't help. the symptom is the same.

I tried the instructions from [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) including the patch suggested. that may get rid of some warnings but doesn't solve this issue. The examples given show i386 which is why I am suspicious that this is yet another 64bit issue.

---

### Post by HermanAB on 2009-06-03
Uhmm, in my opinion VMware Server 2.x is best avoided.

---

### Post by bodhi.zazen on 2009-06-03
> **HermanAB said:**
> Uhmm, in my opinion VMware Server 2.x is best avoided.

+1

Server 1.x is nice and has more features and is less buggy then 2.x

I would go as far as to say I would advise you look at KVM or Virtualbox. Is there some feature in VMWare server that is not provided by an alternate ?

If you must go with VMWare I advise you run it on a supported OS (VMWare does not support Ubuntu 9.04).

---

### Post by xOrphenochx on 2009-06-03
> **rlogan said:**
> Wish I could say the same, are you using 64bit or 32 bit Jaunty ?

When compiling I get the vsock issue you advise of when compiling it. At the end of compilation I receive the following message

---------------------------------------------------------------------------

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.1 build-156745 for Linux for this 
running kernel completed successfully.
---------------------------------------------------------------------------

So from what I see all appears to have installed correctly but when I start a newly created vm it gets to 95% and fails with the error message "Failed to initialize monitor device. "


Any help greatly appreciated !!!

Cheers

Richard

Certainly have not seen that before. And indeed, I am running 64bit and haven't had an issue until lately with VSOCK. Anywho after looking around for this issue, it seems it can be a number of things, such as having the kvm module load. Can you post the contents of /var/log/vmware/vmware-serverd.log. 

To the others, whether or not its supported(I would never run this in a production environment) 2 has been working like a charm on my system, so if you can't get it working, it's not VMWare's issue. 

And lastly, the best feature that Server has is VI, which I can access from work and I don't have to have all of the clutter of all my guests' windows on my desktop.

---

### Post by rlogan on 2009-06-04
> **bodhi.zazen said:**
> +1

Server 1.x is nice and has more features and is less buggy then 2.x

I would go as far as to say I would advise you look at KVM or Virtualbox. Is there some feature in VMWare server that is not provided by an alternate ?

If you must go with VMWare I advise you run it on a supported OS (VMWare does not support Ubuntu 9.04).

------------------------------------------------------------------

I have Virtualbox running and I must admit I like to try out different applications to see what suites my needs. I know very little about kvm but will also look at that too !!

Thanks for the reply, I may yet give 1.x a go if things don't work out for v2.x, but that will be after a decent go at getting it working !!

Cheers 

Richard

---

### Post by rlogan on 2009-06-04
> **xOrphenochx said:**
> Certainly have not seen that before. And indeed, I am running 64bit and haven't had an issue until lately with VSOCK. Anywho after looking around for this issue, it seems it can be a number of things, such as having the kvm module load. Can you post the contents of /var/log/vmware/vmware-serverd.log. 

To the others, whether or not its supported(I would never run this in a production environment) 2 has been working like a charm on my system, so if you can't get it working, it's not VMWare's issue. 

And lastly, the best feature that Server has is VI, which I can access from work and I don't have to have all of the clutter of all my guests' windows on my desktop.

--------------------------------------------------------------------------

In my case this machine is only a fresh install on a less than 2 week old machine, so can't say what it was like before in the VSOCK issue.

Are you running Jaunty 64 bit or Hardy ? I must admit it has me a little stumped as to what is wrong. Everything seemed to compile fine with the exception of VSOCK.

I would post the log file but there is no such file at the path you indicated. There are files that are hostd.log, hostd-x.log, hostd-index.log and hostd-trace.log in the /var/log/vmware path though.

Thanks for your help, any tips ???

Cheers

Richard

---

### Post by xOrphenochx on 2009-06-04
> **rlogan said:**
> --------------------------------------------------------------------------

In my case this machine is only a fresh install on a less than 2 week old machine, so can't say what it was like before in the VSOCK issue.

Are you running Jaunty 64 bit or Hardy ? I must admit it has me a little stumped as to what is wrong. Everything seemed to compile fine with the exception of VSOCK.

I would post the log file but there is no such file at the path you indicated. There are files that are hostd.log, hostd-x.log, hostd-index.log and hostd-trace.log in the /var/log/vmware path though.

Thanks for your help, any tips ???

Cheers

Richard

Yes, using Jaunty. Will have to check when I get home, I think we have to enable logging since I do not have that file either.

---

### Post by wandernot on 2009-06-04
> **wandernot said:**
> There is certainly something wrong at least in the 64bit realm. I had upgraded to jaunty release. at that point I was running vmware-server-2.0.0 and everything worked normally. at some point in the last two weeks, well after the upgrade, the virtual machines which were running closed their console windows and none of the vms would boot. all get to that 95% point and then die with the "failed to start dialog". Creating a new vm doesn't help. the symptom is the same.

I tried the instructions from [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) including the patch suggested. that may get rid of some warnings but doesn't solve this issue. The examples given show i386 which is why I am suspicious that this is yet another 64bit issue.

My memory started working this morning. The issue is the kvm_(intel|amd) interference problem again. There were at least 2 bugs posted about this but both were closed based on the modules properly cleaning up a flag setting when the were removed.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252871) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268981)

the module does indeed clean up properly as executing a "rmmod kvm_intel" on my machine allowed the vmware-server virtual machines to find and attach to the monitors and the dialog shows 100% now.

The problem with not being able to blacklist the these modules via /etc/modprobe.d/blacklist.conf is still present. anybody know a way to properly and automatically remove a module other than the blacklist? switching away from vmware-server at this point is not an option as I need to be compatible with others in the workgroup.

---

### Post by xOrphenochx on 2009-06-04
> **wandernot said:**
> My memory started working this morning. The issue is the kvm_(intel|amd) interference problem again. There were at least 2 bugs posted about this but both were closed based on the modules properly cleaning up a flag setting when the were removed.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252871) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268981)

the module does indeed clean up properly as executing a "rmmod kvm_intel" on my machine allowed the vmware-server virtual machines to find and attach to the monitors and the dialog shows 100% now.

The problem with not being able to blacklist the these modules via /etc/modprobe.d/blacklist.conf is still present. anybody know a way to properly and automatically remove a module other than the blacklist? switching away from vmware-server at this point is not an option as I need to be compatible with others in the workgroup.

Did you previously try KVM as another virtualization method before upgrading to Jaunty? I'm wondering why my clean install did not have this module loaded. Hopefully this will fix rlogan's issue too.

---

### Post by wandernot on 2009-06-04
> **xOrphenochx said:**
> Did you previously try KVM as another virtualization method before upgrading to Jaunty? I'm wondering why my clean install did not have this module loaded. Hopefully this will fix rlogan's issue too.

I didn't install them knowingly on my work machine where i've reported this issue. Though i've looked at virtualbox when I had problems with vmware. I'll try some new 9.04 installs myself to see if they show up. it would appear that ubuntu is heading to the multiple virtual environment though the GUI (virtual manager) will have to be improved. Unfortunately, from some comments i've seen that ubuntu and vmware are not as close as they once were.. I use vmware because it is our project standard and that nat/bridged/private networks are so easy to manage.

---

### Post by rlogan on 2009-06-04
Looks like I have found the issue, well I can now get the VM's to power on !

Found another person having issues with VMWare on another forum and tried there suggestion.

IT appears that cannot have KVM running in the background as it interferes with VMWare Server 2 running correctly. So you need to stop KVM running.

The suggested method was to install BootUp Manager from synaptic and then disable "Full virtualization on i386 and amd64 hardware - kvm" and apply this. It also allows you to stop the service from Bootup manager.

The server function now appears to be working correctly. I have the console up and running with a VM now being installed.

Thanks to all that helped, it is greatly appreciated !!!

Cheers

Richard

---

### Post by rlogan on 2009-06-08
Problem Solved !!!

I removed KVM from system and working fine except for audio but will work on that !

---

### Post by kgpdeveloper on 2009-06-24
I am getting these errors:
```
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual machine communication interface                             done
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                         failed

```

---

### Post by rlogan on 2009-06-25
Is your user a member of the vbox group by any chance ?

---

### Post by bkochis on 2009-07-15
> **bodhi.zazen said:**
> +1

Server 1.x is nice and has more features and is less buggy then 2.x

. Is there some feature in VMWare server that is not provided by an alternate ?

.

VMware server supports multiple CPU's and multiple network adapters.  I know VirtualBox does not support the CPU's, not sure about the network adapters.

Bob

---

### Post by bodhi.zazen on 2009-07-16
> **bkochis said:**
> VMware server supports multiple CPU's and multiple network adapters.  I know VirtualBox does not support the CPU's, not sure about the network adapters.

Bob

Virtualbox supports multiple network adapters, up to 4. Multiple virtual CPU may or may not be an advantage, depending on what you are doing with them.

KVM supports both multiple CPU and multiple network adapters.

---

### Post by cipi.ro on 2010-03-22
I had the same problem. I think it occurred because I was also running a VirtualBox virtual machine while trying to power on a virtual machine with VMWare. Closing VirtualBox allowed me to power the VMWare virtual machine.

---

