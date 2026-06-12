---
title: "Using Windows Shares with VMware"
date: 2008-12-29
forum: Virtualisation
---

### Post by saturninus on 2008-12-29
Hi everyone.

I installed the latest edition of Ubuntu Studio via VMware.  Everything is working fine, except for the network sharing aspect.

Ubuntu detects my Windows machine but none of the folders I have share enabled show inside Ubuntu.

If anyone has any insight on this it would be appreciated.

---

### Post by bodhi.zazen on 2008-12-29
Try the command line :

Make sure you are using a bridged connection (in vmware) and that the connection is not being blocked by your firewall.

```
sudo apt-get install smbfs

sudo mkdir /media/windows_share

sudo mount -t cifs //windows_ip_address/Share_name -o username=windows_user
```

Change "windows_ip_address" to the actual windows IP address.

Change "Share_name" to the name of the windows share

Change "windows_user" to your window log in name.

Post any error messages.

---

### Post by saturninus on 2008-12-30
That last sudo command didn't work for me.  Instead it scrolled the directions on how to use sudo.

In VMware I have two network adapters.  The first one gives me Internet access, and if I put it on anything other than NAT it fails to work.

The second network adapter I'm not so sure about, but I assume it's what interfaces between my Windows Vista and Ubuntu Studio machines.

---

### Post by thomasr on 2008-12-30
This worked for me:

Go to Places-->Connect to server
Use the drop down ox to select windows share
fill in server field with the servers IP
fill in share field with the share name
fill in user name
click on connect

If this works for you, you can bookmark it in Nautilus.

Seems Ubuntu 8.10 is unable to browse shares, but can connect to a spcified share.

---

### Post by saturninus on 2008-12-30
It's asking me for a password to the domain workgroup.  Thing is, I never set one up.

---

### Post by thomasr on 2008-12-30
Windows XP Home? Professional? 2000? 2003 Server?

try just pressing enter (blank password) - probably wont work, though

Set up a password on the windows box and then try.

---

### Post by Dedoimedo on 2008-12-30
Are you using any sort of firewall?
Do you allow the machines on the vmware subnet (vmnet1 or vmnet8) to connect to your windows machine?
Dedoimedo

---

### Post by saturninus on 2008-12-31
The only firewall in the physical router.  No software firewall.

I give VMware full access to my network.  Ubuntu goes as far as to recognize the computer name, but none of the share folders come up.

I've tried going in gpedit and alterting the local network policies, but there was no luck there.

I've just about given up.  I really don't want to set up and Windows password and will not do it just for Ubuntu.

---

