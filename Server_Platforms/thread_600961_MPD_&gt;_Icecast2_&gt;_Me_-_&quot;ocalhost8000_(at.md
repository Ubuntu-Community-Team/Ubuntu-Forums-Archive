---
title: "MPD &gt; Icecast2 &gt; Me - &quot;ocalhost:8000 (attempt 1): Socket error&quot;"
date: 2007-11-02
forum: Server Platforms
---

### Post by emil.s on 2007-11-02
I have setup MPD to stream to Icecast2. And I can connect to Icecast status page at "http://*the server*:8000".
But something is wrong in the communication between MPD and Icecast.

The "/var/log/mpd/error.log" says:```

Nov 02 23:45 : problem opening connection to shout server localhost:8000 (attempt 1): Socket error
Nov 02 23:45 : problems opening audio device while playing "any-file.mp3"
```

/var/log/icecast2/access.log:```

127.0.0.1 - - [02/Nov/2007:23:24:04 +0100] "SOURCE /stream.ogg HTTP/1.0" 200 19 "-" "MPD" 11
```

And /var/log/icecast2/error.log:```

[2007-11-02  23:44:49] INFO sighandler/_sig_die Caught signal 15, shutting down...
[2007-11-02  23:44:50] DBUG connection/_handle_connection Connection thread done
[2007-11-02  23:44:50] INFO main/main Shutting down
[2007-11-02  23:44:50] INFO fserve/fserve_shutdown file serving thread stopped
[2007-11-02  23:44:50] DBUG slave/slave_shutdown waiting for slave thread
[2007-11-02  23:44:50] DBUG slave/_slave_thread shutting down current relays
[2007-11-02  23:44:50] INFO slave/_slave_thread Slave thread shutdown complete
[2007-11-02  23:44:51] INFO auth/auth_run_thread Authenication thread shutting down
[2007-11-02  23:44:51] INFO auth/auth_shutdown Auth thread has terminated
[2007-11-02  23:44:51] INFO yp/yp_shutdown YP thread down
[2007-11-02  23:44:51] INFO stats/stats_shutdown stats thread finished
```

Does someone know how to solve this?

---

