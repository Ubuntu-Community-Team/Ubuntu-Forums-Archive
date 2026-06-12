---
title: "Samba with W98"
date: 2006-04-03
forum: Server Platforms
---

### Post by jamesr on 2006-04-03
My network is mixture of linux and windows PCs. My fileserver is running Breezy with Samba. After much fiddling about I was able to set up a common directory which is  seen by all PCs on the network. 

Currently and this is the problem the W98 PCs cannot logon onto the fileserver. They can see the Fileserver but I always get incorrect password.

Actions taken so far.
1)Create a new user and password on the W98 (old one had spaces)
2)Create a new user and password on the fileserver ```
sudo adduser
```the same as in line (1)
3)Add a new password for samba```
sudo passwd username
``` as 1 & 2

I have no problems with W2000pro as it allows me to connect as another user.

---

### Post by Iowan on 2006-04-03
Depending on your setup and password sync, do you need to run **smbpasswd** to set up the Samba password?

---

### Post by jamesr on 2006-04-04
Thanks yes I found that I needed to ```
sudo smbpasswd username
``` as you quite rightly spotted. I have not been able to spend any time on the W98 problem because of other commitments including offering help in this forum :D 
Any other suggestions?

---

### Post by olddog on 2006-04-05
I followed the guide at

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

worked great, including on our Win98 machines.

What you could try to narrow down the problem, is set up the users on the Win98 machine using blank passwords, then Samba will ask them for the password when attempting to access the share.

You may want to make sure in Network properties on Win98 that you are set to use Windows Networking as the logon prompt (i.e. when booting).

---

### Post by jamesr on 2006-04-05
Thanks for the info but I think it may be a windows problem on the one W98SE I was using to checkout the problem. The other W98SE are laptops from various members of the family so I will need to check when they are around.

I have got around the problem by creating a shared directory on the W98 system and logging in to that from another PC on the network. Since the W98 PC in used for faxing and emailing the traffic is low to the network so I am quite happy with the workaround at present.

Yes I believe the setting is Client for Windows Network in the network properties.

---

