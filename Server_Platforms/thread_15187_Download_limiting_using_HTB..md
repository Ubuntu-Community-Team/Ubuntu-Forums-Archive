---
title: "Download limiting using HTB."
date: 2005-02-12
forum: Server Platforms
---

### Post by tvlad on 2005-02-12
This is the script i've made to control downloads.

# RESET QUEUES
tc qdisc del dev eth0 root
tc qdisc del dev eth0 ingress

#CREATE QUEUES
tc qdisc add dev eth0 parent root handle 1:0 htb default 20
tc class add dev eth0 parent 1:0 classid 1:1 htb rate 256kbit

tc class add dev eth0 parent 1:1 classid 1:10 htb rate 48kbit ceil 256Kbit prio 2
tc class add dev eth0 parent 1:1 classid 1:20 htb rate 48kbit ceil 256Kbit prio 2
tc class add dev eth0 parent 1:1 classid 1:30 htb rate 48kbit ceil 256Kbit prio 2
tc class add dev eth0 parent 1:1 classid 1:40 htb rate 128kbit ceil 256Kbit prio 1
tc class add dev eth0 parent 1:1 classid 1:50 htb rate 128kbit ceil 256Kbit prio 0

#ATTACH QDISCS TO QUEUES
tc qdisc add dev eth0 parent 1:10 handle 10: sfq perturb 10
tc qdisc add dev eth0 parent 1:20 handle 20: sfq perturb 10
tc qdisc add dev eth0 parent 1:30 handle 30: sfq perturb 10
tc qdisc add dev eth0 parent 1:40 handle 40: sfq perturb 10
tc qdisc add dev eth0 parent 1:50 handle 50: sfq perturb 10

#CREATE FILTERS TO DETERMINE TO WHICH CUE EACH PACKET GOES
tc filter add dev eth0 parent 1:0 protocol ip prio 0 handle 10 fw classid 1:10
tc filter add dev eth0 parent 1:0 protocol ip prio 0 handle 20 fw classid 1:20
tc filter add dev eth0 parent 1:0 protocol ip prio 0 handle 30 fw classid 1:30
tc filter add dev eth0 parent 1:0 protocol ip prio 0 handle 40 fw classid 1:40
tc filter add dev eth0 parent 1:0 protocol ip prio 0 handle 50 fw classid 1:50 

How can i associate the rules to a MAC ADDRESS, i know how to do it for an ip, but i would like to know if i can mark the packets using the mac address, that way i stand a better chance of the limitation to work, fewer people know of macs than ip.

---

### Post by meyerm on 2005-02-15
To be honest, I don't know HTB good enough to answer your question directly. But you should have a look at an arpwatch daemon. It associates IPs with MACs and can complain or even take actions if an unknown combination occurs at your gateway.

hth
Marcel

---

### Post by devious1 on 2007-03-02
I too have been tring out different cms packages from what I read scms seems to be nice but I got confused. I am planning on streaming alot of video,music, and video chat. swf's, and flv's surely make things easier mp4 is also a good video format look for cms that support these qualities. So far I'm sticking with joomla. got every mod you can think of. Solution I came up with was to try running my own server for my files. for my flash chat I'm planning on installing flash server it's free from adobe. Hope I can integrate with ubuntu. I Got alot to learn. I hope this helped out a lil bit.hit me and lemme know what you find.Hopefully you'll find something I haven't tried yet. oh, alot has been said about flashblocks (not free)

---

### Post by cypresstwist on 2008-06-16
Now, with [WebHTB]("http://www.mylro.org/content/view/929/57/") you can apply rules and do trafic shaping as you please, through a cool-looking AJAX-based web interface. Adding and deleting clients can be done in just a few clicks. Trafic shaping can be done with both public and private IP addresses.

---

