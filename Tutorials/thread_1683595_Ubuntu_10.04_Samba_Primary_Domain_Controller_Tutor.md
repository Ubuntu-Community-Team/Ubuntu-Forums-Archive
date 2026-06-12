---
title: "Ubuntu 10.04 Samba Primary Domain Controller Tutorial"
date: 2011-02-07
forum: Tutorials
---

### Post by Fooshnik on 2011-02-07
[COLOR=#000000][COLOR=#000000]This tutorial is taken from Bulltext’s and elsewhere, and includes a DNS server, time synch, Webmin, OpenSSH, etc. It has been tested to work on both 32-bit and 64-bit installations. By default it comes with roaming profiles enabled. 

Throughout this you need to be consistent in replacing “[COLOR=#3333EE]myserver[/COLOR]” with the name of your server, “[COLOR=#ff0000]mydomain[/COLOR]” with the name of your domain, and “[COLOR=#ff00ff]PassWD55[/COLOR]” with your password. These need to be the same in all places. The text in green is typically something that needs to be typed or entered into forms. The best way to customize this to suit your needs my be to paste this tutorial into Writer or Word and use the replace function to replace [COLOR=#3333EE]myserver[/COLOR], [COLOR=#ff0000]mydomain[/COLOR], and [COLOR=#ff00ff]PassWD55 [/COLOR]respectively with what you're going to use. This is taken from my own notes, thus the colors, to help see all the places that need changing.[/COLOR]

[COLOR=#000000]The options I used at install were:[/COLOR] 

[COLOR=#000000]For hostname put in the name you’re going to use for your server. In this tutorial I used “[COLOR=#3333EE]myserver[/COLOR]”. At the partition editor I highly recommend configuring a partition for the OS and a partition for user data. This will enable you to backup your server configuration much easier than if they were mushed together. I configured a root partition of 6gb, a swap of 2gb (use the amount of RAM you have, or double the amount of RAM if your server’s going to get heavy use), then use the remainder of the drive mounted at /home. Size them as needed, if you're going to be running a database or something you'll need a larger root partition or different structure. For username I used “[COLOR=#009900]sysadmin[/COLOR]”, password I used “[COLOR=#ff00ff]PassWD55[/COLOR]”. No automatic updates. Don’t install any extra software. When done remove the CD and reboot.[/COLOR] 
[/COLOR][COLOR=#000000][COLOR=#000000][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]1. Login as sysadmin then give root a password:[/COLOR] [/COLOR]

[COLOR=#008000][/COLOR] 
[COLOR=#008000]sudo passwd root[/COLOR] 
[COLOR=#ff00ff]PassWD55[/COLOR] 
[COLOR=#000000][/COLOR] 
[COLOR=#000000]Logout and log back in as root.[/COLOR] 

2. Optional: install the GUI. Having the GUI available on the server can make it easier to step through this guide. Here I'm assuming your server received an IP address via DHCP or you already configured a static IP.  You can perform most tasks here using Webmin and PuTTY if you don’t want to install the GUI. 
[COLOR=#008000][/COLOR] 
[COLOR=#008000]apt-get update[/COLOR] 
[COLOR=#008000]apt-get install ubuntu-desktop[/COLOR] 
[COLOR=#008000]reboot[/COLOR] 
 
 
[COLOR=#000000]3. Remove splash screen and GUI startup. Login as root then open a terminal window[/COLOR] 
[COLOR=#008000][/COLOR] 
[COLOR=#008000]mv /etc/init/gdm.conf /etc/init/gdm.conf.nostart[/COLOR] 
[COLOR=#008000]cp /etc/default/grub /etc/default/grub.bak[/COLOR] 
[COLOR=#008000]nano /etc/default/grub[/COLOR] 
[COLOR=#3333EE][/COLOR] 
[COLOR=#3333EE][COLOR=#000000]change line to: [/COLOR][COLOR=#008000]GRUB_CMDLINE_LINUX_DEFAULT=""[/COLOR][/COLOR] 
[COLOR=#008000][/COLOR] 
[COLOR=#008000]update-grub[/COLOR] 
[COLOR=#008000]reboot[/COLOR] 

[COLOR=#000000]Sometimes after this reboot you don't get a login prompt, this seems to be a bug that gets fixed by the next boot. Hit alt-F1, login as root, and enter the GUI with[/COLOR] 
[COLOR=#008000][/COLOR] 
[COLOR=#008000]startx[/COLOR] 
[COLOR=#000000][/COLOR]

4. Install OpenSSH Server, you may wish to use this to step through the tutorial. Download PuTTY to access the server from Windows. 
 
[COLOR=#006600]apt-get install openssh-server[/COLOR] 
[COLOR=#000000]

5. Install Webmin. Get the current link for the Debian package from Webmin.com. Right now its:[/COLOR] 
[COLOR=#006600]```
wget http://downloads.sourceforge.net/project/webadmin/webmin/1.530/webmin_1.530_all.deb?r=http://www.webmin.com -O webmin_1.530_all.deb
```[/COLOR]
[COLOR=#008000]dpkg -i webmin_1.530_all.deb[/COLOR] 
[COLOR=#008000][/COLOR]
[COLOR=#000000]If this times out, get it directly from webmin.com. If you get a dependency error try [/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000][COLOR=#006600]apt-get install -f[/COLOR][/COLOR] 
 
 
[COLOR=#000000]6. Configure a static IP address. You can either navigate to [https://localhost:10000](https://localhost:10000/) from the server GUI, login as root and go to Networking> Network Configuration> Network Interfaces> eth0. Change the IP as needed. 

or [/COLOR]
 
[COLOR=#006600]nano /etc/network/interfaces[/COLOR] 
[COLOR=#000000][/COLOR] 
[COLOR=#000000]Change text under "The primary network interface" to (change IP to suit your network):[/COLOR] 
[COLOR=#008000][/COLOR] 
[COLOR=#008000]auto eth0 
iface eth0 inet static 
address 10.0.1.110 
netmask 255.255.255.0 
gateway 10.0.1.100[/COLOR] 
 
Then:
 
[COLOR=#006600]/etc/init.d/networking restart[/COLOR] 
 
[COLOR=#000000]Check your IP is set correctly[/COLOR] 
[COLOR=#006600][/COLOR] 
[COLOR=#006600]ifconfig[/COLOR] 
[COLOR=#000000][COLOR=#006600]ping 10.0.1.100 [/COLOR](ping your gateway)[/COLOR] 
[COLOR=#006600]ping google.com[/COLOR] 


[COLOR=#000000]7. Configure A Fully Qualified Domain Name[/COLOR] 
 
[COLOR=#006600]nano /etc/hosts[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600]127.0.0.1    localhost[/COLOR] 
[COLOR=#3333EE][COLOR=#006600]127.0.1.1    [/COLOR][COLOR=#3333EE]myserver  [/COLOR][COLOR=#3333EE]myserver[/COLOR][COLOR=#006600].[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#000000]leave other lines the same[/COLOR] 
[COLOR=#000000]
[/COLOR][COLOR=#006600]nano /etc/hostname[/COLOR] 

[COLOR=#3333EE][COLOR=#3333EE]myserver[/COLOR][COLOR=#006600].[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][/COLOR] 
 
 
[COLOR=#000000]8. Since we're going to sync workstations to server time, we want the server to have correct time[/COLOR] 
 
[COLOR=#006600]apt-get install ntp[/COLOR] 
[COLOR=#006600]nano /etc/ntp.conf[/COLOR] 
 
[COLOR=#3333EE][COLOR=#000000]Add "[/COLOR][COLOR=#008000]server pool.ntp.org[/COLOR][COLOR=#000000]" above "[/COLOR][COLOR=#008000]server ntp.ubuntu.com[/COLOR][COLOR=#000000]".[/COLOR][/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#000000]9. Install and configure the DNS server. This is simplest to do with Webmin.[/COLOR]
 
[COLOR=#006600]apt-get install bind9[/COLOR] 
 
[COLOR=#000000]navigate to: [https://10.0.1.110:10000](https://192.168.0.60:10000/) (Use the IP address you assigned to your server.)[/COLOR] 
 
[COLOR=#3333EE][COLOR=#000000]Login as "root" and "[/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][COLOR=#000000]"[/COLOR][COLOR=#006600] 
[/COLOR][COLOR=#000000]Under Servers or Un-used Modules find BIND DNS Server 
Under "Existing DNS Zones" click "Create master zone" 
Enter in the following information:[/COLOR][/COLOR] 
[COLOR=#000000]Zone type: Forward (Names to Addresses)[/COLOR] 
[COLOR=#3333EE][COLOR=#000000]Domain name / Network: [/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][/COLOR] 
[COLOR=#000000]Records file: Automatic[/COLOR] 
[COLOR=#3333EE][COLOR=#000000]Master server: [/COLOR][COLOR=#3333EE]myserver[/COLOR][COLOR=#006600].[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][/COLOR] 
[COLOR=#3333EE][COLOR=#000000]Email address: [EMAIL=sysadmin@mydomain.local]sysadmin@[COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][/EMAIL][/COLOR][/COLOR]
[COLOR=#000000]Click "Create" button 
Click "Address (0)" at the top[/COLOR] 
[COLOR=#000000]Fill in with this information (customize to your needs):[/COLOR] 
[COLOR=#3333EE][COLOR=#000000]Name: [/COLOR][COLOR=#3333EE]myserver[/COLOR][COLOR=#006600].[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][/COLOR] 
[COLOR=#000000]Address: 10.0.1.110 (Use the IP address of your server)[/COLOR] 
[COLOR=#000000]Click "Create" button[/COLOR] 
[COLOR=#3333EE][COLOR=#000000]Name: [/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][/COLOR] 
[COLOR=#000000]Address: 10.0.1.110 (use the IP address of your server)[/COLOR] 
[COLOR=#000000]Click "Create" button[/COLOR] 
[COLOR=#000000]Click "Return to record types"[/COLOR] 
[COLOR=#000000]Click "Apply Zone" button[/COLOR] 
[COLOR=#000000]Click "Apply Configuration"[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600]cp /etc/resolv.conf /etc/resolv.conf.original[/COLOR] 
[COLOR=#006600]nano /etc/resolv.conf[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#000000]Edit the file so that the only lines in the file are the following:[/COLOR] 
 
[COLOR=#3333EE][COLOR=#006600]search[/COLOR] [COLOR=#ff0000]mydomain[/COLOR][COLOR=#008000].local[/COLOR][/COLOR] 
[COLOR=#006600]nameserver 10.0.1.110[/COLOR] 
 
[COLOR=#000000]then[/COLOR] 
 
[COLOR=#006600]reboot[/COLOR] 
 
[COLOR=#000000]Make sure you can still ping google[/COLOR] 
 
[COLOR=#006600]ping google.com[/COLOR] 
 
 
[COLOR=#000000]10. 
[COLOR=#006600]apt-get update 
apt-get dist-upgrade[/COLOR] 

At this point I recommend imaging the sda1 partition using a utility like Ghost 4 Linux. This will allow you to return to this point in a few minutes in case the below fails (on an old laptop it was about 5 minutes to restore a 6GB partition). One error this doesn’t work and it's difficult to determine why.[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600]...[/COLOR] 
[COLOR=#000000]11.[/COLOR] 
[COLOR=#3333EE][COLOR=#006600]apt-get install slapd ldap-utils
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif[/COLOR][/COLOR]
 
 
[COLOR=#000000]12. You will need to modify the following to include your password and domain name. [/COLOR]

[COLOR=#006600][/COLOR]
[COLOR=#006600]nano backend.ldif[/COLOR]

[COLOR=#000000]Add:[/COLOR]

```
dn: cn=module,cn=config
objectClass: olcModuleList
cn: module
olcModulepath: /usr/lib/ldap
olcModuleload: back_hdb

dn: olcDatabase=hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcSuffix: dc=[COLOR="Red"]mydomain[/COLOR],dc=local
olcDbDirectory: /var/lib/ldap
olcRootDN: cn=admin,dc=[COLOR="Red"]mydomain[/COLOR],dc=local
olcRootPW: [COLOR="Magenta"]PassWD55[/COLOR]
olcDbConfig: set_cachesize 0 2097152 0
olcDbConfig: set_lk_max_objects 1500
olcDbConfig: set_lk_max_locks 1500
olcDbConfig: set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcAccess: to attrs=userPassword by dn="cn=admin,dc=[COLOR="Red"]mydomain[/COLOR],dc=local" write by anonymous auth by self write by * none
olcAccess: to attrs=shadowLastChange by self write by * read
olcAccess: to dn.base="" by * read
olcAccess: to * by dn="cn=admin,dc=[COLOR="red"]mydomain[/COLOR],dc=local" write by * read

```
 
[COLOR=#000000]Then[/COLOR]
 
[COLOR=#000000][COLOR=#006600]ldapadd -Y EXTERNAL -H ldapi:/// -f backend.ldif[/COLOR][/COLOR]
 
 
[COLOR=#000000]13. Install Samba[/COLOR] 
 
[COLOR=#3333EE][COLOR=#006600]apt-get install samba samba-doc libpam-smbpass smbclient smbldap-tools[/COLOR][COLOR=#000000]

Here is the smb.conf I use. The parts you need to edit are near the top. Where it shows “Workgroup”, use what you’ve been using for “[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#000000]”. For “Netbios Name”, use what you’ve been using for “[/COLOR][COLOR=#3333EE]myserver[/COLOR][COLOR=#000000]”. Also change the lines “LDAP Suffix and “LDAP Admin”. Specify a user to be Samba admin if you want. Leave “Logon Path” as is for roaming profiles, or change to “logon path =” for no roaming profiles.[/COLOR][/COLOR] 
[COLOR=#000000][/COLOR]
[COLOR=#006600]nano smb.conf[/COLOR]
 

```
[global]

#  Customize these entries as needed
#  Replace with your domain name
	workgroup = [COLOR="red"]mydomain[/COLOR]

#  Replace with your server name
	netbios name = [COLOR=#3333EE]myserver[/COLOR]

#  Replace "mydomain" with the workgroup name you're using
	ldap suffix = dc=[COLOR="Red"]mydomain[/COLOR],dc=local
	ldap admin dn = cn=admin,dc=[COLOR="red"]mydomain[/COLOR],dc=local

#  Roaming profiles enabled. Replace "myserver" to match your netbios name
	logon path = \\[COLOR=#3333EE]myserver[/COLOR]\profiles\%U\%a
#  No roaming profiles, uncomment
;	logon path =

	
#  Server Information
	server string = SMB Server


#  Specify global admin user, will have root in all shares
;	admin users = 


#  PW Backend
	obey pam restrictions = Yes
	unix password sync = no
	ldap passwd sync = yes
	passdb backend = ldapsam:ldap://localhost
	pam password change = Yes


#  SMBLDAP Scripts
	add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
	add user script = /usr/sbin/smbldap-useradd -m '%u'
	add machine script = /usr/sbin/smbldap-useradd -w '%u'
	add group script = /usr/sbin/smbldap-groupadd -p '%g'
	delete group script = /usr/sbin/smbldap-groupdel '%g'
	delete user script = /usr/sbin/smbldap-userdel %u
	delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
	set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'


#  LDAP Configuration
	ldap ssl = no
	ldap user suffix = ou=Users
	ldap machine suffix = ou=Computers
	ldap group suffix = ou=Groups
	ldap idmap suffix = ou=Idmap


#  Logon script located in netlogon share. Individual logon scripts uncomment
	;logon script = %U.bat
	logon script = allusers.bat


#  Logging
	max log size = 1000
	syslog = 0
	log file = /var/log/samba/log.%m


#  Printing
	printing = cups
	printcap name = cups
	load printers = yes


# Domain Controller
	domain master = Yes
	domain logons = Yes
	wins support = true
	os level = 35
	server signing = auto
	server schannel = Auto
	panic action = /usr/share/samba/panic-action %d
	dns proxy = No
;	logon drive = H:
;	logon home = \\%N\%U


# Allow file permissions change to group members
	acl group control = yes


# Inherit permissions from parent
; 	inherit acls = yes
; 	inherit owner = yes
;	map acl inherit = yes
; 	inherit permissions = yes


# Do NOT inherit permissions from parent
	inherit acls = no
	inherit owner = no
	map acl inherit = no
	inherit permissions = no


# Do not show files that are unreadable
	hide unreadable = yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   browseable = no
# to allow user 'guest account' to print.
   guest ok = yes
   writable = no
   printable = yes
   create mode = 0700

[Home]
	security mask = 0770
	writeable = yes
	path = /home/userhome
	force security mode = 0
	force directory security mode = 0
	directory security mask = 0770

[netlogon]
	comment = Network Logon Service
	writeable = yes
	public = yes
	path = /home/netlogon

[profiles]
	browseable = no
	printable = no
	writable = yes
	path = /home/profiles
	store dos attributes = no
	guest ok = no
	comment = Users Profiles
# fixes everyone having read
	create mode = 0700
	directory mode = 0700


```
[COLOR=#000000]


[COLOR=#006600]
[/COLOR]Once you modified the values type:[/COLOR]

[COLOR=#000000][COLOR=#006600]cp /etc/samba/smb.conf /etc/samba/smb.conf.original[/COLOR]
[COLOR=#006600]cp -rf smb.conf /etc/samba/smb.conf[/COLOR][/COLOR]


[COLOR=#000000]Everytime you edit your smb.conf you should:[/COLOR] 
[COLOR=#006600]testparm /etc/samba/smb.conf[/COLOR]

[COLOR=#000000]If you see an rlimit_max: error you can ignore it.[/COLOR] 
 
 
[COLOR=#000000]14.[/COLOR] 
[COLOR=#006600]smbpasswd -W[/COLOR]
 
[COLOR=#3333EE][COLOR=#000000]Enter the same password you’ve been using for “[/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][COLOR=#000000]”[/COLOR][/COLOR] 
 
[COLOR=#006600]service smbd restart[/COLOR]
[COLOR=#006600]smbclient -L localhost[/COLOR]
 
[COLOR=#000000]Hit enter, **do not type in password**. This should show your server/workgroup information without error.[/COLOR] 
 
[COLOR=#000000][COLOR=#006600]mkdir -v -m 1777 /home/profiles[/COLOR] 
[COLOR=#006600]mkdir -v -m 1777 /home/netlogon[/COLOR][/COLOR]
 
 
[COLOR=#000000]15.[/COLOR] 
[COLOR=#006600]cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap/schema/[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#006600]gzip -d /etc/ldap/schema/samba.schema.gz[/COLOR]
[COLOR=#006600]nano schema_convert.conf[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]insert:[/COLOR] ```
include /etc/ldap/schema/core.schema
include /etc/ldap/schema/collective.schema
include /etc/ldap/schema/corba.schema
include /etc/ldap/schema/cosine.schema
include /etc/ldap/schema/duaconf.schema
include /etc/ldap/schema/dyngroup.schema
include /etc/ldap/schema/inetorgperson.schema
include /etc/ldap/schema/java.schema
include /etc/ldap/schema/misc.schema
include /etc/ldap/schema/nis.schema
include /etc/ldap/schema/openldap.schema
include /etc/ldap/schema/ppolicy.schema
include /etc/ldap/schema/samba.schema
```Then:
 
[COLOR=#006600]mkdir /tmp/ldif_output[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#000000]All one line:[/COLOR]
 
[COLOR=#006600]slapcat -f schema_convert.conf -F /tmp/ldif_output -n0 -s "cn={12}samba,cn=schema,cn=config" > /tmp/schema_samba.ldif[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#006600]nano /tmp/schema_samba.ldif[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#000000]At the top, edit[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]dn: cn{12}=samba,cn=schema,cn=config[/COLOR] 
[COLOR=#000000][/COLOR] 
[COLOR=#000000]to show[/COLOR] 
[COLOR=#006600][/COLOR] 
[COLOR=#006600]dn: cn=samba,cn=schema,cn=config[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000]Edit[/COLOR] 
[COLOR=#000000][/COLOR] 
[COLOR=#000000]cn: {12}samba[/COLOR] 
[COLOR=#000000][/COLOR] 
[COLOR=#000000]to show[/COLOR] 
[COLOR=#006600][/COLOR] 
[COLOR=#006600]cn: samba[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000]Delete the following from the end:[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#000000]structuralObjectClass: olcSchemaConfig 
entryUUID: b53b75ca-083f-102d-9fff-2f64fd123c95 
creatorsName: cn=config 
createTimestamp: 20080827045234Z 
entryCSN: 20080827045234.341425Z#000000#000#000000 
modifiersName: cn=config 
modifyTimestamp: 20080827045234Z[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600][/COLOR] 
[COLOR=#006600]ldapadd -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f /tmp/schema_samba.ldif[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#3333EE][COLOR=#000000]Enter Password “[/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][COLOR=#000000]”, or the same one you’ve been using.[/COLOR][/COLOR] 
[COLOR=#000000][/COLOR]
[COLOR=#006600]nano samba_indexes.ldif[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#000000]Enter:[/COLOR] ```
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcDbIndex
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq,pres,sub
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub
```[COLOR=#000000]Then[/COLOR] 
[COLOR=#006600][/COLOR] 
[COLOR=#006600]ldapmodify -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f samba_indexes.ldif[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000]Enter Password “[COLOR=#ff00ff]PassWD55[/COLOR]”, or the same one you’ve been using.[/COLOR] 
[COLOR=#000000][/COLOR]
[COLOR=#000000][/COLOR] 
 
[COLOR=#000000]16. The following should execute without error:[/COLOR] 
[COLOR=#000000][/COLOR]
[COLOR=#006600]ldapsearch -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -b cn=config -W olcDatabase={1}hdb[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]Enter Password “[COLOR=#ff00ff]PassWD55[/COLOR]”, or the same one you’ve been using.[/COLOR] 
[COLOR=#000000]Verify olcSuffix:, olcAccess:, olcAccess:, olcRootDN:, olcRootPW:.[/COLOR] 
[COLOR=#000000][/COLOR]
[COLOR=#006600]net getlocalsid[/COLOR]
 
[COLOR=#000000]Should run without error and look similar to[/COLOR] 
[COLOR=#000000]SID for domain MYSERVER is: S-1-5-21-2159403287-619955039-1086301409[/COLOR] 
 
 
[COLOR=#000000]17.[/COLOR] 
[COLOR=#006600]gzip -d /usr/share/doc/smbldap-tools/configure.pl.gz[/COLOR]
[COLOR=#006600]perl /usr/share/doc/smbldap-tools/configure.pl[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#000000]Here hit Enter at all times except:[/COLOR] 
[COLOR=#000000]"Logon Home", put a “.” (period without quotes)[/COLOR] 
[COLOR=#000000]"Logon Path", put a "."[/COLOR] 
[COLOR=#3333EE][COLOR=#000000]Default passwd validation time, I put [/COLOR][COLOR=#006600]3650[/COLOR][/COLOR] 
[COLOR=#3333EE][COLOR=#000000]When prompted for password, use your password or “[/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][COLOR=#000000]”.[/COLOR][/COLOR] 

Then:

[COLOR=#006600]smbldap-populate[/COLOR]
 
[COLOR=#000000]Enter Password “[COLOR=#ff00ff]PassWD55[/COLOR]”, or the same one you’ve been using.[/COLOR] 
 
 
[COLOR=#000000]18. Move the home directory so personal data doesn’t fill mix with the shared folders.[/COLOR]
 
[COLOR=#006600]mkdir -v /home/userhome[/COLOR]
[COLOR=#006600]cp /etc/smbldap-tools/smbldap.conf /etc/smbldap-tools/smbldap.conf.original[/COLOR]
[COLOR=#006600]nano /etc/smbldap-tools/smbldap.conf[/COLOR]
 
[COLOR=#3333EE][COLOR=#000000]Locate and change to: [/COLOR][COLOR=#006600]userHome="/home/userhome/%U"[/COLOR][/COLOR] 

Then:
 
[COLOR=#3333EE][COLOR=#006600]/etc/init.d/slapd stop
slapindex
chown openldap:openldap /var/lib/ldap/*
/etc/init.d/slapd start[/COLOR][/COLOR]
[COLOR=#006600]smbldap-groupmod -m 'root' 'Administrators'[/COLOR]
 
 
[COLOR=#000000]19.[/COLOR] 
[COLOR=#3333EE][COLOR=#006600]apt-get --yes install ldap-auth-client[/COLOR][/COLOR]
 
For LDAP server Uniform Resource Identifier, leave it as it is "ldapi:///" 
[COLOR=#3333EE][COLOR=#000000]For Distinguished name of the search base, put[/COLOR][/COLOR][COLOR=#3333EE][COLOR=#000000] [/COLOR][/COLOR][COLOR=#000000]"[/COLOR][COLOR=#006600]dc=[/COLOR][COLOR=#3333EE][COLOR=#ff0000]mydomain[/COLOR][/COLOR][COLOR=#006600],dc=local[/COLOR][COLOR=#000000]"[/COLOR] 
For LDAP account for root, put[COLOR=#3333EE][COLOR=#000000] [/COLOR][/COLOR][COLOR=#000000]"[/COLOR][COLOR=#006600]cn=admin,dc=[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600],dc=local[/COLOR][COLOR=#000000]"[/COLOR] 
[COLOR=#3333EE][COLOR=#000000]When it asks for LDAP password use "[/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][COLOR=#000000]" or the pw you’ve been using.[/COLOR][/COLOR] 

[COLOR=#3333EE][/COLOR]
[COLOR=#3333EE][COLOR=#000000]Use "[/COLOR][COLOR=#006600]dpkg-reconfigure ldap-auth-config[/COLOR][COLOR=#000000]"[/COLOR][COLOR=#006600] [/COLOR][COLOR=#000000]if you make a mistake. [/COLOR][/COLOR]
 
[COLOR=#000000]Then[/COLOR] 
 
[COLOR=#006600]auth-client-config -t nss -p lac_ldap[/COLOR]

[COLOR=#006600][/COLOR]
[COLOR=#3333EE][COLOR=#000000]20. 
[/COLOR][COLOR=#006600]pam-auth-update ldap[/COLOR][/COLOR]
 
[COLOR=#000000]Make sure there’s an asterisk next to all listed.[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600]getent group[/COLOR]
 
[COLOR=#000000]Should show similar to:[/COLOR] 
[COLOR=#000000]Domain Admins:*:512:root 
Domain Users:*:513: 
Domain Guests:*:514: 
Domain Computers:*:515: 
Administrators:*:544:root 
Account Operators:*:548: 
Print Operators:*:550: 
Backup Operators:*:551: 
Replicators:*:552:[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600]reboot[/COLOR] 

[COLOR=#006600][/COLOR]
[COLOR=#000000]21. See if it lives. Add a user:[/COLOR]
 
[COLOR=#006600]smbldap-useradd -a -m -P test[/COLOR]
[COLOR=#006600]smbldap-groupmod -m test 'Domain Admins'[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#3333EE][COLOR=#000000]On a Windows 7 workstation, go to Control Panel> System> for Computer Name click Change Settings> Change> member of Domain, enter “[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#000000]” or the domain you’ve been using (ONLY the name of your domain, do not enter [/COLOR][COLOR=#3333EE]myserver[/COLOR][COLOR=#006600].[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local[/COLOR][COLOR=#000000])> when prompted for username enter “root”, pw enter “[/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][COLOR=#000000]”, you may receive a DNS error, ignore it, click OK a few times then reboot Windows. Try to login as “Test”. Note: Sometimes after switching domains Windows will come up still configured to log into the local workstation. You may have to manually tell it to log into the domain.[/COLOR][/COLOR] 
[COLOR=#000000][/COLOR]
[COLOR=#000000]If you have a working domain, now would be a good time to image/backup the sda1 partition.[/COLOR] 

[COLOR=#006600][/COLOR]
[COLOR=#3333EE][COLOR=#000000]22.[/COLOR][COLOR=#006600] [/COLOR][COLOR=#000000]Enable ACL for the home partition. This will allow for much more granularity and flexibility when setting file permissions.[/COLOR][/COLOR]
 
[COLOR=#006600]apt-get install acl[/COLOR]
[COLOR=#006600]cp /etc/fstab /etc/fstab.original[/COLOR]
[COLOR=#006600]nano /etc/fstab[/COLOR]
 
[COLOR=#3333EE][COLOR=#000000]change the /home mount so it says "[/COLOR][COLOR=#006600]defaults,acl[/COLOR][COLOR=#000000]" instead of "defaults"[/COLOR][/COLOR]
 
[COLOR=#006600]reboot[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#000000]Test it:[/COLOR]
 
[COLOR=#006600]mkdir -v /home/mp3[/COLOR]
[COLOR=#006600]setfacl -R -m u:test:rwx /home/mp3[/COLOR]
[COLOR=#006600]setfacl -R -d -m u:test:rwx /home/mp3[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#006600]getfacl /home/mp3[/COLOR]
[COLOR=#006600][/COLOR]
[COLOR=#000000]Should show [/COLOR]
[COLOR=#000000]# file: home/mp3[/COLOR] 
[COLOR=#000000]# owner: root[/COLOR] 
[COLOR=#000000]# group: root[/COLOR] 
[COLOR=#000000]user::rwx[/COLOR] 
[COLOR=#000000]user:test:rwx[/COLOR] 
[COLOR=#000000]group::r-x[/COLOR] 
[COLOR=#000000]mask::rwx[/COLOR] 
[COLOR=#000000]other::r-x[/COLOR] 
[COLOR=#000000]default:user::rwx[/COLOR] 
[COLOR=#000000]default:user:test:rwx[/COLOR] 
[COLOR=#000000]default:group::r-x[/COLOR] 
[COLOR=#000000]default:mask::rwx[/COLOR] 
[COLOR=#000000]default:other::r-x[/COLOR] 

[COLOR=#000000]You should now be able to modify file/folder properties using Windows Explorer. Right-click the file, Properties> Security> Advanced. Note that Windows and POSIX permissions do not map identically, but this configuration is still more flexible than stock. [/COLOR]


[COLOR=#3333EE][COLOR=#000000]23. Add a logon script. The sample smb.conf is configured with one logon script for all users, to change to individual logon scripts change line to “[/COLOR][COLOR=#006600]logon script = %U.bat[/COLOR][COLOR=#000000]” in smb.conf. This script will also sync workstation time to the server. NOTE: For a user designated as “Admin Users =” in smb.conf, you have to manually set the owner of their profile directory to that username in order for roaming profiles to work, by default files created by the samba admin are owned by root which messes with Windows.[/COLOR][/COLOR] 
[COLOR=#000000][/COLOR]
[COLOR=#006600]nano /home/netlogon/allusers.bat[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000]Enter the following text, replace [COLOR=#3333EE]myserver[/COLOR] with the name of your server:[/COLOR] 
[COLOR=#000000]
[COLOR=#006600]@echo off[/COLOR]
[COLOR=#006600]REM    # SYNC THE TIME WITH THE SERVER[/COLOR]
[COLOR=#006600]net time \\[/COLOR][COLOR=#3333EE]myserver[/COLOR][COLOR=#006600] /set /y[/COLOR]

[COLOR=#006600]REM    # MAP Home Drives[/COLOR]
[COLOR=#006600]net use x: /delete[/COLOR]
[COLOR=#006600]net use x: \\[COLOR=#3333EE]myserver[/COLOR][COLOR=#006600]\Home\%username%[/COLOR][/COLOR][COLOR=#000000][/COLOR][/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]Install flip to convert the file to something windows can use[/COLOR]
 
[COLOR=#006600]apt-get install flip[/COLOR]
[COLOR=#006600]flip -m /home/netlogon/allusers.bat[/COLOR]
 
 [COLOR=#000000]Miscellaneous:[/COLOR]
 
[COLOR=#000000]24. As a sample, create a user “mp3user”, make an MP3 group, add the user to the group, make a folder for MP3s, set Linux permissions for the MP3 directory, add the MP3 Samba share, add a mapped drive in the login script.[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#000000]Create the user:[/COLOR]
 
[COLOR=#006600]smbldap-useradd -a -m -P mp3user[/COLOR]
 
[COLOR=#000000]Add user to 'Domain Admins'. Optional - this makes user local admin on windows:[/COLOR]
 
[COLOR=#006600]smbldap-groupmod -m mp3user 'Domain Admins'[/COLOR]
 
[COLOR=#000000]Create the group:[/COLOR]
 
[COLOR=#006600]smbldap-groupadd -a MP3[/COLOR]
 
[COLOR=#000000]Add mp3user to the group:[/COLOR]
 
[COLOR=#006600]smbldap-groupmod -m mp3user 'MP3'[/COLOR]
 
[COLOR=#000000]Make the MP3 directory (note if you did the test above you already made this directory)[/COLOR]
 
[COLOR=#006600]mkdir -v /home/mp3[/COLOR]
 
[COLOR=#000000]Set permissions so group MP3 can access the mp3 folder:[/COLOR]
 
[COLOR=#006600]setfacl -m g:MP3:rwx /home/mp3 
setfacl -d -m g:MP3:rwx /home/mp3[/COLOR]
 
[COLOR=#000000]The first adds the group MP3, the second adds it as a default group so new files inherit that permission.[/COLOR]
 
[COLOR=#000000]Create the Samba share, open the smb.conf:[/COLOR]
 
[COLOR=#006600]nano /etc/samba/smb.conf[/COLOR]
 
[COLOR=#000000]Paste the following at the bottom of smb.conf:[/COLOR]
 
[COLOR=#006600][MP3] 
		writeable = yes 
		inherit permissions = yes 
		path = /home/mp3 
		force directory mode = 770 
		force create mode = 770 
		valid users = @MP3[/COLOR]
 
[COLOR=#000000]Note that you can also configure Samba using the Samba module in Webmin.[/COLOR] 

[COLOR=#000000][/COLOR]
[COLOR=#000000]Then:[/COLOR]
 
[COLOR=#006600]service smbd restart[/COLOR]
 
[COLOR=#000000]Add a map in the login script:[/COLOR]
 
[COLOR=#006600]nano /home/netlogon/allusers.bat[/COLOR]
 
[COLOR=#000000]Add the following:[/COLOR]
 
[COLOR=#000000][COLOR=#006600]REM    # MAP MP3 Drive[/COLOR] 
[COLOR=#006600]net use m: /delete[/COLOR]
[COLOR=#006600]net use m: \\[COLOR=#3333EE]myserver[/COLOR][COLOR=#006600]\MP3[/COLOR][/COLOR][/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000]then[/COLOR]
 
[COLOR=#006600]flip -m /home/netlogon/allusers.bat[/COLOR]
 
[COLOR=#000000]You should now be able to log in as mp3user and have a writable M:\ drive.[/COLOR]
 
 
[COLOR=#000000]25. Other command line options:[/COLOR] 

[COLOR=#000000]    * smbldap-groupadd - add a new group[/COLOR] 
[COLOR=#000000]    * smbldap-groupdel - delete a group[/COLOR] 
[COLOR=#000000]    * smbldap-groupmod - modify a group, including adding or removing members[/COLOR] 
[COLOR=#000000]    * smbldap-groupshow - show the properties of a group, including members[/COLOR] 
[COLOR=#000000]    * smbldap-passwd - change a user password[/COLOR] 
[COLOR=#000000]    * smbldap-populate - populate LDAP database[/COLOR] 
[COLOR=#000000]    * smbldap-useradd - add a new user account[/COLOR] 
[COLOR=#000000]    * smbldap-userdel - delete a user account[/COLOR] 
[COLOR=#000000]    * smbldap-userlist - list users and machines[/COLOR] 
[COLOR=#000000]    * smbldap-usershow - show information for one user account[/COLOR] 
[COLOR=#000000]    * smbldap-usermod - modify the Unix and Samba properties of a user account (many properties)[/COLOR] 
[COLOR=#000000]    * smbldap-userinfo - modify gecos information in a user account (only a few properties)[/COLOR] 
 
 
26. You can configure windows to use this server as a DNS, in fact this may be necessary on some workstations before you can join the domain. In Windows 7 go to Control Panel> Network and Sharing Center> for your Local Area Connection (or wireless connection), click View Status> Properties> Double-click Internet Protocol Version 4> Use the following DNS Server Addresses, enter the IP address of your server. Use [COLOR=#006600]ipconfig /all[/COLOR] to verify your change. You should then be able to [COLOR=#3333EE][COLOR=#006600]ping [/COLOR][COLOR=#660000][COLOR=#a0a0a0][COLOR=#3333EE]myserver[/COLOR][COLOR=#006600].[/COLOR][COLOR=#ff0000]mydomain[/COLOR][COLOR=#006600].local [/COLOR][COLOR=#000000] [/COLOR][/COLOR][/COLOR][/COLOR]and have this return your server's IP address. 
[COLOR=#660000][COLOR=#3333EE][COLOR=#a0a0a0][/COLOR][/COLOR][/COLOR]
[COLOR=#660000][COLOR=#3333EE][COLOR=#a0a0a0][/COLOR][/COLOR][/COLOR] 
[COLOR=#660000][COLOR=#3333EE][COLOR=#a0a0a0][COLOR=#000000]27. To browse your LDAP tree you can use [/COLOR][LDAP Admin](http://ldapadmin.sourceforge.net/download/ldapadmin.html).[COLOR=#000000] Make a new connection using the settings:[/COLOR][/COLOR][/COLOR][/COLOR]
[COLOR=#660000][COLOR=#3333EE][COLOR=#a0a0a0][/COLOR][/COLOR][/COLOR] 
[COLOR=#660000][COLOR=#3333EE][COLOR=#000000]Host: [/COLOR][COLOR=#006600][COLOR=#3333EE]myserver[/COLOR][/COLOR][/COLOR][/COLOR] 
Base: [COLOR=#006600]dc=[COLOR=#ff0000]mydomain[/COLOR],dc=local[/COLOR] 
Username:[COLOR=#006600] cn=admin,dc=[COLOR=#ff0000]mydomain[/COLOR],dc=local[/COLOR] 
Password:[COLOR=#3333EE][COLOR=#006600] [/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][/COLOR] 
You can also use [COLOR=#3333ff][PHPLDAPAdmin](http://phpldapadmin.sourceforge.net/wiki/index.php/Main_Page)[/COLOR] or the LDAP Server module in Webmin. 
 
 
[COLOR=#000000]28. Verify NTP is working[/COLOR] 
[COLOR=#006600][/COLOR]
[COLOR=#006600]ntpq -p[/COLOR]
 
[COLOR=#000000]Should show two servers, one with a * one with a +[/COLOR]
 
[COLOR=#006600]date[/COLOR]

[COLOR=#000000]Should show correct time. You can compare with time.gov.[/COLOR]
 
 
[COLOR=#000000]29. You can see this hotfix about the Windows 7 DNS error: [http://support.microsoft.com/kb/2171571](http://support.microsoft.com/kb/2171571)[/COLOR] 
[COLOR=#000000]The error will not affect anything except the error message itself.[/COLOR] 
 
 
[COLOR=#000000]30. Users added to the 'Domain Admins' group will automatically receive local admin permissions on a Windows workstation. If you want the user to have only user level permissions then do not add the user to the 'Domain Admins' group.[/COLOR] 
 
 
[COLOR=#000000]31. To always prompt for username and password at login instead of icons (and showing the last username logged in)[/COLOR] 
[COLOR=#000000]Click Start> Run>Secpol.msc> Local Policies> Security Options> Interactive Login: Do Not Display Last Username> Enabled.[/COLOR] 
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]32. You can backup your server config with [Ghost 4 Linux](http://sourceforge.net/projects/g4l/). DL, burn, boot, hit Enter a few times until you can type in G4L. Select Raw Mode, Local Use. Select "Pick Drive" and pick the sda6 partition (the destination drive - your large partition if you made one), or your external drive. "Config Filename", type in a name. Select "Backup", pick the sda1 partition and let it roll. Should take less than 10 minutes and you'll have an image you can restore in case your server develops a problem. [/COLOR]

---

### Post by kevdog on 2011-02-19
Newbie to Domain Controllers Here: How would setting up a Domain Controller Help me?

---

### Post by cynicl12000 on 2011-03-26
You tut was incredibly easy to follow and use.  I am setting up my first DNS/LDAP setup and had tried following a few other tuts, but they were all incorrect or incomplete.  From empty vm to install was quick and painless thanks to you.

Thanks!

---

### Post by otacon507 on 2011-04-22
bump

---

### Post by asturgeon on 2011-04-23
I've tried this several times using a fresh install (in VMWare) of Ubuntu Lucid. Guide works very well, I can map drives using users I create with smbldap-useradd. However, I can't join a Windows 7 machine to the domain. I get an "Access is Denied" error in windows. Looking in my log files, I see the following in syslog:

Apr 23 16:54:58 cloudgw slapd[842]: SASL [conn=1023] Failure: realm changed: authentication aborted
Apr 23 16:54:59 cloudgw slapd[842]: SASL [conn=1024] Failure: realm changed: authentication aborted
Apr 23 16:54:59 cloudgw slapd[842]: <= bdb_equality_candidates: (displayName) not indexed
Apr 23 16:54:59 cloudgw slapd[842]: <= bdb_equality_candidates: (cn) not indexed

I tried with XP also. I don't get the authentication realm messages, but I still get Access Denied, even though I can map a drive manually

Does anyone know what the authentication realm messages mean?

---

### Post by J_brand on 2011-05-13
Ran into a slight snag at step 17.  After "smbldap-populate"

the command executed until it reached the UID, CN and sambaDomainName entries
adding new entry: uid=root,ou=Users,dc=callisto,dc=local
failed to add entry objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 55.

adding new entry: cn=Domain Admins,ou=Groups,dc=callisto,dc=local
failed to add entry objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 95.

adding new entry: sambaDomainName=calisto,cd=callisto,dc=local
failed to add entry : invalid DN at /usr/sbin/smbldap-populate line 498, <GEN1> line 236

Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist.

any thoughts on how to overcome the errors in adding uid root and nobody and beyond?

---

### Post by tawiggie on 2011-05-24
So I am working through the tutorial and I get this error when I try to add any of the schemas to ldap

root@MCUSD25-PDC:/etc/ldap/schema# ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=cosine,cn=schema,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
    additional info: olcAttributeTypes: Duplicate attributeType: "0.9.2342.19200300.100.1.2"

So what does this error mean? And how can I fix it? If you need more info let me know. 
If I go on in the tutorial I get to this command:

root@MCUSD25-PDC:/etc/ldap/schema# smbclient -L localhost
Enter root's password: 
session setup failed: NT_STATUS_LOGON_FAILURE

As you can see this is failing also any help would be gladly accepted.

---

### Post by tawiggie on 2011-05-24
ok did some more research and the first error is not of importance as it just means the schema is already there and I am trying to write it again. so I still have the second error I am dealing with.

---

### Post by darksoul7 on 2011-06-01
Here's an interesting little bit. 

I'm running VirtualBox for both the server and the Windows box.

Both are on the same Internal Network.

I can ping both by IP. 

I can ping none by name. 

From my Windows machine I can ping mydomain.local but not mydomain
From my Windows machine I cannot ping myserver

When I try to add the Win7 box to the domain, it tells me it can't find it.

Any ideas?

---

### Post by bmullan on 2011-06-01
You might want to check out the open source project called Resara.

[http://www.resara.org]("http://www.resara.org")

They used a fairly recent Samba4 (v14... I think latest is 15) and their features a pretty nice.

[Resara Features List]("http://resara.org/index.php/features")

They provide Source, a Vmware or VirtualBox VM image but they do have an Ubuntu 10.04 ppa Packages available for Ubuntu Lucid (10.04).

To add this repository run

1.apt-add-repository ppa:resaraserver/resaraserver

Or add these lines to your /etc/apt/sources.list file.

1.deb [http://ppa.launchpad.net/resaraserver/resaraserver/ubuntu](http://ppa.launchpad.net/resaraserver/resaraserver/ubuntu) lucid main
2.deb-src [http://ppa.launchpad.net/resaraserver/resaraserver/ubuntu](http://ppa.launchpad.net/resaraserver/resaraserver/ubuntu) lucid main

Once the repositories have been added, you'll want to update the package lists and install our packages. The package for the client admin tool is called "rdsconsole", and the server side components can be found in "rdsserver"

1.apt-get update
2.apt-get install rds rdsserver

During this you will get prompted for DNS name etc for your domain (and bind9's use).

You should also install the Web based GUI Admin console as it makes user/object management easier.

1.apt-get install rdsconsole

Installing is about as simple as installing any other application using Synaptic.

If you want to see Samba4 working you can watch the Samba.org's Demo video's

Samba4 Demonstration Videos

The Samba Team have put together a series of screencast videos demonstrating some of the capabilities of Samba4.

Note that these videos are in the Ogg Theora format. If you want to view these videos on Windows, then you may find these instructions useful
Demo1 : [Joining Windows 7 to a Samba domain]("http://samba.org/tridge/Samba4Demo/s4demo1.ogv")

This video shows the initial provisioning of a Samba4 domain controller, then a domain join of a Windows7 client as a member of the domain. The Windows7 client is then used to manage the domain via the Active Directory Users and Computers tool

Ogg video: Joining a domain
Demo2 : [Group Policy Managemen]("http://samba.org/tridge/Samba4Demo/s4demo2.ogv")t

This video shows the setup of Group Policy Object (GPO) management of Windows clients with a Samba4 domain.

Ogg video: Group Policies
Demo3 : [Roaming Profiles]("http://samba.org/tridge/Samba4Demo/s4demo3.ogv")

This video shows the setup of roaming profiles for Windows clients in a Samba4 domain.

Ogg video: Roaming Profiles
Demo4 : [dcpromo]("http://samba.org/tridge/Samba4Demo/s4demo4.ogv")

This video shows joining a Windows2008R2 server as an additional domain controller in a Samba domain

Ogg video: dcpromo

---

### Post by kellyfischer on 2011-06-21
Thanks so much for the instructions, a very big help to a novice like myself. I now need to setup a Backup Domain Controller. 

I am assuming that for redundancy sake, I will need to bring up an additional Ubuntu box with DNS (slave zone?), Openldap (how to setup replication?) and Samba (how to configure?). 

Is there an order that I should tackle these or any good documentation that I can dig into that will help me with this? Any advice will be much appreciated.

---

### Post by apamix on 2011-07-29
After I follow the instructions strict I get this error when I try to join Windows 7 or
Windows XP on the domain :(

```
Note: This information is intended for a network administrator.  If you are not your network's administrator, notify the administrator that you received this information, which has been recorded in the file C:\Windows\debug\dcdiag.txt.

The following error occurred when DNS was queried for the service location (SRV) resource
record used to locate an Active Directory Domain Controller (AD DC) for domain
"apamix.local":

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.apamix.local

Common causes of this error include the following:

- The DNS SRV records required to locate a AD DC for the domain are not registered in DNS. These records are registered with a DNS server automatically when a AD DC is added to a domain. They are updated by the AD DC at set intervals. This computer is configured to use DNS servers with the following IP addresses:

192.168.1.99

- One or more of the following zones do not include delegation to its child zone:

apamix.local
local
. (the root zone)


```Is this a problem in the BIND or win the LDAP  :confused:

---

### Post by maverickaddicted on 2011-08-05
I am trying to setup Samba LDAP Server, but I am stuck. Please help me
[http://ubuntuforums.org/showthread.php?t=1813689](http://ubuntuforums.org/showthread.php?t=1813689)

---

### Post by rayne127 on 2011-08-19
> **apamix said:**
> After I follow the instructions strict I get this error when I try to join Windows 7 or
Windows XP on the domain :(

```
Note: This information is intended for a network administrator.  If you are not your network's administrator, notify the administrator that you received this information, which has been recorded in the file C:\Windows\debug\dcdiag.txt.

The following error occurred when DNS was queried for the service location (SRV) resource
record used to locate an Active Directory Domain Controller (AD DC) for domain
"apamix.local":

The error was: "DNS name does not exist."
(error code 0x0000232B RCODE_NAME_ERROR)

The query was for the SRV record for _ldap._tcp.dc._msdcs.apamix.local

Common causes of this error include the following:

- The DNS SRV records required to locate a AD DC for the domain are not registered in DNS. These records are registered with a DNS server automatically when a AD DC is added to a domain. They are updated by the AD DC at set intervals. This computer is configured to use DNS servers with the following IP addresses:

192.168.1.99

- One or more of the following zones do not include delegation to its child zone:

apamix.local
local
. (the root zone)


```Is this a problem in the BIND or win the LDAP  :confused:

I had the same problem. I'm pretty sure it is an issue with samba not adding computer accounts to LDAP when trying to join the domain. If you download the LDAP Admin program and manually add the computer, you will be able to join the domain.

Here's the LDAP Admin program from the OP:
> **Fooshnik said:**
> [COLOR=#000000][COLOR=#000000]27. To browse your LDAP tree you can use [/COLOR][LDAP Admin](http://ldapadmin.sourceforge.net/download/ldapadmin.html).[COLOR=#000000] Make a new connection using the settings:[/COLOR][/COLOR][/COLOR][/COLOR]
[COLOR=#660000][COLOR=#3333EE][COLOR=#a0a0a0][/COLOR][/COLOR][/COLOR] 
[COLOR=#660000][COLOR=#3333EE][COLOR=#000000]Host: [/COLOR][COLOR=#006600][COLOR=#3333EE]myserver[/COLOR][/COLOR][/COLOR][/COLOR] 
Base: [COLOR=#006600]dc=[COLOR=#ff0000]mydomain[/COLOR],dc=local[/COLOR] 
Username:[COLOR=#006600] cn=admin,dc=[COLOR=#ff0000]mydomain[/COLOR],dc=local[/COLOR] 
Password:[COLOR=#3333EE][COLOR=#006600] [/COLOR][COLOR=#ff00ff]PassWD55[/COLOR][/COLOR] 
You can also use [COLOR=#3333ff][PHPLDAPAdmin](http://phpldapadmin.sourceforge.net/wiki/index.php/Main_Page)[/COLOR] or the LDAP Server module in Webmin. 
 

In XP, use your domain name when joining (ex. server.domain.local, use domain). I had to use username: "root" and the password I used when setting up LDAP to be able to join, but at least it works!

--Adam

---

### Post by rayne127 on 2011-08-19
I just want to say this tutorial is amazing. Very easy to use and follow. I've tried other Samba PDC/LDAP tutorials in test environments and most have failed or were extremely difficult to follow. This one works amazingly and I would definitely recommend following this tutorial in a production environment.

I just have a quick question, I have set up a login script to map H: drive to the user's home directory. Is there a way to mount, say H:\Documents, to the user's My Documents folder in XP/Vista/7? I found a way to do it using a registry file that gets called from the login script. This works perfectly, just curious is there was a way to keep everything in one login script rather than having to call another file to do the rest.

Also, I am having problems getting Samba to automatically add computer accounts when joining the domain. I have to manually add them to LDAP in order to join. I haven't found a fix that has worked for this yet. Just wondering if anyone knew of one.

Thanks!
Adam

---

### Post by pcmanrules on 2011-08-25
Hi there, I have followed this guide to a T on 11.04 and I am getting stuck at: 
```
ldapmodify -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f samba_indexes.ldif
```

and get the error:
```
root@Deep-Space-9:~# ldapadd -Y EXTERNAL -H ldapi:/// -f samba_indexes.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: No such object (32)
        matched DN: cn=config

```

I have also tried this guide [http://www.server-world.info/en/note?os=Ubuntu_11.04&p=samba&f=4]("http://www.server-world.info/en/note?os=Ubuntu_11.04&p=samba&f=4") and get stuck at the same command.

Any advice?

---

### Post by elwarreno on 2012-01-17
just fyi that Resara Server has just released 1.1, which now features multi-server replication and load balancing.  The open source community edition is located at [www.resara.org]("http://www.resara.org")

---

### Post by taihard on 2012-06-04
This tutorial was great and easy to follow. I was able to set up the server (couldn't use 11.10 or 12.04, had to make sure I got 10.04) and I was able to use a win XP box to join. Now i'm trying to figure out how to get an ubuntu desktop box to join, I've tried various different tutorials but none seem to work (maybe server was set up differently!?). Does anyone know how to join a linux box to the server set up using this tutorial so I can use the same username/passwords as I do with windows box?? Thanks so much in advance!!!!

---

### Post by nickaceph on 2012-08-11
Hi, Resara support is closing but the package is still available and it will be opensource sometime later.

I have tried Resara myself, I have fully configure it. with manual install to a new box. ubuntu 10.04 and the newly released resara server package.

in our office we have a few winxp/win7 box and other's are linux mint and ubuntu desktop.

situation:
1. winxp/7 and linux box is able to ping each other by ip and hostname. 
2. winxp/7 and linux box can ping the server by hostname and by the domain name. 

problem 
1. windows box can join the domain without a problem. but the linux box when joining the domain is issuing an error below

DNS_ERROR_BAD_PACKET [code 0x0000251e]


Please help thanks

---

