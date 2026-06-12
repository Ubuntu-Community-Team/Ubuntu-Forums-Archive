---
title: "Guest accessible, host not"
date: 2017-03-01
forum: Virtualisation
---

### Post by theredspecial on 2017-03-01
I'm at a loss regarding my Ubuntu Server 16.04 setup.

I'm running an Ubuntu Server 16.04 (headless) host with a kvm guest - also running that same Ubuntu Server 16.04. The host is not running many applications (NFS, Webmin and SSH are the only main packages I've installed), the guest is running Webmin, SSH and MPD so far.
I'm able to access my guest through SSH and Wembin, but not the host. Both are assigned their fixed IPs by the home router. 
```
sudo ifconfig
``` shows the expected IP addresses on both (when logging in locally on the host).
```
ssh myname@host-ip results in ssh: connect to host-ip port 22: connection time out
```

When looking for the NFS exports of the host on the guest, they don't show up.

I'm not sure what to look for and particularly not what to look for when trying to connect over ssh or how to ensure how I can connect to the host. Any tips?

---

### Post by dajavex71 on 2017-03-01
Are you able to Ping your host - externally from another machine or from within the kvm?
is ufw enabled on host, 
> sudo ufw status

was ssh on the host, setup to use a different port?

---

### Post by theredspecial on 2017-03-05
Hi, it took a while for me to find the time again...:(
Yes, I can ping the host and am getting good results.
```
sudo ufw status
``` shows ```
Status: inactive
```

SSH is operating at port 22.

(I am still setting up my environment, so I was planning to add security layers once the stuff works)

---

### Post by KillerKelvUK on 2017-03-05
Have you listed the listening ports on the host verify the processes are in fact working as opposed to just how they are configured?

```
sudo netstat -tulpn
```

for example?

---

### Post by theredspecial on 2017-03-05
Hi,

netstat shows many ports open, often like so:
```
0.0.0.0:10000
```
10000 and 22 for Webmin and SSH are listed as well.

I've noticed that sometimes it does work, after rebooting and sometimes not.
So, I'll have to dive into the boot messages I suppose.

---

### Post by KillerKelvUK on 2017-03-05
If you have listening sockets then what's your reason for thinking the problem is with the host and not upstream in the local networking layer?  You mention your home router is assigning fixed IP's are they in the same subnet etc?

---

### Post by theredspecial on 2017-03-05
I'm thinking so coz I'm not that much of an expert... this is the thing that comes to mind :/. And because sometimes it does works... when the only difference is restarting the server.
Yes, my home router puts all devices on the same subnet I believe.

---

