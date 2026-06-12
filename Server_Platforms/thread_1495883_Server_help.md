---
title: "Server help"
date: 2010-05-28
forum: Server Platforms
---

### Post by sgosnell on 2010-05-28
I decided to use my EEE-701 as a file server for my home network, since I wasn't using it for much of anything else, and it seems about perfect for that, with a USB HDD attached.  I installed 10.04 server edition, configured it according to the instructions in the sticky, and have had no luck in accessing it with any computer in my network.  I'm probably overlooking something obvious, but I'm at the point where I'm not seeing the forest for the trees, and I could use some help.  

The 701 is connected to my router via ethernet, and I have a good internet connection on it.  The router shows it connected, and I have the internal IP for it.  I can ssh to it, but I can't get to it any other way.  Either the configuration is wrong, or I'm accessing it incorrectly.  I've installed NFS, vsftpd, and everything else I think I need from the Ubuntu Server Guide, but I still can't get to the server from another PC.

---

### Post by lykwydchykyn on 2010-05-28
Are you running a firewall on it?  Maybe try installing nmap on your workstation and then run:
```

nmap server_ip

```
To see what ports are open on it.

nmap is in the repositories.

---

### Post by sgosnell on 2010-05-28
No, I don't see the need for a firewall.  It's behind my router, and only intended to serve the internal network computers, not be accessible from the internet.

In any case, nmap shows that ftp, ssh, rpcbind, netbios-ssn, ldap, microsoft-ds, and nfs ports are open.

---

### Post by lykwydchykyn on 2010-05-28
What do you get from running:
```

sudo netstat -tnap

```
on the server?

---

### Post by sgosnell on 2010-05-28
How do I copy from the Putty terminal?  There's a lot of stuff that comes up, and copy/paste is the only way to do it.  I can paste there fine, but I've never tried to copy.

---

### Post by sgosnell on 2010-05-28
OK, I figured it out.  I had to go dig out a mouse, because I never use one.

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1217/vsftpd
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1135/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1202/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1315/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1150/exim4
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      706/smbd
tcp        0      0 0.0.0.0:35935           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:38303           0.0.0.0:*               LISTEN      615/rpc.statd
tcp        0      0 0.0.0.0:41216           0.0.0.0:*               LISTEN      1261/rpc.mountd
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN      1980/slapd
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      706/smbd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      588/portmap
tcp        0      0 192.168.1.6:22          192.168.1.3:47427       ESTABLISHED 2023/sshd: administ
tcp6       0      0 :::22                   :::*                    LISTEN      1202/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      1315/cupsd
tcp6       0      0 ::1:25                  :::*                    LISTEN      1150/exim4
tcp6       0      0 :::389                  :::*                    LISTEN      1980/slapd

```

---

### Post by dtfinch on 2010-05-28
I'm leaning towards name resolution problems. Can you ping it by name, or just IP?

---

### Post by lykwydchykyn on 2010-05-28
I notice your sshd is listening on ip 192.168.1.6, while your dnsmasq is listening on 192.168.122.1.  Something doesn't seem right there; do you have this thing set up on multiple networks?

If you are not running a firewall on the server, you should get prompted for a login if you run this on the workstation:

```

ftp 192.168.1.6

```

What happens when you run that?

Try the nmap thing, it'd be good to know what the workstation is seeing now that we know what the server is seeing.

EDIT: nevermind, I see that you did that already.

---

### Post by sgosnell on 2010-05-28
I can ping it only by IP.

```
stan@stan-eee900:/$ ftp 192.168.1.6
Connected to 192.168.1.6.
500 OOPS: cannot locate user entry:ftpsecure

```

---

### Post by sgosnell on 2010-05-28
It's just on one network, and I don't know where the 192.168.122.1 came from.

---

### Post by sgosnell on 2010-05-28
Actually, when I ping it by name, I get a reply from openDNS.  It does seem to be a name resolution problem.  I need to look at that, I guess, but I'm not sure where to start.

---

### Post by CharlesA on 2010-05-28
Are you running a local DNS server? (looks like DNSMacq is running but I am not sure why it is listening on that ip address)

Sounds like it's trying to do a lookup via DNS.

As for copying text from Putty, try Ctrl + C.

---

### Post by sgosnell on 2010-05-28
Ctrl-C in the terminal kills the current operation.  I figured out the copy, it's just highlight what you want to copy, and then middle-click where you want to paste.  I finally remembered that a 3-finger tap on my touchpad is a middle-click.

I don't think I installed the DNS server software, but I'll check.

---

### Post by CharlesA on 2010-05-28
Ctrl + C will copy whatever is on the screen that's highlighted (and kill whatever is running, if anything).

Right click will paste. :)

---

### Post by sgosnell on 2010-05-28
After more research, I found that the 192.168.122.0 was a virtual bridge, virbr0.  I must have inadvertently tagged the virtual server box on the install.  The virtual bridge was never configured.  Removing bridge-utils seems to have solved that, but I've made no other progress.  The latest output of the requested commands is below:
```
Starting Nmap 5.00 ( http://nmap.org ) at 2010-05-28 20:12 CDT
Interesting ports on 192.168.1.6:
Not shown: 993 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
389/tcp  open  ldap
445/tcp  open  microsoft-ds
2049/tcp open  nfs

```
```
administrator@server:~$ sudo netstat -tnap
[sudo] password for administrator:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      932/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      908/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1240/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1141/exim4
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      685/smbd
tcp        0      0 0.0.0.0:44958           0.0.0.0:*               LISTEN      1186/rpc.mountd
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN      822/slapd
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      685/smbd
tcp        0      0 0.0.0.0:43597           0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:36365           0.0.0.0:*               LISTEN      596/rpc.statd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      569/portmap
tcp        0      0 192.168.1.6:22          192.168.1.3:53496       ESTABLISHED 1463/sshd: administ
tcp6       0      0 :::22                   :::*                    LISTEN      908/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      1240/cupsd
tcp6       0      0 ::1:25                  :::*                    LISTEN      1141/exim4
tcp6       0      0 :::389                  :::*                    LISTEN      822/slapd

``````
stan@stan-eee900:~$ ftp 192.168.1.6
Connected to 192.168.1.6.
500 OOPS: cannot locate user entry:ftpsecure
ftp> 

```
Does anyone know of a good source for information on setting up a server?  The Ubuntu guide isn't that good, at least for me, and the one on HowToForge is flaky, with some very bad advice and a lot of typos.  I'd like to learn to do this, just for the experience, and maybe eventually set up a server to let me ftp my files from away from home, but that's way in the future.  Right now I'd like to just get a file server working on my home network.  It shouldn't be this difficult, but I'm finding it very tough going.

---

### Post by sgosnell on 2010-05-28
Some progress.  I can mount the HDD attached to the server on my Ubuntu laptop, using NFS.  That's convenient, like having the HDD on my computer.  But I still can't ftp to the server.  It's obviously a configuration problem in the vsftpd.conf, but I can't find it, and I'm tired of dealing with it tonight.  I'll try again later.  Thanks for the help so far.

---

### Post by CharlesA on 2010-05-28
Why not just use sftp instead of ftp, since you already have SSH installed?

---

### Post by sgosnell on 2010-05-28
That's not working either, probably because of my ignorance.  I would prefer to just use anonymous ftp, though, for convenience.  I don't really need security here, behind my router.  I'm comfortable with the security of the router.  I'll probably eventually go to either sftp or ftps if I put the server outside the router for access from the internet, but I'd rather ease into that gradually.

---

### Post by CharlesA on 2010-05-29
Are you getting any errors when trying to use SFTP?

It should work as long as you can SSH into the box.

I've used sftp on my server without needing to have a normal ftp server running.

---

### Post by sgosnell on 2010-05-29
```
Status:	Connecting to 192.168.1.6:21...
Status:	Connection established, waiting for welcome message...
Response:	500 OOPS: cannot locate user entry:ftpsecure
Error:	Critical error
Error:	Could not connect to server
```
I don't have keyfiles set up, don't know if that's required.  This has become a low priority due to other life events, and having NFS working on the server.  NFS is what I really wanted to establish, and it's working fine on both my Ubuntu machines and on my wife's Vista machine.  I doubt I'll need to use ftp until I move the server outside the network for access from the internet, and that won't be soon.

Thanks for the advice, you all helped get me going in the right direction.  The docs aren't that clear, but I have what I need working for now.

---

### Post by CharlesA on 2010-05-29
I'm not sure what's wrong. Did you chroot the ftp server?

What happens when you run this:

```
sftp user@host
```

---

### Post by krodrigue on 2010-05-30
In Ubuntu select Applications, then Ubuntu Software Center. Once the window opens in the top right you will see the search box, type samba there...you should see at the top of the list Samba...create, modify, and delete samba shares, install that program and it will allow you to share what ever you like on your network with ease.

---

### Post by Vishal Agarwal on 2010-05-30
> **sgosnell said:**
> ```
stan@stan-eee900:~$ ftp 192.168.1.6
Connected to 192.168.1.6.
500 OOPS: cannot locate user entry:ftpsecure
ftp> 

```

Have you installed any ftp server link vsftpd or proftp. if any one is installed then start it.

---

### Post by sgosnell on 2010-05-30
Samba is installed, vsftpd is installed, all are running.  I did get sftp to work from the command line, but not from Filezilla, and only by using the IP address, not the host alias.  Anonymous FTP still doesn't work, though.  I haven't really been working on it that much, since I'm just mounting the HDD on my other computers, which is really the best solution.  FTP is clunky at best, and while it is useful for transferring files between a remote server and a local machine, NFS is much more efficient.  I'll work on the anonymous FTP when I get more time, but I don't really need it that badly right now.  It's almost certainly a configuration problem on the server, but I haven't found a really good guide for that.

Thanks to everyone for the help, but I think I'll mark this one solved for now, because NFS works, and that's what I really wanted in the first place.  I'm still not certain exactly what I did to get it going, but it's working, and I'm liking it.

---

### Post by lykwydchykyn on 2010-05-30
If vsftp isn't working, there are several other ftp servers available with different features and levels of complexity.  Some have GUI configuration tools, and many can be configured with Webmin, if the config files aren't your cup of tea.

I normally use proftpd myself, though in some cases I've used pure-ftpd.

---

