---
title: "invalid keytab using mod-auth-kerb with Active Directory"
date: 2007-06-05
forum: Server Platforms
---

### Post by schauera on 2007-06-05
To host subversion, I've planed to install apache on ubuntu and allow the webserver to authenticate users against our existing Active Directory.

Therefore I downloaded the latest stable version of ubuntu server (7.04) and did an clean new install without any preconfiguration (no DNS/LAMP) and installed the apache2, subversion, krb5-user, libpam-krb5 and ssh packages along with libapache2-mod-auth-kerb and libapache2-mod-svn.
After configuring Kerberos (starting with [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto))
Everything looks very good and I became enthused about the ease of installatoin and configuration in ubuntu, but when I try to configure apache, I get the following error in error.log:
> gss_acquire_cred() failed: Miscellaneous failure (No principal in keytab matches desired name)

After searching formums and maling list archives for days I still don't understand completely, how the keytab should work. I will try to list all relevant information and hope someome can help me fixing the mentioned error.

I've already listed the installed packages above (apache reports: "Apache/2.2.3 (Ubuntu) mod_auth_kerb/5.3 DAV/2 SVN/1.4.3 Server at nike.sc.local Port 80"), I want to authenticate against Active Directory with 2 domain controllers (Domain functional level: Windows Server 2003, Forest functional level: 2000) using only the first DC at the moment. My domain is sc.local, so the realm is SC.LOCAL - I give the original names to avoid burking the failure; the new server is named "nike"

My /etc/krb5.conf look like this:
```

[logging]
default = FILE:/var/log/krb5lib.log

[libdefaults]
        default_realm = SC.LOCAL
        default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
        default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
        options = tgt_verify=no
[realms]
SC.LOCAL = {
                kdc = lizard.sc.local
                admin_server = lizard.sc.local
                default_domain = sc.local
        }

[domain_realm]
        sc.local = SC.LOCAL
        .sc.local = SC.LOACAL

```

kinit seems to work:
```
# kinit andreas@SC.LOCAL
# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: andreas@SC.LOCAL

Valid starting     Expires            Service principal
06/05/07 11:13:40  06/05/07 21:13:47  krbtgt/SC.LOCAL@SC.LOCAL
        renew until 06/06/07 11:13:40


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached

```

After installing apache I could access the defautl page without problems. My changed apache config (/etc/apache2/sites-enabled/000-default) to enable kerberos authentication looks as this (no Subversion at the moment):

```

        <Directory /var/www/>
                AuthType Kerberos
                AuthName "Kerberos login"
                Krb5Keytab /etc/HTTP3.keytab
                KrbAuthRealms SC.LOCAL
                KrbMethodNegotiate on
                KrbMethodK5Passwd off
                require valid-user
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

I created a user in Active Directory called "http/nike.sc.local", with logon-name nike.sc.local
the keytab file was generatet on the KDC using:
```

ktpass -princ HTTP/nike.sc.local@SC.LOCAL -pass mypassword -mapuser "http/nike.sc.local" -out HTTP3.keytab

```

At first I tried the logon-name but while seaching for a solution I found a post sugesting the Displayname.
Verifying this configuration using kinit with the password of the nike.sc.local user looks good
```

# kinit HTTP/nike.sc.local@SC.LOCAL
# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: HTTP/nike.sc.local@SC.LOCAL

Valid starting     Expires            Service principal
06/05/07 11:23:51  06/05/07 21:23:54  krbtgt/SC.LOCAL@SC.LOCAL
        renew until 06/06/07 11:23:51


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached

```

But when I try to access [http://nike.sc.local](http://nike.sc.local) the Client (IE7 / Opera on WinXP SP2, with Basic Auth and Negotiation) gets an Internal Serevr error andn the apache error log lists the mentioned entry:
> gss_acquire_cred() failed: Miscellaneous failure (No principal in keytab matches desired name)

All servers use the same DNS-Server and can (reverse-)lookup each other. The eventlogs on server and client gives no hints. Running klist on the client includes an entry for the server:
```

Server: HTTP/nike.sc.local@SC.LOCAL
      KerbTicket Encryption Type: Kerberos DES-CBC-MD5
      End Time: 6/5/2007 19:12:47
      Renew Time: 6/12/2007 9:12:47

```

Have I missed something? What else can I check? How to check the "desired name"?

Any help would be greatly appreciated. If I have choosen the wrong forum feel free to relocate or merge my post if I've missed an other.

Have a nice day
Andreas

---

### Post by ipguy on 2008-06-30
hey, did you ever get this to work, I'm having the same issue...


> **schauera said:**
> To host subversion, I've planed to install apache on ubuntu and allow the webserver to authenticate users against our existing Active Directory.

Therefore I downloaded the latest stable version of ubuntu server (7.04) and did an clean new install without any preconfiguration (no DNS/LAMP) and installed the apache2, subversion, krb5-user, libpam-krb5 and ssh packages along with libapache2-mod-auth-kerb and libapache2-mod-svn.
After configuring Kerberos (starting with [https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto))
Everything looks very good and I became enthused about the ease of installatoin and configuration in ubuntu, but when I try to configure apache, I get the following error in error.log:


After searching formums and maling list archives for days I still don't understand completely, how the keytab should work. I will try to list all relevant information and hope someome can help me fixing the mentioned error.

I've already listed the installed packages above (apache reports: "Apache/2.2.3 (Ubuntu) mod_auth_kerb/5.3 DAV/2 SVN/1.4.3 Server at nike.sc.local Port 80"), I want to authenticate against Active Directory with 2 domain controllers (Domain functional level: Windows Server 2003, Forest functional level: 2000) using only the first DC at the moment. My domain is sc.local, so the realm is SC.LOCAL - I give the original names to avoid burking the failure; the new server is named "nike"

My /etc/krb5.conf look like this:
```

[logging]
default = FILE:/var/log/krb5lib.log

[libdefaults]
        default_realm = SC.LOCAL
        default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
        default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
        options = tgt_verify=no
[realms]
SC.LOCAL = {
                kdc = lizard.sc.local
                admin_server = lizard.sc.local
                default_domain = sc.local
        }

[domain_realm]
        sc.local = SC.LOCAL
        .sc.local = SC.LOACAL

```

kinit seems to work:
```
# kinit andreas@SC.LOCAL
# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: andreas@SC.LOCAL

Valid starting     Expires            Service principal
06/05/07 11:13:40  06/05/07 21:13:47  krbtgt/SC.LOCAL@SC.LOCAL
        renew until 06/06/07 11:13:40


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached

```

After installing apache I could access the defautl page without problems. My changed apache config (/etc/apache2/sites-enabled/000-default) to enable kerberos authentication looks as this (no Subversion at the moment):

```

        <Directory /var/www/>
                AuthType Kerberos
                AuthName "Kerberos login"
                Krb5Keytab /etc/HTTP3.keytab
                KrbAuthRealms SC.LOCAL
                KrbMethodNegotiate on
                KrbMethodK5Passwd off
                require valid-user
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

I created a user in Active Directory called "http/nike.sc.local", with logon-name nike.sc.local
the keytab file was generatet on the KDC using:
```

ktpass -princ HTTP/nike.sc.local@SC.LOCAL -pass mypassword -mapuser "http/nike.sc.local" -out HTTP3.keytab

```

At first I tried the logon-name but while seaching for a solution I found a post sugesting the Displayname.
Verifying this configuration using kinit with the password of the nike.sc.local user looks good
```

# kinit HTTP/nike.sc.local@SC.LOCAL
# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: HTTP/nike.sc.local@SC.LOCAL

Valid starting     Expires            Service principal
06/05/07 11:23:51  06/05/07 21:23:54  krbtgt/SC.LOCAL@SC.LOCAL
        renew until 06/06/07 11:23:51


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached

```

But when I try to access [http://nike.sc.local](http://nike.sc.local) the Client (IE7 / Opera on WinXP SP2, with Basic Auth and Negotiation) gets an Internal Serevr error andn the apache error log lists the mentioned entry:


All servers use the same DNS-Server and can (reverse-)lookup each other. The eventlogs on server and client gives no hints. Running klist on the client includes an entry for the server:
```

Server: HTTP/nike.sc.local@SC.LOCAL
      KerbTicket Encryption Type: Kerberos DES-CBC-MD5
      End Time: 6/5/2007 19:12:47
      Renew Time: 6/12/2007 9:12:47

```

Have I missed something? What else can I check? How to check the "desired name"?

Any help would be greatly appreciated. If I have choosen the wrong forum feel free to relocate or merge my post if I've missed an other.

Have a nice day
Andreas

---

