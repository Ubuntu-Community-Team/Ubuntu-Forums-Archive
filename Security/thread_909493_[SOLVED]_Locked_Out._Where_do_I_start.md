---
title: "[SOLVED] Locked Out. Where do I start?"
date: 2008-09-03
forum: Security
---

### Post by champishere on 2008-09-03
I'm having a problem connecting to my server using sftp or ftp
I usually used filezilla for this.
For some reason I am not able to login with one of my user account. I can login with ssh but not sftp. I can login with another user so I don't think it has anything to do with my settings.

??? Anyone know how I can get access again, what program locked me out or how I can resolve this???

Any response greatly appreciated.


Example

this is what happen when i login with thisuser

Status: Connecting to 192.168.1.100...
Response: fzSftp started
Command: open "thisuser@192.168.1.100" 22
Command: Pass: **********************
Status: Connected to 192.168.1.100
Error: Connection timed out
Error: Could not connect to server



this is what happen when i login with the otheruser

Status: Connecting to 192.168.1.100...
Response: fzSftp started
Command: open "otheruser@192.168.1.100" 22
Command: Pass: **************
Status: Connected to 192.168.1.100
Status: Retrieving directory listing...
Command: pwd
Response: Current directory is: "/home/otheruser"
Command: ls
Status: Listing directory /home/otheruser
Status: Calculating timezone offset of server...
Command: mtime ".bash_history"
Response: 1218521529
Status: Timezone offsets: Server: -18009 seconds. Local: -18000 seconds. Difference: 9 seconds.
Status: Directory listing successful


Some programs that's running on my system that may have something to this problem.
Apparmor
DenyHosts
OpenBSDSecure Shell server sshd
securityfs
ufw

---

### Post by HermanAB on 2008-09-03
You can get debug info with:
$ ssh -vvv user@server

---

### Post by champishere on 2008-09-03
After trying

sftp -vvv thisuser@192.168.1.100

The only part on the message that seemed to be an error was this.




debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
Received message too long 172516716        <----------- this seems to be where the error started
debug2: channel 0: read<=0 rfd 4 len -1
debug2: channel 0: read failed
debug2: channel 0: close_read
debug2: channel 0: input open -> drain
debug2: channel 0: ibuf empty
debug2: channel 0: send eof
debug2: channel 0: input drain -> closed
thisuser@thisserver:~$ debug2: channel 0: write failed
debug2: channel 0: close_write
debug2: channel 0: output open -> closed
debug2: channel 0: rcvd eof
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd close
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

debug3: channel 0: close_fds r -1 w -1 e 6 c -1
debug1: fd 0 clearing O_NONBLOCK
debug3: fd 1 is not O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.3 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 0



Any Suggestions??????????????

---

### Post by champishere on 2008-09-03
After reading info on this site

[http://www.snailbook.com/faq/sftp-corruption.auto.html](http://www.snailbook.com/faq/sftp-corruption.auto.html)

regarding sftp "Received message too long"
I realized that the script that I added to my .bashrc file was
causing the problem.

Many thanks to HermanAB for leading me in the right direction.

---

### Post by eeried on 2008-11-06
Hello,

I have a similar problem but I have never edited my .bashrc file.

I've upgraded to Ibex through the net.

Here's part of the debug file:
> debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug3: channel 0: will not send data after close

This is a disabled shell account.

You can enable login for this account on the panel by selecting an
appropriate shell in the user preferences section.

debug3: channel 0: will not send data after close
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 6 c -1
Connection to sftp.tuxfamily.net closed.
Transferred: sent 1696, received 2552 bytes, in 0.2 seconds
Bytes per second: sent 6811.2, received 10248.9
debug1: Exit status 1

Can you help me?

---

