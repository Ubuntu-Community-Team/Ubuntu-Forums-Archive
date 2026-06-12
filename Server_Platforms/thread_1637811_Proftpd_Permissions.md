---
title: "Proftpd Permissions"
date: 2010-12-04
forum: Server Platforms
---

### Post by Jay_PC on 2010-12-04
Im having an ineresting issue with Proftpd, Fresh install when I upload my file permissions are 602...

I have Umask set to 000

my .conf here:```


ServerName                      "DebianServ"
ServerType                      standalone
DefaultServer                   on
Port                            21
MaxInstances                    30
User                            root
Group                           derp

<Directory /*>
  AllowOverwrite                on
</Directory>

```

---

