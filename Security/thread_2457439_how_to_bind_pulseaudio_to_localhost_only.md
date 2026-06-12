---
title: "how to bind pulseaudio to localhost only?"
date: 2021-02-02
forum: Security
---

### Post by mollat on 2021-02-02
Hi there,

I am using several xbuntu installations, that are now and then directly exposed to the internet. So I want to have as few open ports as possible or take non-usual port alternatives. So this is mostly not very complicated.
However - I can not manage to fix this for pulseaudio:

```

root@mollat-pc:/home/mollat# netstat -lp | grep pulseaudio
tcp        0      0 0.0.0.0:37747           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:39189           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:45721           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:34235           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:45309           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:45957           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:38341           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:44391           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:40329           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:45065           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:4713            0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:36045           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:35727           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp        0      0 0.0.0.0:38191           0.0.0.0:*               LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:46195              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:41591              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:33915              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:34821              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:41511              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:4713               [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:46475              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:44427              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:36941              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:35917              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:38797              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:42895              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:45551              [::]:*                  LISTEN      8078/pulseaudio     
tcp6       0      0 [::]:44529              [::]:*                  LISTEN      8078/pulseaudio     
root@mollat-pc:/home/mollat#

```

I searched extensively but did not find any option in pulseaudio's config files to advise it to bind only to local interfaces. (Searching for "port", "bind" and "interface" in the context of pulseaudio is very unproductive anyway, as these words are used in a different context all the time... ;)
Does anyone know where to look further?

Thanks in advance,

Andreas

---

### Post by TheFu on 2021-02-02
Here's what I see on an 18.04 system (sorta LXDE-based, but openbox is seldom used). Sorry, but I don't have any Xubuntu here.

```
$ sudo netstat -lp | grep pulseaudio
unix  2      [ ACC ]     STREAM     LISTENING     114907   18447/pulseaudio     /run/user/1000/pulse/native
unix  2      [ ACC ]     STREAM     LISTENING     1694656  28531/pulseaudio     /tmp/pulse-KdhtXMmr18n2/native

```
With pulse, I've only changed the ~/.config/pulse/client.conf file to add 1 line:
```
enable-shm = no
```
No changes to the "server" side config. 

That system is currently playing music using mpd, controlled by any mpc on the LAN.

On a 20.04 desktop using fvwm, 
```
$ sudo netstat -lp | grep pulseaudio  
tcp        0      0 0.0.0.0:4713            0.0.0.0:*               LISTEN      1056/pulseaudio     
```
It is a virtual machine.  Let me start a full GUI on it.```

tcp        0      0 0.0.0.0:4713            0.0.0.0:*               LISTEN      1056/pulseaudio     
unix  2      [ ACC ]     STREAM     LISTENING     28446    973/systemd          /run/user/1000/pulse/native
```
Not much difference. This system doesn't have any client.conf file overrides.

I'd just use ufw.
Setup ufw to block access by default, except for ssh.
```
  $ sudo ufw enable
  $ sudo ufw default deny
  $ sudo ufw limit 22/tcp
```
If you need to allow other access the general format is:
```
  $ sudo ufw allow from {IP_SUB/net} to any port 22 proto tcp
```
If you wanted, you could allow all connections on your LAN, for example.

I should mention, I disable all IPv6 support on all my systems in the kernel boot options.

---

### Post by mollat on 2021-02-08
> **TheFu said:**
> 

[/CODE]
With pulse, I've only changed the ~/.config/pulse/client.conf file to add 1 line:
```
enable-shm = no
```


I don't know why (I don't understand the short documentation) - but this does the trick. No more open ports from pulse.

Thanks!

---

