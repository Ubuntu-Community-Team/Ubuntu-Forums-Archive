---
title: "configuring samba for file serving"
date: 2010-03-15
forum: Server Platforms
---

### Post by nikonboy2009 on 2010-03-15
new guy, installed ubuntu 8.10 64bit on left over parts for file serving with windows 7, tried the sample config file that installed with it with no luck, then tried new config file, looking at the samba.org website and other peoples configurations i came up with this, any help would be greatly appreciated

[global]
  
  netbios name = NETBIOS_NAME
  workgroup = workgroup
  security = user
  encrypt passwords = yes
  smb passwd file = /etc/samba/smbpasswd
  interfaces = 192.168.1.1/8

[FILE_SHARING]
  
 comment = COMMENT
 path = .................
 writeable = yes
 create mode = 0600
 directory mode = 0700
 locking = yes

---

### Post by Ghostbear121 on 2010-03-15
lol your config is a mess..

```


[global]

netbios name = <YOUR COMPUTER NAME GOES HERE>
workgroup = <YOUR DOMAIN/WORKGROUP GOES HERE>
security = user
encrypt passwords = yes
interfaces = <YOUR NETWORK ADAPTER GOES HERE, IE: ETH0>

[TestShare]
comment = <COMMENT HERE>
path = <YOUR PATH HERE
browseable = yes
writeable = yes
guest ok = no
create mode = 0770
directory mode = 0770

```


Now restart samba, run this:
```

smbpasswd -a  <A samba username you want to use>

```
Now you can connect to your server via  //servername/TestShare  (because we defined the name as TestShare above).

---

### Post by nikonboy2009 on 2010-03-16
thank you for the assistance, I tried that configuration and still nothing, I don't even see the server show up in my network tab in windows, I'm thinking I don't have the server configured properly to be discovered on the network.  any inputs or suggestions?

---

### Post by FiveSidedPoly on 2010-03-16
If you server is not being recognized by Windows then there is possibly several other things that are the issues, not just your Samba config.
 
What resource did you use/follow to configure the server during install?
 
If you haven't at least browsed over the official documentation, here is it.
 
[Official Ubuntu 8.10 Server Documentation]("https://help.ubuntu.com/8.10/serverguide/C/index.html")
 
 
As for Samba, start with this guide.
 
[Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")
 
 
Then if your issues are Windows 7 related, this guide should be of some use.
 
[Howto: Fix Windows share browsing issues]("http://ubuntuforums.org/showthread.php?t=1169149")
 
 
I suggest configuring your server with a static IP as well, it will help with trouble shooting the cause.
 
If you get stuck on something specific you can post about it, but there is a lot of resources on these forums, just give a good search first.  :)

---

