---
title: "Problem running ssl-audit"
date: 2009-10-15
forum: Security
---

### Post by tribaldata on 2009-10-15
Hi guys, 

I'm trying to run ssl-audit on my server and i keep getting errors which i believe are related to python global variables.

If anyone could help decypher the output of that command ```
ssl-audit -d blacklist.db remote:sitetocheck
```

This is my output from the command above,
```
ssl-audit -d blacklist.db remote:domain.com
/usr/local/lib/python2.6/dist-packages/ssl_audit-0.2devdev_r10-py2.6.egg/sslaudit/ssl.py:8: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
/usr/local/lib/python2.6/dist-packages/ssl_audit-0.2devdev_r10-py2.6.egg/sslaudit/openvpn.py:6: DeprecationWarning: the md5 module is deprecated; use hashlib instead
Traceback (most recent call last):
  File "/usr/local/bin/ssl-audit", line 5, in <module>
    pkg_resources.run_script('ssl-audit==0.2devdev-r10', 'ssl-audit')
  File "/usr/local/lib/python2.6/dist-packages/setuptools-0.6c9-py2.6.egg/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/local/lib/python2.6/dist-packages/setuptools-0.6c9-py2.6.egg/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/local/lib/python2.6/dist-packages/ssl_audit-0.2devdev_r10-py2.6.egg/EGG-INFO/scripts/ssl-audit", line 66, in <module>

  File "build/bdist.linux-i686/egg/sslaudit/db.py", line 86, in open
NameError: global name 'os' is not defined

```

I tried to search high and low for that db.py file to add an import os in it but for the life of me i cannot find that file.

Even after updatedb running i cannot locate this file so anyone with any idea i'm willing to try :)

Thanks

---

### Post by tribaldata on 2009-10-29
One week bump... Anyone ?

---

