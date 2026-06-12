---
title: "proftpd 1.3.1 stopped working"
date: 2008-11-24
forum: Server Platforms
---

### Post by the-bna on 2008-11-24
I've had proftpd 1.3.1 running for a couple of months, and it has worked just fine. Now - all of a sudden - it has stopped working. I have changed nothing, and have tried rebooting the machine, and stopping/starting the process, but it just won't work.

The client seems to be able to connect after a while, but it cannot retrieve any information at all - cannot browse the file structure, put or get any files.

This problem has started spontaneously, so I'm hoping maybe there's a simple fix.

I'm not really good with linux, so please consider that too.

Thanks

---

### Post by pdwerryhouse on 2008-11-24
Have there been any networking changes between the server and the client that you are talking to it from? Firewalling, perhaps?

If it connects but can't transfer files, it sounds to me like the ftp server isn't able to create the channel that it passes data back along.

---

### Post by the-bna on 2008-11-25
I wouldn't think anything has changed. It's on slicehost. I have changed nothing.

When I try to connect via passive mode, the log says to check PassivePorts and MasqueradeAdress. Some of the times it says Refused EPRT, adress mismatch. Not all the times though.

In active mode it just connects, and basically times out and closes the session. Client side it feels like the same response as passive though.

If I were to open the passive ports, how do I do that without creating a massive hole in the firewall?

Again, it used to work. Now, all of a sudden, it doesn't. The web server still works, and it serves immediately. Most of all I would like to be running secure ftp, but I couldn't even get it to connect on that.

---

### Post by pdwerryhouse on 2008-11-25
I think your best bet here is going to be via looking at the logs. Change proftpd's configuration to do verbose logging, if it can, and then see what it says when you connect and try to transfer files.

You might also try running tcpdump on the network interface to see what traffic is going through it at each stage.

Finally, with regard to sftp - if ssh can work, then sftp should be able to work too, since it uses the same network protocol and port. Might be work checking the /etc/ssh/sshd_config file to see if there is something misconfigured.

---

