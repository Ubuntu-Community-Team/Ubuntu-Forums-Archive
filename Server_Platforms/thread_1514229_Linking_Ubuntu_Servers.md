---
title: "Linking Ubuntu Servers"
date: 2010-06-20
forum: Server Platforms
---

### Post by dalitso on 2010-06-20
What is the easiest yet reliable way of linking ubuntu servers? Like in a scenario where branch servers need to link to head office server in services like samba shares or more.

---

### Post by kevin11951 on 2010-06-20
> **dalitso said:**
> What is the easiest yet reliable way of linking ubuntu servers? Like in a scenario where branch servers need to link to head office server in services like samba shares or more.

Research a "VPN"

---

### Post by HermanAB on 2010-06-21
NFS or Samba over an encrypted link (VPN).  Note that NFS is much more efficient than Samba and much easier to set up.  Windows also supports NFS (Services for UNIX is a free download from Microsoft):
[http://www.aeronetworks.ca/nfs-howto.html](http://www.aeronetworks.ca/nfs-howto.html)

---

### Post by dalitso on 2010-06-21
Thanks alot guys, I will check out those links.

---

### Post by dalitso on 2010-06-21
I setup openvpn following the documentation and it works

I have realized that mounting the folders of server 1 on server 2 via either samba or nfs results in those folders being unavailable once the internet connection is not available.

I mounted nfs this way ```
mount 192.168.1.20:/export/share /home/user/share
```
I was just testing so I didn't mount in /etc/fstab

Is there a way server 2 can still have the files in its folder /home/user/share/
even when the connection is absent?

---

### Post by tonyric on 2010-06-21
One thing to keep in mind if you decide to use NFS (not sure about samba)... DO NOT hard mount in a closed loop. In other words server1:/export1 mounted on server2:/mount1 and server2:export2 mounted on server1:/mount2

This will cause MAJOR issues on bootup if you attempt to mount them in /etc/fstab. Circular dependencies suck on bootup and shutdown.

---

### Post by BobVila on 2010-06-22
> **dalitso said:**
> I setup openvpn following the documentation and it works

I have realized that mounting the folders of server 1 on server 2 via either samba or nfs results in those folders being unavailable once the internet connection is not available.

I mounted nfs this way ```
mount 192.168.1.20:/export/share /home/user/share
```I was just testing so I didn't mount in /etc/fstab

Is there a way server 2 can still have the files in its folder /home/user/share/
even when the connection is absent?

If you want to MIRROR them, look into rsync. Standard samba and nfs mounts rely on an active connection to the file 'server'.

That said, maintaining an rsync (especially if users are editing files (ESPECIALLY the same files)), is going to be a pita.

---

### Post by dalitso on 2010-06-26
Thanks, I am going to use rsync

---

### Post by joeoshawa on 2010-07-01
I am probably hijacking a thread but I am at the end of my rope here. I do my research and do my best to help others but I rarely get a response on the forums and none have been helpful. Thank you for the attempt to the newbies like me who tried to help i do appreciate it.  I am trying to set up nfs my ubuntu 10.04 machine is the server and a kubuntu 9.4 machine is the one i am trying to access from. users id and id numbers are the same on both machines nfs is up and running on the server and all looks good on the server however i cannot see the server from the client.

rpcinfo -p 192.168.0.112
No remote programs registered.
jen@kimono:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  36263  status
    100024    1   tcp  52064  status
hosts.deny
portmap : ALL
hosts.allow
portmap : 192.168.0.112
hosts
127.0.0.1    localhost.localdomain    localhost
127.0.1.1    kimono            kimono
192.168.0.112    server1.example.com    server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

out of shear frustration i copied all i could down to the server name and now not sure how to change it. I have no idea what is wrong i checked the id numbers for jen on both the server and kimono and they are the same including the password i can ssh from one machine to the other but cannot mount.
jen@kimono:~$ sudo mount 192.168.0.112:/home/jen/music /home/jen/jmusic
mount.nfs: mount to NFS server '192.168.0.112:/home/jen/music' failed: RPC Error: Program not registered

jen@kimono:~$ sudo mount -v 192.168.0.112:/home/jen/music /home/jen/jmusic
mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Thu Jul  1 12:15:01 2010
mount.nfs: text-based options: 'addr=192.168.0.112'
mount.nfs: mount(2): Operation not supported
mount.nfs: mount to NFS server '192.168.0.112:/home/jen/music' failed: RPC Error: Program not registered

---

### Post by joeoshawa on 2010-07-01
here is the rpc from the server on the server
joe@server1:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  56672  status
    100024    1   tcp  44540  status
    100021    1   udp  55258  nlockmgr
    100021    3   udp  55258  nlockmgr
    100021    4   udp  55258  nlockmgr
    100021    1   tcp  34672  nlockmgr
    100021    3   tcp  34672  nlockmgr
    100021    4   tcp  34672  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  42354  mountd
    100005    1   tcp  36132  mountd
    100005    2   udp  42354  mountd
    100005    2   tcp  36132  mountd
    100005    3   udp  42354  mountd
    100005    3   tcp  36132  mountd

hosts
127.0.0.1    localhost.localdomain    localhost
192.168.0.112    server1.example.com    server1
192.168.0.108    kimono            kimono

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
hosts.allow
ALL: 192.168.0.108/255.255.255.0
hosts.deny
ALL: ALL

---

### Post by dalitso on 2010-07-01
Try this

On server side
```
nano /etc/exports
```

add the following lines
```
/home/jen/music 192.168.0.0/24(rw,sync,no_root_squash)

```
Then save
```
sudo /etc/init.d/nfs-kernel-server restart

```


On client side
```
sudo mount 192.168.0.112:/home/jen/music /home/jen/jmusic
```


Make sure nfs is installed on client
```
sudo apt-get install portmap nfs-common

```

Check [https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html)

---

