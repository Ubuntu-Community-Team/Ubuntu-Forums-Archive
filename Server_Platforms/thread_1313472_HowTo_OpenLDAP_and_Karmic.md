---
title: "HowTo: OpenLDAP and Karmic"
date: 2009-11-03
forum: Server Platforms
---

### Post by apalacheno on 2009-11-03
In Ubuntu 9.10 Karmic Koala the installation of OpenLDAP got a bit complicated. Upon installation you are not asked for your password anymore, and you have to set up the database yourself. And this is only possible using the OpenLDAP server's root account. Yes, you read correctly: only a very minimal cn=config is provided by default.

There is an official statement about this [1] (in short: this is part of a future strategy to bring OpenLDAP to a broader spectrum - keyword: Kerberos), but unfortunately there is neither (november 4th, 2009) an official nor an inofficial HowTo on how to set up the whole thing. So here is my take:

First, install OpenLDAP:
```
apt-get -y install slapd ldap-utils
```

A *dpkg-reconfigure slapd* is useless btw.

Now add a few schemata (only *core.schema* is provided by default):

```
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
```

After that, we set up the initial cn=config database. Open a temporary file in your favourite text editor:

```
vi /root/db.ldif
```

and insert the following listing:

```
###########################################################
# DATABASE SETUP
###########################################################

# Load modules for database type
dn: cn=module{0},cn=config
objectClass: olcModuleList
cn: module{0}
olcModulePath: /usr/lib/ldap
olcModuleLoad: {0}back_hdb

# Create directory database
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=home,dc=com
olcRootDN: cn=admin,dc=home,dc=com
olcRootPW: 1234
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=home,d
 c=com" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=home,dc=com" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: uid pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
olcDbIndex: objectClass eq


###########################################################
# DEFAULTS MODIFICATION
###########################################################
# Some of the defaults need to be modified in order to allow
# remote access to the LDAP config. Otherwise only root
# will have administrative access.

dn: cn=config
changetype: modify
delete: olcAuthzRegexp

dn: olcDatabase={-1}frontend,cn=config
changetype: modify
delete: olcAccess

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: {CRYPT}7hzU8RaZxaGi2

dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess
```

Apply this configuration with the following command:

```
ldapadd -Y EXTERNAL -H ldapi:/// -f /root/db.ldif
```

This creates an administrative LDAP user *cn=admin,dc=home,dc=com* with the password *1234*. Be aware: from now on this user has all privileges on your LDAP-server!

Now set up a minimal LDAP DIT. Open another temporary file:

```
vi /tmp/base.ldif
```

and insert the following:

```
# Tree root
dn: dc=home,dc=com
objectClass: dcObject
objectclass: organization
o: home.com
dc: home
description: Tree root

# LDAP admin
dn: cn=admin,dc=home,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
userPassword: 1234
description: LDAP administrator
```

...and apply it:

```
ldapadd -x -D cn=admin,dc=home,dc=com -W -f /tmp/base.ldif
```
when asked for a password, enter *1234*. From now on you should be on the level of a fresh OpenLDAP installation in Jaunty. The rest is your part.

By the way, with the following commands you can read your cn=config:

```
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W
```

and your LDAP DIT (this time as anonymous user - hence no password is shown for your *cn=admin,dc=home,dc=com*):

```
ldapsearch -xLLL -b dc=home,dc=com
```

Good luck!
Robert



[1] [https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003182.html](https://lists.ubuntu.com/archives/ubuntu-server/2009-August/003182.html)

---

### Post by druhboruch on 2009-11-03
Thank you for a great howto.

There is already a discussion in this forum about this issue.
It contains links to the bugs opened in launchpad:

[http://ubuntuforums.org/showthread.php?p=8154148](http://ubuntuforums.org/showthread.php?p=8154148)

---

### Post by sammonsjl on 2009-11-09
I just figured out that you can configure OpenLDAP in Karmic to use the old slapd.conf file by doing the following:

Modify /etc/default/slapd

Set the SLAPD_CONF parameter to where your slapd.conf file is located: eg: SLAPD_CONF=/etc/ldap/slapd.conf

---

### Post by Yanlux on 2009-11-12
Hello,
is there a way to have OpenLDAP (slapd) and phpldapadmin working, installed from repository, on Ubuntu 9.10 as it was working before (7.10, 8.xx)? I'm going mad on this and I could not fix it in any way... Already googled but with no luck.
Thank you.

---

### Post by apalacheno on 2009-11-12
Is slapd standalone (without phpldapadmin) working already? I'm not using phpldapadmin, but at least the LDAP server should be in a functional state before using any admin tools.

---

### Post by Yanlux on 2009-11-12
Yes, slapd is installing fine but it is not possible to configure it via dpkg-reconfigure and I'm not so good with LDAP itself: I'm using it, through phpdalpadmin, to share an email address book. Thanx alot for your help.

---

### Post by apalacheno on 2009-11-12
dpkg-reconfigure is useless in karmic. Instead follow the described steps in the first post and it should work for you.

Unfortunately there is no way to avoid manually creating the LDAP database. The good news, however, is that it's just a matter of ten minutes to get it working.

---

### Post by Yanlux on 2009-11-12
Ok, I'm going to try this on a new server as soon as it is ready and I'll let you know if it will work... Thank you very much for your help, it is really invaluable.

P.S.: Just a little complaint about this whole matter. I think Ubuntu is also intended to be used to spread Linux open OS to the mass and this kind of attitude from the developers will not help. Not everyone has to be a coder/developer and the users should be advised when similar changes have to be introduced in critical services as LDAP is.

---

### Post by apalacheno on 2009-11-12
Good luck!

---

### Post by Yanlux on 2009-11-16
Thanks alot for the guide, now I managed to have OpenLDAP and PHPLDAPADMIN working.
Bye!

---

### Post by calitaco on 2009-11-16
Hey guys,

I'm new to ldap and I am having a little trouble with this.  I followed the directions in the first post and it seems like everything is working.  I then set up an ldap client and install the required packages, [COLOR=#0000ff]libpam-ldap libnss-ldap nss-updatedb libnss-db, [/COLOR]and did the necessary configurations.  End result, I can't seem to log into the client with a user account.  I installed ldapfinger on the client and was able to finger all the users I've set up on the server, but still don't understand why it wouldn't allow logins.  Am I missing something?

Forgot to add that it's running Ubuntu 9.10 64bit server.

Thanks!

---

### Post by Yanlux on 2009-11-16
From the very bottom of my very limited knowledge I think I had a similar problem: I had to change domain in all the oocurences in the files posted above, and than I also had to change LDAP password, changing it in the files (also the encrypted one). Can't say more, I'm really a newbie.

---

### Post by calitaco on 2009-11-16
Yes, I had to do that too to match my domain.  I have a feeling I must have missed something along the way.  And I thought NIS+ was bad :)

---

### Post by calitaco on 2009-11-16
I've made some progress.  By changing uri ldap:/// to uri ldap:// I was able to su to the user now but still can't log in normally on the client.  Why it defaulted to the 3 slashes, I don't know :?  Also, when I tried to chown the user's directory to the user's login name on the server, it complains that the user doesn't exist.  I shared the /home directory from the server to client to have a common home directory for all users.  Is this the correct way to do it?

Another Question:
Does the user's home directory get auto created during user account creation?  Currently I have to manually create them.  FYI, I'm using ldapadduser that came with the package ldapscripts.

Does the ldap server be it's own client?

Any help is appreciated.

---

### Post by apalacheno on 2009-11-17
Hey calitaco,
well, LDAP Client Authentication is another issue really, but it works in Karmic as well.

First, home directory creation has to be activated manually by adding this line to */etc/pam.d/common-session* (quite at top of the file; depending on your setup):

```
session		required	pam_mkhomedir.so skel=/etc/skel/ umask=0027
```

For the authentication issue have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1243884").

Cheers,
Robert

---

### Post by calitaco on 2009-11-17
Thanks for the response, Robert.

The thing that confuses me is that there's no mention of what machine these setting need to be on, client or server.  

I added that line on the server and when I run ldapadduser, it created the user but not the home directory.  But it did automatically created it on the client when I su to the user.  Still can't log in to the client though even after modifying the files suggested in that link you sent.

Does the server also need to be an ldap client?  Currently it isn't.  I've made so many different changes that I think I might need to start from scratch again:confused:

Thanks,
Pete

---

### Post by apalacheno on 2009-11-17
Hi again,

if the server should be a ldap client as well depends on what you want. It can be, but it doesn't have to. Technically it's no harm in any case, but remember to always have a local (non-LDAP) root user that can access the server even if LDAP breaks. And security wise you usually wouldn't want to have normal users log on to your servers.

The pam settings as well as the /etc/ldap.conf and /etc/nsswitch.conf settings are needed on all clients that should use ldap authentication.

The */etc/ldap/ldap.conf* is needed on the server in any case.

I have no current documentation for LDAP client auth lying around here, as we use kerberos. However I sumbled upon an older config that you can look at. Not sure if it works with karmic though and it doesn't utilize cached credentials.

You'd need the package *ldap-auth-client*.

This is the content of the **/etc/ldap.conf**:

```
# Pre-configured values 
base				dc=home,dc=ro 
uri				ldap://ldap.home.ro 
ldap_version			3 
pam_password			md5 

# Own settings 
ssl				start_tls 
tls_checkpeer			yes 
use_sasl			yes 
bind_policy			soft 
nss_base_passwd			ou=users,ou=accounts,dc=home,dc=ro?one 
nss_base_group			ou=groups,ou=accounts,dc=home,dc=ro?one	 
nss_initgroups_ignoreusers	avahi,avahi-autoipd,backup,bin,daemon,games,gdm,gnats,haldaemon,hplip,irc,klog,libuuid,list,lp,mail,man,messagebus,news,polkituser,proxy,pulse,root,saned,sync,sys,syslog,uucp,vboxadd,www-data
```

**/etc/ldap/ldap.conf**:

```
BASE		dc=home,dc=ro 
URI		ldap://ldap.home.ro 
TLS_REQCERT	demand 
TLS_CACERT      /etc/ssl/certs/cacert_home.pem
```

**/etc/nsswitch.conf**:

```
...
passwd:         files ldap
group:          files ldap
...
```

**/etc/pam.d/common-auth**:

```
auth	[success=2 default=ignore]	pam_unix.so nullok_secure 
auth	[success=1 default=ignore]	pam_ldap.so use_first_pass 
auth	requisite			pam_deny.so 
auth	required			pam_permit.so
```

**/etc/pam.d/common-account**:

```
account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=1 default=ignore]	pam_ldap.so 
account	requisite			pam_deny.so 
account	required			pam_permit.so
```

**/etc/pam.d/common-password**:

```
password	[success=2 default=ignore]	pam_unix.so obscure sha512 
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so use_authtok try_first_pass 
password	requisite			pam_deny.so 
password	required			pam_permit.so
```

**/etc/pam.d/common-session**:

```
session	required			pam_mkhomedir.so skel=/etc/skel/ umask=0027
session	[default=1]			pam_permit.so 
session	requisite			pam_deny.so 
session	required			pam_permit.so 
session	required			pam_unix.so 
session	optional			pam_ldap.so 
session	optional			pam_ck_connector.so nox11
```

Hope it can give you an idea at least.

Cheers,
Robert

---

### Post by calitaco on 2009-11-17
Finally got it to work.  I installed the client on a different machine and it worked.  I must have messed something up on the old client.  This is all I did on the new client.

apt-get install libnss-ldap
auth-client-config -t nss -p lac_ldap
pam_auth_update

#/etc/ldap.conf file
base                        dc=removed,dc=com
uri                           ldap://172.20.0.46/
ldap_version            3
rootbinddn               cn=admin,dc=removed,dc=com
bind_policy              soft
pam_password        md5
nss_base_passwd    ou=people,dc=removed,dc=com?one
nss_base_group      ou=groups,dc=removed,dc=com?one

#/etc/pam.d/common-session add entry
session         required        pam_mkhomedir.so skel=/etc/skel/ umask=0027

Here's a strange thing though, every user's home directory is created with "nobody" as the owner but the group name is normal.  Any ideas?

---

### Post by apalacheno on 2009-11-17
Great it works now!

Regarding the home directory owner... hmm no idea. That's strange indeed and I haven't experienced something similiar. A user's home directory should be created with the user's *uid* as owner and his primary group *cn* as group.

---

### Post by mamnmamn on 2009-11-17
Hi,

I have followed the how to. When I try to login via phpldapadmin, it lets me but the domain is still set to dc=example,dc=com. ie: I and get;

Logged in as: cn=admin,dc=my,dc=domain,dc=org
---> dc=example,dc=com

Can anyone point me to the silly mistake I must have made?

Thanks!

---

### Post by mamnmamn on 2009-11-19
No Worries, I figured it out. I had forgotten to edit the phpldapadmin config as it was hard coded to dc=example,dc=com.

---

### Post by apalacheno on 2009-11-20
Good to hear you found the issue!

Cheers,
Robert

---

### Post by paolocollector on 2009-11-20
Hi,
I have followed the instructions and the basic database seems to bu up.
I have to say "seems" because I can't use with any ui.

After all the add I end up with this situation:
[INDENT][FONT=Courier New]ldapsearch -x[/FONT]
[FONT=Courier New]# extended LDIF[/FONT]
[FONT=Courier New]#[/FONT]
[FONT=Courier New]# LDAPv3[/FONT]
[FONT=Courier New]# base <dc=home, dc=local> (default) with scope subtree[/FONT]
[FONT=Courier New]# filter: (objectclass=*)[/FONT]
[FONT=Courier New]# requesting: ALL[/FONT]
[FONT=Courier New]#[/FONT]

[FONT=Courier New]# home.local[/FONT]
[FONT=Courier New]dn: dc=home,dc=local[/FONT]
[FONT=Courier New]objectClass: top[/FONT]
[FONT=Courier New]objectClass: dcObject[/FONT]
[FONT=Courier New]objectClass: organization[/FONT]
[FONT=Courier New]o: home.local[/FONT]
[FONT=Courier New]dc: home[/FONT]
[FONT=Courier New]description:: SG9tZSBuZXR3b3JrIA==[/FONT]

[FONT=Courier New]# people, home.local[/FONT]
[FONT=Courier New]dn: ou=people,dc=home,dc=local[/FONT]
[FONT=Courier New]objectClass: organizationalUnit[/FONT]
[FONT=Courier New]ou: people[/FONT]

[FONT=Courier New]# groups, home.local[/FONT]
[FONT=Courier New]dn: ou=groups,dc=home,dc=local[/FONT]
[FONT=Courier New]objectClass: organizationalUnit[/FONT]
[FONT=Courier New]ou: groups[/FONT]

[FONT=Courier New]# search result[/FONT]
[FONT=Courier New]search: 2[/FONT]
[FONT=Courier New]result: 0 Success[/FONT]

[FONT=Courier New]# numResponses: 4[/FONT]
[FONT=Courier New]# numEntries: 3[/FONT]
[/INDENT]This looks ok to me, but if i try to connect with a client like phpldapadmin it says:
Error: Redirect Loop Detected
and Error:
Our attempts to find your SCHEMA for "attributetypes" have FAILED.
I tried to connect with JExplorer as well, and i receive an error "unable to list" and schema is forever in reading status.

Is there something else that i should do?

thanks

---

### Post by apalacheno on 2009-11-20
Hi,
your DIT looks fine to me.

For troubleshooting I suggest that you try to pin down the error by eliminating possible error sources. So if the schemas are there and if you can read your cn=config and your LDAP DIT just fine using these commands:

```
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W
ldapsearch -xLLL -b dc=home,dc=com
```

then your ldap server seems to be okay and you can exclude slapd as the error source almost for sure.


I have no experience with phpldapadmin though, maybe someone else can help.

---

### Post by paolocollector on 2009-11-20
Thanks,
only the last command works, here the output:

[INDENT][FONT=Courier New]# ldapsearch -xLLL -b dc=home,dc=local[/FONT]
[FONT=Courier New]dn: dc=home,dc=local[/FONT]
[FONT=Courier New]objectClass: top[/FONT]
[FONT=Courier New]objectClass: dcObject[/FONT]
[FONT=Courier New]objectClass: organization[/FONT]
[FONT=Courier New]o: home.local[/FONT]
[FONT=Courier New]dc: home[/FONT]
[FONT=Courier New]description:: SG9tZSBuZXR3b3JrIA==[/FONT]

[FONT=Courier New]dn: ou=people,dc=home,dc=local[/FONT]
[FONT=Courier New]objectClass: organizationalUnit[/FONT]
[FONT=Courier New]ou: people[/FONT]

[FONT=Courier New]dn: ou=groups,dc=home,dc=local[/FONT]
[FONT=Courier New]objectClass: organizationalUnit[/FONT]
[FONT=Courier New]ou: groups[/FONT]
[/INDENT]The other 2 ask for a password but admin doesnt work (and i'm sure is the one i introduced)
[INDENT][LEFT]# [FONT=Courier New]ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb[/FONT]
[FONT=Courier New]Enter LDAP Password:[/FONT]
[FONT=Courier New]ldap_bind: Invalid credentials (49)[/FONT]
[/LEFT]
[/INDENT]

---

### Post by apalacheno on 2009-11-20
Ok, then there's a problem with slapd. Are you sure you replaced all occurences of *dc=home,dc=com* with *dc=home,dc=local*?

Since the problem is happening at such an early state it is propably better to start again from scratch?

---

### Post by paolocollector on 2009-11-20
I would like to start all over again, but i dont want to reinstall ubuntu.
Is there any chance to uninstall ldap only and get rid of all the config files, then install it again?

---

### Post by apalacheno on 2009-11-20
Sure, your directory is stored in */var/lib/ldap*, as defined by *olcDbDirectory*. Just stop slapd, delete the data files (no, better make a backup of them), restart slapd and you are right at beginning again.

In words (commands):

```
/etc/init.d/slapd stop
mv /var/lib/ldap /var/lib/ldap.old
/etc/init.d/slapd start
```

If it still does not work, try the config exactly as in the first post.

---

### Post by paolocollector on 2009-11-20
in the original post some lines seem a bit strange:
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=home,d  c=ro" write by anonymous auth by self write by * none 

is that correct?

---

### Post by apalacheno on 2009-11-20
The original post reads

```
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=home,d
 c=ro" write by anonymous auth by self write by * none
```

the space at the beginning of the second line is by convention a way to tell slapd that it should interpret these two lines as a single line. If you want this string on a single line (which is perfectly fine and results in the same), then you must remove that leading space, so that this line reads:

```
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=home,dc=ro" write by anonymous auth by self write by * none
```

Maybe that was causing the error you experienced?

Cheers,
Robert

---

### Post by paolocollector on 2009-11-20
not sure, i meant:
dc=ro
is a bit strange: shuld it not be
dc=com
as everywhere else?
anyway i tried with the exact configuration described and it works fine, so im going to try again changing the home.com and the admin password and let you know
Thanks for helping

---

### Post by paolocollector on 2009-11-20
Just to let you know, i changed the home.com and everything works fine now.
I think i messed up some ldif file editing.
Thanks again

---

### Post by apalacheno on 2009-11-22
Whoopsie, that's a bugger. I've corrected it in the original post. Thanks for mentioning it!

Great it works now!

---

### Post by stefanadelbert on 2009-11-25
I'm having trouble installing schemas using the described method

```
$ ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=cosine,cn=schema,cn=config"
ldap_add: Insufficient access (50)
```

If I create a fresh installation of ldap and run dpkg I can see that ldap is running by logging into phpldapadmin anonymously. The domain is correctly setup and there is a cn=admin entry there already. However, if I try to login to phpldapadmin using admin:<LDAPpasswd> it denies. Would the admin user have a different password to the LDAPpasswd?

Any ideas on why this might be the case?

I suppose that it's definitely worth mentioning that I'm still running Jaunty on the server. I'm planning on upgrading the server at some point, but I really don't want to break anything, so I'm reluctant.

---

### Post by Verikon on 2009-11-25
@stefan

try this:

#apt-get --purge remove slapd ldap-utils
#apt-get -y install slapd ldap-utils
#ldapadd -Y EXTERNAL -H ldapi://// -f /etc/ldap/schema/cosine.ldif


I had the same issue and purging the install completely worked.

---

### Post by stefanadelbert on 2009-11-26
Thanks for the reply, Verikon.

I had actually tried exactly that before, but I tried it again (using apt-get --purge remove rather than apt-get purge), but I have the same problems. I did need to use one less forward-slash after "ldapi:".

```
$ ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=cosine,cn=schema,cn=config"
ldap_add: Insufficient access (50)
```

I would greatly appreciate any other tips.

---

### Post by apalacheno on 2009-11-26
Since you're using jaunty, you don't have to follow this howto. Upon installation your database is already set up correctly, and you can start to play with it immediately.

E.g. if you want additional schemes, use this command:

```
ldapadd -x -D cn=admin,cn=config -W -f /etc/ldap/schema/cosine.ldif
```

When asked for a password enter the password you choose during installation.

---

### Post by lizard2802 on 2009-12-01
Hi, i'm a  kind of newbie with OpenLdap. i run Karmic server at home on a via-powered computer.
I followed the instructions given o nthe first post, and unfortunately, i can't manage to get everything sorted out.

I did install slapd and ldap-utils.
I passed the three command ldapadd
When i submit the db.ldif file with the ldapadd command, i get the following error message : 
```

SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module{0},cn=config"

adding new entry "olcDatabase={1}hdb,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
        additional info: <olcAccess> handler exited with 1

```Then i submit de base.ldif file and i get this kind of answer :
```

Enter LDAP Password:
ldap_bind: Invalid credentials (49)

```i entered 1234 as the password, and just didn't modify the files given in example.
May be somenody can help me ?
Cheers
Phil

---

### Post by rubic on 2009-12-12
I've got the same error messages as lizard2802, on a fresh karmic installation.

[update: repeated error on another karmic system]

---

### Post by rubic on 2009-12-12
To quickly reproduce the errors, I'm using the following script.  Warning: It will delete any current ldap settings.  To reproduce, first copy the attached base.txt, db.txt files to /tmp. 

```

#!/bin/sh
# Note: This will remove any changes you've made to /etc/ldap.
# SAVE YOUR CHANGES BEFORE PROCEEDING FURTHER.
apt-get --purge remove slapd ldap-utils
rm -rf /var/lib/ldap /etc/ldap
apt-get -y install slapd ldap-utils
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
cp /tmp/db.txt /root/db.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /root/db.ldif 
cp /tmp/base.txt /tmp/base.ldif
ldapadd -x -D cn=admin,dc=home,dc=com -W -f /tmp/base.ldif

```

When asked for password:  1234, which returns:

[I]ldap_bind: Invalid credentials (49)
[/I]
However, the script actually fails here:

[FONT="Courier New"]**ldapadd -Y EXTERNAL -H ldapi:/// -f /root/db.ldif**[/FONT]
[I]SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module{0},cn=config"

adding new entry "olcDatabase={1}hdb,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
	additional info: <olcAccess> handler exited with 1
[/I]

The results of the attempted installation are available in the attached results.txt file.  I hope this helps someone with their investigations.

---

### Post by apalacheno on 2009-12-21
Hi,
you are missing the NIS schema.

It should work if you add the NIS schema before adding the db.ldif. You can add the NIS schema using this command:

```
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif 
```

Btw @rubic: In your db.ldif you state that the admin DN is *cn=admin,dc=techota,dc=com*, however, in the last line of your script you are using *cn=admin,dc=home,dc=com*.

Also check if your */etc/ldap/ldap.conf* is setup correctly - these lines should be present:

```
BASE            dc=techota,dc=com
URI             ldap://localhost

```

Using these corrections with your script I can successfully set up the OpenLDAP server.

Cheers,
Robert

---

### Post by bobwdn on 2009-12-22
Ok, so now I have followed you first post and ldap is working.

I cannot thank you enough. Thank you. :-D

Now, I would like to change the "1234" password to something unique. How do I do this?

---

### Post by rubic on 2009-12-23
apalacheno, thanks for your reply.  I didn't think NIS was necessary, but by putting it in everything works fine now.  The techota/home issue was simply copy-n-paste fumbling in my post to this forum.  Thanks again!

---

### Post by bobwdn on 2009-12-24
Well patiently waiting to see what anyone thinks about how I should change the "1234" password, I discovered a related question.

Within the db.ldif script contained in the first post, there are two references to the "olcRootPW". The first is below the "# Create directory database" header and displays (in plain text) "1234". The second is near the end and appears as "olcRootPW: {CRYPT}7hzU8RaZxaGi2".

Are these related in any way? When adjusting the plain text "1234" password (above), should the CRYPT password hash (below) be regenerated?

---

### Post by apalacheno on 2009-12-24
@rubic: Sure, no problem. You're welcome!

> **bobwdn said:**
> When adjusting the plain text "1234" password (above), should the CRYPT password hash (below) be regenerated?

Yes. If you change the password, I'd recommend changing it in the following three places:

[LIST]
[*]dn: olcDatabase={1}hdb,cn=config
[*]dn: olcDatabase={0}config,cn=config
[*]dn: cn=admin,dc=home,dc=com
[/LIST]

If you install e.g. Luma (*luma*), you find an option to generate encrypted passwords in the "Admin utilities".

Good luck!
Robert

---

### Post by bobwdn on 2009-12-24
Thanks for the reply, apalacheno.

Sorry, I am confused. You reference changes in three places. I am only seeing two places?

I do not see a password to change under "olcDatabase={1}hdb,cn=config". Down lower under "olcRootDN: cn=admin,dc=home,dc=com", yes I see a "olcRootPW". (This area appears to use plain text.)

I did read somewhere and tried using slappasswd with a '-c' software switch. "slappasswd -c" did create a CRYPT hash password. Am I correct to say that that created CRYPT hash replaces the existing CRYPT hash below "olcDatabase={0}config,cn=config"?

(BTW, happy holidays.)

---

### Post by bobwdn on 2009-12-24
I kept searching Google and I found the answer to my question at 

[[="http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala"]]([="http://www.howtoforge.com/install-and-configure-openldap-on-ubuntu-karmic-koala"]).

Again, apalacheno, Thanks for your help. Great howto!

---

### Post by apalacheno on 2009-12-25
Heyja,
the first two passwords are in the db.ldif:

```
olcRootPW: 1234
olcRootPW: {CRYPT}7hzU8RaZxaGi2
```

the third password is in the base.ldif:

```
userPassword: 1234
```

As you already mentioned, you can use **slappasswd -h {CRYPT}** to generate the encrypted password.

Cheers,
Robert

---

### Post by AlexanderDGreat on 2009-12-26
Hi everyone, I want to try this tutorial, but I'm not really sure what LDAP does and if it's for me.

I'm using Karmic and have an experience with GPO in WinServer2003 before. Our server is in an office environment with 20 workstations. We use NFS & Samba for file sharing, CUPS for printing, Squid for Proxy, LAMP for internal CMS website, and VMserver2/Virtualbox to interact with MS apps and IE websites. I just add the users via the "System>Administration>Users and Groups" so we'll have a basic form of authentication in the file shares and other services.

Will LDAP benefit us? Hoping for your enlightenment. Thanks.

PS By the way, will LDAP play nicely with the above services or do I need tweak each service's config files or install other files to make them interact together?

---

### Post by foobarbituric on 2010-01-07
Thank's a lot for this How-to. That's great and OK for me.
I do the Howto with example.com, but now i'll want to do it with a correct name, etc.
I don't want to re-install.
Do you have a quick solution to clean the database and do it again with correct DIT without uninstall?
Please.
Thank's

---

### Post by jarlt on 2010-01-21
I am a novice at LDAP, previously used OS X as it was fast to deploy a simple LDAP instance. I am in the process of migrating to Ubuntu 9.10 for LDAP services and have installed and populated my directory.  I've been asked to create a password policy to "harden passwords".  My understanding is I need to use the ppolicy.schema that I have in my /etc/ldap/schema directory.  I found one blog post by [Andy Loughran]("http://zrmt.com/2007/10/19/howto-ppolicy-openldap") but I have not been able to make it work as it is from 2007 and I am not very knowledgeable about modifying ldap.  

mlmlitech@ldap3:~$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W -x olcDatabase={1}hdb
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=mlml,dc=calstate,dc=edu
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=mlml,d
 c=calstate,dc=edu" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=mlml,dc=calstate,dc=edu" write by * read
olcLastMod: TRUE
olcRootDN: cn=admin,dc=mlml,dc=calstate,dc=edu
olcRootPW: {crypt}83yJyPH/Q4cwA
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: objectClass eq
olcDbIndex: entryUUID eq
olcDbIndex: uid eq,pres,sub

Thanks

---

### Post by iamquand on 2010-02-12
Hey all,

I come to you a defeated man. I've tried just about every guide I can find and for the life of me cannot get openldap working. I am plagued by errors of "Invalid credentials" and "Insufficient access". On the initial post and several others I try the ldapadd command and receive credential errors.

The specific command I'm typing is:
```
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
```

I receive this error:
```
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=cosine,cn=schema,cn=config"
ldap_add: Insufficient access (50)

```
purging and installing again yields no new results. I'm running Ubuntu 9.04.

Any advice would be greatly appreciated.

---

### Post by JeshurunDaniel on 2010-02-16
I was stuck with the same problem. Uninstalling slapd (apt-get remove), deleting the slap.d directory and and slapd.conf files, and re-installing slapd again and then following the steps in this guide solved my problem. Wish you luck!

Oh and a word of caution. If you ever remove libldap-2.4-2 look out for the packages it says it is going to remove. Last time i removed it uninstalled a whole bunch and rendered my system unusable. 

> apt-get remove libldap-2.4-2 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-bugbuddy empathy-doc libsilcclient-1.1-3 erlang-crypto libwxbase2.8-0 kdebase-runtime-data-common telepathy-gabble libqt4-qt3support libwebkit-1.0-common
  python-evince libqt4-phonon python-avahi libxine1-x erlang-xmerl gnome-games-common libotf0 libmysqlclient15off obexd-client python-couchdb erlang-syntax-tools
  python-louis liblouis-data libibus1 ibus-gtk libxcb-xv0 python-speechd libsctp1 libpolkit-gtk-1-0 libgupnp-1.0-2 gnome-sudoku libindicate-gtk1 libempathy-common
  lksctp-tools libapr1 python-totem-plparser libchm1 libexiv2-5 telepathy-salut apache2-utils m17n-db liblzma0 erlang-runtime-tools python-webkit python-gtksourceview
  libgdata-common python-aptdaemon kde-icons-oxygen python-qt3 libclutter-gtk-0.10-0 telepathy-butterfly libclucene0ldbl python-nautilusburn mysql-admin liblouis0
  python-sip4 libaprutil1-dbd-sqlite3 libevent-1.4-2 erlang-mnesia libclutter-1.0-0 python-telepathy libart2.0-cil erlang-public-key aptdaemon libxine1-console
  python-rsvg python-aptdaemon-gtk libflickrnet2.2-cil erlang-inets libm17n-0 mysql-gui-tools-common m17n-contrib libwebkit-1.0-2 libgupnp-igd-1.0-2 libwxbase2.8-dev
  usb-creator-common libanthy0 media-player-info python-papyon libstreams0 libqt4-webkit libzephyr4 erlang-ssl exiv2 python-wnck ttf-wqy-zenhei wx2.8-headers
  python-gnomeprint libnice0 libxcb-shape0 gstreamer0.10-nice libloudmouth1-0 libxcb-shm0 python-ibus kdebase-runtime-data libjson-glib-1.0-0 libaprutil1 php5-common
  libgssdp-1.0-1 libxine1-bin telepathy-mission-control-5 python-gtop erlang-base libstreamanalyzer0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acroread aisleriot apache2 apache2-mpm-prefork apache2.2-bin apache2.2-common apturl at-spi bluez-cups brasero capplets-data checkbox-gtk compiz
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin cups
  cups-driver-gutenprint desktopcouch empathy eog evince evolution evolution-couchdb evolution-data-server evolution-exchange evolution-indicator evolution-plugins
  evolution-webcal f-spot file-roller firefox-3.5-gnome-support firefox-gnome-support foo2zjs foomatic-db foomatic-db-engine gcalctool gconf-defaults-service
  gconf-editor gconf2 gdebi gdm gdm-guest-session gedit ghostscript-cups gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-applets gnome-applets-data
  gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-games gnome-keyring gnome-mahjongg gnome-media gnome-media-common gnome-nettool
  gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-settings-daemon
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gnupg
  gstreamer0.10-plugins-good gtali gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse hpijs hplip iagno ibus ibus-m17n ibus-table indicator-applet
  indicator-applet-session indicator-messages indicator-session kerneloops-daemon ldap-utils libapache2-mod-php5 libaprutil1-ldap libbonoboui2-0 libbrasero-media0
  libcamel1.2-14 libcouchdb-glib-1.0-1 libcryptui0 libcurl3 libcurl3-gnutls libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-gtk-common libempathy-gtk28 libempathy30 libexchange-storage1.2-3 libgail-gnome-module
  libgconf2-4 libgconf2.0-cil libgdata5 libgksu2-0 libgnome-desktop-2-11 libgnome-media0 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgpgme11 libgstfarsight0.10-0 libgtkhtml-editor0 libgtkhtml3.14-19 libgweather-common libgweather1 libldap-2.4-2
  libldap2-dev liblpint-bonobo0 libmetacity0 libpanel-applet2-0 libpq5 libpurple0 libraptor1 librasqal1 librdf0 libsmbclient libsoup-gnome2.4-1 libtelepathy-farsight0
  libwxgtk2.8-0 libwxgtk2.8-dev luma metacity metacity-common mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome
  notification-daemon notify-osd nspluginwrapper onboard openoffice.org-base-core openoffice.org-calc openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-writer openprinting-ppds php5 php5-ldap
  pidgin pidgin-libnotify pulseaudio-module-gconf pxljr python-desktopcouch python-desktopcouch-records python-gconf python-gnome2 python-gnomeapplet
  python-gnupginterface python-ldap python-pyatspi python-smbc python-software-properties python-uno raptor-utils redland-utils rhythmbox samba-common-bin same-gnome
  seahorse slapd smbclient software-center software-properties-gtk splix system-config-printer-common system-config-printer-gnome telepathy-haze tomboy totem
  totem-common totem-mozilla totem-plugins transmission-gtk ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-wallpapers update-manager update-manager-core
  update-notifier usb-creator-gtk vinagre vino xchm xulrunner-1.9.1-gnome-support yelp
0 upgraded, 0 newly installed, 248 to remove and 0 not upgraded.
After this operation, 1,255MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


---

### Post by lokimon on 2010-03-02
> **apalacheno said:**
> Heyja,
the first two passwords are in the db.ldif:

```
olcRootPW: 1234
olcRootPW: {CRYPT}7hzU8RaZxaGi2
```

the third password is in the base.ldif:

```
userPassword: 1234
```

As you already mentioned, you can use **slappasswd -h {CRYPT}** to generate the encrypted password.

Cheers,
Robert

i'm a bit confused about this now.

i have also been struggling with LDAP for months and am frustrated with it.

i managed to follow this guide to get a basic LDAP setup working but also want to change my admin password from "1234" to something better.

i used slappasswd -h {CRYPT} to generate a password and then replaced "1234" with that in both db.ldif and base.ldif.  then i tried to load those files just as before but i got an error this time:

```
root@ldap:~# ldapadd -Y EXTERNAL -H ldapi:/// -f /root/db.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module{0},cn=config"
ldap_add: Insufficient access (50)
```

short of starting over from scratch with a better password, i'm sort of at a loss as to how to set the admin password now.

---

### Post by lokimon on 2010-03-02
> **lokimon said:**
> i'm a bit confused about this now.

i have also been struggling with LDAP for months and am frustrated with it.

i managed to follow this guide to get a basic LDAP setup working but also want to change my admin password from "1234" to something better.

i used slappasswd -h {CRYPT} to generate a password and then replaced "1234" with that in both db.ldif and base.ldif.  then i tried to load those files just as before but i got an error this time:

```
root@ldap:~# ldapadd -Y EXTERNAL -H ldapi:/// -f /root/db.ldif
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module{0},cn=config"
ldap_add: Insufficient access (50)
```

short of starting over from scratch with a better password, i'm sort of at a loss as to how to set the admin password now.

i just started from scratch and replaced the 1234 with crypt passwords.  seems to work so far.

---

### Post by Ortpor on 2010-03-03
I had the same question regarding setting a new admin password for "cn=config" because there wasn't one set on my fresh Karmic install.

I used the following LDIF file to add one:
> dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: secretIf you want to change an existing password you just have to delete the old entry first with:
> dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcRootPW


---

### Post by sk72 on 2010-03-25
When I run "ldapadd -x -D cn=xxxxx,dc=yyyyy,dc=org -W -f /tmp/base.ldif"  I get the following error:

ldapadd -x -D cn=xxxxx,dc=yyyyy,dc=org -W -f /tmp/base.ldif
Enter LDAP Password:
adding new entry "dc=xxxxx,dc=org"
ldap_add: Already exists (68)

Note: I have hidden my cn and dc names. 

What am I doing wrong? 

Thanks.

---

### Post by sk72 on 2010-03-25
> **lokimon said:**
> i just started from scratch and replaced the 1234 with crypt passwords.  seems to work so far.

I had the same problem. I uninstalled and reinstalled slapd and ldap-utils.

1. apt-get --purge remove slapd ldap-utils
2. apt-get -y install slapd ldap-utils

This worked for me. But I am stuck at "ldapadd -x -D cn=admin,dc=home,dc=com -W -f /tmp/base.ldif" which gives me the following error: 
ldap_add: Already exists (68)

---

### Post by airtonix on 2010-03-28
Since page 1 of this thread is being considered for a ubuntu wiki page, I think that for the purposes of providing a complete wiki page on "centralised login server" aka ldap, this guide needs to : 

+ Have clearly marked sections that define steps that should be taken on the server and clients, so far I don't see anything that outlines the steps to take on a client in order to complete the scenario.
Ideally I would like to see a test case scenario described and then have the guide take the user through the required steps in order to achieve the scenario described in the test case.

+ Outline how to setup a roaming profile template on the server, and point out key elements and their purposes.

+ Consider creating articles that talk about controlling bandwidth through a proxy to a wan connection based on the accounts contained on the ldap server.

----

If we can get the documentation to explain it clearly with no assumptions about the users previous experience with ldap, kerberos, etc, etc... then many who found ldaps current state of documentation would re-consider it again.

I know I would.

Ideally A python GUI that operates over ssh to the ldap server with the purpose of providing the means to remotely administer, configure & maintain the ldap server and related services might also be really attractive to people who find themselves attracted to ubuntu but lack the long term experience currently required to implement a ubuntu client/server environment with confidence.

---

### Post by shams_i on 2010-03-31
Hi Robert,

I'm using Ubuntu 9.10 server & I have been able to get my LDAP server running using your 1st post! Thanks!

Then I followed this link for User & Group Managment
My ultimate aim is to get LDAP client authetication working for my lab.

[https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

I'm facing issues when I any of the ldapscripts to add user or group

Throws following error:
admins@x6:/etc/ldap$ sudo ldapadduser george cms
Cannot resolve group cms to gid : not found

& ldapscripts.log show

>> 03/31/10 - 06:59 : Command : /usr/sbin/ldapadduser george cms
ldap_bind: Invalid credentials (49)
Cannot resolve group cms to gid : not found

LDAP admin passwd :1234 works for any other commands when prompted so I'm not sure what credentials are failing here.Could you could throw some light on it?

If you have come across any good documentation to follow after this in order to get LDAP client authetication which can be managed from server side please let me know.

PFA cnconfig & ldap.conf files

Thanks for your time in advance
Shamika

---

### Post by shams_i on 2010-04-01
Hi all,I guess I had messed up something in my ldif files. I removed slapd & ldap utils, followed ur post again & it is working great! Thanks

However I have a question if you could answer 
 My desired implementation is to control user logins on different lab machines based on the project groups. 
Scenario: Bob is part of project group 'mars' & John is part of 'venus' then I have added lab machines x1-x3 to group 'mars' & y1-y3 to group venus. Now I want John to only access machines allocated for project 'mars' i.e x1 to x3 & John to access machines allocated for 'venus' i.e y1 to y3

I went through this link [http://www.hurricanelabs.com/september2009_login_security_using_openldap_and_pam ]("http://www.hurricanelabs.com/september2009_login_security_using_openldap_and_pam")learned that it can be achieved using "overlay dynlist". Please correct me if I've got it wrong.
However my lab LDAP server is running on Ubuntu 9.10 (karmic koala) and it is using slapd.d (not slapd.conf)
So now if I want to attempt to use "overlay dynlist" how should I go about it? Has anyone done this before? Any help will be appreciated.

Thanks
Shamika

---

### Post by sk72 on 2010-04-01
I figured out the solution for "ldap_add"/"ldap_bind" errors.

rm /var/lib/ldap/*
apt-get --purge remove slapd ldap-utils
apt-get -y install slap ldap-utils

and follow the rest from the OP's thread.

---

### Post by The Sleeping God on 2010-04-05
Still having trouble with this. Every time i try to sudo ldapadd the db.ldif file I get 
```
ldap_add: Other (e.g., implementation specific) error (80)
             additional info: <olcDbDirectory> failed startup
```

The directory /var/lib/ldap is owned by openldap.
I've tried googling this, but to no avail. Any ideas what this error message means?

---

### Post by Squeazer on 2010-04-12
My man, you have saved my life. Where are you from? I'll buy you a beer! Srsly, i've been at this OpenLDAP database for 2 days now, trying to figure it out, trying to find slapd.conf etc... And now.... it finaly works! YAAAY! :popcorn:

---

### Post by Squeazer on 2010-05-09
And if it's important.... in lucid lynx you have to put sudo in front of most commands here. I'm not sure how it is for keramic koala

---

### Post by jagnikam on 2010-05-10
can anyone please guide me for changing objectclass 

Current objectclass
objectClasses: ( 2.5.6.6 NAME 'person' DESC 'RFC2256: a person' SUP top STRUCTURAL MUST ( sn $ cn ) MAY ( userPassword $ telephoneNumber $ seeAlso $ description ) )

Wanted like this 
objectClasses: ( 2.5.6.6 NAME 'person' DESC 'RFC2256: a person' SUP top STRUCTURAL MUST cn MAY ( sn $ userPassword $ telephoneNumber $ seeAlso $ description ) )

tried to change by using below command
$ldapmodify -d -1 -D "cn=admin,dc=example,dc=com" -w secret -f modify.ldif

$cat modify.ldif
dn: cn=schema
changetype: modify
add: objectclasses
objectClasses: ( 2.5.6.6 NAME 'person' DESC 'RFC2256: a person' SUP top AUXILIARY  MUST cn MAY ( sn $ userPassword $ telephoneNumber $ seeAlso $ description ))



getting error
ldap_modify: Invalid syntax (21)
	additional info: objectclasses: value #0 invalid per syntax

Thanks in advance

---

### Post by bjorgein on 2010-05-17
I have a problem.

In all these guides it is assumed that your FQDN used for the root is only two parts long like dc=home,dc=local. I can get all the example codes to work but as soon as I change the code for building the front and backend databases to my actual FQDN which is dc=ldaptest,dc=omited,dc=com. The building no longer works which i assume is to the structure of the database. How do I fix this? I have been bashing my head on my keyboard for a few hours now trying to figure this out. Anyone offer a linux newb a hand in this matter?

---

### Post by antenagora on 2010-05-19
Same problem here, i'm searching for a solution

---

### Post by ipguy on 2010-06-02
Hi all

Is slapd.conf depreciated in ubuntu 9.10 running OpenLDAP 2.4.18 ?
I'm running the OP's setup but there is now mention of slapd.conf
How does one add a new schema ?

---

### Post by apalacheno on 2010-06-21
Hint: My original HowTo is valid for Lucid as well, you just need to adjust the following section in */root/db.ldif*:

Instead of
> **apalacheno said:**
> 
```
###########################################################
# DEFAULTS MODIFICATION
###########################################################
# Some of the defaults need to be modified in order to allow
# remote access to the LDAP config. Otherwise only root
# will have administrative access.

dn: cn=config
changetype: modify
delete: olcAuthzRegexp

dn: olcDatabase={-1}frontend,cn=config
changetype: modify
delete: olcAccess

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: {CRYPT}7hzU8RaZxaGi2

dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess
```

You need this (effectively adding the **olcRootDN**):

```
###########################################################
# DEFAULTS MODIFICATION
###########################################################
# Some of the defaults need to be modified in order to allow
# remote access to the LDAP config. Otherwise only root
# will have administrative access.

dn: cn=config
changetype: modify
delete: olcAuthzRegexp

dn: olcDatabase={-1}frontend,cn=config
changetype: modify
delete: olcAccess

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,cn=config

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: {CRYPT}7hzU8RaZxaGi2

dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess
```

Cheers,
Robert

---

### Post by init-0 on 2010-08-11
Hi, thanks for the tutorial, 

I have made a script for Ubuntu 10.0.4 and it is the following:

```

#!/bin/sh
passwd=xxxxxx
dc1=host
dc2=com
hash_pw=`slappasswd -s $passwd`
tmpdir=/tmp
#--------------------------------------------------------------#
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/misc.ldif
#&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-#
# database.ldif
#&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-#
cat <<EOF > $tmpdir/database.ldif
# Load dynamic backend modules
dn: cn=module{0},cn=config
objectClass: olcModuleList
cn: module{0}
olcModulePath: /usr/lib/ldap
olcModuleLoad: {0}back_hdb

# Create directory database
dn: olcDatabase={1}hdb,cn=config
objectClass: olcDatabaseConfig
objectClass: olcHdbConfig
olcDatabase: {1}hdb
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=$dc1,dc=$dc2
olcRootDN: cn=admin,dc=$dc1,dc=$dc2
olcRootPW: $hash_pw
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=$dc1,dc=$dc2" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=$dc1,dc=$dc2" write by * read
olcLastMod: TRUE
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: uid pres,eq
olcDbIndex: cn,sn,mail pres,eq,approx,sub
olcDbIndex: objectClass eq
################################
#        Modifications
################################

dn: cn=config
changetype: modify
delete: olcAuthzRegexp

dn: olcDatabase={-1}frontend,cn=config
changetype: modify
delete: olcAccess

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootDN
olcRootDN: cn=admin,cn=config

dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: $hash_pw

dn: olcDatabase={0}config,cn=config
changetype: modify
delete: olcAccess
EOF
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f $tmpdir/database.ldif
####################################
#         Mini DIT
####################################
cat <<EOF> $tmpdir/dit.ldif
# Tree root

dn: dc=$dc1,dc=$dc2
objectClass: dcObject
objectclass: organization
o: $dc1.$dc2
dc: $dc1
description: Tree root

# LDAP admin
dn: cn=admin,dc=$dc1,dc=$dc2
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
userPassword: $hash_pw
description: LDAP administrator
EOF

sudo ldapadd -x -D cn=admin,dc=$dc1,dc=$dc2 -W -f $tmpdir/dit.ldif

```Now all is fine until:

```

adding new entry "olcDatabase={1}hdb,cn=config"

modifying entry "cn=config"
ldap_modify: Undefined attribute type (17)
    additional info: olcAuthRegexp: attribute type undefined

Enter LDAP Password: 
adding new entry "dc=host,dc=com"

adding new entry "cn=admin,dc=host,dc=com"

```The password is OK

UPDATE_ Fixed, I removed the olcAuthRegexp line.
Now work just fine.

---

### Post by alextvm on 2010-08-27
I'm trying to revive LDAP with ubuntu 10.04 in one of the labs at my school but our domain consists of dc=cs,dc=school,dc=edu, why does it complain about name attributes? Does it only like a 2 part domain?

---

### Post by apalacheno on 2010-08-29
> **alextvm said:**
> Does it only like a 2 part domain?

That shouldn't post a problem. If you've followed the tutorials in this thread, make sure that you've replaced all occurences of **dc=home,dc=com** with **dc=cs,dc=school,dc=edu**.

Good luck!
Robert

---

