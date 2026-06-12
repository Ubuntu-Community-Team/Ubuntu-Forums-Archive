---
title: "How to install samba 4 as an active directory domain controller"
date: 2013-05-17
forum: Tutorials
---

### Post by Toxic64 on 2013-05-17
[FONT=arial]In this tutorial, we will setup samba 4 from source as an Active Directory domain controller on Ubuntu server (12.04.2).


First, you need to configure your network interface for static IP. (we'll use  192.168.0.100 as IP for this Domain Controller,  DC01 for the name and MYDOMAIN.LAN as FQDN )
Edit your **/etc/network/interfaces **file.

```
sudo nano /etc/network/interfaces
```

change** iface eth0 inet [COLOR=#ff0000]dhcp[/COLOR]** to ** iface eth0 inet [COLOR=#006400]static[/COLOR]**

 then add these lines:
```

address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1 
dns-nameservers 192.168.0.100 8.8.8.8 (we use our server as DNS + google DNS as secondary DNS)
dns-search mydomain.lan
```


Save and close

then we need to configure our **/etc/hosts** file like so:
```


127.0.0.1       localhost.localdomain   localhost 
192.168.0.100   DC01.mydomain.lan       DC01
```

save and close

then run


 ```
sudo echo DC01.mydomain.lan > /etc/hostname

 /etc/init.d/hostname restart
```

now restart networking so that the changes are made 

```
/etc/init.d/networking restart
```


now we need to install the prerequisites for samba kerberos etc....

```
sudo apt-get update [COLOR=#0000cd](I generally add "&& apt-get upgrade -y" so that my server is fully up  to date)[/COLOR]
sudo apt-get install git build-essential libacl1-dev libattr1-dev libblkid-dev libgnutls-dev libreadline-dev python-dev python-dnspython gdb pkg-config libpopt-dev libldap2-dev dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev libpam0g-dev ntp -y
```

You'll be asked for kerberos informations.[/FONT]
[FONT=arial]When asked for the default realm etc, enter mydomain.lan and DC01 as the host.[/FONT][FONT=arial] 

when it's done, we need to download the samba4 sources (this line goes for latest stable release):

```
git clone -b v4-0-stable git://git.samba.org/samba.git samba4
```

then go to the samba4 folder:

```
cd samba4
```
[/FONT]
[FONT=arial][FONT=arial]run

[/FONT] ```
 ./configure --enable-debug --enable-selftest 
make 
make install 
```

depending on your computer it may take a while ( 15-20 mins)


Once it's done, we need to provision our domain: (we'll use SAMBA_INTERNAL but you can use BIND9 also)

```
/usr/local/samba/bin/samba-tool domain provision --realm=mydomain.lan --domain=mydomain --adminpass="your_password" --server-role=dc --dns-backend=SAMBA_INTERNAL 
```

start samba
```
/usr/local/samba/sbin/samba
```

check samba and smbclient version ( they should match )

```
/usr/local/samba/sbin/samba -V
/usr/local/samba/bin/smbclient -V
```

listing administrative share will show you sysvol, netlogon shares etc....

```
/usr/local/samba/bin/smbclient -L localhost -U%
```

you should see somethin like this:
```

  

Sharename      Type      Comment      
---------        ----       -------        
netlogon         Disk 
sysvol            Disk 
IPC$              IPC         IPC Service (Samba 4.0.5)  

 
```

it means your server is up and running...

now you need to check authentication

```
/usr/local/samba/bin/smbclient //localhost/netlogon -UAdministrator%"your_password" -c 'ls'
```

you should see this:
```

Domain=[MYDOMAIN] OS=[Unix] Server=[Samba 4.0.5]  
.                                   D        0  Fri May 17 21:40:08 2013   
..                                  D        0  Fri May 17 21:42:36 2013
```


Then we need to configure SAMBA_INTERNAL DNS

```
echo  domain MYDOMAIN.LAN >> /etc/resolv.conf
```

edit** /usr/local/samba/etc/smb.conf**

```
sudo nano  /usr/local/samba/etc/smb.conf
```

add 

```
dns forwarder = 8.8.8.8 [COLOR=#0000CD](I use google DNS here again)[/COLOR]
```

save and close.

Now we need to test DNS. Issue the next commands.

[/FONT]```
[FONT=arial]

[/FONT][FONT=arial]host -t SRV _ldap._tcp.mydomain.lan
[/FONT][FONT=arial]_ldap._tcp.mydomain.lan has SRV record 0 100 389 DC01.mydomain.lan.[/FONT][FONT=arial]
[/FONT][FONT=arial]

host -t SRV _kerberos._udp.mydomain.lan[/FONT]
[FONT=arial]_kerberos._udp.mydomain.lan has SRV record 0 100 88 DC01.mydomain.lan[/FONT]

[FONT=arial]host -t A DC01.mydomain.lan[/FONT]
[FONT=arial]DC01.mydomain.lan has address 192.168.0.100[/FONT]. 
```[FONT=arial]

If you recieved something like "host mydomain.lan not found 3(NXDOMAIN)" your samba probabaly failed to start for some reason...

Next, we need to  configure and test Kerberos:

edit file [B]/usr/local/samba/share/setup/krb5.conf

[/B]and replace $(REALM) by MYDOMAIN.LAN

```
kinit administrator@MYDOMAIN.LAN [COLOR=#0000cd](has to be capital letters or will fail / will ask for your domain administrator password )[/COLOR]
klist -e [COLOR=#0000ff](will display informations about the kerberos ticket you received)[/COLOR]
```[/FONT]


[FONT=arial]AD DC need functional Ntp servers: 

edit** /etc/ntp.conf** and add your ntp servers here.
 I used french servers from [http://www.pool.ntp.org/zone/fr](http://www.pool.ntp.org/zone/fr)

now issue the following commands

```
service ntp restart
ntpdate 0.fr.pool.ntp.org
ntpq -p

```

and you're done...

You might want to add users home folders or profile folders etc...

```
mkdir -m 770 /Users
chmod g+s /Users
chown root:users /Users
```

then edit [B]/usr/local/samba/etc/smb.conf

[/B]and add the following lines:

```
[Users]
directory_mode: parameter = 0700
read only = no
path = /Users
csc policy = documents
```
[/FONT]
[FONT=arial]
finally set no expiration flag fro your active directory administrator password (or you'll have problems after 42 days)
[/FONT]
```
/usr/local/samba/bin/[FONT=arial]samba-tool user setexpiry administrator --noexpiry  [/FONT]
```


administration can be done from any windows client with admin(XP,2003) pack or RSAT(Vista,Seven,Eight,2008,2012)

for the lazy, you can edit variables in my script and use it.:P just be sure to reboot between script 1 and script 2 or it won't work (I don't know why)[ATTACH]243002[/ATTACH]

---

### Post by JnPson on 2013-05-17
Excellent tutorial. Thank you Toxic64.

---

### Post by Roswebnet on 2013-05-24
Nice one. :)
But I have some critic about script. ;) 
First one you don&#8217;t give a user to choose a network adapter (It can be that user have more than one physical or virtual adapters ;).
Second one you do not create a revers dns zone what should have very handy in nslookup.
Third one where is bind? As far as I know due bind is production oriented dns so it is better than internal dns.
Maybe I miss something. I will add it later.

---

### Post by Toxic64 on 2013-05-25
Hi , thanks for your appreciation and remaks.
For the interface choice, you are totally right. My mistake. I'll correct the script to set the interface choice as a variable.

For the reverse zone, I didn't do it from the script because It was easier to do from dnsmgmt.msc console on a windows xp client and wanted to write a tutorial about administration from S4AD with MS consoles. if you want to create one from command line just use this command:
```

samba-tool dns zonecreate <server> **[COLOR=#ff0000]xxx.xxx.xxx[/COLOR]**.in-addr.arpa --username=administrator (where [COLOR=#ff0000]xxx.xxx.xxx[/COLOR] is your network address first 24 bits reversed)

ex : 
samba-tool dns zonecreate myserver **[COLOR=#008000]0.168.192[/COLOR]**.in-addr.arpa --username=administrator (network is 192.168.0.x)

then add the PTR record:

samba-tool dns add <server> **[COLOR=#008000]0.168.192[/COLOR]**.in-addr.arpa** [COLOR=#ff0000]xxx[/COLOR]** PTR  myserver.mydomain.lan --username=administrator (where [COLOR=#ff0000]xxx[/COLOR] is your machine's IP address last 8 bits)

ex:
samba-tool dns add myserver **[COLOR=#008000]0.168.192[/COLOR].**in-addr.arpa** [COLOR=#008000]17[/COLOR]** PTR  myserver.mydomain.lan --username=administrator (IP is 192.168.0.17)

```

As for bind, I know you are absolutely right about it BUT by default S4 comes and installs SAMBA_INTERNAL if you don't provision a backend during setup, that's why I chose to stick with it and the reason is simple:Bind doesn't handle active directory integrated zones,Samba internal dns does.

---

### Post by Roswebnet on 2013-05-25
For the first point. You can use my provision but devided in question like:
Please provide domain functional level

[LIST=1]
[*]Windows 2000
[*]Windows 2003
[*]Windows 2008
[*]Windows 2008_R2
[/LIST]
 
My provision:
```
 samba-tool domain provision \--realm=ODM.LAN \--domain=ODM \--adminpass='Pa$$w0rd' \--dns-backend=BIND9_DLZ \--server-role=dc \--function-level=2008_R2 \--use-xattr=yes \--use-rfc2307 \--host-ip=10.1.1.1 \--simple-bind-dn=ODM.LAN \--ipaddress=10.1.1.1 
```
 
 \--simple-bind-dn=ODM.LAN \--ipaddress=10.1.1.1 &#8211; I am not sure if it is useful.
 
About second point. Agree. However, some noob (like I was in samba4 couple of month ago) could not know about it. Samba4 still miss a good portion of documentation and different scenario implementation examples. 
About different implementation scenarios. I got one time an idea to write a good tutorial based on Ubuntu repository. But I have not so much times and I still have a problems with samba4.
 
About third point. Can you please provide some readings about active directory integrated zones? I came from Windows Server, but I newer dive deep enough to those things. If it works do not touch it. You know right? : )
 
I found fourth point in NTP CONFIGURATION. As far as I know NTP update the server list according geographical location. It use some geographically closest (in my situation it detects one Dutch server) time server and couple of far placed servers e.g. USA servers. Therefore in my opinion it&#8217;s better to just use:
```

Apt-get install ntp
Ntpq &#8211;p

```
Correct me if I am wrong.

---

### Post by Toxic64 on 2013-05-25
> For the first point. You can use my provision but devided in question like:
Please provide domain functional level


[LIST=1]
[*]Windows 2000 
[*]Windows 2003 
[*]Windows 2008 
[*]Windows 2008_R2 
[/LIST]


Don't!!! or be very carefull because functional level can not be set back to anterior version.
this could mess MS Exchange and a few other MS infrastructure products. ( all 2000 functionalities like TSE etc will instantly fail with no possibiility to roll-back)
More than that any DC with an OS anterior to your domain level won't work anymore.
I'd advise to do it after once you are really sure about what you're gonna do.

> After you set the domain functional level to a certain value in Windows  Server 2008 R2, you cannot roll back or lower the domain functional  level, with one exception: when you raise the domain functional level to  Windows Server 2008 R2 and if the forest functional level is Windows  Server 2008 or lower, you have the option of rolling the domain  functional level back to Windows Server 2008. You can lower the domain  functional level only from Windows Server 2008 R2 to Windows  Server 2008. If the domain functional level is set to Windows  Server 2008 R2, it cannot be rolled back, for example, to Windows  Server 2003.
[http://technet.microsoft.com/en-us/library/cc787290%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc787290%28v=ws.10%29.aspx)

Same goes for the forest functional level


AD integrated zones: [http://technet.microsoft.com/en-us/library/cc772746%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc772746%28v=ws.10%29.aspx)
Be my guest :wink:

Ntp: Ntp is installed at the begining of the script on your ubuntu server. You can use whatever location you want from :[http://www.pool.ntp.org/fr/](http://www.pool.ntp.org/fr/)

Automatic ntp detection according to geographical zone is not always the best choice.

Example scenario: you have a DC in paris and another DC London. timezone is different by one hour. your DC won't replicate as AD won't handle more than 5 minute in time difference between 2 AD DCs.
In this scenario you'll have to use the same ntp so that they're set at the exact same time/date so they will replicate.
In an AD environement, you absolutely want to avoid stale objects.

---

### Post by Roswebnet on 2013-05-25
About functional levels. Oh, I get a feeling that there is my problem with squid, openchange, freeradius and other ldap authentication oriented software. By default samba4 use windows 2003 functional level. Am I right? And Functional level 2008 + is specific software oriented such as Exchange 2010 +, Forefront TMG 2010, Lync 2010, SCOM and etc&#8230;
I will test it with default functional level.
About DNS. Thanks I will take my time to read it. : )
NTP. I thought when you chose in Ubuntu your time, geo location and installs NTP server, NTP looks to it and contact by itself the closest server.

---

### Post by Toxic64 on 2013-05-25
Not sure your problem with those products come from functional level but indeed samba 4 comes with DL 2003 by default.
Domain lvl upgrades are feature specific for example, 2003 to 2008 brings a change in AD replication method from NTFRS to DFS-R (it also brings a lot of other features ...too long to enumerate)
rest assured that an inconsiderate domain level upgrade will inevitably render all your DC's with an anterior OS useless and your AD buggy to hell.then you'll need a Forest Disaster recovery plan to restore.. can assure you that you don't want to do that (In my job, I once had to because on of my customer decided it would be a trivial operation and didn't consult or ask for any advice before doing it...little clicks bring chaos)
Generally, they won't impact exchange forefront etc but sometimes depending on your config, they will mess a few things up.

---

### Post by JnPson on 2013-05-29
> **Toxic64 said:**
> 
```

samba-tool dns zonecreate <server> **[COLOR=#ff0000]xxx.xxx.xxx[/COLOR]**.in-addr.arpa (where [COLOR=#ff0000]xxx.xxx.xxx[/COLOR] is your network address first 24 bits reversed)

ex : 
samba-tool dns zonecreate myserver **[COLOR=#008000]0.168.192[/COLOR]**.in-addr.arpa (network is 192.168.0.x)

then add the PTR record:

samba-tool dns add <server> **[COLOR=#008000]0.168.192[/COLOR]**.in-addr.arpa** [COLOR=#ff0000]xxx[/COLOR]** PTR  myserver.mydomain.lan --username=administrator (where [COLOR=#ff0000]xxx[/COLOR] is your machine's IP address last 8 bits)

ex:
samba-tool dns add myserver **[COLOR=#008000]0.168.192[/COLOR].**in-addr.arpa** [COLOR=#008000]17[/COLOR]**PTR  myserver.mydomain.lan --username=administrator (IP is 192.168.0.17)

```



I didn't get this working at first but then I realized you have to add --username=administrator to this line too:
```
samba-tool dns zonecreate <server> **[COLOR=#ff0000]xxx.xxx.xxx[/COLOR]**.in-addr.arpa **--username=administrator** (where [COLOR=#ff0000]xxx.xxx.xxx[/COLOR] is your network address first 24 bits reversed)

ex : 
samba-tool dns zonecreate myserver **[COLOR=#008000]0.168.192[/COLOR]**.in-addr.arpa **--username=administrato**r (network is 192.168.0.x)


```
And for those as noob as me, the path to samba-tool is /usr/local/samba/bin/samba-tool.

---

### Post by Toxic64 on 2013-05-29
Yep indeed , all administrative management tasks in AD/ MSDNS environement requires the use of the administrator account or any other administrative acount with the adequat rights you might have created in the domain admins group (though some tasks might require higher permissions than domain admins).

AD won't run any task with the root account as it doesn't exist in an AD environement.

---

### Post by Roswebnet on 2013-05-29
I did it like this: ```
#DNS reverse zone
kinit [administrator@ODM.LAN]("http://vk.com/write?email=administrator@ODM.LAN")
samba-tool dns zonecreate 10.1.1.1 [1.1.10.in-addr.arpa]("http://vk.com/away.php?to=http%3A%2F%2F1.1.10.in-addr.arpa")

samba-tool dns add 10.1.1.1 [1.1.10.in-addr.arpa]("http://vk.com/away.php?to=http%3A%2F%2F1.1.10.in-addr.arpa") 1 PTR odm-gw-srv01.odm.lan 
``` Here you will type the name once, password 2 times.

---

### Post by Toxic64 on 2013-05-29
yep issuing a Kerberos ticket for the administrator account. same effect and pretty good alternative too.

---

### Post by nextraa on 2013-06-29
Hi Toxic64,

I followed your tutorial on how to install samba4 on an Ubuntu server. I got to the step to check the DNS functionality. I got the "host present.local not found 3(NXDOMAIN)" error. I wasn't sure what to do. I read somewhere that resolv.conf couldn't handle .local so I changed that to .lan, but now I get the following error:

root@ubuntu:/home/martijn# /usr/local/samba/bin/smbclient -L locahost -U%
Connection to locahost failed (Error NT_STATUS_UNSUCCESSFUL)

I don't know what to do anymore and I hope I don't have to do another fresh install of the entire ubuntu server. Can you help me out?

---

### Post by nextraa on 2013-06-29
Hi Toxic64,

I changed the workgroup setting in my smb.conf file and SAMBA does seem to be responding again to:

root@ubuntu:~# /usr/local/samba/bin/smbclient //localhost/netlogon -UAdministrator%"**********" -c 'ls'
Domain=[PRESENT] OS=[Unix] Server=[Samba 4.0.6]
  .                                   D        0  Sat Jun 29 12:27:51 2013
  ..                                  D        0  Sat Jun 29 12:28:08 2013


		36608 blocks of size 2097152. 32672 blocks available

But I still get the DNS errors:

root@ubuntu:~# host -t SRV _ldap._tcp.present.lan
Host _ldap._tcp.present.lan not found: 3(NXDOMAIN)
root@ubuntu:~# host -t SRV _kerberos._udp.present.lan
Host _kerberos._udp.present.lan not found: 3(NXDOMAIN)
root@ubuntu:~# host -t A ubuntu.present.lan
Host ubuntu.present.lan not found: 3(NXDOMAIN)

---

### Post by nextraa on 2013-06-29
Also DNSupdates doesn't work:

root@ubuntu:~# /usr/local/samba/sbin/samba_dnsupdate --verbose
IPs: ['192.168.178.8']
Looking for DNS entry A present.lan 192.168.178.8 as present.lan.
Failed to find DNS entry A present.lan 192.168.178.8
Looking for DNS entry A ubuntu.present.lan 192.168.178.8 as ubuntu.present.lan.
Failed to find DNS entry A ubuntu.present.lan 192.168.178.8
Looking for DNS entry A gc._msdcs.present.lan 192.168.178.8 as gc._msdcs.present.lan.
Failed to find DNS entry A gc._msdcs.present.lan 192.168.178.8
Looking for DNS entry CNAME f4f59ff6-83dc-4f1a-96da-0d500c948555._msdcs.present.lan ubuntu.present.lan as f4f59ff6-83dc-4f1a-96da-0d500c948555._msdcs.present.lan.
Failed to find DNS entry CNAME f4f59ff6-83dc-4f1a-96da-0d500c948555._msdcs.present.lan ubuntu.present.lan
Looking for DNS entry SRV _kpasswd._tcp.present.lan ubuntu.present.lan 464 as _kpasswd._tcp.present.lan.
Failed to find DNS entry SRV _kpasswd._tcp.present.lan ubuntu.present.lan 464
Looking for DNS entry SRV _kpasswd._udp.present.lan ubuntu.present.lan 464 as _kpasswd._udp.present.lan.
Failed to find DNS entry SRV _kpasswd._udp.present.lan ubuntu.present.lan 464
Looking for DNS entry SRV _kerberos._tcp.present.lan ubuntu.present.lan 88 as _kerberos._tcp.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _kerberos._tcp.dc._msdcs.present.lan ubuntu.present.lan 88 as _kerberos._tcp.dc._msdcs.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.dc._msdcs.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _kerberos._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 88 as _kerberos._tcp.default-first-site-name._sites.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _kerberos._tcp.default-first-site-name._sites.dc._msdcs.present.lan ubuntu.present.lan 88 as _kerberos._tcp.default-first-site-name._sites.dc._msdcs.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.default-first-site-name._sites.dc._msdcs.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _kerberos._udp.present.lan ubuntu.present.lan 88 as _kerberos._udp.present.lan.
Failed to find DNS entry SRV _kerberos._udp.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _ldap._tcp.present.lan ubuntu.present.lan 389 as _ldap._tcp.present.lan.
Failed to find DNS entry SRV _ldap._tcp.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _ldap._tcp.dc._msdcs.present.lan ubuntu.present.lan 389 as _ldap._tcp.dc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.dc._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _ldap._tcp.gc._msdcs.present.lan ubuntu.present.lan 3268 as _ldap._tcp.gc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.gc._msdcs.present.lan ubuntu.present.lan 3268
Looking for DNS entry SRV _ldap._tcp.pdc._msdcs.present.lan ubuntu.present.lan 389 as _ldap._tcp.pdc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.pdc._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _ldap._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 389 as _ldap._tcp.default-first-site-name._sites.present.lan.
Failed to find DNS entry SRV _ldap._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _ldap._tcp.default-first-site-name._sites.dc._msdcs.present.lan ubuntu.present.lan 389 as _ldap._tcp.default-first-site-name._sites.dc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.default-first-site-name._sites.dc._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _ldap._tcp.default-first-site-name._sites.gc._msdcs.present.lan ubuntu.present.lan 3268 as _ldap._tcp.default-first-site-name._sites.gc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.default-first-site-name._sites.gc._msdcs.present.lan ubuntu.present.lan 3268
Looking for DNS entry SRV _ldap._tcp.0ca37e40-b704-4539-9694-c828038af196.domains._msdcs.present.lan ubuntu.present.lan 389 as _ldap._tcp.0ca37e40-b704-4539-9694-c828038af196.domains._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.0ca37e40-b704-4539-9694-c828038af196.domains._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _gc._tcp.present.lan ubuntu.present.lan 3268 as _gc._tcp.present.lan.
Failed to find DNS entry SRV _gc._tcp.present.lan ubuntu.present.lan 3268
Looking for DNS entry SRV _gc._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 3268 as _gc._tcp.default-first-site-name._sites.present.lan.
Failed to find DNS entry SRV _gc._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 3268
Traceback (most recent call last):
  File "/usr/local/samba/sbin/samba_dnsupdate", line 506, in <module>
    get_credentials(lp)
  File "/usr/local/samba/sbin/samba_dnsupdate", line 119, in get_credentials
    creds.get_named_ccache(lp, ccachename)
RuntimeError: kinit for UBUNTU$@PRESENT.LAN failed (Cannot contact any KDC for requested realm)

---

### Post by nextraa on 2013-06-29
Found the problem. I pointed SAMBA to my router IP as a DNS name server. But this wasn't correct. So I pointed SAMBA to the server itself and then the problem was solved.

---

### Post by Toxic64 on 2013-06-29
yep 3NXDOMAIN message says samba_internal isn't working. samba can't start correctly.

---

### Post by nextraa on 2013-07-02
Hi Toxic,

I hope you can help me some more, because I'm drowning in a sea of my own ignorance. First of all I had things all working, except for the part that I couldn't add Windows clients to the AD domain. The error was that the computer account already existed. Which is impossible because I have never been able to add any computer to the domain. However now it seems SAMBA won't even start anymore. It seems to start:

root@ubuntu:/home/martijn# /usr/local/samba/sbin/samba
Global parameter domain logons found in service section!
Global parameter domain master found in service section!
Global parameter local master found in service section!
Global parameter preferred master found in service section!
Global parameter logon path found in service section!
Global parameter logon drive found in service section!
Global parameter logon home found in service section!
Global parameter add machine script found in service section!

But when I test it I get no response:

root@ubuntu:/home/martijn# host -t A ubuntu.present.lan
Host ubuntu.present.lan not found: 3(NXDOMAIN)

I don't know what to do anymore. It is also very frustrating that there are no clear guidelines what should be in the smb.conf. In the older SAMBA version the smb.conf was ready-made and you only had to take away some hashtags for the options you want to use. Also a big question mark with me is whether I should choose security = user or security = ADS as the servertype. Hope you can help or if anyone can help me?

---

### Post by JnPson on 2013-07-02
I use Samba 4.0.6 and I use Adminpak to administer it from an XP machine. With that tool you can see graphically if your computers exists in the domain. The englsh version is found here: [http://www.microsoft.com/en-us/download/details.aspx?id=16770](http://www.microsoft.com/en-us/download/details.aspx?id=16770)

---

### Post by Toxic64 on 2013-07-03
Hi sorry for the delay.

I never had such behaviour with Samba 4 perhaps you did something wrong when you changes your extension from ".local" to ".lan".
It seems like your domain fails on many points. Did you by any chance try to do this modification after your DC promotion? 

By the way Samba 4.0.7 is out. lots of bugs have been corrected and  few features have been added (support for MX records for example)

---

### Post by nextraa on 2013-07-03
Hi JnPson,

I installed the AD remote adminstration package and installed several of these "plugins" on my Windows 7 Ultimate client. However I cannot connect to the domain from these tools. I don't know if my Windows machine has to be part of the domain first. But like I said I'm unable to connect this Windows 7 client to my domain.

---

### Post by Toxic64 on 2013-07-03
As I said, I have never had such problems.
those definitely come from your S4 installation.

As I have no mean to know what you did during your setup, I would advise to make a fresh install.
then I can assist you in each and every step you want. or just use my script and it'll work just fine.

---

### Post by nextraa on 2013-07-03
Hi Toxic,

I started from scratch again after changing ".local" to ".lan". I installed ubuntu server again. Created the partition again. So it's a fresh install with only ".lan" as the extension. I tried working with the "old" smb.conf I found in /usr/share/samba, but that didn't work. So I removed the old smb.conf and reinstated the original smb.conf. I changed the dns forwarder to the Google DNS (8.8.8.8) in smb.conf. And I removed the Google DNS from /etc/network/interfaces as was suggested in this other tutorial [http://www.jadota.com/2013/01/installing-samba4-on-ubuntu-12-04/](http://www.jadota.com/2013/01/installing-samba4-on-ubuntu-12-04/) which follows your tutorial to a great extent.

---

### Post by Toxic64 on 2013-07-03
[FONT=arial]
you have to work with this smb.conf:[B]/usr/local/samba/etc/smb.conf

please try my script. it will automate installation and configuration. if it works, then it means you have done something wrong while following the tutorial.

Also fresh install in core mode with no selected package at the end (no BNS, no openssh server, no nothing... if you need them you'll be able to do so with the tasksel command right after.


[/B][/FONT]

---

### Post by nextraa on 2013-07-03
Okay, I'll try your scripts...

---

### Post by JnPson on 2013-07-03
nextraa, you're right, I'm not that experienced in Linux and Samba. But I know that you can still use AD Users and Computers to see what error you get. If it's working it will give the error: ```
The following domain controller could not be contacted: dc.mydomain.lan. **Permission denied. **
```

Or if it's not working: ```
The following domain controller could not be contacted: dc.mydomain.lan. **The RPC-Server is not available. **
```
But I recommend you to use Toxic64's script instead.

---

### Post by nextraa on 2013-07-03
Hopefully I can do it tonight. I will let you know.

What do I do with the samba4.conf file?

I ran the first script. I don't have time to run the second script tonight, so I will do it tomorrow.

I ran the second script. But that didn't go so well. I put my values in and I changed the time servers. During the script I saw it couldn't find my network adapter. And the DNS tests failed. Also the copying of the .conf file failed.

---

### Post by nextraa on 2013-07-05
I need to go on. I'm going to thinker with it some more today, but if I don't succeed (which is likely) I'm going to install samba3 and see if that suits my purposesses better.

Thanks anyway...

---

### Post by lingpanda on 2013-07-05
> **nextraa said:**
> Hi JnPson,

I installed the AD remote adminstration package and installed several of these "plugins" on my Windows 7 Ultimate client. However I cannot connect to the domain from these tools. I don't know if my Windows machine has to be part of the domain first. But like I said I'm unable to connect this Windows 7 client to my domain.
  
If I recall yes your Windows machine must be part of the domain to administer with RSAT.

---

### Post by Toxic64 on 2013-07-06
not a mandatory condition...

Once RSAT is installed you can choose to connect to a DC on a domain from DSA.MSC. credentials will be asked for...

---

### Post by Toxic64 on 2013-07-06
Hi , 

Sorry, I was a little busy these days. I will help you with the script

You have to change the values in the two scripts according to your needs.

In the second script, the last Variable is SHARE, I used it because my script files were on a windows share, I mounted with the mount command but you don't need to do this.

you just have to put the 3 files somewhere in a folder on your system.
Let's say you create a **/SCRIPT** folder and put the files inside
then the share value will be :

SHARE=/SCRIPT/

the Samba4.conf file is the Upstart instructions for samba to start at boot. so put it in your folder along with the script files

Be shure to reboot before you execute samba4-2.sh

If you need any help, feel free to add me to your Skype contacts, I'll be glad to helplike I did with [**[COLOR=#000000]JnPson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1778575"). (you can send me a message via skype from the forum)

---

### Post by lingpanda on 2013-07-15
I'm believe I should be able to view samba logs using RSAT(Event Viewer). I can't remember the commands needed in Samba smb.conf. Anyone?

Edit:

Found this [https://wiki.samba.org/index.php/Event_Logging](https://wiki.samba.org/index.php/Event_Logging) but I believe it may be over my head.

---

### Post by Toxic64 on 2013-07-17
Hi, 

Sorry my friend, I was so busy creating my company, that I couldn't find a single second to log on the forum.

Probably what you are looking for: [http://wiki.samba.org/index.php/Event_Logging](http://wiki.samba.org/index.php/Event_Logging)

Anyway, It won't relay malfunction or windows-like event as those rely on WMI and a set of DLLs.

I believe their only purpose is to relay custom created events.

Edit: Over your head?

---

### Post by lingpanda on 2013-07-17
> **Toxic64 said:**
> Hi, 


Edit: Over your head?

Meaning beyond my expertise. I'm Looking for a way to manage invalid login attempts and users actively logged in.

---

### Post by Aye_Cloud on 2013-08-02
Very well written, Set mine up today with a few hiccups but nothing alittle  coffee/common sense couldn't solve. Cant wait for the next one.

"skynet"
smb4 4.0.7
ubuntu "raring" 13.04

---

### Post by Toxic64 on 2013-08-04
well thanks a lot mate
I'm already on the next suject about administrating AD from windows RSAT & Admin pack.
Let me know if you have other subjects you are interested in. you can contact me via skype if needed

---

### Post by lingpanda on 2013-08-05
The Samba Wiki was updated with a Sysvol replication how to. Seems to be working so far on all 4 of my DC's. This was a big deal in my environment.

---

### Post by umaxtu2 on 2013-08-06
Should this process be any different on Ubuntu 13.04?

---

### Post by Toxic64 on 2013-08-24
No, I think It should work correctly.not tested yet though.

---

### Post by umaxtu2 on 2013-08-24
It does. I was using the desktop version which has samba preinstalled. I had to hack /etc/init/smbd.conf (thats off the top of my head, it might not be the right file) to start the version I built instead of the default one. The service command doesn't seem to like it but it starts on boot and thats all I care about.

**Edit: **I've successfully joined the domain with another computer but the admin tools refuse to work. Any ideas?

---

### Post by Toxic64 on 2013-08-26
Yep probably not doing AD mode...you start samba 4 service with the "/usr/local/samba/sbin/samba -D" command. nothing with smbd.conf.
Samba 4 will start with the upstart script that you'll find at the end of my tutorial in the correctedscript.zip downloadable file.
these scripts (once the values modified to the ones needed for your environnement) will simply install latest stable version fo samba and configure it for you.
you only need to reboot between the two scripts.

Enjoy!!!

---

### Post by umaxtu2 on 2013-08-26
Thank you for the help but the problem was that the client computer was using google for its dns, not the domain controller.

---

### Post by chuck4 on 2013-08-30
Toxic64, I followed your tutorial with good result except in one area --- which was _not_ the fault of your instruction.  The FQDN for which I am working is very long.  At the command "make" I received ERROR after ERROR and was very much puzzled.

After using Google to search the error text, I found mention of a sixteen character limit.  My domain was eighteen characters PLUS the dot and "com"  So, I changed my domain name on the server to a shorter version with twelve characters plus the dot and com.  Once I made that change all went well until time for the administrator password.  Although my password was very secure, it failed the test until I capitalized one letter and added a numeric digit.  Those were my only two problems.  

Thank you very much for your excellent work.  My samba is version 4.0.9 and seems to be working.

Chuck

---

### Post by Toxic64 on 2013-08-30
you are welcome.Thank you.

as a matter of fact, 253 characters is the maximum length of a full domain name...I don't know why it failed to accept an 18 characters domain name.

The Administrator password must be complex (Active directory default password policy on domain controllers)

password must:


[LIST]
[*]Not contain the user's account name or part of the user's full name that exceed two consecutive characters
[*]The password is at least six characters long
[*]The password must contain characters from at least three of the following four categories:
[LIST]
[*]English uppercase characters (A &#8211; Z)
[*]English lowercase characters (a &#8211; z)
[*]Base 10 digits (0 &#8211; 9)
[*]Non-alphanumeric (For example: $, #, or %)
[/LIST]
 
[/LIST]

---

### Post by chuck4 on 2013-09-01
It did seem strange to me, but I'm not the only one.  I'm using ubuntu 12.04.3 LTS   Samba4 seems to be the only program that has a problem with the hostname length.

Here's a link to a discussion about the hostname length:

[https://answers.launchpad.net/ubuntu/+source/samba/+question/150894](https://answers.launchpad.net/ubuntu/+source/samba/+question/150894)

Regardless, your tutorial is excellent!  Thanks.
Chuck

---

### Post by Toxic64 on 2013-09-02
thanks for the link.seems to be quite a bug.we'll see if they correct it.

---

### Post by Luke_KOtarba on 2013-09-10
Thanks for the guide I have some questions.

1. Once I create a user with Windows RTS do I need to link samba user to Ubuntu like in previous versions?

2. I am able to connect to my share folder when I go to map the drive. However I do not see them under windows networks. Any idea?

3. Love the Guide and Thanks

---

### Post by JnPson on 2013-09-10
As far as I know you don't have to link AD users to ubuntu.  You can't see the samba server in network neighborhood, this is annoying to me too, You have to type in *\\dc01 *to get to the server shares.  You can always connect to you shared folder after you have mapped it to your Windows computer. It is always present in the network, it's just that it isn't visible.

---

### Post by Luke_KOtarba on 2013-09-10
Ok that answers my question why I cant see samba shares in network neighborhood. But I still cant access a private folder names Luke. Below is the smb.conf file for that folder.

> [Luke]
        comment = Luke Private User folder
        path = /SAMBA_SHARE/data/PRIVATE/Luke
        read only = no
        writable = yes
        printable = yes
        browseable = yes
        valid users = luke


It tell me I have no access to this folder.

please Help

---

### Post by JnPson on 2013-09-10
I've had this problem before and I got this answer from this thread:: [http://ubuntuforums.org/showthread.php?t=2132573](http://ubuntuforums.org/showthread.php?t=2132573).

---

### Post by Toxic64 on 2013-09-11
hi, Luke and thanks for your appreciation.

*"I am able to connect to my share folder when I go to map the drive. However I do not see them under windows networks. Any idea?"*

You can see the shares from a windows machine just run **\\ServerIP**, it will ask for a login and password which will be [EMAIL="administrator@yourdomain.xxx"]administrator@yourdomain.xxx[/EMAIL] the password will be the one you set for administrator account on your samba.

Enjoy!


Also see that: [http://askubuntu.com/questions/236746/how-to-turn-on-network-discovery-and-share-between-computers-with-samba](http://askubuntu.com/questions/236746/how-to-turn-on-network-discovery-and-share-between-computers-with-samba)

---

### Post by casper4 on 2013-09-17
Hi all,

My setup is the following:

Proxmox VE 3.1

VM is:

OpenVZ ubuntu 12.04.2 64 bit

Im trying to get samba up and running on this VM and i have tried twice now.

One problem I have solved is that when ever i try to use smbclient or samba-tool i get a error saying it doesn't know the command. if i do ./smbclient or ./samba-tool it works.. don't know why that is???

So when i have installed my Samba4 i need to varify everything is working... my problem is when i get to this part:

```

[COLOR=#000000][FONT=verdana]listing administrative share will show you sysvol, netlogon shares etc....[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]/usr/local/samba/bin/smbclient -L localhost -U%[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]you should see somethin like this:[/FONT][/COLOR]




[COLOR=#000000][FONT=verdana]Sharename Type Comment [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]--------- ---- ------- [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]netlogon Disk [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sysvol Disk [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]IPC$ IPC IPC Service (Samba 4.0.5) [/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]it means your server is up and running...
[/FONT][/COLOR]
```[COLOR=#000000][FONT=verdana]

I get this errror:

```

[/FONT][/COLOR]root@DC01:/usr/local/samba/bin# ./smbclient -L localhost -U%
session setup failed: NT_STATUS_CONNECTION_REFUSED

```[COLOR=#000000][FONT=verdana]

How do i solve this?

This step also fails:

```

[/FONT][/COLOR][COLOR=#000000][FONT=verdana]now you need to check authentication[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]/usr/local/samba/bin/smbclient //localhost/netlogon -UAdministrator%"your_password" -c 'ls'[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]you should see this:[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]Domain=[MYDOMAIN] OS=[Unix] Server=[Samba 4.0.5] [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]. D 0 Fri May 17 21:40:08 2013 [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana].. D 0 Fri May 17 21:42:36 2013
[/FONT][/COLOR]
```[COLOR=#000000][FONT=verdana]

with the error:

```

[/FONT][/COLOR]root@DC01:/usr/local/samba/bin# ./smbclient //localhost/netlogon -UAdministrator%"your_password" -c 'ls'
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

```

How do i fix this????

THANKS

Casper

---

### Post by Toxic64 on 2013-09-17
> [COLOR=#000000][FONT=verdana]I get this errror:

     Code:
      
[/FONT][/COLOR]     Code:
     root@DC01:/usr/local/samba/bin# ./smbclient -L localhost -U%
session setup failed: NT_STATUS_CONNECTION_REFUSED 
[COLOR=#000000][FONT=verdana]

How do i solve this?
[/FONT][/COLOR]

Please try:

```
kinit administrator@MYDOMAIN.LAN [COLOR=#0000cd](has to be capital letters or will fail / will ask for your domain administrator password )[/COLOR] 
klist -e [COLOR=#0000ff](will display informations about the kerberos ticket you received)[/COLOR]
```

But it seems to me you messed up somewhere with Kerberos.


did you do this?

```
[FONT=arial]sudo apt-get update [COLOR=#0000cd](I generally add "&& apt-get upgrade -y" so that my server is fully up  to date)[/COLOR]
sudo apt-get install git build-essential libacl1-dev libattr1-dev libblkid-dev libgnutls-dev libreadline-dev python-dev python-dnspython gdb pkg-config libpopt-dev libldap2-dev dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev libpam0g-dev ntp
[/FONT]
```

It installs all requirement, Kerberos included.

Also you never just execute samba-tool or smbclient just like that unless you have them in your environement path. I explained it here : [http://ubuntuforums.org/showthread.php?t=2171746](http://ubuntuforums.org/showthread.php?t=2171746)

The commands are **"/usr/local/samba/bin/samba-tool" **and same for **smbclient**.
 Don't **cd** to the directory.
you have to prefix them with** "/usr/local/samba/bin/"** or it doesn't work.

---

### Post by casper4 on 2013-09-18
Hi

Yes i did run the following commands:

```

[FONT=arial]sudo apt-get update [COLOR=#0000cd](I generally add "&& apt-get upgrade -y" so that my server is fully up  to date)[/COLOR]
sudo apt-get install git build-essential libacl1-dev libattr1-dev libblkid-dev libgnutls-dev libreadline-dev python-dev python-dnspython gdb pkg-config libpopt-dev libldap2-dev dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev libpam0g-dev ntp
[/FONT]
```
During the installation I was met with some questions from Kerberos that i don't think you guide adresse. At one point there comes this blue gui like screen where Kerberos asks for domain realm and PDC and BDC i think... 
As fare as i remember i chose offerlamnet.local for realm and DC01 for both PDC and BDC.. maybe that wrong? perhaps i should just leave BDC blank since i have no BDC?

as for:
```

kinit [EMAIL="administrator@MYDOMAIN.LAN"]administrator@MYDOMAIN.LAN[/EMAIL] [COLOR=#0000cd](has to be capital letters or will fail / will ask for your domain administrator password )[/COLOR] 
klist -e [COLOR=#0000ff](will display informations about the kerberos ticket you received)
[/COLOR]
```

I got this as response, definently looks like a Kerberos issue:
```

root@DC01:~# kinit [EMAIL="administrator@OFFERLAMNET.LOCAL"]administrator@OFFERLAMNET.LOCAL[/EMAIL]
kinit: Cannot contact any KDC for realm 'OFFERLAMNET.LOCAL' while getting initial credentials
root@DC01:~# klist -e
klist: No credentials cache found (ticket cache FILE:/tmp/krb5cc_0)
root@DC01:~# 

```

Could i be because i CD to the directory that it fails on me? or will it work if you just use ./smbclient or ./samba-tool?? it looks like its working but that is from a untranied eyes perspektive :)

THANKS

Casper

---

### Post by Toxic64 on 2013-09-18
> During the installation I was met with some questions from Kerberos that  i don't think you guide adresse. At one point there comes this blue gui  like screen where Kerberos asks for domain realm and PDC and BDC i  think... 

it's in the guide that's not pdc and bdc (which don't exist in this context.) it's KDC and adminserver if you left one blank you found your problem.

please send over your /etc/krb5.conf and /usr/local/samba/etc/krb5.conf files. We ll correct the issue.


> Could i be because i CD to the directory that it fails on me? or will it work if you just use ./smbclient or ./samba-tool??

nope, not that problem. but by doing this you might encounter other problems

---

### Post by casper4 on 2013-09-18
Ok so i created a new VM and tried againg.. 

just to note i forgot to mention a perhaps very important fact I had to add 
[COLOR=#000000][FONT=Monaco]--use-ntvfs
[/FONT][/COLOR]In the end of the:

```

sudo apt-get install git build-essential libacl1-dev libattr1-dev libblkid-dev libgnutls-dev libreadline-dev python-dev python-dnspython gdb pkg-config libpopt-dev libldap2-dev dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev libpam0g-dev ntp -y
```

i don't know if that changes allot.. If i don't do that i get:

```

root@DC01:~/samba4# /usr/local/samba/bin/samba-tool domain provision --realm=offerlamnet.local --domain=OFFERLAMNET --adminpass="XXXXXXX" --server-role=dc --dns-backend=SAMBA_INTERNALYou are not root or your system do not support xattr, using tdb backend for attributes. 
not using extended attributes to store ACLs and other metadata. If you intend to use this provision in production, rerun the script as root on a system supporting xattrs.
Looking up IPv4 addresses
Looking up IPv6 addresses
No IPv6 address will be assigned
set_nt_acl_no_snum: fset_nt_acl returned zero.
ERROR(<class 'samba.provision.ProvisioningError'>): Provision failed - ProvisioningError: Your filesystem or build does not support posix ACLs, which s3fs requires.  Try the mounting the filesystem with the 'acl' option.
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/domain.py", line 398, in run
    use_rfc2307=use_rfc2307, skip_sysvolacl=False)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/provision/__init__.py", line 2042, in provision
    raise ProvisioningError("Your filesystem or build does not support posix ACLs, which s3fs requires.  Try the mounting the filesystem with the 'acl' option.")

```

Now during the Kerberos install where i get that blue background gui i wrote 
offerlamnet.local in the first box
OFFERLAMNET in the second
and the two following i wrote DC01 in both..

I ran the samba command with the full string like this:

```

/usr/local/samba/bin/samba-tool bla bla bla


/usr/local/samba/sbin/samba


/usr/local/samba/sbin/samba -V
/usr/local/samba/bin/smbclient -V


/usr/local/samba/bin/smbclient bla bla bla
```

and i still got the error... 

any advice?

THANKS

Casper

---

### Post by Toxic64 on 2013-09-18
I have my samba DC running on Proxmox 3.1 too. no probleme there.
Why did you add --use-ntvfs?
I think we might need to step up could you contact me via skype?

---

### Post by casper4 on 2013-09-18
I have send a request :)

---

### Post by l-fulgenzi on 2013-10-04
i followed the tutorial, all is fine....but i'm stuck here

> kinit [email]administrator@MYDOMAIN.LOCAL[/email]
kinit: Cannot contact any KDC for realm 'MYDOMAIN.LOCAL' while getting initial credentials


any suggestions?

---

### Post by Toxic64 on 2013-10-05
yup, You have a kerberos issue.

Check /etc/krb5.conf and /usr/local/samba/share/setup/krb5.conf

Also, you can skype me if you want me to take a look and help you troubleshoot.

---

### Post by Corey_Clarke on 2013-10-12
An excellent tutorial, sir.  Thank you!

I had a bunch of trouble here and there in getting setup, but that's mostly due to me not being much of a Linux person.

---

### Post by Toxic64 on 2013-10-12
thank you for your appreciation, Sir.

---

### Post by dreamtrick on 2013-10-20
> **l-fulgenzi said:**
> i followed the tutorial, all is fine....but i'm stuck here



any suggestions?

I had this same problem. In my case, my ubuntu installation had Bind9 installed by default, but I chose samba_internal as the tutorial said. So I had to uninstall Bind9, and afterwards it worked.

---

### Post by Toxic64 on 2013-10-20
can't see the original message.
Guess that would help though if debug is needed... ;)

---

### Post by Roswebnet on 2013-10-20
I am using now the Samba4.0.3 on Ubuntu 13.10 (default pakkage). In my provision was a BIND used as a DNS server. Working fine. No problems yet. Only the canonical forgot to define correct version of the BIND in [COLOR=red][FONT=Calibri]Vim /var/lib/samba/private/named.conf[/FONT][/COLOR]
 ```
[COLOR=#00b050][FONT=Calibri]dlz "AD DNS Zone" {[/FONT][/COLOR]
 [COLOR=#00b050][FONT=Calibri]    # For BIND 9.8.0[/FONT][/COLOR]
 [COLOR=#00b050][FONT=Calibri]    # database "dlopen /usr/lib/x86_64-linux-gnu/samba//bind9/dlz_bind9.so";[/FONT][/COLOR]
 
 [COLOR=#00b050][FONT=Calibri]    # For BIND 9.9.0[/FONT][/COLOR]
 [COLOR=#00b050][FONT=Calibri]    database "dlopen /usr/lib/x86_64-linux-gnu/samba//bind9/dlz_bind9_9.so";[/FONT][/COLOR]
 [COLOR=#00b050][FONT=Calibri]};[/FONT][/COLOR]
```

I reed somewhere that in production the BIND is more preferable choice than internal DNS. I do not have links sorry...

---

### Post by Toxic64 on 2013-10-20
you should go Samba 4.1 (it's been out for 1 week now) compile from source no problem .
 4.0.3 is quite old and can't handle replication and such.
I ve been using samba_internal in production. it's quite effective and I don't know why Bind would be better. I know it's robust etc but Samba_internal is based on MS dns so if you re going to have mixed infrastructures MS/Linux both will work fine as long as you don't use isc-dhcp-server (samba_internal won't update records at least prior to 4.0.7, didn't test since). 
that's been tested every day since the first install I did with samba 4.1

---

### Post by Toxic64 on 2013-10-20
probably your link about bind (quite old): [https://lists.samba.org/archive/samba/2012-November/170194.html](https://lists.samba.org/archive/samba/2012-November/170194.html)

---

### Post by Roswebnet on 2013-10-20
Agreed, but the 4.0.3 is tested by canonical, and should work stable.
Moreover, for test propose it's a good start point. In addition, many of LDAP related software (SOGo, OpenChange, Squid, OpenERP etc...) are good tested only with Samba 4.0.3. However, the 4.1.0 is recommended by most of software vendors with no guidance.

There is just a question: what do you need from your samba appliance?

Yeah, exactly I think this was one of the links about "greatness" of the BIND  :)

---

### Post by Toxic64 on 2013-10-20
> here is just a question: what do you need from your samba appliance?

I have a complex mixed infrastructure with AD service working just great with Samba_internal. 
AD Service integration with openfire for example has been as easy as it could be. 
So my samba appliance as pretty much the same use a standard AD would have. (directory services, Kerberos authentication, DNS, directory replication)
all is just perfect

> Agreed, but the 4.0.3 is tested by canonical, and should work stable.

Mine is 4.1 from source on Ubuntu 12.04.3 LTS no problem there. Samba 4.1 is final stable. not beta anymore

---

### Post by Roswebnet on 2013-10-20
It was a rhetorical question. 
By this question I mean if I need only test things and I would like to understand how things working than I prefer a fast installation method. However, if I would like to have a production environment with FSMO, GC and etc., I will definitely go to the 4.1.0... It seems to me we have here a versions holy war :P 

By the way, do you know something about this:

[http://ubuntuforums.org/showthread.php?t=2182061](http://ubuntuforums.org/showthread.php?t=2182061)

Thank you

---

### Post by Toxic64 on 2013-10-20
just answerd to your other post.

4.0.3 also has FSMO and GC management etc from Samba-tool.

That's not a version holy war (although I like the term) but by experience up to date products still will show your better how things work (more functions, corrected bugs, etc.. )
for instance samba-tool got a lot of improvement since 4.0.3 (process subcommand appeared in 4.0.10, domain join MEMBER also is easier than net ads etc...)

---

### Post by Bernd_Schuhmacher on 2013-10-21
Hello


At first: Many thanks for this great tutorial.

As 4.1 of samba is released is it safe to get the sources and do
```
[FONT=arial]./configure --enable-debug --enable-selftest 
make 
make install[/FONT]
```
for upgradeing. Or do I need to clean up some things first?

For the tutorial:
Is this step needed?
```
[FONT=arial]edit file [B]/usr/local/samba/share/setup/krb5.conf

[/B]and replace $(REALM) by MYDOMAIN.LAN[/FONT]
```
I forgot it when I set up and so far I could not find a problem. could it be that $(REALM) is substituted with the default_realm fomr /etc/krb5.conf?

Thanks again

---

### Post by Toxic64 on 2013-10-21
you ll have to download 4.1 to another directory like that

```
[FONT=arial]git clone -b v4-1-stable git://git.samba.org/samba.git samba41[/FONT]
```
then go to that new folder and go

```
[FONT=arial]./configure --enable-debug --enable-selftest 
make 
make install[/FONT]
```



> For the tutorial:
Is this step needed?
 	Code:
 	[FONT=arial]edit file [B]/usr/local/samba/share/setup/krb5.conf

[/B]and replace $(REALM) by MYDOMAIN.LAN[/FONT] 
I forgot it when I set up and so far I could not find a problem.  could it be that $(REALM) is substituted with the default_realm fomr  /etc/krb5.conf?

It seems it's not a problem indeed but still I keep on doing it.
we might need a broader vision to know what service exactly would need this file.

---

### Post by tibreizh29 on 2013-11-15
Hello,

I followed the tutorial and after a ./configure, make and make install, my server told me "**The**** program 'Samba' is currently not installed You can install it by typing: sudo apt-get install samba4"**.

Could someone help me understand why this message is still displayed when the manual install samba 4 went well?

thank you

---

### Post by Toxic64 on 2013-11-15
Yup , untill you append necessary paths to the environnement path configuration file, you need so prefix every single of your commands with **/usr/local/samba/bin/** or **/usr/local/samba/sbin/ **depending on the command you are trying to use.

---

### Post by Bernd_Schuhmacher on 2013-11-20
Hi

I found another two "issues" in this tutorial.
1. i think there is a little typo in this line:
> echo  domain MYDOMAIN.LAN >> /etc/resolv.conv[FONT=arial][/FONT]
it must be
> echo  domain MYDOMAIN.LAN >> /etc/resolv.conf[FONT=arial][/FONT]
2. I think the mentioned line is not needed. As "/etc/resolv.conf" is recreated by resolvconf everytime the server is restarted it will get deleted. Another point is that as far as I know the "Domain entry" in resolv.conf is deprecated in favour of "search". As we have a "dns-search" entry in "/etc/network/interface" we do not need this one.

I hope I am not on a wrong way with his.

---

### Post by Toxic64 on 2013-11-20
echo  domain MYDOMAIN.LAN >> /etc/resolv.conf ...indeed. I just corrected it. thanks. 			 		

> . I think the mentioned line is not needed. As "/etc/resolv.conf" is  recreated by resolvconf everytime the server is restarted it will get  deleted. Another point is that as far as I know the "Domain entry" in  resolv.conf is deprecated in favour of "search". As we have a  "dns-search" entry in "/etc/network/interface" we do not need this one.


according to samba wiki, it's required.

---

### Post by victor22 on 2014-02-21
> **casper4 said:**
> Hi all,

My setup is the following:

Proxmox VE 3.1

VM is:

OpenVZ ubuntu 12.04.2 64 bit

Im trying to get samba up and running on this VM and i have tried twice now.

One problem I have solved is that when ever i try to use smbclient or samba-tool i get a error saying it doesn't know the command. if i do ./smbclient or ./samba-tool it works.. don't know why that is???

So when i have installed my Samba4 i need to varify everything is working... my problem is when i get to this part:

```

[COLOR=#000000][FONT=verdana]listing administrative share will show you sysvol, netlogon shares etc....[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]/usr/local/samba/bin/smbclient -L localhost -U%[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]you should see somethin like this:[/FONT][/COLOR]




[COLOR=#000000][FONT=verdana]Sharename Type Comment [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]--------- ---- ------- [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]netlogon Disk [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sysvol Disk [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]IPC$ IPC IPC Service (Samba 4.0.5) [/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]it means your server is up and running...
[/FONT][/COLOR]
```[COLOR=#000000][FONT=verdana]

I get this errror:

```


```[/FONT][/COLOR]```
root@DC01:/usr/local/samba/bin# ./smbclient -L localhost -U%
session setup failed: NT_STATUS_CONNECTION_REFUSED

```[COLOR=#000000][FONT=verdana]

How do i solve this?

This step also fails:

```


```[/FONT][/COLOR]```
[COLOR=#000000][FONT=verdana]now you need to check authentication[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]/usr/local/samba/bin/smbclient //localhost/netlogon -UAdministrator%"your_password" -c 'ls'[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]you should see this:[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]Domain=[MYDOMAIN] OS=[Unix] Server=[Samba 4.0.5] [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]. D 0 Fri May 17 21:40:08 2013 [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana].. D 0 Fri May 17 21:42:36 2013
[/FONT][/COLOR]
```[COLOR=#000000][FONT=verdana]

with the error:

```


```[/FONT][/COLOR]```
root@DC01:/usr/local/samba/bin# ./smbclient //localhost/netlogon -UAdministrator%"your_password" -c 'ls'
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

```

How do i fix this????

THANKS

Casper

Hi I had this problem with using the ubuntu desktop and debian desktop distribution. I solved this by using the Ubuntu server.. I know im a complete scrub but the fact that the bidrectional clipboard in virtualbox doesnt seem to work, so i had to type out all the code in the terminal made it extremely tedious..

---

### Post by martel2 on 2014-03-27
What a great tutorial!
Your scripts were an excellent starting point, I have upgraded and tweaked them.
I have them here:[ATTACH]251515[/ATTACH] for everyone.
If you have any suggestions I might add them in.
Tested flawlessly on Ubuntu 12.04.4 LTS x64

---

### Post by Toxic64 on 2014-03-27
Nice man. 
Thanks

---

### Post by gladston3 on 2014-04-05
First of all, thank you so much for this great tutorial. It made it possible for me to set up my first samba AD. Everything seems to work fine so far, but I face one problem. It is more a DNS issue than a samba issue but maybe you can give me an advice anyway.
I have isc-dhcp server running on my samba dc and I am using bind-dlz as dns backend now (I started with the internal-dns but thought maybe that is causing the issue so I switched). When I connect a Windows Client (7 or 8) which is set to dhcp there is automatically created an A entry in the standard forward lookup zone. The problem is now though, that there will not be created a PTR entry in the reverse lookup zone (I created the zone of course). With a Windows dc this works fine.
I tried to google the problem but was not able to find much. There seems to be a solution with GPOs but I did not find it too elegant so I would like to know if there is any other possibility to fix this.

---

### Post by Toxic64 on 2014-04-06
Thanks for your comment mate.

AFAIK, it's not possible yet to have the PTR automatically created in the RLZ...(at least it was not possible last time I updated samba4) so you will have to use the GPO.

---

### Post by gladston3 on 2014-04-06
Thx for the fast reply (:
So I guess it is not possible with internal-DNS neither? It is really hard for me to gather such specific information and mailing lists as a source are still confusing (yes, I come from Windows (; )
So if I understand correctly, with samba4 not the dhcp is setting the A entries, but the clients themselves? That is why I have to use the GPO to tell the clients to set the PTR too?

---

### Post by curtis11 on 2014-05-03
Hey. I'm a new Ubuntu user trying to setup a Samba4 DC on a server. I have installed 12.04 LTS and have been following this guide which has been very helpful! However, when I try to provision the domain controller, I get the following error:

```
ldb: module schema_load initialization failed : No such object
ldb: module rootsdse initialization failed : No such object
ldb: module samba_dsdb initialization failed : No such object
ldb: Unable to load modules for /usr/local/samba/private/sam.ldb: (null)
sambd_connect failed
VFS connect failed!
ERROR(<class 'samba.provision.ProvisioningError'>): Provision failed -ProvisioningError: Your filesystem or build does not support posix ACLs, which s3fs requires. Try the mounting the filesystem with the 'acl' option.
File "/usr/local/samba/lib/python2.7/site-packages/samba/provision/__init__.py", line 2052, in provision raise ProvisioningError("Your filesystem or build does not support posix ACLs, which s3fs requires. Try the mounting the filesystem with the 'acl' option.")

```

When I ran the selftest all tests passed and the make and make install commands ran successfully. So, I'm not sure why I've done wrong. Since the error said that I needed to mount the filesystem using ACL, I installed ACL, following the instructions here:

[https://help.ubuntu.com/community/FilePermissions#ACL_.28Access_Control_List.29](https://help.ubuntu.com/community/FilePermissions#ACL_.28Access_Control_List.29)

Running ```
sudo mount -o remount /home
``` returned ```
/dev/sda1 on /boot type ext2 (rw,acl)
``` which to me suggests that the filesystem is now mounted using ACL. However, I tried again to provision the domain controller and got the exact same error message.

Can someone help me here? I'm not sure what else to check. Thanks!

---

### Post by Toxic64 on 2014-05-04
Hi,
did you install Samba4 for the repo or from the Git tree?
Also did you install the required dependencies mentioned at the begining of the tutorial?

Kris

---

### Post by curtis11 on 2014-05-08
> **Toxic64 said:**
> Hi,
did you install Samba4 for the repo or from the Git tree?
Also did you install the required dependencies mentioned at the begining of the tutorial?

Kris

I cloned Samba4 using Git. And yes, I installed the dependencies. I followed the steps in the guide exactly.

---

### Post by philipp9 on 2014-07-10
Nice tutorial. Everything worked as expected but I have some small problem with my domain now. Sometimes it's available and sometimes not. When I try to manage users or group policies sometimes an error occurs that says that "no information could be found because the number of procedures is not in the allowed range". This is roughly translated from german. I included the screenshot in case anyone here can provide a proper translation.

I cannot reproduce this error, currently it's random and sometimes everything works but in the next minute the domain is gone and a few seconds it's there again.

Maybe you can provide some help

[https://www.dropbox.com/s/t9t37o3f2jj66or/fehler.jpg](https://www.dropbox.com/s/t9t37o3f2jj66or/fehler.jpg)

---

### Post by meaje2 on 2014-09-03
Curtis: try the mount option user_xattr in addition to the acl option, or better yet use the ext4 filesystem with the acl and user_xattr options. 

Hope this helps,
Jeff M

---

### Post by mufid on 2014-09-04
nextraa, you're right, I'm not that experienced in Linux and Samba. hahahaha

---

### Post by andre32 on 2014-10-23
Just registered to say that even though I'm using CentOS 7, following the official samba tutorial, something was going wrong. 
Started to search for solutions and found this tutorial (which is pretty much similar to the official one - as expected).
Followed the instructions, and it worked like a charm! Still don't know what went wrong, but who cares?! It's all done now! 
So, THANK YOU!

---

### Post by Landorin on 2015-02-04
Toxic64, thank you soooo very much! I tried at least 3 different tutorials to get Samba4 up and running as domain controller and all of them failed due to errors or missing information.
Your tutorial, however, worked straight away and I'm really glad the steps were so detailed and explained what the user is actually doing. Now I got a working domain controller AND increased my linux / samba knowledge thanks to you!

Just a few questions: could you explain where exactly the NTP server is to be added within the ntp.conf file?
Also, does this tutorial actually install and configure everything that is needed for ACL?
And what is the exact command to restart samba in case I want any samba config changes to be applied without restarting the whole machine?

Thanks again!

P.S.: next step for me: learn about cups and hopefully get printers working on the samba machine. You don't happen to have written a tutorial for that? ;)

---

### Post by Adhi_Dazz on 2015-03-27
Hi Toxic64, thanks for this great tutorial,
(hope you still reading this thread :) )

I was running smooth following all steps,
but I stumble upon this command

 > smbclient //localhost/netlogon -UAdministrator%'Pa$$worD' -c 'ls'
comes out 
> Connection to \\localhost\netlogon failed - NT_STATUS_LOGON_FAILURE
any clue why its happened ?

although error with this command is working ok

> #host -t SRV _kerberos._udp.test.sg
> _kerberos._udp.4ecap.sg has SRV record 0 0 88 4ecapsvsg6.test.sg.

meanwhile the command
> #host -t SRV _ldap._tcp.test.sg comes out result
> _ldap._tcp.4ecap.sg has SRV record 0 0 389 4ecapsvsg6.test.sg.
and
> #host -t A 4ECAPSVSG6.test.sg comes out result
> _ldap._tcp.4ecap.sg has SRV record 0 0 389 4ecapsvsg6.test.sg.

could you help me out ?

Thanks

---

### Post by AQwert on 2015-04-08
Installed Samba by following this video: [https://www.youtube.com/watch?v=Rf7Hk8qWt1Q](https://www.youtube.com/watch?v=Rf7Hk8qWt1Q)
[http://ubuntuforums.org/showthread.php?t=2146198](http://ubuntuforums.org/showthread.php?t=2146198)

Need:
Configure Ubuntu Server as domain controller

But receiving errors:

Receiving error in the authentication step verification:
# smbclient //localhost/netlogon -U 'administrator'
Enter administrator's password: 
Domain=[USERVER] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
**tree connect failed: NT_STATUS_BAD_NETWORK_NAME**

==

And next also receiving error:
kinit [EMAIL="administrator@MYDOMAIN.LOCAL"]administrator@MYDOMAIN.LOCAL[/EMAIL]
**kinit: Cannot contact any KDC for realm 'MYDOMAIN.LOCAL' while getting initial credentials**
--

On the side of Win7 I applied two registrie fixes (found this on the web).
But cannot connect the station to the domain. 
Cannot even ping the domain: not the host and not the full domain host.mydomain.local
But, when placing the DNS in Win7 with IP of my server can ping the  host, but still not the domain: not host.mydomain.local and not  mydomain.local, only host unswering pings. 


Dont really understand if this is an authomated task: thus mean, that by  adding from the side of win7 station to the domain it will create the  station name authomaticaly on the side of Ubuntu Server. Or, I need  first write this station name somwhere on the side of Ubuntu Server,  give the permissions to this specific station and only than add it from  the side of Win7. 
But all this should be the next steps, presently, as I understand the problem is in correct Samba configuration

Can someone suggest the correction?

Thank you in advance!

---

### Post by Adhi_Dazz on 2015-04-09
man i think you should reinstall kerberos, don't go next step yet if you found error
do it like this :

> apt-get purge krb5-kdc krb5-admin-server libpam-krb5 krb5-user -y
REBOOT !

then install again
> apt-get install krb5-kdc krb5-admin-server libpam-krb5 krb5-user -y

then do
> sudo krb5_newrealm
enter password for Kerberos database
> sudo kadmin.local
then in
> kadmin.local : addprinc administrator
enter password for administrator
after that
> kadmin.local : quit
then
> kinit administrator
enter your administrator kerberos password just now
then 
> klist

voila !

good luck

---

### Post by AQwert on 2015-04-09
> **Adhi_Dazz said:**
> man i think you should reinstall kerberos, don't go next step yet if you found error
do it like this :


REBOOT !

then install again


then do

enter password for Kerberos database

then in

enter password for administrator
after that

then

enter your administrator kerberos password just now
then 


voila !

good luck

Hi, 
Thank you for your help!

After re-installing received errors during the installations:

```
* Starting Kerberos KDC krb5kdc                                                krb5kdc: cannot initialize realm MYADOMAIN.LOCAL - see log file for details
                                                                         [fail]
Processing triggers for ureadahead (0.100.0-16) ...
Setting up krb5-admin-server (1.12+dfsg-2ubuntu5.1) ...
 * Starting Kerberos administrative servers kadmind                             kadmind: No such file or directory while initializing, aborting
                                                                         [fail]

```

What does it mean "cannot initialize realm"?
And also the second error..

How do you think it can be solved?

---

### Post by dennis-furr on 2015-07-01
Well done on the quality of this tutorial.

I'm working within a Dev-Ops environment that has a CI capability and want to build and package Samba 4 on a build server using Jenkins.  I noticed early in the tutorial we install krb5-user.  Is this a build requirement or was it added for the convenience of the installation?

I'm considering moving the ntpd configuration up in the installation process.  This is primarily because I'm building my PoC on Banana PI and this platform doesn't have a hardware real time clock.  This seems like a safe move but I'd value your opinion.

Just a bit of background, I'm working on an Ansible playbook for deploying this solution.  I'm plagiarising your tutorial but will make sure you get an acknowledgement in the readme.

---

### Post by Toxic64 on 2015-07-01
Hi, Thanks for your feedback.

Kerberos is needed indeed or your administrator user account for the domain won't be able to authenticate against said domain. (...and probably the provision step won't work)
ntp is mandatory as AD Domain controllers rely on ntp to synchronise their data so a 5 minutes gap and replication won't work(along with a bunch of other things).
Also, you could add this to your Bpi : [http://tinyonestore.com/blogs/blog/18079459-banana-pi-has-a-new-add-on-module-bpi-rtc-real-time-clock-for-the-banana-pi-computer-board](http://tinyonestore.com/blogs/blog/18079459-banana-pi-has-a-new-add-on-module-bpi-rtc-real-time-clock-for-the-banana-pi-computer-board)

Please feel free to plagiarise as much as you want.

---

### Post by dennis-furr on 2015-07-03
I'm afraid I wasn't terribly clear so I'll try again.  I have it in mind to build and package Samba v4 on a build server then deploy the resulting .deb to my PoC.  This is primarily intended to be a method I can reuse as newer versions of Samba are released over the life-cycle of my ADCs.  I want to play with federation so I might end up with a few of these.  The question is about whether I need to have krb5-user installed in my build environment or if we think it will build without it.  Certainly I'll install both krb5-user and ntpd on the target but I'll implement ntpd early in the build instead of doing it at the end of the implementation process.

---

### Post by dennis-furr on 2015-07-03
I've worked it out or at least worked out my dependencies by referring to the Samba instructions for building from source, not that it matters.  It appears that there is a package ([http://packages.ubuntu.com/precise/samba4](http://packages.ubuntu.com/precise/samba4)) for this so we don't have to go through the pain of "rolling our own".  This would be a great alternative and would have saved me some time but I had a bad case of target fixation around compiling from source.  I'll test this out on an AMD64 VM first as I don't see a package for ARM and I may very well end up compiling and packaging after all.

---

### Post by Deeboxi on 2015-10-04
Hello, 
Thank you for the tutorial and fellow member's suggestions. 
I had installed Samba 4.2 on Ubuntu 12.04 and it worked peferctly for a year until i upgraded to Ubuntu 14.04. I tried to make it work for several days and finally uninstalled samba 4.2 by 'make uninstall' command as suggested throughout various forums. Since then i installed Samba 4.4 clone from Git on Ubuntu server 14.04, and have been struglling to make it work since. 

having read all the threads, i am currently experiencing the same problem as per nextraa penultimate  post of which he indicated that he solved the problem, can you please  detail how you solved it. 

One more point to clarify, i can't seem to ping the gateway and our LAN pcs but can ping the internet. 
It seems i have a dns issue, which other files appart from smb.conf, /etc/krb5.conf, /etc/network/interfaces, /etc/resolve.conf, /etc/hosts should i look into

Anyone please help, its been a week trying to sort this thing out. Thanking you in advance.


 thank you

---

### Post by Christopher_Angulo on 2015-10-09
This is a great tutorial, the only part that tripped me up was installing SAMBA4, it did not work installing it as SUDO, It only worked when I did it as SU.

The problem I have right now and I am not sure if it was addresses becaue this thread is long, and I am lazy, but when I was going through the section updating the host file, I ran into a problem on the last step.  The message I get is this:

Code:  host -t A dco1.mydomain.lan

response:  dco1.mydomain.lan is an alias for ghs.googlehosted.com
ghs.googlehosted.com has address of x.x.x.x

I changed the names to protect the innocent, but the issue is that Google hosts my domain, and I want them to still host the website, but I also want to use my domain on my local lan as well.

I am thinking I need to add an A record to Googlehosted?  but just wanted to check here first.  Thanks for your help.

---

### Post by Deeboxi on 2015-10-10
Hello again,
I re-provisioned samba and now everything works except that i still can't seem to ping from the server the **gateway** and our **LAN PCs,** but can ping the internet 

I think i am nearly there, someone please rescue me.

Thanks in advance

---

### Post by lingpanda on 2015-10-21
> **Deeboxi said:**
> Hello again,
I re-provisioned samba and now everything works except that i still can't seem to ping from the server the **gateway** and our **LAN PCs,** but can ping the internet 

I think i am nearly there, someone please rescue me.

Thanks in advance

Do you still have this issue? If so can you post your network settings from '/etc/network/interfaces'?

---

### Post by Deeboxi on 2015-10-26
Thank you for the response Lingapanda, yes i still have the same issue

here is my **/etc/networking/interfaces**
[FONT=arial]address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1 
dns-nameservers 192.168.1.3 8.8.8.8 (we use our server as DNS + google DNS as secondary DNS)
dns-search mydomain.co.com

**/etc/hosts**
127.0.0.1 localhost
192.168.1.3 Server1.mydomain.co.com Server1

[B]/etc/hostname
[/B]Server1

**/etc/resolv.con**f
[/FONT]nameserver 192.168.1.3
dns-search  mydomain.co.com

---

### Post by lingpanda on 2015-10-26
This won't have any affect on your issue but you should set your hostname to your FQDN(ie. Server1.mydomain.co.com)

So while logged in locally or via SSH you can't ping IP 192.168.1.1? Have you verified you can ping your gateway from any other device? What do you mean you can ping the internet?

---

### Post by Deeboxi on 2015-10-27
Thanks again,
Yes I can ping the gateway from the other workstations, When i said i can ping the internet I meant i can ping all the addresses in the internet, e.g. yahoo.com, cnn.com, bbc.co.uk etc.

The problem i am having is pinging from the ubuntu server to gateway (192.168.1.1) and other workstations... I can not ping this server from workstations either


Will correct the hostname to: server1.mydomain.com and see what happens


I am really puzzled why this wont work

---

### Post by Deeboxi on 2015-11-01
Thank you for the help, I changed the server ip to a high address  xxx.xxx.xxx.155, i am now ablee to ping the LAN and can ping the  gateway, thanks to [**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") for the hint.

There are two problems now:
1. Ounce i reboot the machine i have to change the IP adress again for it to work again.
2. host -t A mydomain.com gives out the result/record of the old IP addresses.

---

### Post by lingpanda on 2015-11-03
You have what appears to be a network issue and not a Samba related issue. I think. I'm of little help in this regard. 

hots -t A is giving out your old IP because it's not updated in your DNS server.

---

### Post by Deeboxi on 2015-11-08
If i change the IP address to any unreserved DHCP addresses (e.g.  192.168.1.10) i am able to connect and can ping both ways but the  problem is that the samba retains the old dns records(192.168.1.3), if i  go back to the ip address (192.168.1.3) then i can't ping nor resolve  the local dns. its a catch 22.

Which files in Samba directories can i look into.

Anyone with an idea what i can do to resolve this, its been a while

Thank you

---

### Post by Deeboxi on 2015-11-10
Solved, i found out that it was Pluto that was hogging the IP address, disabled it now everything is fine

---

### Post by Christopher_Angulo on 2016-05-20
Just an update for Ubuntu 16.04LTS

When you get to:

git clone -b 

You will want to use a newer version of Samba, as I write this it is version 4.4.3  I found if you use the current command given in this tutorial it will fail on make. so the code should be:

```
git clone -b v4-3-stable git://git.samba.org/samba.git samba4
```[FONT=arial]I will add any other comments on possible changes for 16.04LTS if I find any.
[/FONT]

---

### Post by cbr179 on 2016-07-24
> **nextraa said:**
> Also DNSupdates doesn't work:

root@ubuntu:~# /usr/local/samba/sbin/samba_dnsupdate --verbose
IPs: ['192.168.178.8']
Looking for DNS entry A present.lan 192.168.178.8 as present.lan.
Failed to find DNS entry A present.lan 192.168.178.8
Looking for DNS entry A ubuntu.present.lan 192.168.178.8 as ubuntu.present.lan.
Failed to find DNS entry A ubuntu.present.lan 192.168.178.8
Looking for DNS entry A gc._msdcs.present.lan 192.168.178.8 as gc._msdcs.present.lan.
Failed to find DNS entry A gc._msdcs.present.lan 192.168.178.8
Looking for DNS entry CNAME  f4f59ff6-83dc-4f1a-96da-0d500c948555._msdcs.present.lan  ubuntu.present.lan as  f4f59ff6-83dc-4f1a-96da-0d500c948555._msdcs.present.lan.
Failed to find DNS entry CNAME f4f59ff6-83dc-4f1a-96da-0d500c948555._msdcs.present.lan ubuntu.present.lan
Looking for DNS entry SRV _kpasswd._tcp.present.lan ubuntu.present.lan 464 as _kpasswd._tcp.present.lan.
Failed to find DNS entry SRV _kpasswd._tcp.present.lan ubuntu.present.lan 464
Looking for DNS entry SRV _kpasswd._udp.present.lan ubuntu.present.lan 464 as _kpasswd._udp.present.lan.
Failed to find DNS entry SRV _kpasswd._udp.present.lan ubuntu.present.lan 464
Looking for DNS entry SRV _kerberos._tcp.present.lan ubuntu.present.lan 88 as _kerberos._tcp.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _kerberos._tcp.dc._msdcs.present.lan ubuntu.present.lan 88 as _kerberos._tcp.dc._msdcs.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.dc._msdcs.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV  _kerberos._tcp.default-first-site-name._sites.present.lan  ubuntu.present.lan 88 as  _kerberos._tcp.default-first-site-name._sites.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV  _kerberos._tcp.default-first-site-name._sites.dc._msdcs.present.lan  ubuntu.present.lan 88 as  _kerberos._tcp.default-first-site-name._sites.dc._msdcs.present.lan.
Failed to find DNS entry SRV _kerberos._tcp.default-first-site-name._sites.dc._msdcs.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _kerberos._udp.present.lan ubuntu.present.lan 88 as _kerberos._udp.present.lan.
Failed to find DNS entry SRV _kerberos._udp.present.lan ubuntu.present.lan 88
Looking for DNS entry SRV _ldap._tcp.present.lan ubuntu.present.lan 389 as _ldap._tcp.present.lan.
Failed to find DNS entry SRV _ldap._tcp.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _ldap._tcp.dc._msdcs.present.lan ubuntu.present.lan 389 as _ldap._tcp.dc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.dc._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _ldap._tcp.gc._msdcs.present.lan ubuntu.present.lan 3268 as _ldap._tcp.gc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.gc._msdcs.present.lan ubuntu.present.lan 3268
Looking for DNS entry SRV _ldap._tcp.pdc._msdcs.present.lan ubuntu.present.lan 389 as _ldap._tcp.pdc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.pdc._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV  _ldap._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan  389 as _ldap._tcp.default-first-site-name._sites.present.lan.
Failed to find DNS entry SRV _ldap._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV  _ldap._tcp.default-first-site-name._sites.dc._msdcs.present.lan  ubuntu.present.lan 389 as  _ldap._tcp.default-first-site-name._sites.dc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.default-first-site-name._sites.dc._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV  _ldap._tcp.default-first-site-name._sites.gc._msdcs.present.lan  ubuntu.present.lan 3268 as  _ldap._tcp.default-first-site-name._sites.gc._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.default-first-site-name._sites.gc._msdcs.present.lan ubuntu.present.lan 3268
Looking for DNS entry SRV  _ldap._tcp.0ca37e40-b704-4539-9694-c828038af196.domains._msdcs.present.lan  ubuntu.present.lan 389 as  _ldap._tcp.0ca37e40-b704-4539-9694-c828038af196.domains._msdcs.present.lan.
Failed to find DNS entry SRV _ldap._tcp.0ca37e40-b704-4539-9694-c828038af196.domains._msdcs.present.lan ubuntu.present.lan 389
Looking for DNS entry SRV _gc._tcp.present.lan ubuntu.present.lan 3268 as _gc._tcp.present.lan.
Failed to find DNS entry SRV _gc._tcp.present.lan ubuntu.present.lan 3268
Looking for DNS entry SRV  _gc._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan  3268 as _gc._tcp.default-first-site-name._sites.present.lan.
Failed to find DNS entry SRV _gc._tcp.default-first-site-name._sites.present.lan ubuntu.present.lan 3268
Traceback (most recent call last):
  File "/usr/local/samba/sbin/samba_dnsupdate", line 506, in <module>
    get_credentials(lp)
  File "/usr/local/samba/sbin/samba_dnsupdate", line 119, in get_credentials
    creds.get_named_ccache(lp, ccachename)
RuntimeError: kinit for UBUNTU$@PRESENT.LAN failed (Cannot contact any KDC for requested realm)

> **nextraa said:**
> Found the problem. I pointed SAMBA to my router IP as a DNS name server. But this wasn't correct. So I pointed SAMBA to the server itself and then the problem was solved.

Hi nextraa,
I,m a new member and a newbie in linux. When i setup ubuntu, i have a same your error but i don't know fix. Please help me.
Thanks

---

### Post by sangotunhienst on 2016-07-25
When i bought new computer, The OS default is Ubuntu but I cant customize it :(

---

