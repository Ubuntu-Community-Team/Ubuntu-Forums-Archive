---
title: "Likewise Open - Ubuntu Desktop - Open Directory"
date: 2011-10-17
forum: Server Platforms
---

### Post by FiVAL on 2011-10-17
Hi / Hello !

Here at our company we like to mix everything together.
So our Open Directory server is Apple's OS X.
Our clients are Windows XP (most), Apple OS X (second most) and the developers work with Ubuntu.

The Windows and the OS X users work now for a couple of years perfect on the Open Directory Server without problems. Their environments are in sync and access is granted...

Because we want for new workstations to shift to Ubuntu. Ubuntu also has to get connected with the Open Directory Server. This is the part we get stucked.

I followed every manual out there about likewise-open. And try to get the connection, but with no luck. Maybe it's because I have somewhere a tiny setting fault OR connection to Apples OD is totally different then connecting to Microsoft AD. (because every manual is about MS AD).

Thx!



**--- smb.conf (on Apple OD Server) ---**

[global]
        log level = 1
        server string = SERVER.company.com
        map to guest = Bad User
        dos charset = 437
        os level = 65
        domain master = yes

        security = USER
        add machine script = /usr/bin/opendirectorypdbconfig -c create_computer_account -r %u -n /LDAPv3/127.0.0.1
        add user script = /usr/bin/opendirectorypdbconfig -c create_user_account -r %u -n /LDAPv3/127.0.0.1
        domain logons = yes
        logon drive = H:
        logon path = \\%N\profiles\%u
        auth methods = guest odsam
        netbios name = SERVER
        workgroup = NLFRL
        realm = SERVER.COMPANY.COM
        ntlm auth = yes
        lanman auth = no
        max smbd processes = 100
        use kerberos keytab = yes
        preferred master = yes
        enable disk services = yes
        enable print services = yes
        wins support = yes
        unix extensions = no
[...]


**--- Error on Ubuntu Desktop with LikeWise ---**

$ sudo domainjoin-cli join SERVER.COMPANY.COM diradmin

[...]

Error: DNS_ERROR_BAD_PACKET [code 0x0000251e]

A bad packet was received from a DNS server. Potentially the requested address does not exist.

---

### Post by vasile002 on 2011-10-17
check if server.domain.com is resolvable by the ubuntu server you are running this on

---

### Post by FiVAL on 2011-10-17
Yes it is... (with 'dig' and 'dig -x')

It is by the way a Ubuntu Desktop (and an Apple Server)

The Ubuntu Desktop gets its IP by the same DHCP Sever as all the other Windows and OS X clients... So the timeserver and the dns server setting are identical (and correct! I checked ;-)

---

### Post by samosamo on 2011-10-17
This doesn't really help you with your DNS problem, it is just a suggestion off the top of my head because I believe Open Directory is sort of a hybrid between LDAPv3 and NT4 style domain:

Did you try just using Ubuntu with LDAPv3? Why are you even bothering with the Windows domain stuff?

---

### Post by FiVAL on 2011-10-17
> **samosamo said:**
> This doesn't really help you with your DNS problem, it is just a suggestion off the top of my head because I believe Open Directory is sort of a hybrid between LDAPv3 and NT4 style domain:

Did you try just using Ubuntu with LDAPv3? Why are you even bothering with the Windows domain stuff?

I didn't even Google about LDAPv3 :oops:
But now I did, I believe it's even the way we connected the Apple clients to this Apple Open Directory Server...

So thanks very much!!!
When I'm back at work tomorrow I'll right away check it out.
(and post my findings so I can probably close this thread)

---

### Post by FiVAL on 2011-10-19
LDAPv3 is the solution... (but still ain't easy :-) )

Because it's a total different subject I'll close this thread.
Thx to you both!

(I'm now using these tutorials and logged-in successfully with a network account from the Apple Open Directory OS X Server. The problems i have at the moment are user rights (the local groups) and the home directory)

[http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2](http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2)
[http://www.linuxquestions.org/questions/linux-desktop-74/ubuntu-10-04-ldap-authentication-cant-login-to-gui-811773/](http://www.linuxquestions.org/questions/linux-desktop-74/ubuntu-10-04-ldap-authentication-cant-login-to-gui-811773/)

---

