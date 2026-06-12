---
title: "dovecot sieve Filter Add header problem"
date: 2014-02-04
forum: Server Platforms
---

### Post by stefan-buehler-e on 2014-02-04
Hi all

I want to add a new header by mailfiltering with sieve on my ubuntu (sieve, dovecot, postfix) mailserver.
I've add following:
```
if not header :contains "X-Sieve-Filtered"
                ["yes"]
        {
                addheader "X-Sieve-Filtered" "yes";
                        }
```

May i receive following error:
```
sieve: info: started log at Feb 04 19:53:36.
main script: line 5: error: unknown command 'addheader' (only reported once at first occurence).
main script: error: validation failed.
```

How could i fix it?

Thx
Stefan

---

