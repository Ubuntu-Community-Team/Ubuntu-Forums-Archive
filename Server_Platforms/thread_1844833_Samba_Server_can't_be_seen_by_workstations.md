---
title: "Samba Server can't be seen by workstations"
date: 2011-09-15
forum: Server Platforms
---

### Post by ml_nelson on 2011-09-15
I've had a small network running for years. It looked like this:
 
1.) D-Link VPN 8 Port Router
2.) Multiple Windows XP workstations
3.) An Old Ubuntu box running 6.X (?) & Samba & used only as a server
4.) A New Ubuntu Server running 9.04 & Samba & " " " " " " 
 
The D-Link router crapped out, so I replaced it with a LinkSys router. After minimal fooling around the router, the network was up but with one problem... 
 
the XP Workstations can't see the New Ubuntu box, only the Old Ubuntu. ??? WTF ???
 
If I test out the connectivity of the New Ubuntu box, it appears to connect to the Internet, it can view the setup page of the router. In general it seems connected to the network even though no XP Workstation can see it.
 
What is going on? What configuration in Ubuntu would allow the New Ubuntu to be seen via one router, but not via another? Any setting of a Router that explains this?
 
Mike
 
p.s. The New Ubuntu was set up as a file server using the scheme shown in this video:
[http://www.youtube.com/watch?v=89hjWOb8qmY&annotation_id=annotation_888326&feature=iv](http://www.youtube.com/watch?v=89hjWOb8qmY&annotation_id=annotation_888326&feature=iv)

---

### Post by arrrghhh on 2011-09-15
I assume the new Ubuntu box worked fine on the old D-Link router...?

That certainly is an odd thing to happen.  Since they are all on the same router, I also have to assume all the devices are on the same subnet and there's no VLAN's in use - correct me if I'm wrong.  If you don't know what that is, and they are all connected to the same router, don't worry about it :p.

Can the new Ubuntu box ping the XP machines?  How about in the other direction?  If you have nmap, that might be useful as well...  Nmap will allow you to probe the Ubuntu machine from one of the XP machines, so you can see which ports are open to the XP machines.

Also, do you use UFW or any sort of a firewall on the new Ubuntu machine?

Silly question, but have you ensured samba is running properly on the new Ubuntu box? ;)

---

### Post by capscrew on 2011-09-16
> **ml_nelson said:**
> ...
 
If I test out the connectivity of the New Ubuntu box, it appears to connect to the Internet, it can view the setup page of the router. In general it seems connected to the network even though no XP Workstation can see it.
 
What is going on? What configuration in Ubuntu would allow the New Ubuntu to be seen via one router, but not via another? Any setting of a Router that explains this?


The device you replaced is more than just a router.  It *[COLOR="DarkGreen"]**may be able to**[/COLOR]* provide LAN side DNS and DHCP services and it is a layer 2 switch.  Some of these home network *edge devices *do not provide DNS sevices for the LAN and some don't.  It is certainly possible to run LAN side Samba with just a simple switch connecting all the hosts.

The condition you have is most likely due to the loss of LAN side DNS services that the original router provided and the new device doesn't or is not setup to provide it at this time.

To test this out you can try any mount the share by IP address.  From a Windows host see if you can connect to the share using an IP address via the terminal (Start>>Run>>CMD) with this```
net use x: \\IP_address_of_Ubuntu_9.04\share_name
```

If this works (and I'm sure it will) it will confirm that the only thing that has changed is you have lost LAN side DNS services.  This can be set up individually on each host.  That is why one Ubuntu/Samba setup is working and the other isn't.

In reality what you are missing is the ability to browse that network: sharing should still be working.

Once we confirm that the above is true we can decide how to restore network browsing. > 
 
p.s. The New Ubuntu was set up as a file server using the scheme shown in this video:
[http://www.youtube.com/watch?v=89hjWOb8qmY&annotation_id=annotation_888326&feature=iv](http://www.youtube.com/watch?v=89hjWOb8qmY&annotation_id=annotation_888326&feature=iv)

This is a terrible howto.  It really doesn't explain enough and in some cases it is flat out wrong.

---

### Post by ml_nelson on 2011-09-18
OK.... Here is the results..... I can't duplicate the problem!  It works just fine now.
 
I've had the New Server turned off for the past weeks waiting for ideas & resolution. When I turned it on, all the XP Workstations see it just fine.
 
I'm confused and I hate problems like this!  I'm left with the uneasy feeling that this issue will be back.
 
Mike

---

### Post by volkswagner on 2011-09-18
It is likely a DNS issue.  For access to LAN machines using hostname, you either need a local DNS server, or mapped ip addresses to hostnames in your /etc/hosts file.

If this happens again, try to connect with the ip address to confirm this is the issue.

You can allow your router to act as a local DNS server by making your static ip machines get a reserved DHCP address. Then add the routers address to the DNS list or Local DNS in the router config.  This will make the router "aware" of hostname rather than having static ip setup in /etc/network/interfaces.

With this setup you will need to restart workstations  or networking service if your router gets rebooted.

---

### Post by capscrew on 2011-09-18
> **ml_nelson said:**
> OK.... Here is the results..... I can't duplicate the problem!  It works just fine now.
 
I've had the New Server turned off for the past weeks waiting for ideas & resolution. When I turned it on, all the XP Workstations see it just fine.
 
I'm confused and I hate problems like this!  I'm left with the uneasy feeling that this issue will be back.
 
Mike

Hi Mike,

There are a couple of things you can regularly check to see how everything is working.  The first is to check that you have **both **the smbd and nmbd daemons running.  The simplest way is from the terminal with this command```
pgrep -l mbd
```

This will show something like this (at least 2 smbd and 1 nmbd processes) ```
[COLOR="DarkGreen"]**pgrep -l mbd**[/COLOR]
926 smbd
1066 smbd
1698 nmbd

```

If you don't have the nmbd daemon running it will look like this```
pgrep -l mbd
926 smbd
1066 smbd

```

You will have the same symptoms as you describe when the nmbd daemon is not running.  To start the daemon I believe your Ubuntu version uses this command```
sudo service nmbd start
```

Another thing you can check is whether you can browse using samba itself.  To do that from the terminal you can use this command ```
smbtree
```

You shoild get something like this back```
BEACHES
	\\MALIBU         		malibu
		\\MALIBU\Capscrew          	Home Directories
		\\MALIBU\IPC$           	IPC Service (malibu)
		\\MALIBU\Backup         	Backup Data Share
		\\MALIBU\ISO            	Ubuntu ISO's
		\\MALIBU\Public         	Public Share

```

This is browsing only the Ubuntu host that has Samba running on it.  I have everything else turned off at the moment, but it will list every host that it can log into with your password.  It will show errors on those that it cant but did attempt to login to.

---

### Post by ml_nelson on 2011-09-19
> **capscrew said:**
> Hi Mike,
 
There are a couple of things you can regularly check to see how everything is working. The first is to check that you have **both **the smbd and nmbd daemons running. The simplest way is from the terminal with this command```
pgrep -l mbd
```
 
This will show something like this (at least 2 smbd and 1 nmbd processes) ```
[COLOR=darkgreen]**pgrep -l mbd**[/COLOR]
926 smbd
1066 smbd
1698 nmbd

```
 
**[COLOR=#8b0000]It shows 1 instance of nmbd and 4 of smbd, OK[/COLOR]**
 
You shoild get something like this back```
BEACHES
    \\MALIBU                 malibu
        \\MALIBU\Capscrew              Home Directories
        \\MALIBU\IPC$               IPC Service (malibu)
        \\MALIBU\Backup             Backup Data Share
        \\MALIBU\ISO                Ubuntu ISO's
        \\MALIBU\Public             Public Share

```
 
This is browsing only the Ubuntu host that has Samba running on it. I have everything else turned off at the moment, but it will list every host that it can log into with your password. It will show errors on those that it cant but did attempt to login to.
 
[COLOR=darkred]**So Ii do get something like that for for the New Server. I also get of pile of other workstations on the network & those it shows that it fails to log into anything, but it tried everything on the network. OK**[/COLOR]

---

### Post by capscrew on 2011-09-19
> **ml_nelson said:**
> [COLOR=darkred][B]So Ii do get something like that for for the New Server. 

I also get of pile of other workstations on the network & those it shows that it fails to log into anything, but it tried everything on the network. OK[/B][/COLOR]

If you can post that we will try and solve the problems.  ;-)

Add debug to the command, save it to a file and post it here.  Try this ```
smbtree -d3 > treetest
```

This will create a text file in your home directory named treetest.

---

