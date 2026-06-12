---
title: "Where is my VMware"
date: 2010-08-16
forum: Virtualisation
---

### Post by lwalper on 2010-08-16
I installed VMware Server 2.0.2-???. The install seemed to go well and everything seemed to go where it belonged. Shouldn't there be a link somewhere to the program? How do I access it? I was reading the documentation and it says there is supposed to be VMware Tools somewhere. Did that not load with the server software?

---

### Post by lwalper on 2010-08-16
I'm at the VI Web access screen which asks for a username and password. I have entered my host username and password, which is recognized, but it tells me I don't have permissions to login to the server. How do I login - or is there a different user interface?

---

### Post by lwalper on 2010-08-16
OK, think I figured it out. Re-installed the software and entered my username as admin. That seems to work.

---

### Post by lwalper on 2010-08-16
Spoke too soon ...

Everything seemed to be working fine and I was going to create a new NFS datastore - at the moment didn't have time to complete the job so closed the browser and shut down the computer. Now, a few hours later I try to access VM Tools by opening my browser and entering [http://localhost:8222](http://localhost:8222) and my browser returns the message "unable to connect" "check Firefox firewall settings" and some other stuff so tried using Chrome with the same result. What happened to my computer in the OFF state over the past few hours? Everything worked before I turned it off.

I checked my /etc/hosts file and everything seems OK there (I suppose??)

127.0.0.1	localhost
127.0.1.1	leslie-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

The userguide suggests entering the FQDN. I know what the acronym means, but how do I enter it without a domain? or actual domain name?

---

### Post by lwalper on 2010-08-16
And now my computer won't shut down, but restarts to a login screen.

---

### Post by GrumpyBum on 2010-08-16
Hello, I am no expert with Ubuntu but handy with VMware, the following my help.

1. From the terminal run '**/etc/init.d/vmware status**' and confirm that the status shows vmware services to be running.
If these are not running you will want to run '**/etc/init.d/*service* start**' where *service* is, enter the service that is not started.

2. What webbrowser are you running? I have found that not all browsers can access vmware server over port 8222 so try browsing '**[https://localhost:8333/](https://localhost:8333/)**' and you may gain access this way.

3. I have noticed since starting to use Ubuntu a few years back that not all applications will start automatically by default. You may need to enable this default startup. I have had this issue with vmware server on Ubuntu 9.10 before.
From the terminal run '**sudo nano /etc/vmware/config**' then browser to the line '**autostart=**' and ensure this is entered as '**autostart="poweron"**'
Note that I have used nano, but you can use any text editor you wish.

4. Just for the record, by default in vmware server, any account with root permission will be able to log onto the server GUI.

Let us know how you go, I have seen a lot of setup issues with vmware server 2 before

---

### Post by GrumpyBum on 2010-08-16
> **lwalper said:**
> And now my computer won't shut down, but restarts to a login screen.

Try running the following from a terminal '**sudo shutdown -h now**' and this will shut down after the root password has been supplied.
If you system reboots after this I would be lead to believe it is a power management setting in the BIOS or the power button on you computer is shorting out.

---

### Post by lwalper on 2010-08-18
Thanks for that. I'll check those options. Something I think I may have neglected to say is that I'm also running Apache2. That may be causing a problem with VMware. Since my previous post I have removed Apache and reinstalled VMware. Everything now seems to be running OK.

As far as the shutdown problem, that also seems to have fixed itself. Don't think there's a problem sith the power switch. It was the "normal" shutdown procedure that was not working correctly.

I'll try to reinstall Apache.

---

