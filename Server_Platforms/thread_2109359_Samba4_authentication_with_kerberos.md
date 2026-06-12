---
title: "Samba4 authentication with kerberos"
date: 2013-01-27
forum: Server Platforms
---

### Post by fromberg100 on 2013-01-27
Hi All,

Im thrying to setup a server with Samba4 with Kerberos.  When I want to see list all shares with smbclient with samba authentication, everything works fine.  But when I try to authenticate using Kerberos, I get and error.

The command I execute is:

smbclient -L localhost -k

The error message from Samba is:

using SPNEGO
Selected protocol [8][NT LANMAN 1.0]
GSS server Update(krb5)(1) Update failed:  Miscellaneous failure (see text): Decrypt integrity check failed for checksum type hmac-sha1-96-aes256, key type aes256-cts-hmac-sha1-96
SPNEGO(gssapi_krb5) NEG_TOKEN_INIT failed: NT_STATUS_LOGON_FAILURE
SPNEGO login failed: NT_STATUS_LOGON_FAILURE


Any help will be appreciated.

Thanks and regards,
fromberg100

---

### Post by luvshines on 2013-01-28
Can you share more info please, like, what is your KDC, how are you requesting tickets (kinit, klist) etc

---

### Post by fromberg100 on 2013-01-29
HI luvshines,

thanks for your reply.

Im running Kerberos 5.  You can see my kdc.conf below:

[kdcdefaults]
    kdc_ports = 750,88

[kdc]
    enable-kerberos4 = false

[realms]
    MYDOMAIN.COM = {
        database_name = /var/lib/krb5kdc/principal
        admin_keytab = FILE:/etc/krb5kdc/Administrator.keytab
        acl_file = /etc/krb5kdc/kadm5.acl
        key_stash_file = /etc/krb5kdc/stash
        max_life = 10h 0m 0s
        max_renewable_life = 7d 0h 0m 0s
        master_key_type = des3-hmac-sha1
        supported_enctypes = supported_enctypes = aes256-cts:normal arcfour-hmac:normal des3-hmac-sha1:normal des-cbc-crc:normal des-cbc-crc:v4

        default_principal_flags = +preauth
    }

When run kinit, im asked for root's password.  Then I run klist and I get the ticket listing as follows:

Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [email]root@MYDOMAIN.COM[/email]

Valid starting    Expires           Service principal
29/01/2013 00:55  29/01/2013 07:35  krbtgt/MYDOMAIN.COM@MYDOMAIN.COM


Then I run the following command:

smbclient -L localhost -k

Then I get the error message

Thanks and regards,

---

### Post by luvshines on 2013-01-29
> **fromberg100 said:**
> HI luvshines,

Im running Kerberos 5.


Looks like MIT KDC if I am not mistaken

So, did you define 'cifs' service principals with the 'netbios name' of the CIFS server
Something like```

# Assuming 'netbios name' of your CIFS server[defined in samba registry] is 'mysambaserver'
cifs/mysambaserver@MYDOMAIN.COM
```

Also make sure that the mysambaserver resolves to IP address of the CIFS server

If you have defined the required CIFS principal, check if from client you can acquire those service tickets```
# After kinit with root
kvno cifs/mysambaserver@MYDOMAIN.COM
```

Not to forget, I am assuming that you have done the CIFS server side kerberos configs. What's the output of 'testparm -s' command ?

---

### Post by fromberg100 on 2013-01-29
Hi luvshines,

thanks for your reply.

Yes, Im running MIT Kerberos 5.

Regarding CIFS, if I run getprincs from kadmin.local, I get the following with cifs:

cifs/localhost@MYDOMAIN.COM
[email]cifs@MYDOMAIN.COM[/email]


Regarding testparm -s I get the following:

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[netlogon]"
Processing section "[sysvol]"
Processing section "[shared]"
Loaded services file OK.
Server role: ROLE_ACTIVE_DIRECTORY_DC
[global]
    workgroup = MYDOMAIN
    realm = MYDOMAIN.COM
    server role = active directory domain controller
    passdb backend = samba_dsdb
    server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, smb
    dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
    rpc_server:tcpip = no
    rpc_daemon:spoolssd = embedded
    rpc_server:spoolss = embedded
    rpc_server:winreg = embedded
    rpc_server:ntsvcs = embedded
    rpc_server:eventlog = embedded
    rpc_server:srvsvc = embedded
    rpc_server:svcctl = embedded
    rpc_server:default = external
    idmap config * : backend = tdb
    create mask = 0777
    directory mask = 0777
    map archive = No
    map readonly = no
    store dos attributes = Yes
    vfs objects = dfs_samba4, acl_xattr

[netlogon]
    path = /var/lib/samba/sysvol/mydomain.com/scripts
    read only = No

[sysvol]
    path = /var/lib/samba/sysvol
    read only = No

[shared]
    path = /shared
    read only = No


For some reason the netbios name is not output, but in my smb.conf I have under [globals]:

netbios name = PDC

Hope this info helps.  If you need anything else, please let me know.

Regards,
Fabian

---

### Post by luvshines on 2013-01-30
Did you configure CIFS server with kerberos ?
I mean, krb5.conf setting, keytab file

I think you'll also need 'kerberos method' in smb.conf```

# This is what I use
kerberos method = system keytab
```

Also, try with another service principal, with the netbios name```

# The name pdc should resolve to the IP
cifs/pdc@MYDOMAIN.COM
```

---

### Post by fromberg100 on 2013-01-31
Hi luvshines,

thanks, I have run the following commands:

ktadd host/PDC.mydomain.com

ktadd -e arcfour-hmac:normal cifs/PDC

Afther this I run: 

smbclient -k -L //PDC/ 

but I get the follwing:


GSS server Update(krb5)(1) Update failed:  Miscellaneous failure (see text): Failed to find PDC$@MYDOMAIN.COM(kvno 2) in keytab FILE:/var/lib/samba/private/secrets.keytab (arcfour-hmac-md5)

As it was not working, I was playing around with ktadd but now i get the following:

GSS server Update(krb5)(1) Update failed:  Miscellaneous failure (see text): Failed to find PDC$@MYDOMAIN.COM(kvno 8) in keytab FILE:/var/lib/samba/private/secrets.keytab (aes256-cts-hmac-sha1-96)

What is the difference between /etc/krb5.keytab and /var/lib/samba/private/secrets.keytab?

Im sorry for this, this is very difficult and complicated to make work.  Hope you can help me.

Regards,
Fabian

---

### Post by luvshines on 2013-01-31
> **fromberg100 said:**
> I have run the following commands:

ktadd host/PDC.mydomain.com  [COLOR="Red"]<-- I don't think you needed this[/COLOR]

ktadd -e arcfour-hmac:normal cifs/PDC

So you would have done, 'addprinc -randkey cifs/PDC' then 
ktadd step.

This will add the principal in the /etc/krb5.keytab file on KDC
You'll have to copy this file over to the CIFS server at /etc/krb5.keytab

Configure /etc/krb5.conf on CIFS server, as you have done on the client.

Then set that samba parameter to let samba know that look for principals in the /etc/krb5.keytab file and not in its default secrets.keytab file

Then try access from client, by first doing a kinit for a valid user then smbclient command

Make sure that the time is in sync on all the 3 entities - client, samba server and the KDC

Well, it's not that complicated, once you have all the steps in order :)

---

### Post by fromberg100 on 2013-01-31
Dear luvshines,

thanks for your help.  I really appreciate.  I will try again tonight at home.

Based on your comments, please consider the following:

- samba and kerberos are running on the same machine (PDC.mydomain.com). Would this cause any problems?

- i have tried smbclient from the same server and not from a client.  Would this cause any troubles?

- the main purpose of setting up this samba4 server is to be used on a windows network environment.

Thanks and regards,
Fabian

---

### Post by luvshines on 2013-02-01
> **fromberg100 said:**
> Dear luvshines,

thanks for your help.  I really appreciate.  I will try again tonight at home.

Based on your comments, please consider the following:

- samba and kerberos are running on the same machine (PDC.mydomain.com). Would this cause any problems?

- i have tried smbclient from the same server and not from a client.  Would this cause any troubles?


I believe none of these should cause a problem.
You'll still need that samba parameter to be set, so that samba looks up the /etc/krb5.keytab file

Then try the access

---

### Post by fromberg100 on 2013-02-03
Hi luvshines,

I just wanted to let you know the following.

It seems there was a conflict with my kerberos.  Im running Samba 4.0.0 release. I installed separately Kerberos 5.  When I do a samba domain provision, the smb.conf is generated and one configuration under [global] is the following:  server services = rpc, nbt, wrepl, ldap, cldap, drepl, kdc, ntp_signd, kcc, dnsupdate, smb  As you can see there is "kdc".  So I suspected there was a conflict.  So I stopped the service of Kerberos5 I installed separately and restarted samba.  After this the loggin was very fast and by debugging I could see the authentication was done via kerberos.  I tried this from a XP machine (client).

Im still setting up my samba server.  If I have further questions I will let you know.

Regards,
Fabian

---

### Post by HermanAB on 2013-02-03
You are not alone:
[https://www.google.com/search?hl=en&q=Decrypt+integrity+check+failed+for+checksum+type+hmac-sha1-96-aes256%2C+key+type+aes256-cts-hmac-sha1-96](https://www.google.com/search?hl=en&q=Decrypt+integrity+check+failed+for+checksum+type+hmac-sha1-96-aes256%2C+key+type+aes256-cts-hmac-sha1-96)

---

