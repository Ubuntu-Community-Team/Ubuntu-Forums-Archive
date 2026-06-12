---
title: "sudo tcpdump port 25"
date: 2007-08-17
forum: Server Platforms
---

### Post by nlbs on 2007-08-17
I was trying the see the trafic on SMTP port 25 of my local PC
first I did ```
sudo tcpdump port 25
``` and then sent a mail using the local SMTP server to my local server . But I saw nothing in the shell Just ```
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

```How can see the commands sent to the SMTP server ??

---

### Post by a9k on 2007-08-17
By default tcpdump selects the lowest number interface in a list it generates.
To see that list type the following in a terminal:
```
sudo tcpdump -D
```

If you have a recent tcpdump version, there should be an interface called [COLOR="Blue"]any[/COLOR]. Then you can use that or another interface in the list to specify the interface you want to listen on. If you don't have [COLOR="Blue"]any[/COLOR] you might try listening to the loopback [127.0.0.1] port [COLOR="Blue"]lo[/COLOR], especially if you are doing your testing by sending mail to l[COLOR="Blue"]ocalhost[/COLOR].
```
sudo tcpdump -i any port 25 # to listen to all interfaces
sudo tcpdump -i lo port 25 # to listen to the the loopback port
```

The reason tcpdump reported errors on your attempt because the eth0 interface had no ip address assigned to it at that time. You can display interface configuration with the **ifconfig** command.

---

### Post by nlbs on 2007-08-17
Thanks 
sudo tcpdump -i lo port 25
solved
But the output is not in human readable format like Wireshark or etharal.
Is it possible to make tcpdump's Output as human readable as wireshark ??

---

### Post by dreadlord_chris on 2007-08-17
> **nlbs said:**
> Thanks 
sudo tcpdump -i lo port 25
solved
But the output is not in human readable format like Wireshark or etharal.
Is it possible to make tcpdump's Output as human readable as wireshark ??

Actually, I'm sure that you can just open the dump with Wireshark, et al...

so...

```

sudo tcpdump -w port25.dump -i lo port 25

```
the **-w**, as you can probably tell, instructs tcpdump to send the output to the file listed after it.

You can then open the resulting file in your favorite analyzer, they pretty much all support the tcpdump format - it's kinda the standard.....

btw...
```

man tcpdump

```
is your friend :guitar:

---

