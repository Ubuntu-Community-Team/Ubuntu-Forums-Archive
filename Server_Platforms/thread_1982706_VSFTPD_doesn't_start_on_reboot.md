---
title: "VSFTPD doesn't start on reboot"
date: 2012-05-19
forum: Server Platforms
---

### Post by webmuppet on 2012-05-19
I have a standard install of 10.04 LTS LAMP. Everything installs and works fine to run a webserver except VSFTPD doesn't start on boot. I can start the service manually fine with start vsftpd and all the other services start on boot.

I'm pretty new to Ubuntu and days of searching hasn't turned up much. It's a VPS so I have no desktop but also, maddenly, I can't seem to find much in the way of logging.

I think it is supposed to start with upstart, this is the conf in /etc/init/vsftpd.conf

> # vsftpd - FTP Daemon
#

description     "vsftpd daemon"
author          "Chuck Short <zulcss@ubuntu.com>"

start on (filesystem
        and net-device-up IFACE!=lo)
stop on runlevel [!2345]
respawn

pre-start script
        check_standalone_mode()
        {
                # Return 1 if vsftpd.conf doesn't have listen yes or listen_ipv6=yes
                CONFFILE="/etc/vsftpd.conf"

                if [ -e  "${CONFFILE}" ] && ! egrep -iq "^ *listen(_ipv6)? *= *yes" "${CONFFILE}"
                then
                        echo "${CONFFILE}: listen disabled - service will not start"
                        return 1
                fi
        }
        [ -d /var/run/vsftpd ] || install -m 755 -o root -g root -d /var/run/vsftpd
        [ -d /var/run/vsftpd/empty ] || install -m 755 -o root -g root -d /var/run/vsftpd/empty
        check_standalone_mode || stop
end script

exec /usr/sbin/vsftpd


Any help much appreciated.

---

### Post by webmuppet on 2012-05-22
/bump

Anyone any ideas, I'm really stuck here.

---

### Post by druhboruch on 2012-05-22
There may be some clue in the log...

---

### Post by webmuppet on 2012-05-22
That was the first place I tried to look but there doesn't seem to be much in the way of bootlogging and since it's a VPS I can't get access to the actual machine at boot time. If you could give me some direction on increasing logging (or finding logs I may not know about) it would be much appreciated.

> **druhboruch said:**
> There may be some clue in the log...

---

### Post by wattz3 on 2012-06-08
> **webmuppet said:**
> That was the first place I tried to look but there doesn't seem to be much in the way of bootlogging and since it's a VPS I can't get access to the actual machine at boot time. If you could give me some direction on increasing logging (or finding logs I may not know about) it would be much appreciated.

I had the same issue, and also with MySQL. They don't start on reboot. Seems to be some kind of bug. Only work-around I found was to edit the startup script.
Change "start on" to:
start on runlevel [2345]


Found this info here: [http://askubuntu.com/questions/15222/mysql-server-upstart-script-not-working-on-boot](http://askubuntu.com/questions/15222/mysql-server-upstart-script-not-working-on-boot)

---

### Post by webmuppet on 2012-06-09
> **wattz3 said:**
> I had the same issue, and also with MySQL. They don't start on reboot. Seems to be some kind of bug. Only work-around I found was to edit the startup script.
Change "start on" to:
start on runlevel [2345]


Found this info here: [http://askubuntu.com/questions/15222/mysql-server-upstart-script-not-working-on-boot](http://askubuntu.com/questions/15222/mysql-server-upstart-script-not-working-on-boot)

This did indeed work. Cheers!

---

