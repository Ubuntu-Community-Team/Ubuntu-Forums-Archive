---
title: "Stuck Neatx session"
date: 2010-06-08
forum: Server Platforms
---

### Post by semick on 2010-06-08
I'm using the Neatx server on Lucuid 10.04. I have been using it for a while with no problems. 
My session crashed when I was logged in, not when I try to log in, I get internal error from the nomachine client.  The details say: 
```
NX> 203 NXSSH running with pid: 12504
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XX.XX.XX.XXX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0 - GPL
NX> 105 Hello nxclient - version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set SHELL_MODE: SHELL
NX> 105 Set AUTH_MODE: PASSWORD
NX> 105 Login
NX> 101 User: scott
NX> 102 Password: **********
Could not find ':' in DISPLAY: 
NX> 103 Welcome to: venus user: scott
NX> 105 Listsession --user="scott" --status="suspended,running" --geometry="1680x1050x32+render" --type="unix-gnome"
NX> 127 Session list of user 'scott':
Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
940     unix-gnome       8955BA9D7806E1CB625C83F912A9C987 -RD--PSA    24 1024x768       Running     venus

NX> 148 Server capacity: not reached for user: scott
NX> 105 Restoresession  --link="adsl" --backingstore="1" --encryption="1" --cache="16m" --images="64m" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="venus" --type="unix-gnome" --geometry="1024x768" --client="winnt" --keyboard="pc102/en_us" --id="8955ba9d7806e1cb625c83f912a9c987" --resize="1"
NX> 500 Internal error
NX> 999 Bye.
Sessions still open, not unmounting
NX> 280 Exiting on signal: 15
```

I can still login with other users, just not mine now.  I have rebooted the server, that didn't help.

---

### Post by semick on 2010-06-08
I fixed it.  If neatx crashes and doesn't delete the sessions, you can delete them yourself.  On my system they are stored in:

/var/lib/neatx/sessions

after doing this, I could connect again with my user.

---

### Post by continuous on 2010-06-10
Thanks, solved the problem for me too. 
Cheers.

---

### Post by penny8 on 2010-10-09
Hi, It was really helpful big thanks for You. I had some big problems and I lost a lot of time trying to resolve problem with neatx sessions.

One more time thanks.

---

