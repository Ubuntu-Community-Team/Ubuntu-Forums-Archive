---
title: "Samba PDC - XP client cant join domain"
date: 2011-03-31
forum: Server Platforms
---

### Post by pangeh on 2011-03-31
Hi All,

I'm new to ubuntu and linux. 

I am practising setting up a small network using UBUNTU as a PDC through SAMBA to service xp clients. 

I have sucessfully setup DNS on the Ubuntu server using Bind9 and can nslookup from both the client and the server by FQDN and can also ping ipaddress.

I have setup a basic smb.conf file however when I try to add the xp client to the domain I get an error message saying a domain controller for the domain could not be contacted. 

I have disabled the firewalls on both the server and the xp client and still get the same error message when trying to join the domain. I've checked my network settings on the client, its set to use a static IP address and the DNS server and WINS server are set as my Ubuntu Samba PDC address.

I haven't been able to see anything odd in the smb.conf file that might cause this issue. I can connect directly to the shares using the samba network account that I created by going to start run and typing in the unc path.

Not sure what the cause of this issue is, I thought it might be a DNS issue on the client. One odd thing I noticed is that when I do nslookup using just the server name and not the FQDN i get a message in dos saying that the default server cannot be found but says that the server name for the [ipadress] cannot be found. It does list the correct ip.

I'm not sure what is causing the problem of stopping my xp client from joining the Ubuntu Samba PDC. I'm using UBUNTU server 10.04.

Thanks in advance for any assistance/pointers in the right direction.

kind regards
P

---

### Post by pangeh on 2011-04-01
After some investigation and looking on the net I loaded service pack 3 on the xp virtual machine as it was only sp2. I also installed .net. This seems to have  resolved the issue. It appears to be something to do with security in XP itself and not anything to do with the samba setup on the server or Bind DNS settings I had configured.

So in conclusion the resolution to this issue is to update the XP machine with latest patches and security updates. (although Loading SP3 I think is enough)

---

