---
title: "bind9 failed to start"
date: 2010-10-06
forum: Server Platforms
---

### Post by hemi519 on 2010-10-06
Hi All, 

when i  started bind9, it showed me this error, Can anyone help me in this, according to me i dont have a file sysklogd so i can not restart that. that is why i think iam getting error while starting bind9. How to get that file and how to get started Bind9.



This is the error iam getting while starting bind9

Oct  6 14:33:52 abc kernel: [ 2663.310104] type=1503 audit(1286355832.304:20):  operation="open" pid=1828 parent=1815 profile="/usr/sbin/named" requested_mask="r::" denied_mask="r::" fsuid=120 ouid=120 name="/var/lib/named/etc/bind/named.conf"

---

### Post by hemi519 on 2010-10-06
Now iam able to install syslogd but still iam unable to start bind9.

---

### Post by SeijiSensei on 2010-10-06
Looks like a problem with AppArmor or SELinux, two security systems that monitor programs and restrict what they can do.  If you've installed bind9 from a repository, this shouldn't be an issue.  If you installed from source, you might need to register it. 

Unfortunately, I can't help with this, but someone else probably can.  Also are you using Ubuntu?  If so, then you want to search for information on AppArmor.  RedHat/CentOS systems use SELinux.

---

### Post by hemi519 on 2010-10-07
iam using Ubuntu server edition

---

### Post by SeijiSensei on 2010-10-07
Looks like you're trying to run a chrooted server?  In /etc/default/bind9 do you have OPTIONS='-u bind -t /var/lib/named'?  

If you run 'sudo aa-status' is there a profile listed as enforced for /usr/sbin/named?  How about the profile /etc/apparmor.d/usr.sbin.named?  In my version of that file, the entries for /var/lib/bind and /var/lib/bind** are both tagged read/write like this:

```

    /var/lib/bind/ rw,
    /var/lib/bind/** rw,

```

Is that what you see as well?

My /var/lib/bind is owned by root.bind with 775 permissions?  Yours, too?

---

