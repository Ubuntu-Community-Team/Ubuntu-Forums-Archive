---
title: "LDAP getent shows correct groups, id does not"
date: 2012-10-25
forum: Server Platforms
---

### Post by sandyd on 2012-10-25
What I would like to do is to add a LDAP group to /etc/sudoers, so that all users in the group can get the ability to run sudo.

From what I know, LDAP groups should be honored as normal unix groups, so I added the group to /etc/sudoers.

I have already tried %ldapgroupname ALL=(ALL) ALL, which did not work.

I then ran id on the user - for some reason, all the secondary groups for the user are missing.

I can view them, and show that the group contains the user using
```

getent group
```
but ```

id
``` does not show the group - which means that it did not propagate to linux.

Any ideas?

I have also read [http://serverfault.com/questions/422422/libpam-ldapd-not-looking-for-secondary-groups](http://serverfault.com/questions/422422/libpam-ldapd-not-looking-for-secondary-groups) , which allowed me to get getent group working.

---

### Post by anonymouschief on 2012-10-25
Does this help?

[http://manpages.ubuntu.com/manpages/karmic/man5/sudoers.ldap.5.html](http://manpages.ubuntu.com/manpages/karmic/man5/sudoers.ldap.5.html)

---

### Post by sandyd on 2012-10-25
> **anonymouschief said:**
> Does this help?

[http://manpages.ubuntu.com/manpages/karmic/man5/sudoers.ldap.5.html](http://manpages.ubuntu.com/manpages/karmic/man5/sudoers.ldap.5.html)

not really - that only shows how I can put the sudo permissions into LDAP. 

I have figured out my main problem however, and updated the first post

---

### Post by luvshines on 2012-10-26
The network capture shows that for basic setup, the filter used for group lookups is of the form```

Filter: (&(objectclass=posixGroup)(|(memberUid=<username>)(uniqueMember=cn=<username>,<group-base>)))
```

Of course this will change depending upon your config file(can be any of these depending which mechanism you chose - ldap.conf; nslcd.conf; sssd.conf)

Maybe you can try the above filter to do ldapsearch and see if it returns the groups. OR, capture network trace of your own and see what is happening over the wire

---

### Post by sandyd on 2012-10-26
ah, Ive figured it out - was a typo on my end.

passwd != passwrd

---

