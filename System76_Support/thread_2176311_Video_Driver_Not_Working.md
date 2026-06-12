---
title: "Video Driver Not Working"
date: 2013-09-23
forum: System76 Support
---

### Post by Priswell on 2013-09-23
I have a System76 Wildebeest that came preinstalled with Ubuntu 10.04. A couple of weeks back, I upgraded to Ubuntu 12.04 with no problems. Today I installed the updates, and when I logged on, my video was not at the proper resolution. It's now at 1024x768, but before it was 1920x1080. 

When I tried to install the proprietary video drivers I got the following error message:

"Sorry. Installation of this driver failed. Please have a look at log file details at /var/log/jockey.log" as seen at:

[http://pastebin.com/gRD6SWic](http://pastebin.com/gRD6SWic)

How can I proceed? Is there a System76 driver I should look for? or do I start looking for solutions elsewhere?

---

### Post by houstonbofh on 2013-09-23
A few weeks back I too noticed that the nvidia drivers crashed hard with an upgrade.  Log in and remove all of the nvidia drivers (Not common as that is a ubuntu-desktop dependency) and reboot.  Then run the driver manager again and install the backports updated.

---

### Post by Priswell on 2013-09-23
Like the instructions found here?

[http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

---

### Post by Priswell on 2013-09-23
OK, got it working following above instructions. Thank you very much for responding!

---

