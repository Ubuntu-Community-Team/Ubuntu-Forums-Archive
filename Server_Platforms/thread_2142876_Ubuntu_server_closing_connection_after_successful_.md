---
title: "Ubuntu server closing connection after successful login"
date: 2013-05-07
forum: Server Platforms
---

### Post by sajithmohan on 2013-05-07
[COLOR=#000000][FONT=Arial]i was unable to connect server through winscp (after i changed permissions of www directory of Apache server accidently),it shows *Cannot initialize SFTP protocol. Is the host running a SFTP server?* when executing this command in terminal sftp -P port-vv username@serverip ,i am getting following response,what will be the problem?[/FONT][/COLOR]

debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to ***** 
debug2: fd 4 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: subsystem request accepted on channel 0
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype [email]eow@openssh.com[/email] reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: rcvd close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 1952, received 1960 bytes, in 0.3 seconds
Bytes per second: sent 6473.8, received 6500.3
debug1: Exit status 141

---

### Post by sajithmohan on 2013-05-07
solved
the problem is about file permission,some file permission has changed,so i cant run SFTP .to reset permissions i followed the link
[http://sysadminnotebook.blogspot.in/2012/06/how-to-reset-folder-permissions-to.html](http://sysadminnotebook.blogspot.in/2012/06/how-to-reset-folder-permissions-to.html)

---

