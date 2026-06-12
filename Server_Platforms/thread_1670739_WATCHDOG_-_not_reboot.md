---
title: "WATCHDOG - not reboot"
date: 2011-01-19
forum: Server Platforms
---

### Post by draio on 2011-01-19
Hi, I'm trying to use the watchdog system (on ubuntu 9.10) so that the  PC will reset if there are not updates on /dev/watchdog (as it should be  by default I think).

I installed watchdog
** apt-get install watchdog **

It seems that watchdog is already present on kernel because I found **ipmi_watchdog** under the modules (**/sys/module/ipmi_watchdog**)

I loaded the module with **modprobe ipmi_watchdog** and i didn't have any problem. 
Checking with **lsmod** i found the module loaded.

[B] 17 104 0 ipmi_watchdog
ipmi_msghandler 35,256 a ipmi_watchdog [/B]

On **/etc/watchdog.conf** I removed the comment to ** watchdog-device = /dev/watchdog ** to control the file/device. In a second test, I also enabled ** interval = 10 ** as test.

Finally, I added ** ipmi_watchdog ** to ** /etc/modules ** so that is loaded at boot.

The problem is that nothing happens.

The file **/dev/watchdog** is not created by the installation or by the deamon.
I tried to create it (**mknod /dev/watchdog c 10 130**) but nothing happens. 

I also copied and compiled a test program found here:
[http://kernel.ubuntu.com/git-repos/rtg/ubuntu-hardy/Documentation](http://kernel.ubuntu.com/git-repos/rtg/ubuntu-hardy/Documentation) /watchdog /src /

It work correctly ... but if I stop updating the file **/dev/watchdog** nothing happens.

Finally, I checked **/boot/config-2.6.31-20-generic** and I found  this configuration:

[B] y = CONFIG_CLOCKSOURCE_WATCHDOG
CONFIG_IPMI_WATCHDOG = m
CONFIG_WATCHDOG = y
# CONFIG_WATCHDOG_NOWAYOUT is not set
CONFIG_SOFT_WATCHDOG = y
CONFIG_WM8350_WATCHDOG = m
CONFIG_TWL4030_WATCHDOG = m
# CONFIG_HP_WATCHDOG is not set
CONFIG_SBC_EPX_C3_WATCHDOG = m
CONFIG_PCWATCHDOG = m
CONFIG_PCIPCWATCHDOG = m
CONFIG_USBPCWATCHDOG = m
[/B]

Can anyone help me?
Thanks

---

