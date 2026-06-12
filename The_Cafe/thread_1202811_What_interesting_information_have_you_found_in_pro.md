---
title: "What interesting information have you found in /proc?"
date: 2009-07-02
forum: The Cafe
---

### Post by learningcurb on 2009-07-02
So far I've found two that are handy: /proc/acpi/thermal_zone/ contains some information that is reported by your computer's internal temperature sensors.

Also, /proc/cpuinfo displays details about your processors and their current frequency setting.  Neat eh?

---

### Post by wojox on 2009-07-02
This is a real time, memory resident file system
that tracks the processes running on your machine and the state of your
system. I wouldn't monkey around in there to much.
Are you in there thru the terminal it'll be ok.

---

### Post by learningcurb on 2009-07-02
Yeah, I am just browsing /proc via the terminal and using cat and less to look at files.  Shouldn't it be fairly safe to poke around /proc as long as you don't write anything to it?

---

### Post by wojox on 2009-07-02
yeah

---

### Post by nmccrina on 2009-07-02
> **learningcurb said:**
> /proc/cpuinfo

+1

---

### Post by FuturePilot on 2009-07-02
Try /proc/meminfo
Gives info on RAM

---

### Post by learningcurb on 2009-07-02
Neat, /proc/meminfo is even more detailed than free -l.

> **nmccrina said:**
> +1

What does "+1" mean by the way?

---

### Post by sdowney717 on 2009-07-02
it means "thumbs up", Good, I like it.

---

