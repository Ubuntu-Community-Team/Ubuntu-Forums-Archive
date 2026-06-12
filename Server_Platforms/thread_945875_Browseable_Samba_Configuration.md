---
title: "Browseable Samba Configuration"
date: 2008-10-12
forum: Server Platforms
---

### Post by adri_ht_ on 2008-10-12
Hello guys,

I'm having some issues with Samba and making it browse able through the network places. As of now I have a simple configuration:

```
[global]
	
server string = %h
	
map to guest = Bad User
	
obey pam restrictions = Yes
	
passdb backend = tdbsam
	
pam password change = Yes
	
passwd program = /usr/bin/passwd %u
	
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	
syslog = 0
	
log file = /var/log/samba/log.%m
	
max log size = 1000
	
dns proxy = No
	
usershare allow guests = Yes
	
panic action = /usr/share/samba/panic-action %d
	
invalid users = root



[webspace]
	
path = /var/www/



[ftpspace]
	
path = /home/ftp
	
read only = No


```

With this I can get to the shares in a Windows Box by using only the "net use" command.

I looked through the Samba documentation on how to make the shares browse able through Network Places in Windows, but it seems to be a bit confusing. I would appreciate a good link or a hint on this topic. Thx

---

### Post by lykwydchykyn on 2008-10-12
Are you running a firewall, and if so what ports have you opened?  You can check with:
```

sudo iptables -L

```

Also, are your windows clients capable of browsing shares on other servers?  And if you type \\server_ip_address into start=>run, can you view the shares?

It's also worth noting you haven't assigned a workgroup to this machine.

---

### Post by adri_ht_ on 2008-10-13
> **lykwydchykyn said:**
> Are you running a firewall, and if so what ports have you opened?  You can check with:
```

sudo iptables -L

```

Also, are your windows clients capable of browsing shares on other servers?  And if you type \\server_ip_address into start=>run, can you view the shares?

It's also worth noting you haven't assigned a workgroup to this machine.

Yes I'm running a firewall, but I'm 100% sure it is not the problem because I have the necessary ports open. By the way I also tested it with the firewall off.

Yes, my Windows boxes are capable of browsing shares. I even have a Buffalo NAS running samba aswell and it is browseable. If I try to access the server with \\ip\share it won't go through. All computers are set to use the same WorkGroup. 

Like I said the only way of accessing the server is by mounting the share manually with the net use command. Thanks

---

### Post by lykwydchykyn on 2008-10-13
Are there any errors in /var/log/samba/log.nmbd?  I'm thinking netbios name resolution isn't working out here.

---

### Post by adri_ht_ on 2008-10-18
> **lykwydchykyn said:**
> Are there any errors in /var/log/samba/log.nmbd?  I'm thinking netbios name resolution isn't working out here.

Finally I had time to play with it. The first thing that I did was to reduce the smb.conf file to a workable minimun:

```

[global]
workgroup = HOMENET
server string = %h
invalid users = root
log file = /var/log/samba/log.%m
max log size = 1000

[share1]
path = /var/www
[share2]
path = /home/ftp

```

At first I was amazed that it worked. I mean all computers could browse the shares. Then I decided to add some more features to the .conf file and messed the whole thing again. Obviously I reconfigured the .conf file to its previous working state and no matter what now it doesn't work!

Note: I check log.nmbd and no errors so far...

---

### Post by adri_ht_ on 2008-10-24
The server fails to work most of the time. It usually never works through "Network Places"; always giving a 'network path not found'. It work sometimes by running \\servers_ip\

smb.conf

```

[global]
workgroup = HOMENET
server string = %h
invalid users = root 
log file = /var/log/samba/log.%m
max log size = 1000

[share1]
path = /var/www
[share2]
path = /home/ftp

```

Iptable commands...

```
# Ports needed by Samba

$IPTABLES -A INPUT -i $WAN_IFACE -p udp -m udp --dport 137 -j ACCEPT
$IPTABLES -A INPUT -i $WAN_IFACE -p udp -m udp --dport 138 -j ACCEPT
$IPTABLES -A INPUT -m state --state NEW -m tcp -p tcp --dport 139 -j ACCEPT
$IPTABLES -A INPUT -m state --state NEW -m tcp -p tcp --dport 445 -j ACCEPT
```

Also the Ubuntu Server is on a VM box under Windows Vista. FTP and Apache work flawlessly. My network has another unix base server, a "Buffalo NAS". I was reading a little bit about setting the server as a "Local Master" or "Domain Master" or "Preferred Master". Could this be the problem? I still don't get the concept really well. Please help....

---

### Post by david_lynch on 2008-10-24
> **adri_ht_ said:**
> Also the Ubuntu Server is on a VM box under Windows Vista. 
Ouch. all bets are off in that case.

---

### Post by doas777 on 2008-10-24
if you are trying to browse vista, your connection needs to login with ntlmv2. to enable it, add this line to your conf:
```
client NTLMv2 auth = Yes
```

this is the authentication section I use:
```

####### Authentication #######
	 security = user
   	client schannel = Auto
   	server schannel = Auto

   	lanman auth = No
   	ntlm auth = No
   	client NTLMv2 auth = Yes
   	client lanman auth = No
   	client plaintext auth = No
	encrypt passwords = true

	obey pam restrictions = yes
	unix password sync = yes

   	passwd program = /usr/bin/passwd %u
   	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

  	pam password change = yes
	map to guest = bad user


```

good luck,
franklin

---

### Post by adri_ht_ on 2008-11-01
Thanks everyone for helping me out. I recently reinstalled Ubuntu Server in a HDD instead of a VM box and the netbios worked flawlessly out of the box. I guess my VM box under Vista was causing all the unexpected errors. Thanks again.

---

