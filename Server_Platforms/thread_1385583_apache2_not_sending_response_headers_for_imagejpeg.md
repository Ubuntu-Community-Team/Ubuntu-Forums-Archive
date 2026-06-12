---
title: "apache2 not sending response headers for image/jpeg"
date: 2010-01-19
forum: Server Platforms
---

### Post by garageguy on 2010-01-19
Here's one that has me stumped.

Ubuntu 9.10, apache 2.2.12.  Server info:
```

Server Version: Apache/2.2.12 (Ubuntu)Server Built: Nov 12 2009 22:49:46Server loaded APR Version: 1.3.8Compiled with APR Version: 1.3.8Server loaded APU Version: 1.3.9Compiled with APU Version: 1.3.9Module Magic Number: 20051115:23Hostname/port: localhost:80Timeouts: connection: 300    keep-alive: 15MPM Name: PreforkMPM Information: Max Daemons: 150 Threaded: no Forked: yesServer Architecture: 32-bitServer Root: /etc/apache2Config File: /etc/apache2/apache2.confServer Built With: 
 -D APACHE_MPM_DIR="server/mpm/worker"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D HTTPD_ROOT=""
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="/etc/apache2/mime.types"
 -D SERVER_CONFIG_FILE="/etc/apache2/apache2.conf"Loaded Modules: 
[mod_status.c]("http://localhost/server-info#mod_status.c"), [mod_setenvif.c]("http://localhost/server-info#mod_setenvif.c"), [mod_negotiation.c]("http://localhost/server-info#mod_negotiation.c"), [mod_mime.c]("http://localhost/server-info#mod_mime.c"), [mod_info.c]("http://localhost/server-info#mod_info.c"), [mod_include.c]("http://localhost/server-info#mod_include.c"), [mod_env.c]("http://localhost/server-info#mod_env.c"), [mod_dir.c]("http://localhost/server-info#mod_dir.c"), [mod_deflate.c]("http://localhost/server-info#mod_deflate.c"), [mod_cgi.c]("http://localhost/server-info#mod_cgi.c"), [mod_autoindex.c]("http://localhost/server-info#mod_autoindex.c"), [mod_authz_user.c]("http://localhost/server-info#mod_authz_user.c"), [mod_authz_host.c]("http://localhost/server-info#mod_authz_host.c"), [mod_authz_groupfile.c]("http://localhost/server-info#mod_authz_groupfile.c"), [mod_authz_default.c]("http://localhost/server-info#mod_authz_default.c"), [mod_authn_file.c]("http://localhost/server-info#mod_authn_file.c"), [mod_auth_basic.c]("http://localhost/server-info#mod_auth_basic.c"), [mod_alias.c]("http://localhost/server-info#mod_alias.c"), [mod_so.c]("http://localhost/server-info#mod_so.c"), [http_core.c]("http://localhost/server-info#http_core.c"), [prefork.c]("http://localhost/server-info#prefork.c"), [mod_logio.c]("http://localhost/server-info#mod_logio.c"), [mod_log_config.c]("http://localhost/server-info#mod_log_config.c"), [core.c]("http://localhost/server-info#core.c")

```Now what happens is:  text/html content is served fine, no problems.  But there is a problem serving image/jpeg content.  For example:

```
$ wget http://kokoro.ucsd.edu/raft.jpg
--15:20:29--  http://kokoro.ucsd.edu/raft.jpg
Resolving kokoro.ucsd.edu... 132.239.9.38
Connecting to kokoro.ucsd.edu|132.239.9.38|:80... connected.
HTTP request sent, awaiting response... 200 No headers, assuming HTTP/0.9
Length: unspecified
Saving to: `raft.jpg'

    [                <=>                     ] 3,807       --.-K/s   in 14s    

15:20:44 (267 B/s) - `raft.jpg' saved [3807]
```Note: No response headers, extremely slow download, incorrect resulting filesize (should be 3515).    It is the same with different clients on different machines, not just wget!

One possible clue: There are two interfaces on the server.  So far as I can tell, all requests coming over eth0 have the above problem, but over eth1: 

```
$ wget http://kokoro.ucsd.edu/raft.jpg
--2010-01-19 15:16:43--  http://kokoro.ucsd.edu/raft.jpg
Resolving kokoro.ucsd.edu... 132.239.9.38
Connecting to kokoro.ucsd.edu|132.239.9.38|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3515 (3.4K) [image/jpeg]
Saving to: `raft.jpg'

100%[======================================>] 3,515       --.-K/s   in 0s      

2010-01-19 15:16:43 (193 MB/s) - `raft.jpg' saved [3515/3515]
```... it works fine.  Which makes me think that there might be some broken caching on the network eth0 is connected to, but:  when I install boa and run it instead of apache2, everything works fine over both interfaces.

No errors appear in the logs.

Any ideas what is going on here, and what I can do to fix it?!

Thanks,

--Paul

---

### Post by garageguy on 2010-01-20
Just another clue, for anyone who is thinking about this problem...

I noticed that small .jpg images (and .gif, and .png) are fine, with headers sent and received, so I spent a little time trying to determine a size threshold for this issue.  Consider these image files:

```
-rw-r--r-- 1 www-data www-data 2565 2010-01-20 11:41 raft8.jpg
-rw-r--r-- 1 www-data www-data 2588 2010-01-20 11:40 raft9.jpg
```The larger one doesn't have headers received for it, the smaller one does.  Output from wget -d:

```

$ wget -d http://kokoro.ucsd.edu/raft9.jpg
DEBUG output created by Wget 1.12 on linux-gnu.

--2010-01-20 11:55:46--  http://kokoro.ucsd.edu/raft9.jpg
Resolving kokoro.ucsd.edu... 132.239.9.38
Caching kokoro.ucsd.edu => 132.239.9.38
Connecting to kokoro.ucsd.edu|132.239.9.38|:80... connected.
Created socket 3.
Releasing 0x080a28f0 (new refcount 1).

---request begin---
GET /raft9.jpg HTTP/1.0
User-Agent: Wget/1.12 (linux-gnu)
Accept: */*
Host: kokoro.ucsd.edu
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... 
---response begin---
---response end---
200 No headers, assuming HTTP/0.9
Length: unspecified
Saving to: `raft9.jpg'

    [                <=>                                                                                                                ] 2,881       --.-K/s   in 14s     

Closed fd 3
2010-01-20 11:56:01 (202 B/s) - `raft9.jpg' saved [2881]

``````
$ wget -d http://kokoro.ucsd.edu/raft8.jpg
DEBUG output created by Wget 1.12 on linux-gnu.

--2010-01-20 11:57:22--  http://kokoro.ucsd.edu/raft8.jpg
Resolving kokoro.ucsd.edu... 132.239.9.38
Caching kokoro.ucsd.edu => 132.239.9.38
Connecting to kokoro.ucsd.edu|132.239.9.38|:80... connected.
Created socket 3.
Releasing 0x080a28f0 (new refcount 1).

---request begin---
GET /raft8.jpg HTTP/1.0
User-Agent: Wget/1.12 (linux-gnu)
Accept: */*
Host: kokoro.ucsd.edu
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... 
---response begin---
HTTP/1.1 200 OK
Date: Wed, 20 Jan 2010 19:57:22 GMT
Server: Apache/2.2.12 (Ubuntu)
Last-Modified: Wed, 20 Jan 2010 19:41:56 GMT
ETag: "108c-a05-47d9dc76fcc8f"
Accept-Ranges: bytes
Content-Length: 2565
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: image/jpeg

---response end---
200 OK
Registered socket 3 for persistent reuse.
Length: 2565 (2.5K) [image/jpeg]
Saving to: `raft8.jpg'

100%[==================================================================================================================================>] 2,565       --.-K/s   in 0.008s  

2010-01-20 11:57:22 (309 KB/s) - `raft8.jpg' saved [2565/2565]
```Now why would that be...?

--Paul

---

### Post by garageguy on 2010-01-23
Geez, hate to be solving my own problems here, but what can you do.

Wireshark and telnet to port 80 showed the response headers in question were in fact being sent out on the wire from the server, but prefixed with some apparently random binary junk, so the client can't read them.  

Searching on that symptom, I came across folks having success with the following:

# EnableMMAP and EnableSendfile: On systems that support it,
# memory-mapping or the sendfile syscall is used to deliver
# files. This usually improves server performance, but must
# be turned off when serving from networked-mounted
# filesystems or if support for these functions is otherwise
# broken on your system.
#
EnableSendfile off 

Tried it, and problem fixed.  I don't know why my ubuntu install has broken support for sendfile (the partition I'm serving from is not network mounted), or why the breakage shows up only in this particular way, but I have a working server now.

Cheers,

--Paul

---

### Post by xianic on 2010-08-17
I had the same problem, and fixed it with the solution you have shown [http://ubuntuforums.org/showthread.php?p=9730221](http://ubuntuforums.org/showthread.php?p=9730221). I too am intreeged as to why sendfile is broke (if indeed it is?) as it's serving from a local partition (not network mounted).

---

### Post by ghost1k on 2010-10-22
Many thanks for your solution, works great. Just added "EnableSendfile off" to my apache2.conf and images now load OK.

---

