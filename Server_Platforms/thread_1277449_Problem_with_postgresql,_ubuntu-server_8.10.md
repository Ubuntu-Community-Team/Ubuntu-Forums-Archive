---
title: "Problem with postgresql, ubuntu-server 8.10"
date: 2009-09-28
forum: Server Platforms
---

### Post by arch_friend on 2009-09-28
good evening, guys!

have just installed fresh ubuntu-server (also have installed postgres, during installing whole system), updated and upgraded it. But when i tried to restore one of my databases from backup, i'm getting errors, like:
pg_restore: [archiver (db)] Error from TOC entry 777; 1255 18249 FUNCTION pldbg_abort_target(integer) postgres
pg_restore: [archiver (db)] could not execute query: ERROR:  could not access file "$libdir/pldbgapi": No such file or directory
    Command was: CREATE FUNCTION pldbg_abort_target(session integer) RETURNS SETOF boolean
    AS '$libdir/pldbgapi', 'pldbg_abort_target'
.....
pg_restore: [archiver (db)] Error from TOC entry 778; 1255 18250 FUNCTION pldbg_attach_to_port(integer) postgres
pg_restore: [archiver (db)] could not execute query: ERROR:  could not access file "$libdir/pldbgapi": No such file or directory
    Command was: CREATE FUNCTION pldbg_attach_to_port(portnumber integer) RETURNS integer
    AS '$libdir/pldbgapi', 'pldbg_attach_to_port'
..........

why this sthuff happens? (on my previous system, arch linux, it worked well)

---

