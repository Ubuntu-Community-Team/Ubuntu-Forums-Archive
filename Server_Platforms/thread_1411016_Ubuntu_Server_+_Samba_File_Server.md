---
title: "Ubuntu Server + Samba File Server"
date: 2010-02-19
forum: Server Platforms
---

### Post by endlessracingz on 2010-02-19
**Background**
I am very new to Ubuntu, or Linux for that matter.

I like most people have mostly used Windows but for the last 5 years have been in love with my mac and am trying my hand at Linux.

I have an old desktop PC that I wanted to convert to a home server. As of now my main goals are:

[LIST]
[*]File Server (share files across LAN)
[*]Print server (anyone on LAN to print to printer)
[*]Auto Backup Computers (Backup specific computers on the LAN)
[*]Media Server (access the media on the server from PS3)
[/LIST]
**Issues**
I have been searching the internet and come across most of the howto's to my list above but integrating them all is what is confusing me. They explain how to do something but not all of them go into detail about what their steps are actually doing or what the theory behind the steps are. I have no server experience at all other than using already setup ones at work or the like.

If everyone on the LAN has their own computer I want them to be able to have their own /home that only they can write too but everyone else can read too. I know how to add users to ubuntu but how do I get that user and their home to appear on a computer for either a Mac or Windows and only for that specific user?

From what I have read to do the file server and print server what I want is Samba. I have read a few Samba howto's but again I am confused as how it should integrate into Ubuntu Server. Samba seems to have its own usernames and passwords. If I already have usernames and passwords for the individuals in the ubuntu server, from what I have read they can be the same. How do I do this? Is this what I want to do/the way its meant to be done?

I also want there to be an open "share" directory for computers that are allowed access to the LAN to access but they do not have an ubuntu server or samba server username and password.

Please advise  ](*,)

---

### Post by mcarrara on 2010-02-19
I know Samba can do the first two points, I am doing that for about 400 users and 9 printers.  A sub-project on Samba is rsync which can be used for backup.

I had extensive Windows networking before I saw the light, so the change was not too daunting.  But if you do not have a strong understanding of Windows networking it will be hard to integrate Linux and Windows with Samba.  I learned a lot from books, web sites and hours of trial and error.

Mark

---

### Post by bab1 on 2010-02-19
> **endlessracingz said:**
> 

I have an old desktop PC that I wanted to convert to a home server. As of now my main goals are:

[LIST]
[*]File Server (share files across LAN)
[*]Print server (anyone on LAN to print to printer)
[*]Auto Backup Computers (Backup specific computers on the LAN)
[*]Media Server (access the media on the server from PS3)
[/LIST]
...Please advise  ](*,)

The best guide I have seen is [**_Samba by Example_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  It takes you from very basic to complex installation in steps.  I believe it is Red Hat centric but the examples will all work on Ubuntu.

After that I would read the official [**_Samba Guide _**]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/").

These can be a bit dry but they are accurate and leave nothing out.

---

### Post by endlessracingz on 2010-02-19
> **bab1 said:**
> The best guide I have seen is [**_Samba by Example_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  It takes you from very basic to complex installation in steps.  I believe it is Red Hat centric but the examples will all work on Ubuntu.

After that I would read the official [**_Samba Guide _**]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/").

These can be a bit dry but they are accurate and leave nothing out.

I have slowly been working through the Samba Guide you listed, but haven't gotten to what I need. I'm looking into the Samba by Example. It seems way more complex than anything I would need for Home Server setup, but hopefully I can take tidbits of info from the examples and get what I want.

I was hoping there was something more concise and specific to what I'm looking for. There will never be anywhere near 20 users on my home network, so the examples seem like overkill.

I am surprised there hasn't be a detailed howto written on what I need from a complete beginners stand point. Home Servers and networks seem to be on a rapid growth.

If anyone has anything more specific to my needs please post it! :KS

---

### Post by bab1 on 2010-02-19
> **endlessracingz said:**
> I have slowly been working through the Samba Guide you listed, but haven't gotten to what I need. I'm looking into the Samba by Example. It seems way more complex than anything I would need for Home Server setup, but hopefully I can take tidbits of info from the examples and get what I want.

I listed Samba by Example first because it is more of a howto (with explanations.  There are plenty of howto's out there just use Google to find them.  Some are inaccurate, some are outdated.  The Samba Guide is the definitive documentation not a howto at all.> 

I was hoping there was something more concise and specific to what I'm looking for. There will never be anywhere near 20 users on my home network, so the examples seem like overkill.
[QUOTE]The amount of users is irrelevant.  The procedures are.  

I am surprised there hasn't be a detailed howto written on what I need from a complete beginners stand point. Home Servers and networks seem to be on a rapid growth.
[/QUOTE]Like I said there are plenty.  See [**_here_**]("http://www.google.com/search?hl=en&q=samba+server+howto&aq=f&aqi=g-c1&oq=").  > 

If anyone has anything more specific to my needs please post it! :KS

---

### Post by endlessracingz on 2010-02-19
> **bab1 said:**
> Like I said there are plenty.  See [**_here_**]("http://www.google.com/search?hl=en&q=samba+server+howto&aq=f&aqi=g-c1&oq=").

I have read through a lot of those already and I'm still not understanding everything completely. They simply state do this and then this but don't help me understand Samba much better. I am working through the Samba by Example right now. Hopefully something will "click".

---

### Post by joberly on 2010-02-19
I think you need to take a step back and read up on how Linux works in a more basic fashion before taking on a project like this. For someone as new as you, at least get down how file permissions work on a Unix system. You need to start from the ground up if you really want to understand how it works and be able to implement/change things.

Yes file sharing w/ Samba is fairly easy, but add in file permissions that aren't set correctly with a user that doesn't know the concept behind it, and it will be very frustrating for you.

Start there and work up to a basic file share. Then move up to setting permissions to shares based on users. Then define what you mean by remote /home locations. Are we talking network logins to the server with all data stored there? Or simply a place for each user to backup their stuff? One is much easier than the other. Good luck!

---

### Post by endlessracingz on 2010-02-19
> **joberly said:**
> I think you need to take a step back and read up on how Linux works in a more basic fashion before taking on a project like this. For someone as new as you, at least get down how file permissions work on a Unix system. You need to start from the ground up if you really want to understand how it works and be able to implement/change things.

Yes file sharing w/ Samba is fairly easy, but add in file permissions that aren't set correctly with a user that doesn't know the concept behind it, and it will be very frustrating for you.

Start there and work up to a basic file share. Then move up to setting permissions to shares based on users. Then define what you mean by remote /home locations. Are we talking network logins to the server with all data stored there? Or simply a place for each user to backup their stuff? One is much easier than the other. Good luck!

I read all of the Ubuntu Pocket Guide by Keir Thomas so I have a basic understanding on how Linux/Ubuntu work including file permissions.

As far as the remote /home directories I planned on having them all be a maximum storage size for each user, not sure how to do this, but its simply "a place for each user to backup their stuff". I did want them easy to navigate to by having them "mounted" (not sure if this is the right term) as a drive on the windows and mac machines alike when they are connected to the LAN. I eventually want some web based GUI to access the server remotely from anywhere via the internet so each user can access their own /home directories. So for example if they were using a computer in say a library, one where they cannot add software or anything, they could still access their /home directories.

I know I am shooting for the :KS stars :KS with my goals but these are long term. I am right now just trying to slowly work on them and learn in the process.

---

### Post by endlessracingz on 2010-02-20
So to bump this back up and hopefully to get some help...

I am working through the Samba Guide using the very first example.

My smb.conf is very simple and looks like this:

```
[global]
        workgroup = HOME
        security = SHARE

[share]
        comment = Shared Data
        path = /home/share
        read only = No
        guest ok = Yes
```

I follow the example and validate the new samba configuration.

```
$ smbclient -L localhost -U%
Domain=[HOME] OS=[Unix] Server=[Samba 3.4.0]

    Sharename       Type      Comment
    ---------       ----      -------
    share           Disk      Shared Data
    IPC$            IPC       IPC Service (Samba 3.4.0)
Domain=[HOME] OS=[Unix] Server=[Samba 3.4.0]

    Server               Comment
    ---------            -------
    UBUNTU               Samba 3.4.0

    Workgroup            Master
    ---------            -------
    HOME                 UBUNTU

```

Everything seems fine so far but when I try and verify samba handling a username and password and having it answer its own name I get the following:

```
$ smbclient -L ubuntu -Uroot%password
Domain=[HOME] OS=[Unix] Server=[Samba 3.4.0]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

```

So it seems something is wrong. If everything worked correctly I have read I am suppose to get the same output as above... :confused:

help please

---

### Post by joberly on 2010-02-20
Typically user share access is used, instead of the security = share.

Try using security = user and supply Samba with a valid username and password. (Only required if you actually have the specific share requiring certain user(s), which you're current configuration is not setup for.)

Also use the 'testparm' utility to test the Samba configuration, as well as the command 'smbtree' to show your current shares.

---

### Post by endlessracingz on 2010-02-20
> **joberly said:**
> Typically user share access is used, instead of the security = share.

Try using security = user and supply Samba with a valid username and password. (Only required if you actually have the specific share requiring certain user(s), which you're current configuration is not setup for.)

Also use the 'testparm' utility to test the Samba configuration, as well as the command 'smbtree' to show your current shares.


Changing the security = user did help. By valid username and password those would be the samba added username and passwords and not the ubuntu ones correct?

I currently use ```
testparm -s smb.conf.master > smb.conf
``` to test the samba configuration as was suggested via the Samba Guides and howto's out there.

Although I have that working now on a Mac OSX computer when I go to Connect to server and attempt to connect to smb://ubuntu it gives me a connection failed error. With this small amount of configuration shouldn't I at least be able to see the share directory on my Mac?

I also when restarting samba and reloading the smb.conf have this issue
```
$ /etc/init.d/samba reload
 * Reloading /etc/samba/smb.conf smbd only
start-stop-daemon: warning: failed to kill 1534: Operation not permitted
1 pids were not killed
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.

```

What pid? are they talking about? this seems like an issue that I should be fixed although it may not be hurting anything, but I have no idea.

---

### Post by joberly on 2010-02-20
First off, to restart system services you need to do it as root (use sudo). That is why it cannot kill the samba process, you don't have sufficient permissions.

As far as the usernames and passwords, they can be valid system users, or users setup in the samba password file. You utilize this based on the valid users flag in your specific share.

Example,

valid user = jsmith

You can allow multiple users,

valid user = jsmith, jdoe, ataylor

These directives will go within each specific share declaration in your smb.conf.

I am not too familiar with Macs and how they implement CIFS/SMB, so I unfortunately cannot help with Mac clients. Do you have a Windows client or another Linux client that you can test with?


EDIT: I am also not sure why you are using those paramiters with testparm. You can simply issue 'testparm' and it will test the correct /etc/samba/smb.conf that you should be using. Unless you specifically instructed Samba to use a file called smb.conf.master.

---

### Post by endlessracingz on 2010-02-20
> **joberly said:**
> First off, to restart system services you need to do it as root (use sudo). That is why it cannot kill the samba process, you don't have sufficient permissions.

Oops :redface: a little embarrassing

> As far as the usernames and passwords, they can be valid system users, or users setup in the samba password file. You utilize this based on the valid users flag in your specific share.

Example,

valid user = jsmith

You can allow multiple users,

valid user = jsmith, jdoe, ataylor

These directives will go within each specific share declaration in your smb.conf.If the directories filer permissions is read and writable to a group, say administrators, would i still have to specify the individual user names as you stated above. Then again I guess that thinking is flawed since the groups are associated with ubuntu and not the samba usernames or can they? Previously you did say the could be system or samba users. If that is so why have I read that you have to create a samba user in order for samba to work, or in order to use the system info for samba is there something in the smb.conf file I need to set in the global area?

> I am not too familiar with Macs and how they implement CIFS/SMB, so I unfortunately cannot help with Mac clients. Do you have a Windows client or another Linux client that you can test with?Unfortunately I do not at the moment, but I have followed howto's online and i can't seem to find the /share directory that I'm trying to share through samba.

---

### Post by joberly on 2010-02-20
You can pass groups to Samba in a similar fashion:

valid user = @group

Does the Mac have a "network neighborhood" style structure where you can simply browse local networked computers? Also, making sure the Mac is on the same workgroup as defined in your smb.conf.

Try using smb://hostname/share and also smb://ip_address/share

---

### Post by pirateghost on 2010-02-20
> **endlessracingz said:**
> 
Although I have that working now on a Mac OSX computer when I go to Connect to server and attempt to connect to smb://ubuntu it gives me a connection failed error. With this small amount of configuration shouldn't I at least be able to see the share directory on my Mac?



to hit on this, it is a problem with DNS resolution.  try to connect smb://ipaddress

unless you have something in your network acting as a dns server (some routers will do this) your mac has no idea that ubuntu exists on the network, as it has no way of resolving the name to an ip address

---

### Post by bab1 on 2010-02-20
> **endlessracingz said:**
> ...Then again I guess that thinking is flawed since the groups are associated with ubuntu and not the samba usernames or can they? Previously you did say the could be system or samba users. ...
I believe you have to have a valid Ubuntu user first. Then you add to the smbpasswd account.  The groups are the Ubuntu groups.

See [**_here_**]("http://optics.ph.unimelb.edu.au/help/samba/smbpasswd.5.html").

---

### Post by bab1 on 2010-02-20
> **pirateghost said:**
> to hit on this, it is a problem with DNS resolution.  try to connect smb://ipaddress

unless you have something in your network acting as a dns server (some routers will do this) your mac has no idea that ubuntu exists on the network, as it has no way of resolving the name to an ip address

Maybe...

It would depend upon what the "*connection failed error*" was.

---

### Post by endlessracingz on 2010-02-21
> **pirateghost]to hit on this, it is a problem with DNS resolution.  try to connect smb://ipaddress

unless you have something in your network acting as a dns server (some routers will do this) your mac has no idea that ubuntu exists on the network, as it has no way of resolving the name to an ip address[/QUOTE]

I have tried smb://ipaddress and i have the same error/issue. My router might possibly be acting as a DNS server but I'm not sure at the moment. Even if it is shouldn't I have no problem connecting using the smb://ipaddress method?

[QUOTE=bab1 said:**
> I believe you have to have a valid Ubuntu user first. Then you add to the smbpasswd account.  The groups are the Ubuntu groups.

See [**_here_**]("http://optics.ph.unimelb.edu.au/help/samba/smbpasswd.5.html").

I have already added several smbpasswd accounst. I came across the ```
 pdbedit -w -L
``` command to list out the samba users so I know I have added them.

[QUOTE=bab1][QUOTE=pirateghost]to hit on this it is a problem with the DNS resolution. try to connect smb://ipaddress

unless you have something on your network acting as a dns server (some routers will do this) you mac has no idea that ubuntu exists on the network, as it has no way of resolving a name to an ip address[/QUOTE]

Maybe...

It would depend upon what the "*connection failed error*" was.     
[/QUOTE]

The error my Mac gives me is:

Connection failed

The server &#8220;192.168.1.190&#8221; may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.

---

### Post by bab1 on 2010-02-21
> **endlessracingz said:**
> I have tried smb://ipaddress and i have the same error/issue. My router might possibly be acting as a DNS server but I'm not sure at the moment. Even if it is shouldn't I have no problem connecting using the smb://ipaddress method?
You should have solid network infrastructure in place. 

I would suggest that you have a network numbering scheme in mind and a hostname for each of you devices.  All of my hosts except the laptops use a static IP address (manually configured).  The laptops get their addresses from a DHCP server incorporated into the router.     

You also absolutely must have some sort of nameservice for the LAN.  I use DNS for this.  As you are using MAC clients that have no idea what NetBIOS is, you must also use DNS.

For me this means:
```
192.168.1.0 /24 network 
192.168.1.1 -- gw1 (Router/DNS/DHCP) 
192.168.1.10 -- wilshire
192.168.1.12 -- melrose (Samba Server)
192.168.1.150 -- vermont (Latptop)
192.168.1.152 -- western (Laptop)
192.168.1.200 -- printer (HP 2200)
192.168.1.245 -- ap1 (Linksys Access Point)
```

This gives me IP addresses that are consistent and hostnames that are memorable.  In this case we have Los Angeles placenames (gw stands for gateway). > 

I have already added at least one smbpasswd account. I have looked for a way to look at what accounts I have already added but still haven't found a way to do that yet. I came across the ```
 pdbedit -w -L


``` command to list out the samba users but get the following error:
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/passdb.tdb!
Segmentation fault
This indicates a problem with the file [FONT="Courier New"]/var/lib/samba/passdb.tdb[/FONT].  Does the file exist? What is in the directory [FONT="Courier New"]/var/lib/samba[/FONT]?> 

The [connection] error my Mac gives me is:

Connection failed

The server &#8220;192.168.1.190&#8221; may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.

Can you ping this address?

---

### Post by endlessracingz on 2010-02-21
> **bab1 said:**
> You should have solid network infrastructure in place. 

I would suggest that you have a network numbering scheme in mind and a hostname for each of you devices.  All of my hosts except the laptops use a static IP address (manually configured).  The laptops get their addresses from a DHCP server incorporated into the router.     

You also absolutely must have some sort of nameservice for the LAN.  I use DNS for this.  As you are using MAC clients that have no idea what NetBIOS is, you must also use DNS.

For me this means:
```
192.168.1.0 /24 network 
192.168.1.1 -- gw1 (Router/DNS/DHCP) 
192.168.1.10 -- wilshire
192.168.1.12 -- melrose (Samba Server)
192.168.1.150 -- vermont (Latptop)
192.168.1.152 -- western (Laptop)
192.168.1.200 -- printer (HP 2200)
192.168.1.245 -- ap1 (Linksys Access Point)
```This gives me IP addresses that are consistent and hostnames that are memorable.  In this case we have Los Angeles placenames (gw stands for gateway).

Currently I have a similar arrangement or at least I believe I do. 
The network range is 192.168.1.2/254 
Router as 192.168.1.1
Then I have several devices with static IP's such as the server which is 192.168.1.190
as well as a PS3 at 192.168.1.180
I have a few other items on the network with static IP's but they wont have anything to do with the server.

All other laptops and computers are dynamic and assigned ip's from the routers dhcp.

I believe i know what DNS is but no idea how to implement it on my home network. This may be my issue. I'll do some searching into that matter, but please if you can as easily help me out with it, I would very much appreciate it.

> Can you ping this address?

Yes I can I receive the following output ```
PING 192.168.1.190 (192.168.1.190): 56 data bytes
64 bytes from 192.168.1.190: icmp_seq=0 ttl=64 time=2.021 ms
64 bytes from 192.168.1.190: icmp_seq=1 ttl=64 time=4.416 ms
64 bytes from 192.168.1.190: icmp_seq=2 ttl=64 time=1.806 ms
64 bytes from 192.168.1.190: icmp_seq=3 ttl=64 time=0.734 ms
64 bytes from 192.168.1.190: icmp_seq=4 ttl=64 time=1.554 ms
64 bytes from 192.168.1.190: icmp_seq=5 ttl=64 time=3.746 ms
64 bytes from 192.168.1.190: icmp_seq=6 ttl=64 time=2.911 ms
64 bytes from 192.168.1.190: icmp_seq=7 ttl=64 time=1.088 ms
64 bytes from 192.168.1.190: icmp_seq=8 ttl=64 time=2.583 ms
64 bytes from 192.168.1.190: icmp_seq=9 ttl=64 time=2.014 ms

--- 192.168.1.190 ping statistics ---
10 packets transmitted, 10 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.734/2.287/4.416/1.091 ms

```

but I still cannot connect to the shared directories on the server. Perhaps this is the DNS issue you stated above...

---

### Post by bab1 on 2010-02-21
```

```> **endlessracingz said:**
> ...
I believe i know what DNS is but no idea how to implement it on my home network. This may be my issue. I'll do some searching into that matter, but please if you can as easily help me out with it, I would very much appreciate it.

DNS (Domain Name Services) is a method to map IP addresses to hostnames of devices.  What brand and model is your router?> 

Yes I can I receive the following output 
```
PING 192.168.1.190 (192.168.1.190): 56 data bytes
64 bytes from 192.168.1.190: icmp_seq=0 ttl=64 time=2.021 ms
64 bytes from 192.168.1.190: icmp_seq=1 ttl=64 time=4.416 ms
64 bytes from 192.168.1.190: icmp_seq=2 ttl=64 time=1.806 ms
64 bytes from 192.168.1.190: icmp_seq=3 ttl=64 time=0.734 ms
64 bytes from 192.168.1.190: icmp_seq=4 ttl=64 time=1.554 ms
64 bytes from 192.168.1.190: icmp_seq=5 ttl=64 time=3.746 ms
64 bytes from 192.168.1.190: icmp_seq=6 ttl=64 time=2.911 ms
64 bytes from 192.168.1.190: icmp_seq=7 ttl=64 time=1.088 ms
64 bytes from 192.168.1.190: icmp_seq=8 ttl=64 time=2.583 ms
64 bytes from 192.168.1.190: icmp_seq=9 ttl=64 time=2.014 ms

--- 192.168.1.190 ping statistics ---
10 packets transmitted, 10 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.734/2.287/4.416/1.091 ms

```
This means you have connectivity at the basic IP level.  Try pinging the sever by hostname.  What do you get?

EDIT:  I just had a thought.  

Is this:```
onnection failed

The server &#8220;192.168.1.190&#8221; may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.
```from a web browser?

---

### Post by endlessracingz on 2010-02-21
> **bab1 said:**
> DNS (Domain Name Services) is a method to map IP addresses to hostnames of devices.  What brand and model is your router?

Its an ASUS.

> 
This means you have connectivity at the basic IP level.  Try pinging the sever by hostname.  What do you get? I get:```
 ping: cannot resolve ubuntu: Unknown host

```
> EDIT:  I just had a thought.  

Is this:```
connection failed

The server &#8220;192.168.1.190&#8221; may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.
```from a web browser?

No it is not. Using the Finder on the Mac OSX > Go > Connect to Server...
After entering the server address as ```
smb://192.168.1.190
```then that error occurs.

---

### Post by cariboo on 2010-02-21
You can't just enter the server ip address without specifying a share name eg:

```
smb://192.168.1.190/stuff
```

---

### Post by bab1 on 2010-02-21
> **endlessracingz said:**
> Its an ASUS.

Without knowing the specific model I can only guess.  It seems like ASUS ADSL routers do not have LAN side DNS resolution available.  :-(> 

 I get:```
 ping: cannot resolve ubuntu: Unknown host

```

So we need to provide DNS resolution ourselves.  The easiest way is to add the mapping in the [FONT="Courier New"]/etc/hosts[/FONT] files on **[COLOR="DarkSlateGray"]EVERY [/COLOR]**host that needs this service.  This requires a bit of thought.  Do you need DNS resolution on every machine.  Not really.  Only the ones that will refer to another host by name.  If you decide to use this method _[COLOR="Navy"]all mapped IP addresses[/COLOR]_ must be static.> 


No it is not. Using the Finder on the Mac OSX > Go > Connect to Server...
After entering the server address as ```
smb://192.168.1.190
```then that error occurs.

This must be equivalent to Gnome Nautilus.  The error is due to time out of the request.  I just tried this with a host that had NetBIOS over TCP (NBT) turned off.  I get a similar error.  

Lets try to connect to the Samba server via the command line.  I have to guess at the syntax but I believe something like [FONT="Courier New"]smbclient -L *[COLOR="Green"]ipaddress[/COLOR]*[/FONT] will work.

As you can see DNS is important.  Try this:  on the MAC host you are using as a client to the Samba server add the IP ADDRESS hostname mapping.  This is an example of that:```
92.168.1.10 wilshire   [COLOR="Red"]#<-this is an example use your own IP to name mapping[/COLOR]
```

---

### Post by endlessracingz on 2010-02-21
> **cariboo907 said:**
> You can't just enter the server ip address without specifying a share name eg:

```
smb://192.168.1.190/stuff
```

I have tried that. In my case the directory being shared is "share" so I have tried ```
smb://192.168.1.190/share
``` and still receive an error.

Also on all the howto's on that subject I have seen, you would first just do smb://ipaddress once if found the server it would have a dropped down of the directories that are being shared. You would select it then enter the necessary username and pass, but I have not been able to get that far.

---

### Post by bab1 on 2010-02-21
> **cariboo907 said:**
> You can't just enter the server ip address without specifying a share name eg:

```
smb://192.168.1.190/stuff
```

Be careful what you say.  It works with my setup.  In Nautilus I can use [FONT="Courier New"]smb://hostname[/FONT] and list all the shares for that host.  I do not use NetBIOS.  I do use LAN side DNS.  You can legitimately call the host without listing the resources in SMB/CIFS.

---

### Post by endlessracingz on 2010-02-22
> **bab1 said:**
> Without knowing the specific model I can only guess.  It seems like ASUS ADSL routers do not have LAN side DNS resolution available.  :-(

The model is WL500W

> So we need to provide DNS resolution ourselves.  The easiest way is to add the mapping in the [FONT=Courier New]/etc/hosts[/FONT] files on **[COLOR=DarkSlateGray]EVERY [/COLOR]**host that needs this service.  This requires a bit of thought.  Do you need DNS resolution on every machine.  Not really.  Only the ones that will refer to another host by name.  If you decide to use this method _[COLOR=Navy]all mapped IP addresses[/COLOR]_ must be static.

I am going to repeat what you said in my own words to make sure I understand you correctly. Essentially the easiest way to provide DNS resolution on Linux/Unix and Mac OS systems is to edit the [FONT=Courier New]/etc/hosts[/FONT] file on each system that needs to access the Samba server. There will be windows computers that I have to do this for too eventually and I am not sure  how I would do that at the moment. My samba server has a static IP so as you said I should be able to input the ipaddress and server name into the list to provide the DNS resolution. Please correct me if this is wrong.

But... won't that just allow me to connect via [FONT=Courier New]smb://ubuntu[/FONT] rather than [FONT=Courier New]smb://192.168.1.190[/FONT]? I still cannot even connect using the ipaddress.

> Lets try to connect to the Samba server via the command line.  I have to guess at the syntax but I believe something like [FONT=Courier New]smbclient -L *[COLOR=Green]ipaddress[/COLOR]*[/FONT] will work. 
So from my Mac Laptop I opened up a terminal and did the command you suggest ```
$ smbclient -L 192.168.1.190
timeout connecting to 192.168.1.190:445
timeout connecting to 192.168.1.190:139
Error connecting to 192.168.1.190 (Operation already in progress)
Connection to 192.168.1.190 failed (Error NT_STATUS_ACCESS_DENIED)

```
It seems the connection is timing out...

This seems weird to me since in fact I use the laptop's terminal and ssh to login to the server to do my configurations and the like.

> As you can see DNS is important.  Try this:  on the MAC host you are using as a client to the Samba server add the IP ADDRESS hostname mapping.  This is an example of that:```
192.168.1.10 wilshire   [COLOR=Red]#<-this is an example use your own IP to name mapping[/COLOR]
```

I am assuming your referring to the /etc/host. I have the following listed on that file on the ubuntu server which houses samba.
```
192.168.1.190    ubuntu    ubuntu
```

and pulling up that file on the Mac system I see
```
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1       localhost
255.255.255.255 broadcasthost
::1             localhost
fe80::1%lo0     localhost

```

I would guess the host mapping would be listed either at the bottom or preferably after the "broadcasthost" is this a correct assumption?

But I cannot see how this would fix the issue of connecting because I haven't been able to with just smb://192.169.1.190

---

### Post by bab1 on 2010-02-22
> **endlessracingz said:**
> ...
I am going to repeat what you said in my own words to make sure I understand you correctly. Essentially the easiest way to provide DNS resolution on Linux/Unix and Mac OS systems is to edit the [FONT=Courier New]/etc/hosts[/FONT] file on each system that needs to access the Samba server. There will be windows computers that I have to do this for too eventually and I am not sure  how I would do that at the moment. My samba server has a static IP so as you said I should be able to input the ipaddress and server name into the list to provide the DNS resolution. Please correct me if this is wrong.

The [FONT="Courier New"]/etc/hosts [/FONT]file also exists on Windows hosts.  It is located at```
C:\Windows\System32\drivers\etc\hosts
```
> 


But... won't that just allow me to connect via [FONT=Courier New]smb://ubuntu[/FONT] rather than [FONT=Courier New]smb://192.168.1.190[/FONT]? I still cannot even connect using the ipaddress.

You do have connectivity between the MAC client and the Samba server.  You can ping it.  
> 

So from my Mac Laptop I opened up a terminal and did the command you suggest ```
$ smbclient -L 192.168.1.190
timeout connecting to 192.168.1.190:445
timeout connecting to 192.168.1.190:139
Error connecting to 192.168.1.190 (Operation already in progress)
Connection to 192.168.1.190 failed (Error NT_STATUS_ACCESS_DENIED)

```
It seems the connection is timing out...

This seems weird to me since in fact I use the laptop's terminal and ssh to login to the server to do my configurations and the like.

I'll bet you have a firewall running and it blocks the TCP ports Samba uses. The number after the colon in the following is the TCP port```
timeout connecting to 192.168.1.190:[COLOR="Indigo"]445[/COLOR]
timeout connecting to 192.168.1.190:[COLOR="Indigo"]139[/COLOR]
```
> 

I am assuming your referring to the /etc/host. I have the following listed on that file on the ubuntu server which houses samba.
```
192.168.1.190    ubuntu    ubuntu
```

and pulling up that file on the Mac system I see
```
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1       localhost
255.255.255.255 broadcasthost
::1             localhost
fe80::1%lo0     localhost

```

I would guess the host mapping would be listed either at the bottom or preferably after the "broadcasthost" is this a correct assumption?

The order is not important.  The readability is strictly for humans.  The machine doesn't care about the order. The last 2 entries are for IPv6.  More important is that there are no extra spaces before or after each line.   
> 

But I cannot see how this would fix the issue of connecting because I haven't been able to with just smb://192.169.1.190

You are correct here.  Your thought is very logical.

---

### Post by endlessracingz on 2010-02-22
> **bab1 said:**
> 
I'll bet you have a firewall running and it blocks the TCP ports Samba uses.    

You are correct sir... I followed a howto on the UFW supplied with Ubuntu right after i installed it and you mentioning the firewall caused me too remember. I simply disabled it and was able to connect right to the server. Even without adding the host to my Mac I was able to connect via smb://ubuntu

DOH! ](*,)

Now I feel like I wasted your time... but I am thankful as now I understand not only my system better but several networking concepts.

Thanks!

Although I am not sure why I receive the following...
```
$ smbclient -L 192.168.1.190
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE

```

---

### Post by bab1 on 2010-02-22
> **endlessracingz said:**
> You are correct sir... I followed a howto on the UFW supplied with Ubuntu right after i installed it and you mentioning the firewall caused me too remember. I simply disabled it and was able to connect right to the server. Even without adding the host to my Mac I was able to connect via smb://ubuntu

DOH! ](*,)

Now I feel like I wasted your time... but I am thankful as now I understand not only my system better but several networking concepts.

Thanks!

Although I am not sure why I receive the following...
```
$ smbclient -L 192.168.1.190
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE

```

We now have Samba connectivity!  The error indicates the password is not correct or missing.

Here is some basic MAC/Samba setup information. [_[COLOR="Navy"]http://support.apple.com/kb/HT1812[/COLOR]_]("http://support.apple.com/kb/HT1812") and [_[COLOR="navy"]http://www.informit.com/library/content.aspx?b=Mac_OS_X_Unleashed&seqNum=232[/COLOR]_]("http://www.informit.com/library/content.aspx?b=Mac_OS_X_Unleashed&seqNum=232").

Let me know if you need more help.

**Edit:** Here is the MAC SMB/CIFS (Samba) client setup. [_[COLOR="Navy"]http://www.informit.com/library/content.aspx?b=Mac_OS_X_Unleashed&seqNum=233[/COLOR]_]("http://www.informit.com/library/content.aspx?b=Mac_OS_X_Unleashed&seqNum=233").

---

