---
title: "Howto:  Firewall NFS in Ubuntu
 (static ports)"
date: 2007-02-03
forum: Server Platforms
---

### Post by Randy R on 2007-02-03
Howto:  Firewall NFS in Ubuntu


(Edit thanks Blinkiz)
Created in Ubuntu 7.04 verified to work in 7.10 but should work with other systems too.
      -Kernel: 2.6.20-16-generic (current kernel)
      -nfs version: 1:1.0.12-4 (current version)
(/Edit)

Background: I have a fairly tight internal firewall and wanted to keep it locked down. The ports that nfs uses in the standard configuration change making it difficult to firewall (maybe someone knows how to do this easier or another better way &#8211; Please post)

I am writing this for me (so I can replicate the configuration without the research). It took me 5 hours to figure this out. If it helps you so much the better.

I am assuming nfs is installed and operating properly before you start this howto (Dirk_DC indicates that you could also use nfs-user-server if you would like to. His instructions are included, I have not verified that it works.) There are many sources of information on how to do it (probably as simple as: apt-get install nfs)

check with:  rpcinfo -p (run the command in your favorite shell)

should look something like (except ports):

[INDENT]program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp   4001  nlockmgr
    100021    3   udp   4001  nlockmgr
    100021    4   udp   4001  nlockmgr
    100021    1   tcp   4001  nlockmgr
    100021    3   tcp   4001  nlockmgr
    100021    4   tcp   4001  nlockmgr
    100005    1   udp   4002  mountd
    100005    1   tcp   4002  mountd
    100005    2   udp   4002  mountd
    100005    2   tcp   4002  mountd
    100005    3   udp   4002  mountd
    100005    3   tcp   4002  mountd
    100024    1   udp   4000  status
    100024    1   tcp   4000  status[/INDENT]

if you have those services running, you are good to go

(the following shamelessly &#8220;borrowed&#8221; from [http://www.lowth.com/LinWiz/nfs_help.html]("//http://www.lowth.com/LinWiz/nfs_help.html") and modified.)
The following table lists the NFS daemons and summarizes the relevant information for them. The sections that follow give more detail.

go to the attachment to see the table. It is not essential but makes it easier to understand (I can't figure out how to do a table in forums)

Edit /etc/default/nfs-common
find the line STATDOPTS and revise as follows:

	[INDENT]STATDOPTS="--port 4000"[/INDENT]

next restart the service:  /etc/init.d/nfs-common restart

run  rpcinfo -p and you should see something like:
	[INDENT]100024    1   udp   4000  status
    	100024    1   tcp   4000  status[/INDENT]

Note the port

Edit /etc/default/nfs-kernel-server
find the line RPCMOUNTDOPTS and revise as follows:
	[INDENT]RPCMOUNTDOPTS="--p 4002"[/INDENT]

next restart the service:  /etc/init.d/nfs-kernel-server restart
run  rpcinfo -p and you should see something like:

	[INDENT]100005    1   udp   4002  mountd
    	100005    1   tcp   4002  mountd
    	100005    2   udp   4002  mountd
    	100005    2   tcp   4002  mountd
    	100005    3   udp   4002  mountd
    	100005    3   tcp   4002  mountd[/INDENT]

(EDIT) (Thanks Dirk_DC for the following): 

When using the nfs-user-server there is no /etc/default/nfs-kernel-server
to set the port for the mountd to 4002

In this case what you need to do is edit /etc/init.d/nfs-user-server
and change the line
start-stop-daemon --start --oknodo --quiet --exec /usr/sbin/rpc.mountd
to
start-stop-daemon --start --oknodo --quiet --exec /usr/sbin/rpc.mountd -- -P 4002

In other words, add [dash dash space dash Capital "P" space 4002] to the one in the "start)" section

next restart the service: /etc/init.d/nfs-user-server restart

(/Edit)

The following also shamelessly borrowed from: 
[http://bencer.cauterized.net/blog/index.php?blog/show/Laptop_firewall_NFS_client]("http://bencer.cauterized.net/blog/index.php?blog/show/Laptop_firewall_NFS_client")
Now create a new file /etc/modprobe.d/local with these lines:

[INDENT]# /etc/modprobe.d/local
options lockd nlm_udpport=4001 nlm_tcpport=4001
install ipv6 /bin/true
[/INDENT]
(the second line disables ipv6) - I don't know if this is necessary, it is just how I did it.

(Edit) (Thanks Dirk_DC)
In order for the above to take effect, you need to reboot, or instead of rebooting the system after changing the lockd port, you could do::
modprobe -r nfs
modprobe -r lockd
modprobe nfs
modprobe lockd

This unloads and reloads the nfs and lock kernel modules, provided you have no nfs filesystems mounted and in use.
(/Edit)

Now all you need to do is configure your favorite firewall to allow the ports listed in the table.

---

### Post by Dave M G on 2007-04-19
Small edit.

Where it says:

> Edit /etc/defaults/nfs-kernel-server
find the line RPCMOUNTDOPTS and revise as follows:
RPCMOUNTDOPTS="--p 4002"

On my system the file was in /etc/default, not /etc/defaults 

I don't know if that's a typo in the original, or if something changed along the way, but that's where I found the file in Feisty.

---

### Post by marsanpin on 2007-05-01
Hi,

it's correct: "default" not "defaults".
Nevertheless it's a terrific how-to Randy R!
Many thanks for your help.

:) 
Mario

---

### Post by Elif Tymes on 2007-05-02
Awesome how to! Helped me set up my home NFS mount so I can access it from work :)

---

### Post by ranjeetrao on 2007-05-31
Hi.  I, also wanted to thank you for this. Helped settle my NFS problems real quick.

---

### Post by tarap on 2007-09-06
This was so very simple and worked great. Thanks!! :cool:

---

### Post by Randy R on 2007-09-08
Thanks guys.

I edited the howto to show default instead of defaults as pointed out.

---

### Post by Dirk_DC on 2007-11-10
When using the nfs-user-server there is no /etc/default/nfs-kernel-server
to set the port for the mountd to 4002

In this case what you need to do is edit /etc/init.d/nfs-user-server
and change the line
start-stop-daemon --start --oknodo --quiet --exec /usr/sbin/rpc.mountd
to
start-stop-daemon --start --oknodo --quiet --exec /usr/sbin/rpc.mountd -- -P 4002

In other words, add [dash dash space dash Capital "P" space 4002] to the one in the "start)" section

next restart the service: /etc/init.d/nfs-user-server restart

Also instead of rebooting the system after changing the lockd port, one could do::
modprobe -r nfs
modprobe -r lockd
modprobe nfs
modprobe lockd

This unloads and reloads the nfs and lock kernel modules, provided you have no nfs filesystems mounted and in use.

---

### Post by Blinkiz on 2007-12-14
Thank you for a great guide. As always on the ubuntuforums. You really gave me a bunch of hours extra.

I would like to give two suggestions.

First, tell the users that it has been created in Ubuntu 7.10 but should work with other systems to. Also tell what kernel version you are using and NFS version.
My problem when I surfed around the web was that every guide seems outdated. But when I found your guide it said "posted 4 weeks ago" and I know it was fresh. You should include some info so it's easier to know after maybe a year when a new cool NFS version has been released, that your guide is outdated.

Second, the last step with disable of ipv6. Why?

---

### Post by Randy R on 2008-02-06
Blinkiz thanks for your suggestions, I have updated the howto.

I have tried using ipv6 internally, and think I have somthing not quite right in my system. I have not bothered to try to figure it out, but with ipv6 disabled, mine works.

Dirk_DC thanks for your info. I have included it in the howto

---

