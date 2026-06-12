---
title: "rkhunter rules for Nexus Personal"
date: 2009-06-28
forum: Security
---

### Post by mkalen on 2009-06-28
Greetings,

After getting some rkhunter warnings about suspicious shared memory device files in /dev/shm I did some digging on my system and found the Mozilla PKCS #11 crypto device from Nexus Personal to be the culprit.

The warnings:```

Warning: Suspicious file types found in /dev:
        /dev/shm/sem.se.nx.tapi.4926.5: data
        /dev/shm/sem.se.nx.tapi.4926.4: data
        /dev/shm/sem.se.nx.tapi.4926.3: data
        /dev/shm/sem.se.nx.tapi.4926.2: data
        /dev/shm/sem.se.nx.tapi.4926.1: data
        /dev/shm/sem.GlobalCacheMutex1000: data
```

Here is a rule set to get rid of the warnings:```

sudo editor /etc/rkhunter.conf
(To first set your editor preference use:
sudo update-alternatives --config editor)

Search for "ALLOWDEVFILE" and add the following lines:

# Nexus Personal PKCS11-plugin
ALLOWDEVFILE=/dev/shm/sem.GlobalCacheMutex[0-9]*
ALLOWDEVFILE=/dev/shm/sem.se.nx.tapi.[0-9]*.[0-9]*

```

Nexus Personal is commonly used e.g. in Sweden for certificate validation by banks and various government organizations. See also: [Nexus Personal product page]("http://www.nexussafe.com/en/Products/Nexus-Personal/").

Using strings on the tokenapi shared library (installed at /usr/local/lib/personal/libtokenapi.so) you can verify the string patterns "GlobalCacheMutex" and "se.nx.tapi.%d.%d". Also, to verify that Personal creates these files you can uninstall the PKCS #11 crypto device, restart Firefox and check /dev/shm to see that the device files are gone (GlobalCacheMutex does not seem to be deleted on exit though).

---

