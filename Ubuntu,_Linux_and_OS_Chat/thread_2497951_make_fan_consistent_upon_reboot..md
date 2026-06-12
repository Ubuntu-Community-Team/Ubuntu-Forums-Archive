---
title: "make fan consistent upon reboot."
date: 2024-05-23
forum: Ubuntu, Linux and OS Chat
---

### Post by sblantipodi on 2024-05-23
hi there... I have a docker compose file that should mount this volume:
/sys/devices/platform/cooling_fan/hwmon/hwmon3/fan1_input

the weird thing is that sometimes the file is written in
/sys/devices/platform/cooling_fan/hwmon/hwmon3/fan1_input
and sometimes in
/sys/devices/platform/cooling_fan/hwmon/hwmon2/fan1_input


if I reboot it switched from hwmon2 to hwmon3 and viceversa


why this file is not consistent upon reboot? is it possible to make it consistent upon reboot?

---

### Post by sblantipodi on 2024-05-24
I solved by populating an environment variable with a bash script and using it in my docker compose.
not the best practice I think, but it works.

---

