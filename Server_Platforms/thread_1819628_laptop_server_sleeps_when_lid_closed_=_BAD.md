---
title: "laptop server sleeps when lid closed = BAD"
date: 2011-08-06
forum: Server Platforms
---

### Post by pwb1 on 2011-08-06
I have an old Dell Inspiron 7000 laptop that makes a sweet home web server (don't laugh).  One great virtue under UB6 was that I could close the lid and the display would turn off (mechanical switch) but the server would keep running.  This made a compact box I could just stick on a shelf, out of the way.

Upgrading to 10.04 LTS "improved" things so now the server sleeps when the lid closes.  Even worse, when it wakes up, it just reboots instead of resuming. The BIOS and hardware have not changed, so this must be an OS behavior.  I would like to turn this feature OFF so I can again close the lid without disrupting the server operation.

I have combed the web for a solution and have not discovered one.  It's a server, so desktop-based solutions are not helpful. Command line is a must.

TIA

---

### Post by jerrrys on 2011-08-07
don't know if this is an option on a server,but on a desktop install you could change these to false or #

/etc/default/acpi-support

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

---

### Post by SeijiSensei on 2011-08-07
A quick googling for "/proc/acpi close lid" brought up some useful ideas as well.

---

### Post by pwb1 on 2011-08-08
/etc/default/acpi-support does not exist on my system.

I will investigate the "/proc/acpi close lid" trail.

Thanks!

---

