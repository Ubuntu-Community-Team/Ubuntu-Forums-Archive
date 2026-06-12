---
title: "64bit Apache ITK"
date: 2011-04-12
forum: Server Platforms
---

### Post by polypill on 2011-04-12
Running 10.04 64bit and it appears that apache2-mpm-itk does not function properly. I ran it for a long time on 8.04 32bit without issues.

As far as I can tell its just plain not working at all and I don't have anything special in my setup.

Just an entry in each virtual host like this:
```

        <IfModule mpm_itk_module>
                AssignUserId ecmecc hosted
        </IfModule>

```

The error I get is like:
```

[Tue Apr 12 04:08:55 2011] [warn] (itkmpm: pid=25395 uid=1001, gid=1001) itk_post_perdir_config(): initgroups(ecmecc, 1001): Operation not permitted
[Tue Apr 12 04:08:55 2011] [warn] Couldn't set uid/gid/priority, closing connection.

```

The uid of 1001 isn't correct, that's the uid of a different user that has its own virtual host.

---

### Post by polypill on 2011-04-12
Some more Information, amybe it will help


```
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  itk.c
  http_core.c
  mod_so.c
```

```
Linux apache64-2 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux
```

```
Package: apache2
Status: install ok installed
Priority: optional
Section: httpd
Installed-Size: 36
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.2.14-5ubuntu8.4
```

```
Package: apache2-mpm-itk
Status: install ok installed
Priority: extra
Section: httpd
Installed-Size: 80
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: apache2
Version: 2.2.14-5ubuntu8.4
```

---

### Post by polypill on 2011-04-14
Anyone at all have any idea what the deal is with this? I have a feeling  its just plain broken on the 64bit implementation.

---

### Post by t3r0 on 2011-04-15
> **polypill said:**
> Anyone at all have any idea what the deal is with this? I have a feeling  its just plain broken on the 64bit implementation.

Hi,

Could it be some appArmor rule that is blocking this? Try stopping appArmor and then starting apache..

 -Tero

---

### Post by polypill on 2011-04-18
There's no appArmor file about Apache, so I don't think its paying attention to it.

With recent apt updates it seems to have improved, like I'm seeing processes from apache being spawned as the user as it should be and the errors in the log file have calmed down. Its now like one or two entries a day instead of 100.

---

