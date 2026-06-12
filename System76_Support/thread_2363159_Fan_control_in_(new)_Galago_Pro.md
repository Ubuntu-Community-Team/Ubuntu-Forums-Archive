---
title: "Fan control in (new) Galago Pro"
date: 2017-06-06
forum: System76 Support
---

### Post by anthonywc on 2017-06-06
Anyone able to get fan control to work with the Galago Pro?  

Tried lm-sensor/sensor-detect which can't seem to detect the fan even with adding GRUB_CMDLINE_LINUX_DEFAULT="acpi_enforce_resources=lax" to grub. I don't see fan_input in any of the hwmon subfolder either.

Also lm-sensor doesn't support i915 gmbus and lm-sensor project itself isn't very active ([https://github.com/groeck/lm-sensors/graphs/contributors](https://github.com/groeck/lm-sensors/graphs/contributors)) :(

---

### Post by april-system76 on 2017-06-08
Hi,

Fans aren't exposed to the OS at all right now, it's a limitation we're hoping to get around in the future. No hard plans yet, though.

---

### Post by Naaatan on 2017-06-21
Could you guys at least calibrate them properly? My biggest annoyance with the Galago Pro so far is that the fans just constantly start and stop (start as in become audible). Of course ideally I'd like to hear them as little as possible but if it's gonna run them then I prefer it do so steadily and not constantly start and stop in a matter of seconds.

---

### Post by april-system76 on 2017-06-22
Have you opened a support ticket with us? Send me a message or open a ticket if you could, I'd like to chat with you further about the fans starting and stopping. We're in the final stages of testing an EC update.

---

### Post by luismontreal on 2017-07-04
On of the issues that I see is not directly related to the fans but how the CPU behaves.    I have the i57200U and it doesn't matter what process I start the CPU will go to 100% usage momentarily.  This makes the fan to activate immediately and with high noise for a couple of seconds.   I have managed to limit the frecuency of the cpus by using cpufreq-utils, it helps a little with the annoyance but it's far from the best solution.  Also, kaby lake processor  support  is pretty new to linux (kernel 4.10, ubuntu 17.04).   Hopefully the driver is improved.

---

