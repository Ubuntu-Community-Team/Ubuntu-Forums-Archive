---
title: "Samba smbldap-tools cannot find /usr/bin/netx"
date: 2012-05-27
forum: Server Platforms
---

### Post by natomb on 2012-05-27
Hello,

to administer samba accounts held in ldap I intend to use the smbldap-tools. Yet, whichever command I execute I get the following output (german text translated into english).

```

Use of qw(...) as parentheses is deprecated at /usr/share/perl5/smbldap_tools.pm line 1423, <DATA> line 522.
Can't exec "/usr/bin/netx": File not found at /usr/share/perl5/smbldap_tools.pm line 245.
Failed to get SID from Samba net command at /usr/share/perl5/smbldap_tools.pm line 249.
Compilation failed in require at /usr/sbin/smbldap-useradd line 29.
BEGIN failed--compilation aborted at /usr/sbin/smbldap-useradd line 29.

```

As this behavior is "out of the box", I assume the package is broken. The command /usr/bin/net is available (and would return the SID of the local machine). In google were hints to ignore a specific perl warning (I assume it is the first line). For the 'netx' issue I could find further assumptions about a bug in the tool, e.g. [https://gna.org/support/?2901](https://gna.org/support/?2901) .


Please note that this problem is - I assume - not connected to my samba/ldap integration problem described here: [http://ubuntuforums.org/showthread.php?t=1986841](http://ubuntuforums.org/showthread.php?t=1986841)


Thank you for your support
  Bjoern

---

### Post by natomb on 2012-05-29
Hello,


fixed the problem in the following way:

change smblap_tools.pm line 245 to point to /usr/bin/net .

---

