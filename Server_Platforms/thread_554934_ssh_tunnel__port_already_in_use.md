---
title: "ssh tunnel : port already in use ?"
date: 2007-09-19
forum: Server Platforms
---

### Post by NarsilAnduril on 2007-09-19
Hi falks,

I need some help with ssh tunneling to run VNC from a Edgy machine (source) to a Feisty machine (target)

My first debugging investigations :

[LIST]
Vino-server is up on target machine, connection from source works when using port 5900.[/LIST]
[LIST]openssh is up on target machine, connection from source works straight[/LIST]
[list]netstat -tap|grep LISTEN returns

```
tcp        0      0 localhost:2208          *:*                     LISTEN     -                   
tcp        0      0 localhost:ipp           *:*                     LISTEN     -                   
tcp        0      0 localhost:2207          *:*                     LISTEN     -                   
tcp6       0      0 *:5900                  *:*                     LISTEN     6824/vino-server    
tcp6       0      0 *:ssh                   *:*                     LISTEN     -
```[/list]

Now, when I try to open the tunnel, I get :
```
me@source:~$ ssh -L 5900:xxx.xxx.xxx.xxx:5900 target@xxx.xxx.xxx.xxx
target@xxx.xxx.xxx.xxx's password: 
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 5900
Could not request local forwarding.
Linux lautre-desktop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Sep 19 21:17:16 2007 from nnn.nnn.nnn.nnn
target@target-desktop:~$
```

So, what's up doc ?

Of course, port 5900 is already in use ... but if Is I stop vino-server on target and free the port, the answer is the same.

Any suggestion ?

Thanks

---

### Post by NarsilAnduril on 2007-09-19
vino-server was running on source ...

Stopped vino-server, freed the port, build connection:guitar::popcorn:

---

