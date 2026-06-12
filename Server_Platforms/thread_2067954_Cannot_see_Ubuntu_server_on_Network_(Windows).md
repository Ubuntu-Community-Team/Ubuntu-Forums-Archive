---
title: "Cannot see Ubuntu server on Network (Windows)"
date: 2012-10-08
forum: Server Platforms
---

### Post by MorneDJ on 2012-10-08
I got myself two HP Microservers for NAS purposes. Both were the same. I installed Ubuntu server on the one without a glitch, and everything worked from scratch. It is currently doing service as the backup server in my office. 

The send one however have been giving trouble since day one. I think I reinstalled Ubuntu probably 7 times on that, everytime to try and sort out something else, most being the RAID system. I currently have it up and running with RAID operational, and I can copy files to it from another PC on the network. But! I need to search for the PC. I have to type in the IP address as it does not resolve the host name. The other server is called "backup-NAS" and situated at 192.168.0.210. The problem server is called "movie-NAS" and is at 192.168.0.211.

I see backup-NAS on the network and can easily connect to it using either the host name or IP address. 

I cannot see movie-NAS on the network. I cannot connect to it using the host name, neither can I connect to webmin using [https://movie-nas:10000/](https://movie-nas:10000/). I can type in \\192.168.0.211 to connect to it and then I can copy stuff to it and connect to webmin using [https://192.168.0.211:10000/](https://192.168.0.211:10000/)

Clearly it is a broadcast thing but I have no idea how to solve this. Any help will really be appreciated. I mainly connect to it via a Windows machine(s).

---

### Post by albandy on 2012-10-08
Open the file /etc/samba/smb.conf:
sudo gedit /etc/samba/smb.conf

Uncomment the following line (remove the semicolon)
; name resolve order = lmhosts host wins bcast

save and restart samba
sudo /etc/init.d/samba restart

---

### Post by MorneDJ on 2012-10-08
Thanks. I uncommented that line, yet, when I tried restarting SAMBA it told me command not found.

```
> sudo /etc/init.d/samba status
sudo: /etc/init.d/samba: command not found
```

I did try:
```
sudo apt-get install samba
```

It just tells me samba is already the newest version ???

---

### Post by nothingspecial on 2012-10-08
*Thread moved to **Server Platforms**.*

---

### Post by albandy on 2012-10-08
sorry,

sudo service smbd restart

---

### Post by MorneDJ on 2012-10-08
Sigh. Still no luck.

---

### Post by albandy on 2012-10-08
> **MorneDJ said:**
> Sigh. Still no luck.

Can you upload your samba configuration file?

---

### Post by newbie-user on 2012-10-08
Resolving IP address and hostnames is a DNS thing. Check your DNS server to see that movie-NAS is set up properly in DNS.

---

### Post by MorneDJ on 2012-10-09
I have a small network and never had to use it. Everything used to resolved the host names. I thought that the switch that I use did that automatically.

Here is the smb.conf file. I removed the uncommented stuff:

```
[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = WORKGROUP
;	os level = 20
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

name resolve order = lmhosts host wins bcast



[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

 [print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[Storage]
	force user = root
	writeable = yes
	public = yes
	path = /Storage

```

---

### Post by albandy on 2012-10-09
OK, I think I found the problem:

add in [global] section

netbios name = machine_name

and restart

---

### Post by MorneDJ on 2012-10-09
Sigh. Still not working. I cannot understand. I have two identical servers, namely HP 40L Microservers. They each have 4x 2GB Seagate Baracuda drives booting from a 8 GB Kingston flashdrive. I think the only difference is the MAC address of the network card and of course serial numbers.

The installation on the first server went without any problems. Using the same installation process on this server just didn't work. I have had issues since day one. This server is possessed by a demon, and I am turning to a priest to come and drive it from it ...

---

### Post by joiseystud on 2012-10-09
Have you tried resetting the router, or clearing out the dns tables from the router?  

If you ping that hostname from each server, what ip does it resolve to?

---

### Post by Morbius1 on 2012-10-09
From your smb.conf:
> name resolve order = lmhosts host wins bcastlmhosts doesn't exist by default in Ubuntu, host isn't set up for samba /smb by default, and wins refers to a WINS server which I would guess does not exist on your network. That leaves bcast ( in Windows it's called broadcast ) and it's the only one that is fuctional by default.

Rearrange the parameter in smb.conf so that it looks like this:
> name resolve order = bcast host lmhosts winsAnd restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```Wait a few minutes for things to settle down after a samba restart and try it again. Broadcast will take care of all your ip address - netbios name conversions without resorting to more complicated lan side dns configurations.

If you are still having issues post the output of the following command:
```
smbtree
```
[COLOR=Blue]*BTW: Is this for real?*[/COLOR]
> [Storage]
[COLOR=Blue]**force user = root**[/COLOR]     
writeable = yes     
public = yes     
path = /Storage

---

### Post by MorneDJ on 2012-10-10
> **Morbius1 said:**
> From your smb.conf:

[COLOR=Blue]*BTW: Is this for real?*[/COLOR]

Hmm ... yeah. Is that wrong / risky. The server is not on the net and only visible on my home network.

I restarted and waiting for it to "settle".

Thanks

---

### Post by MorneDJ on 2012-10-10
Result of smbtree

```
WORKGROUP
	\\VIDEO-SERV-PC  		
	\\SOUND          		
		\\SOUND\Printer        	PDF-XChange for ABBYY PDF Transformer 2.0
		\\SOUND\C$             	Default share
		\\SOUND\ADMIN$         	Remote Admin
		\\SOUND\Printer2       	Microsoft XPS Document Writer
		\\SOUND\Printer5       	Creates Adobe PDF
		\\SOUND\Printer4       	HP CLJ 3600
		\\SOUND\Games          	
		\\SOUND\SharedDocs     	
		\\SOUND\print$         	Printer Drivers
		\\SOUND\IPC$           	Remote IPC
		\\SOUND\E$             	Default share
	\\SERVER         		
		\\SERVER\HP A3          	HP Deskjet 9800 Series
		\\SERVER\C$             	Default share
		\\SERVER\ADMIN$         	Remote Admin
		\\SERVER\E              	
		\\SERVER\Menco Docs     	
		\\SERVER\R$             	Default share
		\\SERVER\MENCO (E)      	
		\\SERVER\print$         	Printer Drivers
		\\SERVER\IPC$           	Remote IPC
		\\SERVER\E$             	Default share
	\\MORNE-PC       		
	\\MENCO-NAS1     		MENCO-NAS1 server (Samba, Ubuntu)
		\\MENCO-NAS1\IPC$           	IPC Service (MENCO-NAS1 server (Samba, Ubuntu))
		\\MENCO-NAS1\MENCO_Backup1  	
		\\MENCO-NAS1\print$         	Printer Drivers
	\\JOHAN-PC       		
	\\JEANETTE-PC    		
	\\FREENAS        		FreeNAS Server
		\\FREENAS\IPC$           	IPC Service (FreeNAS Server)
		\\FREENAS\FreeNAS_1      	Movies
	\\MUSIC-PC         		
```

---

### Post by Morbius1 on 2012-10-10
Did you run smbtree from "movie-nas"? 

I don't see "backup-nas" which you say you do not have a problem connecting to by name or "movie-nas" which you say is the problem machine.

Are you sure that "movie-nas" is the correct name of the machine? If you run the following command does it come up with that name:
```
testparm -sv | grep "netbios name"
```And do you have a firewall running on that machine. If so, disable it and try smbtree again.

---

### Post by MorneDJ on 2012-10-11
Sorry. Backup-NAS is now called MENCO-NAS1, as I plan installing a second server for backup purposes.

The movie-NAS is the correct name. It was run from the problem PC. It does not want to show.

---

### Post by MorneDJ on 2012-10-11
```
> testparm.samba3 | grep "netbios name"
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
> testparm.samba3 | grep "movie-NAS"
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
```

I have no firewall on this server specifically. I make use of a broadband router (with some crap firewall) connected to a separate PC running a dedicated firewall in some sort of bridge mode which is connected to the Server PC.

---

### Post by Morbius1 on 2012-10-11
What is the output of the following command please:
```
testparm -sv | grep "netbios name"
```And this one:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of movie-nas.*[/COLOR]

---

### Post by MorneDJ on 2012-10-11
```
> testparm -sv | grep "netbios name"
bash: testparm: command not found
> testparm -sv | grep movie-NAS
bash: testparm: command not found
```

```
> sudo nmap -sS -sU -T4 192.168.0.211

Starting Nmap 5.21 ( http://nmap.org ) at 2012-10-11 16:39 SAST
Nmap scan report for 192.168.0.211
Host is up (0.0018s latency).
Not shown: 1994 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
3389/tcp  open  ms-term-serv
10000/tcp open  snet-sensor-mgmt
10000/udp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.36 seconds
```

---

### Post by MorneDJ on 2012-10-11
```
> testparm.samba3 -sv | grep movie-NAS
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
```

---

### Post by Morbius1 on 2012-10-11
> > testparm -sv | grep "netbios name"
bash: testparm: command not foundI do not know why it's giving you that error unless you don't have samba installed or maybe are running samba4.

testparm.samba3 seems to work for some odd reason so what is the oputput of this command:
```
 testparm.samba3 -sv | grep "netbios name"
```If that comes back blank then there is something definitaly wrong with your install. Debian / Ubuntu takes your hostname and makes it the samba netbios name - it does this automatically. You can override this process by adding a line to smb.conf and specifying the netbios name explicitly but I'm not aware of any way to remove it.

And I'm also not ware of any way not to have a host name so the whole thing is perplexing. If this particular server is otherwise fully functional and can be accessed by ip address then I would give it a static one and have all clients access it that way.

---

### Post by MorneDJ on 2012-10-12
Sorry, misunderstood you.

```
> testparm.samba3 -sv | grep "netbios name"
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
	netbios name = MOVIE-NAS
```

I actually thought of trying a different distro, but now it has become an issue to solve this issue. If I need to reformat/re-install, any other distro that you can recommend that will allow a RAID use. The server is purely to act as a file server / NAS.

---

### Post by Morbius1 on 2012-10-12
There is still something wrong with your install if testparm cannot be run but I just noticed that your firewall has the nmbd ( name service ) ports closed - UDP: 137 and 138.

Turn off your firewall. The output of nmap for samba should look something like this:
> Nmap scan report for 192.168.0.100
Host is up (0.0000030s latency).
Not shown: 1990 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm

---

### Post by MorneDJ on 2012-10-12
Hi,

I should not have a firewall installed. I never selected it to be installed (as far as I know). How can I check.

Lemme search the net a bit.

---

### Post by MorneDJ on 2012-10-12
Seems Ubuntu installs ufw by default, but it remains inactive till enabled.

```
> ufw status
Status: inactive
```

---

### Post by Morbius1 on 2012-10-12
I don't know what to tell you. This is what you posted earlier:
> > sudo nmap -sS -sU -T4 192.168.0.211

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-10-11 16:39 SAST
Nmap scan report for 192.168.0.211
Host is up (0.0018s latency).
Not shown: 1994 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
3389/tcp  open  ms-term-serv
10000/tcp open  snet-sensor-mgmt
10000/udp open  unknownYou are missing the nmbd ports I mentioned in my last post.  Your system doesn't close these ports by itself it's something you did or something that you installed that did it.

---

