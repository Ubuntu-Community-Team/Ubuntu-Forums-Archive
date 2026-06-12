---
title: "Set up a tftp server using Ubuntu's tftpd-hpa"
date: 2008-12-20
forum: Server Platforms
---

### Post by docplastic on 2008-12-20
This procedure will set up a tftp server (running as a daemon) using Ubuntu's tftpd-hpa.

This procedure is also useful while trying to solve problems of LTSP thin client failing to boot at the tftp fase.

(Tested on 8.04 and 8.10)

## purge any old config
sudo aptitude purge tftpd-hpa openbsd-inetd

## install only tftpd-hpa
sudo aptitude -R install tftpd-hpa

## enable RUN_DAEMON
sudo sed -i 's/.*RUN_DAEMON.*/RUN_DAEMON="yes"/' /etc/default/tftpd-hpa

## disable tftp inetd supervision
sudo sed -i 's/^tftp/#<off># tftp/' /etc/inetd.conf # has the same effect as: sudo update-inetd --disable tftp

## enable it to auto-start
sudo update-rc.d -f tftpd-hpa remove # remove auto boot
sudo update-rc.d tftpd-hpa start 20 2 3 4 5 . stop 20 1 . # reinstall auto boot

## start the service with the new parameters
# sudo /etc/init.d/tftpd-hpa restart is broken (the restart script exits after executing the first stop), use instead:
sudo /etc/init.d/tftpd-hpa stop
sudo /etc/init.d/tftpd-hpa start

---

