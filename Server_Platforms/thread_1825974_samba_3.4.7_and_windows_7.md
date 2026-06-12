---
title: "samba 3.4.7 and windows 7"
date: 2011-08-16
forum: Server Platforms
---

### Post by menglim on 2011-08-16
Hi,

1. able to join xp machines to the samba pdc
2. able to add domain users to xp machines
3. able to join win7 to the samba pdc
4. Not able to add domain users to win7 machines

also in the xp machines. even if I were able to add the domain users locally. the users still cannot login to the machine unless they have network connection to the PDC.

below is the smb.conf.

[global]
    workgroup = [domain]
    server string = [server hostname]
    client NTLMv2 auth = yes
    client lanman auth = No
    client plaintext auth = No
    log file = /var/log/samba/samba.%m
    max log size = 50
    add user script =  sudo /usr/sbin/useradd -s /bin/bash -m %u
    delete user script = sudo /usr/sbin/userdel %u
    add group script =  sudo /usr/sbin/groupadd %u
    delete group script = sudo /usr/sbin/groupdel %g
    delete user from group script = sudo /usr/sbin/deluser %u %g
    add machine script =  sudo /usr/sbin/useradd -s /bin/false -d /dev/null %u
    logon path =
    logon home =\\alugbati\%U
    logon script = %U.bat
    logon drive = M:
    domain logons = Yes
    os level = 64
    preferred master = Yes
    domain master = Yes
    encrypt passwords = yes


also did the following already on the win7 machine

HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters
  DWORD  DomainCompatibilityMode = 1
  DWORD  DNSNameResolutionRequired = 0

any help ?

---

### Post by hawk2010 on 2011-08-16
First of all you should actually ask this in a Samba forum or mailing list but i will be nice. :-)

Can you try adding 
*[I]winbind offline logon* = true 

after that do /etc/init.d/smbd reload
/etc/init.d/nmbd reload

This assumes that the user had logged in at least ones with the network connection because the credentials are cached on the client

[/I]

---

### Post by menglim on 2011-08-16
hi. 
thanks much :)

I checked the winbindd and I can't seem to make it start. is there a way to check if this is installed/configured properly.

I think samba broke when I did an update on the server for samba. I was able to make win7 join and add users before with no problem

thanks again for the help

---

### Post by menglim on 2011-08-16
tried the winbind offline logon = true and that didn't work for me

---

