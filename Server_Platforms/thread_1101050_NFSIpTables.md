---
title: "NFS/IpTables"
date: 2009-03-19
forum: Server Platforms
---

### Post by cscomplab on 2009-03-19
we are trying to mount nfs file on our server which is running iptables, in iptables we have allow all protocols on input, forward, output.  when we try to mount from client, the serve times out.  we can ping our serve so we know the ip is correct.  what iptable rules do we need to allow NFS?

cheerio!

---

### Post by netztier on 2009-03-20
> **cscomplab said:**
> what iptable rules do we need to allow NFS?


Classic NFS (over UDP) uses RPC on tcp/udp 111 to negotiate the actual UDP port number to be used. If a firewall must support NFS-over-UDP, it must inspect the RPC communication and adapt dynamically.

Easier: switch to NFS-over-TCP (on the client, set the mount option "proto=tcp") and open tcp/2049 on the firewall. 


regards

Marc

---

### Post by cscomplab on 2009-04-02
Thank you for replying.  We're sure you're reply is very helpful but it's a little over our heads.

We have this IpTable rule in all of these chains(input, forward, output):
accept all--anywhere anywhere

and in etc/fstab we have:
(IP of server:/home/share /home/mnt nfs nosuid,proto=tpc 0 0)

why isn't it working?  Is there any way we can check errors?

---

### Post by vpsville on 2009-04-03
It sounds like your firewall is completely disabled, so the problem lies elsewhere.

---

### Post by netztier on 2009-04-03
> **cscomplab said:**
> Thank you for replying.  We're sure you're reply is very helpful but it's a little over our heads.


Then let me rephrase:

NFS when used without special configuration will use UDP as transport protocol, but it does this on a UDP port you normally cannot know in advance. But if you want to run a firewall, you want to know which ports are used by the communications flowing across it.

So the NFS client and NFS server start an intial dialog on port (tcp or udp) 111 (a.k.a. "the portmapper") to tell each other the actual UDP ports to use for the NFS communication - and these ports might be almost anything between 1024 and 65535.

So if you want to run NFS-over-UDP through a firewall, you basically have two possibilites:

a) allow "all udp ports >1024" between NFS-server and NFS-client. Bluntly put, this pretty much defeats the purpose of the firewall, so you might just as well disable it.

b) give the firewall the intelligence to understand the RPC protocol, so it can observe the dialogue between NFS Server and NFS client: "oh, while talking RPC on udp/111, NFS-server and NFS-client have agreed to use udp/33567, so I'll open that port for these two systems (and leave all others closed)".

I am not really good at iptables, so I don't know if iptables has the features to support b), but there are firewall products on the market that do.

Hence my suggestion to use NFS-over-TCP instead. Here things get a lot easier, because there is no dynamic negotiation of ports. It will always use port tcp/2049. This makes firewall configuration rather straightforward.

> 
and in etc/fstab we have:
(IP of server:/home/share /home/mnt nfs nosuid,**proto=[COLOR="Red"]tpc[/COLOR]** 0 0)


[COLOR="Red"]tpc[/COLOR]? That should be [COLOR="Green"]**tcp**[/COLOR]. Typo in the posting or in the client's configuration file?


Now since your iptables seems to be "completely open", you'll need to check if the server is actually listening on the network interfaces..

On the server, perform these two commands and look for these lines. There might me multiple instances of rpc.mountd or rpc.statd, but at first, the ones with "2049" and the "portmap" ones are of interest:

```
user@server:/etc$ **sudo netstat -napu**                     
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
[COLOR="Red"]udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
[/COLOR]udp        0      0 0.0.0.0:651             0.0.0.0:*                           21675/rpc.statd
[COLOR="Red"]udp        0      0 0.0.0.0:111             0.0.0.0:*                           21514/portmap[/COLOR]
udp        0      0 0.0.0.0:57200           0.0.0.0:*                           21675/rpc.statd
udp        0      0 0.0.0.0:47607           0.0.0.0:*                           21843/rpc.mountd
...


user@server:/etc$ **sudo netstat -napt**
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
[COLOR="Red"]tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      - [/COLOR]              
tcp        0      0 0.0.0.0:34730           0.0.0.0:*               LISTEN      21675/rpc.statd
[COLOR="Red"]tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      21514/portmap[/COLOR]
tcp        0      0 0.0.0.0:46325           0.0.0.0:*               LISTEN      21843/rpc.mountd
...

```




regards

Marc


On a side note: Please do put [ CODE][/CODE ] tags around text excerpts from console or configration files (highlight the text and press the **#** button in the toolbar above the edit box), it makes it so much easier to read and spot in the text.

---

### Post by cscomplab on 2009-04-23
we ran the tests you told us to   here are our results:
r@server:/etc$ sudo netstat -napu                     
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
udp        0      0 179.47.7.2:137        0.0.0.0:*                           - 5255/nmbd              
udp        0      0 192.168.0.1:137         0.0.0.0:*                           5255/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           5255/nmbd
udp        0      0 179.47.7.2:138          0.0.0.0:*                           5255/nmbd
udp        0      0 192.168.0.1:138         0.0.0.0:* 
5255/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           - 5255/nmbd              
udp        0      0 0.0.0.0:67              0.0.0.0:*                           5327/dhcpd3
udp        0      0 0.0.0.0:111             0.0.0.0:* 
4539/portmap
...

user@server:/etc$ sudo netstat -napt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      -
5301/dovecot               
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      5301/dovecot
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4997/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN 5257/smbd
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      -
5301/dovecot               
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      5301/dovecot
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      4539/portmap
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN 5382/apache2
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -
5118/cupsd               
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      5074/postgres
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      5239/master
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN 5257/smbd
tcp6        0      0 :::22                  :::*                    LISTEN     
4879/sshd               
...
  sorry the lines got messed up.
what should we do next?

---

### Post by netztier on 2009-04-24
> **cscomplab said:**
> 
  sorry the lines got messed up.


They wouldn't if you'd put CODE tags around them, by highlighting the text with the mouse and klicking the **#** button in the toolbar above the edit box

> what should we do next?

The output suggests that there is no process listening on port tcp/2049 on your server, and we can see no **rpc.statd** nor **rpc.mountd**

I suspect that NFS is not installed properly on that machine, or the NFS server didn't find any relevant configuration in /etc/exports, so during startup, it didn't bother to start all subprocesses or it disabled itself entirely.

Try to stop/start the NFS deamon with:

```
user@server:~$ **sudo /etc/init.d/nfs-kernel-server restart**
```

And then have a look at the last 50 lines of the file /var/log/syslog with...

```
user@server:~$ **tail -50 /var/log/syslog**
```

... to see if the restarting NFS deamons complain about something going wrong.

regards

Marc

---

### Post by shade5 on 2009-04-24
Hello,

I am working on the same problem. But I might misunderstood something. If I got you right all you have to do is telling the mount client to use tcp and then connect to 2049? I searched the man page of mount for an option to do that but I did not find anything. Whats the cmd please?

Thanks.

---

### Post by netztier on 2009-04-24
> **shade5 said:**
>  Whats the cmd please?


the mount option is **proto=tcp**, so int /etc/fstab, you would just add

```
<server>:/<path>/<export> /<localpath>/<localmountpoint> rw,**[COLOR="Red"]proto=tcp[/COLOR]**,rsize=<value>,wsize=<value>  0 0

```

or manual shell command:

```
sudo mount -t nfs <server>:/<path>/<export /<localpath>/<localmountpoint> -o=rw,**[COLOR="Red"]proto=tcp[/COLOR]**,rsize=<value>,wsize=<value>
```

I don't know which man page you were looking at, but in **man nfs**, we find:

```
**Valid options for the nfs file system type**
       Use these options, along with the options in the above subsection, for mounting the **nfs** file system type.

       [COLOR="Red"]**proto**=_netid_    The  transport  protocol  used  by  the NFS client to transmit requests to the NFS server for this mount point.  _netid_ can be
                      either **udp** or **tcp**.  Each transport protocol uses different default **retrans** and **timeo** settings; refer to  the  description  of
                      these two mount options for details.
[/COLOR]
                      In  addition  to  controlling  how  the  NFS client transmits requests to the server, this mount option also controls how the
                      **mount**(8) command communicates with the server’s rpcbind and mountd services.  Specifying **proto=tcp** forces  all  traffic  from
                      the **mount**(8) command and the NFS client to use TCP.  Specifying **proto=udp** forces all traffic types to use UDP.
```


regards

Marc

---

### Post by shade5 on 2009-04-24
```
sudo mount -t nfs <server>:/<path>/<export /<localpath>/<localmountpoint> -o=rw,proto=tcp,rsize=<value>,wsize=<value>
```

I tried it, it seems to be tcp only but I dont know how to use a specified port. 

Btw I was searching in the mount man not the nfs man thats why I did not find anything.

---

### Post by netztier on 2009-04-24
> **shade5 said:**
> 
I tried it, it seems to be tcp only but I dont know how to use a specified port.

Ah.. you want to change the tcp port that's being used for NFS?

er .. now I'm stumped. I have no clue... you'll need to dig deeper for that. I took a glance at /etc/default/nfs-kernel-server, but in there, you can only specifiy the port for rpc.mountd.

Do you have a particular reason for not using tcp/2049 for that?

regards

Marc

---

### Post by shade5 on 2009-04-24
I just noticed that we might mean different things. The problem for me is the mount protocol. NFS itself always was static for me on port 2049. 

Actually 2049 is fine and I could use it. 

I also found a link that might work. But its in german. But according to your name it should be fine for you: [http://www.ubuntu-forum.de/artikel/18361/gel%C3%B6st-nfs-und-port-638-firewall.html](http://www.ubuntu-forum.de/artikel/18361/gel%C3%B6st-nfs-und-port-638-firewall.html) 

I am trying this right now. Ill post my results then. 


I also found on this site:

[http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Deployment_Guide-en-US/s1-nfs-client-config-options.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Deployment_Guide-en-US/s1-nfs-client-config-options.html)

this description:

port=num — Specifies the numeric value of the NFS server port. If num is 0 (the default), then mount queries the remote host's portmapper for the port number to use. If the remote host's NFS daemon is not registered with its portmapper, the standard NFS port number of TCP 2049 is used instead.

That sounds like you have to unregister the NFS demon first. However my NFS is running on 2049 already. It might still be interesting.

---

### Post by netztier on 2009-04-24
> **shade5 said:**
> 

I also found a link that might work. But its in german. But according to your name it should be fine for you: [http://www.ubuntu-forum.de/artikel/18361/gel%C3%B6st-nfs-und-port-638-firewall.html](http://www.ubuntu-forum.de/artikel/18361/gel%C3%B6st-nfs-und-port-638-firewall.html) 

Why yes, german is my first foreign language (if you knew how archaic my native dialect sounds,  you'd easily imagine why german still is foreign language to many of my fellow country(wo)men ;-) ). 

I see, and I do like the info I found in there, thanks a lot for the hint. I always wondered why some of the NFS related deamons had to work with source port numbers below 1023. I know some firewall admins who are not always fond of such behaviour. 

In an IT environment where security and operational stability is an important issue, running NFS (or Samba/CIFS) across a firewall is not considered good practice, and is often sneered at by the security officers or forbidden by the policies they impose. Yet, there are use cases where you can't avoid it. Now at least I have some means to force NFS to predictable behaviour in terms of port selection :-)

There is a URL in  /etc/default/nfs-kernel-server and /etc/default/nfs-common: [http://wiki.debian.org/?SecuringNFS](http://wiki.debian.org/?SecuringNFS), but it's wrong, it should be:

[http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)

And it is a very nice and short document explaining what to do to nail-down the ports for the NFS deamons.

regards

Marc

---

### Post by shade5 on 2009-04-25
To explain that link I posted for those who did not understand or could not read, its basically just configuring these files like this:

```
/etc/default/nfs-common

# Options for rpc.statd.
# Should rpc.statd listen on a specific port? This is especially useful
# when you have a port-based firewall. To use a fixed port, set this
# this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
# For more information, see rpc.statd(8) or http://wiki.debian.org/SecuringN$
STATDOPTS="--port 4000 --outgoing-port 4001"
```

```
/etc/default/nfs-kernel-server

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
RPCMOUNTDOPTS="--port 4002"
```

Then you should restart. Now mount with the cmd Netztier gave. However there is still a problem for me now. I configured two computers but one is using port 4002 and one is using 2049. I was getting similar problems, too. Maybe it is a bug. I just recommend restarting. 

@ Threadstarter maybe you should reinstall nfs. Get nfs-common and nfs-server-kernel from the SPM. 

Btw thanks for fixing the URL.

---

