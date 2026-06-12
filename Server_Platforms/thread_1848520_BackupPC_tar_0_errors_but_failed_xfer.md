---
title: "BackupPC tar 0 errors but failed xfer"
date: 2011-09-22
forum: Server Platforms
---

### Post by jklaverstijn on 2011-09-22
Hi,

I am puzzled by the fact that the backup of the local server /etc directorey started to fail. What used to work suddenly and without knowingly having changed anything (I know: famous last words).

The log shows no indication of actual errors, but the transfer reportedly failed. Th elog contains some Dutch. It translates into "number of bytes written". The messages repeats every day and the number of bytes is always exactly the same.


tarExtract: Done: 0 errors, 3962 filesExist, 89191515 sizeExist, 21968608 sizeExistComp, 3964 filesTotal, 89469367 sizeTotal
Got fatal error during xfer (Totaal aantal geschreven bytes: 92538880 (89MiB, 2,6MiB/s))
Backup aborted (Totaal aantal geschreven bytes: 92538880 (89MiB, 2,6MiB/s))
Saving this as a partial backup

The backup command is

/usr/bin/sudo /bin/gtar -c -v -f - -C /etc --totals .

I hope someone can shed sone light on this.

Regards Jan

---

