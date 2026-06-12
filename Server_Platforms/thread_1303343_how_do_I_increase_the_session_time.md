---
title: "how do I increase the session time?"
date: 2009-10-28
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-10-28
I'm hosting a website using ubuntu 9.04 desktop with LAMP installed.

users log on using php.

I want to change the time that it takes for a session to expire.

how do I do that?

---

### Post by dgoosens on 2009-10-28
these are set in the [Session] section of your php.ini file

if I recall this correctly, you have to change the number of seconds in 
"session.gc_maxlifetime"

---

### Post by rhythmiccycle on 2009-11-06
i changed the 1440 to a 14400. I think this will make the session 4 hours long (14400 / 60 / 60 = 4)

can anyone confirm this?

what is a chunk of "php.ini"

```

; Define the probability that the 'garbage collection' process is started
; on every session initialization.
; The probability is calculated by using gc_probability/gc_divisor,
; e.g. 1/100 means there is a 1% chance that the GC process starts
; on each request.

; This is disabled in the Debian packages, due to the strict permissions
; on /var/lib/php5.  Instead of setting this here, see the cronjob at
; /etc/cron.d/php5, which uses the session.gc_maxlifetime setting below.
; php scripts using their own session.save_path should make sure garbage
; collection is enabled by setting session.gc_probability
;session.gc_probability = 0
session.gc_divisor     = 100

; After this number of seconds, stored data will be seen as 'garbage' and
; cleaned up by the garbage collection process.
session.gc_maxlifetime = 14400

```

---

