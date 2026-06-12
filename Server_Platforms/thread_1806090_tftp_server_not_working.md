---
title: "tftp server not working"
date: 2011-07-17
forum: Server Platforms
---

### Post by s7nf on 2011-07-17
Hello guys!

I have big problems with getting tftp server to work. Yesterday I was trying with tftpd, today i'm trying with **atftp**:

I configured it by this HOW-TO: [http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html)

Im testing this on my local network, on the same computer. Im trying to get files from /tftpboot to /home/user/tftpreceive

so in my /etc/default/atftp is :

```
USE_INETD=false
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /srv/tftp"
```

then I made /tftpboot directory, for which *ls -l* gives ```
drwxrwxrwx   2 nobody root  4096 2011-07-17 09:41 tftpboot

```

inside I made hda.txt for which *ls -l* gives ```
-rwxrwxrwx 1 nobody root 0 2011-07-15 13:21 hda.txt
```

then I start the client atftp with command: *atftp localhost*
and then: *get hda.txt*
which results in  *can't open hda.txt for writing* if my working dir is owned by nobody or root, if it is owned by me then I just get *timeout: retrying *


*netstat -a | grep tftp* gives 
```
udp        0      0 *:tftp                  *:*  
```

and there are visible tftp requests in wireshark.

and im using ubuntu 10.10

---

### Post by Lars Noodén on 2011-07-17
Depending on how you are planning to use TFTP, you might wish to use the one built into dnsmasq.  It is set up by changing only two or three lines in the configuration file.

---

### Post by s7nf on 2011-07-17
I need it to transfer configuration file to router.
I dont think i need dnsmasq for this. But maybe i'm wrong, as I'm not using linux systems for a long time.

---

### Post by Lars Noodén on 2011-07-17
Dnsmasq is a DNS forwarder/cacher, DHCP and TFTP server.  You might not need the DNS or DHCP and might use it only for TFTP.  It might be faster to set up than debugging other TFTP servers.

---

### Post by s7nf on 2011-07-17
If everything else fails, I will try it, but first I want to figure out how to do it with either atftp or tftpd

---

### Post by HermanAB on 2011-07-17
Note that TFTPD will only work if the data directory and the files in it are marked Read Only.  It is the only security that TFTP has, so it will refuse to work otherwise.

---

### Post by s7nf on 2011-07-17
Thank you HermanAB, my weren't read only. 

As for atftp, i found my mistake. The tftp folder was all the time /srv/tftp and not /tftpboot

---

### Post by HermanAB on 2011-07-17
You are welcome.  Many moons ago, I banged my head on the wall for a looooong time before I figured that out...

---

