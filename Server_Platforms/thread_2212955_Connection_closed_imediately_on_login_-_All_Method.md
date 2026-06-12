---
title: "Connection closed imediately on login - All Methods"
date: 2014-03-24
forum: Server Platforms
---

### Post by Don Barnett on 2014-03-24
I am running a 12.04 Ubuntu server.  Last Friday I install vsftpd on my production server.  Now I cannot get logged back into the server whether at the console or ssh.  Immediately after entering my password the connection is closed.  I am desperate and dead in the water without this server.   At this point I can't even get in to modify anything.

I did an ssh login from my test server to my production server with the -vvv option.  Below are the results from the point I entered the password.  you will notice that I get the login welcome screen just before the connection is closed.   Any help would be greatly appreciated.  

Thanks
Don B

debug3: packet_send2: adding 64 (len 59 padlen 5 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 0
debug3: tty_make_modes: 7 0
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 0
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 0
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug1: Sending environment.
debug3: Ignored env SHELL
debug3: Ignored env TERM
debug3: Ignored env OLDPWD
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SUDO_USER
debug3: Ignored env SUDO_UID
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env MAIL
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env SHLVL
debug3: Ignored env SUDO_COMMAND
debug3: Ignored env HOME
debug3: Ignored env LOGNAME
debug3: Ignored env LESSOPEN
debug3: Ignored env SUDO_GID
debug3: Ignored env LESSCLOSE
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-30-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Sun Mar 23 20:52:51 PDT 2014

  System load:  0.0                Processes:           106
  Usage of /:   1.4% of 663.07GB   Users logged in:     0
  Memory usage: 2%                 IP address for eth0: 192.168.3.155
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

233 packages can be updated.
136 updates are security updates.

Last login: Sun Mar 23 20:52:02 2014 from 192.168.1.155
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 10 c -1
Connection to 192.168.3.155 closed.
debug1: Transferred: stdin 0, stdout 0, stderr 37 bytes in 1.2 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 29.8
debug1: Exit status 1
root@fhsctestserver:/etc/bind#

---

