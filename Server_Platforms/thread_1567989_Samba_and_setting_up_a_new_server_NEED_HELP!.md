---
title: "Samba and setting up a new server: NEED HELP!"
date: 2010-09-04
forum: Server Platforms
---

### Post by J.Byram on 2010-09-04
Hello All,

I am trying to set up a server for use at home.  Eventually, it will be hosting a website or two on a better hardware setup, but at the moment, I want to get the basics squared away with.  I am currently running this server on an old E-Machines desktop with a AMD 1.3Ghz processor and 1 Gb of ram.  I am using this machine as a learning experience more than anything (want to make sure I can set this up before spending money on better hardware).  

For my first accomplishment on this server, I am trying to set up a simple network file sharing system so that I can use the Window's backup service to back up to the server.  I am running a Samba server and every other computer on the network has a separate login to the server that is identical to login on the client.  

The problem that I am running into is that I can ONLY access the server from my desktop that is running on the same switch as the server.  I can see the server from another computer in the network, but I cannot access the shared folders.  On my laptop, I cannot see the server at all.  I can ping the IP from every machine without issues.  I also have all the computers in question and the samba server running on the same workgroup.  

Here is a picture of the network tree: 

[[IMG]http://imgur.com/wGg4E.jpg[/IMG]](http://imgur.com/wGg4E.jpg)

I can access the server (ByramServ) from ByramBot.  I cannot access it from LHC-PC or the JB-DV3T laptop.  

Is there a setting that I might be overlooking?  I am relatively new to this and I want to make sure this works before I spend any serious money.  

If you guys have any insight or suggestions, it will be greatly appreciated.  Also, if you need additional info about the network or machines, just ask.  

Thanks a bunch
-John

Edit: Added network tree picture.

---

### Post by CharlesA on 2010-09-04
Sounds like a name resolution problem, if you can ping via ip address.

Are you able to connect to it via \\ipaddress\share ?

Are you running a local dns server on yer network?

---

### Post by J.Byram on 2010-09-04
> **CharlesA said:**
> Sounds like a name resolution problem, if you can ping via ip address.

Are you able to connect to it via \\ipaddress\share ?

Are you running a local dns server on yer network?

I am not running a local DNS server on the network.  Should I be?  I am currently using OpenDNS.org's DNS servers as my DNS because the router I have tends to insert its own DNS (192.168.1.1) and causes webpage re-directs.  Due to this I had to manually set DNS servers on the machines.  If you look at the network tree, JB-DV3T and ByramBot and Dell D620 are all using the OpenDNS servers.  

I tried the \\ipaddress\share as well as \\ipaddress and \\ByramServ and had no luck with any of them.  Currently, the laptop (JB-DV3T) and the desktop (LHC-PC) do not see the server on the network as a network device.  They see each other, but cannot access the shared folders.

---

### Post by koenn on 2010-09-04
yes, name resolution would be my first guess too.
Do all switches represent separate networks,routed by that Linksys router ?
In that case, hosts on the same switch probably resolve each others names by broadcast - and you normally can't broadcast across a router.

look into dnsmasq for an easy, efficient dns server to resolve your local names. Since OpenDNS doesn't know your servers name or IP address, it's not going to be of any use, is it?


another solution would be to setup samba to be a WINS server, then configure your (windows) clients to use WINS in stead of broadcasts


However, since you can't access shares by ip address, you may have other issues as well. Check the Samba logs for failed connections or so

---

### Post by CharlesA on 2010-09-04
+1 for dnsmasq.


Try running these commands on the server.

```
smbtree
```
```
testparm
```

---

### Post by J.Byram on 2010-09-05
> **koenn said:**
> yes, name resolution would be my first guess too.
Do all switches represent separate networks,routed by that Linksys router ?
In that case, hosts on the same switch probably resolve each others names by broadcast - and you normally can't broadcast across a router.

look into dnsmasq for an easy, efficient dns server to resolve your local names. Since OpenDNS doesn't know your servers name or IP address, it's not going to be of any use, is it?


another solution would be to setup samba to be a WINS server, then configure your (windows) clients to use WINS in stead of broadcasts


However, since you can't access shares by ip address, you may have other issues as well. Check the Samba logs for failed connections or so

I was finally able to access the shares folder on the machines that could not before.  I ended up setting up DHCP reservation on my router for the server and that seemed to resolve the access side of things.  That being said, I still cannot see the server as a networked machine or shared system.  

As for the switches, I do not want them to act as their own subnets but it makes sense that I the system is acting the way it is because of how it is set up.  

If I use dnsmasq, do I need to set up a linux router (i.e. smoothwall or something to that extent) in order to host dnsmasq?  Or can I set it up on the current server and have it redirect back to everything else?  Also, how might one set up dnsmasq for this situation?  If dnsmasq doesn't work, I will try the WINS server.  

Of the two, which is more of a stable solution?

---

### Post by J.Byram on 2010-09-05
> **CharlesA said:**
> +1 for dnsmasq.


Try running these commands on the server.

```
smbtree
```
```
testparm
```

So I ran: 
```
smbtree
``` and found that I did not have the smbclient installed.  I ran: 
```
apt-get install smbclient
```

and then the smbtree command and got this response from the server:

WORKGROUP
[INDENT]\\OFFICE1  Office front desk[/INDENT]
[INDENT]\\BYRAMNET[/INDENT]

BYRAMWG
[INDENT]\\LHC-PC[/INDENT]
[INDENT]\\BYRAMSERV  ByramServ[/INDENT]
[INDENT][INDENT]\\BYRAMSERV\servadmin  Home Directories[/INDENT][/INDENT]
[INDENT][INDENT]\\BYRAMSERV\IPC$  IPC Service (ByramServ)[/INDENT][/INDENT]
[INDENT][INDENT]\\BYRAMSERV\print$  Printer Drivers[/INDENT][/INDENT]
[INDENT][INDENT]\\BYRAMSERV\homes  Home Directories[/INDENT][/INDENT]
[INDENT]\\BYRAMBOT[/INDENT]

The Office1 and ByramNet machines are not on the workgroup in question and that is fine.  I will end up including Office1 and getting rid of ByramNet when I get this whole project hashed out.

---

### Post by CharlesA on 2010-09-05
I've got mine set up to just use a local DNS server, since WINS is pathetically outdated. You can just set up dnsmasq on that server and have the DHCP server assign that DNS server as primary, and the router's DNS server as secondary.

Check [here]("https://help.ubuntu.com/community/Dnsmasq") to see how to set up dnsmasq. 

Are you running a firewall on the server? if so, make sure that TCP ports 139 and 445 are unblocked and UDP ports 137 and 138 are unblocked as well.

---

### Post by J.Byram on 2010-09-05
> **CharlesA said:**
> I've got mine set up to just use a local DNS server, since WINS is pathetically outdated. You can just set up dnsmasq on that server and have the DHCP server assign that DNS server as primary, and the router's DNS server as secondary.

Check [here]("https://help.ubuntu.com/community/Dnsmasq") to see how to set up dnsmasq. 

Are you running a firewall on the server? if so, make sure that TCP ports 139 and 445 are unblocked and UDP ports 137 and 138 are unblocked as well.

I set up dnsmasq on the server and I am wondering how I "have the DHCP server assign that DNS server as primary..."?  I have not set static DNS servers on my router and the router is the only thing acting as the DHCP.  I do have DHCP reservation set up for every device here, so that might make this process easier.  

At this point, I am confused as to whether this is working or not and what I need to do on the client side to make sure that this set up works.  Also, how I go about doing that. 

So far, this is what I can do:
- Access and see the shared folders with the desktop (ByramBot) on the same switch as the server.
- Access the server from my laptop (JB-DV3T) through the wireless via "\\server IP" but I CANNOT see it as a networked device.

---

### Post by CharlesA on 2010-09-05
Yah, it's definitely a name resolution thing.

What you could do is test it on a client machine: point the dns server to the ip of the machine running dnsmasq and see if you can connect to the Samba share.

I've got DD-WRT on my router, but I believe you can just set DHCP to assign static DNS servers.

---

### Post by J.Byram on 2010-09-05
> **CharlesA said:**
> Yah, it's definitely a name resolution thing.

What you could do is test it on a client machine: point the dns server to the ip of the machine running dnsmasq and see if you can connect to the Samba share.

I've got DD-WRT on my router, but I believe you can just set DHCP to assign static DNS servers.

so, just to get it straight: change the DNS server settings under the network device IPv4 settings to the ByramServ running dnsmasq?  

I have the default firmware on the Linksys and it allows me to set up to three static DNS servers.  Should I set it to the internal IP so that the router gets the DNS information from the server?  

And thank you so much for helping this far...this has been the most progress that I have had on this issue from the start!

---

### Post by CharlesA on 2010-09-05
Yeah, you can do it to see if it works.

I've not used the default linksys firmware in ages, but the way the DD-WRT firmware work, is that if you set the static DNS servers, they are assigned via DHCP.

---

### Post by J.Byram on 2010-09-05
> **CharlesA said:**
> +1 for dnsmasq.


Try running these commands on the server.

```
smbtree
```
```
testparm
```

I tried, just to see, what the SMBTREE command would result now that we have dnsmasq up and my laptop is on.  It returned a much different result: 

I get this response for \\OFFICE1, \\BYRAMNET, \\LHC-PC, and \\JB-DV3T:

cli_start_connection: failed to connect to _OFFICE1_<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

The underlined part changed for each computer.  I don't know if this is significant, but it seems like a problem.

---

### Post by CharlesA on 2010-09-05
Basically what smbtree does is go out and try to list all the shares that are available on the network. The error message means that it can't connect to those machines to see if they have shares on them. That's probably ok, if you haven't enabled file and printer sharing on them.

Do you have the same user on every machine?

This is what mine returns:

```
WORKGROUP
        \\ATLANTIS                      atlantis server (Samba, Ubuntu)
                \\ATLANTIS\IPC$                 IPC Service (atlantis server (Samba, Ubuntu))
                \\ATLANTIS\print$               Printer Drivers
ASGARD
        \\XP
        \\THOR
                \\THOR\IPC$             IPC Service ()
                \\THOR\Shared           Shared Folder
                \\THOR\Music            Music Folder
                \\THOR\Karen            Karen's Folder
                \\THOR\ISOs             ISO Folder
                \\THOR\DVDs             DVD Folder
                \\THOR\Charles          Charles' Folder
        \\OSIRIS
cli_start_connection: failed to connect to OSIRIS<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
        \\ODIN
                \\ODIN\Users
                \\ODIN\IPC$             Remote IPC
                \\ODIN\F$               Default share
                \\ODIN\D$               Default share
                \\ODIN\clone
                \\ODIN\C$               Default share
                \\ODIN\ADMIN$           Remote Admin

```

Osiris is unable to be found since it's off. :P

---

### Post by J.Byram on 2010-09-05
> **CharlesA said:**
> Basically what smbtree does is go out and try to list all the shares that are available on the network. The error message means that it can't connect to those machines to see if they have shares on them. That's probably ok, if you haven't enabled file and printer sharing on them.

Do you have the same user on every machine?

This is what mine returns:

```
WORKGROUP
        \\ATLANTIS                      atlantis server (Samba, Ubuntu)
                \\ATLANTIS\IPC$                 IPC Service (atlantis server (Samba, Ubuntu))
                \\ATLANTIS\print$               Printer Drivers
ASGARD
        \\XP
        \\THOR
                \\THOR\IPC$             IPC Service ()
                \\THOR\Shared           Shared Folder
                \\THOR\Music            Music Folder
                \\THOR\Karen            Karen's Folder
                \\THOR\ISOs             ISO Folder
                \\THOR\DVDs             DVD Folder
                \\THOR\Charles          Charles' Folder
        \\OSIRIS
cli_start_connection: failed to connect to OSIRIS<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE
        \\ODIN
                \\ODIN\Users
                \\ODIN\IPC$             Remote IPC
                \\ODIN\F$               Default share
                \\ODIN\D$               Default share
                \\ODIN\clone
                \\ODIN\C$               Default share
                \\ODIN\ADMIN$           Remote Admin

```

Osiris is unable to be found since it's off. :P

I do not have the same user on every machine, however, I made a separate user account on the server that corresponds to every different machine.  Initially, I have not added OFFICE1 or PETER or the other laptops and HP homeserver because they are not that important to get this running on at the moment.  Eventually, they will be added, but that will happen when the new hardware is implemented for this server.

---

### Post by J.Byram on 2010-09-05
Also, when I set up the DNS settings under my network device settings to the IP for the server running DNSMASQ, I lost connection and could not resolve any hosts on my laptop or the desktop that is on the same switch as the server.  

I wonder what I did wrong...

---

### Post by CharlesA on 2010-09-05
Was that machine you modified to point to the DNSMASQ server have the ip address of the router as secondary DNS server?

---

### Post by J.Byram on 2010-09-06
> **CharlesA said:**
> Was that machine you modified to point to the DNSMASQ server have the ip address of the router as secondary DNS server?

No, it did not have the router as the secondary DNS server.  That being said, I tried that on my desktop and my laptop and they both have connection to the internet again, however, I still cannot see the server from my laptop.  I can connect to it directly using its IP address, but that is it.  

Is there some other setting that I am missing to allow for the server to broadcast and be seen by everything on the network?  Also, by having my DNS servers set manually, am I going to have issues when I try and use my laptop at school on the university network?  I would assume that I would have issues, but I could be wrong.

---

### Post by CharlesA on 2010-09-06
It would be easier to set it up to have the DNS and whatnot assigned via DHCP, that way it won't mess it up if you aren't connected to the home network.

---

