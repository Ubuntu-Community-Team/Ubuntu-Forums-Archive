---
title: "SSSD + Active Directory authentication"
date: 2016-12-29
forum: Server Platforms
---

### Post by xenios2 on 2016-12-29
I want to login with AD users on a client with no gui. It is a Ubuntu 16.04 machine with SSSD. Active Directory server is Windows Server 2012 R2. I cannot login on console login with "aduser@srv.local" or "aduser\srv.local" neither "su aduser" works however I can kinit and successfully get a ticket and adding the machine to the domain also works. 


I followed this tutorial: [https://help.ubuntu.com/lts/serverguide/sssd-ad.html](https://help.ubuntu.com/lts/serverguide/sssd-ad.html)


I'm not sure if PAM is configured correctly or that ticket is not created at boot time or that keytabs are correct. 


The SSSD version is: 1.13.4-1ubuntu1.1
The version of libpam-modules is: 1.1.8-3.2ubuntu2


[SIZE=4]What I have did: [/SIZE]


```
    root@srv2:~# sudo kinit Administrator
    Password for Administrator@SRV.LOCAL:
    root@srv2:~# sudo klist
    Ticket cache: FILE:/tmp/krb5cc_0
    Default principal: Administrator@SRV.LOCAL
    
    Valid starting       Expires              Service principal
    12/29/2016 07:27:28  12/29/2016 17:27:28  krbtgt/SRV.LOCAL@SRV.LOCAL
            renew until 01/05/2017 07:27:27

```

Join domain:


```
    root@srv2:~# net ads join -k
    Using short domain name -- SRV
    Joined 'SRV2' to dns domain 'srv.local'

```

After configuration and join to domain I rebooted the computer I created a test user in active directory named linux. I tried su linux to change to that user but it hasn't been added in the passwd


Getent passwd:


```
    root@srv2:~# getent passwd
    root:x:0:0:root:/root:/bin/bash
    daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
    bin:x:2:2:bin:/bin:/usr/sbin/nologin
    sys:x:3:3:sys:/dev:/usr/sbin/nologin
    sync:x:4:65534:sync:/bin:/bin/sync
    games:x:5:60:games:/usr/games:/usr/sbin/nologin
    man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
    lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
    mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
    news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
    uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
    proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
    www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
    backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
    list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
    irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
    gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
    nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
    systemd-timesync:x:100:102:systemd Time Synchronization,,,:/run/systemd:/bin/false
    systemd-network:x:101:103:systemd Network Management,,,:/run/systemd/netif:/bin/false
    systemd-resolve:x:102:104:systemd Resolver,,,:/run/systemd/resolve:/bin/false
    systemd-bus-proxy:x:103:105:systemd Bus Proxy,,,:/run/systemd:/bin/false
    syslog:x:104:108::/home/syslog:/bin/false
    _apt:x:105:65534::/nonexistent:/bin/false
    lxd:x:106:65534::/var/lib/lxd/:/bin/false
    messagebus:x:107:111::/var/run/dbus:/bin/false
    uuidd:x:108:112::/run/uuidd:/bin/false
    dnsmasq:x:109:65534:dnsmasq,,,:/var/lib/misc:/bin/false
    sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin
    mark:x:1000:1000:mark,,,:/home/mark:/bin/bash
    ntp:x:111:117::/home/ntp:/bin/false
    sssd:x:112:118:SSSD system user,,,:/var/lib/sss:/bin/false

```



wbinfo query information:


```
    root@srv2:~# wbinfo -t
    checking the trust secret for domain SRV via RPC calls succeeded

```

wbinfo -u -g:

```
    root@srv2:~# wbinfo -u -g
    SRV\administrator
    SRV\guest
    SRV\krbtgt
    SRV\mark
    SRV\test1
    SRV\linux
    SRV\winrmremotewmiusers__
    SRV\domain computers
    SRV\domain controllers
    SRV\schema admins
    SRV\enterprise admins
    SRV\cert publishers
    SRV\domain admins
    SRV\domain users
    SRV\domain guests
    SRV\group policy creator owners
    SRV\ras and ias servers
    SRV\allowed rodc password replication group
    SRV\denied rodc password replication group
    SRV\read-only domain controllers
    SRV\enterprise read-only domain controllers
    SRV\cloneable domain controllers
    SRV\protected users
    SRV\dnsadmins
    SRV\dnsupdateproxy
    SRV\dhcp users
    SRV\dhcp administrators

```

ldapsearch with GSSAPI shows error with keytabs: 


```
    root@srv2:~# /usr/bin/ldapsearch -H ldap://srv.local -Y GSSAPI -N -b "dc=src,dc=local" "(&(objectClass=user)(sAMAccountName=ad
    user))"
    SASL/GSSAPI authentication started
    ldap_sasl_interactive_bind_s: Local error (-2)
            additional info: SASL(-1): generic failure: GSSAPI Error: Unspecified GSS failure.  Minor code may provide more information (No Kerberos credentials available)

```

/var/log/sssd/ldap_child.log:


```
    (Thu Dec 29 07:27:40 2016) [[sssd[ldap_child[33841]]]] [ldap_child_get_tgt_sync] (0x0010): Failed to init credentials: Preauthe
    ntication fail

```

/var/log/auth.log:


    ```
Dec 29 20:03:59 srv2 login[1344]: pam_unix(login:auth): check pass; user unknown
    Dec 29 20:03:59 srv2 login[1344]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser$Dec 29 20:04:24 srv2 sssd_be: GSSAPI client step 1
    Dec 29 20:04:24 srv2 sssd_be: GSSAPI client step 1
    Dec 29 20:04:24 srv2 sssd_be: GSSAPI client step 1
    Dec 29 20:04:24 srv2 sssd_be: GSSAPI client step 1
```


I used tcpdump to filter ldap, dns and krb5 ports. The capture can be viewed here: [http://www.filedropper.com/ldap-sssd](http://www.filedropper.com/ldap-sssd)


Errors that occurred are: 


    ```
67    0.112875    192.168.253.200    192.168.253.100    DNS    151    Standard query response 0xe2ee No such name SRV _kerberos-master._tcp.SRV.LOCAL SOA dc1.srv.local

```

I have read that the error below can safely be ignored:


    ```
31    0.094884    192.168.253.200    192.168.253.100    KRB5    231    KRB Error: KRB5KDC_ERR_PREAUTH_REQUIRED

```


Configuration files: 
==============


/etc/hosts:


```
    127.0.0.1 localhost
    192.168.253.100 srv2.srv.local srv2
    
    # The following lines are desirable for IPv6 capable hosts
    #::1     localhost ip6-localhost ip6-loopback
    #ff02::1 ip6-allnodes
    #ff02::2 ip6-allrouters

```

/etc/resolv.conf


```
    # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
    #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
    nameserver 192.168.253.200
    search srv.local

```

/etc/krb5.conf:

```
    [libdefaults]
        default_realm = SRV.LOCAL
        renew_lifetime = 7d
        ticket_lifetime = 24h
        dns_lookup_realm = true
        dns_lookup_kdc = true
    
    # The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true
        rdns = false
    
    # The following encryption type specification will be used by MIT Kerberos
    # if uncommented.  In general, the defaults in the MIT Kerberos code are
    # correct and overriding these specifications only serves to disable new
    # encryption types as they are added, creating interoperability problems.
    #
    # Thie only time when you might need to uncomment these lines and change
    # the enctypes is if you have local software that will break on ticket
    # caches containing ticket encryption types it doesn't know about (such as
    # old versions of Sun Java).
    
    #    default_tgs_enctypes = des3-hmac-sha1
    #    default_tkt_enctypes = des3-hmac-sha1
    #    permitted_enctypes = des3-hmac-sha1
    
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
        SRV.LOCAL = {
            kdc = srv.local
            admin_server = srv.local
            default_domain = srv.local
        }
        ATHENA.MIT.EDU = {
            kdc = kerberos.mit.edu:88
            kdc = kerberos-1.mit.edu:88
            kdc = kerberos-2.mit.edu:88
            admin_server = kerberos.mit.edu
            default_domain = mit.edu
        }
        MEDIA-LAB.MIT.EDU = {
            kdc = kerberos.media.mit.edu
            admin_server = kerberos.media.mit.edu
        }
        ZONE.MIT.EDU = {
            kdc = casio.mit.edu
            kdc = seiko.mit.edu
            admin_server = casio.mit.edu
        }
        MOOF.MIT.EDU = {
            kdc = three-headed-dogcow.mit.edu:88
            kdc = three-headed-dogcow-1.mit.edu:88
            admin_server = three-headed-dogcow.mit.edu
        }
        CSAIL.MIT.EDU = {
            kdc = kerberos-1.csail.mit.edu
            kdc = kerberos-2.csail.mit.edu
            admin_server = kerberos.csail.mit.edu
            default_domain = csail.mit.edu
            krb524_server = krb524.csail.mit.edu
        }
        IHTFP.ORG = {
            kdc = kerberos.ihtfp.org
            admin_server = kerberos.ihtfp.org
        }
        GNU.ORG = {
            kdc = kerberos.gnu.org
            kdc = kerberos-2.gnu.org
            kdc = kerberos-3.gnu.org
            admin_server = kerberos.gnu.org
        }
        1TS.ORG = {
            kdc = kerberos.1ts.org
            admin_server = kerberos.1ts.org
        }
        GRATUITOUS.ORG = {
            kdc = kerberos.gratuitous.org
            admin_server = kerberos.gratuitous.org
        }
        DOOMCOM.ORG = {
            kdc = kerberos.doomcom.org
            admin_server = kerberos.doomcom.org
        }
        ANDREW.CMU.EDU = {
            kdc = kerberos.andrew.cmu.edu
            kdc = kerberos2.andrew.cmu.edu
            kdc = kerberos3.andrew.cmu.edu
            admin_server = kerberos.andrew.cmu.edu
            default_domain = andrew.cmu.edu
        }
        CS.CMU.EDU = {
            kdc = kerberos.cs.cmu.edu
            kdc = kerberos-2.srv.cs.cmu.edu
            admin_server = kerberos.cs.cmu.edu
        }
        DEMENTIA.ORG = {
            kdc = kerberos.dementix.org
            kdc = kerberos2.dementix.org
            admin_server = kerberos.dementix.org
        }
        stanford.edu = {
            kdc = krb5auth1.stanford.edu
            kdc = krb5auth2.stanford.edu
            kdc = krb5auth3.stanford.edu
            master_kdc = krb5auth1.stanford.edu
            admin_server = krb5-admin.stanford.edu
            default_domain = stanford.edu
        }
            UTORONTO.CA = {
                    kdc = kerberos1.utoronto.ca
                    kdc = kerberos2.utoronto.ca
                    kdc = kerberos3.utoronto.ca
                    admin_server = kerberos1.utoronto.ca
                    default_domain = utoronto.ca
        }
    
    [domain_realm]
        .srv.local = dc1.srv.local
        srv.local = dc1.srv.local
        .mit.edu = ATHENA.MIT.EDU
        mit.edu = ATHENA.MIT.EDU
        .media.mit.edu = MEDIA-LAB.MIT.EDU
        media.mit.edu = MEDIA-LAB.MIT.EDU
        .csail.mit.edu = CSAIL.MIT.EDU
        csail.mit.edu = CSAIL.MIT.EDU
        .whoi.edu = ATHENA.MIT.EDU
        whoi.edu = ATHENA.MIT.EDU
        .stanford.edu = stanford.edu
        .slac.stanford.edu = SLAC.STANFORD.EDU
            .toronto.edu = UTORONTO.CA
            .utoronto.ca = UTORONTO.CA
    
    [login]
        krb4_convert = true
        krb4_get_tickets = false
    
    [logging]
        default = FILE:/var/log/krb5libs.log

```



permissions sssd.conf


```
    drw-------  2 root root 4096 Dec 29 08:37 . 
    drwxr-xr-x 96 root root 4096 Dec 29 08:34 ..
    -rw-------  1 root root  696 Dec 29 08:30 sssd.conf

```

/etc/sssd/sssd.conf:


```
    [sssd]
    services = nss, pam
    config_file_version = 2
    domains = SRV.LOCAL
    #default_domain_suffix = SRV.LOCAL
    
    [domain/SRV.LOCAL]
    id_provider = ad
    access_provider = ad
    
    # Use this if users are being logged in at /.
    # This example specifies /home/DOMAIN-FQDN/user as $HOME.  Use with pam_mkhomedir.so
    override_homedir = /home/%d/%u
    
    # Uncomment if the client machine hostname doesn't match the computer object on the DC.
    # ad_hostname = srv2.srv.local
    
    # Uncomment if DNS SRV resolution is not working
    # ad_server = dc1.srv.local
    
    # Uncomment if the AD domain is named differently than the Samba domain
    # ad_domain = SRV.LOCAL
    
    # Enumeration is discouraged for performance reasons.
    # enumerate = true

```

/etc/samba/smb.conf:


```
    [global]
    
    workgroup = SRV
    client signing = yes
    client use spnego = yes
    kerberos method = secrets and keytab
    realm = SRV.LOCAL
    security = ads

```

/etc/nsswitch.conf:


```
    passwd:         compat sss
    shadow:         compat
    group:          compat sss
    gshadow:        files
    hosts:          files dns
    
    bootparams:     files
    
    ethers:         files
    netmasks:       files
    networks:       files
    protocols:      files
    rpc:            files
    services:       files sss
    
    netgroup:       nis sss
    
    publickey:      files
    
    automount:      files
    aliases:        files
    sudoers:        files sss

```

/etc/pam.d/common-auth


```
        #
        # /etc/pam.d/common-auth - authentication settings common to all services
        #
        # This file is included from other service-specific PAM config files,
        # and should contain a list of the authentication modules that define
        # the central authentication scheme for use on the system
        # (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
        # traditional Unix authentication mechanisms.
        #
        # As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
        # To take advantage of this, it is recommended that you configure any
        # local modules either before or after the default block, and use
        # pam-auth-update to manage selection of other modules.  See
        # pam-auth-update(8) for details.
        
        # here are the per-package modules (the "Primary" block)
        auth    [success=2 default=ignore]      pam_unix.so nullok_secure
        auth    [success=1 default=ignore]      pam_sss.so use_first_pass
        # here's the fallback if no module succeeds
        auth    requisite                       pam_deny.so
        # prime the stack with a positive return value if there isn't one already;
        # this avoids us returning an error just because nothing sets a success code
        # since the modules above will each just jump around
        auth    required                        pam_permit.so
        # and here are more per-package modules (the "Additional" block)
        # end of pam-auth-update config

```    
/etc/pam.d/common-password
    
```
    #
    # /etc/pam.d/common-password - password-related modules common to all services
    #
    # This file is included from other service-specific PAM config files,
    # and should contain a list of modules that define the services to be
    # used to change user passwords.  The default is pam_unix.
    
    # Explanation of pam_unix options:
    #
    # The "sha512" option enables salted SHA512 passwords.  Without this option,
    # the default is Unix crypt.  Prior releases used the option "md5".
    #
    # The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
    # login.defs.
    #
    # See the pam_unix manpage for other options.
    
    # As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
    # To take advantage of this, it is recommended that you configure any
    # local modules either before or after the default block, and use
    # pam-auth-update to manage selection of other modules.  See
    # pam-auth-update(8) for details.
    
    # here are the per-package modules (the "Primary" block)
    password    requisite            pam_pwquality.so retry=3
    password    [success=2 default=ignore]    pam_unix.so obscure use_authtok try_first_pass sha512
    password    sufficient            pam_sss.so use_authtok
    # here's the fallback if no module succeeds
    password    requisite            pam_deny.so
    # prime the stack with a positive return value if there isn't one already;
    # this avoids us returning an error just because nothing sets a success code
    # since the modules above will each just jump around
    password    required            pam_permit.so
    # and here are more per-package modules (the "Additional" block)
    # end of pam-auth-update config

```

---

