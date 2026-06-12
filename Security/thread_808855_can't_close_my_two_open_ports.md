---
title: "can't close my two open ports"
date: 2008-05-26
forum: Security
---

### Post by zornan on 2008-05-26
I am new to linux security and have been doing some reading to fortify my linux box. Using nmap I found i have only two open ports of the 65535 ports i scanned. I want to disable them, but can't find them in the services list or even by using sysvconfig. The first service is H.323/Q.931. Some Googeling told me that this service is used for VOIP which I don't have a use for. How do I disable this service thereby closing this port? 

The second service is iss-realsecure-sensor. I can't find much useful info on this service, and i can't find it listed anywhere for me to disable in sysvconfig. Can you tell me what this service is, and how to disable it if i so choose?

any help you can offer would be greatly appreciated.

---

### Post by cdenley on 2008-05-27
Are you scanning your computer, or your router? You can check what ports your computer is listening on with this command
```

netstat -tln

```

---

### Post by zornan on 2008-05-27
I scanned my computer's IP with nmap from another computer within my network. There is no router between them. Unless i missed it, netstat doesn't tell me what services are using the open ports. The two services i listed are keeping two ports open. I just need to know how to disable them since i can't find them listed in the services list.

---

### Post by cdenley on 2008-05-27
I was just making sure you were scanning correctly. I figured since you don't seem to remember installing voip software, and many routers have built-in voip functionality, you must have been scanning your router. However, if that is not the case, this command should indicate what process is listening on that port.
```

sudo lsof -i :22

```
Replace 22 with the appropriate port number.

My computer gives me this output
```

COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
sshd    5899 root    3u  IPv6  14081       TCP *:22 (LISTEN)

```
which shows sshd is listening on port 22. A search of my installed packages shows which package installed that service.
```

cdenley@ubuntu:~$ dpkg-query -S sshd
openssh-server: /usr/sbin/sshd
openssh-server: /usr/share/man/man8/sshd.8.gz
openssh-server: /var/run/sshd
openssh-server: /etc/pam.d/sshd
openssh-server: /usr/share/man/man5/sshd_config.5.gz

```
If I don't want that server anymore, I can remove it
```

sudo apt-get remove openssh-server

```

---

### Post by niteshifter on 2008-05-27
Hi,

netstat is your friend:
```
sudo netstat -tulnp
```

will give you TCP, UDP and PID/Program name.

---

### Post by zornan on 2008-05-27
wonderful! exactly what i was looking for! Thank you both. I've learned to love the openness and customability of linux for the past year or so that I have been working with it. With linux security, i'm really learning both networking and linux security at the same time.. there is so much to learn.. but I like computers and there is no way I am going back to windows.. Once microsoft drops support for XP, my wife will be converting to Linux also, though she does not know this yet ;)  Anyway, thanks for your help!

---

