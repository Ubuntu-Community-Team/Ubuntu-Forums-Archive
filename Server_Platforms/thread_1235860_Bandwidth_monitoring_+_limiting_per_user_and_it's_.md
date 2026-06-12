---
title: "Bandwidth monitoring + limiting per user and it's processes"
date: 2009-08-09
forum: Server Platforms
---

### Post by loco41211 on 2009-08-09
To summarise:
I have a dedicated server with a few friends running a torrent client with web gui. Each user is running a client under their username on the server so downloads go in their user dir, and only they have access to their own files etc.

How can I monitor and limit the bandwidth per month on a per user basis?

I was thinking there must be a way using iptables maybe. And by monitoring the bandwidth used by all processes of user X. And if they have used more then their monthly allowed bandwidth of Y GB, they get a message saying that and networking gets blocked for their torrent client, or the client gets killed completely.

But I'm not sure how to do it...

would this be possible at all? I am grateful for even just partial solutions to this...

thanks in advance

---

### Post by billschu on 2009-09-19
I generated script using
[http://easyfwgen.morizot.net/gen/index.php](http://easyfwgen.morizot.net/gen/index.php)

to that I added

$IPT -I FORWARD 1 -j traffic_in
$IPT -I FORWARD 2 -j traffic_out
$IPT -A traffic_in -d 192.168.5.4
$IPT -A traffic_out -s 192.168.5.4
$IPT -A traffic_in -d 192.168.5.8
$IPT -A traffic_out -s 192.168.5.8
(above sample for only two users)

still working on optimizing a bandwidth per user solution but the above would at least let you monitor usage with 

sudo iptables -L traffic_in -vn
sudo iptables -L traffic_out -vn

you could script something to block IPs at your DHCP server if they went over limit

Cheers,

---

