---
title: "sssd-ssh.socket failed"
date: 2020-09-17
forum: Ubuntu Development Version
---

### Post by VMC on 2020-09-17
I only see this if I remove quiet splash.
```
Job sssd-ssh.socket/start failed with result 'dependency'.Job sssd-pam.socket/start failed with result 'dependency'.
Job sssd-pam-priv.socket/start failed with result 'dependency'.
Job sssd-nss.socket/start failed with result 'dependency'.
Job sssd-sudo.socket/start failed with result 'dependency'.
Job sssd-autofs.socket/start failed with result 'dependency'.
Job sssd-pac.socket/start failed with result 'dependency'.
Job sssd-ssh.socket/start failed with result 'dependency'.
Job sssd-pam.socket/start failed with result 'dependency'.
Job sssd-pam-priv.socket/start failed with result 'dependency'.
Job sssd-nss.socket/start failed with result 'dependency'.
Job sssd-sudo.socket/start failed with result 'dependency'.
Job sssd-autofs.socket/start failed with result 'dependency'.
Job sssd-pac.socket/start failed with result 'dependency'.
Job sssd-ssh.socket/start failed with result 'dependency'.
Job sssd-pam.socket/start failed with result 'dependency'.
Job sssd-pam-priv.socket/start failed with result 'dependency'.
Job sssd-nss.socket/start failed with result 'dependency'.
Job sssd-sudo.socket/start failed with result 'dependency'.
Job sssd-autofs.socket/start failed with result 'dependency'.
Job sssd-pac.socket/start failed with result 'dependency'.
Job sssd-ssh.socket/start failed with result 'dependency'.
Job sssd-pam.socket/start failed with result 'dependency'.
Job sssd-pam-priv.socket/start failed with result 'dependency'.
Job sssd-nss.socket/start failed with result 'dependency'.
Job sssd-sudo.socket/start failed with result 'dependency'.
Job sssd-autofs.socket/start failed with result 'dependency'.
Job sssd-pac.socket/start failed with result 'dependency'.
```

This also is related
```
&#9679; sssd-nss.socket - SSSD NSS Service responder socket     Loaded: loaded (/lib/systemd/system/sssd-nss.socket; enabled; vendor preset: enabled)
     Active: inactive (dead)
   Triggers: &#9679; sssd-nss.service
       Docs: man:sssd.conf(5)
     Listen: /var/lib/sss/pipes/nss (Stream)


Dependency failed for SSSD NSS Service responder socket.
sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Dependency failed for SSSD NSS Service responder socket.
sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Dependency failed for SSSD NSS Service responder socket.
sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Dependency failed for SSSD NSS Service responder socket.
sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
Dependency failed for SSSD NSS Service responder socket.
sssd-nss.socket: Job sssd-nss.socket/start failed with result 'dependency'.
```

There are several bug reports, but differ somewhat.

edit: I found that sssd is enabled only for Ubuntu, not Kubuntu, Lubuntu. I don't remember it being enabled before at all:
```
sssd-autofs.socket                 enabled enabled
sssd-nss.socket                    enabled enabled      
sssd-pac.socket                    enabled enabled      
sssd-pam-priv.socket               enabled enabled      
sssd-pam.socket                    enabled enabled      
sssd-ssh.socket                    enabled enabled      
sssd-sudo.socket                   enabled enabled
```

edit2:
I read this, and don't think 'sssd' should be enabled for desktop, but for server:
> [h=1]SSSD[/h][COLOR=#111111][FONT=Ubuntu]SSSD stands for System Security Services Daemon and it&#8217;s actually a collection of daemons that handle authentication, authorization, and user and group information from a variety of network sources. At its core it has support for:[/FONT][/COLOR]

[LIST]
[*]Active Directory
[*]LDAP
[*]Kerberos
[/LIST]

---

### Post by P-I H on 2020-09-17
I get this error too.
I think the sssd client isn't installed in Ubuntu.
There is some info about sssd on this web page
[https://www.thegeekdiary.com/understanding-system-security-services-daemon-sssd/](https://www.thegeekdiary.com/understanding-system-security-services-daemon-sssd/)

---

