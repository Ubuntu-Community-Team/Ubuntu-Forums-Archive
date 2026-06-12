---
title: "Hylafax on Ubuntu 8.04"
date: 2008-07-20
forum: Server Platforms
---

### Post by dileep@networkgulf.com on 2008-07-20
Hi,
I am trying to setup hylafax on Ubuntu 8.04 server with Mainpine IQ express 2port card.

The modems wre detected and configured as ttyS2 & ttyS3 automatically. Hylafax also installed without any problems. Faxsetup and faxaddmodem went on smoothly and the modems were configured for hylafax without any problems. 

I ran into problems when i tried to configure faxgetty to respawn the modems. As Ubuntu uses Upstart in place of init, I created ttyS2 & ttyS3 in /etc/event.d with the following entries

------------
     start on runlevel 2
     start on runlevel 3
     start on runlevel 4
     start on runlevel 5
     stop on runlevel 0
     stop on runlevel 1

     stop on runlevel 6
     respawn
     exec /usr/sbin/faxgetty ttyS#
---------------

The last line was modified with the appropriate entry for the modem devices (ttyS2 & ttyS3). After reboot hylafax was completely stopped working.

Faxstat says 'Can not reach server at host "localhost" , port 4559. Attempts to restart the server also fails and says that 'Not starting hylafax daemons since they are already running'. However ps -ae does not list any faxq or hfaxd processes.

It looks like a problem with faxgetty trying to respawning the modems, as the server comes backup normally if I remove the modem entries from /etc/event.d. 

The device files (/dev/ttyS2 & S3) had ownership of uucp.dialout. Any changes to this is reset on reboot. As I read that any non root user wanting to access the modems in Ubuntu has to be part of the dialout group, I added uucp to dialout group without any success.

I am at a loss to understand where the problem could be, as many people seem to have got this working. It will be a great help if anybody can help me on this.

Thanks in advance.

regards

Dileep

---

### Post by renepilz on 2008-08-11
edit /etc/default/hylafax

after
---cut---
# try to check for the correct USE_FAXGETTY value
if grep -E '^[^#]*:respawn:/usr/sbin/fax(getty|modem).*$' /etc/inittab >/dev/null 2>&1
then
        USE_FAXGETTY=init
else
        USE_FAXGETTY=yes
fi
---cut---

add the following:
---cut---
# Also check event.d-dir
if grep -E '^exec /usr/sbin/fax(getty|modem)' /etc/event.d/* >/dev/null 2>&1
then
        USE_FAXGETTY=init
fi
----cut---

---

### Post by pkombala on 2008-08-25
guy 
I work with and I were able to setup a Linux (Ubuntu) server. We've installed Hylafax, configured it, and even got it working. Both sending and receiving. The problem we are having is, the Windows client we are using to send the data to the Linux server implies that you can get an email confirmation that the fax was sent through. What needs to be setup on the server so that it can email that information out? I am figuring that is were the problem lies. Any help in these matters would be greatly appreciated.
Please give me how to setup Exim4 for receiving email notification for sendfax ...

---

### Post by barbarian on 2009-05-19
> **renepilz said:**
> edit /etc/default/hylafax

after
---cut---
# try to check for the correct USE_FAXGETTY value
if grep -E '^[^#]*:respawn:/usr/sbin/fax(getty|modem).*$' /etc/inittab >/dev/null 2>&1
then
        USE_FAXGETTY=init
else
        USE_FAXGETTY=yes
fi
---cut---

add the following:
---cut---
# Also check event.d-dir
if grep -E '^exec /usr/sbin/fax(getty|modem)' /etc/event.d/* >/dev/null 2>&1
then
        USE_FAXGETTY=init
fi
----cut---

Thank you, but it doesn't help at all:(

---

