---
title: "mount to NFS server...server is down"
date: 2008-01-10
forum: Server Platforms
---

### Post by Unstuck on 2008-01-10
I am making my very first attempt at any kind of home networking.  I followed [this]("http://ubuntuforums.org/showthread.php?t=249889") advice to retrieve files from a desktop running 7.10 and copy them to a laptop running 7.04.  The steps seem straightforward, but when I try to mount the files to the laptop I get a message that reads,
> mount to NFS server '192.168.0.10' failed: server is down.

I saw the following command on another thread, entered it in the laptop and received the following response.
> portmap getport: RPC: Timed out

I'm not sure what to do next...

---

### Post by stump138 on 2008-01-10
is nfs-kernel-server running on the server?  Also make sure that you have the folders listed in your /etc/exports file.  I have found this to be the best short how-to for NFS [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by notwen on 2008-01-10
I would recommend using the ubuntuguide nfs instructions.  I run a NFS server and their guide made it very simple.  You may want to make sure your server has a static ip, so you can always trust that the specified ip will be assigned to your PC running the nfs server.  Here is a [link]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server") to said guide.  Just install the server package son your server PC and the client on your client PC.  Post back should you run into any issues and good luck. =]

---

### Post by Unstuck on 2008-01-10
I ran **rpcinfo -p** to see if the NFS server is running--I think that is the correct thing to do--and received the following response:
> loggy@desktop:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32768  status
    100024    1   tcp  34004  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32810  nlockmgr
    100021    3   udp  32810  nlockmgr
    100021    4   udp  32810  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  50862  nlockmgr
    100021    3   tcp  50862  nlockmgr
    100021    4   tcp  50862  nlockmgr
    100005    1   udp  32811  mountd
    100005    1   tcp  35160  mountd
    100005    2   udp  32811  mountd
    100005    2   tcp  35160  mountd
    100005    3   udp  32811  mountd
    100005    3   tcp  35160  mountd


Here is my /etc/exports file:
> /home/loggy/Music 192.168.0.11(rw,async) 
/home/loggy/Pics 192.168.0.11(rw,async) 
/home/loggy/Wallpaper 192.168.0.11(rw,async)
where "loggy" is the desktop with the files I want copied and the ip address is the laptop I want to copy files to

---

### Post by bodhi.zazen on 2008-01-10
and what mount command are you using ?

sudo mount -t nfs 192.168.0.10:/home/loggy/Music /mount/point

Firewall ?

---

### Post by Unstuck on 2008-01-10
I have been using the following commands to mount based on the instructions in the [HOWTO: NFS Server/Client]("http://ubuntuforums.org/showthread.php?t=249889") and I[nstalling NFS Server]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server") guides:
> sudo mount 192.168.0.10:/home/loggy/Music /home/lappy/Music

I have Firestarter installed.

The guides that have been posted by stump138 and notwen seem to be very similar to the one I used; I think the one I used is an abbreviated version of several guides.

---

### Post by stump138 on 2008-01-10
Try adding the nfs syntax from a terminal and see what you get
```
sudo mount -t nfs 192.168.0.10:/home/loggy/Music /home/lappy/Music
```

---

### Post by Unstuck on 2008-01-10
> **stump138 said:**
> Try adding the nfs syntax from a terminal and see what you get
```
sudo mount -t nfs 192.168.0.10:/home/loggy/Music /home/lappy/Music
```

I gave it a try and got the same response:
> mount to NFS server '192.168.0.10' failed: server is down.

Just curious, what does "mount -t" mean?

---

### Post by stump138 on 2008-01-10
the "-t" syntax means you are going to describe the type of mount you are trying to do.  Next question I would ask is if you are blocking the nfs port or using a firewall? and have you tried opening the nfs port with iptables?

---

### Post by bodhi.zazen on 2008-01-10
Shut down your firewalls on both server and client. If it then works we need to configure iptables (firestarter).

-t = file type. If none is specified it defaults to auto(detect).

see man mount

---

### Post by Unstuck on 2008-01-10
> Shut down your firewalls on both server and client. If it then works we need to configure iptables (firestarter).
Closing the firewall did not help.

> Next question I would ask is if you are blocking the nfs port or using a firewall? and have you tried opening the nfs port with iptables?
I did not make any changes to iptables...can you recommend a guide to opening the nfs port?

Thanks so much to everyone that has helped so far.  I truly appreciate it.

---

### Post by stump138 on 2008-01-10
if you have nfs on the standard port of 2049 than it's just this on the server:
```
sudo iptables -A INPUT -p tcp --dport 2049 -j ACCEPT
```

you can also do the same for udp packets with

```
sudo iptables -A INPUT -p udp --dport 2049 -j ACCEPT
```

---

### Post by bodhi.zazen on 2008-01-10
> **Unstuck said:**
> Closing the firewall did not help.

You have to be more specific then that. What is "closing the firewall" ?

I assume you mean you are running firestarter or a gui ?

Well, assuming firestarter, firestarter is a gui config tool. Closing firestarter does nothing to your firewall settings.

If you are running firestarter you need to "stop" the firewall, not just close the gui.

If it is firestarter you should not be running that gui tool all the time anyway, it runs as root ans is a security risk.

Other gui tools vary ...

---

### Post by Unstuck on 2008-01-10
> sudo iptables -A INPUT -p tcp --dport 2049 -j ACCEPT 
After I entered this code and tried to mount the files, Firestarter informed me the laptop was trying to connect.  I allowed the connection and now the files mount quickly.

Now I understand the difference between the firewall and firestarter and do not run firestarter all the time.  In the future, I will try to be more specific with my questions.

Thank you very much, bodhi and stump!

---

