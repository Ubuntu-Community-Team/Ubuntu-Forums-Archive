---
title: "bacula plugins - version problem probably"
date: 2009-04-14
forum: Server Platforms
---

### Post by snakerdlk on 2009-04-14
Hi,
I've been setting up bacula on a local network lately and the only windows server (2k3) has microsoft exchange running.

I discovered that there is an option to backup exchange information through a plugin where you needed a DLL from the exchange installation and a line in the Fileset entry in bacula-dir.conf.

Plugin information:
[http://www.bacula.org/manuals/en/concepts/concepts/New_Features.html#SECTION005190000000000000000](http://www.bacula.org/manuals/en/concepts/concepts/New_Features.html#SECTION005190000000000000000)

```
FileSet {
  Name = "morseFset"
  Ignore FileSet Changes = yes
  Include {
    Options {
      Compression = GZIP
      signature = MD5
    }
    Plugin = "exchange:/@EXCHANGE/Microsoft Information Store/"
  }
}

```

but when I restart the bacula-director daemon I get the following error:

```
14-Apr 17:23 bacula-dir: ERROR TERMINATION at inc_conf.c:378
Config error: Keyword Plugin not permitted in this resource
            : line 29, col 11 of file /etc/bacula/directorIncludes/morse
    Plugin = "exchange:/@EXCHANGE/Microsoft Information Store/"

   ...fail!

```

The bacula-director I'm using is 2.4.2 (through $bconsole),
while the most recent version is 3.0.0.
I've already run apt-get update and apt-get upgrade but bacula was not upgraded and since the bacula apt-get installation package doesn't use the same folders as the bacula source or rpm installation I've been afraid of just installing a newer version on top of the current one.(I've noticed this while quarreling with the mysql database that bacula uses and the non-existant scripts that delete and recreate it)

Or if anyone knows if there is a way of backing the exchange information up without the use of that plugin, I appreciate it.

---

