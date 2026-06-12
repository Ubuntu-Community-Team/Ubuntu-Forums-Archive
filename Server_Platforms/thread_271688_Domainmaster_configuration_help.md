---
title: "Domainmaster configuration help"
date: 2006-10-05
forum: Server Platforms
---

### Post by Gaimlz on 2006-10-05
Hello.

On work now, i'm setting up an ubuntu-server. It would stand as domainserver, dhcp, and print server. 

But now i have a problem. I fallowd [this howto]("http://howtoforge.com/samba_setup_ubuntu_5.10")

I manged to setting up the DHCP by my self, and Its up and running.

But, i can't join a windows machine into the domain (I'havent tried a *nix machine yet, because there ain't no one here)

I manged once and joining the domain on a machine. And it worked fine, but this was early in the stage of configuring the server. Can there be some fouls in my interface? hosts?

Heeelp, please?

```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.11.100
        netmask 255.255.255.0
        network 192.168.11.0
 broadcast 192.168.11.255
        gateway 192.168.11.9
        dns-nameservers 10.2.202.7, 62.97.193.53, 62.97.193.3

```

```
127.0.0.1       localhost.skulen localhost skulen

192.168.11.150


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Should I have all the machine-IP in the workgroup\domain in the /etc/hosts ? - At some places they say I should, some other places not. 

Thanks In advance, and sorry my bad english.

I can try to translate the norwegian-error message; "an error came up, when trying to connect to the domain. This domain dosen't exsist, or can't be reached"

This error came after I typed in my root/administrator password for the domain.

---

### Post by kidders on 2006-10-05
Hi there,

I've never tried to set up a Samba PDC without a proper DNS server, so I'm not sure what you have to do to avoid doing that.

In any case, you should check for other errors. As I'm sure you know, Windows can be quite poor when it comes to giving accurate error messages, so don't take its word for anything! See what your Samba logs tell you.

The first thing I would try is to make sure your Windows machines know how to find the domain controller. Try pinging it by name from a Windows box. (If that fails, Windows might in fact be telling the truth!) 

> Should I have all the machine-IP in the workgroup\domain in the /etc/hosts ?
I imagine you should at least have the domain controller in there, and specify its full domain name. As I understand it, Samba uses /etc/hosts to broadcast naming information to machines in the domain.

Could you post your smb.conf and the Norwegian text of the error message?

---

### Post by Gaimlz on 2006-10-05
Thanks for replaying. 

I'had the machine ip in /etc/host before, then I allways got an error while doing "apt-get update & upgrade" and after googling i understand that should only stand 127.0.0.1 - insteed of whole local ip (in this case; 192.168.11.100)

I can't ping from the ubuntubox, do not get any anwsers. Not even the windows machine in my local network. But the gateway it reach (an redhat firewall/gateway trough out the internet)

```
Pinger skulen [192.168.11.100] med 32 byte data:

Svar fra 192.168.11.100: byte=32 tid<1ms TTL=64
Svar fra 192.168.11.100: byte=32 tid<1ms TTL=64
Svar fra 192.168.11.100: byte=32 tid<1ms TTL=64
Svar fra 192.168.11.100: byte=32 tid<1ms TTL=64
```




```
--- 192.168.11.200 ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 10999ms

```

192.168.11.200 Is the windows machine IP, get from the dhcp server in ubuntu.

So I guess it some interfaces/dhcp fouls?

Samba.conf

```
[global]  
workgroup = Brakanes  
netbios name = Skulen   
server string = %h server (Ulvik Herad)
      
passdb backend = tdbsam   
security = user   
username map = /etc/samba/smbusers   
name resolve order = wins bcast hosts   
domain logons = yes   
preferred master = yes   
domain master = yes
wins support = yes


# Set CUPS for printing   
printcap name = CUPS   
printing = CUPS      
# Default logon   
logon drive = O:   
logon script = scripts/logon.bat   
logon path = \\server1\profile\%U


# Useradd scripts   
add user script = /usr/sbin/useradd -m %u   
delete user script = /usr/sbin/userdel -r %u   
add group script = /usr/sbin/groupadd %g   
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/usermod -G %g %u
add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u   
idmap uid = 15000-20000   
idmap gid = 15000-20000

# sync smb passwords woth linux passwords   
passwd program = /usr/bin/passwd %u   
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .   
passwd chat debug = yes   unix password sync = yes
 
# set the loglevel   log level = 3

[homes]   
comment = Home   
valid users = %S  
read only = no  
browsable = no

[printers]   
comment = All Printers   
path = /var/spool/samba   
printable = yes
guest ok = yes   
browsable = no

[netlogon]  
comment = Network Logon Service   
path = /home/samba/netlogon   
admin users = Administrator   
valid users = %U   
read only = no

[profile]   
comment = User profiles   
path = /home/samba/profiles   
valid users = %U   create mode = 0600   
directory mode = 0700   
writable = yes   
browsable = no

```

---

### Post by Gaimlz on 2006-10-05
Strange, checking syslog now.

```
Oct  5 14:48:36 localhost nmbd[4005]:   Samba name server SKULEN is now a local master browser for workgroup BRAKANES on subnet 192.168.11.100

Oct  5 14:48:57 localhost nmbd[4005]:   for workgroup BRAKANES at IP 192.168.11.227 failed.


```

WHY is samba connecting to the wrong subnet? in interfaces and dhcp config, it stand subnet 192.168.11.0, NOT 100. And why are it trying to connect to 192.168.11.227, that was a local IP that he got from the windows-dhcp server earlyer.

---

### Post by Iowan on 2006-10-05
Never mind - I misread machine ID for subnet ID
(192.168.11.0 and 192.168.11.100 are in the same 255.255.255.0 subnet - aren't they?)

---

### Post by Gaimlz on 2006-10-05
Yes It is. But Why is It connecting to the wrong ip? the ip-adress 192.168.11.227 do not exist on the network (an old release from windows dhcp It is)

---

### Post by Gaimlz on 2006-10-06
Now I'm happy. The linux box is up and running. Smooth! I don't realy know what I did, but heey, It's working allright? fine for me.:-k

---

