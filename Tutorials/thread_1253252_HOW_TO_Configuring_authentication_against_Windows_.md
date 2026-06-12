---
title: "HOW TO: Configuring authentication against Windows Domain"
date: 2009-08-28
forum: Tutorials
---

### Post by uylug on 2009-08-28
[SIZE=5]Setting up Samba to authenticate against a Windows Domain

[/SIZE][SIZE=2]This guide aims to help those people who are interested in configuring their Ubuntu boxes to login using an account from a Windows Domain. This is particularly important to integrate Ubuntu computers in large Windows networks. I have got this to work using a Windows 2003 Server with an Ubuntu Server 9.04.

It is recommended that you login as root during the process. To login as root run

[/SIZE]```
sudo bash
```[SIZE=2] 

[SIZE=3]1. Getting the necessary packages

[SIZE=2]Install the necessary packages by running the following command in a terminal:[/SIZE][/SIZE][/SIZE]
[SIZE=2][SIZE=3][SIZE=2]
[/SIZE][/SIZE][/SIZE]```
apt-get install samba winbind krb5-user
```[SIZE=2][SIZE=3][SIZE=2]

This will install Samba, Winbind and Kerberos, which are needed to configure our domain member server.

This should not be a problem... as long as you have a working internet connection.


[SIZE=3]2. Configuring your DNS server
[SIZE=2]
You'll need to make Ubuntu use your windows server as DNS. This is essential as this will make it possible to resolve names of computers under your domain.

Before start, make sure you can ping your domain server *by ip address*, like this:

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]```
ping 192.168.1.20
```[SIZE=2]Replace the ip, according to your domain server settings. If this works, we can then continue and configure the DNS server.

The DNS settings are stored in the /etc/resolv.conf file. We can edit this file by doing:
[/SIZE]```
nano /etc/resolv.conf
```[SIZE=2]

Make sure it looks like this:

[/SIZE]```
search domain.local

nameserver 192.168.1.20
```[SIZE=2]

The search keyword adds the given address to the name of the host you're resolving. For example, if you ping myubuntuserver it will actually ping myubuntuserver.domain.local using the ip provided as the Domain Name Server (DNS). Instead of typing domain.local you'll need to get your FQDN which can be done from the Windows Domain server. In [this case]("http://www.bloggix.com/blogs/microsoft/w2k8install/w2k8_62.jpg") development.local is what you're looking for. So in that case, you would replace domain.local by development.local. There are several guides which can help you find your Fully Qualified Domain Name.

Save the file using CTRL+O and then exit CTRL + X and see if you can ping your Windows server *by name**, ***like this:

[/SIZE]```
ping domainserver
```[SIZE=2]

You should get your server name resolved and see its ip address. Otherwise something is not working. Also, if you're having problems while resolving names, double check whether the /etc/resolv.conf still reflects the changes you have made since it gets reset by network managers.

[SIZE=3]
3. Configuring Kerberos[/SIZE]

*Updated: Some people have found problems while configuring Kerberos.*

We will be editing the /etc/krb5.conf file so make sure you make a backup copy before proceeding, this way.

[/SIZE]```
cp /etc/krb5.conf /etc/krb5.conf.original
```[SIZE=2]

That should be enough to undo any changes.

Replace the contents of the krb5.conf file with the following:
[/SIZE][SIZE=2]
[/SIZE]```
    [logging]
    default = FILE10000:/var/log/krb5lib.log

    [libdefaults]
    ticket_lifetime = 24000
    default_realm = DOMAIN.LOCAL
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc

    [realms]
    DOMAIN.LOCAL = {
    kdc = windows_server_name
    admin_server = windows_server_name
    default_domain = DOMAIN.LOCAL

    }

    [domain_realm]
    .domain.local = DOMAIN.LOCAL
    domain.local = DOMAIN.LOCAL

```[SIZE=2] 
If everything goes ok so far, you should be able to check whether Kerberos is working by issuing the following command. You will need an account with administrative privileges on the Windows side to make this work.

[/SIZE]```
kinit Administrator@DOMAIN.LOCAL
```[SIZE=2]
If it fails to resolve the host name, you've got a DNS problem right there. If your DNS settings are working just fine, you will be prompted for the password of the account you just entered and if everything goes fine, you will get no output after you enter your password. If an error occurs you will be notified.

If you get an error saying that the encryption is not supported, then remove these two lines in the /etc/krb5.conf file and try again.

[/SIZE]```
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
```
[SIZE=2] 
If you did not get any errors or messages, it probably worked. In order to know exactly what happened, run the command:

[/SIZE]```
klist
```[SIZE=2]
This should provide details on the Domain Server Kerberos is configured to use. It should look like this:

[/SIZE]```
root@lampsrv:~# klist 
Ticket cache: FILE:/tmp/krb5cc_0 
Default principal: Administrator@DOMAIN.LOCAL

Valid starting     Expires            Service principal 
08/27/09 23:22:52  08/28/09 09:22:57  krbtgt/DOMAIN.LOCAL@DOMAIN.LOCAL
    renew until 08/28/09 23:22:52 


Kerberos 4 ticket cache: /tmp/tkt0 
klist: You have no tickets cached 
```[SIZE=2]


[SIZE=3]4. Configuring Samba

[/SIZE]In order to configure samba, edit the /etc/samba/smb.conf file. You can do it by running

[/SIZE]```
nano /etc/samba/smb.conf
```[SIZE=2]
Replace and/or add the following lines to the samba configuration file:

[/SIZE]```

[global]


workgroup = DOMAIN_NAME
realm = DOMAIN.LOCAL
netbios name = ubuntu_server_name
server string = %h server (Samba %v, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = ADS
domain master = no
idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash
template homedir = /home/%D/%U
winbind enum groups = yes
winbind enum users = yes
winbind use default domain = yes
winbind separator = +
usershare allow guests = yes
```[SIZE=2]

This will configure Samba with some generic settings. Make sure you change DOMAIN_NAME to the domain name you're connecting to and DOMAIN.LOCAL should be your FQDN. You can later customize it according to your needs but lets get it working first.

Now, check whether the samba settings are correct by running

[/SIZE]```
testparm
```[SIZE=2]

Restart the Winbind and Samba services by running
[/SIZE]
```

/etc/init.d/winbind stop
/etc/init.d/samba restart
/etc/init.d/winbind start
```[SIZE=2]


[SIZE=3]5. Join the Windows Domain[/SIZE]

You should now be able to join the Windows domain by running the following command:
[/SIZE]```

net ads join -U Administrator@DOMAIN.LOCAL
```[SIZE=2]

If it works, your Ubuntu server should now appear in the Windows Domain Server as a Domain Computer. If you get an error like

[/SIZE]```
Malformed representation of principal
```Try to do it like this:

```

net ads join -U Administrator
```[SIZE=2]
[/SIZE]
[SIZE=2] 
[SIZE=3]6. Configure Winbind
[SIZE=2]
Edit the /etc/nsswitch.conf file and make it look like this:

[/SIZE][/SIZE][/SIZE]```
passwd: compat winbind
group:  compat winbind
shadow: compat winbind

hosts:     files dns wins
networks:  files dns

protocols:   db files
services:    db files
ethers:      db files
rpc:         db files

netgroup:     nis
```[SIZE=2]Restart Samba and Winbind

[/SIZE]```

/etc/init.d/winbind stop
/etc/init.d/samba restart
/etc/init.d/winbind start
```[SIZE=2]

If everything is alright you should be able to retrieve information from your Windows Domain.

To get a list of users run
[/SIZE]```
wbinfo -u
```[SIZE=2]

To get a list of groups run
[/SIZE]```
wbinfo -g
```[SIZE=2]

To get details about the domain run
[/SIZE]```
net ads info
```[SIZE=2]

You will probably notice everythings great but... still cannot login using a user from the domain. So continue to step number 7.


[SIZE=3]7. Enabling login from domain accounts[/SIZE]

Edit the file /etc/pam.d/common-auth[/SIZE][SIZE=2] and add the following line at the start of the file:

[/SIZE]```
auth sufficient pam_winbind.so
```[SIZE=2]

This basically means that if a user successfully logins using a domain account that is enough to login to the system.

Edit the /etc/pam.d/common-session file and add the following line to enable automatic creation of home folder when a new user logins to the linux box:

[/SIZE]```
session required pam_mkhomedir.so
```[SIZE=2]
The folder will be created according to the parameter in the smb.conf file

[/SIZE]```
template homedir = /home/%D/%U
```[SIZE=2]

Hope that helps! :P

Note: If your /etc/resolv.conf file content keeps getting replaced run this command to make sure no processes can alter its content (not even root will be able to write changes to it):
```
chattr +i /etc/resolv.conf
```
[/SIZE]

---

### Post by uylug on 2009-09-05
Guide updated as some people have been getting errors while configuring Kerberos.

---

### Post by uylug on 2009-09-12
Guide updated.

---

### Post by Diamond2 on 2009-09-30
How do user change their account password themselves in linux box if their password have expired and they cannot log in linux box?

---

### Post by uylug on 2010-08-05
Um i really dont know... I'll check that later

---

### Post by dougmorin on 2010-08-17
When logging onto the main screen do they login as user@domain or workgroup\user?

---

### Post by uylug on 2010-08-22
Depends on your settings really... Users were able to login as 'user' without the need to add any sort of domain information because I had set it to be the default domain.

If you've got more than one domain, this HOW TO will probably need further editing and commands for it to work.

---

### Post by Romu on 2012-07-02
Hi,
Thanks for this tuto. It works great. My last issue is now how: to connect graphically through LightDM?

LightDM stills displays local user accounts and there is no way to enter a domain account.

Thanks.

---

### Post by goldan on 2012-07-29
> **Romu said:**
> Hi,
Thanks for this tuto. It works great. My last issue is now how: to connect graphically through LightDM?

LightDM stills displays local user accounts and there is no way to enter a domain account.

Thanks.



enable nonlocal users to login:

edit /etc/lightdm/lightdm.conf 
and add

greeter-hide-users=true

---

### Post by snake2903 on 2012-10-17
This is great tutorial but i have questions.

In my company we have 3 server for our domain, example:

Our domain naame:    INT.COMPANY.COM

3 servers that give as above domain name:

dc-1.int.company.com     this is main server
dc-2.int.company.com
dc-3.int.company.com

Is this good configuration of krb5.conf file for my situation:

```

    [logging]     default = FILE10000:/var/log/krb5lib.log
    [libdefaults]     
    ticket_lifetime = 24000     
    default_realm = INT.COMPANY.COM     
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc     
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc      
    [realms]     
    INT.COMPANY.COM = {    
    kdc = dc-1.int.company.com
    kdc = dc-2.int.company.com
    kdc = dc-3.int.company.com
    admin_server = dc-1.int.company.com
    master_kdc = dc-1.int.company.com
    default_domain = INT.COMPANY.COM     
    }     
    [domain_realm]    
    .domain.local = INT.COMPANY.COM    
    domain.local = INT.COMPANY.COM

```The part that is confusing me is:
Is it good that i defined my main domain server as master_kdc?
Do i need define admin_server for secondary domain servers (dc-2 and dc-3 )?
Will this configuration automatically switch me to secondary kdc if kdc1 crash?

I hopu you understand me :-)

---

### Post by skinfrakki on 2013-04-05
I have tried both upper case and lower case. Still fails. In upper case I get 

kinit: Cannot resolve servers for KDC in realm "REALM.DOMAIN.COM" while getting initial credentials

In lower case

kinit: KDC reply did not match expectations while getting initial credentials

nslookup can find the domain in both upper and lower case

---

