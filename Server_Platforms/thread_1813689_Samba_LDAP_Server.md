---
title: "Samba LDAP Server"
date: 2011-07-28
forum: Server Platforms
---

### Post by maverickaddicted on 2011-07-28
Hello Everyone,

I have installed ubuntu 11.04 server edition on my server. Now, I want to create the SAMBA LDAP server. I have followed several guide on the Internet, but it is not working.
I am very new to linux and not able to tackle the problem as needed. I need a guide, so please help me.

In my office, there are 10 ubuntu machines and 10 windows machines (XP, Vista and Seven).

---

### Post by akha666 on 2011-07-28
Hello
I spend 2 weeks to build my own PDC server and folder redirection with Ubuntu 11.04
at the end I have done it , follow this guide [here at this link]("http://www.server-world.info/en/note?os=Ubuntu_11.04&p=samba&f=4")
but first you have to change your server hostname and add FQDN
If you did it the new LDAP installation will work fine with, as happen with me
I hope you make it

---

### Post by maverickaddicted on 2011-07-28
Thank You for helping.
I already followed this guide but it gives me error - 

**root@openserver:/etc/samba#** smbldap-groupadd -a admindomain
Cannot confirm gidNumber 1000 is free: checking for the next one
Cannot confirm gidNumber 1001 is free: checking for the next one
Cannot confirm gidNumber 1002 is free: checking for the next one
Cannot confirm gidNumber 1003 is free: checking for the next one
Cannot confirm gidNumber 1004 is free: checking for the next one
Cannot confirm gidNumber 1005 is free: checking for the next one
Cannot confirm gidNumber 1006 is free: checking for the next one
Cannot confirm gidNumber 1007 is free: checking for the next one
Cannot confirm gidNumber 1008 is free: checking for the next one
Cannot confirm gidNumber 1009 is free: checking for the next one
**root@openserver:/etc/samba#** smbldap-useradd -am -g admindomain admindomain
Cannot confirm uidNumber 1000 is free: checking for the next one
Cannot confirm uidNumber 1001 is free: checking for the next one
Cannot confirm uidNumber 1002 is free: checking for the next one
Cannot confirm uidNumber 1003 is free: checking for the next one
Cannot confirm uidNumber 1004 is free: checking for the next one
Cannot confirm uidNumber 1005 is free: checking for the next one
Cannot confirm uidNumber 1006 is free: checking for the next one
Cannot confirm uidNumber 1007 is free: checking for the next one
Cannot confirm uidNumber 1008 is free: checking for the next one
Cannot confirm uidNumber 1009 is free: checking for the next one
**root@openserver:/etc/samba#** smbldap-passwd admindomain
Changing UNIX and samba passwords for admindomain
New password: 
Retype new password: 
r**oot@openserver:/etc/samba#** su - domainadmin
Unknown id: domainadmin
**root@openserver:/etc/samba# **

**My smb.conf file is **

# Global parameters
[global]
    workgroup = NEXUSONE.LOCAL
    netbios name = openserver
    security = user
    enable privileges = yes
    #interfaces = 192.168.5.11
    #username map = /etc/samba/smbusers
    server string = Samba Server %v
    #security = ads
    encrypt passwords = Yes
    #min passwd length = 3
    #pam password change = no
    #obey pam restrictions = No

    # method 1:
    #unix password sync = no
    #ldap passwd sync = yes

    # method 2:
    unix password sync = yes
    ldap passwd sync = yes
    passwd program = /usr/sbin/smbldap-passwd -u "%u"
    passwd chat = "Changing *\nNew password*" %n\n "*Retype new password*" %n\n"

    log level = 0
    syslog = 0
    log file = /var/log/samba/log.%U
    max log size = 100000
    time server = Yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    mangling method = hash2
    Dos charset = CP932
    Unix charset = UTF-8

    logon script = logon.bat
    logon drive = H:
        logon home = 
        logon path = 

    domain logons = Yes
    domain master = Yes
    os level = 65
    preferred master = Yes
    wins support = yes
    # passdb backend = ldapsam:"ldap://ldap1.company.com ldap://ldap2.company.com"
    passdb backend = ldapsam:ldap://192.168.1.5/
    ldap admin dn = cn=admin,dc=nexusone,dc=local
    #ldap admin dn = cn=samba,ou=DSA,dc=company,dc=com
    ldap suffix = dc=nexusone,dc=local
        ldap group suffix = ou=groups
        ldap user suffix = ou=people
        ldap machine suffix = ou=Computers
    #ldap idmap suffix = ou=Idmap
        add user script = /usr/sbin/smbldap-useradd -m "%u"
        #ldap delete dn = Yes
        delete user script = /usr/sbin/smbldap-userdel "%u"
        add machine script = /usr/sbin/smbldap-useradd -t 0 -w "%u"
        add group script = /usr/sbin/smbldap-groupadd -p "%g" 
        delete group script = /usr/sbin/smbldap-groupdel "%g"
        add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
        delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
    set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
    admin users = admindomain
    ldap ssl = no
    # printers configuration
    #printer admin = @"Print Operators"
    load printers = Yes
    create mask = 0640
    directory mask = 0750
    #force create mode = 0640
    #force directory mode = 0750
    nt acl support = No
    printing = cups
    printcap name = cups
    deadtime = 10
    guest account = nobody
    map to guest = Bad User
    dont descend = /proc,/dev,/etc,/lib,/lost+found,/initrd
    show add printer wizard = yes
    ; to maintain capital letters in shortcuts in any of the profile folders:
    preserve case = yes
    short preserve case = yes
    case sensitive = no

[netlogon]
    path = /home/netlogon/
    browseable = No
    read only = yes

[profiles]
    path = /home/profiles
    read only = no
    create mask = 0600
    directory mask = 0700
    browseable = No
    guest ok = Yes
    profile acls = yes
    csc policy = disable
    # next line is a great way to secure the profiles 
    #force user = %U 
    # next line allows administrator to access all profiles 
    #valid users = %U "Domain Admins"

[printers]
        comment = Network Printers
        #printer admin = @"Print Operators"
        guest ok = yes 
        printable = yes
        path = /home/spool/
        browseable = No
        read only  = Yes
        printable = Yes
        print command = /usr/bin/lpr -P%p -r %s
        lpq command = /usr/bin/lpq -P%p
        lprm command = /usr/bin/lprm -P%p %j
        # print command = /usr/bin/lpr -U%U@%M -P%p -r %s
        # lpq command = /usr/bin/lpq -U%U@%M -P%p
        # lprm command = /usr/bin/lprm -U%U@%M -P%p %j
        # lppause command = /usr/sbin/lpc -U%U@%M hold %p %j
        # lpresume command = /usr/sbin/lpc -U%U@%M release %p %j
        # queuepause command = /usr/sbin/lpc -U%U@%M stop %p
        # queueresume command = /usr/sbin/lpc -U%U@%M start %p

[print$]
        path = /home/printers
        guest ok = No
        browseable = Yes
        read only = Yes
        valid users = @"Print Operators"
        write list = @"Print Operators"
        create mask = 0664
        directory mask = 0775

[public]
    path = /tmp
    guest ok = yes
    browseable = Yes
    writable = yes

I have followed all the steps correctly.

---

### Post by maverickaddicted on 2011-07-29
:confused: Please Help Me..................

---

### Post by akha666 on 2011-07-30
do this command
**# getent group**
it should be look like this 
#######################################################################
Domain Admins:*:512:root
Domain Users:*:513:
Domain Guests:*:514:
Domain Computers:*:515:
Administrators:*:544:root
Account Operators:*:548:
Print Operators:*:550:
Backup Operators:*:551:
Replicators:*:552: 
#######################################################################

---

### Post by arrrghhh on 2011-07-30
As was stated in the other thread you posted in.

[www.zentyal.com](www.zentyal.com) - makes things much easier if you don't want to learn how to do it on your own.  It'll also make training other admins easier...

---

### Post by maverickaddicted on 2011-08-01
Here is the output of getent group command - 

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:nexusadmin
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:nexusadmin
fax:x:21:
voice:x:22:
cdrom:x:24:nexusadmin
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:telnetd
video:x:44:
sasl:x:45:
plugdev:x:46:nexusadmin
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
mysql:x:105:
kvm:x:106:
mlocate:x:107:
ssh:x:108:
messagebus:x:109:
avahi:x:110:
netdev:x:111:
bind:x:112:
ssl-cert:x:113:postgres
postfix:x:114:
postdrop:x:115:
lpadmin:x:116:nexusadmin
dovecot:x:117:
libvirtd:x:118:nexusadmin
postgres:x:119:
sambashare:x:120:nexusadmin
winbindd_priv:x:121:
landscape:x:122:
tomcat6:x:123:
nexusadmin:x:1000:
admin:x:124:nexusadmin
avahi-autoipd:x:125:
bluetooth:x:126:
gdm:x:127:
nopasswdlogin:x:128:
pulse:x:129:
pulse-access:x:130:
utempter:x:131:
rtkit:x:132:
saned:x:133:
openldap:x:134:
machines:x:201:
domainadmins:x:1001:
ftp:x:1004:ftp
clamav:x:135:
amavis:x:136:
postgrey:x:137:
telnetd:x:138:
nexusadmin@openserver:~$ su root
Password: 
root@openserver:/home/nexusadmin# getent group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:nexusadmin
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:nexusadmin
fax:x:21:
voice:x:22:
cdrom:x:24:nexusadmin
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:telnetd
video:x:44:
sasl:x:45:
plugdev:x:46:nexusadmin
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
mysql:x:105:
kvm:x:106:
mlocate:x:107:
ssh:x:108:
messagebus:x:109:
avahi:x:110:
netdev:x:111:
bind:x:112:
ssl-cert:x:113:postgres
postfix:x:114:
postdrop:x:115:
lpadmin:x:116:nexusadmin
dovecot:x:117:
libvirtd:x:118:nexusadmin
postgres:x:119:
sambashare:x:120:nexusadmin
winbindd_priv:x:121:
landscape:x:122:
tomcat6:x:123:
nexusadmin:x:1000:
admin:x:124:nexusadmin
avahi-autoipd:x:125:
bluetooth:x:126:
gdm:x:127:
nopasswdlogin:x:128:
pulse:x:129:
pulse-access:x:130:
utempter:x:131:
rtkit:x:132:
saned:x:133:
openldap:x:134:
machines:x:201:
domainadmins:x:1001:
ftp:x:1004:ftp
clamav:x:135:
amavis:x:136:
postgrey:x:137:
telnetd:x:138:

---

### Post by maverickaddicted on 2011-08-05
Facing lots of problem in setting up the Ubuntu server, should I revert back to the Windows? I don't want to.

---

### Post by stevenroose on 2011-08-05
I just wanted to install an Ubuntu server myself but the ubuntu-11.04-iso seemed corrupt, in the installation I kept getting a corrupt python-x.x-minimal file and failed to install base system...
So I decided to install a desktop and from there install SAMBA. Then we can use the machine as a backup desktop if we would want to.
I still have to try setup samba, the installation was complete but I have exams soon so I continued studying :D (I always try new things on soms older machines when in exams, just to not have to study :D)
If I succeed I'll post here.
I was about to follow one of following guides:
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)
[http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic](http://www.unixmen.com/linux-tutorials/566-install-samba-server-in-ubuntu-karmic)
I just fast Google'd them during the installation, will see of one of them works...
I hope you manage to get it fixed soon!

---

### Post by arrrghhh on 2011-08-05
> **maverickaddicted said:**
> Facing lots of problem in setting up the Ubuntu server, should I revert back to the Windows? I don't want to.

No one is forcing you to use Ubuntu.  We're here to help you, but you've gotta be willing to help yourself in order for us to help you.  In other words, it's going to take some work and a lot of reading.

Did you try my earlier suggestion?  I don't need to use LDAP, but that solution seems pretty good for those who don't really care about the stuff that happens underneath, they just want it to work.

---

### Post by maverickaddicted on 2011-08-09
> **arrrghhh said:**
> No one is forcing you to use Ubuntu.  We're here to help you, but you've gotta be willing to help yourself in order for us to help you.  In other words, it's going to take some work and a lot of reading.

Did you try my earlier suggestion?  I don't need to use LDAP, but that solution seems pretty good for those who don't really care about the stuff that happens underneath, they just want it to work.
Zentyal is for Ubuntu 10.04, but I have installed ubuntu 11.04. Will it going to work on Ubuntu 11.04? As I have configured my server as web server and our company's developers are using it and I don't want to create any problem. I am a newbie and this is my first sever. So, please be kind.

---

### Post by arrrghhh on 2011-08-09
> **maverickaddicted said:**
> Zentyal is for Ubuntu 10.04, but I have installed ubuntu 11.04. Will it going to work on Ubuntu 11.04? As I have configured my server as web server and our company's developers are using it and I don't want to create any problem. I am a newbie and this is my first sever. So, please be kind.

10.04 is recommended for production server platforms anyways - you shouldn't be using 11.04 on a production server.

Unfortunately while I recommend Zentyal, I recommend it based on others I know and trust - I've never actually used the product myself.

Any person who wants sanity in their data centers are going to stick with LTS releases - for their longer support, and the requirement to upgrade comes much less frequently.  In theory the platforms LTS releases are built on are more stable as well.  So I would **strongly** recommend sticking with LTS releases on the server platforms.  Upgrading every 6 months on the desktop version isn't so painful, but doing it on a production server environment is crazy :p.

---

### Post by maverickaddicted on 2011-08-10
OK, I will roll back to 10.04 in the upcoming holidays. However, I have one more question. I want to create multiple phpmyadmin users, so that users will have access to their database only. Do you have any guide?

---

### Post by arrrghhh on 2011-08-10
> **maverickaddicted said:**
> OK, I will roll back to 10.04 in the upcoming holidays. However, I have one more question. I want to create multiple phpmyadmin users, so that users will have access to their database only. Do you have any guide?

First, you can't 'roll back'.. You'll have to do a complete fresh install of 10.04.

As for multiple users for phpmyadmin, I assume it would be the same as creating regular users... I'll have to Google for a guide.

---

### Post by maverickaddicted on 2011-08-11
I sorted out that mulitple user issue. I don't know whether it is a real problem or not. My phpmyadmin.conf was having a <?php in the beginning of the file, but there was no ?> at the end of the file. I just added that tag, and created a database user from the phpmyadmin and it works.

However, I have one doubt. Why it was not giving me any error before?

---

### Post by maverickaddicted on 2011-08-11
Hey one more thing. Have you gone through this guide - 

[http://www.server-world.info/en/note?os=Ubuntu_11.04&p=install](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=install)

It is having all the information required for configuring Ubuntu 11.04 server and according them it works perfectly. This is the only guide that motivated me to go for the Ubuntu 11.04 server, instead of its LTS version. 

I also tried to contact them via email, but didn't get any reply from them.

---

