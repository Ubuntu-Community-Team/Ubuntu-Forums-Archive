---
title: "[SOLVED] BackupPC can't find Windows XP Home hosts"
date: 2008-02-11
forum: Server Platforms
---

### Post by Pitt Stains on 2008-02-11
Hello,

I am running BackupPC from the repos on Ubuntu 7.10.  I am not sure if this is a problem with BackupPC, the Windows hosts, or something about the networking environment, but here goes:

I'm having a heck of a time getting the application to find the hosts on the network.  The hosts are running Windows XP Home.  They are getting IP addresses via DHCP.

**_Documentation_**
Here's the info on how BackupPC finds hosts: [http://backuppc.sourceforge.net/faq/BackupPC.html#how_backuppc_finds_hosts](http://backuppc.sourceforge.net/faq/BackupPC.html#how_backuppc_finds_hosts).

**_DHCP Flag Set to 0 -- Recommended for Most Hosts_**
When this flag is set to 0, BackupPC first checks for DNS entries.  All the hosts on this network are DHCP, so this fails.

Next, BackupPC attempts a NetBios multicast to find the host, using the command:

```
nmblookup this-host
```

This also fails, but I'm not sure why.  It actually works for one of my two test machines.  One is a virtual machine (working) and the other is a Dell laptop.  Both are running WinXP Home, and both are pretty fresh installs.  I had a lot of trouble getting the VM to work and then all of a sudden it just did.

**_DHCP Flag Set to 1 -- Recommended for Most Hosts_**
I also tried setting the DHCP flag to 1 in the host configuration file.  According to the manual, you only need to use this DHCP feature if your client machine doesn't respond to the NetBios multicast request:

```
nmblookup this-host
```

but does respond to a request directed to its IP address:

```
nmblookup -A W.X.Y.Z
```

I believe the host does respond to the latter request, but I'm not currently at the office to double-check.

Anyway, when this flag is set, BackupPC will check the NetBIOS name of each machine in the IP range you provide, using a command of the form:

```
nmblookup -A W.X.Y.Z
```

Even with the DHCP flag set to 1, BackupPC is unable to find the machine.

**_Identifying the Problem_**
I don't know much about NetBIOS, but I can only conclude that the Windows machines aren't correctly configured to broadcast their NetBIOS names.

I'll be able to test a few more things when I get back in the office tomorrow, and maybe a fresh look is all that's needed to resolve the problem, but if anyone has any suggestions in the meantime or has experienced similar problems, your help would be much appreciated.

Thank you very much,
-Pitt

---

### Post by Skoude on 2008-02-12
HEllo!

If your Backuppc server cannot find the windows xp machines that are in the same network, so check that you are using the same dns servers in windows machines and in backuppc server. 

Make shure that your backuppc server has been registered to dns server by issuing for example 'ping backuppcserverhostname' - command from windows hosts and also check that the ping works from backuppc server to windows hosts. 

If the 'ping hostname' works then try the nmblookup commands. 

Also check that you get full hostname in backuppc server by issuing command:
'hostname -f'  - command. It should return something like 
mymachine.mydomain.com

I hope this helps.. :)

---

### Post by Pitt Stains on 2008-02-12
Thanks for your response, Skoude.

I've verified that the BackupPC server and the Windows host are both on the same network, and they are both using the same DNS, though I'm not clear why the DNS matters.

From the Windows host, I can ping backuppc.office successfully.  From the server, I can ping the Windows machine by its IP address.  From the server, pinging the Windows machine by hostname does not work (I didn't expect it to).

If I issue:
```
hostname -f
```
from the server I get just backuppc, not backuppc.office.  However, I don't see that this matters, as it's the server that's looking for the Windows machine and not the other way around.

Now I'm testing the nmblookup command.  This command fails for every hostname on the network (Linux or Windows) except two: backuppc and vm-testbox.  vm-testbox is the hostname of the virtual machine that I mentioned in my first post, which is working correctly.  I should mention that backuppc and vm-testbox are both virtual machines hosted on the same physical machine.  I think there may be some funky VM-specific network thing going on here.

When I issue commands in the form of:
```
nmblookup -A W.X.Y.Z
```
I also get failure, except for the backuppc and vm-testbox.

Interestingly, when I do the nmblookup command using -A and the IP address of backuppc, I get:
```

        BACKUPPC         <00> -         B <ACTIVE> 
        BACKUPPC         <03> -         B <ACTIVE> 
        BACKUPPC         <20> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
        MSHOME          <1d> -         B <ACTIVE> 
        MSHOME          <1e> - <GROUP> B <ACTIVE> 
        MSHOME          <00> - <GROUP> B <ACTIVE> 

```

The nmblookup man page is not clear on what all this means, but MSHOME is not the name of the Windows workgroup here in the office.  I think this might be an area worth looking into as well.

Will post back when I know more.

Thanks a lot!

---

### Post by Pitt Stains on 2008-02-12
I edited smb.conf to reflect the correct workgroup name, then restarted Samba and BackupPC.  As far as I can tell, nothing has changed and my problem remains the same.

My other suspicion -- that the two machines could talk because they are both virtual machines on the same host -- is looking less promising, as a third virtual machine on that host doesn't respond to the nmblookup command either.

Anyone?

---

### Post by Pitt Stains on 2008-02-12
After all that, it turned out to be a firewall issue.  Make sure you have the following ports open on your Windows machines:

**File and Printer Sharing**
TCP 139, 445
UDP 137, 138

**Rsync**
TCP 873

Thanks for your help, and good luck out there!

---

### Post by rickyjones on 2008-02-12
Do you have filesharing enabled and the firewall OFF on the XP machines?

I personally suggest that you run some sort of DNS server in the environment and make sure that all computers are registered in DNS. This will alleviate this issue as well.

-Richard

---

### Post by Pitt Stains on 2008-02-12
Yes, File and Printer Sharing need to be turned on.  I was able to leave the firewall up so long as the exceptions I noted earlier are allowed.

The DNS server idea is a good one, but in this environment, most of the staffers use laptops and connect by DHCP.  Configuring their machines to connect with a static IP wouldn't be practical, as they'd have to change those settings each time they left the office and tried to connect from home or the road.

---

### Post by rickyjones on 2008-02-12
> **Pitt Stains said:**
> Yes, File and Printer Sharing need to be turned on.  I was able to leave the firewall up so long as the exceptions I noted earlier are allowed.

The DNS server idea is a good one, but in this environment, most of the staffers use laptops and connect by DHCP.  Configuring their machines to connect with a static IP wouldn't be practical, as they'd have to change those settings each time they left the office and tried to connect from home or the road.

I hate to threadjack here but what are you using as a DHCP server? If it can be moved to an actual server running DNS then you can automatically register your clients in DNS when they receive and IP address from DHCP, therefore you won't have to assign static IP addresses to your clients.

-Richard

---

### Post by Pitt Stains on 2008-02-12
> **rickyjones said:**
> I hate to threadjack here
No worries :-)

> **rickyjones said:**
> but what are you using as a DHCP server?
Errrr, this is a tiny office, and router serves as the DHCP server.  Nothing fancy here.

> **rickyjones said:**
>  If it can be moved to an actual server running DNS then you can automatically register your clients in DNS when they receive and IP address from DHCP, therefore you won't have to assign static IP addresses to your clients.
I had no idea that was possible!  We currently have a BIND9 server handling DNS for internal (development) websites plus one or two other servers.  I don't expect a full how-to here, but if you wouldn't mind pointing me to a link, I'd be very interested to learn more.

Thanks!
-Pitt

---

### Post by rickyjones on 2008-02-12
> **Pitt Stains said:**
> No worries :-)


Errrr, this is a tiny office, and router serves as the DHCP server.  Nothing fancy here.


I had no idea that was possible!  We currently have a BIND9 server handling DNS for internal (development) websites plus one or two other servers.  I don't expect a full how-to here, but if you wouldn't mind pointing me to a link, I'd be very interested to learn more.

Thanks!
-Pitt

Pitt,

The Bind9 server - does it have enough resources to handle another service? What you can do is configure the DHCP server to hand out IP addresses and dynamically update DNS.

I'm looking for a tutorial but I can't seem to find one that will incorporate dynamic DNS updates. It looks like you want dhcp3-server, however.

Lack of documentation bites me in the butt again. Looks like I'll be working on a virtual test of /this/ now...

-Richard

---

### Post by Pitt Stains on 2008-02-12
> **rickyjones said:**
> The Bind9 server - does it have enough resources to handle another service?
Probably.  The demands on the DHCP server would probably be pretty light, as there aren't many machines in the office.
> **rickyjones said:**
> What you can do is configure the DHCP server to hand out IP addresses and dynamically update DNS.
This is handled by the DHCP package, or have you written some custom script that does this?

PS: This sounds so cool; thanks for sharing!

---

### Post by rickyjones on 2008-02-12
> **Pitt Stains said:**
> Probably.  The demands on the DHCP server would probably be pretty light, as there aren't many machines in the office.

This is handled by the DHCP package, or have you written some custom script that does this?

PS: This sounds so cool; thanks for sharing!

This would be handled by the actual DHCP package. It is a part of the DHCP protocol.

---

