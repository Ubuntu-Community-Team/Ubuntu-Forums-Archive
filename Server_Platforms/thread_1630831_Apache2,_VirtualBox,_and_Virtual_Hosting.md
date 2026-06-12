---
title: "Apache2, VirtualBox, and Virtual Hosting"
date: 2010-11-25
forum: Server Platforms
---

### Post by samurailink3 on 2010-11-25
I'm in quite the mood to learn something new today, so here is my predicament:

I'm running a central server with a hostname (lets say, example.com), and I've created some development virtual Ubuntu machines using VirtualBox (Bridged networking, each VM has its own internal IP). They are running just fine with 'vboxheadless' and I'm able to view the sites I've created, but what would I do if I wanted to make these public-facing for users to test?

One such virtual server is running Diaspora on port 3000, and the end goal is for the user to receive that site on social.example.com. 

How can I utilize Apache2, VirtualHosts, and VirtualBox to make 192.168.1.103:3000 forward over to social.example.com ?

---

### Post by dirtyhabanero on 2011-01-30
Looks like there is still no answer...

I'm looking into this at the moment. If I understand correctly, you want to run a server (samba, apache or squid - I'm not sure which one is best) on a virtual machine that can then be accessed by the public, i.e. a lady sitting at a cafe. 

So far, I can set up Apache in the VM just like I would on this box. But the problem arises, when I try to ping the VM from this computer, the address cannot be reached. I think I'm not setting the IP address up correctly...I'll let you know how I go.

---

### Post by Bob.Davis@wibble.net.nz on 2011-01-30
If I understand what you are trying to do:

you need two things really, 

1: A router/firewall on the external IP address that will translate/route the incoming traffic on port 80 to the correct internal address.  

2: If you want the name to resolve for the lady at the cafe you have to have the names created in your external DNS  providers records

Most ADSL routers will do step on for you, and to test it you can add the DNS in the hosts file of the computer to get around the DNS requirement..

---

### Post by samurailink3 on 2011-01-31
From a software setup on apache, how would the configuration look?

---

### Post by ensenadaubuntulover on 2011-04-01
> **samurailink3 said:**
> From a software setup on apache, how would the configuration look?

maybe this will help...


cd to /yourhome/.VirtualBox/Machines/YourServerName/

find YourServerName.xml and open with editor


add this lines...

      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/apache/GuestPort" value="80"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/apache/HostPort" value="8888"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/apache/Protocol" value="TCP"/>

      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort" value="22"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort" value="2222"/>
      <ExtraDataItem name="VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/Protocol" value="TCP"/>



where it says ExtraDataItem

you can reach your virtual machine in

[http://yourhostadress:8888](http://yourhostadress:8888)


and you can ssh to your server by

ssh -l YourUser -p 2222 localhost

---

