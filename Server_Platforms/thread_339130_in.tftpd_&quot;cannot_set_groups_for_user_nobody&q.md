---
title: "in.tftpd: &quot;cannot set groups for user nobody&quot;"
date: 2007-01-15
forum: Server Platforms
---

### Post by xdcdx on 2007-01-15
Hello,

I'm trying to setup in.tftpd (tftpd-hpa) for net boot.

I am adding the following line to inetd

```
tftp dgram wait nobody /usr/sbin/tcpd in.tftpd /tftboot
```

When a machine tries to netboot, the dhcp part goes fine, but then in.tftpd gives the following error: in.tftpd: "cannot set groups for user nobody"

If I set tftpd to run as the root user in inetd, everything works fine, but I reckon this is a security risk.

I also tried the following lines in inetd, to no avail.

```
tftp dgram wait nobody.nogroup /usr/sbin/tcpd in.tftpd /tftboot
```
```
tftp dgram wait anotheruser /usr/sbin/tcpd in.tftpd /tftboot
```

I tried playing with the access permissions of /tftboot and the files therein. I even tried making /tftboot writable by everyone, but was of no use.

In all cases the error message is the same: in.tftpd: "cannot set groups for user nobody"

What else can I do? Is this possibly a in.tftpd bug?

---

### Post by happynix on 2007-12-20
tftpd NEEDS to run as root.

That is why you are getting that error message.
add 
   -u tftpuser and -s /somedirectorytftpusercanmesswith

to the end of your inetd.conf line for tftp

---

### Post by larytet on 2008-03-22
I am putting here a short TFTPD+INETD howto for Ubuntu 7.10 - the Gutsy Gibbon and probably other versions as well. This HOWTO is relevant for the clean systems, where no attempts were done to use xinetd. 

Step 1 - install components inetd, tftpd, tftp
```

sudo apt-get install inetutils-inetd 
sudo apt-get install tftpd tftp

```


Step 2 - configure INETD
Edit file /etc/inetd.conf. File should contain line
```

tftp            dgram   udp4    wait    nobody  /usr/sbin/tcpd  /usr/sbin/in.tftpd /tftpboot

```

Step 2.1 Important note.
All blanks/spaces between words are tabs. In the part "/usr/sbin/in.tftpd /tftpboot" this is a blank and not a TAB
Line in the /etc/inetd.conf means following. If a UDP4 packet arrives to this machine port tftp (69) execute command 
```

/usr/sbin/in.tftpd /tftpboot

```
under user nobody. In essence inetd runs /usr/sbin/in.tftpd

Step 3 - TFTP root directory
Create /tftpboot and set owner and mod
```

mkdir /tftpboot
sudo chown -R nobody.nogroup /tftpboot
sudo chmod -R 777 /tftpboot

```

Step 4 - restart INETD 
```

sudo /etc/init.d/inetutils-inetd restart

```


Step 5 - tests
Some tests can be done. Run tftp client and try to get a file from the TFTP server
```

tftp 192.168.1.12
get myfile

```

Check netstat output if there is a process listening on port 69
```

netstat -anp | grep ":69"

```

Check that tftpd and inetutils-inetd are running 
```

ps -ef | grep "inetd"
ps -ef | grep "tftpd"

```

---

