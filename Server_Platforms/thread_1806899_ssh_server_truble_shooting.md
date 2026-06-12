---
title: "ssh server truble shooting"
date: 2011-07-18
forum: Server Platforms
---

### Post by archro on 2011-07-18
Hello all,

I was installed an ubuntu server 11.04 32bit system, right now I was stucked by a ssh service issue.

I was install the open-ssh server on this server, and it's running. because I can see it by ps -ef |grep ssh,  this is a sshd process.
and I can ssh from the server self by ssh   xxx@localost.

but I can't ssh this server from a client. the client  always show no response. 

I was checked no iptables service, the ufw status is inactive. 

added: sshd:ALL in the hosts.allow file 

is there any other firewall program block the ssh request?

I was googled this but not luckly. 
any idera about this issue.

all help will be appreciate.

---

### Post by Wayne_V on 2011-07-18
what is the output of:

# lsof -i :22
# ifconfig -a

can you ping the system from the other node?

if the other system is linux as well try:

# nmap <ip of problem system>

and try the nmap from the problem system as well:

# nmap <ip of problem system>

if you don't already have lsof and nmap installed they are in the repository:

# apt-get install lsof nmap

---

### Post by archro on 2011-07-18
thank you for your replay,

lsof -i :22

sshd  1254 root  3r IPv4 9060 0t0 TCP *:ssh (LISTEN)    looks good

ifconfig -a

eth0   192.168.1.60

yes I can ping each other from both client and server.

the client is a win7 and running putty on it.

is there any special request for the putty?
 i can use the default setting for putty and ssh to a freeNAS machine.

I will try to run another ubuntu to check it, maybe  i can get more information.

BTW, apt-get install nmap:

unable to locate package nmap.

---

### Post by Wayne_V on 2011-07-18
interesting ... nmap should be in the main 11.04 repo:  [http://www.ubuntuupdates.org/packages/show/266630](http://www.ubuntuupdates.org/packages/show/266630)

does 'apt-cache search nmap' find it?

from the windows box try "telnet 192.168.1.60 22" and see if you get any response.

---

### Post by collisionystm on 2011-07-18
What are you using for the client machine? Windows? Linux?

What program are you using to connect to your server

---

