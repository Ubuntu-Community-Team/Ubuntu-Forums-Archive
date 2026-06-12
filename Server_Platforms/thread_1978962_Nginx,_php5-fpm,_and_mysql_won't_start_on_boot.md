---
title: "Nginx, php5-fpm, and mysql won't start on boot"
date: 2012-05-12
forum: Server Platforms
---

### Post by mathcolo on 2012-05-12
Hi everyone&#8211;last night I decided to go ahead and do a migration from my old Ubuntu 10.10 server to a new 12.04 one. Everything works great&#8211;my only problem is that nginx, php5-fpm, and mysql won't start up on boot. Instead, I have to manually run "service nginx start", "service php5-fpm start", and "service mysql start".

I've read some threads over on stackoverflow and other forums about people who have problems with getting those services to start at all on 12.04, but that's not exactly my problem. For me, they work&#8211;they just don't start up on boot.

I've tried messing with update-rc.d to remove the links to the init.d scripts and then re-add them, but nothing I've tried with update-rc has worked. I've also tried looking in /var/log for any log files that would show me why they aren't starting up on boot, and I haven't found anything.

Any assistance would be greatly appreciated, because I'm so close to having a great experience with my new 12.04 install, I'm just not 100% there yet :) Thanks

---

### Post by sandyd on 2012-05-13
> **mathcolo said:**
> Hi everyone–last night I decided to go ahead and do a migration from my old Ubuntu 10.10 server to a new 12.04 one. Everything works great–my only problem is that nginx, php5-fpm, and mysql won't start up on boot. Instead, I have to manually run "service nginx start", "service php5-fpm start", and "service mysql start".

I've read some threads over on stackoverflow and other forums about people who have problems with getting those services to start at all on 12.04, but that's not exactly my problem. For me, they work–they just don't start up on boot.

I've tried messing with update-rc.d to remove the links to the init.d scripts and then re-add them, but nothing I've tried with update-rc has worked. I've also tried looking in /var/log for any log files that would show me why they aren't starting up on boot, and I haven't found anything.

Any assistance would be greatly appreciated, because I'm so close to having a great experience with my new 12.04 install, I'm just not 100% there yet :) Thanks
Post output of
```

ls /etc/init
```

---

### Post by wingeong on 2012-12-09
for me ,the same problem, can anybody help me.
mine /etc/init is as follows:

when I manually boot them, it's ok. but when I let nginx/php-fpm start at boot, they failed.

sudo update-rc.d nginx defaults 96
sudo sysv-rc-conf nginx on 

for example, the above command doesn't make any senses.
thanks in advance.


ls /etc/init
acpid.conf                mysql.conf
alsa-restore.conf         networking.conf
alsa-store.conf           network-interface.conf
anacron.conf              network-interface-container.conf
apport.conf               network-interface-security.conf
atd.conf                  network-manager.conf
avahi-daemon.conf         plymouth.conf
binfmt-support.conf       plymouth-log.conf
bluetooth.conf            plymouth-splash.conf
console.conf              plymouth-stop.conf
console-setup.conf        plymouth-upstart-bridge.conf
container-detect.conf     procps.conf
control-alt-delete.conf   qemu-kvm.conf
cron.conf                 rc.conf
cryptdisks-enable.conf    rcS.conf
cryptdisks-udev.conf      rc-sysinit.conf
cups.conf                 resolvconf.conf
dbus.conf                 rfkill-restore.conf
dmesg.conf                rfkill-store.conf
failsafe.conf             rsyslog.conf
failsafe-x.conf           screen-cleanup.conf
flush-early-job-log.conf  setvtrgb.conf
friendly-recovery.conf    shutdown.conf
hostname.conf             tty1.conf
hwclock.conf              tty2.conf
hwclock-save.conf         tty3.conf
hybrid-gfx.conf           tty4.conf
irqbalance.conf           tty5.conf
lightdm.conf              tty6.conf
modemmanager.conf         udev.conf
module-init-tools.conf    udev-fallback-graphics.conf
mountall.conf             udev-finish.conf
mountall-net.conf         udevmonitor.conf
mountall-reboot.conf      udevtrigger.conf
mountall-shell.conf       ufw.conf
mounted-debugfs.conf      upstart-socket-bridge.conf
mounted-dev.conf          upstart-udev-bridge.conf
mounted-proc.conf         ureadahead.conf
mounted-run.conf          ureadahead-other.conf
mounted-tmp.conf          wait-for-state.conf
mounted-var.conf          whoopsie.conf

---

