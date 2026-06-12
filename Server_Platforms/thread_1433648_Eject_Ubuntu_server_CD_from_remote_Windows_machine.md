---
title: "Eject Ubuntu server CD from remote Windows machine?"
date: 2010-03-19
forum: Server Platforms
---

### Post by mlfrancis on 2010-03-19
Hello All, 
How can I eject a Ubuntu server's CD/DVD that is shared over samba from a networked Windows machine?

I've Googled and searched and still don't have a solution. 

My wife's new laptop does not have a CD/DVD drive.  The only thing she needs one for is installing stuff so I shared our home server (Ubuntu server) cd/dvd drive.  All works fine until we need to switch disks.  At that point I have to ssh into the machine and eject the disk.

Is there anyway to eject the disk from her machine without installing ssh tools?  I figure if I install ssh tools on her machine I should be able to do a ssh remote command to eject the disk, but it seems there should be a way to do it without going through that hassle.

Any thoughts appreciated.

---

### Post by cdenley on 2010-03-19
> **mlfrancis said:**
> Is there anyway to eject the disk from her machine without installing ssh tools?  I figure if I install ssh tools on her machine I should be able to do a ssh remote command to eject the disk, but it seems there should be a way to do it without going through that hassle.

Putty does not require installation. I don't know of any way to remotely eject a disc without using a shell. Actually, I guess you can configure an inetd service to eject the disc when a TCP connection on a given port is established, but that would allow anyone with access to that port to eject the disc without authentication.

1. install xinetd
```

sudo apt-get install xinetd

```

2. create your service (/etc/xinetd.d/eject)
```

service telnet
{
protocol        = tcp
port            = 23
socket_type     = stream
wait            = no
user            = root
server          = /usr/bin/eject
server_args     = -v -T /dev/scd0
disable         = no
}

```

3. restart xinetd
```

sudo /etc/init.d/xinetd restart

```

4. eject from wherever
```

telnet myfileserver

```

---

### Post by mlfrancis on 2010-03-19
That's pretty unique.  Thanks!

---

