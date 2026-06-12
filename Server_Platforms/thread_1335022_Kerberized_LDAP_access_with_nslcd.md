---
title: "Kerberized LDAP access with nslcd"
date: 2009-11-23
forum: Server Platforms
---

### Post by Despot on 2009-11-23
Kerberos provides a secure mechanism for authenticating hosts and users to services, even on insecure or untrusted networks. OpenLDAP supports Kerberos authentication as a GSSAPI implementation. This allows the system administrator to authenticate connections to the LDAP directory with Kerberos, providing a secure mechanism for authentication on networks where security is a concern.

Used in conjunction with the Kerberos PAM module and SSL/TLS encryption, the method outlined below can provide secure, encrypted account and authentication information to properly configured hosts anywhere on the network. This will allow a user to authenticate with the same set of credentials on any configured host, as part of a Single Sign-on (SSO) environment.

This guide uses the Upstart service management service to start and stop the nslcd daemon and maintain the necessary Kerberos credentials cache. These scripts are not necessary for Ubuntu 11.04 and newer. A similar configuration using the /etc/network/if-up.d/ script hooks is quite possible as well.

**Prerequisites**

This guide assumes you have the following in place and operational:

[LIST]
[*]A working Kerberos 5 environment (can acquire tickets with kinit, etc). A tutorial on configuring a Kerberos environment can be found here: [http://www.alittletooquiet.net/text/kerberos-on-ubuntu/](http://www.alittletooquiet.net/text/kerberos-on-ubuntu/)
[*]The host is properly configured to get account information from the LDAP directory (ldapwhoami, ldapsearch, getent passwd etc). Some useful information for setting up a host to get account information from an LDAP directory is available here: [https://help.ubuntu.com/community/LDAPClientAuthentication#Name%20Service](https://help.ubuntu.com/community/LDAPClientAuthentication#Name%20Service)
[*]SASL/GSSAPI authentication to the LDAP server using your Kerberos credentials is functional (ldapsearch -Y GSSAPI)
[*](Ubuntu 10.10 and older) Upstart is installed and functional. Upstart is installed and enabled by default in Ubuntu 9.10 (Karmic Koala). It is available as an option in older versions for Ubuntu.
[*]Both forward and reverse DNS lookups resolve to matching names, that is to say "nslookup client.hostname" resolves to the correct IP address, and vice versa.
[/LIST]
**Setup**

[LIST=1]
[*]Create the appropriate Kerberos principals in the Kerberos realm. In my configuration, the principals are in the format "host/<fqdn>", where "<fqdn>" is the Fully Qualified Domain Name of the host that will need access the LDAP directory. Some people may want to use a separate "ldap" service, in which case the principals would take the form "ldap/<fqdn>".
[*]Create a keytab for the principal that will be used to access the LDAP directory:
[LIST=1]
[*]Start kadmin and log in as an admin
[*]Run the following command:
```
ktadd -k /path/to/keytab <principal>
```
[*]Securely transfer (via flash drive, disk, or encrypted connection) the keytab to the client host.
[/LIST]
[*]For Ubuntu versions prior to 10.10, it is advisable to add the Debian unstable repo to the software repository list so we can download the latest version of nslcd:
[LIST=1]
[*]Add the apt-line to your sources.list, manually or through Synaptic:
```
 deb ftp://ftp.debian.org/debian/ unstable main
```
[*]Get GPG key as indicated here: [http://ftp-master.debian.org/keys.html](http://ftp-master.debian.org/keys.html)
[*]Add the GPG key to the apt keyring as explained here: [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)
[/LIST]
 
[*]Install packages:
```
sudo apt-get install libnss-ldapd kstart
```
During the initial configuration, make sure to enable name services for passwd, groups, and shadow.
[*]Disable or remove the Debian unstable repository to avoid messages from the Update Manager.
[*](Optional) If you plan to use Kerberos for local authentication via the Kerberos pluggable authentication module (which is recommended), remove the libpam-ldapd package that is installed as a recommended package.
[/LIST]

**Upstart Setup**

Add the following Upstart scripts to /etc/init/. The first script starts the nslcd daemon, the second maintains the Kerberos credentials cache.

_/etc/init/nslcd.conf_:

```
# nslcd - LDAP connection daemon
#
# nslcd is a daemon that is used to do LDAP queries
# for NSS and PAM modules.
#
# Adapted from the System V nslcd init script and http://ubuntuforums.org/showthread.php?t=1335022

description "LDAP connection daemon"
author "Caleb Callaway <enlightened.despot@gmail.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

env PATH=/bin:/usr/bin:/sbin:/usr/sbin
env NSLCD_BIN=/usr/sbin/nslcd
env NSLCD_DESC="LDAP connection daemon"
env NSLCD_CFG=/etc/nslcd.conf
env NSLCD_LOGFILE="/tmp/nslcd.log"

pre-start script
	[ -x "$NSLCD_BIN" ] || exit 1
end script

script
	# read defaults
	[ -f /etc/default/nslcd ] && . /etc/default/nslcd

	# start nslcd
	echo "Starting $NSLCD_DESC nslcd" > $NSLCD_LOGFILE
end script

exec $NSLCD_BIN

post-start script
	if [ -e /etc/init.d/nscd ];
	then
		/etc/init.d/nscd restart
	fi
end script

post-stop script
	if [ -e /etc/init.d/nscd ];
	then
		/etc/init.d/nscd stop
	fi
end script

```
_/etc/init/nslcd-kerberos.conf_

```

# nslcd-k5start - Maintain a Kerberos ticket cache for nslcd
# Adapted from the System V nslcd init script

description	"Maintain a Kerberos ticket cache for nslcd"
author "Caleb Callaway <enlightened.despot@gmail.com>"

start on starting nslcd
stop on stopping nslcd

env PATH=/bin:/usr/bin:/sbin:/usr/sbin
env NSLCD_CFG=/etc/nslcd.conf

env K5START_BIN=/usr/bin/k5start
env K5START_DESC="Kerberos cache maintainer for nslcd"
env NSLCD_USER=nslcd
env NSLCD_GROUP=nslcd
env K5START_MODE=600
env K5START_KEYTAB=/etc/krb5.keytab
env K5START_CCREFRESH=60
env K5START_LOGFILE="/tmp/nslcd-k5start.log"

pre-start script
	[ -f "$NSLCD_CFG" ] || exit 1

	#upstart's env stanza seems to be a bit simplistic, so we do fancy stuff here.
	NSLCD_STATEDIR=/var/run/nslcd
	K5START_PIDFILE=$NSLCD_STATEDIR/k5start_nslcd.pid
        NSLCD_USER=$(sed -n 's/^uid *\([^ ]*\) *$/\1/ip' $NSLCD_CFG)
        NSLCD_GROUP=$(sed -n 's/^gid *\([^ ]*\) *$/\1/ip' $NSLCD_CFG)
        K5START_PRINCIPAL="host/$(hostname -f)"
        K5START_CCFILE=$(sed -n 's/^krb5_ccname *\(FILE:\)\?\([^: ]*\) *$/\2/ip' $NSLCD_CFG)

        if [ -e /etc/default/nslcd ]
        then
        . /etc/default/nslcd
        fi

	#make sure we have a state directory for the Kerberos cache
	[ -d "$NSLCD_STATEDIR" ] || ( mkdir -m 755 "$NSLCD_STATEDIR" ; \
		                chown $NSLCD_USER:$NSLCD_GROUP "$NSLCD_STATEDIR" )

	date >> $K5START_LOGFILE
	echo "Initializing credentials cache."  >> $K5START_LOGFILE
	echo "Init command: \"/usr/bin/kinit -V -c $K5START_CCFILE -k -t $K5START_KEYTAB $K5START_PRINCIPAL\"" >> $K5START_LOGFILE

	#make sure we have a credentials cache before nslcd starts.
	/usr/bin/kinit -V -c $K5START_CCFILE -k -t $K5START_KEYTAB $K5START_PRINCIPAL 1>>$K5START_LOGFILE 2>>$K5START_LOGFILE
end script

script
	#upstart's env stanza seems to be a bit simplistic, so we do fancy stuff here.
	NSLCD_STATEDIR=/var/run/nslcd
	K5START_PIDFILE=$NSLCD_STATEDIR/k5start_nslcd.pid
        NSLCD_USER=$(sed -n 's/^uid *\([^ ]*\) *$/\1/ip' $NSLCD_CFG)
        NSLCD_GROUP=$(sed -n 's/^gid *\([^ ]*\) *$/\1/ip' $NSLCD_CFG)
        K5START_PRINCIPAL="host/$(hostname -f)"
        K5START_CCFILE=$(sed -n 's/^krb5_ccname *\(FILE:\)\?\([^: ]*\) *$/\2/ip' $NSLCD_CFG)

        if [ -e /etc/default/nslcd ]
        then
        . /etc/default/nslcd
        fi
	
	echo "Starting daemon" >> $K5START_LOGFILE        
	echo "Command: \"$K5START_BIN -p $K5START_PIDFILE -o $NSLCD_USER -g $NSLCD_GROUP -m $K5START_MODE -f $K5START_KEYTAB -K $K5START_CCREFRESH -u $K5START_PRINCIPAL -k $K5START_CCFILE\"" >> $K5START_LOGFILE

        # check if we should use k5start by default (sasl_mech should be GSSAPI and
        # krb5_ccname should be found)
        if [ -x "$K5START_BIN" ] && \
           grep -q '^sasl_mech *GSSAPI$' $NSLCD_CFG && \
           [ -n "$K5START_CCFILE" ]
        then
            $K5START_BIN -p $K5START_PIDFILE -o $NSLCD_USER -g $NSLCD_GROUP -m $K5START_MODE -f $K5START_KEYTAB -K $K5START_CCREFRESH -u $K5START_PRINCIPAL -k $K5START_CCFILE
        log_end_msg $?

        fi
end script

post-stop script
	#upstart's env stanza seems to be a bit simplistic, so we do fancy stuff here.
	NSLCD_STATEDIR=/var/run/nslcd
	K5START_PIDFILE=$NSLCD_STATEDIR/k5start_nslcd.pid
        NSLCD_USER=$(sed -n 's/^uid *\([^ ]*\) *$/\1/ip' $NSLCD_CFG)
        NSLCD_GROUP=$(sed -n 's/^gid *\([^ ]*\) *$/\1/ip' $NSLCD_CFG)
        K5START_PRINCIPAL="host/$(hostname -f)"
        K5START_CCFILE=$(sed -n 's/^krb5_ccname *\(FILE:\)\?\([^: ]*\) *$/\2/ip' $NSLCD_CFG)

	if [ -e /etc/default/nslcd ]
	then
	. /etc/default/nslcd
	fi

	[ -n "$K5START_PIDFILE" ] && rm -f $K5START_PIDFILE
	[ -n "$K5START_CCFILE" ] && rm -f $K5START_CCFILE
end script
```

**Configuration**

[LIST=1]
[*]Add the following lines to /etc/nslcd.conf:
```
#SASL
use_sasl on
sasl_mech GSSAPI
krb5_ccname FILE:/tmp/host.tkt

```Adjust the path to the credentials cache as necessary.
[*]Modifiy or create the /etc/default/nslcd configuration file referenced in the Upstart scripts:```

#Kerberos stuff
KRB5_KEYTAB=/etc/krb5.keytab
KRB5_CCNAME=/tmp/host.tkt
KRB5_PRINCIPAL="host/`hostname -f`"
#time in minutes between cache updates
KRB5_CCREFRESH=60
```Adjust the options as necessary.
[/LIST]
**Starting Up**

To trigger the event that starts the script, issue the following command:
```
sudo initctl emit net-device-up IFACE=<iface>
```<iface> is typically "eth0". The name of your network interfaces will be displayed as part of the "ifconfig -a" output.

If the command returns silently, the job probably started correctly. This can be verified with this command:

```
initctl list | grep nslcd
```The nslcd and nslcd-kerberos jobs should be listed as running.

The "net-device-up" event is emitted by the system's networking subsystems whenever the applicable interface is brought up, so it is only necessary to issue this command once, for testing.

**Testing**

To verify the daemon is getting account information from the LDAP directory, issue the following command:

```
getent passwd
```If everything is configured correctly, account information from the LDAP directory should show up in the output.

NOTE: be careful with users or groups that are defined both locally and in the LDAP directory. The /etc/nsswitch.conf file controls the order in which requests for user and group information is resolved, and if the local resources are consulted first (or vice versa) you may *think* things are working correctly when they are in fact not. It is best to test the configuration with users or groups that exist in only one source.

**Troubleshooting**

In the event something does *not* work as expected (for instance, you get an "event failed" message when running initctl), here are some tips:

[LIST]
[*]You can start the NSLCD daemon manually by running:
```
sudo nslcd -d
```The messages about SASL support being unstable are expected.
[*]Try starting the nslcd-kerberos Upstart job manually:
```
sudo start nslcd-kerberos
```
[*]Make sure the keytab you intend to use for the credentials cache is present, valid, and has the correct access permissions (read/write by root, no access by anyone else).
[*]Debug information can sometimes be found in /var/log/daemon.log and /var/log/auth.log
[*]the verbosity of Upstart can be increased by issuing the command
```
sudo initctl log-priority <level>
```Valid levels are found on the initctl manpage.
[*]It appears to be necessary for various aspects of Kerberos authentication that both forward and reverse DNS lookups resolve to matching names. To test this (assuming DNS is deployed on your network), do an "nslookup" against the client's hostname (Fully Qualified Domain Name if applicable), then do a lookup against the IP address that is listed. The DNS names should be exactly equivalent.
[*]The command "hostname -f" should also return the fully qualified domain name of the client. To enable this behavior, re-order the service list on "hosts" line in /etc/nsswitch.conf so "dns" comes before "files" (this assumes that DNS is available on your network).
[/LIST]

---

### Post by simbloke on 2010-05-11
Thanks for this, I am setting this up on 10.04 but have modified the upstart nslcd.conf to be simpler and not refer to a particular eth interface:

```
# nslcd - LDAP connection daemon
#
# nslcd is a daemon that is used to do LDAP queries
# for NSS and PAM modules.

description	"LDAP connection daemon"
author		"Caleb Callaway <enlightened.despot@gmail.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

env NSLCD_STATEDIR=/var/run/nslcd
env LOGFILE="/var/log/nslcd.log"

script
	date >> $LOGFILE
	echo "Starting nslcd." >> $LOGFILE

  	[ -d "$NSLCD_STATEDIR" ] || ( mkdir -p -m 755 "$NSLCD_STATEDIR" ; \
                                chown nslcd:nslcd "$NSLCD_STATEDIR" )

	exec /usr/sbin/nslcd
end script

post-start script
	if [ -e /etc/init.d/nscd ];
	then
		/etc/init.d/nscd restart
	fi
end script
```

---

### Post by Despot on 2011-05-30
Thanks for the changes, simbloke, I've incorporated them into the howto, and also updated it for newer Ubuntu releases.

---

### Post by 1971hemicuda on 2011-11-10
With the release of 11.10...I was wondering if there was another update needed...this LOOKS like it would be exactly what I need where i'm at...but i can't seem to get everything to start up properly.  ...i have another jenky upstart job that I wrote which just basically runs k5start with a bunch of options...but I would love to get this working, as its much more elegant.  

as for the 2 upstart scripts...it is said they aren't needed in 11.04...but i don't see upstart jobs, or a way of starting k5start without them...

---

### Post by Despot on 2011-12-20
1971hemicuda: check out the Troubleshooting section for ideas. If you describe exactly what's going wrong, I may be able to help.

I've removed the note about the configuration possibly being unnecessary in Natty...it was confusingly worded and only applicable in some cases. Basically, sometimes the init.d scripts will start nslcd after the network connection comes up, which is the desired behavior. In this scenario, the Upstart scripts aren't strictly necessary. Generally speaking, the Upstart scripts are preferrable because they provide a stronger guarantee that nslcd won't start until a network connection is available.

---

### Post by RoadRunnr on 2012-01-03
Calling an init.d script from an upstart job is not very. It would be much more helpful to convert the init.d script completely into an upstart job

nslcd.conf can IMHO simplified to this:
```

# for NSS and PAM modules.
#
# Adapted from the System V nslcd init script and http://ubuntuforums.org/showthread.php?t=1335022

description "LDAP connection daemon"
author "Caleb Callaway <enlightened.despot@gmail.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

env PATH=/bin:/usr/bin:/sbin:/usr/sbin
env NSLCD_BIN=/usr/sbin/nslcd
env NSLCD_DESC="LDAP connection daemon"
env NSLCD_CFG=/etc/nslcd.conf
env NSLCD_LOGFILE="/tmp/nslcd.log"

pre-start script
	[ -x "$NSLCD_BIN" ] || exit 1
end script

script
	# read defaults
	[ -f /etc/default/nslcd ] && . /etc/default/nslcd

	# start nslcd
	echo "Starting $NSLCD_DESC nslcd" > $NSLCD_LOGFILE
end script

exec $NSLCD_BIN

```

---

### Post by simbloke on 2012-01-03
> **RoadRunnr said:**
> Calling an init.d script from an upstart job is not very. It would be much more helpful to convert the init.d script completely into an upstart job

Yes you're right, it's not very something ;) Don't know what I was thinking at the time...

---

### Post by RoadRunnr on 2012-01-03
> **simbloke said:**
> Yes you're right, it's not very something ;) Don't know what I was thinking at the time...

;)

just update my initial post with a simplified version of the nslcd.conf, the calls to init.d can IMHO go away completely.

I'm thinking about removing the kinit calls from nslcd-kerberos.conf completely. k5start is supposed to do the same thing. Or is there a specific reason it has to be called first?

---

### Post by Despot on 2012-04-27
RoadRunnr: k5start does do the same thing. The reason for the kinit call is to make sure a valid credentials cache was present before the nslcd-kerberos script returns. k5start daemonizes, so we can't guarantee nslcd will have a valid cache using k5start alone, unless k5start has some "block until credentials cache is initialized, then daemonize" flag that I don't know about.

---

