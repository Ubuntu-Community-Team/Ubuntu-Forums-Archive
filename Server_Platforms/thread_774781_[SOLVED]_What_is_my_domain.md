---
title: "[SOLVED] What is my domain??"
date: 2008-04-29
forum: Server Platforms
---

### Post by weryl on 2008-04-29
Hi all,

Ive been using Ubuntu & Xubuntu for a while but now I'd like to get a comp running on ubuntu server. I'm still reading the guide but there's something i cant figure out about the domain. Say i just wanna have a NFS at home, i read from the guide that i must install the right packages but then i have to type this from the client:

sudo mount example.hostname.com:/ubuntu /local/ubuntu

does that mean that i have to pay for a domain? when i installed ubuntu server i left the domain blank, so what do i have to do now? cant i just type the name of the machine \\example or example:/ubuntu ?

Thanx alot,

Mike

---

### Post by cdtech on 2008-04-29
I setup my server reading this post:
[[COLOR="DarkRed"]The perfect setup[/COLOR]]("http://howtoforge.com/perfect_setup_ubuntu_6.06")

I also registered with [[COLOR="DarkRed"]dyndns[/COLOR]]("http://www.dyndns.com/") for a domain name using a dynamic ip address from my provider. Works really well and it's free.

Once you have your free domain name you can type on a command line:
```
hostname server.mydomain.com
```
This will give your home server the name SERVER with your FQDN of mydomain.com

Setup your apache server and login to your domain name. Happy webing :)

Hope this helps......

---

### Post by weryl on 2008-04-29
> **cdtech said:**
> I setup my server reading this post:
[[COLOR="DarkRed"]The perfect setup[/COLOR]]("http://howtoforge.com/perfect_setup_ubuntu_6.06")

I also registered with [[COLOR="DarkRed"]dyndns[/COLOR]]("http://www.dyndns.com/") for a domain name using a dynamic ip address from my provider. Works really well and it's free.

Once you have your free domain name you can type on a command line:
```
hostname server.mydomain.com
```
This will give your home server the name SERVER with your FQDN of mydomain.com

Setup your apache server and login to your domain name. Happy webing :)

Hope this helps......

Thanx alot, exactly what i was looking for!

---

### Post by scorp123 on 2008-04-29
> **weryl said:**
>  I'm still reading the guide but there's something i cant figure out about the domain. Say i just wanna have a NFS at home, i read from the guide that i must install the right packages but then i have to type this from the client:

sudo mount example.hostname.com:/ubuntu /local/ubuntu

does that mean that i have to pay for a domain?  If that's just for home use (opening up NFS towards the Internet would be crazy anyway ..) you can make something up. Or you could just use the one of your provider (e.g. whatever it says in your e-mail address after the "@" ...). And if your router is working properly the mount command will probably also work without a domain. Or you could use IP addresses too. Or you could add the IP addresses of your hosts into the **/etc/hosts** file .... 

But you definitely don't have to pay for a domain and don't need to setup your own DNS server if all you want is to mount a NFS share.

---

### Post by scorp123 on 2008-04-29
> **cdtech said:**
> I setup my server reading this post:
[[COLOR="DarkRed"]The perfect setup[/COLOR]]("http://howtoforge.com/perfect_setup_ubuntu_6.06")

I also registered with [[COLOR="DarkRed"]dyndns[/COLOR]]("http://www.dyndns.com/") for a domain name using a dynamic ip address from my provider. Works really well and it's free.

Once you have your free domain name you can type on a command line:
```
hostname server.mydomain.com
```
This will give your home server the name SERVER with your FQDN of mydomain.com  Did you read his posting? He's just trying to mount a NFS share. Your guide is total overkill here IMHO.

---

### Post by weryl on 2008-04-29
Hum thanx scorp123, i think your answer's perfect for what i described. I'll look into what cdtech said too though since it seems to be free.

---

### Post by ginjabunny on 2008-05-02
When I install the server I just give it a name, e.g. fred.

if this is only for home use, then only thing that seems to demands a fqdn is postfix, which I only set it up for local use, so I just made one up.

I just mount nfs shares from my other linux boxes using the IP address, I am not sure if this is the recommended way to do it but I just created a dir /net on each pc then a subdir with the share name and add it to fstab like

192.168.1.1:/home/backups	/net/backups		nfs	rsize=8192,wsize=8192,timeo=14,intr,noatime	0	0

works for me :)

---

