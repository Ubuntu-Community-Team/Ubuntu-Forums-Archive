---
title: "Ubuntu/Samba not showing in Win7 Network Places, but accesable via \\server\sharename"
date: 2011-12-05
forum: Server Platforms
---

### Post by Demented ZA on 2011-12-05
I'm running Ubuntu Server 11.04, and Samba. I'm trying to get Samba to be browsable/discoverable via Windows 7's equivalent of Network Places/Network Neighborhood.

I can access the server by opening \\192.168.0.1\share or \\servername\share, but its not discoverable under My network Places.

The reason for this is that I have some media players (WD TV Live for one) that doesn't see my shares, but it used to when the server showed up under Network Places.

The server in question is a standalone server. No domains/authentication etc.

My Samba config file:
```
#======================= Global Settings =======================

[global]
        security = user
        encrypt passwords = true
        map to guest = bad user
        guest account = nobody
        netbios name = SERVER
        log file = /var/log/samba/log.%m
        load printers = no
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
#       obey pam restrictions = yes
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = yes
        server string = SERVER
        unix password sync = yes
        workgroup = WORKGROUP
        os level = 20
#       auto services = global
#       syslog = 0
        preferred master = yes
        panic action = /usr/share/samba/panic-action %d
        max log size = 1000
        pam password change = yes
#       usershare allow guests = yes
        wins support = yes
        local master = yes
        preferred master = yes
        name resolve order = lmhosts host wins bcast
#       interfaces = eth0 eth1
#       bind interfaces only = yes
        SO_RCVBUF=8192 SO_SNDBUF=8192
        socket options = TCP_NODELAY


#======================= Share Definitions =======================

[public]
        comment = Public Share
        path = /srv
        browseable = yes
        read only = yes
        guest ok = yes
```

---

### Post by kleverbear on 2011-12-05
There is another thread from a couple of months ago with same issue, try looking for it i think it will help.

---

### Post by bab1 on 2011-12-05
> **Demented ZA said:**
> I'm running Ubuntu Server 11.04, and Samba. I'm trying to get Samba to be browsable/discoverable via Windows 7's equivalent of Network Places/Network Neighborhood.

I can access the server by opening \\192.168.0.1\share or \\servername\share, but its not discoverable under My network Places.

The reason for this is that I have some media players (WD TV Live for one) that doesn't see my shares, but it used to when the server showed up under Network Places.

The server in question is a standalone server. No domains/authentication etc.



You can start by changing this ```
       name resolve order = lmhosts host wins **bcast**

```

to this```
       name resolve order = **bcast** lmhosts host wins 

```

and making sure that the **nmbd **process is running with the following command```
pgrep -l mbd
```

It should look something like this```
971 smbd
1017 smbd
1037 nmbd
```

Edit:  What was the reason for the commenting the lines out that you did?

---

### Post by Demented ZA on 2011-12-05
> **kleverbear said:**
> There is another thread from a couple of months ago with same issue, try looking for it i think it will help.

I forgot to mention that I've been searching myself blue in the face. I've been working on this for the past 13 hours straight. I don't suppose you have a link? Or what words I should search for? All I get is posts about Windows not seeing Shares etc.

Thanks for the reply.

---

### Post by Demented ZA on 2011-12-05
> **bab1 said:**
> You can start by changing this ```
       name resolve order = lmhosts host wins **bcast**

```to this```
       name resolve order = **bcast** lmhosts host wins 

```and making sure that the **nmbd **process is running with the following command```
pgrep -l mbd
```It should look something like this```
971 smbd
1017 smbd
1037 nmbd
```Edit:  What was the reason for the commenting the lines out that you did?

I made the changes you mentioned.

pgrep -l mbd
```
3859 nmbd
3860 nmbd
3867 smbd
3869 smbd
3879 smbd
```The comments were me trying to simplify the config. Occam's razor approach.

My current config file:
```
[global]
security = user
encrypt passwords = true
map to guest = bad user
guest account = nobody
netbios name = SERVER
log file = /var/log/samba/log.%m
load printers = no
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *
password\supdated\ssuccessfully* .
obey pam restrictions = yes
passwd program = /usr/bin/passwd %u
passdb backend = tdbsam
dns proxy = yes
server string = SERVER
unix password sync = yes
workgroup = WORKGROUP
os level = 20
auto services = global
syslog = 0
preferred master = yes
panic action = /usr/share/samba/panic-action %d
max log size = 1000
pam password change = yes
usershare allow guests = yes
wins support = yes
local master = yes
preferred master = yes
name resolve order = bcast lmhosts host wins
interfaces = eth0 eth1
bind interfaces only = yes
SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

#======================= Share Definitions =======================

[share]
        create mask = 0666
        directory mask = 0777
        writeable = yes
        browseable = yes
        public = yes
        path = /srv
```I also just upgraded to Samba 3.5.11 from 3.4.0, just to rule out a version specific problem.

Still not showing up under Network Places. I restarted two PC's and the server (not just the Samba processes).

I can access the server using \\server and that works fine. I have cleared my IP tables firewall just to rule that out as well.

---

### Post by bab1 on 2011-12-05
> **Demented ZA said:**
> I made the changes you mentioned.

pgrep -l mbd
```
3859 nmbd
3860 nmbd
3867 smbd
3869 smbd
3879 smbd
```The comments were me trying to simplify the config. Occam's razor approach.

My current config file:
```
[global]
security = user
encrypt passwords = true
map to guest = bad user
guest account = nobody
netbios name = SERVER
log file = /var/log/samba/log.%m
load printers = no
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *
password\supdated\ssuccessfully* .
obey pam restrictions = yes
passwd program = /usr/bin/passwd %u
passdb backend = tdbsam
dns proxy = yes
server string = SERVER
unix password sync = yes
workgroup = WORKGROUP
os level = 20
auto services = global
syslog = 0
preferred master = yes
panic action = /usr/share/samba/panic-action %d
max log size = 1000
pam password change = yes
usershare allow guests = yes
wins support = yes
local master = yes
preferred master = yes
name resolve order = bcast lmhosts host wins
interfaces = eth0 eth1
bind interfaces only = yes
SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

#======================= Share Definitions =======================

[share]
        create mask = 0666
        directory mask = 0777
        writeable = yes
        browseable = yes
        public = yes
        path = /srv
```

I also just upgraded to Samba 3.5.11 from 3.4.0, just to rule out a version specific problem.

Still not showing up under Network Places. I restarted two PC's and the server (not just the Samba processes).

I can access the server using \\server and that works fine. I have cleared my IP tables firewall just to rule that out as well.

Did you restart the 2 services (smbd and nmbd)?  Like this```
sudo service smbd restart
``` and ```
sudo service nmbd restart
```


Wait a few minutes for the master browse list to be re-populated.

Edit: The system has defaults even if you comment out the line in the smb.conf file.  All the defaults are listed in the man pages or at the samba.org [**_[COLOR="Blue"]documentation[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

**Edit2:** Try turning off the firewall while testing.  Later on you can set the following to  pass the firewall

[LIST]
[*]NetBIOS name management traffic over UDP port 137
[*]NetBIOS datagram traffic over UDP port 138
[*]NetBIOS session traffic over TCP port 139
[*]NetBIOS raw over TCP port 445
[/List]

---

### Post by Demented ZA on 2011-12-05
> **bab1 said:**
> Did you restart the 2 services (smbd and nmbd)?  Like this```
sudo service smbd restart
``` and ```
sudo service nmbd restart
```Wait a few minutes for the master browse list to be re-populated.
Thats exactly what I did. It didn't seem to work, so I restarted the two PC's and the server. Played some Skyrim for an hour and when I came back, still not discovered under Network Places.
> 
Edit: The system has defaults even if you comment out the line in the smb.conf file.  All the defaults are listed in the man pages or at the samba.org [**_[COLOR=Blue]documentation[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")Thats what I was going for. I want to get the most basic config to get this to work, and then build from there. I can wipe my entire config and start from scratch. Most of the settings in the config thus far are a combination of what was in, and what guides told me to use, but still I couldn't get it to work.

I do see other PC's though, so networking etc is working as expected.
[ATTACH]208598[/ATTACH]

>  Edit2: Try turning off the firewall while testing. I have turned off the firewall, and flushed all rules/routes. Still no joy.

I think I'm going to bed now and will tackle it again in the morning.

Thanks for the help so far!

---

### Post by bab1 on 2011-12-05
> **Demented ZA said:**
> Thats exactly what I did. It didn't seem to work, so I restarted the two PC's and the server. Played some Skyrim for an hour and when I came back, still not discovered under Network Places.
Thats what I was going for. I want to get the most basic config to get this to work, and then build from there. I can wipe my entire config and start from scratch. Most of the settings in the config thus far are a combination of what was in, and what guides told me to use, but still I couldn't get it to work.

I do see other PC's though, so networking etc is working as expected.
[ATTACH]208598[/ATTACH]

Thanks for the reply.

See my edit(s).  Try turning off the FW.

---

### Post by Morbius1 on 2011-12-05
The thing that's perplexing about this problem is this observation:
> I can access the server by opening \\192.168.0.1\share or \\servername\share, but its not discoverable under My network Places.If it was an nmbd, smbd, or firewall problem you would not be able to do a \\servername\share.

I don't know if this works anymore in Win7 but go into Command Prompt ( or whatever Win7 may call it today ) and run the following command to see if it outputs any errors:
```
net view
```It should list every machine by name or give you errors if it finds anything odd.

---

### Post by bab1 on 2011-12-05
> **Morbius1 said:**
> The thing that's perplexing about this problem is this observation:
If it was an nmbd, smbd, or firewall problem you would not be able to do a \\servername\share.

I don't know if this works anymore in Win7 but go into Command Prompt ( or whatever Win7 may call it today ) and run the following command to see if it outputs any errors:
```
net view
```It should list every machine by name or give you errors if it finds anything odd.

Hmmmm, I missed the \\servername\share bit.  I stopped at \\ip_address\share.

I have to agree with Morbius1 here.  I wonder if the firewall is stopping part of the netbios discovery.  :-(

---

### Post by volkswagner on 2011-12-05
You should not rule out Win7 network settings. You did not mention you network/sharing setting on Win7.

I do notice many of your SAMBA settings are changed from default.

I would suggest setting as much back to default that your system would allow.  If you can get it to work with defaults, change one item at a time to see what breaks it.


Things that stand out:

Do you have DNS proxy setup?  Correctly?
```
dns proxy = yes
```

Is your windows box set to the same workgroup?
```
workgroup = WORKGROUP
```

This is listed twice and also not the default:
```
preferred master = yes
```

Not default
```
wins support = yes
local master = yes
```

Do you need both interfaces here?  Are they correct?
```
interfaces = eth0 eth1
```


I have no issues with the following default config using SMBD version Version 3.4.7 With Win7 client.

```
[global]

   workgroup = myworkgroup
   netbios name = fileserver
   dns proxy = no
;   name resolve order = bcast host lmhosts wins
   interfaces = eth0
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
```

---

### Post by Demented ZA on 2011-12-06
> **bab1 said:**
> Hmmmm, I missed the \\servername\share bit.  I stopped at \\ip_address\share.

I have to agree with Morbius1 here.  I wonder if the firewall is stopping part of the netbios discovery.  :-(

I suppose you and I were both busy editing our posts at the same time, cause that's when I mentioned that I have disabled and cleared the firewall to allow all traffic.

---

### Post by Demented ZA on 2011-12-06
> **volkswagner said:**
> You should not rule out Win7 network settings. You did not mention you network/sharing setting on Win7.

Well both machines are fresh installs, formatted them expressly for this problem before posting here. Both have only the windows firewall, and that is set do allow all traffic. Both PC's have the network chosen as "Work Networks". And then there's the WD TV Live Media player that has NO FIREWALL, connected via cable and has been reset to factory settings.

> 
I do notice many of your SAMBA settings are changed from default.

I would suggest setting as much back to default that your system would allow.  If you can get it to work with defaults, change one item at a time to see what breaks it.
That's exactly what I did with the comments earlier, though I had more commented out than that before I came here to post.

> 
Things that stand out:

Do you have DNS proxy setup?  Correctly?
```
dns proxy = yes
```Not sure. Nothing changes whether its yes or no. I've commented it out in the meantime to keep it at default.

> 
Is your windows box set to the same workgroup?
```
workgroup = WORKGROUP
```Yup. All are on the "WORKGROUP" workgroup. If I change this, net view gives errors on any of the clients. Otherwise, it works, though not listing the server.

> 
This is listed twice and also not the default:
```
preferred master = yes
```I removed the duplicate line. I assume this should be set to yes, as the server is the master browser here isn't it?

> Not default
```
wins support = yes
local master = yes
```Should they be different? According to a lot of guides, they should be set as above.

> Do you need both interfaces here?  Are they correct?
```
interfaces = eth0 eth1
```Ultimately I'll need both interfaces, but for now I removed eth1 for testing purpose.

> 
I have no issues with the following default config using SMBD version Version 3.4.7 With Win7 client.
I kept feeling like I should just try someone's basic config that's working, but I can't really find a simple working config on the internet. I could only find fragments, and none worked. Thank you for your sample. I'll give it a try. What does your share definitions look like if I may ask?

---

### Post by Demented ZA on 2011-12-06
On a hunch, I set my IP up statically, adding the server as a wins server and forcing Netbios on. Suddenly the server shows up and my media player sees the server as well. I'm also using volkswagner's above config (adapted to my network) so I thought it was that, that solved my problem. When I set my IP settings back to DHCP, I couldn't see the server under net view anymore, nor would my media player.

I suspect now that the problem is with my DHCP server and how it hands out lease information pertaining to WINS. Does this make sense?

With static IP's, this is what ipconfig /all looks like, and this is how its working:
```
Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 6C-F0-49-5E-3E-ED
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.0.128(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . : 192.168.0.1
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   Primary WINS Server . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
```Output of net view:
```
Server Name            Remark

------------------------------------
\\Windows-PC
\\SERVER                     Samba 3.5.11
The command completed successfully.


```Vs. DHCP settings and its not working:
```
Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 6C-F0-49-5E-3E-ED
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.0.128(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 06 December 2011 11:39:54 AM
   Lease Expires . . . . . . . . . . : 06 December 2011 11:49:54 AM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   Primary WINS Server . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

```And then net view:
```
C:\Users\Demented>net view
There are no entries in the list.


```Its clear that when using DHCP, net view can't obtain a list, but with static settings, everything works as expected.

Following is my DHCP configuration file:
```
use-host-decl-names on;
option netbios-name-servers 192.168.0.1;
ddns-update-style interim;
ignore client-updates;
ddns-rev-domainname "in-addr.arpa.";

option domain-name-servers 192.168.0.1;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

key DHCPUPD8 {
    algorithm hmac-md5;
    secret MASKED;
    }

zone 0.168.192.in-addr.arpa. {
  primary 127.0.0.1;
  key MASKED;
}


# Local
subnet 192.168.0.0 netmask 255.255.0.0 {
    option netbios-name-servers 192.168.0.1;
    option broadcast-address 255.255.0.0;
    authoritative;
    ddns-updates on;
    range 192.168.0.10 192.168.0.240;
    option routers 192.168.0.1;
    option domain-name-servers 192.168.0.1;
    }

# Windows-PC
host weekwarrior {
    hardware ethernet MASKED;
    fixed-address 192.168.0.127;
    }


```

---

### Post by Demented ZA on 2011-12-06
I noticed that Static and DHCP differed with only the subnet, allocating 255.255.255.0 and 255.255.0.0 respectively. I corrected my DHCP server to configure clients for 255.255.255.0. Heres my config file:
```
[global]
option subnet-mask 255.255.255.0;
use-host-decl-names on;
option netbios-name-servers 192.168.0.1;
ddns-update-style interim;
ignore client-updates;
ddns-rev-domainname "in-addr.arpa.";

option domain-name-servers 192.168.0.1;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

key MASKED {
    algorithm hmac-md5;
    secret MASKED;
    }

zone 0.168.192.in-addr.arpa. {
  primary 127.0.0.1;
  key MASKED;
}


# Local
subnet 192.168.0.0 netmask 255.255.0.0 {
    option netbios-name-servers 192.168.0.1;
    option broadcast-address 255.255.0.0;
    authoritative;
    ddns-updates on;
    range 192.168.0.10 192.168.0.240;
    option routers 192.168.0.1;
    option domain-name-servers 192.168.0.1;
    }


```Everything seems to be working now. It doesn't make sense to me that this made the difference, but if it did, you won't see me arguing.

Now I've got a foundation to work from. Thanks for everybody's help! :guitar:

---

### Post by Demented ZA on 2011-12-08
Just to confirm, the problem was with my DHCP server all along.

I restored my entire Ubuntu server to a previous backup, and only kept the new DHCP configuration. Immediately after renewing client leases, my server was visible under my network places.

Something so seemingly unrelated.

Also, I discovered [Swat]("https://help.ubuntu.com/community/Swat") for Samba which is a web based Samba server administration tool. Very handy as it neatly explains all the options. Really helps getting some semblance of Samba and its configuration options.

Hope the above will help others!

---

### Post by DUCKFACE on 2012-07-12
same problem here !
Can't see samba server in Microsoft windows network! 
ubuntu version 12.04 


samba conf:
[global]
    display charset = cp1251
    passwd chat debug = yes
    name resolve order = wins bcast hosts
    idmap gid = 15000-20000
    passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
    time server = yes
    hosts allow = 192.168.0., 127.0.0.1/255.255.255.0 
    passwd program = /usr/bin/passwd %u
    netbios name = SERVER
    printing = CUPS
    idmap uid = 15000-20000
    logon script = login.bat
    dos charset = cp1251
    workgroup = EXPERT2002
    os level = 64
    printcap name = CUPS
    security = user
    add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u
    delete user script = /usr/sbin/userdel -r %u
    max log size = 1000
    log file = /var/log/samba/log.%m
    load printers = yes
    smb passwd file = /etc/samba/smbpasswd
    add group script = /usr/sbin/groupadd %g
    socket options = TCP_NODELAY
    delete group script = /usr/sbin/groupdel %g
    add user to group script = /usr/sbin/usernod -G %g %u
    logon drive = H:
    guest ok = no
    interfaces = 127.0.0.1/255.0.0.0 192.168.0.1/254.255.255.0 eth1
    username map = /etc/samba/smbusers
    encrypt passwords = true
    passdb backend = tdbsam
    logon home = \\%N\%U
    template shell = /bin/bash
    wins support = yes
    unix password sync = yes
    logon path = \\%N\%U\
    add user script = /usr/sbin/useradd -m '%u' -g users -G users
    syslog = 3
    preferred master = yes
    panic action = /usr/share/samba/panic-action %d
    unix charset = utf8
    domain logons = yes
    server string = %h (Samba, Ubuntu)

#### Networking ####

#### Debugging/Accounting ####

####### Authentication #######
# sync smb passwords woth linux passwords

########## Domains ###########
#logon path = \\%L\profiles\%U
#logon home = \\%L\%U


########## Printing ##########

#======================= Share Definitions =======================
#======================= Global Sharing START ======================

[printers]
comment = All Printers
path = /var/spool/samba
printable = yes
public = no
writable = no
create mode = 0700

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no
write list = root, @smbadmin

[netlogon]
comment = Network Logon Service
path = /home/samba/netlogon
#path = /media/externalHDD/documents
admin users = Administrator
valid users = %U
read only = yes
guest ok = yes
#browseable = no
writable = no
share modes = no

[homes]
comment = Home Directories
browseable = no
read only = no
create mask = 0700
directory mask = 0700
valid users = %S

[Profiles]
comment = User profile
path = /home/%U
valid users = %U
writeable = yes
browseable = no
create mask = 0600
directory mask = 0700
nt acl support = yes
profile acls = yes 

#======================= Global Sharing END ======================

[Apis6]
comment = Apis 6
path = /media/externalHDD/apis6
writable = yes
create mask = 0660
directory mask = 0770
force group = users
valid users = @users

[Rankom]
comment = Rankom software
path = /media/externalHDD/rankom
writable = yes
create mask = 0660
directory mask = 0770
force group = users
valid users = @users

[Documents]
comment = Shared documents
path = /media/externalHDD/documents
writable = yes
create mask = 0660
directory mask = 0770
force group = users
valid users = @users

[Archive]
comment = Archive
path = /media/externalHDD/archive
writable = yes
create mask = 0660
directory mask = 0770
force group = users
valid users = @users
veto files = /*.exe/*.com/*.dll/*.bat/*.pif/


i can't see Samba server from my network in Windows XP

```
pgrep -l mbd
```

26935 nmbd
26936 nmbd
26940 nmbd
26950 nmbd
26957 nmbd
26964 nmbd
26971 nmbd
26978 nmbd
26985 nmbd
26992 nmbd
26999 nmbd
27006 nmbd
27013 nmbd
27020 nmbd
29238 smbd
29240 smbd
29253 nmbd
29261 nmbd
29269 nmbd
29277 nmbd
29285 nmbd
29293 nmbd
29301 nmbd
29309 nmbd
29317 nmbd
29325 nmbd
29333 nmbd
29353 nmbd
29361 nmbd
29369 nmbd
29377 nmbd
29385 nmbd
29393 nmbd
29402 nmbd
29410 nmbd
29418 nmbd
29426 nmbd
29434 nmbd


```
testparm
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "idmap gid" option is deprecated
WARNING: The "idmap uid" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[netlogon]"
WARNING: The "share modes" option is deprecated
Processing section "[homes]"
Processing section "[Profiles]"
Processing section "[Apis6]"
Processing section "[Rankom]"
Processing section "[Documents]"
Processing section "[Archive]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC


```
netstat -tunap | grep mbd
```

tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      30997/smbd
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      30997/smbd
udp        0      0 192.168.1.255:137       0.0.0.0:*                           26935/nmbd
udp        0      0 192.168.1.2:137         0.0.0.0:*                           26935/nmbd
udp        0      0 10.8.0.255:137          0.0.0.0:*                           26935/nmbd
udp        0      0 10.8.0.1:137            0.0.0.0:*                           26935/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           26935/nmbd
udp        0      0 192.168.1.255:138       0.0.0.0:*                           26935/nmbd
udp        0      0 192.168.1.2:138         0.0.0.0:*                           26935/nmbd
udp        0      0 10.8.0.255:138          0.0.0.0:*                           26935/nmbd
udp        0      0 10.8.0.1:138            0.0.0.0:*                           26935/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           26935/nmbd

---

### Post by DUCKFACE on 2012-08-10
noone around ?

---

### Post by bearsinthesea on 2013-06-02
> **Demented ZA said:**
> Just to confirm, the problem was with my DHCP server all along.

I restored my entire Ubuntu server to a previous backup, and only kept the new DHCP configuration. Immediately after renewing client leases, my server was visible under my network places.

Something so seemingly unrelated.

Also, I discovered [Swat]("https://help.ubuntu.com/community/Swat") for Samba which is a web based Samba server administration tool. Very handy as it neatly explains all the options. Really helps getting some semblance of Samba and its configuration options.

Hope the above will help others!

This solved my problem, thank you so much for sharing, here I will do the same. But it was not DHCP. My ubuntu server was not showing up in Network Places or Network Neighborhood on my Windows 7 machine. It was not becoming the broswer master for the workgroup. I checked my other systems using smbclient, and they did not see the new machine (Greta). But when I checked using smbclient -L localhost on Greta, it said it was the Master Browser.

Finally, I looked again comparing the output of ifconfig on my two linux machines. one had a netmask of 255.255.0.0, and teh other 255.255.255.0. They should both be 255.255.255.0, so I changed that using NetworkManager, which required a reboot. Now it works. Apparently the tcp/ip connections were more forgiving, ssh, web browsing, everythign worked with the mismatched netmasks, except the SMB protocols.

---

