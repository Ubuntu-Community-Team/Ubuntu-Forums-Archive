---
title: "Joining server 22.04 to active directory issues"
date: 2023-06-30
forum: Server Platforms
---

### Post by jonike0072 on 2023-06-30
I am having an issue trying to join to our active directory and it has to be something simple im overlooking.

```
realm join -v --user=test_admin@domain.com test.domain.com

! Couldn't get kerberos ticket for: [EMAIL="test_admin@domain.com"]test_admin@domain.com[/EMAIL]: Realm not local to KDC
adcli: couldn't connect to test.domain.com: Couldn't get kerberos ticket for: [EMAIL="test_admin@domain.com"]test_admin@domain.com[/EMAIL]: Realm not local to KDC
 ! Failed to join the domain
realm: Couldn't join realm: Failed to join the domain
```

I think the issue is because my user name is [EMAIL="test_admin@domain.com"]test_admin@domain.com[/EMAIL] and the domain is test.domain.com but im not sure.

```
realm -v discover test.domain.com
``` comes back as expected (from the docs and forums i have been looking at)

I think the issue is my krb5.conf but in not sure what to change.
```

krb5.conf
[libdefaults]
        default_realm = TEST.DOMAIN.COM

   kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true

        fcc-mit-ticketflags = true

[realms]
        TEST.DOMAIN.COM = {
                kdc = domaincontroller.test.domain.com
                admin_server = domaincontroller.test.domain.com
        }
        DOMAIN.COM = {
                kdc = domaincontroller.test.domain.com
                admin_server = domaincontroller.test.domain.com
        }
         test.domain.com = {
                kdc = domaincontroller.test.domain.com
                admin_server = domaincontroller.test.domain.com
        }
         domain.com = {
                kdc = domaincontroller.test.domain.com
                admin_server = domaincontroller.test.domain.com
        }


[domain_realm]
    .test.domain.com = TEST.DOMAIN.COM
    test.domain.com = TEST.DOMAIN.COM
    .domain.com = DOMAIN.COM
    domain.com = DOMAIN.COM
```





thanks for any help in advance.

---

### Post by MAFoElffen on 2023-07-01
Please go back to your last post and edit it. Raw output and commands should be wrapped within CODE Tags like this:

[noparse]```

Paste your 
   output 
        here

```[/noparse]

...or go to the Advanced Editor, select the output to highlight it, then select the "#" icon to wrap the selected text within CODE Tags for you.

First-- Did you follow the steps here? [https://help.ubuntu.com/community/22.xx/Active_Directory](https://help.ubuntu.com/community/22.xx/Active_Directory)

EDIT:
I've done this a few times, while testing Windows Server Insider Dev Versions and Ubuntu Dev cycle servers and desktops... I have quite a few KVM VM Guests doing this to verify the process...

---

### Post by jonike0072 on 2023-07-02
Thanks for your tip on code tags someone was nice enough to fix it it looks like and i cleaned it up a bit myself.  The link you provided was some of the same things i went through when trying this myself.  But i will re look through everything to make sure.

---

### Post by MAFoElffen on 2023-07-03
Those were the steps I used in my tests as a start... Seemed to work for me, but there is more involved to actually configure it. To explain that, I brought up one of my test cases so I could show you what the .conf files ended up as...

This is the snip in my /etc/krb5.conf
```

[realms]
# The relevant part...
    FERREIRA.LOCAL = {
        kdc = dc1.ferreira.local
        admin_server = dc1.ferreira.local
        default_domain = dc1.ferreira.local
    }

```
On your Windows Server that is the Domain Controller > in Server Manager >  Local Server > Properties 
```

Computer Name: DC1
Domain:               FERREIRA.LOCAL

```
Notice they match...

My /etc/nsswitch.conf
```

passwd:    files systemd sss
group:       files systemd sss
shadow:    files systemd sss
shadow:    files sss
gshadow:  files sss

hosts:        files mdns4_minimal [NOTFOUND=return] dns
networks:  files

protocols:  db files
sevices:     db files sss
ethers:       db files
rpc:            db files

netgroup:   nis sss
automount:

```
My /etc/sssd/sssd.conf file
```

[sssd]
domains = ferreira.local
config_file_version = 2
services = nss, pam
reconnection_retries = 4
full_name-format = %2$s

[nss]
#debug_level = 2

[pam]
#pam_verbosity = 1

[domain/ferreira.local]
#debug_level = 6
ad_server = dc1.ferreira.local
ad_domain = ferreira.local
krb5_realm = FERREIRA.LOCAL
krb5_kasswd = dc1.ferreira.local

auth_provider = krb5
#hostid_provider = ad
#access_provider = ad
id_provider = ldap

default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
realmd_tags = manages-system joined-with-adcli
fallback_homedir = /home/%u
use_fully_qualified_names = True
ldap_id_mapping = True

```
My join command is
```

sudo realm join -U mafoelffen dc1.FERREIRA.LOCAL

```
Server is Ubuntu Lunar 23.04 Server Editio, install as ZFS-O_Root, encrypted (LUKS2)

Domain controller is Windows Server 2022 Datacenter, 22H2, build 25246.1001

Like I said, during Dev cycles, one of my test cases is to make sure the Dev Cycle Ubuntu Server can join to an Win Server Insider Domain Controller. It really isn't as basic as the tutorial makes it seem. It makes assumptions that after you install sssd, ldap, and kerberos, that you correctly configure each... That you have correctly configured a Windows Domain... And in that domain, that you are a Domain Admin user, that is a member of the correct groups... My admin user is a member of Administrators, Domain Users, Enterprise Admins, Group Policy Creator Owners, and Schema Admins. It doesn't need all that, but remember that I do Dev testing on both, so I set it to to the same as equivalent root user, but with safety's.

My niche as an IT Consultant was to get dissimilar OS'es to play nicely together in the same infrastructure. So my test cases follow that perspective. As you can see from AD > Computers (attached screenshot), part of the test case is to create a Windows Desktop (whatever is the current Windows Insider build) with RMS to act as a Remote Active Directory Rights Management Service Console. ...And to verify that the remote console on that Domain can also see and connect to the Ubuntu Server from Server Management.

---

### Post by jonike0072 on 2023-07-03
So i modified my krb5.conf file again 

to just
```
[realms]
        CPK.CHPK.COM = {
                kdc = elscdc01.cpk.chpk.com
                admin_server = elscdc01.cpk.chpk.com
        }


[domain_realm]
    .cpk.chpk.com = CPK.CHPK.COM
    cpk.chpk.com = CPK.CHPK.COM



```

Tried ```
[COLOR=#000000][FONT=&amp]realm join -v --user=test_admin@cpk.domain.com test.domain.com[/FONT][/COLOR]
```  even though my user name is **@domain.com**
and got a different error. but for giggles i tries ```
[COLOR=#000000][FONT=&amp]realm join -v --user=test_admin@**TEST.DOMAIN.COM** test.domain.com[/FONT][/COLOR]
``` and it connected.

I am almost 100% positive i tired it as caps before and i thought 
```
[domain_realm]
    .cpk.chpk.com = CPK.CHPK.COM
    cpk.chpk.com = CPK.CHPK.COM
```  would allow lower case letters

---

### Post by MAFoElffen on 2023-07-03
LOL. Yes. was thinking about mentioning 'Case' in my last post as I was typing it. Windows doesn't care about case differences, but Linux does.

---

