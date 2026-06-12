---
title: "Cannot connect with rssh in ubuntu server 12.04.1"
date: 2012-12-05
forum: Server Platforms
---

### Post by Cfhs_1 on 2012-12-05
Hello everyone!

I've tried setting up rssh for a user on my server, I've done this in the past, and got it working, but this time it's not working right. I can connect, but it immediently kicks me back out, and gives me this:

```
This account is restricted by rssh.
Allowed commands: scp 

If you believe this is in error, please contact your system administrator.

debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
Connection to ubercraft.dyndns.org closed.
Transferred: sent 2136, received 2480 bytes, in 0.5 seconds
Bytes per second: sent 3949.2, received 4585.2
debug1: Exit status 1
```

Any ideas? I really need to get this working. This user needs access, but I don't want him to have standard ssh access. He's only going to be running a small script I wrote once he's logged in. I don't want him to be able to do much else.

Thanks in advance,
-NCB

---

### Post by Cfhs_1 on 2012-12-05
BUMP

Anyone? I really need help with this.

---

