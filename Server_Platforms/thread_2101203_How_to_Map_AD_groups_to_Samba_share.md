---
title: "How to Map AD groups to Samba share"
date: 2013-01-04
forum: Server Platforms
---

### Post by sunnysthakur on 2013-01-04
I am setup a samba share server which is authenticating from Active Directory.

I am able to access the share with AD user but not able to access when group defined in "valid users" parameters.

below are the steps i performed.

**_In smb.conf_**

**[global]**
workgroup = QASLABS
password server = WIN-60I6H2BG237.qaslabs.net
realm = QASLABS.NET
preferred master = no
security = ADS
idmap backend = ad
idmap uid = 100-20000000
idmap gid = 100-20000000
winbind separator = +
template shell = /bin/bash
winbind use default domain = true
winbind offline logon = false
preferred master = no
server string = Linux Test Machine
encrypt passwords = yes
log level = 3
log file = /var/log/samba/%m
max log size = 50
printcap name = cups
printing = cups
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind nested groups = yes
netbios name = smbad
hosts allow = 127.0.0.1 192.16.17.0/24
passdb backend = tdbsam
template homedir = /home/%U
winbind nss info = rfc2307

**[Data]**
[COLOR="RoyalBlue"]comment = Directory for storing Data
path= /opt/data
valid users = @NETWORK+itadmin NETWORK+testadmin
#valid users = @"QASLABS.NET\\itadmin"
writeable = yes
browseable=yes
create mask = 775
directory mask = 775
hosts allow = 127.0.0.1 192.16.17.0/24[/COLOR]

**In /etc/nsswitch.conf **

passwd: files winbind
shadow: files winbind
group: files winbind
hosts: files dns wins
bootparams: nisplus [NOTFOUND=return] files
ethers: db files
netmasks: files
networks: files
protocols: db files
rpc: files
services: files
netgroup: files
publickey: nisplus
automount: files
aliases: files nisplus

On executing the wbinfo -u i am getting the user list from AD

[B][root@smbad ~]# wbinfo -u
[/B]administrator
guest
krbtgt
testdev
testadmin
testhr
testqa
testit
testcmt
testsupp
testituser

On executing the wbinfo -u i am getting the user list from AD. But groups i created on AD is not displaying in this list [i.e itadmin]

[root@smbad ~]# wbinfo -g
BUILTIN+administrators
BUILTIN+users
SMBAD+itadmin
domain computers
domain controllers
domain admins
domain users
domain guests
group policy creator owners
read-only domain controllers
dnsupdateproxy
cert publishers
ras and ias servers
allowed rodc password replication group
denied rodc password replication group
dnsadmins
schema admins
enterprise admins
enterprise read-only domain controllers

Please help on how to map AD group to samba so that group permissions can be setup on samba

---

### Post by luvshines on 2013-01-04
Does the group you are trying in 'valid users' resolve to a GID ```
#try this command
getent group QASLABS.NET+itadmin
```

The wbinfo -g shows that the itadmin has been defined as group in the local domain SMBAD and not the AD domain.
How did you define the group in AD ?

---

### Post by sunnysthakur on 2013-01-05
Thanks luvshines
When executing getent group QASLABS.NET+itadmin it shows me null result and goes to next prompt.

[root@smbad ~]# getent group QASLABS.NET+itadmin
[root@smbad ~]#

---

### Post by luvshines on 2013-01-06
How did you add the group in AD ?

---

### Post by sunnysthakur on 2013-01-07
I just created a users/groups on AD using dsa.msc. I am using Win 2008 r2 ent edition.

---

### Post by sunnysthakur on 2013-01-09
After changing the parameters in /etc/smb.conf i am able to view users/groups i created on AD.

**/etc/samba/smb.conf**

workgroup = QASLABS
server string = Samba Server Version %v
password server = adserver.qaslabs.net
realm = QASLABS.NET
preferred master = no
security = ADS
;idmap backend = ad
idmap uid = 500-20000000
idmap gid = 500-20000000
winbind separator = +
template shell = /bin/bash
winbind use default domain = true
winbind offline logon = false
preferred master = no
encrypt passwords = yes
log level = 3
log file = /var/log/samba/%m
max log size = 50
printcap name = cups
printing = cups
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind nested groups = yes
;netbios name = smbad
hosts allow = 127.0.0.1 192.16.17.0/24
passdb backend = tdbsam
template homedir = /home/%U
;winbind nss info = rfc2307

On executing the wbinfo i am able to view the AD users created by me.

[root@smbad samba]# wbinfo -u
administrator
guest
krbtgt
[COLOR="Blue"]tlit
usrit
tladmin
usradmin
tlcmt
usrcmt
tldev
usrdev
tlhr
usrhr
tlqa
usrqa
tlsupp
usrsupp[/COLOR]

and on executing the wbinfo with -g i am able to view the AD groups created by me.

[root@smbad samba]# wbinfo -g
BUILTIN+administrators
BUILTIN+users
domain computers
domain controllers
schema admins
enterprise admins
cert publishers
domain admins
domain users
domain guests
group policy creator owners
ras and ias servers
allowed rodc password replication group
denied rodc password replication group
read-only domain controllers
enterprise read-only domain controllers
dnsadmins
dnsupdateproxy
[COLOR="blue"]itadmin
ituser
admadmin
adminuser
cmtadmin
cmtuser
devadmin
devuser
hradmin
hruser
qaadmin
qauser
suppadmin
suppuser[/COLOR]

I am also able to test the ad users with password

[root@smbad samba]# wbinfo -a tladmin%Password1
plaintext password authentication succeeded
challenge/response password authentication succeeded

But now the issue is when i am accessing the samba share using these usernames i am not able to login to share and below error is coming in logs file.

[COLOR="Red"]  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2013/01/10 02:04:28, 3] smbd/sec_ctx.c:pop_sec_ctx(356)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2013/01/10 02:04:28, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [itusr] -> [itusr] FAILED with error NT_STATUS_NO_SUCH_USER
[2013/01/10 02:04:28, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
[2013/01/10 02:04:28, 3] smbd/process.c:timeout_processing(1382)
  timeout_processing: End of file from client (client has disconnected).
[2013/01/10 02:04:28, 3] smbd/sec_ctx.c:set_sec_ctx(241)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0[/COLOR]

Also on login to the AD user from putty it is not accepting passwords.

[admin@smbad ~]$ su tladmin
Password:
su: incorrect password

Where as on login to AD user from putty from root account i am able to login [Password not prompted from switching from root user to AD user]

Please help me on this.

Thanks in advance..

---

### Post by luvshines on 2013-01-09
Sorry, I was not able to respond earlier.

I was thinking along the same lines of the idmapping backend you were trying to use. But I didn't know that commenting out the 'ad' backend and switching to the default 'tdb' backend will resolve that issue.

For the newly reported 2 issues:
a) In the first one, I think you are committing a typo. The username is 'ituser' but you are trying 'itusr' which is evident from the logs

b) For the second issue, did you setup sshd PAM file to allow logins for AD account ?

---

### Post by sunnysthakur on 2013-01-23
Hello Luvshines

Thanks for your prompt help.
This seems to be fixed now and i am able to view AD users and groups on wbinfo -u and wbinfo -g.

You are right i think backend as tdb resolve this issue.

I used below lines on smb.conf

[HTML]        workgroup = QASLABS
        server string = Samba Server Version %v
        password server = adserver.qaslabs.net
        realm = QASLABS.NET
        preferred master = no
        security = ADS
        ;idmap backend = ad
        idmap uid = 500-20000000
        idmap gid = 500-20000000
        winbind separator = +
        template shell = /bin/bash
        winbind use default domain = true
        winbind offline logon = false
        preferred master = no
        encrypt passwords = yes
        log level = 3
        log file = /var/log/samba/%m
        max log size = 50
        printcap name = cups
        printing = cups
        winbind enum users = yes
        winbind enum groups = yes
        winbind use default domain = yes
        winbind nested groups = yes
        ;netbios name = smbad
        hosts allow = 127.0.0.1 192.16.17.0/24
        passdb backend = tdbsam
        template homedir = /home/%U[/HTML]

---

### Post by rocoulon on 2013-01-23
interesting post.

[posicionamiento]("http://www.posicionamientobuscadores.cl/")

[mariachis a domicilio]("http://www.mariachisensantiago.cl/")

[recuperacion de datos]("http://www.gramaweb.cl/discoduro.php")

---

### Post by mackarenax3 on 2013-01-24
conozca informacion de:

[departamentos amoblados providencia](http://www.chileamoblados.cl/category/providencia/) 
[cilindros hidraulicos](http://www.mslcilindros.cl/cilindros)
[constitucion de sociedad](http://www.constituyendo.cl/a/constitucion-de-sociedades)

---

