---
title: "[all variants] Updating SSH over SSH"
date: 2008-06-17
forum: Server Platforms
---

### Post by mdmadph on 2008-06-17
I've got an 8.04 server that I remote into and admin, etc.  I've been running "apt-get upgrade" for a while now to update it every now and then, but i've noticed that there are a few updates that are held back (ssl ones and ssh, I think).   I'm supposing they're being held back because I'm currently logged in via SSH, so is there any way that I can configure my system to run apt-get upgrade periodically without me ssh'ing in?  something with cron maybe?

---

### Post by HermanAB on 2008-06-17
If the server is on the other side of the globe, then first talk to the help desk people at the server farm and give them your root password BEFORE you mess with SSH.  Then later if all went well, change the root password.

If the server is in the room next door or under your desk, simply install the new packages using dpkg and then restart SSH - you should not even lose your connection, but it is best to be prepared for the worst.  If it screws up, plug in a keyboard and screen.

---

### Post by littlegreiger on 2008-06-17
I don't believe the reason for the packages being held back is because of SSH being in use when you issue the command, I could be wrong though. I had the same "problem" a few weeks ago and the way I solved it was with ```
sudo aptitude safe-upgrade
``` that should allow you to update any packages that are being held back. I can't remember the exact reasons they're being held back but you will definitely want to update SSH and SSL because of the fairly recent error that was found in the Debian (which Ubuntu is based off) random number generator that was used in the creation of SSH keys. Leaving the old version of SSH is a security risk.

Also when the updated SSH package installs, the host key will be changed so any computers that SSH into the server will need that key removed from their known_hosts file or they will give an error and not connect.

---

### Post by gtdaqua on 2008-06-18
> **littlegreiger said:**
> I don't believe the reason for the packages being held back is because of SSH being in use when you issue the command, I could be wrong though. I had the same "problem" a few weeks ago and the way I solved it was with ```
sudo aptitude safe-upgrade
``` that should allow you to update any packages that are being held back. I can't remember the exact reasons they're being held back but you will definitely want to update SSH and SSL because of the fairly recent error that was found in the Debian (which Ubuntu is based off) random number generator that was used in the creation of SSH keys. Leaving the old version of SSH is a security risk.

Also when the updated SSH package installs, the host key will be changed so any computers that SSH into the server will need that key removed from their known_hosts file or they will give an error and not connect.

safe-upgrade doesnt 'solve' it. 

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Why are they still kept back???

---

### Post by littlegreiger on 2008-06-18
Try ```
sudo aptitude full-upgrade
``` I just tried this on a VMware image that had ntfs-3g held back and it upgraded it.

However, the man page says that using this command may have unwanted actions. I believe that it should work without any problems though.

---

### Post by gtdaqua on 2008-06-18
I had to do: 

```

sudo apt-get install linux-server

```

and it upgraded the linux-image-server and the linux-server packages. And wherever openssh-client and openssh-server were kept back, I had to do an explicit:

```

sudo apt-get install openssh-server

```

and it upgraded the server and client packages and re-generated the RSA/DSA keys.

---

### Post by MJN on 2008-06-18
Just so you know for next time, the 'problem' you were seeing (i.e. packages being held back) is due to your use of the **upgrade** option with apt-get.
 
Specifically, **upgrade **tells apt-get to only upgrade what's already installed, i.e. it will not install any new packages. So, if an installed package requires new packages to be installed in order for itself to be upgraded then they will be held back.
 
There are two solutions to this - either explicitly **install** the held-back packages (which will also include the installation of any dependencies required to complete) as you did, or use the **dist-upgrade** option which will perform an upgrade to existing packages and install any new dependencies as required.
 
(Incidentally, the SSH server is a good example - it wasn't because you were SSHing in that it was held back (though that is an understandable assumption to make) but rather that the upgrade also included the installation of a new package to check for weak keys hence why it was being held back when only using the **upgrade** option).
 
Mathew

---

### Post by firecat53 on 2008-06-18
Another option is to actually just start up aptitude:

sudo aptitude

and then reload your packages (u), mark upgradeable packages (U) and the apply your changes (gg).

Sort of like Synaptic for the command line :)

Scott

---

