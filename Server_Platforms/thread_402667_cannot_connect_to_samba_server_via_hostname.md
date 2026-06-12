---
title: "cannot connect to samba server via hostname"
date: 2007-04-06
forum: Server Platforms
---

### Post by skeeloo on 2007-04-06
I have a Samba Server that is working fine. I've used testparm and smbclient to test my smb.conf configuration file. Everything seems ok.

I have Windows Server 2003 as a domain controller. Our users are being authenticated via ADS.

Whenever our users want to access the samba shares, samba authenticates user with ADS, and opens up share.

Problem is that to actually access the server, we have to use the ip address or FQDN.

The hostname for Samba is:

linux

To access our Samba Server, we have to type in either 192.168.10.10 (example) or linux.domain.com (example, I didn't want to publish our internal network).

Further, when I ssh into the server, I can use hostname (linux), but actually logging into the public shares (XP --> start, run, \\192.168.10.10\ or \\linux\) when user authenticates, either 

192.168.10.10\username
pwd

or linux.domain.com\username
pwd

must be used.

Hopefully this is not too confusing and enough information to where somebody can help. 

Please Help.

Thanks.

---

### Post by spin2cool on 2007-04-06
I think what you'll need to do is add a line to your /etc/hosts file with the IP address of the server and the alias.

for example:
192.168.0.123      servername

you may have to restart for the change to take effect.

---

### Post by skeeloo on 2007-04-11
Thanks.

My original /etc/hosts file had this

127.0.0.1   localhost
127.0.1.1   dappersamba.domain.local 

I am just using a regular domain name for example

I then added:

192.168.20.22   dappersamba.domain.local   dappersamba

Is this what you were talking about?

I still can't access my shares via hostname.

From an XP workstation, I would go to start, run, then type in \\dappersamba\somedata

I would proceed to input:

(generic)
username: testuser
password: *******

What shows up next is:

username: dappersamba\testuser
password:  ******

however if I input Fully Qualified Domain Name (FQDN, is this right term)

username: dappersamba.domain.local\testuser
password: ******

or IP Address of dappersamba

username: 192.168.20.22\testuser
password: *******

I would be connected to share.

I can ping dappersamba from an XP workstation, and get replies from 192.168.20.22

from dappersamba, I can ping XP1, which is the XP workstation I am using, and get replies from 192.168.20.38 (again generic ip address for example).

My Active Directory, workstations, dappersamba can resolve each other by name, yet when I try to authenticate, I get that problem.

Please help me out! I am not an experienced Linux user, I would appreciate any help I can get.

Thanks.

---

