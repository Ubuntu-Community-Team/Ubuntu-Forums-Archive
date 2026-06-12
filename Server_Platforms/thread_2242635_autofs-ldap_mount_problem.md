---
title: "autofs-ldap mount problem"
date: 2014-09-03
forum: Server Platforms
---

### Post by richard51 on 2014-09-03
I recently decided to move my mounts over to **ldap**. When using **autofs-ldap** I noticed strange mounting problems:

[LIST=1]
[*]In Ubuntu 14.04, it seems that **autofs** will *still* not start at boot. 
[*]When **ldap** users log-in, they start in */home* and not */home/<user name>*, even-though their home folder is mounted. 
[/LIST]
Below is an *edited* version of my *automount.ldif* file I created for the mounts, I think it's right... It should mount */home/<user name>* (per user) and there&#8217;s a direct mount called */Share*. It does mount */Share* and* /home/** _with all users homes visible_ (*not what I wanted*), but the main problem is **No2**. I have tried removing --ghost, but then nothing works.

```
dn: ou=admin,dc=example,dc=com
ou: admin
objectClass: top
objectClass: organizationalUnit

dn: ou=automount,ou=admin,dc=example,dc=com
ou: automount
objectClass: top
objectClass: organizationalUnit

dn: ou=auto.master,ou=automount,ou=admin,dc=example,dc=com
ou: auto.master
objectClass: top
objectClass: automountMap

dn: cn=/home,ou=auto.master,ou=automount,ou=admin,dc=example,dc=com
cn: /home
objectClass: top
objectClass: automount
automountInformation: ldap:ou=auto.home,ou=automount,ou=admin,dc=example,dc=com --timeout=60 --ghost

dn: ou=auto.home,ou=automount,ou=admin,dc=example,dc=com
ou: auto.home
objectClass: top
objectClass: automountMap

dn: cn=/,ou=auto.home,ou=automount,ou=admin,dc=example,dc=com
cn: /
objectClass: top
objectClass: automount
automountInformation: -fstype=nfs4,rw,hard,intr,nofsc,sec=krb5 storage.example.com:/home/&

dn: cn=/-,ou=auto.master,ou=automount,ou=admin,dc=example,dc=com
cn: /-
objectClass: top
objectClass: automount
automountInformation: ldap:ou=auto.direct,ou=automount,ou=admin,dc=example,dc=com --timeout=60 --ghost

dn: ou=auto.direct,ou=automount,ou=admin,dc=example,dc=com
ou: auto.direct
objectClass: top
objectClass: automountMap

dn: cn=/shared,ou=auto.direct,ou=automount,ou=admin,dc=example,dc=com
cn: /shared
objectClass: top
objectClass: automount
automountInformation: -fstype=nfs4,rw,hard,intr,nofsc,sec=krb5 storage.example.com:/shared
```

---

### Post by richard51 on 2014-09-03
Just an update: The mounted directories were just leftover from my previous setup. The ldap mounts don't work at all...

**syslog** reports the following after a **autofs** restart:
```
Sep  3 13:19:12 primary automount[1913]: autofs stopped
Sep  3 13:19:13 primary automount[1934]: Starting automounter version 5.0.7, master map ou=auto.master,ou=automount,ou=admin,dc=example,dc=com
Sep  3 13:19:13 primary automount[1934]: using kernel protocol version 5.02
Sep  3 13:19:13 primary automount[1934]: no mounts in table
```

---

### Post by richard51 on 2014-09-03
I managed to get **auto-ldap** to mount my directories by editing the **/etc/autofs_ldap_auth.conf** file, and by adding a **kerberos** principal for **autofsclient/**. My server uses **kerberos** for authentication and according to [http://linux.die.net/man/5/autofs_ldap_auth.conf](http://linux.die.net/man/5/autofs_ldap_auth.conf) it will use "*autofsclient/<fqdn>@<REALM>*" as the default principal name.

**/etc/autofs_ldap_auth.conf edit:**
```
<autofs_ldap_sasl_conf
        usetls="yes"
        tlsrequired="yes"
        authrequired="yes"
        authtype="GSSAPI"
/>
```

**Added principal to client computers (THIS IS REQUIRED):**
```
$ sudo kadmin -p administrator/admin -q "addprinc -randkey autofsclient/$(hostname -f)"
$ sudo kadmin -p administrator/admin -q "ktadd autofsclient/$(hostname -f)"
```

So it mounts ok, but it still doesn't autostart at boot or at log-in (*trys to mount before kerberos or ldap has started*), and I have to start it manually on the clients  !!!

**Additional:**  I was thinking about adding a **cron job** to restart the **autofs** service at boot on the client machines? Is there a better way?

---

### Post by mamnmamn on 2014-09-04
Hi,

I have a very similar problem although I won't add all the details here as I don't want to hijack your post. I have an openldap server with automounts. I have also recently added automounting homes. The automounts always worked previous to Ubuntu 14.04 I believe. The whole setup works well with RHEL.

On 14.04, I have to start/restart autofs as root before it could mount ldap automounts. I can however, automount nfs shares via the /net function if that is uncommented in /etc/auto.master. I set autofs to start in verbose mode in /etc/init/autofs.conf and can see that it is starting after NetworkManager but before eth0 has an IP address from the DHCP server. The order things are starting/being triggered is;

NetworkManager
SSSD
AutoFS
AutoFS mounted indirect /net
Kernel reports eth0: link ready
NM starts DHCP
eth0 gets IP address

If I restart autofs then all works fine accept GUI logins hang for ldap clients. I think this is an unrelated PAM issue. Can you confirm if this is the same issue as you have else I will create a new post?

Thanks

---

### Post by richard51 on 2014-09-04
> **mamnmamn said:**
> Hi,

I have a very similar problem although I won't add all the details here as I don't want to hijack your post. I have an openldap server with automounts. I have also recently added automounting homes. The automounts always worked previous to Ubuntu 14.04 I believe. The whole setup works well with RHEL.

On 14.04, I have to start/restart autofs as root before it could mount ldap automounts. I can however, automount nfs shares via the /net function if that is uncommented in /etc/auto.master. I set autofs to start in verbose mode in /etc/init/autofs.conf and can see that it is starting after NetworkManager but before eth0 has an IP address from the DHCP server. The order things are starting/being triggered is;

NetworkManager
SSSD
AutoFS
AutoFS mounted indirect /net
Kernel reports eth0: link ready
NM starts DHCP
eth0 gets IP address

If I restart autofs then all works fine accept GUI logins hang for ldap clients. I think this is an unrelated PAM issue. Can you confirm if this is the same issue as you have else I will create a new post?

Thanks

Both our problems are well documented as a bug (*or issue*), with **autofs** and **ldap** mounts. Yours is more common (*starting before the interfaces are up*). I was hoping the bug would have been addressed in 14.04, guess not! I am not sure what the best workaround is, but I think I will add a **cron job** to restart the **autofs** service on reboot.

---

### Post by mamnmamn on 2014-09-04
Hi Thanks,

I have been looking for a fix and created (adapted) an upstart script to wait until eth0 has an IP (or atleast the command returns a line with "inet " in it) and then restarts autofs. It seems to work. I tested it with network unplugged on boot and then pluggin in and it worked;

> start on (runlevel [2345]
      and (starting network-interface
          or starting network-manager
          or starting networking))
stop on runlevel [!2345]



#expect fork


pre-start script
    TIMEOUT=50 #5 second timeout - eatch iteration sleeps for 1/10th of a second
    LOG_FILE=/var/log/autofs-img

    until [ $TIMEOUT -eq 0 ]; do
        if ip addr show dev eth0 | grep -e 'inet '; then
                echo "Detected inet link" >> $LOG_FILE
                ip addr show dev eth0 >> $LOG_FILE
                exit 0;
        fi
        TIMEOUT=$((TIMEOUT-1))
        sleep .1
    done

    echo "Timeout waiting for IP address" >> $LOG_FILE
    exit 1;
end script

script
    exec stop autofs && start autofs
end script

Feel free to try / improve!!

---

### Post by richard51 on 2014-09-04
I was just looking into editing the autofs.conf upstart script, since using **@reboot** in **crontab** still suffered the same fate (*started to soon*). My problem is that it starts before **ldap** and **kerberos**, so I need to really write my own script (never done an upstart one before, give me a minute...).

---

### Post by mamnmamn on 2014-09-04
Hi,

can you use 

start on started sssd

that's is you are using sssd for ldap and kerberos?

---

### Post by richard51 on 2014-09-04
Don't use sssd. But, I could make it start on another service, or even make it wait for another service or services to start. Which to choose!

The point really is... Why hasn't this been fixed yet, it is a well known (*documented*) bug.

**sssd:** I find it easier and quicker to implement single sign-on, without **sssd**. Having used it recently, I decided it was just a bit of extra work I didn't need.

---

### Post by mamnmamn on 2014-09-04
> The point really is... Why hasn't this been fixed yet, it is a well known (documented) bug.

I completely agree!

---

### Post by richard51 on 2014-09-05
Having tried various methods to fix this problem, I think editing the **/etc/rc.local** file is the most elegant. It should also fix both our problems (**mamnmamn**[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=320554")), and any future ones that may arise. Note: **rc.local** is run after every multiuser runlevel. I have only tested it for a short time with 14.04, so let me know if it works for you!

Add the line(s) in **bold** to the **/etc/rc.loca**l file.
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[B]# AutoFS Automount Hack/Fix
service autofs restart[/B]

exit 0
```

---

