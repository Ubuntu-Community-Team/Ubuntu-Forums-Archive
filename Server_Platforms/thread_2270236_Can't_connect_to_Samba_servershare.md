---
title: "Can't connect to Samba server/share"
date: 2015-03-21
forum: Server Platforms
---

### Post by brian54 on 2015-03-21
Hello!

I was finally able to get samba installed and working (somewhat :x ). I can see my ubuntu server on my network and ping it. However, when I go to connect to it (from my Windows computer), I get prompted for Windows Security credentials. I have tried EVERYTHING, at least I feel like I have. I decided to use the Samba GUI and made so many usernames to cover my self and no matter what I use it will come back with: The user name or password is incorrect. 

Here is the full smb.conf file:

```
#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
        workgroup = workgroup


# server string is the equivalent of the NT Description field
        server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
        dns proxy = no


#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0


# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes






#### Debugging/Accounting ####


# This tells Samba to use a separate log file for each machine
# that connects
        log file = /var/log/samba/log.%m


# Cap the size of the individual log files (in KiB).
        max log size = 1000


# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no


# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
        syslog = 0


# Do something sensible when Samba crashes: mail the admin a backtrace
        panic action = /usr/share/samba/panic-action %d




####### Authentication #######


# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
        server role = standalone server


# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;       passdb backend = tdbsam
        obey pam restrictions = yes


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
        unix password sync = yes


# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
        pam password change = yes


# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
        map to guest = bad user


########## Domains ###########


#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#


# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile


# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U


# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd


# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u


# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u


# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m


# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.


# Maximum number of usershare. 0 (default) means that usershare is disabled.
;       usershare max shares = 100


# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
        usershare allow guests = yes
        username map = /etc/samba/smbusers
        security = user
        encrypt passwords = no
;       guest ok = no
;       guest account = nobody


#======================= Share Definitions =======================


# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes


# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700


# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes






;   valid users = %S


# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


[printers]
        comment = All Printers
        browseable = no
        path = /var/spool/samba
        printable = yes
;       guest ok = no
;       read only = yes
        create mask = 0700


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
;       browseable = yes
;       read only = yes
;       guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin


[test]
        path = /samba/test
        writeable = yes
;       browseable = yes
        guest ok = yes


[sambatest]
        path = /home/sambatest
        writeable = yes
;       browseable = yes
        guest ok = yes

```





The server IP: 192.168.2.190 and when I go to my Windows PC and go to: \\192.168.2.190 or select from the network map, it will prompt for username/password. Again, I have used all of my users I have made (mixed and matched, etc) and all of them come back that the username/password is incorrect.....

My smbusers file only has a few usernames that I made:

```

nobody = Dudash
brian = Dudash
root = Brian



```

Any help is appreciated... :)

---

### Post by nerdtron on 2015-03-21
did you already added samba password for the users?

```
sudo smbpasswd -a brian
```

Also you can add the valid users for the brain share on the samba conf. something like this:
```

[data]
    comment = data
    path = /samba/data
    public = no
    force user = brian
    valid users = brian
    writable = yes
    browseable = yes[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]

```



Also make sure that the folder is owned by brian:
```
 chown -R brain.brian /samba/data 
```

Then restart the samba service
```
sudo service samba restart
```

---

### Post by Morbius1 on 2015-03-21
Go into /etc/samba/smb.conf, find this section, and change this:
> # Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
        usershare allow guests = yes
        username map = /etc/samba/smbusers
        security = user
        [COLOR=#0000cd]encrypt passwords = **no**[/COLOR]
;       guest ok = no
;       guest account = nobody
To this:
> # Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
        usershare allow guests = yes
        username map = /etc/samba/smbusers
        security = user
        [COLOR=#0000cd]encrypt passwords = **yes**[/COLOR]
;       guest ok = no
;       guest account = nobody
Then restart smbd:
```
sudo service smbd restart
```
You may have to wait a few minutes for things to settle down since a restart of samba makes the network hysterical .. momentarily.

Note: Even though your shares allow guest access this parameter still needs to be set to yes.

---

### Post by brian54 on 2015-03-21
Thanks for the quick response.

I did set the password before (but did it again to be safe) and I also followed the rest that you gave me. I still can't get authenticated into the server..... :(

Just in case this may help, in the Windows Security dialog it says: Enter your credentials to connect to: UBUNTU (which is what the server was named). But below the user name and password boxes it does say Domain: BRIANMAIN

Could this be causing some issues? I've tried different things in the user name box like UBUNTU\brian but nothing works. I still get the user name or password is incorrect. What is this looking for? I am so confused.

EDIT: Just realized there was a second post...Trying your suggestion now.

---

### Post by brian54 on 2015-03-21
THAT DID IT!!!!!! 

Thank you sooooo much!!!!! :)

EDIT:

I can see and get into the shares now but I can't add anything. I get a message that I don't have the proper permissions. Why would that be? I thought I set the share to allow guests and anyone to write to it?

---

### Post by brian54 on 2015-03-21
I was able to get it. I had to mess around with the directory/folder permissions and ownership. Thanks again to the both of you for you help!

---

### Post by brian54 on 2015-03-22
I am back again!

So my Samba server is still working for the most part. Yesterday when I made the changes that Morbius suggested everything was working. The whole network could reach the Samba server and add/remove files. Life was good. 

Now today I wanted to verify this was still the case but now for some reason my wireless clients can't access the Samba share. They can ping the server IP address but when the computers go to navigate the the shares it comes back with the generic error: Windows cannot access \\192.168.2.5\. Check the spelling of the name, etc...

Based on how my small network is laid out, my LAN clients are on 192.168.10.0/24 and can still reach the Samba shares and add/remove files (GREAT!).

My wireless clients are off of the Raspberry Pi and are on the 192.168.20.0/24 subnet. These clients for some reason can't access the Samba shares anymore (yesterday the could). Again, I can ping the Samba server IP but can't navigate the the actual shares.

Any ideas? I have been searching the web but I am stuck...

---

### Post by brian54 on 2015-03-22
Also just to add:

It's not Windows Firewall or the wireless that is causing it. I took the same laptop that connected into the 10.0/24 LAN and it works and then disconnected the cable and went wireless to my Pi (20.0/24) and it doesn't work. I went even a step further just to rule out the wireless drivers or something being the issue by taking the laptop and connecting it to my other wireless connection that is part of the ASUS router (my home router that is in the middle of my LAN Linux router and Pi wireless router) and I could access the Samba shares.

---

### Post by volkswagner on 2015-03-22
It would be very helpful to show a map of your network.

Can wireless clients ssh or telnet into the server?

---

### Post by brian54 on 2015-03-22
Sorry I forgot that the picture of my network map was in a different topic post. I attached it.

I haven't even tried to telnet or ssh into the server on any client up until this point. I just tried to telnet in with one of my LAN clients (I'll try a wireless client soon) and it said connection refused.

I updated the server so it's IP is reserved for 192.168.2.5

---

### Post by volkswagner on 2015-03-22
That picture type is very small and most difficult for me to read.

Basically you need to make sure you have routes from WiFi clients to your SAMBA server.
Check route command from wireless client to see if it has a route to your server.

---

### Post by brian54 on 2015-03-22
I made the image larger but it keeps defaulting to only 11.9kb in size when really the file is much bigger...not sure why, maybe there is a file size limit?

I do have routes to the samba server. On my windows client that is connected to the wireless Pi it has the 192.168.2.0 network when I do route print and so does the Pi.

I can ping the Samba server (192.168.2.5) from both my wireless clients and the Pi itself. But once I go to connect/add the share it fails with the error I mentioned above. 

Thanks for you help by the way!

---

### Post by volkswagner on 2015-03-23
Were you able to ssh into the server from pi connected wifi?
You should be able to establish a telnet connection to your samba server on port 139.

You should setup a simple share on a windows client on same subnet as SAMBA. Check to see
if your pi connected clients can connect. I suspect the issue is with the pi network config/firewall.

---

### Post by brian54 on 2015-03-23
I tried to ssh and telnet into the Samba server from both LAN clients and Wireless clients today and when I used telnet port 139 it just stays at the black screen and eventually times out. 

I did some more testing with a Windows share and its the same results. I can access the Windows share from any device except the ones connected the the Pi wireless. So it does seem to be something with the Pi itself. I just don't get what...It has the routes to the Samba server and I can ping the server.

I'm thinking it maybe something with iptables? I do iptables -L and there was nothing for all 3 chains (input, forward, and output). I decided to add some just to test:

INPUT:
iptables -I INPUT 1 -s 0.0.0.0/0 -j ACCEPT

FORWARD:
iptables -I FORWARD 1 -s 0.0.0.0/0 -j ACCEPT

OUTPUT:
iptables -I OUTPUT 1 -s 0.0.0.0/0 -j ACCEPT

Now with that entered above, that would essentially allow everything to come in and out of the Pi, right? This still didn't fix my issue...

---

### Post by volkswagner on 2015-03-23
Well you certainly should be able to telnet from lan if you can access shares.

What does your telnet command look like? Did you use ip?

You Server should be listening, to check run:

```
 netstat -an | grep 139
```

Here is my result:
```
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN 
```

Telnet into my SAMBA server:

```
srvadmin@trusty:~$ telnet 192.168.7.129 139
Trying 192.168.7.129...
Connected to 192.168.7.129.
Escape character is '^]'.
^]

telnet> close
Connection closed.
```

Why are you using the pi?  Why is the pi on a separate network?
Can you post output of print route?

Again I cant read the image of your network, perhaps you can add some notes/reference.

Can you post ifconfig on the pi?

---

### Post by brian54 on 2015-03-23
[http://i288.photobucket.com/albums/ll184/dudash2021/Topology1_zpsxx8pfghi.png](http://i288.photobucket.com/albums/ll184/dudash2021/Topology1_zpsxx8pfghi.png)   

Hopefully this picture will work. Decided to use photo bucket. If you go to the link and click the image you should be able to blow it up a bit.

I still can't telnet in from any client (LAN or Wireless)..it just times out.

I did netstat -an | grep 139 and I got the same exact output, so it is listening. 

The reason why I am using the Pi and also why it is on a separate network is because it is for my school project. I focus on Cisco networking but I wanted to expand and go with Linux so I could learn and expand my knowledge, which I have. I learned a lot and actually want to keep going! So I am trying to "simulate" a mini-network that is based on linux equipment. I took an old computer and turned it into the IPCop router (which is fully functional). Then I bought the Pi to turn into a Wireless router (which is like 85% done) It would be 100% if I could get clients connected to be able to reach the Samba shares. I hope I explained this well enough.

As for the outputs:

Route print on the laptop connected to the Pi:

```
IPv4 Route Table
===========================================================================
Active Routes:
Network      Destination       Netmask       Gateway              Interface          Metric
                     0.0.0.0         0.0.0.0           192.168.20.1    192.168.20.96         25
                     127.0.0.0      255.0.0.0         On-link             127.0.0.1            306
                     127.0.0.1      255.255.255.255 On-link           127.0.0.1            306
                    127.255.255.255 255.255.255.255 On-link        127.0.0.1            306
                 192.168.2.0    255.255.255.0    192.168.20.1      192.168.20.96        26
                 192.168.20.0    255.255.255.0      On-link          192.168.20.96       281
                 192.168.20.96   255.255.255.255 On-link            192.168.20.96      281
                 192.168.20.255 255.255.255.255   On-link          192.168.20.96       281
224.0.0.0 240.0.0.0 On-link 127.0.0.1 306
224.0.0.0 240.0.0.0 On-link 192.168.20.96 281
255.255.255.255 255.255.255.255 On-link 127.0.0.1 306
255.255.255.255 255.255.255.255 On-link 192.168.20.96 281
===========================================================================
```


Route command on the Pi:

```
root@Pi-AP1:~# routeKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     192.168.2.1     255.255.255.0   UG    0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.10.0    192.168.2.1     255.255.255.0   UG    0      0        0 eth0
192.168.20.0    *               255.255.255.0   U     0      0        0 wlan0
```



ifconfig on the Pi:

```
root@Pi-AP1:~# ifconfigeth0      Link encap:Ethernet  HWaddr b8:27:eb:6c:99:47
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:42209182 (40.2 MiB)  TX bytes:9900810 (9.4 MiB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr 00:13:ef:80:21:87
          inet addr:192.168.20.1  Bcast:192.168.20.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:267248 errors:0 dropped:3345 overruns:0 frame:0
          TX packets:54673 errors:0 dropped:125 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12734771 (12.1 MiB)  TX bytes:44615149 (42.5 MiB)



```


Iptables -L:

```
root@Pi-AP1:~# iptables -LChain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere



```


Sorry for any stupid mistakes..I'm learning on the go.

---

### Post by volkswagner on 2015-03-23
You didn't post the telnet command.

Have you seen [this]("http://www.tldp.org/HOWTO/SMB-HOWTO-12.html") or [this]("http://www.oreilly.com/openbook/samba/book/ch04_06.html")?

What does the routing table look like for the Asus? 

You will learn a lot if you fire up a wireshark and/or tcpdump during testing.

You should start with ssh. You should be able to ssh from pi to smb server and it's host. You should be able to ssh from wireless client
to both smb server and it's host.

What are you using for vm and the networking mode?

---

### Post by brian54 on 2015-03-23
I've tried to telnet using Putty and enabling the Telnet client in Windows and both can't connect. It says attempting and eventually goes back to the C:\ prompt or says it timed out. I don't get why. But I really think it is something on the Pi but I can't figure it out.

I've tried telnet 192.168.2.5 139

Asus routing table:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface192.168.1.254   *               255.255.255.255 UH    0      0        0 WAN
192.168.20.0    192.168.2.3     255.255.255.0   UG    1      0        0 LAN
192.168.2.0     *               255.255.255.0   U     0      0        0 LAN
192.168.1.0     *               255.255.255.0   U     0      0        0 WAN
192.168.10.0    192.168.2.2     255.255.255.0   UG    1      0        0 LAN
default         192.168.1.254   0.0.0.0         UG    0      0        0 WAN
```

---

### Post by volkswagner on 2015-03-24
You didn't answer all of my previous questions.

I don't understand your Asus routing table, there's no mention of a public IP.
Did you change your public ip to "192.168.1.254"? Is the Asus behind yet another router?
What firmware are you using on the Asus (stock, dd-wrt, openWRT, etc.)? If you want
to mask your public ip (for forum posting), simply use xxx.xxx to replace the last two octets.

You need to start simple. If you cant ssh and telnet from a lan connected machine in the 192.168.2.0/24
to both the VM and the VM host, then you need to fix that first. This is why I asked what network mode and VM software you are using.

You should be able to ssh into your Asus from any lan device, then create an ssh session to VM Host, then verify
you can also create a session to the VM. You can then move outward and ssh into Asus from pi, then from VM. You
should then make sure you can connect from pi to the VM host and VM guest. Then move outward again, ssh from
WiFi connected pi guest into Asus, then into VM host, then into VM guest.

FYI, I'm no expert in routing.

---

### Post by darkod on 2015-03-24
I agree with this last START SIMPLE statement. At this point, really slow down and take a deep breath.

So.... According to your photobucket image, and if there are no internal firewalls active, start by testing this:

1. From Laptop: ping 192.168.20.1 (that will show you connectivity to Pi)

2. From PC A: ping 192.168.2.1 (connectivity to ASUS)

3. From PC B: ping 192.168.10.1 (connectivity to IPCop)

Please let us know if all of those work...

---

### Post by darkod on 2015-03-24
If the first step tests work and you wanna continue without waiting for our reply, next round is:

1. From Laptop: ping 192.168.2.1; ping 192.168.2.44

2. From PC B: ping 192.168.2.1; ping 192.168.2.44

That should show connectivity to the 192.168.2.0 network, in other words if routing works good 192.168.20.0 -> 192.168.2.0 and 192.168.10.0 -> 192.168.2.0.

Be careful with your IPCop config, if you set it too restrictive it might actually cut your traffic between .10.0 and .2.0. But wifi clients through the Pi should still work regardless of IPCop.

---

### Post by brian54 on 2015-03-24
I have full connectivity between the subnets. I ran through the pings you suggested (as I have done before) and they still can ping each other and all clients have full Internet connectivity. The laptop can even ping the Ubuntu VM (that is bridged to PC A) at 192.168.2.5....

---

### Post by darkod on 2015-03-24
Hmmm.... with full connectivity how can it be that telnet or ssh don't work?

So you can ping ubuntu vm but not ssh into it?

Silly question: Did you install ssh server on it?

---

### Post by brian54 on 2015-03-24
I can ssh into the Pi from the laptop but not PCA or PCB. Not sure if iptables or something is blocking it?

EDIT:

Actually I can ssh in from PCB. So not sure why my PCA can't, it may be windows firewall or something

Double Edit:

Now I can ssh into from all PCs lol

---

### Post by brian54 on 2015-03-24
I did two Wireshark captures. The one is when the laptop was connected to the Pi and I attempted to connect to the share on the Samba server.

The other is when the same laptop was disconnected from the Pi and connected to the IPCop LAN (10.0/24) and I connected to the share (which is succuessful).

I wanted to upload the files to the forum but it says invalid file type. I'm not too familiar with Wireshark but looking quickly, it looks like when the laptop is connected to the Pi, it is not negotiating the protocol.

There are many packets like [TCP Retransmission] Negotiate Protocol Request. I'll post a screenshot soon.

---

### Post by darkod on 2015-03-24
Good, but why are you trying to ssh into the Pi?

The idea is to double check connectivity to the samba/ubuntu server right? So I meant to ssh into it from all clients (laptop, pc a, pc b). That will confirm connectivity and routes on top of the ping that you already tested.

If that works next is to try open any configured samba share. From windows you can try \\192.168.2.44

---

### Post by brian54 on 2015-03-24
Sorry I'm getting all stressed out and not thinking right....:mad:

I can finally ssh into the Samba server from PC A and PC B but not the laptop (connected to the Pi). I had to install the openssh-server. But something with the Pi...ah!!!!

I can access the samba shares from PCA and PCB but still can't from the Laptop.

---

### Post by darkod on 2015-03-24
So at this point it looks like an issue with the Pi. I haven't used one so I can't comment too much. But not a networking or routing issue. That seems to be working good. Maybe some config issue, or how ubuntu gets installed on a Pi, etc. You can ping the samba server from .20.0 but you mentioned wireshark catches protocol negotiation and not much. No connection established to samba shares.

On the other hand PCB connects to the shares, so you have the samba config etc right.

---

### Post by brian54 on 2015-03-24
Yea I am truly stumped..oh well. I really do appreciate your help!

---

