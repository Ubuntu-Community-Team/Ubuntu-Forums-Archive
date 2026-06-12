---
title: "Openldap - unable to add entries PLEASE help"
date: 2007-01-09
forum: Server Platforms
---

### Post by yonta on 2007-01-09
Hi :)

I just installed ubuntu, so i'm quite newbie. That said i managed to install ldap & openldap ok. I then got phpldapmyadmin and i am able to login. And the trouble starts.. 

phpldapadmin recognizes my rootdn because it shows 
dc=moodleldap,dc=com 
but it says it doesn't exist. I then procceed to create it but it just gives me the error 'the object doesn't exist'.

If i try 
ldapadd -D cn=users,dc=moodleldap,dc=com -W
it asks me for the password and then shows this error:
SASL/DIGEST-MD5 authentication started
ldap_sasl_interactive_bind_s: Internal (implementation specific) error (80)
        additional info: SASL(-13): user not found: no secret in database
 
I know the password must be right because i'm able to login at phpldapadmin.

i have a host configured in the hosts file at moodleldap.com

Here's my slapd.conf (most relevant parts):

# 'database' directive occurs
database        bdb
# The base of your directory in database #1
suffix          "dc=moodleldap, dc=com"
rootdn		"cn=admin,dc=moodleldap,dc=com"
rootpw		mypass
defaultaccess read
                 access to attr=userpassword
                 by self write
                 by dn="cn=admin, dc=moodleldap, dc=com" write
                 by * compare

And here's my ldap.conf (relevant part)

BASE	dc=moodleldap,dc=com
#URI	ldap://moodleldap
HOST	127.0.0.1
#master.example.com:666
moodleldap.com:666
#com:666

So pleaase if anyone can help me, i would really appreciate it... (i'm in a tight schedule to make this work)

best to you all,

sofia

---

