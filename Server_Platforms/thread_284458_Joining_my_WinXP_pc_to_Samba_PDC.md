---
title: "Joining my WinXP pc to Samba PDC"
date: 2006-10-25
forum: Server Platforms
---

### Post by bstear on 2006-10-25
Hi I setup Samba initially just to serve files and printers. I can get to the shares but I want to setup Samba as a Domain controller for my small network at home consisting of 2-3 computers. I want it to hold all my profile information. I uncommented the necessary fields within smb.conf and for some reason when did apt-get install samba I don't have any files but two under /etc/samba  they are smb.conf and gdbcommands. I do not have smbd, nmbd , smbusers, smbclient..  and im not sure why. 

I looked through the documentation on samba's website and it says you can set it up so that it will automatically join the computer to the domain without having to specify it first. 

When I try to use the only account on my Ubuntu LAMP installation to join it to the domain it says that I cannot use a username that is logged in already to join it to the domain... or something to that effect. I am not in front of it right now. Perhaps someone knows what I am talking about.  When I get home I can post the exact error. But I have it set to security = share 
Domain logons = yes   domain master = auto

Thanks..

---

### Post by Iowan on 2006-10-25
On my system, **find / -name "smbclient"** turned up:
/usr/bin/smbclient
/usr/share/doc/smbclient
I'm still very early in the attempt to build a Samba DC. I've found a few guides -  one called _LDAP-Samba PDC (for Linux and Windows_) looks promising... 
[edit] Finally found it here:
[https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?]("https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?")
See if this one helps:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba")

Here's another one:
[https://help.ubuntu.com/community/SettingUpSambaPDC]("https://help.ubuntu.com/community/SettingUpSambaPDC")

---

### Post by bstear on 2006-10-25
Here is a screen capture of the Error Box

---

### Post by hortimech on 2006-10-26
It would seem that you are already connected, have you been looking at whats on your server through "My Network" on your windows box?
If so easiest way is to just reboot it and then try again to join the domain. Right click "My Computer", down to properties, then click Computer name tab. This will show the workgroup name, click on change, click the button next to domain and enter the domain name that is in your smb.conf (by the way change security=share to security=user), a box should open, enter 'root' as the user and the root password for your server (you did install your server as an expert didn't you). You need to be root to join to the domain, with an UID of 0 , I think with standard ubuntu your user/administrator gets a UID of 1000.

---

### Post by bstear on 2006-10-26
I doubt I installed my Server as a expert because I have no idea what your talking about. I only have one account on the computer and I have to sudo whenever I want to run something. So I guess I need to enable to root account and assign a password then I can join it to the domain.  Hopefully your still nearby and can reply soon. I did get around the problem of it saying I was logged on already but it still won't join. Now it says that the Parameter is incorrect. The name of my server is homefs so I type in the username box \\homefs\username .. then my password. But this might be because of the root user not being active that Im having issues.

---

### Post by hortimech on 2006-10-26
if when you start the install you look at the bottom of the screen there is a line which gives you various options, the last one is (I think) F6, if you press this twice, it gives you the option to do a normal or expert option. If you select expert you get lots of options, just keep accepting the defaults until you get to the one that asks if you want to allow root logins, answer yes to this, enter your root password and when you finish you can log in as root, As You would want to on a server. 
There will be a file somewhere in /etc that will allow root logins if it is changed but I do not know which, perhaps somebody else does?. To get a root password just "sudo passwd root" and enter the password.

---

