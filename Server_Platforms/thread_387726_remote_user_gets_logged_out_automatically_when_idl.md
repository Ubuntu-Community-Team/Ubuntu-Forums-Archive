---
title: "remote user gets logged out automatically when idle"
date: 2007-03-18
forum: Server Platforms
---

### Post by cpbl on 2007-03-18
I'm using the latest edgy, ssh'ing to an (also edgy) server.
I run X applications remotely.
Whenever I am away for 40 minutes, I come back to find the connections closed, applications killed.
My sshfs connections to the server seem to die after such a period too.

This didn't used to happen, and it is not desired. I would like my connections to stay live until I tell them otherwise.
Does anyone know what is controlling the ssh impatience?  Can I fix it?

Thanks!
c

---

### Post by Mr. C. on 2007-03-18
man ssh_config

See if setting ServerAliveInterval helps.

MrC

---

### Post by cpbl on 2007-03-18
Thanks. I haven't tried fiddling with it yet, but the way it reads, this is only for noticing when the connection goes down. Is that right? The connection should not be going down, even intermittently, so if that's what I'm experiencing, I should maybe also chase down that problem.
c

---

### Post by Mr. C. on 2007-03-19
No, I think you've misread:

> ServerAliveInterval 

    Sets a timeout interval in seconds after which if **no data** has been
received from the server, ssh will send a message through the encrypted
channel to request a response from the server.  The default is 0, indicating
that these messages will not be sent to the server, or 300 if the BatchMode
option is set.  This option applies to protocol version 2 only.

The problem has several layers of complexity:

 1) shells can be configured to auto-exit
 2) system-enforced idle-logouts
 3) ssh-level
 4) TCP level

I've only addressed (3) here.

There server has no way to know if the client has disappeared, and can't tell the difference between idle and absent connection.

With no data coming through the tunnel, the connection may be dropped.  The setting above keeps it alive, by periodically requesting the server to send a message.  Many SSH clients have such anti-idle / send no-op sequences to allow users to maintain their connections for long periods of time.

This is discussed in much more detail in the SSH The Secure Shell by O'Reilly and probably others.

MrC

---

### Post by cpbl on 2007-04-27
Ah, I see; I did misread. Thank you very much for explaining.
The problem is odd because it occurs from one IP address on campus here, but not from another.
I will look into the serverAliveInterval.

Chris

---

