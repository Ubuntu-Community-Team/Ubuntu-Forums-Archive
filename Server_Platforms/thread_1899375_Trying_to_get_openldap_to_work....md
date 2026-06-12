---
title: "Trying to get openldap to work..."
date: 2011-12-23
forum: Server Platforms
---

### Post by obatron on 2011-12-23
I thought I had this working, but it stopped...

I set up an Ubuntu 11.10 server with OpenSSH and OpenLDAP per the guide(s), community documentation, copious google searching, and forum searching..nothing suggested works, thus I presume it's something I'm overlooking being to close it working on it too long.

Everything seems to be in place on the server, "ldapsearch -H ldapi:/// -x -ZZZ" spits out the expected information, phpldapadmin works.   I even believe I have the TLS/SSL configuration set appropriately (self signed certs until I can verify that it works in general.)

When I try "ldapsearch -x -H ldaps://host.one.two.edu" on a client, I get "ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1).   I tried "-d 8" but it doesn't spit out any debug information.  The sad part, this worked at one point...

My /etc/default/slapd.conf on the server:

```

SLAPD_CONF=
SLAPD_USER="openldap"
SLAPD_GROUP="openldap"
SLAPD_PIDFILE=
SLAPD_SERVICES="ldaps://host.one.two.edu ldapi:///"
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd
SLAPD_OPTIONS=""

```

My /etc/ldap/ldap.conf on the server:

```

BASE dc=ece,dc=cornell,dc=edu
URI ldaps://host.one.two.edu/
TLS_REQCERT allow

```

My /etc/ldap/ldap.conf on the client:

```

BASE	dc=ece,dc=cornell,dc=edu
URI 	ldapi://host.one.two.edu/
TLS_REQCERT allow

```

It doesn't appear to be listening on right ports on the server (although there is nothing in the logs to indicate there is a problem.)

```

$ sudo netstat -plane | grep ":389"
$ sudo netstat -plane | grep ":636"
tcp        0      0 127.0.1.1:636           0.0.0.0:*               LISTEN      0          7386        853/slapd       
$ sudo netstat -plane | grep "slapd"
tcp        0      0 127.0.1.1:636           0.0.0.0:*               LISTEN      0          7386        853/slapd       
unix  2      [ ACC ]     STREAM     LISTENING     7387     853/slapd           /var/run/slapd/ldapi
unix  2      [ ]         DGRAM                    7383     853/slapd           
$ 

```

I'm about to give up and just use NIS, it's not that big of an environment.   I was just hoping for a more secure authentication method. 

...and before you suggest it, I can't use a commercial product.   The university is cutting back on expenses and they've determined that IT is too costly (although HR is growing expotentially, go figure.)

---

### Post by alsdkjhf23465 on 2012-02-03
hello there,
have you have any luck woth setting up your ldap authentication?

I'm in a similar situation...
[http://ubuntuforums.org/showthread.php?t=1919119]("http://ubuntuforums.org/showthread.php?t=1919119")

thank you for your time

---

