---
title: "unable to share removable media through NFS"
date: 2008-01-12
forum: Server Platforms
---

### Post by chiron69 on 2008-01-12
Good afternoon,

I'm using Kubuntu Gutsy and I have this problem
I can not share /media with NFS. On the client machine I can see the directory but I can not browse inside my external usb drives, I have the icon with the padlock.
However I can share my /home folder without any problem.

I tried then the following:
sudo mount /dev/sdb1 /home/jyl/test

On the server machine I can browse inside the usb drive from the /home/jyl/test directory, but from the client side the directory is empty.
the external drive is formatted with EXT3.

Can anybody help?

---

### Post by k_grdn on 2008-01-12
Hi,

What have you got in your /etc/exports?

Have you firewalled your system?
 
rpc.mountd uses a random port under 1024 every time the daemon is loaded so to firewall nfs you need to create a static entry to mount in /etc/services.

Regards,

k_grdn

---

### Post by chiron69 on 2008-01-12
My system is not firewalled, my /home share with NFS works perfectly.
I've checked with firestarter, nothing relevant.

my /etc/exports file:

```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/jyl/ 192.168.1.10/255.255.255.0(rw,async)
/media/ 192.168.1.10/255.255.255.0(rw,async)


```

192.168.1.10 is the IP adress of the client, it is always the same (IP reserved on the dhcp server).

---

### Post by k_grdn on 2008-01-12
Hi,

So you external drive is mounted on:/home/jyl/test ?

If so the exports entry should be:

/home/jyl/test 192.168.1.10/255.255.255.0(rw,async)

To share your drive in /media.

On server:

mount /dev/sda1 /media/usb 

Edit /etc/exports

/media/usb 192.168.1.10/255.255.255.0(rw,async)

On Client:

mount -t nfs server:/media/usb 

Or add the entry to /etc/fstab

server:/media/usb     /client-mount-dir      nfs     timeo=14,intr,soft



Regards,

k_grdn

---

### Post by chiron69 on 2008-01-13
> **k_grdn said:**
> Hi,

So you external drive is mounted on:/home/jyl/test ?

If so the exports entry should be:

/home/jyl/test 192.168.1.10/255.255.255.0(rw,async)

To share your drive in /media.

On server:

mount /dev/sda1 /media/usb 

Edit /etc/exports

/media/usb 192.168.1.10/255.255.255.0(rw,async)

On Client:

mount -t nfs server:/media/usb 

Or add the entry to /etc/fstab

server:/media/usb     /client-mount-dir      nfs     timeo=14,intr,soft



Regards,

k_grdn


I've already done all of that, I can not access the drive from the client. With the same method I can share any other directory of my system without any problem. Why?:confused:

---

### Post by chiron69 on 2008-01-29
up. I'm still stuck with that.:(

---

### Post by xdefconx on 2008-01-30
up. I also looking for this solutions huhuhu...it is here anyone had done succesfully to share your pendrive/USB drive on ur Ubuntu over the LAN ? huhuhuhu

---

