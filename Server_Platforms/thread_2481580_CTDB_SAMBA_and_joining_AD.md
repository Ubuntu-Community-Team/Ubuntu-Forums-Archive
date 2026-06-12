---
title: "CTDB SAMBA and joining AD"
date: 2022-12-03
forum: Server Platforms
---

### Post by thetravelingsandwich on 2022-12-03
Hello everyone :)
I have the following setup
3 supermicro servers running the latest version of ubuntu server.
i have created a zfs pool on the backend
to replicate the data i have setup glusterFS
Then I use CTDB to replicate the settings and take care of everything else

At this point the setup works great and i can connect with ssh, nfs etc and share files, however i need to use SMB/CIFS for our windows clients
I setup samba and this also works great.

The problem i run into now is i have to join the server to the domain and when i do this ctdb stops and it is not working properly
Ill break down what i have done to my setup

ZFS
```

check Hostname	hostnamectl
Install ZFS
	sudo apt install zfsutils-linux -y
	sudo apt install zfsutils-linux zfs-dkms -y
	sudo systemctl enable zfs.target zfs-import.target zfs-mount.service zfs-import-cache.service zfs-import-scan.service
	which zfs
Setup array
        sudo mkdir /mnt/gluster
        sudo zpool create -f -m /mnt/gluster gluster

```

Gluster
```

	sudo apt install software-properties-common -y
	sudo apt install glusterfs-server -y
	sudo apt install glusterfs-client -y
Check gluster service
		sudo systemctl enable glusterd.service
		sudo systemctl start glusterd.service
		sudo systemctl status glusterd.service
Configure Gluster
	sudo gluster peer probe ho-sm-sto-00
	sudo gluster peer probe ho-sm-sto-01
	sudo gluster peer probe ho-sm-sto-02
	sudo gluster peer status
	sudo mkdir /mnt/gluster/Archive/
	sudo mkdir /mnt/gluster/Prod/
	sudo mkdir /mnt/gluster/ctdb
Create Gluster Volumes
	sudo gluster volume create Archive replica 3 transport tcp HO-SM-Sto-00:/mnt/gluster/Archive/ HO-SM-Sto-01:/mnt/gluster/Archive/ HO-SM-Sto-02:/mnt/gluster/Archive/ force
	sudo gluster volume create Prod replica 3 transport tcp HO-SM-Sto-00:/mnt/gluster/Prod/ HO-SM-Sto-01:/mnt/gluster/Prod/ HO-SM-Sto-02:/mnt/gluster/Prod/ force
	sudo gluster volume create ctdb replica 3 transport tcp HO-SM-Sto-00:/mnt/gluster/ctdb/ HO-SM-Sto-01:/mnt/gluster/ctdb/ HO-SM-Sto-02:/mnt/gluster/ctdb/ force
Start Volume
	sudo gluster volume start Archive
	sudo gluster volume start Prod
	sudo gluster volume start ctdb
Mount GlusterFS to allow replicated data
	sudo mkdir /mnt/glusterfs
	sudo mkdir /mnt/glusterfs/Archive
	sudo mkdir /mnt/glusterfs/Prod
	sudo mkdir /mnt/glusterfs/ctdb
	sudo mount -t glusterfs ho-sm-sto-00:/Archive /mnt/glusterfs/Archive
	sudo mount -t glusterfs ho-sm-sto-00:/Prod /mnt/glusterfs/Prod
	sudo mount -t glusterfs ho-sm-sto-00:/ctdb /mnt/glusterfs/ctdb
Setup Automounts
	sudo su -l
	echo "ho-sm-sto-00:Archive /mnt/glusterfs/Archive glusterfs defaults,_netdev 0 0" >>/etc/fstab
	echo "ho-sm-sto-00:Prod /mnt/glusterfs/Prod glusterfs defaults,_netdev 0 0" >>/etc/fstab
	echo "ho-sm-sto-00:ctdb /mnt/glusterfs/ctdb glusterfs defaults,_netdev 0 0" >>/etc/fstab




```

Samba
```

Install Samba and utilities
	sudo apt-get install ctdb samba samba-common winbind smbclient -y
	sudo add-apt-repository ppa:sergiodj/samba-glusterfs
	sudo apt update --allow-insecure-repositories
	sudo apt-get install samba-vfs-glusterfs -y
Edit samba conf file
	cp /etc/samba/smb.conf /mnt/glusterfs/ctdb/
	mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
	vi /mnt/glusterfs/ctdb/smb.conf
		under global add the following lines
			[global]	
				netbios name = ho-sm-storage
				clustering = yes
				workgroup = DOMAIN
				realm = DOMAIN.CA
				wins server = 172.16.2.20
				idmap backend = tdb
			# enabling this breaks ctdb from starting samba security = ADS
				private dir = /mnt/glusterfs/ctdb/
				registry shares = yes		
				#idmap backend = autorid
				#idmap config * : backend = autorid
				#idmap config * : range = 1000000-1999999
				# idmap config * is for non domain users
				# make sure ranges do not overlap
				idmap config * : backend = tdb2
				idmap config * : range = 10000-19999
			# idmap config DOMAIN is for domain users
				idmap config DOMAIN : backend = rid
				idmap config DOMAIN : range = 100000-1999999
			# include = registry
				vfs objects = gpfs fileid acl_xattr
				gpfs:sharemodes = yes
				fileid:algorithm = fsname
				windbind enum groups = yes
				windbind enum users = yes
			# important for windows ACL use
				ea support = yes
				map acl inherit = yes
				store dos attributes = yes
			# this is newly added
			#	encrypt passwords = yes
			#	password server = *
			[Archive]
				comment = Highly available share for Archive Data
				path = /mnt/glusterfs/Archive
				readonly = no
				writable = yes
				browsable = yes
			[Prod]
				comment = Highly available share for Production Data
				path = /mnt/glusterfs/Prod
				readonly = no
				writable = yes
				browsable = yes


```

CTDB
```

edit CTDB File
	vi /mnt/glusterfs/ctdb/ctdb.conf
		[logging]
        # Enable logging to syslog
        file = /var/log/ctdb/log.ctdb
        # Default log level
        log level = NOTICE
		[cluster]
		CTDB_RECOVERY_LOCK=/mnt/glusterfs/ctdb/lockfile
		CTDB_PUBLIC_ADDRESSES=/etc/ctdb/public_addresses
		CTDB_MANAGES_SAMBA=yes
		# change windbind back to yes after domain join
		CTDB_MANAGES_WINDBIND=no
		# CIFS only
		CTDB_NODES=/etc/ctdb/nodes
Remove orignal ctdb.conf
	sudo mv /etc/ctdb/ctdb.conf /etc/ctdb/ctdb.conf.bak
Link new shared ctdb config file
	ln -s /mnt/glusterfs/ctdb/ctdb.conf /etc/ctdb/ctdb.conf
setup virtual ip
	vi /mnt/glusterfs/ctdb/public_addresses
		172.16.22.39/24 bond0
	vi /mnt/glusterfs/ctdb/nodes
		172.16.22.40
		172.16.22.41
		172.16.22.42
Link files
	ln -s /mnt/glusterfs/ctdb/public_addresses /etc/ctdb/public_addresses
	ln -s /mnt/glusterfs/ctdb/nodes /etc/ctdb/nodes
        ln -s /mnt/glusterfs/ctdb/smb.conf /etc/samba/smb.conf
start ctdb service
	sudo systemctl enable ctdb
	sudo systemctl start ctdb
Add legacy events to ctdb
	ctdb event script enable legacy 50.samba
	ctdb event script enable legacy 49.winbind


```

AD Stuff

```

Set timezone for AD joining
	timedatectl set-timezone America/Edmonton
Setup AD Join
	sudo apt install sssd-ad sssd-tools realmd adcli libpam-sss samba-common-bin
Make sure ubuntu can see the domain
	realm -v discover domain.ca
	sudo realm join -v -U dmackenzieadm DOMAIN.ca
Now check to make sure that it can pull AD information
	getent passwd donald.mackenzie@DOMAIN.CA
Install Kerberos
	sudo apt install krb5-user -y
Test kerbos
	smbclient -L dc0-2.domain.ca -U dmackenzieadm


```

I have also setup this incase i need it
```

Edit Name Switch Service
	change passwd and group to look like below 
	vi /etc/nsswitch.conf
	# passwd:         files systemd sss
	# group:          files systemd sss
	passwd:         compat winbind
	group:          compat winbind
	shadow:         compat
setup DNS
	vi /etc/systemd/resolved.conf
	DNS=172.16.2.20 172.16.2.21 172.16.22.20 172.16.22.21
	Domains=DOMAIN.CA
	DNSStubListener=yes
edit nsswitch.conf
            vi /etc/nsswitch.conf
	  change from hosts:   files dns
	  hosts:	files resolve dns


```


here are my tests

```

wbinfo -u
Error looking up domain users

```


```

resolvectl status
Global
       Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub

Link 8 (bond0)
    Current Scopes: DNS
         Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 172.16.22.20
       DNS Servers: 172.16.22.20 172.16.2.20
        DNS Domain: DOMAIN.ca


```


```

root@ho-sm-sto-00:~# smbclient -L dc0-2.DOMAIN.ca -U dmackenzieadm
lpcfg_do_global_parameter: WARNING: The "idmap backend" option is deprecated
Unknown parameter encountered: "windbind enum groups"
Ignoring unknown parameter "windbind enum groups"
Unknown parameter encountered: "windbind enum users"
Ignoring unknown parameter "windbind enum users"
Password for [DOMAIN\dmackenzieadm]:


        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        NETLOGON        Disk      Logon server share
        reports         Disk
        SYSVOL          Disk      Logon server share
SMB1 disabled -- no workgroup available



```




```

ctdb status
Number of nodes:3
pnn:0 172.16.22.40     OK (THIS NODE)
pnn:1 172.16.22.41     OK
pnn:2 172.16.22.42     OK
Generation:473124237
Size:3
hash:0 lmaster:0
hash:1 lmaster:1
hash:2 lmaster:2
Recovery mode:NORMAL (0)
Recovery master:1
root@ho-sm-sto-00:~#



```

Checking AD i see the 3 machines all joined and showing in the computers OU
I can ping the Public IP Address Specified in /etc/ctdb/public_addresses

---

### Post by thetravelingsandwich on 2022-12-03
I was under the impression from seeing other threads that specifying "netbios name = ho-sm-storage" in the smb.conf should join the domain using this name and then there i 0 worry if one of the machines fails as CTDB pickups the config and continues on as if nothing has happened.

---

### Post by MAFoElffen on 2022-12-05
Please explain more on this in /etc/samba/smb.conf:
```

# enabling this breaks ctdb from starting samba security = ADS

```
...because with mine, if I don't have that, then I get an error trying to join, saying it's not member server...

---

### Post by thetravelingsandwich on 2022-12-06
ok i think i got it mostly working now except for the kerbos things.
I blew away all 3 nodes and started over.
I was probably forgetting to change the ctdb file and it was trying to start samba or windbind and failing.
Below is my config that is working for the initial issue.
zfs settings we untouched
glusterfs i changed the following:
```

sudo mkdir /mnt/gluster/sys
sudo gluster volume create sys replica 3 transport tcp HO-SM-Sto-00:/mnt/gluster/sys/ HO-SM-Sto-01:/mnt/gluster/sys/ HO-SM-Sto-02:/mnt/gluster/sys/ force
sudo gluster volume start sys
sudo mkdir /mnt/glusterfs/sys
sudo mkdir /mnt/glusterfs/sys/ctdb
sudo mkdir /mnt/glusterfs/sys/samba
sudo mount -t glusterfs ho-sm-sto-00:/sys /mnt/glusterfs/sys

```

Fstab
```

echo "ho-sm-sto-00:sys /mnt/glusterfs/sys glusterfs defaults,_netdev 0 0" >>/etc/fstab

```

Setup DNS
```

vi /etc/systemd/resolved.conf
	DNS=172.16.2.20 172.16.2.21 172.16.22.20 172.16.22.21
	Domains=DOMAIN.CA
	DNSStubListener=yes

```

Make Director for keytab File
```

	mkdir /mnt/glusterfs/sys/krb5

```

SAMBA
```

	vi /mnt/glusterfs/sys/samba/smb.conf
		under global add the following lines
			[global]	
				netbios name = ho-sm-storage
				clustering = yes
				workgroup = DOMAIN
				realm = DOMAIN.CA
			Uncomment line after joining domain	
			#	Security = ADS
				server role = member server
				kerberos method = secrets and keytab
				dedicated keytab file = /mnt/glusterfs/sys/krb5/krb5.keytab
				max log size = 50
				log file = /var/log/samba/%m.log
				client signing = yes
				client use spnego = yes	
				idmap config * : backend = tdb2
				idmap config * : range = 10000-19999
			# idmap config DOMAIN is for domain users
				idmap config DOMAIN : backend = rid
				idmap config DOMAIN : range = 100000-1999999
			# include = registry
				vfs objects = gpfs fileid acl_xattr
				gpfs:sharemodes = yes
				fileid:algorithm = fsname
				windbind enum groups = yes
				windbind enum users = yes
				winbind separator = +
			# important for windows ACL use
				ea support = yes
				map acl inherit = yes
				store dos attributes = yes
				inherit acls = yes
				inherit permissions = yes
				encrypt passwords = yes
				password server = *
			[Archive]
				comment = Highly available share for Archive Data
				path = /mnt/glusterfs/Archive
				readonly = no
				writable = yes
				browsable = yes
				inherit acls = yes
			[Prod]
				comment = Highly available share for Production Data
				path = /mnt/glusterfs/Prod
				readonly = no
				writable = yes
				browsable = yes
				inherit acls = yes

```


Setup Kerberos config
```

	vi /mnt/glusterfs/sys/krb5/krb5.conf
	[logging]
	default = FILE:/var/log/ktb5libs.log
	kdc = FILE:/var/log/krb5kdc.log
	admin_server = FILE:/var/log/kadmind.log
	[libdefaults]
	default_realm = DOMAIN.CA
	dns_lookup_realm = true
	dns_lookup_kdc = true
	ticket_lifetime = 24h
	renew_lifetime = 7d
	forwardable = true
	[realms]
		DOMAIN.CA = {
				kdc = dc0-2.domain.ca
				kdc = dc1.domain.ca
				kdc = dc2.domain.ca
				kdc = dc4-2.domain.ca
				admin_server = dc0-2.domain.ca
	}
	[domain_realm]
	.domain.ca = DOMAIN.CA
	domain.ca = DOMAIN.CA

```

Edit Name Switch Service
```

	vi /mnt/glusterfs/sys/nsswitch.conf
	passwd: files sss
	# testing passwd: files sss winbind
	shadow: files sss
	# testing group: files sss winbind
	group: files sss


	hosts: files dns
	networks: files
	
	bootparams: files
	ethers: files
	netmasks: files
	
	protocols: files
	rpc: files
	services: files sss


	netgroup: files sss
	publickey: files


	automount: files sss
	aliases: files
	sudoers : files sss


```

Setup Kerbos
```

	kinit dmackenzieadm

```


Make sure ubuntu can see the domain
```

	realm -v discover domain.ca

```


Try join with Kerbos if this fails go to next step
```

	net ads join -n ho-sm-storage -U dmackenzieadm -k
	net ads join -n ho-sm-storage -U dmackenzieadm
	net ads keytab add cifs -U dmackenzieadm
	realm join domain.ca --computer-name ho-sm-storage -U dmackenziead

```

Edit CTDB and restart service
```

	vi /mnt/glusterfs/sys/ctdb/ctdb.conf
	CTDB_MANAGES_WINDBIND=yes

```


Edit Samba config
```

	vi /mnt/glusterfs/sys/samba/smb.conf
	Uncomment line
			Security = ADS
	sudo systemctl restart ctdb

```


Now check to make sure that it can pull AD information
```

	getent passwd donald.mackenzie@domain.ca
	smbclient -L dc0-2.domain.ca -U dmackenzieadm


```

Edit SSSD File to allow non fqdn names
```

	vi /etc/sssd/sssd.conf
	use_fully_qualified_names = False

```

---

