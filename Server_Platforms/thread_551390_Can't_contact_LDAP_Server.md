---
title: "Can't contact LDAP Server"
date: 2007-09-15
forum: Server Platforms
---

### Post by dc.manage.service on 2007-09-15
Hi there

I was following the documentation to setup openLDAP stuff - [https://help.ubuntu.com/7.04/server/C/openldap-server.html](https://help.ubuntu.com/7.04/server/C/openldap-server.html)

I've modified the ldap.conf and slapd.conf accordingly. Also,  I've created init.ldif.

But when I tried for testing by doing: ldapsearch -xLLL -b "dc=dewacorp,dc=com" uid=testname sn givenName cn

I got the following message: Can't contact LDAP Server

Any ideas?

---

### Post by NewbieNik on 2007-09-15
dc, I get the same problem on Feisty only. Its because the sudo /etc/init.d/slapd start command does NOT start the server.
For some reason and Im looking to the community for help on this, the only way I can get it to start correctly is to use the logging level command so,

sudo slapd -s 256

then check using the network tool netstat  to see if port 389 is open, if so, roberts your dads brother. I just need to find a way to get slapd to start as part of the inetd system now

---

### Post by dc.manage.service on 2007-09-15
Hi NewbieNik

Thanks for that and it is CONNECTED now. I've added the port 389 by doing this:

```
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 389 -j ACCEPT
```

and also check again the port by doing this:

netstat -an | grep "LISTEN "

Run the command:

sudo slapd -s 256

It's working !!! I have to reinstall again though cause LDIF is not picking up the entry that I want. I was playing around on this. :) But at least it's connecting!!! Woo hoo.

If I want to use server version 6 instead and the client is 7 leave as it is, does this thing work?

---

### Post by info on 2007-09-15
I'm also seeing this. Can someone compare pre-Feisty and Feisty files and see what is different? the slapd script does stop the server, but won't start or restart. I was able to get it to run using just 'sudo slapd', but didn't require the other option. It doesn't automatically start when rebooted, either.

If I figure it out, I'll post it here. If anyone has an earlier version of the script, that might help, too.

---

### Post by dc.manage.service on 2007-09-15
BTW .. how to find whether the service is running or not?

Thanks

---

### Post by info on 2007-09-16
use this command: 
ps -A | grep slapd

You can try and run it using:
sudo slapd

Then see if it's running again or not. I saw another post that said you needed to use the -s option, but I didn't need to.

---

### Post by info on 2007-09-16
Okay, I finally figured it out for me; I hope this helps you. I finally found some of the issue in the syslog. I was getting this error:
```
hostname slapd[1234]: daemon: bind(6) failed errno=13 (Permission denied)
```

I went the the /etc/init.d/slapd script and traced the functions and ran it in a number of ways manually. It just wouldn't run when specifying *openldap* as the user/group in the options. 

The error above along with web research made me realize that it was an access/file permission issue. I tried making sure files could be read and written as needed using the *openldap* account (use sudo -u openldap).

Finally, I figured it out. The database files I created upon importing my initial *init.ldif* file were owned by *root*. As such, *openldap* couldn't read or touch them. The instructions here tell you to create an ldap database and run the command as sudo (and thus *root*:
```
sudo slapadd -l init.ldif
```

This creates the database, but the database files are owned by *root* when you do this. Therefore, to create these owned by the *openldap* user, you probably need to run them as *openldap*:
```
sudo -u openldap slapadd -l init.ldif
```

Or just chown then (using sudo) after the fact. My slapd now starts up just fine.

BTW, I think I might have found an error in the /etc/init.d/slapd script. It runs okay as is, but lines 25-31:
```
# Load the default location of the slapd config file
if [ -z "$SLAPD_CONF" ]; then
        SLAPD_CONF="/etc/ldap/slapd.conf"
else
        SLAPD_OPTIONS="-f $SLAPD_CONF $SLAPD_OPTIONS"
        SLURPD_OPTIONS="-f $SLAPD_CONF $SLURPD_OPTIONS"
fi
```
looks to me like they should be this:
```
# Load the default location of the slapd config file
if [ -z "$SLAPD_CONF" ]; then
        SLAPD_CONF="/etc/ldap/slapd.conf"
fi
SLAPD_OPTIONS="-f $SLAPD_CONF $SLAPD_OPTIONS"
SLURPD_OPTIONS="-f $SLAPD_CONF $SLURPD_OPTIONS"
```
because otherwise the *-f configfile* command option isn't appended properly to the command. It would be nice if someone could confirm that. It works either way for me, but I'm also using the default. :-)

Hope this helps others.

---

