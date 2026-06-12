---
title: "VMWaer 2 Install"
date: 2009-03-08
forum: Virtualisation
---

### Post by sw34963 on 2009-03-08
Hi All,

Ima trying to follow the vmware 2 install [https://help.ubuntu.com/community/VMware/Server ]("https://help.ubuntu.com/community/VMware/Server")

All is going well till near the end of the install when it tries to stop the vmware machines and services.  Now I understand that there are no vm's yet,  but it comes up fails and then hangs.
Here is an extract from the installation at that point
> Checking for active VMs:
There are no Active VMs.
Stopping services for VMware Server

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access   (it hangs here)
   


Any ideas?

Thanks guys

---

### Post by sw34963 on 2009-03-08
Ahh,  my mistake.  It just took about 15mins before it continued,  which I would assume is alot longer than it should.  But,  the install is finished and working fine, so far...

Cheers;)

---

### Post by sw34963 on 2009-03-08
The install went well and all is running:
> Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family:                           done
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

The configuration of VMware Server 2.0.0 build-122956 for Linux for this
running kernel completed successfully.

BUt...
Trying to access the web front is not happening for me.
I have followed the Troubleshooting guide on the above link and tried the telnet and was unsuccessful so I reinstalled xinetd successfully.  I then ran through the vmware-config.pl again and still I cant get the "connection refused".

Any other suggestions?

---

### Post by sw34963 on 2009-03-09
Any Ideas?

---

### Post by Nxion on 2009-03-09
When you say you get a "Connection Refused" error. is this error in Firefox? if so can you post a screenshot so I can see the exact error. I ran across this as well for my install but it was because Firefox didn't regonize the SSL cert and by default it refuses the connection unless you explicitly allow it.

---

### Post by veloce on 2009-03-09
> **Nxion said:**
> When you say you get a "Connection Refused" error. is this error in Firefox? if so can you post a screenshot so I can see the exact error. I ran across this as well for my install but it was because Firefox didn't regonize the SSL cert and by default it refuses the connection unless you explicitly allow it.

Also, check your firewall settings.  (e.g. windows firewall will block access.)

---

### Post by sw34963 on 2009-03-09
> **Nxion said:**
> When you say you get a "Connection Refused" error. is this error in Firefox? if so can you post a screenshot so I can see the exact error. I ran across this as well for my install but it was because Firefox didn't regonize the SSL cert and by default it refuses the connection unless you explicitly allow it.

Cant get the screenshot to attach:(

Also,  this I feel is a noob question but I confused with the whole bridged Network interface thing.  The address I am tring to get to is the address of the host @ port 8222,  is that correct or should I be pointing it to the vmnet0 address?  If so not sure how to work out its address,  I tried ifconfig and it only shows me the eth0 interface.

Cheers for responding..

---

### Post by lawson23 on 2009-03-09
bridged Network interface thing. The address I am tring to get to is the address of the host @ port 8222

the address you want is the address of the Machine you installed VMware Server on.

Bridged Networking in Vmware is for giving your VM's direct access to your main network.  They will act as if they have a physical nic card connected directly to your network.  Nat Networking your VM's would get a nat address and communicate through your VMserver IP.

Hope this clears that up a little it is my quick explanation.

---

### Post by veloce on 2009-03-10
> **sw34963 said:**
> The address I am tring to get to is the address of the host @ port 8222,  is that correct

Yes, that is correct.  

Can you ping the host?
Can you try accessing the web interface on the host (i.e. then it will be localhost:8222)

Also try https://{host}:8333/

---

### Post by sw34963 on 2009-03-10
I am running it on Ubuntu server so on-board browser to browse to localhost.

Ok here is the screen shot trying to get to the server with firefox
note the address is the IP of the Host server
[ATTACH]105961[/ATTACH]

---

### Post by Nxion on 2009-03-10
try adding https. By default it setups VMware Server 2 with a secure port and that the safest way to connect to it so try this:

[https://1.2.3.4:8222](https://1.2.3.4:8222)

or 

[https://1.2.3.4:8333](https://1.2.3.4:8333)

The reason why I put two different addresses is because I cant remember off the top of my head which port it is. Of course replace 1.2.3.4 with your IP address.

---

### Post by sw34963 on 2009-03-10
Thanks Nxion, I had tried the https connection also - its [https://1.2.3.4:8333](https://1.2.3.4:8333),  but the same thing happens.

I have a couple of thoughts:
 - could it be a permisions thing
 - should I need to do an etc/init.d/vmware start  or /etc/init.d/vmware-mgnt start ?

If it is a permissions thing which permisions would I need to change?

---

### Post by Nxion on 2009-03-10
I don't believe it is a permissions thing. Have you tried rebooting the machine?

---

### Post by Nxion on 2009-03-10
Are you trying to acces the web interface on Windows or Ubuntu? And is VMWare Server installed on the same machine you are accessing it from?

---

### Post by sw34963 on 2009-03-10
Accessing from my Windows PC and the server is on a seperate machine on the same subnet

---

### Post by veloce on 2009-03-10
> **sw34963 said:**
> Accessing from my Windows PC and the server is on a seperate machine on the same subnet

Have you tried turning off the windows firewall?

---

### Post by sw34963 on 2009-03-11
Hey Veloce,  As the windows firewall is set with group permissions and my manager is reluctant to want to turn it off - yes I know I though the same thing ;)

So I have run up a Linux VM and without a problem I was able to get to the Web Interface.   The only thing is,  I login with the root name and password and its telling me I dont have permissions to log onto this server.  So it looks like Im going to have to play around with the permissions :(

Thanks for the suggestion

---

### Post by veloce on 2009-03-11
> **sw34963 said:**
> Hey Veloce,  As the windows firewall is set with group permissions and my manager is reluctant to want to turn it off - yes I know I though the same thing ;)

So I have run up a Linux VM and without a problem I was able to get to the Web Interface.   The only thing is,  I login with the root name and password and its telling me I dont have permissions to log onto this server.  So it looks like Im going to have to play around with the permissions :(

Thanks for the suggestion

You need to log in as the administrative user you set up when installing.  (This may not be the root user.)

I think you can change it by running vmware-config again.

---

### Post by sw34963 on 2009-03-11
I ran the install script again,  but this time put the administrator name in and now I can access the Web Interface _and_ login.

Thanks all for your assistance,  its much appeciated :D

---

### Post by sw34963 on 2009-03-12
WoW,  this web interface is great,  its much better than the older console with vmware 1. 

For anyone wanting to try it I would recommend it highly:KS

---

### Post by Nxion on 2009-03-13
Glad we can all help :)

---

