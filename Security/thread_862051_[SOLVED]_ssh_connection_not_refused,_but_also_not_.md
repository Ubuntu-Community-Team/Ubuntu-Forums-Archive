---
title: "[SOLVED] ssh connection not refused, but also not working"
date: 2008-07-17
forum: Security
---

### Post by gastur on 2008-07-17
Good day!

I have the following trouble with ssh connections:

Two PC's with sshd enabled (7.10 and 8.04.1) can not connect (no matter in which direction, authentication is via password). After the password is sent nothing happens, though /var/log/auth.log shows, that remote user is authorised. sshd is not apparmored, iptables has empty ruleset. None of the machines complain about wrong host keys etc. Sometimes even 'w' and 'who' show, that there is remote user logged in (not always).

Sniffer shows seemingly nothing useful (for it is ssh...).

It is possible to ssh from both machines into Dlink router. Also it is possible to ssh via Putty from a pocket communicator into the 7.10 machine, with 8.04 machine the trouble is the same.

IIRC, about a week ago there were no such problems. The only system updated during last 10 days is 8.04.1 (fresh install at the new computer + recent updates).

Will be glad to see your suggestions :)

---

### Post by kevdog on 2008-07-17
Can each machine connect to itself?  ssh localhost

---

### Post by gastur on 2008-07-17
> **kevdog said:**
> Can each machine connect to itself?  ssh localhost

Yes.

---

### Post by kevdog on 2008-07-17
Just using passwords, can you present the output of:

ssh -vvv <username>@<serveripaddress>

---

### Post by gastur on 2008-07-17
After the password promt (trying to connect from 8.04.1 to 7.10):

debug3: packet_send2: adding 64 (len 58 padlen 6 extra_pad 64)
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
debug3: tty_make_modes: 6 255
debug3: tty_make_modes: 7 255
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
debug3: tty_make_modes: 39 1
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 1
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
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env SHELL
debug3: Ignored env DESKTOP_STARTUP_ID
debug3: Ignored env TERM
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = ru_UA.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768

P.S. Output from the second machine seems pretty similar

P.P.S. At the same time 'w' on 8.04.1 machine shows external user connected, on 7.10 machine - does not.

And at last (after about 15 minutes):

debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i0/0 o0/0 fd 4/5 cfd -1)

debug3: channel 0: close_fds r 4 w 5 e 6 c -1
Read from remote host usx: Connection timed out
Connection to usx closed.
debug1: Transferred: stdin 0, stdout 0, stderr 76 bytes in 941.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.1
debug1: Exit status -1

The difference with normal connection (machine to itself) - I get
debug2: channel 0: rcvd adjust 2097152
as a last line before bash promt appears.

---

### Post by gastur on 2008-07-17
**kevdog**,

thank you for trying to help - but it seems, I found the problem. It's something with wireless connection settings - possibly, transmit window sizes. When I connect 8.04.1 machine to the LAN not with WiFi but with twisted pair ethernet, the problem goes away.

---

### Post by gastur on 2008-07-17
Solved completely.

Sad, but true - the problem was caused by 'wl' restricted driver for Broadcom 4310 USB.

When I returned back to ndiswrapper + windows driver, the trouble went away.

---

### Post by kevdog on 2008-07-17
Good detective work since I'm not sure I would have guessed that as a possible solution.

---

### Post by gastur on 2008-07-17
Well, but your idea to take a look at 'ssh -vvv' output was that hint, that led me to the right decision :)

---

### Post by kevdog on 2008-07-17
Yea but nobody ACTUALLY reads the output from the -vvv command -- I mean that would be silly to actually read the output, think about it, and then try some things.:)

---

### Post by jsandeo on 2008-08-05
Man, you definitely saved my day. After installing Hardy in a new Dell Vostro 1510, I was having the exact same problem with ssh and it was driving me nuts... Thx !

---

