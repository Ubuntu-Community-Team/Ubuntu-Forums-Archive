---
title: "Can view smb://www/apache_proj but can't mount via smbfs"
date: 2011-01-04
forum: Server Platforms
---

### Post by altonbr on 2011-01-04
I have three folders I need to connect to via samba. I have two of them working, one of them has a password.

working:
```
//freenas.local/shared/ /home/user/Desktop/shared smbfs guest,rw,iocharset=utf8,uid=1000,gid=1000 0 0
```working:
```
//lamp/www/ /home/user/Desktop/lamp smbfs username=edited,password=edited,rw,iocharset=utf8,uid=1000,gid=1000 0 0
```not working:
```
//www/apache_proj/ /home/user/Desktop/apache smbfs guest,rw,iocharset=utf8,uid=1000,gid=1000 0 0
```Yet, for the last one, like the other two, I can view smb://www/apache_proj in Nautilus.

When I try to mount my /etc/fstab, this is the error I get:
```
$ sudo mount -a
Warning: mapping 'guest' to 'guest,sec=none'
mount error: could not resolve address for www: No address associated with hostname
```Does anyone know why that could be?

---

### Post by the dsc on 2011-01-05
A common workaround is to use IPs instead of names, but I'm also looking for a real solution. Funnily enough, it seems that for some people, the problem is the opposite, they can't use IPs, only names will work!


I'm suspicious that dnsmasq may interfere with that, that's one possibly related thing I think I have installed/active.

---

### Post by the dsc on 2011-01-05
Dnsmasq probably had nothing to do with that.

Apparently I have it working now.

I had to add "wins" to /etc/nsswitch.conf. (And nave wins installed).

Here's how the line looks on my file:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```



I've found this answer here:

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=10183736&postcount=8](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=10183736&postcount=8)

somewhere at the end of the post. I had found something about nsswitch before, so I started googling "nsswitch" "couldn't resolve hostname", or whatever was the error message when I tried to mount.

---

### Post by HermanAB on 2011-01-05
Note that smbfs is deprecated. Rather use its successor cifs.

---

