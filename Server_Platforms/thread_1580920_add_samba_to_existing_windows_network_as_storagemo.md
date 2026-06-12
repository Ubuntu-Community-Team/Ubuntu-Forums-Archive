---
title: "add samba to existing windows network as storage/mounted drive"
date: 2010-09-24
forum: Server Platforms
---

### Post by snek on 2010-09-24
I recently found an unused server at our office with 2x500GB drives in it.
So I set it up as RAID1 and plan to use it as an extra storage server.

Now, I have everything setup, but I don't know how to add it to the network.
Our Windows server is running 2008 R2, it is currently the DHCP, DNS and storage server.
It's a quadcore beast and the LAN consists of only Cisco Gbit equipment.

Preferably I'd want to share it so that it can automatically be mounted by the XP clients as another harddrive.

Can anybody help me with this problem?
I've tried googling this, but of course it's near impossible to find any kind of answer.
All I find is how to setup Samba as the primary server to setup a Windows network, but considering we already have a primary Windows server those guides are useless.

---

### Post by Oaknut on 2010-09-24
[http://www.howtoforge.com/ubuntu-10.04-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-10.04-samba-standalone-server-with-tdbsam-backend)
 
Samba stand alone serving smb shares to the network - in your case Windows clients :)
 
 
Actually - even simpler ....... [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

---

### Post by snek on 2010-09-25
That's not what I'm asking, I need to know how to add a samba share to Windows Server 2008 R2 so that it shows up on everyone's computer automatically...
I have all the clients configured to run a logon.bat which mounts two shares to drive letters already.
But since the Windows Server is the primary SMB server how do I go about making the 2nd server accessible as well. In this case there's no need for different users, it's just simple filestorage.

---

### Post by SeijiSensei on 2010-09-25
Once the server is up and running they just need to map a drive to \\server\share.  I'd assume you could just add a "net use" command to login.bat.

What happens if you export a share from a Windows workstation?  Can you map that to a network drive in your login.bat?  Samba should be no different as long as you've got the right domain/workgroup definitions and authentication configured correctly in /etc/samba/smb.conf.

---

### Post by koenn on 2010-09-25
> **snek said:**
> I've tried googling this, but of course it's near impossible to find any kind of answer.
All I find is how to setup Samba as the primary server to setup a Windows network, but considering we already have a primary Windows server those guides are useless.

The internet is full of guides on Samba in all sorts of configurations. If google doesn't seem to get you the answer, this probably means that you don't fully understand the problem you're trying to solve, and/or don't recognize the solutions. 

As the others in this thread have pointed out, you can simply map a drive letter to a samba share - this is done by the clients (eg. via a logon script);  no need to pass through that Windows server at all.

Unless, of course, you have issues with users and passwords.
You didn't mention how you (are planning to) manage user accounts for the samba server and its shares ...

---

