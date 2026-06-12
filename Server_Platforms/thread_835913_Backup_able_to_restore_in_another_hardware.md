---
title: "Backup able to restore in another hardware"
date: 2008-06-20
forum: Server Platforms
---

### Post by jmz2 on 2008-06-20
Hello,

I am looking for a backup solution able to restore my Ubuntu remote server to another hardware, does this exits?

What I really want is to completely backup my Ubuntu file system and been able to reinstall it quickly on any computer.

I think cloning HD solutions is not an option if you change architecture, is it?

Maybe I need to make a personalised LiveCD for this, maybe not, hope you clarify.

For instance, imagine that I move from a RAID1 software server to  another single disk server, I would like a tool able to deal with this real quick.


Thanks for your help.

---

### Post by windependence on 2008-06-21
The only way I know to do this sucessfully is to run your OS in a virtual machine on something like VMware server (free). Your VM is then just a directory and you can just move the directory to ANY hardware running Vmware and fire it up with no problems. Works great on my systems.

-Tim

---

### Post by jmz2 on 2008-06-21
> **windependence said:**
> The only way I know to do this sucessfully is to run your OS in a virtual machine on something like VMware server (free). Your VM is then just a directory and you can just move the directory to ANY hardware running Vmware and fire it up with no problems. Works great on my systems.

-Tim

I do as well run VMware, but my case is that I want to backup the VMware Host Machine.

---

### Post by windependence on 2008-06-21
Changing architecture is gonna mess it up. I don't know how you can garuntee it would run on whatever new hardware you select. Why do you want to do this?

-Tim

---

### Post by jmz2 on 2008-06-21
> **windependence said:**
> Changing architecture is gonna mess it up. I don't know how you can garuntee it would run on whatever new hardware you select. Why do you want to do this?

-Tim

I have a remote server on a Datacenter. Imagine your server cracks and you can only get a new server with different hardware, in this case I don't want to reinstall and setup my server security again because it is going to take me days and I need to be onlina ASAP.

I need a backup that can quickly restore on a new server whatever the hardware. Once the serveris running I can set up my VMware machines with a quick tar and scp.

Thanks.

---

### Post by windependence on 2008-06-21
Well I'm a bit confused because all my hosts are not accessible from the outside, just the VMs. What security are you setting up on the host? Your host company should also be running a proper firewall. If not, you should consider putting one in place. Running a firewall on your webserver is asking for trouble because a simple DDOS attack could take down your machine by using CPU and memory. You want that stuff off the production box.

-Tim

---

### Post by koenn on 2008-06-21
IIRC, even virtual machines might have trouble when moving to a different type of processor. VM guests are aware of the processor they run on, i.e. the processor of the host.

The best way I see is to reproduce the system : you collect all relevant information about the system (configuration files, what packages are installed, etc ). 
You the do a clean install, but preferably automated (eg preseed) with the config you collected from the original system. The clean install will match the new hardware, the preseed file and some scripts (eg to install all software from the original system) will configure it to match the original system. Then copy the data, and you're done. 

It requires some work and some preparation, but lots (if not all) of it can be scripted, so in the end it's about as easy as restoring from backups. 

I've played with this a couple of times, here are some notes : 
[http://users.telenet.be/mydotcom/howto/linux/ubuntuexpert.htm](http://users.telenet.be/mydotcom/howto/linux/ubuntuexpert.htm)

---

### Post by jmz2 on 2008-06-21
> **windependence said:**
> Well I'm a bit confused because all my hosts are not accessible from the outside, just the VMs. What security are you setting up on the host? Your host company should also be running a proper firewall. If not, you should consider putting one in place. Running a firewall on your webserver is asking for trouble because a simple DDOS attack could take down your machine by using CPU and memory. You want that stuff off the production box.

-Tim

I access by SSH. How do you access your host? 

When I speak about security I mean firewall configuration, Portsentry, Snort.... 

I understand running the iptables can mean a DDOS but  before I supose you have to find an open port. I run scanning with Nessus to be sure that no port is showing opened on the server.

---

### Post by windependence on 2008-06-21
Well I haven't moved from say AMD to intel or from 32 bit to 64 bit or vice versa but that would be rather drastic. I think if you stayed with either 32 bit or 64 bit you should be OK because of the hardware abstraction layer. I have moved mine to different processors but not aother brand or data width.

-Tim

---

### Post by windependence on 2008-06-21
> **jmz2 said:**
> I access by SSH. How do you access your host? 

When I speak about security I mean firewall configuration, Portsentry, Snort.... 

I understand running the iptables can mean a DDOS but  before I supose you have to find an open port. I run scanning with Nessus to be sure that no port is showing opened on the server.

Well to be honest I have a box on the network that only allows ssh connections and no root access. From that box, I ssh to the hosts. I rarely have to do anything to the hosts anyway. All my VMs are FreeBSD and I run a hardware firewall in front of them. The servers only have 80 and 443 open to the outside world. I can control the VMs on the host via command line. I think it would be safe to allow ssh to the outside world via a non-standard port and without root login though.

-Tim

---

### Post by koenn on 2008-06-21
> **windependence said:**
> Well I haven't moved from say AMD to intel or from 32 bit to 64 bit or vice versa but that would be rather drastic. I think if you stayed with either 32 bit or 64 bit you should be OK because of the hardware abstraction layer. I have moved mine to different processors but not aother brand or data width.

-Tim
moving from 32 bit to 64 bit would certainly be drastic, but even a move from say AMD to Intel might fail (even for a VM) e.g. if it runs Linux with an AMD-optimized kernel. 

In this sort of scenario, you'd need an identical or compatible  2nd machine standing by, and test if your restore would work, in stead of relying on "any available machine". Or prepare for a disaster recovery scenario based on automatic installs, like the one I mentioned earlier.

---

### Post by jmz2 on 2008-06-21
> **koenn said:**
> 
The best way I see is to reproduce the system : you collect all relevant information about the system (configuration files, what packages are installed, etc ). 

Let's see if I make it right, please sugestions are welcomed:
To collect config files a tar /etc would do? Is there anything else to collect for config's?
To collect packages installed: dpkg --get-selections plus dpkg --set-selections, right?
What else to collect?

> **koenn said:**
> 
You the do a clean install, but preferably automated (eg preseed) with the config you collected from the original system. The clean install will match the new hardware, the preseed file and some scripts (eg to install all software from the original system) will configure it to match the original system. Then copy the data, and you're done. 
I will have to learn about this, never done it before.

> **koenn said:**
> 
It requires some work and some preparation, but lots (if not all) of it can be scripted, so in the end it's about as easy as restoring from backups. 
An script of this would be just wonderfull, any ideas if there is one already?

---

### Post by koenn on 2008-06-21
> **jmz2 said:**
> Let's see if I make it right, please sugestions are welcomed:
To collect config files a tar /etc would do? Is there anything else to collect for config's?
To collect packages installed: dpkg --get-selections plus dpkg --set-selections, right?
What else to collect?

An script of this would be just wonderfull, any ideas if there is one already?


tar /etc ad dpkg  --get-selections is a good start. What else you need depends on how you're going to restore, e.g. you might want to create new user accounts with exactly the same UID as on the original system, so the ownership and permissions don't get messed up, or you can recreate new accounts (using the original user names) and reset the permissios and ownership on relevant files. 

Best way to find out is to test it and fix what doesn't work, until you can completely duplicate the system. The link I gave and other pages linjed to from there might give you some pointers.

There isn't a standard script to do this, it depends on what system you have and how you want to go about it, as with the example of the user accounts. Still, all system administration can be done from a shell, and if it can be done from a shell it can be scripted (99.9% of the time).
I imagine your script will include stuff such as

for pkg in list_of_packages; do apt-get install $pkg  (or something with dpkg --set-selections)
tar -x etc.tar.gz
for name in list_of_users; do useradd  [-options] $name
(+ likewise for groups, possibly usermod to add users to groups, etc)

while a preseed file will allow you to pre-answer the questions the installer typically asks (country, time zone, keyboard, which repos, ....)

so, not hard at all, just a bit of work.

---

