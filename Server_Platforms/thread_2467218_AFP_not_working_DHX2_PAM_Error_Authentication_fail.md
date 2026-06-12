---
title: "AFP not working: DHX2: PAM_Error: Authentication failure"
date: 2021-09-19
forum: Server Platforms
---

### Post by stonki on 2021-09-19
Hello,

after many years I reinstalled my server to the latest Ubuntu. Everything works fine expect the AFP Server. Whenever I try to login, I am rejected.

Sep 19 17:16:01.517188 afpd[25760] {uams_dhx2_pam.c:214} (info:UAMS): PAM DHX2: PAM Success
Sep 19 17:16:02.954001 afpd[25760] {uams_dhx2_pam.c:666} (info:UAMS): DHX2: PAM_Error: Authentication failure
Sep 19 17:16:02.957045 afpd[25760] {uams_dhx2_pam.c:214} (info:UAMS): PAM DHX2: PAM Success

-V brings:
```
afpd has been compiled with support for these features:


          AFP versions:    2.2 3.0 3.1 3.2 3.3 3.4 
         CNID backends:    dbd last tdb 
      Zeroconf support:    Avahi
  TCP wrappers support:    Yes
         Quota support:    Yes
   Admin group support:    Yes
    Valid shell checks:    Yes
      cracklib support:    No
            EA support:    ad | sys
           ACL support:    Yes
          LDAP support:    Yes
         D-Bus support:    Yes
     Spotlight support:    Yes
         DTrace probes:    Yes


              afp.conf:    /etc/netatalk/afp.conf
           extmap.conf:    /etc/netatalk/extmap.conf
       state directory:    /var/lib/netatalk/
    afp_signature.conf:    /var/lib/netatalk/afp_signature.conf
      afp_voluuid.conf:    /var/lib/netatalk/afp_voluuid.conf
       UAM search path:    /usr/lib/netatalk//
  Server messages path:    /var/lib/netatalk/msg/




```

and ..

```

netatalk 3.1.12 - Netatalk AFP server service controller daemon


This program is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation; either version 2 of the License, or (at your option) any later
version. Please see the file COPYING for further information and details.


netatalk has been compiled with support for these features:


      Zeroconf support:    Avahi
     Spotlight support:    Yes


                  afpd:    /usr/sbin/afpd
            cnid_metad:    /usr/sbin/cnid_metad
       tracker manager:    /usr/bin/tracker daemon
           dbus-daemon:    /usr/bin/dbus-daemon
              afp.conf:    /etc/netatalk/afp.conf
     dbus-session.conf:    /etc/netatalk/dbus-session.conf
    netatalk lock file:    /var/lock/netatalk


```

I played with various PAM examples from the internet, but I reverted to the standard from Ubuntu 20.04


Any ideas?

---

### Post by MAFoElffen on 2021-09-19
Did you configure the authentication for your AFP server?

Example:
```
root@server:/usr/src/netatalk-3.1.11# addgroup netatalk 
root@server:/usr/src/netatalk-3.1.11# adduser testuser
root@server:/usr/src/netatalk-3.1.11# usermod -a -G netatalk testuser
```
Your have to add the group, and add users to that group... Right?

---

### Post by stonki on 2021-09-20
are you sure? I do not see any linking to this group. 

My afp.conf looks like:

```

[COLOR=#000000][FONT=Courier][COLOR=#2FB41D]**stonki@eos**[/COLOR]:[COLOR=#400BD9]**~**[/COLOR]$ cat /etc/netatalk/afp.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier];[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]; Netatalk 3.x configuration file[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier];[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][Global][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]; Global server settings[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]admin auth user = root[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]disconnect time = 3[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]sleep time = 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]log file = /var/log/netatalk.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]log level = default:debug[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]zeroconf = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]save password = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]ea = samba[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][EOS Volume][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]path = /mnt/files/[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]valid users = stonki[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]unix priv = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]file perm = 0600[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][Time Machine Volume][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]path = /mnt/files/backup/[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]time machine = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]unix priv = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]file perm = 0600[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]valid users = stonki[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#2FB41D][FONT=Courier][FONT=Verdana]
```[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]
it refers to valid user, which is my user account on the system. I did not refer to groups (e.g. @apple).[/FONT][/COLOR]

---

### Post by stonki on 2021-09-20
I added 

[COLOR=#000000][FONT=Courier]; Global server settings[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier]uam list = uams_gss.so,uams_dhx2.so,uams_dhx.so

and it works![/FONT][/COLOR]

---

