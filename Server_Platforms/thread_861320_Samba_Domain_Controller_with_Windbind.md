---
title: "Samba Domain Controller with Windbind"
date: 2008-07-16
forum: Server Platforms
---

### Post by ryazkhan on 2008-07-16
Hello to all forum
I was reading this forum and find lot of people are trying to get help with the setup of SAMBA a powerfull Domain controller, This is a almost very basic setup but will give you a ready domain controller. If things configred as I did I can almost gurantee you that will work since I tried it several time and it alway worked for me so Good Luck! with yours
I will assume that you have Ubuntu machine up and running at this point with static IP (you dont have to but it is good practice). If you are not working as root user use sudo with every common or just switch to root by > sudo bash
We need to install these packages> apt-get install samba
apt-get install winbind
apt-get install smbclient
Afterward stop both services> /etc/init.d/samba stop
/etc/init.d/winbind stop
Clear some temporary stuff which can interupt us> rm /var/lib/samba/*.tdb 
rm /var/run/samba/*.tdb
rm /var/cache/samba/*.tdb
Samba Domain Controller configuration be very carefull here I usually rename my old smb.conf file smb.old and then creates new smb.conf in order to avoid mistakes and for other default options you can alway find them in smb.old and can add to smb.conf if you need to according to your setup.> gedit /etc/samba/smb.confAnd paste this but make some change according to your settings> [global]
workgroup = MYDOMAIN (change it with your domain name)
netbios name = ubuntu (name of domain controller)
logon drive = H: 
domain master = yes
preferred master = yes
domain logons = yes
wins support = yes
passdb backend = tdbsam
encrypt passwords = yes
security = user
logon script = logon.cmd [I]if you want to use script for instance map drives etc.
[/I]
[homes]
comment = Home
path = %H
read only = no
browseable = no

[printers]
comment = All Printers
path = /var/spool/samba
printable = yes
public = no
writable = no
create mode = 0700
browseable = no

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no
write list = root

[netlogon]
path = /netlogon *if you using script, it has to be located in this directory*
read only = yes
guest ok = yes 
We almost done with configuration and it is time to start Samba and Windbind services> /etc/init.d/samba start
/etc/init.d/winbind startCheck you */etc/hosts*and make sure you have real IP not 127.0.1.1 address and computername. Now edit your nsswitch.conf> gedit /etc/nsswitch.conf
 We want to resolve naming via winbid before DNS so find hosts line and add files wins before dns so that would look like> hosts:  files wins dns ]*and rest of this file if you have*give root samba password> smbpasswd -a root
Restart services just to be safe you dont have to> /etc/init.d/samba restart
/etc/init.d/winbind restart That is pretty much it so test your setup> smbclient -L localhost
Now that it worked it is good time to add some groups> net groupmap add ntgroup="Domain Admins" unixgroup="root" type=domain 
net groupmap add ntgroup="Domain Users" unixgroup="users" type=domain -U root 
net groupmap add ntgroup="Domain Guests" unixgroup="nogroup" type=domain -U root
We are done and you have samba domain working but one more thing how can we join machines to this domain and logon into those using our new Samba Domain Controller. We need to add machine account first in order to joint it to this domain so > useradd xp-client$*xp-client is the name of machine*Now set password for this account even we would not user it but samba want that....> smbpasswd -a -m xp-client$ Now go to your xp-client machine and logon as administrator to joint it to domain. Right click on my computer->properties->computer name->change->domain radio and type your new domain which in this case is MYDOMAIN, click ok and provide root password you setup earlier. You will see message of success or error (5% chance). Restart your machine and login with root user and in MYDOMAIN (which you can select from drop down list). Enjoy it!
this how can be accessed @ [www.freetech.selfip.info/samba.php](www.freetech.selfip.info/samba.php)

---

