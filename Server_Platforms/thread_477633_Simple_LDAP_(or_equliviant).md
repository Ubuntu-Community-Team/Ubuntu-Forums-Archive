---
title: "Simple LDAP (or equliviant)"
date: 2007-06-18
forum: Server Platforms
---

### Post by Scott07 on 2007-06-18
Is there a simple way to get a LDAP server running, all the guides I have tried so far don't work or are massive.  I say simple as I am looking for a central password store for about 5 computers and about 5 users so I don't want to spend an excessive amount of time reading a 200 page user manual I am using ubuntu server edition version 7.04.

---

### Post by jsmidt on 2007-07-04
I also would be interested in this.  I am in a similar situation.

---

### Post by murraymca on 2007-07-05
Hi,

I have the printed version of the Linux Network Administrators Guide (3rd edition) and that has a short section in the back about migrating to LDAP Authentication.  The guide available on tldp is only the 2nd edition and doesn't seem to cover LDAP...

Unfortunately there is a bit too much info to just type away in here, although it would be easy to follow if you knew what you wanted before hand.  Basically the hardest part seemed to be configuring slapd; the client side was just a matter of changing /etc/nsswitch.conf

This link might help:  [http://www.padl.com/Contents/OpenSourceSoftware.html](http://www.padl.com/Contents/OpenSourceSoftware.html)

After the appropriate changes to slapd, there is a script on that site (migrate_all_online.sh) that helps populate your existing /etc/passwd into LDAP.

Good luck, sorry I couldn't provide much help ;)

I know you said you have followed the guides and they haven't worked, but I just found this link from the padl site:  [http://quark.humbug.org.au/publications/ldap/system_auth/sage-au/system_auth.html](http://quark.humbug.org.au/publications/ldap/system_auth/sage-au/system_auth.html)

It pretty much looks the same as what I was reading in the network administrators guide.  One thing to remember is (I think ;) ) you will need the following packages:  pam_ldap and nss_ldap ([http://www.padl.com/Contents/OpenSourceSoftware.html](http://www.padl.com/Contents/OpenSourceSoftware.html)).  On ubuntu 6.06 LTS they are libpam-ldap and libnss-ldap respectively.

Let us know how you get along, I've been meaning to do this myself but too much on at the moment :)

---

### Post by pclancy on 2007-07-05
I'm also looking into an LDAP server, so I started with the Ubuntu wiki, and I found the following LDAP server howto: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

Simply following the steps with the appropriate substitutions (I used a different base) didn't seem to work.  Then I tried doing exactly what the howto said (I set up an ldap server with the base dc=example,dc=com), and if I used ```
sudo ldapadd -x -W -c -D "cn=admin,dc=example,dc=com" -f init.ldif
``` after the server was started rather than using slapadd with the server stopped, I was able to add an example user.

At this point I thought that I would be okay if I just followed the client howto: [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

I added a sample user lionel like the server howto said, and then I started up my client, installed the required software, and then modified /etc/nsswitch.conf so that it looks in the ldap server.  So, using the command ```
getent passwd lionel
``` you should get a response from the ldap server with that users information.  I was not successful here.

Has anyone actually gotten these howto's to work?  Or, is there something obviously wrong with the howto's that we should know about?

---

### Post by mbradlcu on 2007-07-05
we use openldap at work and it's great,, when nothings broken ; )

anywho on the client machine I would test what can be seen from the openldap server with something like this:
note: replace the "dc's" with the name of yours,,,
```
ldapsearch -x -D "cn=Manager,dc=padl,dc=com" -b "dc=padl,dc=com" -W -h IP_of_your_openldap_server
```
if you get back the entries you put in setting up the server then we at least know it's a client problem..
here's my client setup:
apt-get install libpam-ldap libnss-ldap

Edit /etc/libnss-ldap.conf if needed, dpkg-reconfigure libnss-ldap didn't always configure the file?? go figure.

Edit /etc/nsswitch.conf:
> passwd: files ldap
group: files ldap
shadow: files ldap

Edit /etc/ldap/ldap.conf:
> BASE dc=some,dc=were,dc=com
URI ldap://ldap.your.server.bla

Edit /etc/pam.d/common-auth:
> auth required pam_nologin.so
auth sufficient pam_ldap.so
auth sufficient pam_unix.so shadow use_first_pass
auth required pam_deny.so


let me know if you have any problems with any of this..

---

### Post by murraymca on 2007-07-05
Might not be any help but you could set up logging on OpenLDAP and see if that helps.  I think you just edit slapd.conf with 'loglevel #' replacing # with one of these:

                      1      trace function calls
                      2      debug packet handling
                      4      heavy trace debugging
                      8      connection management
                      16     print out packets sent and received
                      32     search filter processing
                      64     configuration file processing
                      128    access control list processing
                      256    stats                            log
                             connections/operations/results
                      512    stats log entries sent
                      1024   print   communication   with   shell
                             backends
                      2048   entry parsing

Then restart openldap, I'm not sure of the accuracy of those levels, they are from:  [http://terrencemiao.com/Webmail/msg00461.html](http://terrencemiao.com/Webmail/msg00461.html)

Good luck.

---

### Post by jmb365 on 2007-07-08
I missed posting my log.  So see my next post, please

---

### Post by jmb365 on 2007-07-08
Hello all,

I have been banging my head on a wall for the past few days trying to setup an LDAP server and one client PC between 2 Ubuntu 7.04 (Feisty) PCs by following the HowTos posted at:
    [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer) and
    [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

I have read and attempted 4 other HowTos.  So far I have had only limited success.

Also after creating a user "as" (like "lionel") I do not know what to do next.   I tried login at the Client PC userid "as" at a text terminal <Ctrl-Alt-F1> but I get "Login incorrect" when I type the password that does work for the same user in the LDAP server PC.

I am able to successfully see a user "as" on the client that was created on the server, but I am not able to login as that user "as" from the client PC.  Whereas I am able to login at the LDAP server PC as user "as".  I have followed the directions of the above tutorials very carefully and attached below is my "log_level 256" dump.

The user "as" exists on the LDAP server from prior to my attempts at LDAP, created by tradition means (Menu -> User and Groups, etc).  I modified the data.ldif file and changed "lionel" to "as" along with other necessary changes and used:

    ```
sudo ldapadd -x -W -c -D 'cn=admin,dc=company,dc=com' -f /tmp/data.ldif
```

to import into the LDAP database.

My guess is that the LDAP database does not have a password for uid "as" since the data.ldif file only had <password> in the text file that was created.  I am at a loss as to how to set the LDAP password for the user "as" since: 

    ```
ldappasswd -W -x -D 'cn=admin,ou=People,dc=company,dc=com' 'uid=as'
```

does NOT work.  My attempts at using GUI program "gq" were useless too.

So far on the client I have tried:
```
 id as
```
which gives:
> 
uid=1003(as) gid=1003(as) groups=1003(as)


and
```
 ldapsearch -xLLL -b 'dc=company,dc=com' uid=as sn givenName cn
```
gives:
> 
dn: uid=as,ou=people,dc=company,dc=com
sn: s
givenName: as
cn: as


A snippet of "log_level 256" dump (from the LDAP-Server) in /var/log/syslog is shown below:
> 
Jul  8 17:21:00 LDAP-server slapd[7725]: @(#) $OpenLDAP: slapd 2.3.30 (Dec 13 2006 15:54:43) $ ^Ibuildd@palmer:/build/buildd/openldap2.3-2.3.30/debian/build/servers/slapd
Jul  8 17:21:00 LDAP-server slapd[7726]: slapd starting
Jul  8 17:22:59 LDAP-server slapd[7726]: conn=0 fd=11 ACCEPT from IP=192.168.1.30:48433 (IP=0.0.0.0:389)
Jul  8 17:22:59 LDAP-server slapd[7726]: conn=0 op=0 BIND dn="cn=admin,dc=company,dc=com" method=128
Jul  8 17:22:59 LDAP-server slapd[7726]: conn=0 op=0 BIND dn="cn=admin,dc=company,dc=com" mech=SIMPLE ssf=0
Jul  8 17:22:59 LDAP-server slapd[7726]: conn=0 op=0 RESULT tag=97 err=0 text=
Jul  8 17:22:59 LDAP-server slapd[7726]: conn=0 op=1 SRCH base="dc=company,dc=com" scope=2 deref=0 filter="(&(objectClass=shadowAccount)(uid=as))"
Jul  8 17:22:59 LDAP-server slapd[7726]: conn=0 op=1 SRCH attr=uid userPassword shadowLastChange shadowMax shadowMin shadowWarning shadowInactive shadowExpire shadowFlag
Jul  8 17:22:59 LDAP-server slapd[7726]: <= bdb_equality_candidates: (uid) index_param failed (18)
Jul  8 17:22:59 LDAP-server slapd[7726]: conn=0 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text=
Jul  8 17:23:55 LDAP-server slapd[7726]: conn=0 fd=11 closed (connection lost)
Jul  8 17:25:15 LDAP-server slapd[7726]: conn=1 fd=11 ACCEPT from IP=192.168.1.30:44877 (IP=0.0.0.0:389)
Jul  8 17:25:15 LDAP-server slapd[7726]: conn=1 op=0 BIND dn="cn=admin,dc=company,dc=com" method=128
Jul  8 17:25:15 LDAP-server slapd[7726]: conn=1 op=0 BIND dn="cn=admin,dc=company,dc=com" mech=SIMPLE ssf=0
Jul  8 17:25:15 LDAP-server slapd[7726]: conn=1 op=0 RESULT tag=97 err=0 text=
Jul  8 17:25:15 LDAP-server slapd[7726]: conn=1 op=1 SRCH base="dc=company,dc=com" scope=2 deref=0 filter="(&(objectClass=shadowAccount)(uid=as))"
Jul  8 17:25:15 LDAP-server slapd[7726]: conn=1 op=1 SRCH attr=uid userPassword shadowLastChange shadowMax shadowMin shadowWarning shadowInactive shadowExpire shadowFlag
Jul  8 17:25:15 LDAP-server slapd[7726]: <= bdb_equality_candidates: (uid) index_param failed (18)
Jul  8 17:25:15 LDAP-server slapd[7726]: conn=1 op=1 SEARCH RESULT tag=101 err=0 nentries=1 text=
Jul  8 17:25:17 LDAP-server slapd[7726]: conn=1 fd=11 closed (connection lost)


Hope this helps in finding the root of my problem...
Thank you for any suggestions or directions!  Can somebody help please?
Thanks
JMB

---

### Post by murraymca on 2007-07-08
Hello,

Have you had a look here:  [http://www.padl.com/OSS/MigrationTools.html](http://www.padl.com/OSS/MigrationTools.html) ?

It has scripts to migrate users, passwords etc into openldap.

Hope that helps,

Kind Regards.

---

### Post by jmb365 on 2007-07-08
> **murraymca said:**
> Hello,
Have you had a look here:  [http://www.padl.com/OSS/MigrationTools.html](http://www.padl.com/OSS/MigrationTools.html) ?
It has scripts to migrate users, passwords etc into openldap.
Hope that helps,
Kind Regards.


Hello,

Thank you very much for your reply.  I have tried the migration tools, and run into a problem there too.  I get:

```
cd /usr/share/migrationtools/
```
Edit the default migrationtools' config file migrate_common.ph and replace the following parameters with:
> 
$DEFAULT_MAIL_DOMAIN = "company.com";
$DEFAULT_BASE = "dc=company,dc=com";

Then export the values:
To migrate All the groups & users:
```

cd /usr/share/migrationtools/
./migrate_group.pl /etc/group ~/group.ldif
./migrate_passwd.pl /etc/passwd ~/passwd.ldif

```
Unfortunately, the script does not create the Group and People nodes, 
so we need to create it. To do this, 
```
gedit ~/people_group.ldif
```			
and fill it up with:
> 
dn: ou=People, dc=company, dc=com
ou: People
objectclass: organizationalUnit

dn: ou=Group, dc=company, dc=com
ou: Group
objectclass: organizationalUnit

Now, we have our users and groups converted to LDAP's ldif format. 
Import them into our LDAP database.
```

ldapadd -x -W -D "cn=admin,dc=company,dc=com" -f ~/people_group.ldif
ldapadd -x -W -D "cn=admin,dc=company,dc=com" -f ~/group.ldif
ldapadd -x -W -D "cn=admin,dc=company,dc=com" -f ~/passwd.ldif

```

But I get an error:
> 
Enter LDAP Password:
adding new entry "uid=root,ou=People,dc=company,dc=com"
ldap_add: Invalid syntax (21)
        additional info: objectClass: value #5 invalid per syntax


The begining of my ~/passwd.ldif looks like this:
> 
dn: uid=root,ou=People,dc=company,dc=com
uid: root
cn:: cm9vdA==
sn:: cm9vdA==
mail: [email]root@company.com[/email]
objectClass: person
objectClass: organizationalPerson
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: top
objectClass: krb5Principal
userPassword: {crypt}x
krb5PrincipalName: [email]root@COMPANY.COM[/email]
loginShell: /bin/bash
uidNumber: 0
gidNumber: 0
homeDirectory: /root
gecos: root

.
. rest deleted for brevity...
.


Why does it not like "objectClass: top".  Does it have something to do with the schema I have in /etc/ldap/slapd.conf?
> 
# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

One website suggested installing "heimdal-kdc" but that led to a whole lot more problems than I was prepared to tackle!
Do I need to include some other schema?

Besides, I have a very NAIVE question.  Is migrating traditional Linux user ids the only way to populate an LDAP database?  Can one not populate it by adding data through a GUI like "gq"?  Does one have to create a standard linux userid, then migrate it into LDAP?  I am not very clear about these fundamental steps.  Any insight and pointers would be helpful and much appreciated.

Thank you
JMB

---

### Post by murraymca on 2007-07-08
Hi jmb,

I'm not really sure on it all myself sorry, so I shouldn't be trying to help; apologies for that.  I just found this page:  [http://wiki.splitbrain.org/ldap](http://wiki.splitbrain.org/ldap)

The process seems a bit different, mainly info in passwd.ldif, perhaps it could help fix the problem.  Are you using kerberos?

Sorry I couldn't help more, hope you work it out.

Cheers

---

### Post by jmb365 on 2007-07-08
> **murraymca said:**
> Hi jmb,

I'm not really sure on it all myself sorry, so I shouldn't be trying to help; apologies for that.  I just found this page:  [http://wiki.splitbrain.org/ldap](http://wiki.splitbrain.org/ldap)

The process seems a bit different, mainly info in passwd.ldif, perhaps it could help fix the problem.  Are you using kerberos?

Sorry I couldn't help more, hope you work it out.

Cheers

Hello!

I am glad you are helping, because you solved one stumbling block I was encountering.  Upon reading the URL you had posted I realized that the problem was I had
> 
"$EXTENDED_SCHEMA = 1;" in /usr/share/migrationtools/migrate_common.ph


Which was causing the extra fields in the ldif file that the migration tool did not understand.  Changing it to "$EXTENDED_SCHEMA = 0;"  solved the migration problem.

Thanks!  Any other cues that you can offer (Smile)...!?
JMB

---

### Post by murraymca on 2007-07-09
Hiya,

Glad you are making some progress.  I noticed you had some kerberos stuff in your passwd.ldif, are there lines in slapd.conf that you have to uncomment if you want to use that?  Are you even using kerberos, if not I would probably comment those lines out.

Not sure of anything else at the moment, bit busy for the next few days so apologies if I don't reply sooner.  Apparently gq is suppose to be one of the better GUI programs for openldap...

Regards.

---

### Post by jmb365 on 2007-07-11
Hello All,

I have been able to successfully install and LDAP server & LDAP client on Feisty after several days of attempts.  There are many steps that the tutorials listed earlier that are missing in order to migrate user data into the LDAP database.  The migrationtools package needs modifications to make it work:

sudo gedit migrate_common.ph &
# Edit the default migrationtools' config file migrate_common.ph and 
# replace the following parameters with:
# $DEFAULT_MAIL_DOMAIN = "your-domain.com";
# $DEFAULT_BASE = "dc=your-domain,dc=com";
# $EXTENDED_SCHEMA = 0

Also remember to run the migrations tools using "sudo" (safer than being "root"), otherwise the encrypted passwords will not be read from the /etc/shadow file and thus cannot be imported into the LDAP database.  Without passwords in the LDAP database a user will NOT be able to login.

JMB

---

### Post by murraymca on 2007-07-11
Hi JMB,

Congratulations on working it out.  Would you care to share the changes you made?  

I thought you had already modified the migration script...anyways, oh I found a link to another gui tool for openldap; it lets you browse and edit...

[http://www-unix.mcs.anl.gov/~gawor/ldap/](http://www-unix.mcs.anl.gov/~gawor/ldap/)

Thanks for your help.

---

### Post by syadnom on 2007-08-16
i still cannot get ldap running and cant figure out schemas for egroupware.. 

im trying to get ldap up and running, then convert the server to use first local accounts, then ldap accounts, and then have egroupware authenticate off of ldap so that courier or cyrus imap/pop3 mail servers can authenticate off the same ldap! 

i have followed every single guide i can find and jst cant get it to work.  i have started over so many times im almost ready to give up!!

i dont need windows clients to authenticate against it and i dont need samba.  just ldap, courier or cyrus and egroupware.

can anyone help me out?!?!

---

### Post by syadnom on 2007-08-27
anyone at all?

---

### Post by ASquared21 on 2008-05-20
Hi,
my head to is banging off a wall. I need an authorization system, "LDAP", to authenticate 20 Ubuntu 8.04 laptops, 20 Macbooks (the same 20 machines), a Edubuntu server and 150+ website users.

The problem is that I need it ASAP and have no coding or file editing experiance.
Thanks for  any help,
Thanks,
Alex A.

---

### Post by mbradlcu on 2008-05-21
Hi,
I'm not sure why I subscribed to this thread as my openldap systems work very well,, anyway.. I wrote a couple php and shell scripts that add and remove users, notify them when their password or account is going to expire, and another that will allow them to change their password. you are welcome to any of them.
As far as setting up openldap, it can be a little tricky but not to bad. I have instructions but they're centric to my environment. I don't want to post them here but if you respond I could make them available less my specific settings,, and help you with yours.

thanks
Matt


> **ASquared21 said:**
> Hi,
my head to is banging off a wall. I need an authorization system, "LDAP", to authenticate 20 Ubuntu 8.04 laptops, 20 Macbooks (the same 20 machines), a Edubuntu server and 150+ website users.

The problem is that I need it ASAP and have no coding or file editing experiance.
Thanks for  any help,
Thanks,
Alex A.

---

### Post by ASquared21 on 2008-05-22
Hi,
I'll post soon after testing. On the web I found "phpldapadmin". This may answer "Scott 07's" question.
Thanks,
Alex A.

---

### Post by syadnom on 2008-05-22
for me, getting LDAP setup is the issue, not managing it.  webmin has a nice LDAP interface to work with and the command line tools are pretty straight forward replacements for the standard linux tools.

I wish there was an LDAP-Server package that configured LDAP on install and an LDAP-Client package that configured your system to authenticate against LDAP, either local or not.

---

### Post by ASquared21 on 2008-05-24
Hi,
I am using Ldap on a Hardy Hairin desktop. I have no idea why I can log into the Ldap server with PHPldapadmin as annonomous but not with the user name "admin". Do I need a DNS server?
Thanks,
Alex A.

---

### Post by ASquared21 on 2008-05-24
My modifications:

Ubuntu Forums > The Ubuntu Forum Community > Forum Archive > Main Support Categories > Server Platforms > PHPLDAPAdmin and OpenLDAP
PDA
View Full Version : PHPLDAPAdmin and OpenLDAP

rickyjones
November 30th, 2007, 01:01 PM
I'm having problems using PHPLDAPAdmin with OpenLDAP.

I'm trying to setup LDAP for use with Samba for a domain project (to see how feasible it is). I followed the instructions from [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer) to install and setup the initial OpenLDAP database.

The only thing I changed was the domain (dn=example,dn=local) and the passwords assigned.

I then installed PHPLdapAdmin and when I try to login using either the admin account or the user account that the OpenLDAP Wiki page used I get the following error:

Could not bind to the LDAP server.

LDAP said: Undefined attribute type
Error number: 0x11 (LDAP_UNDEFINED_TYPE)
Description: The attribute type specified is invalid. 

Anyone have any idea what needs to be fixed? I can connect fine anonymously but I need to login to make any changes.

Thanks!

-Richard
rickyjones
November 30th, 2007, 02:13 PM
Solved.

In the phpLDAPadmin config.php file I changed the line:

$ldapservers->SetValue($i,'login','attr','dn');


To:
$ldapservers->SetValue($i,'login','attr','cn');


Now I can login with the Admin user.

Anyone know how to contact the writer of the wiki article ([https://help.ubuntu.com/community/InstallingphpLDAPadmin)?](https://help.ubuntu.com/community/InstallingphpLDAPadmin)?) I recommend that the author update their directions to show what I had to do. Obviously the default install, which he writes about, does not work so easily with OpenLDAP based on the original directions.

-Richard
albertlash
February 3rd, 2008, 12:42 PM
Worked for me too - thanks!
mohammadrizki
May 3rd, 2008, 09:34 AM
Works for me too, thanks a lot...
vBulletin® v3.7.0, Copyright ©2000-2008, Jelsoft Enterprises Ltd.

---

### Post by ASquared21 on 2008-05-25
Hi,
My above modifications didn't work.
Thanks,
Alex A.

---

