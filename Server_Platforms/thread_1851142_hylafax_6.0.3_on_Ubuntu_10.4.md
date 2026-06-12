---
title: "hylafax 6.0.3 on Ubuntu 10.4"
date: 2011-09-27
forum: Server Platforms
---

### Post by jm2 on 2011-09-27
I am trying to use hylafax to send a faxs.

I installed the program hylafax-server just fine. 6.0.3
I created the /etc/init/ttyS0.conf
I set up the modem properly, and minicom can connect to another modem just fine.
I have Serial USB Robotics Sporter 33.6 faxmodem
So I doubt it is an incompatible modem issue.
 
my /dev/ttyS0 has right permissions. (yes /etc/group has user in dialout group)
crw-rw-rw- 1 uucp dialout 4, 64 2011-09-27 15:50 /dev/ttyS0

ps - shows the following  is running like it is supposed to.

uucp      1406     1  0 15:46 ?        00:00:00 /usr/sbin/faxq
uucp      1409     1  0 15:46 ?        00:00:00 /usr/sbin/hfaxd -d -i 4559
uucp      3966     1  0 15:58 ?        00:00:00 /usr/sbin/faxgetty ttyS0

Class 1 modem.

Yes modemprobe is fine.  using 38400

/var/spool/hylafax/etc/setup.modem has 38400, 19200  (and downward)

*** on Send ****
sendfax -n -d 1847xxxyyyy EM001067.pdf
or 
sendfax -n -d 1847xxxyyyy EM001067.tiff

root@email-server:/etc/init# faxstat -sdl
HylaFAX scheduler on email-server: Running
Modem ttyS0 (1.847.xxxyyyyy): Waiting for modem to come ready

JID  Pri S  Owner Number       Pages Dials     TTS Status
9    127 W rosewo 1847xxxyyy  0:0   0:12         



It is getting to the queue but the modem won't become ready.


/var/log/syslog

Sep 27 16:35:06 email-server HylaFAX[10741]: Parsing hostPort(): "EPRT"
Sep 27 16:35:06 email-server HylaFAX[10741]: Parsing "|1|127.0.0.1|44606|"
Sep 27 16:35:06 email-server HylaFAX[10741]:  `-> s.length() = 19
Sep 27 16:35:06 email-server HylaFAX[10741]:  `-> s[0] = '|'
Sep 27 16:35:06 email-server HylaFAX[10741]:  `-> s[2] = '|'
Sep 27 16:35:06 email-server HylaFAX[10741]:  `-> s[18] = '|'
Sep 27 16:35:06 email-server HylaFAX[10741]: Looks like extended syntax: "|1|127.0.0.1|44606|" [7C: |]
Sep 27 16:35:06 email-server HylaFAX[10741]: `-> Got a: 127.0.0.1[13]
Sep 27 16:35:06 email-server HylaFAX[10741]: `-> Got a: 44606[19]
Sep 27 16:35:06 email-server HylaFAX[10741]: Parsed: Family 1 Address 127.0.0.1 Port 44606
Sep 27 16:35:09 email-server FaxGetty[10518]: /dev/ttyS0: Can not initialize modem.

This is repeated.

then the job times evenually.

Anyone have ideas of what else to check/Change? or post this issue to?

I am sending on the same machine that the hylafax server is on.

Thanks

** for other users *** beware *** of using the faxadduser command it messes up /etc/hylafax/hosts.hfaxd .. copy this file to a backup first ... known bug .. google for this issue.

---

### Post by jm2 on 2011-10-04
I just wanted to post an update.

I put in 0xFFF in my /etc/hylafax/config.ttyS0

restarted Hylafax /etc/init.d/hylafax restart

checked the /var/log/syslog file

It was brought to my attention the ATZ was not getting a response from the modem.

Note: If ihylafax won't start/stop because a process is still running
do a ps -ef | grep ttyS0     (ttyS0 is my modem line)
and kill this process

now the restart will work.

ubuntu 10.4 does not start the ttyS0 correctly on bootup on my machine.


You need 3 processes  in your ps:

1. /usr/sbin/faxq
2. /usr/sbin/hfaxd -d -i 4449
3. /usr/sbin/faxgetty ttyS0  or /usr/sbin/faxgetty -D ttyS0

yes, you need the /usr/sbin/faxgetty if you only sending faxes.

The last piece was my dip switch settings on my US robotics sportster modem

dip Switch  3 must be DOWN. (I have 3,4,8 down and now I get idle and running)
Dip Switch 3 = Enables result codes

I hope this helps someone else.:p

---

### Post by flecken on 2011-11-17
This is a very old ticket I know... but could you explain where you added those processes? I'm running 10.04 and am having very similar  problems.
Thanks for any help you can provide.

---

