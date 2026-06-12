---
title: "Configuring Ubuntu as a DNS server"
date: 2018-12-18
forum: Server Platforms
---

### Post by peter792 on 2018-12-18
Guys,

I need to set up a DNS server in a lab environment.

I'm following the steps in the following article [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-private-network-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-private-network-dns-server-on-ubuntu-14-04)

The problem is that the lab environment has no internet access  so when I run the the "apt-get install" command it fails.  

Is there a way to either download an ISO with bind9 all ready installed or download the required files manually on another machine and just copy them across the network?

I'm using Ubuntu Server 18.10

Thanks.

---

### Post by Tadaen_Sylvermane on 2018-12-18
Best solution would be to have a local mirror that has internet access. Then point lab to it for packages. This keeps lab machines offline so to speak while still keeping packages available. Only way to do it manually is download the .debs and trial and error until you have it + dependencies.

Why can't  the lab have internet access?

*EDIT* Another note. I'd ssume you are labbing a big system or network.  Therefore you should use 18.04, 5 year lts. Not the 6 month releases.

---

### Post by slickymaster on 2018-12-18
*Thread moved to **Server Platforms**.*

---

### Post by peter792 on 2018-12-18
Thanks for the quick response.  IT dont want to give internet access for security reasons (stupid I know but they wont budge).  Unfortunately I'm not sure the local mirror idea will work either.  

The Ubuntu server is a VM running on a nested ESXi host.  Also the VLAN its on is not routed.

Is there anyway to download an ISO with bind all ready installed?

---

### Post by Tadaen_Sylvermane on 2018-12-18
Could remaster one with it. Out of my knowledge though.

---

### Post by LHammonds on 2018-12-18
Or setup the VM somewhere that does have internet access, then import the VM into the lab environment.

You mentioned ESXi so you could use Oracle VirtualBox or similar to create a VM using vmdk as the HD type.  Then create a new VM and upload / attach the vmdk to it.

However, if you do that, you'd have to do that for every server you want to setup like that.  As mentioned earlier, it might be wiser to do this for a repository server one time like this, then you can build as many servers as you want and direct them to the local repository server.  Then your lab instructions would be almost identical to real-world setup instructions with the exception of the add-repository line at the beginning.

LHammonds

---

