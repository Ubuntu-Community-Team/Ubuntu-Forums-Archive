---
title: "How to search for vulnerable keys in 6.06 LTS"
date: 2008-05-15
forum: Security
---

### Post by lean on 2008-05-15
Hi, 
how do I search for broken ssh keys in 6.06LTS?

I know it is not vulnerable default, but users could have uploaded authorized_keys that are vulnerable.

The perl script mentioned on some sites doesn't work on 6.06, so if anybody have it working, give a hint ;)

---

### Post by Oldsoldier2003 on 2008-05-15
> **lean said:**
> Hi, 
how do I search for broken ssh keys in 6.06LTS?

I know it is not vulnerable default, but users could have uploaded authorized_keys that are vulnerable.

The perl script mentioned on some sites doesn't work on 6.06, so if anybody have it working, give a hint ;)

ssh-vulnkey -a doesn't work?

---

### Post by lean on 2008-05-16
> **Oldsoldier2003 said:**
> ssh-vulnkey -a doesn't work?

Since ssh is not vulnerable in 6.06, I don't think it is packaged.

Which repository/package/version is this program in?

---

### Post by masmad on 2008-05-16
I guess you could search for the keys yourself, copy them to a machine that has ssh-vulnkey and scan them there.

Another question is whether ssh-vulnkey and the other tools should be available to dapper as well.

---

### Post by mannheim on 2008-05-16
There is an alternative tool, dowkd.pl, the "Debian/OpenSSL weak key detector" which you can find [here]("http://security.debian.org/project/extra/dowkd/"). Running, for example,
```
sudo perl dowkd.pl user
```
will look at all keys for all users in the locations

```

~/.ssh/authorized_keys
~/.ssh/authorized_keys2
~/.ssh/id_rsa.pub
~/.ssh/id_dsa.pub

```

and (I think) compares them against a blacklist of keys stored in the perl script. In more detail:
```

usage: dowkd.pl [OPTIONS...] COMMAND [ARGUMENTS...]

COMMAND is one of:

  file: examine files on the command line for weak keys
  host: examine the specified hosts for weak SSH keys
  user: examine user SSH keys for weakness; examine all users if no
        users are given
  help: show this help screen

OPTIONS is one pf:

  -c FILE: set the database cache file name (default: dowkd.db)

dowkd currently handles OpenSSH host and user keys and OpenVPN shared
secrets, as long as they use default key lengths and have been created
on a little-endian architecture (such as i386 or amd64).  Note that
the blacklist by dowkd may be incomplete; it is only intended as a
quick check.

```

I don't know how the blacklist used in this perl script compares with the one that now ships with ubuntu's packages.

---

### Post by Oldsoldier2003 on 2008-05-16
> **mannheim said:**
> There is an alternative tool, dowkd.pl, the "Debian/OpenSSL weak key detector" which you can find [here]("http://security.debian.org/project/extra/dowkd/"). Running, for example,
```
sudo perl dowkd.pl user
```
will look at all keys for all users in the locations

```

~/.ssh/authorized_keys
~/.ssh/authorized_keys2
~/.ssh/id_rsa.pub
~/.ssh/id_dsa.pub

```

and (I think) compares them against a blacklist of keys stored in the perl script. In more detail:
```

usage: dowkd.pl [OPTIONS...] COMMAND [ARGUMENTS...]

COMMAND is one of:

  file: examine files on the command line for weak keys
  host: examine the specified hosts for weak SSH keys
  user: examine user SSH keys for weakness; examine all users if no
        users are given
  help: show this help screen

OPTIONS is one pf:

  -c FILE: set the database cache file name (default: dowkd.db)

dowkd currently handles OpenSSH host and user keys and OpenVPN shared
secrets, as long as they use default key lengths and have been created
on a little-endian architecture (such as i386 or amd64).  Note that
the blacklist by dowkd may be incomplete; it is only intended as a
quick check.

```

I don't know how the blacklist used in this perl script compares with the one that now ships with ubuntu's packages.

I'm not sure but ssh-vulnkey also ships with debian so I'm guessing it will work

---

### Post by mannheim on 2008-05-16
> **Oldsoldier2003 said:**
> I'm not sure but ssh-vulnkey also ships with debian so I'm guessing it will work

Yes, I think so too. But it is a compiled binary program that is not (yet?) packaged for Ubuntu 6.06. So the ready-to-run perl script seems more convenient, if the two tools are indeed equivalent.

---

### Post by masmad on 2008-05-20
[http://www.ubuntu.com/usn/usn-612-7](http://www.ubuntu.com/usn/usn-612-7)

ssh-vulnkey etc are available for 6.06 as well.

---

