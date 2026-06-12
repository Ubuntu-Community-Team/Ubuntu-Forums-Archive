---
title: "acpid:  client connected from"
date: 2012-08-04
forum: Software
---

### Post by LolaMora on 2012-08-04
Hola a tod@s

Después de mucho tiempo sin problemas con mi Ubuntu y mejorando progresivamente, me ocurrió algo que jamás me había sucedido antes.

Utilizando el Chrome, quedó totalmente bloqueada, tampoco accedía a las consolas de texto (ctrl+alt+Fx)
Reseteo y por segunda vez se bloquea totalmente.
Nuevamente reseteo, entro al Visor de sucesos **syslog** y encuentro que en el momento del cuelgue ocurrieron estos sucesos que pego a continuación:

...
Aug  4 10:47:57 tux kernel: [   30.053525] eth0: no IPv6 routers present
Aug  4 10:47:57 tux anacron[1826]: Anacron 2.3 started on 2012-08-04
Aug  4 10:47:57 tux anacron[1826]: Normal exit (0 jobs run)
Aug  4 10:47:59 tux rtkit-daemon[1746]: Sucessfully made thread 1846 of process 1846 (n/a) owned by '1000' high priority at nice level -11.
Aug  4 10:47:59 tux rtkit-daemon[1746]: Supervising 5 threads of 2 processes of 1 users.
Aug  4 10:47:59 tux pulseaudio[1846]: pid.c: Daemon already running.
Aug  4 10:48:01 tux acpid: client connected from 1889[108:114]
Aug  4 10:48:01 tux acpid: 1 client rule loaded
Aug  4 10:48:37 tux pulseaudio[1744]: ratelimit.c: 1 events suppressed
Aug  4 10:49:01 tux AptDaemon: INFO: Initializing daemon
Aug  4 10:58:05 tux kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug  4 10:58:05 tux rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="953" x-info="http://www.rsyslog.com"] (re)start
Aug  4 10:58:05 tux rsyslogd: rsyslogd's groupid changed to 103
Aug  4 10:58:05 tux rsyslogd: rsyslogd's userid changed to 101
Aug  4 10:58:05 tux rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug  4 10:58:05 tux kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  4 10:58:05 tux kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  4 10:58:05 tux kernel: [    0.000000] Linux version 2.6.32-41-generic-pae (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) 
...

Si pongo en Google la búsqueda 
**acpid:  client connected from 1889 [108:114]**
me larga un preocupante mensaje y me sugiere que si no estoy segura, que no haga nada. 
¿Puede ser un ataque o son sucesos normales?

En fin, me entró la paranoia. :(
Maria

---

