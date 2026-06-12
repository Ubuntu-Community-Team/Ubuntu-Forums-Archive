---
title: "nscd: nss_ldap: could not search LDAP server - Server is unavailable"
date: 2007-10-10
forum: Server Platforms
---

### Post by electro93 on 2007-10-10
I am currently having an issue with my Ubuntu clients connecting to an internal OpenLDAP server.  I am edited the proper /etc/pam_ldap.conf,libnss_ldap.conf, but I get this error in the /var/log/auth.log all the time:

nscd: nss_ldap: could not search LDAP server - Server is unavailable

I also have groups that overlap with the local ubuntu groups (i.e. admin).  Is there a flaw in the way nscd is caching these uid/gid, or is it possible that I am missing one setting.

Thanks,

JB

---

### Post by electro93 on 2007-10-12
Seems like I can log in with my account, but other users that try to log in, it gives them an error that:

nscd: nss_ldap: could not search LDAP server - Server is unavailable
sshd[5484]: Invalid user testuser from 192.168.1.1
sshd[5484]: Failed none for invalid user testuser from 192.168.1.1 port 56444 ssh2
sshd[5484]: pam_ldap: error trying to bind as user "uid=testuser,ou=People,dc=example,dc=com" (Invalid credentials)
 sshd[5484]: pam_unix(ssh:auth): check pass; user unknown
sshd[5484]: pam_unix(ssh:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host.example.com


any ideas?

---

### Post by elvis on 2007-10-12
Let's start with the "server unavailable" part.

In your /etc/libnss-ldap.conf file, what is the URI of the LDAP server you want to connect to?

On the server that runs SLAPd, run the command 

netstat -plutn | grep slapd

You should see something like:

```

root@server:~# netstat -plutn | grep slapd
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN     6872/slapd          
tcp6       0      0 :::389                  :::*                    LISTEN     6872/slapd 

```

As you can see on my server, slapd (the OpenLDAP server daemon) is running, and listening on tcp port 389 on all interfaces.  This matches the URI in my libnss-ldap.conf which says to connect to this particular server via tcp port 389.

Additionally, my firewall on the server is set to allow all tcp port 389 traffic on my local subnet to pass through.

Check all these things and let me know how you go.

---

### Post by electro93 on 2007-10-15
Thanks for the help.

This is an existing openldap server environment that I am trying to integrate with.  Below are the ldap server's information you requested:

[users@server ~]$ sudo netstat -plutn | grep slapd
tcp        0      0 0.0.0.0:389                 0.0.0.0:*                   LISTEN      4647/slapd
tcp        0      0 0.0.0.0:636                 0.0.0.0:*                   LISTEN      4647/slapd
tcp        0      0 :::389                      :::*                        LISTEN      4647/slapd
tcp        0      0 :::636                      :::*                        LISTEN      4647/slapd


the URI setting in my libnss-ldap.conf file are as followed: (Please note that I switched back and forth between uri and the regular hosts)

uri ldaps://192.168.1.1 ldaps://192.168.1.2

or 

host 192.168.1.1:636 192.168.1.2:636

Please let me know if more information is needed.  Thanks!

---

### Post by elvis on 2007-10-15
You've got two URIs in your config file.  You've verified LDAP is running on both successfully?

For troubleshooting purposes, try just one at a time in your libnss-ldap.conf

Also when troubleshooting, it's a good idea to run slapd in foreground mode (ie: not as a daemon).

"slapd -d" will do that, and turn debugging on to the default level you have set (see "man slapd" for valid debug levels).  Check slapd's output to see if (a) requests are making it to the server and (b) if once making it to the server, they are valid (TLS was started, communication was verified, etc).

---

