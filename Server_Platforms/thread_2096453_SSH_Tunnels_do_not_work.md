---
title: "SSH Tunnels do not work"
date: 2012-12-20
forum: Server Platforms
---

### Post by shoaibi on 2012-12-20
_**Resolved**_
The command should have been:
```

laptop# ssh -CTnN -o 'ServerAliveInterval 60' -o 'ServerAliveCountMax 3' -i ~/.ssh/keys/special.key -R 80:localhost:80 root@vps.domain.com

```

I have setup a ssh tunnel between my laptop and a remote server to forward my laptop's port 80 to remote server's 80.

Laptop's apache is running and listening on 0.0.0.0:80(though in this case listen address doesn't matter as apache would always get requests from local ip, unless i am mistaken), and apache is configured to "Allow from all" against "Location /" with no access overrides within any vhost. Only default vhost is enabled.


I have been trying to access apache using remote server's domain(using IP causes same effect) but it keep loading forever. Remote server's firewall does allow port 80. Laptop's apache log level is set to debug everywhere and no log files are updated. I did restart apache on laptop multiple times. On remote server telnet to localhost:80 also hangs for hours on "GET /". Same issue is observed by using elinks on remote server to browse to localhost.

Following is the ssh command that i used to create a tunnel.

```
laptop# ssh -CTnN -o 'ServerAliveInterval 60' -o 'ServerAliveCountMax 3' -i ~/.ssh/keys/special.key -R 80:vps.domain.com:80 root@vps.domain.com

```

A netstat -ntlpe on remote server shows port 80 listening against sshd process so tunnel did establish. Traceroute to remote server's ip on my laptop goes upto hop 16 and ends on an ip thats not anywhere near remote server's.

Here is tcpdump from my laptop against ip of remote server: 
```


2012-12-19 10:52:06.620666 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [S], seq 211937063, win 14600, options [mss 1460,sackOK,TS val 20534223 ecr 0,nop,wscale 7], length 0
_k.j.P...'......9.j..........
.9S.........
2012-12-19 10:52:06.687570 IP my.laptop.ip.here.52075 > remote.server.ip.here.80: Flags [S], seq 738946054, win 14600, options [mss 1460,sackOK,TS val 20534239 ecr 0,nop,wscale 7], length 0
_k.k.P,.l.......9.j..........
.9S.........
2012-12-19 10:52:06.960585 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [S.], seq 1519925057, ack 211937064, win 5792, options [mss 1460,sackOK,TS val 629826377 ecr 20534223,nop,wscale 5], length 0
_k...h.P.jZ.7A...(...............
%.cI.9S.....
2012-12-19 10:52:06.960653 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [.], ack 1519925058, win 115, options [nop,nop,TS val 20534308 ecr 629826377], length 0
_k.j.P...(Z.7B...sj......
.9T$%.cI
2012-12-19 10:52:06.961036 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [P.], seq 211937064:211937473, ack 1519925058, win 115, options [nop,nop,TS val 20534308 ecr 629826377], length 409
_k.j.P...(Z.7B...s
......
.9T$%.cIGET / HTTP/1.1
Host: vps.domain.com
Connection: keep-alive
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.4 (KHTML, like Gecko) Ubuntu/12.10 Chromium/22.0.1229.94 Chrome/22.0.1229.94 Safari/537.4
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Encoding: gzip,deflate,sdch
Accept-Language: en-US,en;q=0.8
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3


2012-12-19 10:52:07.026526 IP remote.server.ip.here.80 > my.laptop.ip.here.52075: Flags [S.], seq 1531199532, ack 738946055, win 5792, options [mss 1460,sackOK,TS val 629826384 ecr 20534239,nop,wscale 5], length 0
_k...h.P.k[D@,,.l................
%.cP.9S.....
2012-12-19 10:52:07.026591 IP my.laptop.ip.here.52075 > remote.server.ip.here.80: Flags [.], ack 1531199533, win 115, options [nop,nop,TS val 20534324 ecr 629826384], length 0
_k.k.P,.l.[D@-...sj......
.9T4%.cP
2012-12-19 10:52:07.307126 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [.], ack 211937473, win 215, options [nop,nop,TS val 629826411 ecr 20534308], length 0
_k...h.P.jZ.7B...............
%.ck.9T$
2012-12-19 10:52:20.805787 IP my.laptop.ip.here.52075 > remote.server.ip.here.80: Flags [F.], seq 738946055, ack 1531199533, win 115, options [nop,nop,TS val 20537769 ecr 629826384], length 0
_k.k.P,.l.[D@-...sj......
.9a.%.cP
2012-12-19 10:52:21.144800 IP remote.server.ip.here.80 > my.laptop.ip.here.52075: Flags [.], ack 738946056, win 181, options [nop,nop,TS val 629827796 ecr 20537769], length 0
_k...h.P.k[D@-,.l............
%.h..9a.
2012-12-19 10:52:52.304507 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [.], ack 1519925058, win 115, options [nop,nop,TS val 20545644 ecr 629826411], length 0
_k.j.P....Z.7B...sj......
.9.l%.ck
2012-12-19 10:52:52.642459 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [.], ack 211937473, win 215, options [nop,nop,TS val 629830945 ecr 20534308], length 0
_k...h.P.jZ.7B.........\.....
%.u!.9T$
2012-12-19 10:53:37.640507 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [.], ack 1519925058, win 115, options [nop,nop,TS val 20556978 ecr 629830945], length 0
_k.j.P....Z.7B...sj......
.9..%.u!
2012-12-19 10:53:37.978320 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [.], ack 211937473, win 215, options [nop,nop,TS val 629835480 ecr 20534308], length 0
_k...h.P.jZ.7B...............
%....9T$
2012-12-19 10:54:22.976463 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [.], ack 1519925058, win 115, options [nop,nop,TS val 20568312 ecr 629835480], length 0
_k.j.P....Z.7B...sj......
.9..%...
2012-12-19 10:54:23.314761 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [.], ack 211937473, win 215, options [nop,nop,TS val 629840014 ecr 20534308], length 0
_k...h.P.jZ.7B...............
%....9T$
2012-12-19 10:55:08.312465 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [.], ack 1519925058, win 115, options [nop,nop,TS val 20579646 ecr 629840014], length 0
_k.j.P....Z.7B...sj......
.:.>%...
2012-12-19 10:55:08.650399 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [.], ack 211937473, win 215, options [nop,nop,TS val 629844548 ecr 20534308], length 0
_k...h.P.jZ.7B.........9.....
%..D.9T$
2012-12-19 10:55:53.648490 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [.], ack 1519925058, win 115, options [nop,nop,TS val 20590980 ecr 629844548], length 0
_k.j.P....Z.7B...sj......
.:1.%..D
2012-12-19 10:55:53.986863 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [.], ack 211937473, win 215, options [nop,nop,TS val 629849082 ecr 20534308], length 0
_k...h.P.jZ.7B...............
%....9T$
2012-12-19 10:56:38.984510 IP my.laptop.ip.here.52074 > remote.server.ip.here.80: Flags [.], ack 1519925058, win 115, options [nop,nop,TS val 20602314 ecr 629849082], length 0
_k.j.P....Z.7B...sj......
.:].%...
2012-12-19 10:56:39.322298 IP remote.server.ip.here.80 > my.laptop.ip.here.52074: Flags [.], ack 211937473, win 215, options [nop,nop,TS val 629853616 ecr 20534308], length 0
_k...h.P.jZ.7B........o......

```


If i set my laptop as default virtual server on router, i could access my laptop's default vhost using dynamic dns hostname from anywhere, so it can't be apache.

I also tried a reverse tunnel:
```

remote-server# ssh -f root@my.laptop's.dynamic-dns.here -L 80:my.laptop's.dynamic-dns.here:80 -N

```
When i tried elinks on remote-server browsing to localhost worked this time by showing me the index.html i have in default vhost's docroot on my laptop. This also further confirms that issue is not with apache or a firewall config on my laptop network. However this isn't feasible solution because i would prefer to not open any ports on my router to dmz hosts.

I have tried forwarding other ports beside apache from my laptop to remote server and they all result in same behavior. Any ideas why?

---

