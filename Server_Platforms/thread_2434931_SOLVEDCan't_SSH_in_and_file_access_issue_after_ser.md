---
title: "SOLVED:Can't SSH in and file access issue after server name change"
date: 2020-01-13
forum: Server Platforms
---

### Post by linuxnoob87 on 2020-01-13
All,

I renamed my ubuntu server (18.04.3) that runs plex (which is running in ESXi). After doing so (by manually editing the /etc/hosts and /etc/hostname files) I am no longer able to SSH into the server and have tried from two different computers. Sometimes I can connect to the server briefly before it disconnects me with the error: "dpacket_write_wait: Connection to 192.168.1.131 port 22: Broken pipe" When I briefly connect it tells me that there are updates that need to be run, however, if I connect from the console itself (and log in) it shows that there aren't any updates.

In addition to not being able to SSH in, I am not able to play back any content from within Plex. I can confirm that the folders have mounted correctly and I can browse to the files directly; when I try to playback a file in Plex I get an error that the file cannot be found. This is occurring on both a web browser and a Roku stick.

Neither of these issues started until I attempted to rename the computer. Since then, I've reverted the name change but the above two problem persists.

Any ideas as to why this is occurring?

TIA!

---

### Post by darkod on 2020-01-13
The name of the server should not be relevant for ssh. I have done a rename many times...

1. How are you accessing it, by name (dns) or by IP?

2. Try using ssh in verbose mode, something like ssh -vv user@server, it should give you more log details and maybe point you why it fails.

3. Did you keep the same network settings and IP when renaming?

---

### Post by linuxnoob87 on 2020-01-13
1. By DNS name. When that failed also tried via IP. Both produce the same results.

2. The first two times I tried to connect I recieved the error "Connection reset by 172.16.249.131 port 22". The third time I connected and was disconnected fairly quickly with "packet_write_wait: Connection to 192.168.1.131 port 22: Broken pipe"

3. Yes and I did not modify any of the files pertaining to the static IP.

---

### Post by darkod on 2020-01-13
Why does the error message mention two different IPs? What is the 172 and what is the 192 IP?

If you access it by dns name I assume you manually adjusted the A record in dns if that was needed. Usually linux servers do not autoregister in dns, depending on setup.

This could also be related to vmware configuration.

Are you accessing by ssh key or password?

---

### Post by linuxnoob87 on 2020-01-13
Ok, solved. And it's due to a STUPID problem on my part.

Short version; I recently migrated this server from one ESXi host to another. During the migration I powered down the machine and didn't delete it from the ESXi host. I recently had to power that server back on. In doing so, it brought up the duplicate server.

This lead to two servers with the same IP address being up on the network at the same time.

---

### Post by darkod on 2020-01-13
Great. Please mark the thread solved then. You can do that in Thread Tools above the first post.

---

