---
title: "Ldap dont start recovery error"
date: 2007-01-13
forum: Server Platforms
---

### Post by mattiashem on 2007-01-13
Starting OpenLDAP: running BDB recovery - failed:
Automatic recovery of the OpenLDAP directory database in

        /var/lib/ldap

failed. You will need to perform a manual recovery, possibly from backup.
The failed command was db4.2_recover -eh /var/lib/ldap. Output:

db_recover: Log sequence error: page LSN 1 3397; previous LSN 1 3050915
db_recover: Recovery function for LSN 1 581 failed on forward pass
db_recover: PANIC: Invalid argument
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: PANIC: fatal region error detected; run recovery
db_recover: DB_ENV->open: DB_RUNRECOVERY: Fatal error, run database recovery

---

### Post by mattiashem on 2007-01-13
Sorry
so this is also the error a get when i start my ldap server
A havent run any recovery at all.

// matte

---

