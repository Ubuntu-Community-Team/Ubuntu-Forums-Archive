---
title: "Configuration hardening/questioning"
date: 2009-09-29
forum: Security
---

### Post by shad0w_crash on 2009-09-29
In /etc/ssh/sshd_config there are to settings i'd like to change

1) MACs          > Can i simply remove md5 from the list (and add, for
                   example sha512 instead of sha-1?
    are there other program's allowing md5 and can i also change this to 
    sha512?
2) This line 'PermitRootLogin no' isn't available,. does that mean ssh is
   disabled on this machine, (checked with nmap and 22 is closed but that
   could be done by my firewall and 22 is still open)

Well now i'm allready questioning i've got some more:

- how can i default pipe command to other commands? I want (if i enter rm) that automatically shred is called before remove, so the date is really removed.

- Is there a configuration hardening guide for ubuntu (not like the default: use encryption, use firewall, use virusscanner, use firefox noscript, do update and defailt things) but for real configuration things. (I've found this short list: [https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)) But i'm looking for something like this: [http://www.nsa.gov/ia/guidance/security_configuration_guides/operating_systems/linux.shtml](http://www.nsa.gov/ia/guidance/security_configuration_guides/operating_systems/linux.shtml),. only for ubuntu then and not for redhat)

---

### Post by shad0w_crash on 2009-09-30
no one?

---

### Post by cdenley on 2009-09-30
1. I don't think SHA-512 is supported, but you can give the list of supported MACs to use in the configuration file.
```

man sshd_config

```

2. If an option is not given, then the default is used. The default for "PermitRootLogin" is "yes". This doesn't matter for ubuntu, since there is no valid root password. This option has nothing to do with disabling sshd from listening for connections.
```

man sshd_config

```

---

### Post by bodhi.zazen on 2009-09-30
[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

