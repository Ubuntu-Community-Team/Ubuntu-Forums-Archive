---
title: "Ubuntu Server - Active Directory Member Server"
date: 2006-10-19
forum: Server Platforms
---

### Post by mhinrichsen on 2006-10-19
Because I could not find a complete document for setting up and Ubuntu Server as a member server in Active Directory. I created this HowTo to do just that

Overview:

The key advantages of Active Directory membership are secure central user management, authentication, and single sign-on for the clients accessing the server. Once an Ubuntu Samba server is integrated with Active Directory, share level and file level permissions can be set using the AD users and groups without requiring local account mapping. Using Winbind, the Linux server sees the domain users and groups transparently. Accountants will love this; using a Samba server you avoid paying OS licensing fees on the server and client access license fees. My goal is to implement Samba-Active Directory integration on a single domain using Winbind with Kerberos on a Linux operating system that is free with free updates for at least 3 years.  I selected the Ubuntu Dapper Drake 6.06 Server distribution because it is a Debian downstream distribution which has a reputation for being stable and promises to be Free “forever.” My objective is to make the process transparent (and chocked full of tricks) so that I may reproduce the integration anytime and to make it available to other Ubuntu users. 

Preliminaries:

It is assumed that a functioning Active Directory domain is in place.  The DNS house must also be in order along with a solid Internet connection for updates and installs.  The key pieces needed on the Linux server are NTP, Kerberos Samba & Winbind. The current version of Samba 3.02 on Ubuntu supports Winbind with Kerberos. Winbind supplies the users, groups, & passwords from the AD domain and Kerberos supplies the AD authentication mechanisms for Winbind. Because you will use the Shell to do most of the configuration work on the Ubuntu server, make sure you know how to use VI or VIM to modify files.


Getting the Ubuntu Dapper Drake 6.06 Server ready:

•	Make sure your workstations and servers system clocks are in Sync (to within the default 5 minutes.) If they are not, trust me, the Kerberos authentication and ticket passing will not work and you will get some unexpected results. THIS IS VERY IMPORTANT. So do yourself a favor and make sure. I recommend that you setup an NTP server on your network and use it to synchronize your system clocks. This is easy just go to [http://www.ntp.org](http://www.ntp.org) for instructions and Windows Client. This can and should be done on your Window Servers to make sure your system clocks are synchronized and stay synched. Be sure to use the NTP server pools which will make the process very efficient. YOU HAVE BEEN WARNED.
•	Install the Ubuntu server using the CD or DVD base installs. Once the server is up and running and you have set the fixed IP, test the Internet connection and make sure you can Ping the IP Address of the key Windows Domain Controllers. 
•	Just to make life easy, you might want to enable the root account access so that you do not need to prefix every command with sudo. If you do this you will not have to sudo everything. Once the root account access is enabled the password will be the same as the password used for sudo. The enable root account access type the following:

root@ubuntuserver:/#sudo passwd root

•	Next you will need to modify the repositories /etc/apt/sources.list to include universe and multiverse repositories. This is important because some of the key packages needed, such as krb5-user, are found there.  Backup, and then Modify the /etc/apt/sources.list to include at least the following lines:

deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe

•	Run the following command to download the local repository lists:

root@ubuntuserver:/#sudo apt-get update

•	Update system updates:

root@ubuntuserver:/#sudo apt-get upgrade

•	I recommend installing the packages below using the following command:

root@ubuntuserver:/#sudo apt-get install  samba smbfs smbclient smbldap-tools winbind krb5-user krb5-config krb5-doc libkrb53 libpa-krb5 ntp-server ntp sun-java5-jre swat apache2 inetutils-inetd ssh

•	As part of the installation of krb5-conf you will be prompted to enter the default realm information. It will see your current AD Realm.

You will enter the Active Directory domain server such as DCSERVER.LOCALDOMAIN.NET. Kerberos is case sensitive so the realm is entered in upper case. Do not worry too much here because you will later modify the /etc/krb5.conf file to the correct settings.

Configure and Test NTP :

•	Next, configure your NTP service. Review the design suggestions found on the ntp.org website. I present an example that works well for tier-two US-based servers. To duplicate my example modify the /etc/ntp.conf file to look use settings such as:

root@ubuntuserver:/#sudo vim /etc/ntp.conf

# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example


#use your local NTP server –You may want to set this first
server dcserver.localdomain.net


#For the U.S. Pools:
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org


# pool.ntp.org maps to more than 100 low-stratum NTP servers.
# Your server will pick a different set every time it starts up.

# ... and use the local system clock as a reference if all else fails
# NOTE: in a local network, set the local stratum of *one* stable server
# to 10; otherwise your clocks will drift apart if you lose connectivity.
server 127.127.1.0
fudge 127.127.1.0 stratum 13

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
broadcast 192.168.1.0

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient


•	Once ntp is configured restart it with the following command:

root@ubuntuserver:/#sudo /etc/init.d/ntp-server restart


Configure /etc/hosts

Just to be safe even if your DNS servers are working perfectly, it is a wise to add the kdc server to your local /etc/hosts file. This will make everything work much faster (MAKE SURE YOU USE YOUR IP ADDRESS AND FQDN FOR YOUR DC:

192.168.1.100 	dcserver.localdomain.net	dcserver

Configure and Test Kerberos

Given that the Active Directory domain server is dcserver.localdomain.net,(USE YOUR REALM) The following is the /etc/krb5.conf used to configure the MIT Kerberos that we have installed:

Configure

[logging]

	default = FILE:/var/log/krb5.log
        kdc = FILE:/var/log/krb5kdc.log
	admin_server = FILE:/var/log/kadmin.log


[libdefaults]
	default_realm = LOCALDOMAIN.NET
	dns_lookup_realm = false
	dns_lookup_kdc = true

[appdefaults]
 pam = {
	debug = false
	ticket_lifetime = 36000
	renew_lifetime = 36000
	forwardable = true
	krb4_convert = false
 }

Testing

root@ubuntuserver:/#sudo kinit [email]Administrator@LOCALDOMAIN.NET[/email]
Password for [email]Administrator@LOCALDOMAIN.NET[/email]: ********

Check if ticket request was valid using the klist command: 

root@ubuntuserver:/#sudo klist

Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [email]Administrator@LOCALDOMAIN.NET[/email]

Valid starting 		Expires		Service principal
10/18/06 15:43:51		10/19/06 01:43:55	KRBTGT/LOCALDOMAIN.NET@LOCALDOMAIN.NET
	  Renew until	10/19/06  15:43:51

Kerberos 4 ticket cache: /tmp/tkt0
Klist: You have no tickets cached

root@ubuntuserver:/#

At this point, your base Kerberos installation and configuration is operating correctly. You can release the ticket by issuing the kdestroy command.


Join the AD Domain

Configure the Samba file /etc/samba/smb.conf  -Below is an example of  Global and share settings that will work for your testing purposes on a single domain. Just create the /home/data directory using the following command:

root@ubuntuserver:/#sudo mkdir /home/data

Then modify the smb.conf file:

root@ubuntuserver:/#sudo vim /etc/samba/smb.conf

#/etc/samba/smb.conf
[global]

   workgroup = LOCALDOMAIN
   realm = LOCALDOMAIN.NET
   server string = %h server (Samba %v, Ubuntu)
   wins server = 192.168.1.100
   password server = DCSERVER
   enable privileges =Yes
   allow trusted domains = No
   dns proxy = no
   name resolve order = host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   log level = 3
   security = ADS
   encrypt passwords = true
   socket options = TCP_NODELAY
   time server = Yes
   map to guest = nobody
   idmap uid = 16777217-33554431
   idmap gid = 16777217-33554431
   winbind enum users = yes
   winbind enum groups = yes
   printcap name = cups
   printing = cups
   cups options = raw
   template shell = /bin/bash



#======================= Share Definitions =======================
[data]
   comment = Share Data
   path = /home/data
   read only = No
   create mask = 0775
   directory mask = 0775
   browsable = Yes
   public = Yes 
   writeable = Yes
   force create mode = 0775
   force directory mode = 0775
   force security mode = 0775
   guest ok = no
   inherit permissions = yes
   nt acl support = yes

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

Check the configuration using testparm:

root@ubuntuserver:/#sudo testparm

Be sure to stop and start the Winbind services and restart the samba service after modifying and testing the /etc/samba/smb.conf file by executing the following commands:

root@ubuntuserver:/#sudo /etc/init.d/winbind stop
root@ubuntuserver:/#sudo /etc/init.d/samba restart
root@ubuntuserver:/#sudo /etc/init.d/winbind start


The next step is to make sure the time is synchronized with the domain by typing:

root@ubuntuserver:/#sudo net time set


It is now the moment of truth. Type the following to add the linux server to the AD Domain:

root@ubuntuserver:/#sudo net ads join –U Administrator
Administrator’s password:******

Using short domain name – LOCALDOMAIN
Joined ‘Ubuntuserver’ to realm ‘LOCALDOMAIN.NET’

Success! The computer ‘Ubuntuserver’ will now appear as a machine account under “Computers” in your AD console. 

Now, stop Samba & Winbind for the next steps using the following:


root@ubuntuserver:/#sudo /etc/init.d/winbind stop
root@ubuntuserver:/#sudo /etc/init.d/samba stop


Setup Winbind Authentication

Setup Authentication by modifying the file: /etc/nsswitch.conf


root@ubuntuserver:/#sudo vim /etc/nsswitch.conf


# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind

hosts:          files dns wins
networks:       files dns

protocols:      files
services:       files
ethers:         files
rpc:            files
netgroup: 	files
publickey:	nisplus
automount: 	files
aliases:	files nisplus



Save your changes, and start samba and Winbind in the following order:


root@ubuntuserver:/#sudo /etc/init.d/samba start
root@ubuntuserver:/#sudo /etc/init.d/winbind start


Verify that Winbind is working.  Use the Winbind utility wbinfo to list users and groups from the AD Domain Controller.

root@ubuntuserver:/#sudo wbinfo –u
LOCALDOMAIN\Administrator
LOCALDOMAIN\Guest
LOCALDOMAIN\Mhinrichsen
LOCALDOMAIN\User
…


root@ubuntuserver:/#sudo wbinfo –g
LOCALDOMAIN\Domain Computers
LOCALDOMAIN\Admins
LOCALDOMAIN\Guests
LOCALDOMAIN\Domain Users
…

Verify that logins and passwords are coming from the AD Domain Controller as well as the local files:

root@ubuntuserver:/#sudo getent passwd

root:x:0:0:root:/root:/bin/bash
…

LOCALDOMAIN\administrator:x:10000:10000:Administrator:/home/LOCALDOMAIN/administrator:/bin/bash
LOCALDOMAIN\mhinrichsen:x:10001:10001:mhinrichsen:/home/LOCALDOMAIN/mhinrichsen:/bin/bash
…

If Winbind is working you will see the LOCALDOMAIN\ prefix. If not you will probably just see the local accounts on the linux server. 

The final Winbind test is to run net ads info to display the AD server information.

root@ubuntuserver:/#sudo net ads info

LDAP server: 192.168.1.100
LDAP server name: DCSERVER
Realm: LOCALDOMAIN.NET
Bind Path: dc=LOCALDOMAIN, dc=NET
LDAP port: 389
Server time: Wed, 18 Oct 2006 18:02:18 EDT
KDC server: 192.168.1.100
Server time offset: 0
root@ubuntuserver:/#

Configure PAM to use Winbind for workstations authentication
PAM configuration for samba is accomplished by modifying files in the /etc/pam.d directory. The following files need to be modified: 

/etc/pam.d/samba
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session

It is important to make a copy of these files prior to modification. Here is what each of these files should look like after modification:

root@ubuntuserver:/#vim /etc/pam.d/samba

@include common-auth
@include common-account
@include common-session
@include common-password


root@ubuntuserver:/#vim /etc/pam.d/common-account

#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account	required	pam_unix.so


root@ubuntuserver:/#vim /etc/pam.d/common-auth

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth	required	pam_env.so
auth	required	pam_unix.so


root@ubuntuserver:/#vim /etc/pam.d/common-password

#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define  the services to be
#used to change user passwords.  The default is pam_unix

# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# (Add `md5' after the module name to enable MD5 passwords)
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs. Also the "min" and "max" options enforce the length of the
# new password.
password   sufficient pam_windbind.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required	  pam_cracklib.so retry=3 minlen=6 difok=3
# password required	  pam_unix.so use_authtok nullok md5


root@ubuntuserver:/#vim /etc/pam.d/common-session

#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
session 	required	pam_limits.so
session	required	pam_unix.so


At this point check to make sure you can logon to another terminal session such as tty2. Just type Alt-F2 and make sure you can still login as root then go back by typing Alt-F1. Once this is accomplished I recommend restarting the server at this point just to make sure there are no errors during startup and to get a clean environment for testing.  

Applying ownership & permissions to the shared directory

To set the ownership and group permissions on the shared directory /home/data use the chmod and chown commands. Note: use valid users and groups from the real domain

root@ubuntuserver:/#chown –R ‘localdomain\administrator:localdomain\Domain Users’ /home/data

Final Test with a Windows XP/2000/NT workstation

Test a connection to the Ubuntu server from the Windows XP workstation by clicking on start-run in the open box type\\ubuntuserver and then click OK. A window should open showing the \\ubuntuserver\data share and the Printers and Faxes icon. If you open the share the permission at the directory level should match the user and group settings applied previously. 

Recap
If everything works, your Samba server is a member of the Active Directory domain and the accounts can be used to apply permissions to objects on the Ubuntu Linux Server. The central account database is available to the Samba server along with the local accounts such as root, etc. Also, this process will work for other Linux distributions using tools other than apt for the install on non-Debian based distros as long as you are using MIT Kerberos . Of course, you can still use a secure shell and many other tools to connect to the server and do admin work on the server using local accounts without being forced to use AD accounts.  It’s called the best of both worlds! 


Michael Hinrichsen
[http://www.solutiondesignersinc.com](http://www.solutiondesignersinc.com)
[email]mh@solutiondesignersinc.com[/email]

---

### Post by Chayak on 2006-10-20
Very good HOWTO, thanks for posting it.  There are many who would question why but the majority of networks are windows based so playing nice is a must for linux to first integrate then take over more and more functions.  You have to get a beachhead on the enemy's ground ;)  I've found upper management will hardly ever complain about the addition of an economic server for additonal storage as long as it's use is transparent to them hence the need for a linux server to play nice with AD so you can map the drives for front end users.

---

### Post by mhinrichsen on 2006-10-20
Thanks for "getting it" BTW, I used to live there Silverdale, WA.

---

### Post by UbuWu on 2006-10-20
Nice. You should integrate this stuff here: [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

---

### Post by alphanaut on 2008-02-25
Thank you very much.
This saved me a W2k3sstd lic for just fileshare memberserver.

---

