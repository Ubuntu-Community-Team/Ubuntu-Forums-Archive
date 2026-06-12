---
title: "Single Sign On problems"
date: 2009-08-26
forum: Server Platforms
---

### Post by oliveiraj on 2009-08-26
Hi all,

This is my first. I apologise if I'm doing something wrong here.

I'm trying to integrate an e-mail server and Open MailArchiva. E-mail server works with Openldap but Open MailArchiva only works with AD or Kerberos+Openldap.
Somehow I need to sync users and passwords between Openldap and Kerberos and I found out an how-to about Sign Sign On with Kerberos+OpenLdap.
I tried to follow step-by-step that how-to but things went wrong. I'll paste here my configuration files if necessary.
Since my original goal was to build an Openldap tree I started with Ubuntu 8.04 server edition and installed Openldap (without ssl) plus phpldapadmin: everything went smoothly.
Then I installed, configured Kerberos and added ssl to my ldap. From that point I ceased to access ldap:

 ldapsearch -x -h ldaps://ds1.home-pt.net/ -b "dc=home-pt,dc=net" -s sub "objectclass=*"

results in:

ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

but I can see that port 636 (ldaps) is open and receiving requests. Furthermore all daemons start without errors.

With that I went backwards in my configuration to see what was wrong:

kinit

results in:

kinit(v5): Client not found in Kerberos database while getting initial credentials

and

klist

results in:

klist: No credentials cache found (ticket cache FILE:/tmp/krb5cc_1000)

Kerberos 4 ticket cache: /tmp/tkt1000
klist: You have no tickets cached

kdc.conf
--------------------------------------------------------------------------
[kdcdefaults]
    kdc_ports = 750,88

[realms]
    HOME-PT.NET = {
        database_name = /var/lib/krb5kdc/principal
        admin_keytab = FILE:/etc/krb5kdc/kadm5.keytab
        acl_file = /etc/krb5kdc/kadm5.acl
        key_stash_file = /etc/krb5kdc/stash
        kdc_ports = 750,88
        max_life = 10h 0m 0s
        max_renewable_life = 7d 0h 0m 0s
        master_key_type = des3-hmac-sha1
        supported_enctypes = des3-hmac-sha1:normal des-cbc-crc:normal des:norma$
        default_principal_flags = +preauth
    }

kadm5.acl
--------------------------------------------------------------------------
*/admin@HOME-PT.NET    *

krb5.conf
--------------------------------------------------------------------------
[libdefaults]
        default_realm = HOME-PT.NET

# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true

# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.

#       default_tgs_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#       default_tkt_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5
#       permitted_enctypes = aes256-cts arcfour-hmac-md5 des3-hmac-sha1 des-cbc-crc des-cbc-md5

# The following libdefaults parameters are only for Heimdal Kerberos.
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true

[realms]
        HOME-PT.NET = {
                kdc = 192.168.1.6
                kdc = 192.168.1.7
                admin_server = 192.168.1.6
        }
        ATHENA.MIT.EDU = {
                kdc = kerberos.mit.edu:88
                kdc = kerberos-1.mit.edu:88
                kdc = kerberos-2.mit.edu:88
                admin_server = kerberos.mit.edu
                default_domain = mit.edu
        }
...
[login]
        krb4_convert = true
        krb4_get_tickets = false

--------------------------------------------------------------------------

Kerberos database was created and add principals

slapd.conf
--------------------------------------------------------------------------
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        none

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_hdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         hdb

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# The base of your directory in database #1
suffix          "dc=home-pt,dc=net"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
rootdn          "cn=admin,dc=home-pt,dc=net"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"
rootpw          {SSHA}a2QitAjJz+oPS+Doh2eNDE52N6InX7En

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See [http://bugs.debian.org/303057](http://bugs.debian.org/303057) for more
# information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass,entryCSN,entryUUID eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# Where to store the replica logs for database #1
replogfile      /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword,shadowLastChange
        by dn="cn=admin,dc=home-pt,dc=net" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people

# are wont to do you'll still need this if you
# want SASL (and possible other things) to work
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=home-pt,dc=net" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=home-pt,dc=net" write
#        by dnattr=owner write

# Replica

moduleload      syncprov.la
overlay syncprov
syncprov-checkpoint 100 10
syncprov-sessionlog 100
TLSCACertificateFile /etc/ldap/ssl/server.pem
TLSCertificateFile /etc/ldap/ssl/server.pem
TLSCertificateKeyFile /etc/ldap/ssl/server.pem

sasl-secprops noanonymous,noplain,noactive
authz-regexp uid=([^,]*),cn=[^,]*,cn=auth uid=$1,ou=users,dc=home-pt,dc=net

#######################################################################
# Specific Directives for database #2, of type 'other' (can be hdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"

/etc/default/slpad
--------------------------------------------------------------------------
# Default location of the slapd.conf file. If empty, use the compiled-in
# default (/etc/ldap/slapd.conf). If using the cn=config backend to store
# configuration in LDIF, set this variable to the directory containing the
# cn=config data.
SLAPD_CONF=

# System account to run the slapd server under. If empty the server
# will run as root.
SLAPD_USER="openldap"

# System group to run the slapd server under. If empty the server will
# run in the primary group of its user.
SLAPD_GROUP="openldap"

# Path to the pid file of the slapd server. If not set the init.d script
# will try to figure it out from $SLAPD_CONF (/etc/ldap/slapd.conf by
# default)
SLAPD_PIDFILE=

# slapd normally serves ldap only on all TCP-ports 389. slapd can also
# service requests on TCP-port 636 (ldaps) and requests via unix
# sockets.
# Example usage:
SLAPD_SERVICES="ldaps://ds1.home-pt.net"

# If SLAPD_NO_START is set, the init script will not start or restart
# slapd (but stop will still work).  Uncomment this if you are
# starting slapd via some other means or if you don't want slapd normally
# started at boot.
#SLAPD_NO_START=1

# If SLAPD_SENTINEL_FILE is set to path to a file and that file exists,
# the init script will not start or restart slapd (but stop will still
# work).  Use this for temporarily disabling startup of slapd (when doing
# maintenance, for example, or through a configuration management system)
# when you don't want to edit a configuration file.
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd

# For Kerberos authentication (via SASL), slapd by default uses the system
# keytab file (/etc/krb5.keytab).  To use a different keytab file,
# uncomment this line and change the path.
#export KRB5_KTNAME=/etc/krb5.keytab

# Additional options to pass to slapd
SLAPD_OPTIONS=""

--------------------------------------------------------------------------

openssl s_client -connect ds1.home-pt.net:636 -showcerts

results in:

CONNECTED(00000003)
depth=0 /C=PT/ST=Lisbon/L=Lisbon/O=Mail on demand/OU=Lisbon/CN=ds1.home-pt.net/emailAddress=jvf_oliveira@home-pt.net
verify error:num=18:self signed certificate
verify return:1
depth=0 /C=PT/ST=Lisbon/L=Lisbon/O=Mail on demand/OU=Lisbon/CN=ds1.home-pt.net/emailAddress=jvf_oliveira@home-pt.net
verify return:1
---
Certificate chain
 0 s:/C=PT/ST=Lisbon/L=Lisbon/O=Mail on demand/OU=Lisbon/CN=ds1.home-pt.net/emailAddress=jvf_oliveira@home-pt.net
   i:/C=PT/ST=Lisbon/L=Lisbon/O=Mail on demand/OU=Lisbon/CN=ds1.home-pt.net/emailAddress=jvf_oliveira@home-pt.net
-----BEGIN CERTIFICATE-----
MIIDvzCCAyigAwIBAgIJAIys9qOk92q7MA0GCSqGSIb3DQEBBQUAMIGcMQswCQYD
VQQGEwJQVDEPMA0GA1UECBMGTGlzYm9uMQ8wDQYDVQQHEwZMaXNib24xFzAVBgNV
BAoTDk1haWwgb24gZGVtYW5kMQ8wDQYDVQQLEwZMaXNib24xGDAWBgNVBAMTD2Rz
MS5ob21lLXB0Lm5ldDEnMCUGCSqGSIb3DQEJARYYanZmX29saXZlaXJhQGhvbWUt
cHQubmV0MB4XDTA5MDgyNTEyMzkzMVoXDTE5MDgyMzEyMzkzMVowgZwxCzAJBgNV
BAYTAlBUMQ8wDQYDVQQIEwZMaXNib24xDzANBgNVBAcTBkxpc2JvbjEXMBUGA1UE
ChMOTWFpbCBvbiBkZW1hbmQxDzANBgNVBAsTBkxpc2JvbjEYMBYGA1UEAxMPZHMx
LmhvbWUtcHQubmV0MScwJQYJKoZIhvcNAQkBFhhqdmZfb2xpdmVpcmFAaG9tZS1w
dC5uZXQwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBALfPk6GTABeu182I7Rkx
OI6yEsXpEQVQN8sdBUFJKulGJTafQtm7EboJOgyzjkBF/CzXMmBD/fNkLA4K6hoK
QB0hUgKPKpDviIo8bg5kpCHgU40TVU+D1ItRhWvCA/d8gOjRvGl8EIaxO0Np70Ch
bj3/afKvPCh0F5Qi2cXny2hfAgMBAAGjggEFMIIBATAdBgNVHQ4EFgQUDb7Ql/bF
XndPW7r1y1L63KREVk0wgdEGA1UdIwSByTCBxoAUDb7Ql/bFXndPW7r1y1L63KRE
Vk2hgaKkgZ8wgZwxCzAJBgNVBAYTAlBUMQ8wDQYDVQQIEwZMaXNib24xDzANBgNV
BAcTBkxpc2JvbjEXMBUGA1UEChMOTWFpbCBvbiBkZW1hbmQxDzANBgNVBAsTBkxp
c2JvbjEYMBYGA1UEAxMPZHMxLmhvbWUtcHQubmV0MScwJQYJKoZIhvcNAQkBFhhq
dmZfb2xpdmVpcmFAaG9tZS1wdC5uZXSCCQCMrPajpPdquzAMBgNVHRMEBTADAQH/
MA0GCSqGSIb3DQEBBQUAA4GBAA98Tp3H6WBzVK75yPzxSomyOBu6rrY4HlUToCzM
A7hLWu1Rms27oiYCSLMo7OJEZfgiUZ+RUonfkoJXsEWWydyGqQ7GayloGO443xF3
VLKH6TLsuQEc29LSB1cDSIt6H7pHPkuV75488VxEO/oTjifSyAxySNdVruX1LM+D
oOo8
-----END CERTIFICATE-----
---
Server certificate
subject=/C=PT/ST=Lisbon/L=Lisbon/O=Mail on demand/OU=Lisbon/CN=ds1.home-pt.net/emailAddress=jvf_oliveira@home-pt.net
issuer=/C=PT/ST=Lisbon/L=Lisbon/O=Mail on demand/OU=Lisbon/CN=ds1.home-pt.net/emailAddress=jvf_oliveira@home-pt.net
---
No client certificate CA names sent
---
SSL handshake has read 1301 bytes and written 316 bytes
---
New, TLSv1/SSLv3, Cipher is AES256-SHA
Server public key is 1024 bit
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : AES256-SHA
    Session-ID: 5D8370554946F19A4DE45971267437FD0220266E8497A279E2195F7097340DE9
    Session-ID-ctx: 
    Master-Key: A3BA7FEF403600EC9B3E99AA32E75360BDC17A45249D90F67233892544FA9B60B4E3E4E1404E54009D4E344ABCBC30F4
    Key-Arg   : None
    Start Time: 1251308499
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---

ldap.conf
--------------------------------------------------------------------------
#
# LDAP Defaults
#

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

#BASE   dc=example,dc=com
#URI    ldap://ldap.example.com ldap://ldap-master.example.com:666
BASE    dc=home-pt,dc=net
URI     ldaps://ds1.home-pt.net
TLS_CACERTDIR   /etc/ldap/ssl
TLS_REQCERT     allow

#SIZELIMIT      12
#TIMELIMIT      15
#DEREF          never

Is there any good soul to give me a hand and point out what's wrong?

Many thanks in advance.

Best regards to all,

Jose Oliveira

---

