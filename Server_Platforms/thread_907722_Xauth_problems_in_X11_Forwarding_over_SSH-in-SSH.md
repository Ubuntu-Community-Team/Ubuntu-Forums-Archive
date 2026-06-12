---
title: "Xauth problems in X11 Forwarding over SSH-in-SSH"
date: 2008-09-01
forum: Server Platforms
---

### Post by viordiasko on 2008-09-01
[Solution below.]

I have a remote PC 'R' . I would like to connect to 'R' (with hostname R_hostname) from my client PC 'C' & run X programs. But I have to go through the only PC visible to the outside world, the gateway PC 'G' behind a router. To get round this I set up ssh with ssh port forwarding as detailed below.


Ultimately I get "Invalid MIT-MAGIC-COOKIE-1 key" errors unfortunately.

Background info:

The router forwards port 22000 to 'G'.

**NB: I cannot change the router settings remotely.**

SSH servers runs on both 'G' & 'R' .

```

Client C---SSH-->|ROUTER|--Gateway G---SSH--->Remote R
<---INTERNET----><-------------------LAN------------->

```
~/.ssh/ssh_config on Client 'C':
```
ForwardAgent Yes
ForwardX11 Yes
```
IP addresses:
Router:99.99.99.99 (External, Fixed, world visible)
G:192.168.1.4 (Internal, static)
R:192.168.1.88 (Internal, static)

I can set up an initial port forwarding 
```
ssh -L2001:192.168.1.88:22 99.99.99.99 -p 22000 -i /home/client/.ssh/key
```
And the following executed in another terminal sees me connect transparently to 'R' just as if I could connect directly to 'R' from the internet.
```
ssh -v -p 2001 -o HostKeyAlias=R_hostname localhost -i /home/client/.ssh/key
```

All command line stuff seems to work here but the launching graphical programs fails with :
```
remote@R_hostname:~$ agave &
[1] 9455
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 58123
debug1: channel 1: new [x11]
debug1: confirm x11
remote@R_hostname:~$ Invalid MIT-MAGIC-COOKIE-1 key
Ouch, that hurt.debug1: channel 1: free: x11, nchannels 2

Please report this error to https://gna.org/bugs/?group=colorscheme
Include the following information:
cannot open display:
```

Any suggestions regards xauth/xhost commands and settings would be greatly appreciated.

**SOLVED:**
I had to login to the account on 'C' with the same name ie 'remote' rather than su to 'remote' from my regular a/c on 'C' before setting up the tunnel as above.

FWIW Firefox was ridiculously slow but konqueror was acceptable.

---

