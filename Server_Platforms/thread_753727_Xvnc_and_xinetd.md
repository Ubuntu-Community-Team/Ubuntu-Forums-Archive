---
title: "Xvnc and xinetd"
date: 2008-04-13
forum: Server Platforms
---

### Post by dactex on 2008-04-13
Hello all,

I have got Xvnc working on Gutsy (Desktop 7.10) but only if I start it manually.
WinXP client, Realvnc viewer 4
Server is Gutsy Gibbon, Xvnc (RealVNC)

When it works, I can also run it through a Secure Shell tunnel.
When it doesn't work (xinetd), I take ssh out of the equation and it still doesn't work.
Windows vnc client gives the following after the 30-second timeout:
     "The connection closed unexpectedly
      Do you wish to attempt to reconect to 192.168.1.69:5902?"

Manually, this works, and I can see Xvnc in the process list:
$ Xvnc :2 -query localhost -once -geometry 1024x768 -depth 16 -fp /usr/share/fonts/X11/misc/

If I try to have xinetd start it, I get a Start record in the Xvnc log when I try to make a connection. I then get an Exit message in the Xvnc log file when the 30 second timeout occurs. Related file sections are included below. Any ideas what's going on?

With xinetd as the startup method, I get no log records other than the Xvnc Start and Exit records. This implies (I think) that xinetd has started the Xvnc process, although I never see it in the process list.
------------------------------------------
--/etc/services--
vnc1024     5902/tcp

------------------------------------------
--/etc/xinetd.d/vnc1024--
service vnc1024
{
log_type        = FILE /var/log/xinetd_vnc.log
log_on_success  = HOST DURATION PID USERID
log_on_failure  = HOST USERID ATTEMPT
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :2 -query localhost -once -geometry 1024x768 -depth 16 -fp /usr/share/fonts/X11/misc/
}

-----------------------------------------
--/var/log/xinetd_vnc.log--
08/4/13@00:24:16: START: vnc1024 pid=14790 from=192.168.1.100
08/4/13@00:24:46: EXIT: vnc1024 pid=14790 duration=30(sec)

 Thanks ,
David

---

