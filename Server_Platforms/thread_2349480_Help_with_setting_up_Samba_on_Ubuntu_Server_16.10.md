---
title: "Help with setting up Samba on Ubuntu Server 16.10"
date: 2017-01-15
forum: Server Platforms
---

### Post by Jamie_Edwards on 2017-01-15
Hi guys,

So I've tried for the last couple of days to set up a samba file share server. I've scoured the internet for various tutorials on how to do this and they are all extremely similar. I'm wanting to connect to said server with a windows machine, macOS Sierra machine and an Ubuntu machine.

However, when I think I've set it up, and try to connect to said server I don't get any credentials box or anything.

From the Mac (as this is the thing I have in front of me right now) it comes up with the following error:

```

There was a problem connecting to the server "jamiefileserver".

The server may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.

```

Now, I know it's not an issue with the IP as I've set this to be static and it works (this used to be a minecraft server). It can't be my network connection as I can both see "jamiefileserver" on my Mac, Windows and Ubuntu machines and I'm currently typing this on the webpage through the Mac. I'm also able to ssh into the server through all the machines too.

I have set my user up so that I should be able to log in.

my smb.conf for the shares is as follows:

```

[MacShare]
path = /home/jamie/samba/macOS
comment = Share for macOS
valid users = jamie
write list = jamie
read only = no
available = yes
browsable = yes
writeable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

```

Any ideas on what might be happening and how I could get it up and running?

Thanks guys!

Jamie

---

### Post by Morbius1 on 2017-01-15
> I know it's not an issue with the IP as I've set this to be static
And you cannot access the server with that ip address?

Finder > Connect to Server > smb://192.168.0.100

macOS, Linux , and windows 10 ( and only Windows 10 ) share something in common and that's mDNS ( Bonjour in macOS - Avahi in Linux ) so you should be able to access it by name with a .local attached at the end of it as well:

macOS: smb://jamiefileserver.local
Win10: \\jamiefileserver.local

---

### Post by Jamie_Edwards on 2017-01-15
None of that works on the Mac. 

It constantly says that it doesn't exist. I did change the sambas netbios name and it registered that.

---

### Post by Jamie_Edwards on 2017-01-15
So after a little tinkering and setting up a samba server on a raspberry pi, I figured out that it's actually the firewall on the server that's giving me issues.

I think I don't have the right port open

---

### Post by Morbius1 on 2017-01-15
I don't use a firewall in my home lan but ufw has a "samba" entry that tells you what ports it uses:
> tester@vub1610:~$ cat /etc/ufw/applications.d/samba
[Samba]
title=LanManager-like file and printer server for Unix
description=The Samba software suite is a collection of programs that implements the SMB/CIFS protocol for unix systems, allowing you to serve files and printers to Windows, NT, OS/2 and DOS clients. This protocol is sometimes also referred to as the LanManager or NetBIOS protocol.
[COLOR=#0000cd]ports=137,138/udp|139,445/tcp[/COLOR]
And in addition Bonjour / Avahi / mDNS itself uses 5353 should you want to go that way.

But the most efficient and reliable way to connect two machines is by ip address, then mDNS, and then by netbios name.

[COLOR=#0000cd]*Note: mDNS doesn't use netbios it uses host names.*[/COLOR]

---

