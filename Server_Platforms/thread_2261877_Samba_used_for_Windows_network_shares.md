---
title: "Samba used for Windows network shares"
date: 2015-01-21
forum: Server Platforms
---

### Post by jason166 on 2015-01-21
Hey all,

I have recently taken over administration duties for my department, and I am trying to replicate some functionality they had previously on our new server.

Basically, all users only login to Windows machines using AD for verification. If it is their first login, a directory should be created for them on the Linux machine, and connected as their personal network drive. If they have previously logged in, it should just reconnect them to their directory.

I was trying to replicate the Samba config from the old server, but the config files seem to have a very different internal layout. I am unsure how to proceed.

Old samba version - 3.4.13
New samba version - 4.1.6-Ubuntu


Any help would be greatly appreciated.

---

### Post by lingpanda on 2015-01-21
Are you trying to create home folders?

---

### Post by jason166 on 2015-01-22
Yes. In the user's AD settings, it connects to \\[server]\homes for their 'Home Folder'.

---

### Post by lingpanda on 2015-01-23
> **jason166 said:**
> Yes. In the user's AD settings, it connects to \\[server]\homes for their 'Home Folder'.

OK is this a new Samba 4.1.6 install or did you upgrade the Samba 3.4.13 server? Can you post your smb.conf file?

---

### Post by darkod on 2015-01-23
The smb.conf is not that different. You should be able to copy paste most settings from old one.
If the old server had the same homes share definitely post its definition so people can have a look. In most cases it should work if you copy it into the new smb.conf.
What you can also do is make a copy of the default samba4 smb.conf so that you can always check what it said before you started changing it.

---

### Post by bab1 on 2015-01-23
> **jason166 said:**
> Hey all,

I have recently taken over administration duties for my department, and I am trying to replicate some functionality they had previously on our new server.

Basically, all users only login to Windows machines using AD for verification. If it is their first login, a directory should be created for them on the Linux machine, and connected as their personal network drive. If they have previously logged in, it should just reconnect them to their directory.

I was trying to replicate the Samba config from the old server, but the config files seem to have a very different internal layout. I am unsure how to proceed.

Old samba version - 3.4.13
New samba version - 4.1.6-Ubuntu


Any help would be greatly appreciated.
It is not at all clear what you're trying to replicate.  

If you are going to continue to use a Windows server for AD then the Samba4 server should be configured as a "standalone" server just as you would a Samba3 server (not a PDC).  Both of these versions of Samba configure the *smbd* and *nmbd* daemons (processes) via the the /etc/samba/smb.conf file.  I use the sae smb.conf file on my Samba4 standalone file servers as I do on my soon to be retired Samba3 file servers.

At the present time if you are configuring Samba4 as the AD for your network you should not serve files (create shares) on that host.  This is due to conflicts between the daemon *samba* (Samba4 AD process) and the *smbd* and *nmbd* file sharing daemons.  The Samba devs are working to cure this problem.  So for right now if you want to use Samba4 as both the AD and sharing of files you should use 2 machines.  One for AD and another for file sharing.

---

### Post by jason166 on 2015-01-26
Sorry, I wasn't able to check this for the last few days. What I meant by the internal layout is that the commented instructions are very different. As an example, the Instructions for the 'Realm' directive aren't anywhere to be found in the new config file.

Here is the testparm for the old server:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
Press enter to see a dump of your service definitions

[global]
        workgroup = MWD
        realm = [Internal Realm]
        server string = Nemo Samba File Server
        security = ADS
        allow trusted domains = No
        log file = /var/log/samba/%m.log
        max log size = 50
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        local master = No
        domain master = No
        dns proxy = No
        wins server = [Internal Addresses]
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        template shell = /bin/bash
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        hosts allow = [Internal Address Pool], 10., 192.168., 127.
        cups options = raw

[homes]
        comment = Home Directories
        valid users = %D\%S, %S, IIT\%S
        read only = No
        create mask = 0664
        directory mask = 0775
        browseable = No
        browsable = No

[printers]
        comment = All Printers
        path = /usr/spool/samba
        printable = Yes
        browseable = No
        browsable = No

---

### Post by jason166 on 2015-01-26
Alright, I tried using the same config file. When I tried to change the setting to the new server in AD, I got an error message.

---------------------------
Active Directory Domain Services
---------------------------
The home folder could not be created because: Configuration information could not be read from the domain controller, either because the machine is unavailable, or access has been denied.


Not sure how to proceed.

Thanks.

---

### Post by jason166 on 2015-01-26
Sorry to keep posting, but I keep finding stuff about this. One comment I found said that I needed to join to the domain, so I did that. I still get an error trying to set the home directory setting, but it has changed now.

---------------------------
Active Directory Domain Services
---------------------------
The \\[server]\homes home folder was not created because you do not have create access on the server. The user account has been updated with the new home folder value but you must create the directory manually after obtaining the required access rights.
---------------------------
OK   
---------------------------

I tried messing with the folder permissions a bit, but it didn't help.

---

### Post by lingpanda on 2015-01-26
> **jason166 said:**
> Sorry to keep posting, but I keep finding stuff about this. One comment I found said that I needed to join to the domain, so I did that. I still get an error trying to set the home directory setting, but it has changed now.

---------------------------
Active Directory Domain Services
---------------------------
The \\[server]\homes home folder was not created because you do not have create access on the server. The user account has been updated with the new home folder value but you must create the directory manually after obtaining the required access rights.
---------------------------
OK   
---------------------------

I tried messing with the folder permissions a bit, but it didn't help.

For starters the wiki for Samba will explain how to configure and join a member server to a domain.

[https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server](https://wiki.samba.org/index.php/Setup_a_Samba_AD_Member_Server)

I'm going to assume you have done this successfully? You also can reference the wiki on how to create home folders.

[https://wiki.samba.org/index.php/Setting_up_a_home_share](https://wiki.samba.org/index.php/Setting_up_a_home_share)

I would confirm you have successfully joined the server to your domain and it shows up in ADUC module. After that carefully read the wiki on home folders. Document the first step that fails and report back.

---

### Post by darkod on 2015-01-26
Just to add, as you can see in the first link lingpanda posted, DO NOT use the samba-tool join option. If you joined it like that, it will not work. Remove the server name from ADUC in case it is there, and try again. Not sure if you need to reinstall samba or the server to delete the samba-tool settings it might have done.

You have to add a member server as explained in their wiki, at this moment...

---

### Post by jason166 on 2015-01-27
I went through the first link, and I had some problems at the 'Testing the Winbind User/Group Mapping' section.

I can see my domain users/groups with the wbinfo command, but the other commands are not working.
If I try to set permissions or use the id command, I get 'no such user'.

The instructions said that I should configure /etc/nsswitch.conf, but that didn't help. Text of that file:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by lingpanda on 2015-01-28
> **jason166 said:**
> I went through the first link, and I had some problems at the 'Testing the Winbind User/Group Mapping' section.

I can see my domain users/groups with the wbinfo command, but the other commands are not working.
If I try to set permissions or use the id command, I get 'no such user'.

The instructions said that I should configure /etc/nsswitch.conf, but that didn't help. Text of that file:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Did you remember to go into ADUC and assign a UID/GID to all users or groups that will have access to your member server? I would verify you have give Domain Users and Domain admin groups a GID. You may need to enable Advanced Features uhnder the view tab. You will then see the 'UNIX Attributes' tab under the users properties. Make sure you assign a value you have in your 

idmap config SAMDOM:range = 10000-99999

Look at the following link under 'Administer Unix Attributes In Active Directory'

[https://wiki.samba.org/index.php/Using_RFC2307_on_a_Samba_DC](https://wiki.samba.org/index.php/Using_RFC2307_on_a_Samba_DC)

You should then be able to use 


# **id DomainUser**

# **getent passwd**

# **getent group**

# **chown DomainUser:DomainGroup file**

# **chgrp DomainGroup file**

etc.

---

### Post by jason166 on 2015-01-28
I checked the 'Unix Attributes', and some users have them enabled and some don't. I can't use those commands on either. 

  I also checked the commands from the old server, and they work correctly. There has to be some configuration difference that I'm not seeing. Are there any other config files that govern this type of interaction?    

I did have to install winbind partway through. Perhaps there is a setting there that can cause this?     

J

---

### Post by lingpanda on 2015-01-29
> **jason166 said:**
> I checked the 'Unix Attributes', and some users have them enabled and some don't. I can't use those commands on either. 

  I also checked the commands from the old server, and they work correctly. There has to be some configuration difference that I'm not seeing. Are there any other config files that govern this type of interaction?    

I did have to install winbind partway through. Perhaps there is a setting there that can cause this?     

J

How did you install Samba? What packages have you installed? Can you verify that the following three services are running?

```
service windbind status
```
```
service smbd status
```
```
service nmbd status
```

To be honest I had some trouble setting up Samba as a member server on Ubuntu and had to switch to Debian Wheezy. I could send you a tutorial if you wanted to give it a try.

---

### Post by jason166 on 2015-01-29
I believe I just used apt-get install samba. 

I checked and all three of those services are running.

Anything else stand out as things to check?

---

### Post by lingpanda on 2015-01-29
> **jason166 said:**
> I believe I just used apt-get install samba. 

I checked and all three of those services are running.

Anything else stand out as things to check?

I wonder if you are missing some dependencies. This is recommend to install on Debian/Ubuntu

[h=4]Debian / Ubuntu[/h] # apt-get install build-essential libacl1-dev libattr1-dev \
   libblkid-dev libgnutls-dev libreadline-dev python-dev libpam0g-dev \
   python-dnspython gdb pkg-config libpopt-dev libldap2-dev \
   dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev acl

---

### Post by jason166 on 2015-02-05
Sorry, I haven't been able to get back to this. I installed the listed packages, and the problem still persists.
I noticed kerberos in that list; should I set that up if I'm not looking to allow direct logins?

I think next I will remove the server and rejoin it to the domain to see if that does anything. Other than that, I am at a loss.

---

