---
title: "nss_initgroups_ignoreusers is recreated on each reboot"
date: 2011-02-07
forum: Server Platforms
---

### Post by apalacheno on 2011-02-07
Hey,
In */etc/ldap.conf* I'm using my own *nss_initgroups_ignoreusers* setting.

However, on each system start, Ubuntu adds its default *nss_initgroups_ignoreusers* line additionally to my own, and I have no idea where that comes from (needless to say, it's annoying!).

So when I edit */etc/ldap.con*f as follows:
```

# [...]
nss_initgroups_ignoreusers     avahi,avahi-autoipd,backup,bin,couchdb,daemon,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,news,ntp,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,sync,sys,syslog,usbmux,uucp,www-data,backup

```

After I restart the system (and that happens on *every* startup), I've suddenly got two lines:
```

# [...]
nss_initgroups_ignoreusers     avahi,avahi-autoipd,backup,bin,couchdb,daemon,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,news,ntp,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,sync,sys,syslog,usbmux,uucp,www-data,backup
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,couchdb,daemon,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,news,ntp,proxy,pulse,root,rtkit,saned,speech-dispatcher,sshd,statd,sync,sys,syslog,usbmux,uucp,www-data

```

See, the old (original one) is added below my custom line (which adds the *backup* user to the end of the line).

How can I disable this 'feature'?

Cheers,
Robert

---

### Post by apalacheno on 2011-02-13
To reply to myself (in case somebody is struggling with the same issue):

Since Gutsy a custom script (**/usr/sbin/nssldap-update-ignoreusers**) is delivered with the **libnss-ldap** package. This script is responsible for the above behavior.

To disable it, add an **exit 0** statement at the beginning of the file and you're good to go.

Cheers,
Robert

---

